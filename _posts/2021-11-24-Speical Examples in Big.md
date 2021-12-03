---
layout: post
title: Some special example in Big O
description: Some tricky questions to test your understanding of big O.

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

**Example 9 - All Fibonacci**

```java
void allFib(int n) {
    for (int i= 0; i < n; i++) {
        System.out.println(i + ": "+ fib(i));
    }
}

int fib(int n) {
    if (n <= 0) return 0;
    else if (n == 1) return 1;
    return fib(n - 1) + fib(n - 2);
}
```
<details>
  <summary>Answer</summary>
    $$2^{n} + 2^{n-1} + 2^{n-2} + ... 2^{1}$$
    $$ = O(2^{n}) $$
</details>

**Example 10 - Permutations of a String**

Another very tricky question to tease your brain!

```java
void permutations(String str){
  permutation(str, "");
}
void permutations(String str, String prefix){
  if (str.length() == 0){
    System.out.println(prefix);
  } else {
    for (int = 0; i < str.length(); i++){
      String rem = str.substring(0,i) + str.substring(i + 1);
      permutation(rem, prefix + str.charAt(i));
    }
  }
}
```
<details>
  <summary>Answer</summary>
    How many base cases are there?
    
    If the length of string is N.
    
    There are N combination N*(N-1)*(N-2)...*1, that means we have N! base case
    
    How many calls before based case?
    
    Everytime you call permutation with N-1 call until you reach base case.
    
    Since there N charaters so at most N calls before the based case.
    
    We have N! base each case at most call N times.
    
    So complexity is O(N*N!).
    
    Each call take O(N) time to print and O(N)  to concatenate, which O(2N) = O(N)
    
    Total complexity = O(N^2 * N!)
</details>

**Example 11 - Memorization of a String**
```java
void allFib(int n) {
    int[] memo = new int[n + 1];
    for(inti= 0;i< n;i++){
        System.out.println(i + ": "+ fib(i, memo));
    }
}
int fib(int n, int[] memo) {
    if (n =< 0) return 0;
    else if (n== 1) return 1;
    else if (memo[n] > 0) return memo[n];
    memo[n]= fib(n - 1, memo)+ fib(n - 2, memo);
    return memo[n];
}
```
<details>
  <summary>Answer</summary>
    Any previous number will be remembered in the array.
    So compexity is O(N)
</details>

**Example 12 - Power of 2**
```java
int powers0f2(int n) {
    if (n < 1) {
        return 0;
    } else if (n == 1) {
        System.out.println(l);
        return 1;
    } else {
        int prev = powers0f2(n / 2); int curr = prev * 2; System.out.println(curr); return curr;
    }   
}
```
<details>
  <summary>Answer</summary>
    The complexity is
    $$ log N $$
    The recusrive call divided n/2 in every calls, how many calls until base case which is 0?
</details>

**Example 13 - sum of digits**
```java
int sumDigits(int n) {
    int sum = 0;
    while (n > 0) {
        sum += n % 10;
        n /= 10; return sum;
    }
    return sum;
}
```
<details>
  <summary>Answer</summary>
    The complexity is equal to numbers of digits, lets its d.
    
    What is the largest of value N?
    
    If d is 4, then the largest value is 10000.
    The largest is equal to,
    $$ N = 10 ^ {d} $$
    $$ log N = log 10 ^ {d} $$
    $$ d = log N $$
    
    Hence, the complexity is O(log N).
    
</details>

**Example 14 - sum of digits**
```java
int numChars = 26;
void printSortedStrings(int remaining) {
    printSortedStrings(remaining, "");
}

void printSortedStrings(int remaining, String prefix) 
    { if (remaining== 0) {
        if (isinOrder(prefix)) {
        System.out.println(prefix);
    } else {
        for (int i= 0; i < numchars; i++) {
            char c = ithletter(i);
            printSortedStrings(remaining - 1, prefix + c); }
        }
    }
}

boolean isinOrder(String s) {
    for (int i= 1; i < s.length(); i++) {
        int prev ithLetter(s.charAt(i - 1));
        int curr = ithLetter(s.charAt(i));
        if (prev > curr) {
            return false;
        } 
    }
    return true;
}

char ithLetter(int i) {
    return (char) (((int) 'a') + i); 
}
```
<details>
  <summary>Answer</summary>
    Lets r is the remaining (the length of string).
    
    The loop in printSortedStrings loop though all the numChars, lets say is c.
    
    If r = 4, then there will be 4 printSortedStrings, because the parameters of printSortedStrings is (r-1) until base case which is when r = 0
    
    So the complexity of generating string is,
    $$O(c^{r})$$
    And, we check if the string is sorted, the way we check is to loop though all the string which takes O(r), we did that to every strings.
    
    Total complexity,
    
    $$O(rc^{r})$$
    
</details>
