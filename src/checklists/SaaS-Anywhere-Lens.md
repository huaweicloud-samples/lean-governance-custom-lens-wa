# SaaS 多租户检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：SaaS 多租户检查单（SaaS 架构评估）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## operationalExcellence — Opeational Excellence（5 题）

### OPS1 How are the remote components managed?

说明：In a typical SaaS scenario, SaaS provider has the full control of the environment.  However, in SaaS Anywhere, the remote account is owned by other parties. We suggest the remote accounts should be dedicated to the SaaS workloads in order to have separate charging and governance rules for the SaaS provider solution. 

期望回答（参考）：
- Manage remote accounts through a separate and dedicated account management service e.g. Huawei Cloud Organizations.
- Dedicate remote accounts for the SaaS solution
- Define a clear service SLA of the remote components with different account conditions.
- None of these

### OPS2 How do your team and client's team detect and respond to incident in the remote account?

说明：Both SaaS provider and the remote account owner should collaborate and share the responsibility of the remote account.  SaaS provider should provide a clear RACI matrix on incident response and well communicate with the remote account owner. 

期望回答（参考）：
- Define a clear RACI matrix for cloud operations in remote accounts
- Establish agreements with SaaS consumer on engaging and getting support from the cloud service provider.
- Able to create a representative environment for issue replication
- Integrate cloud service provider support case management with preferred collaboration channels, e.g. email or instant messaging
- None of these

### OPS3 How do you monitor infrastructure and healthiness of the remote application or data plane in the remote accounts?

说明：It is important to have health status and observability data feeding back to control plane which is sited in SaaS provider controlled accounts, so that SaaS provider can respond in time if there is any health event in the remote account.

期望回答（参考）：
- Collect observability data from remote plane to a central control plane.
- Feed health events to the SaaS provider's control plane.
- Deploy a quota monitoring solution in remote accounts to notify SaaS providers when usage reaches defined thresholds.
- Set alternative operational contact in the remote accounts to loop in SaaS provider.
- None of these

### OPS4 How do you manage onboarding in consumer account?

说明：This can be challenging when onboarding a customer where application plane or data plane need to deploy remotely because the account ownership is not under SaaS provider control. The account may mix with other workloads which is not required by SaaS solution, which will impact the security, reliability and performance of the SaaS solution.

期望回答（参考）：
- Fully automate account validation procedure and onboarding
- Define a clear account and permission pre-requisite
- None of these

### OPS5 How do you perform daily operational activities in the remote account?

说明：Daily operational activities include solution upgrades, patching, receiving operational notification from the cloud service provider, raising support cases when needed.

期望回答（参考）：
- Able to access of remote accounts to create support cases and track their status
- Subscribe remote accounts to support tiers matching or exceeding the SaaS provider's required level.
- Agree maintenance windows with SaaS consumers to address the dependent services and SaaS solution maintenance schedules.
- None of these

---

## Security — Security（5 题）

### SEC1 How do you manage the security responsibility in the remote account?

说明：The SaaS provider and consumer should have a well defined security shared responsibility model aligned.  As the remote accounts are owned by the SaaS consumer in most of the cases, SaaS consumer should take care of the account level security , whereas SaaS provider should take care of the workload level security.There should be governance and control rules in place to govern the boundary of both SaaS provider and consumer to avoid unexpected change from either side.

期望回答（参考）：
- Define clear security responsibilities between SaaS providers and consumers.
- Configure security contacts in remote accounts to notify both SaaS providers and consumers of security communications.
- Configure governance and control rules in remote accounts
- None of the above

### SEC2 How do you secure the data in the remote accounts?

说明：The data in the remote accounts could be confidential data of SaaS consumer. SaaS provider should not be able to access those data. In this case, the data should be encrypted by a SaaS consumer managed key so that SaaS provider has no way to decrypt the data. Same for the data provided by SaaS provider.

期望回答（参考）：
- Encrypt SaaS consumer data using consumer-managed encryption keys from SaaS consumer
- Encrypt SaaS provider data using consumer-manager encryption keys from SaaS provider
- None of the above

### SEC3 How do you respond to and investigate security incidents in remote accounts?

说明：When there is a security incident in the remote accounts, both SaaS provider and consumer should collaborate to respond and investigate the incidents so that they can take appropriate action in the earliest time. The model should be aligned with both provider and consumer to ensure they have the required permissions and logs for investigation during the event.

期望回答（参考）：
- Grant SaaS providers permission to investigate security trail logs in consumer-owned remote accounts.
- Create copies of security trail logs for SaaS provider investigations when direct access is not permitted
- Implement automated detection mechanisms in remote accounts
- Implement automated remediation mechanisms in remote accounts
- None of the above

### SEC4 How do you secure cross-account communication and deployment between control and application / data planes?

说明：When an application deployment or upgrade is required, how do they ensure the deployment are triggered by authorized source? In addition, is the remote environment retriscted any untrusted access to avoid unathorized deployment is done?

期望回答（参考）：
- Allow deployments only from authorized source accounts
- Use private connection for secure cross-plane communications
- None of the above

### SEC5 How do your organization gain access to the remote accounts?

说明：Under SaaS Anywhere scenario, SaaS provider should be granted sufficient permission boundary to performa operational activities in remote accounts like deployment, health checking, troubleshooting. We suggest SaaS provider defines a clear permission boundary, so that remote account owner can delegate the identity management to SaaS provider with permission boundary.  

期望回答（参考）：
- Create sufficient permission boundary of the remote account to your organization to perform operational activities.
- Implement break glass access when performing critical activities in remote accounts.
- None of these

---

## Reliability — Realiability（2 题）

### REL1 How do you handle recovery of control plane without impacting application / data planes?

说明：a DR plan should be in place to align with RPO and RTO requirements in case of service outage event, also the SaaS provider should have a regular DR testing in the remote environment to make sure the DR plan works properly in the remote environment.

期望回答（参考）：
- Test cross-plane reconnection regularly
- Document recovery priorities
- NONE

### REL2 How do you ensure reliable communication between control and application / data planes?

说明：SaaS provider should have mechanism to test the reliability of the remote workloads. For example, adopting chaos engineering, having a well defined playbooks for the remote environments.

期望回答（参考）：
- Implement retry mechanism for cross-plane communications.
- Set up a secondary connection path
- NONE

---

## Performance — Performance Efficiency（2 题）

### PERF1 How do you select compute resources for the remote workload?

说明：The best scenario of the compute resources in the remote environment should be consistent with the well tested set of compute options. In case of some regions availabilty or compliance requirements which SaaS provider cannot use the same set of compute options in the remote environment, they should choose the options similar to the default set as many as possible. They should also test enough to benchmark the difference between the remote compute options and the default.

期望回答（参考）：
- Match compute options between SaaS provider local workloads and remote deployments
- Test performance of alternative compute options in SaaS provider-controlled test accounts.
- If similar compute options are selected, test the performance in a SaaS Provider controlled account.

### PERF2 How do you manage resource scaling in the remote accounts?

说明：It is important to scale in time if there is scaling need in the remote account. SaaS solution should have an effective scaling mechanism in the remote account. Besides using pure resource utilizations in remote account for scaling, the remote resources will also need to be scaled based on the control plane metrics in the SaaS provider account.

期望回答（参考）：
- Monitor resource limits or service quotas in the remote accounts

---

## efficiencyOptimization — Efficiency Optimization（3 题）

### COST1 How do you monitor the resource utilization and usage in the remote accounts?

说明：SaaS provider should have a mechanism to visualize the resource utilization of usage data in the remote accounts, so that they can identify any resource utilization optimisation opportunities. Budget and resource utilization abnomaly detection should also be configured in the remote accounts so that the stakeholders of the remote accounts are alerted and take appropriate actions.

期望回答（参考）：
- Configure budgets and alerts in remote accounts with notifications to preferred channels.
- Deploy a central dashboard in SaaS provider-controlled accounts to monitor resource utilization and usage across local and remote accounts.
- None of these

### COST2 How do you explore savings opporunities in the remote accounts?

说明：SaaS provider should review the remote workloads and explore any savings opportunities in the remote environments. If SaaS provider is only allowed to access the remote environments in critical events, the optimisations opportunities data and recommendations should be fed to the control plane for SaaS provider to have regular review. SaaS consumer and provider should align with the process of purchasing plans (e.g. SP / RI) given that the SaaS provider has limited access to the remote environment.

期望回答（参考）：
- Deploy right-sizing tools in remote accounts and stream data to SaaS provider-controlled accounts for optimization insights.
- Decide savings options strategy by remote account owner
- None of these

### COST3 How do you optimise the data transfer resource utilization between control plane and remote application plane?

说明：Data transfer resource utilization between local and remote planes can be significant.  Careful design and evaluate the data transfer across planes can help to control and manage the tenant resource utilization.  If the data transfer resource utilization is based on tenant consumption, SaaS provider should consider to correlate their service charging with the underlaying cross-plane data transfer resource utilization consumption.

期望回答（参考）：
- Optimise all data transferred across local and remote planes
- Document the usage of data transferred across local and remote planes
- Correlate SaaS service charging to the underlying resource utilization of data transfer across local and remote planes
- None of these

---

## sustainability — Sustainability（1 题）

### SUS1 How do you select the most sustainable Regions in your area?

说明：SaaS consumer may have their own requirements to host resources in a specific region where giving a higher carbon emission. We recommend SaaS provider to discuss with the SaaS consumer to minimise the resources hosting in higher carbon emission region, while hosting the resources in lower carbin emission region as many as possible. Also, SaaS provider should regularly review with the SaaS consumer the carbon footprint to identify improvement opportunities.

期望回答（参考）：
- Deploy resources in low-emission regions whenever possible.
- Review carbon footprint regularly with SaaS consumers to identify sustainability improvements.
- Deploy a central sustainability metrics dashboard in SaaS provider-controlled accounts.
- None of these

---


*检查项合计：18 题*
