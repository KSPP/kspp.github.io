# Details

When a memory allocation gets freed but there are still accidentally
users of that memory, it is possible that an attacker could control the
new memory allocation that fills the freed area, and then manipulate the
contents in a way that the system uses its stale pointer and expects a
different structure than is currently present. If there are function
pointers contained in the structure, this allows for trivial execution
control.

# Examples

  - [keyring
    use-after-free](http://perception-point.io/2016/01/14/analysis-and-exploitation-of-a-linux-kernel-vulnerability-cve-2016-0728/)

# Mitigations

  - clearing memory on free can stop attacks where there is no
    reallocation control (e.g. PAX_MEMORY_SANITIZE)
  - segregating memory used by the kernel and by userspace can stop
    attacks where this boundary is crossed (e.g. PAX_USERCOPY)
  - randomizing heap allocations can frustrate the reallocation efforts
    the attack needs to perform (e.g. OpenBSD malloc)
  - reference counter overflow protection (e.g. PAX_REFCOUNT,
    HARDENED_ATOMIC)