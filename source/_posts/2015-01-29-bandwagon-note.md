---
layout: post
title: "bandwagon note"
description: ""
category: breakwall
tags: [bandwagon,tutorial]
---

#相关链接

[tutorial](http://www.advertcn.com/thread-20498-1-1.html)

~~[3.99$ VPS](https://bandwagonhost.com/aff.php?aff=322&pid=19)~~

[7vps.net vps推荐网站](http://www.7vps.net/)

[www.vpser.net](http://www.vpser.net/)

[用 Shadowsocks 来做 SOCKS5 代理](http://blog.miskcoo.com/2014/10/shadowsocks-proxy)

August 24, 2015
---

[【新版】bandwagonhost-美国vps主机最新特价版VPS 支持支付宝](http://www.7vps.net/3332.html)

bandwagonhos（搬砖工）美国vps主机商，已经没有以前的便宜货出售了，由于目前他们拿不到低价的IPv4，或者说拿不到低价的大量IP，所以接下来都不会再卖之前3.99美元一年的VPS了

---

1. 进入搬瓦工ClientArea- [https://bandwagonhost.com/clientarea.php](https://bandwagonhost.com/clientarea.php)输入注册的邮箱和密码登录；

2. 点击Services-My Services-点击你需要架设的VPS对应的KiWiVM Control Panel，这样我们就进入VPS的控制面板（在这里可以看到你的VPS的IP和SSH端口等信息）；

3. 点击Stop（停止掉当前的系统）-停止后点击Instal New OS（这个在页面左侧）-进入选择Debian 7 x86，把红字的勾选上，确认，很快你的新系统就安装完成；

4. 新系统安装完成后，搬瓦工会告诉你VPS 新的Root账户密码，以及新的SSH端口，这两项很重要，记下来后面会用到（VPS的root密码可以在Panel里自行设置）。

5. ssh connect
	
```
#login
ssh -p <port> root@<ip>	

#download
wget https://gist.githubusercontent.com/bumaociyuan/6972132712358e2f0ab3/raw/5503365c05badb5ce49be0a94554134aed01d46e/debian_shadowsocks.sh
#or wget http://tennfyfile.qiniudn.com/debian_shadowsocks_tennfy.sh

#install
bash debian_shadowsocks_tennfy.sh

#stop
/etc/init.d/shadowsocks-libev stop

#start
/etc/init.d/shadowsocks-libev start

#config
vi /etc/shadowsocks-libev/config.json
```

```

{
    "server":"ip",
    "server_port":88,			#change the port need to restart server
    "local_port":1080,
    "password":"password",
    "timeout":60,
    "method":"rc4-md5"
}
```

[mac os client](http://sourceforge.net/projects/shadowsocksgui/)

[windows client](https://sourceforge.net/projects/shadowsocksgui/files/dist/)

[ios client](https://github.com/linusyang/MobileShadowSocks)


