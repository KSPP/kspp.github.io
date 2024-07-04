# Details

When an attacker supplied string is accidentally passed to format string
parsing, the attacker can manipulate the resulting output. The write
primitive available is through the use of the %n specifier, which writes
to memory. All the other formats lead to information leaks.

# Examples

  - [injection via block layer](http://seclists.org/oss-sec/2013/q2/510)

# Mitigations

  - [Eliminate the use of
    %n](https://git.kernel.org/linus/708d96fd060bd1e729fc93048cea8901f8bacb7c)
  - detect non-const format strings at compile time (e.g. gcc's
    -Wformat-security)
  - detect non-const format strings at run time (e.g. memory location
    checking done with glibc's -D_FORITY_SOURCE=2)