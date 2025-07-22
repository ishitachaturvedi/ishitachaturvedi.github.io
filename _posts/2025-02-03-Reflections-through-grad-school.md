---
layout: post
title:  Finding Light in the SHADOW
date:   2025-07-21 16:40:16
description: 
tags: grad-school
categories: posts
---

 Every published paper has a story. In research, we often sell our work as a neat, straight line. To readers, it might seem that the problem was obvious, the solution insightful, the implementation straightforward, and the results amazing—leading effortlessly to a great paper. My experience (and perhaps yours, too) couldn’t be farther from this idealized image.

The purpose of this blog post is to give a behind-the-scenes look at what it took to publish our MICRO'25 paper, [SHADOW: Simultaneous Multi-Threading Architecture with Asymmetric Threads]({{ '/assets/pdf/SHADOW_MICRO.pdf' | relative_url }}). The journey to publication was a challenging yet deeply rewarding experience.

<h2> Getting an idea </h2>

[GhOST](https://liberty.princeton.edu/Publications/isca24_ghost.pdf) took three additional paper cycles to publish after completion. And I realized I'd saturated my curiosity about GPU microarchitecture. I had explored GPUs deeply, grasped their microarchitecture, programming model, and memory behavior, and could clearly visualize their execution flow. It was time for a new direction.

There was just one issue, I had no idea what problem to tackle next.


So, I took the only rational step: at ASPLOS'23 and ISCA'23, I cornered every faculty member I could find and picked their brains. They were incredibly generous with their time, patient with my wild ideas, and straightforward in their feedback. They suggested exploring sparsity on GPUs (but I wanted a GPU break), edge computing (no suitable simulator at the time, and I didn't want to build one from scratch), or building accelerators (which didn’t excite me back then).


The clear next step was CPUs. An area that always interested me was parallelism, and research on SMT in CPUs seemed to have been going cold. We have been moving towards many cores and more diversity. But a clear lesson from GhOST was that there is performance on the table from existing architectures. Going deep (with OoO) on a wide machine has its benefits, why dont we go wide (more SMT) on deep machines (OoO). Well, okay, but how. That is where I hit another stone wall. We dont scale CPU threads not because ot is not useful, but because of area and power. OoO takes up space. But, what if we scale this CPU with a mix of OoO and InO threads? This creates a <b>truly assymetric-SMT CPU core</b>. That sounds really interesting! Mix up InO theads and OoO threads on one core sharing the same back-end and front-end, and let it go (and pray for the best)!


CPUs emerged as a natural next step. I'd always found parallelism fascinating, and research on SMT for CPUs seemed to have grown stagnant. The industry was trending towards many-core systems and diversity. However, GhOST had clearly shown me there was still untapped performance in existing architectures. I thought: if going deep (with OoO) on wide (many-thread) machines has benefits, why not go wide (more SMT threads) on deep (OoO) machines? But how exactly?

That's when I hit another wall: scaling CPU threads isn’t limited by usefulness, but by area and power—OoO execution is resource-intensive. What if we combined OoO and InO threads in the same core, creating a truly asymmetric SMT CPU? The idea of mixing thread types, which run simulanesouly, sharing front-end and back-end resources, seemed genuinely exciting (and mildly terrifying). Now the real question emerged: how on earth do I build this?


<h2> Implementing the idea </h2>

To put it bluntly, implementing SHADOW was painful. Gem5 emerged as my simulator of choice due to its execute-on-execute design, allowing at least partial verification of massive architectural changes. There was one catch: the SMT implementation in Gem5 was broken. Now I had to fix SMT first, integrate InO threads alongside OoO, ensure they properly shared the pipeline, correctly disable register renaming, and verify synchronization.


Debugging this infrastructure drained every ounce of energy and patience I had, taking a full year. Only after this was complete could my actual research begin. And just when I thought the hardest part was over, another big question hit: <b>Which applications would actually benefit?</b>


<h2> Finding the workloads <h/2>

Having built the infrastructure, the idea needed fleshing out. Should each thread run a single-threaded application? Should we prioritize OoO threads for foreground processes, relegating InO threads to background tasks? How would we ensure QoS? Or maybe all threads should run the same multi-threaded process? After significant deliberation, we decided the last approach was most practical for testing SHADOW. But then, another question appeared: which applications?

I strongly believe processors should benefit general-purpose workloads. CPUs need to perform well broadly, even if they specialize occasionally. Moreover, my system only supported pthreads, and frankly, I was too burned out to implement OpenMP support. I ran several pthread benchmarks, and...we saw zero performance gain. In fact, performance degraded.

I had invested more than a year and a half and had nothing positive to show. It felt awful. Now what?

<h2> Study the stalls </h2>

Digging deeper into the system I’d barely gotten working, I discovered optimization opportunities hidden in the interactions between OoO and InO threads—essentially, performance bugs. Fixing these bugs finally yielded measurable, significant performance improvements.


<h2> Understand the system </h2>

After nearly two years of intense building, testing, debugging, and hoping for the best, I could finally start understanding SHADOW’s dynamics. Now we had to answer the fun questions: What truly drives SHADOW’s performance gains? Which applications benefit most, and under what thread configurations? How should threads distribute workloads (static or dynamic)? Is SHADOW configurable per application?—and if so, how? all of which we answered.


SHADOW was a passion project born from genuine curiosity. I sincerely wanted to understand the impact of asymmetric SMT. Ultimately, we uncovered intriguing insights about parallelism, thread behavior, and CPU architecture. It was rejected from ISCA'25, but it is a relief that SHADOW is out in MICRO'25. It will read like everything was obvious, but now you know that was far from the truth.

<h2>Final reflections</h2>
If your research feels chaotic, uncertain, or exhausting, remember you're not alone. Behind every polished paper is a messy journey filled with setbacks, frustrations, and doubts. Sharing this story openly, I hope it resonates with you, reminding you that genuine, worthwhile work rarely comes easy—and that's perfectly okay.

