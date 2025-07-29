---
PDF: "[[蓝牙/Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf|Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library)]]"
tags: 
开始日期: 2025-07-28
---

[[蓝牙/Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf|Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library)]]


> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=20&selection=4,0,18,88&color=翻译|p.20]])
> The application layer is use-case dependent and refers to the implementation on top of the Generic Access Profile and Generic Attribute Profile — itʼs how your application handles data received from and sent to other devices and the logic behind it. This portion is the code that you would write for your specific BLE application and is generally not part of the BLE stack for the platform which you develop. This part will not be covered in the book, since it depends on the specifics of your application and use case.
>
> 应用层是依赖于具体使用场景的，它指的是在通用访问配置文件 (Generic Access Profile, GAP) 和通用属性配置文件 (Generic Attribute Profile, GATT) 之上的实现。它决定了你的应用程序如何处理从其他设备接收和发送的数据，以及其背后的逻辑。

PHY Layer：

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=21&selection=49,33,80,73&color=翻译|p.21]])
> This allows the devices scanning for advertisers to find them and read their advertisement data. The scanner can then initiate a connection if the advertiser allows it. It can also request whatʼs called a scan request, and if the advertiser supports this scan request functionality, it will respond with a scan response. Scan requests and scan responses allow the advertiser to send additional advertisement data to devices that are interested in receiving this data.
>  
>  **这使得扫描设备能够找到广播设备并读取它们的广播数据。如果广播设备允许，扫描设备随后可以发起连接。扫描设备还可以请求所谓的“扫描请求（scan request）”，如果广播设备支持此扫描请求功能，广播设备将回应“扫描响应（scan response）”。扫描请求和扫描响应允许广播设备向有兴趣接收这些数据的设备发送额外的广播数据。**
>  
- **“这使得扫描设备能够找到广播设备并读取它们的广播数据。”**
    
    - **广播设备 (Advertiser)：** 指的是那些主动发送广播数据包的BLE设备。它们通常处于低功耗模式，周期性地向周围环境发送数据，目的是让其他设备发现自己。例如，一个Beacon设备、一个智能手环在等待连接时就可能扮演广播设备的身份。
        
    - **扫描设备 (Scanner)：** 指的是那些主动监听和接收广播数据包的BLE设备。它们会“扫描”周围的空中信号，以发现广播设备并解析它们发送的数据。例如，你的智能手机在打开蓝牙时就扮演扫描设备的角色。
        
    - **广播数据 (Advertisement Data)：** 这是广播设备在广播包中携带的信息。这些数据通常包含设备名称、服务UUID（Universally Unique Identifier，通用唯一标识符）以及一些厂商特定的数据。这些数据量通常有限，因为广播包大小有严格限制（在BLE 4.x中为31字节）。
        
    
    **核心思想：** 广播和扫描是BLE设备相互发现的机制。广播设备“呼喊”，扫描设备“聆听”。
    
- **“如果广播设备允许，扫描设备随后可以发起连接。”**
    
    - **发起连接 (Initiate a Connection)：** 如果扫描设备发现了它感兴趣的广播设备，并且该广播设备被配置为“可连接的”（Connectable Advertiser），扫描设备就可以向其发送连接请求，从而建立一个点对点（P2P）的BLE连接。
        
    - **“如果广播设备允许”：** 这很重要。并非所有的广播设备都允许连接。例如，Beacon设备通常只广播数据，不可连接。而像蓝牙耳机、智能手环这类设备，在被发现后，通常都允许建立连接以进行数据同步或控制。
        
    
    **核心思想：** 广播是连接的前奏。只有可连接的广播设备才能被扫描设备进一步连接。
    
- **“它还可以请求所谓的‘扫描请求（scan request）’，如果广播设备支持此扫描请求功能，它将回应‘扫描响应（scan response）’。”**
    
    - **扫描请求 (Scan Request)：** 当扫描设备发现一个广播设备并对它感兴趣时，它不仅仅是读取广播数据。如果它需要更多信息，它可以向该广播设备发送一个特殊的“扫描请求”包。
        
    - **扫描响应 (Scan Response)：** 这是广播设备对扫描请求的回复。它包含了额外的广播数据，用于补充初始的广播包中受限的信息。
        
    
    **核心思想：** 扫描请求/响应机制是**扩展广播数据量**的一种方式。
    
- **“扫描请求和扫描响应允许广播设备向有兴趣接收这些数据的设备发送额外的广播数据。”**
    
    - **扩展数据：** 正如前面提到的，初始的广播数据包大小有限。通过扫描请求和扫描响应，广播设备可以发送另一组大小有限（同样在BLE 4.x中为31字节）的数据。这意味着一个广播设备实际上可以通过两个阶段（初始广播包和扫描响应包）向外界传递总计达62字节的广播信息。
        
    - **按需提供：** 这种机制是“按需”的。只有当扫描设备明确表示出兴趣（发送了扫描请求）时，广播设备才会发送扫描响应。这有助于节省广播设备的功耗，因为它不必总是发送所有数据。
        
    
    **核心思想：** 这是一个高效的机制，用于在不建立完整连接的情况下，为感兴趣的扫描设备提供更丰富的信息。

### 2.BLE Devices: Peripherals and Centrals

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=27&selection=19,0,33,2&color=关键点|p.27]])
> A peripheral device is a device that announces its presence by sending out advertising packets and accepts a connection from another BLE device (the BLE central — which will be explained shortly).

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=28&selection=19,0,27,6&color=关键点|p.28]])
> A Central is a device that discovers and listens to other BLE devices that are advertising. It is also capable of establishing a connection to BLE peripherals (usually multiple at the same time).


### 3.Advertising and Scaning

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=35&selection=5,0,17,82&color=关键点|p.35]])
> An advertising event is made up of multiple advertising packets being sent on all, or a subset of, the three Primary Advertising Channels (37, 38, and 39). There are seven types of advertising events (think of these as the different types of advertising packets):
> 7种advertising事件

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=37&selection=6,0,7,32&color=其他|p.37]])
> Figure 11: Advertising data packet format
   图来自核心规范1353页

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=38&selection=54,0,58,2&color=关键点|p.38]])
> Appearance: this defines the external appearance of the device according to the Bluetooth Assigned Numbers. 


### 4.Connection

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=40&selection=38,0,52,7&color=关键点|p.40]])
> After this occurs, the connection is considered created, but not yet established. A connection is considered established once the device receives a packet from its peer device.
>   
>   在 BLE 规范中，**“连接已建立 (connection is established)”** 意味着连接双方都已成功从对方接收到**第一个数据包 (first packet from its peer device)**。
>   
>   这个第一个数据包通常是链路层 (Link Layer) 的数据包，用于确认连接参数或进行链路层控制。它标志着双方都已经确认了连接参数，并且链路层的通信链路已经完全可用。


Channel Hopping：

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=43&selection=47,26,58,11&color=关键点|p.43]])
> The used channels are defined by the channel map, which is included in the connection request packet sent by the central to the peripheral to initiate a connection.
> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=43&selection=67,2,69,68&color=关键点|p.43]])
> The hop increment — like the channel map — is also included in the connection request packet.


> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=44&selection=27,0,37,76&color=翻译|p.44]])
> A white list is a list of addresses and address types of specific devices. It is used for determining which peer devices a particular device is interested in. An entry for an anonymous device address type allows matching all advertisements sent with no address.

1. **设备过滤 (Device Filtering)：**
    
    - BLE 设备不是对所有遇到的广播、扫描请求或连接请求都做出响应。设备过滤允许设备根据预设的规则（通常是白名单）来决定是响应还是忽略这些请求/数据包。
        
    - **优点：** 减少了不必要的处理，节省了功耗，提高了安全性（只与信任的设备交互），并降低了主机（通常是应用处理器）的负担。
        
2. **白名单 (White List)：**
    
    - 一个由设备地址和地址类型组成的列表。只有列在此列表中的设备才能被特定的 BLE 流程允许进行交互。
        
    - **匿名设备地址类型：** 这是一个特殊的条目，允许匹配那些为了隐私或特定应用场景而**不发送公共或随机地址**的广播设备。
        
3. **处理层级：**
    - **控制器 (Controller)：** 这是蓝牙协议栈的下层，通常由蓝牙芯片硬件及其固件组成。它负责物理层和链路层的操作。
        
    - **主机 (Host)：** 这是蓝牙协议栈的上层，通常由操作系统（如 Android、iOS、Linux、Windows）的蓝牙协议栈和应用程序组成。
        
    - **关键点：** 设备过滤在**控制器（链路层）**完成。这意味着在数据包到达主机并进行复杂处理之前，控制器就已经根据白名单进行了初步筛选。这大大**节省了时间和开销**，因为主机不需要处理所有进来的数据包。然而，白名单的**配置是由主机负责**的。主机告诉控制器“哪些设备是白名单里的”。
        

4. **广播状态过滤策略 (Peripheral Side 外围设备端)：**
    
    - 针对外围设备在广播时，如何处理来自中央设备的**扫描请求**和**连接请求**。
        
    - **灵活配置：** 可以选择只响应白名单中的设备，或者响应所有设备，甚至可以区分对待扫描请求和连接请求（例如，允许所有设备扫描，但只允许白名单中的设备连接）。这对于 Beacon 这类需要广泛被发现但只允许特定设备连接的应用场景非常有用。
        
5. **扫描状态过滤策略 (Central Side 中央设备端)：**
    
    - 针对中央设备在扫描时，如何处理收到的**广播数据包**。
        
    - **选择性发现：** 可以选择发现所有广播设备，或者只发现白名单中的广播设备。这有助于中央设备专注于它感兴趣的设备，减少不必要的处理和功耗。
        
6. **发起状态过滤策略 (Central Side 中央设备端)：**
    
    - 针对中央设备在尝试**建立连接**时，如何处理广播数据包。
        
    - **精确连接：** 可以选择只尝试连接白名单中的设备，或者更严格地，只连接主机明确指定的单个设备。
        

这意味着，当你作为**中央设备**，并且你**启用了发起状态的过滤策略**时，你**无法**选择连接到一个**不在白名单中的可连接广播设备**。如果你的策略是过滤的，你只能连接白名单内的设备，或者主机明确指定的单个设备。但你可以选择**不启用发起状态的过滤策略**（例如，如果它依赖于更通用的扫描状态过滤），从而允许连接所有设备。

**总结来说：**
- **白名单是一个可选的功能，旨在提供更精细的控制和优化。**
    
- **你可以选择不使用白名单，让设备与所有符合条件的蓝牙设备进行交互。**
    
- **但是，如果你决定使用白名单，特别是在连接发起阶段，它会限制你的连接目标。** 也就是说，如果使用了白名单过滤策略，那么连接就必须针对白名单内的设备，而不是白名单外的设备。但这不意味着你**必须**使用白名单。

### 5.Services and characteristics

#### ATT:

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=46&selection=35,0,37,29&color=关键点|p.46]])
> ATT defines how a server exposes its data to a client and how this data is structured. There are two roles within the ATT:
	1.Server：This is the device that exposes the data it controls or contains, and possibly some other aspects of server behavior that other devices may be able to control.
>
	2.Client：This is the device that interfaces with the server with the purpose of reading the serverʼs exposed data and/or controlling the serverʼs behavior.

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=46&selection=87,0,90,1&color=关键点|p.46]])
> The data that the server exposes is structured as **attributes**.


#### GATT:

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=48&selection=31,0,35,54&color=关键点|p.48]])
> The GATT defines the format of services and their characteristics, and the procedures that are used to interface with these attributes such as service discovery, characteristic reads, characteristic writes, notifications, and indications.

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=48&selection=37,0,57,47&color=关键点|p.48]])
> GATT takes on the **same roles** as the Attribute Protocol (ATT). The roles are not set per device — rather they are determined per transaction (such as request ⟷ response, indication ⟷ confirmation, notification). So, in this sense, a device can act as a server serving up data for clients, and at the same time act as a client reading data served up by other servers (all during the same connection).

 * **GATT 层与 ATT 层的关系和作用**

要理解 Attribute Operation 的作用层级，首先需要理解 **ATT** 和 **GATT** 之间的关系。

- **ATT (Attribute Protocol - 属性协议)**
    
    - **作用：** ATT 是 **GATT 的基础**，它定义了如何在 BLE 连接的两端（通常是 GATT 客户端和 GATT 服务器）之间传输 **属性 (Attributes)**。
        
    - **核心：** ATT 专注于属性的 **读、写、查找** 等基本操作。每个属性都有一个唯一的 **句柄 (Handle)** 和一个 **UUID**。ATT 协议规定了如何使用这些句柄和 UUID 来访问属性的值。
        
    - **低级协议：** ATT 是一种非常底层的协议，它不关心属性的语义（比如这个属性代表温度还是电量），只关心如何通过句柄和 UUID 来操作它们。它提供了诸如 "Read By Type Request"、"Write Request"、"Find Information Request" 等具体的协议数据单元 (PDU)。
        
    - **数据格式：** ATT 协议为了在低功耗设备上高效运行，其数据包非常紧凑，使用尽可能少的字节。
        
- **GATT (Generic Attribute Profile - 通用属性配置文件)**
    
    - **作用：** GATT 是建立在 ATT 之上的一个 **高级框架**。它定义了如何使用 ATT 协议来发现、读取和写入有组织的属性数据。
        
    - **核心：** GATT 引入了 **服务 (Service)** 和 **特征 (Characteristic)** 的概念，将原始的 ATT 属性进行了语义上的分组和抽象。它定义了这些服务和特征的结构、属性（Properties）和描述符（Descriptors）。
        
    - **应用层接口：** GATT 更面向应用程序开发者，提供了一种统一的方式来理解和交互 BLE 设备的功能。当你编程时，你通常是与 GATT 层的概念（服务、特征）打交道，而不是直接操作底层的 ATT 句柄。
        
    - **约定：** GATT 定义了如何将相关的 ATT 属性组合成有意义的服务和特征，以及这些服务和特征应该如何工作，以满足特定的应用场景（例如，心率监测、智能家居控制）。
        

---
 * **Attribute Operation 的作用层级**

**Attribute Operation（属性操作）**，如读取属性值、写入属性值、发现属性等，这些具体的 **数据传输和处理** 都是在 **ATT 层** 完成的。

- **客户端发送请求：** 当 GATT 客户端想要读取一个特征值时，它会向 GATT 服务器发送一个 **GATT Read Request**。
    
- **GATT 层转换：** GATT 层会将这个高级的 "Read Request" **转换** 为底层的 **ATT Read Request PDU**。
    
- **ATT 层执行：** ATT 层接收到这个 PDU 后，会根据 PDU 中的句柄和 UUID 去访问 GATT 数据库中对应的属性，并执行读取操作。
    
- **数据返回：** 读取到的数据会通过 ATT 层封装成 **ATT Read Response PDU** 返回。
    
- **GATT 层解析：** GATT 客户端的 GATT 层会接收并解析这个 ATT Response PDU，将原始的属性数据呈现给应用程序。
    

**举个例子：**

假设你有一个蓝牙体重秤 (GATT 服务器)，你的手机 (GATT 客户端) 想要读取你的体重。

1. **GATT 客户端应用程序：** 你在手机 App 上点击“同步体重”。App（GATT 客户端）知道有一个“体重服务”，服务中有一个“体重测量特征”。
    
2. **GATT 层：** App 会向 GATT 层发出一个请求：“读取体重测量特征的值”。
    
3. **ATT 层：** GATT 层会根据“体重测量特征”在 GATT 数据库中对应的 **ATT 句柄**，构建一个 **ATT Read Request PDU**，然后通过物理层发送给体重秤。
    
4. **体重秤（ATT 服务器）：** 体重秤的 ATT 层收到这个 Read Request PDU，根据句柄找到对应的属性，读取存储的体重数据。
    
5. **体重秤（ATT 服务器）响应：** 体重秤的 ATT 层将体重数据封装成 **ATT Read Response PDU**，并通过物理层发送回手机。
    
6. **手机（ATT 客户端）：** 手机的 ATT 层收到 Response PDU，将原始数据传递给 GATT 层。
    
7. **手机（GATT 客户端）：** GATT 层解析数据，将其转换为 App 能理解的“体重值”，最终显示在你的屏幕上。

#### Services:

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=49&selection=4,0,8,76&color=关键点|p.49]])
> A service is a grouping of one or more attributes, some of which are characteristics. 
> ...
> A service also contains other attributes (non-characteristics) that help structure the data within a service (such as service declarations, characteristic declarations, and others).

> 服务是attribute属性的集合，属性里有一些是特征。

- 特征是服务中最重要的部分，它们代表了设备实际提供的数据点或功能。
    
- **示例：** 文中提到的“电池服务”就是一个很好的例子。一个蓝牙设备如果提供电池信息，它就会暴露一个“电池服务”。这个服务里面，最关键的数据就是“电池电量”——它被定义为一个“特征”。用户或其他设备可以通过读取这个特征来获取当前的电池电量。
---
* 除了特征，服务还包含一些“非特征”的属性。这些属性的主要作用是帮助客户端（请求数据设备，如智能手表）理解服务的结构。
    
- **示例：**
    
    - **服务声明 (Service Declarations):** 告诉客户端这里有一个服务，以及这个服务的唯一标识符（UUID）。
        
    - **特征声明 (Characteristic Declarations):** 告诉客户端这个服务里有哪些特征，每个特征的UUID是什么，以及它们支持哪些操作（读、写、通知等）。
        
- **作用：** 这些声明就像一个目录或索引，让客户端知道如何找到并与服务中的数据进行交互。

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=51&selection=0,28,0,81&color=关键点|p.51]])
> the different attributes that a service is made up of
* One or more include services 
* One or more characteristics 
   * Characteristic properties 
   * A characteristic value 
   * Zero or more characteristic descriptors

#### Characteristics:

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=51&selection=32,0,38,37&color=关键点|p.51]])
> A characteristic is always part of a service and it represents a piece of information/data that a server wants to expose to a client.

**“特征 (Characteristic)”** 两个重要组成部分：**属性 (Properties)** 和 **描述符 (Descriptors)**。

1.  **属性 (Properties)**
    
    - **定义：** 属性是由一系列的位（bits）表示的，它们定义了 **特征值（Characteristic Value）可以如何被使用**。
        
    - **作用：** 它们规定了客户端（比如手机、电脑）可以对这个特征值执行哪些操作。
        
    - **示例：**
        
        - `read`: 客户端可以读取这个特征的值。
            
        - `write`: 客户端可以写入新的值到这个特征。
            
        - `write without response`: 客户端可以写入值，但服务器不会发送响应（更快速，但不保证交付）。
            
        - `notify`: 当特征值在服务器端发生变化时，服务器可以向订阅的客户端发送“通知”。通知是不需要确认的。
            
        - `indicate`: 当特征值在服务器端发生变化时，服务器可以向订阅的客户端发送“指示”。指示是需要客户端发送确认的，因此比通知更可靠。
            
2. **描述符 (Descriptors)**
    
    - **定义：** 描述符是用于包含 **与特征值相关的附加信息** 的属性。
        
    - **作用：** 它们提供了对特征值的更详细的解释、配置或元数据，帮助客户端更好地理解和使用特征值。
        
    - **示例：**
        
        - `extended properties`: 扩展的属性，提供了更多关于特征值的操作信息。
            
        - `user description`: 用户友好的文本描述，解释这个特征值代表什么（比如“当前温度”、“设备状态”）。
            
        - `fields used for subscribing to notifications and indications`: 这是最重要的描述符之一，通常是 **客户端特征配置描述符 (Client Characteristic Configuration Descriptor, CCCD)**。客户端通过写入这个描述符来订阅（启用或禁用）某个特征的通知或指示。
            
        - `a field that defines the presentation of the value such as the format and the unit of the value`: 比如 **特征表示格式描述符 (Characteristic Presentation Format Descriptor)**，它定义了特征值的格式（例如，是整数、浮点数、字符串），以及单位（例如，摄氏度、百分比、米）。

举例：
```xml
<configuration>
    <service uuid="1809"> <description>Temperature Service</description>
        <characteristic uuid="2a1c"> <description>Temperature Value</description>
            <properties read="true" notify="true"/>
            <value type="user" variable_length="true" length="2"/> 
            <descriptor uuid="2904">
                <properties read="true" const="true"/>
                <value type="hex">0400AD270100</value>
            </descriptor>

            <descriptor uuid="2902">
                <properties read="true" write="true"/>
                <value type="hex"></value> 
            </descriptor>

        </characteristic>
    </service>
</configuration>
```

1. **`<service uuid="1809">`**: 定义了一个蓝牙 SIG 标准的 **温度服务**。
    
2. **`<characteristic uuid="2a1c">`**: 定义了一个蓝牙 SIG 标准的 **温度测量特征**。
    
    - **`<properties read="true" notify="true"/>`**: 允许客户端读取温度值，并且可以订阅温度变化的通知。
        
    - **`<value type="user" variable_length="true" length="2"/>`**: 表示温度值由应用程序动态管理，并且以 2 个字节（16 位）表示。这里我们假设它存储的是 IEEE-11073 SFLOAT 格式（一种 16 位浮点数格式）。
        
3. **`<descriptor uuid="2904">`**:
    
    - 这是 **特征表示格式描述符** 的定义。
        
    - **`<properties read="true" const="true"/>`**: 表示这个描述符的值是可读且固定的。
        
    - **`<value type="hex">0400AD270100</value>`**: 这是这个描述符最重要的部分，它是一个十六进制的字节序列，包含了格式信息：
        
        - **`04`**: **Format (格式)**。根据蓝牙 SIG 的 GATT 规范，`0x04` 代表 **SFLOAT (Short Float)**，即 IEEE-11073 16 位浮点数格式。
            
        - **`00`**: **Exponent (指数)**。这里是 `0x00`，表示指数为 0，没有对特征值进行缩放。
            
        - **`AD27`**: **Unit (单位)**。这是 `0x27AD` 的小端序表示（字节顺序颠倒）。`0x27AD` 是蓝牙 SIG 为 **摄氏度 (Celsius)** 定义的标准单位 UUID。
            
        - **`01`**: **Name Space (命名空间)**。`0x01` 表示蓝牙 SIG 命名空间，这是最常见的。
            
        - **`0000`**: **Description (描述)**。通常为 `0x0000`，表示没有额外的描述符来提供更详细的文本描述。
            
4. **`<descriptor uuid="2902">`**:
    
    - 这是 **客户端特征配置描述符 (Client Characteristic Configuration Descriptor, CCCD)**。
        
    - 因为它存在，客户端就可以通过写入这个描述符来订阅或取消订阅温度变化的通知（由 `notify="true"` 属性启用）。
        

通过这个 `<descriptor uuid="2904">`，一个连接到该设备的客户端就知道：我从这个特征读到的 16 位数据，它是一个没有缩放的 IEEE-11073 SFLOAT 浮点数，表示的是摄氏温度。这极大地提高了数据的互操作性。

---

* **GATT 数据库：存在于 ATT 层，但由 GATT 组织**

**GATT 数据库是存储在 ATT 层之上的数据结构，但它的内容和组织方式是由 GATT 定义和管理的。**

让我们来具体解释一下：

1. **ATT (Attribute Protocol)** 是一个 **协议**。它定义了如何传输一系列的 **属性 (Attributes)**。每个属性都有一个句柄、一个类型 (UUID) 和一个值。ATT 协议本身只关心这些属性的读写和发现机制，它不关心这些属性在语义上代表什么，也不关心它们之间有什么关系。你可以把 ATT 看作是一个底层的、通用的“键值对”存储和传输机制。
    
2. **GATT (Generic Attribute Profile)** 是一个建立在 ATT 之上的 **框架或配置文件**。它利用 ATT 提供的基本属性操作能力，将这些无序的属性按照特定的规则（即服务和特征）组织起来，并赋予它们语义。GATT 定义了服务、特征、描述符这些高级概念，以及它们如何映射到 ATT 的属性上。
    
3. **GATT 数据库 (GATT Database)** 是一个 **逻辑概念**，它指代了设备（通常是 GATT 服务器）上所有可用的服务、特征和描述符的集合。这个“数据库”实际上就是一系列按 GATT 规则组织的 **ATT 属性的集合**。
    
**所以：**

- 底层的 **ATT 层** 提供了存储和访问 **单个属性** 的机制。
    
- **GATT 层** 则在这些 ATT 属性之上构建了一个 **结构化的数据库**，使其符合服务的定义。
    
可以这样理解：

想象你有一个巨大的仓库（ATT 层），里面堆满了各种标有编号的箱子（ATT 属性）。ATT 协议定义了你怎么搬运、查找、打开这些箱子。但是这些箱子堆放得很乱，你不知道哪个箱子是干什么的。

GATT 层就是这个仓库的“管理系统”或“清单”。它规定了：

- 某些箱子应该组成一个“区”（服务）。
    
- “区”里最重要的箱子是“物品”（特征），它里面放着你真正需要的数据。
    
- 还有一些小箱子（描述符）用来解释“物品”的细节，比如物品的尺寸、颜色等。
    

所以，当你说“GATT 数据库”时，你指的是一个按照 GATT 规范组织起来的属性集合，这些属性最终通过 ATT 协议进行操作。

---

* **XML 文件是定义了 GATT 数据库吗？**

**是的，你刚刚提供的 XML 文件就是用来定义 GATT 数据库的内容和结构的。**

这个 XML 文件描述了你的蓝牙设备（作为 GATT 服务器）将提供哪些服务，每个服务包含哪些特征，这些特征的属性是什么，以及它们的初始值或管理方式。

- 文件中的 `<service>` 标签定义了 GATT 数据库中的一个服务。
    
- `<characteristic>` 标签定义了服务中的一个特征。
    
- `<properties>` 和 `<value>` 等子标签则定义了这些特征的具体属性和值。
    

当你的 BLE 模块或芯片加载并解析这个 XML 文件后，它会根据文件中的定义来构建其内部的 GATT 数据库。其他蓝牙设备（GATT 客户端）连接到你的设备后，就可以通过 **ATT 协议** 来查询和操作这个由 GATT 定义的数据库中的服务和特征了。

所以，这个 XML 文件是 GATT 数据库的**声明或配置**，它指导了设备如何构建和暴露其蓝牙服务和特征。

#### Profile:

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=52&selection=77,0,85,91&color=关键点|p.52]])
> Profiles are much broader in definition than services. They are concerned with defining the behavior of both the client and server when it comes to services, characteristics and even connections and security requirements. Services and their specifications, on the other hand, deal with the implementation of these services and characteristics on the server side only.


**Profile 本身是一个文档！**

- **Profile** 通常是一个由蓝牙 SIG 或特定厂商发布的**规范文档**。
    
- 这个文档会详细描述一个特定用例（例如心率监测、智能手表、健康医疗设备）所需要的所有服务、特征，以及客户端和服务器之间应该如何进行数据交互、连接管理和安全处理。

-  **XML 文件**定义的是 BLE 设备作为 **GATT 服务器**时，它有哪些货品（服务）以及这些货品（特征）的具体属性和初始值。
    
- **Profile** 则是一个更高级别的“使用手册”或“业务规范”，它指导客户端和服务器如何协作来完成一个特定的应用功能。


#### Attribute Operations

> ([[Intro to Bluetooth Low Energy (Mohammad Afaneh) (Z-Library).pdf#page=56&selection=59,0,65,49&color=关键点|p.56]])
> Queued Writes (atomic operation behavior): these are classified as requests and require a Response from the server. They are used whenever a large value needs to be written and does not fit within a single message.

1. Prepare Write Requests (准备写入请求)

- **目的：** 这个阶段的目的是将大属性值**分块传输**到服务器，并临时存储起来，而不是立即写入最终的属性。
    
- **操作方式：**
    
    - **分段传输：** 客户端会将要写入的完整大值分解成多个小的数据段。
        
    - **包含偏移量 (Offset)：** 每个 `Prepare Write Request` 都包含一个 **偏移量**。这个偏移量告诉服务器，当前发送的这个数据段应该被写入到属性值的哪个位置（从开始处计算）。
        
    - **“准备好的值” (Prepared Values)：** 客户端发送的这些数据段被称为“准备好的值”。
        
    - **服务器端缓冲：** 服务器在接收到 `Prepare Write Request` 后，不会立即将数据写入目标属性，而是将这些“准备好的值”存储在一个**内部缓冲区**中。
        
    - **需要响应：** 每一个 `Prepare Write Request` 都需要服务器返回一个 **`Prepare Write Response`**。这确保了客户端知道每个数据段都已成功接收并缓冲。
        
- **原子性保障：** 这种缓冲机制是原子性行为的关键。在所有 `Prepare Write Request` 都完成之前，目标属性的旧值仍然保持不变。即使中间某个 `Prepare Write Request` 失败，也不会导致属性值被部分更新，从而避免了其他客户端读取到不完整或错误数据的情况。
    

2. Execute Write Request (执行写入请求)

- **目的：** 在所有数据段都通过 `Prepare Write Request` 成功缓冲到服务器后，客户端会发送一个 `Execute Write Request` 来指示服务器执行或取消整个写入操作。
    
- **操作方式：**
    
    - **触发操作：** 客户端发送这个请求给服务器。
        
    - **执行或取消：** 这个请求中包含一个指令，告诉服务器是 **执行 (Execute)** 之前所有缓冲好的数据，将它们一次性写入到目标属性中；还是 **取消 (Cancel)** 整个操作，清空缓冲区，保持目标属性的旧值不变。
        
    - **原子性完成：** 如果选择“执行”，服务器会把缓冲区中的所有数据原子性地写入到目标属性。如果选择“取消”，则什么都不写入。
        
    - **需要响应：** `Execute Write Request` 也需要服务器返回一个 **`Execute Write Response`**。
        
- **结果确认：** 一旦客户端收到 `Execute Write Response`，它就能确定两种情况：
    
    - 如果服务器响应成功执行，那么客户端可以确信目标属性现在持有了它刚刚发送的**完整且正确**的值。
        
    - 如果服务器响应取消或执行失败，客户端则知道属性值没有被改变。

