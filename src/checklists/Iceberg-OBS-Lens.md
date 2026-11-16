# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：OBS 对象存储（对象存储）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（3 题）

### PERF1 How you optimizing read performance

说明：Optimizing data layout and file size in Iceberg tables is crucial for data pruning in order to maintain query efficiency, especially at scale with large datasets.

期望回答（参考）：
- Partition your data
- Use hidden partitioning
- Use partition evolution
- Set target file and row group size
- Run regular compaction
- Optimize column statistics
- Choose the right update/delete strategy
- Use ZSTD compression
- Set the sort order

### PERF2 How you optimizing write performance

说明：Iceberg's write performance is optimized through strategic configuration choices that eliminate unnecessary processing overhead.

期望回答（参考）：
- Set the table write distribution mode
- Choose the right update/delete strategy
- Choose the right file format
- Manage concurrent write conflicts
- Set that granularity to file

### PERF3 Have you use last version of Icebreg

说明：The format version number is incremented when new features are added that will break forward-compatibility. Versions 1 and 2 of the Iceberg spec are complete and adopted by the community. Version 3 is under active development and has not been formally adopted.

期望回答（参考）：
- Use Iceberg format version 2

---

## OPS — Operational Excellence（4 题）

### OPS1 How you manage your data catalog

说明：Iceberg has several catalog back-ends that can be used to track tables, like JDBC, Hive MetaStore and DLI. Each has its characteristics. We recommand you DLI catalog as its cloud-native and better scalability.

期望回答（参考）：
- Use the Huawei Cloud DLI Data Catalog as your data catalog
- Use the Huawei Cloud DLI Data Catalog as lock manager

### OPS2 How you maintaining iceberg tables

说明：Iceberg requires regular maintenance operations since it uses a multi-layered metadata approach that accumulates state over time. Without maintenance, tables experience degraded query performance from fragmented metadata, excessive storage resource utilization from unreferenced files, and slower scan planning due to metadata bloat, ultimately compromising the performance advantages that make Iceberg valuable.

期望回答（参考）：
- Expire Snapshots
- Remove old metadata files
- Delete orphan files
- Compact data files
- Rewrite manifests

### OPS3 What's your compaction strategy

说明：Iceberg supports multiple compaction strategies. This flexibility allows organizations to tailor their maintenance approach to their specific query patterns, data freshness requirements, and computational resource constraints.

期望回答（参考）：
- Running bin packing compaction
- Running compaction to sort data
- Running compaction to cluster the data using z-order sorting
- Running compaction on partitions that might be updated by other applications because of late-arriving data

### OPS4 Do you konw to troubleshooting when using Iceberg workloads in OBS

说明：This section discusses Iceberg properties that you can use to optimize Iceberg's interaction with OBS.

期望回答（参考）：
- Prevent hot partitioning (HTTP 503 errors)
- Use Iceberg maintenance operations to release unused data
- Replicate data across Huawei Cloud Regions

---

## resource utilization — Efficiency Optimization（1 题）

### COST1 Do you know how optimizing storage effect to your storage resource utilization

说明：Iceberg designs to keep the historical data and snapshots for time travel.  Implementing strategic snapshot retention policies and running regular orphan file cleanup. For compliance requirements, moving the old objects to appropriate OBS storage classes can optimize your storage resource utilization. 

期望回答（参考）：
- Enable OBS Intelligent-Tiering
- Archive or delete historic snapshots
- Delete orphan files

---


*检查项合计：8 题*
