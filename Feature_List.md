Feature List
============

This is a list of various interesting security features since v3.4 and
when they were introduced in the upstream kernel. Feel free to add
anything more\!

| Version                                | Feature                                      |
| -------------------------------------- | -------------------------------------------- |
| v3.5                                   | seccomp-bpf, x86                             |
| v3.7                                   | PXN, arm64                                   |
| v3.8                                   | seccomp-bpf, arm                             |
| seccomp reported in /proc/$pid/status  |                                              |
| finit_module syscall and LSM hook     |                                              |
| v3.13                                  | remove %n from printf                        |
| v3.14                                  | ptdump, arm                                  |
| kaslr, x86                             |                                              |
| modules ro/nx, arm                     |                                              |
| stack-protector-strong                 |                                              |
| kexec_load_disabled                  |                                              |
| v3.15                                  | seccomp-bpf, mips                            |
| lkdtm WRITE_KERN                      |                                              |
| module aslr, x86                       |                                              |
| v3.16                                  | harden sysctl writing                        |
| v3.17                                  | seccomp syscall and TSYNC                    |
| request_firmware LSM hook             |                                              |
| v3.18                                  | kernel memory W^X, x86                       |
| overlayfs v3.18                        |                                              |
| v3.19                                  | kernel ro/nx, arm                            |
| modules ro/nx, arm64                   |                                              |
| ptdump, arm64                          |                                              |
| seccomp-bpf, arm64                     |                                              |
| PXN, arm                               |                                              |
| crypto- module prefixing               |                                              |
| ecryptfs one-byte heap write fix       |                                              |
| arm64 mmap ASLR fix                    |                                              |
| vdso ASLR fix, x86_64                 |                                              |
| vsyscall=none, x86_64                 |                                              |
| vdso ASLR, mips                        |                                              |
| v4.0                                   | kernel ro/nx, arm64                          |
| stack ASLR fix                         |                                              |
| seccomp-bpf, RET_ERRNO capped to 4095 |                                              |
| v4.1                                   | kernel stack buffer overflow detection, mips |
| INET_DIAG cookies fixed               |                                              |
| ET_DYN ASLR separate from mmap ASLR   |                                              |
| v4.3                                   | PAN emulation, arm                           |
| ambient capabilities                   |                                              |
| seccomp-bpf, powerpc                   |                                              |
| x86_32 direct socket calls            |                                              |
| v4.4                                   | vsyscall CONFIG                              |
| v4.5                                   | ASLR entropy bits sysctl                     |
| v4.6                                   | KASLR, arm64                                 |
| RODATA on by default, arm64            |                                              |
| RODATA on by default, arm (ARMv7+)     |                                              |
| RODATA mandatory, x86                  |                                              |
| v4.7                                   | LoadPin LSM                                  |
| KASLR text, MIPS                       |                                              |
| SLAB freelist ASLR                     |                                              |
| brk ASLR weakness fixed, arm64 compat  |                                              |
| eBPF JIT blinding                      |                                              |
| v4.8                                   | SLUB freelist ASLR                           |
| KASLR text phys/virt split, x86_64    |                                              |
| KASLR memory, x86_64                  |                                              |
| gcc-plugin infrastructure              |                                              |
| fix _etext, arm                       |                                              |
| fix _etext, arm64                     |                                              |
| HARDENED_USERCOPY lkdtm tests         |                                              |
| KASLR with hibernation, x86            |                                              |
| seccomp vs ptrace fixed                |                                              |
| HARDENED_USERCOPY                     |                                              |
| NX stack and heap, mips                |                                              |
| v4.9                                   | latent_entropy plugin                       |
| vmap stack, x86                        |                                              |
| thread_info in task_struct, x86      |                                              |
| random_page() cleanup                 |                                              |
| RODATA mandatory, arm64                |                                              |
| user_ns restrictions                  |                                              |
| v4.10                                  | CONFIG_DEBUG_LIST hardening                |
| PAN emulation, arm64 v8.0              |                                              |
| thread_info in task-struct, arm64     |                                              |
| get_user zeroing fix, arm             |                                              |
| report nnp                             |                                              |
| seed RNG from UEFI                     |                                              |
| CONFIG_DEBUG_WX, arm64               |                                              |
|                                        |                                              |
