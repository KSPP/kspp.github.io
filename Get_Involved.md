---
title: Get Involved
---

* TOC
{:toc}

Want to get involved in the [Kernel Self Protection Project](/)? Here's how:

# Join the conversations

  - Subscribe to the [**upstream** Linux kernel hardening mailing
    list](http://vger.kernel.org/vger-lists.html#linux-hardening),
    **`linux`**`-hardening@vger.kernel.org`, where development,
    maintenance, and administrivia happen. (And visit the [list
    archive](https://lore.kernel.org/linux-hardening/).)
  - Come to the every-2-weeks status update meeting. See the
    [calendar](https://calendar.google.com/calendar/u/0/embed?src=47005f8f50f21da6133d7239f3cb93d1624d2e1949963ea75dd86d5f2d5721e0@group.calendar.google.com&ctz=America/Los_Angeles)
    for details.
  - Join the `#linux-hardening` IRC channel on
    [Libera.Chat](https://libera.chat/).
  - Optionally subscribe to the [**general** Linux kernel hardening
    mailing list](https://www.openwall.com/lists/kernel-hardening/),
    **`kernel`**`-hardening@lists.openwall.com`, where new hardening
    topics and summaries of completed work are discussed. (And visit the
    [list archive](https://lore.kernel.org/kernel-hardening/).)
      - Note: when sending to `kernel-hardening@lists.openwall.com`,
        please also CC `linux-hardening@vger.kernel.org` too.

# Introduce Yourself

Send an email to the lists to introduce yourself\!

  - What topics are you interested in?
  - What do you want to learn about?
  - What experience do you have with security, the kernel, programming,
    or anything else you think is important.

# Pick something to work on

Pick something from the [issue
tracker](https://github.com/KSPP/linux/issues) (or add a new one),
coordinate on the mailing lists, and get started. If your employer is
brave enough to understand how critical this work is, they'll pay you to
work on it. If not, the [Linux
Foundation](https://www.linuxfoundation.org/)'s [Core Infrastructure
Initiative](https://www.coreinfrastructure.org/faq) is in a great
position to fund specific work proposals. We need kernel developers,
compiler developers, testers, backporters, a documentation writers.

# Contribute patches

Please send new topics and patch series to both
[linux-hardening@vger.kernel.org](http://vger.kernel.org/vger-lists.html#linux-hardening)
and
[kernel-hardening@lists.openwall.com](https://www.openwall.com/lists/kernel-hardening)
for the widest audience possible.

When contributing patches for the Linux kernel, be sure to follow the
Linux kernel [Coding Style
Guide](https://www.kernel.org/doc/html/latest/process/coding-style.html)
and read about [Submitting
Patches](https://www.kernel.org/doc/html/latest/process/submitting-patches.html).
Even if you're only sending your patches to the mailing lists for some
early review, it's best to get as much of the coding style and
submission semantics correct to avoid reviewers needing to recommend
changes in those areas.

## grsecurity and other non-upstream patch sources

As with any other Free Software project, it is particularly important
that if you're working on upstreaming work from other projects, be sure
your patches are giving credit to the original authors, that licenses
are compatible, and that copyright notices are retained, etc.

In the case of new files, or other places where a copyright notice would
be expected to be added, be sure to retain all copyright notices from
the other project. This may require some examination of commit history.
For example, [grsecurity's copyright notice from their most recent
public
patch](https://github.com/linux-scraping/linux-grsecurity/blob/grsec-test/grsecurity/Makefile#L3)
does not include PaX Team's copyright notice, which is only listed in
the patch for GCC plugins. For grsecurity copyright, when more specific
details are not easy to find, the following could be used:

`Copyright (C) 2001-2017 PaX Team, Bradley Spengler, Open Source Security Inc.`

Additionally, grsecurity has asked that contributors include this in
commit messages for non-trivial code ported from grsecurity:

`$CODE is {verbatim,modified} from Brad Spengler/PaX Team's code in the last`
`public patch of grsecurity/PaX based on my understanding of the code. Changes`
`or omissions from the original code are mine and don't reflect the original`
`grsecurity/PaX code.`
