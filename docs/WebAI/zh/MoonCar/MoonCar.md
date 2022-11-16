

# 五、操控 MoonCar

![](../assets/images/upload_3873f6904888518d624142d07ba04302.png)

![](../assets/images/upload_326bf9bc32fc249a00653000a153f85d.png) ![](../assets/images/upload_8e98c3d36fd19f13f6d1b663e752e86c.png)

## 颜色侦测

这个例子中，颜色侦测使用的是 MoonCar 上面的 TCS34725 传感器，可用来侦测颜色。
先使用 class TCS34725 驱动传感器，进行打光和读取颜色值。

![](../assets/images/upload_4d4613a146aca71af6b235cb1e420a0c.png) ![](../assets/images/upload_3d0d9b773a839bc6f1b0389e497370a4.png) ![](../assets/images/upload_3d97627ea1cbecae280f35770f7fa107.png)

~~~python=
from webai_blockly import TCS34725
from webai import *
from machine import I2C

i2c = I2C(id=3, freq=100000, scl=17, sda=15) #1920

pinB=16 # light
fm.fpioa.set_function(pinB,fm.fpioa.GPIO6)
gpioB=GPIO(GPIO.GPIO6,GPIO.OUT)
gpioB.value(0)

s = TCS34725(i2c)
img = webai.snapshot()
img.clear()
v = 100
while True:
   time.sleep_ms(200)
   try:
      data = s.read(raw=True)
      data = (data[0]+v,data[1]+v,data[2]+v)
      print(data)
      img.draw_string(2,2, "Color", color=data, scale=11)
      lcd.display(img)
   except Exception as e:
      print(e)
~~~

## 循迹行驶

让小车沿着黑线行驶。

<iframe src="https://www.youtube.com/embed/D6cet80DZvM" allowfullscreen width="100%" style="aspect-ratio:728/410;border:none " ></iframe>

~~~python=
from webai import *

speed = 60
carType = 1

def tracking(pin):
    global carType,speed

    left = p15.value()
    right = p16.value()
    msg = str(left)+" : "+str(right)

    if left == 0 and right == 0:
        if carType == 1:
            mcar.forward(speed)
        elif carType == 2:
            mcar.move(0,speed)
        elif carType == 3:
            mcar.move(speed,0)

    if left == 1 and right == 1:
        carType = 1
        mcar.forward(speed)
    
    if left == 1 and right == 0:
        carType = 2
        mcar.move(0,speed)
    
    if left == 0 and right == 1:
        carType = 3
        mcar.move(speed,0)

p15 = webai.io.pin(15,pull_mode=webai.io.PULL_NONE)
p15.irq(tracking,GPIO.IRQ_BOTH)
p16 = webai.io.pin(16,pull_mode=webai.io.PULL_NONE)
p16.irq(tracking,GPIO.IRQ_BOTH)
~~~

## 循迹 + 物件追踪

沿着黑线移动，看见红色小怪兽停车，看见绿色小怪兽继续前进。

<iframe src="https://www.youtube.com/embed/PNbYPFdmBk0" allowfullscreen width="100%" style="aspect-ratio:728/410;border:none " ></iframe>

- 第 58 行 ～ 第 61 行：判断处

~~~python=
from webai import *

speed = 60
carType = 1

def tracking(pin):
    global carType,speed
 
    left = p15.value()
    right = p16.value()
    msg = str(left)+" : "+str(right)

    if left == 0 and right == 0:
        if carType == 1:
            mcar.forward(speed)
        elif carType == 2:
            mcar.move(0,speed)
        elif carType == 3:
            mcar.move(speed,0)

    if left == 1 and right == 1:
        carType = 1
        mcar.forward(speed)
    
    if left == 1 and right == 0:
        carType = 2
        mcar.move(0,speed)
    
    if left == 0 and right == 1:
        carType = 3
        mcar.move(speed,0)
    
    #webai.draw_string(140,100,msg,scale=2)

p15 = webai.io.pin(15,pull_mode=webai.io.PULL_NONE)
p15.irq(tracking,GPIO.IRQ_BOTH)
p16 = webai.io.pin(16,pull_mode=webai.io.PULL_NONE)
p16.irq(tracking,GPIO.IRQ_BOTH)


from webai_blockly import ObjectTracking
from time import sleep
from webai_blockly import Lcd

objGroup = None
obj = None

view = Lcd()

_deviceID = '6e5596'


otb = ObjectTracking(flip=1, model='monster', classes=['green','red','yellow','blue'], threshold=0.1, w=320, h=224)
while True:
  otb.checkObjects()
  green = otb.getObjects('green')
  red = otb.getObjects('red')
  if (len(red)) >= 1:
    mcar.stop()
  if (len(green)) >= 1:
    tracking(None)

  sleep(0.001)
~~~

## 马达控制

### 前进

```python
mcar.forward() # 100% 动力前进

mcar.forward(100) # 100% 动力前进

mcar.forward(50) # 50% 动力前进
```

### 后退

```python
mcar.backward() # 100% 动力后退

mcar.backward(100) # 100% 动力后退
```

### 停止

```python
mcar.stop() # 停止

mcar.forward(0) # 停止

mcar.backward(0) # 停止
```

### 左转

```python
mcar.left(100) # 100% 动力左转

mcar.left(30) # 30% 动力左转
```

### 右转

```python
mcar.right(100) # 100% 动力右转

mcar.right(30) # 30% 动力右转
```
### 左右轮

- ==mcar.move( 左轮 , 右轮 )==
- 数值区间：-100 ~ 100

~~~python=
from webai import *
mcar.move( 100 , 100) # 100% 前进
~~~

#### 参考设定

~~~python
mcar.move( -100 , -100) # 100% 后退

mcar.move( 45 , -45 ) # 向右转

mcar.move( -45 , 45 ) # 向左转

mcar.move(0,0) # 停止
~~~

## 相关传感器

### 超音波：距离侦测

利用发送超音波碰撞物体之后反射回来的时间差，来得出传感器与物体之间的距离。

> 使用前请记得先接上超音波传感器！

~~~python=
from fpioa_manager import *
from modules import hcsr04
import time
fm.register(6, fm.fpioa.GPIO0, force = True)
fm.register(11, fm.fpioa.GPIO1, force = True)

device = hcsr04(fm.fpioa.GPIO0,fm.fpioa.GPIO1)

while True:
    try:
        print(device.measure(hcsr04.UNIT_CM,100000))
        time.sleep(0.05)
    #except IDE interrupt
    except Exception as e:
        print(e)
        if(str(e)=="IDE interrupt"):
            break
~~~

### 红外线：无线控制

![](../assets/images/upload_74c8803f271749db2115168b09413649.png)

接收遥控器发射的红外线信号，并显示到屏幕上。

~~~python=
import lcd, image, utime
from Maix import GPIO
from fpioa_manager import fm

img = image.Image()
fm.register(25, fm.fpioa.GPIOHS1)
pin=GPIO(GPIO.GPIOHS1,GPIO.IN,GPIO.PULL_UP)

def read_data():
   a = []
   while pin.value() == 1:
       pass
   utime.sleep_us(13560)
   for i in range(1000):
       v = pin.value()
       a.append(v)
       utime.sleep_us(56)
   a_c = []
   count = 0
   for i in a:
       if i == 1:
           count += 1

       elif i == 0:
           if count > 0 :
               a_c.append(count)
           count =0
   for i in range(len(a_c)):
       if a_c[i] > 10:
           a_c[i] = "1"
       else:
           a_c[i] = "0"
   B1 = "".join(a_c)
   if(len(B1)==33):
       print(B1[1:len(B1)])
       hstr = '%0*X' % ((len(B1[1:len(B1)]) + 3) // 4, int(B1[1:len(B1)], 2))
       print(hstr)
       print("=====")
       img.clear()
       img.draw_string(50, 100, hstr, scale=5)
       lcd.display(img)
   return B1

while True:
   f = read_data()
~~~


### 控制 LED 灯：魔幻 LED

![](../assets/images/upload_c4fb10302e37e3b658d2b6e666042baf.png) ![](../assets/images/upload_08ed64231aeb00a936398be7f7b257dd.png) ![](../assets/images/upload_af8033adf5c9a7e373e13eadf490c257.png)

- MoonCar 的 ws2812 Pin 脚为编号 22，总共有 8 颗灯
- 程序内容：魔幻 LED 示例。
    - 第 4 行：设定 Pin 脚为 22、LED 数量为 8 颗灯。

~~~python=
from modules import ws2812
import time

class_ws2812 = ws2812(led_pin=22,led_num=8)
color = [(30,0,0),(0,30,0),(0,0,30),(30,30,0),(30,0,30),(0,30,30) ,(30,30,30),(0,0,0)]
while True:
    for x in color :
        for i in [0,1,2,3,4,5,6,7] :
            class_ws2812.set_led(i,x)
            class_ws2812.display()
            time.sleep(0.05)
~~~

### 蜂鸣器：播放音乐

- MoonCar 的蜂鸣器 Pin 脚为编号 24。
- 程序内容：播放 3 个音符。
    - 第 3 行：设定发音频率
    - 第 4 行：设定发音时间 ( 秒 )

~~~python=
from webai_ext import Buzzer
buzzer = Buzzer()
tune = [392,692,440]
sec = [0.25,0.25,0.5]
for i in [0,1,2] :
    buzzer.bee(tune[i],sec[i])
~~~

## 万用遥控器控制登月小车

执行程序后开发板屏幕会显示 QRcode，使用手机扫描后即可用 Webduino 万用遥控器控制小车。

> 万用遥控器的使用方式可以参考：[万用遥控器控制登月小车](https://bpi-steam.com/WebAI/zh/MoonCar/MoonCar.html#%E4%B8%87%E7%94%A8%E9%81%A5%E6%8E%A7%E5%99%A8%E6%8E%A7%E5%88%B6%E7%99%BB%E6%9C%88%E5%B0%8F%E8%BD%A6)。

![](../assets/images/upload_755911840efc039cab699de0c0465ec0.png)

~~~python=
from webai import *
import machine , ubinascii , os , time , gc , sensor

mcar.init()
def cmd(name,msg):
    webai.cmdProcess.sub(name,msg)
    if msg == 'up':
        webai.show(file='mrun.jpg')
        mcar.forward(50)
    if msg == 'down':
        webai.show(file='m02.jpg')
        mcar.backward(50)
    if msg == 'left':
        webai.show(file='mleft.jpg')
        mcar.left(50)
    if msg == 'right':
        webai.show(file='mright.jpg')
        mcar.right(50)
    if msg == 'reset':
        webai.show(file='m01.jpg')
        mcar.stop()
    if msg == '开心':
        webai.speaker.play(filename="logo.wav")

webai.show(file='mooncar.jpg')
webai.mqtt.sub('PING',cmd,includeID=True)
~~~