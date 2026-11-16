# 架构域与华为云服务映射表

本表列出检查单库覆盖的**架构域**及其**华为云对应服务**。检查单内的题目语义保持通用最佳实践原意，仅服务名映射为华为云对应服务。

| 架构域 | 华为云对应服务 | 检查单文件 | 对齐度 | 说明 |
|---|---|---|---|---|
| 键值 / NoSQL | GeminiDB / 分布式键值 | `src/checklists/GeminiDB-Lens.md` | 🟡 | 题目语义保留 |
| 文档数据库 | 云数据库 DocDB / GeminiDB Mongo | `src/checklists/DocDB-Lens.md` | 🟡 | 题目语义保留 |
| 容器 | 华为CCE 容器集群 / CCI | `src/checklists/CCE-Lens.md` | 🟡 | 题目语义保留 |
| 对象存储 | OBS | `src/checklists/OBS-Lens.md` | 🟡 | 题目语义保留 |
| 开放表格式 | OBS + 开放表格式 | `src/checklists/Iceberg-OBS-Lens.md` | 🟡 | 题目语义保留 |
| 消息 | DMS / Kafka | `src/checklists/DMS-Lens.md` | 🟡 | 题目语义保留 |
| 身份 | IAM 身份认证 | `src/checklists/IAM-Lens.md` | 🟡 | 题目语义保留 |
| 无服务器 API | APIG + FunctionGraph | `src/checklists/APIG-FGS-Lens.md` | 🟡 | 题目语义保留 |
| Serverless SQL | DLI | `src/checklists/DLI-SQL-Lens.md` | 🟡 | 题目语义保留 |
| 大数据 | MRS | `src/checklists/MRS-Spark-Lens.md` | 🟡 | 题目语义保留 |
| 数据集成（ETL） | 数据集成服务 | `src/checklists/DI-Lens.md` | 🟡 | 题目语义保留 |
| 缓存 | DCS Redis | `src/checklists/DCS-Redis-Lens.md` | 🟡 | 题目语义保留 |
| 检索 | CSS | `src/checklists/CSS-Lens.md` | 🟡 | 题目语义保留 |
| 文档 AI | ModelArts 智能文档 | `src/checklists/IDP-Lens.md` | 🟡 | 题目语义保留 |
| 个性化推荐 | 推荐服务 / ModelArts | `src/checklists/Recommend-Lens.md` | 🟡 | 题目语义保留 |
| AI 开发 | ModelArts AI 开发 | `src/checklists/ModelArts-AutoGluon-Lens.md`、`src/checklists/ModelArts-Flower-Lens.md` | 🟡 | 题目语义保留 |
| 流媒体 | 通用流媒体检查单 | `src/checklists/Streaming-Media-Lens.md` | 🟡 | 题目语义保留 |
| 整体评估 | 架构评估护照 / 运维就绪检查 | `src/checklists/Passport-Lens.md`、`src/checklists/ORR-Lens.md` | 🟢 | 平台无关 |
| SaaS 多租户 | SaaS 多租户检查单 | `src/checklists/SaaS-Anywhere-Lens.md`、`src/checklists/SaaS-Business-Lens.md` | 🟢 | 平台无关 |

**对齐度图例**

| 标记 | 含义 |
|---|---|
| 🟢 | 平台无关检查项，题目不涉及具体云服务，可直接使用 |
| 🟡 | 题目语义完整保留，仅服务名映射为华为云对应服务 |

**结论**：无需要止损的服务；全部为 🟡 / 🟢。检查单为**检查项模板数据**（非运行系统），转写后语义完整保留。

## 扩展新架构域

新增架构域时，按 [`docs/lens-notes/Custom-Lens-Creation-Guide.md`](lens-notes/Custom-Lens-Creation-Guide.md) 的模板约定新建检查单，并在本表中追加对应行。
