#  STM32 OBD-II 车载数据读取器

这是一个基于 STM32 微控制器和 CAN 总线协议开发的简易车载 OBD-II 诊断工具。该项目通过标准的 OBD-II 接口与汽车 ECU 进行通信，实时读取车辆核心运行数据，并通过本地 OLED 屏幕进行直观展示。

##  核心功能

本设备支持实时读取并显示以下 **3 项核心车辆参数**：
1. **发动机转速 (RPM)** - 实时监测引擎工作状态 (PID: 0x0C)
2. **车辆速度 (Speed)** - 实时获取当前行驶速度 (PID: 0x0D)
3. **冷却液温度 (Coolant Temp)** - 监测发动机水温，防止过热 (PID: 0x05)

## ️ 硬件清单

* **主控芯片**: STM32F103C8T6 (基于 STM32 HAL 库开发)
* **显示模块**: 0.96寸 SH1106 OLED 屏幕 (软件模拟 I2C 接口)
* **通信模块**: TJA1050 CAN 总线收发器
* **电源模块**: 12V 转 3.3V 降压模块 (LM1117 等)
* **接口**: 标准 OBD-II 16Pin 接口

##  硬件接线指南

### 1. OLED 屏幕接线 (软件 I2C)

| OLED 引脚 | STM32 引脚 | 说明 |
| :--- | :--- | :--- |
| VCC | 3.3V | 供电 |
| GND | GND | 共地 |
| SCL | PB10 | 时钟线 |
| SDA | PB11 | 数据线 |

### 2. CAN 模块接线

| CAN 模块 | STM32 引脚 | OBD-II 接口 |
| :--- | :--- | :--- |
| CAN_RX | PA11 | Pin 6 (CAN_High) |
| CAN_TX | PA12 | Pin 14 (CAN_Low) |
| GND | GND | Pin 4 / Pin 5 (信号地) |

> ️ **安全警告**：汽车 OBD 接口 Pin 16 为 12V 蓄电池电压，**严禁**直接接入 STM32！请务必使用降压模块将 12V 转换为 3.3V 后再为开发板供电。

##  软件与开发环境

* **IDE**: Keil MDK-ARM / STM32CubeIDE
* **配置工具**: STM32CubeMX
* **底层驱动**: STM32 HAL 库
* **通信协议**: ISO 15765-4 (CAN) / SAE J1979 (OBD-II)

### 代码结构说明
* `Core/Src/main.c`: 主程序，包含 CAN 过滤器配置、OBD 请求轮询及数据解析逻辑。
* `Core/Src/oled.c` / `Core/I
* 
