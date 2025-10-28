


### Category 1: Deep Dive & Troubleshooting

1.  **The Mystery of the Intermittent Connection:** A user reports that a Deployment (let's call it `frontend`) can only *sometimes* successfully connect to its backend Service (`backend`). There are no logs of connection refused, but some requests just time out. The `frontend` and `backend` pods are running on different nodes. What is your systematic troubleshooting process, and what are the top 3 potential root causes you would investigate first?

2.  **The Stuck Terminating Pod:** You have a Pod that has been in the `Terminating` state for over 30 minutes. `kubectl delete pod <pod-name> --grace-period=0 --force` doesn't work. Describe what is happening within the Kubernetes control plane and the kubelet that would cause this. What are the likely culprits, and how would you manually intervene to clear it?

3.  **ImagePullBackOff vs. ErrImagePull:** Explain the precise difference between the `ImagePullBackOff` and `ErrImagePull` states. More importantly, describe a scenario where a pod could be stuck in `ImagePullBackOff` for hours, even though the image is correctly spelled, the tag exists, and the node has full internet access.

4.  **The Case of the Missing CPU:** A node has 4 CPUs available. You schedule a Pod with a `resources.requests.cpu` of `2`. A second pod with a request of `1.5` is scheduled. A third pod with a request of `1` is pending. However, `kubectl top node` shows the node is only using 1.5 cores. Why is the third pod not being scheduled, and what does this tell you about the difference between *requests* and *actual usage*?

---

### Category 2: Networking Nuances

5.  **Headless Service vs. ClusterIP Service:** You have a database cluster that you want clients to connect to directly, without a load balancer. You are considering using a Headless Service. Explain exactly how DNS resolution works for a Headless Service versus a standard ClusterIP Service. What are the specific networking and application-level implications of this choice?

6.  **Egress Traffic Control:** Your security team mandates that a specific group of pods in the `payments` namespace should *only* be allowed to make outbound network calls to `api.stripe.com` on port 443. All other outbound traffic must be denied. Describe the complete Kubernetes-native solution to achieve this, including the specific API objects and their required configuration.

7.  **Ingress Controller Deep Dive:** A user reports getting a `502 Bad Gateway` error from an application behind an Ingress. The application pods are running and healthy. What are the most common causes for this specific error, and how do you debug the path from the user's request, through the Ingress Controller, to the Service and finally to the Pod?

8.  **CNI Plugin Comparison:** A colleague asks you to explain the fundamental difference between a CNI plugin that uses an overlay network (like Flannel in VXLAN mode) versus one that uses routing (like Calico in BGP mode). Discuss the performance implications, operational complexity, and typical use cases for each approach.

---

### Category 3: Scheduling, Autoscaling, and Performance

9.  **Advanced Node Affinity:** You have nodes with three types of attached hardware: GPUs, high-speed NVMe drives, and standard SSDs. You need to schedule three types of workloads: ML training (needs GPU), databases (needs NVMe), and web servers (prefers SSD but is flexible). Design a comprehensive strategy using node labels, taints, tolerations, and node affinity to ensure pods land on the correct nodes while maximizing cluster utilization.

10. **Cluster Autoscaler Failure:** The Cluster Autoscaler (CA) reports that it cannot scale up the node group. The logs show "0 un schedulable pods". However, you have several pods in a `Pending` state. Why might the CA not see these pods as "unschedulable," and what configuration or resource request issues could lead to this discrepancy?

11. **HPA vs. VPA vs. KEDA:** You have a queue-processing worker deployment. Its traffic is highly spiky and is directly correlated with the length of a RabbitMQ queue. Compare and contrast using the Horizontal Pod Autoscaler (HPA), the Vertical Pod Autoscaler (VPA), and KEDA (Kubernetes Event-Driven Autoscaler) for this workload. Which is the best fit and why?

12. **QoS and Eviction:** A node is experiencing memory pressure. The kubelet needs to evict a pod. Describe the exact order of eviction based on Kubernetes Quality of Service (QoS) classes. Explain how a pod's `resources.requests` and `resources.limits` for memory determine its QoS class and its likelihood of being evicted.

---

### Category 4: State, Storage, and Security

13. **StatefulSet Rolling Update:** You have a StatefulSet with 3 replicas managing a consensus-based database (like etcd or Zookeeper). Describe, step-by-step, what happens when you initiate a rolling update. What guarantees does the StatefulSet controller provide regarding pod identity, network names, and persistent storage during this process? Why is this update strategy critical for stateful applications?

14. **CSI Driver Architecture:** Your company wants to add support for a new proprietary storage system. You've been asked to explain the Container Storage Interface (CSI). Describe the roles of the CSI Provisioner, CSI Attacher, and CSI Node Driver. How do they work together to go from a `PersistentVolumeClaim` to a mounted volume inside a pod?

15. **Beyond RBAC:** You need to enforce a cluster-wide policy that prevents users from creating Pods that use the `hostNetwork` setting or run with `privileged: true`. While RBAC can control *who* can create pods, it can't validate the *contents* of the pod spec. What is the modern, recommended Kubernetes-native mechanism to enforce this kind of policy, and how does it work?

16. **Secrets Management Strategy:** The default method of storing secrets in `etcd` (even at rest) is not sufficient for your organization's security compliance. Design a robust strategy for managing secrets in Kubernetes. Your answer should include how you would inject secrets into pods, how you would handle secret rotation, and how you would prevent secrets from being stored in the cluster's primary data store (`etcd`).

---

### Category 5: Architecture and Control Plane

17. **GitOps and Drift Detection:** You are using Argo CD for GitOps. A developer manually runs `kubectl scale deployment my-app --replicas=5` to handle an emergency traffic spike. Argo CD now shows the deployment is "OutOfSync". Explain the concept of "drift" in this context. What are the different ways Argo CD can be configured to handle this drift (e.g., manual sync, auto-sync with pruning), and what are the operational trade-offs of each?

18. **Custom Resource Design:** You want to create a `Backup` custom resource that, when created, triggers a one-time backup of a specific `PersistentVolumeClaim`. Describe the components you would need to build: the CustomResourceDefinition (CRD) itself, and a basic outline of the controller's reconciliation loop. What would the controller *do* when it sees a new `Backup` object?

19. **etcd Consistency and Recovery:** The control plane API servers in your 3-node HA cluster are all running, but you are seeing strange, inconsistent behavior in your cluster objects. You suspect an `etcd` consistency problem. Describe the Raft consensus algorithm at a high level and how it ensures data consistency across the `etcd` members. What would be your immediate steps to diagnose and potentially recover from a split-brain scenario?

20. **Multi-Cluster Service Discovery:** You have two separate Kubernetes clusters, one in `us-east-1` and one in `us-west-2`. You need an application in `us-east-1` to be able to discover and connect to a database running in `us-west-2`. Discuss the challenges involved (e.g., overlapping CIDRs, network latency, DNS). Outline at least two potential architectural patterns to solve this cross-cluster service discovery problem.

---




---

### Category 1: Deep Dive & Troubleshooting (1-15)

1.  **The Mystery of the Intermittent Connection:** A `frontend` pod can only *sometimes* connect to its `backend` Service. There are no "connection refused" logs, but some requests time out. The pods are on different nodes. What is your systematic troubleshooting process, and what are the top 3 potential root causes?
2.  **The Stuck Terminating Pod:** A pod is in the `Terminating` state for over 30 minutes. `kubectl delete --force` doesn't work. Describe what is happening within the control plane and the kubelet to cause this. What are the likely culprits, and how would you manually intervene?
3.  **The Case of the Missing CPU:** A node has 4 CPUs. You schedule a pod with a `request` of `2`, a second with `1.5`, and a third with `1` is pending. However, `kubectl top node` shows the node is only using 1.5 cores. Why is the third pod pending, and what does this illustrate about requests vs. usage?
4.  **ImagePullBackOff vs. ErrImagePull:** Explain the precise difference between these states. Describe a scenario where a pod could be stuck in `ImagePullBackOff` for hours, even though the image name/tag is correct and the node has internet access.
5.  **Silent CrashLoopBackOff:** A pod is in `CrashLoopBackOff`, but `kubectl logs` shows no output from the container. What are the most likely reasons for this behavior, and how would you diagnose the issue without container logs?
6.  **The Pod Stuck in `ContainerCreating`:** A pod remains in the `ContainerCreating` phase indefinitely. `kubectl describe pod` shows no events. What underlying issues could cause this, and where would you look next (e.g., on the node, in the controller manager)?
7.  **`kubectl exec` Fails with "Container Not Found":** You are trying to `exec` into a running pod, but you get an error that the container cannot be found, even though `kubectl get pods` shows it's running. What could cause this discrepancy?
8.  **Node `NotReady` with `Kubelet` Healthy:** A node is `NotReady`. You SSH into it and the `kubelet` service is running without errors in its logs. What other components or conditions on the node could cause this state?
9.  **High `conntrack` Table Usage:** You are seeing `connection timed out` errors for new outbound connections from pods, but existing connections work. `dmesg` on the node shows `nf_conntrack: table full, dropping packet`. What is happening, and what are the potential solutions and their trade-offs?
10. **DNS Resolution Delays:** Applications are experiencing intermittent 5-second delays on the first DNS query to a Kubernetes Service. Subsequent queries are fast. What is the likely cause of this delay, and how does `ndots` configuration play a role?
11. **PodDisruptionBudget (PDB) Blocking Drains:** You are trying to drain a node for maintenance, but `kubectl drain` fails, citing a PDB violation. The deployment has 5 replicas, and the PDB `minAvailable` is 3. Why is the drain failing, and how can you safely proceed?
12. **Init Container Loop:** A pod has an `init` container that checks for the availability of a database. The pod is stuck in a `PodInitializing` phase. The `init` container is not failing, but it's not completing either. What could be happening?
13. **Leaking Finalizers:** You delete a namespace, and it gets stuck in the `Terminating` state forever. You find a custom resource in that namespace with a `finalizer` that its controller is not removing. Explain the finalizer mechanism and how you would manually resolve this.
14. **EndpointSlices Not Updating:** A new pod is started for a Service, but other pods cannot resolve it via DNS. You check the Service's `Endpoints` and it's empty, but the `EndpointSlices` for that service exist and contain the old pod IPs. What could cause this inconsistency between the Endpoint controller and the EndpointSlice controller?
15. **`kube-proxy` in iptables vs. ipvs Mode:** A user reports that after a high-traffic event, some services became unresponsive. You suspect `kube-proxy` in `iptables` mode. Explain the performance bottleneck in `iptables` mode and how `ipvs` mode solves it. What are the operational differences?

---

### Category 2: Networking Nuances (16-30)

16. **Headless Service vs. ClusterIP Service:** Explain exactly how DNS resolution works for a Headless Service versus a standard ClusterIP Service. What are the specific networking and application-level implications of this choice?
17. **Egress Traffic Control:** Mandate that pods in the `payments` namespace can *only* call `api.stripe.com` on port 443. Describe the complete Kubernetes-native solution, including the API objects and their configuration.
18. **Ingress `502 Bad Gateway`:** A user gets a `502` from an app behind an Ingress. The app pods are healthy. What are the most common causes for this error, and how do you debug the path from the user, through the Ingress Controller, to the Service, and to the Pod?
19. **Overlay vs. Routing CNI:** Explain the fundamental difference between a CNI plugin using an overlay network (Flannel/VXLAN) versus one using routing (Calico/BGP). Discuss performance, complexity, and use cases.
20. **Service `externalTrafficPolicy: Local`:** You have a Service of type `LoadBalancer`. What is the effect of setting `externalTrafficPolicy: Local`? What problem does it solve, and what is the major trade-off you must accept?
21. **Network Policy with `ipBlock`:** You create a NetworkPolicy that allows ingress from `ipBlock: 172.16.0.0/12`. A pod in the same cluster, with an IP in that range, tries to connect but is denied. Why does this happen, and what does it reveal about the scope of `ipBlock`?
22. **Dual-Stack Networking Challenges:** You are running a cluster in dual-stack (IPv4/IPv6) mode. An application pod is only getting an IPv6 address assigned, but its dependencies are only reachable via IPv4. What could be misconfigured, and how does the `ipFamilyPolicy` on a Service affect this?
23. **Ingress Path Routing Pitfalls:** You have two Ingress rules: one for `/api/v1` pointing to service `A`, and another for `/api/v1/users` pointing to service `B`. Requests to `/api/v1/users` are inconsistently routed. What is the likely cause, and how do most Ingress controllers handle path matching conflicts?
24. **SNAT and Source IP Preservation:** A pod needs to know the original source IP of an incoming external connection. By default, this source IP is lost due to SNAT. How can you configure a Service and the underlying cloud provider's load balancer to preserve the source IP?
25. **`topologyAwareHints` for Services:** Explain what `topologyAwareHints` on a Service does. In what scenario would this feature significantly improve performance or reduce cloud costs?
26. **Service Mesh Sidecar Injection Failure:** A pod is created but the service mesh sidecar container is not present. The pod's annotation is correct. What are the common points of failure in the mutating admission webhook process that handles injection?
27. **mTLS Handshake Failures:** After enabling mTLS in a service mesh, services that previously communicated now fail with TLS handshake errors. What are the most common causes (e.g., certificate issues, `DestinationRule` misconfigurations, `ServiceEntry` problems)?
28. **TCP vs. UDP Load Balancing:** You create a Service of type `LoadBalancer` for a UDP-based game server. Clients report connection issues and high latency. What are the unique challenges of load balancing UDP traffic in Kubernetes compared to TCP?
29. **CNI Plugin Upgrade Strategy:** Describe a zero-downtime strategy for upgrading the CNI plugin on a running production cluster. What are the risks, and how do you mitigate them?
30. **Direct Server Return (DSR):** Is DSR a feasible networking model for Kubernetes Services? Explain the concept, its benefits, and why it is extremely difficult to implement in a standard Kubernetes environment.

---

### Category 3: Scheduling, Autoscaling, and Performance (31-45)

31. **Advanced Node Affinity:** Design a strategy using node labels, taints, tolerations, and node affinity to schedule ML workloads (need GPU), databases (need NVMe), and web servers (prefer SSD) onto the appropriate nodes while maximizing utilization.
32. **Cluster Autoscaler (CA) Failure:** The CA reports it cannot scale up, with logs showing "0 un schedulable pods." However, you have several `Pending` pods. Why might the CA not see these pods as "unschedulable"?
33. **HPA vs. VPA vs. KEDA:** For a queue-processing worker whose traffic is spiky and correlated with a RabbitMQ queue length, compare and contrast using the HPA, VPA, and KEDA. Which is the best fit and why?
34. **QoS and Eviction Order:** A node is under memory pressure. Describe the exact order of pod eviction based on QoS classes. Explain how `requests` and `limits` determine a pod's QoS class.
35. **Descheduler Use Cases:** The Kubernetes scheduler is "optimistic" but not "proactive." What problems can arise from this over time? Describe two specific scenarios where you would use the Descheduler to rebalance the cluster.
36. **`PriorityClass` and Preemption:** A high-priority pod is `Pending`. The scheduler preempts a lower-priority pod to make room for it. Describe the step-by-step process the scheduler follows to select the victim pod(s) for preemption.
37. **`ResourceQuotas` vs. `LimitRanges`:** Explain the difference between these two objects. How would you use them together to enforce fair resource consumption and prevent a single team from monopolizing cluster resources in a shared namespace?
38. **Custom Scheduling Profiles:** You have a mix of latency-sensitive batch jobs and long-running services. How would you use custom scheduling profiles in the kube-scheduler to apply different filtering and scoring logic to these different workload types?
39. **HPA with Custom Metrics:** You need to scale a deployment based on the length of an Apache Kafka consumer lag. Describe the full stack of components required to make this work, from the metric collection to the HPA configuration.
40. **Pod Topology Spread Constraints:** You have a 3-zone cluster. A deployment has 6 replicas. They are all landing in two zones, leaving one empty. How would you use `TopologySpreadConstraints` to enforce a more even distribution, and what are the trade-offs with `maxSkew`?
41. **CPU Pinning and Static Policy:** For a low-latency network function virtualization (NFV) workload, you need to dedicate CPU cores to a pod and prevent the kubelet from moving them. Describe how to configure the kubelet's CPU manager policy and the pod's `resources` to achieve this.
42. **Pod Overhead:** You are running pods in a virtual Kubelet (like KubeVirt or Firecracker). The virtualization layer itself consumes resources. Explain the `podOverhead` field in a `RuntimeClass` and why it is critical for accurate scheduling in this scenario.
43. **`kubelet` Image Garbage Collection:** A node is running out of disk space. You check `/var/lib/containerd` and find thousands of old image layers. The `kubelet` is supposed to clean these up. Why might the garbage collection not be working, and how do you tune its thresholds?
44. **Performance Profiling a Pod:** An application in a pod is experiencing high CPU usage. How would you use tools like `pprof` (for Go) or `perf` to profile the application *inside* the running container without modifying the Dockerfile?
45. **Huge Pages Configuration:** A database application requires huge pages for performance. Describe the end-to-end process of configuring huge pages on the node OS and then requesting them in a pod spec.

---

### Category 4: State, Storage, and Security (46-60)

46. **StatefulSet Rolling Update:** Describe, step-by-step, what happens when you update a 3-replica StatefulSet managing a consensus database. What guarantees does the controller provide regarding identity, networking, and storage during this process?
47. **CSI Driver Architecture:** Explain the roles of the CSI Provisioner, Attacher, and Node Driver. How do they work together to go from a `PersistentVolumeClaim` to a mounted volume inside a pod?
48. **Beyond RBAC:** You need to prevent the creation of pods with `hostNetwork: true`. RBAC can't validate pod spec contents. What is the modern, recommended Kubernetes-native mechanism to enforce this, and how does it work?
49. **Secrets Management Strategy:** Design a robust strategy for managing secrets that avoids storing them in `etcd`. Your answer should cover secret injection into pods, rotation, and auditing.
50. **Volume Expansion Challenges:** You try to resize a `PVC` that is currently being used by a pod, but it fails. What are the potential reasons for this failure, involving the CSI driver, the `StorageClass`, and the `kubelet`?
51. **VolumeSnapshot and Restore Workflow:** A user accidentally deletes data in a database. You need to restore it from a previous snapshot. Describe the API objects (`VolumeSnapshot`, `VolumeSnapshotContent`) and the process the CSI controller follows to create a new PVC from the snapshot.
52. **`StorageClass` with `WaitForFirstConsumer`:** Explain the `volumeBindingMode: WaitForFirstConsumer` in a `StorageClass`. What problem does this solve, particularly in topologically-aware cloud environments?
53. **PodSecurityAdmission vs. PodSecurityPolicies:** `PodSecurityPolicies` are deprecated. Explain how the built-in `PodSecurityAdmission` replaces their functionality. How would you enforce a "baseline" policy for all namespaces in a cluster?
54. **OPA Gatekeeper Policy Writing:** You need to write a Gatekeeper policy that ensures all Ingress resources have a specific annotation for rate limiting. Outline the `ConstraintTemplate` and the `Constraint` you would create.
55. **ServiceAccount Token Security:** Describe the evolution of ServiceAccount tokens from long-lived secrets to short-lived, audience-bound tokens. Why was this change critical for cluster security, and how do you request a token with a specific audience?
56. **ImagePolicyWebhook:** Your organization requires all container images to be signed by a trusted authority. Describe how you would implement an `ImagePolicyWebhook` to enforce this at admission time.
57. **RuntimeClass for gVisor/Kata:** Explain what a `RuntimeClass` is. How would you use it to schedule a pod to run in gVisor for enhanced security, and what are the performance trade-offs?
58. **`seccomp` and `AppArmor` Profiles:** What are `seccomp` and `AppArmor`? How do they provide a deeper level of security than just dropping Linux capabilities in a pod spec? Provide an example of when you would use them.
59. **Rootless Container Runtimes:** What is the primary security benefit of running a container runtime like rootless Podman or containerd? What are the limitations of this approach, especially regarding networking and CNI plugins?
60. **Encrypting Specific etcd Keys:** Your compliance policy requires that `Secret` resources be encrypted at rest in `etcd`, but other objects can remain unencrypted. Describe how to configure the Kube-API Server with a KMS provider to achieve this selective encryption.

---

### Category 5: Architecture and Control Plane (61-75)

61. **GitOps and Drift Detection:** A developer manually scales a deployment. Argo CD now shows it as "OutOfSync." Explain the concept of "drift." What are the different ways Argo CD can handle this, and what are the operational trade-offs?
62. **Custom Resource Design:** You want to create a `Backup` CR that triggers a one-time backup of a `PVC`. Describe the `CRD` and outline the controller's reconciliation loop. What would the controller *do* when it sees a new `Backup` object?
63. **etcd Consistency and Recovery:** You suspect an `etcd` consistency problem in your 3-node HA cluster. Describe the Raft consensus algorithm at a high level. What would be your immediate steps to diagnose and potentially recover from a split-brain scenario?
64. **Multi-Cluster Service Discovery:** You have two clusters in different regions. An app in `us-east-1` needs to discover a DB in `us-west-2`. Discuss the challenges (CIDR overlap, latency, DNS) and outline two architectural patterns to solve this.
65. **API Server Aggregation Layer:** What is the purpose of the API server aggregation layer? How does it enable tools like the Prometheus Operator or the metrics-server to expose their own APIs without modifying the core Kubernetes codebase?
66. **`kube-controller-manager` Leader Election:** You have a 3-node control plane. How does the `kube-controller-manager` ensure that only one instance is active at a time? Describe the leader election process and what happens if the leader node disappears.
67. **`cloud-controller-manager`:** What is the purpose of the `cloud-controller-manager`? Why is it separated from the main `kube-controller-manager`, and what specific functionalities does it typically handle (e.g., for AWS, Azure, GCP)?
68. **etcd Backup and Restore Strategy:** Describe your strategy for performing regular, consistent backups of `etcd`. Outline the step-by-step process for restoring a control plane from one of these backups onto a new set of nodes.
69. **etcd Defragmentation:** Over time, `etcd` database files can become fragmented, leading to increased memory usage and slower performance. How do you trigger a defragmentation of the `etcd` database, and what operational risks are involved?
70. **Admission Webhook Timeouts:** Your `ValidatingWebhook` is configured with a 10-second timeout. It is occasionally failing, causing pod creation to be rejected. What are the implications of increasing the timeout? What is the difference between a webhook failing due to timeout vs. a non-2xx HTTP response?
71. **CRD Versioning and Conversion:** You have a CRD with versions `v1alpha1` and `v1beta1`. You want to introduce a breaking change in a new `v1` version. Explain how the CRD's `conversion` webhook works to allow the API server to serve all versions seamlessly.
72. **Building a Stateful Operator:** You are building an operator for a clustered database. What are the key design considerations for the controller's reconciliation loop when managing the state of a complex, multi-pod application?
73. **GitOps Tooling Comparison:** Compare and contrast Argo CD and Flux CD. What are the key architectural differences (e.g., pull vs. push model, CRD usage), and what might make you choose one over the other for a given project?
74. **API Server Audit Logging:** You need to implement a security-focused audit logging strategy. What are the key audit policy stages (`Metadata`, `Request`, `RequestResponse`), and how would you configure a policy to log every change to a `Secret` or `NetworkPolicy`?
75. **`kube-scheduler` Performance Tuning:** You are running a very large cluster (10,000+ nodes). The `kube-scheduler` is becoming a bottleneck. What are some configuration options and architectural patterns (e.g., multiple schedulers) you can use to improve its performance?

---

### Category 6: Service Mesh & Advanced Networking (76-90)

76. **mTLS Certificate Rotation:** In a service mesh like Istio, how are mTLS certificates automatically issued and rotated for all workloads? Describe the role of `istiod`/the control plane and the Envoy sidecar agent in this process.
77. **Envoy Filter Configuration:** You need to add a custom HTTP header to every response from a specific service. How would you achieve this using an `EnvoyFilter` in Istio? What is the risk of using such powerful, low-level filters?
78. **Traffic Mirroring for Canary Analysis:** You want to mirror 100% of live production traffic to a new version of your service for analysis without affecting users. How would you configure this in a service mesh, and what are the limitations of this approach?
79. **The "Thundering Herd" Problem with Retries:** A downstream service fails. All upstream services, configured with retries, immediately send a flood of retries, overwhelming the downstream service. How do modern service meshes help mitigate this problem?
80. **Distributed Tracing Implementation:** You have deployed Jaeger for tracing. What must your application do to participate in the trace? How does the service mesh (e.g., via Envoy proxies) automatically propagate tracing context (e.g., B3 headers) between services?
81. **Egress Gateway for Legacy Services:** Your application in the mesh needs to call an external, legacy API that uses IP whitelisting for security. How would you use an Egress Gateway to ensure all traffic to this API originates from a single, known IP address?
82. **Ingress Gateway vs. API Gateway:** What is the difference in function between a service mesh's Ingress Gateway and a dedicated API Gateway (like Kong or Ambassador)? When would you use one, the other, or both?
83. **Securing the Service Mesh Control Plane:** The service mesh control plane (e.g., `istiod`) is a critical component. How would you secure its communication with the data plane and protect it from unauthorized access?
84. **Multi-Cluster Service Mesh Federation:** You have two clusters and want to enable seamless service discovery and secure communication between them as if they were one. Describe the architecture of a multi-cluster service mesh (e.g., Istio multi-primary or primary-remote).
85. **Performance Impact of a Sidecar:** What is the performance overhead of injecting a sidecar proxy into every pod? Discuss the impact on latency, CPU, and memory, and how you can mitigate these costs.
86. **Debugging a Request Flow:** A user reports a 500 error. Using the service mesh's observability tools (metrics, logs, traces), describe your step-by-step process to trace the exact path of the failing request and identify the faulty component.
87. **WASM Filters in Envoy:** What is WebAssembly (WASM) in the context of a service mesh? What new capabilities does it unlock for customizing proxy logic compared to the traditional `EnvoyFilter`?
88. **Splitting Traffic Between Mesh Versions:** You are upgrading your service mesh from version 1.17 to 1.18. How would you perform a canary upgrade of the mesh control plane and data plane proxies with minimal disruption?
89. **Handling TCP Traffic in a Mesh:** Most service mesh features are optimized for HTTP/HTTPS. What are the limitations when handling raw TCP traffic? What L7-aware features are lost, and how do you configure routing for TCP services?
90. **Zero-Trust Networking with a Mesh:** Explain how a service mesh helps you implement a "zero-trust" network policy inside your cluster. How does this complement or replace Kubernetes Network Policies?

---

### Category 7: Observability & Telemetry (91-100)

91. **Prometheus at Scale:** You need to monitor a cluster with 1000+ services. Describe a high-availability Prometheus architecture (e.g., Thanos, Cortex) to solve the problems of scalability, long-term storage, and global query views.
92. **`kube-state-metrics` vs. Custom Metrics:** What is the purpose of `kube-state-metrics`? How does the data it provides differ from the metrics collected by the node exporter or custom metrics exposed by your application?
93. **OpenTelemetry Collector Architecture:** You are deploying the OpenTelemetry Collector. What are the different deployment modes (DaemonSet, Sidecar, Gateway), and what are the pros and cons of each for processing metrics, logs, and traces?
94. **Correlating the Three Pillars:** A user reports a slow request. You have metrics, logs, and traces. Describe the ideal workflow to correlate this single request across all three data sources to pinpoint the root cause.
95. **Centralized Logging Architecture:** Design a robust, scalable logging pipeline using Fluent Bit/Fluentd, Kafka, and Elasticsearch/OpenSearch. Why would you include a buffer like Kafka between the collectors and the storage backend?
96. **Alerting on SLOs:** You have defined an SLO: "99% of API p99 latency must be below 200ms over a rolling 30-day window." How would you translate this SLO into a concrete alerting system (e.g., using Prometheus and Alertmanager) that warns you when you are about to burn your error budget?
97. **`cAdvisor` Metrics:** What is `cAdvisor`, and what kind of metrics does it provide? How can you use its `container_fs_...` metrics to detect a pod that is writing to its filesystem excessively and might cause a node to run out of space?
98. **`eBPF` for Observability:** How can `eBPF`-based tools like Cilium/Pixie provide deeper network and system observability than traditional sidecar-based agents? What can you see with `eBPF` that is difficult or impossible to see otherwise?
99. **`kubectl debug` and Ephemeral Containers:** A pod is running in production and exhibiting a strange networking issue. You cannot `exec` into it because the container image doesn't have debugging tools. How would you use `kubectl debug` to attach an ephemeral container with `tcpdump` and `nslookup` to troubleshoot the live pod without restarting it?
100. **Profiling for Memory Leaks:** A Go application running in a pod is slowly increasing its memory usage over time, suggesting a leak. How would you use `pprof` to collect a heap profile from the running application and analyze it to find the source of the leak?
