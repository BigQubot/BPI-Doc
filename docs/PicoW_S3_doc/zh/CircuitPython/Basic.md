# 基础功能使用

## REPL简单使用

###  Hello World!

1. 确保已在Mu编辑器中正确连接开发板，参考[配置使用环境(Mu编辑器)](config_mu-editor.md)。
2. 在CircuitPython REPL窗口中通常会出现如下信息，`>>>`符号的出现即代表我们可以开始在其后输入命令与其交互了。
```
]0;🐍Wi-Fi: off | Done | 8.0.0-beta.0-49-g14fc4a079\Auto-reload is on. Simply save files over USB to run them or enter REPL to disable.

Press any key to enter the REPL. Use CTRL-D to reload.
]0;🐍Wi-Fi: off | Done | 8.0.0-beta.0-49-g14fc4a079\]0;�Wi-Fi: off | REPL | 8.0.0-beta.0-49-g14fc4a079\
Adafruit CircuitPython 8.0.0-beta.0-49-g14fc4a079 on 2022-09-20; BPI-PicoW-S3 with ESP32S3
>>> 
```
3. 在`>>>`符号右侧开始输入命令，例如：`print("Hello World！")`。
> 注意使用英文输入法，中文字符无法被REPL识别。
```py
>>> print("Hello World!")
Hello World!
>>> 
```

### REPL快捷键

1. 复制 `ctrl + shift + c`。
2. 粘贴 `ctrl + shift + v`。
   使用鼠标左键在REPL中拖选需要复制的命令，键盘按下复制快捷键，再按下粘贴快捷键即可复制粘贴命令。
3. 软复位 `ctrl + d`。
4. 中断 `ctrl + c`, 中断当前正在执行的程序，但不会重启复位。

### 查看内置模块

1. 在REPL中输入 `help("modules")` 将列出当前CircuitPython开发板内所有模块。
2. 导入模块后可再使用`help()`函数查看该模块内部可用的函数名或变量名，例如查看`board`模块，即可看到开发板所有可用的引脚与外设功能。
```py
>>> import board
>>> help(board)
object <module 'board'> is of type module
  __name__ -- board
  board_id -- bpi_picow_s3
  GP0 -- board.GP0
  GP1 -- board.GP1
  GP2 -- board.GP2
  GP3 -- board.GP3
  GP4 -- board.GP4
  GP5 -- board.GP5
  GP6 -- board.GP6
  GP7 -- board.GP7
  GP8 -- board.GP8
  GP9 -- board.GP9
  GP10 -- board.GP10
  GP11 -- board.GP11
  GP12 -- board.GP12
  GP13 -- board.GP13
  GP14 -- board.GP14
  GP15 -- board.GP15
  GP16 -- board.GP16
  GP17 -- board.GP17
  GP18 -- board.GP18
  GP19 -- board.GP19
  GP20 -- board.GP20
  GP21 -- board.GP21
  GP22 -- board.GP22
  GP25 -- board.GP25
  LED -- board.GP25
  GP26 -- board.GP26
  GP26_A0 -- board.GP26
  A0 -- board.GP26
  GP27 -- board.GP27
  GP27_A1 -- board.GP27
  A1 -- board.GP27
  GP28 -- board.GP28
  GP28_A2 -- board.GP28
  A2 -- board.GP28
  GP29 -- board.GP29
  GP29_A3 -- board.GP29
  A3 -- board.GP29
  NEOPIXEL -- board.NEOPIXEL
  TX -- board.GP0
  RX -- board.GP1
  BOOT0 -- board.BOOT0
  UART -- <function>
>>> 
```

## 输出

### 使WS2812彩灯闪烁

1. 在Mu编辑器中点击**Load**按钮，选择CircuitPython开发板上的 code.py 文件，点击 **打开**，即可开始编辑 code.py 。

2. 在编辑器中输入如下代码：

```python
import time
import board
import neopixel

pixels = neopixel.NeoPixel(board.NEOPIXEL, 1, brightness=0.1)

while 1:
    pixels[0] = (255,0,0)
    pixels.show()
    time.sleep(0.5)
    pixels[0] = (0,255,0)
    pixels.show()
    time.sleep(0.5)
    pixels[0] = (0,0,255)
    pixels.show()
    time.sleep(0.5)
    pixels[0] = (255,255,255)
    pixels.show()
    time.sleep(0.5)
```

3. 点击**Save**按钮，编辑的内容将保存到CircuitPython开发板，代码无误的情况下，开发板上的彩色LED将循环闪烁 红绿蓝白。将开发板复位或重新上电，程序将重新开始运行。
4. 在REPL中使用中断快捷键即可停止程序的运行。
5. 代码也可直接复制粘贴到REPL中运行。

> 后续所有示例都可如此编辑code.py文件或复制粘贴到REPL中运行。但在code.py文件中的程序代码执行完毕后，开发板会恢复未运行时的状态，不会保留状态，但在REPL中执行则会保留状态。

### 使引脚输出高低电平，控制LED

1. `board.LED`控制着PicoW-S3上的一颗单色LED发光二极管，高电平点亮，低电平熄灭，在REPL中输入以下代码：
```py
import board
import digitalio
ledpin = digitalio.DigitalInOut(board.LED)
ledpin.direction = digitalio.Direction.OUTPUT
ledpin.value = True
```

2. 或者这么做：
```py
import board
import digitalio
ledpin = digitalio.DigitalInOut(board.LED)
ledpin.switch_to_output(value=True) # value=1
```

3. 让LED间隔0.5秒闪烁：
```py
import board
import digitalio
import time
ledpin = digitalio.DigitalInOut(board.LED)
while True:
    ledpin.switch_to_output(value=1)
    time.sleep(0.5)
    ledpin.switch_to_output(value=0)
    time.sleep(0.5)

```
4. 在REPL中使用中断快捷键即可停止程序的运行。

5. 在REPL中输入`import board;help(board)`即可列出所有可控制的引脚。`board.GP25` 与 `board.LED`完全相同。

### PWM输出，控制LED亮度

1. 可通过控制PWM占空比来控制LED灯亮度，控制占空比从0%~100%，采用16位精度，十进制为 0~65535 ，16进制为 0~FFFF 。在REPL中输入以下代码：
```py
import board
import pwmio
ledpin = pwmio.PWMOut(board.LED, frequency=25000, duty_cycle=0)
ledpin.duty_cycle = 32768  # mid-point 0-65535 = 50 % duty-cycle
```
2. 仅需在REPL中再次输入最后一行代码即可改变PWM占空比，使LED达到最大亮度：
```py
ledpin.duty_cycle = 65535
```
3. 呼吸灯：
```py
import board
import pwmio
import time

ledpin = pwmio.PWMOut(board.LED, frequency=25000, duty_cycle=0)

while True:
    for i in range(0, 65535, 1):
        ledpin.duty_cycle = i
    for i in range(65535, 0, -1):
        ledpin.duty_cycle = i
```

## PWM输出，控制180度舵机

![](../assets/images/MG90S-Wiring-Diagram.jpg)

以MG90S舵机为例，其他各种舵机参考其对应的使用手册，在以下代码中修改相应的参数。

1. MG90S舵机关键参数：
   * 控制角度，0° ~ 180°
   * PWM 占空时长控制，500us ~ 2500us 对应 0° ~ 180°
   * 工作电压：4.8V 至 6V（典型值为 5V）
   * 失速扭矩：1.8 kg/cm (4.8V)
   * 最大失速扭矩：2.2 kg/cm (6V)
   * 工作速度为 0.1s/60° (4.8V)
2. 求取任意一个旋转角度所需的占空时长的表达式为：
   ```
    设y为占空时长，x为旋转角度
    y=(2500-500)/180*x+500
    y=(100*x+4500)/9
    ```
3. 根据参数，可以确定舵机角度由PWM波的高电平持续时长所控制，且由于舵机的控制必须由周期性的PWM波形控制，所以一个周期时长必须超过控制此舵机达到180°所需的占空时长，即超过2500us，则PWM频率要低于400hz。
4. 设定PWM频率为200hz，则周期时长为5000us，对应控制此舵机旋转 0° ~ 180°的占空比为10% ~ 50% 。
5. circuitpython的PWM占空比控制精度为16bit，100%占空比在 2进制中表达为 1111 1111 1111 1111，16进制表达为 FFFF，10进制表达为 65535。
6. 求取任意一个旋转角度所需的占空比的表达式为：
    ```
    设y为占空比，x为旋转角度
    y=((50-10)/180*x+10)/100*65535
    y=(4369*x+196605)/30
    ```
7. 舵机与BPI-PicoW-S3的接线方式:
   > BPI-PicoW-S3的VBS引脚可输出+5V；除GP0以外，所有GP引脚都可以用于输出PWM，仅需在程序中修改到对应引脚即可。

| 舵机 | BPI-PicoW-S3 |
| :----: | :----: |
| GND 棕色 | GND |
| +5V 红色 | VBS |
| PWM 橙色 | GP0 |


8. 根据以上表达式与参数设计一个可以任意控制此舵机旋转角度的程序：
    ```py
    import board
    import pwmio
    import time
    servo_1 = pwmio.PWMOut(board.GP0, frequency=200, duty_cycle=0)#200hz, one cycle 5000us

    def get_duty_cycle(x):
        return int((4369*x+196605)/30)

    servo_1.duty_cycle = get_duty_cycle(90)# 90 degrees
    ```
9. 通过一个逻辑分析仪可以读出此程序所控制输出的PWM占空时长，与计算的数值应当相符。
   ![](../assets/images/MG90S_pulseveiw_2.png)
   ![](../assets/images/MG90S_pulseveiw_1.png)

10. 使用列表设计一套连续的舵机动作：
   ```py
   import board
   import pwmio
   import time
   servo_1 = pwmio.PWMOut(board.GP0, frequency=200, duty_cycle=0)#200hz, one cycle 5000us

   def get_duty_cycle(x):
       return int((4369*x+196605)/30) 

   action_list1 = [0,45,90,135,180,0,180,45,135,90]

   while True:
       for i in action_list1:
           servo_1.duty_cycle = get_duty_cycle(i)
           time.sleep(0.5)
   ```

## ADC输入，读取双轴摇杆坐标

![](../assets/images/Dual-axis_joystick.jpg)

这是一个常见的双轴XY摇杆模块，使用了两个电位器最为其核心器件，通过芯片的ADC 模/数转换器 读取它们各自的电压数值，即可将读数转化为其在XY坐标轴上的位置。

| 双轴摇杆 | BPI-PicoW-S3 |
| :----: | :----: |
| GND  | GND |
| +5V  | 3V3 |
| VRx  | GP26_A0 |
| VRY  | GP27_A1 |

1. 在CircuitPython中提供的ADC精度是16bit，即最大值的16进制表达为 FFFF，10进制表达为 65535，对应的电压量程为0mv ~ 3300mv。BPI-PicoW-S3所使用的EPS32S3芯片实际ADC电压量程为0mv ~ 3100mv，所以实际应用时仅能测量到3100mv。

2. 基础ADC读数，读取两个电位器的数值，转换为电压数值。
```python
import board,analogio,time

x_axis_pin = analogio.AnalogIn(board.A0)
y_axis_pin = analogio.AnalogIn(board.A1)

while True:
    x_axis = x_axis_pin.value
    y_axis = y_axis_pin.value
    # print((x_axis,y_axis))
    x_value = x_axis / 65535 * 3300
    y_value = y_axis / 65535 * 3300
    print("{0}mv,{1}mv".format(x_value,y_value))
    time.sleep(0.1)
```

3. 在Mu编辑器中，点击`Plotter`图标即可显示绘图仪，可以实时将REPL输出的数值显示为与时间相关的图表。
![](../assets/images/circuitpython_plotter.png)
   
4. 静止摇杆获取零点数值，校准坐标零点。
```python
import board,analogio,time

x_axis_pin = analogio.AnalogIn(board.A0)
y_axis_pin = analogio.AnalogIn(board.A1)

def get_zero(times =500, sleep = 0.01):
    x_total = 0
    y_total = 0
    for i in range (times):
        x_axis = x_axis_pin.value
        y_axis = y_axis_pin.value
        x_total += x_axis
        y_total += y_axis
        time.sleep(sleep)
    x_zero = x_total // times
    y_zero = y_total // times
    return (x_zero,y_zero)

zero = get_zero(times =500, sleep = 0.01)
print(zero)

while True:
    x_axis = x_axis_pin.value - zero[0]
    y_axis = y_axis_pin.value - zero[1]
    print((x_axis,y_axis))
    time.sleep(0.1)
```
4. 获取摇杆方向，这是双轴摇杆最常见的应用。
```python
import board,analogio,time

x_axis_pin = analogio.AnalogIn(board.A0)
y_axis_pin = analogio.AnalogIn(board.A1)

direction_list = ["East","Southeast","South","Southwest","West","Northwest","North","Northeast","Centre"]

def get_zero(times =500, sleep = 0.01):
    x_total = 0
    y_total = 0
    for i in range (times):
        x_axis = x_axis_pin.value
        y_axis = y_axis_pin.value
        x_total += x_axis
        y_total += y_axis
        time.sleep(sleep)
    x_zero = x_total // times
    y_zero = y_total // times
    return (x_zero,y_zero)

def get_direction(zero = (32767,32767)):
    x_axis = x_axis_pin.value - zero[0]
    y_axis = y_axis_pin.value - zero[1]
    if x_axis >= 10000 and -10000 < y_axis < 10000:
        return direction_list[0]
    elif x_axis >= 10000 and y_axis <= -10000:
        return direction_list[1]
    elif -10000 < x_axis < 10000 and y_axis <= -10000:
        return direction_list[2]
    elif x_axis <= -10000 and y_axis <= -10000:
        return direction_list[3]
    elif x_axis <= -10000 and -10000 < y_axis < 10000:
        return direction_list[4]
    elif x_axis <= -10000 and y_axis >= 10000:
        return direction_list[5]
    elif -10000 < x_axis < 10000 and y_axis >= 10000:
        return direction_list[6]
    elif x_axis >=10000 and y_axis >= 10000:
        return direction_list[7]
    else :
        return direction_list[8]

zero = get_zero(times =50, sleep = 0.01)
print(zero)

while True:
    x_axis = x_axis_pin.value - zero[0]
    y_axis = y_axis_pin.value - zero[1]
    print((x_axis,y_axis))
    print(get_direction(zero = zero))
    time.sleep(0.1)
```
5. 设置坐标精度等级，计算每级跨度，可以按需求消除抖动，增强数据的实用性。
```python
import board,analogio,time

x_axis_pin = analogio.AnalogIn(board.A0)
y_axis_pin = analogio.AnalogIn(board.A1)

def get_zero(times =500, sleep = 0.01):
    x_total = 0
    y_total = 0
    for i in range (times):
        x_axis = x_axis_pin.value
        y_axis = y_axis_pin.value
        x_total += x_axis
        y_total += y_axis
        time.sleep(sleep)
    x_zero = x_total // times
    y_zero = y_total // times
    return (x_zero,y_zero)

def get_extremum(times =500, sleep = 0.01):
    x_list = []
    y_list = []
    for i in range (times):
        x_axis = x_axis_pin.value
        y_axis = y_axis_pin.value
        x_list.append(x_axis)
        y_list.append(y_axis)
        time.sleep(sleep)
    x_extremum = (min(x_list),max(x_list))
    y_extremum = (min(y_list),max(y_list))
    return (x_extremum,y_extremum)
    
def get_spacing(level = 16 , zero =(32767,32767) ,x_extremum = (0,65535),y_extremum = (0,65535)):
    x_temp_1 = (zero[0] - x_extremum[0]) // level
    x_temp_2 = (x_extremum[1] - zero[0] ) // level
    y_temp_1 = (zero[1] - y_extremum[0]) // level
    y_temp_2 = (y_extremum[1] - zero[1] ) // level
    x_spacing = (x_temp_1,x_temp_2)
    y_spacing = (y_temp_1,y_temp_2)
    return (x_spacing,y_spacing)

def get_coordinates(zero = (32767,32767), x_spacing = (2048,2048),y_spacing = (2048,2048)):
    x_value = x_axis_pin.value - zero[0]
    y_value = y_axis_pin.value - zero[1]
    if x_value >= 0:
        x_axis = x_value // x_spacing[1]
    else:
        x_axis = - ((-x_value) // x_spacing[0])
    if y_value >= 0:
        y_axis = y_value // y_spacing[1]
    else:
        y_axis = - ((-y_value) // y_spacing[0])
    return (x_axis,y_axis)
    
zero = get_zero(times =500, sleep = 0.01)
print(zero)
(x_extremum,y_extremum) = get_extremum(times = 500, sleep = 0.01)
print((x_extremum, y_extremum))
(x_spacing,y_spacing) = get_spacing(level = 128 , zero = zero, x_extremum = x_extremum,y_extremum = y_extremum)
print((x_spacing, y_spacing))

while True:
    coordinates = get_coordinates(zero = zero, x_spacing = x_spacing, y_spacing = y_spacing)
    print(coordinates)
    time.sleep(0.1)
```
