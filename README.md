# Motivation

- online contests
- school contests
- friends (inter-school competitions)

# Method

- Think more & Learn more

# Materials

## Online judges
https://judge.hkoi.org/ \
https://codeforces.com/ @QwertyPi \
https://atcoder.jp/ @QwertyPi


## Online Guides
https://usaco.guide/ (guide in OI) \
https://stackoverflow.com/ (debug) \
https://www.geeksforgeeks.org/ (simple knowledges)

## Fun
https://www.codingame.com/home

## References
https://hkoi.org/zh/useful-links/ \
https://en.cppreference.com/w/ \
https://www.cplusplus.com/reference/

# Modular Arithmetic

## Introduction

In competitive programming, you often see wordings in combinatorics or probabilistic tasks like “output the answer modulo 10^9+7”, or when the answer is a fraction pq, “output the value p/q modulo 10^9+7”. We all know that modulo(%) just means remainder: But how can we find the value of pq?

## Basics in modular arithmetic

Imagine there is a clock, while you keep rotating it, clockwise and anticlockwise. Indeed, we can treat clockwise as addition, and anticlockwise as subtraction. Consider the following situation:

The clock is at 8 o'clock. You rotate it clockwise 5 hours, the resulting clock is at 1 o’clock direction: 8 + 5 = 13. However, we all know that 13 o’clock doesn’t exist: and it is exactly 1 o’clock.

So, is 13 o’clock equivalent to 1 o’clock if we consider the clock, in which 12 hours is a cycle? It is trivial to see that it is true for addition and subtraction. Does it also hold for multiplication?

Indeed, this is undoubtedly true: you may verify with several examples. Therefore, by considering these equivalence relationships, we define a ≡ b (mod m): a and b are equivalent under modulo m. Or it simply means that when a and b are divided by m, their remainder are the same. We can deduce some crucial identities from it:

a (mod m) + b (mod m) mod m ≡ a + b (mod m) \
a (mod m) - b (mod m) mod m ≡ a - b (mod m) \
a (mod m)  b (mod m) mod m ≡ ab (mod m)

Which exactly means, where two numbers are equivalent under modulo m, they can be replaced by each other under addition, subtraction and multiplication!

## Raising High Power of Number

Sometimes you are required to raise a number to a really big integer modulo m, for example ~10^8. How can we do it efficiently? Binary exponential is a solution. We can recursively solve that for lower power, and inductively find the answer. Indeed a^{2k} = (a^k)^2 and a^{2k+1} = a(a^k)^2, and these two relationships are enough to find the power of numbers (if one is familiar with recursion).

Suppose we have a chain. We can split it into almost half, and we can observe that the two parts are almost the same: therefore we need not compute the same thing repeatedly (this technique is also called divide-and-conquer). Time complexity O(log n) for computing a^n.

## Modular Division
You may ask, how about division? How can we divide a number by another in modulo? How can we solve bk ≡ a(mod m) for k? A natural idea is, maybe there exist an inverse b^{-1} for each number b such that bb^{-1} ≡ 1 (mod m). Then, multiply both sides by b-1, we have  k ≡ ab^{-1}(mod m). Indeed, such inverse exists and is unique for every integer b coprime to m, i.e. gcd(b, m) = 1, but the proof is beyond the scope of this text. (For interested readers, one can search for Bezout’s lemma and the uniqueness of modular inverse.) For now,  a(φ(m)-1) is the inverse of a, where φ(n) is the Euler totient function, which counts the number of coprime number to n, since a^(φ(m)) ≡ 1(mod m) by Euler’s theorem. Normally, if m is prime, φ(m) = m - 1. Therefore for usual prime p (e.g. 10^9+7, 998244353), a^{p-2} is exactly the modular inverse of a.

You may also calculate Combination & Permutation via this way, with stored factorials modulo m, and prefix-sum-style technique.
