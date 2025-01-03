---
layout: post
title:  My journey into graduate school
date:   2025-01-03 16:40:16
description: 
tags: grad-school
categories: posts
---

Applying to graduate school is a journey. If you are on this path, it can be an exciting experience, and I wish you the best of luck with your applications!

Below are some excellent resources about applying to graduate school and what life as a graduate student might look like:

<ul>
    <li><a href="https://www.cs.cmu.edu/~harchol/gradschooltalk.pdf">Applying to Ph.D. Programs in Computer Science</a></li>
    <li><a href="https://cseweb.ucsd.edu/~wgg/grad-school.html">Applying to Graduate School in Computer Science (A U.S. Perspective)</a></li>
    <li><a href="https://shuyuej.com/resources/The-PhD-Grind.pdf">THE PH.D. GRIND: A Ph.D. Student Memoir</a></li>
</ul>

I decided to pursue a PhD because I wanted to deeply understand parallelism and why parallel programs are written the way they are. While working at NCRA on developing a real-time transient detection pipeline, I struggled to write CUDA code. As a physics undergraduate with no background in computer architecture, I had taught myself C, C++, Python, the works. I had written extensive single threaded code and it never made me think about the hardware I ran my program on. 

Writing CUDA code was a completely different experience. A simple change in the algorithm could result in a performance difference of ±10x. It was no joke—and extremely frustrating. I had to learn computer architecture on the job. Starting with almost no knowledge of what a GPU was, I gradually worked my way up to understanding threads, warps, caches, SMs, and pipelines during my internship. It was a steep learning curve, but I fell in love with it. Although I started the transient pipeline project with the intention of using computer science to solve interesting physics problems, I ended up spending all my time diving into computer architecture.

While I loved the work and saw parallelism as an incredibly efficient tool to solve complex problems quickly, I noticed a clear challenge in its implementation. Writing efficient parallel code often required one to be a computer architect—or at least to have a solid understanding of the underlying architecture. Adding more threads to enable parallelism, especially in GPUs (which operate with thousands of threads), made the problem exponentially more complicated. Developers needed to think about thread interactions: Should we use locks, and if so, when? Should we synchronize threads, and if so, at what level? What about memory management? And so on.

By the end of the internship, I knew I wanted to be a computer architect. I also realized I wanted to support other physicists so they could focus on their research without being bothered by the details of the hardware running their programs. With that in mind, I decided to pursue a PhD.

Coming from a three-year undergraduate program, my options for schools were limited. After researching, I found the perfect fit with Professor David August at Princeton. David’s interests in parallelism, CPUs, and GPUs aligned with mine. He was open to fundamentally questioning why CPUs and GPUs are architected the way they are—often more for historical reasons than fundamental ones. Once a design becomes popular, it is more efficient to fine-tune it than to fundamentally change it. This is how we ended up with CPUs and later GPUs. David was very enthusiastic about the problems I wanted to solve, and that excitement has stayed consistent throughout my PhD.

During my PhD, I worked on bridging the gap between CPUs and GPUs. I developed a profiler for GPUs to identify second-level stalls (which failed), implemented efficient out-of-order execution on GPUs (see <a href="https://liberty.cs.princeton.edu/Publications/isca24_ghost.pdf">GhOST</a>), and improved simultaneous multithreading on CPUs. All of this was possible because I had an advisor who gave me the freedom to pursue the work I wanted to do.


<strong>Choosing an Advisor:</strong> Your advisor is your source of funding, research support, and often your first point of contact as an international student. A good advisor can help shape your research philosophy, guide you toward important and interesting problems, introduce you to valuable professional contacts, and much more. When choosing an advisor, consider what matters most to you: How well do your interests align? What do their graduate students think of them? Most importantly, pay attention to the <strong>VIBES</strong>.



