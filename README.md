# Azure AKS Terraform Infrastructure

Production-grade Azure Kubernetes Service (AKS) infrastructure deployed with Terraform, showcasing modern DevOps practices and cloud-native architecture.

## 🎯 Project Overview

This project demonstrates the deployment of a complete Azure infrastructure for running containerized applications on Kubernetes, following infrastructure-as-code best practices.

### What's Included

- **Networking Layer**: Azure Virtual Network with subnets, NSGs, and proper segmentation
- **Container Registry**: Azure Container Registry (ACR) for Docker images
- **Kubernetes Cluster**: Azure Kubernetes Service (AKS) with managed control plane
- **Storage**: Azure Storage Account for Terraform remote state
- **Security**: Network isolation, RBAC, and Azure security best practices

## 🏗️ Architecture
```
Azure Resource Group
├── Virtual Network (10.0.0.0/16)
│   ├── AKS Subnet (10.0.1.0/24)
│   ├── Services Subnet (10.0.2.0/24)
│   └── Network Security Groups
├── Azure Container Registry
├── AKS Cluster
│   ├── System Node Pool
│   └── User Node Pool
└── Storage Account (Terraform State)
```

Detailed architecture diagram: [docs/architecture.md](docs/architecture.md)

## 🛠️ Tech Stack

- **Infrastructure as Code**: Terraform (modular design)
- **Cloud Provider**: Microsoft Azure
- **Container Orchestration**: Azure Kubernetes Service (AKS)
- **Container Registry**: Azure Container Registry (ACR)
- **Version Control**: Git / GitHub
- **CI/CD**: GitHub Actions (coming soon)

## 📋 Prerequisites

- Azure CLI (`az`) installed and authenticated
- Terraform >= 1.14
- kubectl >= 1.34
- An active Azure subscription
- Git

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone git@github.com:LeonTH096/azure-aks-terraform-infra.git
cd azure-aks-terraform-infra
```

### 2. Configure Azure Authentication
```bash
az login
az account set --subscription "YOUR_SUBSCRIPTION_ID"
```

### 3. Initialize Terraform
```bash
cd terraform/environments/dev
terraform init
```

### 4. Plan and Apply
```bash
# Review the plan
terraform plan

# Apply the infrastructure
terraform apply
```

### 5. Configure kubectl
```bash
az aks get-credentials --resource-group <rg-name> --name <aks-name>
kubectl get nodes
```

## 📁 Project Structure
```
azure-aks-terraform-infra/
├── terraform/
│   ├── modules/              # Reusable Terraform modules
│   │   ├── networking/       # VNet, Subnets, NSGs
│   │   ├── acr/             # Azure Container Registry
│   │   ├── aks/             # AKS cluster configuration
│   │   └── storage/         # Storage account for state
│   └── environments/
│       └── dev/             # Development environment
│           ├── main.tf
│           ├── variables.tf
│           ├── terraform.tfvars
│           └── backend.tf
├── kubernetes/
│   └── manifests/           # Kubernetes YAML manifests
├── docs/
│   └── architecture.md      # Detailed architecture docs
└── README.md
```

## 🗺️ Development Roadmap

### Phase 1: Foundation ✅ (In Progress)
- [x] Project structure
- [ ] Networking module (VNet, Subnets, NSGs)
- [ ] Storage module (Remote state)
- [ ] Remote state configuration

### Phase 2: Container Infrastructure
- [ ] Azure Container Registry module
- [ ] AKS cluster module
- [ ] Integration testing

### Phase 3: Application Layer
- [ ] Sample microservices deployment
- [ ] Ingress controller (NGINX)
- [ ] Monitoring setup (Prometheus/Grafana)

### Phase 4: Automation
- [ ] GitHub Actions CI/CD pipeline
- [ ] Terraform validation workflow
- [ ] Security scanning

## 📚 Documentation

- [Architecture Overview](docs/architecture.md)
- Module documentation in respective `README.md` files
- Variables documented in `variables.tf` with descriptions

## 🔒 Security Considerations

- Network segmentation with dedicated subnets
- Network Security Groups for traffic control
- Azure RBAC for access management
- Private endpoint for ACR (optional)
- AKS security best practices

## 💰 Cost Estimation

Estimated monthly cost for dev environment: ~€100-150 EUR/month
- AKS cluster (B-series VMs): ~€70
- Azure Container Registry (Basic): ~€5
- Networking & Storage: ~€20-25

> **Note**: Costs vary by region and usage. Always check Azure pricing calculator.

## 🤝 Contributing

This is a portfolio project, but suggestions and improvements are welcome!

## 📝 License

MIT License - See [LICENSE](LICENSE) file for details

## 👤 Author

**Leonardo Colangelo**
- GitHub: [@LeonTH096](https://github.com/LeonTH096)
- LinkedIn: [leonardocolangelo](https://linkedin.com/in/leonardocolangelo)
- Location: Torino, Italy

---

⭐ If you find this project useful, please give it a star!
