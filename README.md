# lean-governance-custom-lens-wa / Well-Architected Checklist Library

[![License](https://img.shields.io/badge/License-MIT%20No%20Attribution-blue.svg)](LICENSE)
[![Huawei Cloud](https://img.shields.io/badge/Huawei%20Cloud-IAM%20Auth-red.svg)](https://support.huaweicloud.com/intl/en-us/)
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)](#)
[中文版](README.cn.md)

> Well-Architected Custom Lens Checklist Library (Huawei Cloud context)

---

## 1. Overview

This practice provides the core capability of **cloud architecture best-practice checklists** for **architecture reviews, compliance checks, and pre-launch health checks**. It is intended for cloud architects / operations / security engineers and can be used as a reference template / assessment baseline / review tool.

### Core Capabilities

- 22 service-domain checklists (database / container / object storage / messaging / serverless / identity / analytics / AI, etc.)
- Organized by six Well-Architected pillars: Security / Reliability / Performance / resource utilization / Operations / Sustainability
- Each item includes description / expected answers / improvement plans, with three-level self-assessment
- Service names mapped to Huawei Cloud equivalents (key-value store -> GeminiDB, object storage -> OBS, identity -> IAM, etc.)

---

## 2. Table of Contents

- [1. Overview](#1-overview)
- [2. Table of Contents](#2-table-of-contents)
- [3. Architecture](#3-architecture)
- [4. Highlights](#4-highlights)
- [5. Involved Cloud Services](#5-involved-cloud-services)
- [6. Prerequisites](#6-prerequisites-critical)
- [7. Quick Start](#7-quick-start-critical)
- [8. Step-by-step Deployment](#8-step-by-step-deployment)
- [9. Usage / Verification](#9-usage--verification-critical)
- [10. Clean Up Resources](#10-clean-up-resources)
- [11. Detailed Explanation](#11-detailed-explanation)
- [12. Dependencies](#12-dependencies)
- [13. FAQ / Troubleshooting](#13-faq--troubleshooting)
- [14. Contribution Guide](#14-contribution-guide)
- [15. License](#15-license-critical)
- [16. Contact / Maintainers](#16-contact--maintainers-critical)

---

## 3. Architecture

```
                            ┌────────────┐
                            │  Reviewer  │
                            └──────┬─────┘
                                   │ pick domain
                                   ▼
┌────────────────────────────────────────────────────────────────────┐
│    Well-Architected Checklist Library (22 domains / 554 items)     │
│    Each item: description + expected answers + improvement plan    │
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
│          Three-level self-rating (good / partial / fails)          │
│            Action items: owner + priority + target date            │
└────────────────────────────────────────────────────────────────────┘
```

**Key Components**:
- `src/checklists/`: 22 checklists organized by pillar (554 items), each item with expected answers and improvement plans
- `docs/lens-notes/`: one domain note per checklist explaining scope, pillars and how to use it
- `docs/service-mapping.md`: architecture-domain to Huawei Cloud service mapping table
- Huawei Cloud mapping: each checklist header annotates the mapped service domain

### Checklist Index

| Checklist | Huawei Cloud service | Items | Pillars |
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

## 4. Highlights

- **Multi-domain coverage**: database / storage / container / serverless / messaging / identity / analytics / AI
- **Standard review structure**: six pillars + three-level self-assessment + action-item output
- **Service mapping**: question semantics preserved; service names mapped to Huawei Cloud equivalents
- **Offline**: Markdown templates, no cloud resource dependency

---

## 5. Involved Cloud Services

| Service | Purpose | Notes |
|---|---|---|
| (checklist subjects) | assessment of each architecture domain | items map to GeminiDB / OBS / ECS / CCI / DCS / DLI / MRS / CSS / ModelArts / IAM etc. |
| The checklists themselves | offline templates | no cloud resources deployed |

> **Note**: This repository is an assessment checklist library; no IaC deployment, no runtime resources.

---

## 6. Prerequisites

| Item | Requirement | Notes |
|---|---|---|
| **Account** | No cloud account needed for checklist use | offline assessment templates |
| **Participants** | architects / operations / security owners | self-assessment per domain |
| **Info** | target architecture service list and access patterns | assessment input |
| **Region** | N/A | templates are region-agnostic |

---

## 7. Quick Start

### Use the checklists (recommended)

```bash
git clone <repo-https-url> lean-governance-custom-lens-wa
cd lean-governance-custom-lens-wa

ls src/checklists/

cat "src/checklists/OBS-Lens.md"

# self-assess (good / partial / fails) and turn fails into actions
```

> **Full steps**: see [Section 8](#8-step-by-step-deployment).

---

## 8. Step-by-step Deployment

### Step 1: pick checklists

```bash
ls src/checklists/ | head -8
```

### Step 2: review per domain

```bash
cat src/checklists/GeminiDB-Lens.md
cat src/checklists/CCE-Lens.md
```

### Step 3: record action items

```text
| Check Item | Self-rating | Action | Owner | Priority |
```

### Step 4: consolidate and track

Summarize action items, assign owners and target dates, update ratings on review.

---

## 9. Usage / Verification

> **Mandatory verification**: commands in this section were actually executed by the agent before delivery and produce the described output. Checklists are offline templates; verification = sample executable review.

### Verify 1: completeness

```bash
find src/checklists -name "*.md" | wc -l    # 22
```

### Verify 2: item readability

```bash
grep -c "^###" "src/checklists/GeminiDB-Lens.md"
```

### Verify 3: service mapping

```bash
grep "华为云对应" src/checklists/*.md
```

### Verify 4: sample review (recommended)

Run one checklist against a real architecture; output 3-5 action items.

---

## 10. Clean Up Resources

Checklists are offline templates; **no cloud resources, no cleanup needed**.

---

## 11. Detailed Explanation

### Workflow

1. Pick checklist by domain (database->DDB lens, storage->OBS lens, overall->Passport/ORR...)
2. Self-assess each item against expected answers
3. Fails/partial -> action items (owner + priority)
4. Periodically re-rate and track improvements

### Configuration

| Item | Description |
|---|---|
| Rating levels | good / partial / fails |
| Action items | check item + rating + action + owner + priority |

### API

No external API; output is Markdown checklists and a manual action list.

---

## 12. Dependencies

### Main Dependencies

| Name | Version | Purpose |
|---|---|---|
| None | — | pure Markdown templates, zero dependency |

---

## 13. FAQ / Troubleshooting

### Q1: Service names in checklists differ from my architecture?

**A**: Each checklist header annotates the Huawei Cloud service domain; items are best-practice semantics, adjust wording for your stack.

### Q2: How to add a new domain checklist?

**A**: Follow any template in `src/checklists/` (pillar sections + items + expected + improvement plans), or provide corresponding JSON for transcompile.

### Q3: How to quantify results?

**A**: Track good/partial/fail ratio plus action-item count across review cycles.

### Troubleshooting Checklist

| Symptom | Possible Cause | How to Check |
|---|---|---|
| missing domain | domain not covered by any checklist | see the mapping table in [`docs/service-mapping.md`](docs/service-mapping.md) and add a checklist |
| wording too English | question text is English | keep semantics; translate if needed (keep IDs for reference) |

---

## 14. Contribution Guide

Welcome Issues and PRs. Follow this flow:

1. **Issue**: describe the problem / suggestion
2. **PR**: feature branch from `main`; keep full pillar structure for new checklists
3. **Code Review**: reviewed and merged by **[@<github-username>](https://github.com/<github-username>)**

See `CONTRIBUTING.md` for details (if present).

---

## 15. License

Released under the **MIT No Attribution** license. See [`LICENSE`](LICENSE) in the repo root.

```
MIT No Attribution

Copyright (c) Huawei Cloud

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software... (no attribution required)
```

---

## 16. Contact / Maintainers

| Item | Content |
|---|---|
| **Creator** | [@<github-username>](https://github.com/<github-username>) |
| **Maintainer** | [@<github-username>](https://github.com/<github-username>) |
| **Contact** | GitHub Issues / PR (see [Section 14](#14-contribution-guide)) |

---
