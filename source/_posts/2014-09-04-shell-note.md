---
layout: post
title:  "shell note"
date:   2014-09-04 16:41:50
categories: terminal
---

February 2, 2015

```
caffeinate -t 3600
```

Where 3600 is the number of seconds in one hour. You may modify it to any number of seconds, or alternatively just enter caffeinate without a timer to disable sleep mode until that terminal window is closed.

-------
January 14, 2015



[List Your 15 Most Used Terminal Commands](http://osxdaily.com/2012/11/02/list-most-used-terminal-commands/)

```bash
history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head -15
```

-------

[Linux Shell Scripting Tutorial v1.05r3
A Beginner's handbook](http://www.freeos.com/guides/lsst/)

[link](http://www.92csz.com/study/linux/12.htm)

---2014.12.05--

[gitbook](http://anotheruiguy.gitbooks.io/gitforeveryone/content/terminal/cheat-sheet.html)




`Ctrl + A `     Go to the beginning of the line you are currently typing on 

`Ctrl + E `    Go to the end of the line you are currently typing on  

`Ctrl + U `    Clear the line before the cursor 

`Ctrl + K `    Clear the line after the cursor 

`Ctrl + W `    Delete the word before the cursor 



---2014.11.09--

```
rm -rf dirPath
```

-----2014.10.25-------

* 创建以当前时间为文件名的
	
	mkdir `date +%Y%m%d`
	
* split

```
	string="hello,world,i,like,you,babalala"  
	array=(${string//,/ })  
  
	for i in ${array[@]}  
	do  
   	 echo $i  
	done 
```
* join

```
	array=(${string//,/})
	printf -v var "%s-" "${array[@]}"
	var=${var%?}

```



-----2014-09-04-------
#### 1. 记录命令历史
* `!! （”连续两个”!”），表示执行上一条指令`
* !n（这里的n是数字），表示执行命令历史中第n条指令，例如”!100”表示执行命令历史中第100个命令
* `!字符串（字符串大于等于1），例如!ta，表示执行命令历史中最近一次以ta为开头的指令。`
	
#### 2. 指令和文件名补全
* `按tab键，它可以帮你补全一个指令，也可以帮你补全一个路径或者一个文件名。连续按两次tab键，系统则会把所有的指令或者文件名都列出来。`

#### 3. 别名 alias
![image](http://www.92csz.com/study/linux/images/12_7.png)
* alias语法很简单，alias [命令别名]=[’具体的命令’]。

#### 4. 通配符
* 在bash下，可以使用*来匹配零个或多个字符，而用?匹配一个字符。
![image](http://www.92csz.com/study/linux/images/12_8.png)

#### 5. 管道符
* `前面已经提过过管道符”|”，就是把前面的命令运行的结果丢给后面的命令。`

#### 6. 作业控制
* 当运行一个进程时，`你可以使它暂停（按Ctrl+z），然后使用fg命令恢复它`，利用bg命令使他到后台运行，你也可以使它终止（按Ctrl+c）。

#### 7. 变量
* 前面章节中笔者曾经介绍过环境变量PATH，这个环境变量就是shell预设的一个变量，通常shell预设的变量都是大写的。变量，说简单点就是使用一个较简单的字符串来替代某些具有特殊意义的设定以及数据。就拿PATH来讲，这个PATH就代替了所有常用命令的绝对路径的设定。因为有了PATH这个变量，所以我们运行某个命令时不再去输入全局路径，直接敲命令名即可。你可以使用echo命令显示变量的值。
* 使用env命令即可全部列出系统预设的全部系统变量了。不过登录的用户不一样这些环境变量的值也不一样。当前显示的就是root这个账户的环境变量了。下面笔者简单介绍一下常见的环境变量：

```
使用env命令即可全部列出系统预设的全部系统变量了。不过登录的用户不一样这些环境变量的值也不一样。当前显示的就是root这个账户的环境变量了。下面笔者简单介绍一下常见的环境变量：
PATH	决定了shell将到哪些目录中寻找命令或程序

HOME	当前用户主目录

HISTSIZE	历史记录数

LOGNAME	当前用户的登录名

HOSTNAME	指主机的名称

SHELL	前用户Shell类型

LANG	语言相关的环境变量，多语言可以修改此环境变量

MAIL	当前用户的邮件存放目录

PWD	当前目录

env命令显示的变量只是环境变量，系统预设的变量其实还有很多，你可以使用set命令把系统预设的全部变量都显示出来。
```

* set不仅可以显示系统预设的变量，也可以连同用户自定义的变量显示出来。用户自定义变量？是的，用户自己同样可以定义变量

```
myname=zx //不能有空格 myname='first name'
set|grep myname
//output : myname=zx

myname="$myname"dddd //变量内容可以累加其他变量的内容，需要**加双引号**

set|grep myname
//output : myname=zxdddd

work=/Users/niko/work/handday/
cd $work
pwd //output : /Users/niko/work/handday
```

#### 8. 特殊符号
1. \* ：代表零个或多个字符或数字。
2. ? ：只代表一个任意的字符
3. \# ：这个符号在linux中表示注释说明的意思，即”#”后面的内容linux忽略掉。
4. \ ：转义字符，将后面的特殊符号（例如”*” ）还原为普通字符。
5. | ：管道符，前面多次说过，它的作用在于将符号前面命令的结果丢给符号后面的命令。这里提到的后面的命令，并不是所有的命令都可以的，一般针对文档操作的命令比较常用，例如cat, less, head, tail, grep, cut, sort, wc, uniq, tee, tr, split, sed, awk等等，其中grep, sed, awk为正则表达式必须掌握的工具，在后续内容中详细介绍。
6. $ ：除了用于变量前面的标识符外，还有一个妙用，就是和’!’结合起来使用。

```
ls test.txt 
test.txt
ls !$
ls test.txt
test.txt

```
‘!$’表示上条命中中最后一个变量（也许称为变量不合适，总之就是上条命令中最后出现的那个东西）例如上边命令最后是test.txt那么在当前命令下输入!$则代表test.txt。

* grep ：过滤一个或多个字符
* cut ：截取某一个字段 -d ：后面跟分隔字符，分隔字符要用双引号括起来, -c ：后面接的是第几个字符, -f ：后面接的是第几个区块

* sort ：用做排序 -t 分隔符 ：作用跟cut的-d一个意思, -n ：使用纯数字排序, -r ：反向排序, -u ：去重复
* wc ：统计文档的行数、字符数、词数，常用的选项为：-l ：统计行数, -m ：统计字符数, -w ：统计词数
* uniq ：去重复的行，笔者常用的选项只有一个：-c ：统计重复的行数，并把行数写在前面

7. ：分号。平时我们都是在一行中敲一个命令，然后回车就运行了，那么想在一行中运行两个或两个以上的命令如何呢？则需要在命令之间加一个”;”了。
8. [ ] ：中括号，中间为字符组合，代表中间字符中的任意一个 

```
	zx:terminal_study niko$ ls
	ddd	error	text
	zx:terminal_study niko$ ls t*
	text
	zx:terminal_study niko$ ls [te]*
	error	text
	zx:terminal_study niko$ 

```

