# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：DMS/Kafka 消息（消息队列）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance（5 题）

### PERF1 How do you ensure your cluster is sizing efficiently?

说明：Right-sizing your cluster from all aspects to optimize performance and resource utilization-efficiency. Some key areas like number of brokers, number of partitions per broker, replication factors...etc. Remember that right-sizing is an ongoing process, and it's important to continuously monitor and adjust your DMS cluster configuration based on changing workload patterns and requirements.

期望回答（参考）：
- The number of brokers per cluster is estimated to meet your throughput, availability, resource utilization and latency requirements.
- The number of partitions (including leader and follower replicas) per broker is following the recommended value for each instan
- Ensure the leader replicas are balanced evenly across the cluster.
- Use KRaft mode for any new DMS clusters running versions 3.7 to 3.9.
- Choose the DMS cluster type that best fits your business needs.

### PERF2 How do you ensure the instances resources are utilized efficiently?

说明：Instance resources like CPU utilization, network throughput, memory and JVM heap..etc. Make sure you select the correct instance configuration to maintain the performance requirement.

期望回答（参考）：
- When using m5.4xl, m7g.4xl, or larger instances, you can optimize the cluster throughput by tuning the num.io.threads and num.n
- Maintain the total CPU utilization for your brokers, defined as CPU User + CPU System under 60 percent.
- Take action when HeapMemoryAfterGC increases above 60 percent.
- Right size for network and storage throughput.
- Monitor that VolumeReadBytes and VolumeWriteBytes stay within EVS 云硬盘 throughput capacity.
- Ensure TrafficShaping remains within the instance's network capacity.

### PERF3 How do you ensure the storage resources are utilized efficiently?

说明：Producer's performance is influenced by the disk IOPS and throughput of the broker storing log segments.  On the other hand, disk capacity is also a factor to consider, it directly impacts the cluster's ability to retain messages, handle high-volume data streams, and maintain performance over time.

期望回答（参考）：
- Store data in tiered storage for historical data
- Specify a retention time period or retention log size to free up spaces.
- Take action when KafkaDataLogsDiskUsed metric is reaches or exceeds 85 percent.
- If disk throughput is the bottleneck, enable provisioned storage throughput to specify a higher throughput without having to pr

### PERF4 How do you make sure your producers execute efficiently?

说明：Kafka producers send messages to the Kafka cluster. This section explains how to monitor and improve producer s performance.

期望回答（参考）：
- Scale out or enable provisioned throughput to increase cluster write throughput.
- Monitor broker-level BytesInPerSec for the amount of data ingested into the cluster.
- Monitoring the producer-side metrics such as request-latency-avg using your preferred metric capture mechanism.
- Set linger.ms to control the amount of time a producer waits for a batch to fill.
- Batch send message (recommend batch.size 128KB and buffer.memory 64MB for most use cases).
- Understang the trade-off between message size and performance.
- Enable data compression for messages (recommend either lz4 or zstd running a producer on a high latency network).

### PERF5 How do you make sure your consumers execute efficiently?

说明：Kafka consumers retrieve and process messages from brokers. The way you configure partitions and batch messages directly affects the throughput and latency. This section shows you how to monitor and improve consumer's performance.

期望回答（参考）：
- Number of consumers at least equal to the number of partitions.
- Scale up to increase cluster read throughput.
- Monitor broker-level BytesOutPerSec for the amount of data consumed from the cluster.
- Monitor consumer lags metrics: EstimatedMaxTimeLag, EstimatedTimeLag, MaxOffsetLag, OffsetLag, and SumOffsetLag for consumer's 
- Monitoring the producer-side metrics such as records-lag-max using your preferred metric capture mechanism.
- Reduce the number of fetches (recommend fetch.min.bytes for a minimum 32 bytes to a higher value of 128 bytes for most use cas
- Reduce consumer rebalance events.

---

## OPS — Operational Excellence（4 题）

### OPS1 Does your DMS cluster performance metrics meet the suggested criteria?

说明：Do you know the key cloudwatch metrics that need to be monitored?

期望回答（参考）：
- CPU Utilization (CpuUser + CpuSystem)
- KafkaDataLogsDiskUsed
- PartitionCount
- TrafficShaping
- UnderMinIsrPartitionCount
- ActiveControllerCount
- UnderReplicatedPartitions
- HeapMemoryAfterGC

### OPS2 How will you manage DMS cluster's metadata?

说明：Do you know Kafka can be decoupled from ZooKeeper?

期望回答（参考）：
- DMS replaced ZooKeeper with KRaft since version 3.7
- Create a whole new cluster with KRaft for metadata management.

### OPS3 Do you know how to avoide impact during DMS maintenance

说明：Do you know the key Kafka parameters that need to be considered?

期望回答（参考）：
- Replication factor
- min.insync.replicas
- Ensure client connection strings include at least one broker from each availability zone.
- retries
- retry.backoff.ms

### OPS4 Do you know DMS by default does not clean any old messages?

说明：How to set retention policy to clean old messages?

期望回答（参考）：
- Kafka log.retention parameters
- Kafka log.segment.bytes

---

## SEC — Security（7 题）

### SEC1 How are you managing security control for your DMS cluster?

说明：Review your security settings to ensure that access is restricted only to trusted networks and clients.

期望回答（参考）：
- Network isolation
- Encryption
- Audit with Huawei Cloud CTS
- Monitoring with LTS 日志服务
- Authentication
- Authorization
- Patching

### SEC2 How are you managing access permissions for your DMS cluster?

说明：This prevents unauthorized interception and ensures data protection.

期望回答（参考）：
- Access control
- Client authentication and authorization
- Regular access audits

### SEC3 How are you managing data security?

说明：How are you secure communication between clients and DMS brokers, and data at rest?

期望回答（参考）：
- Only allow TLS encrypted data in transit. This is the default setting.
- Only allow plaintext data in transit
- Allow both plaintext, as well as TLS encrypted data in transit.
- Encryption at rest with SSE (sever-side-encryption)
- Encryption at rest with CMK (customer-managed-keys)

### SEC4 How do you manage logs?

说明：How do you manage your DMS logs and incident?

期望回答（参考）：
- View on incident
- Enable broker logs to external storage (OBS, LTS, Data Firehose etc.)
- Automatic review and alert system like CSS.

### SEC5 How do you manage the organization compliance?

说明：How do you managed the organization compliance?

期望回答（参考）：
- Regular audit to comply for internal
- Regular audit to comply with 3rd-party
- I don't know any compliance

### SEC6 How will you manage secuirty patches?

说明：What is your strategy for keeping DMS brokers updated and patched?

期望回答（参考）：
- Understand the supported Apache Kafka versions
- Set the topic replication factor (RF) and min.insync.replicas as best practices.
- Configure clients to use multiple broker connection strings.
- Set the retries and retry.backoff.ms as client best practices.

### SEC7 How are you managing and rotating credentials used for DMS authentication?

说明：Evaluate the use of Huawei Cloud Secrets Manager or other secure methods for storing and rotating SASL/SCRAM credentials, certificates, etc.

期望回答（参考）：
- Set up a secret in Huawei Cloud Secrets Manager
- Connecting to your cluster with sign-in credentials

---

## REL — Reliability（8 题）

### REL1 How are you ensuring that your DMS cluster is set up to support high availability and reliability?

说明：Ensure cluster has the right architectural foundation to handle growth and potential failures.

期望回答（参考）：
- Deploy across multiple Availability Zones (AZs)
- Appropriate broker and topic configuration
- Storage management
- Chaos testing

### REL2 Are you monitoring your DMS cluster to maintain availability?

说明：Introduce that Huawei Cloud provides several tools to monitor the health of resources.

期望回答（参考）：
- LTS Metrics
- LTS Alarms
- LTS Logs
- Huawei Cloud Health Dashboard

### REL3 What is your DMS cluster backup strategy, and how quickly can you recover from a disaster or outage?

说明：It s important to review the client s backup and disaster recovery (DR) plans.

期望回答（参考）：
- Understand the definition of RTO and RPO
- Automatic Recovery
- Client Configuration for Resilience

### REL4 How about your data retention and durability policy?

说明：Ensure your data retention policies

期望回答（参考）：
- Define data retention policies
- Backups
- Segment cleanup policies
- Tiered storage

### REL5 How are you handling increases in traffic or demand without impacting performance?

说明：Discuss how the client handles fluctuating workloads and plans for growth.

期望回答（参考）：
- Right-sizing partitions
- Right-sizing brokers
- Autoscaling with DMS Serverless
- LTS Alarms for Provisioned DMS Clusters
- Use of data compression
- Shorten log retention for high-traffic topics
- Storage management

### REL6 How do you manage DMS updates or infrastructure changes while maintaining reliability?

说明：Understand how the client introduces changes to their DMS cluster.

期望回答（参考）：
- Leverage rolling upgrades
- Distribute replicas across AZs
- Implement client-side retry logic and backpressure management
- Ensure client connection strings include at least one broker from each availability zone.

### REL7 How often do you test your DMS cluster s resilience to failure and recovery procedures?

说明：Discuss the importance of simulating failure scenarios.

期望回答（参考）：
- Test in a staging environment
- periodically failover and recovery drills
- After significant changes
- Document disaster recovery runbooks

### REL8 How are your Kafka clients configured for reliable operations?

说明：Evaluate client retry policies, timeout settings, buffer configurations, and consumer group strategies.

期望回答（参考）：
- Producer configuration
- Consumer configuraiton
- Ensure client connection strings include at least one broker from each availability zone

---

## resource utilization — Efficiency Optimization（9 题）

### COST1 Are you optimizing your cluster size to meet workload needs while minimizing resource utilization?

说明：Ensure your cluster is sized appropriately to meet workload needs while minimizing unnecessary resource utilization.

期望回答（参考）：
- Have you evaluated and selected the appropriate number of brokers?
- Are current instance types meeting performance requirements?
- Is auto-scaling mechanism in place?

### COST2 Are you optimizing your storage configuration to meet workload requirements while reducing unnecessary resource utilization?

说明：Evaluate and adjust your storage configuration to meet workload requirements while avoiding over-provisioning and unnecessary resource utilization.

期望回答（参考）：
- Do you regularly assess storage capacity usage?
- Have you selected the most resource-efficient storage type?
- Is data lifecycle management implemented?

### COST3 Are you optimizing your network configuration to support workload needs while minimizing unnecessary resource utilization?

说明：Assess and configure your network setup to meet performance needs while minimizing data transfer and infrastructure resource utilization.

期望回答（参考）：
- Is network traffic compression implemented?
- Have network routing configurations been optimized?

### COST4 Are you improving operational efficiency to streamline processes and reduce unnecessary operational resource utilization?

说明：Evaluate and refine your operational workflows to minimize manual effort, lower overhead, and maintain resource-efficient operations.

期望回答（参考）：
- Are automated operational processes established?
- Is a comprehensive monitoring system implemented?
- Are standardized operating procedures in place?

### COST5 Are you using a efficiency-improving checklist to consistently identify and eliminate unnecessary spend across your workloads?

说明：Implement and review a structured efficiency-improving checklist to ensure ongoing visibility, accountability, and optimization of cloud resources.

期望回答（参考）：
- Do you conduct regular resource utilization reviews?

### COST6 Are you setting up effective resource utilization monitoring to track spending, detect anomalies, and maintain resource utilization control?

说明：Establish and configure resource utilization monitoring tools to provide visibility into usage patterns and enable timely efficiency optimization actions.

期望回答（参考）：
- Have you set up daily resource utilization tracking in Huawei Cloud resource explorer?
- Have you established resource utilization alerting mechanisms?
- Have you implemented a resource tagging strategy?

### COST7 Are you optimizing your charging model choices to align with workload patterns and minimize overall resource utilization?

说明：Evaluate and select the most resource-efficient charging models such as on-demand, reserved, or savings plans based on your workload behavior and long-term requirements.

期望回答（参考）：
- Have you evaluated the use of Reserved Instances?

### COST8 Are you leveraging available efficiency-improving tools to identify optimization opportunities and reduce unnecessary spending?

说明：Use automated efficiency-improving tools to gain insights into usage patterns and continuously drive efficient resource utilization.

期望回答（参考）：
- Are you utilizing Huawei Cloud Compute Optimizer?

### COST9 Are you performing regular resource utilization assessments to ensure your workloads remain optimized and free of unnecessary spend?

说明：Conduct recurring resource utilization reviews to identify inefficiencies, validate resource alignment with demand, and maintain ongoing efficiency optimization.

期望回答（参考）：
- Do you conduct regular performance-to-resource utilization analysis?
- Do you periodically review and update efficiency optimization strategies?

---


*检查项合计：33 题*
