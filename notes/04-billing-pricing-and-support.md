# Day 4 — Billing, Pricing, and Support  
**AWS Cloud Practitioner Curriculum — Domain 4**

---

## Domain 4 Overview

| Domain | Description |
|------|-------------|
| 4.1 | Compare AWS pricing models |
| 4.2 | Understand resources for billing, budget, and cost management |
| 4.3 | Identify AWS technical resources and AWS Support options |

---

## Hour 1 — AWS Pricing Models  
**Domain 4.1: Compare AWS pricing models**

AWS follows a **pay‑as‑you‑go** pricing model with multiple options to reduce cost based on commitment and flexibility.

### Core pricing principles
- Pay only for what you use
- No upfront infrastructure cost
- Discounts for long‑term commitment
- Volume‑based pricing

### EC2 pricing models

| Model              | Commitment | Discount        | Best for                                      |
| ------------------ | ---------- | --------------- | --------------------------------------------- |
| On‑Demand          | None       | None            | Short‑term, unpredictable workloads           |
| Reserved Instances | 1 or 3 yrs | Up to 72%       | Steady, predictable workloads                 |
| Savings Plans      | 1 or 3 yrs | Up to 66%       | Flexible compute usage                        |
| Spot Instances     | None       | Up to 90%       | Fault‑tolerant, interruptible workloads       |
| Dedicated Hosts    | Varies     | Varies          | Compliance, BYOL requirements                 |

### Pricing decision flow
Workload type?
│
├── Short-term / unpredictable → On-Demand
├── Steady for 1–3 years       → Reserved / Savings Plans
├── Flexible usage             → Savings Plans
├── Can be interrupted         → Spot Instances
└── Compliance / licensing     → Dedicated Hosts


---

## Hour 2 — Billing & Cost Management Tools  
**Domain 4.2: Billing, budget, and cost management**

AWS provides multiple tools to **track, analyze, and control costs**.

### AWS Pricing Calculator
- Estimate monthly AWS costs
- Used **before** deployment
- Not tied to your AWS account

### AWS Cost Explorer
- Visualize historical spending
- Identify trends
- Forecast future costs

### AWS Budgets
- Set cost or usage thresholds
- Sends alerts via email or SNS
- Used for proactive cost control

### Cost & Usage Report (CUR)
- Most detailed billing dataset
- Used for deep financial analysis
- Exported to S3

---

## Hour 3 — AWS Support Plans & Resources  
**Domain 4.3: AWS technical resources and support options**

AWS offers four support plans with increasing levels of access.

### Support plan comparison

| Plan        | Technical Support | Response Time | Key Features                                  |
| ----------- | ----------------- | ------------- | --------------------------------------------- |
| Basic       | ❌ None           | N/A           | Billing support, docs, forums                 |
| Developer   | Email (business)  | < 24 hours    | General guidance                              |
| Business    | 24/7 phone/chat   | < 1 hour      | Full Trusted Advisor checks                  |
| Enterprise  | 24/7 + TAM        | < 15 minutes  | Mission‑critical support, concierge           |

### Trusted Advisor
- Best‑practice checks for:
  - Cost optimization
  - Security
  - Performance
  - Fault tolerance
  - Service limits
- **Full checks require Business or Enterprise support**

---

## Hour 4 — Cost Optimization Strategies  
**Domain 4.1 & 4.2 (Applied Cost Optimization)**

### Right‑sizing
- Choose correct instance types
- Remove unused resources
- Use AWS Compute Optimizer

### Use Auto Scaling
- Scale out during peak demand
- Scale in during low usage
- Avoid paying for idle capacity

### Use Serverless
- Lambda, Fargate, DynamoDB
- No cost when idle

### Use Spot Instances
- Up to 90% cheaper
- Use only for fault‑tolerant workloads

### Choose correct storage class
- S3 Standard → frequent access
- S3 IA → infrequent access
- Glacier / Deep Archive → long‑term archival

---

## Day 4 Summary (Domain 4)

| Concept              | Key Fact                                                     |
| -------------------- | ------------------------------------------------------------ |
| On‑Demand            | No commitment, highest per‑hour cost                         |
| Reserved Instances   | 1–3 year commit, biggest savings for steady workloads        |
| Savings Plans        | Flexible $/hour commitment across compute services           |
| Spot Instances       | Cheapest option, can be interrupted                          |
| Pricing Calculator   | Cost estimation before deployment                            |
| Cost Explorer        | Visualize and analyze spending                               |
| Budgets              | Alerts when thresholds are exceeded                          |
| Trusted Advisor      | Best‑practice recommendations                                |
| Enterprise Support   | Includes Technical Account Manager (TAM)                     |

---

## Exam Tips Cheat Sheet (Domain 4)

> **Inbound data transfer is free. Outbound is charged.**

> **Savings Plans are more flexible than Reserved Instances.**

> **Business support unlocks full Trusted Advisor checks.**

> **Spot Instances are cheapest — but never guaranteed.**

> **Use Budgets for alerts, Cost Explorer for analysis.**
