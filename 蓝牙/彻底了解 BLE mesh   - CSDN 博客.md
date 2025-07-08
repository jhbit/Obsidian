> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [wlink.blog.csdn.net](https://wlink.blog.csdn.net/article/details/147954790)

> CSDN Wireless-link

一. Mesh 整体介绍
------------

### 1. 概念

BLE Mesh（Bluetooth Low Energy Mesh）是一种基于蓝牙低功耗（BLE）的网络协议，专门设计用于创建大规模的设备网络，支持设备之间的多对多通信。这使其特别适合智能家居、工业自动化、照明控制等场景。以下是对 BLE Mesh 的详细介绍：

#### a. 网络架构

*   **节点（Node）：** 网络中的每个设备被称为节点。每个节点可以发送和接收消息。
*   **元素（Element）：** 一个节点可以包含一个或多个元素，每个元素是可以独立控制的基本功能单位。
*   **模型（Model）：** 定义元素的行为和功能，如开关、调光器等。
*   **消息（Message）：** 节点之间通过消息进行通信，消息可以是命令、状态更新或数据。

#### b. **网络特性**

*   **多对多通信：** BLE Mesh 支持多对多通信，允许节点之间自由发送和接收消息。
*   **转发机制（Relaying）：** 中继节点（Relay Node）可以转发消息，使得消息可以传递到远离源节点的设备。
*   **低功耗（Low Power）：** 支持低功耗节点（Low Power Node），这些节点依赖于朋友节点（Friend Node）来缓存消息，从而减少能耗。

#### c. **网络组成**

*   **Provisioning（配置过程）：** 将新节点加入网络的过程，通常由一个配置器（Provisioner）来管理。
*   **地址分配：** 每个节点在网络中都有一个唯一的地址，支持单播、组播和广播通信。
*   **安全性：** BLE Mesh 使用 AES-CCM 加密来确保消息的安全性，支持消息加密和网络密钥管理。

#### d. **应用场景**

*   **智能照明：** 实现远程和自动控制灯光，包括调光、开关和色彩控制。
*   **楼宇自动化：** 控制暖通空调、门锁、传感器等设备，实现智能楼宇管理。
*   **工业物联网（IIoT）：** 监控和控制工业设备，实现设备间的高效通信。
*   **智能家居：** 家庭中的各种设备，如门锁、温控器、传感器等都可以通过 BLE Mesh 进行互联。

#### e. **优势**

*   **扩展性强：** BLE Mesh 网络可以包含成千上万个节点，适合大规模部署。
*   **可靠性高：** 通过中继机制和组播通信，确保消息能够可靠传输，即使部分节点出现故障。
*   **低功耗：** 特别适合电池供电的设备，通过低功耗特性延长设备的使用寿命。

#### f. **实现与支持**

*   BLE Mesh 是由蓝牙技术联盟（Bluetooth SIG）定义和维护的标准，许多芯片厂商和设备制造商都提供对 BLE Mesh 的支持。
*   设备可以使用手机、平板或专用的配置器来配置和管理 BLE Mesh 网络。

BLE Mesh 是一种强大且灵活的网络协议，能够满足现代物联网设备的通信需求，特别适用于需要大规模部署和高可靠性的场景。

### 2. 发展历程

![](https://i-blog.csdnimg.cn/img_convert/2e7224e5a07baae2823c69d6059bb4d3.png)

BLE Mesh 的发展历程反映了蓝牙技术联盟（Bluetooth SIG）及其成员持续推进和优化低功耗蓝牙技术，以满足物联网（IoT）和智能设备市场的需求。以下是 BLE Mesh 发展的主要阶段和里程碑：

#### a. **蓝牙技术的早期发展**

*   **1998 年：** 蓝牙技术由爱立信公司发起，随后多个公司组成了蓝牙特别兴趣小组（Bluetooth SIG）。
*   **2000 年：** 蓝牙 1.0 标准发布，主要用于短距离设备间的点对点通信。

#### b. **低功耗蓝牙（BLE）的引入**

*   **2010 年：** 蓝牙 4.0 标准发布，引入了低功耗蓝牙（Bluetooth Low Energy，BLE），专注于低功耗、低成本的短距离通信。这为 BLE Mesh 的发展奠定了基础，特别是在电池供电设备中。

#### c. **BLE Mesh 的研发阶段**

*   **2014 年左右：** 随着物联网的兴起，对支持大规模、多对多通信的需求日益增加。蓝牙技术联盟开始关注如何在 BLE 环境中实现网状网络。
*   **多家公司参与：** 一些公司和研究机构开始开发自己的 BLE Mesh 解决方案，但缺乏统一的标准，导致市场上出现多个不兼容的方案。

#### d. **BLE Mesh 标准的制定**

*   **2015 年：** 蓝牙技术联盟正式启动 BLE Mesh 标准化工作，目标是创建一个统一、互操作的网状网络标准。
*   **2017 年 7 月：** BLE Mesh 标准（Bluetooth Mesh Profile 和 Bluetooth Mesh Model）正式发布。该标准定义了基于 BLE 的网状网络的基础架构、通信协议和安全机制。

#### e. **标准发布后的发展**

*   **2018 年起：** BLE Mesh 得到广泛支持，许多芯片厂商和设备制造商开始推出兼容 BLE Mesh 的产品。
*   **生态系统扩展：** 智能照明、工业自动化、智能家居等领域开始大量采用 BLE Mesh，推动了整个生态系统的发展。
*   **软件工具和开发包：** 为开发者提供了许多支持 BLE Mesh 的软件工具和开发套件（SDK），如 Nordic Semiconductor、Silicon Labs 等公司的解决方案。

#### f. **持续优化和扩展**

*   **2019 年及以后：** 蓝牙技术联盟持续改进 BLE Mesh 标准，发布了多次技术更新和新功能扩展，如增强的安全性、改进的配置流程以及更高效的通信机制。
*   **应用场景扩展：** 随着技术的成熟，BLE Mesh 开始应用于更多复杂场景，如智能楼宇、智慧城市、资产追踪等。
*   **2023 年蓝牙**发布了 BLE Mesh 1.1, 由原来的 BLE Mesh profile 更名为 BLE Mesh protocol

#### g. **未来展望**

*   **物联网的深度融合：** BLE Mesh 将继续在物联网领域发挥重要作用，推动设备间更高效、更智能的互联互通。
*   **与其他技术的集成：** 未来可能会与 5G、Wi-Fi 等其他通信技术集成，提供更全面的连接解决方案。

通过这些发展阶段，BLE Mesh 已成为支持物联网设备大规模部署和可靠通信的重要技术，为智能化的未来奠定了坚实的基础。

### 3. 架构

#### a. Mesh 在蓝牙中的架构

整体传统蓝牙跟低功耗蓝牙以及 BLE Mesh 的架构以及依赖关系分别如下，绿色部分为 BLE Mesh 部分

![](https://i-blog.csdnimg.cn/img_convert/a5c0f462ec3e0baa13f39fee05e0c080.png)

![](https://i-blog.csdnimg.cn/img_convert/909c479c7cdffb92f4a5b839306c54ab.png)

#### b. BLE Mesh 自身架构

![](https://i-blog.csdnimg.cn/img_convert/7cf456db0acc945fabb946aeee43ff9e.png)

![](https://i-blog.csdnimg.cn/img_convert/6365ca4020f8232c94961ac106f4d053.png)

如果了解过 BLE Mesh 可以看到 Mesh 1.1 的架构跟 Mesh 1.0 架构稍微有点区别，主要是把 provisioning 抽象出来了。上面主要分为两个部分：Mesh networking stack/Mesh provisioning stack.

*   The mesh networking stack used by mesh nodes to communicate with each other
*   The mesh provisioning stack used to provision devices on the network.

**承载层（Bearer Layer）**

Bearer Layer 定义了 Mesh 节点怎么传递网络消息的。定义了两种 Bearer，广播 advertising bearer 和 GATT bearer 。Advertising Bearer 利用的是 BLE 广播包的 advertising 和 scanning 的功能来传递接收 mesh 的报文。

The GATT Bearer 允许不支持 Advertising Bearer 的设备间接的与 mesh 节点进行通讯。怎么通讯呢？使用前面讲的代理 (Proxy Protocol)。Proxy Protocol 是封装在 GATT 里面，当然会用特别定义的 GATT characteristics。支持 Proxy Feature 的 Proxy Node 也就是代理节点，因为可以同时支持两种 Bearer Layer，所以可以作为 mesh 节点和非 mesh 节点的中间桥梁。

**网络层（Network Layer）**

网络层定义了几件事情， 一个是定义了多种网络地址类型，我之前有说过关于 Mesh 地址的内容。二是定义了网络层的格式，打通传输层（Transport layer）和承载层 (Bearer layer)；三是定义了一些输入输出 Filter，决定哪些消息需要转发，处理还是拒绝。四是定义了网络消息的加密和认证。

**底层传输层（Lower Transport Layer）**

这层做的事情很简单，就是拆拆拼拼。把太长的传输层的包拆成若干个分给网络层，把短的网络层的包再组成一个长的传输层的 PDU(Protocol Data Unit)。

**上层传输层（Upper Transport Layer）**

上层传输层主要是负责加密，解密和应用数据授权。一句话，消息的安全性和机密性就是有这一层负责的。还有就是会定义一些节点间在这一层的一些会话，比如 Friend 功能，心跳包（Heartbeats）。

**访问层（Access Layer）**

访问层主要负责：1. 定义更高层的应用如何跟 upper transport layer 通讯。2. 定义应用数据的格式。3. 定义和控制 upper transport layer 应用数据的加解密。4. 在把应用数据扔到上层之前，会检查校验接收过来的应用数据是否合法。

**基础 Model 层（Foundation Models Layer）**

基础 model 层定义访问层（access layer）的状态，消息，模型配置和 mesh 网络管理。

**Model 层（Model Layer）**

Model 层定义了典型的用户场景标准化操作的相关 models（相关的 models 定义在 Bluetooth Mesh Model specification 文档中）。更高层次模型规范的例子包括照明和传感器的模型。

### 4. 名词概念

![](https://i-blog.csdnimg.cn/img_convert/6be4f7f87fb7e9114b206981076463c4.png)

二. Mesh provisioning stack
--------------------------

我们先来介绍下 Mesh provisioning stack，主要是这个是 Mesh 入网的第一步，也就是红框部分, 注意这部分都是**大端**架构来进行协议通信的！

![](https://i-blog.csdnimg.cn/img_convert/c17d7d2615ec0581ec39a3bf2c330e11.png)

把这块差分开就如下所示：

![](https://i-blog.csdnimg.cn/img_convert/2c248ceccb246d25e34d4e72a710858a.png)

**PB-ADV 承载**：允许通过广播承载（Advertising Bearer）对未配置设备进行配置。  
**PB-GATT 承载**：允许通过 Mesh 配置服务（Mesh Provisioning Service）对未配置设备进行配置。  
**PB-Remote 承载**：允许超出未配置设备直接无线电范围的配置器（Provisioner）通过支持远程配置服务器（Remote Provisioning Server）模型的节点与未配置设备进行通信。这个节点用作转发器，利用 PB-ADV 或 PB-GATT 与未配置设备通信。通过这种方式，配置器可以使用网状网络的节点来配置远程未配置设备。

**PB-Remote 承载架构如图所示：**

![](https://i-blog.csdnimg.cn/img_convert/fe6fe28ead06b0e19e72d4a2b9d19cf4.png)

### 1. Provisioning bear

配置承载层是 BLE Mesh 中负责在配置过程中传输数据的基础层。不同的承载层提供了不同的传输方式，用于将配置数据从配置器（Provisioner）传输到未配置设备 (unprovisioned device)。以下是常见的配置承载层：

**PB-ADV（广告承载）**：

*   *   通过广播（Advertising）方式传输配置数据。
    *   使用 BLE 广播通道，适合近距离设备间的配置。
    *   主要用于无需复杂连接的场景，提供快速、低功耗的设备配置方式。

**PB-GATT（GATT 承载）**：

*   *   基于 GATT（通用属性协议）传输配置数据。
    *   通过 Mesh 配置服务（Mesh Provisioning Service）在 BLE 连接通道上传输。
    *   适用于需要可靠连接的设备，尤其是在智能手机或其他支持 GATT 的设备进行配置时常用。

**PB-Remote（远程承载）**：

*   *   允许配置器通过网状网络的中继节点（Mesh Relay）远程传输配置数据。
    *   配置器可通过支持远程配置服务器模型（Remote Provisioning Server）的节点将数据传递给超出直接无线电范围的未配置设备。
    *   适合大型网状网络，尤其是需要跨越较大距离或存在物理障碍的场景。

一共分为 6 中角色

<table><tbody><tr><td><p><strong>分类</strong></p></td><td><p><strong>角色</strong></p></td><td><p><strong>扮演角色</strong></p></td><td><p><strong>交互数据 layer</strong></p></td></tr><tr><td rowspan="2"><p>PB-ADV</p></td><td><p>PB-ADV Client</p></td><td><p>Provisioner</p></td><td><p>generic provisioning layer</p></td></tr><tr><td><p>PB-ADV Server</p></td><td><p>unprovisioned device</p></td><td><p>generic provisioning layer</p></td></tr><tr><td rowspan="2"><p>PB-Remote</p></td><td><p>PB-Remote Client</p></td><td></td><td></td></tr><tr><td><p>PB-Remote Server</p></td><td></td><td></td></tr><tr><td rowspan="2"><p>PB-GATT</p></td><td><p>PB-GATT Client</p></td><td><p>Provisioner</p></td><td></td></tr><tr><td><p>PB-GATT Server</p></td><td><p>unprovisioned device</p></td><td></td></tr></tbody></table>

#### a. PB-ADV

PB-ADV 是一种配置承载层，用于通过广播信道（advertising channels 37/38/39）使用通用配置 PDU（Generic Provisioning PDUs）来配置未配置设备 (这个我们在后面介绍)。这种配置机制是基于会话的。未配置设备每次只能支持一个会话，而配置器则没有此限制。会话通过链接建立过程来建立。PB-ADV 配置承载层在关闭链接时需要提供关闭原因，并在链接关闭时提供关闭原因。

使用 PB-ADV 时，配置器 (Provisioner) 应扮演 PB-ADV 客户端角色，未配置设备 (unprovisioned device) 应扮演 PB-ADV 服务器角色。PB-ADV 承载层用于传输通用配置 PDU。PB-ADV 承载层的最大传输单元（MTU）大小为 24 个字节。

使用 PB-ADV 时，通用配置 PDU 应通过由 «PB-ADV» 标识的 PB-ADV 广告类型（AD type）发送。支持 PB-ADV 的配置器和未配置设备应尽可能接近 100% 的占空比进行被动扫描，以避免错过任何传入的 PB-ADV PDU。

PB-ADV 广告类型包含一个 PB-ADV PDU 字段。PB-ADV 广告类型的格式定义见表

![](https://i-blog.csdnimg.cn/img_convert/fe02c9cd5cb8e263d7ddc7672f53c0ee.png)

其中 AD Type 为：0x29

![](https://i-blog.csdnimg.cn/img_convert/85a8b87b67c8480f0c81e29a9a6082a8.png)

其中 PB-ADV(0x29) 是未入网之前发送的广播数据包，Mesh Message(0x2A) 是入网之后发送的数据包，Mesh Beacon(0x2B) 可以是入网之前 / 入网之后发送的数据包

![](https://i-blog.csdnimg.cn/img_convert/729b532c1c714b64585fc2cea66cccf6.png)

**需要注意的是：广播类型必须是** **ADV_NONCONN_IND，否则会被对方忽略**

下面我们来分别介绍下这三种类型：PB-ADV/Mesh Message/Mesh Beacon

##### ⅰ. PB-ADV

![](https://i-blog.csdnimg.cn/img_convert/3c393ead672e0b09d599eb4b8701cf32.png)

整个 PB-ADV 是广播数据的 LTV(length-type-valve)，其中 length 就是长度，type 就是我们上面表格中的 0x29, 其中 PB-ADV PDU 格式为：

![](https://i-blog.csdnimg.cn/img_convert/7a2f0ac706b657778233a509be7f6ae3.png)

Link ID 就是为了标识 ID，Transaction Number 就是传输标号，Generic Provision PDU 我们在后面介绍。

我们来看下一个 btsnoop 的巩固下格式：

![](https://i-blog.csdnimg.cn/img_convert/b009f6d3e1d833f0bc08443e7d77cf6d.png)

![](https://i-blog.csdnimg.cn/img_convert/7550c194082f4690a6408dca5eaf612a.png)

其中可以看到 length 是 23，Type 是 PB-ADV，data 就是按照 PB-ADV 格式来的

##### ⅱ. Mesh Beacon

其中 Mesh Beacon 的格式也是广播数据的 LTV(length-type-valve) 模型

![](https://i-blog.csdnimg.cn/img_convert/056253c5a95f2e81f6bb828a71ca862a.png)

![](https://i-blog.csdnimg.cn/img_convert/23afd4b82cb7a3f5b504908f796efcd3.png)

其中 Beacon 有三种类型。如下：

![](https://i-blog.csdnimg.cn/img_convert/d59c8c521e7b442bfba06cb2cd572cad.png)

其中 Beacon Data 对应不同类型的数据格式不同

###### 1. Unprovisioned Device Beacon

**用途**：

*   用于设备未加入 Mesh 网络时的发现和配网（Provisioning）。
*   设备通过此 Beacon 宣告自身可被配网，例如新设备首次上电或重置后。

**数据格式**：

![](https://i-blog.csdnimg.cn/img_convert/fba7716def50ca8cfd59366926702469.png)

###### 2. Secure Network Beacon

**用途**：

*   用于已加入网络的节点周期性广播网络状态，维护网络安全性。
*   分发网络密钥更新、IV Index（初始化向量索引）等安全参数。
*   防止重放攻击（Replay Attack）。

**数据格式**：

![](https://i-blog.csdnimg.cn/img_convert/289e62094c45db73c7848473bf42ecbb.png)

###### 3. Private Beacon

**用途**：

*   用于厂商自定义的私有 Beacon，可携带特定数据（如设备状态、传感器数据等）。
*   需遵循蓝牙 Mesh 规范中的私有 Beacon 格式。

**数据格式**：

![](https://i-blog.csdnimg.cn/img_convert/ae2b396f04d5fdd974369a47da81e5f6.png)

#### b. PB-GATT

PB-GATT 是一种配置承载层，用于通过代理 PDU（Proxy PDUs）封装配置 PDU（Provisioning PDUs），并通过网状网络配置服务（Mesh Provisioning Service）进行设备配置。PB-GATT 是**为了解决配置器因应用接口限制而无法支持 PB-ADV** 的情况而提供的。

使用 PB-GATT 时，配置器 (Provisioner) 应扮演 PB-GATT 客户端角色，未配置设备（Provisioner ）应扮演 PB-GATT 服务器角色。

为了支持 PB-GATT 服务器的超低功耗运行，并允许其在不需要保持空闲链接的情况下计算 Diffie-Hellman 共享密钥，PB-GATT 客户端与 PB-GATT 服务器之间的连接间隔应在 250 到 1,000 毫秒之间。

PB-GATT 服务器应能够在单个写入命令 ATT PDU 中接收一个代理 PDU。PB-GATT 服务器应使用单个句柄值通知（Handle Value Notification）ATT PDU 将配置 PDU 发送给 PB-GATT 客户端。

如果协商的 ATT_MTU 小于所需的代理 PDU 大小，则网状网络配置数据输入和配置数据输出特性在传输时需要进行分片和重组。在处理之前，每个 PDU 都应完全重组。

PB-GATT 服务器应能够在一个或多个 ATT PDU 中接收代理 PDU。根据消息的大小和协商的 ATT_MTU，PB-GATT 服务器应使用一个或多个句柄值通知 ATT PDU 向 PB-GATT 客户端发送代理 PDU。

下图说明了配置协议、PB-GATT 服务器和网状网络配置服务的交互。

![](https://i-blog.csdnimg.cn/img_convert/4dc3d0bd7b5f05c057e85553f1cf4d6f.png)

其中牵扯到的服务有：

![](https://i-blog.csdnimg.cn/img_convert/480388cd26c8c01a2d162f5cbacaa54f.png)

![](https://i-blog.csdnimg.cn/img_convert/0c6c359e3b752d036cff6d0ae8fd3871.png)

![](https://i-blog.csdnimg.cn/img_convert/eb4042f8123415f2c913863f1a148a52.png)

##### ⅰ. 发现服务流程

![](https://i-blog.csdnimg.cn/img_convert/9a45b988c904fdcbea06908b648b7880.png)

**步骤一. Node 节点广播**

我们直接来看下 btsnoop，可以看到 node 广播数据

![](https://i-blog.csdnimg.cn/img_convert/4a9215bbb77cddc799f27e9d95389864.png)

![](https://i-blog.csdnimg.cn/img_convert/2e1290bb58aa673d25e3d7b0b593b95d.png)

**步骤二. provisioner 发起 ble 连线，连接 gatt**

![](https://i-blog.csdnimg.cn/img_convert/c2fc32ca5660a167ec42475f93285cff.png)

**步骤三. provisioner 进行 GATT discovery 流程，查看对方是否支持 Mesh provisioning service**

![](https://i-blog.csdnimg.cn/img_convert/fb45f8973120e0b05423b3af96512518.png)

![](https://i-blog.csdnimg.cn/img_convert/1c34146a07763b19eaff8646091a9454.png)

![](https://i-blog.csdnimg.cn/img_convert/08ce48984a8899f86835e54701050f7f.png)

**步骤四. provisoner 发现 node 的服务特征**

![](https://i-blog.csdnimg.cn/img_convert/16af8020e1165425f0fb8fd499cfc784.png)

![](https://i-blog.csdnimg.cn/img_convert/386bde95cc168b83e895fbe1801ad8f6.png)

可以发现 node 回复有 Mesh provisoning Data In/Out

**步骤五. 服务特定 Descriptor 发现**

![](https://i-blog.csdnimg.cn/img_convert/bfe6adc074ef874518be2f1c792de5e2.png)

![](https://i-blog.csdnimg.cn/img_convert/fe3aabae15460af02396f14e24be3b53.png)

可以发现只有一个 CCC description, 也就是 indication/notification 的 enable/disable

**步骤六. 使能 indication/notification**

![](https://i-blog.csdnimg.cn/img_convert/8f03bedae9b3c837c5f0bb6a0a710526.png)

![](https://i-blog.csdnimg.cn/img_convert/aaae6892ed554d36cc768c6c3c49a6a2.png)

#### c. PB-Remote

### 2. Provisioning transport

![](https://i-blog.csdnimg.cn/img_convert/951cf594cbffabead25a87bebd7bbbbd.png)

我们可以看到 provisioning transport 分为有以上三个。我们来一一介绍。

#### a. Generic provisioning layer

![](https://i-blog.csdnimg.cn/img_convert/d07cd942d0a7409ea130c3bc4c06a62d.png)

在介绍常规的 PB-ADV/PB-GATT/PB-Remote 后，因为部分依赖于 Generic provisioning layer ，所以我们来介绍下 generic provisioning layer ，这个主要用于 advertising bearer 以及 PB-ADV provisioning bearer。

通用供应层负责在不可靠的无连接供应承载器上传输 Generic Provisioning PDU 。就像 PB-ADV 就是传输的这个。我们在前面介绍过了 PB-ADV 的格式，我们在结合 generic provisioning PDU 再来贴下

![](https://i-blog.csdnimg.cn/img_convert/8c43eeb1708c255e22e3be7b50a10312.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Length</p></td><td><p>1</p></td><td><p>表示后面数据的长度</p></td></tr><tr><td><p>AD Type</p></td><td><p>1</p></td><td><p>PB-ADV 类型</p></td></tr><tr><td><p>Link ID</p></td><td><p>4</p></td><td><p>链路的标识符</p></td></tr><tr><td><p>Transaction Number</p></td><td><p>1</p></td><td><p>事务的标识符</p></td></tr><tr><td><p>Generic Provisioning PDU</p></td><td><p>1-24</p></td><td><p>配网 PDU</p></td></tr></tbody></table>

而其中 Generic Provisioning PDU 格式为：包括 Generic Provisioning Control (GPC) 跟 Generic Provisioning Payload

![](https://i-blog.csdnimg.cn/img_convert/879295d37c56c5dba47c4e951009e1c7.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Generic Provisioning Control</p></td><td><p>1-17</p></td><td><p>配网数据控制域</p></td></tr><tr><td><p>Generic Provisioning Payload</p></td><td><p>0-64</p></td><td><p>配网数据载荷</p></td></tr></tbody></table>

在结合下拆分开格式为：

![](https://i-blog.csdnimg.cn/img_convert/2822c82205d699d956d9abd90bd50671.png)

在 Generic Provisioning Control byte 0 的 bit 0/bit 1 叫做 Generic Provisioning Control Format (GPCF) ，分别表示 start/ack/continue/control

![](https://i-blog.csdnimg.cn/img_convert/5cb4cebebbd66a4bfb0161eea2769fca.png)

![](https://i-blog.csdnimg.cn/img_convert/e746c97c344744cf6a3295a0c23d18e0.png)

4 种 Generic Provisioning Control Format 对应的格式不同，我们来一一介绍

##### ⅰ. Transaction Start PDU

表示开始传输分段消息，其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/e6f66e0ed32fee1c65049c2664546cbe.png)

在结合到 PB-ADV 中的格式为：

![](https://i-blog.csdnimg.cn/img_convert/97f919b4b3b88c44edee0cc99fc9734f.png)

![](https://i-blog.csdnimg.cn/img_convert/b1567627e99526ec0360bf180bbf0656.png)

##### ⅱ. Transaction Acknowledgment PDU

用于响应 Provisioning PDU 消息，其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/c08e8454ee84b0b3919f62e5be9f2896.png)

结合到 PB-ADV 中的格式为：

![](https://i-blog.csdnimg.cn/img_convert/34634c266183419f7193f76f15e360e9.png)

Padding=0b000000，GPCF=**0b01**，Data 域为空。

##### ⅲ. **Transaction Continuation**

表示传输分段消息附加段，其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/f7fde8d5ab820cd80775e5c8513ace2d.png)

结合到 PB-ADV 中的格式为：

![](https://i-blog.csdnimg.cn/img_convert/87744f4ceb8814c5d1a53b2588fd27ef.png)

![](https://i-blog.csdnimg.cn/img_convert/b03114fea7e8a78de42b9af17467ec83.png)

##### ⅳ. **Transaction Bearer Control**

用于管理承载层的会话，即建立配网者与未配网设备的通道，其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/056cadf626dc9c5585be5f644a620d1b.png)

结合到 PB-ADV 格式为：

![](https://i-blog.csdnimg.cn/img_convert/b8ca2aca08650cd54301b5cb480c2d25.png)

![](https://i-blog.csdnimg.cn/img_convert/adfef9aa4e71299dfc5822abd61f3c4a.png)

可以看到有三种 Link Open、Link ACK、Link Close，我们来分别介绍下

###### 1. Link Open

配网者发起，要求与未配网设备建立一个链接，设备收到后需要响应一个 Link Ack 消息，一个设备只能同时处理一个 Link（？？），因此在 Link 存在期间，无视 Link Open 消息。其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/363075d5a09d5851829499c74b1a568d.png)

Device UUID 为配网者选择的设备的 UUID，为 16 个 byte

![](https://i-blog.csdnimg.cn/img_convert/99586b4a68b5577ee44b5838db8e6bb7.png)

结合 PB-ADV 跟 Transaction Bearer Control 格式如下：

![](https://i-blog.csdnimg.cn/img_convert/fe294dcc521a12f34d9d70c90eb86f10.png)

我们先来看一个 btsnoop

![](https://i-blog.csdnimg.cn/img_convert/5d514edc7836007094f66f5ca8b610d7.png)

![](https://i-blog.csdnimg.cn/img_convert/8d118b829835e71ac194071e81b286f7.png)

###### 2. Link ACK

未配网设备收到配网者的 Link Open 消息后，响应的消息。数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/d40a3ab83a191379a0424af2af51e86f.png)

结合 PB-ADV 跟 Transaction Bearer Control 格式如下：

![](https://i-blog.csdnimg.cn/img_convert/b33b7e5efa38355c730bbee353824a54.png)

![](https://i-blog.csdnimg.cn/img_convert/71319ea0c86dbf9cfdf0316b47e40f46.png)

![](https://i-blog.csdnimg.cn/img_convert/c99777a0861987d8631705b76dabe739.png)

###### 3. Link Close

配网者和未配网设备都可发起，该消息至少发送三次，不需要 ack。用于告知对端链路关闭，当前配网流程结束及配网的结果。  
其数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/d459a20f5744ff9da98ce2be4cef52ca.png)

结合 PB-ADV 跟 Transaction Bearer Control 格式如下：

![](https://i-blog.csdnimg.cn/img_convert/295e7332f8657a68928799b804476d80.png)

参数域为关闭原因，其具体含义如下：

![](https://i-blog.csdnimg.cn/img_convert/b23ba20839283a68402c8c7043a630b1.png)

###### 4. Link Establishment 流程

PV-ADV 在交换配网数据之前需要建立一个链接（Link），使用 Transaction Bearer Control 消息来建立链路。未配网设备发出的 Unprovisioned Beacon 里面包含了 UUID 等信息，配网者收到多个 Unprovisioned Beacon 后，需要选择一个设备，然后开始配网，选择了这个设备的第一件事就是建立链路。链路建立的流程如下：

![](https://i-blog.csdnimg.cn/img_convert/250e31f11284fe02247b32c6af034dfe.png)

我们也分析一个 btsnoop 来加深下流程分析

![](https://i-blog.csdnimg.cn/img_convert/0d02f29884317c712386b6a312698d7e.png)

**① Unprovisioned device 发送 Beacon 广播**

格式先不用纠结，我们后面再介绍，你就知道，这个就是发送一个 mesh beacon 就好了，意思就是告诉 provisioner 期待入网，并且 Unprovisioned device 的 uuid 为 16 个 byte 全 0

![](https://i-blog.csdnimg.cn/img_convert/7d2750b87f64a555040c7f7a7ef6175a.png)

**② 配网者选择一个 Unprovisioned Beacon，然后向该设备发送一个 Link Open 消息，该消息带有该设备的 Device UUID，并在 PB-ADV 的 Link ID 字段填上一个未使用的 ID 值。**

![](https://i-blog.csdnimg.cn/img_convert/6b49393b22e9a8d13ce661c4e9b00cdd.png)

**③ 未配网设备收到 Link Open 消息后，需要响应一个 Link ACK 消息，其消息的 Link ID 字段为接收的 Link Open 的 Link ID。**

![](https://i-blog.csdnimg.cn/img_convert/33cfa0f579b5c1756c39092dcea547f9.png)

**④ Link 通道建立完成后，两者之间进行配网流程。**

这个过程我们在其他章节介绍

**⑤ 配网结束发送 Link Close 关闭通道。**

![](https://i-blog.csdnimg.cn/img_convert/9715dd8e1c1089ff0fbfe17fef406182.png)

每一个 Generic Provisioning PDU 发送时都要附加 20-50ms 的延时。对于分段消息，发送端通过 Transaction Start 和 Transaction Continuation 发送所有分段，接收端收到所有分段后计算 FCS，然后再响应 Transaction Acknowledgment 消息。

#### b. Proxy protocol

BLE Mesh Proxy Protocol 是 BLE Mesh 网络中的一种关键协议，用于让传统的 BLE 设备与 Mesh 网络进行通信。由于普通 BLE 设备（非 Mesh 设备）无法直接参与 Mesh 网络，Proxy Protocol 提供了一种桥接机制，使它们可以通过支持 Proxy 功能的 Mesh 节点（称为 Proxy 节点）访问 Mesh 网络的功能。

**BLE Mesh Proxy Protocol 的主要功能和概念：**

*   **Proxy 节点**：

*   *   Proxy 节点是具有 BLE Mesh 功能的设备，它能够与 Mesh 网络通信，同时也支持与传统 BLE 设备（例如手机、平板等）建立标准的 BLE 连接。
    *   Proxy 节点通过 BLE GATT（通用属性配置文件）服务来提供访问 Mesh 网络的入口。

*   **Proxy 协议的工作原理**：

*   *   Proxy 协议允许普通 BLE 设备通过标准 BLE 连接访问 Mesh 网络中的功能。
    *   它使用了 **Proxy PDU（Protocol Data Unit）**，这些 PDU 被封装在 GATT 的特定特征中，用于传输 Mesh 数据。
    *   Proxy 节点通过 `Mesh Proxy Service` 向传统 BLE 设备暴露 Mesh 网络数据。

*   **Mesh Proxy Service**：

*   *   Proxy 节点通过 GATT 提供 `Mesh Proxy Service`。该服务包含两个主要特征：

*   *   *   **Mesh Proxy Data In**：用于从传统 BLE 设备向 Mesh 网络发送数据。
        *   **Mesh Proxy Data Out**：用于从 Mesh 网络向传统 BLE 设备发送数据。

*   **Proxy Protocol 数据传输**：

*   *   Mesh Proxy Protocol 使用 Proxy PDU 来封装和传输 Mesh 网络中的消息。
    *   在 BLE 连接中，Mesh 消息通过 GATT 服务传输，Proxy 节点充当桥梁，将消息从 BLE 网络传递到 Mesh 网络，反之亦然。

*   **使用场景**：

*   *   **手机与 Mesh 网络通信**：例如，用户通过手机控制家中的智能灯光，这些灯具组成一个 Mesh 网络。手机通过 Proxy 协议与最近的 Proxy 节点通信，从而访问和控制整个 Mesh 网络。
    *   **Mesh 网络配置与管理**：Proxy 协议也可以用于通过普通 BLE 设备（如手机）配置和管理 Mesh 网络中的设备。

**Proxy 协议的优点：**

*   **兼容性**：使得普通 BLE 设备能够与 Mesh 网络通信，无需特殊的 Mesh 功能。
*   **灵活性**：通过 Proxy 节点，可以方便地使用标准 BLE 设备来控制和管理 Mesh 网络。

**主要特点总结：**

*   使用 GATT 代理服务桥接 BLE 设备和 Mesh 网络。
*   通过 Proxy PDU 实现 Mesh 消息的封装和传输。
*   支持低功耗设备与 Mesh 网络的通信。

Proxy 协议的设计确保了 BLE Mesh 网络的广泛兼容性和实用性，使得普通 BLE 设备能够轻松接入并参与 Mesh 网络。

![](https://i-blog.csdnimg.cn/img_convert/31365395c32ecb7ffcdc4b1bbdccedbc.png)

**注意：proxy PDU 并不仅仅用在 provisioning stack 中，我们放在这里介绍，是因为我们这里用到了 proxy PDU**

PDU 格式为：

![](https://i-blog.csdnimg.cn/img_convert/83e6818ea6d3e8cab889eaa00254720f.png)

![](https://i-blog.csdnimg.cn/img_convert/15c55da8737a8ccd743e680a3983bc6d.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>SAR</p></td><td><p>2</p></td><td><p>0b00：表示消息是一个完整的消息<br>0b01：表示分段消息的第一个分段<br>0b10：表示分段消息的中间某一段<br>0b11：表示分段消息的最后一分段</p></td></tr><tr><td><p>Message Type</p></td><td><p>6</p></td><td><p>0x00：Network PDU<br>0x01：Mesh Beacon<br>0x02：Proxy Configuration<br>0x03：Provisioning PDU<br>0x04-0x3F：RFU</p></td></tr><tr><td><p>Data</p></td><td><p>variable</p></td><td><p>message</p></td></tr></tbody></table>

##### ⅰ. Proxy filtering

每个代理过来的消息，接收端收到都要进行 dst 地址的检查，为了避免无效地址的消息，在代理端增加过滤机制。配置黑白名单，通过 Message Type=0x02 的 Proxy PDU 来配置，其 Data 域的数据格式如下：

![](https://i-blog.csdnimg.cn/img_convert/a4e01794091c3f97f317dd7c12ee6b37.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Opcode</p></td><td><p>1</p></td><td><p>0x00：设置过滤表类型<br>0x01：添加地址到过滤表<br>0x02：删除过滤表中的地址<br>0x03：当前过滤表的状态<br>0x04-0xFF：RFU</p></td></tr><tr><td><p>Parameters</p></td><td><p>Variable</p></td><td><p>消息参数</p></td></tr></tbody></table>

每个 Opcode 对应的 Parameters 对应的格式如下：

![](https://i-blog.csdnimg.cn/img_convert/f56ffd0f076517f72f7de6f428b62543.png)

##### ⅱ. Proxy Server/Client

Client：只能使用 GATT 连接，不能使用 ADV 进行 mesh 通信的节点。  
Server：能在 ADV Bearer 和 GATT Bearer 之间转换的节点。

![](https://i-blog.csdnimg.cn/img_convert/eda64472c3a3f0bb61d86618927d7cb9.png)

① client 连接 server

② server 端初始化过滤名单为空的白名单

③ 连接成功后，server 端发送 Secure Network Beacon 给 client 端。

④ client 设置过滤表类型，server 响应过滤表状态。更改过滤表类型后，新的过滤表为空。

⑤ client 修改黑白名单内容，两者之间根据过滤表进行通信。

### 3. Provisioning protocol

PB-ADV 通过 Transaction Start/Acknowledgment/Continuation/Bearer Control 来进行链路的建立和分段数据的发送，同样的功能 PB-GATT 使用 Proxy 协议来实现。两种方法的最终目的是为了传输 Provisioning PDUs，来进行配网数据的交换。架构如下：

![](https://i-blog.csdnimg.cn/img_convert/7426acc8bf4113dc9475e978ed4d8c25.png)

provisioning protocol 分为两个角色：Provisioner/Provisionee

The Provisioner is a device that initiates the provisioning protocol. The Provisionee is a device that  
participates in the execution of the provisioning protocol with the Provisioner, upon request from the Provisioner .

我们本次介绍的主要就是配网过程，也就是红框部分！

![](https://i-blog.csdnimg.cn/img_convert/4353194717a7d0eba05ca0867d1cafe8.png)

Provisioning PDUs 的消息格式如下：

![](https://i-blog.csdnimg.cn/img_convert/a390f915be5853184b900a4b1081ae4a.png)

![](https://i-blog.csdnimg.cn/img_convert/d7b37491440411da913844f40d2d3e79.png)

![](https://i-blog.csdnimg.cn/img_convert/3ad07237dbe8bb6be81c43fe5b980953.png)

其中 Type 定义在 Assigned number 中，有以下定义：

![](https://i-blog.csdnimg.cn/img_convert/f57e6875db0930e2d6ff1b91592fe670.png)

![](https://i-blog.csdnimg.cn/img_convert/cfb8a1915e41227613f2952cea794827.png)

#### a. Provisioning Invite

配网者发起，表明配网程序开始。格式如下：

![](https://i-blog.csdnimg.cn/img_convert/461ebb38144aa8ad95e5c32538d8caeb.png)

![](https://i-blog.csdnimg.cn/img_convert/4ddbbbc9d3028ce7ad54085a3c50df82.png)

<table><tbody><tr><td><p><strong>Value</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>0x00</p></td><td><p>Attention Timer 关闭</p></td></tr><tr><td><p>0x01-0xFF</p></td><td><p>Timer 开启的剩余时间，单位 1s</p></td></tr></tbody></table>

#### b. Provisioning Capabilities

未配网设备发送此消息告诉配网者当前节点支持的配网功能。

![](https://i-blog.csdnimg.cn/img_convert/78b449f42d88de6f3205b7d4ff97e347.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>Number of Elenments</p></td><td><p>1</p></td><td><p>当前设备有多少个元素，取值范围为 0x01-0xFF。配网者可以通过此字段计算出下一个未配网设备的首元素地址</p></td></tr><tr><td><p>Algorithms</p></td><td><p>2</p></td><td><p>支持的算法</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/4c933b96b78f46acb877eb5370af789b.png"></p></td></tr><tr><td><p>Public Key Type</p></td><td><p>1</p></td><td><p>支持的 Public Key 类型</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/974ac610026a06c3406ae35bef6a0414.png"></p></td></tr><tr><td><p>Static OOB Type</p></td><td><p>1</p></td><td><p>支持的 Static OOB 类型</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/54e9afeec5c51a79fcde23c6b687c8c1.png"></p></td></tr><tr><td><p>Output OOB Size</p></td><td><p>1</p></td><td><p>设备支持的最大 Output OOB 的长度<br>0x00：不支持 output OOB<br>0x01-0x08：设备支持的最大 Output OOB 的长度<br>0x09-0xFF：RFU</p></td></tr><tr><td><p>Output OOB Action</p></td><td><p>2</p></td><td><p>设备支持的 Output OOB 的行为</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/7bce529b8878d79c9502f60f440acf1a.png"></p></td></tr><tr><td><p>Input OOB Size</p></td><td><p>1</p></td><td><p>设备支持的最大 Input OOB 的长度<br>0x00：不支持 Input OOB<br>0x01-0x08：设备支持的最大 Input OOB 的长度<br>0x09-0xFF：RFU</p></td></tr><tr><td><p>Input OOB Action</p></td><td><p>2</p></td><td><p>设备支持的 Input OOB 的行为</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/905e497cd971659eaa793207576cd9dd.png"></p></td></tr></tbody></table>

#### c. Provisioning Start

配网者发送此消息告诉未配网设备选择的配网方式。

![](https://i-blog.csdnimg.cn/img_convert/370d8ce1ba6902d22c444d1d5293ab62.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>Algorithms</p></td><td><p>1</p></td><td><p>使用的算法</p><p><img class="" src="https://i-blog.csdnimg.cn/img_convert/bae9b3411b32def1a0c04eabba016b01.png"></p></td></tr><tr><td><p>Public Key</p></td><td><p>1</p></td><td><p>是否使用 Public Key<br>0x00：不使用 OOB Public Key<br>0x01：使用 OOB Public Key<br>0x02-0xFF：无效值</p></td></tr><tr><td><p>Authentication Method</p></td><td><p>1</p></td><td><p>授权方式选择<br>0x00：使用 No OOB 方式授权<br>0x01：使用 Static OOB 方式授权<br>0x02：使用 Output OOB 方式授权<br>0x03：使用 Input OOB 方式授权<br>0x04-0xFF：无效值</p></td></tr><tr><td><p>Authentication Action</p></td><td><p>1</p></td><td><p>授权行为</p><p>若授权方式为 No/Static OOB，Action=0x00。</p><p>若授权方式为 Output OOB，取值含义如下：</p><p>0x00：Blink</p><p>0x01：Beep</p><p>0x02：Vibrate</p><p>0x03：Output Numeric</p><p>0x04：Output Alphanumeric</p><p>0x05-0xFF：RFU</p><p>若授权方式为 Input OOB，取值含义如下：</p><p>0x00：Push</p><p>0x01：Twist</p><p>0x02：Input Numeric</p><p>0x03：Input Alphanumeric</p><p>0x04-0xFF：RFU</p></td></tr><tr><td><p>Authentication Size</p></td><td><p>1</p></td><td><p>授权码的长度<br>若授权方式为 No/Static OOB，Size=0x00。<br>若授权方式为 Output/Input OOB，取值含义如下：<br>0x00：无效<br>0x01-0x08：授权码长度<br>0x09-0xFF：RFU</p></td></tr></tbody></table>

#### d. Provisioning Public Key

配网者发送此消息，传输 Public Key。

![](https://i-blog.csdnimg.cn/img_convert/69633fb88bec1bb1c6167be7dc3714e9.png)

#### e. **Provisioning Input Complete**

未配网设备发送此消息，表明 Input 操作完成，参数域为空。

![](https://i-blog.csdnimg.cn/img_convert/cc57e0585071364417d6012697bf5abf.png)

#### f. Provisioning Confirmation

发送给对端的 OOB 授权码数据。

![](https://i-blog.csdnimg.cn/img_convert/b080bf821eb367db0410a8e7d24ce488.png)

Output OOB 方式：未配网设备展示授权码，配网者输入授权码，配网者响应 Confirmation 消息。  
Input OOB 方式：配网者展示授权码，未配网设备输入授权码，未配网设备响应 Input Complete 消息，然后配网者响应 Confirmation 消息。

#### g. Provisioning Random

发送给对端的随机值认证确认信息。

![](https://i-blog.csdnimg.cn/img_convert/7c4d530674708c2d19d580b410394e74.png)

未配网设备收到配网者发送的 Confirmation 信息，然后响应 Confirmation 信息回配网者，此时配网者收到后发送 Random 消息，未配网设备收到后验证 Confirmation 信息，验证完毕后再响应 Random 消息回配网者，然后配网者也进行 Confirmation 的验证操作。

#### h. Provisioning Data

配网者传递给未配网设备的配网信息。  
配网信息中 Provisioning Data 主要有以下信息：

![](https://i-blog.csdnimg.cn/img_convert/1be0dbcd0fe972701e0019bc59b98ef1.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>Network Key</p></td><td><p>16</p></td><td><p>配网者分配的 NetKey</p></td></tr><tr><td><p>Key Index</p></td><td><p>2</p></td><td><p>NetKey 对应的 Index 值</p></td></tr><tr><td><p>Flags</p></td><td><p>1</p></td><td><p>网络更新状态的标志位</p><p>Key Refresh Flag=0：表示当前网络处于 Key Refresh Phase 0。</p><p>Key Refresh Flag=1：表示当前网络处于 Key Refresh Phase 2。</p><p>IV Update Flag=0：表示当前网络未进行 IV Update。</p><p>IV Update Flag=1：表示当前网络正在进行 IV Update。</p></td></tr><tr><td><p>IV Index</p></td><td><p>4</p></td><td><p>当前的 IV Index 值</p></td></tr><tr><td><p>Unicast Address</p></td><td><p>2</p></td><td><p>配网者分配的首元素的单播地址</p></td></tr></tbody></table>

#### i. Provisioning Complete

未配网设备发送此消息表明配网成功。参数域为空。

![](https://i-blog.csdnimg.cn/img_convert/56e3aab74a598506fb6504b71c01ad9c.png)

#### j. Provisioning Failed

未配网设备发送此消息表明配网失败。参数域为失败原因。

![](https://i-blog.csdnimg.cn/img_convert/bc51feaae694a759ac4e0bf17906cb0e.png)

![](https://i-blog.csdnimg.cn/img_convert/52a71ced83b4500a52f735e6910b9e1d.png)

#### k. Provisioning Record Request

#### l. Provisioning Record Response

#### m. Provisioning Records Get

#### n. Provisioning Records List

#### o. 流程整理

官网文档的图示如下：

![](https://i-blog.csdnimg.cn/img_convert/d55fea4fc3bd406b3e5e971e8699d426.png)

![](https://i-blog.csdnimg.cn/img_convert/83c120468bc114b482d4803da7152344.png)

![](https://i-blog.csdnimg.cn/img_convert/ec3f99f3616aefabef398d082bbe5f20.png)

① Link 通道链路建立完成后，配网者发送 **Provisioning Invite PDU**，未配网设备收到后开启 Attention Timer，可以是闪灯，震动或者声音来提醒配网者你配置的是这个设备，接着再响应 **Provisioning Capabilities PDU** 告诉配网者，这个设备支持的配网方式。

② 配网者发送 **Provisioning Start PDU** 告诉设备配网端选择的配网方式，未配网设备收到此消息后，需要停止 Attention Timer。**Provisioning Start PDU** 选择的方式有选择最优的算法，OOB 方式等。然后进入第二阶段 Public Key 交换。

③ 若设备的能力中不能通过 OOB 的方式传输 Public Key，即 Public Key Type 域为 0x00，此时配网者发送 Provision Public Key 消息，设备端收到后响应 Provision Public Key 消息，使两端交换 Public Key。

④ 若设备能通过 OOB 的方式传输 Public Key，比如 NFC 等，则配网者通过 OOB 的方式将 Public Key 传输至未配网设备端。

⑤ 设备端收到 Public Key 后，两端计算 ECDHSecret 值。接下来进入第三阶段 OOB 认证。

⑥ OOB 认证有四种方式，当配网者选择 No OOB 认证的方式时，配网者发送 **Provisioning Confirmation** 消息，参数域为空，设备收到后响应 **Provisioning Confirmation** 消息，表示确认。

⑦ 当配网者选择 Static OOB 认证的方式时，配网者发送 **Provisioning Confirmation** 消息，参数域为 Static 授权数据，设备收到后响应 **Provisioning Confirmation** 消息，表示确认。

⑧ 当配网者选择 Output OOB 认证的方式时，收到 Start PDU 消息后，设备按照被选择的 Output Action，做出相应的操作，比如闪灯，声音，震动，屏上显示数字或字符等，配网者将观察到的数据通过 Provisioning Confirmation 发送给未配网设备，设备收到并确认后响应 **Provisioning Confirmation** 消息。

⑨ 当配网者选择 Input OOB 认证的方式时，配网者发送完 Start PDU 后，在配网端显示授权信息，如屏幕显示数字或者字母等，设备端收到 Start PDU 后，弹框需要用户输入观察到的授权码，输入完毕后，通过 **Provisioning Input Complete** 消息发送给配网者告诉配网者这边输入完毕，配网者收到后发送 **Provisioning Confirmation** 发送给未配网设备，设备收到并确认后响应 Provisioning Confirmation 消息。

⑩ 配网者收到未配网设备响应的 Provisioning Confirmation 消息后，确认无误后，发送 P**rovisioning Random** 消息 ConfirmationProvisioner。

⑪ 设备端收到 Random 消息后，验证无误后，响应 **Provisioning Random** 消息，其参数域值为 ConfirmationDevice。

⑫ 配网者收到后验证 random 值的有效性。开始进入第四阶段，配网数据的的分发。配网者发送 **Provisioning Data PDU**，包含设备需要的配网信息，其中的信息通过授权后的数据信息进行加密传输。

⑬ 设备收到数据后，响应 **Provisioning Complete** 消息，配网结束。

⑭ 若配网期间出现错误，发送 **Provisioning Failed** 消息给对端，配网结束。

⑮ 配网结束后，发送 Link Close 消息关闭链路。

我们来分析一个 btsnoop 来看下整个流程

![](https://i-blog.csdnimg.cn/img_convert/6f6cf652ec2374f4405dd39644428aff.png)

##### ⅰ. 配网者发送 Provisioning Invite PDU

配网者发起，表明配网程序开始，Attention 的值为 5S

![](https://i-blog.csdnimg.cn/img_convert/343815f105d07d7d7bf392a01314ea54.png)

##### ⅱ. 待配网者响应 Provisioning Capabilities PDU

![](https://i-blog.csdnimg.cn/img_convert/db23fb70c2a7ce638506e7ca48748eb5.png)

参数如下：

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>Number of Elenments</p></td><td><p>1</p></td><td><p>1 个元素</p></td></tr><tr><td><p>Algorithms</p></td><td><p>2</p></td><td><p>0x03, 代表支持</p><p>BTM_ECDH_P256_CMAC_AES128_AES_CCM</p><p>BTM_ECDH_P256_HMAC_SHA256_AES_CCM</p></td></tr><tr><td><p>Public Key Type</p></td><td><p>1</p></td><td><p>0x00, 代表不支持 OOB</p></td></tr><tr><td><p>Static OOB Type</p></td><td><p>1</p></td><td><p>0x00, 代表不支持 Static OOB</p></td></tr><tr><td><p>Output OOB Size</p></td><td><p>1</p></td><td><p>0x04，设备支持的最大 Output OOB 的长度为 4</p></td></tr><tr><td><p>Output OOB Action</p></td><td><p>2</p></td><td><p>0x08, 设备支持的 Output OOB 的行为，仅仅支持显示数字</p></td></tr><tr><td><p>Input OOB Size</p></td><td><p>1</p></td><td><p>0x00：不支持 Input OOB</p></td></tr><tr><td><p>Input OOB Action</p></td><td><p>2</p></td><td><p>0x00, 设备支持的 Input OOB 的行为, 都不支持</p></td></tr></tbody></table>

根据参数写上，我们就做这条路来继续交互

![](https://i-blog.csdnimg.cn/img_convert/553b5bb233f8fdc76693ffcbefdc7e70.png)

##### ⅲ. 配网者发送 Provisioning Start PDU

![](https://i-blog.csdnimg.cn/img_convert/2380f515773538f26eff2c1f61ce5947.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>Algorithms</p></td><td><p>1</p></td><td><p>0x01 :BTM_ECDH_P256_HMAC_SHA256_AES_CCM</p></td></tr><tr><td><p>Public Key</p></td><td><p>1</p></td><td><p>0x00：不使用 OOB Public Key</p></td></tr><tr><td><p>Authentication Method</p></td><td><p>1</p></td><td><p>0x00：使用 No OOB 方式授权</p></td></tr><tr><td><p>Authentication Action</p></td><td><p>1</p></td><td><p>0x00 Action None</p></td></tr><tr><td><p>Authentication Size</p></td><td><p>1</p></td><td><p>0x00 授权码的长度</p></td></tr></tbody></table>

##### ⅳ. 交互 public key

![](https://i-blog.csdnimg.cn/img_convert/17d41c56263a9653f3efe6e91d8602b5.png)

![](https://i-blog.csdnimg.cn/img_convert/4d9241dabab447867494b486bfdf3fb3.png)

![](https://i-blog.csdnimg.cn/img_convert/bae1603f185b29237de5b345cdec167c.png)

根据上面的交互，我们匹配到了这条路

![](https://i-blog.csdnimg.cn/img_convert/e3b045ee2ff9713dba946d81029024c5.png)

所以我们继续分析

##### ⅴ. 交互 Provisioning Confirmation

![](https://i-blog.csdnimg.cn/img_convert/49b45a0e584ebc156d8d4e582c15ec91.png)

![](https://i-blog.csdnimg.cn/img_convert/889487441596d52c336bd912d5c76cd6.png)

![](https://i-blog.csdnimg.cn/img_convert/a67a04a6ef9d1c18f3a91a881a798268.png)

##### ⅵ. 交互 Provisioning Random

![](https://i-blog.csdnimg.cn/img_convert/6971a4bc106b0a401775f8e7f7a8239e.png)

![](https://i-blog.csdnimg.cn/img_convert/15c9c518b9d345fb624cfdfe33659c8c.png)

![](https://i-blog.csdnimg.cn/img_convert/50b818229c079d1a9762881a9d2e64a4.png)

##### ⅶ. Provisioning Data

配网者传递给未配网设备的配网信息。

![](https://i-blog.csdnimg.cn/img_convert/c72677a55a23531ffaaa818dd5318a64.png)

![](https://i-blog.csdnimg.cn/img_convert/23b92c3d4ea0cafb546848f3ca993fdf.png)

##### ⅷ. Provisioning Complete

未配网设备发送此消息表明配网成功。参数域为空。

![](https://i-blog.csdnimg.cn/img_convert/6afb674ca6f172c44eefd4621163521c.png)

三. Mesh networking stack
------------------------

### 1. network layer

![](https://i-blog.csdnimg.cn/img_convert/4f9b0b20315af0f251e446c0f55cc42d.png)

BLE Mesh 网络层（Network Layer）是 BLE Mesh 协议栈的重要组成部分，负责在节点之间转发消息，确保消息能够跨越多个中继节点到达目标节点。以下是 BLE Mesh 网络层的主要功能和特点：

**消息转发**

*   **中继功能**：网络层支持节点作为中继，将接收到的消息转发给其他节点，扩展了网络的覆盖范围。
*   **TTL（生存时间）**：消息中包含一个 TTL 字段，指示消息还能转发的次数，防止消息在网络中无限传播。

**地址管理**

*   **Unicast 地址**：分配给单个节点的唯一地址，用于点对点通信。
*   **Group 地址**：用于将消息发送给一组节点，实现组播通信。
*   **Virtual 地址**：使用哈希算法生成的地址，支持更灵活的组播通信。

**加密与认证**

*   **网络密钥（NetKey）**：用于网络层的加密和认证，确保消息的完整性和机密性。
*   **消息认证码（MIC）**：附加在消息中的认证码，验证消息的完整性和真实性。

**去重功能**

*   网络层通过消息序列号和源地址来识别和丢弃重复消息，防止网络资源浪费和循环。

**低功耗支持**

*   支持低功耗节点（Low Power Node, LPN）和好友节点（Friend Node），通过减少消息转发频率和存储消息来优化低功耗设备的能耗。

**网络消息格式**

*   网络消息通常由以下部分组成：

*   *   **网络头部（Network Header）**：包含 TTL、控制位、源地址、目标地址等信息。
    *   **网络帧控制字段（Control Field）**：标识消息类型（数据或控制消息）。
    *   **负载（Payload）**：实际的应用层数据或控制信息。
    *   **消息认证码（MIC）**：用于消息认证。

**支持多种消息类型**

*   **数据消息（Data Message）**：承载应用层的数据。
*   **控制消息（Control Message）**：用于网络管理和控制，如心跳消息、配置消息等。

**路径选择与优化**

*   虽然 BLE Mesh 网络是基于泛洪（Flooding）方式的，但网络层仍支持基本的路径优化，如通过 TTL 值限制消息传播范围。

BLE Mesh 网络层的这些功能和特点使其能够在大规模分布式网络中高效地管理消息传递、确保网络的可靠性和安全性，并支持不同类型的节点和用例。

#### a. 地址

在 BLE Mesh 网络中，网络层定义了四种基本类型的地址，每种地址都有其特定的用途和作用。以下是这四种地址的简要介绍：

**未分配地址（Unassigned Address）**：

*   *   这是默认的地址，当一个节点还没有被分配任何地址时，会使用未分配地址（0x0000）。这个地址表示该节点尚未在网络中注册，不能参与任何通信。

**单播地址（Unicast Address）**：

*   *   单播地址是唯一分配给每个节点的地址，用于一对一的通信。每个节点都需要有一个唯一的单播地址，这个地址的范围是从 0x0001 到 0x7FFF。单播地址用于目标明确的消息传递，比如控制单个设备的状态。

**虚拟地址（Virtual Address）**：

*   *   虚拟地址是一种基于 UUID 的地址，用于标识具有相同 UUID 的节点组。它允许多个节点共享一个虚拟地址，实现基于特定属性或功能的消息广播。虚拟地址使用 128 位的 UUID 来表示，适用于需要逻辑分组的场景。

**组播地址（Group Address）**：

*   *   组播地址用于一对多的通信，允许将消息发送给属于同一组的多个节点。组播地址的范围是从 0xC000 到 0xFEFF。组播地址用于需要控制一组设备的场景，比如同时打开或关闭一组灯具。

通过这四种地址类型，BLE Mesh 网络能够灵活地支持各种通信需求，从单个设备的精确控制到整个设备组的管理。下面是整个

![](https://i-blog.csdnimg.cn/img_convert/2b17fbec96643fc8afeb58f6e3157fa5.png)

#### b. PDU 介绍

网络层数据大小为 **18-29 字节**

![](https://i-blog.csdnimg.cn/img_convert/7189ffae03ea16863bbe9185613b2b9b.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(octets)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>IVI</p></td><td><p>1</p></td><td><p>32bits IV 值的最低有效位</p></td></tr><tr><td><p>NID</p></td><td><p>7</p></td><td><p>由 NetKey 生成的 7bits NID</p></td></tr><tr><td><p>CTL</p></td><td><p>1</p></td><td><p>CTL=0，表明这条消息是 access msg；CTL=1，表明这条消息是 control msg。</p></td></tr><tr><td><p>TTL</p></td><td><p>7</p></td><td><p>Time To Live 值</p></td></tr><tr><td><p>SEQ</p></td><td><p>24</p></td><td><p>Sequence Number</p></td></tr><tr><td><p>SRC</p></td><td><p>16</p></td><td><p>源地址</p></td></tr><tr><td><p>DST</p></td><td><p>16</p></td><td><p>目的地址</p></td></tr><tr><td><p>TransportPDU</p></td><td><p>8-128</p></td><td><p>传输层下发的数据载荷。CTL=0， 最大载荷为 128bits；CTL=1，最大载荷为 96bits。</p></td></tr><tr><td><p>NetMIC</p></td><td><p>32/64</p></td><td><p>Network Message Integrity Check。CTL=0，NetMIC =32bits；CTL=1，NetMIC=64bits。</p></td></tr></tbody></table>

#### c. Network layer behavior

**Relay/Proxy**

网络层负责消息的转发。

若当前节点支持中继，且接收到的消息 TTL 大于 2，目的地址非本节点元素的单播地址。则该消息可以被中继，将 TTL 减 1，附加一个随机延迟，然后再广播出去。

若当前节点支持代理，且接收到的消息 TTL 大于 2，目的地址非本节点元素的单播地址。若该消息来自 GATT 连接，则该消息 TTL 减 1，再通过 ADV Bearer 转发出去；若该消息来自 ADV Bearer，则该消息 TTL 减 1，再通过 GATT Bearer 转发出去。

**Network Message Cache**

TTL 从时间上保证了一条消息不能无限次中继，每中继一次 TTL 减 1，为 1 时就不再中继。

而 Network Message Cache 就从空间上保证，同一条消息不会被同一节点中继两次。

**Network Layer 消息接收**

① 检查 NID 是否匹配已知的 NID。

② 授权匹配 NetKey。

③ 检查 SRC/DST 是否有效。

④ 检查是否处于 cache 中。

⑤ 上报至传输层。

⑥ 检查是否可以被代理或中继。

**Network Layer 消息发送**

① 设置 IVI 域为 32bits IV 只得最低有效位。

② 设置 NID 域为通过加密 key 生成的 NID。

③ 对 DST 和 TransportPDU 进行加密，生成 NetMIC。

④ 对 CTL/TTL/SEQ/SRC 进行混淆处理。

⑤ 将消息发送至所有的网络接口，通过该接口规则对消息进行过滤，然后发送至 Bearer Layer。

### 2. Lower transport layer

![](https://i-blog.csdnimg.cn/img_convert/f604d9e198ab0d949a2738761b7ff35b.png)

BLE Mesh 的下层传输层（Lower Transport Layer）是网络层和上层传输层之间的桥梁，负责消息的分片、重组、加密和解密等任务。它在整个数据传输过程中起到了至关重要的作用。以下是对 BLE Mesh 下层传输层的详细介绍：

**消息分片与重组**

*   **分片**：当应用层或上层传输层发送的消息长度超过基础 BLE 链路层支持的最大传输单元（MTU）时，下层传输层会将长消息分片为多个较小的段，每个段可以独立传输。
*   **重组**：接收端的下层传输层会将收到的各个分片重新组合成完整的消息，再交给上层处理。

**消息类型**

*   **单个分片消息（Single Segment Message）**：适用于长度小于等于 BLE 链路层 MTU 的消息，可以在一次传输中完成。
*   **分段消息（Segmented Message）**：适用于长度超过 MTU 的消息，需要分片传输，多个分片需要按照顺序接收并重组。

**可靠性和重传**

*   **确认机制**：下层传输层支持可靠传输，即通过接收端的确认（ACK）来确保消息成功到达。如果发送端在规定时间内未收到 ACK，会进行重传。
*   **重传机制**：对于分段消息，若某些分片丢失或未能被接收端确认，发送端会重新发送丢失的分片，确保消息的完整性和可靠性。

**加密与解密**

*   **加密**：在发送消息前，下层传输层会对消息进行加密，以确保数据在传输过程中的安全性。
*   **解密**：接收端在收到消息后，会使用与发送端相同的加密密钥进行解密，确保消息的完整性和机密性。

**心跳消息**

*   下层传输层还负责处理心跳消息，这种消息用于网络拓扑的管理和健康监控，帮助节点了解网络中的其他节点的存活状态。

**应用场景**

*   下层传输层在 BLE Mesh 网络中非常关键，确保消息能够可靠、完整地传输和接收，同时也提供了安全保障，适用于智能家居、工业自动化等需要稳定和安全数据传输的场景。

总的来说，BLE Mesh 的下层传输层通过分片与重组、加密与解密、可靠传输等机制，为 BLE Mesh 网络提供了稳定和安全的数据传输基础。

#### a. Lower Transport PDU

在 Lower Transport PDU 中的第一个 byte 的有 SEG filed 中决定是否分段

![](https://i-blog.csdnimg.cn/img_convert/d6b57131629d2209b583aeb41fa12732.png)

在 network layer 中有 CTL Field 中，决定是 Access Message 还是 Control Message, 所以对于 Lower Transport PDU 有以下四种格式：

![](https://i-blog.csdnimg.cn/img_convert/a62600c95ce7507aa97f82e0b0090363.png)

##### ⅰ. 未分段接入层消息（Unsegmented Access Message）

未分段接入层消息（**6-16 字节**）的每个分段的结构如下：

![](https://i-blog.csdnimg.cn/img_convert/d1e445d9b8773e7707b47e3b02f72ce4.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(bits)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>SEG</p></td><td><p>1</p></td><td><p>SEG=0，表示当前消息是未分段消息</p></td></tr><tr><td><p>AKF</p></td><td><p>1</p></td><td><p>AKF=1，表示使用 Appkey 加密；</p><p>AKF=0，表示使用 DevKey 加密，AID=0b000000</p></td></tr><tr><td><p>AID</p></td><td><p>6</p></td><td><p>AppKey ID，当 AKF= 1 时有效</p></td></tr><tr><td><p>Upper Transport Access PDU</p></td><td><p>40-120</p></td><td><p>上层传输层接入消息 PDU</p></td></tr></tbody></table>

接入层消息至少有 4 字节的 TransMIC，以及 1 字节的 Opocde，所有未分段接入层消息最少为 5 字节。  
接入层消息最大为 15 字节，除去 4 字节的 TransMIC，所以从 Model Layer 下来的消息最大为 11 字节，超过 11 字节就要分段。

##### ⅱ. 分段接入层消息（Segmented Access Message）

分段接入层消息（**5-16 字节**）的每个分段的结构如下：

![](https://i-blog.csdnimg.cn/img_convert/b3bb09ba6b548a6e4a322b9583a0be7e.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(bits)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>SEG</p></td><td><p>1</p></td><td><p>SEG=1，表示当前消息是分段消息</p></td></tr><tr><td><p>AKF</p></td><td><p>1</p></td><td><p>AKF=1，表示使用 Appkey 加密；</p><p>AKF=0，表示使用 DevKey 加密，AID=0b000000</p></td></tr><tr><td><p>AID</p></td><td><p>6</p></td><td><p>AppKey ID，当 AKF= 1 时有效</p></td></tr><tr><td><p>SZMIC</p></td><td><p>1</p></td><td><p>TtansMIC 的大小。SZMIC=0，表示 TransMIC 为 4 字节；SZMIC=1，表示 TransMIC 为 8 字节</p></td></tr><tr><td><p>SeqZero</p></td><td><p>13</p></td><td><p><strong>SeqAuth</strong> 的最低 13 位有效位</p></td></tr><tr><td><p>SegO</p></td><td><p>5</p></td><td><p>表示当前分段位第几个分段</p></td></tr><tr><td><p>SegN</p></td><td><p>5</p></td><td><p>表示此条消息总共有多少分段</p></td></tr><tr><td><p>Segment m</p></td><td><p>8-96</p></td><td><p>此分段的消息内容，只有最后一个分段的 size 才小于 96</p></td></tr></tbody></table>

SeqN 为 5bit，说明最大支持 32 个分段，每个分段满载的 payload 为 12 字节，所以 Upper Transport Layer 下发的消息包括 TransMIC 最大为 32*12=384 字节。

对于同一条消息的不同分段，只有 SegN 和 Segment m 不同。

SeqAuth 是第一个分段的 IV|SeqNum 组合值，通过接收消息的 IV，SeqNum 和 SeqZero 三者组合而成 SeqAuth，对于同一条消息的所有分段具有同样的 SeqAuth 值。

##### ⅲ. 未分段控制消息（Unsegmented Control Message）

未分段控制消息（**1-12 字节**）的每个分段的结构如下：

![](https://i-blog.csdnimg.cn/img_convert/6b5b1a353304d49e2559fc7bb974e1df.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(bits)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>SEG</p></td><td><p>1</p></td><td><p>SEG=0，表示当前消息是未分段消息</p></td></tr><tr><td><p>Opcode</p></td><td><p>7</p></td><td><p>分段控制消息的 Opocde，见 Upper Transport Layer</p></td></tr><tr><td><p>Parameters</p></td><td><p>0-88</p></td><td><p>此分段的消息内容，只有最后一个分段的 size 才小于 64</p></td></tr></tbody></table>

未分段的控制消息最大 size 为 11 字节。

在 Upper Transport Layer 的控制消息中提到当 Opcode=0x00 是为 Lower Transport Layer 预留。

当 Opcode=0x00 时表示当前消息为分段确认消息（大小为 7 字节）。其实也是一种控制消息而已。

其消息格式为：

![](https://i-blog.csdnimg.cn/img_convert/4be1a9e8a74e575f057ee4a8e6f46d4f.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(bits)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>SEG</p></td><td><p>1</p></td><td><p>SEG=0，表示当前消息是未分段消息</p></td></tr><tr><td><p>Opcode</p></td><td><p>7</p></td><td><p>Opcode=0x00</p></td></tr><tr><td><p>OBO</p></td><td><p>1</p></td><td><p>OBO=0，表示是当前节点的行为；</p><p>OBO=1，表示这是 Friend 替 LPN 发的分段确认消息</p></td></tr><tr><td><p>SeqZero</p></td><td><p>13</p></td><td><p>确认分段的 SeqZero</p></td></tr><tr><td><p>RFU</p></td><td><p>2</p></td><td><p>Reserverd for Future Use</p></td></tr><tr><td><p>BlockAck</p></td><td><p>32</p></td><td><p>分段的 Bitmap 位</p></td></tr></tbody></table>

##### ⅳ. 分段控制消息（Segmented Control Message）

分段控制消息（**5-12 字节**）的每个分段的结构如下：

![](https://i-blog.csdnimg.cn/img_convert/61709800d28c8903f513138e66abab26.png)

<table><tbody><tr><td><p><strong>Field</strong></p></td><td><p><strong>Size(bits)</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>SEG</p></td><td><p>1</p></td><td><p>SEG=1，表示当前消息是分段消息</p></td></tr><tr><td><p>Opcode</p></td><td><p>7</p></td><td><p>分段控制消息的 Opocde，见 Upper Transport Layer</p></td></tr><tr><td><p>RFU</p></td><td><p>1</p></td><td><p>RFU</p></td></tr><tr><td><p>SeqZero</p></td><td><p>13</p></td><td><p><strong>SeqAuth</strong> 的最低 13 位有效位</p></td></tr><tr><td><p>SegO</p></td><td><p>5</p></td><td><p>表示当前分段位第几个分段</p></td></tr><tr><td><p>SegN</p></td><td><p>5</p></td><td><p>表示此条消息总共有多少分段</p></td></tr><tr><td><p>Segment m</p></td><td><p>8-64</p></td><td><p>此分段的消息内容，只有最后一个分段的 size 才小于 64</p></td></tr></tbody></table>

##### ⅴ. 分段 / 重组

![](https://i-blog.csdnimg.cn/img_convert/1fdddd64dff7b703bbc0b835f0462e15.png)

分段流程

① Access PDU 大于 12 字节，Control PDU 大于 8 字节进行分段，填充各个字段。

② 若目的地址为组播地址或者虚拟地址，把所有分段广播出去多次，并且每次之间附加上一个小的随机延时。结束。

③ 若目的地址为单播地址，先把所有分段广播出去一次，然后启动一个至少 200+50TTL ms 的定时器（segment transmission timer）。

④ 在 timer 期间，若收到对端的分段确认消息，然后根据分段确认消息里面的 BlockAck 域，将对端未收到的分段，再重新发送一次，然后再重启 segment transmission timer。

⑤ 若收到的 BlockAck 域为 0x00000000，表示对端 busy 或者资源不足，本端则取消分段消息的发送，结束。

⑥ 若收到的 ack 消息表示分段消息接收完毕，则关闭 timer，消息发送成功，结束。

⑦ 若 timer 耗尽，仍未收到分段确认消息，则再次广播所有分段，重启 timer。此操作至少进行 2 次，若多次仍未有确认消息，则消息发送失败，结束。

重组流程

① 收到第一个分段消息，储存此分段消息的 SeqAuth，开启一个至少 10s 的 incomplete timer。

② 若收到的消息的目的地址为单播地址，开启一个至少 150+50TTL ms 的 acknowledgment timer，标记 ack 消息的 BlockAck 字段，表示此分段已收到。

③ 若 acknowledgment timer 耗尽，将此期间标记的 Ack 消息发送至对端。

④ 再次收到分段消息，若此消息的 SeqAuth 小于第一个分段的 SeqAuth，则此消息是过期的，需要被抛弃。标记 ack 消息的 BlockAck 域，若此时 acknowledgment timer 耗尽，则重启 acknowledgment timer，注意此时 BlockAck 域不清零。若此时 incomplete timer 未耗尽，则需要重启 incomplete timer，重新开始计时。（incomplete timer 的意义在于规定两次分段的最大时间间隔）

⑤ 若 incomplete timer 耗尽，则消息接收失败，结束。

⑥ 若已接收完毕所有分段后仍受到分段消息，需要立即响应 ack 消息。（说明对端未收到 ack 消息）

![](https://i-blog.csdnimg.cn/img_convert/57b017f80f65e15fdf3743fc3e9e5b9f.png)

![](https://i-blog.csdnimg.cn/img_convert/c01f0d700ccd95644378b1cc73ba9b4f.png)

### 3. Upper transport layer

上层传输层负责接入层 (Access layer) 消息的加密，和控制消息的交互。

![](https://i-blog.csdnimg.cn/img_convert/d10e51f5974911c824cb891aba597220.png)

##### ⅰ. Access PDU

由 Access 层下发来的消息为 Access PDU，Access PDU 经过 Appkey 或者 DevKey 加密后生成 4/8 字节的 TransMIC(transport message integrity check)。

![](https://i-blog.csdnimg.cn/img_convert/bcf6dc24caaf9bf16feba31dc1ca19ec.png)

Encrypted Access Payload 的最大 size 为 380 个字节。

##### ⅱ. Control PDU

用于节点之间控制消息即非应用消息的传递，用于特殊消息收发通道的建立，主要为 Friend 消息和 Heartbeat 消息。

CTL 消息在这一层不需要加密，所以没有 TransMIC，但 NetMIC（利用 NetKey 二次加密的 MIC）为 8 个字节。

Access PDU 中的 payload 包含 Opcode，而 CTL PDU 中 Opcode 单独提出来。在每个分段的 CTL PDU 都有 Opocde，分段只是对 Param 域进行分段。

![](https://i-blog.csdnimg.cn/img_convert/3b329355a1c77f8ed6f74c4936c10b14.png)

控制消息有以下几种类型：

<table><tbody><tr><td><p><strong>Value</strong></p></td><td><p><strong>Opcode</strong></p></td><td><p><strong>Notes</strong></p></td></tr><tr><td><p>0x00</p></td><td><p>-</p></td><td><p>Reserved for lower transport layer</p></td></tr><tr><td><p>0x01</p></td><td><p>Friend Poll</p></td><td><p>LPN 向 Friend 请求 Friend 存储的消息</p></td></tr><tr><td><p>0x02</p></td><td><p>Friend Update</p></td><td><p>Friend 通知 LPN 安全更新和消息</p></td></tr><tr><td><p>0x03</p></td><td><p>Friend Request</p></td><td><p>LPN 向所有 Friend 请求建立 Friendship</p></td></tr><tr><td><p>0x04</p></td><td><p>Friend Offer</p></td><td><p>Friend 收到 LPN 的请求后发出邀请</p></td></tr><tr><td><p>0x05</p></td><td><p>Friend Clear</p></td><td><p>Friend 与 LPN 建立 Friendship 后，通知 LPN 之前的 Friend 移除 Friendship</p></td></tr><tr><td><p>0x06</p></td><td><p>Friend Clear Confirm</p></td><td><p>Old Friend 收到 Clear 消息响应给 New Friend</p></td></tr><tr><td><p>0x07</p></td><td><p>Friend Subscription List Add</p></td><td><p>通知 Friend 添加某个 LPN 的订阅地址</p></td></tr><tr><td><p>0x08</p></td><td><p>Friend Subscription List Remove</p></td><td><p>通知 Friend 移除某个 LPN 的订阅地址</p></td></tr><tr><td><p>0x09</p></td><td><p>Friend Subscription List Confirm</p></td><td><p>Friend 响应订阅地址操作已完成</p></td></tr><tr><td><p>0x0A</p></td><td><p>Heartbeat</p></td><td><p>节点发送心跳消息</p></td></tr><tr><td><p>0x0B-0x7F</p></td><td><p>RFU</p></td><td><p>Reserved for Future Use</p></td></tr></tbody></table>

### 4. Access layer

![](https://i-blog.csdnimg.cn/img_convert/9f8c875394611a4514e9f65039faebdf.png)

Access layer 将 Model 下发的消息转化成 Mesh 协议栈规定的格式，并将下层的数据上传至指定的 Model。

### 5. Foundation model layer

![](https://i-blog.csdnimg.cn/img_convert/4b0fdfe3740ccb492c7e63cf10a3a19a.png)

### 6. Model layer

![](https://i-blog.csdnimg.cn/img_convert/90dca94aa2c80e38f988befe98ca08ea.png)

编写 Mesh 的 Model 需要先知道节点 (node)，元素 (element)，模型 ([model](https://so.csdn.net/so/search?q=model&spm=1001.2101.3001.7020 "model")) 的概念

**节点 (Node)**

简单来讲，一个节点就是一个 mesh 芯片。要使一个节点成为 Mesh 网络里面的点，需要配网者 (provisioner) 配网，配置客户端 (configuration client) 配置后才能正常使用。

**元素 (Element)**

一个元素就是执行一组功能的单位实体，一个节点里面至少有一个元素，称做主元素 (primary element)，其余的是次要元素 (secondary element)。

每个元素都会被配网者分配一个单播地址 (unicast address) 作为唯一标识。

**模型 (Model)**

一个模型定义了特定功能的实现及交互流程。模型一般是配套的，设计一组 Model，既需要设计 Client 又需要设计 Server。一端发送指定类型消息，对端响应另一指定消息，这些都属于模型的设计范畴。