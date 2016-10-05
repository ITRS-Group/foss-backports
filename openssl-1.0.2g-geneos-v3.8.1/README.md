# OpenSSL 1.0.2g for Geneos v3.8.1

## Origin

This was mostly taken from openssl 1.0.2g-1ubuntu4.5 source package in Ubuntu 16.04

* [Changelog](https://launchpad.net/ubuntu/+source/openssl/1.0.2g-1ubuntu4.5)

As per Debian/Ubuntu policy, patches are applied against the pristine upstream source. It can be verified that upstream 
OpenSSL 1.0.2g and [Ubuntu 16.04's OpenSSL 1.0.2g](https://launchpad.net/ubuntu/+archive/primary/+files/openssl_1.0.2g.orig.tar.gz) 
source package are the same given the SHA256 checksum.


## ITRS-specific changes

* Support classic ELF ".hash" and ".gnu.hash" hash tables in the linker
* Disable native chip optimization when building OpenSSL with Solaris Studio 12.3
* Remove FIPS patches introduced by Canonical Inc. to enable AIX builds (merely disabling does not work).

## Build Environment

* Linux x86: GCC 3.4.6 (from compat-gcc34-c++ package) on RHEL 5.11
* Linux x86_64: GCC 4.1.2 (vendor) on RHEL 5.11
* Solaris x86/x86_64: Solaris Studio 12.3 on Solaris 10u11
* Solaris SPARC/SPARC64: Solaris Studio 12.3 on Solaris 10u11
* AIX PPC: xlC 12.1 on AIX 6.1 TL8
* Windows x86: Visual Studio 2010 SP1 on Windows Server 2008 SP2


## Configuration

### Linux x86 

```
  ./config shared -I/usr/lib/gcc/i386-redhat-linux/3.4.6/include no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Linux x86_64

```
  ./config shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Solaris x86

```
  ./Configure solaris64-x86-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Solaris x86_64

```
  ./Configure solaris64-x86_64-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Solaris SPARC

```
  ./Configure solaris-sparcv9-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Solaris SPARC64

```
  ./Configure solaris64-sparcv9-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### AIX PPC

```
  ./Configure aix-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### AIX PPC64

```
  ./Configure aix64-x86_64-cc shared no-ssl2 no-ssl3 no-asm enable-tlsext
  make
```

### Windows x86
```
  perl Configure VC-WIN32 no-asm enable-tlsext enable-capieng
  ms\do_nt
  nmake -f ms\ntdll.mak
```

## Backported fixes

* CVE-2016-2177
* CVE-2016-2178
* CVE-2016-2179
* CVE-2016-2180
* CVE-2016-2181
* CVE-2016-2182
* CVE-2016-2183
* CVE-2016-6302
* CVE-2016-6303
* CVE-2016-6304
* CVE-2016-6306
