

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
