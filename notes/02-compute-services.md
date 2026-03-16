# Day 2

| Hour   | Topic                | Key Concepts                                                 |
| ------ | -------------------- | ------------------------------------------------------------ |
| Hour 1 | EC2 Fundamentals     | EC2 instances, AMI, instance types, security groups, ports   |
| Hour 2 | EC2 Pricing Models   | On-Demand, Reserved Instances, Spot Instances, Savings Plans |
| Hour 3 | Scaling Architecture | Load Balancing, Auto Scaling                                 |
| Hour 4 | Serverless Compute   | Lambda, serverless architecture                              |


## Hour 1 – Amazon EC2

EC2 provides virtual servers in the cloud.

Key concepts:
- EC2 instance
- AMI
- Instance types
- Security groups

Example use case:
Running web applications on virtual servers.

** Example 1; Architecture**
A typical AWS web architecture looks like this:
Internet
   ↓
Port 443
   ↓
Load Balancer
   ↓
EC2 Instances
   ↓
Database

** Example 2: Architecture **

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

** Common Port Diagram **

Client
   │
   ├── Port 22   → SSH (Linux EC2)
   ├── Port 3389 → RDP (Windows EC2)
   ├── Port 80   → HTTP (Web traffic)
   └── Port 443  → HTTPS (Secure web traffic)



## Hour 1 Self Test

Score: 10 / 10

Concepts understood:
- EC2 instance basics
- AMI templates
- Instance types
- Security groups
- Common ports (22, 80, 443)
