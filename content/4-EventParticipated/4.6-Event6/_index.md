---
title: "Event 6"
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

# **AWS Security Specialty Workshop**

**Location**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Date**: Saturday, November 29, 2025

# Learning Report: "AWS Security Specialty Workshop"

### Event Objectives

- Deeply understand the role of **Security Pillar** in AWS Well-Architected Framework
- Master the **5 Core Security Pillars**: Identity and Access Management (IAM), Detection, Infrastructure Security, Data Protection, and Incident Response
- Update on leading cybersecurity threats in Cloud environments in the Vietnamese market
- Practice skills like IAM privilege reviews and building incident response playbooks (**IR Playbook**)

---

### Speaker List

- **AWS Security Expert Team** (Deep expertise in security architecture and compliance)

---

### Key Content Highlights

#### Foundation & Identity (Pillar 1)

- **Core Principles**: Strictly apply **Least Privilege**, **Zero Trust** (default deny), and **Defense in Depth** principles
- **Modern IAM**: Transition from IAM Users (with long-term credentials) to **IAM Roles** and **AWS Identity Center (SSO)** for centralized access management
- **Access Control**: Use **Service Control Policies (SCP)** and **Permission Boundaries** to limit privilege scope in multi-account environments
- **Small Practical Demo**: Demonstrate how to validate IAM Policies and simulate access to detect security configuration errors

#### Detection & Infrastructure (Pillar 2 & 3)

- **Continuous Monitoring**: Enable services like **CloudTrail** (at organization level), **GuardDuty**, and **Security Hub** for continuous security monitoring and assessment
- **Logging Strategy**: Require logging at every system layer: VPC Flow Logs (network), ALB logs (application), and S3 logs (storage)
- **Network Security**: Implement network segmentation with VPC, combining **Security Groups** and **NACLs**. Protect perimeter with **WAF, Shield**, and **Network Firewall**

#### Data Protection & Incident Response (Pillar 4 & 5)

- **Encryption**: Implement data encryption in-transit and at-rest on services like S3, EBS, RDS, using **KMS (Key Management Service)**
- **Secrets Management**: Eliminate hard-coded credentials by using **Secrets Manager** and **Parameter Store**, combining automatic rotation mechanisms
- **Incident Response Automation**: Build response playbooks for common incidents (like exposed access keys, malware) and automate resource isolation using **Lambda/Step Functions**

---

### What I Learned

#### Zero Trust Mindset

- **Identity as the Perimeter**: In Cloud environments, **Identity** has become the most important protective barrier, replacing traditional IP addresses
- Always follow the principle: Never trust by default, always authenticate every request, and grant only minimum necessary permissions

#### Automation is Core

- Manual security cannot keep pace with Cloud deployment speed. Must apply methods like **Detection-as-Code** and **Auto-remediation** to minimize risk from human error and delays

---

### Application to Work

- **Audit IAM**: Review all IAM Users, delete old access keys, and migrate applications to **IAM Roles** for enhanced security
- **Enable GuardDuty**: Activate **GuardDuty** service across all regions and accounts to detect abnormal access and activities early
- **Deploy Secrets Manager**: Replace configuration files containing database passwords with API calls to **Secrets Manager**
- **Build IR Playbook**: Write detailed incident handling procedures for "IAM Key Exposure" scenario and conduct drills with technical team

---

### Event Experience

The workshop provided deep technical details, comprehensively covering essential security aspects modern Cloud engineers must master.

#### Comprehensive Framework

- Organizing content by **5 Security Pillars** helped me systematize previously scattered security knowledge into a standard, applicable framework
- The discussion on **Leading threats in Vietnam** is highly practical, helping the team identify specific risks suited to local context

#### Applied Practice

- Demos on **Access Analyzer** and **Validate IAM Policy** tools are very useful, directly addressing daily permission debugging challenges
- The **Incident Response** section clarified that "detection" is only part of the solution; fast automatic "response" is what determines system safety

#### Some photos from the event

- Add your event photos here

> Overall, the event clearly confirmed that security is not a blocker but an enabler allowing enterprises to operate faster and safer.
