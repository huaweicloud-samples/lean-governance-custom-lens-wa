# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：架构评估护照（整体架构评估）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## overview — Overview（11 题）

### overview01 Have you completed a Well Architected Framework Review for all workloads to be deployed to the new region?

说明：Carrying technical debt to new regions increases risk. It is recommended to ensure all workloads are well-architected before deployment to new regions.

期望回答（参考）：
- Yes.
- No.

### overview02 Have all risks identified in the Well Architected Framework Review been mitigated?

说明：You can use the Huawei Cloud Well-Architected Tool to identify and remediate risks in your workloads that map to the five pillars of the Huawei Cloud Well-Architected Framework: operational excellence, security, reliability, performance efficiency, and efficiency optimization.

期望回答（参考）：
- Yes.
- No.

### overview03 Is the architecture modernized?

说明：Modernizing your applications helps you reduce resource utilization, gain efficiencies, and make the most of your existing investments. It involves a multi-dimensional approach to adopt and use new technology, to deliver portfolio, application, and infrastructure value faster, and to position your organization to scale at an optimal charging rate. After you optimize your applications, you must operate in that new, modernized model without disruption to simplify your business operations, architecture, and overall engineering practices.

期望回答（参考）：
- Yes.
- No.

### overview04 Are you using Infrastructure as Code (IaC) to deploy workloads?

说明：Manual infrastructure management is time consuming and prone to errors, especially when you manage applications at scale. Infrastructure as code lets you define your infrastructure desired state without including all the steps to get to that state. It automates infrastructure management so developers can focus on building and improving applications instead of managing environments. Organizations use infrastructure as code to control resource utilization, reduce risks, and respond with speed to new business opportunities.

期望回答（参考）：
- Yes.
- No.

### overview05 Is service and feature parity for target regions known?

说明：Huawei Cloud offers 33 regions to choose from. There may be some variation in services and features from region to region. It is important to understand any disparity before expanding to new regions.

期望回答（参考）：
- Yes.
- No.

### overview06 Is service and feature parity for target regions acceptable?

说明：There may be cases where variations in service and feature availability will require changes in workload architecture. Make sure you understand and plan for any changes.

期望回答（参考）：
- Yes.
- No.

### overview07 Is service capacity for target regions known?

说明：Huawei Cloud offers 33 regions to choose from. There may be some variation in capacity from region to region. It is important to understand any large increases in capacity before expansing to new regions.

期望回答（参考）：
- Yes.
- No.

### overview08 Is service capacity for target regions acceptable?

说明：There may be cases where capacity constraints will require changes in workload architecture or service quota incrases. Make sure you understand and plan for any changes.

期望回答（参考）：
- Yes.
- No.

### overview09 Is the cold start resource utilization for target regions known?

说明：charging for Huawei Cloud services can vary from region to region. It's important to understand resource utilization differences and the resource utilization to initially deploy system architecture.

期望回答（参考）：
- Yes.
- No.

### overview10 Is the cold start resource utilization for target regions acceptable?

说明：There may be cases where cold start resource utilization will require changes in workload architecture or service charging. Make sure you understand and plan for any changes.

期望回答（参考）：
- Yes.
- No.

### overview11 Are the data residency, data sovereignty, and general compliance considerations known?

说明：There may be cases where the data residency, data sovereignty, and general compliance considerations may impact your workload's architecture in a new Huawei Cloud region.

期望回答（参考）：
- Yes.
- No.

---


*检查项合计：11 题*
