---
layout: post
title:  "AFNetworking issues"
date:   2014-08-19 14:28:00
categories: ios

---
error :

`Request failed: unacceptable content-type: text/html`

or

`The operation couldn’t be completed (Cocoa error 3840 ) `

fix this issue

 		AFHTTPRequestOperationManager *manager = [AFHTTPRequestOperationManager new];
		NSMutableSet *set = manager.responseSerializer.acceptableContentTypes.mutableCopy;
    	[set addObject:@"text/html"];
   		manager.responseSerializer.acceptableContentTypes = set;