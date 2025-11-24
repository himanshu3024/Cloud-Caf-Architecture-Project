# Cloud-Caf-Architecture-Project

# ☕ Cloud Café Architecture Project

A complete journey of building and evolving a cloud-based café application on AWS, from a simple static website to a fully automated, scalable, and cost-optimized solution.

## 📋 Project Overview

This project demonstrates the step-by-step evolution of a small business café application through seven distinct phases. Each version builds upon the previous one, introducing new AWS services and architectural best practices to solve real-world business challenges.

**Key Focus Areas:**
- Progressive cloud architecture design
- Security and networking best practices
- High availability and disaster recovery
- Cost optimization and automation
- Serverless computing

## 🎯 Project Goals

- Transform a basic website into a production-ready cloud application
- Implement industry-standard security practices
- Build resilient and scalable infrastructure
- Automate deployment and management processes
- Optimize operational costs while maintaining performance

## 🏗️ Architecture Evolution

<details>
<summary><b>Version 1: Static Website Hosting</b></summary>

**Business Goal:** Build a static website for a small business

**Technical Implementation:**
- Host the website on Amazon S3

**AWS Services Used:**
- Amazon S3

**Skills Demonstrated:**
- Static website hosting
- S3 bucket configuration

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 2: Dynamic Content & Online Ordering</b></summary>

**Business Goal:** Update the website to support dynamic content and online ordering

**Technical Implementation:**
- Deploy web application and database on Amazon EC2

**AWS Services Used:**
- Amazon EC2

**Skills Demonstrated:**
- EC2 instance deployment
- Database setup
- Dynamic web application hosting

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 3: Managed Database Migration</b></summary>

**Business Goal:** Reduce the effort to maintain the database and secure its data

**Technical Implementation:**
- Separate web and database layers
- Migrate the database to Amazon RDS on a private subnet

**AWS Services Used:**
- Amazon EC2
- Amazon RDS

**Skills Demonstrated:**
- Database migration
- Network segmentation
- Managed database services

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 4: Enhanced Security</b></summary>

**Business Goal:** Enhance the security of the web application

**Technical Implementation:**
- Use Amazon VPC features to configure and secure public and private subnets

**AWS Services Used:**
- Amazon VPC
- Security Groups
- Network ACLs

**Skills Demonstrated:**
- VPC design and configuration
- Public and private subnet architecture
- Network security implementation

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 5: High Availability & Auto Scaling</b></summary>

**Business Goal:** Ensure the website can handle increased traffic and remain highly available and resilient to failure

**Technical Implementation:**
- Add a load balancer
- Implement auto scaling on EC2 instances
- Distribute compute and database instances across two Availability Zones

**AWS Services Used:**
- Elastic Load Balancer (ELB)
- Auto Scaling Groups
- Multi-AZ RDS
- CloudWatch

**Skills Demonstrated:**
- Load balancing configuration
- Auto scaling policies
- Multi-AZ architecture
- High availability design

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 6: Infrastructure as Code</b></summary>

**Business Goal:** Automate deployments so the café can consistently deploy, manage, and update resources across Regions

**Technical Implementation:**
- Build a version-controlled CloudFormation template to deploy the network and application layers
- Deploy the CloudFormation stack to another Region

**AWS Services Used:**
- AWS CloudFormation
- Multi-Region deployment

**Skills Demonstrated:**
- Infrastructure as Code (IaC)
- CloudFormation template development
- Version control integration
- Multi-region deployment

**Screenshots:**
*[Screenshots will be added here]*

</details>

<details>
<summary><b>Version 7: Serverless Reporting</b></summary>

**Business Goal:** Add reporting capabilities while reducing operational burden, improving performance, and reducing costs

**Technical Implementation:**
- Deploy Lambda functions that connect to Amazon RDS database
- Generate reports based on a schedule

**AWS Services Used:**
- AWS Lambda
- Amazon EventBridge/CloudWatch Events
- Amazon RDS

**Skills Demonstrated:**
- Serverless architecture
- Event-driven automation
- Cost optimization
- Lambda-RDS integration

**Screenshots:**
*[Screenshots will be added here]*

</details>

## 🛠️ Technologies & Services

| Category | AWS Services |
|----------|-------------|
| **Compute** | EC2, Lambda, Auto Scaling |
| **Storage** | S3 |
| **Database** | RDS (Multi-AZ) |
| **Networking** | VPC, Subnets, Security Groups, Load Balancer |
| **Automation** | CloudFormation, EventBridge |
| **Monitoring** | CloudWatch |

## 📚 What You'll Learn

- **Cloud Architecture Design:** Build scalable and resilient applications
- **Security Best Practices:** Implement network segmentation and security controls
- **High Availability:** Design multi-AZ architectures with load balancing
- **Cost Optimization:** Transition from always-on to serverless where appropriate
- **Infrastructure as Code:** Automate deployments using CloudFormation
- **Serverless Computing:** Leverage Lambda for event-driven workloads

## 🎓 Prerequisites

- AWS Account (Free Tier eligible)
- Basic understanding of web applications
- Familiarity with cloud computing concepts

## 📈 Project Progression

```
Static Website (S3)
    ↓
Dynamic App (EC2)
    ↓
Managed Database (RDS)
    ↓
Secure Network (VPC)
    ↓
High Availability (Load Balancer + Auto Scaling)
    ↓
Automation (CloudFormation)
    ↓
Serverless (Lambda)
```

## 🚀 Getting Started

Each version of this project builds on the previous one. Start with Version 1 and progress sequentially through each phase. Detailed implementation steps and screenshots are available in each version's section above.

## 📝 Documentation

This project follows AWS best practices and aligns with the AWS Well-Architected Framework pillars:
- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization

## 🤝 Contributing

This is a personal learning project documenting my journey through AWS cloud architecture. Feel free to use this as a reference for your own learning!

## 📄 License

This project is created for educational purposes as part of AWS Academy Cloud Architecting course.

---

**Status:** 🚧 In Progress

*Last Updated: November 2025*
