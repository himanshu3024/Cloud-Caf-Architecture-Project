# PROJECT: CAFÉ CLOUD
### *The Evolving Café Architecture*

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazon-aws) ![Status](https://img.shields.io/badge/STATUS-V4%20COMPLETE-success?style=for-the-badge) ![Operator](https://img.shields.io/badge/OPERATOR-HIMANSHU-blue?style=for-the-badge)


---

## 🔭 PROJECT SYNOPSIS
**Café Cloud** is a comprehensive cloud engineering project demonstrating the end-to-end migration and evolution of a business application on AWS.

Starting from a humble **static website (V1)**, this project documents the iterative transformation of the café's infrastructure into a **dynamic, highly available, and fault-tolerant system**. The journey covers the migration to **EC2 compute (V2)**, database decoupling with **RDS (V3)**, network hardening via **VPC (V4)**, scaling with **ELB & ASG (V5)**, multi-region automation via **CloudFormation (V6)**, and finally, optimizing with **Serverless Lambda (V7)**.

This repository serves as a master log of every architectural decision, configuration, and deployment step taken to modernize the business.

---

## 📖 SCENARIO & BACKGROUND

### ☕ The Business Case
**Frank and Martha** are a husband-and-wife team who own and operate a small, beloved café in a large city, famous for its high-quality desserts and coffee. They are assisted by their daughter, **Sofía**, and their employee, **Himanshu** (a post grad student at George Brown College, Me basically).

Despite their reputation among locals, the café lacks a marketing strategy and relies entirely on foot traffic and word-of-mouth. They have **zero web presence** and currently use **no cloud computing services**.

### 💡 The Transformation
Sofía has proposed expanding community awareness to showcase what the café has to offer. The goal is to launch a website that provides:
*   Visual showcases of their desserts and coffee.
*   Business details (location, hours, telephone number).

I have been tasked with leading this digital transformation.

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

![Each Layer of the Architecture](assets/Project%20Details.png)

<details>
<summary><strong>✅ V1: Creating a Static Website for the Café</strong></summary>

<br>

> **Business Goal**: Launch a website to visually showcase offerings and provide location/hours.
> **Technical Goal**: Host a static website on Amazon S3.
> **Status**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION
![Architecture Diagram](V1/architectural%20diagram/mod-4-challenge-lab-cafe-static-website-architecture.png)

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
> ![Website Live](V1/screenshots/Screenshot%201%20-%20Website%20Live%20Preview.png)
> *The café website running live on the S3 endpoint.*

> **2. S3 Bucket Configuration**
> ![S3 Config](V1/screenshots/Screenshot%202%20-%20S3%20Bucket%20Configuration.png)
> *Showing Static Website Hosting enabled.*

> **3. Bucket Policy**
> ![Bucket Policy](V1/screenshots/Screenshot%203%20-%20Bucket%20Policy.png)
> *JSON policy granting public read access.*

> **4. Replication Policy**
> ![Replication Policy](V1/screenshots/Screenshot%204%20-%20Replication%20policy.png)
> *Cross-Region Replication configuration.*

> **5. Lifecycle Rule**
> ![Lifecycle Rule](V1/screenshots/Screenshot%205%20-%20Lifecycle%20rule%20for%20S3%20Bucket.png)
> *Lifecycle rule to transition objects to Standard-IA.*

</details>

<details>
<summary><strong>✅ V2: Add the Support dynamic content and online ordering</strong></summary>

<br>

> **Business Goal**: Allow customers to place orders online and provide staff the ability to view submitted orders.
> **Technical Goal**: Deploy a LAMP stack application on Amazon EC2, integrate with AWS Secrets Manager, and implement a Multi-Region Disaster Recovery strategy using AMIs.
> **Status**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION

![Architecture Diagram](V2/architectural%20diagram/m5ch-lab-end-arch.png)
I have successfully completed the following tasks to launch the dynamic version of the website:

**1. Environment Configuration (LAMP Stack)**
*   **OS**: Amazon Linux (Red Hat derivative).
*   **Web Server**: Apache HTTP Server (configured on port 8000).
*   **Database**: MariaDB 10.5 (installed and enabled).
*   **IDE**: Connected to VS Code Server running on the EC2 instance.
*   **Permissions**: Configured file ownership (`chown`) and symlinks to allow editing web files directly from the IDE.

**2. Application Deployment**
*   Downloaded and extracted the café application source code and database scripts.
*   Installed the **AWS SDK for PHP** to allow the application to interact with AWS services.
*   **Secrets Management**:
    *   Used `set-app-parameters.sh` to store sensitive configuration (DB credentials) in **AWS Secrets Manager**.
    *   Configured the application to retrieve these secrets at runtime.
*   **Database Setup**:
    *   Ran `create-db.sh` to initialize the `cafe_db` schema and tables.
    *   Verified database connectivity using the MySQL CLI.

**3. Security & IAM**
*   Analyzed the **IAM Role** (`CafeRole`) attached to the EC2 instance.
*   Verified the role grants permission to read from Secrets Manager, resolving initial application permission errors.
*   Configured **Security Groups** to allow inbound traffic on TCP port 8000 (Web) and 22 (SSH).

**4. Multi-Region Expansion (Disaster Recovery)**
*   **AMI Creation**: Created a custom Amazon Machine Image (`CafeServer`) from the fully configured development instance in `us-east-1`.
*   **Production Deployment**:
    *   Launched a new instance (`ProdCafeServer`) in the **Oregon Region (us-west-2)** using the custom AMI.
    *   Configured the new instance with the `CafeRole` and appropriate Security Groups.
*   **Region-Specific Configuration**:
    *   Updated the application parameters in `us-west-2` to reflect the new region's public DNS.
    *   Verified that the production site operates independently of the development site.



#### 📸 VISUAL EVIDENCE
> **1. Online Menu & Ordering**
> ![Online Menu](V2/screenshots/Screenshot%202%20-%20Cafe%20Menu.png)
> *The dynamic menu allowing customers to place orders.*

> **2. Order Confirmation**
> ![Order Success](V2/screenshots/Screenshot%203%20-%20Order%20history%20depicting%20that%20Website%20works.png)
> *Confirmation message after placing an order.*

> **3. Multi-Region Instances**
> ![EC2 Console](V2/screenshots/Screenshot%204%20-%20New%20Instance%20ProdServer%20created%20using%20the%20AMI%20in%20different%20region.png)
> *Showing instances running in both N. Virginia and Oregon.*

> **4. Database Configuration**
> ![Database Config](V2/screenshots/Screenshot%201%20-%20Database%20Information%20in%20Code%20Editor.png)
> *Database connection details configured in the application.*

</details>

<details>
<summary><strong>✅ V3: Migrating a Database to Amazon RDS</strong></summary>

<br>

> **Business Goal**: Secure customer data and reduce manual server maintenance.
> **Technical Goal**: Separate the web and database layers. Migrate the database to Amazon RDS in a private subnet.
> **Status**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION
![Architecture Diagram](V3/architectural%20diagram/m6ch-lab-end-arch.png)

I have successfully completed the following tasks to migrate the database:

**1. RDS Instance Creation**
*   **Service**: Amazon RDS (MariaDB)
*   **Instance**: `db.t3.micro` (Dev/Test template)
*   **Configuration**:
    *   Created in `Lab VPC` with `lab-db-subnet-group`.
    *   Configured Security Group `dbSG` to allow traffic on port 3306.
    *   Set up Master credentials and initial database parameters.

**2. Data Analysis & Export**
*   Connected to the `CafeServer` EC2 instance via **AWS Systems Manager Session Manager**.
*   Analyzed the existing local MariaDB database (`cafe_db`) and verified order history.
*   Exported the existing data using `mysqldump` to `CafeDbDump.sql`.

**3. Data Migration**
*   Established connectivity from the EC2 instance to the new RDS instance.
*   Imported the `CafeDbDump.sql` data into the RDS instance.
*   Verified data integrity by querying tables (`order`, `order_item`) on the new RDS database.

**4. Application Reconfiguration**
*   Updated **AWS Secrets Manager** (`/cafe/dbPassword`, etc.) with the new RDS endpoint and credentials.
*   The PHP application automatically picked up the new connection details.
*   Stopped the local MariaDB service on EC2 to ensure the app is using the RDS instance.
*   Verified the application functionality by placing new orders and viewing order history.

#### 📸 VISUAL EVIDENCE
> **1. RDS Instance Details**
> ![RDS Details](V3/screenshots/Screenshot%201%20-%20New%20RDS%20Details.png)
> *The newly created MariaDB instance in Amazon RDS.*

> **2. EC2 Database Status**
> ![EC2 DB Status](V3/screenshots/Screenshot%202%20-%20EC2%20Session%20Manager%20DB%20Status.png)
> *Checking the status of the local database before migration.*

> **3. Existing Data Verification**
> ![Show Tables](V3/screenshots/Screenshot%203%20-%20MySQL%20Show%20DB%20Tables.png)
> *Verifying tables in the local database.*

> **4. Imported Data Verification**
> ![Imported Data](V3/screenshots/Screenshot%204%20-%20Imported%20RDS%20DB%20Tables%20and%20Count.png)
> *Confirming data count in the new RDS instance after import.*

> **5. Secrets Manager Update**
> ![Secrets Update](V3/screenshots/Screenshot%205%20-%20Secrets%20List%20After%20Update.png)
> *Updating database connection secrets for the application.*

</details>

<details>
<summary><strong>✅ V4: Creating a VPC Networking Environment for the Café</strong></summary>

<br>

> **Business Goal**: Ensure the application is protected against network threats by isolating resources.
> **Technical Goal**: Create a VPC with public and private subnets, a bastion host for secure access, and a NAT gateway for internet connectivity.
> **Status**: **COMPLETED**

#### ⚙️ TECHNICAL IMPLEMENTATION
![Architecture Diagram](V4/architectural%20diagram/module-7-challenge-lab-final-architecture.png)

I have successfully completed the following tasks to secure the network environment:

**1. Public Subnet & Internet Gateway**
*   **VPC**: Used the existing `Lab VPC`.
*   **Public Subnet**: Created `Public Subnet` (10.0.0.0/24) in `us-east-1a`.
*   **Internet Gateway**: Created and attached an IGW to the VPC.
*   **Routing**: Updated the public route table to route `0.0.0.0/0` to the Internet Gateway.

**2. Bastion Host Setup**
*   **Instance**: Launched `Bastion Host` (t2.micro, Amazon Linux 2023) in the `Public Subnet`.
*   **Security**: Created `Bastion Host SG` allowing SSH (Port 22) only from `My IP`.
*   **Key Pair**: Used `vockey` for access.

**3. Private Subnet & NAT Gateway**
*   **Private Subnet**: Created `Private Subnet` (10.0.1.0/24) in `us-east-1a`.
*   **NAT Gateway**: Deployed `Lab NAT Gateway` in the `Public Subnet` with an Elastic IP.
*   **Routing**: Created `Private Route Table` routing `0.0.0.0/0` to the NAT Gateway and associated it with the `Private Subnet`.

**4. Private Instance & Security**
*   **Instance**: Launched `Private Instance` (t2.micro, Amazon Linux 2023) in the `Private Subnet`.
*   **Key Pair**: Created a new key pair `vockey2` for this instance.
*   **Security**: Created `Private Instance SG` allowing SSH (Port 22) only from the `Bastion Host SG`.

**5. SSH Passthrough & Connectivity**
*   **Agent Forwarding**: Configured SSH agent forwarding (Pageant/ssh-agent) to pass the `vockey2` key through the Bastion Host.
*   **Verification**: Successfully connected from local machine -> Bastion Host -> Private Instance.
*   **Internet Test**: Verified the Private Instance can access the internet (ping 8.8.8.8) via the NAT Gateway.

**6. Network ACLs**
*   **Custom NACL**: Created `Lab Network ACL` and associated it with the subnets.
*   **Testing**: Launched a `Test Instance` in the Public Subnet allowing ICMP.
*   **Traffic Control**: Configured the NACL to DENY ICMP traffic from the Private Subnet to the Test Instance, verifying that the ping command stops responding.

#### 📸 VISUAL EVIDENCE
> **1. Bastion Host Creation**
> ![Bastion Host](V4/screenshots/Screenshot%201%20-%20Created%20New%20Bastion%20Host.png)
> *Bastion Host running in the Public Subnet.*

> **2. Bastion Access**
> ![Bastion Access](V4/screenshots/Screenshot%202-%20Accessing%20the%20Bastion%20Host.png)
> *Successful SSH connection to the Bastion Host.*

> **3. NAT Gateway**
> ![NAT Gateway](V4/screenshots/Screenshot%203%20-%20Created%20the%20NAT%20Gateway.png)
> *NAT Gateway created to allow internet access for private resources.*

> **4. Route Table**
> ![Route Table](V4/screenshots/Screenshot%204%20-%20Created%20the%20Route%20Table%20for%20NAT%20gateway.png)
> *Private Route Table directing traffic to the NAT Gateway.*

> **5. Private Instance**
> ![Private Instance](V4/screenshots/Screenshot%205%20-%20Private%20Instance%20in%20Private%20Subnet.png)
> *Private Instance running securely in the Private Subnet.*

> **6. Private Access**
> ![Private Access](V4/screenshots/Screenshot%206%20-%20Accessing%20the%20Private%20Instance%20using%20Bastion%20Host.png)
> *Accessing the Private Instance via the Bastion Host using SSH Agent Forwarding.*

</details>

<details>
<summary><strong>🚧 V5: Creating a Scalable and Highly Available Environment for the Café</strong></summary>

<br>

> **Business Goal**: Ensure the website stays online during traffic spikes and server failures.
> **Technical Goal**: Add a load balancer, enable auto scaling on EC2 instances, and distribute compute and database resources across two Availability Zones.
> **Status**: **PENDING**

*   **Objective**: Ensure high availability and elasticity.
*   **Tech Stack**: ELB (Load Balancer), Auto Scaling Groups, Multi-AZ.

</details>

<details>
<summary><strong>🚧 V6: Automating Infrastructure Deployment</strong></summary>

<br>

> **Business Goal**: Quickly launch the café website in new regions as the business expands globally.
> **Technical Goal**: Build a version controlled CloudFormation template to deploy network and application layers. Deploy the CloudFormation stack to another Region.
> **Status**: **PENDING**

*   **Objective**: Infrastructure as Code (IaC) and Disaster Recovery.
*   **Tech Stack**: AWS CloudFormation, Multi-Region.

</details>

<details>
<summary><strong>🚧 V7: Implementing a Serverless Architecture for the Café</strong></summary>

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
├── v2-dynamic-ec2/     # (Completed) EC2 UserData & Scripts
├── v6-cloudformation/  # (Pending) IaC Templates
└── assets/             # Architecture diagrams and screenshots
```

---
