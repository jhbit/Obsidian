> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [wlink.blog.csdn.net](https://wlink.blog.csdn.net/article/details/107466841)

> CSDN Wireless-link

本文主要介绍蓝牙 5.2 协议栈，Bluetooth stack, 蓝牙 5.2 的架构，包含传统蓝牙 / 低功耗蓝牙的协议概述以及作用

一. 声明
-----

本专栏文章我们会以连载的方式持续更新，本专栏计划更新内容如下：

![](https://i-blog.csdnimg.cn/blog_migrate/6c1caa55979fc879969decad820c5e23.png)

第一篇: 蓝牙综合介绍 ，主要介绍蓝牙的一些概念，产生背景，发展轨迹，市面蓝牙介绍，以及蓝牙开发板介绍。

第二篇: Transport 层介绍, 主要介绍蓝牙协议栈跟蓝牙芯片之前的硬件传输协议, 比如基于 UART 的 H4,H5,BCSP，基于 USB 的 H2 等

第三篇: 传统蓝牙 controller 介绍，主要介绍传统蓝牙芯片的介绍，包括射频层（RF），基带层（baseband），链路管理层（LMP）等

第四篇: 传统蓝牙 host 介绍，主要介绍传统蓝牙的协议栈，比如 HCI,L2CAP,SDP,RFCOMM,HFP,SPP,HID,AVDTP,AVCTP,A2DP,AVRCP,OBEX,PBAP,MAP 等等一系列的协议吧。

第五篇：低功耗蓝牙 controller 介绍，主要介绍低功耗蓝牙芯片，包括物理层（PHY），链路层（LL）

第六篇：低功耗蓝牙 host 介绍，低功耗蓝牙协议栈的介绍，包括 HCI,L2CAP,ATT,GATT,SM 等

第七篇：蓝牙芯片介绍，主要介绍一些蓝牙芯片的初始化流程，基于 HCI vendor command 的扩展

第八篇：附录，主要介绍以上常用名词的介绍以及一些特殊流程的介绍等。

另外，开发板如下所示，对于想学习蓝牙协议栈的最好人手一套。以便更好的学习蓝牙协议栈，相信我，学完这一套视频你将拥有修改任何协议栈的能力（比如 Linux 下的 bluez，Android 下的 bluedroid）。

------------------------------------------------------------------------------------------------------------------------------------------

蓝牙交流扣扣群：970324688

Github 代码：[https://github.com/sj15712795029/bluetooth_stack](https://github.com/sj15712795029/bluetooth_stack)

**入手开发板：**[https://item.taobao.com/item.htm?spm=a1z10.1-c-s.w4004-22329603896.18.5aeb41f973iStr&id=622836061708](https://item.taobao.com/item.htm?spm=a1z10.1-c-s.w4004-22329603896.18.5aeb41f973iStr&id=622836061708)

------------------------------------------------------------------------------------------------------------------------------------------

二. 前言
-----

三. HCI 蓝牙架构
-----------

在介绍架构之前我们先介绍下两个名词:

**1）BT Controller：此部分指的是蓝牙芯片，包括 BR/EDR 芯片（蓝牙 2.1 芯片），AMP 芯片（蓝牙 3.0 芯片），LE 芯片（蓝牙 4.0 芯片），后续我们把 4.0 以下统称为传统蓝牙，4.0 以上称为低功耗蓝牙，芯片层面会有 2 种模式，包括**

单模蓝牙芯片：单一传统蓝牙芯片，单一低功耗蓝牙芯片

双模蓝牙芯片：同时支持传统蓝牙跟低功耗蓝牙的芯片

**2）BT Host：**蓝牙协议栈

所以 HCI 架构的蓝牙会有以下几种架构

 ![](https://i-blog.csdnimg.cn/blog_migrate/e0f2e3413d6e60e24f28bc2b63101bc4.png)  

四. HCI 架构的蓝牙协议简要介绍
------------------

细展开以上的架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/cd794d5675bc8c10ae9b85c2b4658fcb.png)

以上架构图从最底下开始大概说明，在后续章节也会逐一展开

***HW 层：****这里就是蓝牙芯片层，包含以下几个部分

1）RF（RADIO）：射频层，本地蓝牙数据通过射频发送给远端设备，并且通过射频接收来自远端蓝牙设备的数据

2）BB（BASEBAND）：基带层，进行射频信号与数字或语音信号的相互转化，实现基带协议和其它的底层连接规程。

3）LMP（LINK MANAGER PROTOCOL）：链路管理层，负责管理蓝牙设备之间的通信，实现链路的建立、验证、链路配置等操作

4）HCI（HOST CONTROLLER INTERFACE）：主机控制器接口层，HCI 层在芯片以及协议栈都有，芯片层面的 HCI 负责把协议栈的数据做处理，转换为芯片内部动作，并且接收到远端的数据，通过 HCI 上报给协议栈。

5）BLE PHY：BLE 的物理层

6）BLE LL：BLE 的链路层

***TRANSPORT 层：****此部分在硬件接口（UART/USB/SDIO）实现 HOST 跟 CONTROLLER 的交互，此部分会分为以下几个协议，在后续章节会对 transport 协议做详细的说明

1）H2：USB 的 transport

2）H4:  UART 的 transport

H4 是 UART 传输种最简的一个 Transport，只是在 HCI raw data 的前面加一个 type 就行，如下 HCI 一共有五种 HCI data:

* HCI COMMAND: 由蓝牙协议栈发送给芯片的命令

* HCI EVENT: 由蓝牙芯片上报给蓝牙协议栈的事件

* HCI ACL: 蓝牙协议栈跟蓝牙芯片双向交互的普通数据

* HCI SCO: 蓝牙芯片跟蓝牙协议栈双向交互的通话 / 语音识别等音频数据

* HCI ISO（这部分是在 core5.2 才添加）:LE audio 用的数据包格式

交互数据格式为：

![](https://i-blog.csdnimg.cn/blog_migrate/045de94c70f7466df1547fe3403a0041.png)

其中 H4 type 定义如下：

![](https://i-blog.csdnimg.cn/blog_migrate/044bd171b749fa57834635ba79221e30.png)

3）H5:  UART 的 transport

4）BCSP: UART 的 transport

5）SDIO Transport, 我不知道叫什么 transport, 但是有走 SDIO 的蓝牙芯片，比如 Marvell8887，可以选择走 SDIO 或者 UART

其中 2,3,4 的主要差别在于 H4 需要 BT CHIP UART_TX/UART_RX/UART_CTS/UART_RTS/VCC/GND 接到 MCU，而 H5,BCSP 只需要 BT CHIP 的 UART_TX/UART_RX/VCC/GND 接到 MCU 就可以通信。

***HOST 层：****此部分就是蓝牙协议栈，是我们本书的重点

1）HCI（HOST CONTROLLER INTERFACE）：主机控制层接口，主要负责透过 transport 把协议栈的数据发送给蓝牙芯片，并且接受来自蓝牙芯片的数据，数据主要分为 **HCI COMMAND**(HOST->CONTROLLER),**HCI EVENT**(HOST<-CONTROLLER),**HCI ACL**(HOST<->CONTROLLER),**HCI SCO**(这个有点些微差异，因为部分芯片的 SCO 数据不是透过 TRANSPORT 直接跟 HOST 沟通，而是通过特殊的引脚，PCM IN/OUT/SYNC/CLK 脚来传输数据)，core 文档 HCI 的架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/59f689fe25eddb720fdb56fbf1caedd1.png)

![](https://i-blog.csdnimg.cn/blog_migrate/ab183232a2dbf188d32d4809f0507f2e.png)

2）L2CAP（Logical Link Control and Adaptation Protocol）：逻辑链路控制与适配协议，将 ACL 数据分组交换为便于高层应用的数据分组格式，并提供协议复用和服务质量交换等功能。

通过协议多路复用、分段重组操作和组概念, 向高层提供面向连接的和无连接的数据服务, L2CAP 还屏蔽了低层传输协议中的很多特性，使得高层协议应用开发人员可以不必了解基层协议而进行开发。架构如下:

![](https://i-blog.csdnimg.cn/blog_migrate/d0d2d4b956e0ab99f1b8c29bfa19a354.png)

3）SDP（SERVICE DISCOVERY PROTOCOL）：服务发现协议，服务发现协议 (SDP) 为应用程序提供了一种方法来发现哪些服务可用，并确定这些可用服务的特征

![](https://i-blog.csdnimg.cn/blog_migrate/5a726f92b06b18828fc7f88ca2ed0c6d.png)

4）RFCOMM（Serial Port Emulation）：串口仿真协议，上层协议蓝牙电话，蓝牙透传 SPP 等协议都是直接走的 RFCOMM

![](https://i-blog.csdnimg.cn/blog_migrate/68433a9517de459589108d76ae5f2b90.png)

5）OBEX：对象交换协议，蓝牙电话本，蓝牙短信，文件传输等协议都是走的 OBEX

![](https://i-blog.csdnimg.cn/blog_migrate/80b391345627dc00eb51162e5d3eb82a.png)

6）HFP（Hands-Free）：蓝牙免提协议

![](https://i-blog.csdnimg.cn/blog_migrate/c3b3cf5f13aa57f33e897601787b119e.png)

一共分为两个角色：AG 跟 HF，举一个例子你一下就会懂，蓝牙耳机跟手机连接，那么手机的角色就是 AG，蓝牙耳机的角色是 HF

![](https://i-blog.csdnimg.cn/blog_migrate/3620cf0e4b2da625987095d83e76fadb.png)

7）HSP：蓝牙耳机协议，最开始的蓝牙耳机协议，目前已经没有产品在用这个了吧，至少我没有看到了。算是一个简化版的 HFP。

8）SPP（SERIAL PORT PROFILE）：蓝牙串口协议，架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/896bd756fded23782b2f2cd1ec482cb1.png)

角色没有啥新奇古怪的，就是 Device A/Device B

![](https://i-blog.csdnimg.cn/blog_migrate/15ddcda5a323af726dc6002d214ea745.png)

9）IAP：苹果的特有协议，分为 IAP1/IAP2，一般做 Carplay 或者 iPod 功能的人肯定接触过这块，有需要这块的私下联系我

10）PBAP（Phone Book Access）：蓝牙电话本访问协议, 架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/f7bc775902900d0483637f6c2e549b9f.png)

此部分尤其注意，PBAP 在 V1.2 跟 V1.1 架构变化很大，V1.1 PBAP 直接走的 RFCOMM，在 V1.2 的时候如果 GOEP 是 V2.0 版本，那么 PBAP 是直接走的 L2CAP，并且是 L2CAP ERTM mode，不是 basic mode.

角色如下：同样举例说明，我们车载蓝牙跟手机连接，车载蓝牙下载手机的电话本，那么手机的角色就是 PSE，车载蓝牙就是 PCE，多嘴提一句，我刚进公司的时候第一个协议是 PBAP，所以对 PBAP 有额外的亲切感。

![](https://i-blog.csdnimg.cn/blog_migrate/cddf4ddd4c298ebf1ee60534248d4b3c.png)

11）MAP（MESSAGE ACCESS PROFILE）：蓝牙短信访问协议，架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/5ed6c6beb93353e2523baa3ff2808bda.png)MAP 跟 PBAP 很像，都是在 V1.2 的时候架构有变化，V1.1 MAP 直接走的 RFCOMM，在 V1.2 的时候如果 GOEP 是 V2.0 版本，那么 MAP 是直接走的 L2CAP，并且是 L2CAP ERTM mode，不是 basic mode.

角色如下：

![](https://i-blog.csdnimg.cn/blog_migrate/479aa899d0ee1b97c42ed508a3b1b690.png)

![](https://i-blog.csdnimg.cn/blog_migrate/3ed7c5c0bca98bdc9c24b54257869147.png)

12）OPP（OBJECT PUSH PROFILE）：对象推送协议，架构如下

![](https://i-blog.csdnimg.cn/blog_migrate/b7bfe767435d0332b0affd6d78ec30bd.png)

角色如下：

![](https://i-blog.csdnimg.cn/blog_migrate/919feda78babf6a0cec359c5a109d777.png)

![](https://i-blog.csdnimg.cn/blog_migrate/fe4181f740aaf447fde779e26ec66601.png)

13）AVCTP（AUDIO/VIDEO CONTROL TRANSPORT PROTOCOL）：音视频控制传输协议，是 AVRCP 的地方，架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/35ba699b0740fc96b7edd7b6c3d82439.png)

14）AVDTP（AUDIO/VIDEO DISTRIBUTION TRANSPORT PROTOCOL）：音视频分布传输协议，是 A2DP 的底层，架构如下

![](https://i-blog.csdnimg.cn/blog_migrate/3bc6ec5e35c43fe8ba64de12b883ae1c.png)

15）HID（HUMAN INTERFACE DEVICE）：人机接口协议，架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/5251f0496589a8018a0435929c0e1056.png)

HID 还是有很多广泛的用途的，比如蓝牙鼠标，蓝牙键盘，蓝牙自拍杆，蓝牙手柄等，学好 HID 还是能做很多产品的

16）A2DP（Advanced Audio Distribution）: 蓝牙音乐协议，架构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/3a6bea9409a3c400fc89a136a96e9bf6.png)

角色如下：举一个例子说明，还是拿蓝牙耳机跟手机连接，手机传输音乐给蓝牙耳机，那么手机就是 A2DP source 端，蓝牙耳机是 A2DP sink 端

![](https://i-blog.csdnimg.cn/blog_migrate/a6a6dfc2b271c3c3b12f2d9cd8140445.png)

![](https://i-blog.csdnimg.cn/blog_migrate/9e5c3798854ff985b97c4d4a65a45cdf.png)

17）AVRCP（AUDIO/VIDEO REMOTE CONTROL PROFILE）：蓝牙音乐控制协议

![](https://i-blog.csdnimg.cn/blog_migrate/ae3af505ac0dceea33cd8bb35c466876.png)

角色如下: 举例说明，哈哈，继续拿手机跟蓝牙耳机举例（前提是蓝牙耳机有上一首下一首的功能），那么蓝牙耳机就是 controller(CT), 手机就是 target(TG)

![](https://i-blog.csdnimg.cn/blog_migrate/338595650bac43c941196055c8d24db3.png)

![](https://i-blog.csdnimg.cn/blog_migrate/1acd113bb432b364f9b06fb2bdcbc246.png)

![](https://i-blog.csdnimg.cn/blog_migrate/052bae7c09de07de92fec59f5752dc7d.png)

18）ATT：蓝牙属性协议

ATT，Attribute Protocol，用于发现、读、写对端设备的协议 (针对 BLE 设备),ATT 允许设备作为服务端提供拥有关联值的属性集 ，让作为客户端的设备来发现、读、写这些属性；同时服务端能主动通知客户端。

说到属性协议，我们就不得不提属性是什么，在 ATT 中属性分为 3 个内容：

*   属性类型 (attribute type)，用 UUID 的形式来表现
*   属性句柄 (attribute handle)，用于标识一个属性
*   属性权限 (permissions), 控制是否该 Attribute 可读、可写、属性值是否通过加密链路发送！

ATT 分为两个角色：Server/Client

19）GATT：蓝牙通用属性协议

GATT(Generic Attribute Profile)，描述了一种使用 ATT 的服务框架 ，该框架定义了服务 (Server) 和服务属性 (characteristic) 的过程 (Procedure) 及格式 。  
Procedure 定义了 characteristic 的发现、读、写、通知 (Notifing)、指示(Indicating) 及配置 characteristic 的广播。

GATT 可以被 Application 或其他 Profile 使用，其协议栈如下图

![](https://i-blog.csdnimg.cn/blog_migrate/f24ab97855279f913cca490903befe14.png)

GATT 可以配置为如下两种角色 (Role)，原文如下：

![](https://i-blog.csdnimg.cn/blog_migrate/ac7af4f0ec1478fedb1c991a03869bec.png)

其中 PC 就是做 GATT client, 温度计 Sensor 做 GATT server

20）SM: 蓝牙 BLE 安全管理协议

***APP 层：****蓝牙应用层，比如要做耳机，做蓝牙 HID 设备，做车载，做蓝牙防丢器，做蓝牙穿戴设备等等
