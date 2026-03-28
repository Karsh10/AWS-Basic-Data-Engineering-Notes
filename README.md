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
