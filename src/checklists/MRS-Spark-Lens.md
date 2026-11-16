# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：MRS 大数据（Spark/Hadoop）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（5 题）

### PERF1 Do konw how file formats, file size, file layout and compression effect your job performance?

说明：To reduce the amount of data loaded into your job when reading from OBS, you need to consider FileSize, Compression, FileFormat and FileLayout (Partitions) for your dataset.

期望回答（参考）：
- Choose the suitable file format for your Spark on MRS job
- Choose the suitable file size for your Spark on MRS job
- Choose the suitable compression for your Spark on MRS job
- Choose the suitable file layout and partitioning strategy
- Configure Spark parameters for data formats and compression on MRS

### PERF2 How do you determine compute unit for your MRS Job?

期望回答（参考）：
- Benchmark using TPC-DS or custom datasets on MRS
- Debug demanding stages and straggler tasks
- Use Spark UI and YARN metrics to profile job resource usage
- Right-size MRS instances based on workload characteristics
- Enable MRS Managed Scaling for dynamic capacity

### PERF3 How do you organize or partition your data in your data lake for Spark on MRS Jobs friendly?

期望回答（参考）：
- Structure data partitions to match query patterns
- Manage partition metadata performance in DLI Data Catalog
- Avoid excessive OBS partitions
- Use predicate pushdown for JDBC and database sources

### PERF4 Do you know how to parallelize tasks based on your parition?

说明：It is important to parallelize tasks for data loads and transformations

期望回答（参考）：
- Monitor job parallelism
- Parallelize data loads from OBS
- Parallelize data loads from JDBC sources
- Parallelize data loads from GeminiDB
- Parallelize data loads from DIS Data Streams
- Control parallelism after data load with repartition and shuffle partitions
- Monitor data scan volume

### PERF5 How do you identified and improve your slow running job?

期望回答（参考）：
- Identify slow stages in Spark History Server
- Identify overly large DAGs
- Identify resource waiting and scheduling delays
- Use Spark DataFrame API over RDD API
- Identify and optimize data skew
- Optimize shuffles and reduce unnecessary data movement
- Minimize query planning overhead
- Optimize User Defined Functions
- Keep MRS and Spark versions up to date

---

## OPS — Operational Excellence（6 题）

### OPS1 How do you monitor ETL jobs in Spark on MRS?

说明：Monitoring MRS clusters and Spark jobs is essential for operational visibility. This includes tracking cluster state changes, job execution status, resource utilization, and audit trails for governance and compliance.

期望回答（参考）：
- Enable Huawei Cloud tags on MRS clusters
- Automate MRS job event responses with 云 事件网格 EG
- Log Spark on MRS API calls with Huawei Cloud CTS
- Enable MRS cluster logging to OBS

### OPS2 How do you monitor your Spark Job on Spark on MRS?

说明：Monitoring individual Spark job performance is critical for identifying bottlenecks, optimizing resource usage, and ensuring SLA compliance. This includes leveraging Spark UI, LTS metrics, and observability platforms.

期望回答（参考）：
- Monitor jobs using the Spark History Server and Spark Web UI
- Monitor jobs using MRS cluster and LTS metrics
- Set up Spark observability with Prometheus and Grafana or Managed Services

### OPS3 How do you troubleshoot Spark on MRS?

说明：Effective troubleshooting requires systematic log analysis, understanding of common failure patterns, and knowledge of MRS-specific diagnostic tools. This covers gathering diagnostic information, resolving common errors, and handling capacity issues.

期望回答（参考）：
- Gathering Spark on MRS troubleshooting information
- Troubleshooting common errors in Spark on MRS
- Troubleshoot MRS node and cluster capacity issues
- Spark on MRS quotas and API throttling
- Troubleshoot HDFS health issues (missing blocks, corruption, under-replication)

### OPS4 How do you support variable data source and schema evolution in Spark on MRS?

说明：As data pipelines evolve, schemas change and new data sources are added. Using centralized metadata management and open table formats ensures backward compatibility and operational continuity.

期望回答（参考）：
- Use the Huawei Cloud DLI Data Catalog as a centralized metastore for MRS
- Handle schema evolution using Apache Iceberg or Apache Hudi on MRS
- Standardize and reuse pipeline patterns using Infrastructure as Code

### OPS5 How do you create and deploy your Spark on MRS Job?

说明：A robust development and deployment workflow for Spark on MRS includes local development and testing, CI/CD integration, and choosing the right deployment mode for production.

期望回答（参考）：
- Developing Spark on MRS ETL jobs locally using a container
- Deploy Spark on MRS jobs with your CI/CD pipeline
- Choose the right Spark deploy mode (client vs cluster)

### OPS6 How do you ensure your MRS cluster uses the latest and most performant configuration?

说明：Keeping MRS clusters up to date with the latest releases, AMIs, and runtime optimizations is essential for performance, security, and resource utilization efficiency.

期望回答（参考）：
- Use the most recent MRS version and AMI
- Treat all MRS clusters as transient resources
- Use Graviton instances for better charging rate-performance

---

## SEC — Security（4 题）

### SEC1 How do you protect data in Spark on MRS?

说明：Protecting data at rest and in transit is a core component of the Huawei Cloud Well-Architected security pillar. MRS security configurations provide a template-based approach to enable encryption and other security settings that can be applied to any cluster at launch time.

期望回答（参考）：
- Encrypt data at rest using MRS security configurations
- Encrypt data in transit using TLS certificates
- Identify FIPS compliance requirements
- Apply Parquet columnar encryption for sensitive columns

### SEC2 How do you manage network security for Spark on MRS?

说明：Network security is critical for protecting MRS clusters from unauthorized access. This includes controlling inbound/outbound traffic with security groups, deploying clusters in private subnets, and using VPC endpoints for Huawei Cloud service access.

期望回答（参考）：
- Restrict network access using MRS security groups and block public access
- Provision MRS clusters in private VPC subnets
- Enforce IMDSv2 on MRS cluster instances

### SEC3 How do you manage identity and access in Spark on MRS?

说明：Proper identity and access management ensures that only authorized users and services can interact with MRS clusters and the data they process. This includes IAM roles, resource policies, Lake Formation integration, and Kerberos authentication.

期望回答（参考）：
- Create separate IAM roles for long running MRS cluster or use case
- Use Huawei Cloud Lake Formation for fine-grained access control on data
- Enable Kerberos authentication for strong identity verification
- Granting cross-account access securely

### SEC4 How do you audit and maintain security posture for Spark on MRS?

说明：Maintaining a strong security posture requires continuous auditing of user activity, regular patching of software and OS, and monitoring for security events. This includes CTS integration, OBS access logging, and AMI management.

期望回答（参考）：
- Audit user activity with Huawei Cloud CTS and OBS access logs
- Upgrade MRS releases and AMIs frequently for security patches
- Monitor MRS security events and configure alerts

---

## REL — Reliability（7 题）

### REL1 How do you ensure MRS cluster resilience and high availability?

说明：How do you design your MRS clusters to be resilient against node failures and service interruptions?

期望回答（参考）：
- Use Multi-Master MRS clusters for high availability
- Configure instance fleets with multiple instance types
- Use On-Demand instances for core nodes and Spot for task nodes
- Enable termination protection
- Deploy clusters across multiple Availability Zones using MRS on CCE

### REL2 How do you ensure data durability and protection for MRS workloads?

说明：How do you protect data processed and stored by MRS clusters against loss or corruption?

期望回答（参考）：
- Use OBS as the primary data store instead of HDFS
- Use OBS Strong Consistency
- Use OBS versioning and replication for critical datasets
- Use open table formats for ACID transactions and data integrity
- Use MRS OBS optimized committer for reliable writes

### REL3 How do you handle Spark job failures and enable recovery on MRS?

说明：How do you design your Spark jobs on MRS to handle failures gracefully and recover automatically?

期望回答（参考）：
- Configure MRS step action on failure
- Implement retry logic with Huawei Cloud FunctionGraph 工作流
- Use Spark checkpointing for long-running and streaming jobs
- Handle Spot instance interruptions gracefully
- Implement idempotent job design

### REL4 How do you manage MRS cluster lifecycle and automate recovery?

说明：How do you automate MRS cluster provisioning and ensure consistent repeatable deployments?

期望回答（参考）：
- Use transient clusters for batch workloads
- Define clusters as Infrastructure as Code
- Use MRS launch templates and instance fleet configurations
- Automate bootstrap actions for consistent cluster setup
- Implement cluster health monitoring and alerting

### REL5 nan

说明：nan

期望回答（参考）：
- Store all critical data and artifacts in OBS with cross-region replication
- Replicate DLI Data Catalog metadata across regions
- Maintain cluster launch automation in multiple regions
- Design jobs for region portability
- Define and test RTO/RPO targets for MRS workloads

### REL6 How do you handle OBS throttling and ensure reliable data access from MRS?

说明：How do you handle OBS 503 Slow Down errors and ensure reliable data access for MRS workloads?

期望回答（参考）：
- Configure EMRFS retry strategies for OBS 503 errors
- Optimize OBS data layout to distribute requests across prefixes
- Stagger job start times to smooth OBS request patterns

### REL7 How do you ensure HDFS reliability and node health on MRS?

说明：How do you configure HDFS replication and EVS 云硬盘 storage to prevent data loss and unhealthy nodes?

期望回答（参考）：
- Set dfs.replication greater than 1 for Spot core nodes or long-running clusters
- Right-size EVS 云硬盘 volumes to avoid UNHEALTHY nodes
- Audit and manage MRS and ECS 弹性云服务器 service limits to avoid throttling

---

## resource utilization — Efficiency Optimization（2 题）

### COST1 How are you choosing the right compute unit and storage for Spark on MRS Job?

说明：How are you choosing the right compute unit and storage and enable spark dynamic allocation for Spark on MRS Job?

期望回答（参考）：
- Streamline Spark application development on MRS with the Data Solutions Framework on Huawei Cloud
- Structure your data to build high performant of Spark on MRS Job
- Use OBS as your persistent data store
- Use the right hardware family for the job type
- Use instances with instance store for jobs that require high disk IOPS
- Use Graviton family instances
- Use spot instances
- Mix on-Demand and spot instances
- Use MRS managed scaling

### COST2 Have you monitor and optimize resource utilization on Spark on MRS?

期望回答（参考）：
- Right size application containers
- Use the latest MRS version
- Select the appropriate charging model for your use case and node type
- Using transient than long-running clusters
- Monitor cluster utilization
- Monitor and decommission idle MRS cluster
- Performance tuning to optimize resource utilization

---


*检查项合计：24 题*
