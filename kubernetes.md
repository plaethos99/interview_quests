


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

Alright, I'm ready. Which question would you like to tackle first?
