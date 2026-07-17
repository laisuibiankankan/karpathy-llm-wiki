# EPSCU DTC 故障目录

> Sources: Project Handbook, 2026-07-16; DTC List V6.0, 2023-11-14
> Raw: [EPSCU DTC 故障诊断手册](../../raw/steering/2026-07-16-epscu-dtc-diagnostic-handbook.md); [DTC List V6.0](../../raw/steering/2023-11-14-dtc-list-v6.0.md)

## 概述

EPSCU (Electric Power Steering Control Unit) 的 DTC (Diagnostic Trouble Code) 故障目录，融合两份源文件：
1. **project_handbook** (2026-07-16) — 46 条故障码，按 DFC 分类，含 DFC Value 和等级
2. **DTC List V6.0** (2023-11-14) — 83 条故障记录，含 SPN/FMI、产生条件、消除条件、修复指导、故障等级、故障灯

覆盖传感器、CAN 通信、控制器内部、电机驱动、电源、下线标定及转向机械等方面。

> **注意**: DTC List V6.0 的故障等级范围 1-6（1最低，6最高），与 project_handbook 的高/中/低划分尺度不同。

## 按 DFC 分类整理

### Torque and Angle Sensor（扭矩和角度传感器）

扭矩/角度传感器相关的故障，共 4 项，以高等级为主：

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| Angle signal fault | 中 | 角度信号故障 | 721939 |
| Communication error | 高 | 通讯错误 | 656403 |
| TAS torque signal fault | 高 | 扭矩信号故障 | 394259 |
| Torque sensor supply voltage is abnormal | 高 | 扭矩传感器电源电压异常 | 197651 |

### Vehicle CAN（车载 CAN 总线）

CAN 总线通信相关的故障，共 22 项，绝大部分为低等级。包含两大类：

**消息超时错误（Message Timeout）** — 多条 CAN 消息超时：
- CCVS1 CAN, EBC2 CAN, EPSI CAN, ETC2 CAN, HRW CAN, VDHR CAN 各通道均有超时报文

**消息信号错误（Signal Error）** — 各节点信号异常：
- 刹车信号、驻车刹车信号、车轮速度、档位、方向盘振动、里程等

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| Bus Off | 中 | 总线关闭故障 | 131347 |
| DTC_CAN_M_CCVS1_TO | 低 | 消息超时错误 (CCVS1) | 655635 |
| DTC_CAN_M_EBC2_TO | 低 | 消息超时错误 (EBC2) | 721171 |
| DTC_CAN_M_EPSI_CRC | 低 | 消息 CRC 错误 | 198931 |
| DTC_CAN_M_EPSI_MC | 低 | 消息计数器错误 | 1181971 |
| DTC_CAN_M_EPSI_TO | 低 | 消息超时错误 (EPSI) | 1048851 |
| DTC_CAN_M_ETC2_TO | 低 | 消息超时错误 (ETC2) | 786707 |
| DTC_CAN_M_HRW_TO | 低 | 消息超时错误 (HRW) | 852243 |
| DTC_CAN_M_VDHR_TO | 低 | 消息超时错误 (VDHR) | 983315 |
| DTC_CAN_S_CCVS1_BRAKE | 低 | 消息刹车信号错误 | 1313043 |
| DTC_CAN_S_CCVS1_PBRAKE | 低 | 消息驻车刹车信号错误 | 1378579 |
| DTC_CAN_S_CCVS1_WHEELSPD | 低 | 消息车轮速度信号错误 | 1444115 |
| DTC_CAN_S_EBC2_FRXL_SPEED | 低 | 消息前轴速度信号错误 | 1509651 |
| DTC_CAN_S_EPSI_STEERFEELVAR | 低 | 消息手感曲线选择信号错误 | 985363 |
| DTC_CAN_S_EPSI_STEERWHEELVIBLV | 低 | 消息方向盘振动级别信号错误 | 1050899 |
| DTC_CAN_S_EPSI_STEERWHEELVIBMODREQ | 低 | 消息方向盘振动模式请求信号错误 | 1116435 |
| DTC_CAN_S_ETC2_CURGEAR | 低 | 消息变速箱当前档位信号错误 | 1575187 |
| DTC_CAN_S_HRW_WSPEED_FL | 低 | 消息前轴左轮速度信号错误 | 1640723 |
| DTC_CAN_S_HRW_WSPEED_FR | 低 | 消息前轴右轮速度信号错误 | 1706259 |
| DTC_CAN_S_HRW_WSPEED_RL | 低 | 消息后轴左轮速度信号错误 | 1771795 |
| DTC_CAN_S_HRW_WSPEED_RR | 低 | 消息后轴右轮速度信号错误 | 1837331 |
| DTC_CAN_S_VDHR_HIRESDIS | 低 | 消息车辆里程信号错误 | 2230547 |

### Steering Control Unit（转向控制单元）

ECU 内部及电机驱动相关的故障，共 14 项，涵盖内部硬件故障、软件故障、电机相关及温度传感器：

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| DTC_ECU_INTERNAL_FAILURE | 中 | 内部错误 | 198419 |
| DTC_ECU_INTERNAL_RAM_FAILURE | 高 | 内部错误 (RAM) | 984851 |
| DTC_ECU_INTERNAL_ROM_FAILURE | 高 | 内部错误 (ROM) | 1050387 |
| DTC_ECU_INTERNAL_SW_FAILURE | 中 | 软件功能错误 | 2098963 |
| DTC_ECU_INTERNAL_SW_SAFETY_FAILURE | 高 | 内部功能错误 | 1967891 |
| DTC_ECU_INTERNAL_UNCRITICAL_FAILURE | 低 | 内部警告 | 657171 |
| DTC_WRONG_SW | 高 | 特殊软件版本 | 919315 |
| Motor current is abnormal | 高 | 电机电流异常 | 329235 |
| Motor driver circuit failure | 高 | 电机驱动电路失效 | 198163 |
| Motor position sensor failure | 高 | 电机位置传感器故障 | 459795 |
| Temperature sensor fault | 高 | 温度传感器故障 | 525331 |
| The different of actual current and target current is too large | 高 | 助力电机实际电流和目标电流差异过大 | 132627 |
| The ECU internal chip fault | 高 | 控制器内部芯片故障 | 132883 |

### Steering System（转向系统）

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| DTC_MECHANIC_END_OF_LIFE | 高 | 转向机械达到使用寿命 | 2164499 |

### Power Supply（电源）

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| Over-voltage | 中 | 蓄电池供电过压 | 196627 |
| Under-voltage | 中 | 蓄电池供电欠压 | 262163 |

### Vehicle End of Line（整车下线标定）

| DFC名称 | 等级 | 中文解释 | DFC Value |
|---|---|---|---|
| ECU don't perform Steering Angle Calibration | 低 | 未进行角度标定 | 853779 |
| Left soft end stop not learned | 低 | 左侧软限位未学习 | 788243 |
| Right soft end stop not learned | 低 | 右侧软限位未学习 | 722707 |

## DTC List V6.0 补充数据

> 源：`02_诊断服务及故障列表_V6.0_20231114.xlsx` 的「故障列表(DTC list)」sheet
> 注：已排除 DTC 故障码列。以下按主题归纳。

### 新增故障类型（DTC List V6.0 独有）

以下故障在 project_handbook 中未出现，由 DTC List V6.0 补充：

**ECU/软件相关**
- **ECU_ECU** (SPN 520192, FMI 12) — ECU 电控单元失效，等级 6，亮黄灯
- **RESET** (SPN 520199, FMI 31) — 软件未正确重启，等级 1
- **ESB_LCK** (SPN 520198, FMI 31) — 软件纠正状态/ESB未锁定，等级 1，亮黄灯
- **PRODUCTION_MODE** (SPN 520207, FMI 31) — 工厂模式，等级 5，亮红灯
- **DATA_FLASH_WRONG_LAYOUT** (SPN 520196, FMI 31) — 无效软件(DF地址不匹配)，等级 6

**热管理/降级**
- **ECU_RED** (SPN 520194, FMI 31) — 转向机电器件温度过高-助力降级，等级 4
- **MP_RED** (SPN 520195, FMI 31) — 电机温度过高-助力降级，等级 4
- **CR_RED** (SPN 520197, FMI 31) — 电机助力降级输出(颤振)，等级 1
- **FLOAT_TEMP_DIFF** (SPN 520231, FMI 12) — HWLib 温度偏差错误，等级 4

**转向机械/涡轮**
- **GEARHR** (SPN 520200, FMI 31) — 涡轮失效（高风险），等级 6，亮红灯
- **GEARLR** (SPN 520201, FMI 31) — 涡轮失效风险，等级 4，亮黄灯

**液压系统**
- **HYDRAULICS** (SPN 520202, FMI 31) — 液压系统失效，等级 5，亮红灯
- **HYDR_CLAMP15_OFF** (SPN 520209, FMI 31) — 液压助力中断(15电关闭)，等级 5，亮红灯

**外部控制/脱手检测 (ESR)**
- **ESR_HANDSOFF_WARN1/2/3** (SPN 520211-520213, FMI 31) — 外部控制时脱手警告 1/2/3 级，等级 1
- **YELLOW_LAMP** (SPN 520214, FMI 31) — 琥珀黄指示灯亮
- **RED_LAMP** (SPN 520215, FMI 31) — 红色停止指示灯亮

**摩擦力/转子角度**
- **FRICTION** (SPN 520232, FMI 31) — 转向系统摩擦力过大，等级 1
- **ROTANG** (SPN 520233, FMI 2) — Rotor Angle 无效，等级 1，亮黄灯

**EPSI 外部接口（3路）** — CRC/MC 错误、CAN Time Out、DLC 错误
- EPSI1 (SPN 520217), EPSI2 (SPN 520223), EPSI3 (SPN 520227) — 各 3 种故障模式，等级 1

**EPSI 信号源错误**（等级 1）
- SIG_EXTMODE, SIG_FBFT, SIG_MOT, SIG_STANG, SIG_ACTRET, SIG_ANGWET, SIG_ANGCTRLTQ
- SIG_STRVBRMODE, SIG_STRVBRLV, SIG_STRFVAR

**CAN 信号源错误（扩展）** — 等级 1
- VDC2 (YawRate), VDC2 (LateralAcc), HRW 各轮速、CCVS1 轮速/刹车、EBC2 前轴速、TCO1 车速、EEC1 发动机转速、VDHR 里程、TD 时间信息

**电源相关（DTC List V6.0 版更详细）**
- SPN 168 多个 FMI：HIGH_VOLT_OFF(等级4), LOW_VOLT_OFF(等级4), HIGH_VOLT_WARN(等级1), UCO_RED(等级4), LOW_VOLT_WARN(等级1), UCU_RED(等级1), VOLT_NOSTART(等级4)

### 字段对应关系

| project_handbook 字段 | DTC List V6.0 对应字段 | 说明 |
|---|---|---|
| DFC名称 / 英文解释 | 故障简写 | 故障简写可关联匹配 |
| 中文解释 | 故障描述（中文部分） | 描述更详尽 |
| DFC等级 | 故障等级 | 尺度不同（3级 vs 1-6级） |
| 报错原因 | 产生条件 | DTC V6.0 补充了此项 |
| 报错分析 | — | 待后续补充 |
| 报错处理方案 | 消除条件及处理 / 修复指导 | DTC V6.0 提供了详细内容 |

## 等级分布统计

### project_handbook 高/中/低分布

| 等级 | 数量 | 占比 |
|---|---|---|
| 高 (High) | 21 | 45.7% |
| 中 (Medium) | 6 | 13.0% |
| 低 (Low) | 19 | 41.3% |

高等级故障占近半数，主要分布在：电机驱动电路、位置传感器、扭矩传感器、ECU 内部要害部件（RAM/ROM/安全功能）、以及转向机械寿命到期。

### DTC List V6.0 1-6 级分布

| 等级 | 数量 | 说明 |
|---|---|---|
| 1（最低） | 52 | 主要为 CAN 超时/信号错误/脱手警告 |
| 4 | 9 | 温度降级/电压警告/涡轮风险 |
| 5 | 3 | 液压失效/工厂模式/助力中断 |
| 6（最高） | 9 | ECU失效/涡轮失效/无效软件/传感器无效 |

> 合计 73 条（不含故障灯为空的 2 条）

## 备注

- project_handbook 中「整车DFC等级」「报错类型」「报错原因」「报错分析」「报错处理方案」列为空，待后续补充。DTC List V6.0 已部分补充了产生条件(报错原因)和消除条件/修复指导(报错处理方案)。
- 所有故障的「预处理」字段均为"否"
- 所有故障的「关联变量」列为空，待后续补充

## See Also

- [Steering Case Analysis](/home/ubuntu/.openclaw/workspace/skills/steering-case-analysis/SKILL.md) — 转向系统客诉案例分析 skill
