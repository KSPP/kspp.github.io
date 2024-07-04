# Details

Integer overflows (or underflows) occur when a multiplication happens
that exceeds the size that can be represented by the datatype, generally
wrapping around. This usually results in either writing to too-small
buffers, or producing out of bound array indexes. Exploitation is most
common via heap overflows, since the (too-small) buffers tend to be
allocated on the heap. Additionally, reference counting can overflow and
wrap around, leading to use-after-free exploits.

# Examples

  - [slub
    overflow](https://jon.oberheide.org/blog/2010/09/10/linux-kernel-can-slub-overflow/)
  - [group_info refcount
    overflow](https://cyseclabs.com/page?n=02012016)
  - [keyring refcount
    overflow](http://perception-point.io/2016/01/14/analysis-and-exploitation-of-a-linux-kernel-vulnerability-cve-2016-0728/)
  - [netfilter xt_alloc_table_info integer
    overflow](https://code.google.com/p/google-security-research/issues/detail?id=758)

# Mitigations

  - check for refcount overflows (e.g. PAX_REFCOUNT)
  - compiler instrumentation to detect multiplication overflows at
    runtime (e.g.
    [PAX_SIZE_OVERFLOW](https://github.com/ephox-gcc-plugins))