---
title: 'Guarantees'
slug: 'guarantees'
date: 2008-07-26T10:45:00-08:00
tags: ['programming']
---

Suppose you have a function in C# with the following signature:

    int f(int i) { ... }

Given this signature, can you guarantee to me what the return type of the
function is? Seems like a no brainer, right? Not so fast... examine this code
for a second:

    int f(int i) { return i / 0; }

In this instance, function `f` will not return an `int` at all, but it will
rather raise an exception. I just wanted to illustrate the point that even in a
statically typed language like C#, there is no guarantee that you will get back
exactly what the language is advertising to you.
