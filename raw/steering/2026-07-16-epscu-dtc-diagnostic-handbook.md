# EPSCU DTC Diagnostic Handbook (故障诊断手册)

> Source: `project_handbook_202607161200(1).xlsx` (本地文件)
> Collected: 2026-07-17
> Published: 2026-07-16 (文件日期)

## 数据说明

此为 EPSCU (Electric Power Steering Control Unit，电动助力转向控制单元) 的 DTC (Diagnostic Trouble Code，诊断故障码) 手册。包含 46 个故障项的完整列表，涵盖 DFC 分类、等级、DFC Value 等信息。

列说明：
- **控制器**: 始终为 EPSCU
- **DFC名称**: 诊断故障码名称（英文）
- **DFC分类**: 故障所属分类域，如 Torque and Angle Sensor、Vehicle CAN、Steering Control Unit 等
- **整车DFC等级**: （空，待补充）
- **DFC等级**: 故障严重等级：低 / 中 / 高
- **英文解释**: 英文描述
- **中文解释**: 中文描述
- **DFC Value**: 诊断故障码数值（十进制）
- **关联变量**: （空，待补充）
- **预处理**: 是否进行预处理（均为"否"）
- **报错类型 / 报错原因 / 报错分析 / 报错处理方案**: （空，待补充）

## 故障汇总表

| 控制器 | DFC名称 | DFC分类 | 整车DFC等级 | DFC等级 | 英文解释 | 中文解释 | DFC Value |
|---|---|---|---|---|---|---|---|
| EPSCU | Angle signal fault | Torque and Angle Sensor |  | 中 | Angle signal fault | 角度信号故障 | 721939 |
| EPSCU | Bus Off | Vehicle CAN |  | 中 | Bus Off | 总线关闭故障 | 131347 |
| EPSCU | Communication error | Torque and Angle Sensor |  | 高 | Communication error | 通讯错误 | 656403 |
| EPSCU | DTC_CAN_M_CCVS1_TO CCVS1 CAN | Vehicle CAN |  | 低 | DTC_CAN_M_CCVS1_TO CCVS1 CAN | 消息超时错误 | 655635 |
| EPSCU | DTC_CAN_M_EBC2_TO EBC2 CAN | Vehicle CAN |  | 低 | DTC_CAN_M_EBC2_TO EBC2 CAN | 消息超时错误 | 721171 |
| EPSCU | DTC_CAN_M_EPSI_CRC EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_M_EPSI_CRC EPSI CAN | 消息CRC错误 | 198931 |
| EPSCU | DTC_CAN_M_EPSI_MC EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_M_EPSI_MC EPSI CAN | 消息计数器错误 | 1181971 |
| EPSCU | DTC_CAN_M_EPSI_TO EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_M_EPSI_TO EPSI CAN | 消息超时错误 | 1048851 |
| EPSCU | DTC_CAN_M_ETC2_TO ETC2 CAN | Vehicle CAN |  | 低 | DTC_CAN_M_ETC2_TO ETC2 CAN | 消息超时错误 | 786707 |
| EPSCU | DTC_CAN_M_HRW_TO HRW CAN | Vehicle CAN |  | 低 | DTC_CAN_M_HRW_TO HRW CAN | 消息超时错误 | 852243 |
| EPSCU | DTC_CAN_M_VDHR_TO VDHR CAN | Vehicle CAN |  | 低 | DTC_CAN_M_VDHR_TO VDHR CAN | 消息超时错误 | 983315 |
| EPSCU | DTC_CAN_S_CCVS1_BRAKE CCVS1 CAN | Vehicle CAN |  | 低 | DTC_CAN_S_CCVS1_BRAKE CCVS1 CAN | 消息刹车信号错误 | 1313043 |
| EPSCU | DTC_CAN_S_CCVS1_PBRAKE CCVS1 CAN | Vehicle CAN |  | 低 | DTC_CAN_S_CCVS1_PBRAKE CCVS1 CAN | 消息驻车刹车信号错误 | 1378579 |
| EPSCU | DTC_CAN_S_CCVS1_WHEELSPD CCVS1 CAN | Vehicle CAN |  | 低 | DTC_CAN_S_CCVS1_WHEELSPD CCVS1 CAN | 消息车轮速度信号错误 | 1444115 |
| EPSCU | DTC_CAN_S_EBC2_FRXL_SPEED EBC2 CAN | Vehicle CAN |  | 低 | DTC_CAN_S_EBC2_FRXL_SPEED EBC2 CAN | 消息前轴速度信号错误 | 1509651 |
| EPSCU | DTC_CAN_S_EPSI_STEERFEELVAR EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_S_EPSI_STEERFEELVAR EPSI CAN | 消息手感曲线选择信号错误 | 985363 |
| EPSCU | DTC_CAN_S_EPSI_STEERWHEELVIBLV EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_S_EPSI_STEERWHEELVIBLV EPSI CAN | 消息方向盘振动级别信号错误 | 1050899 |
| EPSCU | DTC_CAN_S_EPSI_STEERWHEELVIBMODREQ EPSI CAN | Vehicle CAN |  | 低 | DTC_CAN_S_EPSI_STEERWHEELVIBMODREQ EPSI CAN | 消息方向盘振动模式请求信号错误 | 1116435 |
| EPSCU | DTC_CAN_S_ETC2_CURGEAR ETC2 CAN | Vehicle CAN |  | 低 | DTC_CAN_S_ETC2_CURGEAR ETC2 CAN | 消息变速箱当前档位信号错误 | 1575187 |
| EPSCU | DTC_CAN_S_HRW_WSPEED_FL HRW CAN | Vehicle CAN |  | 低 | DTC_CAN_S_HRW_WSPEED_FL HRW CAN | 消息前轴左轮速度信号错误 | 1640723 |
| EPSCU | DTC_CAN_S_HRW_WSPEED_FR HRW CAN | Vehicle CAN |  | 低 | DTC_CAN_S_HRW_WSPEED_FR HRW CAN | 消息前轴右轮速度信号错误 | 1706259 |
| EPSCU | DTC_CAN_S_HRW_WSPEED_RL HRW CAN | Vehicle CAN |  | 低 | DTC_CAN_S_HRW_WSPEED_RL HRW CAN | 消息后轴左轮速度信号错误 | 1771795 |
| EPSCU | DTC_CAN_S_HRW_WSPEED_RR HRW CAN | Vehicle CAN |  | 低 | DTC_CAN_S_HRW_WSPEED_RR HRW CAN | 消息后轴右轮速度信号错误 | 1837331 |
| EPSCU | DTC_CAN_S_VDHR_HIRESDIS VDHR CAN | Vehicle CAN |  | 低 | DTC_CAN_S_VDHR_HIRESDIS VDHR CAN | 消息车辆里程信号错误 | 2230547 |
| EPSCU | DTC_ECU_INTERNAL_FAILURE ECU | Steering Control Unit |  | 中 | DTC_ECU_INTERNAL_FAILURE ECU | 内部错误 | 198419 |
| EPSCU | DTC_ECU_INTERNAL_RAM_FAILURE ECU RAM | Steering Control Unit |  | 高 | DTC_ECU_INTERNAL_RAM_FAILURE ECU RAM | 内部错误 | 984851 |
| EPSCU | DTC_ECU_INTERNAL_ROM_FAILURE ECU ROM | Steering Control Unit |  | 高 | DTC_ECU_INTERNAL_ROM_FAILURE ECU ROM | 内部错误 | 1050387 |
| EPSCU | DTC_ECU_INTERNAL_SW_FAILURE ECU | Steering Control Unit |  | 中 | DTC_ECU_INTERNAL_SW_FAILURE ECU | 软件功能错误 | 2098963 |
| EPSCU | DTC_ECU_INTERNAL_SW_SAFETY_FAILURE ECU | Steering Control Unit |  | 高 | DTC_ECU_INTERNAL_SW_SAFETY_FAILURE ECU | 内部功能错误 | 1967891 |
| EPSCU | DTC_ECU_INTERNAL_UNCRITICAL_FAILURE ECU | Steering Control Unit |  | 低 | DTC_ECU_INTERNAL_UNCRITICAL_FAILURE ECU | 内部警告 | 657171 |
| EPSCU | DTC_MECHANIC_END_OF_LIFE | Steering System |  | 高 | DTC_MECHANIC_END_OF_LIFE | 转向机械达到使用寿命 | 2164499 |
| EPSCU | DTC_WRONG_SW | Steering Control Unit |  | 高 | DTC_WRONG_SW | 特殊软件版本 | 919315 |
| EPSCU | ECU don't perform Steering Angle Calibration | Vehicle End of Line |  | 低 | ECU don't perform Steering Angle Calibration | 未进行角度标定 | 853779 |
| EPSCU | Gateway lost | Vehicle CAN |  | 中 | Gateway lost | 网关丢失 | 590099 |
| EPSCU | Left soft end stop not learned | Vehicle End of Line |  | 低 | Left soft end stop not learned | 左侧软限位未学习 | 788243 |
| EPSCU | Motor current is abnormal | Steering Control Unit |  | 高 | Motor current is abnormal | 电机电流异常 | 329235 |
| EPSCU | Motor driver circuit failure | Steering Control Unit |  | 高 | Motor driver circuit failure | 电机驱动电路失效 | 198163 |
| EPSCU | Motor position sensor failure | Steering Control Unit |  | 高 | Motor position sensor failure | 电机位置传感器故障 | 459795 |
| EPSCU | Over-voltage | Power Supply |  | 中 | Over-voltage | 蓄电池供电过压 | 196627 |
| EPSCU | Right soft end stop not learned | Vehicle End of Line |  | 低 | Right soft end stop not learned | 右侧软限位未学习 | 722707 |
| EPSCU | TAS torque signal fault TAS | Torque and Angle Sensor |  | 高 | TAS torque signal fault TAS | 扭矩信号故障 | 394259 |
| EPSCU | Temperature sensor fault | Steering Control Unit |  | 高 | Temperature sensor fault | 温度传感器故障 | 525331 |
| EPSCU | The different of actual current and target current is too large | Steering Control Unit |  | 高 | The different of actual current and target current is too large | 助力电机实际电流和目标电流差异过大 | 132627 |
| EPSCU | The ECU internal chip fault | Steering Control Unit |  | 高 | The ECU internal chip fault | 控制器内部芯片故障 | 132883 |
| EPSCU | Torque sensor supply voltage is abnormal | Torque and Angle Sensor |  | 高 | Torque sensor supply voltage is abnormal | 扭矩传感器电源电压异常 | 197651 |
| EPSCU | Under-voltage | Power Supply |  | 中 | Under-voltage | 蓄电池供电欠压 | 262163 |

## DFC分类分布

- **Torque and Angle Sensor (扭矩/角度传感器)**: Angle signal fault, Communication error, TAS torque signal fault, Torque sensor supply voltage abnormal — 4项，等级以高为主
- **Vehicle CAN (车载CAN总线)**: Bus Off, 及大量 CAN 消息超时/信号错误 — 22项，等级以低为主
- **Steering Control Unit (转向控制单元)**: ECU内部故障、电机相关故障、温度传感器故障等 — 14项，等级涵盖低/中/高
- **Steering System (转向系统)**: 转向机械使用寿命 — 1项，高
- **Power Supply (电源)**: Over-voltage, Under-voltage — 2项，中
- **Vehicle End of Line (整车下线)**: 标定/学习类 — 3项，低
