---
layout: post
title:  "xcode errors"
date:   2014-06-19 18:28:50
categories: ios

---

---
February 4, 2015

**Showing first 200 notices only**
静态库重复


---

**Mach O Link Error- linker command failed with exit code 1 (use -v to see invocation)**

[link](http://stackoverflow.com/questions/12591711/mach-o-link-error-linker-command-failed-with-exit-code-1-use-v-to-see-invocat)
```
"build active architecture only" to yes
```

---
**E79CDDB501B68E74DDF03EA4E75246A7FDF010D0: no identity found Command /usr/bin/codesign failed with exit code 1**

[link](http://stackoverflow.com/questions/26376166/e79cddb501b68e74ddf03ea4e75246a7fdf010d0-no-identity-found-command-usr-bin-cod)

Xcode > Preferences > Accounts > View Details > And just refresh the Provisioning Profile 

---

**Command /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/clang failed with exit code 1**

将Apple LLVM compiler 4.2 - Language ->c++ Standard Library 修改为 libstdc++ （GNU C++ standard library）

---

**Could not change executable permissions on the application.**

Delete the app, restart iPhone