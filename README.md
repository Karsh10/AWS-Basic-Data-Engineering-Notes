# AWS-Basic Data Engineering Notes
### I’m using this repo to keep track of what I study and to revise later.
### The notes are written in a simple way so they’re easy to understand and revisit


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

# STORAGE TYPES OVERVIEW

## 3 Types:

|Type|Example|Use|
|---|---|---|
|Block Storage|EBS|OS, databases|
|Object Storage|S3|Files, logs|
|Data Lake|S3|Analytics|

---

---

# BLOCK STORAGE (EBS)

## What is EBS?

- Disk-like storage
- Attached to EC2
<img width="391" height="346" alt="11" src="https://github.com/user-attachments/assets/b7442456-e88e-40b3-ab47-483a0ffc3b88" />
<img width="431" height="237" alt="12" src="https://github.com/user-attachments/assets/2dfb3e22-0062-473b-914d-1e2f55dc4b09" />

---

## Features:

- Persistent
- High performance
- Can detach/attach

---

## Use Cases:

- OS storage
- Databases
- Applications

---

## Analogy:

> EBS = Hard drive of your computer

---

---

#  BLOB STORAGE (S3)

## What is Object Storage?

- Stores data as objects (files)
<img width="415" height="288" alt="14" src="https://github.com/user-attachments/assets/c9a98c93-571f-4e35-9b92-adf894b928b3" />
<img width="435" height="322" alt="15" src="https://github.com/user-attachments/assets/c64747b4-9cda-4d65-af0c-28e014ca2d67" />

---

## Features:

- Unlimited storage
- Highly durable
- Accessible via internet

---

## Use Cases:

- Images, videos
- Logs
- Backups

---

## Analogy:

> S3 = Google Drive of AWS

---

---

# DATA LAKE (VERY IMPORTANT)

## What is Data Lake?

A data lake is a system to store:

- Raw data
- Structured + unstructured
<img width="332" height="134" alt="16" src="https://github.com/user-attachments/assets/f096ce80-09bb-4bfc-a64c-43964a71d7be" />

---

## Built Using:

- S3

---

## Features:

- Stores all types of data
- Schema-on-read
- Used in analytics

---

## Example:

- Logs
- JSON files
- CSV files

---

---

# ⚔️ STORAGE COMPARISON

|Feature|EBS|S3|Data Lake|
|---|---|---|---|
|Type|Block|Object|Object|
|Usage|OS|Files|Analytics|
|Attach to EC2|Yes|No|No|
|Scalability|Limited|Unlimited|Unlimited|
#  AWS S3 (Simple Storage Service) 🪣

## What is S3?

S3 is a **cloud storage service** used to store files.

---

## Simple Definition

> S3 = place where you store files (like Google Drive, but for systems)

---

## What can you store?

- CSV files
- JSON data
- Images
- Logs
- Videos

---

---

# S3 Core Concepts

## 1. Bucket

- Container for files
- Must have **unique name globally**

Example:

my-data-bucket

---

## 2. Object

- Actual file stored in S3

Example:

data.csv

---

## 3. Key

- Path of file inside bucket

Example:

my-data-bucket/raw/data.csv

---

## Think like this:

|Concept|Real Meaning|
|---|---|
|Bucket|Folder|
|Object|File|
|Key|File path|

---

---

# S3 Features (Detailed)

## 1. Unlimited Storage

- No limit on number of files

---

## 2. High Durability

- Data stored across multiple AZs
- Very low chance of loss

---

## 3. Versioning

- Keeps old versions of files

---

## 4. Lifecycle Rules

- Move data automatically:
    - To cheaper storage
    - Or delete after time

---

## 5. Encryption

- Protects data

---

## 6. Event Notifications

- Can trigger actions when file uploaded

---

---

# S3 Storage Classes

|Class|Use|
|---|---|
|Standard|Frequently used data|
|Standard-IA|Less frequently used|
|Glacier|Backup / archive|
|Intelligent Tiering|Auto optimization|
# Ways to Access AWS Services

There are **4 main ways**:

1. AWS Console (UI)
2. AWS CLI (Terminal)
3. SDK (boto3, Java, etc.)
4. REST APIs (direct HTTP calls)
<img width="425" height="302" alt="13" src="https://github.com/user-attachments/assets/bbbb39de-89ba-4053-a44a-d5c82015cc87" />

---

# Big Picture

You → (Console / CLI / SDK / API) → AWS → Service (S3, EC2, etc.)

---

#  1. AWS CONSOLE (EASIEST)

Website UI (what you’ve been using)

### Example:

- Upload file manually to S3

---

## Pros

- Easy
- Beginner-friendly

## Cons

- Not scalable
- Not used in automation

---

---

#  2. AWS CLI (VERY IMPORTANT)

Use AWS from terminal

---

## Setup (one-time)

aws configure

---

## Example: List buckets

aws s3 ls

---

## Example: Upload file

aws s3 cp file.txt s3://my-bucket/

---

## Meaning

You are sending commands directly from terminal

---

## Pros

- Fast
- Used in real jobs
- No coding needed

---

## Cons

- Manual commands

---

---

# 3. SDK (boto3, etc.)
# What is SDK?

SDK (Software Development Kit) lets your code talk to AWS.

---

## Simple Idea

Your Code → boto3 → AWS → S3

boto3 = AWS SDK for Python

---

# Why use `.env`?

## ❌ Problem without `.env`

aws_access_key_id = "ABC123"  
aws_secret_access_key = "XYZ456"

Bad because:

- Keys exposed ❌
- Not secure ❌

---

## Solution: `.env`

Store secrets in a separate file:

AWS_ACCESS_KEY_ID=your_key_here  
AWS_SECRET_ACCESS_KEY=your_secret_here

---

##  Why this is good

- Keeps code clean
- Protects secrets
- Used in real projects

---

---

# How `.env` works

## Step 1: Install

pip install python-dotenv

---

## Step 2: Load variables

from dotenv import load_dotenv  
load_dotenv()

---

## Step 3: Access values

os.getenv('AWS_ACCESS_KEY_ID')

---

## Flow

.env → load_dotenv() → os.getenv() → boto3 → AWS

---

---

# CODE (EXPLAINED)

import boto3  
import os  
from dotenv import load_dotenv  
  
load_dotenv()  
  
s3_client = boto3.client(  
    's3',  
    aws_access_key_id=os.getenv('AWS_ACCESS_KEY_ID'),  
    aws_secret_access_key=os.getenv('AWS_SECRET_ACCESS_KEY')  
)

---

## What this does

- Loads `.env` file
- Gets credentials
- Creates connection to S3

---

---

# 📄 LIST BUCKETS

response = s3_client.list_buckets()  
  
for bucket in response['Buckets']:  
    print(bucket['Name'])

---

## 🧠 Meaning

👉 Show all S3 buckets in your account

---

---

# 🗑️ DELETE BUCKET

response = s3_client.delete_bucket(  
    Bucket='anshbucket123343',  
    ExpectedBucketOwner='847324761542'  
)

---

## 🧠 Explanation

|Parameter|Meaning|
|---|---|
|Bucket|bucket name|
|ExpectedBucketOwner|AWS account ID (extra safety)|

---

## ⚠️ IMPORTANT RULE

> Bucket must be EMPTY before deleting

---

---

# How Authentication Works

## Step-by-step

.env → credentials → boto3 → AWS verifies → action allowed/denied

---

## Two Concepts

- Authentication → Who you are
- Authorization → What you can do

# OFFICIAL DOCUMENTATION

👉 boto3 S3 Docs  
[https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)
## Example:

import boto3  
s3 = boto3.client('s3')  
s3.list_buckets()

## ✅ Pros

- Automation
- Used in pipelines

---

## ❌ Cons

- Requires coding
