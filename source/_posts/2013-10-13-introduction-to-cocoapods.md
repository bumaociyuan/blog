---
layout: post
title:  "Introduction to CocoaPods"
date:   2013-10-13 16:06:50
categories: ios
tags: [cocoapods,tutorial]

---
references: [raywenderlich](http://www.raywenderlich.com/12139/introduction-to-cocoapods)




	 sudo gem install cocoapods

	 sudo gem update cocoapods


error:
![image](http://www.dasdoc.com/uploads/origin/201310/131615156.png)

To solve this error 
run this command :

	sudo xcode-select -switch /Applications/Xcode.app
	

`platform :ios, "7.0"`


	pod install --verbose --no-repo-update
	pod update --verbose --no-repo-update
