 
#安装MU编辑器
MU 是一个简单的代码编辑器，可以与Easy Python学习板一起使用。它是用Python编写的，适用于Windows、Mac OS、Linux和Raspberry PI。在Easy Python学习板的内置里已经建置USB CDC串口控制，因此使用者可以从学习板的内置中调用串口的资源输出,即可以得到即时反馈！
MU编辑器有着强大的资源, 如果你没有编程的相关经验, 我们建议你从MU编辑器开始上手, 跟着图文, 就可以简单上手！

### 为Windows或Mac OS X安装MU

要安装用于Windows或Mac OS X的 “MU”，请到网站下载Download MU (https://www.e-py.net/MU) 页面, 并且按照指引说明进行操作。
因为每一个Linux版本都有所不同，因此请特别注意其作指导原则！

 

 1. 安装MU前，请先确认Windows操作系统版本
 (1) 32位操作系统，请下载MU_WIN_32.zip进行安装
 (2) 64位操作系统，请下载MU_WIN_64.zip进行安装

 2. 安装包内容
 | -------- | 32位操作系统    |	64位操作系统 |
| --------    | :-----  |
| ZIP File	| MU_WIN_32.zip	| MU_WIN_64.zip | 
| Python setup	| python-3.7.3.exe	| python-3.7.3-amd64.exe
| CDC driver setup	| cdc_32\dpinst_x86.exe	| cdc_64\dpinst_x64.exe
| MU setup	| mu_32\Mu_1.1.0a1.exe	| mu_64\Mu_1.1.0a1.exe
 
 3. “MU” 的安装将分成三个部份
(1) Python version3 (第三版)
(2) CDC Driver
(3) MU Editor编译程序
 

当你完成以上三步骤，恭喜你！现在你可以准备开始使用指令运行MU编辑器。
另外，你也可以按照（https://www.e-py.net/MU）的python使用说明安装MU.
 
### Python 安装
(1) 32位操作系统 – 请执行MU_WIN_32\ python-3.7.3.exe
(2) 64位操作系统 – 请执行MU_WIN_64\ python-3.7.3-amd64.exe

以下以32位操作系统为例，说明python安装步骤
(1)执行MU_WIN_32\ python-3.7.3.exe
(2)执行后，出现以下画面，请按执行按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8621.png)

(3)点选执行按钮后，出现以下画面，请选取Upgrade Now

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8653.png)

(4)安装中画面如下

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8663.png)

(5)安装完成画面如下

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8674.png)

### CDC driver安装
您需要安装EasyPy驱动程序才能使用串行USB设备。首先根据Windows操作系统的版本来执行安装檔. 然后按照下面安装步骤来操作. 

(1)32位操作系统 – 请执行MU_WIN_32\cdc_32\dpinst_x86.exe
(2)64位操作系统 – 请执行MU_WIN_64\cdc_64\dpinst_x64.exe
**以下以32位操作系统为例，说明CDC driver安装步骤**
(1)执行MU_WIN_32\cdc_32\dpinst_x86.exe，出现以下画面，请按下一步按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8932.png)

(2)安装中画面如下

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8942.png)

(3)安装完成画面如下，请按完成按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8960.png)

### MU安装
(1)32位操作系统 – 请执行MU_WIN_32\mu_32\Mu_1.1.0a1.exe
(2)64位操作系统 – 请执行MU_WIN_64\mu_64\Mu_1.1.0a1.exe
以下以32位操作系统为例，说明MU安装步骤
(1)执行MU_WIN_32\mu_32\ Mu_1.1.0a1.exe，出现以下画面，请按Next按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9132.png)

(2)出现以下画面，请按I Agree按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9153.png)

(3)按照默认Install just for me设定，请按Next按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9190.png)

(4)按照默认路径设定，请按Install按钮

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9213.png)

(5)安装中画面如下

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9223.png)

(6)安装完成画面如下，请按Finish按钮 
 
 ![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9245.png)
 
###使用MU
当你第一次启动MU时，系统会引导你选择“模式”。在未来，你可以随时依照你指定的模式来做选择与设定。现在请你先选择设定为EasPy后在点击右下角的ＯＫ按键。当前模式荧幕画面在窗口右下角的“档位”有图标旁边。如果你看到的模式是显示“microbit”或其他内容，请点击该按钮，然后在出现的对话框中选择“EasyPy”。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9393.png)

MU会自动尝试去检测你的学习板，因此此刻请务必保持Easy Python设备是连接上，并确保它在启动MU之前已经是显示为Easy Python驱动器。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9471.png)

现在万事具备！让我们踏上人工智能的学习之路

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9495.png)


**(1)浏览文件系统**
点击菜单“文件File”，打开EasyPy板上文件系统”From on your device”, 目前为了确保EasyPy板文件系统能被正确打开，这个过程约需要3秒。界面右下是本地文件系统，对应目录在 C:\Users\{user}\mu_code.

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9632.png)

打开本地文件在电脑文件区右键菜单“在编辑区打开”.

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9660.png)

**(2)代码编辑区**

代码提示功能：输入前两个字符，可以自动提示指令内容. 方便来提醒指令.

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9705.png)

**(3)EasyPy文件系统**

界面左下是EasyPy文件系统， EasyPy上有一个小的内部文件系统（驱动器），称为`/flash`存储在微控制器的闪存中。如果将micro SD卡插入插槽，则可以使用`/sd`。当EasyPy启动时，它需要选择要从中启动的文件系统。如果没有SD卡，则使用内部文件系统`/flash`作为启动文件系统，否则使用SD卡`/sd`。如果EasyPy启动时该文件存在，那么将跳过SD卡，并且EasyPy将始终从内部文件系统启动（在这种情况下，SD卡将不会被挂载，但您仍然可以在程序中安装和使用它使用`os.mount`）。

启动文件系统用于两件事：它是从哪个文件系统`boot.py`和`main.py`文件中搜索，并且它是由您的PC通过USB电缆上的文件系统。

文件系统将作为PC上的USB闪存驱动器提供。您可以将文件保存到驱动器，然后编辑`boot.py`和`main.py`。

**(4)向EasyPy写入代码文件**

现在，可以向ePy board写入Python代码文件。
写入方式可以是：
1.通过菜单“New”一个Python文件，把当前编辑区的内容另存新档”Save as”来载入EasPy.

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps10195.png)

2.从电脑文件区拖动文件到EasyPy
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9495.png)

**(5)EasyPy文件区菜单**

**a**.在编辑区打开
把EasyPy上的文件内容读取到编辑区内，与电脑文件不同，来自EasyPy的文件名称，会以中括号标起来。
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps10195.png)

**b**.运行指定代码
选定一个程序通过菜单”Flash”来实时运行。 若运行成功，在易控板上可以看实时效果。
**c**.停止
停止当前正在运行的程序可以按键盘”CTRL+C”来中断程序运行。
**d**.重命名
重命名某个文件。
**e**.删除
删除易控板上某个文件。删除，不可撤销。

**(6)执行EasyPy文件**

a.启动模式
如果你正常上电，或者按下复位按钮，EasyPy将启动进入标准模式：`boot.py`首先执行文件，然后配置USB，然后`main.py`运行。
b.执行REPL
现在让我们尝试直接在EasyPy上运行一些EasyPython代码。REPL代表Read Evaluate Print Loop，是您可以在EasyPy上访问的交互式EasyPython提示的名称。到目前为止，使用REPL是测试代码和运行命令的最简单方法。
打开MU编辑器并找到写有”REPL”的图标, 按下此图标后, 您会看到MU编辑器的下面窗口中出现Easy Python and ePy board的相关版本信息。按Enter键，您将看到一个EasyPython提示符，即`>>>`。到目前为止，使用REPL是测试代码和运行命令的最简单方法。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps10215.png)

c.执行当前EasyPy文件
通过菜单“Flash”可以直接来执行当前编辑区的EasyPy文件来实时运行。 若运行成功，在易控板上可以看实时效果

### LED指示灯

用户可以从LED灯来清楚了解ePy board的运行状态, 方便排除硬件的问题. 其状态有
**a.状态1**: 开机中, 会闪绿灯
**b.状态2**: 开机过程因硬件问题而中断开机 , 将会常亮红灯. 这是出现硬故障。这无法恢复，您需要进行硬重置。
**c.状态3**: 开机过程因Python 脚本或main.py 问题而中断开机, 会闪红灯. 那么可以使用REPL进行调试。
**d.状态4**: 成功开机, 绿灯将常亮
**e.状态5**: 开始作软件更新, 红绿灯将交互闪
**f. 状态6**: 完成软件更新, 绿灯及红灯会常亮, 用户需要重新上电来启动ePy board. 



###安装USB驱动
以下提供了有关在Windows中使用EasyPy的信息，包括设置串行提示和使用DFU编程下载新固件。预设情况下, Windows 8 和8.1 不允许安装未签名的驱动程序。在安装排行榜驱动程序之前, 必须以特殊模式启动 Windows。可从多个网站获得说明: 

[HTTP://revryl.com/2013/08/06/install-unsigned-drivers/](HTTP://revryl.com/2013/08/06/install-unsigned-drivers/)

[HTTP://www.nextofwindows.com/how-to-install-an-un-signed-3rd-party-driver-in-windows-8/1](HTTP://www.nextofwindows.com/how-to-install-an-un-signed-3rd-party-driver-in-windows-8/1)

1.MSC。大容量存储类。pyboard 上的闪存显示为可移动磁盘磁盘驱动器, 其方式与 USB 拇指磁盘驱动器相同。无需安装驱动程序。插入 pyboard, 打开 Windows 资源管理器并找到磁盘驱动器。记下磁盘驱动器号。它应该显示以下文件 
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps8.jpg) 

2.CDC. 通信设备类.
> * 你可以看到一个信息弹出, 指出未成功安装驱动程序
> * 打开”控制台”。在ePy板上右键单击, 然后选择”更新驱动程序软件

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps9.jpg) 

> * 选择”浏览计算机上的驱动程序软件, 然后选择上面找到的磁盘驱动器。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps10.jpg) 

> * Windows 将搜索 ePy board 内存磁盘驱动器, 并查找并安装 pybcdc. inf。pybcdc. inf 没有签名 (未经微软验证, Windows 将显示警告)。Pybcdc 不包含任何驱动程序, 它只是将 ePy board 连结到现有的 Windows 驱动程序, 因此忽略此警告是安全的。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps11.jpg) 

> * 一旦驱动程序安装, 请注意 COM 埠号

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps12.jpg) 

> * 你也可以从控制台中找到埠号

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps13.jpg) 

3.HID. 人机接口设备。此模式允许 ePy board 仿真为鼠标或键盘。无需安装驱动程序。默认情况下不启用 HID 模式, 但可以通过编辑boot. py
4.DFU, 设备固件升级。这使得 ePy board 内存磁盘驱动器可以重新程序设计与新版本的Micro Python。

###浏览文件系统
点击菜单“文件”，打开EasyPy板上文件系统，目前为了确保EasyPy板文件系统能被正确打开，这个过程约需要3秒。
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps14.jpg) 


###代码编辑区
代码提示功能：输入前两个字符，可以自动提示内容

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps15.jpg) 

打开本地文件，在电脑文件区右键菜单“在编辑区打开”

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps16.jpg)

从Windows资源管理器拖动任意文件到编辑区

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps17.jpg) 

###EasyPy文件系统
界面左下是EasyPy文件系统，初次使用EasyPy，文件列表可能是空白的。 界面右下是本地文件系统，对应目录在 C:\Users\{用户名}\mu_code

###写入基础库
易控板文件区菜单自带基础库easypy.py，初次使用需要先把基础库写入易控板。 如图，在易控板文件区任意地方，鼠标右键点击“写入基础库(easypy.py)”
![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps18.jpg)

> * 注解  
写入基础库的目的是：以后在程序中可以使用 from easypy import * 的语句

###向EasyPy写入代码文件
现在，可以向EasyPy写入代码文件。
写入方式可以是：
1.通过菜单“刷入”，把当前编辑区的内容刷入EasyPy

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps19.jpg) 

2.从电脑文件区拖动文件到EasyPy

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps20.jpg) 

###EasyPy文件区菜单
在编辑区打开
把EasyPy上的文件内容读取到编辑区内，与电脑文件不同，来自EasyPy的文件名称，会以中括号标起来。

![](https://raw.githubusercontent.com/Honor-D/EasyPython/master/img/wps21.jpg) 

运行指定代码

选定一个程序来实时运行。 若运行成功，在易控板上可以看实时效果。

停止

停止当前正在运行的程序（但无法停止main.py）。因为程序已经实现了连续运行不同代码，此功能现在较少用到。

设为默认运行

把某个代码设定为易控板默认运行程序，在通电或者重启后立即运行。

> * 注意
部分不能实时运行的代码，有可能设置为默认程序后可以运行。

重命名

重命名某个文件。

删除

删除易控板上某个文件。删除，不可撤销。

###本地文件系统和SD卡
EasyPy上有一个小的内部文件系统（驱动器），称为`/flash`存储在微控制器的闪存中。如果将micro SD卡插入插槽，则可以使用  `/sd` 。

当EasyPy启动时，它需要选择要从中启动的文件系统。如果没有SD卡，则使用内部文件系统`/flash`作为启动文件系统，否则使用SD卡`/sd`。引导后，当前目录设置为上面的目录之一。

如果需要，您可以通过创建一个名为的空文件来阻止使用SD卡`/flash/SKIPSD`。如果EasyPy启动时该文件存在，那么将跳过SD卡，并且EasyPy将始终从内部文件系统启动（在这种情况下，SD卡将不会被挂载，但您仍然可以在程序中安装和使用它使用`os.mount`）。

（请注意，在旧版本的电路板上，`/flash`调用`0:/`并`/sd` 调用`1:/`）。
启动文件系统用于两件事：它是从哪个文件系统`boot.py`和`main.py`文件中搜索，并且它是由您的PC通过USB电缆上的文件系统。

文件系统将作为PC上的USB闪存驱动器提供。您可以将文件保存到驱动器，然后编辑`boot.py`和`main.py`。
在重置EasyPy之前，请记住弹出（在Linux上，卸除）USB驱动器。

启动模式

如果你正常上电，或者按下复位按钮，EasyPy将启动进入标准模式：`boot.py`首先执行文件，然后配置USB，然后`main.py`运行。
您可以在电路板启动时按住用户开关来覆盖此启动顺序。按住用户开关并按下复位，然后当您继续按住用户开关时，LED将以二进制形式计数。当LED达到您想要的模式时，松开用户开关，所选模式的LED将快速闪烁，电路板将启动。

模式是：
1.仅绿色LED，标准启动：运行`boot.py`然后`main.py`。
2.仅限橙色LED，安全启动：启动时不运行任何脚本。
3.绿色和橙色LED一起，文件系统重置：将闪存文件系统重置为出厂状态，然后以安全模式启动。
如果您的文件系统损坏，请启动进入模式3以修复它。如果在插入计算器时重置文件系统不起作用，则可以在将电路板插入USB充电器或其他没有数据连接的USB电源时尝试执行相同的步骤。
错误：LED闪烁
您可能会看到以下两种错误：
1.如果红色和绿色LED交替闪烁，那么就是Python脚本
（例如`main.py`）有错误。使用REPL进行调试。
2.如果所有4个LED缓慢地开启和关闭，那么就会出现硬故障。这无法恢复，您需要进行硬重置
