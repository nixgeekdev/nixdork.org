---
title: 'Get a prime number sequence using Java 8 Streams'
slug: 'prime-number-sequence-using-java-streams'
date: 2016-04-01T07:29:18-08:00
tags: ['java']
---

With a spirit of expanding on my previous post about
[checking numbers for primality](/posts/check-number-primality-using-java-streams), here's a
quick way to generate a sequence of prime numbers using streams:

    public static LongStream primeSequence(long max) {
        return LongStream.iterate(2, i -> i + 1)
                .filter(x -> isPrime(x))
                .limit(max);
    }

The above returns a `LongStream` of prime numbers up to a specified `max`
value. It uses my previous prime checker function `isPrime`.
