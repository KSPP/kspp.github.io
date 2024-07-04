# Details

Heap overflows tend to occur due to integer overflows or otherwise
broken bounds checking. Exploits overwrite adjacent heap memory, or
manipulate the heap metadata values.

# Examples

  - [pty race
    condition](http://blog.includesecurity.com/2014/06/exploit-walkthrough-cve-2014-0196-pty-kernel-race-condition.html)

# Mitigations

  - runtime validation of variable size vs
    copy_to_user/copy_from_user size (e.g. PAX_USERCOPY)
  - guard pages
  - metadata validation (e.g. glibc's heap protections)