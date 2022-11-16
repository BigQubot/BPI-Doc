刷入 MicroPython 固件
=====================

第一次使用，请先烧入 MicroPython 固件，如果不烧录就没有 MicroPython编程环境。

> 使用请确认已经安装驱动，且已经得知自己的硬件串口名称，例如：COM5、ttyUSB0。

在 Windows 下
-------------

-   从[BPI-BIT-MicroPython/release](https://github.com/BPI-STEAM/BPI-BIT-MicroPython/releases/tag/FlashTool)中获取烧写工具的链接，附有国内微云网盘分流。
-   下载后打开 FlashMicroPython-\*.zip 压缩包，然后运行里面的Flashtool.exe 工具即可。

![](../../assets/micropython/basic/flash_mpy/flash_mpy.png)

-   请先插入硬件后打开软件，这个软件会自动运行烧写，你也可以直接点击 Flash 按钮烧写。
-   你也可以自己选择串口烧录，升级固件只需要替换压缩包中的 firmware.bin 重新烧入即可。

在其他系统下
--------------

请参照其他网络教程，如果有特别的需求，可以到 社区 提交问题 或 开 issue。

> 有问题可以到 [中文社区](https://forum.banana-pi.org.cn/c/bpi-bit)反馈。
