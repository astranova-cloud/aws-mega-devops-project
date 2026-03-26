# AWS DevOps Mega Project

##  Networking Layer — VPC (Day 1)

---

##  Overview

This repository represents the **networking foundation** of the AWS DevOps Mega Project, focusing on designing a secure, scalable, and highly available Virtual Private Cloud (VPC).

The implementation follows real-world enterprise networking practices by creating a fully controlled environment with public and private subnet segmentation, secure routing, and controlled internet access.

---

##  Organizational Context

This project is part of the **astranova-cloud** organization, where multiple systems are structured to reflect a real enterprise setup.

- DevSecOps Platform (existing system)  
- AWS DevOps Mega Project (this implementation)  

Each phase of the project is maintained in a separate repository to ensure modularity, clarity, and maintainability of infrastructure components.

---

##  Architecture Overview

The networking layer is designed using a **multi-tier and multi-AZ architecture**:

- **VPC**: Custom Virtual Private Cloud with defined CIDR range  
- **Public Subnets**: For internet-facing resources (NAT, Load Balancer, Bastion)  
- **Private Subnets**: For backend services (Application and Database layers)  
- **Internet Gateway**: Enables internet access for public subnets  
- **NAT Instance**: Enables secure outbound internet access for private subnets  
- **Route Tables**: Controls traffic routing within the VPC  
- **VPC Endpoint (S3)**: Secure internal access to S3 without internet  

---

##  Key Objectives

- Design custom VPC without using default AWS setup  
- Implement subnet segmentation (public and private)  
- Enable secure and controlled internet access  
- Achieve high availability using Multi-AZ architecture  
- Build a strong networking foundation for upcoming layers  

---

##  Implementation Approach

The networking layer was implemented step-by-step to ensure clarity and correctness:

| Step | Component |
|------|----------|
| Step 1 | Created custom VPC (10.0.0.0/16) |
| Step 2 | Designed subnets across multiple AZs |
| Step 3 | Configured Internet Gateway |
| Step 4 | Implemented public and private route tables |
| Step 5 | Deployed NAT Instance for private subnet access |
| Step 6 | Configured security groups for controlled access |
| Step 7 | Validated connectivity using real-time testing |

---

##  CIDR Design

| Component         | CIDR Block     |
|------------------|---------------|
| VPC              | 10.0.0.0/16   |
| Public Subnet 1  | 10.0.1.0/24   |
| Public Subnet 2  | 10.0.2.0/24   |
| Private Subnet 1 | 10.0.3.0/24   |
| Private Subnet 2 | 10.0.4.0/24   |

---

##  Security Design

- Private subnets are not directly accessible from the internet  
- SSH access is restricted via security groups  
- NAT instance is used for controlled outbound traffic  
- Internal communication allowed only within VPC CIDR  
- No direct exposure of backend services  

---

##  High Availability

- Subnets distributed across multiple Availability Zones (ap-south-1a, ap-south-1b)  
- Fault-tolerant network design  
- Isolation of public and private workloads  

---

##  Validation

Connectivity tests performed:

```bash
ping google.com
curl google.com
