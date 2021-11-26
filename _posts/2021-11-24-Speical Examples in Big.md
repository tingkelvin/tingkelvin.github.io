---
layout: post
title: Some special example in Big O
date: 2021-11-05 20:21:00-2100
description: Some tricky question to test your understanding of big O.

---
Here are some tricky questions about big O. 

Given the following codes, what is its complexity?

**Example 1 - Recursive Runtimes**

```java
int f(n){
	if (i <= 1){
    return 1;
  }
	return f(n-1) + f(n-1);
}
```
<details>
  <summary>Answer</summary>
  Answer     is $$O(2^{N})$$
  If N = 4, f(4) will produce 2 f(3). Then, each f(3) will produce 2 f(2). Since there are 2 f(3), there will 4 f(2). Each f(2) will produce 2 f(1). Since there are 4 f(2), there will be 8 f(1). There are $$2^{0} + 2^{1} + 2^{2} ... 2^{N}$$ recursive calls which is equal to $$2^{N} - 1$$.
</details>


**Example 2 - Pairs**

```java
void printPairs(int[] array) {
    for (int i= 0; i < array.length; i++) {
        for (int j= i + 1; j < array.length; j++) {
            System.out.println(array[i])
        }
    }
}
```
<details>
  <summary>Answer</summary>
  Answer is $$O(2^{N})$$ 
  How many loops?

  $$(N-1)+(N-2)+...+2+1$$
  $$= 1+2+3+...+(N-1)$$
  $$=\frac{N(N-1)}{N}$$
  $$=O(N^{2})$$

  Or,
  Loop (i,j) produced when N = 5:
  (0,1)(0,2)(0,3)(0,4)
       (1,2)(1,3)(1,4)
            (2,3)(2,4)
                 (3,4)
  Looks like a (N,N) matrix but divided by 2, total amount of loops approximately is
  $$\frac{N*N}{2}$$
  $$ = O(N^{2})$$
</details>


**Example 3 - Unordered Pairs**

```java
void printUnorderedPairs(int[] arrayA, int][ arrayB) {
    for (inti= 0; i < arrayA.length; i++) {
        for (int j = 0; j < arrayB.length; j++) {
            for (int k= 0; k < 100000; k++) {
                    System.out.println(arrayA[i] + "," + arrayB[j]);
            }
        }
    }
}
```

<details>
  <summary>Answer</summary>
  Answer is 
  $$O(100000MN})$$
  $$O(MN})$$
</details>


**Example 3 - Unordered Pairs**

This one is tricky!

Suppose we had an algorithm that took in an array of N strings, the length of each string is s.
Sorted each string, and then sorted the full array. What would the runtime be? Asuming sorting took O(x log x). 

<details>
  <summary>Answer</summary>
  Sorting a string takes s log s and there N strings.
  Soring  strings takes O(N * s log s).
  Now sorting the array! This is the tricky part.
  The way we sort string in a array is to compare each character in string.
  There are s characters, each time takes O(s).
  There N log N comparsion, therefore this will take O(s*N log N) time

  Answer is O(N * s log s) + O(s * N log N) = O(N * s(log N + log s)).
</details>


**Example 4 - Prime Number**

```
boolean isPrime(int n) {
    for (int x = 2; x * x <= n; x++) {
        if (n % X == 0) {
            return false;
        }
    return true;
} 
```

<details>
  <summary>Answer</summary>
  When this loop stop?
  x will mutiply itself until it is smaller or equal to n
  We can write this,
  $$ x * x = n $$
  $$ x ^{2} = n $$
  When,
  $$ x = \sqrt{n}$$
  The loop exists, so the complexity is
  $$ = O (\sqrt{n})$$

  If n is 100,
  x will go though,

  2*2->4*4->5*5->6*6->7*7->8*8->9*9->10*10

  This is when the loops tops because 10*10 <= 100. 
</details>

**Example 5 - n Factorial**

```
boolean isPrime(int n) {
    for (int x = 2; x * x <= n; x++) {
        if (n % X == 0) {
            return false;
        }
    return true;
} 
```

<details>
  <summary>Answer</summary>
  When this loop stop?
  x will mutiply itself until it is smaller or equal to n
  We can write this,
  $$ x * x = n $$
  $$ x ^{2} = n $$
  When,
  $$ x = \sqrt{n}$$
  The loop exists, so the complexity is
  $$ = O (\sqrt{n})$$

  If n is 100,
  x will go though,

  2*2->4*4->5*5->6*6->7*7->8*8->9*9->10*10

  This is when the loops stops because 10*10 <= 100. 
</details>

**Example 7 - Binary Search Tree**

```
int sum(Node node){
    if (node == null){
    	return 0
    }
    return sum(node.left) + node.value + sum(node.right);
}
```

<details>
  <summary>Answer</summary>
  First glance at this question, you might think binary tree means O(Log N)!
  But if you think carefully, this code travrses all nodes which means its complexity is O(N).
  
  Mathematically, we said that in first examples, each recusive calls will produce 2 recursive calls and there are $$2^{0} + 2^{1} + 2^{2} ... 2^{N}$$ recursive calls which is equal to $$2^{depth} - 1$$. The depth is $$Log N$$, where N is the amount of nodes. Put it together we have,
  $$Let P = 2^{log N}$$
  $$ log P = log 2^{log N}$$
  $$ log P = log N$$
  $$ p = N $$
  $$ 2^{log N} = N $$
 which is also O(N).
</details>
