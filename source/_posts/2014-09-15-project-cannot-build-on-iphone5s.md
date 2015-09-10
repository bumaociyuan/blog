---
layout: post
title:  "project cannot build on iphone5s"
date:   2014-09-15 14:19:52
categories: ios

---

**No architectures to compile for (ONLY_ACTIVE_ARCH=YES, active arch=arm64, VALID_ARCHS=armv7 armv7s).**

[Xcode 5.1 - No architectures to compile for (ONLY_ACTIVE_ARCH=YES, active arch=x86_64, VALID_ARCHS=i386)](http://stackoverflow.com/questions/22328882/xcode-5-1-no-architectures-to-compile-for-only-active-arch-yes-active-arch-x)



1. Delete the "Pods" project from the workspace in the left pane of Xcode and close Xcode.
2. Run "pod install" from the command line to recreate the "Pods" project.
3. Re-open Xcode and make sure "Build Active Architecture Only" is set to "No" in the build settings of both the "Pods" project and your own project.
4. Clean and build.
