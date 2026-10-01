# AWS VPC Networking Project

## Objective

Build a custom AWS VPC with public and private subnets, configure secure administrative access to a private EC2 instance through a public bastion host, and provide outbound Internet access to the private subnet using a NAT Gateway.

## Architecture

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
        10.10.0.0/24                 10.10.1.0/24
              |                           |
       +------+------                     |
       |             |                    |
       v             v                    v
   Public EC2    NAT Gateway          Private EC2
   Bastion Host      |                    |
       |             +--------------------+
       |
       | SSH
       +------------------------------> Private EC2
```

## What I Implemented

1. Created a custom VPC with CIDR `10.10.0.0/16`.
2. Created a public subnet and a private subnet.
3. Attached an Internet Gateway to the VPC.
4. Created separate route tables for the public and private subnets.
5. Added a default route from the public subnet to the Internet Gateway.
6. Launched a public EC2 instance with a public IP address.
7. Launched a private EC2 instance without a public IP address.
8. Connected to the public EC2 instance from my laptop using SSH.
9. Used the public EC2 instance as a bastion host to access the private EC2 instance.
10. Troubleshot an SSH key mismatch that initially prevented access to the private EC2 instance.
11. Verified that the private EC2 instance initially had no outbound Internet access.
12. Created a NAT Gateway in the public subnet.
13. Updated the private subnet route table with:

```text
Destination: 0.0.0.0/0
Target: NAT Gateway
```

14. Verified outbound Internet connectivity from the private EC2 instance.

## Routing Design

### Public Subnet Route Table

```text
10.10.0.0/16   local
0.0.0.0/0      Internet Gateway
```

### Private Subnet Route Table

Before NAT Gateway:

```text
10.10.0.0/16   local
```

After NAT Gateway:

```text
10.10.0.0/16   local
0.0.0.0/0      NAT Gateway
```

## Verification

From the private EC2 instance, outbound Internet connectivity was tested after the NAT Gateway and route table were configured.

The private EC2 instance remained without a public IP address while still being able to initiate outbound Internet connections.

## Key Learning

This project demonstrated:

- Public vs private subnet behavior
- Internet Gateway routing
- Bastion-host SSH access
- EC2 private IP connectivity
- SSH key-pair authentication
- NAT Gateway operation
- Private subnet outbound Internet access
- Separation between inbound public access and outbound Internet connectivity
