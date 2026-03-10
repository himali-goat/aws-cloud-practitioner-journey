# Day 1 – Cloud Concepts

## Topics Covered

- What is Cloud Computing
- AWS Global Infrastructure
- Regions
- Availability Zones
- Edge Locations

## Key Ideas

Cloud computing allows organizations to rent computing resources instead of owning physical hardware.

AWS regions consist of multiple Availability Zones for high availability and fault tolerance.

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

**Quick Knowledge Check (important)**

Try answering these:
1️⃣ What is the difference between CAPEX and OPEX?
2️⃣ Why does cloud allow faster innovation?
3️⃣ What does elasticity mean?
4️⃣ What problem does capacity planning solve?

## Questions

- What is the difference between Region and Availability Zone?
