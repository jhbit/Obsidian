[伦茨科技](https://www.yuque.com/lenzetech)





## ***2 BLE的协议体系结构***
BLE广播事件：[03:37](https://www.bilibili.com/video/BV1oz42197bm/?t=217.666215#t=03:37.67) 

## ***3 BLE [Controller](https://www.bilibili.com/video/BV1wZ42117uW?vd_source=bca40517a4e6c2b830f187ab070fb9a1&spm_id_from=333.788.videopod.sections)***
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

**dB**：
**dB是对数单位，可以表示功率的增益/衰减、路径损耗、信噪比等**  
用来表示功率(电功率，声功率)的比值，使用的是10log，P1为待测功率，P0为参考功率。
$$10log_{10}(\frac {P_1} {P_0})$$

用来表示幅度（电压，声压）的比值，使用的是20log，V1为待测功率，V0为参考功率。
$$20log_{10}(\frac {V_1} {V_0})$$

| dB的值  | 功率   | 幅度                 |
| ----- | ---- | ------------------ |
| -3dB  | ÷ 2  | $\frac 1 {\sqrt2}$ |
| +10dB | x 10 |                    |
| -20dB | ÷100 | $\frac 1 {10}$     |


室内，使用1M PHY，几十米通信距离。室外，能达到100——200米。

==蓝牙地址==
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710111803261.png)
Public需要购买。Random分为Static和Private，静态上电自动随机生成，也可以自行设置。private针对保护蓝牙隐私，多用于手机。会定时更新。

### 链路层
![image.png](https://raw.githubusercontent.com/jhbit/image-bed/main/Obsidian_image/20250710112113467.png)
Uncoded PHY指的是1M PHY和2M PHY

链路层状态 **==最核心的部分，理解BLE Controller，就可以理解核心规范以及协议栈==**  
链路层的主要功能是去控制Radio的使用。

状态机：  

| 状态       | 英文名称                             | 作用                                                                                                                                                                               | 典型行为与转换要点                                                              |
| -------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 就绪态      | Standby                          | 上电默认状态，既不发射也不接收任何射频包。可以切换到==除连接态connection==以外的任何状态。一般用来进行参数设置。                                                                                                                  | 所有状态最终都可回到 Standby；系统空闲时保持低功耗                                          |
| 广播态      | Advertising                      | 周期性地在 37/38/39 信道发送 **Advertising PDU**<br>可被 Scanner 发现或连接                                                                                                                      | • 广播完毕 → 回到 Standby<br>• 收到 **CONNECT\_REQ** → 进入 Connection（作为 Slave） |
| 扫描态      | Scanning                         | 被动监听广播信道，接收 **Advertising PDU**                                                                                                                                                  | • 仅用于“发现”周边设备<br>• 不会主动建立连接，可随时回到 Standby                              |
| 发起态      | Initiating                       | 与 Scanning 类似，但监听目的明确：收到目标设备的广播后立即发出 **CONNECT\_REQ**                                                                                                                            | • 发出连接请求 → 进入 Connection（作为 Master）                                    |
| 连接态      | Connection                       | 已建立数据链路，双方跳转到 0-36 数据信道，周期交换数据包                                                                                                                                                  | • 连接断开 → 回到 Standby<br>• 支持 Master 或 Slave 角色，角色在连接建立时确定               |
| 等时广播态    | Isochronous Broadcaster          | 在 **广播信道** 上以 **固定间隔** 发送 **BIS（Broadcast Isochronous Stream）**；<br>多个 BIS 组成一个 **BIG（Broadcast Isochronous Group）**，最多 31 个 BIS。<br><br>`AUX_SYNC_IND`、`AUX_CHAIN_IND` 等周期性广播包。 | 主机命令停止或 BIG 结束 → 回到 **Standby**。                                       |
| 同步接收状态   | Synchronized Receiver            | 监听并 **锁定** 指定 BIG 的 **BIS 数据流**；<br>只能 **单向接收**，不做任何 ACK/重传。<br><br>两个子状态：<br> -**Synchronizing**：正在捕获 BIG 的同步信息（跳频序列、锚点）。<br>- **Synchronized**：已锁定，可正常接收数据。                    | 失去同步或超时 → 回到 **Standby** 并通知主机。                                        |



 ~~~
BLE的发起态和广播态如何进入连接态？

广播态（Advertiser）→ 收到 CONNECT_REQ  → 进入 连接态（Slave）
发起态（Initiator） → 发出 CONNECT_REQ → 立即进入 连接态（Master）

不需要等待额外的握手

5.0之前，整个连接建立只靠一个单向数据包 CONNECT_REQ（视频里是CONNECT_IND）：
    
    1. Advertiser 一直在 37/38/39 信道广播 ADV_IND/ADV_DIRECT_IND；
        
    2. Initiator 捕获到目标广播包后，立即在同一信道发出 CONNECT_REQ；
        
    3. CONNECT_REQ 里已携带双方后续使用的完整时序参数（访问地址 AA、首个连接事件锚点、跳频增量、连接间隔等）；
        
    4. 双方各自本地解析这些参数，在同一时刻切换到第一条数据信道，开始第一个连接事件——无需再交互确认。

5.0之后，AUX_CONNECT_IND和AUX_CONNECT_RSP需要握手


 ~~~



Radio在发射/接收的时候电流是mA级别，休眠状态电流是uA级别的。功耗主要来自发送/接收。

#### ==**Advertising**==














