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

## Questions

- What is the difference between Region and Availability Zone?
