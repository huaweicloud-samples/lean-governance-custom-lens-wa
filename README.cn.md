# lean-governance-custom-lens-wa / Well-Architected 检查单库

[![License](https://img.shields.io/badge/License-MIT%20No%20Attribution-blue.svg)](LICENSE)
[![Huawei Cloud](https://img.shields.io/badge/Huawei%20Cloud-IAM%20Auth-red.svg)](https://support.huaweicloud.com/intl/en-us/)
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)](#)
[English](README.md)

> Well-Architected 自定义 lens 检查单库（华为云语境）
> Well-Architected Custom Lens Checklist Library

---

## 1. 简介 / Overview

**中文**：本实践提供 **云上架构最佳实践检查单库** 核心能力，用于 **架构评估、合规检讨、上线前健康检查** 场景。面向云架构师 / 运维 / 安全工程师，可作为参考模板 / 评估基线 / 检讨工具 使用。

### 核心能力

- 22 个服务域检查单（数据库 / 容器 / 对象存储 / 消息 / 无服务器 / 身份 / 数据分析 / AI 等）
- 按 Well-Architected 六支柱组织：安全 / 可靠性 / 性能 / 资源开销 / 运维 / 可持续
- 每题含「说明 / 期望回答 / 改进计划」，支持三档自评（良好 / 部分符合 / 不符合）
- 服务名映射到华为云对应项（GeminiDB→GeminiDB、OBS→OBS、IAM→IAM 等）

---

## 2. 目录

- [1. 简介](#1-简介--overview-critical)
- [2. 目录](#2-目录)
- [3. 架构图](#3-架构图)
- [4. 方案亮点](#4-方案亮点)
- [5. 涉及云服务](#5-涉及云服务)
- [6. 前置条件](#6-前置条件-critical)
- [7. 快速开始](#7-快速开始-critical)
- [8. 分步部署](#8-分步部署)
- [9. 使用方法 / 验证](#9-使用方法--验证-critical)
- [10. 清理资源](#10-清理资源)
- [11. 详细说明](#11-详细说明)
- [12. 依赖](#12-依赖)
- [13. FAQ / 故障排除](#13-faq--故障排除)
- [14. 贡献指南](#14-贡献指南)
- [15. 许可证](#15-许可证-critical)
- [16. 联系方式 / 维护者](#16-联系方式--维护者-critical)

---

## 3. 架构图

> 一次引入多域检查单，形成可量化的架构评估基线。

```
                            ┌────────────┐
                            │ 架构评审者 │
                            └──────┬─────┘
                                   │ 选域
                                   ▼
┌────────────────────────────────────────────────────────────────────┐
│       Well-Architected 检查单库（22 个架构域 / 554 检查项）        │
│             每题含：说明 + 期望回答（参考） + 改进计划             │
└──────┬─────────────┬─────────────┬─────────────┬─────────────┬─────┘


 ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
 │ DATABASE │  │CONTAINER │  │ STORAGE  │  │SERVERLESS│  │ANALYTICS │
 │ GeminiDB │  │   CCE    │  │   OBS    │  │   APIG   │  │   MRS    │
 │  DocDB   │  │   CCI    │  │ Iceberg  │  │   FGS    │  │   DLI    │
 └─────┬────┘  └─────┬────┘  └─────┬────┘  └─────┬────┘  └─────┬────┘
       │             │             │             │             │
       └─────────────┴─────────────┬─────────────┴─────────────┘
                                   ▼
┌────────────────────────────────────────────────────────────────────┐
│                三档自评（良好 / 部分符合 / 不符合）                │
│               产出行动项：责任域 + 优先级 + 目标日期               │
└────────────────────────────────────────────────────────────────────┘
```

**关键组件说明**：
- `src/checklists/`：22 个检查单（共 554 题；每检查单按支柱分节，每题含期望回答与改进计划）
- `docs/lens-notes/`：每份检查单对应一份领域说明（覆盖范围、支柱构成、使用方法）
- `docs/service-mapping.md`：架构域与华为云服务映射表
- 华为云对应服务：每检查单头部标注映射域

### 检查单索引

| 检查单 | 华为云对应服务 | 题量 | 支柱数 |
|---|---|---|---|
| [`APIG-FGS-Lens.md`](src/checklists/APIG-FGS-Lens.md) | APIG + FunctionGraph（无服务器 API） | 21 | 4 |
| [`CCE-Lens.md`](src/checklists/CCE-Lens.md) | ECS 容器服务（容器计算） | 36 | 7 |
| [`CSS-Lens.md`](src/checklists/CSS-Lens.md) | CSS 云搜索（检索） | 31 | 5 |
| [`DCS-Redis-Lens.md`](src/checklists/DCS-Redis-Lens.md) | DCS Redis（缓存） | 22 | 5 |
| [`DI-Lens.md`](src/checklists/DI-Lens.md) | 数据集成服务（ETL） | 14 | 4 |
| [`DLI-SQL-Lens.md`](src/checklists/DLI-SQL-Lens.md) | DLI 数据湖分析（Serverless SQL） | 16 | 4 |
| [`DMS-Lens.md`](src/checklists/DMS-Lens.md) | DMS/Kafka 消息（消息队列） | 33 | 5 |
| [`DocDB-Lens.md`](src/checklists/DocDB-Lens.md) | 云数据库 DocDB/GeminiDB Mongo（文档数据库） | 37 | 6 |
| [`GeminiDB-Lens.md`](src/checklists/GeminiDB-Lens.md) | GeminiDB/分布式键值（键值/NoSQL 数据库） | 48 | 6 |
| [`IAM-Lens.md`](src/checklists/IAM-Lens.md) | IAM 身份认证（身份与访问） | 42 | 5 |
| [`IDP-Lens.md`](src/checklists/IDP-Lens.md) | ModelArts 智能文档（文档 AI） | 53 | 6 |
| [`Iceberg-OBS-Lens.md`](src/checklists/Iceberg-OBS-Lens.md) | OBS 对象存储（对象存储） | 8 | 3 |
| [`MRS-Spark-Lens.md`](src/checklists/MRS-Spark-Lens.md) | MRS 大数据（Spark/Hadoop） | 24 | 5 |
| [`ModelArts-AutoGluon-Lens.md`](src/checklists/ModelArts-AutoGluon-Lens.md) | ModelArts AI 开发（机器学习平台） | 15 | 4 |
| [`ModelArts-Flower-Lens.md`](src/checklists/ModelArts-Flower-Lens.md) | ModelArts AI 开发（机器学习平台） | 10 | 4 |
| [`OBS-Lens.md`](src/checklists/OBS-Lens.md) | OBS 对象存储（对象存储） | 35 | 6 |
| [`ORR-Lens.md`](src/checklists/ORR-Lens.md) | 运维就绪检查（运维就绪度（ORR）） | 16 | 3 |
| [`Passport-Lens.md`](src/checklists/Passport-Lens.md) | 架构评估护照（整体架构评估） | 11 | 1 |
| [`Recommend-Lens.md`](src/checklists/Recommend-Lens.md) | 推荐服务/ModelArts（个性化推荐） | 11 | 4 |
| [`SaaS-Anywhere-Lens.md`](src/checklists/SaaS-Anywhere-Lens.md) | SaaS 多租户检查单（SaaS 架构评估） | 18 | 6 |
| [`SaaS-Business-Lens.md`](src/checklists/SaaS-Business-Lens.md) | SaaS 多租户检查单（SaaS 架构评估） | 29 | 5 |
| [`Streaming-Media-Lens.md`](src/checklists/Streaming-Media-Lens.md) | 通用流媒体检查单（流媒体架构评估） | 24 | 5 |

---

## 4. 方案亮点

- **多域覆盖**：数据库/存储/容器/无服务器/消息/身份/分析/AI，一站齐备
- **标准检查结构**：六支柱 + 三档自评 + 行动项输出，可直接用于评审会议
- **服务映射**：问题语义保留，服务名映射华为云（可执行、不产生假服务）
- **离线可用**：Markdown 模板，无云资源依赖

---

## 5. 涉及云服务

| 服务 | 用途 | 备注 |
|---|---|---|
| （检查单对象） | 各架构域评估 | 检查单项映射到：GeminiDB / OBS / ECS / CCI / DCS / DLI / MRS / CSS / ModelArts / IAM 等 |
| 检查单本身 | 离线模板 | 不部署任何云资源 |

> **提示**：本仓库为评估检查单模板库，无 IaC 部署、无运行时资源。

---

## 6. 前置条件

| 项 | 要求 | 说明 |
|---|---|---|
| **账号** | 无需云账号即可使用检查单 | 离线评估模板 |
| **参与人** | 架构师 / 运维 / 安全负责人 | 各域负责人参与自评 |
| **信息** | 目标架构的服务清单与访问模式 | 评估输入 |
| **Region** | 不适用 | 检查单与区域无关 |

---

## 7. 快速开始

### 使用检查单（推荐）

```bash
# 1. 克隆本仓库
git clone <repo-https-url> lean-governance-custom-lens-wa
cd lean-governance-custom-lens-wa

# 2. 查阅检查单列表与映射
ls src/checklists/

# 3. 选择目标架构域的检查单（如对象存储）
cat "src/checklists/OBS-Lens.md"

# 4. 逐题自评（良好/部分符合/不符合），将不符合项形成行动清单
```

> **完整步骤与每步预期输出**：参见 [第 8 节「分步部署」](#8-分步部署)。

---

## 8. 分步部署

### 步骤 1：选择检查单

```bash
ls src/checklists/ | head -8
```

### 步骤 2：逐域评估

```bash
cat src/checklists/GeminiDB-Lens.md    # 键值/NoSQL
cat src/checklists/CCE-Lens.md       # 容器
```

### 步骤 3：记录行动项

```text
| 检查项 | 自评 | 行动 | 责任域 | 优先级 |
```

### 步骤 4：汇总与跟踪

汇总所有域行动项，指定责任人与目标日期；复查时更新自评。

---

## 9. 使用方法 / 验证

> **强制实测**：本节所列命令在交付前已经 agent 实际执行验证，可运行且输出与描述一致。检查单为离线模板，实测 = 检查单可执行性抽样核验。

### 验证 1：检查单完整性

```bash
# 22 个检查单，554 检查项
find src/checklists -name "*.md" | wc -l
```

### 验证 2：题目可读性

```bash
# 抽查某检查单，确认问题/期望/改进计划齐全
grep -c "^###" "src/checklists/GeminiDB-Lens.md"
```

### 验证 3：服务映射

```bash
grep "华为云对应" src/checklists/*.md
```

### 验证 4：样例评估（推荐）

选一个真实架构，用对应检查单走一遍自评 → 输出行动项 3~5 条。

---

## 10. 清理资源

检查单为离线模板，**无云资源，无需清理**。

---

## 11. 详细说明

### 工作流程

1. 按架构域选检查单（数据库→DDB lens、存储→OBS lens、整体→Passport/ORR…）
2. 逐题自评并记录「期望回答」对照
3. 不符合/部分符合项 → 行动项（责任域 + 优先级）
4. 复查周期更新自评，跟踪改进

### 配置项

| 项 | 说明 |
|---|---|
| 自评档位 | 良好 / 部分符合 / 不符合 |
| 行动项 | 检查项 + 自评 + 行动 + 责任域 + 优先级 |

### 接口 / API

无对外 API；输出为 Markdown 检查单与人工行动清单。

---

## 12. 依赖

### 主要依赖

| 名称 | 版本 | 用途 |
|---|---|---|
| 无 | — | 纯 Markdown 模板，零依赖 |

---

## 13. FAQ / 故障排除

### Q1：检查单里的服务名与原架构不一致？

**A**：每检查单头部标注了华为云对应服务域；题目为最佳实践语义，可按实际技术栈调整措辞。

### Q2：如何新增一个服务域的检查单？

**A**：参照 `src/checklists/` 任一模板（支柱分节 + 题目 + 期望 + 改进计划），或提供对应 JSON 用脚本转译。

### Q3：评估结果怎么量化？

**A**：推荐统计「良好/部分/不符合」题数比 + 行动项数量，跨周期对比改进趋势。

### 故障排查清单

| 现象 | 可能原因 | 排查方法 |
|---|---|---|
| 检查单缺失某域 | 该域尚无检查单 | 查 [`docs/service-mapping.md`](docs/service-mapping.md) 映射表并补充检查单 |
| 题目措辞偏英文 | 题目原文为英文 | 保留语义；需中文可自行翻译（建议保留 ID 便于引用） |

---

## 14. 贡献指南

欢迎提交 Issue 与 PR。请遵循以下流程：

1. **Issue**：描述问题 / 建议
2. **PR**：基于 `main` 分支新建 feature 分支；新增检查单注意支柱结构完整
3. **Code Review**：由 **[@<github-username>](https://github.com/<github-username>)** reviewer 审核通过后合并

详细规范参见 `CONTRIBUTING.md`（如有）。

---

## 15. 许可证

本实践采用 **MIT No Attribution** 许可证发布。详见仓库根目录 [`LICENSE`](LICENSE) 文件。

```
MIT No Attribution

Copyright (c) Huawei Cloud

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software... (no attribution required)
```

---

## 16. 联系方式 / 维护者

| 项 | 内容 |
|---|---|
| **创建者** | [@<github-username>](https://github.com/<github-username>) |
| **维护者** | [@<github-username>](https://github.com/<github-username>) |
| **联系方式** | GitHub Issues / PR（见 [第 14 节](#14-贡献指南)） |

---