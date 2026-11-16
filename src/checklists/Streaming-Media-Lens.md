# 通用流媒体检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：通用流媒体检查单（流媒体架构评估）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## SMOPS — Operational Excellence（6 题）

### SMOPS1 How do you prepare for large scale video delivery events?

期望回答（参考）：
- Ensure that your content delivery infrastructure can scale to expected demand
- Evaluate and adjust Huawei Cloud Service Quotas to match your workload s needs in advance
- Consider engaging Huawei Cloud Support programs to assist with large-scale events

### SMOPS2 How do you select the most suitable media services and solutions?

期望回答（参考）：
- Select media services based on scenarios (Live, VOD, Latency)

### SMOPS3 How do you create and deploy your media service pipeline?

期望回答（参考）：
- Automate media pipeline deployment ( CDK, Terraform,..etc)

### SMOPS4 How do you monitor the health of the media service pipeline?

期望回答（参考）：
- Service-specific metrics
- Centralized logging

### SMOPS5 How do you manage operational events for your media application?

期望回答（参考）：
- Remediation steps and notification when events happen

### SMOPS6 How are you evolving your media workload while minimizing the impact of change?

期望回答（参考）：
- Evolving media workload

---

## SMPERF — Performance Efficiency（6 题）

### SMPERF1 How do you optimize media delivery through media origination and processing?

期望回答（参考）：
- Select an appropriate origin technology for your workload

### SMPERF2 How do you approach media source contribution?

期望回答（参考）：
- Begin with the highest quality sources that you can reasonably acquire
- Use specialized media transport and acceleration protocols
- Use private network connectivity between your content provider and media ingest

### SMPERF3 How do you use caching to improve content delivery performance?

期望回答（参考）：
- Use a content delivery network and monitor your cache-hit-ratio
- Ensure that cache-control headers for your content are optimized
- Have a cache invalidation runbook
- Minimize negative (error) caching

### SMPERF4 How do you monitor client Quality of Experience and Quality of Service?

期望回答（参考）：
- Collect and analyze player-side metrics
- Recognize & respond to playback anomalies

### SMPERF5 What tradeoffs have you made in media processing to improve client experience and lower bandwidth resource utilization?

期望回答（参考）：
- Optimize the number of adaptive bitrate (ABR) renditions for your workload
- Select appropriate encoding settings for your content type and quality targets
- Trade higher content processing resource utilization for lower delivery resource utilization for popular content

### SMPERF6 What tradeoffs have you made to lower live glass-to-glass latency?

期望回答（参考）：
- Optimize encoding and origin settings for low latency
- Avoid any unnecessary processing steps

---

## SMSEC — Security（6 题）

### SMSEC1 How do you authorize access to content and content ingest?

期望回答（参考）：
- Use an identity provider to authenticate viewers and access policies to implement least privilege access to protected content
- Restrict content origin access to allow only authorized content distribution networks

### SMSEC2 How do you monitor access to your media distribution workload?

期望回答（参考）：
- Monitor for fraudulent access attempts

### SMSEC3 How do you monitor unauthorized re-distribution of your content?

期望回答（参考）：
- Implement content or sessions forensics

### SMSEC4 How do you protect content ingest endpoints?

期望回答（参考）：
- Encrypt content ingest traffic using TLS
- Use private connectivity when working with partners
- Encrypt content at rest when delivering via physical medium

### SMSEC5 How do you protect content origin from unauthorized access and malicious attacks?

期望回答（参考）：
- Use DDoS protection service to maintain content availability
- Restrict content origin access to only allow known entities
- Use a web application firewall to monitor and control content access
- Encrypt origin to client communication in transit using TLS

### SMSEC6 How do you protect content at-rest and in-transit to prevent unauthorized distribution?

期望回答（参考）：
- Collaborate with business and legal stakeholders to align on content protection requirements
- Select a content protection scheme that meets business objectives

---

## SMCOST — Efficiency Optimization（3 题）

### SMCOST1 What is your strategy for optimizing object storage and data transfer resource utilization?

期望回答（参考）：
- Analyze and define Object Storage access patterns
- Trace and limit data transfer between services, Availability Zones, Regions, and clients

### SMCOST2 What is your strategy for optimizing content processing resource utilization?

说明：Baseline resources and throughput for media processing tasks

期望回答（参考）：
- Baseline resources and throughput for media processing tasks
- Run media processing tasks in parallel

### SMCOST3 How do you minimize distribution resource utilization while maintaining visual quality?

期望回答（参考）：
- Use objective and subjective measurement techniques to benchmark and improve video compression efficiency

---

## SMREL — Reliablilty（3 题）

### SMREL1 How does your streaming infrastructure withstand failures in ingest, processing, origination, or delivery components? 

期望回答（参考）：
- Document all workload dependencies and expected viewer experience in the event of component failure
- Design live streaming ingest architecture to withstand source failure by ingesting redundant video signals that take diverse ne
- Design live streaming workflow to withstand individual processing and origination failures by implementing redundant video pipe

### SMREL2 How does your streaming media workload adapt to viewer demand?

期望回答（参考）：
- Use a CDN and plan capacity with your providers
- Design your origin service to automatically scale to meet viewer demand

### SMREL3 How does your streaming infrastructure respond to or heal from failures in origination or delivery components? 

期望回答（参考）：
- Design your streaming media workflow to automatically distribute traffic to redundant origins
- Monitor live streaming manifests for expected segment update patterns and to alert on staleness

---


*检查项合计：24 题*
