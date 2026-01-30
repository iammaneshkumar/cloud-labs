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