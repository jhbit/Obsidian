





## ***2 BLE的协议体系结构***
BLE广播事件：[03:37](https://www.bilibili.com/video/BV1oz42197bm/?t=217.666215#t=03:37.67) 

## ***3 BLE [Controller]([【BLE系列课】6.2.3 低功耗蓝牙(BLE)的控制器 1_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1wZ42117uW?vd_source=bca40517a4e6c2b830f187ab070fb9a1&spm_id_from=333.788.videopod.sections))***
频段：2.4GHz ISM频段 2400——2483.5MHz
40个信道，每个信道2MHz
广播信道 37 38 39
次要信道/数据信道 0 ~ 36

### 蓝牙的调制解调方式：GFSK
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710110007035.png)

物理层主要解决0和1收发的问题。中心频点+185kHz是1，-185kHz是0。

### PHY
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710110246074.png)

==什么决定了蓝牙的通信范围==
PHY决定了蓝牙的清晰度和语速，通信频谱范围：30K——300GHz
2.4GHz的数据传输范围广，但是速率较低。

范围由接收的灵敏度和发射的功率决定。

**dB**：dB是对数单位，多用于两个功率/幅度的比值。
dB可以表示功率的增益/衰减、路径损耗、信噪比等。

室内，使用1M PHY，几十米通信距离。室外，能达到100——200米。

==蓝牙地址==
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710111803261.png)
Public需要购买。Random分为Static和Private，静态上电自动随机生成，也可以自行设置。private针对保护蓝牙隐私，多用于手机。会定时更新。

### 链路层
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710112113467.png)
Uncoded PHY指的是1M PHY和2M PHY

链路层状态 ==最核心的部分，理解BLE Controller，就可以理解核心规范以及协议栈==
链路层的主要功能是去控制Radio的使用。

Standby：不收发任何的报文，可以切换到除连接态connection以外的任何状态。一般用来进行参数设置。
Advertising：将数据包在广播物理信道上传输，并监听响应。处于广播态的设备叫广播者。
Scanning：监听链路层广播的信号。处于扫描状态的设备叫扫描者。
Initiating：将正在广播的设备发起连接，处于Initiating状态的叫做发起者。发起者把广播者和发起者的状态都切换到连接态。
Connection：
Synchronization：处于同步状态且接收同步数据包的设备叫做同步接收机。

Radio在发射/接收的时候电流是mA级别，休眠状态电流是uA级别的。功耗主要来自发送/接收。

#### ==**Advertising**==














