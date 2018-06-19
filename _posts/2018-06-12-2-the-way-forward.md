---
layout: post
title: The Way Forward
author: Leela Chess Team
date:   2018-6-18 12:16:01 -0600
---

## The Way Forward

With this post we hope to give an overview of where the project is now and where it is going. In particular, we'll address the status of the main training pipeline and the new test pipeline.

### A brief history of Leela Chess Zero

With the advent of Alpha Go Zero, the hunt was on to reproduce Deepmind's results. Leela Zero was a project to develop a Go playing engine with a Neural Network (NN) directing a Monte Carlo Tree Search (MCTS) algorithm. To make up for a lack of resources, a distributed effort was launched. The publication of the Alpha Zero paper for chess and shogi prompted a similar effort for chess.

Leela Chess Zero (LCZ) is an adaptation of Leela Zero to chess, using Stockfish's position representation and move generation.

### Bugs and self play

Leela Chess Zero has had a number of issues and bugs that affected its play. In roughly chronological order, they are:
<!--more-->

1. Move count disabled
2. Underpromotion
3. First Play Urgency (FPU)
4. Two inputs to the Neural Network (rule50 and the all 1s plane) were not connected properly.
5. Oversampling
6. Rule 50 not normalized

We'll go into each of these in greater depths in future posts.

Since LCZ trains its neural network from self play games, these bugs have an affect on the play and, consequently, its training. The underpromotion bug, for example, resulted in the black side not promoting pawns to queens. Fixing the bugs improved play and in some cases the network played its way out of the problem, in others slowly or not completely.

Since the mainline network didn't seem to be recovering fully, a decision was made to bootstrap a network from scratch on self play games that were not directly affected by bugs. This network was placed into the main training pipeline as ID396 on June 10th, 2018 and has been the root of subsequent nets. (Another bootstrap network was placed into the training pipeline on June 17th.)

#### TCEC Season 13

Which network will be used for TCEC Season 13? That depends on a number of factors.

1. What hardware will be available? LCZ runs much better on GPU's. Rumor has it that GPU's may or may not be available. Stay tuned for a future blog post
2. How far will the rating have recovered after the bootstrap net?
3. Will a new pipeline be able to produce a super strong 128x10 net that will run better on CPU?

### lczero, lc0 and the test pipeline

Soon after the start of the Leela Chess Zero project, some on the team, led by Alexander Lyashuk (@crem on the discord chat), started an effort to rewrite the engine from scratch. Once all was said and done, the new engine -- dubbed lc0 -- was able to search 4-8 times quicker than the original lczero on NVIDIA GPU's. This held great promise for increasing the number of training games. In order to test the new engine and several other ideas, the team created a test training pipeline where they have been trying out new ideas and processes. They've trained several generations of neural networks from scratch to see which NN hyperparameters give the best results. They are also experimenting with features like automatic resignation to increase the quantity and quality of self play training games.

#### Future Plans

Once all the issues have been shaken out, the team anticipates rolling out the new software to train networks in the main pipeline from scratch. The team is planning to start with a 256x20 net but will train 64x6, 128x10 and 192x15 nets at the same time so that lczero enthusiasts will have strong smaller nets that will run on their hardware platforms.

With the performance of lc0, the pace of training should be prodigious indeed. Stay tuned for announcements as the rollout date approaches.
