
#EasyPy硬件介绍
EasyPy基于MicroPython开发出一系列的硬件学习板ePy board, 可以让使用者充分来利用ePy board 实现不同的应用场景。本文将指导您设置Easy-python，获取提示，EasyPy上有一个小的内部文件系统（驱动器），以便您轻松地将代码从桌面传输到微控制器或嵌入式系统来使用硬件外围设备以及控制某些外部组件。
下面的引出线用于ePy board v1.0易控板。您还可以查看其他版本的ePy board的引脚分配： ePy-Pro智趣板或ePy-X扩充板等等。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps5574.png) 

### EasyPy技术规格
EasyPy具有优越的芯片功能来尽量兼容MicroPython, 为方便起见，下面提供了一些技术规格：
> * 架构：ARM双核32位Cortex-M3
> * CPU频率：每核高达162MHz
> * 总RAM可用：324KB
> * BootROM：64KB
> * 内部PSRAM: 8MB
> * 内部FlashROM：无
> * 外部FlashROM：代码和数据，通过SPI Flash; 通常的大小8MB
> * GPIO：80（GPIO与其他功能复用，包括外部FlashROM，UART等）
> * UART：2个RX / TX UART
> * SPI：3个SPI接口（一个用于FlashROM）
> * I2C：3个I2C（任何引脚都提供bitbang实现）
> * I2S：5个
> * ADC：10位SAR ADC，最多6个通道
> * USB 2.0高速: 支持MSC/HID/UAC/UVC
> * SD界面：支持SD卡
> * 多媒体接口: 支持TFT 和 CMOS接口 
> * 易控板载

   >  * 三轴加速度计MXC400, 测量范围:±2G
   >  * 光线传感器
   >  * 麦克风
   >  * 5 颗全彩WS2812灯珠
   >  * 蜂鸣器
   >  * 支持4个物理按键(A/B/C/D)

### 外观规格
> * 供电电压：5V 
> * 工作电压：3.3V 
> * 最大工作电流:50mA 
> * 产品尺寸：48*52mm 
> * 包装尺寸：110*110*30mm 
> * 单主控板重量：9.0g
> * 含包装重量：60.0g  
### 组件布局

####易控板正面

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps6168.png)

####易控板反面

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps6176.png)

### 引脚定义

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps5574.png)

###引脚接口说明



| 正面引脚    |	功能描述 |
| --------    | :-----  |
| P0    |	模拟/数字输入,模拟/数字输出, PWM输出 |
| P1    |	模拟/数字输入,模拟/数字输出, PWM输出 |
| P2    |	模拟/数字输入,模拟/数字输出, PWM输出 |
| P21   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P22   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P23   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P24   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P25   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P26   |	数字输入/输出, I2S音频信号, 可接到扩充板音频IC |
| P27   |	数字输入/输出，PWM输出, I2C总线SCL, 可接到扩充板音频IC |
| P28   |	数字输入/输出，PWM输出, I2C总线SCL, 可接到扩充板音频IC |
| P29   |	数字输入/输出, PWM输出, 可以作为SPI 接口使用 |
| P30   |	数字输入/输出, PWM输出, 可以作为SPI 接口使用 |
| P31   |	数字输入/输出, PWM输出, 可以作为SPI 接口使用 |
| P32   |	数字输入/输出, PWM输出, 可以作为SPI 接口使用 |
| P33   |	数字输入/输出，PWM输出, I2C总线SCL |
| P34   |	数字输入/输出，PWM输出, I2C总线SDA |
| 3V3   |	电源正输入:连接USB时,易控板内部稳压输出3.3V,未连接USB可以通过输入(3.6~5.0)V电压为易掌控板供电 |
| P35   |	保留 |
| P36 	| 保留 |
| GND 	| 电源GND | 

| 背面引脚	| 功能描述 |
| --------    | :-----  |
| P0 	| 模拟/数字输入,模拟/数字输出, PWM输出 	|
| P1 	| 模拟/数字输入,模拟/数字输出, PWM输出	|
| P2 	| 模拟/数字输入,模拟/数字输出, PWM输出	|
| P3 	| 模拟/数字输入,模拟/数字输出, PWM输出	|
| P4 	| 模拟/数字输入,模拟/数字输出, PWM输出, 连接易控板光线传感器 	|
| P5 	| 数字输入/输出, 连接易控板按键A 	|
| P6 	| 数字输入/输出, PWM输出, 连接易控板蜂鸣器,不使用蜂鸣器时,可以作为串口IO使用 	|
| P7 	| 数字输入/输出, PWM输出, 可以作为串口IO使用	|
| P8 	| 数字输入/输出, PWM输出, 可以作为串口IO使用	|
| P9 	| 数字输入/输出, PWM输出, 可以作为串口IO使用	|
| P10 	| 模拟/数字输入,模拟/数字输出, PWM输出, 连接易控板声音传感器 	|
| P11 	| 数字输入/输出, 连接易控板按键B 	|
| P12 	| 数字输入/输出, PWM输出 	|
| P13 	| 数字输入/输出, PWM输出, 可以作为SPI 接口使用	|
| P14 	| 数字输入/输出, PWM输出, 可以作为SPI 接口使用 | 
| P15 	| 数字输入/输出, PWM输出, 可以作为SPI 接口使用 | 
| P16 	| 数字输入/输出, PWM输出, 可以作为SPI 接口使用 | 
| 3V3 	| 电源正输入:连接USB时,易控板内部稳压输出3.3V,  未连接USB可以通过输入(3.6~5.0)V电压为易掌控板供电 | 
| P19 	| 数字输入/输出，PWM输出, I2C总线SCL | 
| P20 	| 数字输入/输出，PWM输出, I2C总线SDA | 
| GND 	| 电源GND | 

