# AWS Solutions Architect Hands-On Portfolio

Hands-on AWS infrastructure projects developed while preparing for the AWS Certified Solutions Architect – Associate certification.

This repository documents practical AWS implementations, architecture design, troubleshooting, and cloud networking exercises.

## About Me

I am a PMP-certified Telecom/IT Project Manager with a background in computer networks, telecom operations, and infrastructure projects.

I am currently expanding my career toward Cloud and Solution Engineering, with a focus on AWS architecture, networking, automation, and scalable infrastructure.

## What This Repository Demonstrates

- AWS infrastructure deployment
- Cloud networking
- EC2 administration
- IAM and access control
- Load balancing
- Auto Scaling
- Route 53 and DNS
- High availability
- Public and private subnet design
- NAT Gateway configuration
- SSH and bastion-host access
- Troubleshooting and root-cause analysis

## Projects

| Project | Description | AWS Services |
|---|---|---|
| [VPC Networking](./08-vpc-networking/) | Custom VPC with public/private subnets, bastion access, NAT Gateway, and troubleshooting | VPC, EC2, IGW, NAT Gateway, Route Tables |
| [Application Load Balancer](./05-load-balancing/) | Multi-AZ web application behind an Application Load Balancer | EC2, ALB, Target Groups, Security Groups |
| IAM Security | Identity, permissions, CLI access, roles, and policies | IAM, AWS CLI |
| EC2 Compute | Linux and Windows EC2 deployment and administration | EC2, Security Groups |
| EC2 Storage & AMI | EBS, S3 integration, IAM roles, and reusable AMIs | EC2, EBS, S3, IAM |
| Auto Scaling | Elastic web architecture with automatic instance scaling | EC2, ASG, CloudWatch |
| Route 53 & HTTPS | DNS, custom domain, ALB integration, and TLS | Route 53, ACM, ALB |

## Featured Project: AWS VPC Networking

The VPC project demonstrates a complete public/private subnet architecture.

```text
                         Internet
                            |
                            v
                     Internet Gateway
                            |
              +-------------+-------------+
              |                           |
              v                           v
        Public Subnet                Private Subnet
              |                           |
       +------+------                     |
       |             |                    |
       v             v                    v
   Public EC2    NAT Gateway          Private EC2
   Bastion Host                           |
       |                                  |
       +----------- SSH ----------------->+
```

Key implementation areas:

- Custom VPC
- Public and private subnets
- Internet Gateway
- Separate route tables
- Bastion-host SSH access
- Private EC2 administration
- NAT Gateway
- Outbound Internet access from private subnet
- SSH key mismatch troubleshooting

## Featured Project: Application Load Balancer

```text
                    Internet
                       |
                       v
              Application Load
                 Balancer
                 /      \
                /        \
               v          v
            EC2-A       EC2-B
             AZ-1        AZ-2
```

Key implementation areas:

- Multi-AZ deployment
- EC2 Launch Templates
- Target Groups
- Health checks
- ALB listeners
- Security Groups
- Route 53
- Sticky sessions
- Path-based routing
- Troubleshooting ALB connectivity

## Troubleshooting Approach

The repository also documents issues encountered during the labs, including:

- SSH authentication failure caused by using the wrong EC2 key pair
- ALB connectivity failure caused by an incorrect Security Group
- Availability Zone configuration mismatch
- Private subnet Internet access and routing issues

The troubleshooting sections focus on:

```text
Symptom
   |
Investigation
   |
Root Cause
   |
Resolution
   |
Lesson Learned
```

## AWS Skills

- Amazon EC2
- Amazon VPC
- IAM
- Application Load Balancer
- Auto Scaling Groups
- Elastic Block Store
- Amazon S3
- Route 53
- AWS Certificate Manager
- NAT Gateway
- Internet Gateway
- Security Groups
- AWS CLI
- EC2 User Data
- IMDSv2

## Current Focus

Continuing AWS Solutions Architect Associate preparation and expanding these projects toward:

- Infrastructure as Code
- Terraform
- CloudFormation
- Deployment automation
- CI/CD
- Monitoring and logging

## Disclaimer

This repository contains my own implementation notes, architecture, scripts, screenshots, and troubleshooting experience.

Course slides and copyrighted training material are not redistributed here.
