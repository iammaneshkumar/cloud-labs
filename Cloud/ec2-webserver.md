# EC2 Web server setup (Ubuntu + Nginx)

## Objective
The goal of this lab is to undertand how a cloud server works by launching an AWS EC2 instance, connecting it using SSH, and deploying a basic web server using Ngnix.

This lab demonstrates the real meaning of cloud computing: using remote infrastructure instead of a local computer.

---

## Presequisites
- AWS account (Free tier)
- Ubuntu-based EC2 instance
- Local system with SSH client (Ubuntu)
- Basic linux command knowledge

---

## Step 1: Lanuch EC2 Instance
- Logged in to AWS management console
- selected **EC2 service**
- choose **Ubuntu server (LTS)** AMI
- Instance type: **t2.micro**
- create or select a key pair
- Allowed inbound rules in security group: -
  - Port 22 (SSH)
  - Port 80 (HTTP)

**Result:** EC2 instance launched successfully

---

## Step 2: Connect ot EC2 using SSH
From local ubuntu terminal:

'''bash
ssh -i mkkey.pem ubuntu@<EC2-Public-Ip>

## After seuucesful login, terminal shows:
### ubuntu@<public-ip>: ~$

