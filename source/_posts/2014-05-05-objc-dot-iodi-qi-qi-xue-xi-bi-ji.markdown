---
layout: post
title: "objc.io第七期学习笔记"
date: 2014-05-05 08:57:42 +0800
comments: true
categories:  程序设计
---

objc.io出品，必属精品，我等ios开发人员必当仔细研习之。尤其第七期讲的是平时常用的基础类，获益良多，怕忘之，因此记录一下所得。
放URL，第七期地址，可参看[中文版objccn.io的出品][1]

***NSArray***

第一小章讲基础集合类。
我有个意外所得就是关于三元操作符?:的，竟然可以这么用。

```
NSMutableArray *mutableObjects = [array mutableCopy] ?: [NSMutableArray array];

```

省略掉中间那个表达示的话，即可如真则返回自己。后来找了下，GNU C也有此扩展。但也有某处说到这是不良的代码风格，但我实在太喜欢这个写法了。

```
NSMutableArray *mutableObjects = [NSMutableArray arrayWithArray:array];
```
arrayWithArray这个方法，如果传入的是nil也可以生成一个空的NSMutableArray，这是个保险的用法。

可变与不可变的问题，记住copy永远返回不可变的，性能上来说尽量用不可变的集合。
说到copy的问题，对于不可变的对象，copy与strong/retain一样，没有额外的消耗，因此NSString要大胆用。

arrayWithCapacity这方法没有太大必要使用.

至于其它排序与查找的方法，目前用的不多，用到的时候再来查。

***NSSet***

无序，唯一集合。

***NSIndexSet***

存储无符号整数的集合。
之前我还一直把整数转成NSNumber存到NSArray里，有这个就比较方便，不过个集合的成员不能有重复


***值对象***

自己生成的对象要存到上面那些集合里(NSArray,NSDictionary...)，最好要判等，则要实现两个方法, isEqual: 和 hash
很明显isEqual:是用来比较两个对象是否相等。实现hash是为了性能上的问题吧。

然后为了能序列化，要实现NSCodeing接口。为了能copy 则实现NSCopying接口。












[1]:http://objccn.io/issue-7-1/
