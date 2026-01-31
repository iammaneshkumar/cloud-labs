# AWS S3 (Simple Storage Service) Basics

## Objective
Understand what **S3** is, how it works, and how to access it securely from **EC2** using IAM Roles.

---

## 1. What is S3?
- S3 = **Simple Storage Service** by AWS  
- Cloud-based storage for **files, images, backups, logs, website data, etc.**  
- Objects (files) are stored inside **buckets** (containers)  
- Accessible over the internet if permissions allow  
- Fully managed, scalable, and highly durable  

---

## 2. Key Concepts

| Term | Meaning |
|------|--------|
| Bucket | Container for objects (files) |
| Object | Individual file stored inside a bucket |
| IAM Role | Temporary credentials that allow EC2 or other services to access S3 |
| IAM User | Permanent credentials for humans to access AWS services |

---

## 3. Accessing S3 from EC2

### Using IAM Role
- Attach a **role** like `S3ReadOnlyAccess` to an EC2 instance  
- No AWS keys stored on the instance  
- Inside EC2:
```bash
aws s3 ls