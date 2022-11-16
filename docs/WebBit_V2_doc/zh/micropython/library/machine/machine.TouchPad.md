类 TouchPad -- 触摸
=============================


构建对象
------------

```python
class TouchPad(Pin)
```

创建与设定引脚关联的TouchPad对象。

- ``Pin`` 可用引脚有：``GPIO4``、``GPIO0``、``GPIO2``、``GPIO15``、``GPIO13``、``GPIO12``、``GPIO14``、``GPIO27``、``GPIO33``、``GPIO32``。有关更多信息，请查看[ESP32 系列芯片技术规格书](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_cn.pdf) 中有关ESP32引脚功能的内容。
 

示例:

```python
from machine import TouchPad, Pin

tp = TouchPad(Pin(14))
```

``TouchPad.read`` 返回相对于电容性变量的值。当触摸时，是个较小数字(通常在 *10* 内)，当没有触针时，是较大数字(大于 * 1000 *)是常见的。然而，这些值是“相对的”，可以根据电路板和周围不同而变化，因此可能的需要进行一些校准。

有10个电容触摸控脚,如果调用其他的引脚将会导致 ``ValueError`` 。

方法
---------

```python
TouchPad.read()
```

读取TouchPad的电平。

```python
TouchPad.config(value)
```

设置触摸的阈值

- ``value`` 整数