---
layout: post
title: Special Examples in Big O
date: 2021-11-24 20:21:00-2100
description: We discuss some special examples in Big O.

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
  Ans is $$2^{N}$$
  If N = 4, there will be 4 recusrive calls, first call will produce 1 call f(4). Second call will produce 2 recursive calls f(3). Each f(3) call will produce 2 calls. There are $$2^{0} + 2^{1} + 2^{2} ... 2^{N}$$
</details>

