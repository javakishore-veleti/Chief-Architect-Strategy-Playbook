# KVBank

## Phase D: Technology Architecture

### Part 2: Catalogs and Matrices

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Phase D: Technology Architecture - Part 2 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Technology Standards Catalog
2. Technology Portfolio Catalog
3. Application/Technology Matrix

---

# 1. Technology Standards Catalog

## 1.1 Compute Standards

| Standard ID | Category | Technology | Version | Status | Rationale | Owner |
|-------------|----------|------------|---------|--------|-----------|-------|
| TS-C001 | Container Runtime | containerd | 1.7+ | Mandatory | EKS default, secure | Platform Team |
| TS-C002 | Container Orchestration | Amazon EKS | 1.28+ | Mandatory | Managed Kubernetes | Platform Team |
| TS-C003 | Container Registry | Amazon ECR | Latest | Mandatory | AWS-native, secure | Platform Team |
| TS-C004 | Auto-scaling | Karpenter | 0.32+ | Mandatory | Cost-efficient scaling | Platform Team |
| TS-C005 | Service Mesh | Istio | 1.20+ | Mandatory | mTLS, traffic mgmt | Platform Team |
| TS-C006 | Serverless Compute | AWS Lambda | Latest | Preferred | Event processing | Platform Team |
| TS-C007 | Batch Processing | AWS Batch | Latest | Preferred | Batch workloads | Platform Team |
| TS-C008 | Instance Types | Graviton3 (ARM) | r7g, m7g, c7g | Preferred | Cost/performance | Platform Team |
| TS-C009 | Instance Types | Intel/AMD | r6i, m6i, c6i | Allowed | Compatibility | Platform Team |

## 1.2 Database Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-D001 | Relational DB | Amazon RDS PostgreSQL | 15+ | Mandatory | Transactional data | Data Team |
| TS-D002 | Relational DB | Aurora PostgreSQL | 15+ | Allowed | High throughput | Data Team |
| TS-D003 | In-Memory Cache | Amazon ElastiCache Redis | 7.0+ | Mandatory | Caching, sessions | Data Team |
| TS-D004 | Document Store | Amazon DynamoDB | Latest | Preferred | Key-value, sessions | Data Team |
| TS-D005 | Search Engine | Amazon OpenSearch | 2.11+ | Mandatory | Full-text search | Data Team |
| TS-D006 | Event Store | EventStoreDB | 23.10+ | Mandatory | Event sourcing | Data Team |
| TS-D007 | Time Series | Amazon Timestream | Latest | Preferred | Metrics, IoT | Data Team |
| TS-D008 | Graph Database | Amazon Neptune | Latest | Allowed | Relationship data | Data Team |

## 1.3 Messaging & Streaming Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-M001 | Event Streaming | Amazon MSK (Kafka) | 3.5+ | Mandatory | Event backbone | Platform Team |
| TS-M002 | Schema Registry | Confluent Schema Registry | 7.5+ | Mandatory | Schema management | Platform Team |
| TS-M003 | Message Queue | Amazon SQS | Latest | Preferred | Async messaging | Platform Team |
| TS-M004 | Pub/Sub | Amazon SNS | Latest | Preferred | Notifications | Platform Team |
| TS-M005 | Event Bridge | Amazon EventBridge | Latest | Preferred | Event routing | Platform Team |

## 1.4 Storage Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-S001 | Object Storage | Amazon S3 | Latest | Mandatory | Documents, backups | Platform Team |
| TS-S002 | Block Storage | Amazon EBS gp3 | Latest | Mandatory | Database volumes | Platform Team |
| TS-S003 | File Storage | Amazon EFS | Latest | Preferred | Shared file systems | Platform Team |
| TS-S004 | Archive Storage | S3 Glacier | Latest | Mandatory | Long-term archive | Platform Team |
| TS-S005 | Data Lake Format | Delta Lake | 3.0+ | Mandatory | Analytics storage | Data Team |
| TS-S006 | Data Lake Format | Apache Parquet | Latest | Mandatory | Columnar storage | Data Team |

## 1.5 Network Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-N001 | VPC Design | Hub-Spoke via TGW | N/A | Mandatory | Network isolation | Network Team |
| TS-N002 | Load Balancer | AWS ALB | Latest | Mandatory | HTTP/HTTPS traffic | Network Team |
| TS-N003 | Load Balancer | AWS NLB | Latest | Preferred | TCP/gRPC traffic | Network Team |
| TS-N004 | DNS | Amazon Route 53 | Latest | Mandatory | DNS management | Network Team |
| TS-N005 | CDN | Amazon CloudFront | Latest | Mandatory | Content delivery | Network Team |
| TS-N006 | Private Connectivity | AWS PrivateLink | Latest | Mandatory | VPC endpoints | Network Team |
| TS-N007 | VPN | AWS Site-to-Site VPN | Latest | Preferred | Hybrid connectivity | Network Team |
| TS-N008 | Direct Connect | AWS Direct Connect | Latest | Allowed | Dedicated connectivity | Network Team |

## 1.6 Security Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-SEC001 | Identity | AWS IAM | Latest | Mandatory | AWS access control | Security Team |
| TS-SEC002 | Identity | Keycloak | 23+ | Mandatory | Application identity | Security Team |
| TS-SEC003 | Secrets | HashiCorp Vault | 1.15+ | Mandatory | Secrets management | Security Team |
| TS-SEC004 | Secrets | AWS Secrets Manager | Latest | Mandatory | AWS secrets | Security Team |
| TS-SEC005 | Encryption | AWS KMS | Latest | Mandatory | Key management | Security Team |
| TS-SEC006 | WAF | AWS WAF | Latest | Mandatory | Web protection | Security Team |
| TS-SEC007 | DDoS | AWS Shield Advanced | Latest | Mandatory | DDoS protection | Security Team |
| TS-SEC008 | SIEM | AWS Security Hub | Latest | Mandatory | Security aggregation | Security Team |
| TS-SEC009 | Vulnerability | AWS Inspector | Latest | Mandatory | Vulnerability scan | Security Team |
| TS-SEC010 | Vulnerability | Snyk | Latest | Mandatory | Dependency scan | Security Team |
| TS-SEC011 | Container Security | Trivy | Latest | Mandatory | Image scanning | Security Team |
| TS-SEC012 | Certificate | AWS ACM | Latest | Mandatory | TLS certificates | Security Team |

## 1.7 Observability Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-O001 | APM | Datadog APM | Latest | Mandatory | Application monitoring | SRE Team |
| TS-O002 | Metrics | Datadog Metrics | Latest | Mandatory | Infrastructure metrics | SRE Team |
| TS-O003 | Logging | Datadog Logs | Latest | Mandatory | Centralized logging | SRE Team |
| TS-O004 | Tracing | Datadog APM (traces) | Latest | Mandatory | Distributed tracing | SRE Team |
| TS-O005 | Dashboards | Datadog Dashboards | Latest | Mandatory | Visualization | SRE Team |
| TS-O006 | Alerting | Datadog + PagerDuty | Latest | Mandatory | Incident alerting | SRE Team |
| TS-O007 | Audit Logging | AWS CloudTrail | Latest | Mandatory | API audit | Security Team |
| TS-O008 | Flow Logs | VPC Flow Logs | Latest | Mandatory | Network audit | Security Team |

## 1.8 DevOps Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-DO001 | Source Control | GitHub Enterprise | Latest | Mandatory | Code repository | DevOps Team |
| TS-DO002 | CI/CD | GitHub Actions | Latest | Mandatory | Build & test | DevOps Team |
| TS-DO003 | GitOps | ArgoCD | 2.9+ | Mandatory | Kubernetes deploy | DevOps Team |
| TS-DO004 | IaC | Terraform | 1.6+ | Mandatory | Infrastructure | DevOps Team |
| TS-DO005 | IaC State | Terraform Cloud | Latest | Mandatory | State management | DevOps Team |
| TS-DO006 | Configuration | Ansible | 2.15+ | Preferred | Config management | DevOps Team |
| TS-DO007 | Code Quality | SonarQube | 10+ | Mandatory | Code analysis | DevOps Team |
| TS-DO008 | Artifact Registry | GitHub Packages | Latest | Mandatory | Package storage | DevOps Team |
| TS-DO009 | Feature Flags | LaunchDarkly | Latest | Mandatory | Feature management | DevOps Team |

## 1.9 Development Standards

| Standard ID | Category | Technology | Version | Status | Use Case | Owner |
|-------------|----------|------------|---------|--------|----------|-------|
| TS-DEV001 | Backend Language | Java | 17+ (LTS) | Mandatory | Domain services | Engineering |
| TS-DEV002 | Backend Framework | Spring Boot | 3.2+ | Mandatory | Java services | Engineering |
| TS-DEV003 | Backend Language | Python | 3.11+ | Preferred | ML, scripting | Engineering |
| TS-DEV004 | Backend Language | Go | 1.21+ | Preferred | High-performance | Engineering |
| TS-DEV005 | Backend Language | Node.js | 20+ (LTS) | Mandatory | BFF services | Engineering |
| TS-DEV006 | Frontend Framework | React | 18+ | Mandatory | Web applications | Engineering |
| TS-DEV007 | Mobile iOS | Swift | 5.9+ | Mandatory | iOS apps | Mobile Team |
| TS-DEV008 | Mobile Android | Kotlin | 1.9+ | Mandatory | Android apps | Mobile Team |
| TS-DEV009 | API Specification | OpenAPI | 3.1 | Mandatory | REST APIs | Engineering |
| TS-DEV010 | API Specification | AsyncAPI | 3.0 | Mandatory | Event APIs | Engineering |
| TS-DEV011 | API Query | GraphQL | Latest | Mandatory | BFF APIs | Engineering |
| TS-DEV012 | RPC | gRPC | Latest | Mandatory | Service-to-service | Engineering |

## 1.10 Compliance Standards

| Standard ID | Category | Standard | Status | Scope | Owner |
|-------------|----------|----------|--------|-------|-------|
| TS-CMP001 | Security | ISO 27001 | Mandatory | All systems | CISO |
| TS-CMP002 | Security | SOC 2 Type II | Mandatory | All systems | CISO |
| TS-CMP003 | Payment | PCI DSS 4.0 | Mandatory | Card processing | CISO |
| TS-CMP004 | Privacy | GDPR | Mandatory | All PII systems | DPO |
| TS-CMP005 | Banking | PSD2/Open Banking | Mandatory | Payment systems | Compliance |
| TS-CMP006 | Financial | FCA regulations | Mandatory | All systems | Compliance |
| TS-CMP007 | Cloud | AWS Well-Architected | Mandatory | All infrastructure | Platform Team |

---

# 2. Technology Portfolio Catalog

## 2.1 Compute Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-C001 | EKS Production | EKS Cluster | Production | eu-west-1 | 1.28, managed nodes | €15,000 | Platform |
| TR-C002 | EKS Staging | EKS Cluster | Staging | eu-west-1 | 1.28, managed nodes | €5,000 | Platform |
| TR-C003 | EKS Dev | EKS Cluster | Development | eu-west-1 | 1.28, managed nodes | €3,000 | Platform |
| TR-C004 | EKS DR | EKS Cluster | DR | eu-west-2 | 1.28, warm standby | €4,000 | Platform |
| TR-C005 | Node Group Prod-1 | EC2 Node Group | Production | eu-west-1a | r7g.xlarge x 5 | Included | Platform |
| TR-C006 | Node Group Prod-2 | EC2 Node Group | Production | eu-west-1b | r7g.xlarge x 5 | Included | Platform |
| TR-C007 | Node Group Prod-3 | EC2 Node Group | Production | eu-west-1c | r7g.xlarge x 5 | Included | Platform |
| TR-C008 | Spot Node Group | EC2 Node Group | Production | eu-west-1 | Mixed Spot | Included | Platform |
| TR-C009 | Lambda Functions | Lambda | Production | eu-west-1 | Various | €2,000 | Platform |
| TR-C010 | Batch Compute | AWS Batch | Production | eu-west-1 | Spot instances | €1,500 | Platform |

## 2.2 Database Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-D001 | Customer DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.xlarge, Multi-AZ | €3,500 | Data |
| TR-D002 | Account DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.xlarge, Multi-AZ | €3,500 | Data |
| TR-D003 | Payment DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.2xlarge, Multi-AZ | €5,000 | Data |
| TR-D004 | Card DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.xlarge, Multi-AZ | €3,500 | Data |
| TR-D005 | Wealth DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.xlarge, Multi-AZ | €3,500 | Data |
| TR-D006 | Risk DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.xlarge, Multi-AZ | €3,500 | Data |
| TR-D007 | Treasury DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.large, Multi-AZ | €2,500 | Data |
| TR-D008 | IAM DB | RDS PostgreSQL | Production | eu-west-1 | db.r6g.large, Multi-AZ | €2,500 | Data |
| TR-D009 | Redis Cluster | ElastiCache | Production | eu-west-1 | r6g.xlarge, 6 nodes | €4,000 | Data |
| TR-D010 | OpenSearch | OpenSearch | Production | eu-west-1 | r6g.large.search x 3 | €3,000 | Data |
| TR-D011 | EventStoreDB | EKS Deployment | Production | eu-west-1 | 3-node cluster | €2,000 | Data |
| TR-D012 | DynamoDB | DynamoDB | Production | eu-west-1 | On-demand | €1,500 | Data |

## 2.3 Messaging Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-M001 | MSK Kafka Prod | Amazon MSK | Production | eu-west-1 | kafka.m5.large x 3 | €5,000 | Platform |
| TR-M002 | MSK Kafka Staging | Amazon MSK | Staging | eu-west-1 | kafka.t3.small x 3 | €1,500 | Platform |
| TR-M003 | Schema Registry | EKS Deployment | Production | eu-west-1 | 3 replicas | €500 | Platform |
| TR-M004 | SQS Queues | Amazon SQS | Production | eu-west-1 | Various queues | €500 | Platform |
| TR-M005 | SNS Topics | Amazon SNS | Production | eu-west-1 | Various topics | €300 | Platform |

## 2.4 Network Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-N001 | Production VPC | VPC | Production | eu-west-1 | 10.0.0.0/16 | €0 | Network |
| TR-N002 | Staging VPC | VPC | Staging | eu-west-1 | 10.1.0.0/16 | €0 | Network |
| TR-N003 | Dev VPC | VPC | Development | eu-west-1 | 10.2.0.0/16 | €0 | Network |
| TR-N004 | Shared Services VPC | VPC | Shared | eu-west-1 | 10.3.0.0/16 | €0 | Network |
| TR-N005 | DR VPC | VPC | DR | eu-west-2 | 10.10.0.0/16 | €0 | Network |
| TR-N006 | Transit Gateway | TGW | All | eu-west-1 | Hub connectivity | €500 | Network |
| TR-N007 | ALB Production | ALB | Production | eu-west-1 | Multi-AZ | €1,500 | Network |
| TR-N008 | NLB Internal | NLB | Production | eu-west-1 | Multi-AZ | €500 | Network |
| TR-N009 | CloudFront Dist | CloudFront | Production | Global | All edge locations | €3,000 | Network |
| TR-N010 | NAT Gateways | NAT Gateway | Production | eu-west-1 | 3 AZs | €1,000 | Network |
| TR-N011 | Route 53 Zones | Route 53 | Production | Global | Public + Private | €100 | Network |

## 2.5 Security Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-SEC001 | WAF Web ACL | AWS WAF | Production | Global | OWASP + Custom rules | €1,000 | Security |
| TR-SEC002 | Shield Advanced | AWS Shield | Production | Global | DDoS protection | €3,000 | Security |
| TR-SEC003 | KMS Keys | AWS KMS | Production | eu-west-1 | CMK per service | €500 | Security |
| TR-SEC004 | Secrets Manager | Secrets Manager | Production | eu-west-1 | All secrets | €300 | Security |
| TR-SEC005 | Vault Cluster | HashiCorp Vault | Production | eu-west-1 | 3-node HA | €2,000 | Security |
| TR-SEC006 | Security Hub | Security Hub | Production | eu-west-1 | All standards | €500 | Security |
| TR-SEC007 | GuardDuty | GuardDuty | Production | eu-west-1 | All features | €800 | Security |
| TR-SEC008 | Inspector | AWS Inspector | Production | eu-west-1 | Continuous scan | €400 | Security |
| TR-SEC009 | Macie | Amazon Macie | Production | eu-west-1 | S3 scanning | €300 | Security |
| TR-SEC010 | ACM Certificates | AWS ACM | Production | Global | All domains | €0 | Security |

## 2.6 Observability Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-O001 | Datadog Platform | Datadog | All | N/A | Enterprise | €12,000 | SRE |
| TR-O002 | CloudWatch | CloudWatch | All | eu-west-1 | Logs, Metrics | €2,000 | SRE |
| TR-O003 | CloudTrail | CloudTrail | All | eu-west-1 | All regions | €500 | Security |
| TR-O004 | VPC Flow Logs | Flow Logs | Production | eu-west-1 | All VPCs | €800 | Security |
| TR-O005 | PagerDuty | PagerDuty | All | N/A | Business plan | €1,500 | SRE |

## 2.7 DevOps Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-DO001 | GitHub Enterprise | GitHub | All | N/A | Enterprise Cloud | €5,000 | DevOps |
| TR-DO002 | Terraform Cloud | Terraform | All | N/A | Business tier | €1,500 | DevOps |
| TR-DO003 | ArgoCD | EKS Deployment | All | eu-west-1 | HA deployment | €0 | DevOps |
| TR-DO004 | SonarQube | EKS Deployment | All | eu-west-1 | Enterprise | €1,000 | DevOps |
| TR-DO005 | LaunchDarkly | LaunchDarkly | All | N/A | Pro plan | €1,000 | DevOps |
| TR-DO006 | Snyk | Snyk | All | N/A | Business plan | €2,000 | Security |

## 2.8 Storage Resources

| Resource ID | Resource Name | Type | Environment | Region | Configuration | Monthly Cost | Owner |
|-------------|---------------|------|-------------|--------|---------------|--------------|-------|
| TR-S001 | Data Lake Bucket | S3 | Production | eu-west-1 | ~50TB, Intelligent Tiering | €1,500 | Data |
| TR-S002 | Application Bucket | S3 | Production | eu-west-1 | ~10TB, Standard | €300 | Platform |
| TR-S003 | Backup Bucket | S3 | Production | eu-west-1 | ~20TB, IA + Glacier | €400 | Platform |
| TR-S004 | Logs Bucket | S3 | Production | eu-west-1 | ~5TB, IA | €100 | SRE |
| TR-S005 | DR Replication | S3 | DR | eu-west-2 | Cross-region replica | €500 | Platform |

## 2.9 Cost Summary by Category

| Category | Monthly Cost | % of Total |
|----------|--------------|------------|
| Compute (EKS, Lambda, Batch) | €30,500 | 31% |
| Database (RDS, Redis, OpenSearch) | €38,500 | 39% |
| Messaging (MSK, SQS, SNS) | €7,800 | 8% |
| Network (ALB, CloudFront, NAT) | €6,600 | 7% |
| Security (WAF, Shield, Vault) | €8,800 | 9% |
| Observability (Datadog, CloudWatch) | €16,800 | 17% |
| DevOps (GitHub, Terraform) | €10,500 | 11% |
| Storage (S3) | €2,800 | 3% |
| **Total (with Reserved Instances)** | **€70,000** | **100%** |

*Note: 30% savings achieved from baseline €100K through rightsizing, Reserved Instances, and Spot usage*

---

# 3. Application/Technology Matrix

## 3.1 Channel Applications

| Application | Compute | Database | Cache | Messaging | Storage | CDN |
|-------------|---------|----------|-------|-----------|---------|-----|
| Mobile App (iOS) | N/A (Client) | N/A | N/A | N/A | N/A | CloudFront |
| Mobile App (Android) | N/A (Client) | N/A | N/A | N/A | N/A | CloudFront |
| Web Application | N/A (Client) | N/A | N/A | N/A | S3 (Static) | CloudFront |
| Partner Portal | N/A (Client) | N/A | N/A | N/A | S3 (Static) | CloudFront |
| Advisor Portal | N/A (Client) | N/A | N/A | N/A | S3 (Static) | CloudFront |
| Admin Console | N/A (Client) | N/A | N/A | N/A | S3 (Static) | CloudFront |

## 3.2 BFF Services

| Application | Compute | Database | Cache | Messaging | Load Balancer | Service Mesh |
|-------------|---------|----------|-------|-----------|---------------|--------------|
| Mobile BFF | EKS (Node.js) | None | Redis | Kafka (consume) | ALB | Istio |
| Web BFF | EKS (Node.js) | None | Redis | Kafka (consume) | ALB | Istio |
| Partner BFF | EKS (Node.js) | None | Redis | Kafka (consume) | ALB | Istio |
| Advisor BFF | EKS (Node.js) | None | Redis | Kafka (consume) | ALB | Istio |
| Admin BFF | EKS (Node.js) | None | Redis | Kafka (consume) | ALB | Istio |

## 3.3 Domain Services

| Application | Compute | Database | Cache | Messaging | Storage | Service Mesh |
|-------------|---------|----------|-------|-----------|---------|--------------|
| Customer Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (docs) | Istio |
| Account Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (statements) | Istio |
| Payment Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (receipts) | Istio |
| Card Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (images) | Istio |
| Wealth Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (reports) | Istio |
| KYC Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (documents) | Istio |
| AML Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (evidence) | Istio |
| Fraud Service | EKS (Python) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (models) | Istio |
| Treasury Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (pub/sub) | S3 (reports) | Istio |
| Notification Service | EKS (Go) | DynamoDB | Redis | Kafka (consume), SNS | S3 (templates) | Istio |
| Document Service | EKS (Java) | DynamoDB | Redis | Kafka (consume) | S3 (all docs) | Istio |
| Pricing Service | EKS (Java) | RDS PostgreSQL | Redis | Kafka (consume) | None | Istio |

## 3.4 Platform Services

| Application | Compute | Database | Cache | Messaging | Storage | Special Tech |
|-------------|---------|----------|-------|-----------|---------|--------------|
| API Gateway | Kong on EKS | RDS PostgreSQL | Redis | None | None | Kong Enterprise |
| IAM Service | Keycloak on EKS | RDS PostgreSQL | Redis | Kafka (audit) | None | Keycloak |
| Event Platform | MSK (Managed) | None | None | MSK Kafka | S3 (archive) | Kafka, Schema Registry |
| Event Store | EventStoreDB on EKS | EventStoreDB | None | None | EBS | EventStoreDB |
| Data Platform | EMR, Spark | Delta Lake | None | Kafka (ingest) | S3 (Data Lake) | Spark, Delta |
| ML Platform | SageMaker | None | None | Kafka (features) | S3 (models) | SageMaker |
| Workflow Engine | Temporal on EKS | RDS PostgreSQL | None | None | S3 (history) | Temporal |
| Search Service | OpenSearch (Managed) | OpenSearch | None | Kafka (index) | None | OpenSearch |
| Cache Service | ElastiCache (Managed) | Redis | Redis | None | None | Redis Cluster |
| Secrets Manager | Vault on EKS | Consul | None | None | S3 (backup) | HashiCorp Vault |

## 3.5 Integration Services

| Application | Compute | Database | Cache | Messaging | External Connection |
|-------------|---------|----------|-------|-----------|---------------------|
| SEPA Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | SEPA Network (ISO 20022) |
| SEPA Instant Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | SEPA Instant (ISO 20022) |
| SWIFT Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | SWIFT Network (MT/MX) |
| FPS Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | Faster Payments (ISO 8583) |
| Card Network Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | Visa/MC (ISO 8583) |
| KYC Provider Gateway | EKS (Java) | DynamoDB | Redis | Kafka | Onfido (REST API) |
| Market Data Gateway | EKS (Java) | DynamoDB | Redis | Kafka | Bloomberg (B-PIPE) |
| Investment Platform Gateway | EKS (Java) | RDS PostgreSQL | Redis | Kafka | Global Advisor (FIX) |

## 3.6 Technology Usage Summary

| Technology | # of Applications Using | Primary Use |
|------------|------------------------|-------------|
| EKS | 30+ | All containerized services |
| RDS PostgreSQL | 12 | Domain service databases |
| ElastiCache Redis | 25+ | Caching, sessions |
| MSK Kafka | 20+ | Event streaming |
| S3 | 15+ | Document storage, data lake |
| Istio | 25+ | Service mesh, mTLS |
| CloudFront | 6 | Static content, CDN |
| DynamoDB | 4 | High-throughput key-value |
| OpenSearch | 5 | Full-text search |
| Lambda | 10+ | Event processing |

## 3.7 Security Technology Matrix

| Application | WAF | Shield | KMS | Vault | mTLS | Auth |
|-------------|-----|--------|-----|-------|------|------|
| Mobile BFF | ✓ | ✓ | ✓ | ✓ | ✓ | JWT |
| Web BFF | ✓ | ✓ | ✓ | ✓ | ✓ | JWT |
| Partner BFF | ✓ | ✓ | ✓ | ✓ | ✓ | OAuth 2.0 |
| Customer Service | - | - | ✓ | ✓ | ✓ | mTLS |
| Payment Service | - | - | ✓ | ✓ | ✓ | mTLS |
| Card Service | - | - | ✓ | ✓ | ✓ | mTLS |
| Wealth Service | - | - | ✓ | ✓ | ✓ | mTLS |
| All Internal Services | - | - | ✓ | ✓ | ✓ | mTLS |

---

# 4. Summary Statistics

## 4.1 Technology Standards Summary

| Category | # of Standards | Mandatory | Preferred | Allowed |
|----------|----------------|-----------|-----------|---------|
| Compute | 9 | 5 | 3 | 1 |
| Database | 8 | 4 | 2 | 2 |
| Messaging | 5 | 2 | 3 | 0 |
| Storage | 6 | 4 | 1 | 1 |
| Network | 8 | 5 | 2 | 1 |
| Security | 12 | 12 | 0 | 0 |
| Observability | 8 | 8 | 0 | 0 |
| DevOps | 9 | 7 | 1 | 1 |
| Development | 12 | 8 | 3 | 1 |
| Compliance | 7 | 7 | 0 | 0 |
| **Total** | **84** | **62** | **15** | **7** |

## 4.2 Technology Portfolio Summary

| Category | # of Resources | Monthly Cost |
|----------|----------------|--------------|
| Compute | 10 | €30,500 |
| Database | 12 | €38,500 |
| Messaging | 5 | €7,800 |
| Network | 11 | €6,600 |
| Security | 10 | €8,800 |
| Observability | 5 | €16,800 |
| DevOps | 6 | €10,500 |
| Storage | 5 | €2,800 |
| **Total** | **64** | **€70,000/month** |

---

**Document End**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Platform Team | CTO |
| [Date] | [Date] | [Date] |
