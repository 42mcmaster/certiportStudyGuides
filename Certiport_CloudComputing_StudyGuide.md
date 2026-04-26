# Certiport ITS Cloud Computing — Student Study Guide

A self-paced review for the Certiport / GMetrix Information Technology Specialist (ITS) Cloud Computing certification exam.

---

## How to Use This Guide

This guide is structured as **fourteen short modules**, building from cloud vocabulary up through service models, virtualization, security, compliance, and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

### What This Exam Tests Most Heavily

Across the two practice exams (100 questions total), the heaviest weight is on:

- **Cloud service models** — IaaS, PaaS, SaaS, and the shared responsibility split at each level.
- **Identity and Access Management** — identification vs. authentication vs. authorization, MFA, federation, RBAC.
- **Compliance and regulations** — GDPR, HIPAA, FERPA, GLBA, PCI DSS, FedRAMP, and the ISO standards.
- **Business Continuity and Disaster Recovery** — RTO vs. RPO, BCP vs. DRP, MTTR.
- **Virtualization and containers** — hypervisor types, containers vs. VMs, serverless.

Lighter but reliable: deployment models, storage tiers, monitoring types, and SLAs.

---

## Table of Contents

1. [Cloud Fundamentals and Core Vocabulary](#module-1--cloud-fundamentals-and-core-vocabulary)
2. [The Three Service Models: IaaS, PaaS, SaaS](#module-2--the-three-service-models-iaas-paas-saas)
3. [The Four Deployment Models](#module-3--the-four-deployment-models)
4. [Scaling, Availability, and Performance](#module-4--scaling-availability-and-performance)
5. [Virtualization, Containers, and Serverless](#module-5--virtualization-containers-and-serverless)
6. [Microservices, APIs, and Modern Architecture](#module-6--microservices-apis-and-modern-architecture)
7. [Cloud Storage and Redundancy Tiers](#module-7--cloud-storage-and-redundancy-tiers)
8. [Networking and Security in Transit](#module-8--networking-and-security-in-transit)
9. [Identity and Access Management](#module-9--identity-and-access-management)
10. [Encryption Architecture and the CIA Triad](#module-10--encryption-architecture-and-the-cia-triad)
11. [Risk, Compliance, and Regulations](#module-11--risk-compliance-and-regulations)
12. [SDLC, BCDR, and the Data Lifecycle](#module-12--sdlc-bcdr-and-the-data-lifecycle)
13. [Cost Management, Monitoring, SLAs, and Major CSPs](#module-13--cost-management-monitoring-slas-and-major-csps)
14. [Test-Taking Strategy and Final Review](#module-14--test-taking-strategy-and-final-review)
15. [Exam-Day Cheat Card](#exam-day-cheat-card)
16. [Master Glossary](#master-glossary)

---

## Module 1 — Cloud Fundamentals and Core Vocabulary

### Concept

Most exam questions assume fluency in a small set of foundational terms. The trap is that several pairs sound similar — *scalability* vs. *agility*, *reliability* vs. *resiliency*, *elasticity* vs. *scalability* — and distractors deliberately swap them.

### Anchor: The Vocabulary Map

| Term                         | One-Line Definition                                                                                        |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Cloud computing**          | Delivery of compute, storage, networking, and software over the Internet, on demand, pay-as-you-go.        |
| **CSP (Cloud Service Provider)** | The vendor — AWS, Azure, GCP.                                                                          |
| **CSC (Cloud Service Customer)** | The organization consuming the service.                                                                |
| **Multi-tenancy**            | Multiple customers' workloads share physical infrastructure (logically isolated).                          |
| **Provisioning / Deprovisioning** | Allocating / releasing cloud resources.                                                              |
| **Elasticity**               | Resources grow and shrink on demand.                                                                       |
| **Scalability**              | Ability to handle growth.                                                                                  |
| **Agility**                  | Ability to quickly provision resources **while processes are running**.                                    |
| **Reliability**              | Probability the system performs as intended for a specified period.                                        |
| **Resiliency**               | Ability to maintain acceptable service **during a fault** (depends on monitoring + HA).                    |
| **Portability**              | Ease of moving apps/data between providers — minimizes vendor lock-in.                                     |
| **Cloud migration**          | Transitioning data, applications, and services from on-premises to the cloud.                              |

### Anchor: Three Confusable Pairs

```
SCALABILITY  ↔  AGILITY
   "can it grow?"     "can it provision quickly while running?"

RELIABILITY  ↔  RESILIENCY
   "does it work?"    "can it ride out a fault?"

ELASTICITY   ↔  SCALABILITY
   "grow AND shrink"  "handle growth"
```

### Self-Check

> Which term describes the ability to **quickly provision new resources while existing processes are running**?
> A) Reliability
> B) Scalability
> C) Agility
> D) Resiliency

**Answer:** C.
**Why the others are wrong:** A is about whether the system works as intended over time. B is about handling growth. D is about surviving a fault.

> What does **portability** primarily minimize?
> A) Cost
> B) Vendor lock-in
> C) Network latency
> D) Storage usage

**Answer:** B.

---

## Module 2 — The Three Service Models: IaaS, PaaS, SaaS

### Concept

This is the single most-tested concept on the exam. You must be able to map who manages what at each level. The trick: **as you move from IaaS → PaaS → SaaS, more is handed to the provider and the customer's control shrinks.**

### Anchor: The Shared-Responsibility Stack

| Layer                                       | On-Prem  | IaaS     | PaaS     | SaaS     |
| ------------------------------------------- | -------- | -------- | -------- | -------- |
| Data                                        | Customer | Customer | Customer | Customer |
| Application                                 | Customer | Customer | Customer | Provider |
| Runtime / Middleware / OS                   | Customer | Customer | Provider | Provider |
| Virtualization / Servers / Network / Storage| Customer | Provider | Provider | Provider |

The customer **always** owns the data. Everything else moves to the provider as you climb the stack.

### Anchor: One-Line Definitions

- **IaaS** — Infrastructure as a Service. Provider supplies virtualized compute, storage, networking. Customer manages OS, runtime, middleware, applications, and data. **Most customer control of any cloud model.** Examples: AWS EC2, Azure VMs.
- **PaaS** — Platform as a Service. Provider supplies a managed platform (OS + runtime + middleware). Customer manages **only the application and data**. Used for fast development without managing the underlying infrastructure.
- **SaaS** — Software as a Service. Provider delivers a fully managed application via a browser. Customer manages **only data and user access**. **Customer has the least amount of control over governance.** Examples: Office 365, Salesforce.

### Anchor: Other "X-as-a-Service" Terms

| Term      | What It Stands For                        |
| --------- | ----------------------------------------- |
| **DaaS**  | Desktop as a Service / Data as a Service  |
| **FaaS**  | Function as a Service (serverless)        |

### Anchor: Common Traps

- **SaaS licensing** is the *provider's* responsibility — not the customer's. PaaS and IaaS customers handle their own software licenses.
- "SaaS means no changes can be made" is **false** — the provider makes changes; tenants typically have customization options.

### Self-Check

> Which model gives the customer the **most** control over the operating system, runtime, and middleware?
> A) IaaS
> B) PaaS
> C) SaaS
> D) FaaS

**Answer:** A.
**Why the others are wrong:** B hands OS/runtime/middleware to the provider. C and D push even more to the provider.

> Under SaaS, the customer is responsible for:
> A) Licensing the application
> B) Patching the operating system
> C) Data and user access
> D) Managing the underlying servers

**Answer:** C.

---

## Module 3 — The Four Deployment Models

### Concept

Deployment models describe **where and for whom** the cloud is built. Confusing the four is one of the most common distractor traps.

### Anchor: The Four Models at a Glance

| Model         | Who Uses It                                          | Hosted On                      | Key Trait                                              |
| ------------- | ---------------------------------------------------- | ------------------------------ | ------------------------------------------------------ |
| **Public**    | Open to the general public                           | The CSP's premises             | Low cost, shared resources, no maintenance burden      |
| **Private**   | A single organization                                | On-premises or hosted          | Tighter security, better privacy, higher cost          |
| **Hybrid**    | Combination of public + private                      | Both                           | Supports **cloud bursting** during peak demand         |
| **Community** | Multiple organizations sharing concerns (e.g., regulatory) | Cooperatively owned/managed | Cost shared across like-minded organizations          |

### Anchor: Cloud Bursting (Hybrid Pattern)

```
                Normal Load                       Peak Load
   ┌─────────────────┐               ┌─────────────────┐  ┌────────────┐
   │  PRIVATE CLOUD  │               │  PRIVATE CLOUD  │→ │   PUBLIC   │
   │  (steady state) │               │  (full)         │  │   CLOUD    │
   └─────────────────┘               └─────────────────┘  └────────────┘
                                          (bursts into public for extra capacity)
```

A private cloud "bursts" into the public cloud for extra capacity without service interruption.

### Anchor: A Common Trap

- **Public cloud is on the CSP's premises**, not the customer's.
- **Private cloud** can be either on-prem or hosted by a service provider — but it is dedicated to a single organization.

### Self-Check

> Several hospitals subject to the same regulatory requirements share a cloud cooperatively. Which deployment model is this?
> A) Public
> B) Private
> C) Hybrid
> D) Community

**Answer:** D.

> A retailer's private cloud handles normal load but automatically pushes overflow into a public cloud during Black Friday. What is this pattern called?
> A) Failover
> B) Cloud bursting
> C) Auto-scaling
> D) Cross-region replication

**Answer:** B.

---

## Module 4 — Scaling, Availability, and Performance

### Concept

The exam tests whether you can pick the right scaling strategy for a scenario. The two pairs to memorize are **scale up vs. scale out**, and **scale-in vs. scale-out policy**.

### Anchor: Vertical vs. Horizontal

```
VERTICAL — "scale up / scale down"          HORIZONTAL — "scale out / scale in"
   Bigger single resource                      More instances
   ┌────────┐    ┌──────────┐                  ┌──┐ ┌──┐ ┌──┐ ┌──┐
   │  CPU   │ →  │   CPU    │                  │  │ │  │ │  │ │  │
   │  RAM   │    │   RAM    │                  └──┘ └──┘ └──┘ └──┘
   └────────┘    │ (more)   │                  behind a load balancer
                 └──────────┘
```

- **Scale up / vertical** — give one machine more CPU, RAM, or disk.
- **Scale out / horizontal** — add more machines (VMs, containers) behind a load balancer.

### Anchor: Auto-Scaling Policies

- **Scale-out policy** — adds resources when load rises.
- **Scale-in policy** — tears resources down when load drops; **manages operational costs**.
- **Auto-scaling** as a whole improves cost-efficiency *and* availability without manual intervention.

### Anchor: Availability and Recovery

| Term                | Meaning                                                                  |
| ------------------- | ------------------------------------------------------------------------ |
| **High Availability (HA)** | Operates continuously without failure for a designated period.    |
| **Failover**        | Automatic switch to a standby/redundant system when the primary fails.   |
| **Disaster Recovery (DR)** | Policies and procedures for restoring after a critical outage.    |

### Self-Check

> Adding more web-server instances behind a load balancer is an example of:
> A) Vertical scaling
> B) Horizontal scaling
> C) Failover
> D) Cloud bursting

**Answer:** B.

> Which policy is most directly aimed at managing operational costs?
> A) Scale-out
> B) Scale-in
> C) Failover
> D) High availability

**Answer:** B. Tearing resources down when they're not needed reduces spend.

---

## Module 5 — Virtualization, Containers, and Serverless

### Concept

You should be fluent in the differences between virtual machines, containers, and serverless functions, and recognize the products associated with each.

### Anchor: VMs vs. Containers vs. Serverless

```
VMs                          CONTAINERS                   SERVERLESS / FaaS
each VM runs full OS         share host OS kernel         no servers to manage
heavy, slow startup          lightweight, fast startup    code runs on demand
managed by hypervisor        managed by container engine  auto-scales by call
```

### Anchor: Virtualization

| Term                | Meaning                                                        |
| ------------------- | -------------------------------------------------------------- |
| **Virtualization**  | Running multiple OS instances on shared hardware.              |
| **Hypervisor**      | The "virtual machine monitor" that makes virtualization work.  |
| **Type 1 hypervisor** | Bare-metal — runs directly on hardware.                      |
| **Type 2 hypervisor** | Runs on top of a host OS.                                    |
| **P2V**             | Physical-to-Virtual migration of an OS, apps, and data.        |
| **V2V**             | Moving VMs between host systems.                               |
| **Vagrant**         | Tool that automates VM provisioning from a configuration file. |

### Anchor: Containers — Products to Know

| Product       | What It Is                                            |
| ------------- | ----------------------------------------------------- |
| **Docker**    | The dominant container runtime (a PaaS for containers). |
| **LXC**       | Linux Containers — an older container technology.     |
| **Kubernetes**| Container **orchestration** at scale.                 |
| **VirtualBox**| **Not a container product** — it's a Type 2 hypervisor (VMs). |

Containers **share the host's OS kernel**, which is why they're so much lighter than full VMs. They're ideal for microservices and agile deployments.

### Anchor: Serverless / FaaS

The provider manages all servers, scaling, and infrastructure. Developers write **functions** that automatically scale based on real-time demand — you pay only for actual execution time.

### Self-Check

> Which is the **key** technical difference between a container and a VM?
> A) Containers run on Linux only; VMs run anywhere.
> B) Containers share the host OS kernel; VMs emulate full operating systems.
> C) Containers use more memory than VMs.
> D) Containers cannot run microservices.

**Answer:** B.

> Which product is **not** a container technology?
> A) Docker
> B) Kubernetes
> C) VirtualBox
> D) LXC

**Answer:** C. VirtualBox is a Type 2 hypervisor for VMs.

---

## Module 6 — Microservices, APIs, and Modern Architecture

### Concept

Beyond the basics, the exam expects you to recognize the architecture patterns and integration mechanisms common to cloud-native development.

### Anchor: Microservices

A monolithic application is broken into small, **independently deployable services**, each owning a slice of functionality. Justified when **multiple teams need to develop, test, and deploy services independently**. Improves agility and maintainability.

### Anchor: APIs — REST vs. SOAP

| Framework | Style                              | Use When                                     |
| --------- | ---------------------------------- | -------------------------------------------- |
| **REST**  | Lightweight, HTTP-based, JSON      | Most modern web/cloud APIs                   |
| **SOAP**  | Heavier, XML-based, more ceremony  | Strict standards / legacy enterprise integrations where REST isn't sufficient |

**API vs. Web Service:** All web services are APIs, but **not all APIs are web services** — some APIs aren't accessible over a network at all.

### Anchor: Edge, CI/CD, and Friends

| Concept                         | Meaning                                                                 |
| ------------------------------- | ----------------------------------------------------------------------- |
| **Edge computing**              | Processing data near where it's generated (IoT, video analysis) to reduce latency and central-server load. |
| **Continuous Integration (CI)** | Integrating code into a shared repo many times a day; small frequent changes. |
| **Continuous Delivery (CD)**    | Extension of CI; code is automatically prepared for release to production. |
| **Memcached layer**             | In-memory cache used in multi-tier architectures to offload read-heavy databases. |
| **Git architecture**            | **Distributed** — every clone has full history; no central coordinating system. |

### Self-Check

> Which best describes the difference between REST and SOAP?
> A) REST is heavier and uses XML; SOAP is lightweight and uses JSON.
> B) REST is lightweight and widely used; SOAP is heavier and used when REST isn't sufficient.
> C) Only SOAP can be used for cloud APIs.
> D) They are identical in practice.

**Answer:** B.

> A shipping company wants to process video from cameras at port locations without sending all of it to a central data center. Which approach fits best?
> A) Cloud bursting
> B) Edge computing
> C) Continuous integration
> D) Federation

**Answer:** B.

---

## Module 7 — Cloud Storage and Redundancy Tiers

### Concept

Two question patterns appear repeatedly: matching the right **storage type** to a workload, and picking the right **redundancy tier** for an availability requirement.

### Anchor: The Three Storage Types

| Type              | Structure                              | Best For                                               |
| ----------------- | -------------------------------------- | ------------------------------------------------------ |
| **Block storage** | Low-latency, dedicated; like DAS/SAN   | Databases, ERP systems, VM disks                        |
| **File storage**  | Hierarchical (folders/files) over NFS/SMB | Shared drives, traditional file workloads             |
| **Object storage**| Objects with metadata + unique IDs     | Unstructured data, media, backups (AWS S3, Azure Blob) |

### Anchor: The Redundancy Tiers (Lowest → Highest)

```
LRS  →  ZRS  →  Regional  →  GRS
 ↓       ↓        ↓             ↓
same   across   across       across
data   zones    regions      geographic
center                       regions
```

| Tier                              | Copies Live                                                 |
| --------------------------------- | ----------------------------------------------------------- |
| **LRS** (Locally Redundant Storage) | Multiple copies in the **same data center**               |
| **ZRS** (Zone Redundant Storage)    | Across availability zones in a region                     |
| **Regional Redundant Storage**      | Across regions                                            |
| **GRS** (Geo-Redundant Storage)     | Across **geographic regions** — best for whole-region outage protection |

The exam favors **GRS** when the question is "we need to survive a whole-region outage."

### Self-Check

> A team needs storage for VM disks running a transactional database. Which is the best fit?
> A) Object storage
> B) File storage
> C) Block storage
> D) Archive storage

**Answer:** C.

> A media company must keep its content available even if an entire AWS region goes offline. Which redundancy tier should they choose?
> A) LRS
> B) ZRS
> C) Regional
> D) GRS

**Answer:** D. GRS replicates across geographic regions.

---

## Module 8 — Networking and Security in Transit

### Concept

"Security in transit" means encrypting data as it moves across a network. The exam tests which protocols protect data in transit and which detection/response systems monitor cloud networks.

### Anchor: Secure-Transit Protocols

| Protocol     | What It Does                                       |
| ------------ | -------------------------------------------------- |
| **VPN**      | Creates a secure tunnel for data transfer          |
| **HTTPS / TLS** | Secure web traffic                              |
| **SSH**      | Secure remote access and file transfer             |
| **IPSec**    | Network-layer encryption                           |
| ~~HTTP~~     | **Insecure** — does **not** protect data in transit |

Plain **HTTP** is the most common distractor here — it's unencrypted and never protects data in transit.

### Anchor: Network Defense Components

| Term                                              | Role                                                                          |
| ------------------------------------------------- | ----------------------------------------------------------------------------- |
| **SDN (Software-Defined Networking)**             | Networking implemented as code/configuration in IaaS; controls connections to VMs. |
| **Firewall**                                      | Hardware/software that filters traffic between networks                       |
| **IDS (Intrusion Detection System)**              | Monitors network for malicious traffic and **generates alerts**               |
| **Tuning**                                        | Adjusting IDS sensors to **minimize false positives** — critical to a successful IDS deployment |
| **SIEM (Security Information & Event Management)** | **Aggregates logs and threat info** for analysis and correlation             |

### Self-Check

> Which protocol does **not** protect data in transit?
> A) HTTPS
> B) SSH
> C) HTTP
> D) IPSec

**Answer:** C.

> Why is *tuning* important to a successful IDS deployment?
> A) It encrypts the IDS console's traffic.
> B) It minimizes false positives so real alerts aren't drowned out.
> C) It moves the IDS to the cloud.
> D) It replaces the firewall.

**Answer:** B.

---

## Module 9 — Identity and Access Management

### Concept

IAM is the second-most-tested cluster on the exam. Many questions hinge on whether students can keep **identification**, **authentication**, and **authorization** straight.

### Anchor: The Three I/A/A Steps (in order)

```
1. IDENTIFICATION    →  "Who are you claiming to be?"   (e.g., type a username)
2. AUTHENTICATION    →  "Prove it."                     (password, token, biometric)
3. AUTHORIZATION     →  "What are you allowed to do?"   (permissions, roles)
        +
4. ACCOUNTING / AUDITING / LOGGING  →  Record what happened
```

### Anchor: The User Account Lifecycle

```
Provisioning  →  Maintenance  →  Deprovisioning
   create        update/manage      remove
```

This is the **canonical order**. Distractors often reorder it.

### Anchor: Federation, SSO, and MFA

| Term                            | What It Does                                                                                  |
| ------------------------------- | --------------------------------------------------------------------------------------------- |
| **Federation**                  | Sharing identity across multiple systems/organizations; **reduces the number of passwords** users must remember. |
| **SSO (Single Sign-On)**        | One login grants access to multiple services                                                  |
| **MFA (Multi-Factor Authentication)** | Adds a second verification step (e.g., a code from a phone). Passwords alone aren't sufficient. |

### Anchor: RBAC — Three Pieces

```
SUBJECT       →   a person or automated agent
ROLE          →   a title or job function defining authority level
PERMISSION    →   the action a role can perform on an object
```

A subject is **assigned a role**; the role grants **permissions** on objects.

### Anchor: Identity Proofing

Validating that a claimed identity actually belongs to the person presenting it. Without identity proofing, IAM is ineffective — risk-based access decisions become guesses.

### Self-Check

> Which IAM step **proves** the claim of identity?
> A) Identification
> B) Authentication
> C) Authorization
> D) Accounting

**Answer:** B.
**Why the others are wrong:** A is the *claim*; C is what you can do once authenticated; D is the historical record.

> Which countermeasure most directly addresses the weakness that **passwords alone aren't sufficient**?
> A) SSO
> B) MFA
> C) Federation
> D) RBAC

**Answer:** B.

---

## Module 10 — Encryption Architecture and the CIA Triad

### Concept

Two foundational security topics share this module: the four-part **encryption architecture** and the **CIA triad**.

### Anchor: The Four Pieces of an Encryption Architecture

1. **Data** — what you're protecting.
2. **Encryption engine** — performs the encryption/decryption.
3. **Encryption keys** — values used in encryption.
4. **Key management** — storage, rotation, and access control of keys.

The exam likes distractors that list only two or three of these. The correct answer always names **all four**.

### Anchor: The CIA Triad

```
        CONFIDENTIALITY
         (only authorized
          people see it)
              ╱╲
             ╱  ╲
            ╱    ╲
   INTEGRITY ─── AVAILABILITY
   (no unauthorized   (authorized users CAN access
    modification)      it when needed)
```

| Pillar               | Plain English                                                                          |
| -------------------- | -------------------------------------------------------------------------------------- |
| **Confidentiality**  | Sensitive information available only to authorized people.                             |
| **Integrity**        | Preventing unauthorized modification or alteration.                                    |
| **Availability**     | Authorized users can access information when needed. (It's about **access**, not denial.) |

A common trap: framing **availability** as "preventing access." That's wrong — availability is about *enabling* access for the right people.

### Anchor: Attack Surface

The set of points where an attacker can attempt to enter or extract data. **Increased by**:

- Open APIs
- More public-facing services
- Unpatched components
- Shadow IT

**Attack Surface Analysis** maps these points so you know what to test. **Resource exhaustion** is a risk specific to cloud environments — less of a concern on-prem with controlled capacity.

### Self-Check

> Which is **not** one of the four required components of an encryption architecture?
> A) Data
> B) Encryption engine
> C) Encryption keys
> D) Public IP address

**Answer:** D. The four are data, engine, keys, and key management.

> Which CIA pillar is **most directly violated** when an attacker silently changes a value in a database?
> A) Confidentiality
> B) Integrity
> C) Availability
> D) Authenticity

**Answer:** B.

---

## Module 11 — Risk, Compliance, and Regulations

### Concept

This is the most vocabulary-heavy module on the exam. Most questions are recognition: "Which law/standard governs *this* type of data?" Memorize the matchings and you'll pick up several questions cheaply.

### Anchor: Risk Vocabulary

| Term                  | Meaning                                                          |
| --------------------- | ---------------------------------------------------------------- |
| **Risk tolerance**    | Amount of risk leadership is **willing to accept**               |
| **Risk threshold**    | Level above which **action must be taken**                       |
| **Risk appetite**     | Level of risk an organization seeks **in pursuit of objectives** |
| **Risk mitigation**   | Steps to reduce risk impact or likelihood                        |

### Anchor: Regulations by Data Domain

| Regulation        | Domain                                       | Region  |
| ----------------- | -------------------------------------------- | ------- |
| **GDPR**          | Personal data of EU citizens                 | EU      |
| **HIPAA / HITECH**| **Health** information                       | US      |
| **FERPA**         | **Educational** records                      | US      |
| **GLBA**          | **Financial** information                    | US      |
| **PCI DSS**       | **Credit-card** data (any entity that transmits, stores, or accepts it) | International / private-sector |
| **FedRAMP**       | US **federal** cloud authorization           | US      |
| **FISMA**         | US Federal Information Security Management Act | US    |

A common trap: confusing **PCI DSS** (credit cards) with **FedRAMP** (federal cloud). FedRAMP does **not** specifically regulate credit cards.

### Anchor: ISO Standards and SOC Audits

| Standard / Audit   | Focus                                                                         |
| ------------------ | ----------------------------------------------------------------------------- |
| **ISO/IEC 27001**  | Requires creation of an **Information Security Management System (ISMS)**     |
| **ISO/IEC 27018**  | International privacy standard developed specifically for **cloud providers** |
| **ISO 27034**      | Integrating security into application management                              |
| **ISO 28000**      | Requirements for a security management system                                 |
| **SOC 1 / 2 / 3**  | Auditing standards — financial controls (SOC 1) vs. security/privacy controls (SOC 2/3) |

### Anchor: PII vs. PHI

| Term                                         | Includes                                                                |
| -------------------------------------------- | ----------------------------------------------------------------------- |
| **PII** (Personally Identifiable Information)| Names, birth dates, emails, SSNs, bank account numbers                  |
| **PHI** (Protected Health Information)       | Demographic + medical/lab/insurance/mental-health data held by healthcare providers |

### Self-Check

> An e-commerce company processes credit-card payments for customers worldwide. Which standard applies most directly?
> A) GDPR
> B) HIPAA
> C) PCI DSS
> D) FedRAMP

**Answer:** C.

> Which regulation gives EU citizens the right to access personal information held about them?
> A) FERPA
> B) GLBA
> C) GDPR
> D) FISMA

**Answer:** C.

> ISO/IEC 27018 is best described as:
> A) A US federal cloud authorization program
> B) An international privacy standard developed specifically for cloud providers
> C) A credit-card data security standard
> D) An auditing report

**Answer:** B.

---

## Module 12 — SDLC, BCDR, and the Data Lifecycle

### Concept

Three related lifecycles share this module: how **software** is built, how a **business recovers** from a disaster, and how **data** moves from creation to destruction.

### Anchor: The Software Development Lifecycle

```
1. Requirements gathering & analysis  ← FIRST PHASE; misuse cases & vulnerability mapping happen here
2. Feasibility study
3. Design
4. Implementation / Development
5. Testing
6. Deployment
7. Maintenance
```

**Best practice:** Information security controls should be **specified during the requirements phase**, not bolted on later.

### Anchor: BCP vs. DRP

| Plan                                      | Focus                                                       |
| ----------------------------------------- | ----------------------------------------------------------- |
| **BCP (Business Continuity Plan)**        | Keeps the **business running** during/after a disaster      |
| **DRP (Disaster Recovery Plan)**          | Restores **IT systems and assets** (servers, data, networks) |

DRP is a subset / partner of BCP. **Who invokes BCDR?** Per the contract/SLA — not by IT or Operations alone.

### Anchor: RTO vs. RPO vs. MTTR

```
     |─────────────────────|─── outage ───|──────────────────────|
     │                     │              │                      │
     │                     │              │                      │
   RPO point             OUTAGE        SYSTEM                  RECOVERY
   (last viable          STARTS        DOWN                    COMPLETE
   data point you'll
   recover TO)
                          ←──── RTO ────→
                          (how fast must we recover?)
                          ←──── MTTR ───→
                          (avg time to repair the component)
```

| Term      | Question It Answers                                                    |
| --------- | ---------------------------------------------------------------------- |
| **RTO** (Recovery Time Objective) | **How fast** must we recover after an outage?                  |
| **RPO** (Recovery Point Objective) | **How much data loss** (in time) is tolerable? The point you recover *to*. |
| **MTTR** (Mean Time To Repair) | Average time to return a repairable component to service          |
| **Failover** | Automatic switching to a redundant system                          |

### Anchor: The Cloud Data Lifecycle (Six Phases, In Order)

```
Create → Store → Use → Share → Archive → Destroy
                                              ↑
                                     final phase is DESTROY
```

A **data retention policy** must define:

- Retention period
- Data formats
- Data security

(Encryption keys and destruction procedures are covered by **separate** policies.)

### Anchor: Data Disposal in the Cloud

Physical destruction and degaussing aren't feasible — the customer doesn't own the disks. The cloud-appropriate option is **cryptographic erasure** (also called *crypto-shredding*): destroying the encryption keys so the encrypted data becomes unreadable.

### Self-Check

> Which is the **first** phase of the SDLC?
> A) Design
> B) Implementation
> C) Requirements gathering and analysis
> D) Testing

**Answer:** C.

> A disaster occurs at noon. The last good backup was at 11:00. The system is restored to that 11:00 state at 12:30. The "11:00 point" is the:
> A) RTO
> B) RPO
> C) MTTR
> D) Failover

**Answer:** B. The point in time you recover *to* is the RPO; how long it took to get there is the RTO.

> Which is the **final** phase of the cloud data lifecycle?
> A) Archive
> B) Share
> C) Destroy
> D) Store

**Answer:** C.

---

## Module 13 — Cost Management, Monitoring, SLAs, and Major CSPs

### Concept

The operational layer: how you keep cloud spending under control, what you monitor, what legal documents define your relationship with the provider, and which providers dominate the market.

### Anchor: Cost-Optimization Levers

| Phase / Lever              | What It Does                                                            |
| -------------------------- | ----------------------------------------------------------------------- |
| **Plan phase**             | Use cost calculators to estimate spend before deploying                 |
| **Track phase / tagging**  | Tag resources so costs can be attributed to teams/projects/environments |
| **Inventory provisioned resources** | So you don't pay for unused services                            |
| **Auto-scaling**           | Automatically adjust resource use to demand                             |
| **Right-sizing**           | Match instance size to actual workload                                  |
| **Reserved instances**     | Lower per-hour cost in exchange for a commitment                        |

Cloud advantages stakeholders care about: **reliability** (CSP SLAs), **cost savings** (no hardware maintenance), and **scalability/elasticity**. ("Single tenancy" is a common distractor — cloud services are typically **multi-tenant**.)

### Anchor: Monitoring Types

Each monitoring category has a specific purpose. Picking the wrong one is a frequent trap.

| Type                       | Watches                                                |
| -------------------------- | ------------------------------------------------------ |
| **Storage monitoring**     | Storage solutions; alerts on issues like the OS disk file becoming unreachable |
| **Network monitoring**     | Networking resources                                   |
| **Database monitoring**    | Database performance and availability                  |
| **Virtual machine monitoring** | VM health                                          |
| **Application monitoring** | Application performance                                |
| **Data consumption monitoring** | Usage volume                                       |

### Anchor: Legal and Contractual Documents

| Document                              | Defines                                                                |
| ------------------------------------- | ---------------------------------------------------------------------- |
| **SLA (Service Level Agreement)**     | What the cloud provider **is and is not responsible for**, levels of support, uptime guarantees, and remedies |
| **NDA (Non-Disclosure Agreement)**    | How parties handle confidential information shared between them        |
| **MSA (Master Service Agreement)**    | Overarching contract between provider and customer                     |
| **OLA (Operational Level Agreement)** | **Internal** agreement between teams supporting an SLA                 |

### Anchor: The Big Three CSPs

| Provider          | Signature Services                                                                |
| ----------------- | --------------------------------------------------------------------------------- |
| **AWS**           | EC2 (compute), S3 (object storage), Lambda (serverless), RDS (managed databases) |
| **Microsoft Azure** | VMs, Blob Storage, Functions, Active Directory                                  |
| **Google Cloud Platform (GCP)** | Strong on **analytics and AI**: BigQuery, AutoML, native TensorFlow integration |

Since CSCs don't have direct visibility into a CSP's data center, they verify provider security through **independent third-party audits and certifications** (SOC reports, ISO certifications, etc.).

### Self-Check

> Which document defines what the cloud provider is and is not responsible for, including uptime guarantees?
> A) NDA
> B) SLA
> C) OLA
> D) MSA

**Answer:** B.

> Which CSP is most associated with **analytics and AI** flagship services such as BigQuery and AutoML?
> A) AWS
> B) Microsoft Azure
> C) Google Cloud Platform
> D) Oracle Cloud

**Answer:** C.

---

## Module 14 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### Reading Scenario Questions Under Time Pressure

The cloud exam loves long scenarios. Before reading the answer choices:

1. **Identify the topic cluster** — is this a service-model question, an IAM question, a compliance question, a BCDR question?
2. **Spot the keywords** — "EU citizens," "credit cards," "patients' health data," "private cloud bursting," "RPO," "RTO." Each one points to one topic.
3. **Translate the scenario into a vocabulary question** — most "scenario" questions are vocabulary in disguise.

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"As you go IaaS → PaaS → SaaS, the customer keeps less; the provider takes more."*
- *"Identification is the claim, authentication proves it, authorization decides what's allowed."*
- *"GDPR = EU; HIPAA = health; FERPA = education; GLBA = finance; PCI DSS = credit cards."*
- *"BCP keeps the business running; DRP restores IT."*
- *"RTO is time; RPO is the point you recover to."*
- *"Containers share the host kernel; VMs don't."*

### Common Misconceptions to Drill

The exam recycles these as distractors. Memorize the correct version:

1. SaaS does **not** mean "no changes can be made" — the provider makes changes; tenants can customize.
2. SaaS licensing is the **provider's** responsibility. PaaS/IaaS customers handle their own.
3. **Authentication ≠ Authorization ≠ Identification.**
4. **GDPR ≠ HIPAA ≠ FERPA ≠ GLBA.** Match each to its data domain.
5. **Containers ≠ VMs.** Containers share the host kernel.
6. **Scale up ≠ Scale out.** Up = bigger one; out = more of them.
7. **BCP ≠ DRP.** BCP business; DRP IT.
8. **RTO ≠ RPO.** RTO time; RPO data point.
9. **REST is lightweight; SOAP is heavy.** Both build APIs.
10. **Public cloud is on the CSP's premises**, not the customer's.
11. **Independent third-party audits/certifications** are how CSCs verify CSP security.
12. **Cryptographic erasure** is the cloud-appropriate data-destruction method — not physical destruction or degaussing.

### Mock Quiz (12 Questions Across the Whole Exam)

Try these timed — about 75 seconds per question.

1. In which model does the customer manage **only** data and user access?
2. Which deployment model lets a private cloud "burst" into a public cloud during peak demand?
3. Adding more web-server instances behind a load balancer is which kind of scaling?
4. What is the **key** technical difference between a container and a VM?
5. Which storage redundancy tier best survives a whole-region outage?
6. Which protocol does **not** protect data in transit — HTTPS, SSH, HTTP, or IPSec?
7. Which IAM step *proves* the claim of identity?
8. Which is the cornerstone CIA pillar that an attacker silently modifying data violates?
9. Which regulation governs personal data of EU citizens?
10. Which is the **first** phase of the SDLC?
11. The "point in time you recover to" is the:
12. Which document defines a cloud provider's uptime guarantees and responsibilities?

#### Answer Key (cover until done)

1. **SaaS** — Module 2.
2. **Hybrid cloud (cloud bursting)** — Module 3.
3. **Horizontal scaling (scale out)** — Module 4.
4. **Containers share the host OS kernel; VMs emulate full operating systems.** — Module 5.
5. **GRS (Geo-Redundant Storage)** — Module 7.
6. **HTTP** — Module 8.
7. **Authentication** — Module 9.
8. **Integrity** — Module 10.
9. **GDPR** — Module 11.
10. **Requirements gathering and analysis** — Module 12.
11. **RPO (Recovery Point Objective)** — Module 12.
12. **SLA (Service Level Agreement)** — Module 13.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> Cloud computing delivers compute, storage, networking, and software over the Internet on demand. The CSP is the vendor; the CSC is the customer; cloud is multi-tenant. Scalability handles growth; agility provisions resources quickly while running; reliability is "does it work?"; resiliency is "does it survive a fault?"; portability minimizes vendor lock-in. Service models: **IaaS** (provider does virtualization/servers/network/storage; customer keeps OS, runtime, middleware, app, data — most customer control), **PaaS** (provider also manages OS/runtime/middleware; customer keeps app and data), **SaaS** (provider runs the whole app; customer keeps only data and user access — least control). Customer always owns data. SaaS licensing is the provider's job. Deployment models: **Public** (on CSP's premises, open to all), **Private** (single org, more secure, more expensive), **Hybrid** (mix; supports cloud bursting), **Community** (multiple organizations sharing concerns). Scaling: **vertical/up** = bigger single resource; **horizontal/out** = more instances. Auto-scaling improves cost and availability; scale-in policies manage cost. **Containers share the host OS kernel and are lightweight; VMs use a hypervisor (Type 1 bare-metal, Type 2 on host OS) and emulate full OSes.** Docker, LXC, Kubernetes are containers; VirtualBox is a hypervisor. **FaaS / serverless** auto-scales code on demand. **Microservices** = small independently deployable services. **REST is lightweight; SOAP is heavier.** All web services are APIs; not all APIs are web services. **Edge computing** processes data near where it's generated. **CI** integrates often; **CD** prepares code for release. Storage: **block** for databases/VMs, **file** for shared drives, **object** for unstructured data. Redundancy: LRS → ZRS → Regional → **GRS** (best for whole-region outages). Security in transit: **VPN, HTTPS/TLS, SSH, IPSec** — never plain HTTP. **IDS** alerts on malicious traffic; **tuning** minimizes false positives; **SIEM** aggregates and correlates logs. IAM order: **Identification → Authentication → Authorization → Accounting**. User lifecycle: **Provisioning → Maintenance → Deprovisioning**. **Federation** reduces password counts; **SSO** is one login for many services; **MFA** beats passwords alone. **RBAC**: subject + role + permission. Encryption needs four pieces: **data, engine, keys, key management**. CIA: **Confidentiality** (limit who sees), **Integrity** (no unauthorized changes), **Availability** (authorized users CAN access). Risk: tolerance (willing to accept), threshold (must act), appetite (seeks to take), mitigation (reduce). Regulations: **GDPR** = EU privacy; **HIPAA** = US health; **FERPA** = US education; **GLBA** = US finance; **PCI DSS** = credit cards anywhere; **FedRAMP** = US federal cloud (not credit cards); **ISO 27001** requires an ISMS; **ISO 27018** is privacy for cloud providers. **PII** vs **PHI** — health data is PHI. SDLC: **Requirements → Feasibility → Design → Implementation → Testing → Deployment → Maintenance**; specify security in requirements. **BCP** keeps business running; **DRP** restores IT. **RTO** = how fast to recover; **RPO** = the point you recover to; **MTTR** = avg repair time. Cloud data lifecycle: **Create → Store → Use → Share → Archive → Destroy**. Retention policy = period + format + security. Use **cryptographic erasure** to destroy cloud data. Cost: tag everything, right-size, reserve, auto-scale. **SLA** defines provider responsibilities and uptime; **NDA** protects confidentiality; **MSA** is the master contract; **OLA** is internal. AWS = EC2/S3/Lambda; Azure = VMs/Blob/Functions/AD; GCP = analytics/AI (BigQuery, AutoML, TensorFlow). CSCs verify CSP security through independent third-party audits.

---

## Master Glossary

**Agility** — ability to quickly provision resources while existing processes are running.

**API (Application Programming Interface)** — interface for one piece of software to communicate with another. All web services are APIs; not all APIs are web services.

**Attack Surface** — set of points where an attacker can attempt to enter or extract data; increased by open APIs, public-facing services, unpatched components, and shadow IT.

**Authentication** — verifying a claimed identity (e.g., password + MFA).

**Authorization** — determining what an authenticated user is allowed to do.

**Auto-scaling** — automatically adding or removing resources based on demand.

**BCP (Business Continuity Plan)** — keeps business functions running during/after a disaster.

**Block Storage** — low-latency dedicated storage; ideal for databases and VM disks.

**Cloud Bursting** — hybrid pattern in which a private cloud overflows into a public cloud during peak demand.

**Cloud Computing** — on-demand delivery of compute, storage, networking, and software over the Internet.

**Community Cloud** — cloud shared by multiple organizations with common concerns (e.g., regulatory).

**Confidentiality** — sensitive information available only to authorized people (CIA pillar).

**Container** — OS-level virtualization that shares the host's kernel; lighter and faster than a VM.

**CSC (Cloud Service Customer)** — organization consuming a cloud service.

**CSP (Cloud Service Provider)** — vendor offering cloud services (AWS, Azure, GCP).

**Cryptographic Erasure (Crypto-shredding)** — destroying encryption keys so the encrypted data is unreadable.

**DaaS** — Desktop as a Service, or Data as a Service.

**Deprovisioning** — removing a user account or releasing a cloud resource.

**DRP (Disaster Recovery Plan)** — focuses on restoring IT systems and assets.

**Edge Computing** — processing data close to where it's generated to reduce latency and central-server load.

**Elasticity** — ability for resources to grow and shrink on demand.

**Encryption Architecture** — the four required components: data, engine, keys, key management.

**FaaS** — Function as a Service (serverless).

**Failover** — automatic switching to a redundant system when the primary fails.

**FedRAMP** — US federal cloud authorization standard.

**Federation** — sharing identity across systems/organizations; reduces password sprawl.

**FERPA** — US law protecting educational records.

**File Storage** — hierarchical (folders/files) network-accessible storage (NFS/SMB).

**Firewall** — hardware/software that filters traffic between networks.

**FISMA** — US Federal Information Security Management Act.

**GDPR** — EU privacy regulation; supersedes local laws for EU citizens' data.

**GLBA** — US law protecting financial information.

**GRS (Geo-Redundant Storage)** — replicates data across geographic regions; survives whole-region outages.

**HA (High Availability)** — operating continuously without failure for a designated period.

**HIPAA / HITECH** — US laws protecting health information.

**Hybrid Cloud** — combines public and private clouds; supports cloud bursting.

**Hypervisor** — virtual machine monitor; Type 1 is bare-metal, Type 2 runs on a host OS.

**IaaS (Infrastructure as a Service)** — provider supplies virtualized compute, storage, networking; customer manages OS, runtime, middleware, applications, and data.

**IAM (Identity and Access Management)** — combined system for identification, authentication, authorization, and accounting.

**Identification** — claiming an identity (e.g., entering a username).

**IDS (Intrusion Detection System)** — monitors a network for malicious traffic and alerts.

**Integrity** — preventing unauthorized modification (CIA pillar).

**ISO/IEC 27001** — standard requiring an Information Security Management System (ISMS).

**ISO/IEC 27018** — international privacy standard developed for cloud providers.

**Kubernetes** — container orchestration platform.

**LRS (Locally Redundant Storage)** — multiple copies in the same data center.

**MFA (Multi-Factor Authentication)** — adds a second verification step beyond password.

**Microservices** — small, independently deployable services that compose an application.

**MSA (Master Service Agreement)** — overarching contract between provider and customer.

**MTTR (Mean Time To Repair)** — average time to return a repairable component to service.

**Multi-tenancy** — multiple customers' workloads share physical infrastructure with logical isolation.

**NDA (Non-Disclosure Agreement)** — legal document protecting confidential information.

**Object Storage** — stores data as objects with metadata and unique IDs (e.g., S3, Azure Blob).

**OLA (Operational Level Agreement)** — internal agreement between teams supporting an SLA.

**P2V (Physical to Virtual)** — migrating an OS, applications, and data from a physical disk into a VM.

**PaaS (Platform as a Service)** — provider manages OS, runtime, and middleware; customer manages application and data.

**PCI DSS** — Payment Card Industry Data Security Standard; required for entities that transmit, store, or accept credit-card data.

**PHI (Protected Health Information)** — demographic plus medical/insurance/mental-health data.

**PII (Personally Identifiable Information)** — names, birth dates, emails, SSNs, account numbers, etc.

**Portability** — ease of moving applications and data between cloud environments.

**Private Cloud** — cloud dedicated to a single organization.

**Provisioning** — allocating cloud resources or creating a user account.

**Public Cloud** — cloud open to general public, hosted on the CSP's premises.

**RBAC (Role-Based Access Control)** — subjects are assigned roles; roles grant permissions on objects.

**Reliability** — probability the system performs as intended for a specified period.

**Resiliency** — ability to maintain acceptable service during a fault.

**Resource Exhaustion** — a risk specific to cloud where shared resources can be depleted.

**REST** — lightweight, HTTP-based API framework.

**Risk Appetite** — level of risk an organization seeks in pursuit of objectives.

**Risk Mitigation** — steps to reduce risk impact or likelihood.

**Risk Threshold** — level of risk above which action must be taken.

**Risk Tolerance** — amount of risk leadership is willing to accept.

**RPO (Recovery Point Objective)** — point in time to which data must be recoverable; how much data loss is tolerable.

**RTO (Recovery Time Objective)** — maximum allowed time to recover after an outage.

**SaaS (Software as a Service)** — provider runs the whole application; customer manages only data and user access.

**Scale In / Scale Out** — remove / add instances (horizontal scaling).

**Scale Up / Scale Down** — increase / decrease the capacity of a single resource (vertical scaling).

**SDLC (Software Development Lifecycle)** — Requirements → Feasibility → Design → Implementation → Testing → Deployment → Maintenance.

**SDN (Software-Defined Networking)** — networking implemented as code/configuration in IaaS.

**SIEM** — Security Information and Event Management; aggregates and correlates logs.

**SLA (Service Level Agreement)** — defines provider responsibilities, support, uptime, and remedies.

**SOAP** — heavier, XML-based API framework.

**SOC 1 / 2 / 3** — auditing standards for financial (SOC 1) vs. security/privacy (SOC 2/3) controls.

**SSO (Single Sign-On)** — one login grants access to multiple services.

**Tenant** — a customer in a multi-tenant cloud environment.

**Tuning (IDS)** — adjusting sensors to minimize false positives.

**V2V** — moving virtual machines between host systems.

**Vagrant** — tool that automates VM provisioning from a configuration file.

**VPN (Virtual Private Network)** — secure tunnel for data transfer.

**ZRS (Zone Redundant Storage)** — replicates data across availability zones in a region.
