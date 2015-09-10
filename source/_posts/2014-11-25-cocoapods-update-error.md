---
layout: post
title:  "cocoapods update error"
date:   2014-11-25	15:18:07
categories: [ios]
tags: [cocoapods]

---

Run `pod install`

Get message like below

```
[!] From now on use `abc.xcworkspace`.

[!] The use of implicit sources has been deprecated. To continue using all of the sources currently on your machine, add the following to the top of your Podfile:

    source 'https://github.com/CocoaPods/Specs.git'


[!] The `abc [Debug]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods/Pods.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.

[!] The `abc [Release]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods/Pods.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
```

Build project get error below

```
Undefined symbol for architecture “_OBJC_CLASS_$_AFHTTPClient”

blablabla
```

#Solution :

Add `$(inherited)` to `Ohter Linker Flags`