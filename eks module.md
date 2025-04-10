# EKS Terraform Module

This module deploys an Amazon EKS (Elastic Kubernetes Service) cluster using Terraform.

## Features

- VPC integration
- Worker groups with autoscaling
- IAM roles and security groups
- Supports managed and self-managed node groups

## Usage

```hcl
module "eks" {
  source = "../../modules/eks"
  cluster_name = "my-eks-cluster"
  vpc_id       = module.vpc.vpc_id
  subnet_ids   = module.vpc.private_subnet_ids
}
```

## Inputs

| Name           | Description                          | Type   | Required |
|----------------|--------------------------------------|--------|----------|
| `cluster_name` | EKS cluster name                     | string | yes      |
| `vpc_id`       | VPC ID                               | string | yes      |
| `subnet_ids`   | List of subnet IDs                   | list   | yes      |

## Outputs

| Name         | Description               |
|--------------|---------------------------|
| `cluster_id` | ID of the EKS cluster     |
| `kubeconfig` | Kubernetes config output  |