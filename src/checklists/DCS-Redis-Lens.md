# DCS Redis 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：DCS Redis（缓存）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## waf_ec_1_ops — Operational excellence（5 题）

### waf_ec_ops_dp1 How do you understand and respond to alerts and events triggered by your DCS Redis cluster?

说明：When you operate DCS Redis clusters you can optionally receive notifications and alerts when specific events occur. DCS Redis, by default, logs events that relate to your resources, such as a failover, node replacement, scaling operation, scheduled maintenance, and more. Each event includes the date and time, the source name and source type, and a description

期望回答（参考）：
- Configure DCS Redis to send notifications for important cluster events
- Automate responses to events, use SMN 消息通知 to send emails to DCS Redis administrators
- None of these

### waf_ec_ops_dp2 When and how do you scale your existing DCS Redis clusters?

说明：Right-sizing your DCS Redis cluster is a balancing act that needs to be evaluated every time there are changes to the underlying workload types. Your objective is to operate with the right sized environment for your workload so as not to overprovision or underprovision.

期望回答（参考）：
- CPU and network over utilization on primary nodes 
- Monitor the utilization of critical cluster resources such as CPU, memory, and network.
- Do you monitor trends over time to detect workload changes
- Do you preserve operational consistency and avoid unmanaged configuration changes and stack drifts
- Do you have autoscaling in place for variable workloads using Redis compatible compute engine
- Do you use custom metrics (other then CPU and Memory) to scale a Redis compatible cluster
- None of these

### waf_ec_ops_dp3 How do you manage your DCS Redis cluster resources and maintain your cluster up-to-date?

说明：When operating at scale, it is essential that you are able to pinpoint and identify all your DCS Redis resources. When rolling out new application features you need to create cluster version symmetry across all your DCS Redis environment types: dev, testing, and production. Resource attributes allow you to separate environments for different operational objectives, such as when rolling out new features and enabling new security mechanisms.

期望回答（参考）：
- Run on the latest engine version available and apply the Self-Service Updates as quickly as they become available.
- Organize your DCS Redis resources using tags
- None of these

### waf_ec_ops_dp4 How do you model and interact with data in DCS Redis? 

说明：DCS Redis is heavily application dependent on the data structures and the data model used. Understand the DCS Redis data structures available and ensure you are using the most appropriate data structures for your needs.

期望回答（参考）：
- Reduce unintentional overwriting of data
- Manage operations complexity with lower performance and potential operation timeouts
- Visibility into the data model in your cluster
- None of these

### waf_ec_ops_dp5 How do you manage clients connections to your DCS Redis clusters?

说明：When operating at scale you need to understand how your clients connect with the DCS Redis cluster to manage your application operational aspects (such as response times). 

期望回答（参考）：
- Separate read from write operations and connect to the replica nodes to execute read operations.
- Use connection pooling.
- Ensure that the socket timeout of the client is set to at least one second 
- Using pipelining can significantly boost ingestion performance.
- None of these

---

## waf_ec_2_sec — Security（6 题）

### waf_ec_sec_dp4 What steps are you taking in controlling authorized access to DCS Redis data?

说明：All DCS Redis clusters are designed to be accessed from CCE 容器集群 弹性云服务器 instances in an VPC (VPC), serverless functions (Huawei Cloud FunctionGraph), or containers (CCE 容器集群). The most encountered scenario is to access an DCS Redis cluster from an CCE 容器集群 弹性云服务器 instance within the same VPC. Before you can connect to a cluster from an ECS 弹性云服务器 instance, you must authorize the ECS 弹性云服务器 instance to access the cluster. To access an DCS Redis cluster running in a VPC, it is necessary to grant network ingress to the cluster.

期望回答（参考）：
- Using separate accounts for DCS Redis clusters in production and non-production environments
- Identify compliance requirements for data stored in DCS Redis clusters for production and non-production environments
- Automate configuration management using Terraform
- Latest engine version
- Change default port
- In-transit and at-rest encrpytion
- Security Groups in place to access the cluster
- Use of IAM Policies to access DCS Redis Data
- None of these

### waf_ec_sec_dp5 Do your applications require additional authorization to DCS Redis over and above networking-based controls?

说明：In scenarios where it is necessary to restrict or control access to DCS Redis clusters at an individual client level, it is recommended to authenticate via the DCS Redis AUTH command. DCS Redis authentication tokens, with optional user and user group management, enable DCS Redis to require a password before allowing clients to run commands and access keys, thereby improving data plane security.

期望回答（参考）：
- Define authentication and authorization controls
- Use of Authentication Tokens and Rotation of Tokens
- None of these

### waf_ec_sec_dp9 Is there a risk that commands can be executed inadvertently, causing data loss or failure?

说明：There are a number of Redis commands that can have adverse impacts on operations if executed by mistake or by malicious actors.

期望回答（参考）：
- Set the rename commands parameter to rename commands that need to be effectively disabled
- Not in place

### waf_ec_sec_dp8 How do you ensure data encryption at rest with DCS Redis?

说明：While DCS Redis is an in-memory data store, it is possible to encrypt any data that may be persisted (on storage) as part of standard operations of the cluster. This includes both scheduled and manual backups written to OBS, as well as data saved to disk storage as a result of snapshot, sync and swap operations. Instance types in the M6g and R6g families also feature always-on, in-memory encryption.

期望回答（参考）：
- Encryption at Rest is enabled for the DCS Redis Clusters
- Leverage ECS 弹性云服务器 instance types that encrypt data while it is in memory
- None of these

### waf_ec_sec_dp6 How do you encrypt in-transit data with DCS Redis?

说明：It is a common requirement to mitigate against data being compromised while in transit. This represents data within components of a distributed system, as well as between application clients and cluster nodes. DCS Redis supports this requirement by allowing for encrypting data in-transit between clients and cluster, and between cluster nodes themselves. Instance types in the M6g and R6g families also feature always-on, in-memory encryption.

期望回答（参考）：
- Encryption in Transit is Enabled for all DCS Redis Clusters
- Not in place

### waf_ec_sec_dp7 How do you restrict access to control plane resources?

说明：IAM policies and ARN enable fine-grained access controls for DCS Redis , allowing for tighter control to manage the creation, modification and deletion of DCS Redis clusters.

期望回答（参考）：
- Finer Control over which accounts can perform what actions on clusters
- Not in place

---

## waf_ec_3_rel — Reliability（4 题）

### waf_ec_rel_dp7 How are you supporting high availability (HA) architecture deployments?

说明：Understanding the high availability architecture of DCS Redis will enable you to operate in a resilient state during availability events.

期望回答（参考）：
- Define reliability needs for each type of environment you operate your clusters in
- Use DCS Redis in Cluster Mode
- None of these

### waf_ec_rel_dp8 How are you meeting your Recovery Point Objectives (RPOs) with DCS Redis?

说明：Understand workload RPO to inform decisions on DCS Redis backup and recovery strategies.

期望回答（参考）：
- Document the RPO of your DCS Redis deployments.
- Well-communicated process in place for backing up your cluster and Scheduled backups in place
- None of these

### waf_ec_rel_dp9 How do you support disaster recovery (DR) requirements?

说明：Disaster recovery is an important aspect of any workload planning. DCS Redis offers several options to implement disaster recovery based on workload resilience requirements. With DCS Redis Global Datastore, you can write to your DCS Redis cluster in one region and have the data available to be read from two other cross-region replica clusters, thereby enabling low-latency reads and disaster recovery across regions.

期望回答（参考）：
- Do you have Documented DR Strategies for your workloads
- Global Stores are Enabled
- None of these

### waf_ec_rel_dp10 How do you effectively plan for failovers?

说明：Enabling multi-AZ with automatic failovers is an DCS Redis best practice. In certain cases, DCS Redis replaces primary nodes as part of service operations. Examples include planned maintenance events and the unlikely case of a node failure or availability zone issue. Successful failovers rely on both DCS Redis and your client library configuration.

期望回答（参考）：
- Mechamisms in place based on cluster mode to notify clients for any changes in cluster availability
- Healthy replication environment between the primary and the replica nodes
- Validate the responsiveness of your application during failover
- None of these

---

## waf_ec_4_perf — Performance efficiency（5 题）

### waf_ec_perf_dp9 How do you monitor the performance of your DCS Redis cluster?

说明：HYou need to understand the existing monitoring metrics to identify current utilization. Proper monitoring can help identify potential bottlenecks impacting the performance of your cluster.

期望回答（参考）：
- Baseline performance testing using a subset of your workload
- Do you limit the ability of users to run blocking commands on production clusters
- Analyze slow queries and look for optimization techniques.
- None of these

### waf_ec_perf_dp10 How are you distributing work across your DCS Redis Cluster nodes?

说明：The way your application connects to DCS Redis nodes can impact the performance and scalability of the cluster.

期望回答（参考）：
- Have clients connect to the proper DCS Redis endpoint
- Take advantage of DCS Redis cluster mode enabled to improve scalability
- Implement a strategy for identifying and remediating hot keys in your workload.
- None of these

### waf_ec_perf_dp11 For caching workloads, how do you track and report the effectiveness and performance of your cache?

说明：Caching is a commonly encountered workload on DCS Redis and it is important that you understand how to manage the effectiveness and performance of your cache.

期望回答（参考）：
- Measure and track over time the cache-hits ratio and its efficiency
- Measure and collect your application cache performance in conjunction with latency and CPU utilization values 
- Caching Strategies in place and matches the workload needs across all clusters
- None of these

### waf_ec_perf_dp12 How does your application optimize the use of networking resources and connections?

说明：DCS Redis and Memcached are supported by many application clients, and implementations may vary. You need to understand the networking and connection management in place to analyze potential performance impact.

期望回答（参考）：
- Proactively manage connections to your DCS Redis cluster
- Mechanisms to Reduce network latency in your workload 
- Compress large objects to reduce memory, and improve network throughput
- None of these

### waf_ec_perf_dp13 How do you manage key deletion and/or eviction?

说明：Workloads have different requirements and expected behavior when a cluster node is approaching memory consumption limits. DCS Redis has different policies for handling these situations.

期望回答（参考）：
- Identify an appropriate max-memory policy to control if and how evictions are performed on the cluster
- Standardize delete behavior to control performance impact on your cluster to avoid unexpected performance bottlenecks
- None of these

---

## waf_ec_5_cost — efficiency optimization（2 题）

### waf_ec_cost_dp12 How do you identify and track resource utilization associated with your DCS Redis resources?

说明：Understanding resource utilization metrics requires the participation and collaboration of multiple teams: software engineering, data management, product owners, finance, and leadership. Identifying key resource utilization drivers requires all involved parties understand service usage control levers and resource management trade-offs and it is frequently the key difference between successful and less successful efficiency optimization efforts. Ensuring you have processes and tools in place to track resources created from development to production and retirement helps you manage the resource utilization associated with DCS Redis.

期望回答（参考）：
- Do you have a Cloud Center of Excellence or mechanisms in place to define, track and act on resource utilization metrics
- Use of resource utilization allocation tags to track resource utilization at a low level of granularity
- Does your monitoring include both business and operational metrics
- Maintain up-to-date architectural and operational visibility on metrics and resource utilization
- None of these

### waf_ec_cost_dp13 How do you use continuous monitoring tools to help you optimize the resource utilization associated with your DCS Redis resources?

说明：You need to aim for a proper balance between your DCS Redis resource utilization and application performance metrics. LTS 日志服务 provides visibility into key operational metrics that can help you assess whether your DCS Redis resources are over or under utilized, relative to your needs. From a efficiency optimization perspective, you need to understand when you are overprovisioned and be able to develop appropriate mechanisms to resize your DCS Redis resources while maintaining your operational, availability, resilience, and performance needs. 

期望回答（参考）：
- Use LTS to monitor your DCS Redis clusters and analyze how these metrics relate to your Huawei Cloud resource explorer dashboards
- Understand and document your backup strategy and resource utilization implications.
- Use Reserved Nodes as a deliberate strategy to manage resource utilization for workloads that are well understood and documented
- Use Data Tiering instance types as a deliberate strategy to manage resource utilization for workloads that are well understood and documented
- None of these

---


*检查项合计：22 题*
