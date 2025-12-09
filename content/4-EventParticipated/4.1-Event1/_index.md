---
title: "Event 1"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# **Vietnam Cloud Day 2025:**

# **Ho Chi Minh City Connect Edition for Builders - GenAI and Data Track**

**Location**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Date**: Thursday, September 18, 2025

# Learning Report: "Vietnam Cloud Day 2025: GenAI and Data Track"

### Event Objectives

- Provide an overview of **Agentic AI** and AWS's strategic vision
- Understand how to build a **Unified Data Foundation** to effectively support AI activities and Data Analytics on AWS
- Analyze in detail the GenAI deployment roadmap, **AI Agent Architecture** models, and challenges in moving them to production
- Study the **AI-Driven Development Lifecycle (AI-DLC)** model
- Master core principles of **Security, Risk Management, and Responsible AI** in Generative AI
- Introduce **new AWS services** designed to support AI Agents and maximize business productivity

---

### Speaker List

- **Jun Kai Loke** - Solution Architecture Expert for AI/ML, AWS
- **Kien Nguyen** - Solution Architect, AWS
- **Tamelly Lim** - Storage Solution Architecture Expert, AWS
- **Binh Tran** - Senior Solution Architect, AWS
- **Taiki Dang** - Solution Architect, AWS
- **Christal Poon** - Solution Architecture Expert, AWS

---

### Key Content Highlights

#### Overview of Agentic AI – Jun Kai Loke

- **Agentic AI** is an important strategic trend focusing on creating systems with autonomous capabilities, minimizing human intervention, and automating complex processes at a deep level
- Real-world examples of successful applications: Katalon, Apero, Techcom Securities
- **Amazon Bedrock** serves as the core platform for AI development, supporting:
  - Secure deployment at scale
  - Integration of tools and memory capabilities
  - End-to-end monitoring

#### Building a Unified Data Foundation on AWS – Kien Nguyen

- **Current Challenges**: Many businesses struggle with GenAI deployment due to unprepared data platforms (only 52% of CDOs assess their data platforms as ready, according to HBR), mainly due to data silos, people silos, and separate business units
- **End-to-End Data Strategy** includes three interacting components: **Producers**, **Foundations**, and **Consumers**
- **Essential AWS Data Services**:
  - **Amazon Bedrock** (GenAI platform)
  - **Databases** (RDS and specialized services supporting vector search)
  - **Analytics & ML** (SageMaker, Unified Studio)
  - **Data & AI Governance**
  - **Lake House Architecture** (S3, Redshift Managed Storage, Iceberg Open API)
  - **Amazon DataZone** (Data management and sharing)

#### GenAI Roadmap & AI Agent Architecture – Jun Kai Loke & Tamelly Lim

- AI Agents building blueprint includes: Model & application capabilities, and tool framework
- AWS introduces **Amazon Bedrock AgentCore** to address challenges in moving Agents to production
- **AgentCore** includes: Agent Core Runtime, Agent Core Gateway, Memory, Agent Browser and Code Interpreter, aiming to enhance **security** and **scalability**

#### AI-Driven Development Lifecycle (AI-DLC) – Binh Tran

AI-DLC is a new software development model, maximally automated by AI, consisting of 3 stages:

1. **Inception**: Define context, outline user stories, and plan with work units
2. **Construction**: Code + test, supplement architecture, deploy Infrastructure as Code (IaC) and test
3. **Operation**: Deploy to production using IaC and incident management

#### Security of Generative AI Applications – Taiki Dang

- **Essential Security Elements**: Compliance & Governance, Legal & Privacy, Controls, Risk Management, and Resilience
- **Risk Analysis by Layer**: End-user risks (Hallucination, IP, Legal), fine-tuning risks (data retention), and model provider risks (training data, model construction)
- **Risk Mitigation Strategies**: Use Prompt engineering, Fine-tuning, Retrieval-Augmented Generation (RAG), parameter adjustment, **Bedrock Guardrails**, and prompt security
- Must apply standards such as AWS Well-Architected, MITRE ATLAS, OWASP Top 10 for LLM Apps, NIST AI 600-1, ISO 42001, and EU AI Act

#### AI Agents: Boosting Business Productivity – Christal Poon

- Introduction to AI Agent types: Specialized Agents, Fully-managed Agents, and DIY Agents
- Productivity support services: **Amazon QuickSight** (for business analytics) and **Amazon Q** (providing Dashboards, Reports, Executive summaries, and AI Agent scenarios)

---

### What I Learned

#### Mindset & Strategy

- **Agentic AI** is the next evolution of automation, moving towards autonomous systems with reduced human oversight
- **Strong data platforms** (based on S3, Lake House, Bedrock, SageMaker) are prerequisites for successful GenAI deployment
- **AI-DLC** provides a modern methodology that automates the entire development cycle from planning, coding, testing to deployment

#### Architecture & Technology

- Understanding **AI Agent architecture** and **Amazon Bedrock AgentCore** solutions addresses challenges around security and scalability in production environments
- **Security** must be integrated at every level of the AI stack, from data, model to end-user application, while complying with international standards and regulations

#### Technology Application

- AWS is significantly investing and expanding the **AI Agents & Enterprise AI** ecosystem through services like Amazon Q and QuickSuite (coming soon)

---

### Application to Work

- **Process Optimization**: Research and integrate **AI Agents** into repetitive business tasks to increase efficiency
- **Quality Management**: Use **Amazon Bedrock, Amazon Q, and Guardrails** to control quality, ensure safety, and minimize model "hallucination"
- **Infrastructure Building**: Ensure building a **unified data platform** with clear governance before launching GenAI projects
- **Applying AI-DLC**: Experiment with **AI-DLC** software development model in internal projects to accelerate deployment
- **Business Analysis**: Use **QuickSight and Amazon Q** to quickly create dashboards and insights for leadership and business teams

---

### Event Experience

The workshop provided clear and practical insight into the transition from traditional automation to the **Agentic AI** era. Speakers' presentations provided specific guidance for the GenAI adoption journey in Vietnam. The combination of **AgentCore, Bedrock, AI-DLC, and Amazon Q** painted a comprehensive and powerful picture of the next generation of AI for enterprises, from data platforms, application development, to security and operations.

- Add your event photos here

> Overall, the event not only provided in-depth technical knowledge but also helped shift thinking about how to strategically, responsibly, and safely integrate AI into all aspects of business.

### Speakers

- **Jignesh Shah** – Director, Open Source Databases
- **Erica Liu** – Sr. GTM Specialist, AppMod
- **Fabrianne Effendi** – Assc. Specialist SA, Serverless Amazon Web Services

### Key Highlights

#### Identifying the drawbacks of legacy application architecture

- Long product release cycles → Lost revenue/missed opportunities
- Inefficient operations → Reduced productivity, higher costs
- Non-compliance with security regulations → Security breaches, loss of reputation

#### Transitioning to modern application architecture – Microservices

Migrating to a modular system — each function is an **independent service** communicating via **events**, built on three core pillars:

- **Queue Management**: Handle asynchronous tasks
- **Caching Strategy**: Optimize performance
- **Message Handling**: Flexible inter-service communication

#### Domain-Driven Design (DDD)

- **Four-step method**: Identify domain events → arrange timeline → identify actors → define bounded contexts
- **Bookstore case study**: Demonstrates real-world DDD application
- **Context mapping**: 7 patterns for integrating bounded contexts

#### Event-Driven Architecture

- **3 integration patterns**: Publish/Subscribe, Point-to-point, Streaming
- **Benefits**: Loose coupling, scalability, resilience
- **Sync vs async comparison**: Understanding the trade-offs

#### Compute Evolution

- **Shared Responsibility Model**: EC2 → ECS → Fargate → Lambda
- **Serverless benefits**: No server management, auto-scaling, pay-for-value
- **Functions vs Containers**: Criteria for appropriate choice

#### Amazon Q Developer

- **SDLC automation**: From planning to maintenance
- **Code transformation**: Java upgrade, .NET modernization
- **AWS Transform agents**: VMware, Mainframe, .NET migration

### Key Takeaways

#### Design Mindset

- **Business-first approach**: Always start from the business domain, not the technology
- **Ubiquitous language**: Importance of a shared vocabulary between business and tech teams
- **Bounded contexts**: Identifying and managing complexity in large systems

#### Technical Architecture

- **Event storming technique**: Practical method for modeling business processes
- Use **event-driven communication** instead of synchronous calls
- **Integration patterns**: When to use sync, async, pub/sub, streaming
- **Compute spectrum**: Criteria for choosing between VM, containers, and serverless

#### Modernization Strategy

- **Phased approach**: No rushing — follow a clear roadmap
- **7Rs framework**: Multiple modernization paths depending on the application
- **ROI measurement**: Cost reduction + business agility

### Applying to Work

- **Apply DDD** to current projects: Event storming sessions with business teams
- **Refactor microservices**: Use bounded contexts to define service boundaries
- **Implement event-driven patterns**: Replace some sync calls with async messaging
- **Adopt serverless**: Pilot AWS Lambda for suitable use cases
- **Try Amazon Q Developer**: Integrate into the dev workflow to boost productivity

### Event Experience

Attending the **“GenAI-powered App-DB Modernization”** workshop was extremely valuable, giving me a comprehensive view of modernizing applications and databases using advanced methods and tools. Key experiences included:

#### Learning from highly skilled speakers

- Experts from AWS and major tech organizations shared **best practices** in modern application design.
- Through real-world case studies, I gained a deeper understanding of applying **DDD** and **Event-Driven Architecture** to large projects.

#### Hands-on technical exposure

- Participating in **event storming** sessions helped me visualize how to **model business processes** into domain events.
- Learned how to **split microservices** and define **bounded contexts** to manage large-system complexity.
- Understood trade-offs between **synchronous and asynchronous communication** and integration patterns like **pub/sub, point-to-point, streaming**.

#### Leveraging modern tools

- Explored **Amazon Q Developer**, an AI tool for SDLC support from planning to maintenance.
- Learned to **automate code transformation** and pilot serverless with **AWS Lambda** to improve productivity.

#### Networking and discussions

- The workshop offered opportunities to exchange ideas with experts, peers, and business teams, enhancing the **ubiquitous language** between business and tech.
- Real-world examples reinforced the importance of the **business-first approach** rather than focusing solely on technology.

#### Lessons learned

- Applying DDD and event-driven patterns reduces **coupling** while improving **scalability** and **resilience**.
- Modernization requires a **phased approach** with **ROI measurement**; rushing the process can be risky.
- AI tools like Amazon Q Developer can significantly **boost productivity** when integrated into the current workflow.

#### Some event photos

_Add your event photos here_

> Overall, the event not only provided technical knowledge but also helped me reshape my thinking about application design, system modernization, and cross-team collaboration.
