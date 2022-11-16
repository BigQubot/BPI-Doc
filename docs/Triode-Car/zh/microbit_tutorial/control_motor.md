# 用microbit按钮控制电机

## 例程

<div align=center>
<img src="../assets/Triode-Car_motor_control_1.png" width="300"/>
</div>

[在Github上的例程项目文件](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_motor_control_1.hex)

> 项目文件下载到本地后可导入MakeCode中查看和再编辑，也可直接通过USB烧录到Micro:Bit中运行。

## 设计说明

1. 启动或复位时停车。
2. 同时按下AB按钮直行。
3. 按下A按钮右转。
4. 按下B按钮左转。

在[硬件浅析与调试：驱动电路](../hardware/analysis&calibrate.html#驱动电路)中后半部分有提到，驱动电路中有设计一个切换开关，可以将驱动电路由LM393电压比较器控制切换到由micro:bit控制。而micro:bit控制驱动电路的方法，和LM393电压比较器相同，低电平启动，高电平停止。