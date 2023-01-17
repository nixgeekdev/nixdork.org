---
title: 'Check number primality using Java 8 Streams'
slug: 'check-number-primality-using-java-streams'
date: 2016-03-11T07:27:14-08:00
tags: ['java']
---

The canonical way to check if a number is prime in Java uses a loop. It looks
like this:

    public static boolean isPrime(long x) {
        for (long n = 2; n <= Math.sqrt(x); n++) {
            if (x % n == 0) {
                return false;
            }
        }
        return true;
    }

There is a more streamlined and efficient way of doing this using Streams. It
looks like this:

    public static boolean isPrime(long x) {
        return LongStream.rangeClosed(2, (long)(Math.sqrt(x)))
                .allMatch(n -> x % n != 0);
    }
