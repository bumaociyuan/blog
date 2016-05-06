---
layout: post
title: 极路由安装shadowsocks
date: 2016-02-18 09:35:47
categories: breakwall
tags: [极路由,shadowsocks]
---

为了打PS4可以快一点买了个极路由

# 开启root权限

* 官方开启root方法：[[公告] 【开发者模式功能开放公告】](http://bbs.hiwifi.com/thread-74899-1-1.html)我用的iPhone5s 在微信验证的时候卡住，换个其他手机就可以了
* 安装开发者模式插件

# ssh 登录

```
ssh root@192.168.199.1 -p 1022 #使用root帐号连接路由，端口为1022，密码为后台登陆密码。 ssh能登录就万能了 
```

# 安装ss
```
cd /tmp && wget https://gist.githubusercontent.com/bumaociyuan/8945f34046c296c9a66b/raw/1924c8bc6a648ebdf99c2d924276bc64da6ef89f/shadow.sh && sh shadow.sh && rm shadow.sh

# 我把参考blog的脚本copy了一份放到gist上
```

# 开启ss
* 重新登录极路由的后台的高级设置，会发现shadowsocks加速的选项，在表单中填写SS帐号密码和加密方式，选择智能模式，保存，只要提示运行中 已加速就表示已经成功连上SS了
* **注意不要升级路由器系统**
* 若shadowsocks选项显示的是：{ "msg": "请求的接口不存在.", "code": 560 }，请重启路由器。

<!--more-->

# 自定义pac
```
vim /etc/gw-redsocks/gw-shadowsocks/gw-shadowsocks.dnslist
```

# 加速
* [Setup a Shadowsocks relay](https://github.com/shadowsocks/shadowsocks/wiki/Setup-a-Shadowsocks-relay)
* [使用haproxy实现shadowsocks 国内中转加速](https://smileawei.com/shadowsocks-haproxy/)
* [提速 Shadowsocks](http://www.jianshu.com/p/475182d8c503/comments/468732)

# 参考
* [极路由Shadowsocks家庭无痛翻墙实践](https://luolei.org/hiwifi-shadowsocks/)
