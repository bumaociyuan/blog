title: ngrok note
date: 2015-09-14 14:45:55
categories: ngrok
tags:
---

> `ngrok.com` has been GFWed

# Installation
1. [https://ngrok.com/download](https://ngrok.com/download)
2. unzip `ngrok.zip`

<!--more-->

# Usage

## Expose a local web server to the internet

```
$ ngrok http 8000
```
output will be like

```
ngrok by @inconshreveable     (Ctrl+C to quit)

Tunnel Status                 online
Version                       2.0.19/2.0.19
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://c9f486b5.ngrok.io -> localhost:8000
Forwarding                    https://c9f486b5.ngrok.io -> localhost:8000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```

`http://c9f486b5.ngrok.io` also GFWed

## TCP Tunnels

```
$ ./ngrok tcp 22
```

output will be like

```
ngrok by @inconshreveable     (Ctrl+C to quit)

Tunnel Status                 online
Version                       2.0.19/2.0.19
Web Interface                 http://127.0.0.1:4040
Forwarding                    tcp://0.tcp.ngrok.io:33213 -> localhost:22

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```

ssh login

```
$ proxychains4 ssh zx@0.tcp.ngrok.io -p 33213
# http://bumaociyuan.github.io/breakwall/2015/08/10/using-shadowsocks-in-terminal.html
```