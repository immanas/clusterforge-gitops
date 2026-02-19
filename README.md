## 📦 Repository Purpose:

This repository is the **GitOps layer of the ClusterForge project**.

It is responsible for Kubernetes application deployment, ArgoCD configuration, and multi-environment (dev/prod) GitOps workflows across the EKS clusters provisioned by the `clusterforge-infra` repository.

In short:

- `clusterforge-infra` → Provisions VPC, IAM, and multi-environment EKS infrastructure using Terraform  
- `clusterforge-gitops` (this repo) → Deploys and manages applications on those clusters using ArgoCD and GitOps principles


## 📌 Recommended Reading Order

This repository is part of the larger **ClusterForge platform**.

To fully understand how everything connects, follow this order:

1️⃣ **Start here (Infrastructure Layer)**  
🔗 https://github.com/immanas/clusterforge-infra 
## 📂 ClusterForge GitOps – Folder Structure:
```
clusterforge-gitops/
│
├── .github/
│   └── workflows/
│       └── ci.yml                # CI pipeline (YAML validation / linting)
│
├── apps/
│   └── nginx/
│       ├── deployment.yaml       # Kubernetes Deployment
│       ├── service.yaml          # Kubernetes Service
│       ├── hpa.yaml              # Horizontal Pod Autoscaler
│       ├── namespace.yaml        # Namespace definition
│       └── kustomization.yaml    # Base app configuration (optional but recommended)
│
├── environments/
│   ├── dev/
│   │   ├── app.yaml              # ArgoCD Application manifest (dev cluster)
│   │   └── kustomization.yaml    # Dev-specific overrides
│   │
│   └── prod/
│       ├── app.yaml              # ArgoCD Application manifest (prod cluster)
│       └── kustomization.yaml    # Prod-specific overrides
│
├── LICENSE
├── README.md
└── .gitignore
```
## 🔗 How Both Repositories Connect

- `clusterforge-infra` creates the EKS clusters.
- ArgoCD is installed on the control cluster.
- This repository defines how applications are deployed to dev and prod clusters.
- Git becomes the single source of truth for application state.

Together, they form a complete end-to-end DevOps platform.
