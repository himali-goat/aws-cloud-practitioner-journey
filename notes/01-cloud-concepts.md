Study Time
Date: 2026-03-09
Hours completed: 1

# Day 1 – Cloud Concepts

## Topics Covered

1. What is Cloud Computing
2. Benefits of Cloud
3. Cloud Characteristics
4. Deployment Models
5. Service Models
6. Knowledge Check

## Key Ideas

Cloud computing allows organizations to rent computing resources instead of owning physical hardware.

AWS regions consist of multiple Availability Zones for high availability and fault tolerance.

**Hourly Plan**

Hour 1 – Cloud Fundamentals
Hour 2 – AWS Global Infrastructure
Hour 3 – Regions and AZ
Hour 4 – Edge Locations

## Study Progress

Status: In Progress
Hours studied: 4

### Hourly Progress

#### Hour 1

Topic: What is Cloud Computing

Using computing resources (servers, storage, databases, networking) over the internet instead of owning physical hardware.

Instead of: Company → Buy hardware → Install → Maintain → Replace every few years

With Cloud: Company → Rent infrastructure from AWS → Pay only for usage

**The 6 Key Benefits of Cloud (These appear frequently in the exam)**

1. Trade Capital Expense for Variable Expense
 
   Traditional IT:
   Buy $100,000 servers upfront

Cloud:
   Pay $0.10 per hour

2. Benefit from Massive Economies of Scale

  Large cloud providers like Amazon Web Services buy hardware in huge volumes. This results in customer paying less.
  Example:
  AWS buys 1,000,000 servers
  ↓
  Lower cost per server
  ↓
  Lower price for customers

3. Stop Guessing Capacity

  Traditional problem:
  Too much hardware → wasted money
  Too little hardware → system crashes
  Cloud solves this with elastic scaling.
  Example:
  Traffic spike -> Automatically add servers -> Traffic drops -> Remove servers

4. Increase Speed and Agility

  Traditional IT:
  Provision server = weeks
  Cloud:
  Provision server = minutes
  This allows faster innovation.

5. Stop Spending Money Running Data Centers
  Cloud provider handles:
    hardware
    power
    cooling
    networking
    security
  Your company focuses on applications.

6. Go Global in Minutes
  Example:
  Deploy application in USA, Europe, Asia. No need to build data centers.

**Core Cloud Characteristics**

These are important exam keywords.

1. On-Demand Self Service: Users can create resources instantly.
Example:Create server in AWS console

2. Broad Network Access
Services accessible via internet.
Example: Laptop, Phone, Tablet

3. Resource Pooling: Cloud provider shares infrastructure across customers.
4. Rapid Elasticity: Resources can scale up or down quickly.
5. Measured Service: You only pay for what you use. Example; EC2 running 3 hours -> You pay for 3 hours

**Cloud Deployment Models**

You must know these.

Model	Meaning
Public Cloud:	Infrastructure owned by provider
Private Cloud:	Dedicated infrastructure for one company
Hybrid Cloud:	Mix of on-prem + cloud

Example hybrid: On-prem: database --> AWS: Application servers

**Service Models**
This is very likely to appear on the exam.
## Cloud Service Models

### Infrastructure as a Service (IaaS)
Example: Amazon EC2

### Platform as a Service (PaaS)
Example: Elastic Beanstalk

### Software as a Service (SaaS)
Example: Gmail

**Quick Knowledge Check (important)**

Try answering these:
1️⃣ What is the difference between CAPEX and OPEX?
2️⃣ Why does cloud allow faster innovation?
3️⃣ What does elasticity mean?
4️⃣ What problem does capacity planning solve?


#### Hour 2: AWS Global INnfrastructure

AWS operates a global network of data centers designed for high availability, fault tolerance, and low latency.
The infrastructure has four main components:
     Regions
     Availability Zones
     Edge Locations
     Regional Edge Caches

1. AWS Region
   A Region is a geographical area where AWS has multiple data centers.
   Example:
   | Region     | Location          |
   | ---------- | ----------------- |
   | us-east-1  | Northern Virginia |
   | us-west-2  | Oregon            |
   | eu-west-1  | Ireland           |
   | ap-south-1 | Mumbai            |

Example Architecture
Application
   |
AWS Region (us-west-2)

Each region is indeppendent from other region.
Why?
- Fault isolation
- data sovereignty
- latency optimization

Example:
US users -> US Region
Europe users ->EU Region

2. Availability Zone (AZ)
Each Region contains multiple Availability Zones (AZ).
An AZ is one or more data centers with:
- independent power
- indeppendent cooling
- independent networking

Example

Region: us-west-2
    ├ AZ-a
    ├ AZ-b
    └ AZ-c
AZs are connected by **high-speed** fiber networks.

**Why AZs matter?**: If one data centers fails, traffic moved to another. AZ-a faile, traffic moves to AZ-b. This ensures *high availability* architecture.
Example design: Load balancer | EC2 in AZ-a. EC2 in AZ-b. This is multi-AZ architecture.

3. Edge Locations: These are smaler sites distributed globally that cache content closer to users. This is used mainly by
   - CloudFront
   - Route53
   - AWS Shield
Example:
    User in Tokyo
    ↓
    Edge location in Tokyo
    ↓
    Fetch content from US region
 
 Purpose: Reduce latency. Faster content delivery.

4. Regional Edge Cache: This sits between Edge Location and AWS Region

Purpose: store frequently accessed content. reduce load on origin server.

Summary:

    User
     |
    Edge Location
     |
    Regional Edge Cache
     |
    AWS Region
     |        |
    AZ-A    AZ-B
     |        |
    Servers  Servers

**Rational behind AWS Global Infrastructure:**
- High Availability
- Fault isolation
- Global Scalability
- Low Latency

### Key ideas learned:
- Regions contain multiple Availability Zones
- AZs are isolated data centers
- Edge locations improve latency
- Multi-AZ architecture improves fault tolerance

Example services:
CloudFront
Route53

## Hour 3 – Cloud Service Models

Cloud services are delivered in three main models.  
Each model defines how much responsibility the customer has versus the cloud provider.

As we move from IaaS → PaaS → SaaS, the amount of infrastructure management by the customer decreases.

---

### 1. Infrastructure as a Service (IaaS)

Infrastructure as a Service provides virtual servers and infrastructure resources.

Customer manages:
- Operating system
- Applications
- Runtime
- Middleware
- Data
- Security configuration

Cloud provider manages:
- Physical servers
- Storage hardware
- Networking
- Virtualization

Example AWS service:
Amazon EC2

Example architecture:

Application  
Operating System  
Runtime  
----------------  
AWS manages  
Server  
Storage  
Networking  

Typical use cases:
- Migrating on-premise servers to the cloud
- Running custom server environments
- Applications requiring full OS control

---

### 2. Platform as a Service (PaaS)

Platform as a Service provides a platform where developers deploy code without managing infrastructure.

Customer manages:
- Application code
- Application configuration

Cloud provider manages:
- Operating system
- Runtime
- Infrastructure
- Scaling
- Load balancing

Example AWS service:
AWS Elastic Beanstalk

Example workflow:

Developer uploads code  
↓  
AWS provisions servers  
↓  
Application runs  

Typical use cases:
- Web applications
- APIs
- Microservices

---

### 3. Software as a Service (SaaS)

Software as a Service provides fully managed applications delivered over the internet.

Customer manages:
- User settings
- Application configuration

Provider manages:
- Infrastructure
- Platform
- Application software
- Updates
- Security patches

Examples:
- Google Workspace
- Salesforce
- Microsoft 365

Example flow:

User  
↓  
Web browser  
↓  
Cloud-hosted application  

No infrastructure management is required.

---

### Comparison Summary

| Model | Customer Manages | Provider Manages |
|------|------------------|------------------|
| IaaS | OS + Applications | Infrastructure |
| PaaS | Applications | OS + Infrastructure |
| SaaS | User settings | Everything else |

---

### AWS Example Mapping

| Service Model | AWS Example |
|---|---|
| IaaS | Amazon EC2 |
| PaaS | AWS Elastic Beanstalk |
| Serverless / PaaS style | AWS Lambda |
| SaaS | Cloud-based applications |

---

### Key Exam Tip

Management responsibility decreases in this order:

IaaS → PaaS → SaaS

The service model that requires the least infrastructure management from the customer is **SaaS**.

---

### Knowledge Check

1. What does IaaS allow customers to control that PaaS does not?
2. Which model requires the least infrastructure management?
3. Which AWS service is an example of IaaS?
4. What is the main benefit of PaaS for developers?

## Hour 4 – AWS Shared Responsibility Model

The AWS Shared Responsibility Model defines which security responsibilities belong to AWS and which belong to the customer.

The basic idea is:

AWS secures **the cloud**  
Customers secure **what they put in the cloud**

---

### AWS Responsibilities (Security OF the Cloud)

AWS is responsible for protecting the infrastructure that runs AWS services.

This includes:

- Physical data centers
- Hardware and servers
- Networking infrastructure
- Storage hardware
- Virtualization layer (hypervisor)

Example responsibilities:

- Data center security
- Power and cooling systems
- Network infrastructure protection
- Hardware maintenance

---

### Customer Responsibilities (Security IN the Cloud)

Customers are responsible for securing the resources they deploy on AWS.

This includes:

- Operating system configuration
- Application security
- Identity and access management
- Data protection
- Security group configuration
- Patching operating systems

Example responsibilities:

- Updating OS patches on EC2
- Configuring firewalls
- Encrypting sensitive data
- Managing user access

---

### Visual Explanation

Customer manages:

Applications  
Operating System  
Configuration  
User Access  
Data  

----------------

AWS manages:

Physical Servers  
Networking  
Storage Hardware  
Data Center Security  

---

### Responsibility Changes by Service Type

The customer's responsibility depends on the service used.

| Service | Customer Responsibility |
|------|-------------------------|
| EC2 | OS, applications, configuration |
| S3 | Data and access permissions |
| Lambda | Application code |
| RDS | Database configuration |

---

### Example Scenario

If you run an application on Amazon EC2:

AWS secures:
- Physical servers
- Networking infrastructure
- Data centers

Customer secures:
- Operating system
- Application software
- Security patches
- User access permissions

---

### Key Exam Concept

AWS always secures **the infrastructure of the cloud**, while customers secure **their workloads and data in the cloud**.

---

### Knowledge Check

1. What does AWS secure in the shared responsibility model?
2. What does the customer secure?
3. Who is responsible for operating system patches on EC2?
4. Who secures the physical data center infrastructure?

## Self Test Questions
Day 1 Self-Test (10 Questions)
1
What is the main benefit of cloud computing compared to traditional infrastructure?
A. Higher electricity usage
B. Pay only for what you use
C. More physical hardware
D. Fixed server capacity
2
Which term describes the ability to automatically increase or decrease resources based on demand?
A. Availability
B. Elasticity
C. Compliance
D. Pooling
3
Which of the following is an AWS Region?
A. us-west-2
B. AZ-A
C. Edge-1
D. EC2-zone
4
What is an Availability Zone (AZ)?
A. A physical data center inside a region
B. A DNS service
C. A cloud application
D. A global network
5
Why do architects deploy applications across multiple Availability Zones?
A. To increase cost
B. To improve fault tolerance
C. To reduce storage
D. To limit scaling
6
Which service model allows customers to manage the operating system and applications?
A. SaaS
B. PaaS
C. IaaS
D. FaaS
7
Which service model requires the least infrastructure management by the customer?
A. IaaS
B. SaaS
C. PaaS
D. Hybrid
8
In the Shared Responsibility Model, who is responsible for data center hardware security?
A. Customer
B. AWS
C. Both
D. Application developer
9
In the Shared Responsibility Model, who is responsible for patching the operating system on EC2?
A. AWS
B. Customer
C. Edge locations
D. CloudFront
10
Which AWS infrastructure component helps deliver content to users with low latency?
A. Availability Zones
B. Edge Locations
C. Regions
D. VPC

| Question | Your Answer | Correct Answer | Result |
| -------- | ----------- | -------------- | ------ |
| 1        | B           | B              | ✅      |
| 2        | B           | B              | ✅      |
| 3        | A           | A              | ✅      |
| 4        | A           | A              | ✅      |
| 5        | B           | B              | ✅      |
| 6        | C           | C              | ✅      |
| 7        | B           | B              | ✅      |
| 8        | B           | B              | ✅      |
| 9        | B           | B              | ✅      |
| 10       | B           | B              | ✅      |

I moved on to day 2.
