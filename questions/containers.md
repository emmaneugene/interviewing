### Questions
---

### **I. General Container Concepts & Fundamentals**

1.  **Explain the fundamental difference between containers and virtual machines (VMs).**
    *   *Follow-up:* What are the advantages and disadvantages of each? When would you choose one over the other?
2.  **What problem do containers solve in software development and deployment?**
    *   *Follow-up:* How do they achieve "immutable infrastructure"?
3.  **Distinguish between a Docker image and a Docker container.**
4.  **What is a container registry? Give an example.**
5.  **Explain the concept of container orchestration. Why is it necessary?**

---

### **II. Docker Specific Questions**

1.  **Explain the purpose of a Dockerfile. What are some common instructions you'd find in one?**
    *   *Follow-up:* Describe the `COPY` vs `ADD` instructions.
    *   *Follow-up:* What is the `CMD` instruction vs `ENTRYPOINT`? When would you use each?
2.  **How do you build a Docker image? How do you run a container from an image?**
    *   *Follow-up:* How do you map ports between a host and a container?
3.  **What are Docker volumes, and why are they important?**
    *   *Follow-up:* Explain bind mounts vs named volumes. When would you use each?
4.  **Explain Docker networking modes (e.g., bridge, host, none). When would you use a bridge network versus a host network?**
5.  **How can you inspect a running Docker container (e.g., its logs, processes, network configuration)?**
6.  **What is Docker Compose, and what problem does it solve?**
    *   *Follow-up:* Describe a typical `docker-compose.yml` file structure.
7.  **How can you reduce the size of a Docker image? (Think about multi-stage builds).**
    *   *Follow-up:* Why is image size important?
8.  **What are Docker layers? How do they impact image size and build efficiency?**
9.  **Describe the Docker daemon and the Docker client.**
10. **How would you troubleshoot a Docker container that fails to start or crashes immediately?**

---

### **III. Kubernetes Specific Questions**

1.  **What is Kubernetes, and what problem does it solve?**
2.  **Explain the core components of a Kubernetes cluster (Master/Control Plane and Worker Nodes) and their respective roles.**
    *   *Control Plane Components:* kube-apiserver, etcd, kube-scheduler, kube-controller-manager, cloud-controller-manager (if applicable).
    *   *Node Components:* kubelet, kube-proxy, container runtime.
3.  **What is a Pod in Kubernetes? Can a Pod contain multiple containers? If so, why would you do that?**
    *   *Follow-up:* What are sidecar containers? Give an example.
4.  **Explain the difference between a Deployment, ReplicaSet, and Pod.**
5.  **What is a Service in Kubernetes, and what are its different types? (ClusterIP, NodePort, LoadBalancer, ExternalName). When would you use each?**
6.  **When would you use an Ingress resource? How does it differ from a Service?**
7.  **How does Kubernetes handle persistent storage? Explain Persistent Volumes (PV) and Persistent Volume Claims (PVC).**
    *   *Follow-up:* What are Storage Classes?
8.  **What are ConfigMaps and Secrets, and why are they used? How do they differ in terms of usage?**
9.  **Explain liveness and readiness probes. Why are they crucial for application health and availability in Kubernetes?**
10. **How do you expose an application running in Kubernetes to the outside world?**
11. **Describe the purpose of `kubectl` and some common commands you use.**
12. **What is a DaemonSet, and when would you use it?**
13. **What is a StatefulSet, and when would you use it instead of a Deployment?**
14. **How would you perform a rolling update and a rollback in Kubernetes?**
15. **What is Helm, and how does it relate to Kubernetes?**
16. **How does Kubernetes networking typically work (e.g., CNI plugins)?**
17. **Explain Namespaces in Kubernetes. Why are they useful?**
18. **How do you monitor logs and metrics for applications running in Kubernetes?**

---

### **IV. Troubleshooting & Best Practices**

1.  **What are some common challenges you've faced when working with containers, and how did you overcome them?**
2.  **How do you handle logging and monitoring for containerized applications?**
3.  **What security considerations should you keep in mind when building and running containers?**
    *   *Follow-up:* Discuss concepts like rootless containers, scanning for vulnerabilities, minimizing image attack surface.
4.  **How do you ensure your containerized applications are performant and resource-efficient?**
    *   *Follow-up:* Discuss resource limits/requests in Kubernetes.
5.  **How do containers fit into a CI/CD pipeline? Describe a typical workflow.**
6.  **What strategies do you use for versioning and managing container images?**

---

### **V. Scenario & Design Questions**

1.  **You have a traditional web application (e.g., a Python Flask API, a Node.js frontend, and a PostgreSQL database). Describe how you would containerize it using Docker and then deploy it to Kubernetes.**
    *   *Consider:* Dockerfiles, Docker Compose (for local dev), K8s Deployments, Services, Persistent Volumes, ConfigMaps, Ingress.
2.  **Your Kubernetes pod is constantly crashing. What are your troubleshooting steps?**
3.  **You need to run a batch job that processes a large file periodically. How would you design this in Kubernetes?**
    *   *Hint:* CronJobs, Jobs.
4.  **Describe a scenario where you would use a Kubernetes Network Policy.**
5.  **How would you ensure high availability and disaster recovery for your applications running on Kubernetes?**
6.  **A team is complaining that their application deployed to Kubernetes is slow. How would you start investigating?**
