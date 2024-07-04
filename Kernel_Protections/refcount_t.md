# Summary

The refcount_t API is a kernel self-protection mechanism that greatly
helps with the prevention of
[use-after-free](Bug_Classes/Use_after_free "wikilink") bugs. It is
based off of work done by the [PaX Team](https://pax.grsecurity.net),
originally called
[PAX_REFCOUNT](https://forums.grsecurity.net/viewtopic.php?f=7&t=4173).

# Reference Counting API

Instead of the traditional `atomic_t`, reference counting uses a new
data type: `refcount_t`. This type is to be used for all kernel
reference counters.

The following is the kernel reference counting API.

  - **`REFCOUNT_INIT(unsigned int)`**
    Initialize a `refcount_t` object.

<!-- end list -->

  - **`void refcount_set(refcount_t *, unsigned int)`**
    Set a `refcount_t` object's internal value.

<!-- end list -->

  - **`unsigned int refcount_read(refcount_t *)`**
    Returns the `refcount_t` object's internal value.

<!-- end list -->

  - **`bool refcount_add_not_zero(unsigned int v, refcount_t *r)`**
    Add `v` to `r`. If `r + v` causes an overflow, the result of the
    addition operation is not saved to `r`. Returns `true` if the
    resulting value of `r` is non-zero, `false` otherwise.

<!-- end list -->

  - **`void refcount_add(unsigned int v, refcount_t *r)`**
    Adds `v` to `r` and stores the value in `r`.

<!-- end list -->

  - **`bool refcount_inc_not_zero(refcount_t *r)`**
    Increments `r` and tests whether `r + 1` causes an overflow. If an
    overflow does occur, the result of the increment operation is not
    saved to `r`. Will saturate at `UINT_MAX` and `WARN`. Returns `true`
    if the resulting value of `r` is non-zero, `false` otherwise.

<!-- end list -->

  - **`void refcount_inc(refcount_t *r)`**
    Increment `r`. Will saturate at `UINT_MAX` and `WARN`.

<!-- end list -->

  - **`bool refcount_sub_and_test(unsigned int v, refcount_t *r)`**
    Subtract `v` from `r` and tests whether `r - v` causes an underflow.
    If an underflow does occur, the result of the decrement operation is
    not saved to `r`. Will fail to decrement when saturated at
    `UINT_MAX`. Returns `true` if the resulting value of `r` is
    non-zero, `false` otherwise.

<!-- end list -->

  - **`void refcount_dec(refcount_t *r)`**
    Decrement `r`. If `r - 1` causes an underflow, the result of the
    decrement operation is not saved to `r`. Will fail to decrement when
    saturated at `UINT_MAX`.

<!-- end list -->

  - **`bool refcount_dec_if_one(refcount_t *r)`**
    Attempts to transition `r` from 1 to 0. If `r` is 1, decrement it to
    0. Returns `true` if `r` was decremented, `false` otherwise.

<!-- end list -->

  - **`bool refcount_dec_not_one(refcount_t *r)`**
    Decrement `r` unless the value of `r` is 1. Returns `true` if `r`
    was decremented, </code>false</code> otherwise.

<!-- end list -->

  - **`bool refcount_dec_and_mutex_lock(refcount_t *r, struct mutex
    *lock)`**
    Decrement `r` and lock mutex if `r` becomes 0. Will `WARN` on
    underflow and fail to decrement if `r` is saturated at `UINT_MAX`.
    Returns `true` if `r` is 0 and mutex is held, `false` otherwise.

<!-- end list -->

  - **`bool refcount_dec_and_lock(refcount_t *r, spinlock_t *s)`**
    Decrement `r` and lock spinlock if `r` becomes 0. Will `WARN` on
    underflow and fail to decrement if `r` is saturated at `UINT_MAX`.
    Returns `true` if `r` is 0 and spinlock is held, `false` otherwise.

# Examples

The following use case is an instance of correct usage of the
`refcount_t` API. The object being counted is `struct super_block`,
which represents a virtual filesystem superblock, an object containing a
particular filesystem's metadata such as block size, the root inode,
etc.

#### Member Definition

This is the definition of the reference counter field in the `struct
super_block` object. If the object being counted is a structure, the
reference counter is typically defined as a field of the counted
structure, as we see in `struct super_block` below.

From
[`include/linux/fs.h`](http://lxr.free-electrons.com/source/include/linux/fs.h):

<code>

`   struct super_block {`
`       ...`
`       refcount_t s_active;`
`       ...`
`   };`

</code>

#### Object Initialization

When a counted object is created, its reference counter must be
initialized to something sane, typically 1 (since, by virtue of being
called in an "allocation" method, a user of the object already exists).

From [`fs/super.c`](http://lxr.free-electrons.com/source/fs/super.c):

<code>

`   static struct super_block *alloc_super(struct file_system_type *type, int flags, struct user_namespace *user_ns)`
`   {`
`       struct super_block *s = kzalloc(sizeof(struct super_block), GFP_USER);   `
`       ...`
`       refcount_set(&s->s_active, 1);`
`       ...`
`   }`

</code>

#### Getting a New Reference

This code is executed when a user wishes to obtain a new reference to a
`struct super_block` object. The following code corresponds to the
traditional reference counting "get" method.

From [`fs/super.c`](http://lxr.free-electrons.com/source/fs/super.c):

<code>

`   static int grab_super(struct super_block *s) __releases(sb_lock)`
`   {`
`       s->s_count++;`
`       spin_unlock(&sb_lock);`
`       down_write(&s->s_umount);`
`       if ((s->s_flags & MS_BORN) && refcount_inc_not_zero(&s->s_active)) {`
`           put_super(s);`
`           return 1;`
`       }`
`       up_write(&s->s_umount);`
`       put_super(s);`
`       return 0;`
`   }`

</code>

#### Releasing an Existing Reference

This code is executed when a user currently holding a reference to a
`struct super_block` object no longer needs the object and wants to
release it. The following code corresponds to the traditional reference
counting "put" method.

From [`fs/super.c`](http://lxr.free-electrons.com/source/fs/super.c):

<code>

`   void deactivate_locked_super(struct super_block *s) {`
`       ...`
`       if (refcount_dec_and_test(&s->s_active)) {`
`           ...`
`           put_super(s);`
`       }`
`   }`

`   void deactivate_super(struct super_block *s)`
`   {`
`       if (!refcount_dec_not_one(&s->s_active)) {`
`           down_write(&s->s_umount);nnNnnn`
`           deactivate_locked_super(s);`
`       }`
`   }`

</code>