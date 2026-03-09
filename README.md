# Secure AWS Enterprise Architecture

**Cloud Security Engineering Project**

## Overview

This project demonstrates the design and implementation of a **secure AWS enterprise architecture** focused on cloud-native security best practices. The environment was built to simulate how organizations can securely deploy workloads in AWS while enforcing strong identity controls, network segmentation, centralized logging, and threat detection.

The architecture integrates multiple AWS security services to provide **visibility, monitoring, and incident investigation capabilities** across the cloud environment.

The objective of this project is to show how security controls can be embedded into cloud infrastructure from the design stage.

---

# Project Objectives

The primary goals of this project were to:

* Design a **secure AWS network architecture** using VPC segmentation
* Implement **least-privilege IAM policies**
* Enable **centralized logging and monitoring**
* Deploy **threat detection services**
* Simulate security monitoring and investigation workflows
* Demonstrate how AWS services support **incident response and security operations**

---

# Architecture Overview

The environment is designed using a **segmented VPC architecture** with multiple security layers.

Key design principles:

* Network isolation
* Identity security
* Continuous monitoring
* Threat detection
* Centralized logging

Architecture layers include:

* Internet-facing load balancer
* Public subnet for entry points
* Private application subnet
* Isolated database subnet
* Security monitoring layer

---

# Core Security Components

| Component              | Function                                        |
| ---------------------- | ----------------------------------------------- |
| VPC Segmentation       | Isolates workloads and reduces lateral movement |
| IAM Least Privilege    | Limits permissions to only required actions     |
| AWS CloudTrail         | Logs all API activities                         |
| Amazon GuardDuty       | Detects suspicious activity and threats         |
| Amazon CloudWatch      | Monitoring and alerting                         |
| Centralized S3 Logging | Secure log storage for investigations           |

---

# Network Architecture

The architecture separates infrastructure into **three main subnet tiers**:

### Public Subnet

Used for internet-facing resources such as:

* Application Load Balancer
* NAT Gateway
* Bastion access

### Private Subnet

Hosts internal compute resources such as:

* EC2 instances
* Kubernetes worker nodes
* Application services

These resources are **not directly accessible from the internet**.

### Database Subnet

Contains sensitive data services such as:

* Amazon RDS
* Internal data services

Access is restricted to application resources only.

---

# Identity and Access Management

Security for identities is enforced through the **principle of least privilege**.

Key IAM controls implemented:

* IAM roles instead of long-term credentials
* Minimal permissions for compute resources
* Separation of administrative and operational roles
* Access monitoring using CloudTrail logs

Security benefits:

* Prevents privilege escalation
* Limits damage if credentials are compromised
* Enables traceability of actions

---

# Logging and Monitoring

Centralized logging is implemented to support **security investigations and compliance auditing**.

The logging architecture collects:

* AWS API activity logs
* Infrastructure configuration changes
* service access logs
* security findings

All logs are stored in a **centralized encrypted S3 bucket**.

This enables:

* forensic investigations
* security monitoring
* long-term audit retention

---

# Threat Detection

The architecture integrates **Amazon GuardDuty** for continuous threat monitoring.

GuardDuty analyzes:

* CloudTrail logs
* VPC Flow Logs
* DNS activity

Example threats detected:

* credential compromise
* crypto mining activity
* port scanning
* unusual API behavior
* suspicious network connections

---

# Security Monitoring Workflow

Security monitoring follows this detection pipeline:

AWS Services
↓
CloudTrail / Service Logs
↓
CloudWatch Metrics & Alerts
↓
Security Investigation

This workflow allows security teams to detect suspicious behavior and initiate incident response procedures.

---

# Attack Simulation Scenarios

To validate monitoring and logging capabilities, several simulated scenarios were tested.

### Scenario 1 — Suspicious API Activity

Simulation:

* unauthorized API calls performed using test credentials

Detection:

* CloudTrail logged the activity
* CloudWatch monitoring generated alerts

---

### Scenario 2 — Credential Misuse

Simulation:

* API access from unusual locations

Detection:

* GuardDuty generated anomaly alerts

---

# Security Controls Implemented

| Security Control        | Purpose                       |
| ----------------------- | ----------------------------- |
| VPC segmentation        | restricts network access      |
| IAM least privilege     | prevents unauthorized actions |
| CloudTrail logging      | provides audit trail          |
| GuardDuty monitoring    | detects malicious behavior    |
| centralized log storage | supports investigation        |
| CloudWatch alerts       | enables real-time monitoring  |

---

# Infrastructure Deployment

Infrastructure for this project was defined using **Infrastructure as Code (Terraform)**.

Deployment includes configuration for:

* AWS VPC
* subnet segmentation
* IAM roles and policies
* CloudTrail logging
* GuardDuty detection
* centralized log storage

This approach enables:

* repeatable infrastructure deployment
* version control for cloud infrastructure
* automated security configuration

---

# Repository Structure

```
aws-secure-enterprise-architecture
│
├── architecture
│   └── aws-security-architecture.png
│
├── terraform
│   ├── vpc.tf
│   ├── iam.tf
│   ├── logging.tf
│   └── monitoring.tf
│
├── documentation
│   └── project-details.md
│
└── README.md
```

---

# Lessons Learned

Key insights from this project:

* Proper **network segmentation significantly reduces attack surface**
* **centralized logging is essential for incident investigations**
* **least privilege IAM policies are critical for cloud security**
* threat detection services improve **visibility into suspicious activity**

These principles are fundamental for building secure cloud infrastructure.

---

# Future Improvements

Potential enhancements to extend this project include:

* integration with **AWS Security Hub**
* automated incident response workflows
* SIEM integration for advanced threat analysis
* infrastructure compliance scanning
* automated security posture management

---

# Skills Demonstrated

This project demonstrates practical experience with:

* AWS cloud security architecture
* infrastructure security design
* identity and access management
* cloud threat detection
* centralized logging strategies
* security monitoring and incident investigation
* infrastructure as code

---

# Author

Cloud Security Engineering Portfolio Project

Focus Areas:

* Cloud Security
* Kubernetes Security
* Threat Modeling
* Incident Response
* Security Architecture
