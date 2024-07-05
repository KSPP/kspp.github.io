---
title: Areas of Work Needed
---

We have a lot of work to do! While there are already many upstream
security features, we are still missing many more.

For the list of specific items and desired features, see the
[KSPP Issue Tracker](https://github.com/KSPP/linux/issues).

General concepts and concerns are here:

## Bug Classes

Many bugs in the kernel belong to specific classes. Here we try to focus
on classes of bugs that have security implications, explain them, link
to examples, and link to defenses that are or could be used to entirely
eliminate the bug class.

  - [Stack overflow](Bug_Classes/Stack_overflow)
  - [Integer overflow](Bug_Classes/Integer_overflow)
  - [Heap overflow](Bug_Classes/Heap_overflow)
  - [Format string injection](Bug_Classes/Format_string_injection)
  - [Kernel pointer leak](Bug_Classes/Kernel_pointer_leak)
  - [Uninitialized variables](Bug_Classes/Uninitialized_variables)
  - [Use-after-free](Bug_Classes/Use_after_free)

## Exploitation Methods

When flaws in the kernel provide unintended read and write primitives
to an attacker, there are many techniques used to gain execution control
over the kernel. Here we try to explain them, link to examples, and link
to defenses that are or could be used to eliminate an exploitation method.

  - [Kernel location](Exploit_Methods/Kernel_location)
  - [Text overwrite](Exploit_Methods/Text_overwrite)
  - [Function pointer overwrite](Exploit_Methods/Function_pointer_overwrite)
  - [Userspace execution](Exploit_Methods/Userspace_execution)
  - [Userspace data usage](Exploit_Methods/Userspace_data_usage)
  - [Reused code chunks](Exploit_Methods/Reused_code_chunks)
