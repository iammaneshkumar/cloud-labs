# AWS EC2 Private Instance Access Lab

## Objective
To understand how private EC2 instances work and how to securely access them using a bastion host.

---

## Architecture Overview
- One Public EC2 (Bastion Host)
- One Private EC2 (Application Server)
- Both instances in same VPC
- SSH access via Bastion only

---

## Network Details
- VPC CIDR: 172.31.0.0/16
- Private EC2 IP: 172.31.4.41
- Public EC2 has Public IPv4 enabled

---

## Security Groups
### Bastion Host SG
- SSH (22)
- Source: My IP

### Private EC2 SG
- SSH (22)
- Source: Bastion Host Security Group

---

## Access Flow
1. SSH into Bastion Host using public IP
2. From Bastion Host, SSH into Private EC2 using private IP
3. Private EC2 not accessible from internet directly

---

## Commands Used
```bash
chmod 400 ec2-key.pem
ssh -i ec2-key.pem ubuntu@<public-ip>
ssh ubuntu@172.31.4.41