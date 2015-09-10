---
layout: post
title:  "iOS style guide"
date:   2014-06-20 08:47:50
categories: ios

---

# 命名
## 0.文件命名
        Tip
        文件名须反映出其实现了什么类 – 包括大小写。遵循你所参与项目的约定。
    
类别的文件名应该包含被扩展的类名，如：GTMNSString+Utils.h 或``GTMNSTextView+Autocomplete.h``。

## 1. 变量命名

        Tip
        方法名应该以小写字母开头，并混合驼峰格式。每个具名参数也应该以小写字母开头。
    
变量命名需要能明白两点

* 变量意思
* 变量类型


### BOOL型
**以 ``is``开头**

如：

        //GOOD
        BOOL isShouldReload;
        BOOL isLoading;
        
        //AVOID
        BOOL k;
    

### Array 型
**以 ``s`` 结尾** 或者 `Array` 

如：

        NSArray *users;
        NSArray *messages
    

### Dictionary
以 `Dic` 结尾  或服务器返回对象

        NSDictionary *dateDic;
        NSDictionary *message;
    
    
### String
以 `String` 结尾 ，字段可以不用`String` 结尾

        NSString *urlString;
        
        @property (nonatomic,strong) NSString * topId;//尽量与服务器统一
    
    
### UI Class
**以 ``class`` 结尾** 尽量不使用`btn` `tv`等简写

如：

        //GOOD
        UIButton *loginButton
        UITextField *passwordTextField;
        
        //AVOID
        UIButton *login;
        UITextField *password;
    
### Block 

以 `on` 开头

        typedef void(^OnCompletion)(API *, id value);
        typedef void(^OnFailed)(API *, id error);
        
        OnCompletion  onCompletion;
        OnFailed      onFailed;


## 2. 方法命名
*fds*  
