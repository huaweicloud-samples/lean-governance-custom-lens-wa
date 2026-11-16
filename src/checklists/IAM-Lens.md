# 通用检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：IAM 身份认证（身份与访问）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## CGNSEC — Security（11 题）

### CGNSEC1 How do you enforce strong authentication for your users?

说明：Strong authentication mechanisms protect user accounts from unauthorized access. Multi-factor authentication (MFA), passwordless authentication, and strong password policies are essential security controls.

期望回答（参考）：
- Enable MFA for all users or high-risk users
- Implement passwordless authentication options
- Configure strong password policies
- None of these

### CGNSEC2 How do you use threat protection to defend against attacks?

说明：IAM threat protection provides adaptive authentication, compromised credentials detection, IP address allowlists/denylists, and user activity log export to defend against sophisticated attacks.

期望回答（参考）：
- Enable threat protection features
- Configure adaptive authentication based on risk level
- Monitor and respond to security events
- None of these

### CGNSEC3 How do you secure Identity Pool IAM roles with least privilege?

说明：Identity Pools provide temporary Huawei Cloud credentials to access Huawei Cloud resources. Properly configured IAM roles with least privilege principles prevent unauthorized access to your Huawei Cloud resources.

期望回答（参考）：
- Apply least privilege to IAM roles
- Use role-based access control with user attributes
- Disable unauthenticated access if not required
- Restrict IAM role trust policies to your specific Identity Pool
- None of these

### CGNSEC4 How do you protect data at rest and in transit?

说明：IAM automatically encrypts user data at rest using Huawei Cloud-managed keys - no additional configuration is required. Your responsibility is to ensure data in transit is protected via TLS and that tokens are stored securely on client devices.

期望回答（参考）：
- Enforce TLS for all connections
- Protect tokens and credentials in transit and storage
- Use VPC interface endpoints to keep IAM traffic private
- None of these

### CGNSEC5 How do you manage token security and lifecycle?

说明：Proper token configuration, validation, and revocation mechanisms prevent unauthorized access and token abuse.

期望回答（参考）：
- Configure appropriate token expiration times
- Implement token validation in your application
- Implement token revocation mechanisms
- Use appropriate OAuth scopes
- None of these

### CGNSEC6 How do you secure federated identity provider integration?

说明：When integrating with external identity providers (SAML, OIDC, social), proper configuration prevents security vulnerabilities.

期望回答（参考）：
- Validate identity provider certificates and metadata
- Implement attribute mapping validation
- None of these

### CGNSEC7 How do you implement compliance and auditing requirements?

说明：IAM is compliant with SOC, PCI, HIPAA, and other regulatory frameworks (Huawei Cloud shared responsibility). Your responsibility is to maintain audit trails and implement user data rights (export, deletion) as required by regulations like GDPR.

期望回答（参考）：
- Enable CTS for API activity logging
- Implement user data export and deletion
- None of these

### CGNSEC8 How do you manage user groups and role-based access control?

说明：User groups enable fine-grained access control by mapping users to different IAM roles or application permissions.

期望回答（参考）：
- Use groups for role-based access control
- Use group claims in tokens for application-layer RBAC
- Implement group precedence for overlapping memberships
- None of these

### CGNSEC9 How do you protect sensitive user attributes?

说明：User attributes may contain PII or sensitive data. Proper configuration controls who can read and write these attributes.

期望回答（参考）：
- Configure attribute read/write permissions
- Minimize PII stored in IAM
- None of these

### CGNSEC10 How do you protect IAM endpoints from abuse?

说明：Public-facing IAM endpoints can be targets for abuse, DDoS, or credential stuffing attacks.

期望回答（参考）：
- Associate Huawei Cloud WAF web ACL with your user pool
- None of these

### CGNSEC11 How do you secure FunctionGraph triggers?

说明：FunctionGraph triggers extend IAM functionality but introduce potential security risks if not properly secured. If your workload does not use FunctionGraph triggers, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Apply least privilege to FunctionGraph execution roles
- Validate and sanitize trigger inputs
- Secure secrets and credentials in FunctionGraph
- None of these

---

## CGNREL — Reliability（8 题）

### CGNREL1 How do you design for multi-region resilience?

说明：IAM User Pools are regional resources. For applications requiring high availability across regions, you need a strategy to handle regional failures.

期望回答（参考）：
- Document multi-region failover strategy
- Implement user data export and backup
- Test failover procedures regularly
- None of these

### CGNREL2 How do you monitor service quotas, handle throttling, and design for limits?

说明：IAM has service quotas for API operations. Exceeding these quotas can cause throttling and impact application availability.

期望回答（参考）：
- Monitor service quotas and request increases proactively
- Implement exponential backoff and retry logic
- Optimize API call patterns and design for quota limits
- None of these

### CGNREL3 How do you ensure FunctionGraph trigger reliability and resilience?

说明：FunctionGraph triggers extend IAM functionality but can introduce failure points. Proper error handling, monitoring, idempotency, and concurrency management ensure triggers don't impact authentication flows. If your workload does not use FunctionGraph triggers, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Implement proper error handling in 函数
- Configure appropriate timeouts and retries
- Monitor FunctionGraph trigger performance and errors
- Implement idempotency in triggers
- Set appropriate FunctionGraph concurrency limits
- None of these

### CGNREL4 How do you design account recovery flows for reliability?

说明：Reliable account recovery mechanisms ensure users can regain access while maintaining security.

期望回答（参考）：
- Configure self-service account recovery with multiple channels
- Monitor and alert on recovery failures
- None of these

### CGNREL5 How do you handle dependency failures?

说明：IAM depends on external services like email/SMS providers and federated IdPs. Graceful handling of failures maintains availability.

期望回答（参考）：
- Implement fallback mechanisms for email/SMS
- Monitor external dependency health
- None of these

### CGNREL6 How do you implement graceful degradation?

说明：When IAM or dependencies experience issues, graceful degradation maintains partial functionality.

期望回答（参考）：
- Cache tokens and provide degraded functionality during outages
- Implement circuit breaker patterns
- None of these

### CGNREL7 How do you test reliability of authentication flows?

说明：Regular testing validates that authentication systems can handle failures and recover gracefully.

期望回答（参考）：
- Conduct chaos engineering experiments
- Perform load testing
- Test disaster recovery procedures
- None of these

### CGNREL8 How do you monitor IAM service health and performance?

说明：Comprehensive monitoring enables early detection of issues and supports troubleshooting.

期望回答（参考）：
- Monitor key LTS metrics
- Set up proactive alerting
- Implement end-to-end monitoring
- None of these

---

## CGNOPS — Operational Excellence（11 题）

### CGNOPS1 How do you manage IAM resources as Infrastructure as Code?

说明：Managing IAM resources as code enables version control, repeatability, and consistent deployments across environments.

期望回答（参考）：
- Use IaC to document and recreate IAM configurations
- Version control all IAM configurations
- Protect against accidental User Pool replacement
- None of these

### CGNOPS2 How do you monitor and log IAM events?

说明：Comprehensive monitoring and logging enable quick identification and resolution of issues, and provide audit trails for security and compliance.

期望回答（参考）：
- Enable LTS Logs for User Pool events
- Enable CTS for API activity logging
- Create LTS dashboards and alarms
- None of these

### CGNOPS3 How do you plan and execute user modernization?

说明：User modernization from existing identity systems to IAM requires careful planning to minimize disruption and ensure data integrity. If your workload uses a new user pool with no modernization needed, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Use modernize user FunctionGraph trigger for seamless modernization
- Perform bulk import for pre-modernization
- Test modernization process in non-production environment
- None of these

### CGNOPS4 How do you set up alerting and notifications?

说明：Proactive alerting enables quick response to operational issues and security events.

期望回答（参考）：
- Use 事件网格 EG for event-driven automation
- Implement escalation procedures
- None of these

### CGNOPS5 How do you manage FunctionGraph triggers operationally?

说明：Operational management of FunctionGraph triggers ensures they remain reliable and maintainable. If your workload does not use FunctionGraph triggers, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Use FunctionGraph aliases for trigger management
- Monitor FunctionGraph trigger performance
- Implement FunctionGraph trigger testing
- None of these

### CGNOPS6 How do you manage change and configuration drift?

说明：Preventing configuration drift ensures consistency and reduces operational issues.

期望回答（参考）：
- Detect configuration drift
- Prevent manual changes
- Document all changes
- None of these

### CGNOPS7 How do you maintain operational documentation?

说明：Comprehensive documentation enables effective operations and knowledge transfer.

期望回答（参考）：
- Maintain runbooks for common operations
- Document architecture and design decisions
- Keep documentation in version control
- None of these

### CGNOPS8 How do you implement testing strategies?

说明：Comprehensive testing validates functionality and prevents regressions.

期望回答（参考）：
- Implement unit and functional tests for authentication flows
- Perform integration testing
- Conduct load and performance testing
- None of these

### CGNOPS9 How do you manage multiple environments?

说明：Separate environments enable safe testing and gradual rollout of changes.

期望回答（参考）：
- Maintain separate User Pools per environment
- Ensure environment parity
- Implement environment promotion process
- None of these

### CGNOPS10 How do you handle IAM service updates?

说明：Huawei Cloud regularly updates IAM with new features and deprecations. Staying current ensures security and access to new capabilities.

期望回答（参考）：
- Monitor Huawei Cloud announcements
- Plan for feature adoption
- modernize from deprecated features
- None of these

### CGNOPS11 How do you perform incident response and post-mortems?

说明：Authentication incidents (credential stuffing, FunctionGraph trigger failures, misconfigured token TTLs) directly impact user access. Your team - not Huawei Cloud - is responsible for detecting, responding to, and learning from incidents in your IAM configuration and integration layer.

期望回答（参考）：
- Define incident response procedures
- Conduct blameless post-mortems
- Track and implement improvements
- None of these

---

## CGNPERF — Performance Efficiency（6 题）

### CGNPERF1 How do you optimize region selection for latency?

说明：Choosing the right Huawei Cloud region for your IAM User Pool minimizes authentication latency for your users.

期望回答（参考）：
- Deploy User Pools in regions closest to users
- Monitor authentication latency metrics
- None of these

### CGNPERF2 How do you manage token caching and lifecycle?

说明：Proper token management reduces authentication overhead and improves application performance while maintaining security.

期望回答（参考）：
- Configure appropriate token expiration times
- Implement client-side token caching
- Use refresh tokens efficiently
- Use APIG as a token caching proxy
- None of these

### CGNPERF3 How do you optimize FunctionGraph trigger performance?

说明：FunctionGraph triggers extend IAM functionality but can add latency. Optimizing trigger performance ensures responsive authentication flows. If your workload does not use FunctionGraph triggers, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Minimize FunctionGraph cold start impact
- Optimize 函数 code and dependencies
- Right-size FunctionGraph memory allocation
- None of these

### CGNPERF4 How do you design efficient custom authentication flows?

说明：Custom authentication flows add flexibility but can impact performance if not optimized.

期望回答（参考）：
- Minimize authentication challenge steps
- Optimize FunctionGraph trigger execution time
- None of these

### CGNPERF5 How do you optimize API usage and large-scale operations?

说明：Efficient API usage reduces latency, avoids throttling, and improves application responsiveness for both routine and bulk operations. If your workload does not use IAM API with Huawei Cloud SDK, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Use batch and bulk import operations
- Implement rate limiting with exponential backoff
- Use pagination efficiently
- None of these

### CGNPERF6 How do you monitor and benchmark authentication performance?

说明：Performance monitoring identifies bottlenecks and validates optimization efforts.

期望回答（参考）：
- Track end-to-end authentication latency
- Establish performance baselines
- None of these

---

## CGNCOST — Efficiency Optimization（6 题）

### CGNCOST1 How do you monitor and forecast IAM resource utilization?

说明：Understanding IAM's charging dimensions - MAUs, feature plans, M2M token requests, and dependent service usage - helps avoid charging surprises.

期望回答（参考）：
- Track MAU metrics and usage patterns
- Implement resource utilization allocation tags
- Monitor API quota utilization to anticipate additional capacity resource utilization
- Avoid activating inactive users unintentionally
- None of these

### CGNCOST2 How do you choose the right feature plan?

说明：IAM offers three charging tiers - Lite, Essentials, and Plus - each with different per-MAU resource utilization and capabilities. Choosing the appropriate plan per user pool directly impacts resource utilization.

期望回答（参考）：
- Evaluate feature plan requirements per user pool
- Separate user pools by security tier when resource-efficient
- Review feature plan periodically as requirements change
- None of these

### CGNCOST3 How do you optimize SMS and email delivery resource utilization?

说明：SMS and email messages for MFA, verification, and password recovery are billed through SMN 消息通知和消息邮件服务 respectively. These resource utilization can be significant for high-volume applications.

期望回答（参考）：
- Use 云 消息邮件服务 for email delivery
- Minimize SMS usage where possible
- Use custom sender FunctionGraph triggers for efficiency optimization
- None of these

### CGNCOST4 How do you optimize FunctionGraph trigger resource utilization?

说明：FunctionGraph trigger resource utilization are based on invocations and execution time. Optimization reduces resource utilization without sacrificing functionality. If your workload does not use FunctionGraph triggers, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Optimize FunctionGraph execution time
- Reduce unnecessary FunctionGraph invocations
- None of these

### CGNCOST5 How do you optimize M2M authorization resource utilization?

说明：Machine-to-machine (M2M) authorization using client credentials grants is billed based on token request volume. Optimizing token handling directly reduces resource utilization. If your workload does not use M2M authorization, mark this question as not applicable in the Well-Architected Tool.

期望回答（参考）：
- Cache M2M access tokens with APIG
- Configure appropriate token expiration for M2M clients
- Monitor M2M token request volume
- None of these

### CGNCOST6 How do you leverage basic allowance and understand charging dimensions?

说明：Understanding IAM's basic allowance limits and charging dimensions across User Pools and Identity Pools helps avoid unexpected resource utilization and optimize spending.

期望回答（参考）：
- Understand and leverage the basic allowance
- Account for SAML/OIDC federation charging differences
- Understand Identity Pool charging model
- None of these

---


*检查项合计：42 题*
