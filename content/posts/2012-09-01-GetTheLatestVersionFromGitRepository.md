---
title: 'Get the latest version from a Git repository'
slug: 'get-the-latest-version-from-git-repository'
date: 2012-09-01T21:29:46-08:00
tags: ['git', 'programming']
---

If you want to get the latest version from a Git repository and you don't care
about any local changes, do the following:

    git reset --hard HEAD
    git clean -f
    git pull

The above will copy the latest code from the repo and overwrite the local
copy.
