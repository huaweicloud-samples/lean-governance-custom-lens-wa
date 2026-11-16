# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：APIG + FunctionGraph（无服务器 API）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## APPDESIGN — Application Design（8 题）

### APPDESIGN1 How do you understand the service quota and limitation with APIG and Huawei Cloud FunctionGraph?

说明：Understanding how to work with Service Quotas, when to request increases, and architecting with quotas in mind.

期望回答（参考）：
- Understand APIG has different quota setting for API type per account and per region
- Understand APIG has burst capacity and limit
- Understand Huawei Cloud FunctionGraph has a default concurrency limit.
- Understand FunctionGraph has burst concurrency
- Understand Huawei Cloud FunctionGraph has limitation of payload size.
- Understand the timeout limitation is different between APIG and Huawei Cloud FunctionGraph

### APPDESIGN2 Understanding FunctionGraph scaling options

说明：FunctionGraph is engineered to provide managed scaling in a way that does not rely upon threading or any custom engineering in your code. As traffic increases, FunctionGraph increases the number of concurrent executions of your functions.

期望回答（参考）：
- On-demand scaling
- Provisioned Concurrency
- Reserved Concurrency

### APPDESIGN3 How do you understand the performance from difference runtime environment in Huawei Cloud FunctionGraph?

说明：Different runtimes have different performance profiles

期望回答（参考）：
- Understand your programming language characters in FunctionGraph environment.
- Use CodeGuru Profiler to visualize and optimize your code structure.
- Import correct Huawei Cloud SDK version in 函数 with your requirement

### APPDESIGN4 How do you understand the networking and VPC configuration with APIG and Huawei Cloud FunctionGraph?

说明：APIG and Huawei Cloud FunctionGraph deployed and run inside of VPCs owned by the FunctionGraph serviceas managed services. The managed VPCs are not visible to customers, the network are full managed, maintained and operated by Huawei Cloud. automatically, and monitoring is managed by the service.

期望回答（参考）：
- Understand the network environment and topology is managed by Huawei Cloud
- Understand the ENI mechanisam for FunctionGraph usage
- Understand the constraint for VPC integration

### APPDESIGN5 How do you understand the invocation model of Huawei Cloud FunctionGraph?

说明：函数 can be invoked in synchronously, asynchronously, and polling behavior, depending upon the trigger services.

期望回答（参考）：
- In synchronous FunctionGraph invocations, the caller waits for the function to complete execution and the function can return a value

- In asynchronous FunctionGraph operation, the caller places the event on an internal queue, which is then processed by the FunctionGraph funct

### APPDESIGN6 How do you understand the connection types of APIG?

说明：-

期望回答（参考）：
- Follow protocol format in communication.
- Websocket APIG can push message to client.
- Knowing the difference b/t REST APIs and HTTP APIs
- Understand that Edge-Optimized REST APIG

### APPDESIGN7 How do you control the traffic flow when interact with other services?

说明：If your APIG/函数 interact with other services downstream, its possible to overwhelm those services with data or connection requests.

期望回答（参考）：
- Understand the downstream service limit (eq. Max number of connection)
- Understand REST APIG Usage plan
- Understand HTTP APIG Throttling

### APPDESIGN8 How do you understand the service quota of Huawei Cloud FunctionGraph Invocation?

说明：Huawei Cloud FunctionGraph has different quota and limitation for invocation types.

期望回答（参考）：
- Understand the quota and limitation for synchronous invocation
- Understand the quota and limitation for asynchronous invocation
- Understand the quota and limitation per version or alias

---

## SEC — Security（7 题）

### SEC1 How do you protect your 函数 within execution environments?

说明：When your functions are invoked, the FunctionGraph runs your code inside an execution environment. FunctionGraph scrubs the memory before it is assigned to an execution environment. Execution environments are run on hardware virtualized virtual machines (MicroVMs) which are dedicated to a single Huawei Cloud account. Execution environments are never shared across functions and MicroVMs are never shared across Huawei Cloud accounts.

期望回答（参考）：
- Understand 函数 life cycle
- Understand FunctionGraph process invocation structure

### SEC2 How do you secure your data in Huawei Cloud FunctionGraph execution lifecycle?

说明：It is possible for data from one 函数 to be shared with another invocation of the same function. This may be intended, when used for caching common values or sharing libraries. However, if you have information only intended for a single invocation.

期望回答（参考）：
- Ensure that data is only used in a local variable scope.
- Ensure all the critical local data been clean out before resource release
- Ensure that any callbacks are complete before exiting.

### SEC3 How do you securely build your Huawei Cloud 函数?

说明：Developers should always take precautions against common risks such as misconfiguration, injection flaws, and handling user input.

期望回答（参考）：
- Review OWASP Top 10 Web Application Security Risks
- Review OWASP Serverless Top 10
- Use fo static code analysis tools

### SEC4 How do you manage the permission setting for your APIG and 函数?

说明：-

期望回答（参考）：
- Review security best practices -Applying the principles of least privilege
- Understand APIG permission model
- Understand FunctionGraph permission model

### SEC5 How do you secure your workloads with public endpoints?

说明：For workloads that are accessible publicly, Huawei Cloud provides a number of features and services that can help mitigate certain risks.

期望回答（参考）：
- Understand how APIG evaluating policy
- Understand how APIG controlling and manageing access
- Not using APIG's API Key to AuthN/AuthZ request

### SEC6 How do you encrypt your data and protect your secrets for Huawei Cloud 函数?

说明：-

期望回答（参考）：
- Separate the secrect from source code.
- Use encryption services for secret store
- No plaintext secrets in FunctionGraph environment variables. 

### SEC7 Governance controls with Huawei Cloud CTS

说明：For compliance and operational auditing of application usage, Huawei Cloud CTS logs activity related to your Huawei Cloud account usage

期望回答（参考）：
- Ensure the traceability for invocation
- Build up the incidence response procedure

---

## MNO — Monitoring and Observability（3 题）

### MONITOR1 How do we build the request telemetry with APIG and Huawei Cloud FunctionGraph?

说明：When building our service with APIG and Huawei Cloud FunctionGraph, we should setup tracing mechanism to understand the request telemetry between the managed services.

期望回答（参考）：
- Tracing requests with Huawei Cloud X-Ray

### MONITOR2 How do we monitor the code storage for Huawei Cloud 函数?

说明：The FunctionGraph stores your function code in an internal OBS bucket that’s private to your account. Each Huawei Cloud account is allocated 75 GB of storage in each Region. Code storage includes the total storage used by both 函数 and layers.

期望回答（参考）：
- Understand the Code Storage limitation is regional
- Using FunctionGraph Layer to store share libraries

### MONITOR3 Logging and metrics with LTS 日志服务

说明：To leverage LTS 日志服务 日志服务 for moniroting APIG and Huawei Cloud FunctionGraph, and setup metrics for observability.

期望回答（参考）：
- Do you know how LTS structure logs?
- Important metrics for APIG
- Important metrics for FunctionGraph
- Aware customized LTS Metrics
- Using Huawei Cloud Resource Groups to organize your workload

---

## CnP — Efficiency and Performance（3 题）

### CnP1 How do you understand the service quota and limitation with APIG and Huawei Cloud FunctionGraph?

说明：FunctionGraph execution environments

期望回答（参考）：
- Understand cold starts and latency
- Understand the execution environment lifecycle
- Understand invocation patterns

### CnP2 How do you optimize your memory and computing resource allocation for your Huawei Cloud 函数?

说明：Memory and computing power

期望回答（参考）：
- Understand the memory usage
- Profiling functions with Huawei Cloud FunctionGraph Power Tuning

### CnP3 How do you optimize your spending by reuse available resources?

说明：Optimize the static initialization part in a FunctionGraph Function

期望回答（参考）：
- Understand the static initialization and cold start
- Understand that the initilzation is only run once and static.
- Only import necessary libaries.
- Initiated DB connection pool outside the handler.

---


*检查项合计：21 题*
