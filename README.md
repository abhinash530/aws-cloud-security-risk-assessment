# AWS Cloud Security Risk Assessment

## Project Overview

This project presents a security assessment of a representative Amazon Web Services (AWS) cloud environment.

The assessment identifies common cloud security risks, configuration weaknesses, potential technical and business impacts, and recommended security controls.

The project demonstrates practical concepts related to:

- Cloud Security
- AWS Security
- Identity and Access Management
- Network Security
- Data Protection
- Encryption
- Security Monitoring
- Security Risk Assessment
- Security Remediation

## Objectives

The main objectives of this project are:

1. Document a representative AWS cloud architecture.
2. Identify common AWS security risks and misconfigurations.
3. Categorize findings according to severity.
4. Analyze technical and business impacts.
5. Recommend appropriate security controls.
6. Develop a structured remediation plan.
7. Demonstrate practical understanding of cloud security principles.

## AWS Services Covered

| AWS Service | Security Focus |
|---|---|
| AWS IAM | Identity and access management |
| Amazon S3 | Data and storage security |
| Amazon EC2 | Compute security |
| Amazon VPC | Network security |
| Security Groups | Network access control |
| AWS KMS | Encryption and key management |
| AWS CloudTrail | Audit logging |
| Amazon CloudWatch | Monitoring and alerting |

## Security Findings

| ID | Finding | Severity |
|---|---|---|
| AWS-001 | Excessive IAM Permissions | High |
| AWS-002 | Public S3 Bucket Access | Critical |
| AWS-003 | Unrestricted Security Group Rules | High |
| AWS-004 | Missing Encryption | High |
| AWS-005 | Insufficient CloudTrail Logging | Medium |
| AWS-006 | Insufficient Security Monitoring | Medium |

## Security Architecture

```text
                         Internet
                            |
                            v
                    +---------------+
                    | Internet      |
                    | Gateway       |
                    +---------------+
                            |
                            v
                    +---------------+
                    |     AWS VPC   |
                    +---------------+
                       /           \
                      /             \
                     v               v
             Public Subnet      Private Subnet
                  |                   |
                  v                   v
             +---------+         +---------+
             |   EC2   |         |Database |
             |Application|        | Server  |
             +---------+         +---------+
                  |
                  v
             +---------+
             |   S3    |
             | Storage |
             +---------+

        Security & Monitoring
        ---------------------
        IAM
        CloudTrail
        CloudWatch
        AWS KMS
