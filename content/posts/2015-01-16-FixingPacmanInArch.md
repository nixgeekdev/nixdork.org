---
title: 'Fixing package-query to pacman dependency in Arch Linux'
slug: 'fixing-package-query-to-pacman-dependency-in-arch'
date: 2015-01-16T19:07:51-08:00
tags: ['linux','arch']
---

I was recently trying to update my Arch Linux system and I ran into a peculiar
dependency error with `package-query` that would complety halt the update.

    error: failed to prepare transaction (could not satisfy dependencies)
    :: package-query: requires pacman<4.2

It turns out that this is totally expected and it has to do with the new version
of Pacman (4.2) breaking a few things related to backwards compatibility. This
changes will require me to recompile and reinstall `package-query` and `yaourt`
and here's how to do it:

1.  Uninstall `package-query` and `yaourt`

        sudo pacman -Rdd package-query
        sudo pacman -Rdd yaourt

2. Get the latest bits from the AUR

        curl -O https://aur.archlinux.org/packages/pa/package-query/package-query.tar.gz
        curl -O https://aur.archlinux.org/packages/ya/yaourt/yaourt.tar.gz

3. Explode the tarball and go into the each folder

        tar -zxf package-query.tar.gz
        tar -zxf yaourt.tar.gz
        cd package-query

4. Compile

        makepkg -s

5. Install

        sudo pacman -U package-query-1.5-2-x86_64.pkg.tar.gz

Make sure to do steps 4 and 5 for the `yaourt` package also. And this is
it... All should be in order now.
