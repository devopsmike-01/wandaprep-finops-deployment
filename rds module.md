# RDS Terraform Module

This Terraform module provisions an Amazon RDS instance.

## Features

- Customizable instance type and engine
- Automated backups
- VPC security group integration
- Supports PostgreSQL, MySQL

## Usage

```hcl
module "rds" {
  source            = "../../modules/rds"
  engine            = "postgres"
  engine_version    = "14.1"
  instance_class    = "db.t3.micro"
  allocated_storage = 20
  db_name           = "mydb"
  username          = "admin"
  password          = "supersecure"
}
```

## Inputs

| Name               | Description                       | Type   | Required |
|--------------------|-----------------------------------|--------|----------|
| `engine`           | DB engine (postgres/mysql)        | string | yes      |
| `engine_version`   | Version of the engine             | string | yes      |
| `instance_class`   | RDS instance type                 | string | yes      |
| `allocated_storage`| Storage in GB                     | number | yes      |
| `db_name`          | Database name                     | string | yes      |
| `username`         | Master username                   | string | yes      |
| `password`         | Master password                   | string | yes      |

## Outputs

| Name         | Description            |
|--------------|------------------------|
| `endpoint`   | RDS endpoint URL       |
| `db_name`    | Name of the database   |