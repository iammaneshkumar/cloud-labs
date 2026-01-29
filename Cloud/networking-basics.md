# Networking basics

## Key concepts
- IP address
- Private and public IP
- Ports
- SSH

## Common ports
- 22: SSH
- 80: HTTP
- 443: HTTPS

## Cloud relevance
Networking enables communication between cloud and users.

# Networking Basics in AWS EC2

## Objective
The objective of this document is to understand the basics networking concepts used in AWS EC2, including public IP, private IP, and security groups, and how they control access to cloud servers.

---

### What is Networking in cloud?
In cloud computing, networking defines how a server communicates with users over the internet and with other resoures inside the cloud.

AWS manages the physical network, while user control access using logical configurations such as IP address and security groups.

## Public IP Address
A public IP address is an IP that allows EC2 instance to be accessed over the internet.

Uses:
- Accessing the web server from a browser
- Connecting to EC2 using SSH from a locla system

**The public IP can change when an EC2 instance is stopped and started**

## Private IP address
A private IP address is used for internal communication inside the AWS network.

Uses:
- Commnication between AWS resources
- Internal server operations

**Private IP are not accessible from the public internet**

## Difference between Public and Private IP

| Public IP | Private IP |
|-----------|------------|
| Accesible over the internet | Accesible only inside AWS |
| Used by browsers and SSH | Used for internal communication |
| Can change on Stop/Start | Usually reamins the same |

## Security groups
A security group acts as a virtual firewall for an EC2 instance.

It controls:
- Which traffic is allowed to enter the instance (Inbound Rules)
- Which traffic can leave the instance (Outbound Rules)

## Inbound rules
Inbound rules define what type of traffic is allowed to reach the EC2 isntance.

Examples:
- SSH (Port 22): Allows secure remote login
- HTTP (Port 80): Allows web traffic

## Outbound rules
Outbound rules defines what traffic is allowed to leave the EC2 instance.

By default, AWS allows all outbound traffic.

## Ports used in this lab
- Port 22 (SSH): Used to connect to EC2 using terminal.
- Port 80 (HTTP): Used to access the web server through browser.

## Practical observation
- When port 80 was blocked, the web server was not accessible
- When port 80 was allowed, the web server became accesible
- This confirms that the security groups control network access in the cloud

## What I learned
- Cloud networking is controlled using logical rules, not physical devices
- Public IP enables internet access
- Private IP is used for internal communication
- Security groups are a type of firewall rules for cloud
- Opening or closing ports directly affects accessibility
