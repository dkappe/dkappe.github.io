——
draft: true
title: Project Update
author: Leela Chess Team
layout: post
tag: announcement update
date: 2018-07-17-23:55
—-
![logo](https://raw.githubusercontent.com/dkappe/dkappe.github.io/master/public/images/logo.png)

## Project Update

There’s a fair amount going on with the project, but we’re just going to focus on those things that are critical path to the lc0 rollout to main.

<!—more—>

1. We’re very close to having efficient storage of the enormous 256x20 nets. Error323 is finishing up 16 bit floating point plus protobuf storage. Protobuf (protocol buffer) is a utility library from google. You can read more about it [here](https://developers.google.com/protocol-buffers/).
2. The various programs are now being built and tested automatically when the source code is modified. That’s a huge time saver. That’s what’s known in the biz as Continuous Integration (CI).
3. Once we’re done with the new network storage, there’s a bunch of testing, scripting and migration work that needs to go on. There’s a lot of data and contributors here, and if we’re not careful, it could all fall over in a heap.
4. Rollout of lc0 to main, possibly with the current test net as the starter.

Again, given the volunteer nature of the project, we don’t want to set a date. If you want it to go faster and you have programming or sysadmin skillsets, reach out on discord (see the sidebar) and we’ll put you to work.
