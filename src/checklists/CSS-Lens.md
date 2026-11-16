# CSS 云搜索 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：CSS 云搜索（检索）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## AOSSOPS — Operational Excellence（7 题）

### aossops1 How do you monitor and analyze your CSS domains performance?

说明：CSS emits performance metrics to LTS 日志服务. Regularly review your cluster and instance metrics and configure recommended LTS alarms based on your workload performance.

期望回答（参考）：
- Setup the recommended LTS alarms for your CSS.
- Setup search slow logs, indexing slow logs, and error logs on your CSS domain to obtain more detailed inf
- Enable audit logs if your CSS domain uses fine-grained access control.
- Get notified from LTS alarms for your CSS domains.

### aossops2 How do you troubleshoot common issues in CSS domain?

说明：Operational runbooks can be used to troubleshoot common issues and restore service back into service.

期望回答（参考）：
- Identify and solve common CSS domain issues.
- Identify and solve common CSS node issues.
- Configuring alerts in CSS.

### aossops3 How do you get notification from available CSS updates?

说明：Do you subscribe the notification from CSS 云搜索服务 to get the latest software updates?

期望回答（参考）：
- Read the important changes from CSS.
- Subscribe the notification from CSS to get the lastest software updates.

### aossops4 Do you have enough IP addresses in VPC subnets?

说明：Do you know how many IP addresses you have where your CSS is deployed?

期望回答（参考）：
- Check how many IP addresses you have where your CSS is deployed.
- Review the cluster health and LTS 日志服务 metrics when blue/green deploying.

### aossops5 Do you have the developer guide for the CSS?

说明：Do you have developer guide for application team or client side to aware the CSS excpetion?

期望回答（参考）：
- Use the Huawei Cloud SDKs to interact with CSS.

### aossops6 How do you manage indexes?

说明：Do you enable Index State Management (ISM) in CSS?

期望回答（参考）：
- Use the Index State Management (ISM) in CSS to manage index life cycle.
- Use UltraWarm or cold storage tier for CSS.
- Use an index rollup to create a new index.

### aossops7 How do you operate your multi-tenancy indexes?

说明：Do you have your tenancy strategy?

期望回答（参考）：
- Understand multi-tenancy strategy and best practices.
- Hold the tenant position by a separate pointer.
- Manage your hot tenants.

---

## AOSSPERF — Performance Efficiency（7 题）

### aossperf1 How do you ensure the instances resources are utilized efficiently?

说明：Utilizing domains compute and storage resources efficiently helps you right size the domain.

期望回答（参考）：
- Check the CPU utilization and JVMMemoryPressure metrics on the Opensearch cluster.
- Check the DiskUtilization Metric to gauge storage usage.
- Enable Auto-Tune on your domains to improve cluster speed and stability.

### aossperf2 How do you ensure the storage resources are utilized efficiently?

说明：Choose the right storage solutions for your needs in CSS.

期望回答（参考）：
- Check your storage space.
- Check if there is storage skew.
- Check if the IOPS is the bottleneck.

### aossperf3 How do you make sure your ingestion execute efficiently?

说明：Integrations are a key way to reduce operational resource utilization and improve performance.

期望回答（参考）：
- Understand different ways to ingest data in CSS.
- Check the index performance.

### aossperf4 How do you assess the correct bulk request size to improve ingestion performance?

说明：Using the correct bulk request size and compression helps improve ingestion performance.

期望回答（参考）：
- Tune Refresh Interval to improve indexing performance.
- Check the refresh_interval value.
- Tune your Bulk request size to improve ingestion performance.
- To reduce the size of CSS responses, exclude unnecessary fields with the filter_path parameter.
- Use gzip compression to reduce the payload size of requests and responses.
- Use the Huawei Cloud SDKs to interact with the CSS API.

### aossperf5 How do you make sure your query execute efficiently?

说明：You can optimize the query experience by improving URI parameters, custom packages, SQL support, or asynchronous search.

期望回答（参考）：
- Understand how to query the CSS.
- Use the Huawei Cloud SDKs to interact with the CSS API.
- Check the SQL metrics.
- Using benchmark tools to improve your query experience.

### aossperf6 How do you monitor multi-tenancy index performance?

说明：Try to align shard count and node count.

期望回答（参考）：
- Proactively monitor your index and query performance in CSS.

### aossperf7 How do you analyze your CSS performance?

说明：Try to understand your CSS from tools.

期望回答（参考）：
- Proactively analyze your CSS performance.

---

## AOSSSEC — Security（7 题）

### aosssec1 How do you protect your Huawei Cloud account?

说明：Huawei Cloud is responsible for protecting the global infrastructure that runs all of the Huawei Cloud. You are responsible for maintaining control over your content that is hosted on this infrastructure.

期望回答（参考）：
- Use multi-factor authentication (MFA) with each account.
- How do you log IAM calls?

### aosssec2 How do you control access to your CSS?

说明：CSS provides fine-grained access control in different ways.

期望回答（参考）：
- Fine-grained access control offers additional ways of controlling access to your data on CSS.
- Fine-grained access control lets you establish role based access control to who can access certain data within an CSS Se

### aosssec3 How do you restrict your CSS domains?

说明：You can launch Huawei Cloud resources, such as CSS domains, into a virtual private cloud (VPC). A VPC is a virtual network that's dedicated to your Huawei Cloud account.

期望回答（参考）：
- Are Opensearch domains deployed within a VPC?
- Apply restrictive access policies and follow the principle of least privilege when granting access to the configuration API and

### aosssec4 How do you protect data at-rest and in-transit with CSS?

说明：Data should be encrypted at all times to ensure its security. Data encryption is an available feature of CSS.

期望回答（参考）：
- How do you communicate with CSS?
- Enable node-to-node encryption for CSS domains.
- Enable encryption at rest for CSS domains.
- How do you encrypt logs in LTS 日志服务?

### aosssec5 How do you track and audit the access to the CSS domains?

说明：Domains access should be tracked and audited.

期望回答（参考）：
- Enable Audit-logs on the CSS Domains(only for FGAC enabled domains).
- Monitor the CTS logs for CSS service.
- Monitor domain events in real time with 云 事件网格 EG. The same events are also sent to LTS 日志服务 Events
- Huawei Cloud Config can help to evaluate Huawei Cloud Resource Configurations.

### aosssec6 How do you protect an CSS-managed VPC endpoint?

说明：These endpoints create a private connection between your VPC and CSS.

期望回答（参考）：
- How do you communicate with your CSS VPC endpoint?
- How do you authorize VPC endpoint access?

### aosssec7 How do you protect multi-tenancy data on an CSS?

说明：How to design, deploy, and architect your multi-tenant document structure.

期望回答（参考）：
- How to login the CSS Dashboards?
- How to access the CSS from your VPC?
- How to access your multi-tenancy CSS?

---

## AOSSCOST — Efficiency Optimization（5 题）

### aosscost1 How do you choose the instance types for your CSS domains?

说明：With CSS, you can select the optimal instance type and storage option for your workload easily.

期望回答（参考）：
- Using latest generation instances to create domains.
- modernize to latest generation instances.
- Choose instance type for your CSS master nodes.
- Evaluate instance type for your CSS data nodes and testing.
- Change the node types to Huawei Cloud Graviton-based instances to improve performance.
- Calculating storage requirements.
- Choose the proper EVS 云硬盘卷类型.
- Evaluate the number of shards.

### aosscost2 Will your needs be consistent for the next 1-3 years with reserved capacity?

说明：Benefit from significant efficiency gains of up to 72 percentages compared to On-Demand charging rates. Maximize your savings by following Huawei Cloud resource explorer Savings Plans recommendations.

期望回答（参考）：
- Procure CCE 容器集群 弹性云服务器 Reserved Instances for CSS.
- Use Saving Plan for CSS domain

### aosscost3 Optimizing resource utilization with tiered storage in CSS.

说明：CSS service provides tiered data storage for long term data retention or read-only accessed data and helps reduce resource utilization.

期望回答（参考）：
- Use UltraWarm tier to store large amount of Read-only data.
- Use Cold tier to store infrequently accessed or historical data
- Rolling over with Index State Management (ISM).

### aosscost4 How do optimize the indexes for your tenants?

说明：How you can secure your tenants and how you should plan for capacity to understand the performance implications of your tenancy.

期望回答（参考）：
- Understand tenancy basics.
- Understand different tenancy strategies.
- Managing document-level tenancy.
- Reduce the hot shards.

### aosscost5 How do estimate your CSS resource utilization?

说明：Calculate your CSS and architecture resource utilization in a single estimate tool.

期望回答（参考）：
- You can get started for free on CSS with Huawei Cloud basic allowance.
- Evaluate the ECS 弹性云服务器 instances charging model in CSS.
- Evaluate the storage charging model in CSS.
- Evaluate the Huawei Cloud data transfer charges.
- Evaluate the OBS resource utilization.
- Consult Huawei Cloud charging specialists.

---

## AOSSREL — Reliability（5 题）

### aossrel1 Does your domain uses the latest CSS version and Service Software version?

说明：CSS regularly adds support for community-maintained versions of CSS. Always upgrade to the latest CSS versions when they're available.

期望回答（参考）：
- There are notifications about CSS updates.
- Upgrade your CSS domain to the latest available version.

### aossrel2 What is your disater recovery strategy for your CSS?

说明：Take manual snapshots for you CSS cluster or to replicate data from one cluster to another.

期望回答（参考）：
- Do you define your disaster recovery (DR) for your CSS strategy?
- Considering the cross-cluster replication for CSS.
- Create manual snapshots for CSS indexes.

### aossrel3 How do you ensure that your CSS domains are always available?

说明：Distributes your CSS workloads cross multiple Availability Zones in the same Region.

期望回答（参考）：
- Use dedicated master nodes.
- Configuring a multi-AZ domain in CSS data nodes.
- Index shards distribution.
- Enable zone awareness.

### aossrel4 Do you understand CSS quotas?

说明：Your Huawei Cloud account has default quotas, formerly referred to as limits, for each Huawei Cloud service.

期望回答（参考）：
- CSS domain and instance quotas.
- Adjust CSS domain and instance quotas.

### aossrel5 Do you use ECS 弹性云服务器 instance type T-class in production environment?

说明：Avoid using T2 or t3.small instances for the production environment.

期望回答（参考）：
- Avoid using T-class instances for the production environment.

---


*检查项合计：31 题*
