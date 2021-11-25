---
layout: post
title: Network Flow in Graph Algorithm
date: 2021-11-25 20:21:00-2100
description: What is Network Flow?

---

### Network Flow

Network flow is important in expressing a wide variety of problems eg, load balancing, operating research ..etc. As a result, developing a good understanding of algorithms that solves network flow will get you to solve many other problems as well.

**The Netowrk Flow Problem**

First we need to define what is network flow problem? 

We are given a directed graph, $$G = (V, E)$$ with $$n$$ vertices, $$m$$ edges, a "source" $$n$$ vertices, and a "sink" vertices $$t$$. Moreover, each edge $$e$$ is associated with a non-negative *capacity* $$c(e)$$. For example, consider the graph,

