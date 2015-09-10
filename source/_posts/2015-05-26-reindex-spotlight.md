---
layout: post
title: "reindex spotlight"
description: ""
category: mac
tags: [spotlight]
---

[Spotlight reports “Indexing and searching disabled” in Lion](http://apple.stackexchange.com/questions/24401/spotlight-reports-indexing-and-searching-disabled-in-lion)

```
sudo mdutil -i off /
sudo rm -rf /.Spotlight*
sudo mdutil -i on /
sudo mdutil -E /
```
