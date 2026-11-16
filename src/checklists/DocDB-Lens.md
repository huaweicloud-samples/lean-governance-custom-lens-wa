# 云数据库 DocDB/GeminiDB Mongo 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：云数据库 DocDB/GeminiDB Mongo（文档数据库）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## docdb_ops — Operational Excellence（5 题）

### docdb_ops1 How do you deploy DocumentDB clusters across regions / environments?

说明：Critical workloads with a global footprint have strict availability requirements and may need to tolerate a region-wide outage

期望回答（参考）：
- Use Cloud Formation template for consistent environment configuration across regions / accounts.
- Configure subnet groups with 3 AZs with minimum 2 instances.
- Use Cluster endpoint
- Script global cluster failover and externalize endpoint lookup for applications
- None of above

### docdb_ops2 How do you track and test changes to cluster configuration?

说明：Controlled changes are necessary to deploy new functionality. If these changes are uncontrolled, then it makes it difficult to predict the effect of these changes or to address issues that arise because of them.

期望回答（参考）：
- Define Huawei Cloud config rules to validate DocumentDB best practices
- Trigger Huawei Cloud LTS events rules for Huawei Cloud config events
- Benchmark DocumentDB cluster for performance
- None of above

### docdb_ops3 How do you evaluate operational readiness of your workload?

说明：
Evaluate the operational readiness of your workload, processes, procedures and personnel to understand the operational risks related to your workload.

期望回答（参考）：
- Use Huawei Cloud IAM to control access to DocumentDB resources
- Use playbooks to define operational readiness
- Run periodic readiness tests, according to existing playbooks
- None of above

### docdb_ops4 How do you monitor your DocumentDB cluster(s)?

说明：Define, capture, and analyze workload metrics to gain visibility to workload events and take appropriate action.

期望回答（参考）：
- Configure application to log database connectivity response times & errors.
- Create Huawei Cloud LTS dashboard and alarms for key metrics and application logs.
- Define log insight queries for profiler and audit logs
- Tag instances for organization, identification and resource utilization accounting
- None of above

### docdb_ops6 How do you manage lifecycle of manual snapshots?

说明：A manual snapshot is a full backup that is deleted only when you manually delete it using the Huawei Cloud Management Console or Huawei Cloud CLI. You cannot manually delete an automatic snapshot because automatic snapshots are deleted only when the snapshot's retention period expires or you delete the snapshot's cluster.

期望回答（参考）：
- Create jobs to periodically remove manual snapshots
- Use Huawei Cloud Backup to centrally manage DocumentDB backup
- None of above

---

## docdb_perf — Performance Efficiency（7 题）

### docdb_perf1 What are your query access patterns?

说明：Access patterns for the application dictate the schema structure of documents stored in the database. Schema flexibility offered by JSON allows you to make changes quickly, making document databases an ideal choice for agile development.

期望回答（参考）：
- Optimize access patterns for compute, NOT storage
- Document size smaller than 8KB
- Separate mutable & immutable parts of document
- Use logical modeling and selective denormalization
- Use index in fields with high cardinality
- None of above

### docdb_perf2 How does your application access data?

说明：How you access data will affect how the application performs. Access patterns define how the users and the system access the data to satisfy business needs.

期望回答（参考）：
- Use bulk operations over individual
- Use operators with optimizations such as hint and project
- Avoid sub optimal operators such as distinct(), ne(), nin()
- None of above

### docdb_perf3 How do your customers, across the globe, access data?

说明：If you have offices around the world, you can use a global cluster to keep your main sources of information updated in the primary region.

期望回答（参考）：
- Leverage global clusters for local reads per region.
- None of above

### docdb_perf4 How does your application connect to your DocumentDB cluster(s)?

说明：_

期望回答（参考）：
- Connect as replica set and use replica reads for scalability.
- Deploy the application in same AZs as the DocumentDB cluster.
- None of above

### docdb_perf5 How many concurrent requests does the application support?

说明：To optimize instance performance and response time, it is recommended to evaluate database connection constraints when observing a significant increase in user connections. The appropriate number of user connections for your instance depends on factors such as the instance class and the complexity of the operations being executed.

期望回答（参考）：
- Configure workload specific connection parameters.
- Validate instance size against connection limits.
- None of above

### docdb_perf6 How did you size your cluster?

说明：Continuous right sizing is a crucial practice for resource utilization control in the cloud environment. It entails regularly assessing the performance, usage patterns, and requirements of instances, and taking appropriate actions such as turning off idle instances and optimizing instances that are either overprovisioned or not well-suited for the workload. By adopting this approach, you can effectively manage cloud resource utilization while ensuring optimal resource allocation.

期望回答（参考）：
- Use data characteristics to size workload.
- Ensure Indices and working set fit in cache.
- Validate sizing by performing load test and scale as needed.
- None of above

### docdb_perf7 How do you monitor performance of your cluster?

说明：Monitor performance metrics on a regular basis to see the average, maximum, and minimum values for a variety of time ranges. This helps you identify when performance is degraded.

期望回答（参考）：
- Monitor performance to determine scaling needs.
- Implement autoscaling
- None of above

---

## docdb_rel — Reliability（7 题）

### docdb_rel1 How are you meeting your RPO and RTO with DocumentDB?

说明：Recovery from disaster is typically measured using values for RTO and RPO.
Recovery time objective (RTO) is the maximum acceptable delay between the interruption of service and restoration of service. In other words, RTO measures downtime. For a global cluster, RTO can be in the order of minutes.
Recovery point objective (RPO) is the maximum acceptable amount of time since the last data recovery point. For a global cluster, RPO is typically measured in seconds.

期望回答（参考）：
- Select backup retention period based on RPO
- Use global clusters for low RTO requirements
- Retain manual snapshots beyond retention period based on purge requirements
- None of above

### docdb_rel2 How do you support Disaster Recovery (DR) requirements?

说明：Disaster recovery strategies available to you within Huawei Cloud can be broadly categorized into four approaches, ranging from the low resource utilization and low complexity of making backups to more complex strategies using multiple active Regions.

期望回答（参考）：
- Use global clusters for DR requirements
- Use cluster snapshot copy for flexible RTO requirements
- None of above

### docdb_rel3 How does your application handle exceptions from DocumentDB?

说明：In certain cases, such as certain types of planned maintenance, or in the unlikely event of a primary node or Availability Zone failure, DocumentDB (with MongoDB compatibility) detects the failure and replaces the primary node. So that your applications can resume database operations as quickly as possible without administrative intervention.

期望回答（参考）：
- Implement exception handling with retry techniques
- None of above

### docdb_rel4 How do you manage client connections to clusters?

说明：Consider constraining database connections if you see high numbers of user connections in conjunction with decreases in instance performance and response time. The best number of user connections for your instance will vary based on your instance class and the complexity of the operations being performed.

期望回答（参考）：
- Configure clients for connection and cursor management:
- Use (allowDiskUse: true) for aggregate queries
- Terminate abandoned queries
- None of above

### docdb_rel5 How do you support High Availability(HA) architecture deployments?

说明：You can achieve high availability and read scaling in DocumentDB (with MongoDB compatibility) by using replica instances. A single DocumentDB cluster supports a single primary instance and up to 15 replica instances. These instances can be distributed across Availability Zones within the cluster's Region. The primary instance accepts read and write traffic, and replica instances accept only read requests.

期望回答（参考）：
- Use minimum of 2 instances for Auto failover
- Select the number of instances based on availability target
- Use global clusters for HA deployments across regions
- None of above

### docdb_rel6 How do you automate database deployments?

说明：Infrastructure as code (IaC) helps organizations achieve their DevOps goals of automation and self-service by maintaining declaration files in version control that define your application environments.lets you model, provision, and manage Huawei Cloud and third-party resources by treating infrastructure as code.

期望回答（参考）：
- Automate deployments using Huawei Cloud Terraform
- Use Huawei Cloud SDK for automating deployments
- Use Huawei Cloud CLI for automating deployments
- Other (terraform or similar )
- None of above

### docdb_rel7 How do you monitor the reliability of your workload?

说明：Monitoring your DocumentDB is an important part of keeping your systems healthy and functioning optimally to determine the health and performance of your clusters and instances.

期望回答（参考）：
- Monitor metrics and configure alarms and notifications
- None of above

---

## docdb_sec — Security（6 题）

### docdb_sec1 How do you securely operate your DocumentDB cluster?

说明：Cloud security at Huawei Cloud is the highest priority. As an Huawei Cloud customer, you benefit from a data center and network architecture that are built to meet the requirements of the most security-sensitive organizations.

期望回答（参考）：
- Use default security settings for Data-At-Rest and over the wire encryption
- Use TLS 1.2 and above
- None of above

### docdb_sec2 How do you limit DocumentDB access to other services and applications?

说明：For security best practices, you must use Huawei Cloud Identity and Access Management (IAM) accounts to control access to DocumentDB API operations, especially operations that create, modify, or delete DocumentDB resources. Such resources include clusters, security groups, and parameter groups.

期望回答（参考）：
- Configure security group to limit surface area of attack
- Create IAM users with least access privilege. Avoid use of root credentials
- None of above

### docdb_sec3 How do you ensure secure application connections to DocumentDBDocumentDB?

说明：Huawei Cloud Secrets Manager helps you protect secrets needed to access your applications, services, and IT resources. The service enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle. Users and applications retrieve secrets with a call to Huawei Cloud Secrets Manager API, eliminating the need to hardcode sensitive information in plain text.

期望回答（参考）：
- Isolate credentials from application.
- Use Secrets Manager to retrieve DocumentDB credentials.
- Use external secrets store (Vault or similar)
- None of above

### docdb_sec4 How do you control access to DocumentDB resources?

说明：Every Huawei Cloud resource is owned by an Huawei Cloud account, and permissions to create or access the resources are governed by permissions policies. An account administrator can attach permissions policies to IAM identities (that is, users, groups, and roles), and some services (such as Huawei Cloud FunctionGraph) also support attaching permissions policies to resources.

期望回答（参考）：
- Use Huawei Cloud IAM to control access to DocumentDB resources
- None of above

### docdb_sec5 What are your database auditing requirements?

说明：You can audit events that were performed in your cluster. Examples of logged events include successful and failed authentication attempts, dropping a collection in a database, or creating an index. By default, auditing is disabled on DocumentDB and requires that you opt in to use this feature.

期望回答（参考）：
- Enable audit logging
- Set alarms for anti-patterns
- None of above

### docdb_sec6 How do you automate security best practices?

说明：To improve the ability to continuously monitor and notify when configurations in DocumentDB deviate from best practices, you can create Huawei Cloud Config rules and trigger notifications immediately when the cluster modification violates compliance and standards predefined by your organization.

期望回答（参考）：
- Use default values for security best practices
- Use Huawei Cloud config to enforce compliance
- None of above

---

## docdb_cost — Efficiency Optimization（7 题）

### docdb_cost1 How does your workload characteristics vary for sustained and peak traffic?

说明：Cluster instances need to be appropriately sized to keep all working set memory. This avoids the need to continuously read index pages from the storage volume, which negatively impacts performance and generates higher I/O resource utilization.

期望回答（参考）：
- Size instances for sustained load and scale on demand for peak load
- Use smaller instances in lower environments. Start and stop instances as needed
- None of above

### docdb_cost2 Do you utilize complex analytical queries for adhoc reporting?

说明：One of the best ways to improve cluster performance is to tune your most commonly used and most resource-intensive queries to make them less expensive to run.

期望回答（参考）：
- Start instances with higher compute for adhoc reporting and stop when done
- Optimize inefficient queries
- None of above

### docdb_cost3 How often does your application perform update operations?

说明：While indexes can improve query performance by avoiding the need to scan every document in a collection, this improvement comes with a tradeoff. For every document write (insert/update/delete) in a collection, each index has to be updated as well. The more indexes present, the more potential write overhead.

期望回答（参考）：
- Separate mutable and immutable portions of document
- Use OBS to store images and store link and metadata in DocumentDB
- Remove unused indexes
- Optimize working set by moving least accessed documents to different collection
- None of above

### docdb_cost4 How do you purge older data from your collections?

说明：Identifying and removing or expiry unused document, indexes and snapshot is a best practice that we recommend performing on a regular basis.

期望回答（参考）：
- Use rolling collections over TTL
- Delete unused manual snapshots
- None of above

### docdb_cost5 Do you cleanse data after migrating to DocumentDB?

说明：Cluster instances need to be appropriately sized to keep all working set memory. This avoids the need to continuously read index pages from the storage volume, which negatively impacts performance and generates higher I/O resource utilization

期望回答（参考）：
- Perform data cleansing before migrating data to DocumentDB
- None of above

### docdb_cost6 How do you monitor usage and resource utilization for DocumentDB?

说明：You must regularly report on resource utilization and efficiency within your organization. You can implement dedicated sessions to efficiency optimization, or include efficiency optimization in your regular operational reporting cycles for your workloads.

期望回答（参考）：
- Monitor metrics and set charging alarms
- Use resource utilization allocation tags to track expense at a granular level
- None of above

### docdb_cost7 How do you meet resource utilization targets when you select resource type, size and number?

说明：Right sizing is an ongoing process and its the most effective way to control cloud resource utilization. It involves continually analyzing instance performance and usage needs and patternsand then turning off idle instances and rightsizing instances that are either overprovisioned or poorly matched to the workload.

期望回答（参考）：
- Choose appropriate instance size and number of instances
- Select most resource utilization effective instance type, size and number
- None of above

---

## docdb_sust — Sustainability（5 题）

### docdb_sust1 How do you monitor your DocumentDB usage?

说明：Monitor your DocumentDB usage and regularly asses the usage to identify downscaling opprtunities.

期望回答（参考）：
- Monitoring is done using LTS
- Monitoring is done using Performance Insights
- None of above

### docdb_sust2 How do you detect and decommission unused resources?

期望回答（参考）：
- Automated actions are triggered from Alarms based on LTS Metrics
- Metrics are viewed in the Huawei Cloud web console
- None of above

### docdb_sust3 Can Serverless services be utilized to access DocumentDB?

说明：Can Serverless services be utilized to access GeminiDB?

期望回答（参考）：
- Yes we prioritize using Serverless services
- None of above

### docdb_sust4 Are you using Graviton instances?

说明：DocumentDB supports the R4, R5, R6G, T3, and T4G families of instance classes. These classes are current-generation instance classes that are optimized for memory-intensive applications.

期望回答（参考）：
- Yes, we use R6G or T4G instances
- No, using other instance classes

### docdb_sust5 Can you archive old data to colder storage?

期望回答（参考）：
- Yes, we archive data using TTL and copy to OBS using change streams
- None of above

---


*检查项合计：37 题*
