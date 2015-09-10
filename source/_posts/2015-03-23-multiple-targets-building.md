---
layout: post
title: "multiple targets building"
description: ""
category: ios
tags: [xcode]
---
[link](http://samwize.com/2014/05/22/create-multiple-targets-slash-apps-for-1-xcode-project/)
[stackoverflow.com 233](http://stackoverflow.com/questions/5346767/is-there-a-way-to-rename-an-xcode-4-scheme) 


# Create New Target
1. select project target 
2. right click 
3. `Duplicate`

#Rename Target,Scheme And Product
1. `Manage Schemes`
1. select target , slow click or return key
2. scheme , [stackoverflow.com 233](http://stackoverflow.com/questions/5346767/is-there-a-way-to-rename-an-xcode-4-scheme) 
3. build target, in `Edit Scheme...` `Build` tab if there are multiple targets, remove useless targets with unchecking all checkboxes and delete them
4. `Build Setting` change `Product Name` from `xxx copy` to `newName`

#Info.plist
rename info.plist ,in `Build Settings` `General` tag select new plist file

#Preprocessor
Select “Awesome Lite” target > Build Settings > Preprocessing > Preprocessor Macros > Add TARGET_LITE to each of the configuration (eg both Debug and Release configurations).


```objc
#if defined(TARGET_LITE)
    NSLog(@"Lite version");
#else
    NSLog(@"Original version");
#endif
```

#Resources, Images and Assets Catalog
Select the resource > File Inspector > Target Membership > check the targets intended.