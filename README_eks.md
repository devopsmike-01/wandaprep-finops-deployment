# EKS Terraform Module

## Description
Reusable Terraform module to provision an Amazon EKS Cluster with managed node groups.

## Usage
```hcl
module "eks" {
  source          = "../../modules/eks"
  cluster_name    = "finops-eks-cluster"
  cluster_version = "1.27"
  vpc_id          = modutry
  node_group_name = "finops-node-group"
  desired_capacity = 2
  max_size         = 4
  min_size         = 1
  instance_types   = ["t3.medium"]
}
```

## Inputs

| Name              | Type    | Description                             | Default |
|-------------------|---------|-----------------------------------------|---------|
| cluster_name      | string  | Name of the EKS cluster                 | n/a     |
| cluster_version   | string  | Kubernetes version                      | "1.27"  |
| vpc_id            | string  | VPC ID where EKS will be deployed       | n/a     |
| subnet_ids        | list    | List of subnet IDs                      | n/a     |
| node_group_name   | string  | Name of the EKS node group              | n/a     |
| desired_capacity  | number  | Desired number of worker nodes          | 2       |
| max_size          | number  | Maximum number of nodes                 | 4       |
| min_size          | number  | Minimum number of nodes                 | 1       |
| instance_types    | list    | EC2 instance types for the worker nodes | ["t3.medium"] |

## Outputs

| Name              | Description                      |
|-------------------|----------------------------------|
| cluster_name      | EKS Cluster name                 |
| cluster_endpoint  | Endpoint of the EKS cluster      |
| kubeconfig        | Kubeconfig file for the cluster  |
| node_group_role_arn | IAM Role ARN of node group     |
