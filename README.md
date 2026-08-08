# STM32 OBD-II Scanner

一个基于 STM32 和 SH1106 OLED 屏幕的简易 OBD-II 车辆诊断工具。

## 功能
*   读取发动机转速 (RPM)
*   读取车速 (Speed)

## 硬件
*   **MCU**: STM32F103C8T6 (或其他型号)
*   **屏幕**: 0.96寸 SH1106 OLED (I2C 接口)
*   **CAN 收发器**: TJA1050

## 接线

| OLED | STM32 |
| :--- | :--- |
| SCL  | PB10   |
| SDA  | PB11   |

| CAN | STM32 |
| :--- | :--- |
| RX   | PA11   |
| TX   | PA12   |
