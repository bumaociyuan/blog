---
layout: post
title: How to debug node with atom
date: 2016-09-01 15:01:09
categories: node
tags: [node,atom]
---

# Install Atom and node-debugger

[Atom](https://atom.io/)

```
apm i node-debugger
```

# Config Project
1. Open your node project.
2. Click `Cmd+,` open `Settings`.
3. Select `Packages` and open settings of `node-debugger`.
4. Config `Node Path` and `Script Main`.

# How to debug
<!--more-->
1. Use shortcut or [command-palette:toggle](https://atom.io/packages/command-palette) to run `node-debugger:start-resume`.
2. Use `node-debugger:toggle-breakpoint` to toggle breakpoint where you want.
3. Send request on client.
4. Breakpoint will be trigger.
5. Use `node-debugger:step-next` ,`node-debugger:start-resume` and `node-debugger:stop` for debug.
6. Print variable by input js script in debug console.

![d69cbc5e-ce8f-499e-a482-7981fa97e95f](https://cloud.githubusercontent.com/assets/4977911/18158917/c610c12a-7058-11e6-87c5-01a8ddb5c806.png)
