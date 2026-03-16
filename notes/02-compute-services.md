# Day 2

| Hour   | Topic                | Key Concepts                                                 |
| ------ | -------------------- | ------------------------------------------------------------ |
| Hour 1 | EC2 Fundamentals     | EC2 instances, AMI, instance types, security groups, ports   |
| Hour 2 | EC2 Pricing Models   | On-Demand, Reserved Instances, Spot Instances, Savings Plans |
| Hour 3 | Scaling Architecture | Load Balancing, Auto Scaling                                 |
| Hour 4 | Serverless Compute   | Lambda, serverless architecture                              |

---

## Hour 1 – Amazon EC2

EC2 provides virtual servers in the cloud.

Key concepts:
- EC2 instance
- AMI (Amazon Machine Image)
- Instance types
- Security groups

Example use case:
Running web applications on virtual servers.

**Example 1: Basic architecture**

```
Internet
   ↓
Port 443
   ↓
Load Balancer
   ↓
EC2 Instances
   ↓
Database
```

**Example 2: Full web architecture**

```
Internet
   │
   └── Port 443 (HTTPS)
        │
   Application Load Balancer
        │
   Auto Scaling Group
        │
   EC2 Instances
        │
   Database (RDS / DynamoDB)
```

**Common port diagram**

```
Client
   │
   ├── Port 22   → SSH (Linux EC2)
   ├── Port 3389 → RDP (Windows EC2)
   ├── Port 80   → HTTP (Web traffic)
   └── Port 443  → HTTPS (Secure web traffic)
```

### Instance types

| Family    | Optimized for       | Example use case                        |
| --------- | ------------------- | --------------------------------------- |
| t3, t4g   | General purpose     | Small web apps, dev environments        |
| c5, c6g   | Compute             | High-performance web servers, ML        |
| r5, r6g   | Memory              | In-memory databases, real-time big data |
| i3, i4i   | Storage             | High-frequency OLTP databases           |
| p3, g4    | GPU / Accelerated   | Machine learning, video rendering       |

### AMI (Amazon Machine Image)

```
AMI = Template for an EC2 instance
   │
   ├── Operating system (Linux, Windows)
   ├── Pre-installed software
   ├── Storage configuration
   └── Launch permissions

Sources:
   ├── AWS provided (Amazon Linux, Ubuntu, Windows Server)
   ├── AWS Marketplace (third-party, often pre-licensed)
   └── Custom (your own AMI from an existing instance)
```

---

## Hour 1 Self Test

Score: 10 / 10

Concepts understood:
- EC2 instance basics
- AMI templates
- Instance types
- Security groups
- Common ports (22, 80, 443, 3389)

---

## Hour 2 – EC2 Pricing Models

AWS offers multiple pricing models for EC2 — choosing the right one can save significant cost.

### Pricing models overview

| Model              | Commitment  | Discount vs On-Demand | Best for                                      |
| ------------------ | ----------- | --------------------- | --------------------------------------------- |
| On-Demand          | None        | 0% (baseline)         | Short-term, unpredictable workloads           |
| Reserved Instances | 1 or 3 yrs  | Up to 72%             | Steady, predictable workloads                 |
| Savings Plans      | 1 or 3 yrs  | Up to 66%             | Flexible reserved pricing across EC2/Lambda   |
| Spot Instances     | None        | Up to 90%             | Fault-tolerant, flexible batch jobs           |
| Dedicated Hosts    | On-Demand or Reserved | Varies      | Compliance, bring-your-own-license (BYOL)     |

### On-Demand

- Pay by the hour or second — no upfront cost
- No long-term commitment
- Most expensive per hour
- Use when: testing, unpredictable traffic, short-term projects

```
On-Demand pricing
   │
   ├── No commitment needed
   ├── Start/stop anytime
   └── Pay only for what you use
```

### Reserved Instances (RIs)

- Commit to 1 or 3 years for a specific instance type and region
- Up to 72% cheaper than On-Demand
- Payment options: All Upfront, Partial Upfront, No Upfront

```
Reserved Instance commitment
   │
   ├── 1-year term   → moderate discount
   └── 3-year term   → maximum discount
         │
         ├── All Upfront     → biggest saving
         ├── Partial Upfront → balanced
         └── No Upfront      → smallest saving (still cheaper than On-Demand)
```

### Savings Plans

- Flexible alternative to Reserved Instances
- Commit to a dollar amount per hour (e.g. $10/hr) for 1 or 3 years
- Applies automatically across EC2, Lambda, and Fargate
- Two types:
  - **Compute Savings Plans** — most flexible, applies across instance families, regions
  - **EC2 Instance Savings Plans** — locked to a specific instance family in one region

### Spot Instances

- Use AWS spare capacity at up to 90% discount
- AWS can **reclaim** the instance with a 2-minute warning
- Use when: batch processing, data analysis, CI/CD jobs, rendering

```
Spot Instance lifecycle
   │
   ├── You set a max price
   ├── If spot price < max price → instance runs
   └── If spot price > max price → instance terminated (2-min warning)
```

### Pricing decision diagram

```
Workload type?
   │
   ├── Short-term / unpredictable → On-Demand
   │
   ├── Steady, runs 24/7 for 1–3 years → Reserved Instances or Savings Plans
   │
   ├── Flexible across services/regions → Savings Plans
   │
   ├── Fault-tolerant, can be interrupted → Spot Instances
   │
   └── Compliance / BYOL requirement → Dedicated Hosts
```

---

## Hour 2 Self Test

Score: — / 10

Concepts understood:
- On-Demand: no commitment, most expensive per hour
- Reserved Instances: 1 or 3 year commit, up to 72% saving
- Savings Plans: flexible commit by $/hr, covers EC2 + Lambda
- Spot Instances: up to 90% off, can be interrupted with 2-min warning
- Dedicated Hosts: physical server for compliance or BYOL

---

## Hour 3 – Scaling Architecture

AWS provides tools to automatically adjust compute capacity based on demand — keeping applications available and cost-efficient.

### Two core concepts

```
Scaling Architecture
   │
   ├── Elastic Load Balancing (ELB) → distributes traffic across instances
   └── Auto Scaling               → adds or removes instances automatically
```

### Elastic Load Balancing (ELB)

A load balancer sits in front of your EC2 instances and distributes incoming traffic evenly.

**Types of load balancers:**

| Type                          | Best for                                      |
| ----------------------------- | --------------------------------------------- |
| Application Load Balancer (ALB) | HTTP/HTTPS traffic, path-based routing      |
| Network Load Balancer (NLB)   | TCP/UDP, ultra-high performance, low latency  |
| Gateway Load Balancer (GWLB)  | Third-party virtual appliances (firewalls)    |

**ALB architecture:**

```
Internet
   │
   └── Application Load Balancer (ALB)
         │
         ├── /api/*  → EC2 Instance (API servers)
         │
         └── /web/*  → EC2 Instance (Web servers)
```

**Health checks:**

```
Load Balancer
   │
   ├── Health check every 30s → EC2 Instance A (healthy ✓) → sends traffic
   ├── Health check every 30s → EC2 Instance B (healthy ✓) → sends traffic
   └── Health check every 30s → EC2 Instance C (unhealthy ✗) → stops traffic
```

### Auto Scaling Groups (ASG)

Auto Scaling automatically adjusts the number of EC2 instances based on demand.

**Key settings:**

```
Auto Scaling Group
   │
   ├── Minimum capacity  → always keep at least N instances running
   ├── Desired capacity  → target number of instances
   └── Maximum capacity  → never exceed N instances
```

**Scaling policies:**

| Policy type         | How it works                                          |
| ------------------- | ----------------------------------------------------- |
| Target tracking     | Keep a metric at a target (e.g. CPU at 50%)           |
| Step scaling        | Scale in steps based on alarm thresholds              |
| Scheduled scaling   | Scale up/down at specific times (e.g. every morning)  |

**Scale out vs scale in:**

```
Traffic increases → Scale OUT (add instances)
   │
   ├── CPU > 70% for 5 mins
   └── ASG launches 2 new EC2 instances

Traffic decreases → Scale IN (remove instances)
   │
   ├── CPU < 30% for 10 mins
   └── ASG terminates 2 EC2 instances
```

**Full scaling architecture:**

```
Internet
   │
   └── Application Load Balancer
         │
         └── Auto Scaling Group
               │
               ├── EC2 Instance (AZ-1a)
               ├── EC2 Instance (AZ-1b)  ← added during peak
               └── EC2 Instance (AZ-1c)  ← added during peak
```

---

## Hour 3 Self Test

Score: — / 10

Concepts understood:
- ELB distributes traffic across healthy EC2 instances
- ALB = HTTP/HTTPS, NLB = TCP/UDP high performance
- Auto Scaling adds instances (scale out) or removes them (scale in)
- ASG has minimum, desired, and maximum capacity settings
- Scaling policies: target tracking, step, scheduled

---

## Hour 4 – Serverless Compute

Serverless means you run code without managing or provisioning any servers. AWS handles all the underlying infrastructure.

### EC2 vs Lambda

```
EC2 (server-based)               Lambda (serverless)
   │                                │
   ├── You manage the server        ├── AWS manages everything
   ├── Always running               ├── Runs only when triggered
   ├── Pay while server is on       ├── Pay only when code runs
   └── You choose instance type     └── You only write the function
```

### How Lambda works

```
Trigger
   │
   └── Lambda function runs
         │
         ├── Executes your code (up to 15 minutes)
         ├── Scales automatically — runs 1 or 1,000,000 times
         └── Returns result / writes to another service
```

### Lambda triggers

```
What can trigger a Lambda function?
   │
   ├── API Gateway        → HTTP request from a user
   ├── S3                 → file uploaded to a bucket
   ├── DynamoDB Streams   → record changed in a table
   ├── CloudWatch Events  → scheduled cron job
   ├── SNS / SQS          → message in a queue or topic
   └── Cognito            → user signs up or logs in
```

### Lambda pricing

- **Requests:** first 1 million requests/month are free, then $0.20 per million
- **Duration:** charged by GB-seconds (memory × execution time)
- No charge when function is not running

### Serverless architecture example

```
User
   │
   └── API Gateway (HTTP request)
         │
         └── Lambda function
               │
               ├── Reads/writes to DynamoDB
               ├── Sends email via SES
               └── Returns JSON response to user
```

### When to use Lambda vs EC2

| Scenario                                      | Use          |
| --------------------------------------------- | ------------ |
| Run code in response to an event              | Lambda       |
| Long-running process (> 15 min)               | EC2          |
| Unpredictable, bursty traffic                 | Lambda       |
| Persistent server with custom OS              | EC2          |
| Simple API backend                            | Lambda       |
| High-performance compute workload             | EC2          |
| Zero server management                        | Lambda       |

---

## Hour 4 Self Test

Score: — / 10

Concepts understood:
- Lambda runs code without managing servers
- Triggered by events: API Gateway, S3, DynamoDB, CloudWatch, SQS
- Pay only when code runs — no idle cost
- Max execution time is 15 minutes
- Scales automatically to handle any number of requests

---

## Day 2 Summary

| Concept             | Key fact                                                              |
| ------------------- | --------------------------------------------------------------------- |
| EC2                 | Virtual servers — you choose instance type, OS, and configuration     |
| AMI                 | Template used to launch EC2 instances                                 |
| Security groups     | Virtual firewall controlling inbound/outbound traffic                 |
| On-Demand           | No commitment, pay per hour, most expensive                           |
| Reserved Instances  | 1 or 3 year commit, up to 72% saving                                  |
| Savings Plans       | Flexible $/hr commit across EC2, Lambda, Fargate                      |
| Spot Instances      | Up to 90% off, can be interrupted with 2-min warning                  |
| ELB                 | Distributes traffic across healthy EC2 instances                      |
| Auto Scaling        | Adds/removes EC2 instances based on demand                            |
| Lambda              | Serverless — runs code on events, no server management needed         |

---

## Exam tips cheat sheet

> **Spot Instances:** Cheapest option (up to 90% off) but can be interrupted — never use for critical workloads.

> **Reserved vs Savings Plans:** RIs lock you to an instance type/region. Savings Plans are more flexible.

> **Lambda limit:** Max execution time is 15 minutes — anything longer needs EC2 or Fargate.

> **Load balancer types:** ALB = HTTP/HTTPS (Layer 7). NLB = TCP/UDP (Layer 4).

> **Auto Scaling:** Scale out = add instances. Scale in = remove instances.

> **Serverless:** Lambda, Fargate — no servers to manage. EC2 = you manage the server.

> **Common ports:** 22 = SSH, 80 = HTTP, 443 = HTTPS, 3389 = RDP (Windows).
