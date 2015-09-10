---
layout: post
title: "Xcode 6   xcassets for universal image support"
description: ""
category: 
tags: [ios]
---

>In 1x place image with resolution 320 x 480. 

>In 2x place image with resolution 640 x 960. 

>In Retina 4 2x place image with resolution 640 x 1136. 

>in 3x place image with resolution 1242 x 2208. 

>Images of Retina 4 2x will upscale to resolution 750 x 1334. 

>Images 3x will downscale to resolution 1080 x 1920. 

[http://stackoverflow.com/questions/26020979/xcode-6-xcassets-for-universal-image-support](http://stackoverflow.com/questions/26020979/xcode-6-xcassets-for-universal-image-support)

##Size Class for launch image

* `2x [- +]` for iPhone6
* `2x [- +]` for iPhone4
* `3x [- +]` for iPhone6plus
* `Retina 4 2x [- +]` for iPhone5