---
layout: post
title:  "Basic realtime Linux kernel knowledge"
date:   2021-09-01 11:06:39 +0200
categories: mypost
---

## Introduction

Hi Folks! It's been a while since I wrote a post here. But my blog is not dead, it was just sleeping for a while. :) Now, I'd like to get my first impressions on how to work with a realtime Linux kernel.

Many asks why do you need a realtime kernel at all? Well, in an average use case, you don't need a realtime kernel. For me, it is needed to realize realtime control of hardware. For this, I also need realtime processing of data.

One word about the spelling. You can find real time, real-time or realtime in the literature (or in the Internet) as well. I'll try to use realtime all the time in these (hopefully multiple) blog posts. If you have reasons to write it differently, please contact me, I'll correct.

## What is realtime?

There are some article about what is realtime in the computer system sense and what subcategories there are (hard or soft realtime etc.). I don't want to go into much details, but if you are interested, [Wikipedia][Wikipedia-realtime-computing] has a quite good summary. (If you can find better ones, then please send me and I'll put them here as well. ;) ) The main thing is, that in a realtime environment, you *have to* get answers from the system in a well-defined time-frame (one way or another).

I found a few description/tutorials about this topic, I share them here without any guarantee or quality check.

1. [Real-time Control Systems: A Tutorial][realtime-control-tutorial]
2. [Fundamentals of real-time processing in automation and control][fundamentals-of-realtime-processing]
3. [Real-time control systems: A Tutorial][realtime-control-tutorial2]
4. [Real-Time Systems][realtime-systems]
5. [Real-Time Control System and Real-Time Networks][realtime-control-and-network] (The full lecture is [here][module5-link].)

## Realtime testing

Here is a few sources I found about realtime testing.

1. [Real-Time Testing Best Practices][realtime-testing-best-practices]
2. [RT-Tests][rt-tests]
3. [Real-time Linux materials][realtime-linux]
4. [Real-time Linux Communications][realtime-linux-communications] (And the [paper on Arxiv][rtl-com-paper].)
5. [Red Hat Linux realtime kernel material][red-hat-realtime-material]

## Realtime kernels in Linux distributions

There are Linux distributions with realtime kernel packages (e.g. [Manjaro Linux][Manjaro-realtime-kernel] or [CentOS 7][centos-7-realtime-kernel] or [Rocky Linux 8][rocky-linux-8-realtime-kernel]). Interestingly enough, Ubuntu does not provide (to my knowledge) an out-of-the-box realtime kernel by default. You have to patch your desired kernel to show realtime capabilities. So in the next section I'll look into that matter.

The other possibility (which I will describe in details in the overnext section) is to use low-latency kernel. This is not exactly realtime, but can provide significantly lower response time in the kernel (0.1 ms according to [this source][ubuntustudio-realtime-kernel]. It also mentions a few security considerations for a realtime kernel.).

## How to patch Ubuntu kernel to have realtime properties

According to [this][Stackoverflow-ubuntu-realtime-kernel-patch] Stackoverflow post, it can be done without much pain. However, until I try it myself, I just link the documentation here. When I'll have some own experience with this, I'll go into the details.

## How to install Ubuntu low-latency kernel

This is much easier than the realtime kernel patching, since there is a package ready for install. I use Ubuntu 20.04 (focal). The package can be found in the package index [here][ubuntu-lowlatency-kernel-package].

## Old materials from previous post

```bash
sudo python3 setup.py install
```

This latter will install *idlpy* for every user. To test whether the installation was successful, type the following snippet into your Python3 command prompt.

```python
>>> from idlpy import *
```

[Wikipedia-realtime-computing]: https://en.wikipedia.org/wiki/Real-time_computing
[realtime-control-tutorial]: http://www.kelm.ftn.uns.ac.rs/literatura/mrv/P150.pdf
[fundamentals-of-realtime-processing]:https://www.controleng.com/articles/fundamentals-of-real-time-processing-in-automation-and-control/
[realtime-control-tutorial2]: http://ppedreiras.av.it.pt/resources/str1112/apresentacoes_pesquisa/Real-time-CS.pdf
[realtime-systems]: https://users.ece.cmu.edu/~koopman/des_s99/real_time/
[realtime-control-and-network]: http://www.ipnet.agh.edu.pl/Materials1/Module5/Lecture2.pdf
[module5-link]: http://www.ipnet.agh.edu.pl/Materials1/Module5/
[realtime-testing-best-practices]: https://elinux.org/Realtime_Testing_Best_Practices
[rt-tests]: https://wiki.linuxfoundation.org/realtime/documentation/howto/tools/rt-tests
[realtime-linux]: https://wiki.linuxfoundation.org/realtime/start
[realtime-linux-communications]: https://medium.com/hackernoon/real-time-linux-communications-2faabf31cf5e
[rtl-com-paper]: https://arxiv.org/pdf/1808.10821.pdf
[red-hat-realtime-material]: https://www.redhat.com/sysadmin/real-time-kernel

[Manjaro-realtime-kernel]: https://discover.manjaro.org/packages/linux-rt-lts-manjaro
[centos-7-realtime-kernel]: http://mirror.centos.org/centos/7/rt/x86_64/Packages/
[rocky-linux-8-realtime-kernel]: https://repo.uccs.edu/rocky-linux/8/RT/x86_64/os/Packages/
[Stackoverflow-ubuntu-realtime-kernel-patch]: https://stackoverflow.com/questions/51669724/install-rt-linux-patch-for-ubuntu
[ubuntustudio-realtime-kernel]: https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel
[ubuntu-lowlatency-kernel-package]: https://packages.ubuntu.com/focal/linux-lowlatency
