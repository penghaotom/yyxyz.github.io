---
layout: post
title:  "Vim配置及插件安装自动化脚本"
category: ubuntu
date:   2018-01-02 14:01:00
categories: ubuntu 

---

https://zhuanlan.zhihu.com/p/28795673
### Vim配置及插件安装自动化脚本

[原文链接：Vim配置及插件安装自动化脚本 in wangzhike.github.io](https://wangzhike.github.io/posts/8f8a9ec7/)
## 1. 简介

半年之前，我大概花了一周的时间折腾Ubuntu环境下的Vim，可能有人还不清楚，Ubuntu自带的~~vim~~vi，是vim的tiny版本，之所以预装这个tiny版本，是因为它足够小，而且能够满足一般的编辑需求，但是该tiny版本不能使用小键盘和方向键，这就造成了一个令人发狂的问题：在编辑模式下，移动光标会变成A B C D等字符并换行，而不是原来的上下左右移动，相信这个问题会让许多人和我一样困扰！

所以配置Vim的过程踩了许多坑，第一个就是卸载这个tiny版本的vim，安装完整的vim，之后是在自己的HOME目录建立自己的配置文件.vimrc，以及添加显示行号，语法高亮等基本配置，再到后面知道可以用Vundle插件管理工具安装各种插件，用Vim打造出类似IDE的开发环境......，不断往.vimrc中添加各种配置，折腾起来就是大半天，而

且换台机器，还得重新来一次，简直是累觉不爱。

最近在看shell编程，就萌生出写一个自动化脚本，完成在一个新的Ubuntu系统的机器上Vim的配置及插件安装工作，经过几天的努力，终于这个小脚本诞生了！

| 适用环境 | 脚本地址 |
| ------  | ----- |
| Ubuntu |[Wangzhike/VimConfigScript](https://github.com/Wangzhike/VimConfigScript) |
    
    

注：以上适用环境都已经过验证！

无图无真相，最终的效果见下图：

![](https://github.com/Wangzhike/VimConfigScript/raw/master/Ubuntu%20Vim.png)

2. 安装
2.1 克隆脚本
```
$ git clone https://github.com/Wangzhike/VimConfigScript.git
```

2.2 安装脚本

目前脚本自动安装的插件有：
```
自动补全插件YouCompleteMe
语法检查插件syntastic
代码折叠插件SimpylFold
显示文件树/文件目录插件NERDTree
状态栏增强插件vim-airline
查看显示代码文件中的宏，函数，变量定义等的插件taglist
```

安装：

1. 进入脚本所在目录

$ cd VimConfigScript

2. 执行脚本 `./configVim.sh`

目前脚本支持三种命令行参数：

    `./configVim.sh -all`或`./configVim.sh`

会安装上面提到的所有插件

    `./configVim.sh -s [Plugin1] [Plugin2] ... [PluginN]`

会安装`-s`后面指定的插件，插件名字之间以空格分隔

    `./configVim.sh -v [Plugin1] [Plugin2] ... [PluginN]`

除了`-v`后面指定的插件外，安装上面提到的所有插件

注：

插件名称列表如下：
```
YouCompleteMe
Syntasitic
SimplyFold
NERDTree
AirLine
Taglist
```

举例：

只安装Syntastic SimplyFold Taglist插件
```
$ ./configVim.sh -s Syntastic SimpylFold Taglist
```
2. 安装除了YouCompleteMe以外的所有插件
```
$ ./configVim.sh -v YouCompleteMe
```

欢迎各位试用以及改进，如有问题可以评论留言，一起努力打造更好用的Vim环境。

