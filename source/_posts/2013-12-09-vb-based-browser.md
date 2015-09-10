---
layout: post
title:  "vb based browser"
date:   2013-12-09 16:06:50
categories: vb

---
参考视频教学 [youtube](https://www.youtube.com/watch?v=48Wjvd1vQ4U)

需要两个三方库 sourceCode
[ChromeBasedWebBrowser.rar](http://www.dasdoc.com/uploads/origin/201312/091920306.rar)
,[xulrunner-1.9.en-US.win32.zip](http://ishare.iask.sina.com.cn/f/63101622.html?sudaref=www.baidu.com&retcode=0)

1，新建一个class 继承 `Skybound.Gecko.GeckoWebBrowser`

	Imports Skybound.Gecko
	Public Class FasterBrowser
	    Inherits GeckoWebBrowser
	End Class

2，在ui 上加入 new class

3，

	Imports Skybound.Gecko
	
	Public Class Form1
	
	    Sub New()
	        InitializeComponent()
	
	        Xpcom.Initialize(Environment.CurrentDirectory + "lrunner")
	
	
	    End Sub
	
	    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
	        FasterBrowser1.Navigate("http://www.zmaitech.com")
	    End Sub
	
	End Class