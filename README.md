# PROJECT: CAFÉ CLOUD
### *The Evolving Café Architecture*

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazon-aws) ![Status](https://img.shields.io/badge/STATUS-V1%20COMPLETE-success?style=for-the-badge) ![Operator](https://img.shields.io/badge/OPERATOR-HIMANSHU-blue?style=for-the-badge)

```bash
>_ SYSTEM BOOT SEQUENCE...
> TARGET: "The Café" (Frank & Martha)
> OPERATOR: Himanshu
> OBJECTIVE: Digital Transformation & Scaling
> CURRENT STATE: V1 ONLINE
```

---

## 🔭 PROJECT SYNOPSIS
**Café Cloud** is a comprehensive cloud engineering project demonstrating the end-to-end migration and evolution of a business application on AWS.

Starting from a humble **static website (V1)**, this project documents the iterative transformation of the café's infrastructure into a **dynamic, highly available, and fault-tolerant system**. The journey covers the migration to **EC2 compute (V2)**, database decoupling with **RDS (V3)**, network hardening via **VPC (V4)**, scaling with **ELB & ASG (V5)**, multi-region automation via **CloudFormation (V6)**, and finally, optimizing with **Serverless Lambda (V7)**.

This repository serves as a master log of every architectural decision, configuration, and deployment step taken to modernize the business.

---

## 📖 SCENARIO & BACKGROUND

### ☕ The Business Case
**Frank and Martha** are a husband-and-wife team who own and operate a small, beloved café in a large city, famous for its high-quality desserts and coffee. They are assisted by their daughter, **Sofía**, and their employee, **Himanshu** (a secondary school student).

Despite their reputation among locals, the café lacks a marketing strategy and relies entirely on foot traffic and word-of-mouth. They have **zero web presence** and currently use **no cloud computing services**.

### 💡 The Transformation
Sofía has proposed expanding community awareness to showcase what the café has to offer. The goal is to launch a website that provides:
*   Visual showcases of their desserts and coffee.
*   Business details (location, hours, telephone number).

**Himanshu** (You) has been tasked with leading this digital transformation.

---

## 🧠 TECHNICAL STRATEGY
This project follows the **AWS Well-Architected Framework**, focusing on five key pillars throughout the evolution:

1.  **Operational Excellence**: Automating deployments (V6, V7).
2.  **Security**: Isolating resources in Private Subnets (V3, V4).
3.  **Reliability**: Implementing Multi-AZ and Cross-Region Replication (V5, V6).
4.  **Performance Efficiency**: Using Auto Scaling and Load Balancing (V5).
5.  **Cost Optimization**: Leveraging Serverless architectures (V7).

---

## 🗺️ ARCHITECTURE ROADMAP

### <details>
<summary><strong>✅ V1: Build a simple online presence for the café</strong></summary>

<br>

> **Business Goal**: Launch a website to visually showcase offerings and provide location/hours.
> **Technical Goal**: Host a static website on Amazon S3.
> **Status**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION
I have successfully completed the following tasks to launch the initial version:

**1. File Extraction & Preparation**
*   Downloaded the lab resources zip file.
*   Extracted `index.html`, `css/`, and `images/` folders.
*   Verified the local structure of the website assets.

**2. S3 Bucket Configuration**
*   **Service**: Amazon S3
*   **Region**: `us-east-1` (N. Virginia)
*   **Bucket Settings**:
    *   **Public Access**: *Unblocked* (Disabled "Block all public access").
    *   **ACLs**: Enabled to allow public read access via Access Control Lists.
    *   **Static Website Hosting**: Enabled.
    *   **Index Document**: Set to `index.html`.

**3. Content Deployment**
*   Uploaded the `index.html` file to the root of the bucket.
*   Uploaded the `css` and `images` folders, maintaining the directory structure.
*   Verified the upload was successful.

**4. Access Control (Bucket Policy)**
*   Implemented a **Bucket Policy** to automatically grant read-only permissions to public anonymous users.
*   **Policy Details**:
    *   *Effect*: `Allow`
    *   *Principal*: `*` (Everyone)
    *   *Action*: `s3:GetObject`
    *   *Resource*: `arn:aws:s3:::<bucket-name>/*`

#### 📸 VISUAL EVIDENCE
> **1. Website Live Preview**
> ![Website Live](placeholder_path_to_website_screenshot.png)
> *The café website running live on the S3 endpoint.*

> **2. S3 Bucket Configuration**
> ![S3 Config](placeholder_path_to_s3_config.png)
> *Showing Static Website Hosting enabled.*

> **3. Bucket Policy**
> ![Bucket Policy](placeholder_path_to_policy.png)
> *JSON policy granting public read access.*

</details>

### <details>
<summary><strong>🚧 V2: Support dynamic content and online ordering</strong></summary>

<br>

> **Business Goal**: Allow customers to place orders online.
> **Technical Goal**: Deploy the web application and database on Amazon EC2.
> **Status**: **PENDING**

*   **Objective**: Transition from static hosting to dynamic compute.
*   **Tech Stack**: Amazon EC2.

</details>

### <details>
<summary><strong>🚧 V3: Reduce maintenance load and improve data security</strong></summary>

<br>

> **Business Goal**: Secure customer data and reduce manual server maintenance.
> **Technical Goal**: Separate the web and database layers. Migrate the database to Amazon RDS in a private subnet.
> **Status**: **PENDING**

*   **Objective**: Decouple architecture and enhance database security.
*   **Tech Stack**: Amazon RDS, Private Subnets.

</details>

### <details>
<summary><strong>🚧 V4: Strengthen the security of the application</strong></summary>

<br>

> **Business Goal**: Ensure the application is protected against network threats.
> **Technical Goal**: Use Amazon VPC features to configure and secure public and private subnets.
> **Status**: **PENDING**

*   **Objective**: Implement robust network isolation.
*   **Tech Stack**: Amazon VPC, Public/Private Subnets.

</details>

### <details>
<summary><strong>🚧 V5: Handle higher traffic and achieve high availability</strong></summary>

<br>

> **Business Goal**: Ensure the website stays online during traffic spikes and server failures.
> **Technical Goal**: Add a load balancer, enable auto scaling on EC2 instances, and distribute compute and database resources across two Availability Zones.
> **Status**: **PENDING**

*   **Objective**: Ensure high availability and elasticity.
*   **Tech Stack**: ELB (Load Balancer), Auto Scaling Groups, Multi-AZ.

</details>

### <details>
<summary><strong>🚧 V6: Automate deployments for consistency and multi-Region expansion</strong></summary>

<br>

> **Business Goal**: Quickly launch the café website in new regions as the business expands globally.
> **Technical Goal**: Build a version controlled CloudFormation template to deploy network and application layers. Deploy the CloudFormation stack to another Region.
> **Status**: **PENDING**

*   **Objective**: Infrastructure as Code (IaC) and Disaster Recovery.
*   **Tech Stack**: AWS CloudFormation, Multi-Region.

</details>

### <details>
<summary><strong>🚧 V7: Add reporting while lowering maintenance, improving performance, and cutting costs</strong></summary>

<br>

> **Business Goal**: Generate automated business reports without managing servers.
> **Technical Goal**: Deploy Lambda functions that connect to Amazon RDS and generate scheduled reports.
> **Status**: **PENDING**

*   **Objective**: Serverless automation and reporting.
*   **Tech Stack**: AWS Lambda, Amazon RDS.

</details>

---

## 🛠️ PREREQUISITES & SETUP
To replicate this project, ensure you have the following:
*   **AWS Account**: Active account with administrative access.
*   **AWS CLI**: Installed and configured with your credentials.
*   **Git**: For version control.

## 📂 REPOSITORY STRUCTURE
```
.
├── README.md           # Project Documentation
├── v1-static-website/  # (Completed) Static assets for S3
├── v2-dynamic-ec2/     # (Pending) EC2 UserData & Scripts
├── v6-cloudformation/  # (Pending) IaC Templates
└── assets/             # Architecture diagrams and screenshots
```

---

```bash
>_ SYSTEM STANDBY...
>_ AWAITING NEXT COMMAND.
```
