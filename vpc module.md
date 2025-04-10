# VPC Terraform Module

This Terraform module creates a customizable Virtual Private Cloud (VPC) in AWS, including subnets, route tables, NAT gateway, and more.

## Features

- Customizable VPC CIDR block
- Public, private, and optionally database subnets
- NAT Gateway with Elastic IP
- Route tables and associations
- Outputs for integration with other modules

## Usage

```hcl
module "vpc" {
  source           = "../../modules/vpc"
  name             = "dev-vpc"
  cidr             = "10.0.0.0/16"
  azs              = ["us-east-1a", "us-east-1b"]
  public_subnets   = ["10.0.1.0/24", "10.0.2.0/24"]
  private_subnets  = ["10.0.3.0/24", "10.0.4.0/24"]
  enable_nat_gateway = true
}
```

## Inputs

| Name              | Description                            | Type   | Default | Required |
|-------------------|----------------------------------------|--------|---------|----------|
| `name`            | Name prefix for resources              | string | n/a     | yes      |
| `cidr`            | CIDR block for the VPC                 | string | n/a     | yes      |
| `azs`             | List of availability zones             | list   | n/a     | yes      |
| `public_subnets`  | List of public subnet CIDRs           | list   | n/a     | yes      |
| `private_subnets` | List of private subnet CIDRs          | list   | n/a     | yes      |
| `enable_nat_gateway` | Enable NAT Gateway                   | bool   | false   | no       |

## Outputs

| Name       | Description            |
|------------|------------------------|
| `vpc_id`   | ID of the created VPC  |
| `subnet_ids` | List of subnet IDs   |