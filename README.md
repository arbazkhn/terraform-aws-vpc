# AWS VPC Terraform module

Terraform module which creates VPC resources on AWS.

These types of resources are supported:

* [VPC](https://www.terraform.io/docs/providers/aws/r/vpc.html)
* [Subnet](https://www.terraform.io/docs/providers/aws/r/subnet.html)
* [Route](https://www.terraform.io/docs/providers/aws/r/route.html)
* [Route table](https://www.terraform.io/docs/providers/aws/r/route_table.html)
* [Internet Gateway](https://www.terraform.io/docs/providers/aws/r/internet_gateway.html)
* [Network ACL](https://www.terraform.io/docs/providers/aws/r/network_acl.html)
* [NAT Gateway](https://www.terraform.io/docs/providers/aws/r/nat_gateway.html)
* [VPN Gateway](https://www.terraform.io/docs/providers/aws/r/vpn_gateway.html)
* [VPC Flow Log](https://www.terraform.io/docs/providers/aws/r/flow_log.html)
* [VPC Endpoint](https://www.terraform.io/docs/providers/aws/r/vpc_endpoint.html):
  * Gateway: S3, DynamoDB
  * Interface: EC2, SSM, EC2 Messages, SSM Messages, SQS, ECR API, ECR DKR, API Gateway, KMS,
ECS, ECS Agent, ECS Telemetry, SES, SNS, STS, Glue, CloudWatch(Monitoring, Logs, Events),
Elastic Load Balancing, CloudTrail, Secrets Manager, Config, Codeartifact(API, Repositories), CodeBuild, CodeCommit,
Git-Codecommit, Textract, Transfer Server, Kinesis Streams, Kinesis Firehose, SageMaker(Notebook, Runtime, API),
CloudFormation, CodePipeline, Storage Gateway, AppMesh, Transfer, Service Catalog, AppStream API, AppStream Streaming,
Athena, Rekognition, Elastic File System (EFS), Cloud Directory, Elastic Beanstalk (+ Health), Elastic Map Reduce(EMR),
DataSync, EBS, SMS, Elastic Inference Runtime, QLDB Session, Step Functions, Access Analyzer, Auto Scaling Plans,
Application Auto Scaling, Workspaces, ACM PCA, RDS, CodeDeploy, CodeDeploy Commands Secure

* [RDS DB Subnet Group](https://www.terraform.io/docs/providers/aws/r/db_subnet_group.html)
* [ElastiCache Subnet Group](https://www.terraform.io/docs/providers/aws/r/elasticache_subnet_group.html)
* [Redshift Subnet Group](https://www.terraform.io/docs/providers/aws/r/redshift_subnet_group.html)
* [DHCP Options Set](https://www.terraform.io/docs/providers/aws/r/vpc_dhcp_options.html)
* [Default VPC](https://www.terraform.io/docs/providers/aws/r/default_vpc.html)
* [Default Network ACL](https://www.terraform.io/docs/providers/aws/r/default_network_acl.html)

## Terraform versions

Terraform 0.12 and newer. Pin module version to `~> v2.0`. Submit pull-requests to `master` branch.

Terraform 0.11. Pin module version to `~> v1.0`. Submit pull-requests to `terraform011` branch.

## Usage

```hcl
module "vpc" {
  source = "terraform-aws-modules/vpc/aws"

  name = "my-vpc"
  cidr = "10.0.0.0/16"

  azs             = ["eu-west-1a", "eu-west-1b", "eu-west-1c"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24", "10.0.103.0/24"]

  enable_nat_gateway = true
  enable_vpn_gateway = true

  tags = {
    Terraform = "true"
    Environment = "dev"
  }
}
```