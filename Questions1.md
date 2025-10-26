



### **Cloud Platforms (AWS/Azure/GCP)**
1. **Azure**: Explain how you’d implement *zero-downtime deployments* for AKS using Azure DevOps.  
2. **AWS**: Design a HIPAA-compliant backup strategy for RDS with cross-region replication.  
3. **GCP**: How would you optimize GKE autopilot clusters for cost while handling 500K IoT telemetry events/sec?  
4. **Multi-Cloud**: Compare the tradeoffs between Azure Key Vault, AWS Secrets Manager, and GCP Secret Manager.  
5. **Scenario**: Your Azure SQL DB hits 99% CPU during peak trading hours. How do you diagnose and resolve this *without* downtime?  
6. **Architecture**: Design a multi-cloud disaster recovery plan for TradeOps (Azure) with failover to AWS.  
7. **Cost**: How would you implement reserved instances vs. spot instances in AWS for MediLink’s ECS clusters?  
8. **Security**: Explain VPC Service Controls (VPC-SC) in GCP and its role in Orion’s IoT data security.  
9. **Migration**: Outline steps to migrate on-prem VMs to GCP using Migrate for Compute Engine with *zero data loss*.  
10. **Compliance**: How do you ensure CMC’s financial regulations are met in Azure App Service deployments?  

---

### **Kubernetes & Containers**
11. **Deep Dive**: Explain Kubernetes *control plane components* and how you’d troubleshoot a stuck `Pending` pod.  
12. **AKS vs EKS**: Contrast networking models (CNI plugins) in AKS vs. EKS.  
13. **Scaling**: Design an HPA (Horizontal Pod Autoscaler) policy for a Spring Boot app with variable load.  
14. **Security**: How would you implement *pod security policies* in AKS to prevent privilege escalation?  
15. **Troubleshooting**: Your GKE cluster has nodes in `NotReady` state. Walk through your debugging steps.  
16. **Storage**: Compare Kubernetes `PersistentVolume` types for a database requiring 99.999% durability.  
17. **Multi-Tenancy**: How would you isolate tenant workloads in a shared EKS cluster?  
18. **Upgrades**: Outline a zero-downtime upgrade strategy for AKS from 1.25 to 1.28.  
19. **Networking**: Explain how Calico CNI enforces network policies in Kubernetes.  
20. **Disaster Recovery**: How would you back up/restore an entire EKS cluster across regions?  

---

### **Infrastructure as Code (IaC)**
21. **Terraform**: How do you manage *state locking* in a team environment using Terraform Cloud?  
22. **ARM vs. Bicep**: When would you choose Bicep over ARM templates for Azure infrastructure?  
23. **Modularity**: Design a reusable Terraform module for deploying a 3-tier web app (ALB + EC2 + RDS).  
24. **Drift Detection**: How would you detect and remediate configuration drift in CloudFormation-managed resources?  
25. **Testing**: Explain how you’d implement *unit tests* for Terraform code using Terratest.  
26. **Secrets**: How do you securely inject secrets into Terraform-managed resources?  
27. **Multi-Env**: Structure a Terraform workspace strategy for dev/staging/prod environments.  
28. **Error Handling**: How do you handle partial failures during Terraform `apply`?  
29. **Policy as Code**: Implement Sentinel policies in Terraform to enforce tagging compliance.  
30. **Migration**: Migrate existing CloudFormation stacks to Terraform *without service disruption*.  

---

### **CI/CD & Automation**
31. **Azure DevOps**: Design a multi-stage YAML pipeline for TradeOps with *canary deployments*.  
32. **Jenkins**: How would you optimize Jenkins pipeline parallelism for a monorepo with 20 microservices?  
33. **GitLab CI**: Explain how GitLab’s Auto DevOps compares to custom Azure DevOps pipelines.  
34. **Triggers**: Configure a Jenkins pipeline to trigger on *specific file changes* in a Git repository.  
35. **Artifacts**: How do you manage artifact versioning in Azure DevOps for Docker images?  
36. **Rollbacks**: Automate rollbacks in GitLab CI if a deployment fails smoke tests.  
37. **Security**: Scan Docker images for vulnerabilities in a CI pipeline using Trivy/Clair.  
38. **Compliance**: Enforce HIPAA checks in a Jenkins pipeline before deployment to AWS.  
39. **Speed**: Reduce pipeline execution time by 50% for a Terraform deployment step.  
40. **Self-Service**: Enable developers to deploy their own environments using CI/CD pipelines.  

---

### **Configuration Management (Ansible)**
41. **Playbooks**: Write an Ansible playbook to harden RHEL servers per CIS benchmarks.  
42. **Dynamic Inventory**: Configure Ansible dynamic inventory for AWS EC2 instances with tags.  
43. **Idempotency**: Explain how Ansible ensures idempotency in configuration management.  
44. **Vault**: Encrypt secrets in Ansible Vault and integrate with Azure Key Vault.  
45. **Rolling Updates**: Perform rolling updates for an application using Ansible’s `serial` keyword.  
46. **Error Handling**: Handle failures in Ansible playbooks using `block`/`rescue`/`always`.  
47. **Testing**: Implement Molecule for testing Ansible roles.  
48. **Windows**: Configure a Windows Server using Ansible WinRM modules.  
49. **Compliance**: Audit Ansible-managed nodes for HIPAA compliance.  
50. **Scaling**: Manage 1000+ nodes with Ansible Tower/AWX.  

---

### **Monitoring & Observability**
51. **Prometheus**: Design a Prometheus alerting rule for high memory usage in Kubernetes pods.  
52. **Grafana**: Create a Grafana dashboard showing AKS cluster resource utilization vs. cost.  
53. **ELK**: Explain how you’d use ELK Stack to correlate logs across microservices.  
54. **CloudWatch**: How would you set up CloudWatch Alarms for Lambda errors with SNS notifications?  
55. **Distributed Tracing**: Implement X-Ray tracing in AWS for a Spring Boot microservices architecture.  
56. **Metrics**: What key metrics would you monitor for a financial trading platform (TradeOps)?  
57. **Alert Fatigue**: Reduce false-positive alerts in Prometheus by 90%.  
58. **Log Aggregation**: Centralize logs from Azure App Services, AWS ECS, and GKE in ELK.  
59. **SLA Monitoring**: Track 99.99% uptime SLA for MediLink’s hospital system.  
60. **Cost Monitoring**: Visualize cloud spend vs. performance metrics in Grafana.  

---

### **Security & Compliance**
61. **IAM**: Design a least-privilege IAM policy for an AWS Lambda function accessing S3.  
62. **RBAC**: Configure Kubernetes RBAC for developers to access only their namespace in EKS.  
63. **Secrets**: Rotate secrets in Azure Key Vault automatically using Azure Automation.  
64. **Network Security**: Implement a zero-trust network for GKE using Service Mesh (Istio).  
65. **Compliance**: Prove HIPAA compliance for MediLink’s AWS infrastructure using AWS Config.  
66. **Encryption**: Encrypt data at rest and in transit for Cosmos DB in TradeOps.  
67. **Vulnerability Mgmt**: Scan container images in a CI pipeline and block non-compliant builds.  
68. **Audit Trails**: Enable CloudTrail logging for all AWS API calls and send to ELK.  
69. **Pen Testing**: Describe how you’d conduct a penetration test for Orion’s IoT platform.  
70. **Incident Response**: Create an incident response plan for a data breach in a financial app.  

---

### **Scripting & Automation**
71. **Python**: Write a Python script to auto-scale EC2 instances based on CPU metrics.  
72. **Bash**: Create a Bash script to clean up old Docker images on a Kubernetes node.  
73. **PowerShell**: Automate Azure VM backups using PowerShell and Azure Automation.  
74. **APIs**: Use AWS SDK (Boto3) to list all S3 buckets and their encryption status.  
75. **Error Handling**: Handle exceptions in a Python script that queries CloudWatch logs.  
76. **Scheduling**: Schedule a Python script to run daily using cron and AWS Lambda.  
77. **Data Parsing**: Parse JSON logs from ELK using Python and extract error patterns.  
78. **Parallelism**: Run Ansible playbooks in parallel using Python’s multiprocessing.  
79. **Infrastructure**: Automate DNS record creation in Route 53 using Terraform and Python.  
80. **Testing**: Unit test a Python script that interacts with Azure APIs.  

---

### **Linux/Windows Administration**
81. **Performance**: Diagnose high I/O wait on a Linux server running PostgreSQL.  
82. **Security**: Harden a Windows Server against ransomware attacks.  
83. **Networking**: Troubleshoot network latency between Azure VMs and on-prem servers.  
84. **Patching**: Automate OS patching for 100 RHEL servers using Ansible.  
85. **Filesystems**: Recover a corrupted ext4 filesystem in Linux.  
86. **Services**: Debug a failed systemd service on Ubuntu.  
87. **Active Directory**: Integrate Linux servers with Windows Active Directory.  
88. **Kernel Tuning**: Optimize Linux kernel parameters for a high-traffic web server.  
89. **Backups**: Implement a backup strategy for a mix of Linux and Windows servers.  
90. **Disaster Recovery**: Perform bare-metal recovery of a Linux server from backups.  

---

### **Architecture & Design**
91. **Microservices**: Design a microservices architecture for a hospital management system (MediLink).  
92. **Serverless**: When would you choose AWS Lambda over AKS for a workload?  
93. **Data**: Design a petabyte-scale data pipeline for TradeOps using Azure Synapse.  
94. **High Availability**: Ensure 99.99% uptime for a financial trading platform.  
95. **Hybrid Cloud**: Connect on-prem data centers to Azure using ExpressRoute and VPN.  
96. **Event-Driven**: Build an event-driven architecture for IoT data ingestion in GCP.  
97. **Caching**: Implement Redis caching for a Spring Boot app to reduce database load.  
98. **API Gateway**: Design an API gateway strategy for microservices using Kong/Apigee.  
99. **Multi-Region**: Deploy a global application with active-active replication.  
100. **Cost Optimization**: Reduce cloud costs by 30% for MediLink’s AWS environment.  

---

### **Behavioral & Scenario-Based**
101. **Conflict**: How would you handle a developer who bypasses CI/CD pipelines?  
102. **Failure**: Describe a production outage you caused and lessons learned.  
103. **Prioritization**: How do you prioritize tasks when dealing with multiple incidents?  
104. **Innovation**: Introduce a new DevOps tool to a resistant team.  
105. **Documentation**: How do you ensure documentation stays updated with infrastructure changes?  
106. **Mentoring**: Train a junior DevOps engineer on Kubernetes best practices.  
107. **Stakeholders**: Explain technical debt to non-technical executives.  
108. **Deadlines**: Deliver a project with an aggressive timeline.  
109. **Compliance**: Balance security requirements with developer productivity.  
110. **Incident**: Lead a post-mortem for a critical production failure.  

---

### **Project-Specific Deep Dives**
111. **TradeOps**: How did you achieve 99.99% uptime for a petabyte-scale Azure SQL DB?  
112. **MediLink**: Explain the HIPAA-compliant architecture for Aurora PostgreSQL.  
113. **Orion**: How did you handle 500K IoT events/sec in GCP?  
114. **CNP Assurances**: Describe the fraud detection system in your insurance claims platform.  
115. **Cost Savings**: How did you reduce infrastructure costs by 35% in Orion?  
116. **Blue-Green**: Implement blue-green deployments for TradeOps’ React frontend.  
117. **Auto-Scaling**: Configure auto-scaling for MediLink’s ECS clusters during peak hospital hours.  
118. **Compliance**: Prove financial regulatory compliance for TradeOps.  
119. **Migration**: Migrate Orion’s on-prem workloads to GCP with minimal downtime.  
120. **Monitoring**: Set up ELK Stack for CNP Assurances’ insurance claims platform.  

---

### **Advanced Troubleshooting**
121. **Kubernetes**: Pods are stuck in `CrashLoopBackOff`. How do you debug?  
122. **Networking**: Intermittent connection failures between microservices in AWS VPC.  
123. **Performance**: Latency spikes in a Spring Boot app deployed on AKS.  
124. **Memory**: Java app running out of memory in Kubernetes.  
125. **DNS**: DNS resolution failures in a hybrid cloud environment.  
126. **Storage**: Slow disk I/O in an AWS EBS volume.  
127. **CI/CD**: Pipeline fails intermittently during Terraform `apply`.  
128. **Secrets**: Secrets rotation fails in Azure Key Vault.  
129. **Logging**: Missing logs in ELK Stack.  
130. **Backups**: RDS snapshot restoration fails.  

---

### **DevOps Philosophy & Trends**
131. **GitOps**: Compare GitOps vs. traditional CI/CD.  
132. **Platform Engineering**: How would you build an internal developer platform?  
133. **FinOps**: Implement FinOps practices in your organization.  
134. **AIOps**: Use AI/ML for predictive scaling in Kubernetes.  
133. **Chaos Engineering**: Introduce chaos engineering to your team.  
134. **Shift Left**: How do you "shift left" security in DevOps?  
135. **SRE**: Implement SRE practices (SLOs/SLIs) for a critical service.  
136. **Multi-Cloud**: Debate multi-cloud vs. single-cloud strategies.  
137. **Serverless**: Is serverless the future of DevOps?  
138. **Edge Computing**: Deploy edge computing for IoT devices.  

---

### **Wildcard & Curveballs**
139. **Tool Critique**: What’s the most overrated DevOps tool?  
140. **Failure**: What DevOps practice do you think is fundamentally flawed?  
141. **Innovation**: What emerging technology will disrupt DevOps?  
142. **Ethics**: How do you handle unethical requests from management?  
143. **Career**: Where do you see DevOps in 10 years?  
144. **Hypothetical**: Design a DevOps strategy for a Mars colony.  
145. **Tool Comparison**: Why use Ansible over Puppet/Chef?  
146. **Cloud Lock-in**: How do you avoid cloud vendor lock-in?  
147. **Metrics**: What’s the most useless metric in DevOps?  
148. **Automation**: What should *never* be automated?  
149. **Documentation**: Is documentation dead in DevOps?  
150. **Final Question**: What question should we have asked but didn’t?  

