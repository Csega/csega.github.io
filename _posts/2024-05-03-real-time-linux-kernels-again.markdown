---
layout: post
title:  "Real-time Linux kernels - again"
date:   2024-05-03 11:20:30 +0200
categories: mypost
---

## Introduction

Hi Everyone! Long time no see! :) But now let me tell you a bit about what I've learned about real-time and real-time Linux kernels in specific.

## What is real-time (and what is not)?

Often real-time is associated with something *instantenous* or *immediate*, like real-time video or real-time tracking. However, real-time is nothing like that. Real-time is about determinism. A real-time system give you guarantees, that your tasks run deterministically, reproducible. Often, a real-time system runs slower, than a non real-time. However, a real-time system often runs faster, than the worst-case-scenario on a non real-time system. Phew! Hard stuff. Now that I mention it...

Sometimes comes up two kinds of real-time systems.

1. Hard real-time: could be the mathematically provable type of real-time code OR could be the case, when if the answer is delayed outside of our "tick" range (unbounded latency or outlier), then it is considered a failure. "Hard real-time is really the quality of code, not the design of code." (Steven Rostedt - [Kernel Recipes 2016][who-needs-real-time]). Or let's just see another definition: "In a real-time system the correctness of a computation depends not only upon the logical correctness of the result but upon the **time** at which it is produced. If the timing constraints of the system are not met, system **failure** is said to have occured." or "Realtime in operating systems: the ability of the operating system to provide a required level of service in a **bounded** response time." [An introduction to real-time Linux][ubuntu-intro-to-real-time-linux]

2. Soft real-time: if it is a bit degraded (one or just a few results are dropped or have a too large delay), we don't care that much (e.g. frame drop at a video call or a video game). However, some say the soft real-time is meaningless because something is either deterministic or not, but cannot be both at the same time.

### Who uses real-time (typically)?

Real-time is typically used in places, where an outlier response is not accaptable. E.g. if you have an X-ray examination ahead, you don't want that to get it uncontrollably. Same with e.g. a pacemaker. You need it to intervene just at the right time. Not sooner and not later.

1. Healthcare:
    * Life-supporting equipment
    * Medical robots
    * Medical devices

2. Industrial:
    * Assembly line
    * Factory automation
    * Process control

3. Automotive:
    * Safety systems
    * Autonomous driving

4. Robotics:
    * Autonomous Mobile Robots
    * Manufacturing

5. Other:
    * [NASDAQ](https://www.nasdaq.com/)
    * Energy systems
    * Aviation (both civil and military applications)

## It is all about preemption (or is it?)

TBW (To Be Written...)

[rtai]: https://www.rtai.org
[xenomai]: https://www.xenomai.org
[who-needs-real-time]: https://www.youtube.com/watch?v=4UY7hQjEW34
[ubuntu-intro-to-real-time-linux]: https://www.youtube.com/watch?v=-wAo6bWh4jM