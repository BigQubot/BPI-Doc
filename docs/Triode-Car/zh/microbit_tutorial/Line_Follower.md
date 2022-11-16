# 巡线行驶

## 设计思路

在[校准巡线检测电路](LDR_calibration.html)之后，我们即可开始对巡线检测电路进行有效利用。

根据[硬件的浅析与调试](../hardware/analysis&calibrate.html)中所介绍的原理，巡线需要利用线路与其两侧路面对光线不同的反射率进行实时的光照强度检测，在程序中读取左右两个光敏电阻的电压模拟值，对数值进行比对，以此判断Triode-Car行进路线是否发生偏移以及偏移方向，进而对左右两个电机的启停进行控制，修正Triode-Car的行驶方向，达成沿着线路行驶的目的。

## 例程

<div align=center>
<img src="../assets/Triode-car_Line_Follower.png" width="600"/>
</div>

[在Github上的例程项目文件](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_Line_Follower.hex)

> 项目文件下载到本地后可导入MakeCode中查看和再编辑，也可直接通过USB烧录到Micro:Bit中运行。

## 设计说明

1. "on button A pressed"积木用于控制循迹程序的启动和停止，每按一次按钮A，其中设置的变量就会改变一次状态。
2. "forever"积木将重复执行其内部的程序，每次循环结束或在循环中执行到"show"或1. "pause"积木时会让出线程允许其他的"forever"积木或事件处理程序运行，所以此处三个"forever"积木与一个"on button A pressed"积木可以共同在后台运行，这样使系统具备同时执行多个程序的能力，一般将此称作“多工”。
3. 第一个"forever"积木内的程序用于循环读取左右两个光敏电阻电压模拟值，然后在多级"if"条件积木中进行判断，满足相应条件时改变变量，该变量用于控制电机。
4. 第二个"forever"积木内的多级"if"条件积木对第一个"forever"积木内改变的变量值进行判断，直接输出控制信号来控制左右电机的启停和转速。
5. 第一，二个"forever"积木内的循环条件即为"on button A pressed"积木控制的变量，变量为"true"值时才会循环执行。
6. 第三个"forever"积木略有巧思，其内部的循环仅在用于控制电机的变量发生变化时才会执行一次，对应改变LED当前应当显示的内容。