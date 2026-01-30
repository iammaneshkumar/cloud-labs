# VPC Basics (AWS networking foundation)

## Objective
The objective of this document is to understand how AWS networking works at a basic level, including VPC, Subnet, and Internet gateway, and how an EC2 instance becomes accessible over the internet.

---

## What is VPC?
VPC (Virtual private cloud) is a logically isolated private network created inside AWS.
All AWS resources such as EC2 instances are launched inside a VPC.

A VPC allows users to define their own IP address range, subnets, and routing rules.

## Default VPC
When an AWS account is created, AWS automatically provides a default VPC.

The default VPC includes:
- A predefined IP range.
- Public subnets in each availability zone.
- An attatched Internet gatway.
- A routing table that allows internet access.

This setup heps to launch EC2 instances without manual metwork configuration.

---

## What is a Subnet?
A subnet is s logical subdivision of a VPC.

Subnets are used to:
- Organize resources
- Control network access
- Define availablilty
- Decide whether resources are public pr private

Every EC2 instance must be launched inside a subnet.

---

## Private Subnet vs Public subnet

### Public subnet
A public subnet is a subnet that has a route to an internet gateway.

Resources in a public subnet:
- Can receive inbound traffic from the internet.
- Can send outbound traffic to the internet.
- Are trypically use for web servers.

### Private subnet
A private subnet does not have a direct route to the internet gateway.

Resources in a private subnet:
- Cannot be accessed directly from the internet.
- Can access the internet only through a NAT  Gateway (Outbound only)
- Are typicaclly used for databases and internal services.

---

## Internet gateway (IGW)
An inertnet gateway is a horizontally scaled AWS-managed component that connects a VPC to the public internet.

It enables:
- Inbound traffic from the internet to EC2 instances with public IP
- Outbound traffic from EC2 instances to the internet.

Without an Internet gateway, internet access is not possible even if security group is allowed for traffic.

---

## Route table
A route table defines how network traffic is directed within a VPC.

For internet access, a Public subnet must have the folowing route:
0.0.0.0/0 --- Internet gateway

Without this route, traffic cannot reach the internet.

---

## Traffic flow to an EC2 isntance when a user accesses a web server hosted on EC2, traffic flows as follows:

User (Browser)
-> Intenet
-> Internet gateway
-> Route table
-> Subnet
-> EC2 instance

All components must be correctly configured for successful access:

---

## Practical obervation
In the EC2 webserver lab:
- The instance was placed in a public subnet
- An internet gateway was attatched to the VPC
- The route table allowed internet traffic
- Security group allowed HTTP (port 80)

As a result, the web server was accessible via public IP.

## What I learned in this -
- VPC is the foundation of AWS networking
- EC2 instance can not exist without VPC
- Subnets controls the network exposure
- Route table defines traffic direction
- Security group acts as cloud level firewalls
