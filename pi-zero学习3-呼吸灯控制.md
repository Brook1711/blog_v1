---
title: 'pi-zero学习3: 呼吸灯控制'
date: 2021-02-27 10:17:14
tags: pi_zero
categories:
    - coding
    - pi zero
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100542033.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100613016.png
comment: true
---

# pi-zero学习3: 呼吸灯控制

代码：

```python
import RPi.GPIO as GPIO        # 引入GPIO模块      
from time import sleep              # 引入time模块
      
LedPin = 19    # 引脚定义 （后面用）
freq =100        # 存放PWM频率变量，这里初始值为100，可以根据实际需要修改                
dc = 0              # 存放PWM占空比变量，这里初始值为0，可以根据实际需要修改              

GPIO.setmode(GPIO.BCM)            # 使用BCM编号方式        
GPIO.setup(LedPin, GPIO.OUT)    # 将GPIO19设置为输出模式    

pwm = GPIO.PWM(LedPin, freq)     # 创建PWM对象，并指定初始频率
pwm.start(dc)                                   # 启动PWM，并指定初始占空比

freq = int(input("Please input the frequency of PWM(1-2000Hz): "))   # 等待输入新PWM频率
pwm.ChangeFrequency(freq)        # 改变PWM频率
while True:                                    # 循环
     if dc ==0:                               #如果占空比为0时
         while 1:
                dc = dc+1                   #占空比自加
                sleep(0.01)                #占空比一0.01s的速度自加
                pwm.ChangeDutyCycle(dc)  #灯现实逐渐变亮
                if dc ==100:
                     break                 如果占空比加到一百时跳出循环体
     if dc == 100:      #与上面相反
         while 1:
                dc = dc-1
                sleep(0.01)
                pwm.ChangeDutyCycle(dc) 
                if dc == 0:
                     break
                     
input()                    
GPIO.cleanup()    # 清理释放GPIO资源，将GPIO复位

```

