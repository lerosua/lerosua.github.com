---
layout: post
title: "命令行的世界"
date: 2014-08-06 22:57:51 +0800
comments: true
categories: 程序
---

在公司里给校招的同事普及一些知识，第一讲是一些命令行的知识，下面是大纲讲义。

#命令行的世界  -从另一角度了解系统

命令行里所见内容，输入输出都经由shell，它是我们和系统打交道的窗口。

##文件系统
###分区概念
一个磁盘分完区后，在windows中会看见C,D,E之类的盘符，而在UNIX类系统中，分区都挂在/目录下面

了解GUI里看到的文档在命令行中的表现形式
###了解一些特定目录

- 根目录 /
- 家目录 ~
- 当前目录 .
- 上级目录 ..

使用cd跳转，pwd查看当前所在
常见的目录

- /tmp 临时目录
- /bin 		shell存放的命令的目录
- /usr/bin/  	用户存放的命令目录
- /dev 	   	设备目录
- /sbin 	系统级命令目录
- /etc 		系统配置文件目录
- /Applications osx放app的目录
- /Users 	osx存放各用户的目录

###查看当前目录下所有内容

- ls 列出目录里的内容
- cat 打印出文件内容

###了解文件
- UNIX的角度，一切皆文件
- 以人类视角看文件，可分为文本文件，二进制文件. shell能自动化操纵所有文本文件。
- 权限的角度看文件, 分为可读r，可写w，可执行x
```
ls -l
```

- 文件的类型
```
	b     Block special file.
	c     Character special file.
	d     Directory.
	l     Symbolic link.
	s     Socket link.
	p     FIFO.
	-     Regular file.
```

###操作文件

- 新建文件, 用编辑器新建，用重定向新建，用touch新建
- 新建目录, mkdir
- 删除文件/目录, rm
- 复制文件/目录, cp
- 移动文件/目录，mv

###文件编辑
*vim* VS *Emacs*
####vim基本用法
- vim的两种基本模式，编辑模式和命令模式, 通过ESC切换到命令模式

##### 命令模式
- 打命令 :wq 即保存退出
- 查找命令，向下查找/ 向上查找?
- 移动, hjkl 左下上右,  gg 页首, G页尾,  0 行首，$行尾

##### 编辑模式
- 进入  a A i I o O
- 删除 ctrl+w 



##命令
shell内建命令集，GNU工具集，第三方工具集

- 查看命令的帮助
```
	man cat
```
- 命令的内建帮助
```
	cat --help
```
- 查看上条命令的返回得知执行结果
```
	$cat --help
	$echo $?
```
- 查看命令的历史
```
	history
```

###提升效率 - [shell里的快捷键](https://linuxtoy.org/archives/bash-shortcuts.html)

####编辑命令
- Ctrl + a ：移到命令行首
- Ctrl + e ：移到命令行尾
- Ctrl + f ：按字符前移（右向）
- Ctrl + b ：按字符后移（左向）
- Alt + f ：按单词前移（右向）
- Alt + b ：按单词后移（左向）
- Ctrl + xx：在命令行首和光标之间移动
- Ctrl + u ：从光标处删除至命令行首
- Ctrl + k ：从光标处删除至命令行尾
- Ctrl + w ：从光标处删除至字首
- Alt + d ：从光标处删除至字尾
- Ctrl + d ：删除光标处的字符
- Ctrl + h ：删除光标前的字符
- Ctrl + y ：粘贴至光标后
- Alt + c ：从光标处更改为首字母大写的单词
- Alt + u ：从光标处更改为全部大写的单词
- Alt + l ：从光标处更改为全部小写的单词
- Ctrl + t ：交换光标处和之前的字符
- Alt + t ：交换光标处和之前的单词

####重新执行命令

- Ctrl + r：逆向搜索命令历史
- Ctrl + g：从历史搜索模式退出
- Ctrl + p：历史中的上一条命令
- Ctrl + n：历史中的下一条命令
- Alt + .：使用上一条命令的最后一个参数

####控制命令

- Ctrl + l：清屏
- Ctrl + o：执行当前命令，并选择上一条命令
- Ctrl + s：阻止屏幕输出
- Ctrl + q：允许屏幕输出
- Ctrl + c：终止命令
- Ctrl + z：挂起命令

####Bang (!) 命令

- !!：执行上一条命令
- !blah：执行最近的以 blah 开头的命令，如 !ls
- !blah:p：仅打印输出，而不执行
- !$：上一条命令的最后一个参数，与 Alt + . 相同
- !$:p：打印输出 !$ 的内容
- !*：上一条命令的所有参数
- !*:p：打印输出 !* 的内容
- ^blah：删除上一条命令中的 blah
- ^blah^foo：将上一条命令中的 blah 替换为 foo
- ^blah^foo^：将上一条命令中所有的 blah 都替换为 foo


###行处理
sed awk grep sort uniq perl

- awk (模式匹配文本处理)简单演示
```
	ls -l | awk '{print $1}'
```

- sed (流编辑器)简单演示
```
	ls -l | sed 's/Users/Home/'
```
- grep (匹配行输出)简单演示
以下会在file.txt里输出包含apple的行
```
	grep "apple" file.txt 
```

###重定向概念与管道
- 命令行的默认输出是我们所见的终端，然则可以通过重定向 符号 > 来将输出定向到一个文件里,但注意每次重定向都会重写那个文件
- 重定向符号 >> 是增量输出,与上面的区别在于不会重写文件，是在原文件后面写入内容
- | 是管道符号，是命令之间流通的桥樑。
```
	ls -l |awk '{print $1}'
```
	上面命令中，ls的输出给了管道，awk的输入是从管道中取得。


###其它一些工具
- wget 命令行下载
- tar 命令行压缩工具tar cvfz xxx.tar.gz xxx, tar xvfz xxx.tar.gz
- ssh 远程登录服务器工具 

***当我们熟悉掌握一些命令，并能将之组合起来使用的时候，写在一个文件里，就是一个脚本了***





##关于系统的一些操作

- ps ax		查看系统进程
- top		实时查看系统状态
- df -h 	查看磁盘信息
- ifconfig 	查看网络状态
- kill num	杀死进程号为num的进程

##命令行下面编程

了解IDE所为我们所做的事情

- 1.编辑源码, vim之类写入代码
- 2.预处理源代码
```
gcc -E t.c  默认输出内容到终端
```
- 2.编译成汇编
```
gcc -S t.c    生成t.s
```
- 3.编译成目标文件 
```
gcc -c t.s   生成t.o
```
- 4.链接器链接需要的库生成最终的可执行文件 
```
ld -arch x86_64 -lSystem /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/../lib/clang/5.1/lib/darwin/libclang_rt.osx.a t.o -macosx_version_min 10.8  -o  mypro
```


当然命令行也有智能的方式，甚至如果涉及到跨平台，命令行里的解决方案会比IDE方便。
GNU构建系统Autotools, QT构建系统qmake, 跨平台构建系统CMake
