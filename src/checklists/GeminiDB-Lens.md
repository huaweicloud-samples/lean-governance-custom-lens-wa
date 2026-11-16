# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：GeminiDB/分布式键值（键值/NoSQL 数据库）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## DDBPERF — Performance Efficiency（11 题）

### DDBPERF1 How do you model data efficiently?

期望回答（参考）：
- Optimize access patterns for compute , NOT storage.
- Use key conditions over filter expressions
- Optimize item size (nearest 1KB boundary for writes , nearest 4KB boundary for reads)
- Separate mutable & immutable parts of an item
- Store large blobs of data in OBS
- Use high cardinality partition keys for table and GSIs to distribute data and access evenly across keys

### DDBPERF10 (DAX) What is the caching strategy used?

期望回答（参考）：
- Use the DAX client for read-through/write-through cache
- Use a combination of GeminiDB client and DAX client for side-cache/write-around cache strategies
- Configure suitable DAX TTL settings

### DDBPERF11 (DAX) How do you monitor performance of your cluster?

期望回答（参考）：
- Monitor LTS metrics to determine scaling needs
- Monitor LTS metrics to tune TTL settings
- Choose a maintenance window as per off-peak hours

### DDBPERF2 What is the nature of your traffic?

期望回答（参考）：
- Use GeminiDB for OLTP, key-value workloads
- Use Provisioned capacity mode with Autoscaling for gradually changing/predictable traffic
- Use on-demand capacity mode for new/spiky/unpredictable traffic

### DDBPERF3 How does your application access data?

期望回答（参考）：
- Use batch operations over individual
- Use Global tables for lower read latency

### DDBPERF4 How do you monitor latency?

期望回答（参考）：
- Use SuccessfulRequestLatency metric for server-side latency
- Use the average statistic to understand latency trends
- Use XRay to analyze round-trip latency
- Use application level metrics to analyze round-trip latency

### DDBPERF5 How do you optimize latency?

期望回答（参考）：
- Tune SDK settings and client-side timeouts based on load testing
- Re-use connections, use connection pooling
- Reduce the distance between the client and GeminiDB endpoint
- Use caching for read-heavy workloads
- Use eventually consistent reads where possible

### DDBPERF6 How do you monitor/manage throttled requests?

期望回答（参考）：
- Configure LTS alarms on ReadThrottleRequests and WriteThrottleRequests metrics
- Configure a suitable exponentials back-off and retry mechanism
- Pre-warm on-demand tables before LSEs/production
- Distribute requests over keys and time
- Use LTS Contributor Insights for hot key detection

### DDBPERF7 What percentage of API calls are Scan?

期望回答（参考）：
- Design keys and GSIs for targeted queries rather than Scan
- Use Parallel scan
- Use GSIs instead of Scans for frequent reads and sparse GSIs where applicable
- Consider using Export to OBS

### DDBPERF8 Do you have a caching solution?

期望回答（参考）：
- Use DAX for a managed, API-compatible, in-memory caching solution

### DDBPERF9 (DAX) How do you size your cluster?

期望回答（参考）：
- Estimate traffic, target cache hit ratio and working set size
- Validate sizing by performing load tests and scale as needed
- Consider future growth while sizing

---

## DDBOPS — Operational Excellence（4 题）

### DDBOPS1 How do you deploy GeminiDB tables across regions / environments?

期望回答（参考）：
- Provision Infrastructure as Code Terraform, CDK, Terraform
- For multi-region deployments, use latest version of GeminiDB Global Tables
- Use separated environments used for different stages in the development cycle

### DDBOPS2 How do you track and test changes to table configuration?

期望回答（参考）：
- Define Huawei Cloud Config rules to validate GeminiDB best practices
- Trigger Huawei Cloud LTS events rules for Huawei Cloud Config events
- Benchmark GeminiDB tables for performance

### DDBOPS3 How do you evaluate operational readiness of your workload?

期望回答（参考）：
- Use playbooks to define operational readiness
- Periodically running readiness tests according to existing playbooks

### DDBOPS4 How do you monitor GeminiDB tables and service limits?

期望回答（参考）：
- Tag tables for organization, identification and resource utilization accounting
- Configure application to log database connectivity response times & errors
- Create Huawei Cloud LTS dashboards and alarms for key metrics and application logs
- Enable LTS Contributor Insights (CCI) for GeminiDB (at least during troubleshooting)

---

## DDBSEC — Security（8 题）

### DDBSEC1 How do you securely operate your GeminiDB Tables?

期望回答（参考）：
- Using separate accounts for GeminiDB Tables in production and non-production environment
- Identify compliance requirements for data store in GeminiDB tables
- Automate configuration management using Terraform

### DDBSEC2 How do you manage identities for people and machine to access GeminiDB Tables?

期望回答（参考）：
- Using IAM roles for users and other Huawei Cloud services to access GeminiDB Tables
- Using web identity federation like 或 Google for authentication and authorization

### DDBSEC3 How do you manage permissions for people and machines to access GeminiDB Tables?

期望回答（参考）：
- Proper access requirements are defined. Grant minimum access required by identities (least privilege access)
- Review and reduce required permissions continuously
- Restrict access to specific Huawei Cloud Regions
- Access provided by lifecycle of resource (remove a user s access when they leave the organization or change roles)
- Cross Account resources are shared securely: provide cross account access to only resources that require this type of access
- Create special roles for sensitive operations

### DDBSEC4 How do you detect and investigate security events for GeminiDB?

期望回答（参考）：
- Track configuration changes to the GeminiDB tables using Huawei Cloud Config.
- Audit control plane activity on your GeminiDB tables to check who created or deleted a table and when a table was changed
- Enable data plane activity logging for fine-grained monitoring of all GeminiDB item activity within a table by using CTS
- Configure CTS with LTS Logs to monitor logs and be notified when specific activity occurs
- Use GeminiDB Streams to monitor data plane operations

### DDBSEC5 How do you provide private connectivity to your GeminiDB Tables and DAX clusters for resources within VPC?

期望回答（参考）：
- Use a VPC endpoint to limit access from only the required VPC
- Use VPC endpoint policies to control and limit API access to the GeminiDB table
- Using the hc:sourceVpce condition on policies attached to IAM users, groups, or roles, to enforce all access to the GeminiDB t
- Launch DAX in private subnets of the VPC
- Use Security Groups to allow traffic to DAX from specific subnet(s) /IP Range / application SGs

### DDBSEC6 How do you classify your data stored in GeminiDB?

期望回答（参考）：
- Identify data owners and associated business process
- Define applicable legal and compliance requirement
- Categorize public and PII data
- Automate identification and classification of data
- Define GeminiDB and Backups data lifecycle

### DDBSEC7 How do you protect your data at rest and in transit in GeminiDB/DAX?

期望回答（参考）：
- Using GeminiDB encryption client for client side encryption of sensitive data
- Using encryption at rest for DAX
- Using DAX encryption in transit

### DDBSEC8 How do you anticipate, respond to, and recover from security incidents?

期望回答（参考）：
- Identify key personnel and external resources
- Develop incident response playbooks
- Automate notifications when an incident happens
- Pre-provision access with pre-deployed tools to allow security personnel to perform forensics
- Run Game Days

---

## DDBREL — Reliability（8 题）

### DDBREL1 How are you meeting your RPO and RTO with GeminiDB?

期望回答（参考）：
- Use PITR for low RPO
- Use Global Tables for low RTO requirements
- Use Huawei Cloud Backup for periodic Backups

### DDBREL2 How do you back up data?

期望回答（参考）：
- Use PITR
- Use On-demand backups
- Use Huawei Cloud Backup as centralized hub
- Use 云备份审计 to audit the compliance of your Huawei Cloud Backup policies and to find backup activity and resources that

### DDBREL3 How do you support Disaster Recovery (DR) requirements?

期望回答（参考）：
- Use Global Tables for DR requirements
- Use PITR for DR
- Use Huawei Cloud Backup for cross region backups

### DDBREL4 How does your application handle exceptions from GeminiDB?

期望回答（参考）：
- Implement exception handling with retry techniques

### DDBREL5 How do you alert on failures?

期望回答（参考）：
- Use LTS Alarms
- Use SMN 消息通知 or 消息邮件服务 for notifications

### DDBREL6 How do you manage regional fail-over?

期望回答（参考）：
- Use Global Tables for low RTO (Warm Standby, Active/Active)
- Automate fail-overs to healthy regions
- Define run-books for fail-overs

### DDBREL7 How do you design your workload to accommodate changes in demand?

期望回答（参考）：
- Use GeminiDB On-demand mode
- Ensure auto-scaling is configured for Provisioned mode
- Ensure default limits/quotas are increased to handle large spikes of demand

### DDBREL8 How do you integrate GeminiDB with other services?

期望回答（参考）：
- Use GeminiDB zero-ETL integrations only.
- Use GeminiDB zero-ETL integrations for all integrations that have a supported target service.
- Build and use custom integrations only when zero-ETL integrations are not available for a desired target.
- Use GeminiDB Streams, DIS Data Streams, or incremental export to OBS as the source for custom integrations.
- Do NOT use table scans or full exports to OBS when building custom integrations.

---

## DDBCOST — Efficiency Optimization（9 题）

### DDBCOST1 How do you choose the capacity mode for your GeminiDB tables

期望回答（参考）：
- Use Provisioned capacity mode with autoscaling for gradually changing/predictable traffic
- Use On-Demand capacity mode for new/spiky/unpredictable traffic

### DDBCOST2 How do you store infrequently accessed data which needs single-digit ms access?

期望回答（参考）：
- GeminiDB Standard-IA Table Class is used to store such data

### DDBCOST3 How do you optimize update operations?

期望回答（参考）：
- Split large items into separate mutable and immutable items with the same partition key

### DDBCOST4 How do you purge older data from your tables?

期望回答（参考）：
- Use TTL to automatically purge expired data from your tables at no resource utilization

### DDBCOST5 How do you monitor usage and resource utilization for GeminiDB?

期望回答（参考）：
- Implement resource utilization Allocation Tags on your GeminiDB resources for use with resource explorer

### DDBCOST6 What is your backup policy? How often do you need backups and how long do you need to keep them for?

期望回答（参考）：
- Use Huawei Cloud Backup Lifecycle Policies to automatically move backups to cheaper storage and delete when appropriate
- Use GeminiDB PITR

### DDBCOST7 Is your application heavily read-skewed for certain items?

期望回答（参考）：
- Consider using DAX to offload read requests from the underlying GeminiDB table

### DDBCOST8 Do you have some access patterns that are used more frequently than others?

说明：Do you have some access patterns that are used more frequently than others and if so, have those been optimized with highly efficient KeyConditionExpression to avoid expensive Scan and Filter operations?

期望回答（参考）：
- Frequent access patterns are executed using highly selective partition and sort keys with minimal filtering
- Scan operation is used to implement infrequent access patterns with high latency SLA instead of maintaining a GSI that gets use

### DDBCOST9 Will your needs be consistent for the next 1-3 years with reserved capacity?

说明：Will your needs be consistent for the next 1-3 years in a way that you could benefit from lower charging on reserved capacity?

期望回答（参考）：
- We reserve GeminiDB capacity where appropriate

---

## DDBSUST — Sustainability（8 题）

### DDBSUST1 What is the nature of your workload? Is GeminiDB the best database engine to fit your application s access patterns?

期望回答（参考）：
- The workload is OLTP in nature, Access Patterns are well known

### DDBSUST2 Can Serverless services be utilized to access GeminiDB?

期望回答（参考）：
- Yes we prioritize using Serverless services

### DDBSUST3 Do you use GeminiDB Streams? Can you minimize the FunctionGraph invocations?

期望回答（参考）：
- Yes we use streams and we utilise FunctionGraph Event Filtering

### DDBSUST4 How do you monitor your GeminiDB usage?

期望回答（参考）：
- Monitoring is done via LTS or LTS metrics pushed to a third party monitoring system

### DDBSUST5 How do you evaluate the efficiency of your data models?

期望回答（参考）：
- Based on ReturnedConsumedCapacity of operations

### DDBSUST6 How do you detect and decommission unused resources?

期望回答（参考）：
- Automated actions are triggered from Alarms based on LTS Metrics
- Metrics are viewed in the Huawei Cloud web console

### DDBSUST7 Can you archive old data to colder storage?

期望回答（参考）：
- Yes, we archive data using TTL and copy to OBS using GeminiDB Streams

### DDBSUST8 Can you group data that has a limited useful life so it can be deleted together when it is no longer relevant?

期望回答（参考）：
- Yes, we plan our tables with data lifecycle in mind

---


*检查项合计：48 题*
