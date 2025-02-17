---
layout: post
title: Amortized Analysis in Dynamic Arrays
description: What is the complexity of inserting a new element in a dynamic array?

---
A dynamically resizing array, allows you to have benefits of an array while offering flexibility in size. As a result, you won't run out of space since the capacity of the array will grow as you insert elements. 

So how often should this resizing occurs? And how do you describe the runtime of insertion? This is a tricky question.

When the array is full, we create a new array with double the capacity of the previous array.

Here is a an example of inserting 16 elements (from 1 to 16).

**An example of Array resizing**

| element to insert | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | 12   | 13   | 14   | 15   | 16   |
| ----------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| size of the array | 1    | 2    | 4    | 4    | 8    | 8    | 8    | 8    | 16   | 16   | 16   | 16   | 16   | 16   | 16   | 16   |
| cost of resize    | 1    | 2    | 0    | 4    | 0    | 0    | 0    | 8    | 0    | 0    | 0    | 0    | 0    | 0    | 0    |16    |
| cost of insert    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    | 1    |
{:class="table table-bordered"}

We can see the size of array is double when the array is full (1→2→4→8→16). The process of creating of new array invokes 2 costs: cost of copy the previous elements and cost of inserting new elements. For example, when try to insert element 2, the array is full so we need to create a new with the size of 2 (previous size is 1), first we copy the previous elements, there is only one element (in this case is element 1), we copy the previous element (1 cost) and insert element 2 (1 cost). So the total cost is 2.

**Total Cost**

*Cost of inserting new element*s

If,

$$N = \ total\ number\ of\ elements\  to\  insert$$

There is alway N costs, because each element will cost 1 to insert. For example, if there is 16 elements, there are 16 insertions, we will have a cost of 16.

\begin{equation}
\label{eq:1}
total\ cost\ of\ insertion = N
\end{equation}


*Cost of resizes*

First, we need to ask ourself how many times that resize occurs?

From our previous example,

$$total\ cost\ of\ resizing = (1 + 2 + 4 + 8 + 16)$$

There are 5 terms as resize happens 5 times. 

\begin{equation}
\label{eq:2}
number\ of\ resize = log\ N + 1
\end{equation}
For example, we have 16 elements to insert, the number of time to resize is $$log\ 16 + 1$$, which is 5.
Everytime we resize, we need to copy all the previous elements. For example, the first resize we need to copy 1 element, second time we need to 2 elements, third time we need to copy 4 elements ...etc.

So how many times of copying occurs? We have doubled 5 times, everytime we double the size, in other way we can write this to,

$$(1 + 2 + 4 + 8 + 16) = 2^{0} + 2^{1} + 2^{2} + 2^{3} + 2^{4}$$

which is equal to,

$$(1 + 2 + 4 + 8 + 16) = 2^{5}$$

**HOLD ON**. But if you add up, 1+2+4+8+16, we will have 31. Why? because the first time we resize we only need to copy 1 element. Subract 1, 

$$(1 + 2 + 4 + 8 + 16) = 2^{5} -1 $$

Mathematically, 

$$ total\ resize\ cost = 2^{number\ of\ reszie} - 1 $$

and from \eqref{eq:2}, we can rewrite as, 
\begin{equation}
\label{eq:3}
total\ resize\ cost = 2^{log N + 1} - 1
\end{equation}

**Amortized Analysis**

Amortized Analysis, is the study of the overall performance. It allows us to describe that, worst case happens every once in a while. But once it happens, it won't happen again for so long that the cost is "amortized". 

Combine \eqref{eq:1} and \eqref{eq:3},

$$ total\ cost\ =\ total\ number\ of\ insert + total\ resize\ cost $$

$$= N + 2^{log N + 1} -1 $$

Since,

$$ 2^{log N + 1} - 1 \leq 2N $$

$$2N$$  is the upper bound of $$ 2^{log N + 1} - 1$$ since $$2^{log N + 1}$$ cannot grow larger than $$2N$$.

We can simplify as,

$$ total\ cost\ = N + 2N = 3N$$

Finally, we divide total cost by the number of elements, we get

$$amortized\ cost = \frac{3N}{N} = 3 $$

So the complexity of inserting an element is constant,

$$complexity\ of\ insertion = O(1) $$

**Conclusion** 

When we resize the arary, we double the capacity of the previous array. The complexity of insertion overall is constant.
