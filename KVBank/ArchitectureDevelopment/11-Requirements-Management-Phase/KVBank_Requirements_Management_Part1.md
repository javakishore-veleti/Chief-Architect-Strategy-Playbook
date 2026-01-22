# KVBank

## Requirements Management Phase

### Part 1: Requirements Management Framework

### *The Central Hub of Architecture Development*

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Requirements Management Phase - Part 1 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Introduction and Purpose
2. Requirements Management in ADM Context
3. Requirements Management Process
4. Requirements Repository
5. Requirements Classification and Prioritization
6. Requirements Traceability
7. Summary

---

# 1. Introduction and Purpose

## 1.1 Purpose of Requirements Management

Requirements Management is the continuous process that sits at the center of the TOGAF Architecture Development Method (ADM). Unlike other phases that are executed in sequence, Requirements Management operates throughout the entire ADM cycle, ensuring that requirements are properly managed, changes are handled effectively, and the architecture remains aligned with stakeholder needs.

**KEY PRINCIPLE: Being able to handle change at any time is crucial for the ADM to succeed.**

## 1.2 Objectives

| Objective | Description |
|-----------|-------------|
| Sustain All Phases | Ensure requirements process is maintained through all ADM phases |
| Handle Change | Provide continuous capability to manage change during any phase |
| Maintain Alignment | Keep architecture aligned with evolving business needs |
| Enable Traceability | Link requirements to architecture components and deliverables |
| Support Decisions | Provide information for architecture decision-making |
| Manage Conflicts | Identify and resolve conflicting requirements |

## 1.3 Requirements Management Position in ADM

Requirements Management occupies the **CENTER** of the ADM cycle, interacting with all phases:

```
                           Preliminary
                               │
              Phase H ◄── Requirements ──► Phase A
                  │        Management         │
              Phase G ◄──   (CENTER)    ──► Phase B
                  │             │             │
              Phase F ◄─────────┼──────────► Phase C
                        \       │       /
                         Phase E ─ Phase D
```

This central position means Requirements Management:
- Receives inputs from **ALL** phases
- Provides outputs to **ALL** phases
- Operates **CONTINUOUSLY** throughout the ADM cycle
- Handles changes that emerge at **ANY** time

## 1.4 Key Inputs and Outputs

### 1.4.1 Inputs to Requirements Management

| Source Phase | Input | Description |
|--------------|-------|-------------|
| Preliminary | Principles & Constraints | Foundation requirements from governance |
| Phase A | Business Requirements | High-level stakeholder requirements |
| Phase B | Business Architecture Requirements | Process and capability requirements |
| Phase C | IS Architecture Requirements | Application and data requirements |
| Phase D | Technology Requirements | Infrastructure and platform requirements |
| Phase E | Implementation Requirements | Project and migration requirements |
| Phase F | Planning Requirements | Transition and sequencing requirements |
| Phase G | Operational Requirements | Deployment and operations requirements |
| Phase H | Change Requirements | Requirements from change management |

### 1.4.2 Outputs from Requirements Management

| Output | Description | Consumers |
|--------|-------------|-----------|
| Requirements Repository | Central store of all requirements | All phases |
| Requirements Impact Assessment | Analysis of requirement changes | Phase E, F, G, H |
| Requirements Traceability Matrix | Links between requirements and architecture | All phases |
| Requirements Prioritization | Ranked requirements for implementation | Phase E, F |
| Conflict Resolution | Resolved conflicting requirements | All phases |

---

# 2. Requirements Management in ADM Context

## 2.1 Interaction with ADM Phases

| ADM Phase | Requirements Management Role | Key Activities |
|-----------|------------------------------|----------------|
| Preliminary | Establish requirements framework | Define process, tools, governance |
| Phase A: Vision | Capture initial business requirements | Stakeholder concerns, business goals |
| Phase B: Business | Elaborate business requirements | Process, capability, organization reqs |
| Phase C: IS | Define application & data requirements | Functional, data, integration reqs |
| Phase D: Technology | Specify technology requirements | Platform, infrastructure, NFRs |
| Phase E: Opportunities | Validate implementation requirements | Project constraints, dependencies |
| Phase F: Planning | Confirm transition requirements | Migration, sequencing requirements |
| Phase G: Governance | Track implementation requirements | Compliance, deployment requirements |
| Phase H: Change | Process change requirements | New, modified, retired requirements |

## 2.2 Requirements Flow Through ADM

**REQUIREMENTS LIFECYCLE IN ADM:**

```
Phase A: IDENTIFY → Phase B-D: ELABORATE → Phase E-F: VALIDATE → Phase G: IMPLEMENT → Phase H: EVOLVE
```

At each stage, Requirements Management ensures:
- New requirements are captured and classified
- Existing requirements are refined or retired
- Changes are assessed for impact
- Traceability is maintained
- Conflicts are identified and resolved

## 2.3 KVBank Requirements by ADM Phase

| Phase | Requirements Count | Example Requirements | Status |
|-------|-------------------|----------------------|--------|
| Preliminary | 12 | Architecture principles, governance | Baselined |
| Phase A | 45 | Digital-first, 500K customers, €40M revenue | Baselined |
| Phase B | 127 | Digital onboarding, instant payments, wealth mgmt | Baselined |
| Phase C | 234 | Microservices, event-driven, API-first | Baselined |
| Phase D | 189 | AWS, Kubernetes, Kafka, PostgreSQL | Baselined |
| Phase E | 78 | 12 work packages, phased delivery | Baselined |
| Phase F | 56 | 24-month roadmap, 4 phases | Baselined |
| Phase G | 42 | 99.99% availability, compliance | Active |
| Phase H | 23 | GenAI platform, crypto services | Active |
| **TOTAL** | **806** | | |

---

# 3. Requirements Management Process

## 3.1 Process Overview

The Requirements Management process is continuous and operates in parallel with all ADM phases:

```
REQUIREMENTS MANAGEMENT PROCESS:

IDENTIFY → CAPTURE → CLASSIFY → ANALYZE → PRIORITIZE → TRACE → VALIDATE → MANAGE CHANGE
    ▲                                                                            │
    └────────────────────── CONTINUOUS CYCLE ────────────────────────────────────┘
```

## 3.2 Process Steps

### 3.2.1 Step 1: Identify Requirements

| Activity | Description | Techniques |
|----------|-------------|------------|
| Stakeholder Analysis | Identify all stakeholders and their concerns | Stakeholder mapping |
| Business Goal Analysis | Extract requirements from business objectives | Goal decomposition |
| Gap Analysis | Identify requirements from baseline/target gaps | Gap assessment |
| Constraint Analysis | Identify constraints that become requirements | Constraint catalog |
| Assumption Analysis | Convert assumptions to requirements | Assumption validation |

### 3.2.2 Step 2: Capture Requirements

| Source | Capture Method | Output Format |
|--------|----------------|---------------|
| Stakeholder Interviews | Structured interviews with key stakeholders | Interview notes, requirement statements |
| Workshops | Facilitated sessions with multiple stakeholders | Workshop outputs, user stories |
| Document Analysis | Review existing documentation | Extracted requirements |
| Process Analysis | Analyze business processes | Process requirements |
| System Analysis | Review existing systems | Technical requirements |
| Regulatory Review | Analyze regulatory requirements | Compliance requirements |

### 3.2.3 Step 3: Classify Requirements

| Classification | Description | Examples |
|----------------|-------------|----------|
| Business Requirements | High-level business needs and objectives | Revenue targets, market share |
| Stakeholder Requirements | Needs of specific stakeholder groups | User experience, reporting |
| Functional Requirements | What the system must do | Process payments, KYC |
| Non-Functional Requirements | Quality attributes and constraints | Performance, security |
| Transition Requirements | Requirements for migration/change | Data migration, training |
| Implementation Constraints | Restrictions on implementation | Technology, timeline |

### 3.2.4 Step 4: Analyze Requirements

| Analysis Type | Purpose | Output |
|---------------|---------|--------|
| Completeness Analysis | Ensure all necessary requirements captured | Gap identification |
| Consistency Analysis | Check for conflicting requirements | Conflict register |
| Feasibility Analysis | Assess technical and business feasibility | Feasibility assessment |
| Impact Analysis | Understand impact of requirements | Impact assessment |
| Dependency Analysis | Identify requirement dependencies | Dependency matrix |
| Risk Analysis | Identify requirements-related risks | Risk register update |

### 3.2.5 Step 5: Prioritize Requirements

| Priority Level | Description | Criteria |
|----------------|-------------|----------|
| Critical | Must have - system cannot function without | Regulatory, core business, safety |
| High | Should have - significant business value | Major functionality, key stakeholder |
| Medium | Could have - desirable but not essential | Efficiency gains, nice-to-have |
| Low | Won't have this time - future consideration | Minor features, future phases |

## 3.3 Requirements Management Roles

| Role | Responsibilities | KVBank Assignment |
|------|------------------|-------------------|
| Requirements Manager | Overall ownership of requirements process | Business Architect |
| Business Analyst | Elicit, document, and validate requirements | BA Team (8 FTEs) |
| Domain Architect | Validate technical feasibility | Domain Architects |
| Product Owner | Prioritize and accept requirements | Product Owners |
| Stakeholder | Provide and validate requirements | Business Units |
| Quality Assurance | Verify requirements are testable | QA Team |

---

# 4. Requirements Repository

## 4.1 Repository Structure

The Requirements Repository is the central store for all architecture requirements across the ADM cycle.

```
Requirements Repository
├── Business Requirements
│     ├── Strategic Requirements
│     ├── Operational Requirements
│     └── Regulatory Requirements
├── Architecture Requirements
│     ├── Business Architecture
│     ├── Data Architecture
│     ├── Application Architecture
│     └── Technology Architecture
├── Non-Functional Requirements
│     ├── Performance
│     ├── Security
│     ├── Scalability
│     └── Availability
└── Transition Requirements
      ├── Migration
      ├── Training
      └── Deployment
```

## 4.2 Requirements Attributes

| Attribute | Description | Example |
|-----------|-------------|---------|
| Requirement ID | Unique identifier | REQ-BUS-001 |
| Name | Short descriptive name | Digital Onboarding |
| Description | Detailed requirement statement | Enable 100% digital... |
| Category | Classification type | Functional |
| Priority | Importance level | Critical |
| Source | Where requirement originated | Stakeholder interview |
| Owner | Responsible stakeholder | Head of Digital |
| Status | Current state | Approved |
| ADM Phase | Phase where requirement identified | Phase A |
| Work Package | Implementation work package | WP-04 |
| Version | Requirement version | 1.2 |
| Created Date | When requirement was created | 2024-01-15 |
| Modified Date | Last modification date | 2024-03-20 |

## 4.3 Requirements Status Lifecycle

| Status | Description | Transitions To |
|--------|-------------|----------------|
| Draft | Initial capture, under elaboration | Proposed, Rejected |
| Proposed | Submitted for review | Approved, Rejected, Draft |
| Approved | Accepted and baselined | In Progress, Deferred |
| In Progress | Being implemented | Implemented, Blocked |
| Implemented | Development complete | Verified, In Progress |
| Verified | Tested and validated | Closed, In Progress |
| Closed | Requirement fulfilled | Reopened |
| Deferred | Postponed to future phase | Proposed, Retired |
| Rejected | Not accepted | Draft (if reconsidered) |
| Retired | No longer applicable | - |

## 4.4 KVBank Requirements Repository Summary

| Category | Total | Draft | Approved | In Progress | Closed | Deferred |
|----------|-------|-------|----------|-------------|--------|----------|
| Business Requirements | 182 | 12 | 45 | 67 | 48 | 10 |
| Data Architecture | 124 | 8 | 32 | 54 | 25 | 5 |
| Application Architecture | 198 | 15 | 48 | 89 | 38 | 8 |
| Technology Architecture | 156 | 10 | 38 | 72 | 30 | 6 |
| Non-Functional | 89 | 5 | 24 | 42 | 15 | 3 |
| Transition | 57 | 3 | 18 | 25 | 8 | 3 |
| **TOTAL** | **806** | **53** | **205** | **349** | **164** | **35** |

## 4.5 Sample Requirements

### 4.5.1 Business Requirement Example

| Attribute | Value |
|-----------|-------|
| Requirement ID | REQ-BUS-001 |
| Name | Digital Customer Onboarding |
| Description | Enable 100% digital customer onboarding with real-time KYC verification, allowing customers to open accounts within 10 minutes without visiting a branch |
| Category | Business Requirement - Functional |
| Priority | Critical |
| Source | Phase A - Architecture Vision Workshop |
| Owner | Head of Digital Banking |
| Status | In Progress |
| Work Package | WP-04 Digital Channels |
| Acceptance Criteria | 1) <10 min end-to-end, 2) 95% straight-through processing, 3) Real-time ID verification |

### 4.5.2 Non-Functional Requirement Example

| Attribute | Value |
|-----------|-------|
| Requirement ID | REQ-NFR-015 |
| Name | API Response Time |
| Description | All customer-facing APIs must respond within 200ms at the 95th percentile under normal load conditions |
| Category | Non-Functional - Performance |
| Priority | Critical |
| Source | Phase D - Technology Architecture |
| Owner | Chief Architect |
| Status | In Progress |
| Work Package | WP-01 Platform Foundation |
| Measurement | Datadog APM P95 latency metrics |

---

# 5. Requirements Classification and Prioritization

## 5.1 Classification Framework

### 5.1.1 By Architecture Domain

| Domain | Scope | Count | Percentage |
|--------|-------|-------|------------|
| Business Architecture | Processes, capabilities, organization, information | 182 | 23% |
| Data Architecture | Data entities, quality, governance, lifecycle | 124 | 15% |
| Application Architecture | Applications, services, integrations, APIs | 198 | 25% |
| Technology Architecture | Infrastructure, platforms, networks, tools | 156 | 19% |
| Cross-Cutting | NFRs, security, compliance, transitions | 146 | 18% |

### 5.1.2 By Requirement Type

| Type | Description | Count | Examples |
|------|-------------|-------|----------|
| Functional | What the system must do | 423 (52%) | Process payment |
| Non-Functional | Quality attributes | 189 (23%) | 99.99% uptime |
| Constraint | Restrictions and limitations | 98 (12%) | Must use AWS |
| Transition | Migration and change requirements | 96 (13%) | Data migration |

### 5.1.3 By Work Package

| Work Package | Requirements | Critical | High | Medium | Low |
|--------------|--------------|----------|------|--------|-----|
| WP-01 Platform Foundation | 89 | 34 | 28 | 19 | 8 |
| WP-02 Core Banking | 124 | 52 | 41 | 24 | 7 |
| WP-03 Data Platform | 78 | 28 | 25 | 18 | 7 |
| WP-04 Digital Channels | 112 | 38 | 42 | 25 | 7 |
| WP-05 Payments | 86 | 45 | 26 | 12 | 3 |
| WP-06 Risk & Compliance | 94 | 56 | 24 | 11 | 3 |
| WP-07 Wealth Management | 67 | 22 | 25 | 15 | 5 |
| WP-08 to WP-12 | 156 | 48 | 56 | 38 | 14 |
| **TOTAL** | **806** | **323** | **267** | **162** | **54** |

## 5.2 Prioritization Framework

### 5.2.1 MoSCoW Prioritization

| Priority | Definition | KVBank Count | Percentage | Example |
|----------|------------|--------------|------------|---------|
| Must Have | Non-negotiable, critical for success | 323 | 40% | Payment processing |
| Should Have | Important but not critical | 267 | 33% | Mobile biometrics |
| Could Have | Desirable if resources permit | 162 | 20% | Voice banking |
| Won't Have | Out of scope for this cycle | 54 | 7% | Crypto trading |

### 5.2.2 Value vs. Complexity Matrix

|  | Low Complexity | Medium Complexity | High Complexity |
|--|----------------|-------------------|-----------------|
| **High Value** | 🟢 Quick Wins (145 reqs) | 🟢 Major Projects (198 reqs) | 🟡 Strategic (124 reqs) |
| **Medium Value** | 🟢 Fill-ins (89 reqs) | 🟡 Scheduled (112 reqs) | 🟡 Evaluate (67 reqs) |
| **Low Value** | 🟡 If Time (34 reqs) | 🟠 Reconsider (25 reqs) | 🟠 Avoid (12 reqs) |

## 5.3 Prioritization Criteria

| Criterion | Description | Weight | Scoring |
|-----------|-------------|--------|---------|
| Business Value | Revenue, cost savings, strategic alignment | 30% | 1-5 scale |
| Regulatory Mandate | Legal or compliance requirement | 25% | Yes/No |
| Customer Impact | Effect on customer experience | 20% | 1-5 scale |
| Technical Risk | Implementation complexity and risk | 15% | 1-5 scale |
| Dependencies | Blocking other requirements | 10% | Count |

---

# 6. Requirements Traceability

## 6.1 Traceability Framework

Requirements traceability ensures that every requirement can be traced to its source (backward traceability) and to its implementation (forward traceability).

**TRACEABILITY CHAIN:**

```
Business Goal → Business Req → Architecture Req → Design → Implementation → Test → Deployment
```

## 6.2 Traceability Matrix Structure

| Trace Type | From | To | Purpose |
|------------|------|-----|---------|
| Business Trace | Business Goal | Business Requirement | Ensure goal coverage |
| Architecture Trace | Business Requirement | Architecture Component | Ensure design coverage |
| Implementation Trace | Architecture Component | Work Package/Sprint | Ensure implementation |
| Test Trace | Requirement | Test Case | Ensure test coverage |
| Deployment Trace | Implementation | Deployed Component | Ensure deployment |

## 6.3 Sample Traceability Matrix

| Requirement ID | Business Goal | Arch Component | Work Package | Test Case | Status |
|----------------|---------------|----------------|--------------|-----------|--------|
| REQ-BUS-001 | BG-01 Digital First | Customer Service | WP-04 | TC-ONB-001 | In Progress |
| REQ-BUS-015 | BG-02 Instant Payments | Payment Service | WP-05 | TC-PAY-012 | In Progress |
| REQ-NFR-015 | BG-05 Excellence | API Gateway | WP-01 | TC-PERF-001 | Verified |
| REQ-DAT-008 | BG-03 Data-Driven | Data Lake | WP-03 | TC-DAT-008 | Implemented |
| REQ-SEC-021 | BG-04 Trust | Security Framework | WP-11 | TC-SEC-021 | Verified |

## 6.4 Traceability Coverage

| Trace Level | Total Items | Traced | Coverage | Target |
|-------------|-------------|--------|----------|--------|
| Business Goals to Requirements | 806 | 798 | 99% | 100% |
| Requirements to Architecture | 806 | 756 | 94% | >95% |
| Requirements to Work Packages | 806 | 771 | 96% | >95% |
| Requirements to Test Cases | 806 | 689 | 85% | >90% |
| Implemented to Verified | 349 | 312 | 89% | >90% |

## 6.5 Traceability Tools

| Tool | Purpose | Integration |
|------|---------|-------------|
| Jira | Requirements and work item management | Confluence, GitHub |
| Confluence | Requirements documentation | Jira |
| Enterprise Architect | Architecture modeling and traceability | Jira (via API) |
| TestRail | Test case management and traceability | Jira |
| Custom Dashboard | Traceability reporting and metrics | All tools (via API) |

---

# 7. Summary

## 7.1 Part 1 Deliverables

| Deliverable | Status | Section |
|-------------|--------|---------|
| Requirements Management Purpose & Objectives | ✅ Complete | Section 1 |
| ADM Phase Interactions | ✅ Complete | Section 2 |
| Requirements Management Process | ✅ Complete | Section 3 |
| Requirements Repository Structure | ✅ Complete | Section 4 |
| Classification Framework | ✅ Complete | Section 5 |
| Prioritization Framework | ✅ Complete | Section 5.2 |
| Traceability Framework | ✅ Complete | Section 6 |

## 7.2 Key Metrics

| Metric | Value |
|--------|-------|
| Total Requirements | 806 |
| Critical Requirements | 323 (40%) |
| Requirements In Progress | 349 (43%) |
| Requirements Closed | 164 (20%) |
| Traceability Coverage (to Architecture) | 94% |
| Test Coverage | 85% |

## 7.3 Next Steps (Part 2)

1. Requirements Change Control Process
2. Requirements Baseline Management
3. Impact Assessment Process
4. Requirements Governance
5. Requirements Management Tools & Metrics

---

**Document End - Part 1**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Program Director | CTO |
| [Date] | [Date] | [Date] |
