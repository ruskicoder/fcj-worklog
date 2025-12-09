---
title: "Event 5"
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

# **AWS Mastery 2: AWS DevOps & Modern Operations**

**Location**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Date**: Monday, November 17, 2025

# Learning Report: "AWS DevOps & Modern Operations"

### Event Objectives

- Build **DevOps** mindset and master performance measurement through **DORA metrics**
- Establish complete **CI/CD** workflow, automating with **AWS Developer Tools** suite
- Modernize infrastructure management through code (**Infrastructure as Code - IaC**) with **CloudFormation** and **CDK**
- Deploy containerized applications (Docker) on services like **ECS, EKS** and **App Runner**
- Build comprehensive **Observability** systems for distributed applications

---

### Speaker List

- **AWS Expert Team** (Deep specialists in DevOps, Container and Observability)

---

### Key Content Highlights

#### DevOps Mindset & CI/CD

- **DORA Metrics**: Emphasize importance of performance metrics like Deployment Frequency, Lead Time for Changes, and Mean Time to Recover (MTTR)
- **Git Strategy**: Compare source code management strategies like GitFlow and Trunk-based development
- **Pipeline Automation**: Illustrate complete CI/CD workflow: from **CodeCommit** (code repository), **CodeBuild** (build/test), to **CodeDeploy** (deployment) orchestrated by **CodePipeline**
- **Deployment Strategies**: Introduce safe deployment techniques to minimize risk: Blue/Green, Canary, and Rolling updates

#### Infrastructure as Code (IaC)

- **CloudFormation**: Guide managing infrastructure through templates, including Stacks concept and drift detection mechanisms
- **AWS CDK**: Use popular programming languages to define infrastructure, leveraging reusable "Constructs" and design patterns
- **IaC Selection**: Discuss criteria for choosing between CloudFormation and CDK depending on project requirements and scale

#### Container Services

- **Spectrum of Compute**: From image management with **ECR** to orchestration options: **ECS** (simple, deep AWS integration), **EKS** (open Kubernetes standard), and **App Runner** (maximum simplification for web apps/API)
- **Microservices Deployment**: Compare and demonstrate deploying microservices across different platforms

#### Monitoring & Observability

- **Comprehensive Observability**: Combine **CloudWatch** (for Metrics, Logs, Alarms) and **X-Ray** (for Distributed Tracing) for deep and comprehensive system visibility
- **Best Practices**: Set up visual monitoring dashboards and efficient on-call processes

---

### What I Learned

#### Automation First Priority

- **CI/CD** is a cultural foundation that minimizes human error and accelerates product release velocity
- **IaC** is a mandatory standard for all modern infrastructure, ensuring Dev/Test/Prod environments remain consistent and reproducible

#### Operational Excellence

- **Observability** is more critical than simple Monitoring, especially in Microservices architecture, as it enables rapid root cause analysis through tracing
- Choosing appropriate deployment strategies (like Blue/Green) is key to achieving near-zero downtime

---

### Application to Work

- **Restructure Pipeline**: Convert current manual build processes to **AWS CodePipeline** integrating automated testing steps
- **Apply CDK**: Start using **AWS CDK** to define infrastructure for new projects, moving away from direct Console operations
- **Containerize**: Package applications in Docker and experiment deploying them to **AWS App Runner** for smaller services
- **Set Up Tracing**: Integrate **AWS X-Ray** into applications to monitor latency and communication flows between microservices

---

### Event Experience

The event systematically organized knowledge seamlessly, progressing from mindset formation to tool introduction and operational procedures.

#### Integration Process

- The **"Full CI/CD pipeline walkthrough"** demo was impressive, helping me clearly visualize the entire journey of source code from developer machine to Production environment
- I clearly understood the differences and specific use cases of **ECS versus EKS**, increasing confidence when proposing containerization solutions to the company

#### High Practicality

- Lessons about **Deployment strategies** (like Feature flags, Canary) have high real-world application value, addressing the team's "deployment anxiety"
- The career roadmap guidance at the end provided clear **DevOps** skill development roadmap

#### Some photos from the event

- Add your event photos here

> In summary, the workshop clarified the tight and inseparable connection between Code, Infrastructure as Code, and Observability in modern operations.
