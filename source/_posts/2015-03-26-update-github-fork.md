---
layout: post
title: "update github fork"
description: ""
category: git
tags: []
---

1. [Configuring a remote for a fork
](https://help.github.com/articles/configuring-a-remote-for-a-fork/)

```
$ git remote add upstream git@github.com:ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```

2. [Syncing a fork](https://help.github.com/articles/syncing-a-fork/)

```
$ git fetch upstream
$ git checkout master
$ git merge upstream/master
```
