# VPC Networking Troubleshooting

## SSH Access Denied to Private EC2 Instance

### Problem

I successfully connected from my laptop to the public EC2 instance.

From the public EC2 instance, I then attempted to SSH into the private EC2 instance using:

```bash
ssh -i key.pem ec2-user@<PRIVATE_EC2_IP>
```

However, the SSH connection returned an authentication/access denied error.

### Investigation

The VPC routing and Security Group configuration were already correct, so the issue was traced to SSH authentication.

I discovered that the `key.pem` file on the public EC2 instance had been created using the contents of the wrong private key.

The private EC2 instance had originally been launched with a different AWS key pair.

I had previously saved the correct private key information inside a PowerPoint file.

### Resolution

I used PuTTYgen to recreate/export the correct private key from the key material that matched the key pair used when the private EC2 instance was launched.

I then updated the `key.pem` file on the public EC2 instance with the correct private key content.

The file permission was set appropriately:

```bash
chmod 400 key.pem
```

I retried the SSH connection:

```bash
ssh -i key.pem ec2-user@<PRIVATE_EC2_IP>
```

### Result

SSH authentication succeeded and I was able to connect to the private EC2 instance through the public EC2 instance.

```text
Laptop
   |
   | SSH
   v
Public EC2
   |
   | Correct key.pem
   v
Private EC2
```

### Root Cause

The `key.pem` file initially used on the public EC2 instance contained the private key for a different AWS key pair.

Because the private EC2 instance had been launched with another key pair, SSH authentication failed even though network connectivity was working.

### Key Learning

SSH access to an EC2 instance depends on both:

1. Network connectivity to TCP port 22.
2. Using the private key that matches the key pair associated with that EC2 instance.

A valid `.pem` file is not enough by itself. It must be the correct private key for the key pair used when the EC2 instance was created.
