---
layout: post
title: "osx下crossover安装YY语音小记"
date: 2014-03-15 16:37:03 +0800
comments: true
categories: 技术
---

##前言
因工作关系需要用到YY语音。但这个工具目前并未有计划发布mac版本程序。在网上搜索了一下，曾经有过用CrossOver跑YY语音成功的案例，更奇特的是淘宝还有卖for mac 的YY语音安装包。那么这里尝试最新版本的CrossOver (v13.1)跑YY语音(v6.19)版本。

##准备工作
* 下载**CrossOver**,可去[官网][1]下载试用版，有钱的话就购买正式版吧，暂时没条件就去Google找一个。
* 下载**YY语音**,这个是免费软件，也直接去[官网][2]下载即可。

##安装工作
* 先把**CrossOver**安装到系统中。打开程序后，在菜单中选择`容器管理`,建立一个基本***windows XP***的容器。
* 然后选择容器旁边的`应用程序`的tab页，点击`安装软件`的按钮。选择`运行时支持的组件`里，把***Microsoft Visual C++ 2008(9.0)Redistributable***安装上。
![add-box](https://www.dropbox.com/sh/0zua8qozujowahf/GDT_1Bzjkr/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202014-03-15%2000.30.19.png?dl=1)
* 准备好***YY语音***的安装程序，仍然是`CrossOver软件安装程序`界面里，点选`不支持的程序`下一级`其他应用程序`. 然后在`选择一个程序安装包`里点击`选择安装文件`，把***YY语音***安装程序文件选择上。并在下一行留意到所安装容器。点`执行`即可安装。
![install-vc++](https://www.dropbox.com/s/e4y682c19b7kma4/屏幕截图%202014-03-15%2000.30.36.png?dl=1)
![install-YY](https://www.dropbox.com/sh/0zua8qozujowahf/bIDv4Gvk92/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202014-03-15%2000.31.04.png?dl=1)
* 之后程序基本上就正常执行了。目前只尝试了基本操作。
![installing](https://www.dropbox.com/sh/0zua8qozujowahf/qyX9Wny7ne/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202014-03-15%2000.31.30.png?dl=1)

##美化工作
默认的***CrossOver***模拟出来的程序界面中文字体太虚，看不清。因此可以进行字体替换工作。
	
	cd /Applications/CrossOver.app/Contents/SharedSupport/CrossOver/share/wine/fonts

在这个目录下，把你需要的字体复制成ume-ui-gothic.ttf即可，实际上我尝试了一下，目前只有simsum.ttf的替换效果比较好。
	
	cp simsum.ttf /Applications/CrossOver.app/Contents/SharedSupport/CrossOver/share/wine/fonts/ume-ui-gothic.ttf

最后重启CrossOver即可看到相关效果。

![YYinOSX](https://www.dropbox.com/s/312qarmc37nejiu/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202014-03-15%2000.37.48.png?dl=1)





[1]: http://www.codeweavers.com/products/
[2]: http://www.yy.com/s/download.html
