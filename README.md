\# Cloud Native GitOps Platform using Kubernetes, ArgoCD, Helm and Prometheus



\## Project Overview



This project demonstrates a complete cloud-native DevOps platform using Kubernetes, GitOps, Helm, monitoring, autoscaling, and RBAC security controls.



The platform automates Kubernetes deployments using ArgoCD and GitHub integration while providing monitoring and observability using Prometheus and Grafana.



\---



\## Architecture



GitHub → ArgoCD → Kubernetes → Helm → Monitoring Stack



Components:

\- GitHub for source control

\- ArgoCD for GitOps continuous delivery

\- Kubernetes for container orchestration

\- Helm for package management

\- Prometheus for monitoring

\- Grafana for visualization

\- HPA for autoscaling

\- RBAC for access control



\---



\## Tools \& Technologies Used



| Tool | Purpose |

|------|----------|

| Docker | Containerization |

| Kubernetes | Container orchestration |

| Minikube | Local Kubernetes cluster |

| kubectl | Kubernetes CLI |

| Helm | Kubernetes package manager |

| ArgoCD | GitOps continuous delivery |

| GitHub | Source code management |

| Prometheus | Monitoring and metrics |

| Grafana | Dashboard visualization |

| HPA | Horizontal Pod Autoscaling |

| RBAC | Access management |



\---



\## Features Implemented



\### Kubernetes Deployment

\- NGINX deployment

\- Kubernetes services

\- Pod management

\- Namespace management



\### GitOps using ArgoCD

\- GitHub integration

\- Automatic synchronization

\- Declarative deployments

\- Continuous delivery workflow



\### Helm Charts

\- Helm chart creation

\- values.yaml configuration

\- Helm upgrade and scaling

\- Reusable deployment templates



\### Monitoring Stack

\- Prometheus installation

\- Grafana dashboards

\- Alertmanager setup

\- Node Exporter metrics



\### Autoscaling

\- Metrics Server

\- Horizontal Pod Autoscaler (HPA)

\- CPU-based scaling from 2 to 8 replicas



\### Security

\- RBAC configuration

\- Role and RoleBinding

\- Staging and Production namespaces



\---



\## Project Structure



```bash

k8s-gitops-config/

│

├── nginx-deployment.yaml

├── rbac.yaml

├── README.md

│

└── nginx-chart/

&#x20;   ├── Chart.yaml

&#x20;   ├── values.yaml

&#x20;   └── templates/

```



\---



\## Deployment Steps



\### 1. Start Minikube



```bash

minikube start

```



\### 2. Deploy NGINX



```bash

kubectl create deployment nginx --image=nginx

kubectl expose deployment nginx --port=80 --type=NodePort

```



\### 3. Install ArgoCD



```bash

kubectl create namespace argocd



kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

```



\### 4. Install Helm Chart



```bash

helm create nginx-chart

helm install nginx-release .

```



\### 5. Enable Metrics Server



```bash

minikube addons enable metrics-server

```



\### 6. Configure HPA



```bash

kubectl autoscale deployment nginx --cpu-percent=50 --min=2 --max=8

```



\### 7. Install Monitoring Stack



```bash

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts



helm repo update



helm install monitoring prometheus-community/kube-prometheus-stack

```



\---



\## Verification Commands



\### Check Pods



```bash

kubectl get pods

```



\### Check HPA



```bash

kubectl get hpa

```



\### Check Namespaces



```bash

kubectl get namespaces

```



\### Check Metrics



```bash

kubectl top nodes

```



\---



\## Screenshots



Add screenshots for:

\- ArgoCD Dashboard

\- Grafana Dashboard

\- Kubernetes Pods

\- HPA Autoscaling

\- GitHub Repository

\- Helm Deployment



\---



\## GitOps Workflow



1\. Developer pushes code to GitHub

2\. ArgoCD detects repository changes

3\. Kubernetes manifests sync automatically

4\. Application deploys automatically

5\. Monitoring stack tracks cluster metrics



\---



\## Learning Outcomes



\- Kubernetes administration

\- GitOps workflow implementation

\- Helm chart management

\- Monitoring and observability

\- Autoscaling configuration

\- RBAC security implementation

\- DevOps automation



\---



\## Future Improvements



\- Multi-microservice architecture

\- CI/CD pipeline integration

\- Ingress controller setup

\- SSL/TLS configuration

\- Advanced alert rules

\- Production cloud deployment



\---



\## Author



Aarya Sawant



