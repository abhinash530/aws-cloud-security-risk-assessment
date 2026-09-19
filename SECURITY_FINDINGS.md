# AWS Cloud Security Findings

## 1. Purpose

This document provides a detailed summary of the security findings identified during the AWS Cloud Security Risk Assessment.

The findings focus on common configuration and security weaknesses that may occur in AWS environments. Each finding includes its severity, affected area, risk description, potential impact, and recommended security control.

---

## 2. Risk Rating Methodology

Risk severity is classified into four categories:

| Severity | Description |
|----------|-------------|
| Critical | May result in significant unauthorized access, sensitive data exposure, or major security impact |
| High | Could allow unauthorized access, compromise, or significant security weakness |
| Medium | Could increase security exposure or reduce the ability to detect and respond to incidents |
| Low | Limited impact but should be addressed as part of security improvement |

---

# 3. Finding Summary

| ID | Finding | AWS Service | Severity |
|----|---------|-------------|----------|
| AWS-001 | Excessive IAM Permissions | IAM | High |
| AWS-002 | Public S3 Bucket Access | S3 | Critical |
| AWS-003 | Unrestricted Security Group Rules | VPC | High |
| AWS-004 | Missing Encryption | KMS / S3 / EC2 | High |
| AWS-005 | Insufficient CloudTrail Logging | CloudTrail | Medium |
| AWS-006 | Insufficient Security Monitoring | CloudWatch | Medium |

---

# 4. AWS-001: Excessive IAM Permissions

## Severity

**High**

## Affected Service

AWS Identity and Access Management (IAM)

## Description

IAM permissions should be granted according to the principle of least privilege. Users, groups, and roles should receive only the permissions required to perform their intended tasks.

Excessive permissions can increase the impact of compromised credentials.

## Security Risk

If an attacker obtains credentials belonging to an over-privileged identity, the attacker may be able to access or modify resources beyond the original user's requirements.

## Potential Impact

- Unauthorized resource access
- Data modification
- Data deletion
- Privilege escalation
- Increased attack impact

## Recommended Controls

- Review IAM policies.
- Remove unnecessary permissions.
- Use IAM roles for AWS workloads.
- Avoid unnecessary administrative privileges.
- Enable MFA for appropriate human users.
- Review unused credentials and accounts.

## Remediation

Perform an IAM permission review and replace broad permissions with specific resource and action permissions wherever practical.

---

# 5. AWS-002: Public S3 Bucket Access

## Severity

**Critical**

## Affected Service

Amazon S3

## Description

Amazon S3 buckets may contain sensitive business or application data. Incorrect bucket policies or access configurations can unintentionally expose data to the public internet.

## Security Risk

Publicly accessible objects may be downloaded by unauthorized individuals.

## Potential Impact

- Sensitive data exposure
- Data theft
- Privacy violations
- Compliance concerns
- Reputational damage

## Recommended Controls

- Enable S3 Block Public Access.
- Review bucket policies.
- Review access control configuration.
- Use encryption.
- Apply least-privilege access.
- Monitor access activity.

## Remediation

Review all S3 buckets and remove unintended public permissions. Public access should only be permitted when explicitly required and appropriately controlled.

---

# 6. AWS-003: Unrestricted Security Group Rules

## Severity

**High**

## Affected Service

Amazon VPC / Security Groups

## Description

Security Groups control inbound and outbound network traffic associated with AWS resources.

Allowing unnecessary inbound traffic from the entire internet can expose services to scanning and unauthorized connection attempts.

Example of a risky configuration:

```text
Protocol: TCP
Port: 22
Source: 0.0.0.0/0
