

### **Category 1: Compute & Containers (EC2, ECS, EKS, Lambda)**

1.  You are designing a high-performance computing (HPC) workload that requires low-latency, high-bandwidth networking between instances. Compare and contrast the use of EC2 Enhanced Networking with the Elastic Fabric Adapter (EFA). In which specific scenarios would EFA be the only viable option?
2.  An application running on EC2 instances in an Auto Scaling Group is experiencing a "throttling" error from a downstream API. The API is a third-party service with a strict rate limit. How would you architect a solution on AWS to handle this throttling gracefully, ensuring no requests are lost and the system remains responsive?
3.  Your company is migrating a large, monolithic .NET application to containers. You must choose between ECS and EKS. Detail the key decision points, including operational overhead, community support, Windows container support, Fargate integration, and long-term strategic flexibility.
4.  You need to deploy a stateful, multi-node database cluster (like Cassandra) on Kubernetes. Explain the challenges of running stateful workloads on EKS and how you would use features like StatefulSets, Persistent Volumes (EBS), and the Amazon EBS CSI Driver to meet the requirements.
5.  A Lambda function is experiencing cold starts that are impacting user experience in a synchronous API call. Beyond the general advice of "keep packages small," what are three distinct, advanced techniques you can use to mitigate cold starts, and what are the trade-offs of each (e.g., cost, complexity, concurrency limits)?
6.  Describe the process and security considerations of using AWS Lambda to access resources in a VPC. What is the purpose of the Elastic Network Interface (ENI) that Lambda creates, and how can you prevent ENI exhaustion in a high-concurrency scenario?
7.  Your ECS service on Fargate is failing to deploy. The task is stuck in a `PENDING` state. What are the top five things you would investigate, starting from the service definition down to the underlying VPC and security group configuration?
8.  You need to grant an EKS cluster the ability to manage other AWS resources (like S3 buckets or DynamoDB tables). Describe the most secure method for configuring this, detailing the roles of IAM OIDC providers, Kubernetes Service Accounts, and IAM Roles for Service Accounts (IRSA).
9.  When using EC2 Spot Instances for a batch processing job, you need to ensure that if an instance is terminated, the in-progress work is checkpointed and can be resumed. Design a robust architecture using an SQS queue, a fleet of Spot workers, and a durable storage mechanism (like S3 or DynamoDB) to achieve this.
10. A customer wants to run Windows containers on a serverless platform. Compare the options of using ECS Fargate with Windows containers versus using AWS Batch on Fargate. What are the key differences in scheduling, cost model, and operational characteristics?

---

### **Category 2: Storage (S3, EFS, FSx, EBS)**

11. You are designing a data lake for a financial institution that must be immutable for 7 years for compliance purposes. Design a solution using S3 that prevents object deletion or versioning suspension, even by the root user. Explain the roles of S3 Versioning, MFA Delete, and S3 Object Lock (Governance vs. Compliance mode).
12. An application running on hundreds of EC2 instances across multiple Availability Zones needs to share a common file system with high throughput and low latency. Compare EFS and FSx for Lustre. When would you choose one over the other, and how would you optimize performance for each?
13. You need to replicate an on-premises block storage array to AWS for disaster recovery. The on-premises application uses the iSCSI protocol. Which AWS service is purpose-built for this scenario, and how does its replication mechanism work compared to using EBS snapshots?
14. A media company generates terabytes of data daily into an S3 bucket. They need to run analytics on this data, but frequently accessed data is only from the last 30 days. Design a cost-optimized lifecycle policy that balances access cost, storage cost, and data retrieval latency. Justify your choice of storage classes (e.g., Standard, IA, Glacier Instant Retrieval, Glacier Deep Archive).
15. Your EBS volume is experiencing high I/O latency. You've already provisioned an `io2 Block Express` volume. What are the next steps you would take to diagnose and resolve the bottleneck, considering the instance's performance limits, network saturation, and the application's I/O patterns?
16. Explain the difference between S3 Object Lock's legal hold feature and its retention period. Provide a use case where you would use both simultaneously.
17. You have an S3 bucket with millions of objects and need to find all objects that contain a specific PII pattern (e.g., credit card numbers). How would you design a serverless, automated process to scan, identify, and flag these objects without moving the data out of S3?
18. A customer wants to mount an S3 bucket directly to an EC2 instance as a file system. What are the limitations and performance characteristics of doing this with a third-party tool (like s3fs) versus using a native AWS service like AWS Storage Gateway in the File Gateway mode?
19. Describe the process of creating an EBS volume from a snapshot that resides in a different AWS region. What are the performance and cost implications of this operation?
20. You are architecting a multi-region, active-active application that requires a shared, writable file system in both regions. Design a solution using AWS services to achieve this, explaining the replication strategy and potential consistency challenges.

---

### **Category 3: Networking (VPC, ELB, Route 53, CloudFront)**

21. You need to design a network architecture for a multi-tenant SaaS application where each customer's resources are logically isolated but share some central services. How would you use VPCs, subnets, Transit Gateway, and route tables to achieve this while minimizing operational overhead?
22. An Application Load Balancer (ALB) is returning 502 Bad Gateway errors intermittently. The target is an ECS Fargate service. What is a systematic troubleshooting process to identify the root cause, covering the ALB configuration, target group health checks, the application's health check endpoint, and the underlying container's logs?
23. Explain the concept of "connection draining" on a Classic Load Balancer and its equivalent, "deregistration delay," on a Network Load Balancer (NLB) and Application Load Balancer (ALB). In what scenario is a longer deregistration delay critical?
24. Your company has a global presence and needs to route users to the nearest healthy endpoint based on latency and health. You also need to support failover to a secondary data center in case of a disaster. Design a comprehensive solution using Route 53, detailing the use of latency-based routing, geolocation routing, and health checks.
25. You have a public-facing CloudFront distribution and you want to restrict access to content only to authenticated users of your application. Compare and contrast the use of Signed URLs/Cookies with Lambda@Edge for authorization. What are the security and performance implications of each?
26. You need to establish a secure, private connection between your on-premises data center and your AWS VPC. Compare AWS Direct Connect + VPN over DX versus AWS Site-to-Site VPN. What are the key factors that would influence your decision, including bandwidth, cost, latency, and reliability?
27. An application in a private subnet needs to access the internet for software updates but must not be reachable from the internet. How would you design this using a NAT Gateway versus a NAT instance? What are the key differences in terms of scalability, availability, and cost?
28. You are deploying a fleet of IoT devices that will connect to AWS IoT Core. These devices must be able to invoke a Lambda function. How can you use VPC Endpoints to ensure that the invocation path from IoT Core to Lambda never traverses the public internet?
29. Explain the difference between a security group and a network ACL (NACL). Provide a specific scenario where you would need to use both to enforce a particular security rule.
30. You are using AWS Global Accelerator to improve performance for a global application. How does it differ from a CloudFront distribution, and in what specific use cases (e.g., TCP-based gaming, non-HTTP workloads) would Global Accelerator be the superior choice?

---

### **Category 4: Databases (RDS, Aurora, DynamoDB, ElastiCache, Redshift)**

31. You are tasked with designing a database for a gaming leaderboard that must support millions of writes per second and have sub-10ms latency for reads. Compare and contrast the use of DynamoDB with Aurora Serverless v2. What are the key architectural and cost trade-offs?
32. An Amazon RDS for PostgreSQL instance is experiencing high CPU utilization and slow query performance. You have identified a few long-running queries. What are the advanced steps you would take to analyze and optimize these queries, including using `EXPLAIN ANALYZE`, `pg_stat_statements`, and Performance Insights?
33. You need to create a globally distributed, multi-master database for an e-commerce platform with strict consistency requirements. Design a solution using Amazon Aurora Global Database. How does it handle conflict resolution, and what is the Recovery Point Objective (RPO) and Recovery Time Objective (RTO) in the event of a regional failure?
34. Explain the concept of "eventual consistency" in Amazon DynamoDB. When designing a shopping cart application, how would you architect the data model and write/update logic to handle potential read-after-write inconsistencies?
35. You need to migrate a 100 TB on-premises Oracle database to AWS with minimal downtime. Describe the end-to-end process using AWS Database Migration Service (DMS) and AWS Schema Conversion Tool (SCT), including the steps for a full load and ongoing change data capture (CDC).
36. Your application uses ElastiCache for Redis to cache user session data. You are concerned about high availability and data loss. Design a cluster using Redis Cluster mode enabled. How does it provide high availability and partition tolerance?
37. You are running a large Redshift cluster and notice that query performance is degrading over time. What are the key maintenance and optimization tasks you should perform, including vacuuming, analyzing tables, and using WLM (Workload Management) to manage concurrency?
38. When would you choose to use Amazon RDS Proxy in front of your RDS Aurora or MySQL/PostgreSQL database? Explain how it helps to manage "serverless" or "bursty" workloads and improves failover times.
39. You need to implement a fine-grained access control policy for a DynamoDB table where a user can only access their own data items. Describe how to achieve this using IAM policies, condition keys (`dynamodb:LeadingKeys`), and the concept of "least privilege."
40. Your application requires a graph database to model complex relationships. How would you deploy and manage a graph database on AWS? Compare using a self-managed solution on EC2 versus using Amazon Neptune.

---

### **Category 5: Security & Identity & Compliance (IAM, KMS, Secrets Manager, GuardDuty)**

41. A developer needs temporary, elevated access to a production EC2 instance for debugging. What is the most secure way to grant this access without giving them permanent privileges, and how would you ensure the access is automatically revoked after a set time?
42. Explain the difference between an IAM policy attached to a user/role and a resource-based policy (like an S3 bucket policy). In a scenario where both exist, how does AWS evaluate the effective permissions?
43. You need to encrypt a sensitive file in S3 using a Customer-Managed Customer Master Key (CMK) in AWS KMS. You want to ensure that only a specific Lambda function in another account can decrypt this file. Detail the complete IAM and KMS key policy configuration required to achieve this.
44. Your organization has a compliance requirement to rotate all database credentials every 30 days. Design an automated, secure solution using AWS Secrets Manager and a Lambda function to rotate the credentials for an RDS database without requiring an application restart.
45. AWS GuardDuty has detected an "IAMUser/AnomalousBehavior" finding. What is your immediate incident response plan? What steps would you take to investigate the finding, contain the potential threat, and remediate the vulnerability?
46. Explain the principle of attribute-based access control (ABAC) in IAM. Provide a practical example of how ABAC can simplify permissions management for a large, dynamic workforce compared to traditional role-based access control (RBAC).
47. You need to ensure that all data leaving your VPC destined for a specific S3 bucket is inspected by a third-party security appliance. How would you architect this using VPC Endpoints, a security VPC, and routing?
48. Compare and contrast AWS Macie and Amazon GuardDuty. What specific types of security threats and data classification tasks is each service designed to address?
49. How would you use AWS Config Rules to enforce a security policy that prohibits the creation of public S3 buckets or the modification of security groups to allow inbound traffic from 0.0.0.0/0?
50. Your company needs to log all API calls made across all its AWS accounts and must ensure these logs are tamper-proof and highly available for auditing purposes. Design a comprehensive solution using AWS CloudTrail, S3, S3 Object Lock, and optionally Amazon Athena for querying.

---

### **Category 6: CI/CD, Automation & IaC (CodePipeline, CodeBuild, CloudFormation, Terraform)**

51. You need to create a CI/CD pipeline that deploys a CloudFormation stack across multiple AWS accounts (dev, staging, prod) from a central CodeCommit repository. Design the pipeline using CodePipeline and explain how you would handle cross-account roles and stack parameters for each environment.
52. A CloudFormation stack update is failing with a `UPDATE_ROLLBACK_FAILED` state. What are the potential causes, and what are the methods to continue the rollback or get out of this state without deleting the stack?
53. Compare and contrast using AWS CloudFormation Drift Detection with a third-party IaC tool like Terraform for detecting configuration changes made outside of IaC. What are the pros and cons of each approach?
54. You are using AWS CDK to define your infrastructure. How would you implement a feature flag that allows you to conditionally create or not create a resource (like an S3 bucket) based on a parameter passed in at synthesis time?
55. Your CodeBuild project is failing because it's running out of disk space during a `docker build` step. What are three different ways to resolve this issue, and what are the trade-offs of each?
56. Describe a blue/green deployment strategy for an application behind an ALB using AWS CodeDeploy. How does CodeDeploy use listener rules and target groups to shift traffic?
57. You need to pass a sensitive value (like a database password) to a CloudFormation stack without storing it in plain text in the template or in the parameters file. What is the most secure way to do this?
58. Explain the concept of a custom resource in CloudFormation. Provide a use case where a custom resource is necessary to integrate a non-AWS service or perform a custom action during stack creation/update/deletion.
59. How would you use AWS CodePipeline to orchestrate a canary release for a Lambda function, gradually shifting traffic from an old version to a new version and monitoring for errors before fully promoting it?
60. Your team is using Terraform to manage AWS resources. How would you implement state locking and remote state management to prevent state corruption in a team environment? What are the options on AWS for this?

---

### **Category 7: Monitoring, Logging & Observability (CloudWatch, X-Ray, OpenSearch)**

61. An application is experiencing intermittent performance degradation that is difficult to reproduce. How would you use AWS X-Ray in conjunction with CloudWatch and CloudWatch Logs to trace a request as it flows through multiple microservices and identify the bottleneck?
62. You need to create a CloudWatch alarm that notifies you when the error rate for a specific API endpoint on your ALB exceeds 5% for more than 5 minutes. Describe the exact metric, statistic, period, and alarm configuration you would use.
63. Your application generates a massive volume of logs (terabytes per day). Storing them in CloudWatch Logs is becoming prohibitively expensive. Design a more cost-effective solution for log ingestion, storage, and analysis using a combination of AWS services.
64. Explain the difference between CloudWatch Metrics and CloudWatch Logs Insights. Provide a scenario where you would use Logs Insights to derive a metric that is not available by default in CloudWatch.
65. You need to monitor the memory usage of a Lambda function, as it's not a default metric. How would you implement custom metrics to track memory usage, and what are the two primary ways to do this?
66. Your organization wants a centralized logging solution for all its EC2 instances across multiple accounts and regions. Design a scalable architecture using the CloudWatch agent, Kinesis Data Firehose, and Amazon OpenSearch Service.
67. How can you use CloudWatch Synthetics to proactively monitor the availability and performance of your critical web APIs and user journeys? What can it monitor that a simple health check endpoint cannot?
68. Describe how to create a CloudWatch Dashboard that visualizes the key performance indicators (KPIs) for a multi-tier application, including EC2 CPU, RDS connections, ALB latency, and Lambda error rates.
69. You are using Amazon OpenSearch Service and need to secure the cluster so that it's only accessible from within a VPC and by specific IAM users. How would you configure VPC access and fine-grained access control?
70. Explain the concept of "Contributor Insights" in CloudWatch Logs. How can it help you quickly identify unusual log patterns, such as a sudden increase in 404 errors from a specific IP address?

---

### **Category 8: Serverless & Event-Driven Architecture (SQS, SNS, EventBridge, Step Functions)**

71. You are designing an image processing pipeline. An image is uploaded to S3, which should trigger a thumbnail generation, a watermarking process, and a metadata extraction, all in parallel. Design this using a combination of S3 events, SNS, SQS, and Lambda. Why is this fan-out pattern beneficial?
72. Compare and contrast using Amazon SQS with a Lambda poller versus using an SQS FIFO queue as an event source for Lambda. When is the FIFO queue's ordering and deduplication capability critical?
73. You need to decouple a microservice architecture where a producer service sends events that need to be consumed by multiple, independent consumer services. Compare using Amazon SNS with Amazon EventBridge. What are the key advantages of EventBridge, especially in a multi-account setup?
74. Design a multi-step, long-running workflow using AWS Step Functions. The workflow includes a human approval step, a machine learning model invocation, and a transactional database update. How would you handle errors, retries, and compensation logic in this state machine?
75. An SQS standard queue is experiencing a growing number of messages in the "Messages in Flight" metric, and the consuming Lambda function is timing out. What are the potential causes, and how would you troubleshoot this?
76. You need to schedule a Lambda function to run every 5 minutes, but only on weekdays. What is the most efficient and cost-effective way to achieve this using AWS services?
77. Explain the concept of "dead-letter queues" (DLQs) in the context of SQS and EventBridge. How do they differ, and how would you use them to build a resilient event-driven system?
78. You have an EventBridge rule that is supposed to trigger a Lambda function, but the function is not being invoked. What is a systematic process to debug this, covering the rule, the event pattern, the target, and IAM permissions?
79. Design a serverless ETL (Extract, Transform, Load) process that ingests data from an external API into DynamoDB every hour. The process must handle API rate limits and potential failures. Use Step Functions to orchestrate the workflow.
80. Explain the difference between SNS message filtering and EventBridge content-based filtering. Provide a use case where one is clearly superior to the other.

---

### **Category 9: High Availability & Disaster Recovery**

81. Design a multi-region, active-passive disaster recovery (DR) strategy for a stateless web application and a MySQL database. Detail the components (Route 53, ELB, RDS), the replication mechanism, and the manual/automated failover process. What is the expected RTO and RPO?
82. Compare and contrast the "Pilot Light" and "Warm Standby" DR strategies. For a critical e-commerce platform, which would you choose and why, considering cost, complexity, and recovery time?
83. Your application uses an Auto Scaling Group of EC2 instances behind an ALB. How can you architect the system to automatically recover from an AZ failure without manual intervention?
84. You need to back up an EBS volume every hour and retain the snapshots for 30 days. Design an automated, cost-effective solution using AWS Data Lifecycle Manager (DLM). How would you also create a cross-region copy of the snapshots for DR?
85. Explain how Amazon Aurora Global Database provides a faster recovery than a traditional RDS cross-region read replica setup in a disaster recovery scenario.
86. A critical on-premises application needs to be failed over to AWS in an emergency. The application has a 10 TB database and relies on a 1 Gbps MPLS connection. Design a hybrid DR solution using AWS Storage Gateway and AWS Direct Connect.
87. What is the difference between a Multi-AZ deployment and a Read Replica for Amazon RDS? In what scenarios would you use one, the other, or both together?
88. How would you use AWS Elastic Disaster Recovery (DRS) to replicate a fleet of on-premises VMware VMs to AWS? Describe the process of a failover and failback.
89. Your application's data is stored in an S3 bucket. How can you design a cross-region replication strategy to ensure data durability and availability in the event of a regional outage? What are the consistency considerations?
90. You are designing a highly available DNS strategy. How can you use Route 53's health checks and failover routing to ensure that your users are automatically directed to a healthy endpoint, even if your primary data center goes down?

---

### **Category 10: Advanced & Hybrid Scenarios**

91. Your company needs to run latency-sensitive applications in a specific metropolitan area. Compare the use cases for AWS Local Zones versus AWS Wavelength. What type of application would be best suited for each?
92. Explain the concept of AWS Outposts. In what scenario would a company choose to deploy an Outpost versus using a Direct Connect connection to a parent region?
93. You need to build a data marketplace where different partners can securely upload data to your AWS account, and you can process it without exposing the data to other partners. Design a solution using AWS Lake Formation and IAM.
94. How would you use AWS Control Tower to govern a multi-account AWS environment? Describe the concepts of guardrails, landing zones, and account factories.
95. Your application requires a hardware security module (HSM) for cryptographic operations. How would you use AWS CloudHSM to meet this requirement, and how does it differ from using KMS?
96. Design a cost-optimization strategy for a large AWS environment. What tools and techniques would you use, including Cost Explorer, Budgets, Trusted Advisor, and architectural patterns like using Graviton processors or Spot Instances?
97. Explain the AWS Well-Architected Framework. What are the five pillars, and how would you use the WA Tool to review an existing workload?
98. You need to process streaming data from millions of IoT devices in near real-time. Design an architecture using AWS IoT Core, Kinesis Data Streams, and Lambda or Fargate for processing.
99. Your organization wants to implement a "GitOps" workflow for its Kubernetes deployments on EKS. Describe how you would use a tool like ArgoCD or Flux to achieve this, integrating with a Git repository and an EKS cluster.
100. You are tasked with building a "sandbox" environment for developers that provides them with isolated, temporary AWS resources. How would you automate the creation and scheduled deletion of these sandbox accounts or resources using AWS Control Tower, Service Catalog, or custom scripts?

---

