---
layout: post
title: "shell note 2 coding"
description: ""
category: 
tags: []
---


#search file in dir

```
find . | grep 'keyword'
find . | grep 'keyword' | xargs open #open grepped file
```

#logical

1. 字符串判断

表达式|逻辑
---------|-------------
str1 = str2　　|　　当两个串有相同内容、长度时为真 
str1 != str2　 |　　当串str1和str2不等时为真 
-n str1　　　　 |　 当串的长度大于0时为真(串非空) 
-z str1　　　　 |　 当串的长度为0时为真(空串) 
str1　　　　　　|　   当串str1为非空时为真

2. 数字的判断

表达式|逻辑
---------|-------------
int1 -eq int2　|　　两数相等为真 
int1 -ne int2　|　　两数不等为真 
int1 -gt int2　|　　int1大于int2为真 
int1 -ge int2　|　　int1大于等于int2为真 
int1 -lt int2　|　　int1小于int2为真 
int1 -le int2　|　　int1小于等于int2为真

3. 文件的判断

表达式|逻辑 
---------|-------------
-r file　　|　　用户可读为真 
-w file　　|　　用户可写为真 
-x file　　|　　用户可执行为真 
-f file　　|　　文件为正规文件为真 
-d file　　|　　文件为目录为真 
-c file　　|　　文件为字符特殊文件为真 
-b file　　|　　文件为块特殊文件为真 
-s file　　|　　文件大小非0时为真 
-t file　　|　　当文件描述符(默认为1)指定的设备为终端时为真

4. 复杂逻辑断
 
表达式|逻辑
---------|-------------
-a 　 　|　　 与 
-o　　　|　　 或 
!　　　　|　　非

eg. 

```
if [ $# -eq 0 ]
  then
    echo "No arguments supplied"
fi
# variable will tell you the number of input arguments the script was passed
```

```
if [ -z "$1" ]
  then
    echo "No argument supplied"
fi
#The -z switch will test if the expansion of "$1" is a null string or not. If it is a null string then the body is executed.
```

#file
[ -f "filepath" ] ：判断是否是一个文件 
[ -d "folerpath" ] ：判断是否是一个文件夹 
