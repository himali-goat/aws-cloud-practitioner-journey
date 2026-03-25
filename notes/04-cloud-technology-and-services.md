# AWS Cloud Practitioner — Domain 3 Exam Notes  
**Author:** Rabindra  
**Domain:** 3 — Cloud Technology & Services  
**Format:** High‑yield, exam‑ready, concise

---

## 3.1 Deploying and Operating in AWS

### **Cloud Deployment Models**
- **On‑Premises:** Full control, high cost, slow scaling  
- **Cloud:** Pay‑as‑you‑go, elastic, managed services  
- **Hybrid:** Mix of on‑prem + cloud  
- **Multi‑Cloud:** Multiple cloud providers

### **Infrastructure as Code (IaC)**
- **CloudFormation:** Declarative templates, repeatable infra  
- **Benefits:** Versioning, automation, consistency

### **Monitoring & Logging**
- **CloudWatch:** Metrics, logs, alarms, dashboards  
- **CloudTrail:** API call history (who did what)  
- **Config:** Resource configuration history + compliance

### **Automation**
- **Auto Scaling:** Adjust capacity automatically  
- **Elastic Beanstalk:** PaaS deployment  
- **Systems Manager:** Patch, automate, manage fleets

---

## 3.2 AWS Global Infrastructure

### **Regions**
- Geographic areas  
- Choose based on latency, compliance, cost, service availability

### **Availability Zones (AZs)**
- Independent datacenters  
- High availability + fault isolation

### **Edge Locations**
- Used by CloudFront, Route 53, Global Accelerator  
- Low‑latency content delivery

### **Local Zones**
- Compute closer to metro areas

### **Wavelength Zones**
- 5G edge compute with telecom providers

### **Outposts**
- AWS hardware on‑premises

---

## 3.3 Compute Services

### **EC2**
- Virtual servers  
- Pricing: On‑Demand, Reserved, Spot, Savings Plans  
- Use cases: apps, databases, custom workloads

### **Lambda**
- Serverless compute  
- Event‑driven, pay per ms  
- Zero server management

### **Containers**
- **ECS:** AWS container orchestration  
- **EKS:** Managed Kubernetes  
- **Fargate:** Serverless containers

### **Elastic Beanstalk**
- PaaS deployment  
- Handles provisioning, scaling, patching

### **Lightsail**
- Simple VPS for small apps

### **Batch**
- Large‑scale batch processing

---

## 3.4 Database Services

### **RDS**
- Managed relational DB  
- Engines: MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora

### **Aurora**
- AWS‑built relational DB  
- MySQL/PostgreSQL compatible  
- Highly available (6 copies across 3 AZs)

### **DynamoDB**
- NoSQL key‑value + document  
- Serverless, auto‑scaling, low latency

### **ElastiCache**
- Redis/Memcached caching

### **Redshift**
- Data warehouse  
- Columnar storage  
- Analytics at scale

### **DocumentDB**
- MongoDB‑compatible document store

### **Neptune**
- Graph database

### **QLDB**
- Immutable ledger database

### **Timestream**
- Time‑series database (IoT, metrics)

---

## 3.5 Networking Services

### **VPC**
- Private network in AWS  
- Components: Subnets, Route Tables, NACLs, Security Groups, IGW, NAT

### **Subnets**
- **Public:** Route to IGW  
- **Private:** No direct internet access

### **Internet Gateway**
- Public internet access

### **NAT Gateway**
- Outbound internet for private subnets

### **Route 53**
- DNS service  
- Routing policies: simple, weighted, latency, failover, geolocation

### **CloudFront**
- CDN using edge locations

### **Direct Connect**
- Private dedicated link from on‑prem to AWS

### **VPC Peering**
- Connects two VPCs (no transitive routing)

### **Transit Gateway**
- Hub‑and‑spoke for many VPCs + on‑prem

---

## 3.6 Storage Services

### **S3**
- Object storage  
- 11 nines durability  
- Storage classes: Standard, IA, One Zone‑IA, Glacier, Deep Archive

### **EBS**
- Block storage for EC2  
- Persistent volumes

### **EFS**
- Managed NFS file system  
- Shared, scalable

### **FSx**
- Windows File Server  
- Lustre (HPC)  
- NetApp ONTAP

### **Glacier / Deep Archive**
- Archival storage  
- Low cost, slow retrieval

### **Storage Gateway**
- Hybrid storage (File, Volume, Tape)

### **Snow Family**
- Snowcone, Snowball, Snowmobile  
- Offline data transfer + edge compute

---

## 3.7 AI/ML & Analytics

### **AI/ML**
- **SageMaker:** Build/train/deploy ML  
- **Rekognition:** Image/video analysis  
- **Comprehend:** NLP + sentiment  
- **Lex:** Chatbots  
- **Polly:** Text‑to‑speech  
- **Transcribe:** Speech‑to‑text  
- **Translate:** Language translation

### **Analytics**
- **Athena:** SQL on S3  
- **Glue:** ETL + Data Catalog  
- **Kinesis:** Real‑time streaming  
- **QuickSight:** BI dashboards  
- **EMR:** Hadoop/Spark clusters  
- **Redshift:** Data warehouse

---

## 3.8 Other AWS Services

### **IAM**
- Users, Groups, Roles, Policies  
- Global service  
- Least privilege

### **Organizations**
- Multi‑account management  
- Consolidated billing  
- SCPs (Service Control Policies)

### **CloudTrail**
- API call logging  
- Governance + auditing

### **Config**
- Resource configuration history  
- Compliance + drift detection

### **Trusted Advisor**
- Best practice checks (cost, security, performance, limits)

### **Well‑Architected Tool**
- Evaluates workloads against AWS pillars

### **Budgets & Cost Explorer**
- Budgets = alerts  
- Cost Explorer = spending analysis

### **Shield**
- DDoS protection

### **WAF**
- Protects against SQLi, XSS, bad bots

---

# End of Domain 3 Notes
