# Architecture Development - Data Architecture Phase

## Steps for Data Architecture Phase

1. Select reference models, viewpoints and tools
2. Develop baseline architecture description
3. Develop target architecture descriptino
4. Perform gap analysis
5. Define candidate roadmap components
6. Resolve impacts across the architecture landscape
7. Conduct formal stakeholder review
8. Finalize Data Architecture
9. Create architecture definition document

## Outputs from Data Architecture Phase

1. Refined Phase A Deliverables
2. Define architecture definition document
    a. Baseline data architecture, approved version
    b. Target data architecture, approved version
3. Draft architecture requirements specification - gap analysis
4. Data architecture components of an architecture roadmap    

## Artifacts Produced

### Catalogs
1. Data entity/data component catalog

## Matrices
1. Data entity/business functions  matrix
2. Application/Data matrix

## Diagrams
1. Conceptual data diagram
2. Logical Data diagram
3. Data dissemination diagram
4. Data Security Diagram
5. Data Migration Diagram
6. Data lifecycle diagram


# Phase C: Data Architecture - Part 1 (Steps, Outputs, and Core Architecture):

## Contents:

1. Introduction and Purpose - Objectives, scope, relationship to Phase B
2. Reference Models, Viewpoints and Tools - BIAN, ISO 20022, FIBO, GDPR, tools (Kafka, Delta Lake, etc.)
3. Baseline Data Architecture - Current data landscape, quality assessment, governance gaps
4. Target Data Architecture - Principles, domains, platform architecture
5. Gap Analysis - Capability gaps, domain gaps, technology gaps
6. Candidate Roadmap Components - 12 work packages (DA-01 to DA-12), €10M over 18 months
7. Architecture Definition Document - Components and decisions
8. Requirements Specification - Functional and non-functional requirements



```text

Phase C: Data Architecture - Part 2 (Catalogs and Matrices):
Contents:
1. Data Entity/Data Component Catalog (87 entities across 9 domains):

Customer Domain (10 entities)
Account Domain (10 entities)
Transaction Domain (10 entities)
Card Domain (10 entities)
Investment/Wealth Domain (12 entities - NEW)
Risk & Compliance Domain (12 entities)
Treasury Domain (8 entities)
Reference Data (10 entities)
Event/Audit Entities (7 entities)

2. Data Entity/Business Function Matrix:

Customer Management Functions
Banking Services Functions
Wealth Management Functions (NEW)
Risk & Compliance Functions
Operations Functions

3. Application/Data Matrix:

Customer Domain Applications
Account & Transaction Applications
Wealth Applications (NEW)
Risk & Compliance Applications
Treasury Applications
Analytics & ML Applications
Data Platform Applications
Data Ownership Summary
```

```text
Phase C: Data Architecture - Part 3 (Diagrams):
Contents:
1. Conceptual Data Diagram

Enterprise Conceptual Data Model (ASCII visualization)
Domain Relationships Summary (12 relationships defined)
Core Data Domains overview

2. Logical Data Diagram

Customer Domain Logical Model (with full attribute details)
Account & Transaction Domain Logical Model
Investment/Wealth Domain Logical Model (NEW - complete schema)

3. Data Dissemination Diagram

Real-Time Data Flows (Kafka event streaming with latency targets)
Batch Data Flows (Data Lake pipelines with schedules)
Customer 360 Data Aggregation Flow

4. Data Security Diagram

4-Layer Security Architecture (Perimeter, Access Control, Data Protection, Monitoring)
Data Classification & Controls (6 levels from PII-Critical to Public)
Access Control Matrix
Encryption Standards

5. Data Migration Diagram

Migration Strategy (3 phases over 15 months)
Migration Workflow (Extract → Transform → Validate → Load → Verify)
Detailed Migration Schedule by domain
Rollback Strategy

6. Data Lifecycle Diagram

5 Lifecycle Stages (Create, Store, Use, Archive, Destroy)
Retention Policies by data category
Storage Tiers (Active → Historical → Archive)
GDPR Data Subject Rights implementation


```