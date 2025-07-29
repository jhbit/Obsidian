---
url: https://blog.csdn.net/libin55/article/details/118367509
title: 泰凌微 TLSR825X 开发一蓝牙通信实例_telink wiki 蓝牙射频测试 - CSDN 博客
date: 2025-07-17 14:21:43
tag: 
banner: "https://images.unsplash.com/photo-1750432215919-228924d7ae9c?crop=entropy&cs=srgb&fm=jpg&ixid=M3w0Njc1ODd8MHwxfHJhbmRvbXx8fHx8fHwxfHwxNzUyNzMxNzgzfA&ixlib=rb-4.1.0&q=85&fit=crop&w=1080&max-h=540"
banner_icon: 🔖
---
##### 背景

泰凌微蓝牙方案在消费类产品中近两年才火起来，实际网上也没有太多资料，芯片缺货的情况下作为替代方案还是可行的，手上有块 TLSR8258 的开发板，也就边看文档调试边记录  
这里采用 8258 的方案在调，其实 825X 系列仅内部资源不一样（价格高低），实际选型的时候根据产品定位来选择合适的型号

<table><thead><tr><th>型号</th><th>flash</th><th>sram</th></tr></thead><tbody><tr><td>8251</td><td>512kB</td><td>32kB</td></tr><tr><td>8253</td><td>512kB</td><td>48kB</td></tr><tr><td>8258</td><td>512kB</td><td>64kB</td></tr></tbody></table>

`如有异议，欢迎指正，转载请注明出处`

##### 资源及 SDK 下载

###### 特性

*   BLE5.0；支持 Telink Mesh(私有)
*   Flash 512Kb Ram64Kb(TLSR8258)
*   1.8V~3.6V
*   5.3mA Rxfullchip;
*   4.8mA Tx 0dbm_fullchip;
*   <1uA sleep+sram 0.4uA sleep
*   Tx Max +10dBm
*   工作温度 - 40℃~+85℃(工业级)

###### 架构图

![](https://i-blog.csdnimg.cn/blog_migrate/42ce74847774c622bd2f612bcb935b66.png#pic_center)

###### [SDK 下载](http://wiki.telink-semi.cn/tools_and_sdk/BLE/825x_BLE_SDK.zip)

*   这里可以根据实际的应用来选择 SDK，bz 为了兼容其他相同产品线的方案选择了`Single Connection`的 SDK  
    
    ![](https://i-blog.csdnimg.cn/blog_migrate/10e85fe048209f3b14641e2f25530b47.png#pic_center)
    

[**IDE 安装烧录可以查看 Mesh 博文**](https://blog.csdn.net/libin55/article/details/113137462)

##### SDK 工程

###### 文件结构

工程导入 Eclipse 后的文件结构如下  

![](https://i-blog.csdnimg.cn/blog_migrate/d5c4f95e536b370c33e7c274d2d059ad.png#pic_center)

*   **application**：提供了通用的应用处理程序，主要为打印 print、USB、按键 keyboard、音频 audio
*   **boot**：提供芯片的 software bootloader，即 MCU 上电启动或 deepsleep 唤醒后的汇编处理过程，为后面 C 语言程序的运行搭建好环境（中断向量、堆栈配置）
*   **common**：提供通用的跨平台处理，如标准 C 库的字符串、内存处理函数等
*   **drivers**：提供与 MCU 外设驱动程序
*   **proj_lib**：内部为泰凌微蓝牙协议栈库文件`liblt_8258.a`包括 RF 射频、PM 低功耗等库，这部分对开发用户不开放
*   **stack**：协议栈相关调用的头文件
*   **vendor**：用于存放用户应用层代码，目前支持应用有:
    *   **8258_ble_remote**：遥控应用，配合 IR 模块
    *   **8258_ble_sample**：是 remote 的简化应用，与标准的 ios、android 连接配对
    *   **8258_hci**：提供了基于 USB/UART 的 HCI，和其他 host 通信，组成完整的 ble slave 系统
    *   **8258_module**：蓝牙串口透传模块的应用
    *   **8258_master_kma_dongle**：dongle 的应用代码，是 ble master 的例程
    *   **8258_driver_test**：外设的测试应用
    *   **8258_feature_test**：蓝牙射频相关的测试应用

##### 实例

###### 代码讲解

###### 主函数

这里使用 **8258_ble_sample** 实例，先查看 main.c 中入口函数

*   变量`deepRetWakeUp`来判断系统是否为休眠唤醒，来实现系统快速初始化
*   中断`irq_enable`使能后协议栈开始运行
*   `user_init_normal`为 ble 系统初始化

```
_attribute_ram_code_ int main (void)    //让main运行在ram中，加快加载时间
{
    DBG_CHN0_LOW;   //debug 配合示波器调试使用
    blc_pm_select_internal_32k_crystal();//选择内部32k rc时钟
    cpu_wakeup_init();//硬件初始化, system timer计数器开始工作
    int deepRetWakeUp = pm_is_MCU_deepRetentionWakeup();  //判断唤醒源 1 - deepsleep retention唤醒 0 poweron/deepsleep
    rf_drv_init(RF_MODE_BLE_1M);//1M 通信带宽
    gpio_init( !deepRetWakeUp );  //快速初始化IO
#if (CLOCK_SYS_CLOCK_HZ == 16000000)//选择系统时钟频率，默认16M
    clock_init(SYS_CLK_16M_Crystal);
#elif (CLOCK_SYS_CLOCK_HZ == 24000000)
    clock_init(SYS_CLK_24M_Crystal);
#elif (CLOCK_SYS_CLOCK_HZ == 32000000)
    clock_init(SYS_CLK_32M_Crystal);
#elif (CLOCK_SYS_CLOCK_HZ == 48000000)
    clock_init(SYS_CLK_48M_Crystal);
#endif
    if(!deepRetWakeUp){
        blc_readFlashSize_autoConfigCustomFlashSector();//读取片上flash配置
    }
    blc_app_loadCustomizedParameters();  //加载参数
    if( deepRetWakeUp ){
        user_init_deepRetn (); //休眠唤醒后的快速初始化
    }
    else{
        user_init_normal ();//ble系统初始化
    }
    irq_enable();//开启中断
    while (1) {
#if (MODULE_WATCHDOG_ENABLE)
        wd_clear(); //clear watch dog
#endif
        main_loop ();//主循环任务，ble收发、低功耗
    }
}

```

###### 蓝牙配置

在 **app.c** 文件中主要为 gap 相关配置

*   **修改广播周期**

```
#define     MY_APP_ADV_CHANNEL                  BLT_ENABLE_ADV_ALL//全通道 37 38 39
#define     MY_ADV_INTERVAL_MIN                 ADV_INTERVAL_30MS//30ms
#define     MY_ADV_INTERVAL_MAX                 ADV_INTERVAL_35MS//35ms

```

*   **蓝牙广播**：修改广播报文与扫描应答报文

```
//////////////////////////////////////////////////////////////////////////////
//   Adv Packet, Response Packet
//////////////////////////////////////////////////////////////////////////////
const u8    tbl_advData[] = {
     0x05, 0x09, 'k', 'H', 'I', 'D',                //广播local name
     0x02, 0x01, 0x05,                          // BLE limited discoverable mode and BR/EDR not supported
     0x03, 0x19, 0x80, 0x01,                    // 384, Generic Remote Control, Generic category
     0x05, 0x02, 0x12, 0x18, 0x0F, 0x18,        // incomplete list of service class UUIDs (0x1812, 0x180F)
};
const u8    tbl_scanRsp [] = {
         0x08, 0x09, 'k', 'S', 'a', 'm', 'p', 'l', 'e',
    };

```

*   **连接参数**：修改连接间隔

```
void task_connect (u8 e, u8 *p, int n)
{
//  bls_l2cap_requestConnParamUpdate (8, 8, 19, 200);  // 200mS
    bls_l2cap_requestConnParamUpdate (8, 8, 99, 400);  // 1 S
//  bls_l2cap_requestConnParamUpdate (8, 8, 149, 600);  // 1.5 S
//  bls_l2cap_requestConnParamUpdate (8, 8, 199, 800);  // 2 S
//  bls_l2cap_requestConnParamUpdate (8, 8, 249, 800);  // 2.5 S
//  bls_l2cap_requestConnParamUpdate (8, 8, 299, 800);  // 3 S
    latest_user_event_tick = clock_time();
    device_in_connection_state = 1;//
    interval_update_tick = clock_time() | 1; //none zero
}

```

*   **调整发射功率**

```
#define     MY_RF_POWER_INDEX                   RF_POWER_P3p01dBm

```

###### 主任务

在 main_loop 中运行了主要的应用任务

*   **blt_sdk_main_loop**：必须被周期性调用，内部执行了 BLE 数据解析与逻辑处理
*   **blt_pm_proc**：低功耗处理接口，通过宏`BLE_APP_PM_ENABLE`来配置使能
*   **blt_pm_proc**：蓝牙广播与连接通信时的低功耗，包括超时 60sec 进入 deepsleep，后续在低功耗调试里面展开讲解

```
void main_loop (void)
{
    ////////////////////////////////////// BLE entry /////////////////////////////////
    blt_sdk_main_loop(); //ble数据与逻辑处理
    ////////////////////////////////////// UI entry /////////////////////////////////
#if (!TEST_CONN_CURRENT_ENABLE) //demo板子上的按键，可在头文件使能
    #if (SAMPLE_BOARD_SELECT == EVK_C1T139A30_V1P2)
    proc_keyboard (0, 0, 0);//按键处理
    #elif (SAMPLE_BOARD_SELECT == DONGLE_C1T139A3_V2P0A)
    // process button 1 second later after power on, to avoid power unstable
    if(!button_detect_en && clock_time_exceed(0, 1000000)){
        button_detect_en = 1;
    }
    if(button_detect_en && clock_time_exceed(button_detect_tick, 5000))
    {
        button_detect_tick = clock_time();
        proc_button(0, 0, 0);
    }
    #endif
#endif
    ////////////////////////////////////// PM Process /////////////////////////////////
    blt_pm_proc(); //pm低功耗，在头文件中配置
}

```

###### 运行测试

*   在 vendor 目录下 mesh 工程进行编译，在 8258_ble_sample 目录下生成 8258_ble_sample.bin 的固件，并通过 BDT 工具烧录固件  
    
    ![](https://i-blog.csdnimg.cn/blog_migrate/10602fddc50e72bd9a48185c95091ce4.png#pic_center)
    
*   打开 app 可以扫描到名称为 **ksample** 的设备，其中 **kHID** 是广播名称  
    
    ![](https://i-blog.csdnimg.cn/blog_migrate/3559f645285cbf8aa1088cc684b065d3.png#pic_center)
    
*   连接后可查看到支持的服务，其中 ota 是泰凌微私有定义的，所以 app 显示为未知服务；由于支持了 HID 的服务，可以使用带蓝牙的 PC 来连接设备  
    
    ![](https://i-blog.csdnimg.cn/blog_migrate/d59ad36bdcfe5d4b41bdfe6350e34bec.png#pic_center)