---
layout: post
title: I am interning at Microsoft Research!
date: 2022-05-05 16:11:00-0400
inline: false
related_posts: false
---

I will be interning at Microsoft Research this summer working with Azure! I will be working on memory diagreggation at Azure to improve the hardware utilization to make datacenters greener :smile:

***


> Green computing supports sustainability with only one motto- ” Reduce, Reuse & Recycle“.

Data Centers use a lot of power (both static and dynamic) as they need to keep resources on stand-by to accomodate any incoming VMs, as you certainly dont want paying users to be stalling. The number of running processes is variable and so are their memory and compute requirements. Traditionally compute and memory are strongly coupled on cores. A process might be using all the memory resources of a core while compute resources have zero utilization. To reduce this problem we disaggrgated compute and memory, creating "memory pools" to allocate memory from to processes which are not bound by memory access latency and will not be equiring the compute resources from the additional cores given to them.



***



