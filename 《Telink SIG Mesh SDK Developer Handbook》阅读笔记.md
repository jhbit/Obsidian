---
PDF: "[[蓝牙/Telink SIG Mesh SDK Developer Handbook.pdf|Telink SIG Mesh SDK Developer Handbook]]"
tags: 
开始日期: 2025-07-26
---

[[蓝牙/Telink SIG Mesh SDK Developer Handbook.pdf|Telink SIG Mesh SDK Developer Handbook]]

> ([[Telink SIG Mesh SDK Developer Handbook.pdf#page=29&selection=8,2,25,10&color=关键点|p.29]])
> boot：提供芯⽚的 bootloader，即 MCU 上电启动或 deepsleep 唤醒后的汇编处理过程，为后⾯ C 语⾔ 程序的运⾏搭建好环境。
> 
   这里boot文件夹下的.s文件，是**汇编语言源代码文件**。一般用来**直接访问和操作 CPU 的寄存器、内存地址**，这是进行系统最早期启动配置所必需的。
   所有底层初始化后，汇编代码的最终任务是调用或跳转到 C 语言的 `main` 函数（或更准确地说，是 C 运行时库的初始化函数，它最终会调用 `main` 函数）。这个跳转标志着从**纯硬件操作到高级语言编程的过渡**。


> ([[Telink SIG Mesh SDK Developer Handbook.pdf#page=32&selection=205,2,211,27&color=翻译|p.32]])
> “8258_gw_node”，编译选项：具有 gateway adv provisioner + mesh node 这两个⻆⾊的功能，可以⾃ ⼰建⽴⽹络，把别的未组⽹节点添加进来。也可以被别⼈组⽹
   ***这个是目前觉得需要重点研究的部分***


> ([[Telink SIG Mesh SDK Developer Handbook.pdf#page=62&selection=8,6,8,17&color=关键点|p.62]])
> Model layer
> Node、Model和Provisioner的关系：
	1.Provisioner是组网者。它会把具有Mesh功能的设备并入网络，那个设备就成了Mesh的一个Node。
	2.Node设备所具备的具体功能，是在Model layer被定义的。Model都定义了自己的**操作码Opcode**和**状态Status**。操作码用来发送命令和请求，状态用来表示模型当前状态。**一个Node可以存在多个Model**。
	例如，`Generic OnOff Model` 定义了 `ON/OFF` (设置命令)、`GET` (获取命令) 和 `STATUS` (状态回复) 等操作码。
>	
	Provisioner和Node的交互：
	1.**获取组合数据 (Get Composition Data)：** Provisioner 会向即将加入网络的设备发送 `Get Composition Data` 命令。
>    
	2.**获取模型信息：** 收到 `Composition Data` 后，Provisioner 就能知道这个设备（将来成为节点）支持哪些**模型 ID**。通过这些模型 ID，Provisioner 就明确了这个节点具体能提供或需要哪些功能（比如它是个灯泡、是个开关，还是个传感器）。
>	
	3.**精确控制：** 只有当 Provisioner 知道一个节点支持了某个特定的模型后，它才会向该节点发送该模型定义的操作码（命令）。例如，如果 Provisioner 发现一个节点支持 `Generic OnOff Server Model`，它才会向这个节点发送 `OnOff Set` 命令来控制开关。如果节点不支持这个模型，发送对应的命令将是无效的。
