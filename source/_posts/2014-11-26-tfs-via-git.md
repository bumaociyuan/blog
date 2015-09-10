---
layout: post
title:  "tfs via git"
date:   2014-11-26	09:09:19
categories: [git]
tags: [tfs]

---

[Mac下配置Git-TF来连接TFS2012](http://www.2cto.com/os/201209/157713.html)

[Adding a certificate authority to the Java runtime](http://mikepilat.com/2011/05/adding-a-certificate-authority-to-the-java-runtime.html)

[Git For TFVC Users](http://hamidshahid.blogspot.com/2014/02/git-for-tfvc-users.html)

1. Download [latest release of git tf](https://gittf.codeplex.com/)
2. Extract the contents of git-tf-2.0.3.20131219.zip to a folder on your local machine, i.e. `/Users/[ME]/git-tf/` on mac.
3. Add the path where you extracted Git-TF (i.e. `/Users/[ME]/git-tf/`) to your PATH environment variable.

open ~/.profile

```
export PATH="/Applications/Xcode.app/Contents/Developer/usr/libexec/git-core/":$PATH
export PATH="/Users/[ME]/git-tf/":$PATH
export JAVA_HOME="/System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home"

$ source .profile
```

4. add user name and password

```
git config --global git-tf.server.username username
git config --global git-tf.server.password ***********
```

5. install ca.cer

required java version "1.6.0_65" (must)

[download Java for OS X 2014-001](http://support.apple.com/kb/DL1572)

```
sudo keytool -import -trustcacerts -file zztxca.cer -alias CompanyCA -keystore  /System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home/lib/security/cacerts

#the default password for the cacerts keystore is `changeit`

#When asked Trust this certificate? by keytool, answer yes

```

6. clone project

```
git tf clone https://server.com/tfs $/projectName
```


7. pull

```
git tf pull
``` 


8. checkin

```
git tf configure http://myserver:8080/tfs/mycollection $/TeamProjectA/Main
git tf pull
git commit -a -m "merge commit"
git tf checkin
git push

```

9. recommended git settings

```
git config [--global] core.autocrlf false
git config [--global] core.ignorecase true
```

