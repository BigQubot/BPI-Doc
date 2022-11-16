# 无线电通讯控制电机

## 例程

<div align=center>
<img src="../assets/Triode-Car_radio_control_1.png" width="400"/>
</div>

[在Github上的例程项目文件](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-Car_radio_control_1.hex)

> 项目文件下载到本地后可导入MakeCode中查看和再编辑，也可直接通过USB烧录到Micro:Bit中运行。

## 设计说明

micro:bit支持无线电通讯，在MakeCode中应用无线电扩展积木进行编程，并将程序下载进两块micro:bit后，即可在二者之间建立无线通讯，并可相互控制对方的硬件。

将例程下载进两块micro:bit，一块插在Triode-Car上，一块拿在手上，两块都接通电源，即可通过手上的micro:bit的按钮AB控制Triode-Car的电机启停。

按A左转，按B右转，同时按下AB直行，松开即停车。

其中加入的四个变量并非多余的存在，虽然也可以在积木中填上我们所需要的数值，但使用变量名来代替这些指定的数值有利于我们在认知上建立更清晰的逻辑，在越复杂的程序中越能体现其价值。