#EasyPy的教程
本教程旨在帮助您开始使用EasyPy。您只需要一个EasyPy和一根micro-USB线将其连接到PC。如果这是您的第一次，建议按照以下顺序按照教程进行操作。

> * 1.ePy board简介
> * 2.运行第一个脚本
> * 3.获取EasyPython REPL提示
> * 4.打开LED和基本的Python概念
> * 5.按键Switch，回调和中断
> * 6.加速度计
> * 7.定时器
> * 8.RTC
> * 9.PWM
> * 10.PIN
> * 11.ADC
> * 12.声音侦测
> * 13.电子音乐
> * 14.光感测
> * 15.UART
> * 16.I2C
> * 17.SPI
##4.1 ePy board简介
为了充分利用你的ePy board，有一些基本的东西需要了解它是如何工作的。

 - 插拔USB电缆时要轻柔。虽然USB连接器通过电路板焊接并且相对较强，但如果它断开则可能很难固定。
 - 静电会震动ePy board上的组件并将其破坏。如果您所在地区经历了大量静电（例如干燥和寒冷的气候），请特别注意不要让ePy board受到冲击。如果你的ePy board是一个黑色塑料盒，那么这个盒子是存放和携带EasyPy的最佳方式，因为它是一个防静电盒子（它由导电塑料制成，里面有导电泡沫）。
 
只要你照顾硬件，你应该没问题。破解ePy board上的软件几乎是不可能的，所以随意编写代码，尽可能多地编写代码。如果文件系统损坏，您可能需要重新刷新EasyPy软件，但这可以通过USB完成。
###4.1.1 ePy board的布局

    Micro USB连接器位于上方中间的位置，板子的右下方有4个LED。颜色为：底部为黄色，顶部为红色，绿色和蓝色。有5个按键：再USB座的右边是复位按键，上面左右边是A, B用户按键。背面也有两个按键C, D.

###4.1.2 插入和开机

    ePy board可以通过USB供电。通过micro USB线将其连接到PC。电缆只有一种方式适合。连接后，电路板上的绿色LED应快速闪烁。完成开机, 绿灯将常亮

###4.1.3 通过外部电源供电

    ePy board可以由电池或其他外部电源供电。
    
**务必将电源正极连接到VIN，接地连接到GND。EasyPy上没有极性保护，因此在将任何东西连接到VIN时必须小心。**

**输入电压必须介于3.6V和8.4V之间**

##4.2 运行你的第一个脚本
让我们直接进入并在ePy board上运行Python脚本。毕竟，这就是它的全部！
###4.2.1 连接您的ePy board 
使用micro USB线将ePy board连接到PC。电缆只有一种连接方式，所以你不会错。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps12153.png) 

当ePy board连接到您的PC时，它将打开电源并进入启动过程（启动过程）。绿色LED应亮起半秒或更短时间，当它常亮时表示启动过程已完成。这时候会看到PC会增加一个磁盘槽. 可以找到boot.py和main.py以及一些说明文檔。
###4.2.2 打开EasyPy USB驱动器
您的PC现在应该识别EasyPy。这取决于您拥有的PC类型，接下来会发生什么：

 - Windows：您的EasyPy将显示为可移动USB闪存驱动器。Windows可能会自动弹出一个窗口，或者您可能需要使用资源管理器去那里。
Windows还会看到EasyPy有一个串行设备，它会尝试自动配置这个设备。如果是，请取消该过程。我们将在下一个教程中使用串行设备。

 - Mac：您的EasyPy将作为可移动光盘出现在桌面上。它可能会被称为“NONAME”。单击它打开EasyPy活页夹。

 - Linux：您的EasyPy将显示为可移动媒体。在Ubuntu上，它将自动挂载并弹出一个带有EasyPy活页夹的窗口。在其他Linux发行版上，EasyPy可能会自动挂载，或者您可能需要手动执行。在终端命令行中，键入lsblk 以查看已连接驱动器的列表，然后（替换为相应的设备）。您可能需要root才能执行此操作。mount /dev/sdb1sdb1
好的，所以你现在应该将EasyPy连接为USB闪存驱动器，并且窗口（或命令行）应该显示EasyPy驱动器上的文件。
您正在查看的驱动器称为/flashEasyPy，应包含以下2个文件：

 - boot.py - 当EasyPy启动时执行此脚本。它设定
EasyPy的各种配置选项。
 - main.py - 这是包含Python程序的主脚本。
它执行后boot.py。
###4.2.3 编辑Main.py
现在我们将编写Easy Python程序，因此main.py 在Windows上的MU编辑器中打开文件。在Mac和Linux上，使用您喜欢的文本编辑器。打开文件，您会看到它包含1行：

    # main.py -- put your code here!   ;把你的代码放在这里！

该行以＃字符开头，表示它是注释。这些行不会做任何事情，你可以在那里写下关于你的程序的注释。

让我们在这个main.py文件中加2行，使它看起来像这样：

    # main.py -- put your code here! ; 把你的代码放在这里！

    from machine import LED
    LED(3).on()

我们写的第一行说我们想要使用该machine (ePy)模块。该模块包含控制EasyPy功能的所有函数和类型。

我们写的第二行打开了蓝色LED：它首先LED 从ePy模块中获取类型，创建LED编号3（蓝色LED），然后将其打开。
###4.2.4 重置EasyPy 
要运行此小脚本，您需要先保存并关闭该main.py文件，然后弹出（或卸除）EasyPy USB驱动器。这样做就像普通的USB闪存驱动器一样。

当安全地弹出/卸除驱动器时，您可以进入有趣的部分：按下EasyPy上的RST开关以重置并运行您的脚本。RST开关是板上USB连接器旁边的小黑色按钮。

当您按RST时，绿色LED将快速闪烁，然后蓝色LED应亮起并保持亮起状态。

恭喜！您已经编写并运行了第一个EasyPython程序！

##4.3 获取EasyPython REPL提示
REPL代表Read Evaluate Print Loop，是您可以在EasyPy上访问的交互式EasyPython提示的名称。到目前为止，使用REPL是测试代码和运行命令的最简单方法。除了编写脚本外，您还可以使用REPL `main.py`。

要使用REPL，您必须连接到EasyPy上的串行USB设备。如何执行此操作取决于您的操作系统。

###4.3.1使用REPL提示
现在让我们尝试直接在EasyPy上运行一些EasyPython代码。

打开MU编辑器并找到写有REPL的图标, 按下此图标后, 您会看到MU编辑器的下面窗口中出现Easy Python and ePy board的相关版本信息。按Enter键，您将看到一个EasyPython提示符，即>>>。让我们确保它正在使用强制性测试：

    >>> print （“hello EasyPy！” ）
    hello EasyPy！

在上面，您不应该输入>>>字符。它们表示您应该在提示符后面键入文本。最后，输入文本并按Enter键后，屏幕上的输出应如上所示。print("hello EasyPy!")

如果您已经了解了一些python，现在可以在这里尝试一些基本命令。EasyPy由于空间原因, 没有浮点支持, 也没有数学模块。这意味着浮点数不能在代码中的任何位置使用, 并且必须使用 "//" 而不是 "/" 执行所有分区。如果其中任何一个不起作用，您可以尝试硬重置或软重置; 见下文。

继续尝试输入其他一些命令。例如：

    >>> LED(1).on()
    >>> LED(2).on()
    >>> r=4//2  #运算正常
    >>> r=4/2  #不正常运算
    >>> 1 + 2
    3
    >>> 2 * 4
    8
    >>> 20 * 'py'
    'pypypypypypypypypypypypypypypypypypypypy'

###4.3.2重置板
如果出现问题，您可以通过两种方式重置电路板。第一种是在EasyPython提示符下按CTRL-D，它会执行软复位。你会看到类似的消息

    >>>
    EASYPY: soft reboot					; 软重启
    MicroPython mp_v_1.0000.0001-6-gfe121ad-dirty on 2019-05-14; DEFAULT EASYPY v1.00.00
    Type "help()" for more information.			; 以获取更多信息。
    >>>

如果不起作用，您可以通过按下RST开关（最靠近电路板上的微型USB插座的黑色小按钮）执行硬重置（再次开启和关闭）。这将结束您的会话，断开您用于连接到EasyPy的任何程序。

如果要进行硬重置，建议先关闭串口程序并弹出/卸除EasyPy驱动器。
##4.4 打开LED和基本的Python概念
在EasyPy上最简单的方法是打开连接到电路板的LED。连接电路板，并按照教程1中的说明登录。我们将从解释器中的转动和LED开始，键入以下内容

    >>> from machine import LED
    >>> myled = LED(1)
    >>> myled.on()		;开
    >>> myled.off()		;关

这些命令可以打开和关闭LED。

这一切都很好，但我们希望这个过程是自动化的。在您喜欢的MU编辑器中打开EasyPy上的文件MAIN.py。将以下行写入或粘贴到文件中。如果您是python的新手，那么请确保缩进正确，因为这很重要！

    from machine import Timer
    from machine import LED
    import utime
    
    led = LED(1)
    while True:		;当真的
        led.toggle()
        utime.sleep_ms (1000)	;延迟1000ms

要运行脚本，请执行”Flash”图标。然后EasyPy将下载Main.py并启动，您应该看到红灯持续闪烁。成功，是你建立邪恶机器人军队的第一步！当您对烦人的闪光灯感到厌倦时，请按下终端上的CTRL-C以停止运行。

那么这段代码有什么用呢？首先，我们需要一些术语。类别on是一种面向对象的语言，几乎python中的所有东西都是一个Class (类别)，当你创建一个类别的实例时，你会得到一个对象。类别具有与之关联的方法。方法（也称为成员函数）用于与对象交互或控制对象。

第一行代码创建了一个LED对象，然后我们称之为led对象。当我们创建对象时，它需要一个参数，该参数必须在0到3之间，对应于电路板上的4个LED。ePy LED类有三个我们将使用的重要成员函数：on（），off（）和toggle（）。我们使用的另一个函数是utime.sleep_ms（），这只是等待一个给定的时间，以毫秒为单位。一旦我们创建了LED对象，声明为True：创建一个无限循环，在打开和关闭之间切换LED并等待1秒。4个LED其分别的参数编号为红色LED(1), 绿色LED(2), 蓝色LED(3), 橙色LED(4)。

**练习：尝试更改切换LED和打开不同LED之间的时间。**

**练习：直接连接到EasyPy，创建一个ePy.LED对象并使用on（）方法将其打开**。

###4.4.1 闪动您EasyPy 
到目前为止，我们只使用了一个LED，但是EasyPy有4个可用。让我们首先为每个LED创建一个对象，以便我们可以控制每个LED。我们通过创建具有列表理解的LEDS列表来实现这一点。

    leds = [LED(i) for i in range(1,5)]

如果使用不是1,2,3,4的数字调用LED（），您将收到错误消息。接下来，我们将设置一个无限循环，循环通过每个LED打开和关闭它们。

    from machine import Timer
    from machine import LED
    import utimer
    n = 0
    while True:
      n = (n + 1) % 4
      leds[n].toggle()
      utime.sleep_ms(750)	延迟750毫秒

这里，n跟踪当前LED，每次循环执行时我们循环到下一个n（％符号是模数运算符，保持n在0和3之间。）然后我们访问第n个LED并切换它。如果你运行它，你应该看到每个LED都打开然后所有LED按顺序再次关闭。

您可能会发现的一个问题是，如果您停止脚本然后再次启动它，那就是LED从上一次运行中停留，破坏了我们精心编排的迪斯科舞厅。我们可以通过在初始化脚本然后使用try / finally块关闭所有LED来解决这个问题。当您按CTRL-C时，EasyPython会生成VCPInterrupt异常。异常通常意味着出现了问题，您可以使用try：命令来“捕获”异常。在这种情况下，只是用户中断脚本，因此我们不需要捕获错误，只是告诉EasyPython退出时要做什么。finally块执行此操作，我们使用它来确保所有LED都关闭。完整的代码是：

    from machine import Timer
    from machine import LED
    import utime
    
    leds = [LED(i) for i in range(1,5)]
    for l in leds:
        l.off()
    
    n = 0
    try:
       while True:
          n = (n + 1) % 4
          leds[n].toggle()
          utime.sleep_ms(750)
    finally:
        for l in leds:
            l.off()

##4.5 按键Key和中断
EasyPy有5个小开关，标有A, B, C, D和RST。RST开关是一个硬复位开关，如果按下它，它会从头开始重新启动EasyPy，相当于关闭电源然后再打开电源。

A, B, C, D开关用于一般用途，并通过按键Key对象进行控制。4个按键其分别的参数编号为按键A-KEY(0), 按键B-KEY(1), 按键C-KEY(2), 按键D-KEY(3)。 可以再REPL执行下面对象：

    >>> sw = KEY(0)

请记住，如果您收到名称不存在的错误，则可能需要键入内容。from machine import KEY
使用key对象，您可以获得其状态：

    >>> sw.value()
    1

1如果是未按住按键A或按住按键A，将打印0。尝试在运行上述命令时按住Key按键A。
通过“调用”开关对象，还有一个简写符号来获取开关状态：

    >>> sw.value()
    0

###4.5.1 中断
该开关是一个非常简单的对象，但它确实有一个高级功能：该irq()功能。回调函数设置在按下开关时运行的东西，并使用中断。irq()的指令语法如下

> irq(trigger, handler)

trigger—表示按键触发的形式有

a.PIN.IRQ_BOTH : 设置按键引脚上升沿和下降沿中断触发.
b.PIN.IRQ_FALLING : 设置按键下降沿中断触发.
c.PIN.IRQ_RISING : 设置按键引脚上升沿中断触发.
d.PIN.IRQ_LOW_LEVEL : 设置按键引脚低电平中断触发.
e.PIN.IRQ_HIGH_LEVEL : 设置按键引脚高电平中断触发.

handler—可以创建一个回调函数，此中断处理程序获取您创建的函数并执行它

一个按键中断产生将发生以下情况：

1.按下开关时，引脚发生变化（trigger），微控制器记录此变化。
2.微控制器完成当前机器指令的执行，停止执行并保存其当前状态（将寄存器推入堆栈）。这具有暂停任何代码的效果，例如您正在运行的Python脚本。
3.微控制器开始执行与开关外部触发相关的特殊中断处理程序。此中断处理程序获取您注册的回调函数(handler)并执行它。
4.执行回调函数直到完成，将控制权返回给开关中断处理程序。
5.开关中断处理程序返回，并通知微控制器已经处理了中断。
6.微控制器恢复在步骤2中保存的状态。
7.继续执行一开始运行的代码。除了暂停，此代码不会注意到它被中断。

当多个中断同时发生时，上述事件序列会变得复杂一些。在这种情况下，具有最高优先级的中断首先进行，然后按优先级顺序进行其他中断。开关中断设置为最低优先级。

###4.5.2 按键范例

    from machine import KEY
    from machine import PIN
    
    p=PIN('P12')   #脚位为P4.4
    p.mode(PIN.OUT)
    p.value(0)
    def toggle(t):
        if p.value() == 0:
        p.value(1)
       else :
        p.value(0)
    k=KEY(1)
    k.value()
    k.irq(trigger=PIN.IRQ_BOTH, handler=toggle)

##4.6 点亮RGB LED
ePy board有5颗RGB LED可以来做控制, 导入EasyPython模块后，会为易控创建一个对象rgb, 控制板载的RGB只需对rgb对象操作。

可以设置每个像素点颜色，num 为板载RGB灯的个数，第一个灯为1。 r、g、b 为颜色亮度值，范围值为0~255, 其控制语法如下

> rgb_writer(num,r, g, b)

num—设定RGB LED参数编号1-5
r—设定红色亮度0-255
g—设定绿色亮度0-255
b—设定蓝色亮度0-255

    from machine import LED
    
    rgb_led=LED(LED.RGB)
    rgb_led.rgb_write(1,255,0,0)  # 设置RGB1为红色，全亮度
    rgb_led.rgb_write(2,0,128,0)  # 设定RGB2为绿色，半亮度
    rgb_led.rgb_write(3,0,0,64)   # 设置RGB2为蓝色，四分之一亮度

###4.6.1 多彩LED
点亮ePy board上5颗RGB LED来做七彩灯变化

    from machine import LED
    
    l = LED(LED.RGB)
    print("show render")
    for i in range(0, 256, 1):
        for j in range(1, 6, 1):
            l.rgb_write(j, i, 0, 0)  	##Render red
    for i in range(0, 256, 1):
        for j in range(1, 6, 1):
            l.rgb_write(j, 255, i, 0)  	##Render green
    for i in range(0, 256, 1):
        for j in range(1, 6, 1):
            l.rgb_write(j, 255, 255, i)  ##Render blue
    times = 0
    while times < 10:  		##White LED breath 10 times
        for i in range(255, 1, -1):
            for j in range(1, 6, 1):
                l.rgb_write(j, i, i, i)
        for i in range(0, 256, 1):
            for j in range(1, 6, 1):
                l.rgb_write(j, i, i, i)
        times = times + 1
    for i in range(255, 1, -1):  	##Close LEDs slowly
        for j in range(1, 6, 1):
            l.rgb_write(j, i, i, i)
    l.off()

如果需要使用外部彩带，后续将创建一个新的对象来控制彩带上的LED。
##4.7 音乐
易控板板载无源蜂鸣器，其声音主要是通过高低不同的脉冲信号来控制而产生。声音频率可控，频率不同，发出的音调就不一样，从而可以发出不同的声音，还可以做出“多来米发索拉西”的效果。
###4.7.1 自编乐谱
我们可以通过设置音调来自编乐谱。

    from machine import Music
    
    music=Music()
    tune = [‘C4’,‘D4’,‘E4’,‘C4’,‘C4’,‘D4’,‘E4’,‘C4’,‘E4’,‘F4’,‘G4’,‘E4’,‘F4’,‘G4’]
    music.play('C#3:4', wait = 0, loop = 0)
    music.play(tune)

每个音符都有一个名字（比如C＃或F），一个八度和一个持续时间。八度用数字表示〜0表示最低八度，4表示中央C，8表示您需要的高度。持续时间也表示为数字。 持续时间的值越高，持续时间越长。例如，持续时间4将持续两倍于持续时间2（依此类推）。

每个音符都表示为一串字符，如下所示：

> NOTE[octave][:duration]

octave—表示八度音阶, 其数值范围为0到8
duration—表示节拍, 其数值范围为1~99

例如: C1:4  1指的是八度音阶1中的音符“C”，持续4个节拍时间。
预设初始值为八度音阶4.
R:4 使用音符名称R，则将其视为休息（静音）。
 #:上升音
 b:下降音

> play(music, wait, loop)

music—可以是一个音阶或一首歌
wait—等待直到这首歌播放完成, 预设初始值是”0”
loop—保持最后一个音符播放, 默认初始值是”0”

> stop( )

停止音乐播放

> deinit( )

释放音乐函数

###4.7.2. 频率
您还可以通过频率设置来制作一些非音符的音调。 例如，创建警笛效果：

    from machine import music
    
    music=Music()
    while True:
        for freq in range(880, 1760, 16):
            music.pitch(freq, 20,0)
        for freq in range(1760, 880, -16):
            music.pitch(freq,20,0)

在这个实例中是如何使用 pitch 方法，它需要一个频率。 其中range函数用于生成数值范围。这些数字用于定义音调的高低。 range函数有三个参数，分别是起始值，结束值和步长。因此，range的第一次使用是“以16的步长创建880到1760之间的数字范围”； 第二个次是“以-16”的步长创建1760到880之间的一系列值，持续频率为20毫秒。因此获得像警报器一样在频率上升和下降的频率范围而制作出警笛效果。

> pitch(frequency, duration, wait)

frequency—频率值, 用于定义音调的高低
duration—持续播放音调频率的时间, 以毫秒(ms)为计算单位
wait—等待直到这音调频率播放完成
###4.7.3 节拍设置
您还可以通过节拍来制作一首歌曲演奏的快慢效果。

    from machine import Music
    
    music=Music()
    musci.tempo(ticks=200, bpm=8)
    music.tempo()

> tempo(ticks, bpm)

ticks—设定节拍tick的数值, 默认初始值是”4”
bpm—设定bpm的数值, 其表示每分钟多少拍, 可以表现节奏的快慢

##4.8 ADC 模拟到数字转换
易控板提供6路ADC输入来检测仿真信号, 其信号信道编号为0~5, ADC的采样数据为10bit即最大值为十进制1024. ADC 引脚输入范围为 0-3.3 v (为 3.3 v, 是其能够承受的绝对最大值)。

    from machine import ADC
    adc = ADC(0)		# 创建ADC物件
    adc.init(1)             	# 启动ADC
    adc.channel(0)  		# 创建ADC引脚
    val = adc.read()              # 读取ADC数据

> ADC(adc_channel)

创建与给定引脚关联的 ADC 物件。这样, 您就可以读取该引脚上的模拟值。其硬件脚位定义如下. adc_channel为0~5
| 脚位定义	| ADC Channel
| --| --
| P0 (P0.4)	| ADC Channel 0
| P1 (P0.5)	| ADC Channel 1
| | P2 (P0.6)	| ADC Channel 2
| P3 (P0.7)	| ADC Channel 3 (外部仿真信号输入)
| P4 (P4.2)	| ADC Channel 4 (光线传感器)
| P10 (P4.3)	| ADC Channel 5 (麦克风) 

> ADC.init(adc_channel)

启用 ADC 块

> ADC.deinit()

禁用 ADC 块

> ADC.channel(adc_channel)—可以用以切换ADC输入通道

创建模拟引脚。如果只提供通道 ID, 则将选择正确的引脚。或者, 只能传递引脚, 并选择正确的通道。

    # 所有这些都是等效的, 并在 P0.5 上启用 ADC 通道1
    apin = adc.channel(1)
    apin = adc.channel(pin='P5')
    apin = adc.channel(id=1, pin='P5')

> ADC.read()

读取ADC采样数据, 采样频率为1KHz
###4.8.1 麦克风
ADC 通道可以连接到 MCU 的内部点或 GPIO 引脚, 我们首先来介绍ADC通道连接到板载麦克风，可以用其感知周边环境的声音变化。

例：显示声音值

    from machine import ADC
    from machine import LED
    import utime
    sound = ADC(5)
    led = LED(2)
    
    try:
    while True:
    	if sound.read() > 3 :  #麦克风输入音量大小超过3时, LED会亮绿灯
    		led.on()
    		utime.sleep_ms(750) #维持LED亮750毫秒
    	else: 
    		led.off()
    	utime.sleep_ms(1)
    finally: 
      sound.deinit()
      led.off()	

使用前，导入EasyPython的ADC模块

    from machine import ADC

我们使用 sound.read() 获取麦克风的数据。

学会了如何收集周边环境的声音数据，我们可以结合其他功能做更多有趣的场景。
###4.8.2 光线传感器
易控板板载光线传感器，可以用其感知周边环境的光线变化。光线传感器使用ADC通道”4”做为输入

例：光控灯:

    from machine import ADC
    from machine import LED
    import utime
    light = ADC(4)
    led = LED(2)
    
    try:
    while True:
    	if light.read() < 60 :  #当光线小于60, 输入音量大小超过3时, LED会亮绿灯
    		led.on()
    	else: 
    		led.off()
    	utime.sleep_ms(100)
    finally: 
      light.deinit()
      led.off()	

使用 light.read() 对象来获取光线传感器数据:

学会了如何收集周边环境的光线数据，我们可以结合其他功能做更多有趣的场景。
##4.10 Pin—引脚控制
引脚对象用于控制 I/O 引脚 (也称为 GPIO-通用输入/输出)。引脚对象通常与可以驱动输出电压和读取输入电压的物理引脚相关联。引脚类具有设置引脚模式 (IN、OUT 等) 的方法, 以及获取和设置数字逻辑级别的方法。

引脚对象是使用明确指定特定 I/O 引脚的标识符构造的。标识符的允许形式和标识符映射到的物理引脚是特定于埠的。标识符的可能性是一个整数、一个字符串或一个具有端口和引脚编号的元组。

使用模式:

    from machine import PIN
    p=PIN(‘P12’)			#创建I/O P12
    p.init(mode=PIN.OUT, value=0)	#在引脚P12设置为一个输出, 将值设置为 "低" 
    p.value(1)				#然后设置为 "高"
   

    

>  PIN(id, mode=PIN.IN, pull= PIN.INACTIVE,  value=0, drive=
> PIN.NORMAL_POWER)

创建引脚物件给定id关联的引脚外设 (GPIO 引脚)。如果在建构函式中给出了其他参数, 则它们将用于初始化引脚。这些参数是

i.id: 是必需的, 脚位定义为‘P0’~’P32’, P17和P18为保留
ii.mode: 指定引脚模式, 它可以是: 输出引脚PIN.OUT, 输入引脚PIN.IN
iii.pull : 指定引脚是否连接了 (弱) 拉电阻, 并且可以是
 

 - 上拉电阻启用PIN.PULL_UP, 
 - 向下拉电阻启用PIN.PULL_DOWN, 
 - 无向上或向下电阻PIN.INACTIVE
 
iv.value: 仅对 PIN.OUT和PIN.OPEN_DRAIN 模式有效, 并指定初始输出引脚值 0或1 (如果给定), 否则引脚外设的状态保持不变.
v.drive: 指定引脚的输出功率, 可以是以下各项: PIN.LOW_POWER, PIN.NORMAL_POWER, PIN.MED_POWER, PIN.HIGH_POWER。实际的当前驱动能力取决于埠。并非所有埠都实现此参数.

> PIN.init(mode, pull, value, drive)

使用给定的参数重新初始化引脚。将只设置指定的那些参数。引脚外围状态的其余部分将保持不变。返回无. 
i.mode: 指定引脚模式, 它可以是: 输出引脚PIN.OUT, 输入引脚PIN.IN
ii.pull : 指定引脚是否连接了 (弱) 拉电阻, 并且可以是

 - 上拉电阻启用PIN.PULL_UP, 
 - 向下拉电阻启用PIN.PULL_DOWN, 
 - 无向上或向下电阻PIN.INACTIVE
 
iii.value: 仅对 PIN.OUT和PIN.OPEN_DRAIN 模式有效, 并指定初始输出引脚值 0或1 (如果给定), 否则引脚外设的状态保持不变.
iv.drive: 指定引脚的输出功率, 可以是以下各项: PIN.LOW_POWER, PIN.NORMAL_POWER, PIN.MED_POWER, PIN.HIGH_POWER。实际的当前驱动能力取决于埠。并非所有埠都实现此参数.

> PIN.deinit()

禁用 PIN 块 

> PIN.value([x])

此方法允许设置和获取引脚的值, 具体取决于是否提供了参数x.

如果省略该参数, 则该方法获取引脚的数字逻辑电平, 分别返回与低电压和高压信号相对应的0或1。此方法的行为取决于引脚的模式: 

i.PIN.IN: 该方法返回引脚上当前存在的实际输入值.
ii.PIN.OUT : 方法的行为和传回值是未定义的

如果提供了参数, 则此方法设置引脚的数字逻辑级别。参数x可以是转换为布尔值的任何内容。如果它转换为true, 则引脚设置为 "1" 状态, 否则它将设置为 "0"。此方法的行为取决于引脚的模式:

i.PIN.IN: 该值存储在引脚的输出缓冲区中。引脚状态不会改变, 它保持在高阻抗状态。一旦将存储的值更改为“PIN.OUT"模式, 该值将在引脚上变为活动值.
ii.PIN.OUT : 输出缓冲区立即设置为给定的值.

设置值时, 此方法返回"无"

> PIN.mode([mode])

获取或设置引脚模式。

> PIN.pull([pull])

获取或设置引脚拉状态, 可以是PIN.PULL_UP, PIN.PULL_DOWN, PIN.INACTIVE

> PIN.drive([drive])

获取或设置引脚驱动强度, 可以是PIN.LOW_POWER, 

> PIN.NORMAL_POWER, PIN.MED_POWER, PIN.HIGH_POWER
> PIN.irq(handler=None, trigger=(PIN.IRQ_FALLING |
> PIN.IRQ_RISING|Pin.IRQ_LOW_LEVEL|Pin.BOTH |Pin.IRQ_HIGH_LEVEL))

配置要在引脚的触发源处于活动状态时调用的中断处理程序。如果引脚模式为PIN.IN, 则触发源是引脚上的外部值。如果引脚模式为PIN.OUT, 则触发源是引脚的输出缓冲区。这些参数是:
i.handler: 是一个可选的函数, 当中断触发时调用。handler必须只采用一个参数.
ii.trigger: 配置可以生成中断的事件。可能的值为

 - PIN.IRQ_FALLING, 在下降缘产生中断
 - PIN.IRQ_RISING, 在上升缘产生中断
 - PIN.IRQ_BOTH, 在上升或下降缘产生中断
 - PIN.IRQ_LOW_LEVEL, 在低电平中断
 - PIN.IRQ_HIGH_LEVEL, 在高电平中断

这些值可以或 ' 组合在一起, 以便在多个事件上触发

##4.11 Timer定时器
EasyPy有8个定时器，每个定时器由一个以用户定义的频率运行的独立计数器组成。它们可以设置为以特定间隔运行功能。8个定时器编号为0到7，但Timer 0保留供RGB LED内部使用。尽可能避免使用这些定时器。

让我们创建一个定时器对象：

    >>> tim = Timer(2,mode=Timer.PERIODIC) 

定时器的模式共有三种分别为ONE_SHOT, PERIODIC, 和PWM. 现在让我们看看我们刚刚创建的内容：

    >>> tim
    Timer(2, mode=Timer.PERIODIC)

> Timer(id, mode)

iii.id: 1~7, 0 is for RGB LED use
iv.mode = 
Timer.ONE_SHOT—定时器运行一次, 直到设置的时间周期过期
Timer.PERIODIC—以设置的频率定期运行
Timer.PWM—在引脚上输出 PWM 信号

EasyPy告诉我们tim附加到2号定时器，但它尚未初始化。所以让我们初始化它以10 Hz（每秒10次）触发：

    >>> tim.init(mode=Timer.PERIODIC)
    >>> tim.channel(Timer.A, freq=10)
    Timer.channel(Timer.0, freq=10)

> Timer.deinit( )

初始化定时器。它的模式有

Timer.ONE_SHOT—定时器运行一次, 直到设置的时间周期过期
Timer.PERIODIC—以设置的频率定期运行
Timer.PWM—在引脚上输出 PWM 信号

现在它已初始化，我们可以了解有关定时器的一些信息, 该信息意味着该定时器设置从0开始计数到设定频率数字使定时器触发为10 Hz, 此时它会触发中断。

> Timer.channel (channel, freq, period, duty_cycle=0)

 
如果只传递了通道标识符, 则返回以前初始化的信道对象 (如果没有以前的通道, 则为”无")。否则,将初始化并返回timechannel对象。操作模式是配置为用于创建信道的 timer 对象的模式.

v.channel: Timer.A, Timer.B, Timer.C, Timer.D
时间模式下的channel设定
Timer.TIMER_MATCHER_0 : Set timer channel 0.
Timer.TIMER_MATCHER_1 : Set timer channel 1.
Timer.TIMER_MATCHER_2 : Set timer channel 2.
Timer.TIMER_MATCHER_3 : Set timer channel 

PWM模式下的channel设定
Timer.TIMER_PWM_0 : Set PWM channel 0.
Timer.TIMER_PWM_1 : Set PWM channel 1.
Timer.TIMER_PWM_2 : Set PWM channel 2. 

vi.freq: Hz 为单位设置频率.
vii.period: 以毫秒(milliseconds)为单位设置周期.
**Note: 需要给频率或周期其中一个数值, 但不能同时都给.**
viii.duty_cycle: 适用于PWM模式。它是一个百分比 (0.0-100.00)。由于EasyPy不支持浮点数, 因此必须在0-10000 范围内指定占空比, 其中10000表示 100.00, 5050 表示 50.50, 依此类推.

    当信道处于 PWM 模式时, 将自动分配相应的PWM引脚, 因此无需通过pin类分配引脚的替代功能。支持 PWM 功能的引脚如下所示:
    

 | Timer | 	PWM Channel  | 	PWM pin |  	Timer | 	PWM Channel  | 	PWM pin 
 | ---   | ---            | --       | ---      | --               | -- 
| 0	| 0		|  | 4	| 0	|  | 

	1			1	
	2			2	
1	0	P12	5	0	
	1	P10		1	
	2	P4		2	
2	0	P9	6	0	P3
	1	P8		1	P2
	2	P15		2	P1
3	0	P14	7	0	P0
	1	P13		1	P7
	2	P16		2	P6
###4.11.1 定时器中断回调 (Callback)
我们接下来要做的是为定时器注册一个回调函数，以便在触发时执行（有关回调函数的介绍，请参阅开关教程）：

    >>> tim_a.irq(trigger=Timer.TIMEOUT,handler=toggle)
    

> timerchannel.irq(trigger, handler=None)

此回调函数的行为在很大程度上取决于定时器信道的操作模式:

 - 如果模式是Timer.PERIODIC, 回调函数将使用设置的频率或周期定期执行.
 - 如果模式为timer.ONE_SHOT, 则在设置的定时器过期时执行一次回调函数.
 - 如果模式是timer.PWM, 则在达到占空比值时执行回调函数.
i.trigger: Timer.TIMEOUT ( mode= Timer.PERIODIC或Timer.ONE_SHOT使用), Timer.MATCH (mode=Timer.PWM使用)
ii.handler: 当在触发时间中断时调用, 将执行一个可选的回调函数

在定时器的运行中, 您可以通过下面的方法来改变来更改频率, 周期, 和占空比：

> timerchannel.freq ([value])

获取或设置定时器信道频率 (以 Hz 为单位)。

> timerchannel.period ([value])

获取或设置定时器信道周期 (以毫秒为单位)。

> timerchannel.duty_cycle([value])

获取或设置 PWM 信号的占空比。它是一个百分比 (0.0-100.00)。由于ePy不支持浮点数, 因此必须在0-10000 范围内指定占空比, 其中10000表示 100.00, 5050 表示 50.50, 依此类推。

> Timer.deinit( )

停止定时器, 并禁用定时器外设。
###4.11.2 与时间相关的功能

utime模块提供了获取目前时间和日期、测量时间间隔和延迟的功能.

 
维护实际日历日期时间: 这需要系统时钟 (RTC)。在具有底层操作系统 (包括某些 RTOS) 的系统上, RTC 可能是隐式的。设置和维护实际日历时间是OS/RTOS的责任, 是在 EasyPython 之外完成的, 它只是使用操作系统 API 来查询日期时间。然而在裸机的系统时间取决于machine.RTC( )对象可以使用计算机设置当前日历时间machine.RTC().datetime(tuple)函数, 并通过以下方式进行维护:

 - 备用电池 (可能是特定主板的附加可选组件)。
 - 使用网络时间协议 (需要由 port/使用者设置)。
 - 由使用者在每次上电时手动设置 (许多主板在硬重置时仍保持RTC时间, 但在这种情况下, 有些主板可能需要再次设置RTC时间)。
 
如果实际日历时间未使用 system/EasyPython RTC 维护, 则下面需要引用当前绝对时间的函数可能不会像预期的那样。

> Utime.localtime([secs] )

将Epoch以秒为单位表示的时间转换为8元组, 其中包含: (年、月、月、日、小时、分钟、第二、工作日、日) 如果未提供, 或者没有, 则使用 RTC 的目前时间。

 - 年包括世纪 (例如 2014)。
 - 月份为1-12
 - m 日是1-31
 - 小时是0-23
 - 分钟是0-59
 - 秒是0-59
 - 周一至周日的工作日为0-6
 - 年日是1-366

> Utime.mktime( )

这是localtime时间的反函数。它的参数是一个完整的8元组, 它表示一个时间, 根据本地时间。它返回一个整数, 它是自2000年1月1日以来的秒数。

> utime.sleep(seconds)

在给定的秒数内睡眠。某些主板可能接受以秒作为浮点数, 以在数秒数的时间内休眠。请注意, 其他主板可能不接受浮点参数, 因为与它们兼容, 请使用sleep_ms()和sleep_us()函数。

> utime.sleep_ms(ms)

给定毫秒数的延迟, 应为正数或0。

> utime.sleep_us(us)

给定的微秒数的延迟, 应为正或0。
##4.12 RTC系统时钟
RTC是独立的时钟, 保持纪录日期和时间。
示例用法:

    from machine import RTC
    rtc = RTC(datetime=(2019, 4, 25, 9, 0, 0))  #创建RTC对象, 设定时间为2019/4/25 9:00:00
    print(rtc.now())

> RTC(datetime)

创建RTC物件。获取或设置RTC的日期和时间. 如果没有参数, 此方法将返回具有当前日期和时间的8元组。对于1个参数 (8 元组), 它设置日期和时间.

8元组具有以下格式:

(年、月、日、小时、分钟、秒)

> RTC.now()

获取当前日期时间。

> RTC.init(datetime)

初始化RTC。日期时间是表单的一个元组: (年、月、日 [、小时 [、分钟 [、秒 ]]])。

> RTC.deinit()

将RTC重置为 2015年1月1日, 并重新开始运行。

> RTC.alarm(time, repeat=False)

设置RTC警报。时间可以是将警报程序设计为目前时间 +time _ in _ second的秒值, 也可以是一个日期时间。如果所经过的时间以毫秒为单位, 则可以将重复设置为true, 以使警报定期发生。

i.time: 以秒为单位
repeat: 可以重复设置True or False
ii.time: 以日期时间为单位(year, month, day[, hour[, minute[, second]]])
repeat: 不可以重复设置False

> RTC. alarm_cancel()

取消正在运行的警报。
RTC.irq(trigger, handler=None)
创建由系统时钟警报触发的中断对象。

 - trigger必须是RTC.ALARM0
 - handler是触发中断时要调用的回调函数.
##4.13 加速度计
在这里，您将学习如何使用LED向左和向右倾斜等状态读取加速度计和信号。
###4.13.1 使用加速度计
EasyPy有一个加速度计（微小弹簧上的微小质量），可用于检测电路板的角度和运动。对于x，y，z方向中的每一个，存在不同的传感器。要获取加速度计的值，请创建Accel（）对象，然后调用x（）方法。

    >>> accel = Accel()
    >>> accel.x()

    7

这将返回一个有符号整数，其值介于-30和30之间。请注意，测量结果非常嘈杂，这意味着即使您保持电路板完全静止，您测量的数量也会有一些变化。因此，您不应使用x（）方法的确切值，而是查看它是否在某个范围内。

我们将首先使用加速度计打开灯，如果灯不平。

    from machine import Accel
    from machine import LED
    import utime
    
    accel = Accel()
    light = LED(3)
    
    while True:
        x = accel.x()			;X加速度
        if abs(x) > 10
            light.on()
        else:
            light.off()
    
    	utime.sleep_ms(100)

我们创建Accel和LED对象，然后获取加速度计的x方向的值。如果x的大小大于某个值，则LED会亮起，否则会关闭。循环有一个小的，utime.sleep_ms() 否则当x的值接近时，LED会恼人地闪烁 。尝试在ePy上运行此操作并左右倾斜电路板以使LED打开和关闭。

**练习：更改上面的脚本，使得倾斜EasyPy的蓝色LED越亮。提示：您需要重新调整值，强度从0到255。**
###4.13.2 制作反应层面
上面的示例仅对x方向上的角度敏感，但如果我们使用该y()值和更多LED，我们可以将EasyPy转换为反应级别。

    from machine import Accel
    from machine import LED
    import utime
    
    xlights = (LED(2), LED(3))
    ylights = (LED(1), LED(4))
    
    accel = Accel()
    
    while True:
        x = accel.x()
        if x > 10:
            xlights[0].on()
            xlights[1].off()
        elif x < -10:
            xlights[1].on()
            xlights[0].off()
        else:
            xlights[0].off()
            xlights[1].off()
    
        y = accel.y()
        if y > 10:
            ylights[0].on()
            ylights[1].off()
        elif y < -10:
            ylights[1].on()
            ylights[0].off()
        else:
            ylights[0].off()
            ylights[1].off()
    
        utime.sleep_ms(100)

我们首先为x和y方向创建一个LED对像元组。元组是python中的不可变对象，这意味着它们一旦被创建就无法修改。然后我们像以前一样继续操作，但为正负x值打开不同的LED。然后我们对y方向做同样的事情。这不是特别复杂，但它完成了这项工作。在你的EasyPy上运行它，你应该看到不同的LED打开，这取决于你如何倾斜板。

##4.14 串口
###4.14.1 串口基本概念
####4.14.1.1. 串口原理
串口通信的英文缩写是UART(Universal Asynchronous Receiver Transmitter) 全称是通用异步收发器。

听起来很高深的概念，其实就如下图，两个设备，一根线串起来，发送方在线的一头将数据转换为二进制序列，用高低电平按照顺序依次发送01信号，接收方在线的另一头读取这根信号线上的高低电平信号，对应转化为二进制的01序列。

异步收发指的就是全双工传输，即发送数据的同时也能够接收数据，两者同步进行，就如同我们的电话一样，我们说话的同时也可以听到对方的声音。

每当我们想要在PC和MCU之间或两个MCU之间进行通信时，最简单的方法就是使用UART。在两个UART之间传输数据只需要两根线。数据从发送UART的Tx引脚流向接收UART的Rx引脚。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps31267.png) 

串口通信原理示意
####4.14.1.2. 波特率
波特率(bandrate)是指，每秒钟我们的串口通信所传输的bit个数，通俗的讲就是在一秒内能够发送多少个1和0的二进制数。比如，波特率是9600，就意味着1S中可以发送9600个0和1组成的二进制序列。

####4.14.1.3. 发送端 TX 与 接收端 RX
UART通信基本上使用2个引脚进行数据传输。Tx-用于发送数据的发送数据的引脚，Rx-用于获取数据的接收数据的引脚。两个串口进行通信的话， 最少需要三根线相连。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps31580.png) 

RX 代表信息接收端，TX 代表信息发送端, GND代表电源地线

注意, 如果连接的模块并没有自主供电，还须连接VCC！
###4.14.2 串口操作
在ePy board上支持两组UART, 其硬件脚位定义如下, 在EasyPython中UART0_TxD, UART0_RxD已经被EasyPython中的REPL(Real Evaluate Print Loop)接口所使用，所以不要用EasyPythonn的指令去控制UART0。

| 脚位定义	| UART
| -- |-- 
| P6 (P0.2)	| UART0_TxD
| P7 (P0.3)	| UART0_RxD
| P8 (P4.0)	| UART1_TxD
| P9 (P4.1)	| UART1_RxD
####4.14.2.1 构建UART
UART 对象可以使用以下方法创建和初始化

    from machine import UART                # 导入UART machine
    
    uart=UART(1,baudrate=9600)  		# 构建UART1对象，设置波特率为9600

我们在此处构建UART1时，波特设为9600，后面才能通讯成功。请根据自己需要的连接串口的波特率自行设置。

> UART(id, baudrate)

i.id: 0 或 1, 分别指定UART0 或 UART1
ii.baudarte = 
波特率可以为9600, 14400, 19200, 38400, 57600, 115200, 230400, 460800 

一般只需设置上述参数即可，其他参数会保持默认参数。

UART 对象的作用类似于stream 对象, 读取和写入是使用标准流方法完成的, 下面将详细说明:

uart.read(10)       # 读取10个字符, 返回一个字节对象
uart.read()         # 读取所有可用字符
uart.readline()     # 读一行
uart.readinto(buf)  # 读取并存储到给定的缓冲区
uart.write('abc')   # 写3个字符
####4.14.2.2 串口发送
你可以使用串口助手来连接电脑。这样就可以实现板和电脑的通讯。您可以往串口发送字节数据:

    >>> from machine import UART
    >>> ser=UART(1,115200)
    >>> ser.write('abc')

这时，用串口助手看下，是否接受到易控板发过来的数据。write(buf) 函数为向串口写入（发送）字节数据，返回数据的长度。

> write(buffer)

将字节的缓冲区写入总线。传回值: 写入的字节数或超时时返回"无" 。
####4.14.2.3 串口读取
易控板接收串口数据，并将数据显示至REPL上:

> any( )

返回一个整数, 计算可以读取而不阻塞的字符数。如果没有可用字符, 它将返回 0, 如果有字符, 则返回正数。即使有多个字符可供读取, 该方法也可能返回1。

> read(nbys )

读取字符。如果指定了nbytes, 则最多读取那么多字节, 否则读取尽可能多的数据.
传回值: 包含读取的字节的字节对象。超时时返回无.。

> readinto(buf [, nbys] )

将字节读入buf。如果指定了nbytes, 则最多读取多个字节。否则, 最多读取len (buf)字节.
传回值: 读取并存储到buf或超时时返回无.。

> readline( )

读取行, 以换行字符结尾。
传回值: 读取的行或超时时返回"无".。

        from machine import UART                               # 导入UART machine
        
        uart=UART(1,baudrate=9600)    # 实例UART，设置波特率9600
        
        while True:
            if(uart.any()):                     # 当串口有可读数据时
                data = uart.readline()          # 从串口读取一行数据
                print("received:",data)         #
    
     打印接收到的数据

这时你可以通过串口助手向串口发送数据，当易控板接收到串口数据后，打印并显示至REPL。在while循环中,轮询使用 uart.any() 判断串口中是否有可读数据，当有数据时，用 uart.readline() 读取一行数据。除了 UART.readline() 读取数据，还可以使用 UART.read(length) 从串口读取指定长度的数据。
###4.14.3 拓展
学会了如何使用串口后，你就可以实现易控板与其他MCU(Arduino)、电脑/手机、电子模块间的通讯。应用更为广泛，您可发挥你想象，如何用好串口，做出更有趣的东西！
##4.15 I2C
I²C（Inter-Integrated Circuit）字面上的意思是集成电路之间，它其实是I²C Bus简称。I2C总线类型是由飞利浦半导体公司在八十年代初设计出来的一种简单、双向、二线制、同步串行总线，主要是用来连接整体电路(ICS)

I2C协议是多个设备仅使用两条线（时钟和数据线）相互通信的一种方式。任何设备都可以是控制I2C时钟和数据线以与其他设备通信的主设备。 每个I2C器件都分配有一个唯一的地址，用于在读写操作期间识别它。当设备看到其在I2C总线上发送的地址时，它会响应请求，当它看到不同的地址时，它会忽略它。 使用唯一地址，许多设备可以共享相同的I2C总线而不会产生干扰。


----------


在使用易控板，您可以使用 I2C类别函数与I2C总线上的设备进行交互。在大多数情况下，您将充当I2C“主设备”，可以与其他I2C设备读写数据。 您还可以充当I2C“从属”或外设，它们分配了一个地址，可以监听和响应来自其他I2C设备的请求。ePy board易控板可以支持2个I2C接口界面来与从机设备通信, 其脚位定义如下。

| 脚位定义	| I2C 1	| I2C 2
| --| --| --
| SCL	| P19 (P4.8)	| P27 (P0.0)
| SDA	| P20 (P4.9)	| P28 (P0.1)
###4.15.1 Master主设备
大部分I2C通讯类模块，操作方法类似。ePy board易控板充当I2C主设备，模块作为从机设备，响应主机请求。I2C对象可以在创建时初始化, 也可以在以后初始化。示例用法: 

    from machine import I2C
    
    i2c = I2C(1,freq=400000)      	# 创建频率为400khz 的 I2C 外设, 选择要使用的外设 I2C 1
    
    i2c.read(1, 0x40, buf, 8, 1) 	# 读取8个字节从从设备地址 40
    i2c.write(1, 0x40, buf1, 8, 1)	# 写8个字节到从设备地址 40

> I2C(id, speed)

使用以下参数构造并返回新的 I2C 物件:

 - id标识特定的 I2C 外设。1为I2C1; 2为I2C2.


 - speed应该是一个整数, 它设置 SCL 的最大频率. 
  - o100000 : 100 KHz
  - o400000 : 400 KHz
  - o1000000: 1 MHz 
  

> I2C.deinit( )

关闭 I2C 总线.

> I2C.read(i2c_id, slave_addr, data_buffer_addr, buffer_len, stop)

从addr指定的从属中读入buffer。读取的字节数将是buffer的长度。如果停止为真, 则会在传输结束时生成 stop 条件. 该方法返回"无".

 - i2c_id: id标识特定的 I2C 外设。1为I2C1; 2为I2C2.
 -  slave_addr: 从设备地址ID.
 -  data_buffer_addr: 字节的buffer地址. 
 -  length: 数据长度. 
 - stop condition: 设定停止条件为自动.

> I2C.write(i2c_id, slave_addr, data_buffer_addr,
> 
>  buffer_len, stop)

将字节从buffer写入addr指定的从设备. 如果在从 buffer 写入字节后收到 NACK, 则不会发送剩余的字节。如果停止为真, 则在传输结束时生成 stop 条件, 即使收到了 nack 也是如此。该函数返回接收到的 Ack 数.
 -  i2c_id: id标识特定的 I2C 外设。1为I2C1; 2为I2C2.
 -  slave_addr: 从设备地址ID.
 -  data_buffer_addr: 字节的buffer地址. 
 -  length: 数据长度. 
 -  stop condition: 设定停止条件为自动.
##4.16 SPI
SPI 是一种由主机驱动的同步串行协议。在物理级别, 总线由3条线路组成: SCK、MOSI、MISO。多个设备可以共享同一总线。每个设备都应该有一个单独的, 第四个信号, SS (从选择), 以选择与之通信的总线上的特定设备。SS 信号的管理应在用户代码中进行. 其框架图如下

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps35850.png) 

同步串行端口 (SSP) 控制器可以在 SPI 和4线 SSI 总线上运行。它与总线上的多个主设备和从设备交互。在给定的数据传输过程中, 只有一个主机和一个从站可以在总线上进行通信。数据传输原则上是全双工, 与4到16位数据的框架流动从主设备到从机和从机到主设备。实际上, 这些数据流中往往只有一个带有有意义的数据。

SSP 的特点包括:

 - 兼容摩托罗拉 SPI 和4线 TI SSI 总线。
 -  同步串行通信。
 -  支持主操作或从操作。
 -  8帧 FIFO, 用于发射机和接收机。
 -  4位到16位帧。
 -  主模式下最大 SPI 速度为 40 MHz, 从模式下最大 Spi 速度为 40 MHz
 -  数据传输格式来自由寄存器控制的 MSB 或 LSB
 -  数据采集位置选择的起始阶段为一相或二相控制寄存器
 
大部分SPI通讯类模块，操作方法类似。ePy board易控板可以支持2个SPI接口界面来与从机设备通信, 其脚位定义如下。

| 脚位定义	| SPI 0	| SPI 1
| --| --| --
| CS	| P23 (P0.14)	| P16 (P3.12)
| CLK	| P24 (P0.15)	| P13 (P3.13)
| MISO	| P25 (P1.0)	| P14 (P3.14)
| MOSI	| P26 (P1.1)	| P15 (P3.15)
SPI对象可以在创建时初始化, 也可以在以后初始化。示例用法: 

    from machine import SPI
    
    spi=SPI(0,mode=SPI.MASTER, baudrate=20000000)  
    #创建频率为20MHz的SPI外设, 选择要使用的外设 SPI 0
    
    spi.read(5) 				# 读取5个字节
    spi.write(‘hello’)				# 写5个字节

> SPI.init(ch, mode=SPI.MASTER, baudrate=1000000, polarity=0, phase=0)

在给定总线上构造一个 SPI 对象, ch。ch 的值取决于特定的端口及其硬件。值0、1等通常用于选择硬件 SPI 块 #0、#1 等, 使用以下参数构造并返回新的 SPI 对象:

 - ch标识特定的 SPI 外设。0为SPI0; 1为SPI1.
 - mode =SPI.MASTER(主), SPI.SLAVE (从)
 - baudrate =40000000, 20000000, 10000000, 5000000, 2500000, 1250000. 它应该是一个整数, 它设置 SCLK 的时钟速率. 一般建议使用20MHz
 - polarity = 0 (SCK idles at Low level), 1 (SCK idles at High level). 可以是0或1, 并且是空闲时钟线所处的级别.
 - phase = 0 (Sample at 1st edge), 1 (Sample at 2nd edge). 可以是0或 1, 分别用于采样第一或第二时钟边缘上的资料.
  - opolarity=0, phase=0 : MODE 0
  - opolarity=0, phase=1 : MODE 1
  - opolarity=1, phase=0 : MODE 2
  - opolarity=1, phase=1 : MODE 3

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps37210.png) 

> SPI.deinit()

关闭 SPI 总线.

> SPI.write(buf)

写入buffer中包含的字节但不可超过4096字节。返回无.

> SPI.read(nbytes)

读取nbytes指定的字节数但不可超过4096字节。返回包含已读取数据的字节对象. 
> SPI.readinto(buf)

读取buffer指定的缓冲区但不可超过4096字节。返回无. 

> SPI.write_readinto(write_buf, read_buf)

在读取到read_ buf时, 写入来自write _ buf的字节但buffer不可超过4096字节。缓冲区可以是相同的, 也可以是不同的, 但两个缓冲区的长度必须相同。返回无.












##4. 打开LED和基本的Python概念

在EasyPy上最简单的方法是打开连接到电路板的LED。连接电路板，并按照教程1中的说明登录。我们将从解释器中的转动和LED开始，键入以下内容

    >>> myled = pyb.LED(1)
    >>> myled.on()		;开
    >>> myled.off()		;关

这些命令可以打开和关闭LED。

这一切都很好，但我们希望这个过程是自动化的。在您喜欢的文本编辑器中打开EasyPy上的文件MAIN.PY。将以下行写入或粘贴到文件中。如果您是python的新手，那么请确保缩进正确，因为这很重要！

    led = pyb.LED(2)
    while True:		;当真的
        led.toggle()
        pyb.delay(1000)		;延迟

保存时，EasyPy上的红灯应亮约一秒钟。要运行脚本，请执行软重置（CTRL-D）。然后EasyPy将重新启动，您应该看到绿灯持续闪烁。成功，是你建立邪恶机器人军队的第一步！当您对烦人的闪光灯感到厌倦时，请按下终端上的CTRL-C以停止运行。

那么这段代码有什么用呢？首先，我们需要一些术语。Python是一种面向对象的语言，几乎python中的所有东西都是一个类，当你创建一个类的实例时，你会得到一个对象。类具有与之关联的方法。方法（也称为成员函数）用于与对象交互或控制对象。

第一行代码创建了一个LED对象，然后我们称之为led对象。当我们创建对象时，它需要一个参数，该参数必须在1到4之间，对应于电路板上的4个LED。pyb.LED类有三个我们将使用的重要成员函数：on（），off（）和toggle（）。我们使用的另一个函数是pyb.delay（），这只是等待一个给定的时间，以毫秒为单位。一旦我们创建了LED对象，声明为True：创建一个无限循环，在打开和关闭之间切换LED并等待1秒。

**练习：尝试更改切换LED和打开不同LED之间的时间。**

**练习：直接连接到EasyPy，创建一个pyb.LED对象并使用on（）方法将其打开。**

##4.1. 闪动您EasyPy 
到目前为止，我们只使用了一个LED，但是EasyPy有4个可用。让我们首先为每个LED创建一个对象，以便我们可以控制每个LED。我们通过创建具有列表理解的LEDS列表来实现这一点。

    leds = [pyb.LED(i) for i in range(1,5)]

如果使用不是1,2,3,4的数字调用pyb.LED（），您将收到错误消息。接下来，我们将设置一个无限循环，循环通过每个LED打开和关闭它们。

    n = 0
    while True:
      n = (n + 1) % 4
      leds[n].toggle()
      pyb.delay(50)

这里，n跟踪当前LED，每次循环执行时我们循环到下一个n（％符号是模数运算符，保持n在0和3之间。）然后我们访问第n个LED并切换它。如果你运行它，你应该看到每个LED都打开然后所有LED按顺序再次关闭。

您可能会发现的一个问题是，如果您停止脚本然后再次启动它，那就是LED从上一次运行中停留，破坏了我们精心编排的迪斯科舞厅。我们可以通过在初始化脚本然后使用try / finally块关闭所有LED来解决这个问题。当您按CTRL-C时，EasyPython会生成VCPInterrupt异常。异常通常意味着出现了问题，您可以使用try：命令来“捕获”异常。在这种情况下，只是用户中断脚本，因此我们不需要捕获错误，只是告诉EasyPython退出时要做什么。finally块执行此操作，我们使用它来确保所有LED都关闭。完整的代码是：

    leds = [pyb.LED(i) for i in range(1,5)]
    for l in leds:
        l.off()
    
    n = 0
    try:
       while True:
          n = (n + 1) % 4
          leds[n].toggle()
          pyb.delay(50)
    finally:
        for l in leds:
            l.off()

###4.2.特殊LED控制
黄色和蓝色LED是特殊的。除了打开和关闭它们，您还可以使用intensity（）方法控制它们的强度。这需要一个0到255之间的数字来确定它的亮度。以下脚本使蓝色LED逐渐变亮，然后再将其关闭。

    led = pyb.LED(4)
    intensity = 0
    while True:
        intensity = (intensity + 1) % 255
        led.intensity(intensity)			;LED亮度
        pyb.delay(20)

您可以在LED 1和2上调用intensity（），但它们只能关闭或打开。0将它们关闭，最多255个任何其他数字将它们打开。
##5. 按键Switch，回调和中断
EasyPy有5个小开关，标有A, B, C, D和RST。RST开关是一个硬复位开关，如果按下它，它会从头开始重新启动EasyPy，相当于关闭电源然后再打开电源。

A, B, C, D开关用于一般用途，并通过按键Switch对象进行控制。要使切换对象执行：

    >>> sw = pyb.Switch(A)

请记住，如果您收到名称不存在的错误，则可能需要键入内容。`import pybpyb`

使用switch对象，您可以获得其状态：
>>> sw.value(A)
False
False如果未保持开关或保持开关，将打印True。尝试在运行上述命令时按住Switch开关A。
通过“调用”开关对象，还有一个简写符号来获取开关状态：

    >>> sw(A)
    False

###5.1. 切换回调
该开关是一个非常简单的对象，但它确实有一个高级功能：该`sw.callback()`功能。回调函数设置在按下开关时运行的东西，并使用中断。在了解中断如何工作之前，最好先从一个例子开始。尝试在提示符下运行以下命令：

    >>> sw.callback(lambda:print('press!'))

这告诉开关`press!`每次按下开关时都要打印。继续尝试：按下Switch开关并观察PC上的输出。请注意，此打印将中断您键入的任何内容，并且是异步运行的中断例程的示例。
另一个例子尝试：

    >>> sw.callback(lambda:pyb.LED(1).toggle())

这将在每次按下开关时切换红色LED。在其他代码运行时它甚至可以工作。
要禁用交换机回调，请传递`None`给回调函数：

    >>> sw.callback(None)

您可以将任何函数（接受零参数）传递给交换机回调。上面我们使用lambdaPython 的特性来动态创建一个匿名函数。但我们同样可以做到：

    >>> def f():
    ...   pyb.LED(1).toggle()
    ...
    >>> sw.callback(f)

这将创建一个名为的函数f，并将其分配给交换机回调。当你的函数比lambda允许的更复杂时，你可以这样做 。

请注意，您的回调函数不能分配任何内存（例如，它们不能创建元组或列表）。回调函数应该相对简单。如果您需要创建一个列表，请事先将其创建并将其存储在全局变量中（或将其置于本地并关闭它）。如果需要进行长而复杂的计算，则使用回调设置一个标志，然后其他一些代码会响应。

###5.2. 中断的技术细节
让我们逐步了解交换机回调发生的细节。使用时注册功能时`sw.callback()`，开关会在交换机所连接的引脚上设置外部中断触发（下降沿）。这意味着微控制器将在引脚上侦听任何更改，并将发生以下情况：

 1. 按下开关时，引脚发生变化（引脚从低电平变为高电平），微控制器记录此变化。

 2. 微控制器完成当前机器指令的执行，停止执行并保存其当前状态（将寄存器推入堆栈）。这具有暂停任何代码的效果，例如您正在运行的Python脚本。
 
 3. 微控制器开始执行与开关外部触发相关的特殊中断处理程序。此中断处理程序获取您注册的函数sw.callback()并执行它。
  
 4. 执行回调函数直到完成，将控制权返回给开关中断处理程序。
 
 5. 开关中断处理程序返回，并通知微控制器已经处理了中断。
 
 6. 微控制器恢复在步骤2中保存的状态。
 
 7. 继续执行一开始运行的代码。除了暂停，此代码不会注意到它被中断。

当多个中断同时发生时，上述事件序列会变得复杂一些。在这种情况下，具有最高优先级的中断首先进行，然后按优先级顺序进行其他中断。开关中断设置为最低优先级。

###5.3. 进一步阅读
有关使用硬件中断的更多信息，请参阅  [编写中断处理程序](http://baidu.com)。

##6.点亮RGB LED

    from easypython import *
    
    rgb[0] = (255, 0, 0)  # 设置为红色，全亮度
    rgb[1] = (0, 128, 0)  # 设定为绿色，半亮度
    rgb[2] = (0, 0, 64)   # 设置为蓝色，四分之一亮度
    rgb.write()

首先导入EasyPython模块:

    from easypython import *

注解

导入EasyPython模块后，会为易控创建一个NeoPixel对象rgb, 控制板载的RGB只需对rgb对象操作。

设置颜色:

    rgb[0] = (255, 0, 0)  # 设置为红色，全亮度
    rgb[1] = (0, 128, 0)  # 设定为绿色，半亮度
    rgb[2] = (0, 0, 64)   # 设置为蓝色，四分之一亮度

注解
> * rgb[n] = (r, g, b) 可以设置每个像素点颜色，n 为板载RGB灯的个数，第一个灯为0。 r、g、b 为颜色亮度值，范围值为0~255。
> * rgb.fill(rgb_buf) 可以填充所有像素点的颜色，如：rgb.fill((255,0,0))，所有RGB灯设置为红色，全亮度。

将颜色输出到RGB灯:

    rgb.write()

###6.2. 外部彩带
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps23.png) 

例：点亮外部彩带

    from mpython import *
    import neopixel
    np = neopixel.NeoPixel(Pin(Pin.P15), n=24,bpp=3,timing=1)
    
    
    def wheel(pos):
        # 通过改变在0和255之间的每个颜色参数产生彩虹色光谱
        # Input a value 0 to 255 to get a color value.
        # The colours are a transition r - g - b - back to r.
        if pos < 0 or pos > 255:
            r = g = b = 0
        elif pos < 85:
            r = int(pos * 3)
            g = int(255 - pos*3)
            b = 0
        elif pos < 170:
            pos -= 85
            r = int(255 - pos*3)
            g = 0
            b = int(pos*3)
        else:
            pos -= 170
            r = 0
            g = int(pos*3)
            b = int(255 - pos*3)
        return (r, g, b)
    
    def cycle(np,r,g,b,wait=20):
        # 循环效果,有一个像素在所有灯带位置上运行，而其他像素关闭。
        for i in range(4 * np.n):
            for j in range(np.n):
                np[j] = (0, 0, 0)
            np[i % np.n] = (r, g, b)
            np.write()
            sleep_ms(wait)
    
    def bounce(np,r,g,b,wait=20):
        # 弹跳效果,等待时间决定了弹跳效果的速度
        n=np.n
        for i in range(4 * n):
            for j in range(n):
                np[j] = (r, g, b)
            if (i // n) % 2 == 0:
                np[i % n] = (0, 0, 0)
            else:
                np[n - 1 - (i % n)] = (0, 0, 0)
            np.write()
            sleep_ms(wait)
    
    def rainbow_cycle(np,wait_us):
        # 彩虹效果
        n=np.n
        for j in range(255):
            for i in range(n):
                pixel_index = (i * 256 // n) + j
                np[i] = wheel(pixel_index & 255)
            np.write()
            sleep_us(wait_us)
    
    while True:
        cycle(np,50,50,50,wait=20)
        bounce(np,50,0,0,wait=20)
        rainbow_cycle(np,20)

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps24.jpg) 

cycle循环效果

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps25.jpg) 


bounce弹跳效果

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps26.jpg) 

rainbow彩虹效果

如果需要使用外部彩带，要先创建一个neopixel对象,定义 `pin` 、`bpp` 、 `timeing` 参数，然后才能通过该对象控制彩带上的LED。 更详细的使用方法，请查阅 neopixel 模块 。

提示

EasyPyhton提供 `neopixel` 增强版`ledstrip` 模块，已封装有更丰富的neopixel显示效果，操作简单。

##7. 音乐
易控板板载无源蜂鸣器，其声音主要是通过高低不同的脉冲信号来控制而产生。声音频率可控，频率不同，发出的音调就不一样，从而可以发出不同的声音，还可以做出“多来米发索拉西”的效果。
###7.1. 内置旋律
易控板有很多内置的旋律，完整的清单如下：

 - `music.DADADADUM`
 - `music.ENTERTAINER`
 - `music.PRELUDE`
 - `music.ODE`
 - `music.NYAN`
 - `music.RINGTONE`
 - `music.FUNK`
 - `music.BLUES`
 - `music.BIRTHDAY`
 - `music.WEDDING`
 - `music.FUNERAL`
 - `music.PUNCHLINE`
 - `music.PYTHON`
 - `music.BADDY`
 - `music.CHASE`
 - `music.BA_DING`
 - `music.WAWAWAWAA`
 - `music.JUMP_UP`
 - `music.JUMP_DOWN`
 - `music.POWER_UP`
 - `music.POWER_DOWN`
 

我们可以播放一些内置旋律:


    import music
    
    music.play(music.BIRTHDAY)

> 提示 
>music.BIRTHDAY指内置旋律的名称，如若播放其它旋律，只需把music.BIRTHDAY更换为想要播放的旋律即可。

除了播放内置旋律，我们还可以自编乐谱。

###7.2. 自编乐谱
我们可以通过设置音调来自编乐谱。

    import music
    
    tune = ["C4:4", "D4:4", "E4:4", "C4:4", "C4:4", "D4:4", "E4:4", "C4:4",
            "E4:4", "F4:4", "G4:8", "E4:4", "F4:4", "G4:8"]
    music.play(tune)

每个音符都有一个名字（比如C＃或F），一个八度和一个持续时间。八度用数字表示〜0表示最低八度，4表示中央C，8表示您需要的高度。持续时间也表示为数字。 持续时间的值越高，持续时间越长。例如，持续时间4将持续两倍于持续时间2（依此类推）。 每个音符都表示为一串字符，如下所示：

    NOTE[octave][:duration]

例如，C4：4指的是八度音阶4中的音符“C”，持续4个音阶。如果使用音符名称R，则将其视为休息（静音）。

###7.3. 频率
您还可以通过频率设置来制作一些非音符的音调。 例如，创建警笛效果：

    import music
    
    while True:
        for freq in range(880, 1760, 16):
            music.pitch(freq, 20)
        for freq in range(1760, 880, -16):
            music.pitch(freq,20)

在这个实例中是如何使用 `music.pitch` 方法，它需要一个频率。 其中range函数用于生成数值范围。这些数字用于定义音调的高低。 range函数有三个参数，分别是起始值，结束值和步长。因此，range的第一次使用是“以16的步长创建880到1760之间的数字范围”； 第二个次是“以-16”的步长创建1760到880之间的一系列值，持续频率为20毫秒。因此获得像警报器一样在频率上升和下降的频率范围而制作出警笛效果。

##8. 麦克风
易控板板载麦克风，可以用其感知周边环境的声音变化。
例：显示声音值

    from easypython import *
    
    while True:
        oled.fill(0)
        oled.DispChar('声音：',0,16)
        oled.DispChar("%d" % (sound.read()),40,20)
        oled.show()

使用前，导入EasyPython模块

    from easypython import *

我们使用 `sound.read()` 获取麦克风的数据。

    sound.read()

> 注解 
麦克风使用 read() 函数来读取数据。返回的值为12bit的ADC采样数据，即最大值为十进制4095。

学会了如何收集周边环境的声音数据，我们可以结合其他功能做更多有趣的场景。

##9. 光线传感器
易控板板载光线传感器，可以用其感知周边环境的光线变化。

例：光控灯:

    from easypython import *
    
    while True:
        oled.fill(0)                                   #清屏
        oled.DispChar("亮度:",30,16)                    #显示亮度
        oled.DispChar("%d" % (light.read()), 60, 16)    #显示板载光线传感器
        oled.show()                                     #刷新
        sleep_ms(100)                                   #延时100ms
    
        if light.read() < 200 :                    # 当光线小于200，灯亮
            rgb.fill((50,50,50))
            rgb.write()
        else:                                      # 否则，灯灭
            rgb.fill((0,0,0))
            rgb.write()

使用 light 对象来获取光线传感器数据:

    light.read()

> 注解 
光线传感器使用 read() 函数来读取数据。返回的值为12bit的ADC采样数据，即最大值为十进制4095。

学会了如何收集周边环境的光线数据，我们可以结合其他功能做更多有趣的场景。

##10. 加速度计
在这里，您将学习如何使用LED向左和向右倾斜等状态读取加速度计和信号。

###10.1. 使用加速度计
EasyPy有一个加速度计（微小弹簧上的微小质量），可用于检测电路板的角度和运动。对于x，y，z方向中的每一个，存在不同的传感器。要获取加速度计的值，请创建pyb.Accel（）对象，然后调用x（）方法。

    >>> accel = pyb.Accel()
    >>> accel.x()
    7

这将返回一个有符号整数，其值介于-30和30之间。请注意，测量结果非常嘈杂，这意味着即使您保持电路板完全静止，您测量的数量也会有一些变化。因此，您不应使用x（）方法的确切值，而是查看它是否在某个范围内。

我们将首先使用加速度计打开灯，如果灯不平。

    accel = pyb.Accel()
    light = pyb.LED(3)
    SENSITIVITY = 3		;宁敏度
    
    while True:
        x = accel.x()			;加速度
        if abs(x) > SENSITIVITY:
            light.on()
        else:
            light.off()
    
        pyb.delay(100)

我们创建Accel和LED对象，然后获取加速度计的x方向的值。如果x的大小大于某个值SENSITIVITY，则LED会亮起，否则会关闭。循环有一个小的，pyb.delay() 否则当x的值接近时，LED会恼人地闪烁 SENSITIVITY。尝试在EasyPy上运行此操作并左右倾斜电路板以使LED打开和关闭。

**练习：更改上面的脚本，使得倾斜EasyPy的蓝色LED越亮。**

**提示：您需要重新调整值，强度从0到255。**

###10.2. 制作精神层面
上面的示例仅对x方向上的角度敏感，但如果我们使用该y()值和更多LED，我们可以将EasyPy转换为精神级别。

    xlights = (pyb.LED(2), pyb.LED(3))
    ylights = (pyb.LED(1), pyb.LED(4))
    
    accel = pyb.Accel()
    SENSITIVITY = 3
    
    while True:
        x = accel.x()
        if x > SENSITIVITY:
            xlights[0].on()
            xlights[1].off()
        elif x < -SENSITIVITY:
            xlights[1].on()
            xlights[0].off()
        else:
            xlights[0].off()
            xlights[1].off()
    
        y = accel.y()
        if y > SENSITIVITY:
            ylights[0].on()
            ylights[1].off()
        elif y < -SENSITIVITY:
            ylights[1].on()
            ylights[0].off()
        else:
            ylights[0].off()
            ylights[1].off()
    
        pyb.delay(100)

我们首先为x和y方向创建一个LED对像元组。元组是python中的不可变对象，这意味着它们一旦被创建就无法修改。然后我们像以前一样继续操作，但为正负x值打开不同的LED。然后我们对y方向做同样的事情。这不是特别复杂，但它完成了这项工作。在你的EasyPy上运行它，你应该看到不同的LED打开，这取决于你如何倾斜板。

##11. 安全模式和出厂重置
如果你的EasyPy出了问题，不要惊慌！你几乎不可能通过编写错误的东西来打破EasyPy。

首先要尝试的是进入安全模式：这会暂时跳过执行boot.py和，main.py并提供默认的USB设置。

如果文件系统有问题，可以进行恢复出厂设置，将文件系统恢复到原始状态。

###11.1. 安全模式
要进入安全模式，请执行以下步骤：

 1. 将EasyPy连接到USB，以便打开电源。
 2. 按住USR开关。
 3. 在按住USR的同时，按下并释放RST开关。
 4. 然后LED将循环绿色变为橙色至绿色+橙色并再次返回。
 5. 继续按住USR直到只有橙色LED亮起，然后松开USR开关。
 6. 橙色LED应快速闪烁4次，然后熄灭。
 7. 您现在处于安全模式。

在安全模式下，不会执行`boot.py`和`main.py`文件，因此EasyPy将使用默认设置启动。这意味着您现在可以访问文件系统（应该出现USB驱动器），您可以编辑`boot.py` 并`main.py`修复任何问题。

进入安全模式是临时的，不会对EasyPy上的文件进行任何更改。

###11.2. 出厂重置文件系统
如果你的EasyPy的文件系统被破坏了（例如，你忘了弹出/卸除它），或者你有一些代码`boot.py`或者`main.py`你无法逃脱，那么你可以重置文件系统。

重置文件系统删除的内部EasyPy存储（不是SD卡）的所有文件，并恢复文件`boot.py`，`main.py`，`README.txt` 并`pybcdc.inf`返回到原来的状态。

要对文件系统进行恢复出厂设置，请按照与进入安全模式类似的步骤进行操作，但要将绿色+橙色上的USR释放：

1. 将EasyPy连接到USB，以便打开电源。
2. 按住USR开关。
3. 在按住USR的同时，按下并释放RST开关。
4. 然后LED将循环绿色变为橙色至绿色+橙色并再次返回。
5. 继续按住USR，直到绿色和橙色LED都亮起，然后松开USR开关。
6. 绿色和橙色LED应快速闪烁4次。
7. 红色LED将亮起（因此红色，绿色和橙色现在亮起）。
8. EasyPy现在正在重置文件系统（这需要几秒钟）。
9. LED全部关闭。
10. 您现在有一个重置文件系统，并处于安全模式。
11. 按下并释放RST开关以正常启动。

##12. 使EasyPy充当USB鼠标
EasyPy是一个USB设备，可以配置为鼠标而不是默认的USB闪存驱动器。

为此，我们必须首先编辑`boot.py`文件以更改USB配置。如果你还没有触及你的`boot.py`文件，那么它看起来像这样：

    # boot.py -- run on boot-up						; 在启动时
    # can run arbitrary Python, but best to keep it minimal		;运行＃可以运行任意Python，但最好保持最小化
    
    import pyb
    #pyb.main('main.py') # main script to run after this one			; 在此之后运行的#main脚本
    #pyb.usb_mode('VCP+MSC') # act as a serial and a storage device		; 充当串口和存储设备
    #pyb.usb_mode('VCP+HID') # act as a serial device and a mouse			; 充当串行设备和鼠标

要启用鼠标模式，请取消注释文件的最后一行，使其看起来像：

    pyb.usb_mode('VCP+HID') # act as a serial device and a mouse	; 充当串行设备和鼠标

如果您已经更改了boot.py文件，那么它需要工作的最小代码是：

    import pyb
    pyb.usb_mode('VCP+HID')

这告诉EasyPy在启动时将自身配置为VCP（虚拟COM端口，即串行端口）和HID（人机接口设备，在我们的例子中是鼠标）USB设备。

弹出/卸除EasyPy驱动器并使用RST开关重置它。您的PC现在应该将EasyPy检测为鼠标！

###12.1. 手动发送鼠标事件
要让py-mouse执行任何操作，我们需要将鼠标事件发送到PC。我们将首先使用REPL提示手动执行此操作。使用串行程序连接到EasyPy并输入以下内容：

    >>> hid = pyb.USB_HID()
    >>> hid.send((0, 10, 0, 0))

你的鼠标应该向右移动10个像素！在上面的命令中，您将发送4条信息：按钮状态，x，y和滚动。数字10告诉PC，鼠标在x方向上移动了10个像素。

让我们让鼠标左右摆动：

    >>> import math
    >>> def osc(n, d):
    ...   for i in range(n):
    ...     hid.send((0, int(20 * math.sin(i / 10)), 0, 0))
    ...     pyb.delay(d)
    ...
    >>> osc(100, 50)

函数的第一个参数osc是要发送的鼠标事件的数量，第二个参数是事件之间的延迟（以毫秒为单位）。尝试使用不同的数字。

**练习：让鼠标围成一圈。**

###12.2. 用加速度计制作鼠标
现在让我们使用加速度计，根据EasyPy的角度移动鼠标。可以在REPL提示符下直接输入以下代码，也可以将其放入`main.py`文件中。在这里，我们将投入，`main.py`因为要做到这一点，我们将学习如何进入安全模式。

目前，EasyPy充当串行USB设备和HID（鼠标）。因此，您无法访问文件系统来编辑`main.py`文件。

您也无法编辑您`boot.py`的HID模式并使用USB驱动器返回正常模式...

为了解决这个问题，我们需要进入安全模式。这在[安全模式教程]（tut-reset）中有描述，但我们在此重复说明：

1. 按住USR开关。
2. 在按住USR的同时，按下并释放RST开关。
3. 然后LED将循环绿色变为橙色至绿色+橙色并再次返回。
4. 继续按住USR直到只有橙色LED亮起，然后松开USR开关。
5. 橙色LED应快速闪烁4次，然后熄灭。
6. 您现在处于安全模式。

在安全模式下，不会执行`boot.py`和`main.py`文件，因此EasyPy将使用默认设置启动。这意味着您现在可以访问文件系统（应该出现USB驱动器），您可以编辑`main.py`。（保持`boot.py`原样，因为我们仍然希望在完成编辑后返回HID模式`main.py`。）

在`main.py`下面的代码中：

    import pyb
    
    switch = pyb.Switch()
    accel = pyb.Accel()
    hid = pyb.USB_HID()
    
    while not switch():
        hid.send((0, accel.x(), accel.y(), 0))
        pyb.delay(20)

保存文件，弹出/卸除EasyPy驱动器，然后使用RST开关重置它。它现在应该充当鼠标，并且板的角度将移动鼠标。尝试一下，看看你是否可以让鼠标静止不动！

按USR开关可停止鼠标移动。

您会注意到y轴是反转的。这很容易解决：只需在hid.send()上面一行中的y坐标前面加一个减号。

###12.3. 将EasyPy恢复正常
如果您按原样保留EasyPy，每次插入时它都会像鼠标一样。您可能希望将其更改回正常状态。要执行此操作，您需要先进入安全模式（参见上文），然后编辑该`boot.py`文件。在`boot.py`文件中，注释掉（在前面放一个＃）`VCP+HID`设置的行 ，所以它看起来像：

    #pyb.usb_mode('VCP+HID') # act as a serial device and a mouse		; 充当串行设备和鼠标

保存文件，弹出/卸除驱动器，然后重置EasyPy。它现在恢复正常运行模式。

##13. 定时器
EasyPy有14个定时器，每个定时器由一个以用户定义的频率运行的独立计数器组成。它们可以设置为以特定间隔运行功能。14个定时器编号为1到14，但3个保留供内部使用，5和6用于伺服和ADC / DAC控制。尽可能避免使用这些定时器。

让我们创建一个定时器对象：

    >>> tim = pyb.Timer(4)
    现在让我们看看我们刚刚创建的内容：
    >>> tim
    Timer(4)

EasyPy告诉我们tim附加到4号定时器，但它尚未初始化。所以让我们初始化它以10 Hz（每秒10次）触发：

    >>> tim.init(freq=10)

现在它已初始化，我们可以看到有关定时器的一些信息：

    >>> tim
    Timer(4, prescaler=624, period=13439, mode=UP, div=1)

该信息意味着该定时器设置为以外围时钟速度除以624 + 1运行，它将从0到13439计数，此时它会触发中断，然后从0再次开始计数。这些数字是设置为使定时器触发为10 Hz：定时器的源频率为84MHz（通过运行找到tim.source_freq()），因此我们得到84MHz / 625/13440 = 10Hz。

###14.1. 定时器计数器
那么我们的定时器怎么办呢？最基本的是获取其计数器的当前值：

    >>> tim.counter()
    21504

此计数器将不断变化，并计数。

###14.2. 定时器回调
我们接下来要做的是为定时器注册一个回调函数，以便在触发时执行（有关 回调函数的介绍，请参阅开关教程）：

    >>> tim.callback(lambda t:pyb.LED(1).toggle())

这应该会立即启动红色LED闪烁。它将以5 Hz的频率闪烁（1次闪光需要2次切换，因此以10 Hz的频率切换使其以5 Hz的频率闪烁）。您可以通过重新初始化定时器来更改频率：

    >>> tim.init(freq=20)

您可以通过传递值来禁用回调`None`：

    >>> tim.callback(None)

传递给回调的函数必须使用1个参数，即触发的定时器对象。这允许您从回调函数中控制定时器。

我们可以创建2个定时器并独立运行它们：

    >>> tim4 = pyb.Timer(4, freq=10)
    >>> tim7 = pyb.Timer(7, freq=20)
    >>> tim4.callback(lambda t: pyb.LED(1).toggle())
    >>> tim7.callback(lambda t: pyb.LED(2).toggle())

因为回调是正确的硬件中断，所以我们可以在这些定时器运行时继续将EasyPy用于其他事情。

###14.3. 制作微秒计数器
您可以使用定时器来创建微秒计数器，这在您执行需要精确计时的操作时可能很有用。我们将使用定时器2，因为定时器2有一个32位计数器（定时器5也是如此，但如果你使用定时器5，那么你不能同时使用伺服驱动器）。

我们按如下方式设置定时器2：

    >>> micros = pyb.Timer(2, prescaler=83, period=0x3fffffff)

预分频器设置为83，这使得定时器计数为1 MHz。这是因为以168 MHz运行的CPU时钟除以2，然后除以预分频器+ 1，为定时器2提供168 MHz / 2 /（83 + 1）= 1 MHz的频率。周期设置为a大数字，以便定时器可以计数到大数，然后回绕到零。在这种情况下，它需要大约17分钟才能循环回零。

要使用此定时器，最好先将其重置为0：

    >>> micros.counter(0)

然后执行你的时间：

    >>> start_micros = micros.counter()
    
    ... do some stuff ...
    
    >>> end_micros = micros.counter()

##15. Inline Assembler内联汇编程序
在这里，您将学习如何在EasyPython中编写内联汇编程序。

注意：这是一个高级教程，适用于那些已经了解微控制器和汇编语言的人。

Easyython包含一个内联汇编程序。它允许您将汇编例程编写为Python函数，您可以像普通的Python函数一样调用它们。

###15.1. 返回值
内联汇编程序函数由特殊函数装饰器表示。让我们从最简单的例子开始：

    @easypython.asm_thumb
    def fun():
        movw(r0, 42)

您可以在脚本或REPL中输入。此函数不带参数，返回数字42. `r0`是寄存器，函数返回时该寄存器中的值是返回的值。EasyPython始终将其解释`r0`为整数，并将其转换为调用者的整数对象。

如果你跑步，`print(fun())`你会看到打印42。

###15.2. 访问外围设备
对于更复杂的东西，让我们打开一个LED：

    @easypython.asm_thumb
    def led_on():
        movwt(r0, stm.GPIOA)
        movw(r1, 1 << 13)
        strh(r1, [r0, stm.GPIO_BSRRL])

此代码使用了一些新概念：

 - `stm`是一个模块，它提供了一组常量​​，便于访问EasyPy微控制器的寄存器。尝试运行，然后在REPL。它将为您提供所有可用常量的列表。`import stmhelp(stm)`

 - `stm.GPIOA`是GPIOA外设的内存地址。在EasyPy上，红色LED位于端口A，引脚PA13上。
 
 - `movwt`将32位数字移入寄存器。它是一个便利功能，变成2个拇指指令：`movw`后跟`movt`。它`movt`还将立即值右移16位。
 - `strh`存储一个半字（16位）。上面的指令将低16位r1存储到存储器位置。这具有将端口A上的所有引脚设置为高的效果，其中设置了相应的位。在上面的示例中，第13位设置，因此PA13被拉高。这会打开红色LED。`r0 + stm.GPIO_BSRRLr0r0`
 
###15.3. 接受参数
内联汇编程序函数最多可以接受4个参数。如果它们时，它们必须被命名为`r0`，`r1`，`r2`和`r3`反映寄存器和调用约定。

这是一个添加其参数的函数：

    @easypython.asm_thumb
    def asm_add(r0, r1):
        add(r0, r0, r1)

这执行计算。由于结果被放入，这就是返回的内容。试试，它应该返回3。`r0 = r0 + r1r0asm_add(1, 2)`

###15.4. 循环
我们可以`label(my_label)`使用`b(my_label)`，或使用条件分支来分配卷标和分支 `bgt(my_label)`。

以下示例闪烁绿色LED。它闪现了r0几次。

    @easypython.asm_thumb
    def flash_led(r0):
        # get the GPIOA address in r1			; 在R1得到GPIOA地址
        movwt(r1, stm.GPIOA)
    
        # get the bit mask for PA14 (the pin LED #2 is on)	得到PA14位码（脚LED＃2接通）
        movw(r2, 1 << 14)
    
        b(loop_entry)
    
        label(loop1)
    
        # turn LED on
        strh(r2, [r1, stm.GPIO_BSRRL])
    
        # delay for a bit
        movwt(r4, 5599900)
        label(delay_on)
        sub(r4, r4, 1)
        cmp(r4, 0)
        bgt(delay_on)
    
        # turn LED off
        strh(r2, [r1, stm.GPIO_BSRRH])
    
        # delay for a bit
        movwt(r4, 5599900)
        label(delay_off)
        sub(r4, r4, 1)
        cmp(r4, 0)
        bgt(delay_off)
    
        # loop r0 times
        sub(r0, r0, 1)
        label(loop_entry)
        cmp(r0, 0)
        bgt(loop1)

###15.5. 进一步阅读
有关内联汇编程序支持的指令的详细信息，请参阅参考文档。

##16.电源控制
`pyb.wfi()`用于在等待中断等事件时降低功耗。您将在以下情况下使用它：

    while True:
        do_some_processing()
        pyb.wfi()

控制频率使用`pyb.freq()`：

    pyb.freq(30000000) # set CPU frequency to 30MHz	;设置CPU频率为30MHz

##17. 串口
###17.1. 串口基本概念
####17.1.1. 串口原理
串口通信的英文缩写是UART(Universal Asynchronous Receiver Transmitter) 全称是通用异步收发器。 听起来很高深的概念，其实就如下图，两个设备，一根线串起来，发送方在线的一头将数据转换为二进制序列，用高低电平按照顺序依次发送01信号，接收方在线的另一头读取这根信号线上的高低电平信号，对应转化为二进制的01序列。 异步收发指的就是全双工传输，即发送数据的同时也能够接收数据，两者同步进行，就如同我们的电话一样，我们说话的同时也可以听到对方的声音。

每当我们想要在PC和MCU之间或两个MCU之间进行通信时，最简单的方法就是使用UART。在两个UART之间传输数据只需要两根线。数据从发送UART的Tx引脚流向接收UART的Rx引脚。
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps27.jpg)

串口通信原理示意
####17.1.2. 波特率
波特率(bandrate)是指，每秒钟我们的串口通信所传输的bit个数，通俗的讲就是在一秒内能够发送多少个1和0的二进制数。比如，波特率是9600，就意味着1S中可以发送9600个0和1组成的二级制序列。

####17.1.3. 发送端 TX 与 接收端 RX
UART通信基本上使用2个引脚进行数据传输。Tx-用于发送数据的发送数据的引脚，Rx-用于获取数据的接收数据的引脚。两个串口进行通信的话， 最少需要三根线相连。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps28.jpg)

RX 代表信息接收端，TX 代表信息发送端

> 注意 
如果是连接些模块，模块并没有自主供电，还须连接VCC！

###17.2. 串口操作
下文通过易控板与blue:bit蓝牙从机模块的串口通信，最终实现掌控板蓝牙的通讯功能。
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps29.jpg) 

blue:bit 蓝牙模块
####17.2.1. 构建UART

    from mpython import *                            # 导入mpython所有对象
    
    uart=UART(1,baudrate=9600,tx=Pin.P15,rx=Pin.P16)  # 构建UART对象，设置波特率为9600，TX、RX 引脚分别为P15、P16

HC06(blue:bit 蓝牙从机模块)默认出厂的波特率为9600。所以我们在此处构建UART时，波特设为9600，后面才能通讯成功。请根据自己需要的连接串口的波特率自行设置。

`UART`(`id`, `baudrate`, `bits`, `parity`, `stop`, `tx`,` rx`, `rts`, `cts`, `timeout`) , `id` 为串口号，可设值为1~2.掌控板支持3组串口。0用于REPL。`baudrate` 参数 为波特率，`tx` 参数为映射发送引脚，`rx` 参数为映射接收引脚。所有引脚均可以作为串口的输入RX，除 `P2`、`P3` 、`P4` 、`P10` 只能作为输入，其余所有的引脚理论上都可以作为输出TX。 一般只需设置上述参数即可，其他参数会保持默认参数。如需了解更多UART的参数，请查阅 [machine.UART](http://baidu.com) 章节。

####17.2.2. 串口发送
你可以使用带蓝牙功能的电脑或手机下载蓝牙调试助手，配对蓝牙模块。这样就可以实现掌控板和电脑、手机的通讯。

蓝牙连接配对成功后，往串口发送字节数据:

    >>> uart.write('hello,world!')

这时，用串口助手看下，是否接受到掌控板发过来的数据。`uart.write(buf)` 函数为向串口写入（发送）字节数据，返回数据的长度。

####17.2.3. 串口读取
易控板接收串口数据，并将数据显示至OLED屏幕上:

    from easypython import *                               # 导入mpython所有对象
    
    uart=UART(1,baudrate=9600,tx=Pin.P15,rx=Pin.P16,timeout=200)    # 实例UART，设置波特率9600，TX、RX映射引脚为P15、P16，超时设为200ms
    
    while True:
        if(uart.any()):                     # 当串口有可读数据时
            data = uart.readline()          # 从串口读取一行数据
            print("received:",data)         # 打印接收到的数据
            oled.DispChar("接收:%s" %data.decode('utf-8'),0,30)     # 将数据显示的OLED上，注意需要将字节码解码为字符串
            oled.show()                     # 生效
            oled.fill(0)                    # 清屏

这时你可以通过串口助手向串口发送数据，当掌控板接收到串口数据后，打印并显示至OLED屏。在while循环中,轮询使用 `uart.any()` 判断串口中是否有可读数据，当有数据时，用 `uart.readline()` 读取一行数据。需要注意的是，串口接收到的是字节类型，如果是传至OLED显示，需要用` decode()` 将字节转为字符串。
除了 `UART.readline()` 读取数据，还可以使用 `UART.read(length)` 从串口读取指定长度的数据。

###17.3. 拓展
学会了如何使用串口后，你就可以实现易控板与其他MCU(Arduino)、电脑/手机、电子模块间的通讯。应用更为广泛，您可发挥你想象，如何用好串口，做出更有趣的东西！

##18. I2C
I²C（Inter-Integrated Circuit）字面上的意思是集成电路之间，它其实是I²C Bus简称。I2C总线类型是由飞利浦半导体公司在八十年代初设计出来的一种简单、双向、二线制、同步串行总线，主要是用来连接整体电路(ICS)

I2C协议是多个设备仅使用两条线（时钟和数据线）相互通信的一种方式。任何设备都可以是控制I2C时钟和数据线以与其他设备通信的主设备。

每个I2C器件都分配有一个唯一的地址，用于在读写操作期间识别它。当设备看到其在I2C总线上发送的地址时，它会响应请求，当它看到不同的地址时，它会忽略它。 使用唯一地址，许多设备可以共享相同的I2C总线而不会产生干扰。
__________
在使用掌控板，您可以使用 I2C类 函数与I2C总线上的设备进行交互。在大多数情况下，您将充当I2C“主设备”，可以与其他I2C设备读写数据。 您还可以充当I2C“从属”或外设，它们分配了一个地址，可以监听和响应来自其他I2C设备的请求。

###18.1. Master
大部分I2C通讯类模块，操作方法类似。mPython掌控板充当I2C主设备，模块作为从机设备，响应主机请求。 以下SHT20模块作为演示说明，如何读取从机设备数据。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps30.jpg) 
blue:bit 温湿度模块(SHT20)

读取SHT20温度函数:

    def sht20_temperature():
        i2c.writeto(0x40,b'\xf3')
        sleep_ms(70)
        t=i2c.readfrom(0x40, 2)
        return -46.86+175.72*(t[0]*256+t[1])/65535

`i2c.writeto(addr, buf)` 为I2C写操作函数，向 I2C设备为 `addr` ，发送 `buf` 缓存字节。掌控板需要向SHT20发送 `0xf3` 字节，告诉它，我需要读取温度数据，延时70毫秒后 再向SHT20读取使用2字节数据。读取操作使用 `i2c.readfrom(addr, nbytes)` ，`nbytes` 为读取字节数。

读取到2字节数据后，还需要根据sht20手册说明，做数据处理转换温度单位，转换公式如下图。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps31.jpg)
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps32.jpg)
*SHT20温度转换公式*

湿度读取的方式也类似，首先发送“0xf5”字节，告诉SHT20我要读取湿度数据，最后按公式转换湿度单位:

    def sht20_humidity():
        i2c.writeto(0x40,b'\xf5')
        sleep_ms(25)
        t=i2c.readfrom(0x40, 2)
        return -6+125*(t[0]*256+t[1])/65535

> 提示 
有关更多的I2C操作方法，请查阅 I2C类 章节。

完整SHT20示例:

    from mpython import *                   # 导入mpython 所有对象
    
    def sht20_temperature():
        """获取SHT20模块的温度值
        返回:温度
        """
        i2c.writeto(0x40,b'\xf3')                       # 向0x40地址即SHT20写字节“0xf3”
        sleep_ms(70)                                    # SHT20测量需要时间，须等待
        t=i2c.readfrom(0x40, 2)                         # 从x40地址即SHT20，读取2字节数据
        return -46.86+175.72*(t[0]*256+t[1])/65535      # 对读取数据进行温度转换处理 T=-46.86+175.72*St/2^16
    
    def sht20_humidity():
        """获取SHT20模块的湿度值
        返回:湿度
        """
        i2c.writeto(0x40,b'\xf5')                       # 向0x40地址即SHT20写字节“0xf5”
        sleep_ms(25)                                    # SHT20测量需要时间，须等待
        t=i2c.readfrom(0x40, 2)                         # 从x40地址即SHT20，读取2字节数据
        return -6+125*(t[0]*256+t[1])/65535             # 对读取数据进行湿度转换处理 RH=-6+125*Srh/2^16
    
    while True:
        temper=sht20_temperature()
        humid=sht20_humidity()
        print("sht20 temperature: %0.1fC sht20 humidity: %0.1f%%" %(temper,humid))
        oled.DispChar("温度:%0.1f度, 湿度:%d%%" %(temper,humid),10,25)
        oled.show()
        sleep(1)
