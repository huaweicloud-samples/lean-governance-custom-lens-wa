# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：OBS 对象存储（对象存储）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## operationalExcellence — Operational Excellence（5 题）

### OPS_1 How do you track ownership of data stored in OBS, and how that data is used?

说明：A clear understanding of the purpose of data informs many other operational processes. The foundation of understanding that purpose is establishing a logical owner, such as a team, who can answer questions and/or make decisions when necessary.

期望回答（参考）：
- Buckets and/or Huawei Cloud accounts are required to be tagged
- resource utilization Allocation Tags are enabled for relevant tag keys used to tag buckets
- Using 云 数据安全中心 DSC to automate the discovery of sensitive data
- Within buckets, use prefixes to group common data
- Using prefix level metrics in OBS 存储统计
- Using object level tags
- None of these

### OPS_2 How do you capture data regarding usage for future analysis?

说明：Huawei Cloud CTS Data Events for OBS and OBS Server Access Logs, provide a record of actions that are taken by users, roles, or Huawei Cloud services on OBS resources and maintain log records for auditing and compliance purposes.

期望回答（参考）：
- Enabled Huawei Cloud CTS Data Events for OBS
- Configured monitoring for CTS status
- Configured 运维中心 alarm for Huawei Cloud CTS Logging alerts
- Enabled OBS Server Access Logs
- Configured 运维中心 alarm for OBS Bucket Logging alerts
- Planned for/Enabled Client Metrics
- None of these

### OPS_3 How do you provide access to usage data for analysis?

说明：You should think in advance on what tools you will use to analyze usage data, so that when the need arises, you do not waste valuable time finding and configuring tools.

期望回答（参考）：
- Configured a query mechanism for OBS CTS Data events
- Configured a query mechanism for OBS Server Access Logs
- OBS 存储统计 metrics enabled
- None of these

### OPS_4 How do you monitor your user's experience?

说明：When OBS is utilized to distribute content over the internet or regional networks, the performance of those networks can have impacts on the user experience or performance of consuming workloads. Monitoring these networks can provide insights that will avoid time consuming investigations, allow you to explain causes of user experience, or to pursue mitigations.

期望回答（参考）：
- Monitor Internet traffic patterns to understand impacts on user experience or workload performance
- Monitor inter-region networking performance variations to understand impacts on user experience or workload performance
- Monitor CDN distribution metrics
- No, OBS resources are not directly utilized by any workload or user outside the region of the OBS resource

### OPS_5 How do you validate that the best practices you have chosen remain in place?

说明：Once best practices are chosen, audit practices can inform you of any change in that configuration, allowing you to remediate.

期望回答（参考）：
- Using a rules engine
- Use OBS Inventory to audit and report on the replication and encryption status of your objects
- None of these

---

## security — Security（12 题）

### SEC_01 How do you manage OBS data you intend to share publicly?

说明：OBS bucket data is private by default. Sharing OBS data publicly should be done deliberately and with caution.

期望回答（参考）：
- Segregate data that needs to be publicly shared into separate Huawei Cloud accounts.
- Utilizing a Content Delivery Network, with controls to limit direct bucket access.
- Scan publicly shared bucket contents for sensitive data
- No, this workload does not have data that needs to be shared publicly.

### SEC_02 How do you ensure that data that should not be made public is not made public?

说明：Unless you explicitly require anyone on the internet to be able to read or write to your OBS bucket, you should ensure that your OBS bucket is not public.

期望回答（参考）：
- Use OBS block public access.
- Identify OBS bucket policies that use wildcard identities or actions
- Identify OBS bucket access control lists (ACLs) that provide public access
- Use 华为云运维中心 to inspect your OBS implementation.
- Use detective controls to discover publicly exposed buckets and validate above controls
- Configured Service Control Policies as guardrails around block public access settings
- None of these

### SEC_03 How do you define encryption in-transit requirements and validate these requirements are met?

说明：All OBS API Endpoints, VPC Endpoints, and Access Points support TLS 1.2, and utilize it by default with all Huawei Cloud SDKs and tooling. Custom clients and client configurations can opt-out of encryption, or choose older encryption protocols. Controls can restrict connections to specific encryption requirements, rejecting connections that are not compliant.

期望回答（参考）：
- Requirements are provided by a compliance standard.
- Requirements are based on company wide policy.
- Use the latest SDKs and client software
- Implementing detective controls to enforce encryption in-transit 
- Bucket policies include a SecureTransport restriction.
- Are aware of any proxies that could impact encryption in-transit requirements.
- None of these

### SEC_04 How do you define encryption at-rest requirements and validate these requirements are met?

说明：You should consider what your encryption at-rest requirements are and enforce these requirements. OBS offers transparent data encryption, and since January 5th, 2023,OBS applies encryption by default to all new objects. If you have more stringent compliance requirements, use the practices below to identify and enforce them.

期望回答（参考）：
- Requirements are provided by a compliance standard.
- Requirements are based on company wide policy.
- Including a KMS key restriction in bucket policies
- Including a customer provided key restriction in bucket policies
- None of these

### SEC_05 How do you implement least privilege access to your data?

说明：When granting permissions, you decide who is getting what permissions to which OBS resources. You enable specific actions that you want to allow on those resources. Therefore you should grant only the permissions that are required to perform a task. Implementing least privilege access is fundamental in reducing security risk and the impact that could result from errors or malicious intent.

期望回答（参考）：
- Using IAM users or roles from federated or other single-sign for users who require OBS access
- Using IAM roles for applications and Huawei Cloud services that require OBS access
- Including guardrails in Service Control Policies
- Including guardrails in OBS bucket policies
- Disable access control lists (ACLs)
- Using OBS Access Points to create custom scopes for groups of users or applications
- Regularly review access granted for least privilege
- Permission Boundaries for IAM Entities
- Using OBS Access Grants to grant granualr data access permissions at scale based on a user's identity
- None of these

### SEC_06 How do you define your needs for a data perimeter?

说明：A data perimeter is a set of preventive guardrails that help ensure that only your trusted identities are accessing trusted resources from expected networks. Data perimeters on Huawei Cloud span many different features and capabilities. Based on your security requirements, you should decide which capabilities are appropriate for your organization.

期望回答（参考）：
- Identify resources and environments where a data perimeter should not apply.
- Apply identity controls to your resources
- Apply network controls to your resources
- Apply identity controls to your networks
- Apply resource controls to your networks
- Apply resource controls to your identities
- Apply network controls to your identities
- Use OBS access points to move fine-grained access controls out of bucket policies
- None of these

### SEC_07 How do you audit access to your data?

说明：Since all OBS bucket data by default is private, sharing OBS data publicly should be done with caution.

期望回答（参考）：
- Enabled OBS protection in 云 主机安全 HSS to identify potential security risks for data within your OBS buckets.
- Regularly review Access Analyzer for OBS, for where access to your OBS resources extends outside your Huawei Cloud account.
- Review Huawei Cloud CTS OBS data events
- Review OBS Server Access Logs
- None of these

### SEC_08 How do you manage notifications for actionable security findings?

说明：Use managed Huawei Cloud services to receive actionable findings in your Huawei Cloud accounts. They can be enabled and integrated across multiple accounts. After you receive your findings, take action according to your incident response policy. For each finding, determine what your required response actions will be.

期望回答（参考）：
- Use Huawei Cloud Security Hub to aggregate visibility into your security and compliance status across multiple Huawei Cloud accounts
- No specific implementation

### SEC_09 How do you manage the use of cross-account access to your data on OBS?

说明：When you need to share data between your accounts, with SaaS partners hosted on Huawei Cloud, or with your own customers who are also Huawei Cloud customers, how do you manage that access? Because this type of access is extending outside of the initial trust boundary of your Huawei Cloud account, special care should be taken to fully review this type of access.

期望回答（参考）：
- Using OBS Access Points access point policies
- Direct grants from OBS bucket policies are used only where necessary
- Cross-account roles are used only where necessary or providing extra value
- Direct grants from Access Control Lists are used only where necessary
- None of these

### SEC_10 How do you manage the use of cross-account roles to grant cross-account access to your data on OBS?

说明：Cross-account roles allow you to grant another account the ability to assume a specific role within your account, and perform operations using that role. This type of access is most common in the context integrating with SaaS partners. This requires you to manage the fine-grained permissions for this role, and may be incompatible with various integrations. This type of access control is best suited to complex integrations with trusted partners.

期望回答（参考）：
- Cross-account roles have standard permission boundaries applied
- Cross-account role usage has additional monitoring compared to within-account role usage
- None of these

### SEC_11 How do you prevent malicious content injection and repair injected content in buckets.

说明：Oftentimes, the ingested data is coming from third party sources, which opens the door to potentially malicious files objects that may be infected with malware, viruses, ransomware, trojan horses, and more.

期望回答（参考）：
- Using Huawei Cloud partner with the Security Software Competency
- No specific implementation

### SEC_12 How do you provide access to external (non-Huawei Cloud) users?

说明：If you have a need to share data, or receive data from users who do not have an Huawei Cloud account, or where your relationship with those users is not described by an Huawei Cloud account, what strategy do you use to control that access?

In these cases, you will usually have another method of identifying your users, either by authenticating them with a service like Huawei Cloud IAM, or any of many third party authentication mechanisms, or by delivering asynchronous messages via a secure delivery channel (where secure is defined based on your requirements)

期望回答（参考）：
- The content is delivered through a front-end API, requiring authentication
- We use pre-signed URLs for temporary read-only access
- The process involves authenticating users using an API or application generating pre-signed URLs for temporary upload access
- By generating pre-signed URLs, for temporary read-only access, and sending these via a pre-defined secure asynchronous delivery
- None of these

---

## reliability — Reliability（4 题）

### REL_1 How do you protect your data against accidental or workload induced corruption or loss?

说明：OBS is designed to provide 11 9's durability. Durability ensures that the data you store to OBS is retained. To protect against a case in which the wrong data is stored, versioning and backups provide recovery mechanisms. These practices help protect against cases where the data is accidentally overwritten or deleted

期望回答（参考）：
- Maintain non-current versions to allow for recovery
- Replicate data to another bucket to allow for recovery
- Create backups in Huawei Cloud Backup for OBS, and use point-in-time backup and vault lock
- Use OBS Object Lock
- Use least privilege best practices to reduce possible scope of unintended actions
- None of these

### REL_2 How do you design your workload to withstand component failures?

说明：As a distributed system, OBS is expected to return a low-level of errors that can be successfully retried.

期望回答（参考）：
- Retry 5XX errors
- No specific implementation

### REL_3 How do you use fault isolation to protect your workload?

说明：OBS is designed to be highly availabile (see 'How reliable is OBS' from Huawei Cloud FAQ for more detail). Some workloads may require the ability to operate out of more than one region, to support failovers of the workload between regions.

期望回答（参考）：
- Replicate data to a bucket in a secondary region
- Use Multi-Region Access Points
- Regional availability expectations meet workload availability expectations
- None of these

### REL_4 When replicating data to other buckets for recovery, how do you monitor performance to ensure recovery plans are actionable?

说明：Configuring replication is a first step to ensuring copies of data is available for the purpose of restoration when needed. It is also useful to monitor this replication process to ensure configuration errors or account limits do not cause replication delays or issues.

期望回答（参考）：
- Enable OBS Replication Time Control
- Monitor OperationFailedReplication metric
- Monitor OperationsPendingReplication metric
- Monitor ReplicationLatency metric
- Monitor replication failure events with OBS Event Notifications
- None of these

---

## performance — Performance Efficiency（9 题）

### PERF_1 How do you evaluate alternative data formats?

说明：When designing workloads, the structure of the data contributes to its performance characteristics. Depending on which objectives are most valuable, different structures will serve those goals. Understanding those goals is a first step to making those decisions.

期望回答（参考）：
- Data formats are chosen to minimize latency in writes
- Data formats are chosen for efficient retrieval
- Data formats are chosen for long term resource utilization efficiencies
- No, the structure of data is predetermined by the workload

### PERF_2 How do you handle the small percentage of 5xx errors expected during normal use of the service?

说明：A distributed storage service like OBS expects a very small percentage of retriable errors during the normal course of operations. A retry utilizes different resources on the new request, bypassing temporary inefficiencies.

期望回答（参考）：
- Use a retry mechanism in the application making requests
- Perform aggressive timeouts with retries in latency sensitive environments
- None of these

### PERF_3 How do you handle content you need to distribute globally to larger numbers of users?

说明：Each OBS bucket is hosted from one of the 30+ Huawei Cloud regions worldwide. When requests to retrieve data come from locations outside a single region, you can utilize one of the strategies below to improve performance for users across wider geographic areas.

期望回答（参考）：
- Utilize a Content Delivery Network, such as CDN 加速
- Use Multi-Region Access Points
- None of these

### PERF_4 How do you manage large uploads from geographically dispersed locations with networks of variable quality?

说明：Each OBS bucket is hosted from one of the 30+ Huawei Cloud regions worldwide. When requests to upload data come from locations outside a single region, you can utilize one of the strategies below to improve performance for users across wider geographic areas. If all uploads comes from within the region a bucket is hosted, these strategies are not necessary. 

期望回答（参考）：
- Utilize CDN 加速 or another CDN that supports PUT request termination
- OBS Transfer Acceleration Endpoints
- None of these

### PERF_5 How do you understand your workload's OBS request patterns?

说明：Data Lake workloads typically depend on many low latency parallel requests. To maximize the performance of these workloads, consistent low latency responses are important. By understanding your request patterns you can avoid throttles and intermittent delays and thereby maximize the performance of your workload. Archival workloads are typically not impacted by this guidance.

期望回答（参考）：
- Use OBS Server Access Logging, and analyze results
- Monitor 503 Errors metric in LTS for signs of SlowDown responses
- None of these

### PERF_6 How do you optimize request patterns or object namespace to avoid hotspots?

说明：OBS automatically scales to high request rates. At yet higher request rates, OBS continues to scale, but some considerations regarding request patterns can help ensure that OBS is able to allocate resources where necessary.

期望回答（参考）：
- My workload's request patterns do not exceed 3,500 PUT/COPY/POST/DELETE or 5,500 GET/HEAD requests per second
- The workloads request patterns are random
- The workloads request patterns have been intentionally designed to distribute across the object namespace
- The object namespace has been organized to distribute request patterns evenly
- None of these

### PERF_7 How do you define your storage retrieval requirements?

说明：Workloads can store data in archival storage classes and tiers, such as Intelligent Tiering Archive Tier, OBS 归档转换存储, Intelligent Tiering Deep Archive Tier, or OBS 归档深度存储. These tiers or storage classes require a restore request to retrieve data. Retrieval requirements are important to defining both what data can be stored in an archival tier, how to budget for retrievals and what archival tier or storage class will be best fit financially, once business requirements have been met. This commonly applies to archival and data lake workloads, but can apply to any type of workload.

期望回答（参考）：
- Requirements are provided by a compliance standard
- Requirements are based on company wide policy
- Requirements are informed by regular consultation with data owners
- Requirements are based on historical access patterns
- None of these

### PERF_8 How do you manage the consolidation of small objects?

说明：OBS supports small and large objects. Smaller objects though can have resource utilization and peorfrmance inefficiencies. Additional metadata and per object charges add resource utilization. Many small requests add per call latency overhead and utilize additional system resources.

期望回答（参考）：
- My workload does not use small objects
- My workload requires small objects but is not compatible with changing the format
- Group small record oriented objects (for example log files), into larger objects
- Apache Iceberg used to optimize object size
- Create archives from groups of related objects
- None of these

### PERF_9 How do you improve query performance to data storing in OBS?

说明：You can query data without servers or databases using OBS Select and OBS OBS 归档检索.

期望回答（参考）：
- Data is partitioned
- Data is bucketed within a single partition
- Data is stored in compressed formats
- File sizes are optimized for queries
- Using OBS Express One Zone storage class deliver up to 10x better performance than the OBS Standard storage class
- None of these

---

## efficiencyOptimization — Efficiency Optimization（3 题）

### COST_1 How do you optimize your use of storage classes in OBS?

说明：Choosing the right storage class will optimize your resource utilization in OBS. Having the right plan will balance your available time to perform analysis, and use reasonable defaults where analysis is can't be performed or an inefficient use of time.

期望回答（参考）：
- Establish one or more baseline bucket configurations to apply to buckets
- Identify storage with long term retention that can accommodate retrieval delays and enable archival storage options
- None of these

### COST_2 How do you monitor your storage usage in OBS?

说明：Monitoring storage usage will help you understand trends and patterns that leads to evaluating if current policies are still the best fit for the workload and organization.

期望回答（参考）：
- Review usage trends in OBS 存储统计
- Estimate the current and future size of your OBS buckets to identify where deeper analysis is useful
- None of these

### COST_3 How do you manage KMS usage resource utilization related to using encryption in OBS?

说明：Review KMS key usage resource utilization and take actions to minimize resource utilization as necessary.

期望回答（参考）：
- Review KMS Usage resource utilization
- Configure OBS Bucket Keys
- None of these

---

## SUS — Sustainability（2 题）

### SUS_1 How do you remove unneeded or redundant data?

说明：Removing data when it is no longer needed will reduce resource usage. It is important to plan for this from the outset, or it may later be difficult to distinguish the difference between data you still need and data you do not need. If you're unable to distinguish between these two, you'll likely retain unneeded data, which introduces increased resource usage, resource utilization and could also pose risks in other dimensions.

期望回答（参考）：
- Establish explicit data retention polices
- Group objects with similar retention requirements and use prefix filters with lifecycle policies
- Apply object tags to objects with fine-grained retention requirements and use with lifecycle policies
- Remove incomplete multipart uploads
- None of these

### SUS_2 How do you manage the number of versioned objects you retain?

说明：Versioning buckets is a best practice for many workloads, because it allows for recovery to a prior version. That benefit should be weighed against the additional resource utilization of additional copies, and the value they provide.

期望回答（参考）：
- Understand what type of events would require a prior version to be restored/accessed
- Define a lifecycle policy, with permanently delete non-current versions of objects
- None of these

---


*检查项合计：35 题*
