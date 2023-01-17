---
title: 'Grepping Multiple Files Recursively'
slug: 'grepping-multiple-files-recursively'
date: 2013-04-17T20:26:25-08:00
tags: ['bash', 'linux', 'quick hacks']
---

Recently I was faced with the task of looking for the occurences of a variable
name in all files in a directory recursively. Here is a quick bash incantation
that accomplishes that:

    $ find . -type f -print0 | xargs -0 grep -l variable-name

The above can be understood better if we break it down at the pipe character. To
the left of the pipe we use the `find` command to generate a list of file names
recursively starting at the current directory. We use `find` with the `-print0`
action because we are passing the output to another program via a pipe and this
way the list of file names come out delimited by a null character. Next, we feed
the output of `find` to the input of `xargs` which will split the long list of
file names into sublists and calls `grep` once for every sublist. The `grep`
command then filters the list of file names and returns only the ones that
contain the `variable-name` string in them.

Pretty cool, eh?
