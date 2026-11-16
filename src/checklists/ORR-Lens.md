# 运维就绪检查 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：运维就绪检查（运维就绪度（ORR））

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## architecture — 01 - Architecture（6 题）

### architecture_architecture_diagram Architecture Diagram (H)

说明：Please provide a diagram of your system or application architecture, both at the infrastructure level and at the data/network flow level. Note the locations in the notes section below.

期望回答（参考）：
- Architecture design to reduce the blast radius of failures provided
- Data/network flow diagram provided.

### architecture_api_matrix Impacted API Matrix (H)

说明：Please provide a table enumerating all customer-facing APIs, an explanation of what each does, and the components and dependencies of your service that it touches. Include all APIs whether they are public or private from the customer's perspective.

期望回答（参考）：
- Matrix (or wiki link) has been provided in the notes section.

### architecture_failure_models Failure Models (H)

说明：Please construct a failure model listing soft and hard failure modes for each of your system's components and dependencies.

期望回答（参考）：
- Failure model documented.
- Soft failures known and documented.
- Soft failures conditions are actively monitored for occurrence.
- Known soft failure conditions have documented mitigations or playbooks
- Hard failures known and documented
- Known hard failure conditions are actively monitored for occurrence.
- Known hard failure conditions have documented mitigations or playbooks

### architecture_dependency_retry Dependency Retry/Backoff (M)

说明：What is the retry/back-off strategy for each of your service's dependencies?

期望回答（参考）：
- Safety for code calling out to dependencies within the context of a Sync API established
- Safety for code calling out to dependencies within the context of an async API call established
- Throttling techniques to defensively protect your service from customers established

### architecture_retry_timeouts Retries & Socket Timeouts (H)

说明：Have you intentionally set appropriate retry and socket timeout configuration for all SDK usage?

期望回答（参考）：
- Retry count and socket timeouts reviewed.

### architecture_rpo_rto Recovery Objectives (M)

说明：If your service was temporarily deactivated or shut down, what is your RTO for restarting your service?

期望回答（参考）：
- RTO has been defined
- RTO has been verified through a dry-run or game-day exercise

---

## release_quality — 02 - Release Quality（5 题）

### releases_deployment_rollback Automated Deployment Rollback (M)

说明：Do your customer impacting deployments automatically rollback incorrect deployments before they breach internal SLAs?

期望回答（参考）：
- Manual rollbacks can be initiated by operators
- Automatic rollbacks are initiated by monitoring systems.

### releases_validation Deployment Validation (L)

说明：Do your customer impacting deployments run on-host validation tests?

期望回答（参考）：
- On-host validations run

### releases_change_management Change Management (H)

说明：Do you have a mechanism to ensure all code changes (software, configuration, infrastructure, and operational tooling) to production systems are reviewed and approved by someone other than the code author?

期望回答（参考）：
- The risk presented here has been fully mitigated with no lingering questions or concerns that need to be followed up on.

### architecture_load_testing Load Testing (H)

说明：Have you performed multiple rounds of load testing to discover and address any unexpected performance bottlenecks and establish known breaking points?

期望回答（参考）：
- Tested to expected (1X) load / capacity requirement.
- Test to two times (2X) expected load / capacity requirement.
- Load test performed to break-point.

### releases_canary_errors Independent Canary Errors (L)

说明：Do you publish your canary synthetics errors to an independent metric? Subsequently, do you alarm on this metric?

期望回答（参考）：
- Canary alarms have been configured
- Canary Metrics have alarms tied to them that engage the operations team.

---

## event_management — 03 - Event Management（5 题）

### event_gameday Event preparedness through game days (H)

说明：Have you performed a gameday to verify that your service's monitoring and alarming function as expected and your on-call engineers are engaged and able to rapidly diagnose and remediate failures?

期望回答（参考）：
- Gameday conducted and lessons learnt documented/procedures updated.

### event_canary_alarms Independent Canary Alarms (L)

说明：Does your canary synthetic tests detect and alarm on shallow API test failures in under five minutes?

期望回答（参考）：
- Performance synthetics measure P50, P99 and P99.9s to track variability (including tail latency)
- Canary Metrics have alarms tied to them that engage the operations team.

### event_jvm_metrics JVM Metrics & Alarms

说明：Do you monitor (and alarm) on your JVM metrics? Do you monitor (and alarm on) your hosts for file system, inode, and file descriptor utilization? Do you monitor (and alarm on) your hosts for CPU and memory utilization?

期望回答（参考）：
- JVM metrics monitored and alarmed on as needed.
- Filesystem space capacity
- Filesystem inode capacity
- File descriptor utilization.
- CPU utilization
- Memory utilization

### event_kpis Operational KPIs (H)

说明：When do you look at your weekly and operator dashboards? What operational goals or KPIs (latency, throughput/TPS, etc.) have you identified for your service?

期望回答（参考）：
- Key metrics reviewed in Ops meeting at cadence (weekly/bi-weekly).
- KPIs are known and documented in the notes section.

### event_resilience_recoveries Withstand failures & fast recoveries (M)

说明：What resilience measures implemented when dependencies are impaired? What procedures exist for faster recoveries?

期望回答（参考）：
- Have the ability to weight workload out of an AZ within 15 minutes.
- Workload can withstand loss of AZ without customer impact

---


*检查项合计：16 题*
