---
layout: post
title: Project Update
author: Leela Chess Team
date: 2018-07-02-02:00
tag: update
draft: true
---
![logo](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/logo.png)

## Project Update

1. We have started training a 256x20 net in the test pipeline. Even with the speed of lc0, the generation of self play games is much slower, which points out how critical lc0 will be to the next phase of training. There are some elo fluctuations we’re trying to iron out. Stay tuned.
2. The 192x15 main server net has crashed through the 6000 self play elo barrier!
3. Resign is working. Fingers crossed.
4. Even compressed, the 256x20 weights file is 130MB. That’s a burden on clients, servers and chews up a lot of time. The last thing before rollout of lc0 to the main pipeline, is shrinking the weights file, either by reducing precision to fp16 (there’s also a 8 bit experimental effort), or by moving to a specialized compression library.
1. The blas backend computed the NN incorrectly, and this was fixed today (7/2/2018)
1. lc0 now supports fp16 computation!
5. New pipeline won’t be next week, and probably not week after next, so more cooking on the existing main net.
