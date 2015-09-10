---
layout: post
title:  "make a cocoapods lib"
date:   2014-08-29 13:54:52
categories: ios
tags: [cocoapods,tutorial]

---

---2015.08.02---

**error**`- ERROR | [watchOS] Returned an unsuccessful exit code.` blabla

add flowing code in podspec

```
s.osx.deployment_target = '10.8'
s.ios.deployment_target = '6.0'
s.watchos.deployment_target = '2.0'
```

[build on Xcode 7](https://github.com/CocoaPods/CocoaPods/issues/3925)

---2014.11.05---

update lib

edit the `NSString-BlockHelper.podspec` add `1.0.1` version

```
git tag 1.0.1;	git push --tags
pod trunk push NSString-BlockHelper.podspec --verbose

```

get error `You need to register a session first.`

```
pod trunk register <yourEmail> '<yourName>' --description='macbook pro'
#click the confirm email in yourEmail
pod trunk push NSString-BlockHelper.podspec --verbose
```

`pod search` cannot search the `1.0.1` version

but `pod install` in new project can install `1.0.1`


---2014.08.29---

[nshipster blog](http://nshipster.com/cocoapods/)

[http://guides.cocoapods.org/](http://guides.cocoapods.org/making/making-a-cocoapod.html)

[Your First CocoaPod](http://code.dblock.org/your-first-cocoapod)

demo : [link](https://github.com/bumaociyuan/NSString-BlockHelper.git)

1. create NSString-BlockHelper.podspec

```
Pod::Spec.new do |s|
		s.name     = 'NSString-BlockHelper'
		s.version  = '1.0.0'
s.license  = { :type => 'MIT', :file => 'LICENSE.md' }
s.summary  = "NSString+BlockHelper"
		s.homepage = 'https://github.com/bumaociyuan/NSString-BlockHelper'
s.authors  = { 'bumaociyuan' => 'http://bumaociyuan.github.io/' }
	s.source   = { :git => 'https://github.com/bumaociyuan/NSString-BlockHelper.git', :tag => s.version.to_s }
	s.source_files = 'NSString+BlockHelper/*{h,m}'
	s.requires_arc = true
end

```

2. set the tag
`git tag 1.0.0;	git push --tags`


3. use the cmd
`pod trunk push NSString-BlockHelper.podspec --verbose` to push .podspec to repo

