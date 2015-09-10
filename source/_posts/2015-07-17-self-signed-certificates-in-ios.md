---
layout: post
title: "self signed certificates in iOS"
description: ""
category: ios
tags: []
---

[Five Tips for Using Self Signed SSL Certificates with iOS](http://blog.httpwatch.com/2013/12/12/five-tips-for-using-self-signed-ssl-certificates-with-ios/)
[Create a HTTPS Server to install ipa locally](https://github.com/bumaociyuan/zxIpaServer)

```
openssl genrsa -out myselfsigned.key 2048

openssl req -new -x509 -key myselfsigned.key -out myselfsigned.cer -days 365 -subj /CN=www.mysite.com

openssl pkcs12 -export -out myselfsigned.pfx -inkey myselfsigned.key -in myselfsigned.cer

openssl genrsa -out myCA.key 2048

openssl req -x509 -new -key myCA.key -out myCA.cer -days 730 -subj /CN="My Custom CA"

openssl genrsa -out mycert1.key 2048

openssl req -new -out mycert1.req -key mycert1.key -subj /CN=www2.mysite.com

openssl x509 -req -in mycert1.req -out mycert1.cer -CAkey myCA.key -CA myCA.cer -days 365 -CAcreateserial -CAserial serial
```
www.mysite.com 可以是ip

* 服务器使用`mycert1.cer` `mycert1.key` 创建https服务
* 手机端下载安装`myCA.cer`

