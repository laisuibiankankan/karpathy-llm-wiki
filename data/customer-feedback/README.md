# 客户反馈数据库 Customer Feedback Database

> Source: 转向系统售后客诉反馈记录（含 LLM 分析）
> Database: `database_customerFeedback.db` (SQLite3)
> Records: 273 条客诉反馈，全部含 LLM 拆解结果
> Updated: 2026-07-20

## 表结构

### `customer_feedback` — 客户反馈记录（主表，含 LLM 拆解字段）

273 条记录，每条对应一条客户反馈。涵盖 HPS/EHPS/RAS 等产品线的售后/0km/field 反馈。
LLM 拆解结果作为 9 个 LLM_ 前缀字段直接追加在同一条记录中，无需 JOIN 查询。

#### 基础字段（26 列）

| 字段 | 类型 | 说明 | 示例 |
|---|---|---|---|
| id | INTEGER | 主键自增 | 1 |
| 序号 | TEXT | 反馈序号 | 1 |
| 反馈年 | TEXT | 反馈年份 | 2026 |
| 类别 | TEXT | 反馈类别 | field / 0km / 0KM / 售后 / 试验车 / 出保 |
| 反馈时间 | TEXT | 反馈时间 | 2026-01-15 |
| QMC负责人 | TEXT | QMC 负责人 | 张欢 / 孙鹏鹏 / 徐胜夕 / 王常瑞 / 卢阳 |
| 客户物料号 | TEXT | 客户物料编号 | |
| VIN | TEXT | 车辆 VIN 号 | |
| 客户代码 | TEXT | 客户代码 | |
| 客户 | TEXT | 客户名称 | Yutong New Energy, FAW CC, CNHTC CV... |
| 产品族 | TEXT | 产品系列 | HPS(186), EHPS(46), RAS(36) |
| 博世产品型号 | TEXT | 博世产品型号 | |
| 序列号 | TEXT | 产品序列号 | |
| 生产日期 | TEXT | 生产日期 | |
| 客户反馈 | TEXT | 客户反馈的原始描述 | 「转向沉重，左右打方向均沉重」 |
| 联系电话 | TEXT | 联系电话 | |
| 客户联系人 | TEXT | 客户联系人 | |
| 数量 | TEXT | 涉及数量 | |
| 客户统计中 | TEXT | 客户统计中的分类 | |
| 质保判定 | TEXT | 质保判定结果 | |
| 初步处理过程 | TEXT | 初步处理过程描述 | |
| 根本原因 | TEXT | 根因分析结果 | |
| 措施 | TEXT | 已采取的措施 | |
| 旧件处理 | TEXT | 旧件处理方式 | |
| 是否发送新件替换 | TEXT | 是否发送新件 | |
| 新件的发货单号 | TEXT | 新件发货单号 | |

#### LLM 拆解字段（9 列，追加在基础字段之后）

| 字段 | 类型 | 说明 | 示例 |
|---|---|---|---|
| LLM_反馈方 | TEXT | LLM 识别的反馈方 | 服务站 / 主机厂(宇通技术) / 客户 |
| LLM_问题诊断 | TEXT | LLM 诊断的根因分析 | 「±30°快打快回异响属于非正常操作」 |
| LLM_建议措施 | TEXT | LLM 建议的解决措施 | |
| LLM_措施执行方 | TEXT | 措施执行方 | 博世 / 服务站 / 主机厂 |
| LLM_解决状态 | TEXT | 解决状态 | 已解决 / 未解决 / 待跟踪 |
| LLM_执行结果 | TEXT | 最终执行结果描述 | |
| LLM_责任归属 | TEXT | 责任分类 | 转向机自身 / 外围件 / 安装装配 / 使用条件 / 客户操作 / 未确认 |
| LLM_关键时间节点 | TEXT | 重要时间线事件 | 「2026-07-17：更换福斯PTR640转向油，异响解决」 |
| LLM_排查排除项 | TEXT | 已排查并排除的原因 | 「排除横拉杆球头、直拉杆球头、主销；排除转向管柱」 |

### 说明

- **LLM 拆解字段不在独立表**中，而是作为 `customer_feedback` 的列存在，查询无需 JOIN
- 未拆解的记录对应 LLM 字段为 NULL
- 旧版本中的 `feedback_analysis` 表已废弃

## 数据概览

### 类别分布

| 类别 | 数量 |
|---|---|
| field（市场） | 140 |
| 0km（出厂前） | 66 |
| 0KM（出厂前） | 59 |
| 其他 | 4 |
| 售后 | 2 |
| 试验车 | 1 |
| 出保 | 1 |

### 产品族分布

| 产品族 | 数量 | 说明 |
|---|---|---|
| HPS | 186 | 液压助力转向 |
| EHPS | 46 | 电液助力转向 |
| RAS | 36 | 后桥主动转向 |
| 角传动 | 1 | 锥齿轮箱 |
| Bevel box | 1 | 锥齿轮箱 |

### 负责人

| 负责人 | 负责记录数 |
|---|---|
| 张欢 | 106 |
| 孙鹏鹏 | 96 |
| 徐胜夕 | 51 |
| 王常瑞 | 12 |
| 卢阳 | 4 |

### Top 客户

Yutong New Energy (52) / CNHTC CV (30) / FAW CC (25) / CNHTC Truck (24) / BYD (14) / DFCV (13)

### LLM 拆解结果概览

#### 解决状态

| 状态 | 数量 |
|---|---|
| 已解决 | 131 |
| 待跟踪 | 85 |
| 未确认 | 28 |
| 未解决 | 17 |
| 已升级 | 7 |
| 待验证 | 3 |
| 已放行 | 2 |

#### 责任归属

| 责任归属 | 数量 |
|---|---|
| 未确认 | 123 |
| 外围件 | 30 |
| 客户操作 | 25 |
| 安装装配 | 24 |
| 转向机自身 | 19 |
| 使用条件 | 18 |
| 其他 | 34 |

## 使用方式

```bash
# SQLite 查询示例
sqlite3 data/customer-feedback/database_customerFeedback.db

# 查看所有 field 类 EHPS 投诉
SELECT * FROM customer_feedback 
WHERE 类别 = 'field' AND 产品族 = 'EHPS';

# 查看有 LLM 诊断的沉重问题（无需 JOIN）
SELECT 客户, 客户反馈, LLM_问题诊断, LLM_建议措施
FROM customer_feedback
WHERE 客户反馈 LIKE '%沉重%' AND LLM_问题诊断 IS NOT NULL;

# 按责任归属统计
SELECT LLM_责任归属, COUNT(*) AS cnt
FROM customer_feedback
WHERE LLM_责任归属 IS NOT NULL
GROUP BY LLM_责任归属
ORDER BY cnt DESC;

# 待跟踪且属于转向机自身的问题
SELECT 序号, 客户, 客户反馈, LLM_问题诊断
FROM customer_feedback
WHERE LLM_解决状态 = '待跟踪' AND LLM_责任归属 = '转向机自身';
```

## 关联 Wiki 文章

- [转向系统客诉分析](../../wiki/steering/customer-complaint/目录) — 基于本数据库 + raw 案例编译的概念知识文章
- 数据库中的 LLM_问题诊断 字段可与概念文章中的故障模式分类对应
