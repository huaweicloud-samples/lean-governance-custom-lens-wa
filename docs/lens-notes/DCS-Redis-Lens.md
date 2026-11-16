# 缓存 检查单说明

> 本文件说明本仓 `DCS-Redis-Lens.md` 的定位、覆盖范围与使用方法。该检查单是 内存缓存的运维、安全、可靠性与性能最佳实践。

**华为云对应服务**：DCS Redis（缓存）
**检查单文件**：`src/checklists/DCS-Redis-Lens.md`
**题目总数**：22 题，覆盖 5 个支柱

## 覆盖支柱

| 支柱 | 题量 |
|---|---|
| Operational excellence | 5 |
| Security | 6 |
| Reliability | 4 |
| Performance efficiency | 5 |
| efficiency optimization | 2 |

## 评估方法

1. 逐题对照本仓架构给出**良好 / 部分符合 / 不符合**三档自评
2. 对「部分符合 / 不符合」的题目，参照检查单内的「期望回答（参考）」生成行动项
3. 行动项需明确责任域、优先级与目标日期

## 与其他检查单的关系

本检查单覆盖**缓存**单一架构域。若目标架构同时涉及其他服务域（如存储、身份、消息），请配套使用对应的领域检查单，避免只评估局部而遗漏跨域依赖。

## 题目结构约定

每个检查单统一由以下部分组成：

- **评估说明**：三档自评规则
- **支柱章节**（`## <支柱>（N 题）`）：按支柱组织题目
- **题目条目**（`### <编号> <标题>`）：含「说明」「期望回答（参考）」，部分题目附带改进计划

## 相关文档

- 检查单库总览与使用方式：[`README.md`](../../README.md)
- 中文版：[`README.cn.md`](../../README.cn.md)
- 架构说明：[`docs/architecture.md`](../architecture.md)
- 使用指导书：[`docs/deployment-guide.md`](../deployment-guide.md)
