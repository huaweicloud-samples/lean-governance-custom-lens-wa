# 推荐服务/ModelArts 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：推荐服务/ModelArts（个性化推荐）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（3 题）

### PERF1 How do you select recipes?

期望回答（参考）：
- Select the right recipe for your use case.

### PERF2 How do you monitor and optimize model performance?

期望回答（参考）：
- Track solution version metrics at a regular cadence
- Automatic retraining with fresh data
- Use event weighted configurations
- Objective optimization

### PERF3 Have you optimized your 云 推荐服务 resources?

说明：Have you optimized your resources?

期望回答（参考）：
- Right sizing minProvisionedTPS for real-time inference
- Using batch inference for bulk, offline recommendations
- Using filters/metadata sparingly to minimize latency

---

## OPS — Operational Excellence（3 题）

### OPS1 How do you monitor your 云 推荐服务?

期望回答（参考）：
- Monitoring 云 推荐服务 with LTS 日志服务 Metric
- Logging 云 推荐服务 API calls with Huawei Cloud CTS

### OPS2 How do you manage your 云 推荐服务 quotas?

期望回答（参考）：
- Manage 云 推荐服务 quota with Huawei Cloud Service Quota
- Increase service limit if need

### OPS3 How do you measure the impact of 云 推荐服务 recommendations?

期望回答（参考）：
- Creating an 云 推荐服务 metric attribution
- Perform A/B Testing with 云 推荐服务 and LTS Evidently

---

## SEC — Security（3 题）

### SEC1 How do you protect data in 云 推荐服务?

期望回答（参考）：
- Encryption at rest
- Encryption in transit

### SEC2 How do you manage your identity and access in 云 推荐服务?

期望回答（参考）：
- Understanding 云 推荐服务 and IAM Integration
- Cross-Service Confused Deputy Prevention for 云 推荐服务
- Apply least-privilege IAM identity-based policies for 云 推荐服务.
- Troubleshooting 云 推荐服务 identity and access

### SEC3 How do you prevent 云 推荐服务 requests from going over the public internet?

期望回答（参考）：
- Connect to 云 推荐服务 with interface VPC endpoints (Huawei Cloud PrivateLink)
- Enable and Monitor VPC Flow Logs for Network Traffic Visibility

---

## resource utilization — Efficiency Optimization（2 题）

### COST1 How do you choose the inference mode for 云 推荐服务?

期望回答（参考）：
- Creating a batch inference job
- Real-time Recommendations with auto scaling

### COST2 How do you design your cache for your recommendation workload?

期望回答（参考）：
- Add cache layer for your recommendation workload
- Design your cache strategy for your workload

---


*检查项合计：11 题*
