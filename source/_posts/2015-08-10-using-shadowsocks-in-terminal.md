---
layout: post
title: "using shadowsocks in terminal"
description: ""
category: breakwall
tags: [terminal,shadowsocks]
---

[Using Shadowsocks with Command Line Tools](https://github.com/shadowsocks/shadowsocks/wiki/Using-Shadowsocks-with-Command-Line-Tools)


```
#1
$ brew install proxychains-ng

#2
$ mkdir ~/.proxychains;touch ~/.proxychains/proxychains.conf

```

then copy 

```
strict_chain
proxy_dns 
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.0/255.0.0.0
quiet_mode

[ProxyList]
socks5  127.0.0.1 1080
```

into `~/.proxychains/proxychains.conf`

##usage

```
$ proxychains4 youtube-dl -o funny_video.flv https://www.youtube.com/funny_video
##youtube-dl supported site https://github.com/rg3/youtube-dl/blob/master/docs/supportedsites.md :D
```