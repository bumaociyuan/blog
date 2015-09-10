---
layout: post
title: "open application in terminal"
description: ""
category: terminal
tags: [alias]
---


I found solution of [open sublime in terminal](http://bumaociyuan.github.io/mac/2015/08/10/open-sublime-in-terminal.html), but how can I open others app in terminal ?

##Copy  following lines into  `~/.bashrc` or  `~/.zshrc`

```
# -------
# Function
# -------
function google() { open "https://www.google.com/search?q=$*&gws_rd=ssl"; }
function baidu() { open "https://www.baidu.com/s?ie=UTF-8&wd=$*"; }
function github() { open "https://github.com/search?utf8=%E2%9C%93&q=$*"; }

# -------
# Aliases
# -------
alias chrome='open -a /Applications/Google\ Chrome.app'
alias sublime='open -a /Applications/Sublime\ Text\ 3.app'
alias xcode='open -a /Applications/Xcode.app'
alias mou='open -a /Applications/Mou.app'
...and so on

```

##Make sure `~/bash_profile` contains following line
```
if [ -f ~/.bashrc ]; then . ~/.bashrc; fi
```

#Usage
```
$ github bumaociyuan

$ chrome http://bumaociyuan.github.io/terminal/2015/08/17/open-application-in-terminal.html
```
