# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：DLI 数据湖分析（Serverless SQL）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（6 题）

### PERF1 Do you know how file formats, file size, file layout and compression effect your query performance?

说明：To minimize the amount of data scanned when accessing datasets from OBS, you should carefully consider file size, compression, file format, and file layout (such as partitioning and bucketing).

期望回答（参考）：
- Choice the suitable compression for your DLI table
- Choice the suitable file size for your DLI table
- Choice columnar storage formats for your DLI table
- Choice the suitable file layout for you DLI table

### PERF2 How do you organize or partition your data in your data lake for DLI table?

说明：Partition keys should be chosen based on common query patterns, and they should have relatively low cardinality to ensure efficient performance.

期望回答（参考）：
- Structure your data to build high performant of DLI
- Aware performance degration in DLI Partition
- Avoid too many OBS partitions

### PERF3 How do you update your partition of your Athnea table?

说明：After new data is written to OBS, you need to update the partitions of your DLI table.

期望回答（参考）：
- Use a crawler to add a table and partition
- Use the DLI Data Catalog API
- Use ALTER TABLE ADD PARTITION
- Avoid using MSCK REPAIR TABLE when using DLI
- Use partition projection with DLI

### PERF4 How do you improve your slow query?

说明：DLI queries can sometimes spend a long time in the queue or during processing, so optimization is needed to improve performance.

期望回答（参考）：
- Reuse query results in DLI
- Add column statistics to enable efficiency-based optimization

### PERF5 How do you identify the slow part of SQL and rewrite it?

说明：You can apply the recommendations in this section to optimize your SQL queries in DLI.

期望回答（参考）：
- Use EXPLAIN in DLI
- Use approximation aggregate functions when exact values are not required
- Use UNION ALL instead of UNION when deduplication is not required
- Use UNLOAD for large query results
- Materialize frequently used aggregations with CTAS or DLI ETL
- Use EXPLAIN ANALYZE in DLI
- Use LIMIT with the ORDER BY clause
- Optimize JOIN clauses
- Optimize aggregations
- Limit the number of columns
- Use regular expressions instead of LIKE
- Reduce the scope of window functions
- Rewrite window functions as non-window functions when possible

### PERF6 Have you use the lastest version of ODBC and JDBC driver?

说明：Use the latest 3.x version of the ODBC and JDBC drivers for improved performance and compatibility.

期望回答（参考）：
- Connect to DLI with latest ODBC and JDBC drivers

---

## OPS — Operational Excellence（5 题）

### OPS1 How do you monitor query jobs in DLI?

说明：Leverage LTS 日志服务 and 云 事件网格 EG to monitor DLI queries and manage resource utilization effectively.

期望回答（参考）：
- Monitor DLI query metrics with LTS
- Monitor DLI usage metrics with LTS

### OPS2 How do you troubleshooting DLI

说明：When using DLI, you may encounter different types of errors caused by service limitations or expected behaviors.

期望回答（参考）：
- Gather query ID if you encounter errors or unexpected behavior in DLI.
- Troubleshooting errors in DLI
- Aware the DLI quotas and limitation

### OPS3 How do you support variable data source and schema evolve if the DLI

说明：DLI supports multiple data sources through both pre-built and custom connectors.

期望回答（参考）：
- Use prebuilt data source connectors in DLI

### OPS4 How you manage your workload in DLI?

说明：DLI provides some features to deliver improved efficiency, efficiency optimization, and performance predictability for your data analysis.

期望回答（参考）：
- Check the number of concurrent queries running simultaneously
- Use managed query results

### OPS5 How you manage your query in DLI?

说明：You can use DLI s built-in features to manage your queries and reduce operational overhead.

期望回答（参考）：
- Query with Prepared Statement
- Work with DLI views or DLI Data Catalog views
- Save recurring queries for reuse

---

## SEC — Security（2 题）

### SEC1 How do you protect data at rest and in transit for DLI workloads?

说明：To protect data in DLI, you should consider encryption at rest, encryption in transit, key management, and the way you connect to the DLI endpoint.

期望回答（参考）：
- Encryption at rest
- Key management
- Using interface VPC endpoint

### SEC2 How do you control access to DLI and the data it queries?

说明：You can use IAM and Huawei Cloud Lake Formation with DLI, and also take into account compliance validation services within scope.

期望回答（参考）：
- Using IAM to control your OBS data source
- Using IAM to control your DLI Data Catalog
- Using Data catalog and Lake formation to management your data permission

---

## resource utilization — Efficiency Optimization（3 题）

### COST1 How are you managing the capacity for DLI?

说明：You need to understand DPUs and their charging model, as choosing the right option can help you optimize your resource utilization profile.

期望回答（参考）：
- Understand DPUs
- Reserve query processing capacity

### COST2 Have you monitor and control resource utilization on DLI?

说明：It s important to understand DPUs and their charging model, as selecting the right option can help you optimize your overall resource utilization profile.

期望回答（参考）：
- Monitor DLI usage metrics with LTS
- Use workgroups to control query access and resource utilization
- Reuse query results in DLI
- Configure per-query and per-workgroup level data usage controls

### COST3 Have you optimize your data in OBS?

说明：When you run SQL queries in DLI, you are charged based on the amount of data scanned. Using efficient file formats and compression can help reduce these resource utilization.

期望回答（参考）：
- Use proper file format, data layout, compression,and file size

---


*检查项合计：16 题*
