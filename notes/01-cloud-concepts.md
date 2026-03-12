# Day 1 – Cloud Concepts

**Study Time:** 4 hours  
**Date:** 2026-03-09  

Topics covered:

- Cloud fundamentals
- AWS global infrastructure
- Cloud service models
- Shared responsibility model

---

# Table of Contents

1. Hour 1 – Cloud Fundamentals  
2. Hour 2 – AWS Global Infrastructure  
3. Hour 3 – Cloud Service Models  
4. Hour 4 – AWS Shared Responsibility Model  
5. Day 1 Self Test  
6. Day 1 Summary  

---

# Hour 1 – Cloud Fundamentals

## What is Cloud Computing

Cloud computing means using computing resources such as servers, storage, databases, and networking over the internet instead of owning physical hardware.

Traditional infrastructure:

Company → Buy hardware → Install → Maintain → Replace every few years

Cloud model:

Company → Rent infrastructure from cloud provider → Pay only for usage

---

## Key Benefits of Cloud Computing

1. **Trade Capital Expense (CAPEX) for Operational Expense (OPEX)**  
   Instead of purchasing expensive hardware upfront, organizations pay only for the resources they use.

2. **Benefit from Massive Economies of Scale**  
   Large cloud providers purchase infrastructure at massive scale, reducing overall cost.

3. **Stop Guessing Capacity**  
   Cloud platforms allow automatic scaling when demand increases.

4. **Increase Speed and Agility**  
   Servers and resources can be provisioned in minutes instead of weeks.

5. **Stop Spending Money Running Data Centers**  
   Cloud providers manage data centers, power, cooling, and hardware maintenance.

6. **Go Global in Minutes**  
   Applications can be deployed in multiple geographic regions quickly.

---

## Essential Cloud Characteristics

1. On-demand self service  
2. Broad network access  
3. Resource pooling  
4. Rapid elasticity  
5. Measured service  

---

## Cloud Deployment Models

| Model | Description |
|------|-------------|
| Public Cloud | Infrastructure owned and operated by a cloud provider |
| Private Cloud | Dedicated infrastructure used by a single organization |
| Hybrid Cloud | Combination of on-premise infrastructure and cloud |

---

# Hour 2 – AWS Global Infrastructure

AWS operates a global network of data centers designed for high availability and low latency.

## Regions

A **Region** is a geographic area where AWS operates infrastructure.

Examples:

- us-east-1 (Northern Virginia)
- us-west-2 (Oregon)
- eu-west-1 (Ireland)

Each region is isolated from other regions.

Reasons:

- fault isolation
- regulatory compliance
- reduced latency for users

---

## Availability Zones

Each AWS region contains multiple **Availability Zones (AZs)**.

An AZ consists of one or more data centers with independent:

- power
- cooling
- networking

Example structure:

Region: us-west-2  
AZ-a  
AZ-b  
AZ-c  

Applications are often deployed across multiple AZs to improve fault tolerance.

Example architecture:

Load Balancer  
↓  
EC2 in AZ-A  
EC2 in AZ-B  

If one AZ fails, the application continues running in another AZ.

---

## Edge Locations

Edge locations are smaller infrastructure sites located closer to users.

Purpose:

- reduce latency
- cache frequently accessed content
- deliver content faster

Edge locations are used by services such as content delivery networks and DNS.

---

# Hour 3 – Cloud Service Models

Cloud services are delivered in three primary models.

As we move from IaaS → PaaS → SaaS, the amount of infrastructure management required by the customer decreases.

---

## Infrastructure as a Service (IaaS)

Provides virtualized computing infrastructure.

Customer manages:

- Operating system
- Applications
- Runtime
- Middleware
- Data

Cloud provider manages:

- Physical servers
- Storage hardware
- Networking
- Virtualization

Example:

Virtual server environments such as EC2.

Use cases:

- migrating on-premise applications
- running custom server configurations

---

## Platform as a Service (PaaS)

Provides a platform for developers to deploy applications without managing infrastructure.

Customer manages:

- Application code
- Application configuration

Cloud provider manages:

- Infrastructure
- Operating system
- Runtime environment
- Scaling

Example workflow:

Developer uploads code  
Cloud platform deploys infrastructure automatically

Use cases:

- web applications
- APIs
- microservices

---

## Software as a Service (SaaS)

Provides fully managed software delivered over the internet.

Customer manages:

- user configuration
- access control

Provider manages:

- infrastructure
- platform
- application
- updates
- security patches

Examples:

- Google Workspace
- Salesforce
- Microsoft 365

---

## Service Model Comparison

| Model | Customer Manages | Provider Manages |
|------|------------------|------------------|
| IaaS | OS + applications | infrastructure |
| PaaS | applications | OS + infrastructure |
| SaaS | user settings | everything else |

---

# Hour 4 – AWS Shared Responsibility Model

The AWS Shared Responsibility Model defines security responsibilities between AWS and the customer.

Core principle:

AWS secures **the cloud**  
Customers secure **what they run in the cloud**

---

## AWS Responsibilities (Security OF the Cloud)

AWS manages the infrastructure that runs cloud services.

This includes:

- physical data centers
- hardware
- networking infrastructure
- storage systems
- virtualization layer

Example responsibilities:

- data center security
- hardware maintenance
- network infrastructure protection
- power and cooling

---

## Customer Responsibilities (Security IN the Cloud)

Customers are responsible for securing their workloads.

This includes:

- operating system configuration
- application security
- identity and access management
- data protection
- firewall configuration
- patching operating systems

Example responsibilities:

- updating OS patches
- managing user permissions
- encrypting sensitive data

---

## Responsibility Differences by Service

| Service | Customer Responsibility |
|------|--------------------------|
| EC2 | OS, applications, configuration |
| S3 | Data and access permissions |
| Lambda | Application code |
| Managed databases | Database configuration |

---

# Day 1 Self Test

1. What is the main benefit of cloud computing compared to traditional infrastructure?

A. Higher electricity usage  
B. Pay only for what you use  
C. More physical hardware  
D. Fixed server capacity  

Answer: B

---

2. Which term describes automatically increasing or decreasing resources based on demand?

A. Availability  
B. Elasticity  
C. Compliance  
D. Pooling  

Answer: B

---

3. What is an AWS Region?

A. Geographic area containing AWS infrastructure  
B. DNS service  
C. Virtual machine  
D. Security policy  

Answer: A

---

4. What is an Availability Zone?

A. A physical data center inside a region  
B. A database service  
C. A monitoring tool  
D. A DNS server  

Answer: A

---

5. Why do architects deploy applications across multiple AZs?

A. Reduce cost  
B. Improve fault tolerance  
C. Increase storage  
D. Improve security  

Answer: B

---

# Day 1 Summary

Key takeaways:

- Cloud computing converts CAPEX infrastructure costs into OPEX usage-based costs.
- AWS Regions contain multiple Availability Zones.
- Deploying across multiple AZs improves fault tolerance.
- Service models move from IaaS → PaaS → SaaS with decreasing infrastructure responsibility.
- AWS secures the cloud infrastructure while customers secure their workloads.

---

# Day 1 Progress

Day 1 – Completed. Started on 03/09/26. Completed on 03/11/26  
Score on self-test: 10 / 10
