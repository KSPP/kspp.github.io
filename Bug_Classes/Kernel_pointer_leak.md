# Details

When a kernel memory address (any of text, stack, heap, etc) leaks into
userspace, attackers can learn potentially sensitive information about
data layout, kernel layout, stack layout, architecture layout, etc.
These can be used in turn to perform attacks where those sensitive
locations are needed for a successful exploitation. If locations aren't
identified correctly, an attacker could crash the entire system, which
makes kernel leaks critical to successful exploitation.

# Examples

  - so many: /proc (kallsyms, modules, slabinfo, etc), /sys, etc
  - [alpha-omega.c](http://vulnfactory.org/exploits/alpha-omega.c) uses
    INET_DIAG to target socket structure function pointers on the heap

# Mitigations

  - [kptr_restrict](https://git.kernel.org/linus/455cd5ab305c90ffc422dd2e0fb634730942b257)
    is too weak: requires opt-in by developers
  - remove visibility to kernel symbols (e.g. GRKERNSEC_HIDESYM)
  - detect and block usage of %p or similar writes to seq_file or other
    user buffers (e.g. GRKERNSEC_HIDESYM + PAX_USERCOPY)