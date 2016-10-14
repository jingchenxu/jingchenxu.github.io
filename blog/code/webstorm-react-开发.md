---
title: webstorm react 开发
date: 2016-08-03 20:22:20
tags:
- 编程
- webstorm
description: mac 系统下webstorm搭建react开发遇到的坑
---

## 背景

设计同时开始兼职前端开发，也要搭建react的开发环境，问题就在于同事的电脑是mac的，所以在环境的搭建中遇到了一些问题，在这里记录下，等哪天自己有钱买mac了，可以翻回来看看。

## 开始

bower下安装sementic等包，首先第一个不同的地方就在于命令是不同的，首先要记住的是在命令的签名添加sudo，首先是遇到这样的错误：

``` bash
ECMDERR Failed to execute "git ls-remote --tags --heads git://github.com/twbs/bootstrap.git", exit code of #128
```
出现了这样的错误，我一开始是以为被墙了的原因，后来试了一下网上的解决方案，还是不行，在运行bower时间看到需要安装的是一下的内容


``` bash
bower cached        https://github.com/sachinchoolur/lightslider.git#1.1.5
bower validate      1.1.5 against https://github.com/sachinchoolur/lightslider.git#^1.1.5
bower cached        https://github.com/jquery/jquery-dist.git#2.1.4
bower validate      2.1.4 against https://github.com/jquery/jquery-dist.git#~2.1.0
bower cached        https://github.com/twbs/bootstrap.git#3.1.1
bower validate      3.1.1 against https://github.com/twbs/bootstrap.git#~3.1.0
bower cached        https://github.com/Semantic-Org/Semantic-UI.git#2.1.8
bower validate      2.1.8 against https://github.com/Semantic-Org/Semantic-UI.git#^2.1.8
bower ECMDERR       Failed to execute "git ls-remote —tags —heads https://github.com/jquery/jquery-dist.git", exit code of #128 fatal: unable to access 'https://github.com/jquery/jquery-dist.git/': Failed to connect to github.com port 443: Operation timed out
```

一看以为是自己被墙了，拨了vpn,试了一下还是不行，这时候我想还是不折腾了，换个开发环境还是这么蛋疼，想到了以前自己搭建安卓开发环境的时候也是各种的蛋疼，很多的sdk什么的都需要翻墙才能下载，所以很多的时候都是直接把别人下载好的东西拷过来就好了，我想我自己的Windows下就有下载好的啊！然后我就把我自己电脑上对应的这些东西拷给同事了，你以为我还会去研究具体的原因，不会的，因为我困了。

弄完这个之后，需要在webstorm中配置node服务器，配置好了以后出现了如下的问题：

``` bash
events.js:72
        throw er; // Unhandled 'error' event
              ^
Error: listen EADDRINUSE
    at errnoException (net.js:904:11)
    at Server._listen2 (net.js:1042:14)
    at listen (net.js:1064:10)
    at Server.listen (net.js:1138:5)
    at Object.<anonymous> (F:\socket\index.js:9:6)
    at Module._compile (module.js:456:26)
    at Object.Module._extensions..js (module.js:474
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Function.Module.runMain (module.js:497:10)
```

网上一搜果然有很多这样的问题，原因就是你开启服务器设置的端口被占用了，我设置的是80端口，我看完之后就用81试了一下，同事的电脑80、81都被占用了，我就还是怀疑人生，后来幸好测试了8181端口，行了。

## 结语

难得糊涂


