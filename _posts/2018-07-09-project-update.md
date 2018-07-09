---
layout: post
title: Project Update
author: Leela Chess Team
tag: update
draft: true
date: 2018-07-09-00:30
---
![logo](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/logo.png)

## Project Update

### Continuous Integration

Currently we have the following CI services enabled: 
- [CirecleCI](https://circleci.com/gh/LeelaChessZero/lc0) for linux and mac
- [Appveyor](https://ci.appveyor.com/project/LeelaChessZero/lc0) for windows

CI work continues; not complete, but a lot better than it was 2 weeks ago, mostly thanks to @fersbery and @borg; hopefully that will be even more complete by promo.

### Various Fixes

1. There was mutex contention optimization in lc0, which improved multithread performance.
2.  Edge-Node separation is on the way which will reduce memory need at least 2x, but probably more like 3-4x.
3. A mistake in Blas backend was fixed, it returned slightly incorrect results from NN.

### What's stopping us from rolling out lc0 to main net?

- The network compression is possibly the single most important outstanding
thing. There are attempts to reduce precision to fp16 (worked well), and int8
(didn't work well so far, ~150 Elo drop on same nodes).
- Merging both of @Cyanogenoid's training PRs.
- We'd like to see cpuct 1.7 or 1.8, and perhaps resign-playthru set to 20% instead of 10%.
- Given the above changes, we'd like to see one more
test run that's really really short, to verify that the previous at least work
correctly. It doesn't even need to reach first LR drop, only a couple of days
is necessary
- Then promote!
