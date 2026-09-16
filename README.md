# AWS VPC Terraform module

This is a Terraform module which creates VPC resources on AWS.

These types of resources are supported:

- VPC
- Subnet
- Route
- Route table
- Internet Gateway
- NAT Gateway
- VPN Gateway
- VPC Endpoint (S3 and DynamoDB)
- RDS DB Subnet Group
- ElastiCache Subnet Group
- DHCP Options Set

## Usage

```hcl
module "vpc" {
  source = "github.com/collinsefe/aws_vpc_create"

  name = "my-vpc"
  cidr = "10.0.0.0/16"

  azs             = ["eu-west-1a", "eu-west-1b", "eu-west-1c"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24", "10.0.103.0/24"]

  enable_nat_gateway = true
  enable_vpn_gateway = true

  tags = {
    Terraform   = "true"
    Environment = "dev"
  }
}
```

See [`examples/basic`](examples/basic) for a runnable example.

## Requirements

This module is written in Terraform 0.11 syntax (see [`versions.tf`](versions.tf)) and requires an `aws` provider configured by the caller.

## Inputs and outputs

See [`variables.tf`](variables.tf) for all supported inputs and [`outputs.tf`](outputs.tf) for all exported outputs.
