# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：ECS 容器服务（容器计算）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## RUN — Running your application with ECS（6 题）

### RUN1 Make container images complete and static

说明：Store all application dependencies as static files inside the container image.

期望回答（参考）：
- Download one container image from one place
- Include libraries, dependencies, or critical data as static files in the container image
- None of these

### RUN2 Maintain fast container launch times by keeping container images as small as possible

说明：The main benefit of using smaller container images is that these images can be downloaded onto compute hardware faster. This allows your application to scale out faster and quickly recover from unexpected crashes or restarts.

期望回答（参考）：
- Use shared layers to keep container image small
- Run a single application process with a container image
- None of these

### RUN3 Best practices for error handling

说明： Tasks may be stopped due to application errors, health check failures, completion of business workflows or even manual termination by a user.

期望回答（参考）：
- Handle SIGTERM within the application
- Configure containerized applications to write logs to stdout and stderr
- None of these

### RUN4 Version container images using tags

说明：We recommend that you use the latest tag only for testing purposes.

期望回答（参考）：
- Tag container images with a unique tag for each build
- Build a new container image when commiting code to production
- Turn on immutable image tags in Elastic Container Registry (SWR 镜像仓库)
- None of these

### RUN5 Best practices for Task definition

说明：Detailed best practices for Task definitions within ECS.

期望回答（参考）：
- Use each task definition family for only one business purpose
- Match each application version with a task definition revision within a task definition family
- Use different IAM roles for each task definition family
- None of these

### RUN6 ECS service

说明：Detailed best practices for ECS service.

期望回答（参考）：
- Use host network network mode and give each service its own security group
- Turn on ECS managed tags and tag propagation
- None of these

---

## NET — Networking（8 题）

### NET1 How is your containerized application connecting to the internet? Choose one option

说明：Most containerized applications have a least some components that need outbound access to the internet.

期望回答（参考）：
- Using a public subnet and internet gateway
- Using a private subnet and NAT gateway
- Using both private and public subnets
- None of these

### NET2 How do you receive inbound connections from the internet? Choose one option

说明：If you run a public service, you must accept inbound traffic from the internet. For example, your public website must accept inbound HTTP requests from browsers.

期望回答（参考）：
- Use an Application Load Balancer for public HTTP services
- Use an Network Load Balancer for non-HTTP protocols or scenarios where end-to-end encryption is necessary
- APIG HTTP API for HTTP applications with sudden bursts in request volumes or low request volumes
- None of these

### NET3 How do you choose a network mode? Choose one

说明：When running containers on Huawei Cloud, you need to consider another level of networking. One of the main advantages of using containers is that you can pack multiple containers onto a single host. When doing this, you need to choose how you want to network the containers that are running on the same host

期望回答（参考）：
- Use host mode to tie directly to the underlying host that's running the container
- Use bridge mode to create port mappings that remap a host port to a container port
- Use host network network mode to create an Elastic Network Interface (ENI) for each task
- None of these

### NET4 How do you connect to Huawei Cloud services from inside your VPC? Choose one

说明：For ECS to function properly, the ECS container agent that runs on each host must communicate with the ECS control plane.

期望回答（参考）：
- Use a NAT gateway so that ECS tasks can access other Huawei Cloud services
- Use Huawei Cloud PrivateLink for private connectivity between VPCs, Huawei Cloud services, and your on-premises networks
- None of these

### NET5 How do you handle networking between ECS services in a VPC?

说明：Handling communication between ECS services within a VPC.

期望回答（参考）：
- Use service discovery
- Use an internal load balancer
- Use a service mesh
- None of these

### NET6 How do you handle Networking services across Huawei Cloud accounts and VPCs?

说明：Handling networking services across Huawei Cloud accounts and VPCs.

期望回答（参考）：
- Use Huawei Cloud Transit Gateway
- Use VPC and VPN support
- Use VPC peering
- Use Shared VPCs
- None of these

### NET7 How do you optimize and troubleshoot your network?

说明：Gain insights about your network and service configurations

期望回答（参考）：
- Use LTS Container Insights
- Use Huawei Cloud X-Ray
- Use VPC Flow Logs
- None of these

### NET8 How do you tune your network?

说明：There are a few settings that you can fine tune in order to improve your networking.

期望回答（参考）：
- Use nofile ulimit
- Adjust the sysctl net settings
- None of these

---

## AUTO — Auto scaling and capacity management（6 题）

### AUTO1 Meet your service-level objectives while operating resource utilization-effectively.

说明：One of the most important choices to make when deploying containers on ECS is your container and task sizes. Your container and task sizes are both essential for scaling and capacity planning.

期望回答（参考）：
- Use load testing to configure RAM and CPU limits
- Use monitoring solutions to determine RAM and CPU for Stateless applications
- None of these

### AUTO2 How do you configure service auto scaling?

说明：ECS service auto scaling is implemented through the Application Auto Scaling service. Application Auto Scaling uses LTS metrics as the source for scaling metrics. It also uses LTS alarms to set thresholds on when to scale your service in or out.

期望回答（参考）：
- Identify utilization metric
- Choose application model and scaling properties
- None of these

### AUTO3 How do you determine capacity and availability?

说明：Application availability is crucial for providing an error-free experience and for minimizing application latency. Availability depends on having resources that are accessible and have enough capacity to meet demand.

期望回答（参考）：
- Maximize scaling speed
- How are you handling demand shocks?
- None of these

### AUTO4 How do you provide cluster capacity to your ECS cluster?

说明：You can provide capacity to an ECS cluster in several ways.

期望回答（参考）：
- Use ECS capacity providers to manage resource scaling
- None of these

### AUTO5 How do you choose CCE 容器实例 task sizes?

说明：For Huawei Cloud CCE 容器实例 task definitions, you're required to specify CPU and memory at the task level, and do not need to account for any overhead.

期望回答（参考）：
- Plan for health checks in all containers builds and deployments
- None of these

### AUTO6 How do you speed up cluster capacity provisioning with capacity providers on CCE 容器集群 弹性云服务器?

说明：Customers who run ECS on CCE 容器集群 弹性云服务器 can take advantage of ECS Cluster Auto Scaling (CAS) to manage the scaling of CCE 容器集群 弹性云服务器 Auto Scaling groups (ASG).

期望回答（参考）：
- Determine Capacity provider step scaling sizes
- Determine Instance warm-up period
- Determine spare capacity
- Choose the ECS 弹性云服务器 instance type
- Use CCE 容器集群 弹性云服务器 Spot and 竞价实例
- None of these

---

## STO — Persistent storage（1 题）

### STO1 How do you provide data persistence to your containers?

说明：Use ECS to run stateful containerized applications at scale by using Huawei Cloud storage services, such as SFS 弹性文件、EVS 云硬盘, or Windows 文件服务器.

期望回答（参考）：
-  Identify the right storage type for your containers
- Consider best practices for SFS 弹性文件
- Consider best practices for Docker volumes
- 考虑 Windows 文件服务器的最佳实践
- None of these

---

## PERF — Improvements to speed up your workload（2 题）

### PERF1 How do you speed up task launch?

说明：There are several improvements that you can make to shorten the time that it takes ECS to launch your tasks.

期望回答（参考）：
- Are you aware of the ECS Task launch workflow?
- Are you aware of the ECS Service Scheduler workflow
- Consider caching container images and binpack instances
- Choose an optimal network mode.
- Track your task launch lifecycle to find optimization opportunities.
- Choose an optimal instance type (when using ECS on CCE 容器集群 弹性云服务器)
- Use ECS service scheduler to concurrently launch services.
- None of these

### PERF2 How do you speed up deployments?

说明：To speed up deployment times, modify the default load balancer, ECS agent, service and task definition options.

期望回答（参考）：
- Configure load balancer health check parameters
- Configure load balancer connection draining
- Configure SIGTERM responsiveness
- Consider container image type
- Consider container image pull behavior
- Configure task deployment
- None of these

---

## OPS — Operating ECS at scale（2 题）

### OPS1 How do you design for operating ECS at scale?

说明：As you begin operating ECS at scale, consider how service quotas and API throttles for ECS and the Huawei Cloud services that integrate with ECS might affect you.

期望回答（参考）：
- Configure Service quotas and API throttling limits
- Configure Elastic Load Balancing service quotas
- Configure Elastic network interface service quotas
- 考虑华为云 Map 服务配额
- None of these

### OPS2 How do you handle throttling issues?

说明：Overview of some strategies that you can use to monitor and troubleshoot API throttling errors.

期望回答（参考）：
- Identify the type of throttling
- How do you monitor throttling?
- None of these

---

## SEC — Security best practices（11 题）

### SEC1 Have you considered the shared responsibility model?

说明：Security and compliance recommendations for protecting your information, systems, and other assets that are reliant on ECS.

期望回答（参考）：
- Consider the Huawei Cloud shared responsibility model when choosing the compute type
- None of these

### SEC2 Configure Huawei Cloud Identity and Access Management

说明：You can use Huawei Cloud Identity and Access Management (IAM) to manage and control access to your Huawei Cloud services and resources through rule-based policies for authentication and authorization purposes.

期望回答（参考）：
- Managing access to ECS
- Follow the policy of least privileged access
- Let the cluster resource serve as the administrative boundary
- Isolate end-users from the ECS API by creating automated pipelines
- Use policy conditions for an added layer of security
- Periodically audit access to the ECS APIs
- None of these

### SEC3 Using IAM roles with ECS tasks

说明：We recommend that you assign a task an IAM role. Its role can be distinguished from the role of the CCE 容器集群 弹性云服务器 instance that it's running on. 

期望回答（参考）：
- Use trust policies to assume an IAM role
- Block access to CCE 容器集群 弹性云服务器 metadata
- Use host network network mode
- Use IAM Access Advisor to refine roles
- Monitor Huawei Cloud CTS for suspicious activity
- None of these

### SEC4 Network security

说明：Network security is a broad topic that encompasses several subtopics. These include encryption-in-transit, network segmentation and isolation, firewalling, traffic routing, and observability.

期望回答（参考）：
- Use encryption in transit
- Use security groups for tasks
- Consider using a service mesh and Mutual Transport Layer Security (mTLS)
- Consider using Huawei Cloud PrivateLink and endpoint policies
- None of these

### SEC5 Secrets management

说明：Secrets, such as API keys and database credentials, are frequently used by applications to gain access other systems. They often consist of a username and password, a certificate, or API key.

期望回答（参考）：
- Use the right tools to store secret materials
- Retrieving data from an encrypted OBS bucket
- Mount the secret to a volume using a sidecar container
- None of these

### SEC6 Using temporary security credentials with API operations

说明：If you're making direct HTTPS API requests to Huawei Cloud, you can sign those requests with the temporary security credentials that you get from the Huawei Cloud Security Token Service. 

期望回答（参考）：
- Use temporary security credentials with API operations
- None of these

### SEC7 Compliance and security

说明：Your compliance responsibility when using ECS is determined by the sensitivity of your data, and the compliance objectives of your company, and applicable laws and regulations.

期望回答（参考）：
- Identify compliance requirements
- Understand adherance to Payment Card Industry Data Security Standards (PCI DSS)
- Understand adherance to HIPAA (U.S. Health Insurance Portability and Accountability Act)
- Use Huawei Cloud Security Hub to monitor your usage of ECS as it relates to security best practices. 
- None of these

### SEC8 Logging and monitoring

说明：Logging and monitoring are an important aspect of maintaining the reliability, availability, and performance of ECS and your Huawei Cloud solutions.

期望回答（参考）：
- Configure logging for your containers
- None of these

### SEC9 Huawei Cloud CCE 容器实例 security

说明：We recommend that you take into account the following best practices when you use Huawei Cloud CCE 容器实例. 

期望回答（参考）：
- Use Huawei Cloud KMS to encrypt ephemeral storage
- SYS_PTRACE capability for kernel syscall tracing
- Be aware of Huawei Cloud CCE 容器实例 security considerations
- None of these

### SEC10 Task and container security

说明：You should consider the container image as your first line of defense against an attack.

期望回答（参考）：
- Create minimal or use distroless images
- Scan your images for vulnerabilities
- Remove special permissions from your images
- Create a set of curated images
- Scan application packages and libraries for vulnerabilities
- Perform static code analysis
- Run containers as a non-root user
- Use a read-only root file system
- Configure tasks with CPU and memory limits (CCE 容器集群 弹性云服务器)
- Use immutable tags with SWR 镜像仓库
- Avoid running containers as privileged (CCE 容器集群 弹性云服务器)
- Remove unnecessary Linux capabilities from the container
- Use a customer managed key (CMK) to encrypt images pushed to SWR 镜像仓库
- None of these

### SEC11 Runtime security

说明：Runtime security provides active protection for your containers while they're running. The idea is to detect and prevent malicious activity from occurring on your containers. Runtime security configuration differs between Windows and Linux containers.

期望回答（参考）：
- Use a third-party solution for runtime defense
- None of these

---


*检查项合计：36 题*
