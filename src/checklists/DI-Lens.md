# 数据集成服务 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：数据集成服务（ETL）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（5 题）

### PERF1 Do konw how file formats, file size, file layout and compression effect your job performance?

说明：To reduce the amount of data loaded into your job when reading from OBS, you need to consider FileSize, Compression, FileFormat and FileLayout (Partitions) for your dataset.

期望回答（参考）：
- Choice the suitable file format for you DLI ETL Job
- Choice the suitable file size for you DLI ETL Job
- Choice the suitable compression for you DLI ETL Job
- Choice the suitable file layout for you DLI ETL Job
- Parameters used to interact with data formats and compression in Huawei Cloud DLI

### PERF2 How do you determine compute unit for your DLI Job?

期望回答（参考）：
- Benchmarking using DLI TPC-DS Connector or custom dataset
- Debugging demanding stages and straggler tasks
- Visualize the profiled metrics on the Huawei Cloud DLI console
- Calculating and Monitoring for DPU capacity planning
- Have you enable Auto Scaling in DLI?

### PERF3 How do you organize or partition your data in your data lake for DLI Jobs friendly?

期望回答（参考）：
- Structure your data to build high performant of DLI Job
- Awareness of performance degration in DLI partition
- Avoid too many OBS partitions
- For database and JDBC, Specify a where predicate in a SQL query to reduce data scan

### PERF4 Do you know how to parallelize tasks based on your parition?

说明：It is important to parallelize tasks for data loads and transformations

期望回答（参考）：
- Monitor parallelize tasks
- Parallelize data load from OBS
- Parallelize data load from JDBC
- Parallelize data load from GeminiDB using traditional ETL connector
- Parallelize data load from DIS Data Streams
- Parallelize tasks after data load
- Monitor data scan

### PERF5 How do you identified and improve your slow running job?

期望回答（参考）：
- Identify your slow stage in spark history
- Identify too big DAG in spark history and log
- Identify your job is waiting for cluster resources
- Know the difference between Huawei Cloud DLI Dynamic frame, Apache Spark Dataframe, Apache Spark RDD
- Identify and optimize data skew
- Optimze shuffles and related action
- Minimize planning overhead
- Optimize User Defined Functions
- Updage your spark and DLI version to lasest version

---

## OPS — Operational Excellence（5 题）

### OPS1 How do you monitor ETL jobs in Huawei Cloud DLI?

期望回答（参考）：
- Enable Huawei Cloud tags in Huawei Cloud DLI
- Automating Huawei Cloud DLI with LTS Events
- Logging Huawei Cloud DLI API calls with Huawei Cloud CTS

### OPS2 How do you monitor your Spark Job on Huawei Cloud DLI

期望回答（参考）：
- Monitoring jobs using the Apache Spark web UI
- Monitoring with Huawei Cloud DLI job run insights
- Monitoring with LTS 日志服务
- Job monitoring and debugging

### OPS3 How do you troubleshooting Huawei Cloud DLI

期望回答（参考）：
- Gathering Huawei Cloud DLI troubleshooting information
- Troubleshooting errors in Huawei Cloud DLI
- Huawei Cloud DLI machine learning exceptions
- Build data lineage for data lakes using Huawei Cloud DLI
- Huawei Cloud DLI quotas

### OPS4 How do you support variable data source and schema evolve if the DLI Job?

期望回答（参考）：
- Defining connections in the Huawei Cloud DLI Data Catalog
- Evolving and adding new partitions in the Data Catalog from Huawei Cloud DLI ETL jobs
- Adding classifiers to a crawler to support Custom datasets in Huawei Cloud DLI
- Centrally discover, control, and evolve data stream schemas
- Simplify data integration pipeline development using Huawei Cloud DLI custom blueprints

### OPS5 How do you create and deploy your DLI Job

期望回答（参考）：
- Developing Huawei Cloud DLI ETL jobs locally using a container
- Deploy an Huawei Cloud DLI job with your CI/CD pipeline

---

## SEC — Security（2 题）

### SEC1 How do you protect data in Huawei Cloud DLI?

期望回答（参考）：
- Encryption at rest
- Encryption in transit
- Identify the FIPS compliance requirement
- Restrict access to your Huawei Cloud DLI Data Catalog
- Awareness of Huawei Cloud DLI dependency on other Huawei Cloud services
- Use development endpoint to develop and test your Huawei Cloud DLI scripts

### SEC2 How do you manage your identity and access in Huawei Cloud DLI

期望回答（参考）：
- Identity-based policies (IAM policies) for access control
- Huawei Cloud DLI resource policies for access control
- Granting cross-account access

---

## resource utilization — Efficiency Optimization（2 题）

### COST1 How are you choosing the right compute unit and worker type for DLI Job?

期望回答（参考）：
- Developing Huawei Cloud DLI ETL jobs locally using a container
- Structure your data to build high performant of DLI Job
- Using auto scaling for Huawei Cloud DLI
- Smaller worker type for streaming jobs
- Flex-based jobs for non-urgent ETL jobs

### COST2 Have you monitor and optimize resource utilization on Huawei Cloud DLI for Apache Spark?

期望回答（参考）：
- Monitor overall resource utilization on Huawei Cloud DLI for Apache Spark
- Monitor individual job run resource utilization
- Set the job s timeout period appropriately
- Interactive sessions
- Upgrade to the latest version
- Performance tuning to optimize resource utilization

---


*检查项合计：14 题*
