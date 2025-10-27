


### **AWS Deep Dive (MediLink & CNP Projects)**
1. Design a HIPAA-compliant backup strategy for RDS Aurora with cross-region replication and point-in-time recovery.  
2. Explain how you'd implement VPC endpoints for RDS/S3 in MediLink to ensure traffic never leaves AWS infrastructure.  
3. How would you configure IAM policies for least-privilege access to EKS while enabling developer self-service?  
4. Walk through implementing encryption-at-rest for DynamoDB using KMS with automatic key rotation.  
5. Design a multi-AZ ECS cluster architecture for MediLink that ensures zero data loss during AZ failures.  
6. How would you optimize CloudWatch Container Insights to reduce costs while maintaining critical monitoring for EKS?  
7. Explain how to implement S3 bucket policies that enforce HIPAA data residency requirements.  
8. Design a Lambda function that triggers SNS notifications when RDS Aurora CPU exceeds 90% for 5 minutes.  
9. How would you configure AWS Config rules to continuously audit for HIPAA compliance violations?  
10. Implement a canary deployment strategy for ECS using CodeDeploy and Application Load Balancers.  

---

### **Azure Deep Dive (TradeOps Project)**
11. Design an AKS network policy that prevents frontend pods from directly accessing SQL databases.  
12. Explain how to implement Azure AD Pod Identity for AKS workloads accessing Key Vault.  
13. How would you configure Azure SQL Database geo-replication with automatic failover for TradeOps?  
14. Design a cost-optimized AKS cluster using spot instances while maintaining 99.99% uptime.  
15. Explain how to implement Azure Policy to enforce tagging compliance across all resources.  
16. How would you configure Azure Monitor to detect anomalous trading patterns in real-time?  
17. Design a secure Key Vault access model for microservices with automatic certificate rotation.  
18. Explain how to implement Azure Private Link for all PaaS services in TradeOps.  
19. How would you configure Azure Backup for AKS persistent volumes with application-consistent snapshots?  
20. Design a blue-green deployment strategy in Azure DevOps for AKS with automated rollback.  

---

### **GCP Deep Dive (Orion Project)**
21. Design a GKE Autopilot cluster architecture for 500K IoT events/sec with auto-scaling.  
22. Explain how to implement VPC Service Controls to prevent data exfiltration from Orion's environment.  
23. How would you configure Cloud SQL for PostgreSQL with high availability and cross-region replication?  
24. Design a Pub/Sub topic architecture that handles 500K messages/sec with exactly-once delivery.  
25. Explain how to implement Customer-Managed Encryption Keys (CMEK) for Bigtable and Cloud SQL.  
26. How would you optimize GKE node pools using preemptible VMs while maintaining SLAs?  
27. Design a Cloud Build pipeline that builds Docker images and deploys to GKE with security scanning.  
28. Explain how to configure Cloud Monitoring dashboards for IoT telemetry with predictive alerting.  
29. How would you implement Cloud Identity-Aware Proxy for securing GKE dashboard access?  
30. Design a Bigtable schema for time-series IoT data that optimizes for write performance.  

---

### **Multi-Cloud & Hybrid Architecture**
31. Design a disaster recovery strategy where primary is Azure AKS and secondary is AWS EKS.  
32. Explain how to implement consistent network security across AWS VPC, Azure VNet, and GCP VPC.  
33. How would you design a centralized logging solution aggregating CloudWatch, Azure Monitor, and Cloud Logging?  
34. Design a cost optimization strategy that identifies and rightsizes resources across all three clouds.  
35. Explain how to implement federated identity management across AWS IAM, Azure AD, and GCP IAM.  
36. How would you design a data pipeline that ingests from AWS Kinesis, processes in Azure Functions, and stores in GCP BigQuery?  
37. Design a VPN topology that securely connects on-premises data centers to all three clouds.  
38. Explain how to implement consistent backup policies across AWS EBS, Azure Disk, and GCP Persistent Disk.  
39. How would you design a multi-cloud CI/CD pipeline using GitLab CI that deploys to EKS, AKS, and GKE?  
40. Design a monitoring solution that provides unified dashboards across AWS, Azure, and GCP metrics.  

---

### **Infrastructure as Code (IaC)**
41. Design a Terraform module structure for deploying a 3-tier app across multiple clouds.  
42. Explain how to implement state locking for Terraform in a team environment using S3 and DynamoDB.  
43. How would you design ARM templates for Azure resources that support environment-specific configurations?  
44. Explain how to use CloudFormation nested stacks for complex AWS deployments.  
45. How would you implement policy-as-code using Sentinel for Terraform to enforce compliance?  
46. Design a Terraform workspace strategy for managing dev/staging/prod environments.  
47. Explain how to perform blue-green deployments using Terraform and Kubernetes.  
48. How would you implement drift detection for CloudFormation-managed resources?  
49. Design a CI/CD pipeline for Terraform that includes automated testing and security scanning.  
50. Explain how to manage secrets in Terraform without storing them in state files.  

---

### **Kubernetes & Containers**
51. Design a Kubernetes network policy that prevents database access from unauthorized namespaces.  
52. Explain how to implement pod security policies in EKS to prevent privilege escalation.  
53. How would you design a Helm chart for a microservice that supports multiple environments?  
54. Explain how to implement Kubernetes admission controllers for security validation.  
55. How would you design a storage strategy for stateful applications in Kubernetes?  
56. Explain how to implement horizontal pod autoscaling based on custom metrics.  
57. How would you design a Kubernetes cluster upgrade strategy with zero downtime?  
58. Explain how to implement service mesh (Istio) for microservices communication.  
59. How would you design a backup strategy for etcd in a self-managed Kubernetes cluster?  
60. Explain how to implement multi-tenancy in a shared Kubernetes cluster.  

---

### **CI/CD & Automation**
61. Design a multi-stage Azure DevOps pipeline that includes infrastructure provisioning, app deployment, and testing.  
62. Explain how to implement GitOps workflows using ArgoCD and Kubernetes.  
63. How would you design a Jenkins pipeline that handles 100+ microservices with parallel builds?  
64. Explain how to implement canary analysis in CI/CD using Flagger and Istio.  
65. How would you design a self-service deployment portal for developers?  
66. Explain how to implement infrastructure testing in CI/CD using Terratest.  
67. How would you design a CI/CD pipeline that automatically rolls back failed deployments?  
68. Explain how to implement artifact promotion across environments.  
69. How would you design a pipeline that includes security scanning at every stage?  
70. Explain how to implement progressive delivery using feature flags.  

---

### **Security & Compliance**
71. Design a zero-trust network architecture for a multi-cloud environment.  
72. Explain how to implement automated compliance checking for HIPAA using AWS Config and Azure Policy.  
73. How would you design a secrets management strategy across multiple clouds?  
74. Explain how to implement network segmentation using VPCs, VNets, and VPCs.  
75. How would you design a data encryption strategy that covers all states (at rest, in transit, in use)?  
76. Explain how to implement automated vulnerability scanning for container images.  
77. How would you design an identity federation strategy across clouds and on-premises?  
78. Explain how to implement audit logging for all cloud resources.  
79. How would you design a security incident response plan for cloud environments?  
80. Explain how to implement compliance as code using Open Policy Agent.  

---

### **Monitoring & Observability**
81. Design a monitoring strategy that provides end-to-end visibility across microservices.  
82. Explain how to implement distributed tracing using Jaeger or OpenTelemetry.  
83. How would you design an alerting strategy that reduces false positives?  
84. Explain how to implement log aggregation and analysis using ELK or Splunk.  
85. How would you design a dashboard for monitoring business metrics (e.g., trades processed/min)?  
86. Explain how to implement synthetic monitoring for user experience.  
87. How would you design a capacity planning strategy based on historical metrics?  
88. Explain how to implement anomaly detection using machine learning.  
89. How would you design a monitoring solution for serverless applications?  
90. Explain how to implement SLI/SLO monitoring and reporting.  

---

### **Cost Optimization**
91. Design a cost optimization strategy that identifies and eliminates wasted resources.  
92. Explain how to implement reserved instance planning across multiple clouds.  
93. How would you design a cost allocation strategy showing costs by team/application?  
94. Explain how to implement auto-scaling policies that optimize for cost vs. performance.  
95. How would you design a spot instance strategy for stateless workloads?  
96. Explain how to implement storage lifecycle policies to reduce costs.  
97. How would you design a cost monitoring solution with budget alerts?  
98. Explain how to optimize data transfer costs across clouds and regions.  
99. How would you design a rightsizing strategy for compute resources?  
100. Explain how to implement cost optimization for serverless applications.  

---

### **Troubleshooting & Debugging**
101. Diagnose why pods in an EKS cluster are stuck in Pending state.  
102. Explain how to troubleshoot intermittent network latency between microservices.  
103. How would you diagnose why a Lambda function is timing out?  
104. Explain how to troubleshoot Azure SQL connection timeouts.  
105. How would you diagnose why a GKE cluster has high node memory usage?  
106. Explain how to troubleshoot Terraform apply failures.  
107. How would you diagnose why a Jenkins pipeline is hanging?  
108. Explain how to troubleshoot CloudWatch metric delivery delays.  
109. How would you diagnose why an Azure VM is unreachable?  
110. Explain how to troubleshoot Pub/Sub message delivery failures.  

---

### **Advanced Scenario-Based**
111. Design a solution to handle 1M concurrent users for a financial trading platform.  
112. Explain how to migrate petabytes of data from on-premises to cloud with minimal downtime.  
113. How would you design a system that processes 10M events/sec with sub-second latency?  
114. Explain how to implement a multi-region active-active architecture.  
115. How would you design a system that automatically scales from 0 to 10K instances in minutes?  
116. Explain how to implement a blockchain-based audit trail for compliance.  
117. How would you design a system that maintains consistency across multiple cloud regions?  
118. Explain how to implement a chaos engineering practice for cloud environments.  
119. How would you design a system that automatically heals itself when components fail?  
120. Explain how to implement a serverless architecture for a real-time bidding system.  

---

### **Leadership & Strategy**
121. How would you design a DevOps maturity model for an organization?  
122. Explain how to implement a FinOps practice to optimize cloud spending.  
123. How would you design a cloud governance framework?  
124. Explain how to implement a security-first DevOps culture.  
125. How would you design a disaster recovery strategy with RTO of minutes and RPO of seconds?  
126. Explain how to implement a cloud center of excellence.  
127. How would you design a strategy for adopting new cloud technologies?  
128. Explain how to implement a cloud migration strategy for legacy systems.  
129. How would you design a training program for upskilling teams in cloud technologies?  
130. Explain how to implement a cloud vendor management strategy.  

---

### **Wildcard Challenges**
131. Design a solution to run Kubernetes on edge devices with intermittent connectivity.  
132. Explain how to implement quantum-resistant encryption in cloud environments.  
133. How would you design a carbon-neutral cloud architecture?  
134. Explain how to implement confidential computing for sensitive workloads.  
135. How would you design a cloud architecture for a Mars colony?  
136. Explain how to implement AI-driven cloud optimization.  
137. How would you design a solution to prevent cloud vendor lock-in?  
138. Explain how to implement blockchain-based cloud resource management.  
139. How would you design a cloud architecture that meets both GDPR and CCPA requirements?  
140. Explain how to implement a self-healing cloud infrastructure using AI.  

---

### **Compliance Deep Dives**
141. Design a HIPAA-compliant architecture for telemedicine applications.  
142. Explain how to implement PCI DSS compliance for payment processing in cloud.  
143. How would you design a GDPR-compliant data residency solution?  
144. Explain how to implement SOC 2 Type II controls for cloud infrastructure.  
145. How would you design a FedRAMP-compliant architecture for government agencies?  
146. Explain how to implement ISO 27001 controls in cloud environments.  
147. How would you design a solution that meets financial regulations (SOX, Basel III)?  
148. Explain how to implement continuous compliance monitoring for cloud resources.  
149. How would you design a cloud architecture that passes a SOC 2 audit?  
150. Explain how to implement automated compliance reporting for auditors.  

---

