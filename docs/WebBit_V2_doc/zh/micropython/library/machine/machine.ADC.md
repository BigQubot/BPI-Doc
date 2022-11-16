类 ADC -- 模数转换
=========================================

构建对象
------------

```python
classADC(Pin)
```
创建与设定引脚关联的ADC对象。这样您就可以读取该引脚上的模拟值。

- ``Pin``  ADC在专用引脚上可用，ESP32可用引脚有： ``GPIO36`` / ``ADC1_CH0`` 、``GPIO39`` / ``ADC1_CH3`` 、``GPIO34``/``ADC1_CH6``、``GPIO35``/``ADC1_CH7``、``GPIO32``/``ADC1_CH4``、``GPIO33``/``ADC1_CH5``，可测电压范围为0~3.3V。有关更多信息，请查看[ESP32 系列芯片技术规格书](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_cn.pdf) 中有关ESP32引脚功能的内容。

示例:

```python
from machine import ADC, Pin

adc = ADC(Pin(33))     # create an ADC object
```

方法
-------

```python
ADC.read( )
```

读取ADC并返回读取结果，返回的值将在0到4095之间。




```python
ADC.atten(db)
```

 设置衰减比（即满量程的电压，比如11db满量程时电压为3.3V）,默认为``ADC.ATTIN_0DB``。

- ``db``：衰减比, ``ADC.ATTIN_0DB`` 、``ADC.ATTN_2_5_DB``、``ADC.ATTN_6DB``、``ADC.ATTN_11DB``


```python
ADC.width(bit)
```

 设置数据宽度

- ``bit``： ``ADC.WIDTH_9BIT`` 、 ``ADC.WIDTH_10BIT`` 、 ``ADC.WIDTH_11BIT`` 、 ``ADC.WIDTH_12BIT``



示例:

```python
from machine import ADC, Pin

adc = ADC(Pin(34))     # create an ADC object
adc.atten(adc.ATTN_11DB)   # set 3.3V Range
x = adc.read()
print(x)
```

常量
---------


衰减比

```python
ADC.ATTN_0DB
```

等于0,满量程：1.2v

```python
ADC.ATTN_2_5DB
```

等于1,满量程：1.5v

```python
ADC.ATTN_6DB
```

等于2,满量程：2.0v

```python
ADC.ATTN_11DB
```

等于3,满量程：3.3v


数据宽度

```python
ADC.WIDTH_9BIT
```

等于0，9位数据宽度， 即满量程0x1ff(511)

```python
ADC.WIDTH_10BIT
```

等于1，10位数据宽度， 即满量程0x7ff(2047)

```python
ADC.WIDTH_11BIT
```

等于2，11位数据宽度， 即满量程0x3ff(1023)

```python
ADC.WIDTH_12BIT
```

等于3，12位数据宽度， 即满量程0xfff(4095)





