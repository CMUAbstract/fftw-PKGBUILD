# Arch Linux PKGBUILD for FFTW library.

This repository is (quasi-)forked from Arch Linux ARM
[PKGBUILDs](https://github.com/archlinuxarm/PKGBUILDs) repository. The changes
are to enable ARM NEON SIMD support for better performance.

See branches for ARM cores that this fork supports.

When building, also change flags in `/etc/makepkg.conf` to enable optimization
and tuning for native CPU: `-march=native -mtune=native -mfpu=neon -O3`.
