
```
1. 家族前缀  
    • TL → Telink 品牌缩写  
    • 后续字母/数字 → 工艺或无线协议定位  
    ‑ TLSR = 2.4 GHz BLE/2.4 GHz Proprietary/Zigbee/Thread 多协议  
    ‑ TL721x = 新一代 22 nm AIoT 低功耗 BLE/802.15.4 系列
    
2. 功能/工艺代号（第 4-5 位）  
    • 8 = 55 nm 工艺  
    • 9 = 22 nm 工艺  
    • 2 = 早期 40 nm 工艺  
    例：TLSR**8**25x、TLSR**9**21x、TL721x。
    
3. 容量与版本（中段数字）  
    • 25x：512 kB Flash  
    • 26x：1 MB Flash  
    • 27x：2 MB Flash  
    例：TLSR8258（512 kB）、TLSR8269（1 MB）、TLSR8278（2 MB）。
    
4. 封装代码（后缀 1-2 字符）  
    • E = QFN32 5 mm×5 mm  
    • F = QFN48 6 mm×6 mm  
    • T = TSSOP20  
    • G = WLCSP  
    例：TLSR8258**E**T32、TLSR9218**F**48。
    
5. 温度/版本码（末尾字母/数字）  
    • 无字母：商业级 0 ~ 70 °C  
    • I：工业级 ‑40 ~ 105 °C  
    • 末尾数字：批次或固件版本号（如 TLSR8258**E**T32 中的 “32” 表示 32-pin QFN）。
```

| Price | Part Number              | Status | Type   | Protocol                                                                                                        | MCU           | RAM (KB) | Flash (KB) | Supply Voltage              | Debug Interface | Package and Size | MSL  | MOQ(pcs) | OTP (KB) | I2C | I2S | Temperature    | SPI (M/S) | DSPI (M/S) | SPI (S) | Ext Flash | QSPI (M/S) | UART | GPIO | USB | QDEC | PWM | IR Learning | 7816 | PTA Interface | ADC | Audio Output | AMIC | DMIC |
| ----- | ------------------------ | ------ | ------ | --------------------------------------------------------------------------------------------------------------- | ------------- | -------- | ---------- | --------------------------- | --------------- | ---------------- | ---- | -------- | -------- | --- | --- | -------------- | --------- | ---------- | ------- | --------- | ---------- | ---- | ---- | --- | ---- | --- | ----------- | ---- | ------------- | --- | ------------ | ---- | ---- |
|       | ML7218A-GAIA-M0-PE11     | MP     | Module | 2.4GHz Proprietary,Bluetooth LE 6.0,Bluetooth Mesh,Matter,Thread                                                | RISC-V 32-bit | 512      | 2048       | 1.8V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE,JTAG      | 18x35.3x2.6mm    | MSL3 | 1        | 8        | 2   | 3   | -40°C ~ +85°C  | 4         | 3          | 1       | 0         | 3          | 3    | 48   | 1   | 1    | 7   | 1           | 1    | 1             | 12  | 2            | 2    | 2    |
|       | ML7218D1-MERCURY-M0-PE11 | MP     | Module | 2.4GHz Proprietary,Bluetooth LE 6.0,Bluetooth Mesh,Matter,Thread                                                | RISC-V 32-bit | 512      | 2048       | 1.8V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE,JTAG      | 11.3x26x2.6mm    | MSL3 | 1        | 8        | 2   | 3   | -40°C ~ +85°C  | 4         | 3          | 1       | 0         | 3          | 3    | 20   | 1   | 1    | 7   | 0           | 1    | 1             | 12  | 2            | 2    | 2    |
|       | ML3219D-MERCURY-M0-PE11  | MP     | Module | 2.4GHz Proprietary,Bluetooth LE 5.4,Bluetooth Mesh,Matter,Thread                                                | RISC-V 32-bit | 128      | 2048       | 1.8V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE           | 11.3x26x2.6mm    | MSL3 | 1        | 0        | 2   | 1   | -40°C ~ +125°C | 3         | 2          | 1       | 0         | 2          | 3    | 24   | 1   | 1    | 6   | 1           | 1    | 1             | 12  | 2            | 1    | 1    |
|       | TLSR9527B                | MP     | SoC    | 2.4GHz Proprietary,Bluetooth Classic,Bluetooth LE 6.0,Bluetooth Mesh                                            | RISC-V 32-bit | 512      | 2048       | 2.7V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE           | QFN40 6x4mm      | MSL3 | 15000    | 0        | 2   | 2   | -40°C ~ +85°C  | 2         | 2          | 1       | 1         | 2          | 2    | 13   | 1   | 1    | 6   | 0           | 1    | 1             | 14  | 2            | 2    | 4    |
|       | TLSR9527C                | MP     | SoC    | 2.4GHz Proprietary,Bluetooth Classic,Bluetooth LE 6.0,Bluetooth Mesh                                            | RISC-V 32-bit | 512      | 2048       | 2.7V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE,JTAG,SDP  | QFN56 7x7mm      | MSL3 | 15000    | 0        | 2   | 2   | -40°C ~ +85°C  | 2         | 2          | 1       | 1         | 2          | 2    | 30   | 1   | 1    | 6   | 0           | 1    | 1             | 14  | 2            | 2    | 4    |
|       | TLSR9228H                | MP     | SoC    | 2.4GHz Proprietary,Apple HomeKit,Bluetooth LE 6.0,Bluetooth Mesh,Matter,RF4CE,Thread,Zigbee 3.0                 | RISC-V 32-bit | 512      | 2048       | 1.9V ~ 4.3V                 | SWIRE,JTAG,SDP  | QFN48 6x6mm      | MSL3 | 15000    | 0        | 2   | 0   | -40°C ~ +125°C | 2         | 2          | 1       | 1         | 2          | 2    | 30   | 1   | 1    | 6   | 0           | 1    | 1             | 14  | 0            | 0    | 0    |
|       | TLSR9218A                | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple Find-My,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Thread,Zigbee 3.0 | RISC-V 32-bit | 256      | 1024       | 1.8V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE,JTAG,SDP  | QFN48 6x6mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 0         | 1          | 0       | 0         | 1          | 2    | 26   | 1   | 0    | 6   | 0           | 0    | 1             | 14  | 1            | 1    | 2    |
|       | TLSR9215A                | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Thread,Zigbee 3.0               | RISC-V 32-bit | 256      | 0          | 2.7V ~ 4.3V,USB 4.5V ~ 5.5V | SWIRE,JTAG      | QFN48 6x6mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 0         | 1          | 1       | 1         | 1          | 2    | 28   | 1   | 0    | 6   | 0           | 0    | 1             | 14  | 0            | 0    | 2    |
|       | TLSR8277F512EL40         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Zigbee 3.0                                    | T-MCU 32-bit  | 64       | 512        | 3v~3.6v                     | SWIRE           | LGA40 4x6mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 25   | 1   | 1    | 6   | 1           | 1    | 1             | 14  | 1            | 1    | 0    |
|       | TLSR8278F1KET48          | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh,Zigbee 3.0                        | T-MCU 32-bit  | 64       | 1024       | 1.8V ~ 3.6V,USB 4.5V ~ 5.5V | SWIRE           | QFN48 7x7mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 32   | 1   | 1    | 6   | 1           | 1    | 1             | 14  | 2            | 1    | 1    |
|       | TLSR8273F512ET48         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh                                   | T-MCU 32-bit  | 64       | 512        | 1.8V ~ 3.6V,USB 4.5V ~ 5.5V | SWIRE           | QFN48 7x7mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 32   | 1   | 1    | 6   | 1           | 1    | 1             | 14  | 2            | 1    | 1    |
|       | TLSR8273F512ET32         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE                                               | T-MCU 32-bit  | 64       | 512        | 1.8V ~ 3.6V                 | SWIRE           | QFN32 4x4mm      | MSL3 | 15000    | 0        | 1   | 0   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 12   | 0   | 0    | 0   | 0           | 0    | 0             | 14  | 0            | 0    | 0    |
|       | TLSR8258F1KET48A         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Zigbee 3.0                      | T-MCU 32-bit  | 64       | 1024       | 1.8V ~ 3.6V                 | SWIRE           | TQFN48 7x7mm     | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 32   | 1   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8258F512ET48         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh,Zigbee 3.0          | T-MCU 32-bit  | 64       | 512        | 1.8V ~ 3.6V                 | SWIRE           | QFN48 7x7mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 32   | 1   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8258F1KAT32          | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh,Zigbee 3.0          | T-MCU 32-bit  | 64       | 1024       | 1.8V ~ 3.6V                 | SWIRE           | QFN32 5x5mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +125°C | 1         | 0          | 0       | 0         | 0          | 1    | 17   | 0   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8258F1KET32          | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh,Zigbee 3.0          | T-MCU 32-bit  | 64       | 1024       | 1.8V ~ 3.6V                 | SWIRE           | QFN32 5x5mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 17   | 0   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8258F512ET32         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Apple HomeKit,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh,Zigbee 3.0          | T-MCU 32-bit  | 64       | 512        | 1.8V ~ 3.6V                 | SWIRE           | QFN32 5x5mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 17   | 0   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8253F512ET32         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh                                   | T-MCU 32-bit  | 48       | 512        | 1.8V ~ 3.6V                 | SWIRE           | QFN32 5x5mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +85°C  | 1         | 0          | 0       | 0         | 0          | 1    | 17   | 0   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |
|       | TLSR8253F512AT32         | MP     | SoC    | 2.4GHz Proprietary,802.15.4,Bluetooth LE 5.4,Bluetooth Mesh,RF4CE,Telink Mesh                                   | T-MCU 32-bit  | 48       | 512        | 1.8V ~ 3.6V                 | SWIRE           | QFN32 5x5mm      | MSL3 | 15000    | 0        | 1   | 1   | -40°C ~ +125°C | 1         | 0          | 0       | 0         | 0          | 1    | 17   | 0   | 1    | 6   | 0           | 1    | 0             | 14  | 2            | 1    | 1    |

选型的考虑：
RAM多大
Flash多大（OTA要做吗）
封装？
MCU（T- MCU / Risc-V）
