title: 解决 brew 慢的问题
date: 2015-11-04 13:40:35
categories: mac
tags: homebrew
---

# 方法一: 修改镜像源
[brew update 慢 解决办法 镜像更新源](https://www.logcg.com/archives/1301.html)

* 中科大brew镜像源
* 清华brew镜像源

```
$ cd /usr/local
$ git remote set-url origin git://mirrors.tuna.tsinghua.edu.cn/homebrew.git
# 清华镜像源
$ git remote set-url origin http://mirrors.ustc.edu.cn/homebrew.git
# 中科大镜像源
# 二者选其一即可更新
```

<!--more-->

```
$ cd ~
$ mkdir tmp
$ cd tmp
# 以下要与你选择的镜像源相同
$ git clone git://mirrors.tuna.tsinghua.edu.cn/homebrew.git
$ git clone http://mirrors.ustc.edu.cn/homebrew.git

$ sudo rm -rf /usr/local/.git
$ sudo rm -rf /usr/local/Library
$ sudo cp -R homebrew/.git /usr/local/
$ sudo cp -R homebrew/Library /usr/local/
```

***if***

```
fatal: Unable to create '/usr/local/.git/index.lock': Permission denied
Cannot save the current index state
Error: Failure while executing: git stash save --include-untracked --quiet
```

***then***

```
$ sudo chgrp -R admin /usr/local
# 确保目录归属管理组
$ sudo chmod -R g+w /usr/local
# 确保管理组可读
```
***endif***

# 方法二: 用ss

[using shadowsocks in terminal
](http://bumaociyuan.github.io/breakwall/2015/08/10/using-shadowsocks-in-terminal.html)