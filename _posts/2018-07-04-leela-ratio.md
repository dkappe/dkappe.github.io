---
layout: post
author: Dietrich Kappe
title: The Leela Ratio
date: 2018-07-04-23:00
draft: true
---

## Leela Ratio: What is it?

If you spend any amount of time around the Leela forums and chats, you'll see an announcement about a gauntlet or match
where IDXXX has defeated some vaunted engine. Maybe there'll be a note about the time control and the GPU or the number of
cores the opponent used. But you are often left watching your head as to how strong or weak Leela was relative to their opponent.

Enter the Leela Ratio: LeR = 875 * leela nps/sf9 nps

This is supposed to be one number that encapsulates how powerful the CPU is versus the GPU. Its derived from the reported ratio between
Alpha Zero's and Stockfish 8's nodes per second -- 80k and 70m. So Stockfish 8 was searching 875 times as many nps as A0. Plugging those
figures into the formula you get 1.0. Anything higher than that, and the GPU is stronger, less than 1.0, and the CPU is
stronger.

How does one get the nps for Leela and Stockfish 9 (most people have 9 instead of 8)?
