# Architecture Development - Application Architecture

## Steps for Application Architecture

1. Select reference models, viewpoints and tools
2. Develop baseline application architecture description
3. Develop target application architecture description
4. Perform gap analysis
5. Define candidate roadmap components
6. Define candidate roadmap components
7. Resolve impacts across the architecture landscape
8. Conduct formal stakeholder review
9. Finalize application architecture
10. Create architecture definition document.

## Outputs from Application Architecture

1. Refined Phase A deliverables
2. Draft architecture definition document
    a. Baseline application architecture, approved version
    b. Target application architecture, approved version
3. Draft architecture requirements specfiication - gap analysis
4. Applicatio architecture components of an architecture roadmap

## Artifacts Produced

### Catalogs

1. Application portfolio Catalog
2. Interface Catalog

### Matrices

1. Application/organization matrix
2. Role/Application Matrix
3. Application function matrix
4. Application interaction matrix

### Diagrams

1. Application Communication Diagram
2. Application and User Location Diagram
3. Applicaion Use-Case Diagram
4. Enterprise Manageability Diagram
5. Process/Application Realization Diagram
6. Software Engineering Diagram
7. Application Migration Diagram
8. Software Distribution Diagram


```text
Phase C: Application Architecture is now complete!
All 3 parts delivered:

Part 1: Steps, Outputs, and Core Architecture
Part 2: Catalogs and Matrices
Part 3: Diagrams
```


```text

Phase C: Application Architecture - Part 1 (Steps, Outputs, and Core Architecture):
Contents:

Introduction and Purpose - Objectives, scope, relationship to other phases
Reference Models, Viewpoints and Tools - Microservices, Event-Driven, API-First patterns; Kong, Istio, Kafka, Kubernetes tools
Baseline Application Architecture - Current monolithic landscape, assessment (2-3/5 scores), integration issues
Target Application Architecture - 7 principles, 10 domain services, 8 platform services, full architecture diagram
Gap Analysis - 9 capability gaps identified (Microservices, API Gateway, Event Platform, Wealth Service all Critical/P1)
Candidate Roadmap Components - 12 work packages (AA-01 to AA-12), €22M over 24 months
Architecture Definition Document - Components and 6 architecture decisions
Requirements Specification - 8 functional + 8 non-functional requirements

```

```text
Phase C: Application Architecture - Part 2 (Catalogs and Matrices):
Contents:
1. Application Portfolio Catalog (42 applications total)

1.1 Channel Applications (7): Mobile iOS/Android, Web, Partner Portal, Advisor Portal, Admin Console, Ops Dashboard
1.2 BFF Services (5): Mobile BFF, Web BFF, Partner BFF, Advisor BFF, Admin BFF
1.3 Domain Services (12): Customer, Account, Payment, Card, Wealth (NEW), KYC, AML, Fraud, Treasury, Notification, Document, Pricing
1.4 Platform Services (10): API Gateway, IAM, Event Platform, Data Platform, ML Platform, Workflow Engine, Search, Cache, Secrets, Config
1.5 Integration Services (8): SEPA, SEPA Instant, SWIFT, FPS, Card Networks, Onfido, Bloomberg, Global Advisor
1.6 Legacy Applications (4 to retire)

2. Interface Catalog (41 interfaces)

External Partner APIs (6)
Channel APIs (4)
Internal Service APIs (12)
Event Interfaces/Kafka Topics (10)
External System Interfaces (9)

3. Application/Organization Matrix

Channel Apps by Organization
Domain Services by Organization
Platform Services by Organization

4. Role/Application Matrix

Customer-Facing Roles
Internal Operational Roles
Wealth Management Roles
Technical Roles

5. Application Function Matrix

Customer Management Functions
Banking Functions
Wealth Management Functions
Risk & Compliance Functions
Platform Functions

6. Application Interaction Matrix

Synchronous Interactions (API Calls)
Asynchronous Interactions (Events)
External Integration Summary
```


```text

 Phase C: Application Architecture - Part 3 (Diagrams):
Contents:
1. Application Communication Diagram

High-level communication architecture (ASCII visualization)
Communication protocols by layer (HTTPS, HTTP/2, gRPC, Kafka)
Communication patterns (Request/Response, Pub/Sub, Event Sourcing, CQRS, Saga, Circuit Breaker)

2. Application and User Location Diagram

Geographic distribution (EU-West-1 Primary, EU-West-2 DR)
CDN edge locations across Europe
User location matrix with latency targets
Data residency compliance (GDPR)

3. Application Use-Case Diagram

Retail Customer use cases (Account, Payment, Card)
Wealth Client use cases (Portfolio, Trading, Advisory)
Business Customer use cases (Team, Bulk Payments, Reporting)
Internal User use cases (CS Agent, Advisor, Fraud Analyst, AML, SRE)

4. Enterprise Manageability Diagram

Observability stack (Datadog: Metrics, Logs, Traces, APM)
Alerting & response (PagerDuty, Slack, JIRA, Runbooks)
Dashboards (Executive, Operations, Technical)
SLA management and incident management matrix

5. Process/Application Realization Diagram

Customer onboarding process flow
Payment processing realization
Process to application mapping with orchestration (Temporal)

6. Software Engineering Diagram

CI/CD pipeline (GitHub Actions → ArgoCD)
Development standards and quality gates
Environment matrix (Dev → Staging → UAT → Prod)

7. Application Migration Diagram

Strangler Fig pattern strategy
3-phase migration (Foundation → Core → Complete)
Migration schedule and risks/mitigations

8. Software Distribution Diagram

Artifact repositories (GitHub, ECR, NPM, Maven)
Container image strategy
Deployment configuration (replicas, resources)
Release strategy (Blue-Green, Canary, Feature Flags)


Phase C: Application Architecture is now complete!
All 3 parts delivered:

Part 1: Steps, Outputs, and Core Architecture
Part 2: Catalogs and Matrices
Part 3: Diagrams


```