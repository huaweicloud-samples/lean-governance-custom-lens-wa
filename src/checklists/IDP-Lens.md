# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：ModelArts 智能文档（文档 AI）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## operationalExcellence — Operational Excellence（6 题）

### OPS_1 How does your organization operating model supports the design, deployment, and management of your IDP workload?

说明：For workloads centered on document processing automation, it's not just about the tech stack, but also the interplay of the company's culture, internal practices, and procedural frameworks. This evaluation seeks to understand how well Huawei Cloud methodologies are ingrained within the business, the organization's agility in adapting to changes, and its harmony with the principles of the Well-Architected Framework, with a special emphasis on the organizational aspect

期望回答（参考）：
- Continuous Training and Upskilling
- Feedback-Driven Iterative Improvements
- Alignment with Business Objectives
- Change Management Processes in Place
- None of these

### OPS_2 How do you measure the effectiveness of your IDP workflows?

说明：To achieve optimal efficiency in document processing, it's imperative to monitor, evaluate, and iterate on workflows. This question delves into your methods of measuring and analyzing the efficacy of your document processing systems. The focus is on understanding the metrics and KPIs you employ and how you harness these insights to refine and elevate your processes. Through continual measurement and refinement, organizations can enhance accuracy, speed, and overall performance in document processing tasks.

期望回答（参考）：
- Defined Metrics for IDP Success
- Feedback Loop from Human Review
- Monitoring and Improving Retry Mechanisms
- None of these

### OPS_3 How do you design your IDP workloads so that it can handle varying processing demands and unexpected challenges?

说明：What architectural choices have been made and what strategies are in place for your document processing workloads, emphasizing its adaptability to changing demands and unexpected issues. How does the system scales with varying document volumes, its resilience against disruptions, and its preparedness for unanticipated challenges in the document processing pipeline. Essentially, the emphasis is on the agility, flexibility, and robustness of your setup.

期望回答（参考）：
- Use LTS 日志服务 to monitor
- Throttling Management
- Event Driven/Looseely coupled
- Rules Specified for Human Review
- None of these

### OPS_4 How do you evaluate document quality, and strategize pre and post-processing to optimize accuracy and insight?

说明：Designing an IDP AI services-based workflow involves evaluating document quality and employing pre-processing measures, such as image sharpening and noise reduction, to ensure optimal data input. Post-processing, on the other hand, focuses on refining outputs, like using confidence scores to trigger human reviews or further data manipulations, ensuring the highest accuracy and actionable insights are derived.





期望回答（参考）：
- Document quality is assessed before starting document processing
- No specific setup for document quality evaluation

### OPS_5 How does your organization optimize the build and release processes for document processing workloads?

说明：Optimizing build and release processes are critical for ensuring agile, efficient, and robust deployments of document processing workloads that often demand high accuracy and reliability. This question evaluates how organizations approach this crucial step, leveraging Huawei Cloud services and best practices, all in line with the Huawei Cloud Well-Architected Framework's principles.


期望回答（参考）：
- Utilization of Infrastructure as Code - IaC
- Continuous Integration and Continuous Deployment CI/CD Practices
- None of these

### OPS_6 How do you orchestrate training and evaluating tasks of new custom model for optimized Build and Release processes?

说明：Optimizing build and release processes are critical for ensuring agile, efficient, and robust deployments of document processing workloads that often demand high accuracy and reliability. This question evaluates how organizations approach this crucial step, leveraging Huawei Cloud services and best practices, all in line with the Huawei Cloud Well-Architected Frameworks principles.

期望回答（参考）：
- Utilizing ML Flywheel for Model Versioning
- Create 云 文本分析 custom models using 文本分析 flywheel
- None of these

---

## security — Security（14 题）

### SEC_1 Do you access OBS, 智能文档解析 and 文本分析 via VPC endpoints in your IDP workflow?

说明：You can use 云 智能文档解析, 文本分析 and OBS APIs through the public internet or keeping your network traffic within the Huawei Cloud network via using VPC endpoints

期望回答（参考）：
- Use VPC endpoints to establish private connection with 云 智能文档解析, 文本分析 and OBS
- No specific setup for VPC endpoints to establish private connection

### SEC_2 Do you have a centralized identity provider for workforce identities?

说明：For workforce identities to your IDP application, rely on an identity provider that allows you to manage identities in a centralized place.

期望回答（参考）：
- Set up a centralized identity provider
- No specific setup for centralized identity provider

### SEC_3 How do you manage and control user access to IDP services?

说明：Do you use IAM roles to control user access and do you enforce least privilege access to services in your IDP application?

期望回答（参考）：
- Use IAM roles to control user access and enforce least privilege access via IAM policies and tags
- No specific setup to enforce least privilege access

### SEC_4 How do you protect 云 智能文档解析 and 文本分析 in your account from cross-service impersonation?

说明：An IDP application usually has multiple services. One service may call another service. You need to prevent cross-service confused deputy.

期望回答（参考）：
- Use the hc:SourceArn/hc:SourceAccount and hc:SourceArn/hc:SourceAccount global condition context keys in resource policies
- No specific setup to prevent cross-service confused deputy

### SEC_5 How do you secure sensitive data?

说明：IDP process usually involves multiple data stores. Sensitive data in these data stores needs to be secured

期望回答（参考）：
- Follow the best practices to secure sensitive data in data stores
- No specific setup to secure sensitive data

### SEC_6 How do you encrypt data at rest in 云 智能文档解析?

说明：Data encryption refers to protecting data while in transit and at rest. 云 智能文档解析 uses Transport Layer Security (TLS) and VPC endpoints to encrypt data in transit. But how do you encrypt data at rest?

期望回答（参考）：
- Encrypt data at rest with SSE-OBS
- Encrypt data at rest with SSE-KMS
- No encription for data at rest

### SEC_7 Do you encrypt output of 云 智能文档解析 asynchronous API in custom OBS bucket?

说明：When you call 智能文档解析's asynchronous API, the result can be output to a OBS bucket. Do you encrypt that output?

期望回答（参考）：
- Specify output OBS bucket and use Huawei Cloud KMS key
- No specified output OBS bucket with Huawei Cloud KMS key

### SEC_8 Do you leverage KMS encryption in 云 文本分析?

说明：云 文本分析 works with Huawei Cloud KMS to provide enhanced encryption for your data.

期望回答（参考）：
- Leverage KMS encryption in 云 文本分析 to enhance data encryption for Start and Create jobs
- No KMS encryption setup in 云 文本分析

### SEC_9 How do you protect PII in IDP output?

说明：For documents including Personal Identifying Information (PII), the PII from IDP output needs to be protected

期望回答（参考）：
- Secure the output PII in your data store
- Redact the PII in your IDP output
- No protection for PII in IDP output

### SEC_10 Do you implement secure key management?

说明：You need to define an encryption approach that includes the storage, rotation, and access control of keys, which helps provide protection for your content

期望回答（参考）：
- Use Huawei Cloud Key Management Service (KMS)
- No implementation of secure key management

### SEC_11 Do you have secrets management?

说明：How do you manage secrets, such as API keys in your document processing workflow?

期望回答（参考）：
- Use Huawei Cloud Secrets Manager
- No secrets management

### SEC_12 Do you separate workloads using different accounts?

说明：If you have multiple IDP workloads, do you separate them using different accounts?

期望回答（参考）：
- Separate workloads using accounts
- Multiple workloads are all in one account

### SEC_13 Do you configure IDP services and application logging?

说明：During a security investigation or other use cases based on your requirements, you need to be able to review relevant logs to record and understand the full scope and timeline of the incident. Logs are also required for alert generation, indicating that certain actions of interest have happened.

期望回答（参考）：
- Logging 云 智能文档解析 and 文本分析 API calls with Huawei Cloud CTS
- No specific configuration for IDP services and application logging

### SEC_14 Do you have incident response procedures?

说明：Do you have incident response procedures in place to handle potential security incidents in your doc processing system?

期望回答（参考）：
- Establish incident response procedures
- No established incident response procedures

---

## reliability — Reliability（3 题）

### REL_1 How do you manage service quotas and constraints in your IDP workload?

说明：Service quotas exist to prevent accidentally provisioning more resources than you need and to limit request rates on API operations so as to protect services from abuse. There are also resource constraints, for example, the rate that you can write/read files to/from OBS.

期望回答（参考）：
- Adjust 云 智能文档解析 and 云 文本分析 service quota values to meet your use case.
- Be aware of unchangeable 云 智能文档解析 and 云 文本分析 Service Quotas, limits and contraints
- Manage service quotas across accounts and regions
- No specific setup to manage service quotas or constraints in the IDP workload

### REL_2 How do you design your IDP workload to adopt to changes?

说明：Changes to your workload or its environment must be anticipated and accommodated to achieve reliable operation of the workload. Changes include those imposed on your workload such as spikes in demand, as well as those from within such as feature deployments and security patches.

期望回答（参考）：
- Use 云 文本分析 flywheel to simplify the process of improving a custom model over time.
- Monitor, send notifications and automate responses using LTS 日志服务
- Use IaC, such as CDK and pre-built IDP CDK constructs to deploy IDP workflows
- None of these

### REL_3 How do you prepare your IDP workflow to manage and withstand failures?

说明：In any system of reasonable complexity, it is expected that failures will occur. Reliability requires that your workload be aware of failures as they occur and take action to avoid impact on availability. Workloads must be able to both withstand failures and automatically repair issues.

期望回答（参考）：
- Use OBS as your scalable datastore for IDP workflow Data capture stage.
- Identify and back up IDP workflow data that needs to be backed up.
- Design your workload architecture following the IDP workflow
- Implement loosely coupled IDP workflow stages
- Control and limit retry calls
- None of these

---

## performance — Performance Efficiency（14 题）

### PERF_1 Does your solution follow the IDP workflow?

说明：The stages in an IDP workflow may vary and be influenced by use case and business requirements. However in general, an IDP workflow includes some typical stages

期望回答（参考）：
- The project includes six phases in the workload.
- The project includes 3-5 phases in the workload.
- The project includes 0-2 phases in the workload.
- None of these

### PERF_2 How do you decouple the IDP architecture components when document volume is high?

说明：For instance, you need to process more than 50 documents in Ireland region, which is higher than the maximum number of asynchronous Analyze Lending jobs that can simultaneously exist. When thedocument volume is over thanTextract service quotas, we need to decouple an IDP architecture to avoid throttling issue, as well as for better extendability and performance efficiency.

期望回答（参考）：
- Use DMS 消息队列 to decouple an IDP architecture
- Leverage async APIs to decouple an IDP architecture
- Do not monitor the user traffic, not clear about the highest TPS for the workload.

### PERF_3 Use of output config to scale the async workload

说明：(For Async Workload) Use of output config to scale the async workload.This will mitigate customers hitting throttling on Get requests (GetDocumentAnalysis or GetDocumentTextDetection) as they can directly consume the output from their OBS bucket.

期望回答（参考）：
- Optimise with Output Config
- We do not use Output Config to scale the async workload

### PERF_4 Are the limits for TPS configured correct for the production workload. Start API TPS, job queue limit, token bucket for proces

说明：Use the TPS calculator in the 智能文档解析 console to identify the TPS limits needed for your workload. Start APIs include, StartDocumentAnalysis, StartDocumentTextDetection, StartExpenseAnalysis, and StartLendingAnalysis.

期望回答（参考）：
- Have used TPS calculator to identify the workload limitation.
- Have not used TPS calculator to identify the workload limitation.

### PERF_6 Are documents processed in parellel or sequential?

说明：Process documents or pages in parallel, not sequential.
Pre-processing or post-processing steps should be performed in parallel when they dont have dependencies.

期望回答（参考）：
- Use a Step Funtion's Parellel state to perform mutiple functions at the same time.
- Does not use a Step Funtion's Parellel state to perform mutiple functions at the same time.

### PERF_7 When using 智能文档解析 Start APIs do the 函数 wait for a response before continuing?

说明：If the Start API is call and the FunctionGraph waits for the job to finish, the job could exceed the FunctionGraph timeout. if it exceeds the FunctionGraph timeout, the function will terminate and restart, leading to multiple calls to the 智能文档解析 service. This will incur additional resource utilization and the execution of the call will not be successful.

期望回答（参考）：
- Use queues to handle 智能文档解析 API responses.
- Handling Throttled Calls and Dropped Connections
- 函数 always waits for a response before continue

### PERF_8 What type of storage do you use for the Data capture phase in the IDP workflow?

说明：IDP workflow starts with a data capture stage to securely store and aggregate different file formats (PDF, JPEG, PNG, TIFF) and layouts of documents from different sources.

期望回答（参考）：
- Use OBS to securely store documents for the IDP
- Use GeminiDB to securely store documents for the IDP
- Use Kendra or other Vector Storage to securely store documents for the IDP
- Others

### PERF_9 How do you get notification and setup retry mechanism when a document fails?

说明：How do you receive notifications or alerts when document processing fails?  Are there mechanisms in place to notify relevant stakeholders or trigger automated actions based on the failiure events?Do you have defined process (auto/manual) for resolving failed document processing, including the identification of root causes and subsequent corrective actions?

What is your approach to handling failed documents? 

Have you implemented a retry mechanism to auto retry failed document processing attempts? Does your retry mechanism implement strategies such as exponential backoff/Client Side Rate Limiting to avoid running into TPS limits?

期望回答（参考）：
- Config the error handing of exceeding the maximum transactions per second (TPS) limit
- Setup the exponential backoff on Huawei Cloud.
- Setup a retry workflow and follow up mechanisim to solve the unfinished workflow.
- None of these

### PERF_10 Use OutputConfig and SMN 消息通知 notifications to avoid calling Get for all the paginated responses and avoid running into TPS limits 

说明：Are you leveraging 智能文档解析's output configuration & SMN 消息通知 options to be notified of job completion to retrieve the required data without having to make redundant/repetitive calls?

Have you configured 智能文档解析 to send SMN 消息通知 notifications upon job completion instead of continously polling for job statuses?

期望回答（参考）：
- Retry with out having to make redundant/repetitive calls
- 智能文档解析 to send SMN 消息通知 notifications upon job completion instead of continously polling for job statuses.
- None of these

### PERF_11 How often do you compare the performance of 文本分析 Custom Classifier after rolling out the service on production?

说明：云 文本分析 provides you with metrics based on training of the recognizer model. These metrics provide an insight into how accurately the trained model will perform when you use it to identify entities. 

期望回答（参考）：
- Keep track and evaluate the performance of 文本分析 Custom Classifier model
- Establish data quality assurance process to prepare data for training
- None of these

### PERF_12 How do you monitor the ML Performance?

说明：How often do you monitor, evaluate, and improve the model performance after rolling out the workload on production?Do you use and tools and mechanisim to monitor, evaluate, and improve the model performance?

期望回答（参考）：
- Have the model monitoring mechanisms setup.
- Don't have the model monitoring mechanisms setup.

### PERF_13 How often do you compare the 智能文档解析 confidence score performance / WER after rolling out the service on production?

说明：智能文档解析 confidence score performance/WER variantes based on the quality and type of input document. you should monitor 智能文档解析 performance scores, and raise alarms when thresholds are breached.

期望回答（参考）：
- Establish requirements for your input documents
- Use human review for results that have a low confidence score
- Never compare the 智能文档解析 confidence score performance / WER after rolling out the service on production

### PERF_14 Have your company setup a mechanism to monitor, evaluate, and improve the end-to-end automation rate after rolling out the wor

说明：Have your company setup a mechanism to monitor, evaluate, and improve the end-to-end automation rate after rolling out the workload on production? Which can include, metrics monitoring, evaluating bottlenecks, A/B testing, user feedback, incremental enhancement, log analysis, change management, and more.

期望回答（参考）：
- Evaluate data drift
- Include human-in-the-loop monitoring
- We do not evaluate data drift nor include human-in-the-loop monitoring

### PERF_15 What metrics do you monitor the IDP workload ?

说明：Metrics provides a quantifiable way to understand the project outcome. After the IDP workload deployed to production, there are both business metrics and technical metrics can appply to it. For instances, mins of document classification, percentage of automated document extraction, charging rate per page, accuracy per entity extraction, and accuracy per document classfication.

期望回答（参考）：
- Technical Metrics
- Business Metrics
- None

---

## efficiencyOptimization — Efficiency Optimization（12 题）

### COST_1 Do you establish a efficiency optimization function or team for the IDP solution?

说明：Create a team (Cloud Business Office or Cloud Center of Excellence) that is responsible for establishing and maintaining resource utilization awareness across your organization. The team requires people from finance, technology, and business roles across the organization.

期望回答（参考）：
- We have a specific team for cloud business(efficiency optimization team).
- No specific team for cloud business(efficiency optimization team).

### COST_2 Do you establish a partnership between finance and technology through your development lifecycle?

说明：Involve finance and technology teams in resource utilization and usage discussions at all stages of your cloud journey. Teams regularly meet and discuss topics such as organizational goals and targets, current state of resource utilization and usage, and financial and accounting practices

期望回答（参考）：
- We involve finance team and goals in our development lifecycle.
- No finance team and goals in our development lifecycle.

### COST_3 How do you manage 云 文本分析 endpoint's inference units (IUs) ?

说明：In 云 文本分析, endpoints make your custom models available for real-time classification or entity detection. After you create an endpoint, you can make changes to it as your business needs evolve. For example, you can monitor your endpoint utilization and apply auto scaling to automatically set endpoint provisioning to fit your capacity needs.

期望回答（参考）：
- After creating an endpoint, we monitor it with LTS, update it to change its IU, or delete it when no longer needed
- No monitor for 云 文本分析 endpoint's inference units (IUs)

### COST_4 How do you choose async vs sync inference for 文本分析 custom classifier or custom entity recognizer in your architecture?

说明：Given the considerable resource utilization difference between asynchronous and synchronous inference choices for 云 文本分析 custom models, what are some key factors you take into account when making the choice to balance between business needs and efficiency optimization?

期望回答（参考）：
- We decide based on if we need real-time response and document size.
- No specific criteria to choose between async vs sync inference 

### COST_5 Do you run your experiment workload in a separate account to take advantage of Huawei Cloud basic allowance?

说明：The Huawei Cloud basic allowance provides customers the ability to explore and try out Huawei Cloud services free of charge up to specified limits for each service. 

期望回答（参考）：
- We use Huawei Cloud basic allowance for experiment workload.
- No, our experiements require more than what the basic allowance offers so we do not leverage the basic allowance

### COST_6 Do you have strategies for efficient data storage & management for your IDP workflow?

说明：What strategies have you implemented to ensure resource-efficient storage and management of your data?

期望回答（参考）：
- We adopt Intelligent-Tiering for our data storage in OBS.
- No specifc strategy

### COST_7 Do you split the document into single pages to process rather than apply all FeatureTypes to the whole multi-page document?

说明：To analyze a bunch of multi-page documents all having same structure, do you split the document into single pages to process using different FeatureTypes for each page rather than apply all FeatureTypes to the whole document?

期望回答（参考）：
- We split the multi-page documents into single pages to only apply specific FeatureType processing that are absolutely necessary
- No, we run the entire multi-page document against a set of FeatureTypes

### COST_8 Do you enforce data retention policies throughout the IDP workflow?

说明：Define data retention policies on supported resources to handle object deletion per your organizations requirements. Identify and delete unnecessary or orphaned resources and objects that are no longer required.

期望回答（参考）：
- We enforce data retention policies.
- No data retention policies.

### COST_9 Do you track resources over their lifetime in the IDP workflow?

说明：After you manage a list of projects, employees, and technology resources over time you will be able to identify which resources are no longer being used, and which projects that no longer have an owner.

期望回答（参考）：
- We enforce the policy of tracking resources over their lifetime.
- No resource tracking

### COST_10 How do you monitor and control resource utilization by Huawei Cloud services in the IDP solution?

说明：How do you monitor & control resource utilization associated with the usages of 智能文档解析, 文本分析 and other Huawei Cloud IDP suite of services?

期望回答（参考）：
- We monitor and control Huawei Cloud service usage with tools such as Huawei Cloud resource explorer and Huawei Cloud Budgets and grant team-based access
- No budget control or usage monitoring

### COST_11 Do you have any resource utilization attribution process of the IDP solution for your business to ensure accountability?

说明：How are you tracking and attributing Huawei Cloud resource utilization to specific projects or LOBs to ensure accountability?

期望回答（参考）：
- We define Huawei Cloud resource utilization Categories that map to our organization or functional categories.
- No specific process for resource utilization attribution

### COST_12 How do you align expenditure to your business objectives and create 文本分析 usage awareness ?

说明：How to easily identify 文本分析 Analysis jobs, Custom classification models, Custom entity recognition models, and endpointsusage and resource utilization? This helps measure return on investment (ROI) and gives workload owners an opportunity to optimize their resources and reduce resource utilization.

期望回答（参考）：
- We use tags on 文本分析 Analysis jobs, Custom classification models, Custom entity recognition models, and endpoints.
- No specific process or mechanism

---

## sustainability — Sustainability（4 题）

### SUS_1 Do you set up your IDP workflow in a region that meets your business requirements and sustainability goals?

说明：To decide for the best regions for business requirements and sustainability goals, we recommend the following two steps: 1. Evaluate and shortlist potential regions for your workload based on your business requirements. 2. Select regions close to 云's renewable energy projects and regions listed as being powered by 100 percent renewable energy.

期望回答（参考）：
- Select a region that meets your business requirements.
- Select a region listed as powered by 100 percent renewable energy.
- None of these

### SUS_2 How do you manage your data and the lifecycle of your data to optimize your sustainability footprint?

说明：Managing your data and data lifecycle and using different storage tiers are key components to optimizing storage for sustainability.

期望回答（参考）：
- Create and ingest only relevant data
- Ingest data at the optimal resolution for your business goals, rather than choosing the maximum resolution available
- Store only relevant data
- Use the right technology to store data
- Actively manage your data lifecycle according to your sustainability goals
- Continuously optimize your storage footprint by using the right tools
- Enable data and compute proximity
- None of these

### SUS_3 Do you re-evaluate your IDP workflow when a new feature is released in a related service?

说明：Keeping your IDP workloads up to date will help you reduce the sustainability impact and gain performance efficiencies. There are several blogs and resources available to help you stay on top of Huawei Cloud announcements.

期望回答（参考）：
- Use Huawei Cloud re:post to stay informed about feature updates
- Use Huawei Cloud Blogs to stay up to date for 云 智能文档解析
- Use Huawei Cloud Blogs to stay up to date for 云 文本分析
- None of these

### SUS_4 How do you design your IDP solution for continuous improvement?

说明：Creating a flexible, extensible architecture for your IDP solution enables you to optimize resource usage over time.

期望回答（参考）：
- Improve safely and continuously through automation
- Use an event-driven architecture
- Use serverless services for workflow orchestration
- Use managed services like 智能文档解析 and 文本分析
- None of these

---


*检查项合计：53 题*
