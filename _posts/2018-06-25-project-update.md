---
title: Project Update
author: Team
date: 2018-06-25
draft: true
---
## Project update

This past week saw a lot of work in the testing pipeline on resignation. The idea is that a small number of resignations in hopeless positions will increase the quality and quantity of positions that are fed to the network training. An advantage of testing before it’s rolled out, is that the facts can be identified before hand. So it with “false positives,” resignation in drawn or won positions. The team is working to smooth out these rough spots.

## When will lc0 arrive?

There are two reasons we can’t give a date certain:
1. Much of the work, like tuning the hyper-parameters for Tensorflow, is experimental. You have to try and try again until you get a satisfactory result.
2. The development wordk is being done by volunteers with day jobs, spread across many time zones. Combined that with validation on processes that take a long time to run, and development can be a bit inefficient.

### What remains?

If we can’t have a precise date, what about some info on what remains to be done and its progress? Well I have good news. The team has set up a kanban board to track work and work-in-progress for the relaunch. It can be found [here](https://github.com/orgs/LeelaChessZero/projects/2).

I’ll just point out some of the big items. (Note: what I think is important may not line up 100% with the development team, but is based on my experience shipping working software for over 35 years.)


#### Getting a working lc0 to end users. 

With lczero, you had essentially 6 targets: CPU and GPU (using OpenCL) for Linux, Windows and MacOS. OpenCL hid the variation in GPU’s which greatly simplified matters.

With lc0, you have far more targets. We’re using CUDA 9.2 for NVIDIA GPU’s, as well as supporting multiple other backends for other GPU’s and CPU’s. The pluggable backend is an elegant design, but requires a fair amount of testing across Linux, Windows and MacOS.

Also, the use of CUDA 9.2 brings up a licensing issue. The CUDA and cuDNN libraries from NVIDIA have distribution restrictions. We’d like to be able to distribute executables and libraries to end users, rather than make them download the libraries or, god forbid, essay a complex build process for lc0.

#### Tweaking the new training pipeline

The build pipeline — communicating with clients, splitting test from training games, optimizing self play parameters, etc. — 
