# 🚀 Deploying 10 Microservices on a Single Instance using EKS & Docker

## 📌 Overview
This project demonstrates how to deploy **10 microservices** on a single instance using **Amazon EKS (Elastic Kubernetes Service)** and **Docker**. The guide includes setting up the infrastructure, deploying the services, and ensuring scalability with Kubernetes.

## 🏗️ Architecture
- **EKS Cluster**: Managed Kubernetes cluster for container orchestration
- **Dockerized Microservices**: Each service is containerized using Docker
- **Kubernetes Deployments & Services**: Managing pods, scaling, and networking
- **Ingress Controller**: Handling external traffic
- **AWS Load Balancer**: Distributing traffic efficiently

## 📜 Prerequisites
Before proceeding, ensure you have the following:
- AWS account with IAM permissions
- AWS CLI installed & configured
- kubectl installed
- eksctl installed
- Docker installed
- Helm (for Ingress Controller)

## 🛠️ Setup & Deployment

### 1️⃣ **Clone the Repository**
```sh
 git clone https://github.com/Dev-World7/Micro.git
 cd Micro
```

### 2️⃣ **Create an EKS Cluster**
```sh
 eksctl create cluster --name microservices-cluster --region us-east-1 --nodegroup-name micro-nodes --nodes 2 --nodes-min 1 --nodes-max 3 --managed
```

### 3️⃣ **Build & Push Docker Images**
```sh
 cd services/service-1  # Repeat for other services
 docker build -t my-service-1 .
 docker tag my-service-1:latest <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/my-service-1:latest
 docker push <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/my-service-1:latest
```

### 4️⃣ **Deploy Microservices to EKS**
```sh
 kubectl apply -f k8s/deployments/
```

### 5️⃣ **Verify Deployments**
```sh
 kubectl get pods
 kubectl get services
```

### 6️⃣ **Set Up Ingress (Optional for External Access)**
```sh
 kubectl apply -f k8s/ingress.yaml
```

## 📊 Monitoring & Logging
- **Prometheus & Grafana** for metrics
- **Fluentd/Loki** for log aggregation

## 🎯 Future Enhancements
- Implement auto-scaling with HPA
- CI/CD pipeline with GitHub Actions & ArgoCD
- Service Mesh integration with Istio

## 🤝 Contributing
Feel free to fork and contribute! Open issues for suggestions.

## 📜 License
This project is licensed under the MIT License.

## 📞 Contact
For queries, reach out via [LinkedIn](https://www.linkedin.com/in/ml-vinith-4b2861122/) or [GitHub Issues](https://github.com/Dev-World7/Micro/issues).
