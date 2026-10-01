# AWS VPC Networking Project

## Objective

Build a custom AWS VPC with public and private subnets, configure Internet access, deploy EC2 instances, and validate secure access to a private EC2 instance through a public EC2 bastion host.

## Architecture

- Custom VPC
- Public subnet
- Private subnet
- Internet Gateway
- Route tables
- Public EC2 instance
- Private EC2 instance
- NAT Gateway
- SSH access through a bastion host

## What I Implemented

1. Created a custom VPC.
2. Created public and private subnets.
3. Attached an Internet Gateway to the VPC.
4. Configured separate route tables.
5. Launched one EC2 instance in the public subnet.
6. Launched one EC2 instance in the private subnet.
7. Connected to the public EC2 instance using SSH.
8. Used the public EC2 instance as a bastion host to access the private EC2 instance.
9. Configured NAT Gateway access for outbound Internet connectivity from the private subnet.

## Key Learning

This project helped demonstrate the difference between public and private subnets, routing through an Internet Gateway, outbound Internet access through a NAT Gateway, and secure administration of private EC2 instances using a bastion host.
