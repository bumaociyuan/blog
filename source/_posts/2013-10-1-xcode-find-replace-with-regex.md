---
layout: post
title:  "xcode find and replace with regex"
date:   2013-10-11 16:06:50
categories: ios

---

##update July 6, 2015
replace code with Automator
[Editing text in Automator](http://stackoverflow.com/questions/13495102/editing-text-in-automator)

Add shortcut for services
`Keyboard` -> `Shortcuts` -> `Services` -> `The new Service` add shortcut
in Xcode many shortcuts not working
`cmd+shift+X` works well

---
##2013-10-11

reference [stackoverflow](http://stackoverflow.com/questions/4778847/find-replace-in-xcode-using-regular-expression)

example
search: 
`NSLocalizedString(@"words", nil) `

 with regex: 
 
` (NSLocalizedString\()(@"\w+")(, nil\))`


relace regex: 

`ZXLocalizeble\(\2\)`

replace all  

result: `ZXLocalizeble(@"words")`

insert return

press `ctrl+q` press `return`


