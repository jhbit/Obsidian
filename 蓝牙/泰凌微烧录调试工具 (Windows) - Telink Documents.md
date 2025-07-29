---
url: https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/bdt_wins_cn/
title: 烧录调试工具 (Windows) - Telink Documents
date: 2025-07-26 17:03:26
tag: 
banner: "https://images.unsplash.com/photo-1745964893863-2bf9fd0b4571?crop=entropy&cs=srgb&fm=jpg&ixid=M3w0Njc1ODd8MHwxfHJhbmRvbXx8fHx8fHwxfHwxNzUzNTIwNTg4fA&ixlib=rb-4.1.0&q=85&fit=crop&w=690&max-h=540"
banner_icon: 🔖
---
* * *

## 简介

“Telink Burning and Debugging Tool (BDT)” 适用于基于 Telink SoC（包括 B85M 系列以及 B91、B92、TL721X、TL321X、TC321X、TL751X）的应用开发。

这份文档介绍了如何使用 “Telink Burning and Debugging Tool (BDT)”。

### 功能概述

在 SDK 开发过程中，通过使用 “Telink Burning and Debugging Tool（BDT）”，可以通过 USB 模式或者 “Burning EVK”（EVK）将固件直接下载到目标板（例如开发板）。

它主要的功能包括：擦除 flash 扇区，下载固件，通信失败时激活 MCU，访问包括 Flash/Core/Analog/OTP 在内的内存空间，读 / 写全局变量和查看 USB 日志。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/maininterface.png)

## 操作指南

### 下载固件

#### 连接硬件

在使用 “Telink Burning and Debugging Tool (BDT)” 之前，需要连接目标板和 PC。

有两种方法连接目标板和 PC，如下所示。

**方法 1：** 通过 USB 直接连接目标板和 PC。

这种方法只适用于具有 USB 接口的目标板和支持 USB 功能的 MCU，例如 dongle 板。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/connecttargetboardwithpcdirectly.png)

**方法 2：** 通过 Telink “Burning EVK” TLSR8266ET56 连接目标板和 PC。

（1）通过 USB 线将 “Burning EVK” 与 PC 连接。观察 “Burning EVK” 的指示灯，指示灯闪烁一次，表明 “Burning EVK” 与 PC 连接成功。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ConnectBurningEVKwithPC.png)

（2）连接 “Burning EVK” 和目标板。

有两种方法连接 “Burning EVK” 和目标板。

a. 通过 USB 接口直接连接目标板和 “Burning EVK”，如下图所示。这种连接方式只适用于有 USB 接口的目标板和支持 USB 功能的 MCU，如 dongle 板。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ConnecttargetboardwithBurningEVKviaUSB.png)

b. 通过 Swire（单线）接口连接 “Burning EVK” 和目标板，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ConnecttargetboardwithBurningEVKviaSwire.png)

通过 “USB” 方式或 “Burning EVK” 方式将目标板连接到 PC 后，有两种方法可以将固件下载到目标板上，分别对应上述两种硬件连接方式。

#### 连接设备

在将固件下载到目标板之前，请确保 BDT 已找到该设备，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/BurningandDebuggingTool.png)

如果 BDT 没有找到设备，如下图所示，可以点击 “Refresh” 查看可用设备。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/CheckAvailableDevice.png)

如果 BDT 发现多个设备，所有设备将会列出，如下图所示。点击 “Refresh” 按钮后，默认情况下第一个设备将连接到 BDT。如果想要连接其他设备，可以选择指定的设备，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelecttheSpecifiedDevice.png)

#### 通过 “USB” 模式将固件下载到 “Flash” 中

在使用 “USB” 模式下载或调试 MCU 之前，请确保指定的 MCU 支持 USB 功能，并且其 USB 功能可用。

接下来，用户可以按照本章指南，通过 “USB” 模式将固件下载到目标板的特定 flash 空间。

**步骤 1：** 选择目标板的芯片类型，例如 B92_3V3，支持以下两种方法。

*   方法 1：使用下拉菜单选择芯片类型。
    
*   方法 2：按组合快捷键 “Ctrl+Q” 切换芯片类型。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectchiptype.png)

**步骤 2：** 选择下载模式为 “USB” ，支持以下两种方法。

*   方法 1：使用下拉菜单选择 USB 下载模式。
    
*   方法 2：按组合快捷键 “Ctrl+W” 切换到 USB 下载模式。每次切换后，下拉菜单将自动显示当前下载模式。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelectdownloadmodeasUSB.png)

**步骤 3：** 点击 “Setting” 按钮，打开设置对话窗口。选择 “Flash” 选项。用户可以采用以下任意一种方法，设置目标固件存储的 flash 起始地址偏移量，例如 0x000000（默认选项）。

*   方法 1：使用 “Download Addr” 的下拉菜单选择可用的偏移选项。
    
*   方法 2：在 “Download Addr” 的编辑框中输入偏移地址。
    

**注意：**

*   用户还可以配置 “SRAM”/“OTP” 设置选项，以便将目标固件下载到 SRAM 或 OTP 中的目标区域。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectstartingoffsetaddress.png)

**步骤 4：** 选择要下载到目标板的目标固件文件。

（1）点击 File->Open，打开文件选择窗口。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Openfileselectwindow.png)

（2）在文件选择窗口，选择目标 bin 文件（如 Telink.bin），然后点击 “打开” 按钮。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selecttargetfileandopennewfilepath.png)

文件路径将显示在主界面的底部。每次通过文件选择窗口打开新文件路径时，它都会被添加到 “File->Reopen” 的子菜单中。这样可以简化后续选择固件操作，用户可以直接选择 “Reopen” 子菜单中可用的目标文件路径。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DirectlyselecttargetfilepathinthesubmenuofReopen.png)

**步骤 5：** 检查目标板和 PC 之间的连接状态，确保其正常。

*   如果连接状态正常，主界面左下角将显示 “usb device: ok” 或 “evk device: ok”。
    
*   如果主界面左下角显示 “usb device: not found”，则表示目标板没有正确连接到电脑上。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Connectionstatusindication.png)

**步骤 6：** 将选定的文件下载到目标板。

点击 “Download” 按钮，所选固件文件将通过 USB 模式下载到目标板的指定 flash 空间。日志窗口将显示相应的日志信息，如下所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadFWintoFlashviaUSBmode.png)

**步骤 7：** 复位 MCU，使新下载的程序运行，而无需重启 MCU（从 Burning EVK 上拔下 / 插入），用户可以按照以下任意一种方法启动并运行 MCU。

*   如果通过下拉菜单选择 “manual mode”，固件烧录后，用户可以点击工具右上角的 “Reset” 按钮手动复位 MCU。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ManualMCUreset.png)

*   用户也可以在固件烧录前通过下拉菜单选择 “auto mode” ，以便在固件烧录后自动复位。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AutoMCUreset.png)

#### 通过 “EVK” 模式将固件下载到 “Flash” 中

在使用 “EVK” 模式下载固件之前，请确保目标板通过 “Burning EVK” 方式连接到 PC，并且目标板的单线通信已建立。

用户可以按照本章指导，通过 "EVK" 模式将固件下载到目标板的特定 flash 空间。

**步骤 1：** 选择目标板的芯片类型，例如 B92_3V3。支持以下两种方法。

*   方法 1：使用下拉菜单选择芯片类型。
    
*   方法 2：按组合快捷键 “Ctrl+Q” 切换芯片类型，下拉菜单将自动显示每次切换后的当前类型。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectchiptype.png)

**步骤 2：** 选择下载模式为 “EVK”，支持以下两种方法。

*   方法 1：使用下拉菜单选择 EVK 下载模式。
    
*   方法 2：按组合快捷键 “Ctrl+W” 切换到 EVK 下载模式。每次切换后，下拉菜单将自动显示当前下载模式。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelectdownloadmodeasEVK.png)

**步骤 3：** 点击 “Setting” 按钮，打开设置对话窗口。选择 “Flash” 选项。用户可以采用以下任意一种方法，设置目标固件存储的 flash 起始地址偏移量，例如 0x000000（默认选项）。

*   方法 1：使用 “Download Addr” 下拉菜单选择可用的偏移选项。
    
*   方法 2：在 “Download Addr” 的编辑框中输入偏移地址。
    

**注意：**

*   用户还可以配置 “SRAM”/“OTP” 设置选项，以便将目标固件下载到 SRAM 或 OTP 中的目标区域。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/OpentheSettingDialog.png)

**步骤 4：** 选择要下载到目标板的目标固件文件。

用户可以通过 “File -> Open” 或 “File -> Reopen”（如果在子菜单中可用）选择目标文件，文件路径将在主界面的底部可见。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelecttheTargetFile.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelectbinFile.png)

**步骤 5：** 检查目标板和 PC 之间的连接状态，确保它是正常的。

*   如果连接状态正常，主界面的左下方会显示 "usb device: ok" 或 "evk device: ok"。
    
*   如果主界面的左下方显示 "usb device: not found"，表示目标板没有正确连接到电脑上。
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/CheckConnectionStatus.png)

**步骤 6：** 将选定的文件下载到目标板。

通过点击 “Download” 按钮，所选的固件文件将通过 EVK 模式下载到目标板的特定 flash 空间。日志窗口将显示相应的日志信息，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadFWintoFlashviaBurningEVKmode.png)

**步骤 7：** 复位 MCU，使新下载的程序运行，而无需关闭 MCU 电源。用户可以按照以下两种方法之一启动并运行 MCU。

*   如果通过下拉菜单选择 “manual mode”，固件烧录后，用户可以点击工具右上角的 “Reset” 按钮手动复位 MCU。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ManualMCUreset1.png)

*   用户也可以在固件烧录前，通过下拉菜单选择 “auto mode”，以便在固件烧录后自动复位。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AutoMCUreset1.png)

#### 将固件下载到 “SRAM” 或 “OTP” 中

默认情况下，“Setting” 选项设置为 “Flash”，即通过单击 “Download” 按钮，目标固件将下载到目标板的 “Flash” 空间。

用户还可以将 “Setting” 选项更改为 “SRAM” 或 “OTP”。在这种情况下，通过点击 “Download” 按钮，目标固件将相应地下载到目标板的 “SRAM” 或 “OTP” 空间。

目标文件下载成功后，目标板不会在 “manual mode” 下自动运行新的固件，因此用户需要点击 “Reset” 按钮启动程序。用户还可以在下载前通过下拉菜单选择 “auto mode”，以启用 MCU 自动复位。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadfirmwaretoSRAMviaautomode.png)

如果目标板支持 OTP 功能，用户可以将固件下载到 “OTP” 中。

#### 多地址下载

有时候，需要将多个固件下载到 Flash、SRAM 或 OTP 的不同地址中。

例如，用户可以按照以下步骤将 “Telink.bin” 下载到 Flash 的地址 “0x00000000” 和 “0x00020000” 中。

**步骤 1：** 选择目标内存空间（如 Flash）来存储要下载的固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectdestinationspace.png)

**步骤 2：** 点击 “Tool -> Multi-address download” 或按快捷键 “Ctrl+P” ，打开 “Multi-address Download” 界面。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/OpenMultiaddressDownloadinterface.png)

**步骤 3：** 点击 “Add” 按钮，添加固件文件并设置目标地址。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Addfirmwarefileandsettargetaddress.png)

**步骤 4：** 将固件 1 的路径添加到列表中，并设置起始地址的偏移量以存储此固件。

（1）首先，选择第一行（No.1），然后点击 “File” 按钮将目标 bin 文件（例如 “Telink.bin”）添加到列表中，相应的目录将显示在 “File Path” 列中。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AddFW1.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AddFW2.png)

（2）然后设置起始 Flash 地址的偏移量，将该固件存储在 “Start Address(H)” 列中。

为确保固件存储的目标区域有效，该工具将自动计算固件的大小和结束地址，然后在 “File Size(Bytes)” 和 “End Address(H)” 列中显示计算结果。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Setoffsetaddress1.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Setoffsetaddress2.png)

**步骤 5：** 请参阅步骤 4，将固件 2 的路径添加到列表中，并设置起始地址的偏移量以存储此固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/addthepathoffirmware2.png)

**步骤 6：** 单击 “Download” 按钮，将添加的固件 1 和固件 2 下载到目标板的指定内存位置。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Downloadbutton.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Startdownloadingfirmware1.png)

**步骤 7：** 将所有固件下载到目标板后，点击 “Reset” 按钮使程序运行，而无需重启目标板。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Reset.png)

#### OTP 启动信息下载

（1）配置 OTP 时钟，以 B80 芯片为例，otp 地址 0x3ff8 写入数据 0x060301bf。

*   功能：将 MCU 数字寄存器 0x603 写入 0x01，用于配置 OTP 时钟。

（2）启动代码，以 B80 芯片为例，otp 地址 0x3ff0 写入数据 0x060298bf。

*   功能：将 MCU 数字寄存器 0x602 写入 0x98，MCU 启动代码的执行，程序开始跑起来。

（3）搬代码到 RAM 中，以 B80 芯片为例，otp 地址 0x3ff4 写入数据 0x0001f03f。

*   功能：MCU 将 OTP 中从 0 地址开始的前 7936 个字节的内容搬到 RAM 0 地址处。
    
*   数据长度 = 0x1f0 * 16 =7936 bytes
    

OTP 需要搬多少大小程序到 ram 中，可以参照如下计算方法。

OTP 上电第一次需要将 vector 和 ram code 段都搬到 ram 中，这两个段的大小计算公式为：

ram code 的 LMA 的基地址 + ram code size（之所以不用 vector size + ram_code size 来计算，是因为可能会有对齐因素导致大小计算的不对）

又因为启动信息中的长度信息是：实际长度 / 16。所以启动信息中的长度信息的通用的计算公式总结如下：

（（ram code 的 LMA 的基地址 + ram code size）（16 字节对齐））/ 16。

所以如下 lst 文件的最终计算公式为：0x220+0xAEC，16 字节对齐后的大小为 3344; 3344/16=209(0xd1)

对应 otp 地址 0x3ff4 写入数据 0x0000d13f 即可。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/lst.png)

以 B80 芯片为例，用户可以按照以下步骤进行 OTP 启动信息的下载。

**步骤 1：** 打开 BDT 工具，选择 B80 芯片。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ChipSelect.png)

**步骤 2：** 点击 Tool->Memory Access，输入 OTP 地址，写入启动信息及其长度，并在 data 编辑框按下回车键，对应信息会烧录到 OTP 地址中。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StartOTP.png)

### 擦除 Flash 扇区

“Erase Flash Sector” 功能用于以 4kB 为单位从特定地址开始擦除特定 flash 空间。

例如，要擦除从地址 0x00000000 开始的 64kB 的 flash 空间，用户可以按照以下步骤进行。

**步骤 1：** 点击 “Setting” 按钮打开设置对话框。选择 “FLASH” 设置选项。

设置要擦除 flash 空间的起始地址，例如 0x000000000（默认选项：0x00000000），用户可以通过 “Erase Flash Addr” 下拉菜单选择偏移选项（如果可用），或直接在编辑框中输入偏移地址。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectstartingaddress.png)

**步骤 2：** 以 4kB 为单位设置要擦除的 flash 空间大小，例如 64kB（默认选项：512kB），用户可以通过 “Sector Erase Size” 下拉菜单选择大小（如果可用），或直接在编辑框中输入大小。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Seterasesize.png)

**步骤 3：** 点击 “Erase” 按钮，开始擦除目标板的指定 flash 空间。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Erase512kBflashspacestartingfrom0x000000.png)

### Flash 去除保护

Flash 被写保护之后会导致擦写以及烧录不成功，需要去除保护之后才能对 Flash 进行相应操作。Flash 去除保护操作步骤如下。（该功能从 v5.7.0 版本之后开始支持）

**步骤 1：** 打开 BDT 工具，选择芯片类型。

**步骤 2：** 点击 “Unlock” 按钮，log 中出现 “Flash unlock ok” 代表去除保护成功。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Flash_Remove_Protection.png)

### Flash 保护状态提醒

因当前 SDK 会默认为 Flash 添加写保护，所以在对 Flash 进行擦除、烧录前会先获取写保护状态。获取 Flash 保护状态操作步骤如下。（该功能从 v5.7.8 版本之后开始支持）

**步骤 1：** 打开 BDT 工具，选择芯片类型。

**步骤 2：** 点击 "Download" 或 "Erase", 若 Flash 处于保护状态，则 log 中提示 “Please unlock flash first!”。

**步骤 3：** 点击 “Unlock” 按钮，log 中出现 “Flash unlock ok!” 代表去除保护成功。

**步骤 4：** 再次点击 "Download" 或 "Erase" 按钮，log 中出现 “Flash status：unlocked” 代表当前 flash 未处于写保护状态，可正常进行烧录和擦除。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Flash_Lock_Status.png)

### Flash 自动去除保护

如果需要在每次 Download 或 Erase 前自动进行 unlock 操作，可点击 Auto Unlock 按钮。

**步骤 1：** 打开 BDT 工具，选择芯片类型。

**步骤 2：** 选择 "Auto unlock"。

**步骤 3：** 点击 "Download" 或 "Erase" 按钮。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Flash_Auto_Unlock.png)

### Flash 信息查询

如果需要查询当前 flash 的 mid、status、lock area 以及 uid，可点击 Flash info 按钮。

**步骤 1：** 打开 BDT 工具，选择芯片类型。

**步骤 2：** 点击 "Flash info" 按钮。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Flash_information.png)

### Cache 解析

芯片上电搬运代码，如果即将运行的代码不在 cache 中，则会自动从 Flash 或 OTP 中读取函数到 cache 中。该功能主要是解析 cache 搬运代码是从 flash 哪个地址取数据，以及数据内容是什么。并将解析的数据与原始数据进行比较，来确定 cache 搬运代码是否正确。该功能前提是芯片已下载程序并运行，然后通过如下步骤进行解析。（该功能从 v5.7.0 版本之后开始支持）

**步骤 1：** 打开 BDT 工具，选择芯片类型，选择芯片需要下载的固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Cache_Bin.png)

**步骤 2：** 点击 “Cache” 按钮。下图标记 “1” 为搬运代码所在的 flash 地址。标记 “2” 为对应 flash 地址存储的数据。标记 “3” 代表测试结果。"OK" 代表搬运代码数据正确。"FAIL" 代表搬运代码数据出错。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Cache_Analyze_OK.png)

Cache 数据出错时，"rawdata" 代表 flash 地址对应的正确数据的值。"status" 代表 "rawdata" 和 Cache 中的数据比较的结果。"status" 为 "T"，二者数据一致。"status" 为 "F"，则二者数据不一致。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Cache_Analyze_FAIL.png)

### Activate MCU

“与目标板通信失败时激活 MCU” 功能仅适用于 “Burning EVK” 与 “EVK” 模式下目标板之间的 Swire 连接，即不支持 “USB” 模式或 “Burning EVK” 与 “EVK” 模式下目标板之间的 USB 连接。

当固件烧录失败时，请确保目标板通过 Swire 与 “Burning EVK” 连接，然后点击 “Activate” 按钮启用此功能以激活 MCU。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ActivateMCU.png)

### Debug

MCU 开始运行后，要访问内存空间（Flash/Core/Analog/OTP），用户可以直接按组合快捷键 “Ctrl+M” 或点击 “Tool -> Memory Access”，打开 “Memory Access” 窗口，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/MemoryAccessinterface.png)

#### 访问存储器

(1) 从内存空间读取数据

想要从特定存储空间（Flash/Core/Analog/OTP）读取数据，用户可以执行以下步骤：

**步骤 1：** 在 “Memory Access” 窗口中选择 MCU 类型（如 “TL721X”）和与目标板的通信模式（如 “EVK”）。

**注意：**

如果选择 “USB” 模式与目标板通信，请确保所选 MCU 支持 USB 功能且其 USB 功能可用。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SelectMCUtypeandcommunicationmode.png)

**步骤 2：** 在 “Memory Access” 窗口中选择操作目标（如 “CORE”）并设置操作大小（如 “16”）。

**注意：**

*   如果选择 “OTP” 作为操作目标，请确保所选 MCU 支持 “OTP” 功能。
*   想要设置操作大小，用户可以通过下拉菜单选择大小（如果可用），或直接在编辑框中设置大小。
*   最大操作大小为 1MB。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Setoperationdestinationandsize.png)

**步骤 3：** 将鼠标移动到 “addr” 框，然后输入要读取的起始地址的偏移量（例如 “0x040000”）。将光标保持在 “addr” 框中，通过单击 “Tab” 键，用户可以从指定的内存空间读取数据。

**注意：**

*   每次点击 "Tab" 键启动内存读取操作时，可编辑框的值将会被保存，以便下次可以通过下拉菜单直接选择它。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Setstartingaddressandinitiatereading.png)

*   当读取大于 1kB 的内存空间（如 CORE）时，读取的数据将自动保存到 “user” 文件夹下名为 “read.bin” 的文件中。用户还可以使用特定的命令行更改文件名以保存读取的数据。详细信息请参考章节[命令行](#命令行)。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Savereaddata.png)

(2) 将数据写入内存空间

将数据写入特定的内存空间，用户可以执行以下步骤：

**步骤 1：** 在 “Memory Access” 窗口中选择 MCU 类型（如 “TL721X”）和与目标板的通信模式（如 “EVK”）。

**注意：**

如果选择 “USB” 模式与目标板通信，请确保所选 MCU 支持 USB 功能且其 USB 功能可用。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/MemoryAccessWindow.png)

**步骤 2：** 在 “Memory Access” 窗口中选择操作目标（如 “CORE”）并设置操作大小（如 “16”）。

**注意：**

*   如果选择 “OTP” 作为操作目标，请确保所选 MCU 支持 “OTP” 功能。
*   想要设置操作大小，用户可以通过下拉菜单选择大小（如果可用），或直接在编辑框中设置大小。
*   最大操作大小为 256 字节。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SetOperationSize.png)

**步骤 3：** 将鼠标移动到 “addr” 框，然后输入要写入的起始地址的偏移量（例如 “0x040000”）。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/OffsetoftheStartingAddress.png)

**注意：**

当操作目标选择为 “CORE” 时，如果设置的地址小于 “SRAM” 的起始地址，则实际访问的目标存储空间为数字寄存器；如果设置的地址大于 “SRAM” 的起始地址，则实际访问的目标内存空间是 SRAM。

**步骤 4：** 将数据写入指定的地址。

将鼠标移动到 “data” 框，然后输入要写入的目标数据。将光标保持在 “data” 框中，通过点击 “Enter” 键，用户可以将指定的数据写入指定的存储空间。

**注意：**

当输入数据时，字节之间必须用空格隔开，如下所示：

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Setdataandinitiatewriting.png)

#### 操作变量列表

在查看所有全局变量之前，请确保 “.lst” 文件和 “.bin” 文件位于同一目录下，有可能出现两种情况，如下所示。

**情况 1：** 如果只有一个 “.lst” 文件和 “.bin” 文件位于同一目录下，则会自动选择这个 “.lst” 文件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Case1.png)

**情况 2：** 如果有多个 “.lst” 文件和 “.bin” 文件放在同一目录下，则自动选择与所选 “.bin” 文件同名的 “.lst” 文件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Case2.png)

例如：如果选择 “Telink.bin” 文件，将自动选择 “Telink.lst” 文件。如果没有 “Telink.lst” ，并且所选 “Telink.bin” 文件的目录下仅放置了一个 “xxx.lst” 文件，则将会选择唯一的 “xxx.lst” 文件。

(1) 更新变量列表

想要查看所有全局变量，用户可以选择 “Tdebug” 页面，将鼠标移动到变量列表，然后右键单击鼠标选择 “Refresh” 或按快捷键 “F3” 。每次按 “F3”，变量列表就会更新一次。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Updatevariablelist.png)

(2) 对变量进行排序

根据需要，用户还可以右键单击鼠标，选择 “Sort by address” 将所有变量按地址从低到高排序（默认），或选择 “Sort by name” 将所有变量按变量名称的 ASCII 码值从 A 到 z 排序（比较第一个不同的字符）。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Sortvariablebyname.png)

(3) 查看超过 4 字节的变量

如果变量的长度大于 4 字节，通过点击 “variable list” 的 “Value” 列中的 “…”，其值将显示在右侧的日志窗口中。

如果变量的长度大于 1024 字节，则该变量的所有值都将保存在名为 “Read.bin” 的文件中。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Readvariablevaluemorethan4bytes.png)

(4) 修改变量值

长度不超过 4 字节的变量支持直接写入操作，双击 “Value” 列中相应的框可以直接修改其值。

例如：要将地址 “0x000401e0” 中变量 “g_pm_multi_addr” 的值修改为 “0x00000025”，用户可以执行以下步骤：

**步骤 1：** 双击指定变量对应 “Value” 列中的框（例如 “g_pm_multi_addr”），使该框可编辑。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DoubleclickspecifiedValuebox.png)

**步骤 2：** 输入新的变量值（例如 “0x00000025”）来替换旧的变量值（“0x00000000”）。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Modifyvariablevalue.png)

**步骤 3：** 按 “Enter” 键将新的值写入指定变量的地址中。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Writedatatospecifiedaddress.png)

#### Debug MCU

在使用 “Run”, “Pause”, “Step” and “PC” 等按钮调试 MCU 之前，请确保所选 MCU 支持此功能。

在下面的小节中，以 MCU “B85” 为例介绍该功能。

(1) Run MCU

点击 “Pause” 或 “Step” 按钮后，用户可以通过点击 “Run” 按钮使 MCU 从当前位置继续运行。请点击 “PC” 按钮查看 MCU 状态，读取 PC 并确保程序再次运行。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/RunMCU.png)

(2) Pause MCU

想要查看 MCU 状态的详细信息，用户可以点击 “Pause” 按钮暂停 MCU。点击 “Run” 按钮，MCU 将从当前位置继续运行。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/PauseMCU.png)

(3) Step MCU

如果可以与目标板通信，用户可以点击 “Step” 按钮逐步查看指令的当前位置。

“Trace MCU” 和 “Step MCU” 都支持以下两种模式。

a. 如果选择了 “Single step” 模式，MCU 将进入单步模式，在点击 “PC” 或 “Step” 按钮后，将实施一次 PC 追踪。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StepMCUinSinglestepmode.png)

b. 如果选择 “continuous” 模式，MCU 将进入连续模式，实施连续的 PC 追踪或使 MCU 连续步进。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StepMCUincontinuousmode.png)

想要取消 “continuous” 模式，用户可以将模式切换到 “Single step” 模式，或者点击 “Run”/“Pause” 按钮。

如果目标固件（bin 文件）和 “xxx.lst” 文件位于同一目录下，用户可以通过选择 “View -> interp .lst” 并点击 “PC” 按钮解析 “xxx.lst” 文件来查看更多详细信息，如下所示。请参考章节[操作变量列表](#操作变量列表)。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/xxxlstfile.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Selectinterplst.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StepMCUwithinterplstselectedinSinglestepmode.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StepMCUwithinterplstselectedincontinuousmode.png)

(4) Trace PC

如果可以与目标板通信，用户可以点击 “PC” 按钮查看指令的当前位置，如下所示：

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/TracePCinSinglestepmode.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/TracePCwithinterplstselectedinSinglestepmode.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SwitchSinglestepmodetocontinuousmode.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/TracePCwithinterplstselectedincontinuousmode.png)

(5) Stall MCU

当没有足够的时间查看 MCU 的状态时，用户可以点击 “stall” 按钮暂停 MCU 并查看 MCU 的状态或更改 MCU 的配置。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StallMCU.png)

**注意：**

在 EVK 模式下，只有使用 “Firmware_v3.2.bin”（或更高版本）烧录的 EVK 支持此功能。

(6) Start MCU

暂停 MCU 后，点击 “start” 按钮启动 MCU，使 MCU 从 SRAM 开始运行。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/StartMCU.png)

### 单线同步

在设置单线同步速度之前，请确保以下各项：

（1）电源正常；

（2）MCU 未处于 “低功耗” 模式；

（3）MCU 的单线功能可用；

（4）系统时钟正常。

当 “Burning EVK” 和目标板之间无法建立连接时，用户可以尝试设置 Swire（单线）同步速度来改善通信。**注意：**Swire 寄存器地址可能因芯片类型而异。

（1）在四个可编辑框中更改主速度和从速度，如下所示。**注意：**Swire 寄存器地址可能因芯片类型而异。

（2）点击 “SWS” 按钮以实现 Swire 同步。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SetSwiresynchronizationspeed.png)

在将固件下载到目标板或调试 MCU 之前，建议每次打开 MCU 电源时，用户应执行一次 Swire 同步，以检查与目标板的通信是否正常。

如果与目标板的通信状态错误，用户可以参考章节 [Activate MCU](#activate-mcu) 开头提到的方法解决问题。

### 命令行

用户还可以使用命令行访问内存或将文件下载到目标板。在下面的小节中，以 “read core” 为例。

#### 单命令行

**步骤 1：** 通过选择 “Tool->Cmdline Input” 或按组合快捷键 “Ctrl+I” 打开命令行输入窗口。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Opencmdlineinputwindow.png)

**步骤 2：** 按如下所示输入所需的单个命令，然后按 “Enter” 键。具有指定名称的文件将在指定位置可用。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Entersinglecommandline.png)

#### 多命令行

该工具支持多命令行操作。

所有命令都需要用分号隔开，如下所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Entermultiplecommands.png)

### 日志窗口

该工具支持 USB 打印功能，因此具有 USB 功能的 MCU 可以使用 USB 打印功能，在 PC 端的日志窗口中输出信息。

**步骤 1：** 点击 “View -> usb log -> ASCII” 打开 usb 日志窗口。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Openusblogwindows.png)

**步骤 2：** 在 “usb log” 模式下，所有输出的字符将以 “Ascii” 形式显示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Displayoutputcharacters.png)

**步骤 3：** 再次点击 “View -> usb log” 退出 “usb log” 模式。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Exitusblogmode.png)

### 帮助

点击 “Help -> Command line”，所有命令将显示在 “Download” 或 “Tdebug” 页面的日志窗口中。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Commandline.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/showallcommands.png)

点击 “Help -> User guide”，将打开嵌入的 “Help” 文档 “_Telink Burning and Debugging Tool (BDT) User Guide_”，如下所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Userguide.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Openhelpdocument.png)

要获取有关 Telink 的更多信息，用户可以点击 “Help -> About Telink”, 即可在浏览器中跳转到 Telink 官方网站。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AboutTelink.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/GetinformationaboutTelink.png)

## 升级固件

用户可以按照以下步骤升级 “Burning EVK” 的固件。

**步骤 1：** 点击 “Help -> Upgrade” 打开 “Upgrade EVK” 对话框。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Upgradeevkwindow.png)

**步骤 2：** 点击 “Read FW Version” 按钮检查当前固件版本。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/checkcurrentfwversion.png)

**步骤 3：** 单击 “Load…” 按钮加载新固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/loadnewfw.png)

**步骤 4：** 点击 “Upgrade” 按钮将新固件升级到 “Burning EVK” 中。注意：用户必须在使用 EVK 之前对它进行重启。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/upgradefwintoevk.png)

## 工具指南

本章节主要介绍 BDT 的内置工具，内容包括工具的功能及其使用方法。

### BQB Tool

#### 功能描述 （BQB Tool）

该工具有两个主要的功能：

*   根据需求配置生成用于 BQB 测试的固件（Flash 和 SRAM 两种类型的 bin 文件），其中可配置的选项包括：UART 引脚、PA 控制引脚、TX 能量、内外部电容、内部供电方式以及校准参数的位置。另外，生成的固件可以通过工具直接下载到 DUT 中（通过 Swire 的方式）。**注意：**上述 BQB 测试固件为 uart 两线测试程序，串口通信的波特率为 115200。
    
*   收发包测试
    

#### 界面组成及使用说明 （BQB Tool）

该工具主要由固件下载界面和测试界面两个部分组成，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/bqbtoolui1.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/bqbtoolui2.jpg)

(1) 芯片的选择

通过 BDT 主界面 MCU 列表来进行芯片型号的选择，选择好芯片之后可通过 BQB Tool 界面的标题栏来判断工具是否支持对应芯片。

(2) 固件的保存和下载

**Step1 - 选择模式和协议：** 固件下载界面 “Test Select” 区域，通过 Test Select 选择模式以及 Protocol 选择协议。

**Step2 - 配置固件：** 固件下载界面 “Configure” 区域，Acc.Code 用来配置访问码，Baud Rate 用来配置波特率，Uart TX.(RX.)用来配置 UART 的 TX 和 RX 引脚，Calibration Postion 用来配置校准数据的存储位置（根据实际情况选择，测试时可选择 SRAM）,Power mode 用来配置芯片内部的供电方式，IO Voltage 用来配置 IO 电平模式，TX Power 用来配置发包的能量（default 为默认值, 一般为 7dBm），Capacitor 用来配置内外部电容，DP Through Swire 用来使能 / 禁用该功能，使能 PA Setting 可以打开 PA Cfg.Tool 进行 PA_TX(RX)引脚的配置。

**Step3 - 选择固件类型：** 固件下载界面 “Operation” 区域，通过单选框来选择类型，可供选择的类型包括 Flash 程序和 SRAM 程序两种。

**Step4 - 保存 / 下载固件：** 固件下载界面 “Operation” 区域，通过点击 “Save As Binary” 按钮来保存固件，通过点击 “Download & Run” 按钮来下载固件。

(3) 收发包测试

**Step1 - 连接串口：** 测试界面 “Serial Port Setting” 区域，“Serial Port”为可选择的串口（若列表为空，可通过 “Refresh” 按钮来更新），“Baud Rate”为通信的波特率（默认选用 115200，与固件的串口通信速率保持一致），串口配置好之后点击 “Open” 按钮打开串口。

**Step2 - 配置测试模式：** 测试界面 “BQB Test” 区域，RF Mode 用来选择 RF 模式，Frequency 用来配置测试频点，Pack.Type 用来选择包的数据类型，Payload 用来配置包的数据长度。

**Step3 - 测试：** 测试界面 “BQB Test” 区域，“Initialize”按钮用来初始化 DUT 的状态，“TX”按钮用来控制 DUT 发包，“RX”按钮用来控制 DUT 收包，“END”按钮用来控制 DUT 停止收包或者发包（收包状态下点击 END 按钮可统计收包的个数）。

### Jtag Tool

#### 功能描述 （Jtag Tool）

该工具的主要功能如下：

*   安装 Jtag 硬件相关的驱动
*   通过 Jtag 下载 / 擦除固件
*   通过 Jtag 读写参数
*   通过 Jtag 调试

#### 界面组成及使用说明 （Jtag Tool）

Jtag 工具的界面由两部分组成，分别是 “Target” 区域和 “Debug” 区域，具体如下图所示。其中 “Target” 区域负责设备的连接以及 Jtag 设备驱动的安装，“Debug”区域主要负责读、写、擦以及调试功能。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/jtagtoolui.png)

(1) Jtag 设备的驱动安装

**Step1 - 接入 Jtag 设备：** Jtag 设备如下图所示，通过 USB 与 PC 连接。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/jtagdevice.png)

**Step2 - 检查设备驱动：** 打开设备管理器查看设备，若驱动已安装，则会被正常识别成 “libusbK USB Devices” 设备，如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/jtagconnectok.png)

若驱动未正常安装，则会如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/jtagconnecterror.png)

**Step3 - 安装驱动：** Jtag 工具界面 “Target” 区域，点击下方的 “Install Jtag Driver” 来安装驱动。

(2) 连接调试设备

**Step1 - 接入调试设备：** 将调试设备通过 Jtag 接口连接到 Jtag 设备上，正常连接状态下 Jtag 设备只有蓝灯常亮。若红灯同时处于常亮状态，则先检查 Jtag 的驱动是否安装。若驱动安装正常，接着查看 Jtag 盒子与测试板之间的连线是否正常。

**Step2 - 连接目标设备：** 调试设备成功接入后，点击 Jtag 工具界面 “Target"区域的"Connect Target” 按钮来连接调试设备。若 Jtag 工具界面的标题栏显示为 “Jtag Tool – target connected”，则表示已经连接成功，此时“Debug” 区域的控件变为可操作状态。若连接不成功，可通过插拔一下 USB 接口来解决。

(3) 下载功能

**Step1 - 选择固件：** BDT 工具主界面，通过点击 “File->Open” 来选择需要下载的固件。

**Step2 - 设置起始地址：** Jtag 工具主界面 “Debug” 区域，在 “Addr” 对应的输入框中输入下载的起始地址。

**Step3 - 设置固件载入的对象：** Jtag 工具主界面 “Debug” 区域，通过点击 “FLASH” 和“SRAM”两个单选框控件来选择。

**Step4 - 执行下载：** Jtag 工具主界面 “Debug” 区域，点击 “Download” 按钮来执行下载操作。

**注意：**

下载到 Flash 中的程序需通过点击 “Restart” 按钮来运行，而对于下载到 SRAM 中的程序则通过点击 “Run” 按钮来运行。

(4) 擦除功能

**Step1 - 设置起始地址：** Jtag 工具主界面 “Debug” 区域，在 “Addr” 对应的输入框中输入下载的起始地址。

**Step2 - 设置擦除长度：** Jtag 工具主界面 “Debug” 区域，在 "Erase Flash”按钮下方 “Len” 对应的输入框中输入需要擦除的长度。

**Step3 - 执行擦除：** Jtag 工具主界面 “Debug” 区域，点击 “Erase Flash” 按钮来执行擦除操作。

(5) 读写功能

该工具支持 Memory、Flash 和 Analog 三种模式的读写，其中 Memory 方式可支持 byte、half-word（2 byte）、word（4 byte）三种方式的读写，其他模式只支持按 byte 来读写。

**Step1 - 设置读写模式：** Jtag 工具主界面 “Debug” 区域，点击 “Write” 按钮后面的下拉框来选择模式。

**Step2 - 设置读写宽度：** Jtag 工具主界面 “Debug” 区域，点击读写模式选择框下方的下拉框来选择读写的宽度。

**Step3 - 设置读写的地址、长度：** Jtag 工具主界面 “Debug” 区域，在 “Write” 按钮下方 “Addr” 对应的输入框中输入地址，在 “Len” 对应的输入框中输入长度。如果是写数据，还需要在 “Data” 对应的输入框中输入需写入的数据。

**Step4 - 执行读写操作：** Jtag 工具主界面 “Debug” 区域，点击 “Read” 按钮来执行读操作，点击 “Write” 按钮来执行写操作。

(6) 调试功能

该工具支持的调试功能包括：读状态寄存器、读变量值以及常用的调试操作。

**Step1 - 读状态寄存器：** Jtag 工具主界面 “Debug” 区域，在 “Reg” 对应的输入框中输入状态寄存器的名称，接着按下回车键就可以查找对应的寄存器，接着通过点击下拉框来选择对应的寄存器就可以查看该寄存器的值。如果不知道寄存器的名称，也可通过输入 “*” 来列出所有可查看的寄存器。

**Step2 - 读变量值：** Jtag 工具主界面 “Debug” 区域，在 “Var” 对应的输入框中输入变量的名称，接着按下回车键就可以查找对应的变量，接着通过点击下拉框来选择对应的变量就可以查看该变量的值。如果不知道变量的名称也可通过输入“_” 来列出所有可查看的变量。__注意：_* 要实现该功能需要保证在 bin 文件目录下存在与之同名的 list 文件。

**Step3 - 常用调试操作：** Jtag 工具主界面 “Debug” 区域，点击 “Stall" 按钮来使设备停止，点击“Restart” 按钮使设备从 flash 中重新加载固件运行，点击 “Pause” 按钮来使设备程序暂停，点击 “Run” 按钮使设备从程序暂停处继续运行，点击 “Step” 按钮来使设备程序单步运行，点击 “PC” 按钮来查看设备当前的 PC 指针。另外，如果在 bin 文件目录下存在与之同名的 list 文件，还可以查看对应的汇编代码，不过在使用该功能前还需要在 “Var” 对应的输入框中输入 “*” 并按下回车键。

### TWS Tool

#### Download Tool

(1) 功能描述 （Download Tool）

“Download Tool”主要用来烧写 bin 文件、参数信息等到 Flash 的指定地址当中。该工具支持一次烧录单个和多个对象，最多支持一次烧录 4 个 bin 文件、1 组 “BT Name”参数以及 1 组 “BT MAC” 参数。

(2) 界面介绍

“Download Tool”的界面如下图所示，主要包括 “Setting” 和“Operation”两个区域。其中 “Setting” 区域负责设置下载的信息，“Operation”部分负责执行下载操作。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/twsdownloadtoolui.png)

(3) 使用说明

**Step1 - 设置烧录信息：** Download 工具的主界面 “Setting” 区域，通过最左侧的单选框选择需要烧录的信息，在 “Address” 对应的输入框中输入各信息写入的 Flash 地址，在 “Path/Content” 对应的输入框中输入对应的信息。对于固件下载，通过点击对应得 “Browser” 按钮来加载文件路径。而对于 “BT Name/MAC”，则通过对应的输入框直接输入。“BT Name/MAC” 都有自增的功能（每烧录完一组数据对应的值就会自增），通过右侧的单选框来选择。另外需要注意的是 “BT Name” 的最大长度不得超过 25 字符。

**Step2 - 执行烧写操作：** Download 工具的主界面 “Operation” 区域，通过点击 “Download” 按钮来执行下载操作。

#### EQ Tool

(1) 功能描述 （EQ Tool）

该工具的主要功能如下：

*   生成 EQ 参数
*   进行在线 EQ 调参（需相关协议支持）

(2) 界面组成

EQ 工具的界面由 5 个区域构成，包括图表显示区域、“Configure”区域、“Parameter”区域、log 输出区域以及 “Operation” 区域，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/twseqtoolui.png)

(3) 使用说明

**Step1 - EQ 参数调节：** 首先选择调参的模式，通过 “configure” 区域下的 Mode 进行选择，工具默认提供三种可选模式，分别是：“Music”模式（即 Line Out），“Speech MIC”模式（即 Line In），“Speech SPK”模式（即 Line In to Line Out）。接着选择声道，通过 “configure” 区域下的 Channel 进行选择。接着选择样本频率和 EQ 调参的级数，分别通过 “configure” 区域下的 FreqSmp 和 Stages 进行选择。最后配置各级参数，包括滤波器类型、Q 值、中心频率以及增益值，分别通过 “parameter” 区域下 Type、Q、Fc 以及 dB 来配置。

**Step2 - 查看和保存 EQ 参数值：** 通过点击 “Operation” 区域中的 “Get Parameter” 按钮来获取参数值，通过点击 “Save as bin file” 按钮可以将生成的参数值保存成 bin 文件。

**Step3 - 保存 EQ 配置：** 通过 “Operation” 区域中 Setting 对应的复选框可进行 EQ 配置的保存和还原。对于保存操作，首先复选框选择“Save”，接着在弹窗中输入配置名称，最后点击 OK。对于还原已保存的配置，通过复选框选择已保存的配置名称即可还原配置。

**Step4 - EQ 在线调参：** 首先选择在线调参的方式，通过 “Operation” 区域中的单选框控件（“USB”和 “RF”）来选择在线调参的方式。接着通过点击“Operation” 区域中的 “Download” 按钮将 EQ 参数下载到设备中。

**注意：**

EQ 工具所支持的在线调参方式都需要有相关协议的支持，具体需咨询相关 FAE。

### RISC-V Tool

支持芯片通过 USB 实现如下功能：

*   读写寄存器
*   读写擦 flash
*   上报调试信息
*   VCD 功能

**注意：**

SDK 中必须有相应的交互协议，此工具才能使用。

#### 读存储器

从特定存储空间（RAM/Analog/Flash）读取数据，操作步骤如下。

**Step1 - 选择存储空间类型：** 在界面 “Memory” 区域点击下拉菜单选择类型。

**Step2 - 设置访问区域：** "Addr" 输入框输入所访问空间起始地址，并在 “Size” 输入框输入所需访问地址的个数。

**Step3 - 读取数据：** 将光标保持在 “Addr” 框中，通过按下键盘 “Tab” 按键，用户可以从指定的存储空间读取数据。

**注意：**

Size 输入框中的数据为十六进制。写入 “10” 代表读取 16 个字节数据。最多一次只能读取 256 个字节数据。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_read_memory.png)

#### 写存储器

在特定存储空间（RAM/Analog/Flash）写入数据，操作步骤如下。

**Step1 - 选择存储空间类型：** 在界面 “Memory” 区域点击下拉菜单选择类型。

**Step2 - 设置访问区域：** “Addr”输入框输入所访问空间起始地址，并在 “Size” 输入框输入待写入数据的长度。

**Step3 - 写入数据：** Data 框输入待写入的目标数据, 通过按下键盘 “Enter” 按键, 用户可以将指定的数据写入到指定的存储空间。

**注意：**

写数据最多只能写入四个字节数据。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_write_memory.png)

#### 固件下载

将固件下载到 flash 中，操作步骤如下。

**Step1 - 选择固件：** 点击 “File->Import bin”，选择所需下载的固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_import.png)

**Step2 - 擦除 flash：** 点击 “TS” 按钮，其次点击 “Chip_Erase” 按钮擦除 flash 所有数据。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_erase_flash.png)

**Step3 - 下载固件：** 点击 “Bin_DL” 按钮下载固件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_download.png)

#### VCD 功能

VCD 功能操作步骤如下。

**Step1 - 选择 header 文件：** VCD 功能区点击 “Def” 按钮，选择对应的 header 文件。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_header.png)

**Step2 - 启动 VCD 功能：** 点击 “VCD” 按钮启动。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_vcd.png)

**Step3 - 查看相关任务运行状态：** 点击 “View” 按钮，查看任务运行状态。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_view.png)

**注意：**

header 文件的定义和使用请咨询相关 SDK 负责人员。

#### 命令行说明

为方便调试，可输入对应命令执行相应操作。

(1) 读命令

命令格式: [28] [Type] [Address] [Size]

Type：访问空间类型，“00” 代表访问数字寄存器；“01” 代表访问模拟寄存器；“02” 代表访问 flash。

Address：访问空间的地址，占四个字节。

Size：访问地址的个数，占 4 个字节。

示例：读取数字寄存器 0x140280 地址一个字节数据。

命令：28 00 00140280 000001

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_read_cmd.png)

(2) 写命令

命令格式 [2a] [Type] [Address] [Data1] [Data2]……[DataN]

Type：访问空间类型，“00” 代表访问数字寄存器；“01” 代表访问模拟寄存器；“02” 代表访问 flash。

Address：访问空间的地址，占四个字节。

DataN：待写入的数据。

示例：flash 0x1000 地址写入数据 “0x1122334455”。

命令：2a 02 00001000 55 44 33 22 11

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_write_cmd.png)

(3) 擦 flash 命令

命令格式 [2a] [03] [Address] [Size]

Address：访问空间的地址，占四个字节。

Size：擦除 flash 的空间大小，占四个字节。

示例：flash 0x1000 地址擦除 4k 数据。

命令：2a 03 00001000 00001000

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_erase_cmd.png)

示例：擦整片 flash。

命令：2a 03 00000000 00000000

(4) 保存所读数据

命令格式 [r] [String] [28] [Type] [Address] [Size] [BinPath]

r: 读命令。

String：字符串，可自定义。

Type：访问空间类型，“00” 代表访问数字寄存器；“01” 代表访问模拟寄存器；“02” 代表访问 flash。

Address：访问空间的地址，占四个字节。

Size：所需要读取数据大小，占四个字节。

BinPath：所读数据待保存的路径。

示例：从 flash 0 地址读取 4k 数据，并保存到 D 盘。

命令：r read 0228 00000000 00001000 -d:\read.bin

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_save_cmd.png)

#### 日志清除及保存

日志清除：点击界面 Clear 按钮即可清除日志。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_clear_log.png)

日志保存：点击界面 Save 按钮，选择文件保存路径并输入文件名即可。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/risc_v_save_log.png)

### EMI Tool

#### 功能描述 （EMI Tool）

该工具有两个主要的功能：

*   配置和下载测试固件。
    
*   进行 EMI 测试。
    
*   进行非信令测试。
    
*   进行 RF 电流测试。
    

#### 界面组成及使用说明 （EMI Tool）

该工具主要由固件配置下载界面、EMI 测试界面、非信令测试界面以及 RF 电流测试界面四个部分组成，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/emitoolui1.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/emitoolui2.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/emitoolui3.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/emitoolui4.jpg)

(1) 芯片的选择

通过 BDT 主界面 MCU 列表来进行芯片型号的选择。

(2) 固件的保存和下载

**Step1 - 选择模式和协议：** 固件下载界面 “Test Select” 区域，通过 Test Select 选择测试模式。

**Step2 - 配置固件：** 固件下载界面 “Configure” 区域，"Power Mode" 用来配置芯片内部的供电方式，"IO Voltage" 用来配置 IO 电平模式，"Capacitor" 用来配置内外部电容，"Calibration Position" 用来配置校准数据的存储位置（根据实际情况选择）,"Access Code" 用来配置访问码，如果使用 “DP Through Swire” 功能，则需勾选对应的选项。

**Step3 - PA 配置：** 固件下载界面 “PA Setting” 区域，如果需要使用 PA 功能，则勾选上 “Enable"。除了上述操作，用户还需要将 PA 操作的 binary 文件路径输入到对应的文本框中。PA 操作相关的 binary 文件可通过“PA Configure Tool” 来生成，可点击 “PA.Cfg.Tool” 来打开该工具，工具的使用可参考对应的章节。

**Step4 - 选择固件类型：** 固件下载界面 “Operation” 区域，通过单选框来选择类型，可供选择的类型包括 Flash 程序和 SRAM 程序两种。

**Step5 - 保存 / 下载固件：** 固件下载界面 “Operation” 区域，通过点击 “Save As Binary” 按钮来保存固件，通过点击 “Download & Run” 按钮来下载固件。

(3) EMI 测试

**Step1 - 配置频点、功率和 RF 模式：** EMI 测试界面 “Setting” 区域，输入测试频点、选择 TX 功率（TX 测试需要）、选择 RF 模式。

**Step2 - TX 测试：** TX 测试包括两种 RF 类型的信号，分别是单载波信号和连续的调制信号，可通过 “TX Continue” 区域的 “Carrier” 和“CarrierData”按钮来分别设置，通过 “Packet Type” 可以设置数据包的类型。另外，连续的调制信号是支持跳频模式的，可通过勾选 “Hop” 来设置。

**Step3 - RX 测试：** 通过 “RX” 区域的 “RX Test” 按钮来控制 DUT 进入 RX 测试模式。

(4) 非信令测试

**Step1 - 配置频点、功率和 RF 模式：** 非信令测试界面 “Setting” 区域，输入测试频点、选择 TX 功率（TX 测试需要）、选择 RF 模式。

**Step2 - TX 测试：** 非信令测试界面 “TX Burst” 区域，通过 “Packet Count” 来选择连续的发包个数（仅支持单次发送 1000 个包数据和不限个数两种模式），通过 “Payload Len.” 来设置数据包长，通过 “Packet Type” 来选择数据包的类型，通过 “Duty Cycle” 来设置占空比,"Adaptive" 用来设置 TX burst 自适应测试。

**Step3 - RX 测试：** 通过 “RX” 区域的 “RX Test” 按钮来控制 DUT 进入 RX 测试模式，通过点击 “RX Count” 按钮来查看当前的收包数，通过点击 “RSSI” 按钮来查看 RF 信号源的功率。

(5) RF 电流测试

**Step1 - 下载 RF 电流测试所需的固件：** RF 电流测试界面 “Current Test Firmware” 区域，配置 MCU 内部供电方式，点击 “Download” 按钮来下载电流测试的固件（每次开始时需要对 DUT 进行下电上电操作）。

**Step2 - 进行 TX 电流测试：** RF 电流测试界面 “Current Test Operation” 区域，配置供电方式和功率以及频点，通过点击 “TX Current” 按钮来进入 TX 电流测试。

**Step3 - 进行 RX 电流测试：** RF 电流测试界面 “Current Test Operation” 区域，配置频点，通过点击 “RX Current” 按钮来进入 RX 电流测试。

### PA Configure Tool

#### 功能描述 （PA Configure Tool）

该工具主要用来配置生成 PA 工作所需的 Binary 文件。

#### 界面组成及使用说明 （PA Configure Tool）

该工具的界面如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/paconfigtoolui1.png)

**配置生成 PA 工作文件:**

**Step1 - 添加 PA 控制的 pin 脚：** 通过点击 “Add” 按钮来添加 PA 工作所需的 pin 脚。

**Step2 - 配置各 pin 脚在不同工作模式下的电平：** 分别配置 “Init”、“TX”、“RX” 以及 “Bypass” 模式下各 pin 脚的电平。

**Step3 - 生成 Binary 文件：** 通过点击 “Save As Binary” 按钮来将配置保存成 binary 文件。

### EVK Offline Tool

#### 功能描述 （EVK Offline Tool）

该工具用来配合带有离线下载功能的 BurningEVK 使用，主要功能包括：

*   更新 BurningEVK 中工具固件。
    
*   下载用户程序到 BurningEVK 中。
    

#### 界面组成及使用说明 （EVK Offline Tool）

该工具的界面包括工具固件界面和用户工具界面，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/evkofflinetoolui1.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/evkofflinetoolui2.png)

(1) 更新工具固件

**Step1 - 查看 BDT 中的工具固件：** 通过点击 “List all” 按钮来查看现有的工具固件。

**Step2 - 更新固件：** 通过点击 “Update” 按钮来更新工具固件到 BurningEVK 中。

**注意：**

工具固件界面默认是隐藏的，需要通过修改配置文件来显示。

(2) 下载用户固件

**Step1 - 添加用户固件：** 通过点击 “Add” 按钮来添加用户固件，并配置好 “Chip Name”、“Bin Name”、“Destination”、“Addr” 以及 “File Path” 等信息。

**Step2 - 下载用户固件：** 先将需要下载到 BurningEVK 中的固件勾选上，接着点击 “Download” 按钮来完成下载。

### Secure Boot Tool

该工具主要功能如下：

*   支持芯片配置信息以及固件下载。
    
*   支持重新使能 Debug 接口功能。
    
*   支持读取芯片配置信息。
    

#### 界面组成及使用说明

Secure Boot 工具界面如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SecureBootInterface.png)

(1) Mode Selection

选择 “secure boot mode” 或“normal mode”任意一种模式。

(2) Firmware Encryption

选择启用或禁用 “Firmware Encryption” 功能。

(3) Secure Debug

选择启用或禁用 “Secure Debug” 功能。

(4) Run Description Address

选择 Flash 容量，相应的代码描述地址将自动确认。

**注意：**

此功能仅在 “secure boot mode” 模式下使用。

(5) Pubkey Hash

选择待烧录的 “public_key_hash.bin” 文件。单击 “Download-All” 按钮后，程序会自动检查文件长度是否满足条件。若不满足条件，会进行报错提醒。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/PubkeyHashErr.png)

**注意：**

此功能仅在 “secure boot mode” 模式下使用。

(6) Root Key

输入框输入 16 个字符的字符串或 32 个十六进制字符的字符串作为根密钥，同时也支持选择文本文件导入密钥。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ImportRootKey.png)

输入 32 个十六进制字符的字符串示例：00112233445566778899aabbccddeeff 或 00112233445566778899AABBCCDDEEFF。

输入 16 个字符的字符串示例：tlk_key-1234abcd。

单击 “Download-All” 按钮后，程序会自动检查输入的字符串是否满足条件。若不满足条件，会进行报错提醒。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/RootKeyErr1.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/RootKeyErr2.png)

**注意：**

Firmware Encryption 或 Secure Debug 功能启用时才需设置 Root Key。

(7) Debug Plaintext

输入 16 个字符的字符串或 32 个十六进制字符的字符串作为根密钥，同时也支持选择文本文件导入密钥。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ImportDebugPlaintext.png)

输入 32 个十六进制字符的字符串示例：00112233445566778899aabbccddeeff 或 00112233445566778899AABBCCDDEEFF。

输入 16 个字符的字符串示例：tlk_key-1234abcd。

单击 “Download-All” 按钮后，程序会自动检查输入的字符串是否满足条件。若不满足条件，会进行报错提醒。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DebugPlaintextErr1.png)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DebugPlaintextErr2.png)

**注意：**

Secure Debug 功能启用时才需设置 Debug Plaintext。

(8) Run Code

勾选复选框，选择运行代码 0 或代码 1 以及运行代码地址，并导入固件路径。

(9) Run Code description

勾选复选框，选择运行代码描述文件路径并导入。

**注意：**

此功能仅在 “secure boot mode” 模式下使用。

(10) Download-All

“Setting”区域芯片配置信息下载到 eFuse 中。“Run Code”以及 “Run Code description” 区域选择的文件下载到 Flash 中。

**注意：**

Secure Debug 功能启用，点击 “Download-All” 按钮，无论下载是否成功都会在工具 config\sboot\key 路径下产生 Debug Key 文件。

(11) Download-Flash

“Run Code”以及 “Run Code description” 区域选择的文件下载到 Flash 中。

**注意：**

已烧录过 eFuse，只需要更新固件程序，点击 Download-Flash 按钮即可。

(12) Re-enable Debug-interface

“Secure Debug” 功能启用后，芯片 Debug 功能会被禁用。点击 “Re-enable Debug-interface” 按钮会弹出对话框。选择 Yes，使用默认文件夹中的 DebugKey.txt 文件作为 Debug Key 去恢复 Debug 功能。选择 No，需要手动导入文件作为 Debug Key 去恢复 Debug 功能。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Re-enableDebugInterface.png)

(13) Read-Info

读取芯片 eFuse 中配置信息，不包括 Root Key 以及 Debug Plaintext 中的信息。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ReadInfo.png)

(14) Save

保存界面配置信息，将 Root Key 以及 Debug Plaintext 中的信息保存到 config\sboot\key 路径。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/KeyFolder.png)

#### 常用安全机制组合和工具的使用步骤说明

Secure Boot、Firmware Encryption 以及 Secure Debug 安全机制可单独使用并且可以自由组合。然而，在实践中建议使用以下组合：

*   Option 0: Secure Boot + Secure Debug
    
*   Option 1: Firmware Encryption + Secure Debug
    
*   Option 2: Secure Boot + Firmware Encryption + Secure Debug
    

(1) Secure Boot + Secure Debug

**Step1：** “Mode Selection” 下拉框中选择 “secure boot mode”。

**Step2：** “Firmware Encryption” 下拉框中选择 “Disable”。

**Step3：** “Secure Debug” 下拉框中选择 “Enable”。

**Step4：** 根据芯片封装选择对应 Flash 容量。此处默认选择 “Flash：1M”。

**Step5：** “Run Code” 区域选择运行代码 0 或代码 1 以及运行代码地址，并导入固件路径。

**Step6：** 上一步骤完成后，“public_key_hash.bin”文件路径会自动导入到 “Pubkey Hash” 输入框中，若未成功，则手动导入。

**Step7：** “Run Code description” 区域导入运行代码描述文件路径。

**Step8：** 在 “Root Key” 以及 “Debug Plaintext” 输入框中输入密钥。

**Step9：** 点击 “Download-ALL” 按钮完成下载。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SecureBoot_SecureDebug.png)

(2) Firmware Encryption + Secure Debug

**Step1：** “Mode Selection” 下拉框中选择 “normal mode”。

**Step2：** “Firmware Encryption” 下拉框中选择 “Enable”。

**Step3：** “Secure Debug” 下拉框中选择 “Enable”。

**Step4：** 选择固件下载地址并导入固件路径。

**Step5：** 在 “Root Key” 以及 “Debug Plaintext” 输入框中输入密钥。

**Step6：** 点击 “Download-ALL” 按钮完成下载。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/FirmwareEncryption_SecureDebug.png)

#### Secure Boot + Firmware Encryption + Secure Debug

**Step1：** “Mode Selection” 下拉框中选择 “secure boot mode”。

**Step2：** “Firmware Encryption” 下拉框中选择 “Enable”。

**Step3：** “Secure Debug” 下拉框中选择 “Enable”。

**Step4：** 根据芯片封装选择对应 Flash 容量。此处默认选择 “Flash：1M”。

**Step5：** “Run Code” 区域选择运行代码 0 或代码 1 以及运行代码地址，并导入固件路径。

**Step6：** 上一步骤完成后，“public_key_hash.bin”文件路径会自动导入到 “Pubkey Hash” 输入框中，若未成功，则手动导入。

**Step7：** “Run Code description” 区域导入运行代码描述文件路径。

**Step8：** 在 “Root Key” 以及 “Debug Plaintext” 输入框中输入密钥。

**Step9：** 点击 “Download-ALL” 按钮完成下载。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SecureBoot_FirmwareEncryption_SecureDebug.png)

### Audio Tool

#### EQ Tool

(1) 功能描述 （EQ Tool）

该工具的主要功能如下：

*   生成 EQ 参数
*   进行在线 EQ 调参（需相关协议支持）

(2) 界面组成

EQ 工具的界面由 5 个区域构成，包括图表显示区域、滤波器参数区域、“Configuration” 区域、“Online Operation” 区域以及 log 输出区域，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/audioeqtoolui.jpg)

(3) 使用说明

**Step1 - EQ 参数调节：** 首先选择调参的模式，通过 “configuration” 区域下的 Mode 进行选择，工具默认提供三种可选模式，分别是：“Music”模式（即 Line Out），“MIC”模式（即 Line In），“SPK”模式（即 Line In to Line Out）。接着选择 EQ Group（最大支持 8 group）。接着选择 EQ 类型。最后配置各级参数，点击 “Add” 按键增加一级滤波器，点击 “Remove” 按键删除一级滤波器，分别通过滤波器参数区域下 Type、Q、FC 以及 dB 来配置包括滤波器类型、Q 值、中心频率以及增益值。通过点击 “Reset All Stage” 按键可以复原所有滤波器的参数。调节参数的同时，EQ 曲线也会进行相应的变化。图表右侧的 “Preattenuate” 拖动条代表预衰减值，可以通过拖动来调整整体 EQ 增益。

**Step2 - 查看和保存 EQ 参数值：** 通过点击 “configuration” 区域中的 “View Para” 按钮来查看参数值，通过点击 “Save Para” 按钮可以将生成的参数值保存成 txt 文件。

**Step3 - 保存和导入 EQ 配置：** 通过 “configuration” 区域中 “Save Setting” 按键可以将当前 EQ 参数配置保存为 bin 文件。通过点击 “Load Setting” 按键可以将保存的 EQ 配置 bin 文件还原至工具界面。

**Step4 - EQ 在线调参：** 首先选择在线调参的方式，通过 “Online Operation” 区域中的 “Port” 来选择在线调参的方式，当前支持 “USB_hid”、“usb_print”、“Uart”。如果选择 usb 方式，则需要在下方下拉框中选择对应的 usb 句柄；如果选择 Uart 方式，则需要在 Uart Tool 中选择对应的 COM 并点击“Open”。接着通过点击“Download” 按钮将 EQ 参数下载到设备中，点击 “Disable/Enable” 按键可以关闭 / 打开 EQ，点击 “Sync” 按键可以将设备的 EQ 参数同步到工具界面。

**注意：**

EQ 工具所支持的在线调参方式都需要有相关协议的支持，具体需咨询相关 FAE。

#### DRC Tool

(1) 功能描述 （DRC Tool）

该工具的主要功能如下：

*   生成 DRC 参数
*   进行在线 DRC 调参（需相关协议支持）

(2) 界面组成

DRC 工具的界面由 5 个区域构成，包括图表显示区域、参数配置界面、“Operation” 区域、“Online” 区域以及 log 输出区域，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/audiodrctoolui.jpg)

(3) 使用说明

**Step1 - DRC 参数调节：** 首先选择调参的类型，通过点击 “Noise Gate”、“Expander”、“Compressor” 或是 “Limiter” 区域下的 “Enable” 勾选框使能该工具，接着通过拖动条或者下方编辑框输入来调整 “Threshold”、“Width”、“Ratio” 和“Makeup”参数,，对应的 DRC 曲线也会进行相应的变化。通过编辑框可以修改 “Attack(ms)”、“Release(ms)”、“Hold(ms)” 和“Samples”值。

**Step2 - 查看和保存 DRC 参数值：** 通过点击 “Operation” 区域中的 “View Parameters” 按钮来查看参数值，通过点击 “Save Parameters” 按钮可以将生成的参数值保存成 txt 文件。

**Step3 - 保存和导入 DRC 配置：** 通过 “Operation” 区域中 “Save Setting” 按键可以将当前 DRC 参数配置保存为 bin 文件。通过点击 “Load Setting” 按键可以将保存的 DRC 配置 bin 文件还原至工具界面。

**Step4 - DRC 在线调参：** 首先选择在线调参的方式，通过 “Online” 区域中的 “Port” 来选择在线调参的方式，当前支持 “USB_hid”、“usb_print”、“Uart”。如果选择 usb 方式，则需要在下方下拉框中选择对应的 usb 句柄；如果选择 Uart 方式，则需要在 Uart Tool 中选择对应的 COM 并点击“Open”。接着通过点击“Download Parameter” 按钮将 DRC 参数下载到设备中。

**注意：**

DRC 工具所支持的在线调参方式都需要有相关协议的支持，具体需咨询相关 FAE。

#### ANC Tool

(1) 功能描述 （ANC Tool）

该工具的主要功能如下：

*   生成 ANC 参数
*   进行在线 ANC 调参（需相关协议支持）

(2) 界面组成

ANC 工具的界面由 6 个区域构成，包括图表显示区域、滤波器参数区域、“Configuration” 区域、“Online Operation” 区域、“Parameters” 区域以及 log 输出区域，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/audioanctoolui.jpg)

(3) 使用说明

**Step1 - ANC 参数调节：** 首先选择调参的模式，通过 “configuration” 区域下的 ALG 进行选择 “FF”、“Hybrid” 或者 “FB”。接着选择采样率 384k 或是 768k。接着选择通道 chan 和芯片 Chip。接着选择滤波器组“wz”、“cz0”、“cz1” 或是 “cz2”。可在右侧编辑框内设置该组可配置的最大滤波器阶数。最后配置各级参数，点击“Add” 按键增加一级滤波器，点击 “Remove” 按键删除一级滤波器，分别通过滤波器参数区域下 Type、Option、Opval、FC 以及 dB 来配置包括滤波器类型、Q 类型、Q 值、中心频率以及增益值。通过点击 “Reset All Stages” 按键可以复原所有滤波器的参数。调节参数的同时，ANC 曲线也会进行相应的变化。在 “Parameters” 区域可以对相关参数进行编辑。

**Step2 - 查看 ANC 参数值：** 通过点击 “configuration” 区域中的 “View Para” 按钮来查看参数值。

**Step3 - 保存和导入 ANC 配置：** 通过 “configuration” 区域中 “Save Setting” 按键可以将当前 ANC 参数配置保存为 bin 文件。通过点击 “Load Setting” 按键可以将保存的 ANC 配置 bin 文件还原至工具界面。

**Step4 - ANC 在线调参：** 首先选择在线调参的方式，通过 “Online Operation” 区域中的 “Port” 来选择在线调参的方式，当前支持 “USB_hid”、“usb_print”、“Uart”。如果选择 usb 方式，则需要在下方下拉框中选择对应的 usb 句柄；如果选择 Uart 方式，则需要在 Uart Tool 中选择对应的 COM 并点击“Open”。接着通过点击“Parameters” 按钮将 “Parameters” 区域中的参数下载到设备中，点击 “IIR” 可以将当前滤波器组的参数下发到设备，点击 “FIR” 并选择 FIR 的 txt 文件，可以将 FIR 配置下发到设备，点击 “Sync” 按键可以把设备中的滤波器组阶数同步到工具界面。

**注意：**

ANC 工具所支持的在线调参方式都需要有相关协议的支持，具体需咨询相关 FAE。

### 9118 EMI Tool

#### 功能描述 （9118 EMI Tool）

该工具有两个主要的功能：

*   配置和下载测试固件。
    
*   进行 EMI 测试。
    
*   进行用户指令测试。
    

#### 界面组成及使用说明 （9118 EMI Tool）

该工具主要由固件配置下载界面、EMI 测试界面、发送用户指令测试界面三个部分组成，具体如下图所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/9118emitoolui1.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/9118emitoolui2.jpg)

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/9118emitoolui3.jpg)

(1) 芯片的选择

通过 BDT 主界面 MCU 列表来选择 9118。

(2) 固件配置和下载

**Step1 - 配置固件：** 固件下载界面，在 “Address(H)” 下的编辑框可以配置固件下载的地址，点击 "open" 下的文档按键可以选择固件，选择后会在 “File Path” 下刷新固件所在路径，并自动勾选当前行的 “EN” 使能框。如果不需要下载某一个固件，取消勾选 “EN” 即可。

**Step2 - 选择串口和波特率：** 点击 “Operation” 下的 COM 下拉框选择串口，点击 Baudrate 下拉框配置固件下载时的速率。

**Step3 - 擦除 / 下载固件：** 配置好 Step2 后，点击 “Erase” 即可擦除固件，点击 “Download” 即可下载配置好的多个固件。

**Step4 - MAC 读写：** 点击 “BLE MAC” 或“WIFI MAC”后的 “Read” 下拉框可以切换读写 MAC 指令，通过点击 Start 按键可以执行 MAC 读写指令。

**注意：**

需要在固件下载前确认串口驱动成功，或者点击 Install Uart driver X64(X86) 进行驱动安装。

(3) EMI 测试

**Step1 - 配置串口和波特率：** EMI 测试界面 “Uart Setting” 区域，选择串口和波特率后，点击 "open" 按键即打开串口。

**Step2 - 配置 RF 模式、速率、频点、带宽等：** EMI 测试界面，可在对应的下拉框中选择需要测试的 RF 模式、速率、频点、带宽等。

**Step3 - TX 测试：** TX 测试包括两种 RF 类型的信号，分别是单载波信号和连续的调制信号，可通过 “TX” 区域的 “Carrier” 和“CarrierData”按钮来分别设置，通过 “TX Stop” 可停止 TX 测试。

**Step4 - RX 测试：** 通过 “RX” 区域的 “RX Test” 按钮来控制 DUT 进入 RX 测试模式，点击 “RX Count” 可查看收到的数据包数量，通过 “RX Stop” 可停止 RX 测试。

(4) 用户指令测试

**Step1 - 配置串口和波特率：** EMI 测试界面 “Uart Setting” 区域，选择串口和波特率后，点击 "open" 按键即打开串口。

**Step2 - 指令输入：** 在 “User Data Area” 框内可以输入相关测试指令，支持的指令需要咨询相关 FAE。

**Step3 - 指令发送：** 通过点击 “Send” 按键，即可发送测试指令。

## 命令行操作指南

### 下载固件

#### 通过 “USB” 模式将固件下载到 “FLASH” 中

在使用 “USB” 模式下载或调试 MCU 之前，请确保指定的 MCU 支持 USB 功能，并且其 USB 功能可用。用户可以输入相应的命令，通过 “USB” 模式将固件下载到目标板的特定 flash 空间。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 wf 0 –i C:\Users\Admin\Desktop\bin\Telink.bin -u

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “wf” (写入 flash)
    
*   参数 4：用于存储要下载的目标固件的起始地址 – “0”
    
*   参数 5：可选命令 – “-i” (跟随固件路径)
    
*   参数 6：固件路径 – “C:\Users\Admin\Desktop\bin\Telink.bin”
    
*   参数 7：可选命令 – “-u”(与目标板的通信模式: “USB” 模式)
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadFWinUSBmode.png)

将固件下载到目标板后，用户可以进入相应的命令行，直接复位 MCU，而无需重启目标板。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 rst –u –f

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “rst” (复位)
    
*   参数 4：可选命令 – “-u”(与目标板的通信模式: “USB” 模式)
    
*   参数 5：可选命令 – “-f” (Flash, “-c”: CORE)
    

如果将固件下载到 FLASH，应该选择 “-f” 复位 MCU。

如果将固件下载到 SRAM，应该选择 “-c” 复位 MCU。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ResetMCU.png)

#### 通过 “EVK” 模式将固件下载到 “FLASH” 中

在使用 “EVK” 模式下载固件之前，请确保目标板通过 “Burning EVK” 方法连接到电脑，并且目标板的单线通信已建立。用户可以输入相应的命令，通过 “Burning EVK” 模式将固件下载到目标板的特定 flash 空间。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 wf 0 –i C:\Users\Admin\Desktop\bin\Telink.bin

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “wf” (写入 flash)
    
*   参数 4：用于存储要下载的目标固件的起始地址 – “0”
    
*   参数 5：可选命令 – “-i” (跟随固件路径)
    
*   参数 6：固件路径 – “C:\Users\Admin\Desktop\bin\Telink.bin”
    

由于命令行中不包含可选命令 “-u”，因此选择与目标板使用 “EVK” 通信模式。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadFWinEVKmode.png)

将固件下载到目标板后，用户可以进入相应的命令行，直接复位 MCU，而无需重启目标板。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 rst –f

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “rst” (复位)
    
*   参数 4：可选命令 – “-f” (Flash, “-c”: CORE)
    

如果将固件下载到 FLASH，应该选择 “-f” 复位 MCU。

如果将固件下载到 SRAM，应该选择 “-c” 复位 MCU。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ResetMCUforDownloadingFirmware.png)

#### 将固件下载到 “SRAM” 或 “OTP” 中

用户可以将固件下载到 “SRAM” / “OTP” 而不是 Flash 中。用户可以输入相应的命令行，通过 “USB” 模式将固件下载到目标板的特定 “SRAM” 或 “OTP” 空间。在使用这种方法下载固件之前，用户应该知道特定 MCU 的 “SRAM” 起始地址，例如：B92_3V3：0xc0000000。

**将固件下载到 SRAM 的命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 wc c0000000 –i C:\Users\Admin\Desktop\bin\Telink.bin

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “wc” (写入 CORE，包括数字寄存器和 SRAM)
    
*   参数 4：用于存储要下载的目标固件的起始地址 – “c0000000”
    
*   参数 5：可选命令 – “-i” (跟随固件路径)
    
*   参数 6：固件路径 – “C:\Users\Admin\Desktop\bin\Telink.bin”
    

由于命令行中不包含可选命令 “-u”，因此选择与目标板使用 “EVK” 通信模式。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DownloadFWintoSRAMviaEVKmode.png)

**将固件下载到 OTP 的命令行示例（如果目标板支持 OTP）：**

./Cmd_download_tool.exe 8368 1 wo 0 –i C:\Users\Admin\Desktop\bin\Telink.bin

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – 8368
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “wo” (写入 OTP)
    
*   参数 4：用于存储要下载的目标固件的起始地址 – “0”
    
*   参数 5：可选命令 – “-i” (跟随固件路径)
    
*   参数 6：固件路径 – “C:\Users\Admin\Desktop\bin\Telink.bin”
    

由于命令行中不包含可选命令 “-u”，因此选择与目标板使用 “EVK” 通信模式。

### Reset MCU

将固件下载到目标板后，用户可以复位 MCU，使新下载的程序运行，而无需重启目标板。

**复位 MCU 的命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 rst -f

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “rst”
    
*   参数 4：可选命令 – “-f”
    

将固件下载到目标板的 flash 或 OTP 后，用户应使用可选命令 “-f” 复位 MCU。

将固件下载到目标板的 SRAM 后，用户应使用可选命令 “-c” 复位 MCU。

由于命令行中不包含可选命令 “-u”，因此选择与目标板使用 “EVK” 通信模式。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ResetMCUforDownloadingFirmware.png)

### 擦除 Flash 扇区

“擦除 Flash 扇区” 功能用于以扇区（4kB）为单位从特定地址开始擦除特定 flash 空间。

例如，要擦除从地址 0x004000 开始的 B92_3V3 的 64kB 闪存空间，用户可以输入下面的命令行。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 wf 4000 –s 64k –e

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “wf” (写入 flash)
    
*   参数 4：要擦除的空间起始地址 – “4000”
    
*   参数 5：可选命令 – “-s” (跟随要删除的扇区大小)
    
*   参数 6：要删除的扇区大小 – “64k”
    
*   参数 7：可选命令 – “-e” (擦除 flash)
    

由于命令行中不包含可选命令 “-u”，因此选择与目标板使用 “EVK” 通信模式。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/EraseflashspaceviaEVKmode.png)

### Flash 保护

对 Flash 特定地址区域进行数据保护。通过对 Flash 进行数据保护，可防止 Flash 被意外擦除或编程。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 lf 0 512

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 – “lf”
    
*   参数 4：Flash 受保护区域起始地址
    
*   参数 5：保护区域大小（单位：KB）
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DataProtection.png)

### Flash 解除保护

Flash 被保护，需要解除保护后才能对其进行擦除或编程。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 lf 0 0

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 – “lf”
    
*   参数 4：固定为 0
    
*   参数 5：固定为 0
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/RemoveProtection.png)

### Activate MCU

“与目标板通信失败时激活 MCU” 功能仅适用于 “Burning EVK” 与 “EVK” 模式下目标板之间的 Swire 连接，即不支持 “USB” 模式或 “Burning EVK” 与 “EVK” 模式下目标板之间的 USB 连接。

当固件烧录失败时，请确保目标板通过 Swire 与 “Burning EVK” 连接。用户可以输入相应的命令行来启用该功能，以激活 MCU。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 ac

**参数：**

*   参数 1：设备 ID (详见章节[支持多设备](#支持多设备)) – 1 (只有一个设备)
    
*   参数 2：MCU 类型 – B92_3V3
    
*   参数 3：操作命令 (详见章节[命令列表](#命令列表)) – “ac” (Activate MCU)
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ActivateMCU1.png)

### Debug

MCU 开始运行后，用户可以使用此工具访问内存空间（FLASH/CORE/ANALOG/OTP）。

#### 读取数据

从特定内存空间（FLASH/CORE/ANALOG/OTP）读取数据，用户可以输入相应的命令行。

**命令行示例：**

*   读取 flash: ./Cmd_download_tool.exe 1 B92_3V3 rf 0 –s 16
    
*   读取 core(digital register/SRAM): ./Cmd_download_tool.exe 1 B92_3V3 rc 0 –s 16
    
*   读取 analog register : ./Cmd_download_tool.exe 1 B92_3V3 ra 0 –s 16
    
*   读取 OTP: ./Cmd_download_tool.exe 1 B92_3V3 ro 0 –s 16
    

注意，最大的读取大小是 1MB，详见章节[命令列表](#命令列表)。

当读取大于 1024 字节的内存空间时，数据将被保存到一个文件中，默认名称为 “/user/read.bin”。下面的命令行可用于自定义文件名。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 rc 40000 –s 8k –o C:\Users\Admin\Desktop\bin\Telink_read.bin

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/ReadData.png)

#### 写入数据

用户可以输入相应的命令行，将数据写入特定的内存空间。

**命令行示例：**

*   写入 flash: ./Cmd_download_tool.exe 1 B92_3V3 wf 0 11 22 33 44 –s 4
    
*   写入 core(digital register/sram): ./Cmd_download_tool.exe 1 B92_3V3 wc 40000 11 22 33 44 –s 4
    
*   写入 analog register : ./Cmd_download_tool.exe 1 B92_3V3 wa 34 11 22 33 44 –s 4
    
*   写入 otp: ./Cmd_download_tool.exe 1 8368 wo 0 11 22 33 44 –s 4
    

注意，最大的操作大小是 256 字节，详见章节[命令列表](#命令列表)。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/WriteData.png)

#### Trace PC

用户可以输入相应的命令行来读取 "PC"。

Command line example: ./Cmd_download_tool.exe 1 B92_3V3 pc

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/TracePC.png)

如果想要获得更多的详细信息，则需要提供与固件匹配的 “.lst” 文件。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 pc –i C:\Users\Admin\Desktop\bin\Telink.lst

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/TracePCwithlstfile.png)

### 单线同步

在设置单线同步速度之前，请确保以下各项：

1) 电源正常；

2) MCU 未处于 “低功耗” 模式；

3) MCU 的单线功能可用；

4) 系统时钟正常。

和目标板之间无法建立连接时，用户可以通过输入相应的命令行，尝试设置 Swire（单线）同步速度来改善通信。

**注意：**

Swire 寄存器地址可能会因不同的芯片类型而变化。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 sws b0 10 b0 10

*   Swire 命令：sws
    
*   主设备基址：0xb0
    
*   主设备速度：0x10
    
*   从设备基址：0xb0
    
*   从设备速度：0x10
    

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/SetSwiresynchronizationspeed1.png)

在将固件下载到目标板或调试 MCU 之前，建议每次打开 MCU 电源时，用户执行一次 Swire 同步，以检查与目标板的通信是否正常。

如果与目标板的通信状态错误，用户可以按照前面提到的方法解决问题。

### Windows 日志

该工具支持 USB 打印功能，因此具有 USB 功能的 MCU 可以使用 USB 打印功能在 PC 端的 windows 日志中输出信息。

**命令行示例：**

./Cmd_download_tool.exe 1 B92_3V3 log usb 1 –u

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/usblogwindows.png)

按 “Esc” 退出 windows 日志。

### 命令列表

通过输入下面的命令行，会出现一个列表来显示所有支持的命令行。

**显示命令列表的命令行：**  
./Cmd_download_tool.exe help

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/Commandline1.png)

### 支持多设备

通过输入下面的命令行，设备列表将显示所有可用的 USB 设备。用户可以根据自己的需求选择设备 ID，并访问指定的设备。

**显示命令列表的命令行：**

./Cmd_download_tool.exe all

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/DeviceID.png)

用户可以按设备 ID 访问不同的设备，如下所示。

![](https://doc.telink-semi.cn/doc/zh/software/res/tools/bdt_wins/pic/AccessDifferentDevice.png)