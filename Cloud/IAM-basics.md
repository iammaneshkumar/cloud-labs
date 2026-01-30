# Networking Basics (AWS Cloud)

## 1. What is Networking in Cloud Computing?

Cloud networking allows cloud resources like EC2 instances, databases, and users to communicate with each other over the internet or private networks.

In AWS, networking is mainly managed using **Amazon VPC (Virtual Private Cloud)**. VPC provides a logically isolated network where cloud resources are launched.


---

## 2. What is VPC (Virtual Private Cloud)?

A VPC is a virtual network dedicated to an AWS account. It is isolated from other virtual networks in the AWS cloud.

Key points:
- Every EC2 instance must be launched inside a VPC
- EC2 cannot exist without a VPC
- VPC controls IP range, subnets, route tables, and gateways

In my case, the EC2 instance was launched inside the **default VPC** provided by AWS

---

## 3. What is a Subnet?

A subnet is a smaller network created inside a VPC.

Types of subnets:
- **Public Subnet:** Connected to the internet
- **Private Subnet:** Not directly accessible from the internet

My EC2 instance was placed in a **public subnet** because:
- It had a public IP address (13.x.x.x range)
- I could access it using SSH and a web browser

---

## 4. Public IP vs Private IP

- **Public IP:** Used to access resources from the internet
- **Private IP:** Used for internal communication within the VPC

Examples:
- Public IP: `13.x.x.x`
- Private IP: `172.x.x.x` or `192.168.x.x`

My EC2 instance used:
- Public IP for SSH and HTTP access
- Private IP for internal AWS networking

---

## 5. Internet Gateway (IGW)

An Internet Gateway allows communication between a VPC and the internet.

Important points:
- A public subnet must have an Internet Gateway attached to the VPC
- Without an Internet Gateway, EC2 cannot access or be accessed from the internet

If the Internet Gateway is removed:
- SSH connection will fail
- Website hosted on EC2 will not open

---

## 6. Route Table

A route table defines how network traffic is directed.

In my setup:
- The route table contained the rule:

- This rule allowed internet traffic to reach the EC2 instance

Without this route, even with a public IP, the EC2 instance would not be reachable.

---

## 7. Security Groups (Cloud Firewall)

A security group acts as a virtual firewall for EC2 instances.

In my EC2 configuration:
- Port 22 (SSH) was open for remote login
- Port 80 (HTTP) was open for web access

Security groups:
- Are stateful
- Work at the instance level
- Control inbound and outbound traffic

---

## 8. How Networking Components Work Together (Practical Flow)

When I accessed my EC2 web server from a browser:

1. Browser sent a request to the EC2 public IP
2. Internet Gateway allowed internet traffic into the VPC
3. Route table forwarded traffic to the public subnet
4. Security group allowed port 80 (HTTP)
5. Nginx running on EC2 responded with the web page

This practical setup helped me understand how cloud networking components work together.

---

## 9. Key Learnings

- VPC is the foundation of AWS networking
- Subnets divide the VPC into smaller networks
- Internet Gateway enables internet access
- Route tables define traffic paths
- Security groups protect EC2 instances like firewalls

