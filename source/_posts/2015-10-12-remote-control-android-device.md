title: remote control android device
date: 2015-10-12 15:09:37
categories: android
tags: stf
---

# About STF

[Source Code](https://github.com/openstf/stf)

[Control and manage Android devices from your browser.](https://openstf.io/)


# Demo
![image](https://raw.githubusercontent.com/openstf/stf/master/doc/7s_usage.gif)


# Requirements

[Install](https://github.com/openstf/stf#requirements)


# Installation

[link](https://github.com/openstf/stf#installation)

# Problems

## USB connection

[ADB hasn't whitelisted the manufacturer's vendor ID](https://github.com/apkudo/adbusbini)

[mac OSX上eclipse adb无法识别（调试）小米的解决方案](http://blog.csdn.net/zhaoxy_thu/article/details/11857697)

```
$ echo "0x2717" > ~/.android/adb_usb.ini  
$ adb kill-server  
```



```
$ adb devices

# output likes below
List of devices attached
4***some-number***f		unauthorized
# or
4***some-number***f	    offline
```
Solution

```
$ adb version  
# Android Debug Bridge version 1.0.32
# lowwer version adb should be update
```

[Can't connect Nexus 4 to adb: unauthorized](http://stackoverflow.com/questions/18011685/cant-connect-nexus-4-to-adb-unauthorized) Vasudev's answer

1. Make sure adb is running
2. In device go to Settings -> developer options -> `Revoke USB debugging authorities`
3. Disconnect device
4. In adb shell type > adb kill-server
5. In adb shell type > adb start-server
6. Connect device

## Wireless connection

```
$ stf local --allow-remote
```