---
layout: post
title: Efficient String Matching via Hashing
description: Compute String Matching in O(M+N) under Rabin-Karp Algorithm

---
**String Matching**

String matching is a common problem in natural language processing. Given a text $$t$$ we want to find if a string $$p$$ exists in the text.

The simpliest way to do this is to compare every characters in the text.

If the length of the text is $$n$$ and the length of the text is $$p$$.

Then the complexiry is $$ O(mn)$$ which is not efficient.

**Hashing**

Suppose we have the following weight for characters A to J,


| weight | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   |
| ----------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| character | A    | B    | C    | D    | E    | F    | G    | H    | I   | J   |
{:class="table table-bordered"}

We define the hash function as,

$$hash\ value\ for\ pattern(p) = \sum_{i=1}^{m}{weights[character]*len(weights)^{m-1}} mod\ 13$$

Let's have a concrete example,

The string $$p$$ is,

| m | 3 | 2 | 1 |
| - | - | - | - |
| character | C | D | D |
{:class="table table-bordered"}

Hash value for pattern("CDD") is, 

$$H('CDD')= ((3 * 10^{2}) + (4 * 10^{1}) + (4 * 10^{0}))mod 13 $$

$$ = 344\ mod\ 13$$

$$ = 6$$

**Rabin-Karp Algorithm**

If the hash value of the window is same as the hash value of our pattern, then we need to check every character to see if they match because in some cases, even the hash value is the same, the characters are not the same. 

Given the following text "ABCCDDAEFG",

| character | A    | B    | C    | C    | D    | D    | A    | E    | F   | G   |
{:class="table table-bordered"}

Hash value for the first window "ABC",

$$H('ABC')= ((1 * 10^{2}) + (2 * 10^{1}) + (3 * 10^{0}))\ mod\ 13 $$

$$=\ 123\ mod\ 13$$

$$=\ 6$$

In our example, the H("ABD") = H("CDD"), even though they are not the same.

Then we move to the second window which is 'BCC'. Here is the tricky part. If we want to calcaulte the hash value of second window "BCC", in stead of go though all the calculations. We can subtract it from the first window.

$$H('BCC') = (H(ABC) - H(A))*d + H(C)$$

By mutiplying $$H(ABC) - H(A))$$ by $$d$$, we shift the position of "BC" to left by one, then add the value of$$H(C)$$, we get the hash value of $$H('BCC')$$.

Full caluation,

$$= (((1 * 10^{2}) + (2 * 10^{1}) + (3 * 10^{0}) - (1 * 10^{2}))*10 + 3*10^{0}) mod\ 13$$

$$= 12$$

We have to compute the hash value each window, maximum of number of window is $$M$$, so the complexity of computing all windows is $$O(M)$$, if the hash values of the window and the pattern are the same we check if all the characters are the same which takes $$O(N)$$. 

We get no guarantee the algorithm runs in $$O(n+m)$$ time, because we may get unlucky and have the hash values regularly collide with spurious matches. Still, the odds are heavily in our favor.