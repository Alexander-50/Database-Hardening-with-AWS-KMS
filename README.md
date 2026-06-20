# 🔐 Database Hardening with AWS KMS & DynamoDB

<p align="left">
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white">
  <img src="https://img.shields.io/badge/AWS_KMS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white">
  <img src="https://img.shields.io/badge/DynamoDB-4053D6?style=for-the-badge&logo=amazondynamodb&logoColor=white">
  <img src="https://img.shields.io/badge/IAM-DD344C?style=for-the-badge&logo=amazonaws&logoColor=white">
  <img src="https://img.shields.io/badge/Cloud_Security-2EA44F?style=for-the-badge">
  <img src="https://img.shields.io/badge/Encryption_at_Rest-0066CC?style=for-the-badge">
</p>

## 📖 Project Overview

This project demonstrates how to secure sensitive data stored in Amazon DynamoDB using AWS Key Management Service (AWS KMS).

A Customer Managed Key (CMK) was created and integrated with DynamoDB to implement encryption at rest. Access controls were validated using IAM policies and KMS key permissions to verify both authorized and unauthorized access scenarios.

Amazon DynamoDB supports encryption at rest through AWS KMS, allowing organizations to use AWS-owned, AWS-managed, or customer-managed encryption keys. Customer-managed keys provide the highest level of control over key lifecycle management, auditing, and access permissions.

---

## 🎯 Objectives

* Create and manage a Customer Managed Key (CMK)
* Implement encryption at rest for DynamoDB
* Understand symmetric encryption concepts
* Configure IAM and KMS permissions
* Test authorization and decryption controls
* Apply cloud security best practices

---

## 🏗️ Architecture


<img width="1608" height="772" alt="image" src="https://github.com/user-attachments/assets/532969ce-956e-4046-944a-12de9db9f162" />

---

## 🛠️ Tech Stack

| Service                | Purpose                          |
| ---------------------- | -------------------------------- |
| AWS KMS                | Encryption key management        |
| Amazon DynamoDB        | NoSQL database storage           |
| AWS IAM                | Access control and authorization |
| KMS Key Policies       | Key usage permissions            |
| Symmetric Encryption   | Data protection                  |
| AWS Management Console | Resource configuration           |

---

## 🔑 AWS KMS Configuration

### Key Type

* Customer Managed Key (CMK)
* Symmetric Encryption Key
* Encrypt / Decrypt Operations

### Why Symmetric Encryption?

Symmetric encryption uses a single cryptographic key for both encryption and decryption operations, making it highly efficient for securing large volumes of stored data.

### Why Customer Managed Keys?

Customer-managed keys provide:

* Full control over key lifecycle
* Granular permission management
* Custom key policies
* Audit visibility through CloudTrail
* Compliance and governance flexibility

AWS documentation recommends customer-managed keys when organizations require maximum control over encryption and auditing capabilities.

---

## 🗄️ DynamoDB Encryption

Amazon DynamoDB supports three encryption models:

### AWS Owned Key

* Fully managed by DynamoDB
* No visibility or control

### AWS Managed Key

* Managed by AWS KMS
* Limited customization

### Customer Managed Key (CMK)

* Created and managed by the customer
* Custom access policies
* Advanced auditing capabilities
* Full control over key lifecycle

For this project, a Customer Managed Key was selected to demonstrate enterprise-grade encryption management and access control. DynamoDB transparently encrypts and decrypts table data while using KMS-managed keys behind the scenes.

---

## 🔒 Security Controls Implemented

### Encryption at Rest

The DynamoDB table was configured to use a Customer Managed KMS Key.

This ensures:

* Data remains encrypted when stored
* Encryption keys are centrally managed
* Unauthorized users cannot decrypt protected data
* Encryption operations are auditable

### Access Control Layers

The solution combines:

* IAM Policies
* KMS Key Policies
* DynamoDB Permissions

This creates a defense-in-depth security model where both resource access and decryption permissions must be granted before sensitive data can be viewed.

---

## 🧪 Security Verification & Testing

### Test 1 — Authorized User Access

**Configuration**

* Administrator permissions
* KMS key access granted
* DynamoDB permissions granted

**Result**

![Image](http://learn.nextwork.org/happy_olive_shy_tui/uploads/aws-security-kms_c0d1e2f3)


✅ Successfully viewed encrypted DynamoDB records.

---

### Test 2 — Unauthorized User Access

**Configuration**

* DynamoDB permissions granted
* No KMS permissions assigned

**Result**

![Image](http://learn.nextwork.org/happy_olive_shy_tui/uploads/aws-security-kms_w0x1y2z3)


❌ Access denied (`kms:Decrypt`)

The user could access DynamoDB resources but could not decrypt encrypted records because KMS permissions were missing.

---

### Test 3 — Granting Key User Access

**Configuration**

* User added as a KMS Key User
* Key policy updated

**Result**
<img width="1456" height="574" alt="image" src="https://github.com/user-attachments/assets/d144cb07-4d7a-4430-95be-b44d72d8ad96" />

✅ Successfully accessed encrypted data.

This verified that KMS Key Policies directly control decryption permissions.

---

## 🛡️ Security Best Practices Demonstrated

* Encryption at Rest
* Principle of Least Privilege
* Customer Managed Encryption Keys
* Centralized Key Management
* Defense in Depth
* Authorization Testing
* Access Control Validation


## 📚 Key Learnings

### AWS Managed Keys vs Customer Managed Keys

| AWS Managed Key       | Customer Managed Key   |
| --------------------- | ---------------------- |
| Managed by AWS        | Managed by Customer    |
| Limited control       | Full lifecycle control |
| Limited customization | Custom policies        |
| Basic auditing        | Advanced auditing      |

### Summary of learning

* Encryption protects data confidentiality.
* IAM controls access to resources.
* KMS controls decryption permissions.
* Access to a database does not automatically grant access to encrypted data.
* Strong cloud security requires both encryption and authorization controls.

---

## 🚀 Future Improvements

* Enable automatic key rotation
* Integrate AWS CloudTrail auditing
* Monitor key activity with CloudWatch
* Deploy using Terraform
* Implement organization-wide encryption standards

---

## 🏆 Skills Demonstrated

* AWS KMS
* Amazon DynamoDB
* AWS IAM
* Encryption at Rest
* Customer Managed Keys (CMK)
* Key Policy Management
* Access Control Testing
* Cloud Security Architecture
* Security Validation
* Principle of Least Privilege

---

## 📂 Repository Structure

```text
database-hardening-with-aws-kms/
│
├── README.md
├── LICENSE
│

```

---

## 👨‍💻 Author

**Prabhat Alexander**

Cloud Security | AWS | Cybersecurity | Security Engineering

Built as part of the NextWork AWS Security Project Series.
