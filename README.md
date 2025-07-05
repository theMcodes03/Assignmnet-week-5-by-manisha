# Week 5 Assignment - Kubernetes & AKS Essentials 

This week’s journey was all about understanding the orchestration of containers using Kubernetes—on local machines, cloud environments, and enterprise-scale clusters. I explored setting up clusters, managing roles, deploying applications, and exposing services through multiple methods.

---

## Tasks Completed:

### [Create a Kubernetes cluster using Minikube](task1.md)
> **Summary**: Set up a local single-node Kubernetes cluster using Minikube. This task helped me understand the fundamentals of cluster creation and interaction with `kubectl` on a developer machine. I learned how to create, delete, and manage clusters, as well as how to use `kubectl' to interact with the cluster. I also explored the Kubernetes dashboard and how to access it. This hands-on experience allowed me to grasp the basics of Kubernetes and its command-line interface. 

---

### [Create a Kubernetes cluster using Kubeadm](task2.md)
> **Summary**: Built a Kubernetes cluster from scratch using `kubeadm` on AWS EC2 instances. This gave hands-on experience with a more production-like cluster setup, understanding control plane and worker nodes manually. I also learned about the importance of networking and how to configure it for our cluster. This task deepened my understanding of cluster setup and configuration, especially in a cloud environment. 

---

### [Deploy an AKS cluster using the portal & manage access](task3.md)
> **Summary**: Deployed Azure Kubernetes Service (AKS) using the Azure Portal. I accessed the K8s dashboard, then created roles and role bindings to allow multi-user access and apply RBAC policies. This hands-on experience with AKS and Azure RBAC helped us understand how to manage access and roles in a cloud-based Kubernetes environment. I also learned about the importance of role-based access control (RBAC) in securing our clusters.

---

### [Deploy a microservice on AKS and access it via public internet](task4.md)
> **Summary**: Pushed a Dockerized Flask microservice to Docker Hub, deployed it on AKS, and exposed it to the internet using a LoadBalancer. This demonstrated cloud-native deployment and service exposure. I also explored how to access our service from outside the cluster using the LoadBalancer's public IP address. This hands-on experience with AKS and service exposure helped me understand how to deploy and expose services in a cloud environment. 

---

### [Expose services in the cluster with NodePort, ClusterIP, LoadBalancer](task5.md)
> **Summary**: Explored different ways to expose Kubernetes services—internally using `ClusterIP`, locally using `NodePort`, and publicly using `LoadBalancer`. This task was key to understanding how services are made reachable. I also learned about the differences between these methods and how to choose the right one based on our needs. This hands-on experience helped solidify our understanding of service exposure in a Kubernetes cluster. 

---

## Key Learnings:
- Differentiated between local, semi-managed, and fully managed Kubernetes setups.
- Understood `kubectl`, `kubeadm`, and cloud-native tooling.
- Learned to secure and expose workloads using best practices.
- Worked with real-world deployment pipelines using Docker and Kubernetes.

---

>  _Each linked file contains the screenshots, commands used, explanations, and outcomes for respective tasks._

