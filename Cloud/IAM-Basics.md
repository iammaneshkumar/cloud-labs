# IAM Basics (AWS Identity and Access Management)

## 1. What is IAM?

IAM (Identity and Access Management) is a service in AWS that allows you to:

- Control **who** can access AWS resources
- Define **what** actions they can perform
- Manage **permissions** for users, groups, and roles

IAM ensures secure and organized access to AWS, instead of using the root user for daily tasks.

---

## 2. IAM Users

An **IAM User** represents a person or system that needs AWS access.

Key points from my setup:

- Created a personal IAM user: `iammaneshkumar`
- IAM users have:
  - **Username**
  - **Console password**
  - **Access key + Secret key** (for CLI/programmatic access)
- Root user should be avoided for daily operations

**Learning:** Users allow controlled human access with specific permissions.

---

## 3. IAM Roles

An **IAM Role** is meant for **AWS services** (like EC2 or Lambda):

- Roles provide **temporary credentials** to services
- No password is needed
- EC2 instances can access AWS resources securely without storing access keys

Example from my lab:

- My EC2 had an IAM role attached
- This allowed secure interaction with AWS services automatically

---

## IAM Practical Experience

- Created a personal IAM user (`iammaneshkumar`) to avoid using root user.
- Learned why root user should be avoided for daily AWS operations.
- Verified access via AWS CLI using `aws sts get-caller-identity`.
- Observed how IAM roles provide temporary credentials to EC2 instances.
- Understood the importance of least privilege and secure access management.

**Learning:** IAM ensures safer, controlled access to AWS resources. It is essential for both human users and services (like EC2) to maintain security and proper permission management.

## 4. IAM Policies (Permission Control Layer)

IAM does not automatically grant any permissions to users or roles.  
Actual access is controlled using **IAM Policies**.

An IAM Policy:
- Is a JSON-based permission document
- Explicitly allows or denies actions
- Defines:
  - Which AWS service can be accessed
  - Which actions are allowed
  - On which resources

If AWS shows an error like **AccessDenied**, it means:
- The IAM policy attached to the user or role does not allow that action
- The issue is related to permissions, not networking or EC2 state

Learning from practice:
Access denied errors during IAM operations occurred due to missing permissions in IAM policies, not because of EC2 or VPC misconfiguration.

---

## 5. IAM vs Security Groups (Clear Responsibility Split)

IAM and Security Groups serve completely different purposes.

IAM controls:
- Who can create, modify, or delete AWS resources
- Who can edit Security Groups
- Who can start, stop, or terminate EC2 instances

Security Groups control:
- Which IP addresses can connect to an EC2 instance
- Which ports are open (SSH, HTTP, etc.)
- Inbound and outbound network traffic

Important understanding:
IAM does not allow or block SSH or HTTP traffic directly.  
IAM only decides **who is allowed to modify** Security Group rules.

---

## 6. Inbound and Outbound Rules (Networking Context)

Inbound rules:
- Control incoming traffic to an EC2 instance
- Example: Allow SSH only from “My IP”

Outbound rules:
- Control outgoing traffic from an EC2 instance
- By default, outbound traffic is allowed

IAM is not involved in traffic flow.  
IAM only controls whether a user has permission to edit these rules.

Key distinction:
- SSH connection failure → Security Group or IP issue
- AccessDenied error → IAM policy issue

---

## 7. IAM and AWS CLI (Local vs EC2)

When using AWS CLI on a local machine:
- IAM user access key and secret key are required
- Permissions depend on the IAM user’s policies

When using AWS CLI inside an EC2 instance:
- IAM Role is used
- No access keys are stored on the instance
- AWS provides temporary credentials automatically

Learning:
- Local Ubuntu CLI uses IAM User credentials
- EC2 CLI uses IAM Role credentials

---

## 8. Why IAM is Critical

Without IAM:
- Root user would be required for daily tasks
- Any mistake could impact the entire AWS account

With IAM:
- Access is controlled and limited
- Permissions follow the principle of least privilege
- AWS usage becomes safer and auditable

Final Learning:
IAM is the security foundation of AWS.  
It ensures controlled access for both humans and AWS services.