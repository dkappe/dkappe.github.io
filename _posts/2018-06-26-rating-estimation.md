---
title: Estimating Leela's Strength, Part 1
author: MTGoStark
date: 2018-06-26-00:15
---

![img](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/jumble.jpg)

## The CCRL Rating List

The Leela CCRL Estimate rating list initially began as a personal project, with the goals of a) rating Stockfish difficulties
on the CCRL scale and b) equating it with a human FIDE Elo, adjusted by time control. I wanted to spar against a computer
opponent to get better at chess, but only at an intermediate level. The engines in the <2000 range were generally hard to
find or hard to get working, so I decided to use Stockfish difficulty levels. 

I soon realized that it was inadequate to use traditional rating anchors for this purpose, as they generally inflated the Elo
and produced a lot of variability depending on the engine used. So I produced a CCRL *curve*, and the Bayes Elo deltas
produced from the tournaments I ran were normalized to that, rather than anchored to any given engine. This allowed me to
accurately rate an engine (or Stockfish difficulty) on the CCRL standard, quite accurately, and without any nearby anchors
necessary.

<!--more-->

To translate the rating into human Elo, I gathered all available match results between human GMs and chess engines, and then
normalized for time control, hardware, and odds. This yielded a “dampening factor” (human FIDE Elo is generally lower than
CCRL equivalent), and an intercept value that changes with time/hardware specification, which I keep constant for the purposes
of determining Leela’s rating.

After the AlphaZero paper was published in December 2017, I followed the work surrounding learning programs for chess
intently, and before long discovered Leela Chess Zero, which seemed like the distributed computing counterpart to AlphaZero,
and chess counterpart to Leela Zero. As it so happened, my work on building a rating list that accurately scaled from low to
high Elo on the CCRL standard was a great fit for tracking the progress of the fledgling project. 

For testing, Leela is pitted against a gauntlet of opponents that are composed of traditional Alpha-Beta (AB) engines, as
well as other versions of Leela, with the idea of challenging’s Leela’s tactical strength with the AB engines and positional
strength with the Leela versions. This is most applicable during Leela’s earliest networks, where the self-play Elo is quite
volatile vs. its real performance Elo, and where Leela is tactically quite weak; so while an early network could perhaps
beat prior Leela networks, it may still fail spectacularly even against weak AB engines, which is taken into account in its
rating. Adjudication settings were chosen based on prior experience; overall, the adjudication only introduces ~1% error into
the results, while more than doubling gamerate. 

I’ve been providing up-to-date ratings, progress graphs, and scaling information for the Leela Chess Zero project since March
2018.

The information is contained within this [google spreadsheet](https://docs.google.com/spreadsheets/d/1XSJiCcQpCLv0fNwrUn7jXjdkZFU63YFEWpdXv6dSSg0/edit#gid=0).

### What's Next

For the upcoming Lc0 training run, I am working on implementing some further updates and improvements, including:

1. Improved calibration to CCRL standard and FIDE equivalent
1. Faster testing methodology – goal is to provide rating for every net rather than every 5 (assuming similar schedule)
1. More organized and easier to maintain backend
1. Stockfish 9 scaling curve
1. Leela opening book

