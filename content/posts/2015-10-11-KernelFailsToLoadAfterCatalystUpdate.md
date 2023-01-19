---
title: 'Kernel fails to load after Catalyst update'
slug: 'kernel-fails-to-load-after-catalyst-update'
date: 2015-10-11T13:13:13-08:00
tags: ['linux', 'arch']
---

Today I did a system update on my Arch Linux installation with the command
`yaourt -Syua` and after that the Kernel refused to boot with an error message
similar to the following in `journalctl -b`:

    kernel: RIP firegl trace+0x61/0x1e0

There is a know problem with the proprietary catalyst drivers not supporting
linux kernels >= 4.2. So to fix this issue you have to configure the bootloader
to use a different kernel, such as `linux-lts`. Install `linux-lts` package and
then reinstall the `catalyst*` packages from the Vi0L0 AUR repos and then
re-configure GRUB with `grub-mkconfig -o /boot/grub/grub.cfg`.

I had to boot and mount everything using the Arch live install system then
`chroot` and reinstall the catalyst packages with the LTS kernel to fix the
issue.

When rebooting make sure to pick the LTS kernel from the GRUB menu.

Vi0L0 himself has created a bug for this at the [Unofficial AMD
Bugzilla](http://ati.cchtml.com/show_bug.cgi?id=1189), but a fix may take a long
time if past behavior is any indication of current outcome.
