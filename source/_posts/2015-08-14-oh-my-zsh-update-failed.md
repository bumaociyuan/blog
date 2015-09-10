---
layout: post
title: "oh my zsh update failed"
description: ""
category: terminal
tags: [zsh]
---

Error message like :

```
blabla https://...... certificate .... fail 
:D
```

##Solution

```
$ vim $ZSH/.git/config
#replace origin url with 'git@github.com:robbyrussell/oh-my-zsh.git'

$ upgrade_oh_my_zsh
```