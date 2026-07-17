# 客户反馈数据库 Customer Feedback Database

> Source: 转向系统售后客诉反馈记录（含 LLM 分析）
> Database: `database_customerFeedback.db` (SQLite3)
> Records: 262 条客诉反馈
> Updated: 2026-07-17

## 表结构

### `customer_feedback` — 客户反馈记录（主表）

262 条记录，每条对应一条客户反馈。涵盖 HPS/EHPS/RAS 等产品线的售后/0km/field 反馈。

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
| 产品族 | TEXT | 产品系列 | HPS(173), EHPS(44), RAS(36) |
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

### `feedback_analysis` — LLM 分析结果表

258 条分析记录，通过 `feedback_id` 关联 `customer_feedback.id`。

| 字段 | 类型 | 说明 | 示例 |
|---|---|---|---|
| id | INTEGER | 主键自增 | |
| feedback_id | INTEGER | 关联 customer_feedback.id | 21 |
| LLM_序号 | TEXT | LLM 分析序号 | 21 |
| LLM_反馈方 | TEXT | LLM 识别的反馈方 | 经销商 / 主机厂 |
| LLM_问题诊断 | TEXT | LLM 诊断的根因 | 「转向机进油口处渗油导致外观油污」 |
| LLM_建议措施 | TEXT | LLM 建议的维修措施 | |
| LLM_措施执行方 | TEXT | LLM 建议的措施执行方 | |
| LLM_解决状态 | TEXT | LLM 判定的解决状态 | |
| LLM_执行结果 | TEXT | LLM 判定的执行结果 | |
| LLM_责任归属 | TEXT | LLM 判定的责任方 | |
| LLM_关键时间节点 | TEXT | LLM 提取的关键时间点 | |
| LLM_排查排除项 | TEXT | LLM 识别已排查/排除的项目 | |

## 数据概览

### 类别分布

| 类别 | 数量 |
|---|---|
| field（市场） | 131 |
| 0km（出厂前） | 60 |
| 0KM（出厂前） | 57 |
|（空）| 5 |
| 其他 | 4 |
| 售后 | 3 |
| 试验车 | 1 |
| 出保 | 1 |

### 产品族分布

| 产品族 | 数量 | 说明 |
|---|---|---|
| HPS | 173 | 液压助力转向 |
| EHPS | 44 | 电液助力转向 |
| RAS | 36 | 后桥主动转向 |
| Bevel box | 1 | 锥齿轮箱 |

### 负责人

| 负责人 | 负责记录数 |
|---|---|
| 张欢 | 101 |
| 孙鹏鹏 | 91 |
| 徐胜夕 | 45 |
| 王常瑞 | 12 |

### Top 客户

Yutong New Energy (49) / FAW CC (25) / CNHTC CV (25) / CNHTC Truck (24) / DFCV (13) / BYD (11)

## 关联 Wiki 文章

- [转向系统客诉分析](../../wiki/steering/customer-complaint/目录) — 基于本数据库 + raw 案例编译的概念知识文章
- 数据库中的 LLM_问题诊断 字段可与概念文章中的故障模式分类对应

## 使用方式

```bash
# SQLite 查询示例
sqlite3 data/customer-feedback/database_customerFeedback.db

# 查看所有 field 类 EHPS 投诉
SELECT * FROM customer_feedback 
WHERE 类别 = 'field' AND 产品族 = 'EHPS';

# 查看有 LLM 诊断的沉重问题
SELECT f.客户, f.客户反馈, a.LLM_问题诊断, a.LLM_建议措施
FROM customer_feedback f
JOIN feedback_analysis a ON f.id = a.feedback_id
WHERE f.客户反馈 LIKE '%沉重%';
```
