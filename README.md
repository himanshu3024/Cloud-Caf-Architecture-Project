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

## 📡 MISSION PROTOCOL
To evolve the café's infrastructure from a simple static page to a highly available, multi-region, automated cloud architecture.

## 🗺️ ARCHITECTURE ROADMAP

### <details><summary>✅ V1: Build a simple online presence for the café</summary>

> **GOAL**: Host a static website on Amazon S3.
> **STATUS**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION
1.  **Infrastructure Provisioning**
    *   Created S3 Bucket in `us-east-1` (N. Virginia).
    *   Configured **Static Website Hosting** endpoint.

2.  **Security Configuration**
    *   *Public Access*: **ENABLED** (Unblocked public access settings).
    *   *Access Control*: Configured **Bucket Policy** for anonymous `s3:GetObject` access.

3.  **Deployment**
    *   Uploaded `index.html` and assets (`css/`, `images/`).
    *   Verified site integrity via public endpoint.

#### 📸 VISUAL EVIDENCE
| Site Preview | S3 Config | Policy |
| :---: | :---: | :---: |
| ![Site](placeholder_site.png) | ![Config](placeholder_config.png) | ![Policy](placeholder_policy.png) |

</details>

### <details><summary>🚧 V2: Support dynamic content and online ordering</summary>

> **GOAL**: Deploy the web application and database on Amazon EC2.
> **STATUS**: **PENDING**

*   **Objective**: Transition from static hosting to dynamic compute.
*   **Tech Stack**: Amazon EC2.
</details>

### <details><summary>🚧 V3: Reduce maintenance load and improve data security</summary>

> **GOAL**: Separate the web and database layers. Migrate the database to Amazon RDS in a private subnet.
> **STATUS**: **PENDING**

*   **Objective**: Decouple architecture and enhance database security.
*   **Tech Stack**: Amazon RDS, Private Subnets.
</details>

### <details><summary>🚧 V4: Strengthen the security of the application</summary>

> **GOAL**: Use Amazon VPC features to configure and secure public and private subnets.
> **STATUS**: **PENDING**

*   **Objective**: Implement robust network isolation.
*   **Tech Stack**: Amazon VPC, Public/Private Subnets.
</details>

### <details><summary>🚧 V5: Handle higher traffic and achieve high availability</summary>

> **GOAL**: Add a load balancer, enable auto scaling on EC2 instances, and distribute compute and database resources across two Availability Zones.
> **STATUS**: **PENDING**

*   **Objective**: Ensure high availability and elasticity.
*   **Tech Stack**: ELB (Load Balancer), Auto Scaling Groups, Multi-AZ.
</details>

### <details><summary>🚧 V6: Automate deployments for consistency and multi-Region expansion</summary>

> **GOAL**: Build a version controlled CloudFormation template to deploy network and application layers. Deploy the CloudFormation stack to another Region.
> **STATUS**: **PENDING**

*   **Objective**: Infrastructure as Code (IaC) and Disaster Recovery.
*   **Tech Stack**: AWS CloudFormation, Multi-Region.
</details>

### <details><summary>🚧 V7: Add reporting while lowering maintenance, improving performance, and cutting costs</summary>

> **GOAL**: Deploy Lambda functions that connect to Amazon RDS and generate scheduled reports.
> **STATUS**: **PENDING**

*   **Objective**: Serverless automation and reporting.
*   **Tech Stack**: AWS Lambda, Amazon RDS.
</details>

---

```bash
>_ END OF LOG
```
