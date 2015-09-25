title: ngrok note
date: 2015-09-14 14:45:55
categories: ngrok
tags:
---

# Basic 

> `ngrok.com` has been GFWed

## Installation
1. [https://ngrok.com/download](https://ngrok.com/download)
2. unzip `ngrok.zip`

<!--more-->

## Usage

### Expose a local web server to the internet

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

### TCP Tunnels

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
$ proxychains4 ssh username@0.tcp.ngrok.io -p 33213
# http://bumaociyuan.github.io/breakwall/2015/08/10/using-shadowsocks-in-terminal.html
```

## Free server
[TUNNEL](http://www.tunnel.mobi/)是一个基于NGROK的`免费`网络服务

# Setup ngrok on your own server

[自行编译ngrok服务端客户端，替代花生壳，跨平台](http://www.ekan001.com/articles/38)



## Setup ngrok

```
$ cd /usr/local/src/
$ git clone https://github.com/inconshreveable/ngrok.git
$ export GOPATH=/usr/local/src/ngrok/
$ export NGROK_DOMAIN="yourdomain.com"
```

```
$ openssl genrsa -out rootCA.key 2048
$ openssl req -x509 -new -nodes -key rootCA.key -subj "/CN=$NGROK_DOMAIN" -days 5000 -out rootCA.pem
$ openssl genrsa -out device.key 2048
$ openssl req -new -key device.key -subj "/CN=$NGROK_DOMAIN" -out device.csr
$ openssl x509 -req -in device.csr -CA rootCA.pem -CAkey rootCA.key -CAcreateserial -out device.crt -days 5000
$ cp rootCA.pem assets/client/tls/ngrokroot.crt
$ cp device.crt assets/server/tls/snakeoil.crt 
$ cp device.key assets/server/tls/snakeoil.key
```

## Compiling server

### Installl golang on Ubuntu
```
$ sudo apt-get install golang 					# do not use this
$ go version 									# v1.02 is too low
$ sudo apt-get remove --auto-remove golang		# remove golang v1.02
```
[Install Golang 1.4 on Ubuntu](https://ubuntu.kertaskampus.com/install-golang-1.4-on-ubuntu/)

For `32bit` machine

```
$ wget --no-check-certificate --no-verbose https://storage.googleapis.com/golang/go1.4.2.linux-386.tar.gz
$ tar -C /usr/local -xzf go1.4.2.linux-386.tar.gz
```

Add this line on your `.bashrc`

```
export PATH=$PATH:/usr/local/go/bin
```
### Compile

```
$ GOOS=linux GOARCH=amd64 make 
$ release-server
#如果是32位系统，这里 GOARCH=386
```

Error

```
GOOS="" GOARCH="" go get github.com/jteeuwen/go-bindata/go-bindata
# github.com/jteeuwen/go-bindata
src/github.com/jteeuwen/go-bindata/toc.go:47: function ends without a return statement
make: *** [bin/go-bindata] Error 2
```
[解决办法](https://github.com/inconshreveable/ngrok/issues/237)

## Start server

```
$ bin/ngrokd -domain="$NGROK_DOMAIN" -httpAddr=":8000" #client could not connect
# or
$ bin/ngrokd -tlsKey="assets/server/tls/snakeoil.key" -tlsCrt="assets/server/tls/snakeoil.crt" -domain="yourdomain.com"
```

## Compiling client
### Install golang on mac
[https://golang.org/dl](https://golang.org/dl)

### Compile

Replace `/usr/local/src/ngrok/src/ngrok/log/logger.go` line 5 with 

```
log "github.com/keepeye/log4go"
# Thanks GFW
```

```
$ GOOS=darwin GOARCH=amd64
$ make release-client
```

## Start client

Edit `config.cfg`

```
server_addr: "bumaociyuan.cc:4443"
trust_host_root_certs: false
tunnels:
  http:
    subdomain: "test"
    proto:
      http: "80"
 
  ssh:
    remote_port: 2222
    proto:
      tcp: "22"
```

```
$ ./ngrok -config config.cfg start http ssh
# or
$ ngrok -config config.cfg -subdomain=test 8000
```



Error on server log

```
[09/23/15 01:42:27] [INFO] [tun:2a8cef20]New connection from ***.***.**.**:54043
[09/23/15 01:42:27] [DEBG] [tun:2a8cef20] Waiting to read message
[09/23/15 01:42:27] [WARN] [tun:2a8cef20] Failed to read message: remote error: bad certificate
[09/23/15 01:42:27] [DEBG] [tun:2a8cef20] Closing
```
[Self Hosted ngrokd fails to allow client to connect](https://github.com/inconshreveable/ngrok/issues/84)

Solution

```
$ bin/ngrokd -tlsKey="assets/server/tls/snakeoil.key" -tlsCrt="assets/server/tls/snakeoil.crt" -domain="yourdomain.com"
# compile client with the same certificate
```