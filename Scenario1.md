



### **Cloud Platform Scenarios (AWS/Azure/GCP)**
1. **Azure**: Your AKS cluster in TradeOps has nodes failing every 24 hours. Logs show kernel panics. How do you diagnose and resolve this while maintaining 99.99% uptime?  
2. **AWS**: MediLink's RDS Aurora cluster suddenly becomes unresponsive during peak hospital hours. How do you restore service within 5 minutes without data loss?  
3. **GCP**: Orion's GKE cluster is rejecting new pods due to "Insufficient CPU" despite having 40% cluster utilization. What's your troubleshooting sequence?  
4. **Multi-Cloud**: TradeOps needs to failover from Azure to AWS during a regional outage. Design the failover process and rollback strategy.  
5. **Cost**: You discover MediLink's AWS costs doubled overnight. How do you identify the cause and prevent recurrence?  
6. **Compliance**: An audit reveals TradeOps' Azure Key Vault lacks rotation policies. How do you implement rotation without breaking existing applications?  
7. **Migration**: During Orion's cloud migration, legacy systems can't connect to GCP's VPC. How do you establish connectivity with minimal rework?  
8. **Scaling**: TradeOps' Azure SQL DB hits 100% CPU during trading hours. How do you scale it instantly without code changes?  
9. **Security**: Suspicious traffic is detected from MediLink's AWS environment. How do you isolate and investigate while maintaining hospital operations?  
10. **Disaster Recovery**: GCP region hosting Orion's IoT platform fails. How do you restore operations in another region within 15 minutes?  

---

### **Kubernetes & Container Scenarios**
11. **AKS**: TradeOps' production pods are stuck in `CrashLoopBackOff` after a deployment. Your rollback fails. What's your immediate action plan?  
12. **EKS**: MediLink's EKS cluster has 50% nodes in `NotReady` state. How do you recover without disrupting patient record access?  
13. **GKE**: Orion's GKE workloads are experiencing 30-second latency spikes during IoT data ingestion. How do you identify the bottleneck?  
14. **Networking**: Microservices in TradeOps' AKS cluster can't communicate across namespaces. How do you diagnose and fix?  
15. **Storage**: A persistent volume claim in MediLink's EKS cluster fails to bind. Patient data is at risk. How do you recover?  
16. **Upgrades**: Your AKS cluster upgrade from 1.25 to 1.28 causes 20% of pods to fail. How do you proceed?  
17. **Resource Limits**: Orion's GKE pods are being OOM-killed despite having requested sufficient memory. What's your investigation path?  
18. **Security**: You discover a pod in TradeOps' AKS cluster is running as root. How do you remediate without downtime?  
19. **Multi-Tenancy**: How would you isolate a noisy neighbor in a shared EKS cluster affecting MediLink's pharmacy API?  
20. **Backup**: How do you perform a point-in-time recovery of a corrupted PostgreSQL database running in Kubernetes?  

---

### **IaC & Configuration Management Scenarios**
21. **Terraform**: Your Terraform apply for TradeOps fails halfway, leaving resources in an inconsistent state. How do you recover?  
22. **Ansible**: MediLink's Ansible playbook for server hardening fails on 30% of nodes. How do you identify and resolve the issue?  
23. **Drift**: CloudFormation-managed resources in Orion's AWS environment have configuration drift. How do you detect and remediate?  
24. **State Locking**: Your Terraform state file for TradeOps is corrupted. How do you recover infrastructure state?  
25. **Secrets**: Ansible Vault decryption fails during MediLink's deployment. Patient data configuration is at risk. How do you proceed?  
26. **Modularity**: You need to deploy identical infrastructure across 3 Azure regions for TradeOps. How do you structure your Terraform code?  
27. **Compliance**: How do you ensure all Terraform-deployed resources in MediLink meet HIPAA requirements?  
28. **Rollback**: An ARM template deployment breaks Azure App Service configurations. How do you roll back quickly?  
29. **Testing**: How do you validate that your Ansible playbooks for Orion's GKE nodes won't break during production deployment?  
30. **Multi-Env**: Your Terraform code works in dev but fails in prod for TradeOps. What are the likely causes and solutions?  

---

### **CI/CD & Automation Scenarios**
31. **Pipeline Failure**: TradeOps' Azure DevOps pipeline fails at the container scan stage. How do you unblock deployments?  
32. **Speed**: MediLink's Jenkins pipeline takes 90 minutes to run. How do you reduce it to 20 minutes?  
33. **Rollback**: A canary deployment in GitLab CI for Orion's IoT platform shows 40% error rates. How do you automate rollback?  
34. **Triggers**: Your Jenkins pipeline for MediLink isn't triggering on code commits. How do you diagnose?  
35. **Artifacts**: Docker images in TradeOps' pipeline are being overwritten. How do you implement versioning?  
36. **Security**: A vulnerability scan blocks MediLink's deployment. How do you handle this without delaying critical patient care updates?  
37. **Parallelization**: How do you optimize a monorepo pipeline in Azure DevOps for 20 microservices?  
38. **Self-Service**: Developers complain about slow environment provisioning. How do you enable self-service deployments?  
39. **Compliance**: How do you enforce that all deployments in MediLink pass HIPAA checks before production?  
40. **Infrastructure**: Your Terraform deployment in CI/CD keeps timing out. How do you make it more reliable?  

---

### **Monitoring & Observability Scenarios**
41. **Alert Fatigue**: TradeOps' team gets 200+ alerts/night. How do you reduce this to <10 critical alerts?  
42. **Black Hole**: Logs from MediLink's pharmacy API are missing in ELK. How do you restore logging?  
43. **Latency**: Orion's Grafana dashboard shows 5-second latency spikes in IoT data processing. How do you correlate with application metrics?  
44. **Capacity**: TradeOps' Azure Monitor shows 80% CPU at 3 AM daily. How do you investigate this pattern?  
45. **Distributed Tracing**: How would you implement tracing to find bottlenecks in MediLink's microservices architecture?  
46. **Cost**: Monitoring costs for Orion's GCP environment are 20% of infrastructure costs. How do you optimize?  
47. **Anomaly Detection**: How do you set up anomaly detection for TradeOps' financial transaction processing?  
48. **Log Corruption**: You discover corrupted logs in ELK for MediLink's patient records. How do you recover?  
49. **SLA Violation**: TradeOps' 99.99% uptime SLA was breached. How do you prove what happened?  
50. **Custom Metrics**: How do you track custom business metrics (e.g., claims processed/hour) in MediLink?  

---

### **Security & Compliance Scenarios**
51. **Breach**: You discover TradeOps' Azure Key Vault was accessed by an unauthorized identity. What's your incident response plan?  
52. **Compliance Gap**: MediLink fails a HIPAA audit due to unencrypted S3 buckets. How do you remediate without disrupting hospital operations?  
53. **Secrets Exposure**: A Terraform state file in Orion's GCP project was accidentally committed with secrets. How do you handle this?  
54. **Network Attack**: TradeOps' AKS cluster is under DDoS attack. How do you mitigate while maintaining trading operations?  
55. **Vulnerability**: A critical CVE is found in Kubernetes running MediLink's patient data. How do you patch with zero downtime?  
56. **Audit Trail**: How do you prove to auditors that TradeOps' financial data hasn't been accessed inappropriately?  
57. **Compliance Automation**: How do you automate HIPAA compliance checks for all AWS resources in MediLink?  
58. **Identity Crisis**: Developers can't access resources in Orion's GCP project after IAM changes. How do you restore access?  
59. **Encryption**: How do you rotate encryption keys for TradeOps' Cosmos DB without downtime?  
60. **Pen Test**: During a pen test, you find a way to escalate privileges in MediLink's AWS environment. How do you fix?  

---

### **Scripting & Automation Scenarios**
61. **Emergency Script**: TradeOps' trading platform is down. You need to restart 50 services across 20 VMs immediately. How do you automate this?  
62. **Data Parsing**: MediLink's patient records have formatting errors. How do you write a Python script to clean 1M+ records?  
63. **API Failure**: Orion's IoT data pipeline API is returning 500 errors. How do you script health checks and auto-recovery?  
64. **Backup Failure**: Your backup script for TradeOps' Azure SQL DB failed silently. How do you add validation?  
65. **Performance**: A Bash script for log rotation in MediLink is taking hours. How do you optimize it?  
66. **Parallel Processing**: How do you use Python to process 100K IoT events from Orion's Pub/Sub in parallel?  
67. **Error Handling**: Your PowerShell script for Azure VM backups fails intermittently. How do you add robust error handling?  
68. **Resource Cleanup**: How do you write a script to automatically clean up unused resources in TradeOps' Azure environment?  
69. **Configuration Drift**: How do you script detection of configuration drift across MediLink's AWS environment?  
70. **Automation Testing**: How do you unit test a Python script that interacts with AWS APIs?  

---

### **Linux/Windows Administration Scenarios**
71. **Disk Full**: TradeOps' Linux servers run out of disk space during trading hours. How do you free space without stopping services?  
72. **Performance**: MediLink's Windows Server is running at 100% CPU. How do you identify the culprit process?  
73. **Network Issue**: Orion's IoT devices can't connect to on-prem servers. How do you troubleshoot?  
74. **Patching Emergency**: A zero-day vulnerability is announced. How do you patch 100 Linux servers in 2 hours?  
75. **Service Failure**: A critical service in MediLink's RHEL environment won't start. How do you diagnose?  
76. **Filesystem Corruption**: You suspect filesystem corruption in TradeOps' Ubuntu server. How do you verify and repair?  
77. **Active Directory**: How do you integrate Orion's Linux servers with Windows AD for authentication?  
88. **Kernel Panic**: A production server in TradeOps kernel panics every 48 hours. How do you diagnose?  
89. **Backup Verification**: How do you automate verification that backups for MediLink's patient data are restorable?  
90. **Security Hardening**: How do you harden a Windows Server for MediLink's HIPAA requirements?  

---

### **Architecture & Design Scenarios**
91. **Microservices Disaster**: MediLink's patient record microservice is failing, affecting the entire hospital system. How do you design for resilience?  
92. **Hybrid Cloud**: TradeOps needs to connect Azure cloud with on-prem trading systems. Design the connectivity solution.  
93. **Serverless Decision**: When would you choose AWS Lambda over Kubernetes for Orion's IoT data processing?  
94. **Multi-Region**: Design an active-active architecture for TradeOps' financial platform across Azure and AWS.  
95. **Data Pipeline**: Design a real-time data pipeline for Orion's 500K IoT events/sec using GCP services.  
96. **Caching Strategy**: MediLink's pharmacy inventory system is slow. How do you design a caching layer?  
97. **API Gateway**: Design an API gateway strategy for TradeOps' microservices with rate limiting and authentication.  
98. **Cost Optimization**: How would you redesign MediLink's AWS architecture to reduce costs by 30%?  
99. **Event Sourcing**: Design an event-driven architecture for TradeOps' trading analytics platform.  
100. **Compliance by Design**: How do you build HIPAA compliance into MediLink's architecture from day one?  

---

### **Behavioral & Situational Scenarios**
101. **Conflict**: A senior developer insists on bypassing CI/CD pipelines for "emergency fixes." How do you handle this?  
102. **Outage Communication**: TradeOps has a 30-minute outage during peak trading. How do you communicate with stakeholders?  
103. **Technical Debt**: Your team wants to add features, but MediLink's infrastructure has significant tech debt. How do you prioritize?  
104. **Mentoring**: A junior DevOps engineer deploys a broken Terraform config to production. How do you handle it?  
105. **Stakeholder Pressure**: Executives demand a feature launch in 2 weeks, but security testing needs 3 weeks. What do you do?  
106. **Team Disagreement**: Your team disagrees on whether to use Jenkins or GitLab CI for Orion. How do you resolve?  
107. **Failure Ownership**: You made a mistake that caused a 2-hour outage in MediLink. How do you handle it?  
108. **Resource Constraints**: You need to implement monitoring for Orion with no budget. What's your approach?  
109. **Vendor Management**: A cloud provider is causing repeated outages for TradeOps. How do you manage the relationship?  
110. **Innovation**: How do you introduce new tools (e.g., service mesh) to a resistant team?  

---

### **Project Management Scenarios**
111. **Deadline Crisis**: TradeOps' project deadline is moved up by 2 weeks. How do you adjust the plan?  
112. **Scope Creep**: MediLink's stakeholders keep adding requirements mid-project. How do you manage this?  
113. **Resource Shortage**: Your DevOps engineer for Orion quits mid-project. How do you ensure continuity?  
114. **Remote Team**: Your team for TradeOps is distributed across 3 time zones. How do you ensure collaboration?  
115. **Budget Cut**: Orion's project budget is cut by 40%. How do you deliver critical features?  
116. **Technical Decision**: You need to choose between Kubernetes and ECS for MediLink. How do you decide?  
117. **Risk Management**: Identify top 3 risks for TradeOps' cloud migration and mitigation strategies.  
118. **Compliance Delay**: HIPAA certification is delayed for MediLink. How do you adjust the timeline?  
119. **Post-Mortem**: After an outage in Orion, how do you run an effective blameless post-mortem?  
120. **Success Metrics**: How do you measure success for DevOps initiatives in TradeOps?  

---

### **Troubleshooting Master Scenarios**
121. **Mysterious Failure**: TradeOps' trading platform works in dev but fails randomly in prod. How do you diagnose?  
122. **Intermittent Bug**: MediLink's patient records occasionally show duplicate entries. How do you trace the cause?  
123. **Performance Cliff**: Orion's IoT platform handles 100K events/sec fine but fails at 101K. What's your approach?  
124. **Memory Leak**: A Java app in TradeOps' AKS cluster crashes every 48 hours. How do you find the leak?  
125. **Network Puzzle**: Pods in MediLink's EKS cluster can't reach RDS, but EC2 instances can. How do you solve?  
126. **Dependency Hell**: An Ansible playbook upgrade breaks 10 other playbooks in Orion. How do you recover?  
127. **Configuration Ghost**: A setting in TradeOps' Azure App Service keeps reverting. How do you find the cause?  
128. **Time Bomb**: MediLink's system works fine until the last day of the month when it slows to a crawl. Why?  
129. **Resource Contention**: Orion's GKE nodes have high steal time. What does this indicate and how do you fix?  
130. **Silent Failure**: Backups for TradeOps are failing silently. How do you build detection?  

---

### **Advanced Leadership Scenarios**
131. **Team Restructure**: How would you reorganize a DevOps team for better efficiency in a multi-cloud environment?  
132. **Innovation Culture**: How do you foster experimentation while maintaining stability for TradeOps' financial systems?  
133. **Cross-Team Conflict**: Dev and Ops teams in MediLink are blaming each other for deployment failures. How do you mediate?  
134. **Skill Gap**: Your team lacks GCP expertise for Orion's migration. How do you upskill them quickly?  
135. **Tool Standardization**: How do you choose and standardize tools across TradeOps, MediLink, and Orion?  
136. **Metrics-Driven**: How do you implement DORA metrics to improve DevOps performance?  
137. **Crisis Leadership**: During a major outage, how do you lead the response team while keeping executives informed?  
138. **Succession Planning**: How do you ensure knowledge continuity for critical systems like TradeOps?  
139. **Vendor Evaluation**: How do you evaluate and select a new monitoring tool for all three projects?  
140. **Future-Proofing**: How do you design Orion's architecture to accommodate future IoT device growth?  

---

### **Wildcard & Ethical Scenarios**
141. **Unethical Request**: Management asks you to disable security checks to speed up TradeOps' deployment. What do you do?  
142. **Whistleblowing**: You discover a HIPAA violation in MediLink that management is ignoring. How do you handle?  
143. **Cost vs. Security**: Orion wants to disable encryption to save costs. How do you respond?  
144. **Public Failure**: Your mistake causes a public outage for TradeOps. How do you handle PR?  
145. **Competitor Offer**: You're offered a job by a competitor working on similar projects. How do you decide?  
146. **Open Source Dilemma**: Your team uses open-source tools with no support for critical systems. What's your recommendation?  
147. **Burnout**: Your team is exhausted from on-call duties for MediLink. How do you address this?  
148. **Technical Vision**: Where do you see DevOps in 5 years, and how should Orion prepare?  
149. **Legacy Challenge**: You inherit a fragile system in TradeOps with no documentation. How do you approach it?  
150. **Final Challenge**: Design a DevOps strategy for a Mars colony with intermittent Earth connectivity.  

