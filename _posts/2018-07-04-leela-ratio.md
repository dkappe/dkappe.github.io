---
layout: post
author: Dietrich Kappe
title: The Leela Ratio
date: 2018-07-04-23:00
---

![img](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/D7F9F98E-6367-4821-BBB7-E0E7894D0323.jpeg)

## Leela Ratio: What is it?

If you spend any amount of time around the Leela forums and chats, you'll see an announcement about a gauntlet or match
where IDXXX has defeated some vaunted engine. Maybe there'll be a note about the time control and the GPU or the number of
cores the opponent used. But you are often left scratching your head as to how strong or weak Leela was relative to their opponent.

Enter the Leela Ratio: LeR = 875 * leela nps/sf9 nps

<!--more-->

This is supposed to be one number that encapsulates how powerful the CPU is versus the GPU. Its derived from the reported ratio between
Alpha Zero's and Stockfish 8's nodes per second -- 80k and 70m -- during their match. So Stockfish 8 was searching 875 times as many nps as A0. Plugging those
figures into the formula you get 1.0. Anything higher than that, and the GPU is stronger, less than 1.0, and the CPU is
stronger.

How does one get the nps for Leela and Stockfish 9 (most people have 9 instead of 8)?

### Leela NPS

Quoting from the lc0 benchmark wiki page.

“Run go infinite from start position and abort after depth 26 and report NPS output.”

### SF9 NPS

Fire up the sf9 engine, “go infinite” from the start position, and around depth 26-28, abort and note the nps.

As an example, on my laptop with a GTX 1070 and 1 core for sf9, I get around 10,000 nps with a 192x15 net and 1,410,000 nps for sf9. Plugging that into our equation, we get LeR = 6.2, so a bit in favor of the GPU.

Hope this helps and happy engine matches!
