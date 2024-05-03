---
layout: post
title: GhOST has been accepted to ISCA'24!
date: 2024-05-03 16:11:00-0400
inline: false
related_posts: false
---

Our work [GhOST: a GPU Out-of-Order Scheduling Technique for Stall Reduction](https://liberty.princeton.edu/Publications/isca24_ghost.pdf)  has been accepted to ISCA'24!

***

Graphics Processing Units (GPUs) use massive multi-threading coupled with static scheduling to hide instruction latencies. Despite this, memory instructions pose a challenge as their latencies vary throughout the application's execution, leading to stalls. Out-of-order (OoO) execution has been shown to effectively mitigate these types of stalls. However, prior OoO proposals involve costly techniques such as reordering loads and stores, register renaming, or two-phase execution, amplifying implementation overhead and consequently creating a substantial barrier to adoption in GPUs. This paper introduces GhOST, a minimal yet effective OoO technique for GPUs. Without expensive components, GhOST can manifest a substantial portion of the instruction reorderings found in an idealized OoO GPU. GhOST leverages the decode stage's existing pool of decoded instructions and the existing issue stage's information about instructions in the pipeline to select instructions for OoO execution with little additional hardware.
A comprehensive evaluation of GhOST and the prior state-of-the-art OoO technique across a range of diverse GPU benchmarks yields two surprising insights: 
(1) Prior works utilized Nvidia's intermediate representation PTX for evaluation; however, the optimized static instruction scheduling of the final binary form negates many purported improvements from OoO execution; and (2) The prior state-of-the-art OoO technique results in an average slowdown across this set of benchmarks.
In contrast, GhOST achieves a 36% maximum and 6.9% geometric mean speedup on GPU binaries with only a 0.007% area increase, surpassing previous techniques without slowing down any of the measured benchmarks.


***



