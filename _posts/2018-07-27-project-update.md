---
title: Project Update
author: Leela Chess Team
layout: post
tag: update
date: 2018-07-27-12:10
---
![leela](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/lc0-logo-1-black-red.png)

## Project Update

Again, lots of stuff going on, but we’ll focus on the burning question: when is lc0 getting rolled out to the main pipeline?

1. We almost started to move, but overfitting (the net is very accurate on existing data, but bad on new data) problems started. We are trying various solutions, including increasing CPUCT as suggested in a series of articles by Oracle on Alpha Zero Connect4 ([part5](https://medium.com/oracledevs/lessons-from-alpha-zero-part-5-performance-optimization-664b38dc509e)).
2. It turns out that storage (for training games) is an issue that we haven't yet solved. We expect to generate 110GB of data per day. And it would be good if that data was stored at least at two sites, for backup reasons. Solving this issue is in progress.
3. We need to enable multi-gpu support for Tensorflow. This requires some non-trivial surgery on the model. Otherwise we will
fall further and further behind the massive amounts of generated data. In progress.

All activities in the work queue can be found on the [project board](https://github.com/orgs/LeelaChessZero/projects/2).

