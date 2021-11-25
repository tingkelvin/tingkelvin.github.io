---
layout: post
title: Amortized Analysis in Dynamic Arrays
date: 2021-11-05 20:21:00-2100
description: What is the complexity of inserting a new element in a dynamic array?

---
Here is some tricky questions about big O. 

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
  Ans is $2^{N}$
  If N = 4, f(4) will produce 2 f(3). Then, each f(3) will produce 2 f(2). Since there are 2 f(3), there will 4 f(2). Each f(2) will produce 2 f(1). Since there are 4 f(2), there will be 8 f(1). There are $$2^{0} + 2^{1} + 2^{2} ... 2^{N}$$ recursive calls which is equal to $$2^{N} - 1$$.
</details>
