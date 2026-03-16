# Day 3

| Hour   | Topic                        | Key Concepts                                                              |
| ------ | ---------------------------- | ------------------------------------------------------------------------- |
| Hour 1 | Global Infrastructure Basics | Regions, Availability Zones, Data Centers                                 |
| Hour 2 | Edge & Content Delivery      | Edge Locations, CloudFront, Route 53, Global Accelerator                  |
| Hour 3 | Infrastructure Extensions    | Local Zones, Wavelength Zones, Outposts                                   |
| Hour 4 | Choosing the Right Region    | Latency, compliance, pricing, service availability                        |

---

## Hour 1 – AWS Global Infrastructure

AWS infrastructure is organized in a hierarchy of nested layers — from physical data centers up to a global network of regions and edge locations.

### Infrastructure hierarchy

```
AWS Global Infrastructure
   │
   └── Regions (30+)
         │
         └── Availability Zones (3–6 per region)
               │
               └── Data Centers (1+ per AZ)
```

### Layer 1 – Data centers

- Physical buildings housing tens of thousands of servers
- Each has redundant power, cooling, and networking
- Customers never interact with or choose individual data centers
- Each data center belongs to exactly one AZ

### Layer 2 – Availability Zones (AZs)

- One or more discrete data centers with redundant infrastructure
- Each region has a **minimum of 3 AZs** (some have up to 6)
- AZs are physically separate — typically tens of miles apart
- Connected to each other via high-speed **private fiber links**
- AZ naming: `us-east-1a`, `us-east-1b`, `us-east-1c`
- AZ names are **randomized per AWS account** to distribute load evenly

### Layer 3 – Regions

- A geographic cluster of 3 or more AZs
- AWS has **30+ regions** worldwide
- Each region is fully independent
- Data **does not leave a region** unless you explicitly move it
- Not all AWS services are available in every region

**Example region names:**

| Region Name      | Location            |
| ---------------- | ------------------- |
| us-east-1        | N. Virginia, USA    |
| us-west-2        | Oregon, USA         |
| eu-west-1        | Ireland             |
| eu-central-1     | Frankfurt, Germany  |
| ap-southeast-1   | Singapore           |
| ap-northeast-1   | Tokyo, Japan        |

**Example 1: Region structure**

```
AWS Region: us-east-1 (N. Virginia)
   │
   ├── AZ: us-east-1a
   │     ├── Data Center 1
   │     └── Data Center 2
   │
   ├── AZ: us-east-1b
   │     ├── Data Center 3
   │     └── Data Center 4
   │
   └── AZ: us-east-1c
         ├── Data Center 5
         └── Data Center 6
```

**Example 2: Multi-AZ high availability architecture**

```
Internet
   │
   └── Application Load Balancer
         │
         ├── AZ: us-east-1a
         │     └── EC2 Instance
         │
         ├── AZ: us-east-1b
         │     └── EC2 Instance
         │
         └── AZ: us-east-1c
               └── EC2 Instance
```

---

## Hour 1 Self Test

Score: — / 10

Concepts understood:
- Data center as the physical foundation
- AZ = one or more data centers, minimum 3 per region
- Region = geographic cluster of AZs
- Data sovereignty — data stays in the region you choose
- AZ names are randomized per account

---

## Hour 2 – Edge Locations and CloudFront

Edge locations bring content closer to end users to reduce latency. They are separate from regions and far more numerous.

### Key numbers to memorize

```
400+ Edge Locations  >  ~100 AZs  >  30+ Regions
```

### What are edge locations?

- Points of Presence (PoPs) distributed globally
- Used to **cache and deliver content** to nearby users
- NOT full AWS regions — do not offer the full service catalog
- Used by: CloudFront, Route 53, AWS Global Accelerator, Lambda@Edge

### How CloudFront works

```
User (Tokyo)
   │
   └── Request for image
         │
         ├── First request → Origin server (us-east-1)
         │     └── CloudFront caches the image at Tokyo edge location
         │
         └── Subsequent requests → Served from Tokyo edge location
                                    (no round trip to origin)
```

### Regional edge caches

```
Origin Server (Region)
   │
   └── Regional Edge Cache
         │
         └── Edge Location (closest to user)
               │
               └── End User
```

Regional edge caches sit between the origin and edge locations. They cache larger objects for longer periods.

### Services using edge locations

| Service                  | Purpose                                      |
| ------------------------ | -------------------------------------------- |
| Amazon CloudFront        | CDN — content delivery and caching           |
| Amazon Route 53          | DNS resolution at the edge                   |
| AWS Global Accelerator   | Routes traffic over AWS private network      |
| Lambda@Edge              | Run Lambda functions at edge locations       |

---

## Hour 2 Self Test

Score: — / 10

Concepts understood:
- Edge locations are more numerous than AZs and Regions
- CloudFront uses edge locations, not regions
- First request goes to origin, subsequent requests served from cache
- Route 53 and Global Accelerator also use edge locations

---

## Hour 3 – Infrastructure Extensions

Local Zones, Wavelength Zones, and Outposts extend AWS infrastructure beyond standard regions. All three are **extensions of a parent region**, not standalone regions.

### Local Zones

- Bring AWS compute to large **metro areas** not covered by a region
- Useful for applications needing **single-digit millisecond latency** in specific cities
- Examples: Los Angeles, Chicago, Dallas, Houston

```
Parent Region: us-west-2 (Oregon)
   │
   └── Local Zone: Los Angeles
         └── EC2, EBS, VPC — low latency for LA users
```

### Wavelength Zones

- Embed AWS compute **inside telecom 5G networks**
- Designed for **ultra-low latency** applications on 5G devices
- Use cases: gaming, live video streaming, AR/VR, connected vehicles

```
5G Device (User)
   │
   └── Telecom 5G Network
         │
         └── Wavelength Zone (AWS compute embedded here)
               └── Response back to device in milliseconds
```

### AWS Outposts

- AWS delivers **physical hardware to your own facility**
- Runs AWS services on-premises — looks and feels like AWS
- Use cases: data residency requirements, on-prem latency, legacy systems

```
Your Data Center / Hospital / Factory
   │
   └── AWS Outposts Rack
         └── EC2, EBS, RDS — all running on-premises
               └── Connected back to parent AWS Region
```

### Comparison table

| Feature             | Local Zone              | Wavelength Zone         | Outposts                    |
| ------------------- | ----------------------- | ----------------------- | --------------------------- |
| Location            | Metro city              | Inside 5G network       | Your own facility           |
| Use case            | Low latency in a city   | Ultra-low latency on 5G | On-premises AWS             |
| Part of a region?   | Yes (extension)         | Yes (extension)         | Yes (extension)             |
| Hardware managed by | AWS                     | AWS                     | AWS (on your premises)      |

---

## Hour 3 Self Test

Score: — / 10

Concepts understood:
- Local Zones = specific cities, low latency
- Wavelength Zones = 5G networks, ultra-low latency
- Outposts = your own facility, on-premises AWS
- All three are extensions of a parent region, not standalone

---

## Hour 4 – Choosing the Right Region

When you create AWS resources, you must choose a region. Four key factors drive that decision.

### The four factors

```
Choosing a Region
   │
   ├── 1. Compliance & data residency
   │         Does the law require data to stay in a specific country?
   │
   ├── 2. Latency
   │         Which region is closest to your end users?
   │
   ├── 3. Service availability
   │         Is the AWS service you need available in this region?
   │         (New services launch in us-east-1 first)
   │
   └── 4. Pricing
             Cost varies by region — same service can cost more in some regions
```

### Example scenario

```
Company: EU healthcare provider
Users: Germany and France
Requirement: GDPR compliance — data must stay in EU

Best region choices:
   ├── eu-central-1 (Frankfurt)  ← lowest latency for Germany
   └── eu-west-1 (Ireland)       ← alternative, still EU-compliant
```

### Key rules to remember

- `us-east-1` (N. Virginia) has the **widest service availability** of any region
- By default, data **never leaves** the region you deploy to
- **Global services** (IAM, Route 53, CloudFront, WAF) are NOT region-specific
- **Most services** are region-scoped and must be configured per region

### Global vs regional services

| Scope    | Examples                                      |
| -------- | --------------------------------------------- |
| Global   | IAM, Route 53, CloudFront, WAF, Organizations |
| Regional | EC2, S3, RDS, Lambda, VPC, ECS                |

---

## Hour 4 Self Test

Score: — / 10

Concepts understood:
- Four factors: compliance, latency, service availability, pricing
- us-east-1 has the widest service availability
- IAM and Route 53 are global services — not region-specific
- Data stays in the region by default (data sovereignty)

---

## Day 3 Summary

| Concept              | Key fact                                                        |
| -------------------- | --------------------------------------------------------------- |
| Data centers         | Physical layer — customers never choose them directly           |
| Availability Zones   | Min 3 per region, physically separate, connected by fiber       |
| Regions              | 30+ globally, fully independent, data stays inside by default   |
| Edge locations       | 400+, used by CloudFront/Route 53, NOT full regions             |
| Local Zones          | Metro cities, low latency, extension of parent region           |
| Wavelength Zones     | 5G networks, ultra-low latency, extension of parent region      |
| Outposts             | Your own facility, AWS hardware on-premises                     |
| Region selection     | Compliance, latency, service availability, pricing              |

---

## Exam tips cheat sheet

> **AZ count:** Minimum 3 per region — never 1 or 2.

> **Count hierarchy:** Edge locations (400+) > AZs (~100) > Regions (30+)

> **Multi-AZ vs multi-Region:** Multi-AZ = high availability. Multi-Region = disaster recovery.

> **Data sovereignty:** Your data stays in the region you choose by default.

> **CloudFront:** Uses edge locations — NOT regions. Do not confuse the two.

> **5G / ultra-low latency:** Think Wavelength Zones.

> **On-premises AWS:** Think Outposts.

> **Widest service availability:** us-east-1 (N. Virginia).

> **Global services:** IAM, Route 53, CloudFront — these are NOT region-specific.
