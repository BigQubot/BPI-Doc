Python 标准库
===========

标准的Python库被 “微型化”后，就是micropython标准库。它们仅仅提供了该模块的核心功能。一些模块没有直接使用标准的Python的名字，而是冠以"u"，例如 ``ujson`` 代替 ``json`` 。也就是说micropython标准库（=微型库），只实现了一部分模块功能。
通过他们的名字不同，用户有选择的去写一个Python级模块扩展功能，也是为实现更好的兼容性。。

在嵌入式平台上，可添加Python级别封装库从而实现命名兼容CPython，微模块即可调用他们的u-name，也可以调用non-u-name。
根据non-u-name包路径的文件可重写。

例如，``import json`` 的话，首先搜索一个 ``json.py`` 文件或 ``json`` 目录进行加载。
如果没有找到，它回退到加载内置 ``ujson`` 模块。

> CPython是用C语言实现的Python解释器，也是官方的并且是最广泛使用的Python解释器。除了CPython以外，还有用JAVA实现的Jython和用.NET实现的IronPython，使Python方便地和JAVA程序、.NET程序集成。另外还有一些实验性的Python解释器比如PyPy，使用Python再把Python实现了一遍。
> CPython是使用字节码的解释器，任何程序源代码在执行之前先要编译成字节码。它还有和几种其它语言（包括C语言）交互的外部函数接口。
> [Python标准库文档](https://docs.python.org/zh-cn/3/library/index.html) - CPython文档

- builtin – 内建函数
- array – 数值数组
- gc – 回收内存碎片
- math – 数学运算函数
- sys – 系统特定功能
- ubinascii – 二进制/ ASCII转换
- ucollections – 容器数据类型
- uerrno – 系统错误代码
- uhashlib – 散列算法
- uheapq – 堆队列算法
- uio – 输入/输出流
- ujson – JSON 编码和解码
- os – 操作系统
- ure – 正则表达式
- select – 等待流事件
- usocket – socket 模块
- ussl – SSL/TLS 模块
- ustruct – 打包和解压缩原始数据类型
- time – 时间相关函数
- uzlib – zlib解压缩
