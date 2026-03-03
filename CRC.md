# CRC 算法家族

CRC(Cyclic Redundancy Check, 循环冗余校验) 算法家族
> 差异在于多项式(Polynominal) 的选择、数据位款以及初始值/结果异或值的配置

## 具体成员

1. CRC-8
2. CRC-16-CCITT
3. CRC-16-Modbus
4. CRC-32
5. CRC-64-ISO

算法名称|多项式 (Hex)| 应用场景
:---:|:---:|:---:
 CRC-8|0x07|1-Wire 总线、简单的传感器数据校验。
CRC-16-CCITT|0x1021|X.25、蓝牙、SD 卡、HDLC 协议。
CRC-16-Modbus|0x8005| 工业控制（Modbus 协议），非常经典。
CRC-32|0x04C11DB7| 以太网 (Ethernet)、ZIP / PNG 文件压缩、Gzip。
CRC-64-ISO|0x000000000000001B| 高级数据存储、Redis、大型数据库校验。
