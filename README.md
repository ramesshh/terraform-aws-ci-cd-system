# CI-CD system on AWS ECS Fargate

Test Continuous Integration/Delivery environment on AWS ECS.

[![CircleCI](https://circleci.com/gh/cn-terraform/terraform-aws-ci-cd-system/tree/master.svg?style=svg)](https://circleci.com/gh/cn-terraform/terraform-aws-ci-cd-system/tree/master)
[![](https://img.shields.io/github/license/cn-terraform/terraform-aws-ci-cd-system)](https://github.com/cn-terraform/terraform-aws-ci-cd-system)
[![](https://img.shields.io/github/issues/cn-terraform/terraform-aws-ci-cd-system)](https://github.com/cn-terraform/terraform-aws-ci-cd-system)
[![](https://img.shields.io/github/issues-closed/cn-terraform/terraform-aws-ci-cd-system)](https://github.com/cn-terraform/terraform-aws-ci-cd-system)
[![](https://img.shields.io/github/languages/code-size/cn-terraform/terraform-aws-ci-cd-system)](https://github.com/cn-terraform/terraform-aws-ci-cd-system)
[![](https://img.shields.io/github/repo-size/cn-terraform/terraform-aws-ci-cd-system)](https://github.com/cn-terraform/terraform-aws-ci-cd-system)

## Tools included

* Jenkins
    - Source Code: <https://github.com/cn-terraform/terraform-aws-jenkins>
    - Terraform Module: <https://registry.terraform.io/modules/cn-terraform/jenkins/aws>
* SonarQube
    - Source Code: <https://github.com/cn-terraform/terraform-aws-sonarqube>
    - Terraform Module: <https://registry.terraform.io/modules/cn-terraform/sonarqube/aws>

## Use this code as a Terraform module

Check valid versions on:
* Github Releases: <https://github.com/cn-terraform/terraform-aws-ci-cd-system/releases>
* Terraform Module Registry: <https://registry.terraform.io/modules/cn-terraform/ci-cd-system/aws>

        module "ci-cd" {
            source         = "cn-terraform/ci-cd-system/aws"
            version        = "1.0.0-beta.4"
            name_preffix   = "cicd"
            profile        = "aws_profile"
            region         = "us-east-1"   
            vpc_cidr_block = "192.168.0.0/16"
            availability_zones                          = [ "us-east-1a", "us-east-1b", "us-east-1c", "us-east-1d" ]
            public_subnets_cidrs_per_availability_zone  = [ "192.168.0.0/19", "192.168.32.0/19", "192.168.64.0/19", "192.168.96.0/19" ]
            private_subnets_cidrs_per_availability_zone = [ "192.168.128.0/19", "192.168.160.0/19", "192.168.192.0/19", "192.168.224.0/19" ]
        }

## Deploy CI/CD Infrastructure standalone

1. Clone this repository.

2. To download required plugins and modules run:

        terraform init

3. To update dependencies run:

        terraform get --update

4. To plan a deployment and check what is going to change run:

        terraform plan

5. To deploy changes run:

        terraform apply
