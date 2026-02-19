## 📦 Repository Purpose

This repository is the **GitOps layer of the ClusterForge project**.

It is responsible for Kubernetes application deployment, ArgoCD configuration, and multi-environment (dev/prod) GitOps workflows across the EKS clusters provisioned by the `clusterforge-infra` repository.

In short:

- `clusterforge-infra` → Provisions VPC, IAM, and multi-environment EKS infrastructure using Terraform  
- `clusterforge-gitops` (this repo) → Deploys and manages applications on those clusters using ArgoCD and GitOps principles
