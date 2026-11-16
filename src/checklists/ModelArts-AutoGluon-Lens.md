# ModelArts AI 开发 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：ModelArts AI 开发（机器学习平台）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## PERF — Performance Efficiency（5 题）

### PERF1 Is the model robust across different demand patterns?

说明：Tests model consistency across different demand patterns

期望回答（参考）：
- Segment SKUs into demand type with DLI
- Evaluate metrics per segment with AutoGluon metrics
- Track high-value SKUs separately

### PERF2 Is AutoGluon ensemble worth the resource utilization?

说明：Evaluates ensemble accuracy gain versus training and inference resource utilization

期望回答（参考）：
- Compare single vs ensemble with leaderboard
- Measure training &amp; inference resource utilization with leaderboard
- Apply ensemble selectively

### PERF3 Can the model capture promotions and spikes?

说明：Assesses ability to model promotions and demand spikes

期望回答（参考）：
- Add promotion/event features
- Create lagged promotion features with DLI ETL
- Evaluate promotion-period error with StepFunction

### PERF4 Is forecast horizon aligned?

说明：Forecast horizon matches business decision timeframes

期望回答（参考）：
- Evaluate multiple horizons with prediction length
- Use horizon-specific features

### PERF5 Are long-tail SKUs under-modeled?

说明：Checks if low-volume SKUs are poorly predicted

期望回答（参考）：
- Evaluate low-volume SKUs
- Use group-level and mapping to SKU-level

---

## OPS — Operational Excellence（2 题）

### OPS1 How you collect and monitoring metric and log for your model training and inference?

说明：You can monitor your model training and inference with ModelArts AI and Cloud Watch native integration

期望回答（参考）：
- Metrics for monitoring ModelArts AI with LTS 日志服务
- Log groups and streams that ModelArts AI sends to LTS 日志服务 Logs

### OPS2 How do you design your MLOps process to support your model training and inference?

说明：Ensures automated retraining, data validation, performance tracking, and safe model promotion or rollback

期望回答（参考）：
- Build end-to-end pipeline with StepFunction
- Schedule retraining with 事件网格 EG
- Fallback to previous model with sagemaker deployment
- Validate data freshness and quality

---

## Security — SEC（5 题）

### SEC1 How do you protect sensitive demand forecasting data?

说明：Protects sales, inventory, charging, and forecast data from leakage

期望回答（参考）：
- Encrypt training data with Huawei Cloud KMS
- Encrypt forecast outputs in OBS

### SEC2 How do you control access to training data?

说明：Ensures only authorized users and jobs access training datasets

期望回答（参考）：
- Apply least privilege with Huawei Cloud IAM
- Restrict data by business unit with Lake Formation
- Separate development and production access with Huawei Cloud account

### SEC3 How do you protect forecast outputs?

说明：Prevents leakage of future demand, revenue, or inventory plans

期望回答（参考）：
- Restrict forecast visibility with Huawei Cloud IAM
- Control downstream access with OBS Bucket

### SEC4 How do you secure model artifacts?

说明：Protects trained forecasting models from unauthorized access or misuse

期望回答（参考）：
- Version model artifacts with OBS
- Restrict model access with ModelArts Model Registry

### SEC5 How do you support security audits?

说明：Makes data, model, and deployment actions traceable

期望回答（参考）：
- Track data versions with OBS version
- Track model evidence with OBS
- Log access and changes with CTS

---

## resource utilization — Efficiency Optimization（3 题）

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

### COST3 Is your model inference in right resource and deployment option?

说明：Checks if inference uses appropriate resources and deployment for performance, scalability, and resource utilization

期望回答（参考）：
- Model deployment options in ModelArts AI
- Use ModelArts Inference Recommender for instance selection

---


*检查项合计：15 题*
