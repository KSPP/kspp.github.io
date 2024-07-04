# Details

When variables (on either stack or heap) are used without being
explicitly initialized, behavior is "undefined". In reality,
"uninitialized" just means "still has the prior value". When an attacker
can control prior values, this can lead to exploitation or leaks, either
through regular techniques or through "data-only" attacks.

# Examples

  - [Kernel Exploitation via Uninitialized
    Stack](https://outflux.net/slides/2011/defcon/kernel-exploitation.pdf)

# Mitigations

  - clear kernel stack between system calls (e.g.
    PAX_MEMORY_STACKLEAK)
  - instrument compiler to fully initialize all structures (e.g.
    PAX_MEMORY_STRUCTLEAK)