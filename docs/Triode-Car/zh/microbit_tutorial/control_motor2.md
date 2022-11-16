# 调整电机转速

## 例程

<div align=center>
<img src="../assets/Triode-Car_motor_control_2.png" width="500"/>
</div>

[在Github上的例程项目文件](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_motor_control_2.hex)

> 项目文件下载到本地后可导入MakeCode中查看和再编辑，也可直接通过USB烧录到Micro:Bit中运行。

## 设计说明

1. 按一次A按钮转速加1档
2. 按一次B按钮转速减1档
3. micro:bit显示当前挡位数值。

Triode-Car专用扩展积木中有可单独控制左右电机转速的积木，可进行10级调速。

例程中"forever"积木会在"on start"积木执行完后开始无限循环执行其内部的积木，而在每次循环的间隙则可执行其他事件处理程序，如on button A/B pressed。

加入了一个"if"判断积木，若变量"speed"值小于0或大于10时，将变量"speed"值设为0，这样可以将值限定在0到10范围内不会溢出而报错。