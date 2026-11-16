# ModelArts AI 开发 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：ModelArts AI 开发（机器学习平台）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（4 题）

### PERF1 Are you aware of how data quality affects model performance in federated learning?

说明：Ensure balanced data distribution across nodes to prevent skewed training and improve model accuracy.

期望回答（参考）：
- Anomaly detection in Huawei Cloud DLI Data Quality
- Automates the creation of data quality rules
- Evaluate and enhance data quality in workflow
- Integration of data quality assessments directly into ETL job
- Implementing Custom Data Quality Rules with DQDL in Huawei Cloud DLI
- Setting up alerts, deployments, and scheduling

### PERF2 Do you optimize resource allocation for efficient training and inference?

说明：Chose the right compute resource for model training and inference

期望回答（参考）：
- Choose instances based on model complexity and dataset size for training
- Select instances that meet resource utilization and performance needs for inference
- Consider Auto scaling in your model inference

### PERF3 What aggregation methods ensure consistent learning across nodes?

说明：Use methods like FedAvg for convergence and variance reduction.

期望回答（参考）：
- Use FedAvg to compute a weighted average of client model updates before
- Use FedBN to reduce variance in local model updates, leading to more stable training.
- Use FedProx to add a proximal term that regularizes local training, preventing drastic deviations.
- Use adaptive optimization techniques such as Adam or SGD with momentum at the server to improve global model stability.
- Use secure aggregation to protect local model updates before transmission to the server.

### PERF4 How to communicate efficiently during the federated training process?

说明：Use model compression techniques along with other optimisations to reduce the communication overhead in federated learning

期望回答（参考）：
- Use model compression techniques along with adaptive client sampling and asynchronous updates
- If finetuning large language models, use methods like parameter efficient finetuning (PEFT) to keep update size in limit

---

## OPS — Operational Excellence（2 题）

### OPS1 How do you collect and monitoring metric and log for your model training and inference?

说明：You can monitor your model training and inference with ModelArts AI and Cloud Watch native integration

期望回答（参考）：
- Metrics for monitoring ModelArts AI with LTS 日志服务
- Log groups and streams that ModelArts AI sends to LTS 日志服务 Logs

### OPS2 How do you implement MLOps in federated learning?

说明：One should consider all the steps in a Federated learning process for operations

期望回答（参考）：
- Flower Server starts and notifies the Client to start the process
- Flower Client can send notification to client team
- Deploy and monitor global model

---

## SEC — Security（2 题）

### SEC1 How will you design network infrastructure for multi-environment federated learning?

说明：Use Site to site VPN or Dedicated network connection for secure, scalable connectivity.

期望回答（参考）：
- Build a secure VPN connection between Huawei Cloud and Customer Network
- Build internal and cross-organization networks
- Build a high-performance network connection for Huawei Cloud and Customer Network
- Ensure TLS connections are enabled for Flower internal communications

### SEC2 How do security and privacy measures influence the reliability of federated learning systems?

说明：Implement robust security measures to protect data during transmission, and use privacy-preserving techniques like differential privacy.

期望回答（参考）：
- Use Partial Homomorphic Encryption (PHE) for faster operations or Fully Homomorphic Encryption (FHE) for complex computations.
- Consider Secure Multi-Party Computation (SMPC) in your federated learning process.
- Implement cryptographic techniques for secure model update aggregation.

---

## resource utilization — Efficiency Optimization（2 题）

### COST1 Have you considered ECS 弹性云服务器 Spot Instances for model training, and what are your concerns about interruptions?

说明：Utilize ECS 弹性云服务器 Spot Instances for training models to reduce resource utilization.

期望回答（参考）：
- Consider Spot instance for your Federated Learning Training job
- Handle your training job interruption with checkpoint

### COST2 Do you fully understand the charging model for ModelArts AI?

说明：ModelArts charging depends on instance type, training time, inference, storage, and services.

期望回答（参考）：
- Understand the ModelArts AI charging model
- Consider ModelArts Saving Plans for your model training and inference

---


*检查项合计：10 题*
