---
layout: post
title: The Bootstrap Network
author: Ben
date:   2018-6-20 12:16:01 -0600
draft: true
---

[early nn]: https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/7955F47E-263A-443E-87E2-F535A1F5A341.jpeg

## Bootstrap Nets

As has been previously mentioned, the neural networks trained from self play games were not fully recovering from some of the bugs and issues present during the projects’ lifespan. I decided to train, or “bootstrap,” a new 192x15 network from scratch using only “clean” games, i.e. those self play games free from the effects of bugs.

Based on the 16 million games available, it was easy to eliminate games 4-6.5 million as they were heavily infected with the "black underpromotion bug." Extra games were excluded (11-15 million) based on the regression observed in testing (possibly biased with the oversampling issue).

The first bootstrap used 5 million games for the first half of training and then between 500,000 and 1 million after that. The “window” of games was regularly updated to include recent games.

Starting with ID396, an experiment was implemented to see how much the various bugs had impaired the existing NN. The main network was switched out to a bootstrapped network.

The first bootstrap process suffered from having the learning rate (LR) dropped too quickly. By the time it was released, the LR was at the lowest step available. After the bootstrap was switched to main, the network struggled to progress.

Based on the lack of progress, a second bootstrap was started to test if keeping the LR higher during initial training would give better results. The second attempt quickly increased in strength. At 300,000 steps the second bootstrap had eclipsed the first.

Given that there was much more potential in the second bootstrap, it was switched over to the main pipeline at ID 421. The second bootstrap is strengthening and will hopefully surpass the strength of the previous main network.

Hyper parameters used for second bootstrap:

    Batch Size: 512 (based on memory limitations of the GPU used in training)
    Number of games: set to accomplish a sampling rate of 0.5
    Learning rate:
    0.2 (0-70,000)
    0.025 (70,000-225,000 steps)
    0.0085 (225,000-275,000 steps)
    0.0025 (275,000-300,000 steps)

