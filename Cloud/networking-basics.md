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

# Networking Basics (Practical EC2 Example)

## 1. EC2 Public vs Private Network Access

- My EC2 instance was in a **public subnet**:
  - It had a public IP (e.g., 13.x.x.x)
  - I could access it directly via SSH and a web browser

- If the EC2 instance was in a **private subnet**:
  - Direct SSH or browser access from the internet would fail
  - Access would require a **NAT Gateway** or **bastion host**

**Learning:** Public subnets allow internet access; private subnets are for internal resources.

---

## 2. Security Groups in Practice

- Security groups act as **firewalls** for EC2 instances
- For my EC2:
  - **Port 22 (SSH)**: Allowed my IP for secure login
  - **Port 80 (HTTP)**: Allowed everyone to access the website

**Important observation:**  
- Every time my public IP changed, I needed to update the SSH rule
- This is normal because AWS security groups require **CIDR-based IPs**

---

## 3. Route Tables and Internet Gateway

- My EC2 route table had:

- This allowed traffic from the internet to reach my instance
- Without this route, even with public IP and security group, SSH or HTTP would fail

---

## 4. Practical Flow of a Web Request

When accessing the website hosted on EC2:

1. Browser sends a request to the EC2 public IP
2. Internet Gateway allows traffic into the VPC
3. Route table directs traffic to the public subnet
4. Security group allows HTTP (port 80)
5. Nginx on EC2 responds with the webpage

**Learning:** This shows how AWS networking, security groups, and EC2 work together in a real cloud setup.

---

## 5. Key Takeaways from EC2 Networking

- Public IP is essential for internet-accessible EC2
- Security group rules must match your current IP for SSH
- Internet Gateway + route table = internet access
- EC2 instances in public subnets are directly reachable
- EC2 instances in private subnets require NAT or bastion for external access
- Understanding these basics helps in deploying websites and applications securely on AWS
