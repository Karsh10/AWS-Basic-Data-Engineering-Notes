# AWS-Basic-Data-Engineering-Notes
Beginner AWS notes
# Introduction to AWS

## What is AWS?

Amazon Web Services (AWS) is a cloud platform that provides:

- Compute (EC2)
- Storage (S3)
- Databases (RDS, DynamoDB)
- Networking & other services

### Key Idea

> Instead of owning servers, you rent infrastructure on demand.

---

## Traditional vs AWS

|Feature|Traditional|AWS|
|---|---|---|
|Cost|High upfront|Pay-as-you-go|
|Scaling|Manual|Automatic|
|Maintenance|Required|Managed by AWS|
|Availability|Limited|High|

---

## Real-World Analogy

- Traditional → Buying a car
- AWS → Booking an Uber

---

# What is Cloud Computing?

## Definition

Cloud computing is the delivery of computing services (servers, storage, databases, networking) over the internet.
<img width="392" height="204" alt="Screenshot 2026-03-28 232143" src="https://github.com/user-attachments/assets/7914ef08-562d-4a8a-b446-e417a7627d0a" />

---

## Problems with Traditional Systems

- Expensive hardware
- Limited scalability
- Requires maintenance
- Downtime risks

---

## Advantages of Cloud

- **Scalability** → Increase/decrease resources instantly
- **Elasticity** → Auto-adjust resources
- **Cost-efficient** → Pay only for usage
- **High availability** → Minimal downtime
- **Global access** → Deploy anywhere

---
<img width="385" height="246" alt="Screenshot 2026-03-28 232229" src="https://github.com/user-attachments/assets/c552a12a-0859-4cf8-a354-0697b546ff88" />


## Core Characteristics

- On-demand self-service
- Broad network access
- Resource pooling
- Rapid elasticity
- Measured service

---

#  IaaS vs PaaS vs SaaS

## IaaS (Infrastructure as a Service)

You manage:

- OS
- Applications
- Runtime

AWS manages:

- Hardware & networking

**Example:** EC2

---

## PaaS (Platform as a Service)

You manage:

- Application code

AWS manages:

- OS, runtime, infrastructure

**Example:** Elastic Beanstalk

---

## SaaS (Software as a Service)

Everything is managed by provider.

**Examples:**

- Gmail
- Dropbox
<img width="415" height="305" alt="Screenshot 2026-03-28 232250" src="https://github.com/user-attachments/assets/66b2c2b1-a192-4db3-9e40-71f8dd48b711" />

---

## Comparison Table

|Layer|IaaS|PaaS|SaaS|
|---|---|---|---|
|Application|You|You|Provider|
|Runtime|You|Provider|Provider|
|OS|You|Provider|Provider|
|Infrastructure|Provider|Provider|Provider|

---

## Key Insight

> More control = more responsibility

---

# Public vs Private Cloud
<img width="394" height="182" alt="Screenshot 2026-03-28 232303" src="https://github.com/user-attachments/assets/df1e3c5c-4476-405f-bdfb-013ba14549a9" />

## Public Cloud

- Shared infrastructure
- Accessible to everyone

**Examples:** AWS, Azure, GCP

---

## Private Cloud

- Dedicated infrastructure
- Used by enterprises (banks, government)

---

## Hybrid Cloud

- Combination of public + private

---

## Comparison

|Feature|Public|Private|
|---|---|---|
|Cost|Low|High|
|Security|Medium|High|
|Scalability|High|Limited|

# Summary

- Cloud = on-demand computing over internet
- AWS removes need for physical infrastructure
- IaaS, PaaS, SaaS define levels of control
- Public cloud is most common
- Always manage billing carefully

# AWS Global Infrastructure

## What is a Region?

A **Region** is a physical geographic location where AWS has data centers.

<img width="425" height="394" alt="4" src="https://github.com/user-attachments/assets/368a09bc-e6b5-42ab-ad86-0338c60968fb" />

### Examples:

- ap-south-1 (Mumbai)
- us-east-1 (N. Virginia)
## What is an Availability Zone (AZ)?

An **Availability Zone** is a data center (or group of data centers) inside a region.

 Each region has multiple AZs.

> Region = City  
> AZ = Buildings inside the city

## Why Multiple AZs?

- Fault tolerance
- High availability
- Disaster recovery
- 
If one AZ fails → your app still runs in another AZ
# ⚡ High Availability vs Fault Tolerance

## High Availability

- System stays operational most of the time
- Uses multiple AZs
## Fault Tolerance

- System continues without interruption
- Even during failure

## Simple Difference

|Concept|Meaning|
|---|---|
|High Availability|Minimal downtime|
|Fault Tolerance|No downtime|

# AWS IAM 

## What is IAM?

IAM (Identity and Access Management) controls:

- Who can access AWS
- What actions they can perform
<img width="428" height="427" alt="5" src="https://github.com/user-attachments/assets/1fbb0258-1d07-488a-91e9-cd78cd393846" />

## IAM Components

### 👤 Users

- Individual identities
- Example: developer, admin

---

### 👥 Groups

- Collection of users
- Assign permissions once
<img width="401" height="323" alt="6" src="https://github.com/user-attachments/assets/0aee0e8f-f717-4539-b84f-7d68480304af" />
<img width="435" height="281" alt="7" src="https://github.com/user-attachments/assets/aa7bf83a-8a07-4036-b07d-96dca58aca6a" />

---

### 🎭 Roles (MOST IMPORTANT)

- Temporary permissions
- Used by services
<img width="391" height="223" alt="8" src="https://github.com/user-attachments/assets/844a041b-84d0-4171-98ab-a9192de0180e" />
<img width="358" height="224" alt="9" src="https://github.com/user-attachments/assets/31682cab-4a03-4a7c-a3d2-e725da32e8bd" />

---

## 🔥 Example:

- EC2 accesses S3 using IAM Role
- Databricks accesses S3 using IAM Role

---

### 📜 Policies

- JSON documents defining permissions

Example:

{  
  "Effect": "Allow",  
  "Action": "s3:GetObject",  
  "Resource": "*"  
}

---

#  IAM Concepts (Deep Understanding)

## 1. Authentication vs Authorization

- Authentication → Who you are
- Authorization → What you can do

---

## 2. Least Privilege Principle

> Give only required permissions

---

## 3. Root User

- Full access account
- Should NOT be used daily

---

---

# ⚠️ IAM Best Practices

- Never use root account
- Use IAM roles instead of access keys
- Enable MFA (Multi-Factor Authentication)
- Rotate credentials regularly
- Follow least privilege

---

---

# 🔄 Real-World Usage

## Example Pipeline

Databricks → IAM Role → S3

---

## Example:

- Glue job reads from S3 using role
- Lambda writes to S3 using role

---

# Common Interview Questions

- What is IAM?
- Difference between Role and User?
- What is least privilege?
- How does EC2 access S3?
# Virtualization (Core Concept)

## What is Virtualization?

Virtualization allows multiple **virtual machines (VMs)** to run on a single physical machine.
<img width="440" height="395" alt="10" src="https://github.com/user-attachments/assets/d0b89ea4-02b3-4799-9420-68e2e3064d63" />

## Why it exists:

- Better resource utilization
- Cost efficiency
- Isolation between systems
- A physical server with:
  16 GB RAM
  8 CPU cores
  Can run:
  4 VMs (each 4 GB RAM + 2 cores)

---

## Example:

One physical server → runs:

- 5 different OS
- 5 different applications

---

## Key Idea

> One hardware → multiple virtual systems

## What is a Hypervisor?
- A Hypervisor is software that creates and manages virtual machines.

|Feature|VM|Container|
|---|---|---|
|OS|Separate|Shared|
|Size|Large|Small|
|Speed|Slower|Faster|

## Type 1 (Cloud / AWS)
- Hardware → Hypervisor → VM
- Hypervisor directly controls hardware
- It divides RAM, CPU properly
- No OS in between

That’s why:
Faster
More efficient
Used in AWS

## Type 2 (Your Laptop)
- Hardware → OS → Hypervisor → VM
- Hypervisor depends on your OS
- OS also using RAM + CPU

So:
Slower
Less efficient

---

# AWS EC2 (Elastic Compute Cloud)

## What is EC2?

EC2 is a service that provides **virtual servers in the cloud**.

---

## Simple Definition

> EC2 = rent a computer in the cloud

---

## Use Cases:

- Hosting applications
- Running backend servers
- Big data processing
- Running scripts/jobs

---

---

# EC2 Core Components

## 1. Instance

- A virtual machine
- You choose CPU, RAM, OS

---

## 2. AMI (Amazon Machine Image)

- Pre-configured OS template
- Example: Ubuntu, Windows

---

## 3. Instance Types

- Define power of machine
- Example:
    - t2.micro (small)
    - m5.large (powerful)

---

## 4. Security Group

- Firewall for EC2
- Controls:
    - Inbound traffic
    - Outbound traffic

---

## 5. Key Pair

- Used for SSH login
- Private key = access to server

---

## 6. EBS (Elastic Block Storage)

- Disk attached to EC2
- Persistent storage

<img width="440" height="395" alt="10" src="https://github.com/user-attachments/assets/9e18a8f3-9295-47c7-ad0a-fec0a248d782" />
<img width="391" height="346" alt="11" src="https://github.com/user-attachments/assets/80c74b7e-e3f7-4581-adb0-e393ff4cecf3" />
<img width="431" height="237" alt="12" src="https://github.com/user-attachments/assets/9a000502-2539-4391-a448-c6d51dd8b579" />

---

---

# EC2 Important Concepts

## Stateless vs Stateful

- EC2 = stateless (can terminate anytime)
- EBS = stateful (stores data permanently)

---

## Scaling

- You can launch multiple EC2 instances
- Used in auto-scaling systems
