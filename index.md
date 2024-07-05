---
title: Kernel Self Protection Project
layout: home
redirect_from:
  - /KSPP/
  - /Kernel_Self_Protection/
---

* TOC
{:toc}

# Mission Statement

This project starts with the premise that
[kernel bugs have a very long lifetime](https://lwn.net/Articles/410606/), and that the kernel must be
designed in ways to protect against these flaws. We must think of
[security beyond fixing bugs](http://lwn.net/Articles/662219/). As a
community, we already find and fix individual bugs via static checkers
(compiler flags, [smatch](http://smatch.sourceforge.net/),
[coccinelle](http://coccinelle.lip6.fr/),
[coverity](https://scan.coverity.com/projects/linux-next-weekly-scan?tab=overview)) and
dynamic checkers (kernel configs,
[trinity](http://codemonkey.org.uk/projects/trinity/),
[KASan](https://www.kernel.org/doc/Documentation/kasan.txt)). Those
efforts are important and on-going, but if we want to protect our
[billion Android phones](http://www.techspot.com/news/57228-google-shows-off-new-version-of-android-announces-1-billion-active-monthly-users.html),
our [cars](http://www.zdnet.com/article/2014-the-year-of-the-linux-car/),
the [International Space Station](https://training.linuxfoundation.org/why-our-linux-training/training-reviews/linux-foundation-training-prepares-the-international-space-station-for-linux-migration),
and everything else running Linux, we must get proactive defensive
technologies built into the upstream Linux kernel. We need the kernel to
[fail safely, instead of just running safely](http://kernsec.org/files/lss2015/giant-bags-of-mostly-water.pdf).

These kinds of protections have existed for years in out-of-tree
projects and in piles of academic papers. For various social,
cultural, and technical reasons, they have not made their way into
the upstream kernel, and this project seeks to change that. Our focus
is on kernel self-protection, rather than kernel-supported userspace
protections. The goal is to eliminate classes of bugs and eliminate
methods of exploitation.

# Principles

A short list of things to keep in mind when designing self-protection
features:

  - Patience and an open mind will be needed. We're all trying to make
    Linux better, so let's stay focused on the results.
  - Upstream development is evolutionary, not revolutionary, which means
    it can sometimes [take
    time](https://ieeexplore.ieee.org/abstract/document/6624016) for
    features to become fully realized.
  - Features will be more than finding bugs, and should be active at
    run-time to catch previously unknown flaws.
  - Features will not be developer-"opt-in". When a feature is enabled
    at build time, it should work for all code built into the kernel
    (which has the side-effect of also covering out-of-tree code, like
    in vendor forks).

# Details

Specific details on the project:

  - [Get Involved](Get_Involved)
  - [Areas of Work Needed](Work)
  - [Recommended Kernel Settings](Recommended_Settings)
  - [Patch Tracking](Patch_Tracking)

# Documentation

For kernel protections already in upstream (or under active development)
that have specific documentation:

  - [Self-Protection Guidelines](https://www.kernel.org/doc/html/latest/security/self-protection.html)
  - [refcount_t](Kernel_Protections/refcount_t) Kernel
    reference counter overflow protection
  - [Analysis on Kernel Self-Protection: Understanding Security and
    Performance Implication](https://samsung.github.io/kspp-study/)
    ([github](https://github.com/Samsung/kspp-study))
