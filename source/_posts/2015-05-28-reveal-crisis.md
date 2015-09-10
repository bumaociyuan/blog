---
layout: post
title: "reveal crisis"
description: ""
category: 
tags: [other]
---

27岁生日前一天,入手了正版reveal
装了 reveal loader没的反应
看了[这篇教程](http://c.blog.sina.com.cn/profile.php?blogid=cb8a22ea89000gtw)
这**的blog

>4、将libReveal.dylib上传到设备的/Library/MobileSubstrate/DynamicLibraries

>6、re-spring或重启iOS设备，打开你想看的app，再从Reveal界面左上角选择要连接的机器，进入不同的页面之后还可以点击右上角的刷新钮来刷新监测的页面信息。


这步我的iphone 就无限 apple logo 了,
差点就用 itunes restore 了

幸好看到了这个哥们的[视频](https://youtu.be/MnH3225PFVk)
解决的了无限logo
方法就是`按住音量上30秒或以上`

但是启动了手机之后所有cydia 插件都不能用了, `超雪` `afc2add` 都没的了,多半是 libReveal.dylib 把cydia 的auto load 卡到了,

ifunbox 也不能打开 iphone 的root file system,

不过`openssh` 还可以用, 用`ssh` 到手机果断 `rm /Library/MobileSubstrate/DynamicLibraries/libReveal.dylib`

重启手机完全正常.

reveal crisis

fin

#解决办法

[Reveal 1.5.x 會讓 SpringBoard crash](http://hiraku.tw/2015/03/3779/)

>正確解法是新增 libReveal.plist  設定 filter （對，我以前懶惰都不設定）

>Bundle 設定一個不存在的值就好了，例如 com.apple.Tabemonodesuyo

>之後裝 Reveal Loader，用 loader 去控制要在哪個 App 執行就好，

[Injecting Reveal With MobileSubstrate
](http://www.zdziarski.com/blog/?p=2361)

```
#remove reveal loader
$ scp -r Reveal.framework root@x.x.x.x:/System/Library/Frameworks

$ scp libReveal.dylib root@x.x.x.x:/Library/MobileSubstrate/DynamicLibraries

$ vim /Library/MobileSubstrate/DynamicLibraries/libReveal.plist
#input :{ Filter = { Bundles = ( "com.apple.MobileSMS"; "net.whatsapp.WhatsApp" ); }; }

$ killall SpringBoard

```