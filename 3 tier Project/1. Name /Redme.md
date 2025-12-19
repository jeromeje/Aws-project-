# AWS 3-Tier Architecture – AWS Services

## What is AWS 3-Tier Architecture?
AWS 3-Tier Architecture is a cloud design pattern that separates an application into three logical layers to achieve **scalability, security, high availability, and maintainability**.

### The Three Tiers
1. Presentation Layer (Web Tier)
2. Application Layer (App Tier)
3. Database Layer (Data Tier)

---

## 1. Presentation Layer (Web Tier)

### Purpose
- Handles user interface
- Accepts HTTP/HTTPS requests from users
- Forwards requests to the Application Layer

### AWS Services
- **Amazon Route 53** – DNS routing
- **Amazon CloudFront** – Content Delivery Network (CDN)
- **AWS WAF** – Web Application Firewall
- **Application Load Balancer (ALB)** – Distributes incoming traffic
- **Amazon EC2** – Web servers (Apache/Nginx)
- **Amazon S3** – Static website hosting

### Network Setup
- Deployed in **Public Subnets**
- Internet-facing Load Balancer

### Flow Example




---

## 2. Application Layer (App Tier)

### Purpose
- Contains business logic
- Processes requests from the Web Tier
- Communicates with the Database Layer

### AWS Services
- **Amazon EC2** – Application servers
- **Auto Scaling Group (ASG)** – Automatic scaling
- **Internal Application Load Balancer** – Load distribution
- **AWS Lambda** – Serverless logic (optional)
- **Amazon ECS / EKS** – Container orchestration
- **Amazon SQS / SNS** – Asynchronous messaging

### Network Setup
- Deployed in **Private Subnets**
- No direct internet access
- Accessible only from Web Tier

### Security
- Security Groups allow traffic only from the Web Tier

---

## 3. Database Layer (Data Tier)

### Purpose
- Stores application data securely
- Ensures data durability and availability

### AWS Services
- **Amazon RDS** (MySQL, PostgreSQL, Oracle, SQL Server)
- **Amazon Aurora** – High-performance relational DB
- **Amazon DynamoDB** – NoSQL database
- **Amazon ElastiCache** – In-memory caching
- **Amazon S3** – Backup and object storage

### Network Setup
- Deployed in **Private Subnets**
- No internet access
- Multi-AZ enabled for high availability

### Security
- Accessible only from the Application Layer

---

## Overall Architecture Flow




---

## Supporting AWS Services

### Networking
- Amazon VPC
- Public and Private Subnets
- Route Tables
- Internet Gateway
- NAT Gateway

### Security
- AWS IAM
- Security Groups
- Network ACLs
- AWS KMS

### Monitoring & Logging
- Amazon CloudWatch
- AWS CloudTrail

### Backup & Recovery
- AWS Backup
- RDS Snapshots

### CI/CD
- AWS CodeCommit
- AWS CodeBuild
- AWS CodeDeploy
- AWS CodePipeline

---

## Key Interview Points
- Web Tier runs in **public subnets**
- App and DB tiers run in **private subnets**
- Internet-facing ALB for Web Tier
- Internal ALB for App Tier
- Auto Scaling ensures elasticity
- Multi-AZ ensures high availability
- Least privilege security model

---

## Real-World Example
**E-Commerce Application**
- Frontend: React on S3 + CloudFront
- Backend: Node.js on EC2 / ECS
- Database: Amazon RDS (MySQL)
- Cache: Amazon ElastiCache (Redis)

---

## Summary
AWS 3-Tier Architecture is a best-practice design that separates concerns, improves security, enables scaling, and ensures high availability using managed AWS services.







# AWS Services Overview (Table Format)

| AWS Service | Full Name | Purpose | Common Use Cases |
|------------|-----------|---------|------------------|
| **VPC** | Amazon Virtual Private Cloud | Creates an isolated virtual network to launch AWS resources securely | Creating public/private subnets, network isolation, secure application hosting |
| **EC2** | Amazon Elastic Compute Cloud | Provides scalable virtual servers for running applications | Hosting web/app servers, backend services, custom workloads |
| **IAM** | Identity and Access Management | Manages users, roles, and permissions to securely access AWS resources | User authentication, role-based access control, security policies |
| **S3** | Amazon Simple Storage Service | Object storage service with high durability and scalability | Static website hosting, backups, logs, media storage |
| **RDS** | Amazon Relational Database Service | Managed relational database service | MySQL, PostgreSQL, Oracle, SQL Server databases |
| **Certificate Manager** | AWS Certificate Manager (ACM) | Provides and manages SSL/TLS certificates | Enabling HTTPS for ALB, CloudFront, and APIs |
| **Route 53** | Amazon Route 53 | Scalable DNS and domain management service | Domain registration, DNS routing, health checks |

---

## Notes
- These services are commonly used together in **AWS 3-Tier Architecture**
- IAM secures access to all services
- VPC provides networking foundation
- EC2 hosts applications
- RDS stores structured data
- S3 stores static and unstructured data
- ACM enables secure HTTPS
- Route 53 handles DNS routing
