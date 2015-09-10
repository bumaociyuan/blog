---
layout: post
title:  "run shell script by double click"
date:   2014-10-16 14:38:50
categories: terminal

---
file name as `auto_synch_this_path.command`

content as 
		
		cd `dirname $0`;git status;git add -A;git commit -m 'zx';git pull;git push


$ `chmod a+x auto_synch_this_path.command`

now can run this script by double click