---
layout: post
title: SHADOW has been accepted to MICRO'25!
date: 2025-07-14 16:11:00-0400
inline: false
related_posts: false
---

Our work [SHADOW: Simultaneous Multi-Threading Architecture with Asymmetric Threads]({{ "/assets/pdf/SHADOW_MICRO.pdf" | relative_url }})  has been accepted to MICRO'25!

***

Many important applications exhibit shifting demands between instruction-level parallelism (ILP) and thread-level parallelism (TLP) due to irregular sparsity and unpredictable memory access patterns. Conventional CPUs optimize for one but fail to balance both, leading to underutilized execution resources and performance bottlenecks. Addressing this challenge requires an architecture that can seamlessly adapt to workload variations while maintaining efficiency.

This paper presents SHADOW, the first asymmetric SMT core that dynamically balances ILP and TLP by executing out-of-order (OoO) and in-order (InO) threads simultaneously on the same core. SHADOW maximizes CPU utilization by leveraging deep ILP in the OoO thread and high TLP in lightweight InO threads. It is runtime-configurable, allowing applications to optimize the mix of OoO and InO execution. Evaluated on nine diverse benchmarks, SHADOW achieves up to 3.16x speedup and 1.33x average improvement over an OoO CPU, with just 1% area and power overhead. By dynamically adapting to workload characteristics, SHADOW outperforms conventional architectures, efficiently accelerating memory-bound workloads without compromising compute-bound performance.

***




