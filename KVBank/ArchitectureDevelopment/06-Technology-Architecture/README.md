# Architecture Development - Technology Architecture

## Steps for Technology Architecture

1. Select reference models, viewpoints and tools
2. Develop baseline technology architecture description
3. Develop target technology architecture description
4. Perform gap analysis
5. Define candidate roadmap components
6. Resolve impacts across the architecture landscape
7. Conduct formal stakeholder review
8. Finalize technology architecture
9. Create architecture definition document

## Output of Technology Architecture

1. Refined Phase A deliverables
2. Draft Architecture Definition Document
    a. Baseline technology architecture, approved section
    b. Target technology architecture, approved version
3. Draft architecture requirements specification - gap analysis
4. Technology architecture components of an architecture roadmap

## Artifacts

### Catalogs
1. Technology Standards Catalog
2. Technology portfolio Catalog

### Matrices

1. Application / Technology Matrix

### Diagrams

1. Environment and Locations diagram
2. Platform Decomposition diagram
3. Processing diagram
4. Networked Computing/Hardware diagram
5. Communications Engineering diagram

```text
Phase D: Technology Architecture is now complete!
All 3 parts delivered:

Part 1: Steps, Outputs, and Core Architecture
Part 2: Catalogs and Matrices (Technology Standards, Technology Portfolio, Application/Technology Matrix)
Part 3: Diagrams (Environment & Locations, Platform Decomposition, Processing, Hardware/Network, Communications)
```

```text
 Phase D: Technology Architecture - Part 1 (Steps, Outputs, and Core Architecture):
Contents:

Introduction and Purpose - Objectives (infrastructure, security, scalability, resilience, cost), scope, relationship to other phases
Reference Models and Tools - AWS Well-Architected, Cloud Security Alliance, NIST, ISO 27001, PCI DSS frameworks; Terraform, EKS, Istio, ArgoCD, Datadog tools
Baseline Technology Architecture - Current state assessment (EC2, single RDS, no caching/messaging, single VPC), scores (1-2/5 across all dimensions), €100K/month cost with 30% optimization potential
Target Technology Architecture - 7 principles (Cloud-Native, IaC, Immutable, Zero Trust, Multi-AZ, Cost Opt, Observable), compute platform (EKS, Karpenter, Lambda), data platform (RDS Multi-AZ, Redis, MSK Kafka, OpenSearch, S3), security infrastructure (IAM, Vault, KMS, WAF, Shield, Security Hub), HA design (RTO/RPO targets)
Gap Analysis - 10 infrastructure capability gaps, 7 security gaps
Candidate Roadmap Components - 10 work packages (TA-01 to TA-10), €7M over 12 months across 3 phases (Foundation, Platform, Resilience)
Architecture Definition Document - 8 architecture decisions (ADR-T001 to ADR-T008)
Requirements Specification - 8 functional + 8 non-functional requirements (99.99% availability, <2min failover, <1hr RTO)
```


```text
Phase D: Technology Architecture - Part 3 (Diagrams):
Contents:
1. Environment and Locations Diagram

Global infrastructure overview (ASCII visualization)
CloudFront CDN with 9+ European edge locations
Primary Region: EU-West-1 (Ireland) with Production, Staging, Dev, Shared Services VPCs
DR Region: EU-West-2 (London) with warm standby
Availability Zone distribution (3 AZs with full redundancy)
Data center and connectivity details

2. Platform Decomposition Diagram

Full platform architecture (ASCII visualization)
9 tiers: Presentation → Edge/Security → API → BFF → Service Mesh → Domain Services → Platform Services → Data → Integration
Component details with technologies and scaling strategies

3. Processing Diagram

Synchronous request flow (Mobile → CDN → WAF → ALB → Kong → Istio → BFF → Services → DB)
Latency targets per layer (Total E2E: < 200ms P95)
Asynchronous event processing (Kafka with producers, topics, consumers)
Batch processing architecture (Airflow → AWS Batch/Spark/SageMaker → Data Lake)
Processing summary: 10K TPS sync, 100K msg/s async, 1TB/hr batch

4. Networked Computing/Hardware Diagram

Network topology (Edge → Transit Gateway Hub → VPC Spokes)
Production VPC detail (Public subnets, Private compute subnets, Private data subnets)
Hardware specifications (EKS nodes, RDS, MSK, Redis, OpenSearch)
Network bandwidth matrix (100+ Gbps at edge down to 10 Gbps cross-region)

5. Communications Engineering Diagram

Protocol stack (Application L7: GraphQL, REST, gRPC, WebSocket, Kafka)
Transport layer (TLS 1.3, TCP/HTTP/2)
Service mesh layer (Istio: mTLS, traffic management, circuit breaker, retry, timeout)
External payment networks (SEPA, SWIFT, FPS, Visa/MC with protocols and security)
Third-party services (Onfido, Bloomberg, Twilio, Salesforce)
Communication security matrix
Resilience patterns (Circuit breaker, retry, timeout, rate limiting, bulkhead, fallback)

6. Summary

Infrastructure summary: 2 regions, 5 VPCs, 3 AZs, 4 EKS clusters, ~35 nodes, 16 DB instances
Resilience summary: 99.99% availability, <1hr RTO, <1min RPO
```

