

---

### **Category 1: Kernel & Performance Internals (Questions 1-15)**

1.  Explain the complete lifecycle of a system call from user space to the kernel and back. What are the key mechanisms involved?
2.  Compare and contrast cgroupv1 with cgroupv2. Design a resource-limiting strategy for a multi-tenant web server using cgroupv2, explaining how you would control CPU, memory, and I/O.
3.  The OOM (Out Of Memory) killer has activated on a production database server. Describe your immediate response and your long-term strategy to prevent this, including tuning `/proc/sys/vm/` parameters.
4.  Explain the difference between `perf`, `eBPF/bcc`, and `SystemTap`. For which specific troubleshooting scenario would you choose one over the others?
5.  How does the Linux kernel I/O scheduler (e.g., CFQ, Deadline, NOOP) impact database performance? Describe how you would choose and tune an I/O scheduler for a high-throughput write-intensive database.
6.  What are "huge pages"? Explain the performance benefits and potential trade-offs of using Transparent Huge Pages (THP) versus explicit huge pages for a large in-memory application like Redis or an in-memory database.
7.  Describe the memory management subsystem: pages, slabs, and the slab allocator. How could you use tools like `slabtop` to diagnose a kernel memory leak?
8.  Explain the purpose and mechanics of `futexes` (fast userspace mutexes). How do they relate to `mutexes` and `semaphores` in application performance?
9.  A process is in a state of "Uninterruptible Sleep" (D state). What does this signify, and what are the common causes? How would you investigate and attempt to resolve it?
10. Explain the role of `ksoftirqd` and `kworker` processes. Under what conditions would you see high CPU usage from these, and how would you diagnose the root cause?
11. How does the Completely Fair Scheduler (CFS) work? Explain the concepts of `vruntime` and `nice` values and how they affect process scheduling.
12. Describe the journey of a network packet through the Linux network stack, from the NIC driver to the application socket. Mention key data structures like `sk_buff`.
13. What is `NUMA` (Non-Uniform Memory Access)? How does it affect system performance, and what are the key considerations for configuring a large NUMA-aware server?
14. Explain the `sysrq` key. Provide three distinct examples of its use for emergency system recovery or debugging.
15. What is `eBPF` (extended Berkeley Packet Filter)? Describe how it can be used for advanced observability (e.g., tracing function entry/exit) without requiring kernel modules, and contrast it with traditional `kprobes`.

---

### **Category 2: Advanced Networking (Questions 16-30)**

16. Explain the complete traversal order of a packet through the `iptables` `raw`, `mangle`, `nat`, and `filter` tables for both a locally destined connection and a forwarded connection.
17. Design a high-availability load balancing solution using `keepalived` and `HAProxy`. Explain how VRRP (Virtual Router Redundancy Protocol) works in this context and how you would handle state synchronization.
18. What is `nftables`? Design a complex `nftables` ruleset that replaces an equivalent `iptables` setup for a typical firewall with DNAT, SNAT, and filtering rules, highlighting the advantages of `nftables`.
19. Using the `tc` (Traffic Control) command, how would you simulate a 100ms network latency with 10% packet loss on a network interface for testing application resilience?
20. Explain the concept of a "network namespace." Design a multi-tenant environment where each tenant has its own network stack, including interfaces, routing tables, and firewall rules, all on a single host.
21. What is BGP (Border Gateway Protocol)? Describe a scenario where you would use a BGP daemon like `ExaBGP` or `GoBGP` on a Linux server to advertise routes within a data center.
22. How does the `conntrack` (connection tracking) subsystem work? What are the performance implications of a large `conntrack` table, and how would you tune it for a high-throughput firewall?
23. Explain the differences between VXLAN, GRE, and IP-in-IP tunnels. When would you choose one over the other for building an overlay network?
24. Describe the function of `ethtool`. How would you use it to diagnose and tune network card settings like ring buffer sizes, offload features (TSO, GSO), and interrupt coalescing?
25. What is a "service mesh" (e.g., Istio, Linkerd)? From a Linux networking perspective, what underlying technologies (e.g., `iptables`, `eBPF`, IPVS) are typically used to implement its data plane?
26. A server is experiencing a "SYN flood" attack. Describe, in detail, the steps you would take using `sysctl` and `iptables` to mitigate the attack in real-time.
27. Explain the purpose of `ipvs` (IP Virtual Server). How does it differ from `iptables` DNAT for load balancing, and what are its performance characteristics?
28. How can you use `ss` to debug a "socket in use" error that `netstat` might not clearly show? Demonstrate an `ss` command to find all processes listening on a specific port and show their timers.
29. What is ARP flux? Describe the conditions that cause it and how to prevent it on a multi-homed Linux server.
30. Explain the role of `rp_filter` (Reverse Path Filtering). What are the different modes (`strict`, `loose`), and what are the security implications of disabling it?

---

### **Category 3: Security & Hardening (Questions 31-45)**

31. Compare and contrast SELinux and AppArmor. For a new application, describe the process of creating a security profile for each, from initial enforcement to policy refinement.
32. A process is running in an unexpected SELinux context. Describe your methodology for debugging this issue, including the key commands (`audit2why`, `semanage`, `setroubleshoot`) and log files you would analyze.
33. Explain the concept of Linux Capabilities. How do they provide a more granular alternative to the setuid/setgid bits? Provide an example of giving a web server the `CAP_NET_BIND_SERVICE` capability.
34. Design a sandbox for an untrusted third-party binary using a combination of `chroot`, `namespaces`, `seccomp-bpf`, and a dedicated, unprivileged user. Explain the security benefits of each layer.
35. What is `seccomp-bpf`? How can you use it to restrict the system calls a container or application can make, and why is this a powerful security mechanism?
36. Describe the process of setting up a centralized, immutable logging system using `systemd-journal-remote` and forward-secure sealing. How does this protect against log tampering by an attacker who has gained root access?
37. Explain the security implications of the `ptrace` system call. How would you harden a system to prevent one user process from spying on another?
38. What is a "trusted boot" process? Describe how technologies like TPM (Trusted Platform Module) and UEFI Secure Boot can be used to ensure the integrity of the boot chain.
39. How would you use `fscrypt` or `eCryptfs` to encrypt a user's home directory? What are the performance and recovery implications compared to full-disk encryption (LUKS)?
40. Explain the "principle of least privilege" and apply it to designing a `sudoers` configuration for a junior DevOps engineer who needs to restart specific services but not have full root access.
41. What are the key security considerations when configuring a container registry (like Harbor or Nexus)? Discuss image signing, vulnerability scanning, and access control.
42. Explain the `auditd` daemon. How would you configure `auditd` rules to track all modifications to critical system files (`/etc/passwd`, `/etc/shadow`, `/etc/sudoers`) and log all uses of the `sudo` command?
43. Describe a "zero trust" network architecture. How can Linux technologies like `mTLS`, micro-segmentation (via `iptables`/`eBPF`), and identity-aware proxies be used to implement it?
44. What is the `D-Bus` system and what are its security implications? How would you audit or restrict D-Bus message communication between services?
45. Explain how Address Space Layout Randomization (ASLR) and Stack Canaries work to mitigate memory corruption attacks like buffer overflows.

---

### **Category 4: Storage & Filesystems (Questions 46-55)**

46. Design a highly available, scalable storage solution for a large Kubernetes cluster. Compare and contrast Ceph, GlusterFS, and a cloud provider's solution (e.g., EBS, GKE Persistent Disks), focusing on performance, consistency models, and operational complexity.
47. You are tasked with migrating a running server from a standard partition layout to LVM without downtime. Describe the step-by-step process.
48. Explain the write-ahead logging (WAL) mechanism in filesystems like `ext4` and `XFS`. How does it contribute to filesystem consistency and recovery after a crash?
49. What are the performance characteristics and use cases for `XFS` versus `Btrfs`? Discuss features like copy-on-write, snapshots, and built-in RAID.
50. A database server reports high I/O wait (`%wa`). How would you use tools like `iostat`, `iotop`, and `blktrace` to determine if the bottleneck is hardware, the filesystem, or the application's I/O pattern?
51. Explain the concept of a "copy-on-write" filesystem. What are the advantages (e.g., fast snapshots) and disadvantages (e.g., fragmentation) of this design?
52. Describe how to set up and manage an iSCSI target and initiator on Linux. What are the key considerations for performance and multipathing?
53. What is `dm-verity`? How does it provide integrity protection for block devices, and in what scenario (e.g., embedded systems, immutable OS) would it be essential?
54. Explain the differences between block storage, file storage, and object storage. Provide a Linux-based solution for each.
55. How would you benchmark a new storage system? Describe the tools you would use (e.g., `fio`, `bonnie++`) and the types of tests you would run (sequential vs. random, read vs. write).

---

### **Category 5: System Architecture & Design (Questions 56-70)**

56. Design a "cattle, not pets" infrastructure for a stateless web application. Describe the roles of configuration management, auto-scaling groups, immutable images, and service discovery.
57. You need to design a system for zero-downtime deployments. Describe the blue-green deployment and canary release patterns. How would you implement a canary release using a service mesh or a load balancer?
58. Explain the CAP theorem. Given the choice, when would you design a system for Consistency over Availability (CP) and when for Availability over Consistency (AP)? Provide a Linux-based technology example for each.
59. What is a "sidecar pattern" in containerized architecture? Provide a practical example (e.g., log shipping, metrics collection) and explain how it works.
60. Design a highly available message queuing system using RabbitMQ or Kafka on Linux. Detail the cluster setup, queue mirroring or partition replication, and client failover mechanisms.
61. Explain the concept of "eventual consistency." How would you architect a system using a message queue to ensure data is eventually consistent across multiple microservices?
62. You are building a global application. Describe a multi-region, active-active architecture. How would you handle data synchronization and conflict resolution?
63. What is "Infrastructure as Code" (IaC)? Compare and contrast a declarative tool like Terraform with an imperative tool like Ansible. When would you use one over the other?
64. Design a CI/CD pipeline for a containerized application. Include stages for linting, security scanning (e.g., Trivy), unit testing, building the image, pushing to a registry, and deploying to a staging environment.
65. Explain the "strangler fig" pattern for migrating a monolithic application to microservices. How would you use a reverse proxy (like NGINX or Traefik) to facilitate this?
66. What are the key architectural components of a Prometheus-based monitoring stack? Explain the roles of Prometheus, Alertmanager, Grafana, and the `node_exporter`.
67. How would you design a system to handle massive, spiky traffic (e.g., for a ticketing website)? Discuss the role of autoscaling, load shedding, and asynchronous processing.
68. Explain the concept of "sharding." How would you implement sharding for a data store, and what are the challenges with rebalancing?
69. Describe the principles of a good disaster recovery (DR) plan. What is the difference between RPO and RTO, and how would you achieve a low RPO for a critical database?
70. What is a "service registry" and why is it crucial in a microservices architecture? Compare Consul and etcd in this role.

---

### **Category 6: Containerization & Orchestration (Deep Dive) (Questions 71-80)**

71. Explain the exact sequence of steps `containerd` and `runc` take when a `kubelet` instructs them to start a container.
72. Describe the CNI (Container Network Interface) plugin architecture. How does a CNI plugin (like Calico or Flannel) configure networking for a pod when it's created?
73. A pod in Kubernetes is stuck in `CrashLoopBackOff`. Describe your systematic approach to debugging this, from `kubectl describe` and `kubectl logs` to checking the node's `kubelet` logs and the container's runtime logs.
74. Explain how Kubernetes Ingress controllers work. Compare and contrast the NGINX Ingress Controller with Traefik, focusing on their configuration methods and feature sets.
75. What are Kubernetes Custom Resource Definitions (CRDs)? Design a CRD for a simple "Database" resource that would provision a stateful set and a service.
76. Explain the role of `etcd` in Kubernetes. Describe the process of backing up and restoring `etcd` for disaster recovery.
77. How does Kubernetes manage persistent storage for stateful applications? Explain the lifecycle of a PersistentVolume (PV), PersistentVolumeClaim (PVC), and StorageClass.
78. What are Pod Security Policies (PSPs) or their modern replacements (Pod Security Admission)? Design a policy that prevents pods from running as root and forces them to use a read-only root filesystem.
79. Explain the concept of "init containers" and provide two distinct use cases for them.
80. Describe the metrics that the Kubernetes Horizontal Pod Autoscaler (HPA) can use. How would you configure the HPA to scale based on a custom application metric exposed via Prometheus?

---

### **Category 7: Advanced Troubleshooting & Observability (Questions 81-90)**

81. A production server is experiencing intermittent, high-latency spikes. Your monitoring shows nothing obvious. Describe your end-to-end diagnostic process, from checking hardware interrupts (`/proc/interrupts`) to using `perf` to profile the kernel and applications.
82. How can you use `strace` to debug a "permission denied" error that doesn't show up in the application's own logs? What are the performance implications of running `strace`?
83. Explain the three pillars of observability (logs, metrics, traces). How would you implement distributed tracing in a microservices environment using tools like Jaeger or Zipkin?
84. A process is consuming 100% CPU, but it's not clear what it's doing. How would you use `perf top` or `gdb` to attach to the running process and inspect its call stack to find the problematic function?
85. You suspect a memory leak in a long-running C++ application. How would you use tools like `valgrind` or `AddressSanitizer` to identify the source of the leak?
86. What is "redirection" in the context of `systemd`? How would you use `journalctl -u myservice` to get the logs from a service that failed to start, and how would you increase its log verbosity without restarting it?
87. Explain how to use `tcpdump` and `Wireshark` to debug a TLS handshake failure. What specific information would you look for in the packet capture?
88. A user reports that a specific command is slow, but only when run via `cron`. Describe the potential environmental differences and how you would debug this.
89. How can you use `dmesg` and `/sys/kernel/debug/` to diagnose hardware-related issues, such as a failing disk or a misbehaving driver?
90. Explain the concept of "slos" (Service Level Objectives) and "sli" (Service Level Indicators). How would you define an SLI for a web API's latency and an SLO based on it?

---

### **Category 8: Automation & Tooling (Questions 91-100)**

91. Write an `ansible` playbook that uses a Jinja2 template to deploy a customized `nginx.conf` file to a group of web servers, ensuring the service is reloaded only if the configuration file changes.
92. Explain the difference between an `Ansible` role and a collection. How would you structure a complex project that includes multiple roles and custom modules?
93. How would you use `systemd` to manage a simple application that is not natively a service? Show a sample unit file that handles forking, PID files, and automatic restarts.
94. Write a `bash` script that uses `getopts` to parse command-line arguments for a hypothetical `deploy.sh` script, which takes options like `-e` (environment), `-v` (version), and `-h` (help).
95. Describe how you would use `jq` to parse a complex JSON API response to extract a specific list of values, for example, getting the names of all failed pods from a `kubectl get pods -o json` output.
96. Explain the purpose of a "shebang" line (`#!/bin/bash` vs `#!/usr/bin/env bash`). Why is the latter often considered more portable?
97. How would you write a `systemd` path unit (`*.path`) to monitor a directory for new files and trigger a service unit to process them?
98. What is "idempotency" in the context of configuration management? Why is it a critical property for tools like Ansible, Puppet, and Chef?
99. Design a solution for securely managing secrets (like database passwords or API keys) in an automated CI/CD pipeline. Compare and contrast using HashiCorp Vault with GitOps-style sealed secrets.
100. Explain how to use `LD_PRELOAD` to intercept or override a function call in a dynamically linked library for debugging or testing purposes.









---

### **Category 1: Deep Kernel & Subsystem Internals (Questions 1-15)**

1.  Explain the technology behind kernel live patching (e.g., `kpatch`, `kGraft`). What are the fundamental limitations and risks of applying a live patch to a production system?
2.  Describe the Linux kernel's memory compaction and defragmentation process. Under what conditions would you see it being triggered, and how can you influence its behavior via `/proc/sys/vm/`?
3.  What are `netfilter` hooks? Explain the order in which they are called for a packet traversing the `PREROUTING`, `FORWARD`, and `POSTROUTING` chains.
4.  Explain the difference between `kprobes`, `kretprobes`, and `tracepoints`. When would you choose one over the other for building an eBPF-based monitoring tool?
5.  Describe the `RCU` (Read-Copy-Update) mechanism in the kernel. Why is it critical for performance in highly concurrent systems, and what are its trade-offs?
6.  What is `lockdep`? How would you use it to detect potential deadlocks in a kernel module or a device driver you are developing?
7.  Explain the concept of `user namespaces`. What security benefits do they provide, and how do they enable a root user inside a container to be unprivileged on the host?
8.  Describe the journey of a write operation from the `write()` system call to being physically written to disk on an `ext4` filesystem with journaling enabled.
9.  How does the kernel's `tickless` (`NO_HZ`) feature work? What is its impact on power consumption and latency in virtualized environments?
10. Explain the role of the `initramfs` (initial RAM filesystem). Describe the process of building a custom `initramfs` to unlock an encrypted LVM root partition at boot.
11. What is `ftrace` and how does it differ from `perf`? Provide a scenario where `ftrace`'s function graph tracer would be the ideal tool to diagnose a kernel issue.
12. Explain the difference between a `soft lockup` and a `hard lockup`. What kernel watchdog mechanisms are responsible for detecting them?
13. How would you use `crash` utility to analyze a kernel `vmcore` file from a crashed system? What are the first commands you would run to get a high-level overview of the failure?
14. Describe the `BPF` (Berkeley Packet Filter) Just-In-Time (JIT) compiler. What are its security implications, and how does it dramatically improve eBPF program performance?
15. Explain the concept of `cgroup` controllers. Design a setup using the `pids` and `device` controllers to limit the number of processes and restrict access to specific devices for a set of containers.

---

### **Category 2: Advanced Cloud-Native Networking (Questions 16-30)**

16. Compare and contrast the networking implementations of Cilium (eBPF-based) and Calico (BGP-based). What are the pros and cons of each for a large-scale Kubernetes cluster?
17. Describe the data path of a request through a service mesh like Istio that uses an Envoy proxy sidecar. How are `iptables` rules used to "hijack" traffic to the sidecar?
18. Explain the concept of `eBPF XDP` (eXpress Data Path). How can it be used to build a high-performance DDoS mitigation solution that operates before the kernel's network stack?
19. What is `BGP Confederations` and `Route Reflectors`? Design a BGP topology for a data center that avoids a full-mesh of iBGP peers.
20. Explain how DNS-based service discovery works in Kubernetes. Describe the entire resolution process from a pod inside one namespace querying a service in another namespace.
21. What is `SR-IOV` (Single Root I/O Virtualization)? How does it provide near-native network performance for virtual machines or containers, and what are the management complexities?
22. A pod cannot resolve an external DNS name (e.g., `google.com`) but can resolve internal Kubernetes services. Describe your systematic debugging process, starting from the pod's `/etc/resolv.conf` to the `CoreDNS` pods and their upstream configuration.
23. Explain the `TCP Fast Open` (TFO) feature. What are the security considerations, and how would you enable it on a Linux server?
24. What is `gRPC` and how does it use HTTP/2? From a networking perspective, what are the advantages of gRPC over traditional REST APIs for microservice communication?
25. Describe the function of a Kubernetes `Ingress` vs. a `Gateway API` resource. What problems is the Gateway API trying to solve that traditional Ingress controllers cannot?
26. How would you implement network policies in Kubernetes to enforce a "default deny" posture, only allowing pods in the same namespace to communicate with each other on a specific port?
27. Explain the concept of `MACsec` (Media Access Control Security). In what scenario would you choose it over IPsec for securing network traffic?
28. What is `Anycast`? Design a highly available DNS service using Anycast and explain how it routes clients to the geographically closest server.
29. Describe the `conntrack` synchronization mechanisms required for an active-passive firewall pair using `keepalived` to maintain state during a failover.
30. How does `Envoy Proxy` implement its load balancing algorithms (e.g., Round Robin, Least Request, Ring Hash)? Why is its implementation often more sophisticated than a simple L4 load balancer?

---

### **Category 3: Security, Compliance & Supply Chain (Questions 31-45)**

31. Explain the SLSA (Supply-chain Levels for Software Artifacts) framework. How would you use tools like `Sigstore` (cosign, Rekor) to build a verifiable and tamper-resistant software supply chain?
32. What is a "runtime security" tool? Describe how Falco uses eBPF or `sysdig` to detect anomalous activity within a running container or host.
33. Explain the principle of "separation of duties" in a CI/CD pipeline. Design a GitOps workflow where the developer who merges code cannot approve its deployment to production.
34. What is `mTLS` (mutual TLS)? Describe how you would automate the issuance and rotation of mTLS certificates for all services within a service mesh.
35. A security audit flags that your servers are using weak cryptographic ciphers. How would you harden the `OpenSSH` and `OpenSSL` configurations on a fleet of servers using Ansible?
36. Explain the concept of a "zero-knowledge proof" and provide a hypothetical use case for it in a Linux-based authentication system.
37. What is `TPM 2.0`'s "remote attestation" feature? How can a cloud service use it to verify that a VM is booting into a trusted, unmodified state before providing it with secrets?
38. Describe the process of creating and managing a private Certificate Authority (CA) using `cfssl` or `EJBCA` for internal services.
39. What are the security implications of running Docker-in-Docker (DinD)? What are the safer alternatives for running a CI/CD pipeline that needs to build container images?
40. Explain the concept of "policy as code." Compare and contrast Open Policy Agent (OPA) with Gatekeeper for enforcing policies on a Kubernetes cluster.
41. How would you implement a "break-glass" procedure for emergency access that provides auditable, time-limited, and just-in-time privileged access to a production system?
42. What is the purpose of `chattr` and `lsattr`? Provide an example of how you would use them to make a critical log file immutable, even to the root user.
43. Describe the security model of `Wayland` versus `X11`. Why is Wayland considered more secure by design?
44. How would you use `auditd` to create a real-time alerting pipeline that triggers a response in a SIEM system whenever a user adds a new `sudo` rule or SSH key?
45. Explain the concept of "confidential computing." How do technologies like AMD SEV or Intel SGX create a trusted execution environment (TEE) on a Linux system?

---

### **Category 4: High-Availability & Disaster Recovery Architecture (Questions 46-60)**

46. Design a multi-region active-active database architecture using PostgreSQL. What are the challenges of conflict resolution, and what tools (e.g., BDR, Patroni) would you use to manage it?
47. Explain the difference between synchronous and asynchronous replication. For a financial application requiring zero data loss, which would you choose, and what are the performance trade-offs?
48. What is a "split-brain" scenario in a high-availability cluster? Describe the mechanisms (e.g., quorum, fencing) used to prevent it.
49. Design a disaster recovery plan for a stateless application running in Kubernetes across two cloud providers. Explain how you would manage DNS failover and data replication.
50. Explain the Raft consensus algorithm. How does it compare to Paxos, and where is it implemented in modern distributed systems (e.g., etcd, RethinkDB)?
51. What is the purpose of a `Pacemaker` and `Corosync` stack? Design a highly available NFS server using this stack.
52. Describe the process of performing a full-point-in-time recovery of a MySQL database from a physical backup (e.g., Percona XtraBackup) combined with binary logs.
53. How would you architect a globally distributed rate limiter to prevent API abuse across multiple data centers? What are the challenges of maintaining state?
54. Explain the concept of "backpressure" in a distributed system. How can it be used to prevent cascading failures during a traffic surge?
55. Design a backup strategy for a large `etcd` cluster. How would you automate and test the restore process to ensure it meets your RTO (Recovery Time Objective)?
56. What is "Chaos Engineering"? Describe an experiment you would run on a microservices application to test its resilience to a database connection failure.
57. Explain the difference between a "hot," "warm," and "cold" disaster recovery site. What are the cost and RTO/RPO implications of each?
58. How would you implement a canary analysis system that automatically promotes or rolls back a deployment based on real-time metrics like error rate and latency?
59. Design a highly available message queueing system using NATS JetStream. How does its streaming and persistence model compare to RabbitMQ or Kafka?
60. Your primary data center has a complete power failure. Describe the automated steps your infrastructure should take to fail over to a secondary site, including DNS, load balancers, and application state.

---

### **Category 5: Performance, Observability & Profiling (Questions 61-75)**

61. A Go application is showing high latency. How would you use `pprof` to profile its CPU and memory usage, and what would you look for in the generated graphs?
62. Explain the difference between "whitebox" and "blackbox" monitoring. Give an example of a critical metric for each for a web application.
63. How would you build a cost-effective, long-term metrics storage solution using Prometheus and a remote backend like Thanos or Cortex?
64. Describe the OpenTelemetry project. How does it aim to unify the collection of logs, metrics, and traces, and how would you instrument an application to use it?
65. A Java application is experiencing frequent "Stop-the-World" GC pauses. How would you use `jstat`, `jmap`, and `GC logs` to diagnose the issue and tune the garbage collector?
66. What is "flame graph" visualization? How would you generate one from `perf` data to identify the most CPU-intensive functions in a complex application?
67. Explain the concept of "service level indicators" (SLIs), "service level objectives" (SLOs), and "service level agreements" (SLAs). Design an SLO for API latency, including the error budget calculation.
68. How can you use `eBPF` to trace a specific function within a running Node.js application without modifying its code or restarting it?
69. Describe the architecture of a distributed tracing system like Jaeger. What are the roles of the collector, query service, and UI?
70. You are seeing intermittent packet loss on a 10Gbps network interface. How would you use `ethtool -S`, `dropwatch`, and `perf` to determine if the issue is with the NIC driver, the kernel, or the application?
71. Explain how to use `bpftrace` to write a one-liner that counts all `syscalls` by process name.
72. What is "cardinality" in the context of metrics monitoring? Why is high cardinality a problem for Prometheus, and how can you mitigate it?
73. How would you set up and interpret a "continuous profiling" solution to detect performance regressions in your applications automatically?
74. A database server is slow, but CPU, memory, and I/O metrics are all normal. What advanced tools and techniques would you use to investigate potential lock contention or query plan regressions?
75. Explain how `cAdvisor` integrates with the Kubernetes kubelet to provide container resource usage metrics. What are its limitations?

---

### **Category 6: Automation, Tooling & Platform Engineering (Questions 76-100)**

76. Explain the GitOps operational model. How does it differ from traditional push-based CI/CD? Describe a potential "GitOps drift" scenario and how you would remediate it.
77. What is the purpose of Terraform's `taint` and `import` commands? Provide a scenario for each.
78. How would you write a custom Ansible filter plugin in Python to manipulate a complex data structure?
79. Design an Internal Developer Platform (IDP) using tools like `Backstage`. What core components would you include to improve the developer experience?
80. Explain the concept of a "Kubernetes Operator." Describe the control loop you would implement in a custom operator to manage the lifecycle of a third-party application.
81. What is a `CSI` (Container Storage Interface) driver? Why is it a better abstraction than in-tree storage drivers in Kubernetes?
82. How would you use `Packer` and `Terraform` to build a golden image for a virtual machine and then deploy a fleet of them in a repeatable and automated way?
83. Describe the process of creating a custom Linux distribution for an embedded appliance using `Yocto Project` or `Buildroot`.
84. What is `Docker BuildKit`? How does it improve upon the classic Docker build engine in terms of performance, concurrency, and security?
85. Explain the difference between `helm template` and `helm install --dry-run`. When would you use each?
86. How would you use `Kyverno` to enforce that all pods in a cluster must have resource limits and a specific set of labels?
87. What is `Crossplane` and how does it aim to turn your Kubernetes cluster into a universal control plane for cloud infrastructure?
88. Write a `systemd` unit file that runs a script 5 minutes after boot and then again every 24 hours.
89. Explain the purpose of `OCI` (Open Container Initiative). What are the `runtime-spec` and `image-spec`?
90. How would you manage secrets in a GitOps repository without storing them in plaintext? Describe a solution using Sealed Secrets or a tool like SOPS.
91. What is the purpose of `jq`'s `@sh` and `@base64` functions? Provide a practical example for each.
92. Describe how you would use `Vagrant` to create a local development environment that perfectly mirrors the production setup defined in your Ansible playbooks.
93. Explain the concept of "IaC drift." How would you use a tool like `tfsec` or `checkov` to scan your Terraform code for security and compliance misconfigurations *before* applying it?
94. What is a `Helm` chart hook? Describe a use case for a `post-install` hook.
95. How would you build a multi-arch Docker image (e.g., for `amd64` and `arm64`) using `docker buildx`?
96. Explain the role of a service catalog in an Internal Developer Platform. How does it help developers discover and consume self-service resources?
97. What is the difference between `Argo CD` and `Flux` as GitOps operators for Kubernetes?
98. How would you use `Terraform` to manage a Kubernetes cluster's resources, and what are the pros and cons of this approach compared to using a native Kubernetes tool like `Helm` or `Kustomize`?
99. Design a CI/CD pipeline step that uses `Grype` or `Trivy` to scan a container image for vulnerabilities and fails the build if any critical vulnerabilities are found.
100. Explain the concept of "progressive delivery." How does it extend beyond canary deployments to include feature flags and A/B testing?
