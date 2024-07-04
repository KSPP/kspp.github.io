# Details

The traditional bug results in the stack buffer being written past the
end of the stack frame, which allows the saved instruction pointer to be
overwritten in order to gain execution control ("stack buffer
overflow"). A stack depth overflow bug is when the size of the stack
grows past its maximal size (via deep call stacks or via alloca abuse),
and allows writing on other stacks or threadinfo. Other attacks could
stay within the stack frame, manipulating local variables ("data only"
attacks), and some attacks allow for writing by arbitrary offsets
between kernel stacks.

# Examples

  - [half-nelson.c](https://jon.oberheide.org/files/half-nelson.c) This
    uses stack offsets, rather than the traditional buffer overflow.

# Mitigations

  - stack canaries (e.g. gcc's -fstack-protector and
    [-fstack-protector-strong](https://git.kernel.org/linus/8779657d29c0ebcc0c94ede4df2f497baf1b563f))
  - guard pages (e.g. GRKERNSEC_KSTACKOVERFLOW)
  - alloca checking (e.g. PAX_MEMORY_STACKLEAK)
  - kernel stack location randomization
  - shadow stacks