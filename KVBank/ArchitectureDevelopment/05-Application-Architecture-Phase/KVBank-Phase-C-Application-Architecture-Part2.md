# KVBank

## Phase C: Application Architecture

### Part 2: Catalogs and Matrices

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Phase C: Application Architecture - Part 2 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Application Portfolio Catalog
2. Interface Catalog
3. Application/Organization Matrix
4. Role/Application Matrix
5. Application Function Matrix
6. Application Interaction Matrix

---

# 1. Application Portfolio Catalog

## 1.1 Channel Applications

| App ID | Application Name | Description | Technology | Owner | Status | Users |
|--------|------------------|-------------|------------|-------|--------|-------|
| APP-C01 | Mobile App (iOS) | Customer banking app for iOS | Swift/SwiftUI | Head of Mobile | Target | 600K |
| APP-C02 | Mobile App (Android) | Customer banking app for Android | Kotlin/Compose | Head of Mobile | Target | 400K |
| APP-C03 | Web Application | Customer banking web portal | React/Next.js | Head of Web | Target | 200K |
| APP-C04 | Partner Portal | Partner API management & docs | React | Head of Partnerships | Target | 500 |
| APP-C05 | Advisor Portal | Wealth advisory workstation | React | Head of Wealth | Target | 200 |
| APP-C06 | Admin Console | Internal operations management | React | Head of Operations | Target | 500 |
| APP-C07 | Ops Dashboard | Real-time operational monitoring | React/Grafana | CTO | Target | 100 |

## 1.2 Backend-for-Frontend (BFF) Services

| App ID | Application Name | Description | Technology | Owner | Status | Consumers |
|--------|------------------|-------------|------------|-------|--------|-----------|
| APP-B01 | Mobile BFF | Mobile-optimized API aggregation | Node.js/GraphQL | Head of Mobile | Target | APP-C01, APP-C02 |
| APP-B02 | Web BFF | Web-optimized API aggregation | Node.js/GraphQL | Head of Web | Target | APP-C03 |
| APP-B03 | Partner BFF | Partner API with rate limits | Node.js/REST | Head of Partnerships | Target | APP-C04, Partners |
| APP-B04 | Advisor BFF | Advisor-specific workflows | Node.js/GraphQL | Head of Wealth | Target | APP-C05 |
| APP-B05 | Admin BFF | Admin operations API | Node.js/REST | Head of Operations | Target | APP-C06 |

## 1.3 Domain Services

| App ID | Application Name | Description | Technology | Owner | Status | Domain |
|--------|------------------|-------------|------------|-------|--------|--------|
| APP-D01 | Customer Service | Customer profile & preferences | Java 17/Spring | Head of Retail | Target | Customer |
| APP-D02 | Account Service | Account management & balances | Java 17/Spring | Head of Operations | Target | Account |
| APP-D03 | Payment Service | Payment processing & transfers | Java 17/Spring | Head of Payments | Target | Payment |
| APP-D04 | Card Service | Card lifecycle & transactions | Java 17/Spring | Head of Cards | Target | Card |
| APP-D05 | Wealth Service | Investment & advisory (NEW) | Java 17/Spring | Head of Wealth | Target | Wealth |
| APP-D06 | KYC Service | Identity verification | Java 17/Spring | Head of Compliance | Target | Compliance |
| APP-D07 | AML Service | Transaction monitoring | Java 17/Spring | MLRO | Target | Compliance |
| APP-D08 | Fraud Service | Real-time fraud detection | Python/FastAPI | Head of Fraud | Target | Risk |
| APP-D09 | Treasury Service | FX & liquidity management | Java 17/Spring | Head of Treasury | Target | Treasury |
| APP-D10 | Notification Service | Multi-channel notifications | Go | CTO | Target | Platform |
| APP-D11 | Document Service | Document generation & storage | Java 17/Spring | Head of Operations | Target | Platform |
| APP-D12 | Pricing Service | Product pricing & fees | Java 17/Spring | Head of Product | Target | Platform |

## 1.4 Platform Services

| App ID | Application Name | Description | Technology | Owner | Status | Consumers |
|--------|------------------|-------------|------------|-------|--------|-----------|
| APP-P01 | API Gateway | API management & security | Kong Enterprise | CTO | Target | All channels |
| APP-P02 | IAM Service | Authentication & authorization | Keycloak + Custom | CISO | Target | All services |
| APP-P03 | Event Platform | Event streaming & sourcing | Kafka + EventStoreDB | CTO | Target | All services |
| APP-P04 | Data Platform | Analytics & ML features | Spark + Delta Lake | CDO | Target | Analytics |
| APP-P05 | ML Platform | Model training & serving | SageMaker | CTO | Target | Fraud, Personalization |
| APP-P06 | Workflow Engine | Business process orchestration | Temporal | CTO | Target | Complex processes |
| APP-P07 | Search Service | Full-text search | Elasticsearch | CTO | Target | Search features |
| APP-P08 | Cache Service | Distributed caching | Redis Cluster | CTO | Target | All services |
| APP-P09 | Secrets Manager | Secrets & key management | HashiCorp Vault | CISO | Target | All services |
| APP-P10 | Config Service | Centralized configuration | Spring Cloud Config | CTO | Target | All services |

## 1.5 Integration Services

| App ID | Application Name | Description | Technology | Owner | Status | External System |
|--------|------------------|-------------|------------|-------|--------|-----------------|
| APP-I01 | SEPA Gateway | SEPA payments integration | Java/Spring | Head of Payments | Target | SEPA Network |
| APP-I02 | SEPA Instant Gateway | SEPA Instant payments | Java/Spring | Head of Payments | Target | SEPA Instant |
| APP-I03 | SWIFT Gateway | International payments | Java/Spring | Head of Payments | Target | SWIFT Network |
| APP-I04 | FPS Gateway | UK Faster Payments | Java/Spring | Head of Payments | Target | Faster Payments |
| APP-I05 | Card Network Gateway | Visa/Mastercard integration | Java/Spring | Head of Cards | Target | Visa/Mastercard |
| APP-I06 | KYC Provider Gateway | Identity verification | Java/Spring | Head of Compliance | Target | Onfido |
| APP-I07 | Market Data Gateway | Market data feeds | Java/Spring | Head of Treasury | Target | Bloomberg |
| APP-I08 | Investment Platform Gateway | Trade execution | Java/Spring | Head of Wealth | Target | Global Advisor |

## 1.6 Legacy Applications (To Be Retired)

| App ID | Application Name | Description | Technology | Owner | Retirement Date | Replacement |
|--------|------------------|-------------|------------|-------|-----------------|-------------|
| APP-L01 | Core Banking Monolith | Current core system | Java 8/Spring | CTO | M18 | APP-D01 to APP-D04 |
| APP-L02 | Legacy Admin Portal | Current admin system | PHP | Head of Operations | M12 | APP-C06 |
| APP-L03 | Legacy Risk System | Current risk system | .NET | CRO | M15 | APP-D06, D07, D08 |
| APP-L04 | Legacy Web App | Current web application | Angular 8 | Head of Web | M18 | APP-C03 |

---

# 2. Interface Catalog

## 2.1 External APIs (Partner-Facing)

| Interface ID | Interface Name | Type | Protocol | Provider | Consumers | Auth | Rate Limit |
|--------------|----------------|------|----------|----------|-----------|------|------------|
| API-E01 | Account API | REST | HTTPS | APP-B03 | Partners | OAuth 2.0 | 1000/min |
| API-E02 | Payment API | REST | HTTPS | APP-B03 | Partners | OAuth 2.0 | 500/min |
| API-E03 | Card API | REST | HTTPS | APP-B03 | Partners | OAuth 2.0 | 500/min |
| API-E04 | Customer API | REST | HTTPS | APP-B03 | Partners | OAuth 2.0 | 1000/min |
| API-E05 | Webhook API | REST | HTTPS | APP-B03 | Partners | HMAC | N/A |
| API-E06 | Open Banking API | REST | HTTPS | APP-B03 | TPPs | OAuth 2.0 | 500/min |

## 2.2 Channel APIs (Mobile/Web)

| Interface ID | Interface Name | Type | Protocol | Provider | Consumers | Auth |
|--------------|----------------|------|----------|----------|-----------|------|
| API-C01 | Mobile GraphQL API | GraphQL | HTTPS | APP-B01 | APP-C01, APP-C02 | JWT |
| API-C02 | Web GraphQL API | GraphQL | HTTPS | APP-B02 | APP-C03 | JWT |
| API-C03 | Advisor GraphQL API | GraphQL | HTTPS | APP-B04 | APP-C05 | JWT + MFA |
| API-C04 | Admin REST API | REST | HTTPS | APP-B05 | APP-C06 | JWT + MFA |

## 2.3 Internal Service APIs

| Interface ID | Interface Name | Type | Protocol | Provider | Consumers | Auth |
|--------------|----------------|------|----------|----------|-----------|------|
| API-S01 | Customer Service API | REST | gRPC | APP-D01 | All BFFs, Services | mTLS |
| API-S02 | Account Service API | REST | gRPC | APP-D02 | All BFFs, Services | mTLS |
| API-S03 | Payment Service API | REST | gRPC | APP-D03 | BFFs, Account, Treasury | mTLS |
| API-S04 | Card Service API | REST | gRPC | APP-D04 | BFFs, Account, Fraud | mTLS |
| API-S05 | Wealth Service API | REST | gRPC | APP-D05 | BFFs, Customer, Account | mTLS |
| API-S06 | KYC Service API | REST | gRPC | APP-D06 | Customer, Onboarding | mTLS |
| API-S07 | AML Service API | REST | gRPC | APP-D07 | Payment, Card, Wealth | mTLS |
| API-S08 | Fraud Service API | REST | gRPC | APP-D08 | Payment, Card | mTLS |
| API-S09 | Treasury Service API | REST | gRPC | APP-D09 | Payment, Wealth | mTLS |
| API-S10 | Notification API | REST | gRPC | APP-D10 | All Services | mTLS |
| API-S11 | Document API | REST | gRPC | APP-D11 | All Services | mTLS |
| API-S12 | Pricing API | REST | gRPC | APP-D12 | All BFFs | mTLS |

## 2.4 Event Interfaces (Kafka Topics)

| Interface ID | Topic Name | Type | Publisher | Subscribers | Schema |
|--------------|------------|------|-----------|-------------|--------|
| EVT-01 | customer.events | Event | APP-D01 | D02, D05, D06, P03, P04 | Avro |
| EVT-02 | account.events | Event | APP-D02 | D03, D04, D09, P03, P04 | Avro |
| EVT-03 | payment.events | Event | APP-D03 | D02, D07, D08, D10, P03, P04 | Avro |
| EVT-04 | card.events | Event | APP-D04 | D02, D07, D08, D10, P03, P04 | Avro |
| EVT-05 | wealth.events | Event | APP-D05 | D02, D07, D10, P03, P04 | Avro |
| EVT-06 | kyc.events | Event | APP-D06 | D01, D07, P03, P04 | Avro |
| EVT-07 | aml.events | Event | APP-D07 | D03, D04, D10, P03, P04 | Avro |
| EVT-08 | fraud.events | Event | APP-D08 | D03, D04, D10, P03, P04 | Avro |
| EVT-09 | treasury.events | Event | APP-D09 | D03, D05, P03, P04 | Avro |
| EVT-10 | notification.events | Event | APP-D10 | P03, P04 | Avro |

## 2.5 External System Interfaces

| Interface ID | Interface Name | Type | Protocol | Direction | External System | Owner |
|--------------|----------------|------|----------|-----------|-----------------|-------|
| EXT-01 | SEPA Credit Transfer | File/API | ISO 20022 | Outbound | SEPA Network | Head of Payments |
| EXT-02 | SEPA Instant | API | ISO 20022 | Bidirectional | SEPA Instant | Head of Payments |
| EXT-03 | SWIFT MT/MX | File/API | SWIFT | Bidirectional | SWIFT Network | Head of Payments |
| EXT-04 | FPS | API | ISO 8583 | Bidirectional | UK Faster Payments | Head of Payments |
| EXT-05 | Visa Base II | File | ISO 8583 | Bidirectional | Visa | Head of Cards |
| EXT-06 | Mastercard IPM | File | ISO 8583 | Bidirectional | Mastercard | Head of Cards |
| EXT-07 | Onfido API | REST | HTTPS | Outbound | Onfido | Head of Compliance |
| EXT-08 | Bloomberg B-PIPE | API | Proprietary | Inbound | Bloomberg | Head of Treasury |
| EXT-09 | Global Advisor FIX | FIX | FIX 4.4 | Bidirectional | Global Advisor | Head of Wealth |

---

# 3. Application/Organization Matrix

## 3.1 Channel Applications by Organization

| Application | Retail Banking | Business Banking | Wealth Mgmt | Engineering | Operations | Risk | Compliance |
|-------------|----------------|------------------|-------------|-------------|------------|------|------------|
| APP-C01 Mobile (iOS) | ●●● | ●●○ | ●●○ | ●○○ | ○ | ○ | ○ |
| APP-C02 Mobile (Android) | ●●● | ●●○ | ●●○ | ●○○ | ○ | ○ | ○ |
| APP-C03 Web Application | ●●● | ●●● | ●●○ | ●○○ | ○ | ○ | ○ |
| APP-C04 Partner Portal | ○ | ●●○ | ○ | ●●● | ○ | ○ | ○ |
| APP-C05 Advisor Portal | ○ | ○ | ●●● | ●○○ | ○ | ○ | ○ |
| APP-C06 Admin Console | ●○○ | ●○○ | ●○○ | ●●○ | ●●● | ●●○ | ●●○ |
| APP-C07 Ops Dashboard | ○ | ○ | ○ | ●●● | ●●● | ●●○ | ●○○ |

**Legend:** ●●● = Primary User | ●●○ = Regular User | ●○○ = Occasional User | ○ = No Access

## 3.2 Domain Services by Organization

| Application | Retail Banking | Business Banking | Wealth Mgmt | Engineering | Operations | Risk | Compliance |
|-------------|----------------|------------------|-------------|-------------|------------|------|------------|
| APP-D01 Customer Service | ●●● | ●●● | ●●○ | ○ | ●○○ | ○ | ●○○ |
| APP-D02 Account Service | ●●● | ●●● | ●●○ | ○ | ●●● | ○ | ○ |
| APP-D03 Payment Service | ●●● | ●●● | ●○○ | ○ | ●●● | ●○○ | ○ |
| APP-D04 Card Service | ●●● | ●●○ | ○ | ○ | ●●○ | ●○○ | ○ |
| APP-D05 Wealth Service | ○ | ○ | ●●● | ○ | ●○○ | ●○○ | ●○○ |
| APP-D06 KYC Service | ●●○ | ●●○ | ●●○ | ○ | ●○○ | ○ | ●●● |
| APP-D07 AML Service | ○ | ○ | ○ | ○ | ●○○ | ●●● | ●●● |
| APP-D08 Fraud Service | ○ | ○ | ○ | ○ | ●○○ | ●●● | ○ |
| APP-D09 Treasury Service | ○ | ○ | ●○○ | ○ | ●●● | ○ | ○ |
| APP-D10 Notification Service | ●●○ | ●●○ | ●●○ | ●●● | ●●○ | ●○○ | ●○○ |

## 3.3 Platform Services by Organization

| Application | Engineering | Operations | Security | Data/Analytics |
|-------------|-------------|------------|----------|----------------|
| APP-P01 API Gateway | ●●● | ●●○ | ●●● | ○ |
| APP-P02 IAM Service | ●●○ | ●○○ | ●●● | ○ |
| APP-P03 Event Platform | ●●● | ●●○ | ●○○ | ●●● |
| APP-P04 Data Platform | ●●○ | ●○○ | ●○○ | ●●● |
| APP-P05 ML Platform | ●●● | ○ | ○ | ●●● |
| APP-P06 Workflow Engine | ●●● | ●●○ | ○ | ○ |
| APP-P07 Search Service | ●●● | ●○○ | ○ | ●○○ |
| APP-P08 Cache Service | ●●● | ●○○ | ○ | ○ |
| APP-P09 Secrets Manager | ●●○ | ●○○ | ●●● | ○ |

---

# 4. Role/Application Matrix

## 4.1 Customer-Facing Roles

| Role | Mobile App | Web App | Partner Portal | Description |
|------|------------|---------|----------------|-------------|
| Retail Customer | Full Access | Full Access | - | View accounts, payments, cards |
| Business Customer | Full Access | Full Access | - | + Team management, bulk payments |
| Wealth Client | Full Access | Full Access | - | + Investments, advisory |
| Business Admin | Limited | Full Access | - | Manage business users |
| Partner Developer | - | - | Full Access | API integration, testing |

## 4.2 Internal Operational Roles

| Role | Admin Console | Ops Dashboard | Advisor Portal | Customer Service | Description |
|------|---------------|---------------|----------------|------------------|-------------|
| CS Agent | Full Access | View Only | - | Full | Handle customer queries |
| CS Supervisor | Full Access | Full Access | - | Full | Manage CS team |
| Operations Analyst | Full Access | Full Access | - | View | Monitor operations |
| Operations Manager | Full Access | Full Access | - | Full | Manage ops team |
| Fraud Analyst | Limited | Full Access | - | View | Investigate fraud |
| AML Analyst | Limited | Full Access | - | View | Investigate AML |
| Compliance Officer | Full Access | Full Access | - | View | Compliance monitoring |

## 4.3 Wealth Management Roles

| Role | Advisor Portal | Admin Console | Mobile App | Description |
|------|----------------|---------------|------------|-------------|
| Investment Advisor | Full Access | View Only | Limited | Client advisory |
| Senior Advisor | Full Access | Full Access | Limited | + Approval authority |
| Wealth Operations | Limited | Full Access | - | Back-office support |
| Portfolio Manager | Full Access | View Only | - | Portfolio management |

## 4.4 Technical Roles

| Role | Ops Dashboard | Admin Console | All Services | Description |
|------|---------------|---------------|--------------|-------------|
| Developer | Full Access | Limited | Debug Access | Development, debugging |
| SRE Engineer | Full Access | Full Access | Full Access | Reliability, incidents |
| DevOps Engineer | Full Access | Full Access | Deploy Access | CI/CD, deployments |
| Security Engineer | Full Access | Full Access | Audit Access | Security monitoring |
| Data Engineer | Full Access | Limited | Data Access | Data pipelines |
| Architect | Full Access | Full Access | Design Access | Architecture decisions |

---

# 5. Application Function Matrix

## 5.1 Customer Management Functions

| Function | Customer Svc | Account Svc | KYC Svc | Notification | Mobile App | Web App |
|----------|--------------|-------------|---------|--------------|------------|---------|
| Create Customer | ●●● | ○ | ●●○ | ●○○ | ●●○ | ●●○ |
| Update Profile | ●●● | ○ | ○ | ●○○ | ●●○ | ●●○ |
| Verify Identity | ●○○ | ○ | ●●● | ●○○ | ●●○ | ●●○ |
| Manage Preferences | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |
| View Customer 360 | ●●● | ●○○ | ●○○ | ○ | ●○○ | ●○○ |
| Segment Customer | ●●● | ○ | ○ | ○ | ○ | ○ |
| Manage Consent | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |

**Legend:** ●●● = Primary | ●●○ = Secondary | ●○○ = Supporting | ○ = Not Involved

## 5.2 Banking Functions

| Function | Account Svc | Payment Svc | Card Svc | Treasury Svc | Mobile App | Web App |
|----------|-------------|-------------|----------|--------------|------------|---------|
| Open Account | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |
| View Balance | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |
| View Statement | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |
| Make Payment | ○ | ●●● | ○ | ●○○ | ●●○ | ●●○ |
| Make Transfer | ○ | ●●● | ○ | ○ | ●●○ | ●●○ |
| FX Conversion | ○ | ●●● | ○ | ●●● | ●●○ | ●●○ |
| Issue Card | ○ | ○ | ●●● | ○ | ●●○ | ●●○ |
| Freeze Card | ○ | ○ | ●●● | ○ | ●●○ | ●●○ |
| Set Card Limits | ○ | ○ | ●●● | ○ | ●●○ | ●●○ |
| View Card Txns | ○ | ○ | ●●● | ○ | ●●○ | ●●○ |

## 5.3 Wealth Management Functions

| Function | Wealth Svc | Account Svc | Treasury Svc | Advisor Portal | Mobile App | Web App |
|----------|------------|-------------|--------------|----------------|------------|---------|
| Open Investment Acc | ●●● | ●○○ | ○ | ●●○ | ●●○ | ●●○ |
| Create Portfolio | ●●● | ○ | ○ | ●●○ | ●○○ | ●○○ |
| Execute Trade | ●●● | ●○○ | ●○○ | ●●○ | ●●○ | ●●○ |
| View Positions | ●●● | ○ | ○ | ●●○ | ●●○ | ●●○ |
| Portfolio Valuation | ●●● | ○ | ●○○ | ●●○ | ●●○ | ●●○ |
| Risk Assessment | ●●● | ○ | ○ | ●●● | ●●○ | ●●○ |
| Investment Advice | ●●● | ○ | ○ | ●●● | ●○○ | ●○○ |
| Robo-Advisory | ●●● | ○ | ○ | ○ | ●●○ | ●●○ |
| Performance Report | ●●● | ○ | ○ | ●●○ | ●●○ | ●●○ |

## 5.4 Risk & Compliance Functions

| Function | KYC Svc | AML Svc | Fraud Svc | Customer Svc | Admin Console |
|----------|---------|---------|-----------|--------------|---------------|
| KYC Verification | ●●● | ○ | ○ | ●○○ | ●○○ |
| Document Check | ●●● | ○ | ○ | ○ | ●○○ |
| Sanctions Screening | ●●○ | ●●● | ○ | ○ | ●○○ |
| PEP Check | ●●○ | ●●● | ○ | ○ | ●○○ |
| Transaction Monitor | ○ | ●●● | ●●○ | ○ | ●○○ |
| Generate AML Alert | ○ | ●●● | ○ | ○ | ●●○ |
| Investigate Case | ○ | ●●● | ●●○ | ○ | ●●● |
| File SAR | ○ | ●●● | ○ | ○ | ●●○ |
| Fraud Detection | ○ | ○ | ●●● | ○ | ●○○ |
| Fraud Investigation | ○ | ○ | ●●● | ○ | ●●● |
| Block Transaction | ○ | ●●○ | ●●● | ○ | ●●○ |

## 5.5 Platform Functions

| Function | API Gateway | IAM Svc | Event Platform | Notification | Workflow |
|----------|-------------|---------|----------------|--------------|----------|
| Authenticate User | ●●○ | ●●● | ○ | ○ | ○ |
| Authorize Request | ●●● | ●●● | ○ | ○ | ○ |
| Rate Limiting | ●●● | ○ | ○ | ○ | ○ |
| Route Request | ●●● | ○ | ○ | ○ | ○ |
| Publish Event | ○ | ○ | ●●● | ○ | ○ |
| Subscribe Event | ○ | ○ | ●●● | ●○○ | ●○○ |
| Send Notification | ○ | ○ | ○ | ●●● | ○ |
| Orchestrate Process | ○ | ○ | ●○○ | ●○○ | ●●● |
| Circuit Breaking | ●●● | ○ | ○ | ○ | ○ |

---

# 6. Application Interaction Matrix

## 6.1 Synchronous Interactions (API Calls)

| From \ To | Customer | Account | Payment | Card | Wealth | KYC | AML | Fraud | Treasury | Notification |
|-----------|----------|---------|---------|------|--------|-----|-----|-------|----------|--------------|
| Mobile BFF | ● | ● | ● | ● | ● | ○ | ○ | ○ | ○ | ○ |
| Web BFF | ● | ● | ● | ● | ● | ○ | ○ | ○ | ○ | ○ |
| Partner BFF | ● | ● | ● | ● | ○ | ○ | ○ | ○ | ○ | ○ |
| Advisor BFF | ● | ● | ○ | ○ | ● | ○ | ○ | ○ | ○ | ○ |
| Customer Svc | - | ● | ○ | ○ | ○ | ● | ○ | ○ | ○ | ● |
| Account Svc | ● | - | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ● |
| Payment Svc | ○ | ● | - | ○ | ○ | ○ | ● | ● | ● | ● |
| Card Svc | ○ | ● | ○ | - | ○ | ○ | ● | ● | ○ | ● |
| Wealth Svc | ● | ● | ○ | ○ | - | ○ | ● | ○ | ● | ● |
| KYC Svc | ● | ○ | ○ | ○ | ○ | - | ○ | ○ | ○ | ● |
| AML Svc | ● | ● | ○ | ○ | ● | ○ | - | ○ | ○ | ● |
| Fraud Svc | ○ | ● | ○ | ● | ○ | ○ | ○ | - | ○ | ● |

**Legend:** ● = Direct API Call | ○ = No Direct Call | - = Self

## 6.2 Asynchronous Interactions (Events)

| Publisher \ Subscriber | Customer | Account | Payment | Card | Wealth | KYC | AML | Fraud | Treasury | Notification | Data Lake |
|------------------------|----------|---------|---------|------|--------|-----|-----|-------|----------|--------------|-----------|
| Customer Svc | - | ● | ○ | ○ | ● | ○ | ● | ○ | ○ | ● | ● |
| Account Svc | ● | - | ● | ● | ● | ○ | ● | ● | ● | ● | ● |
| Payment Svc | ○ | ● | - | ○ | ○ | ○ | ● | ● | ● | ● | ● |
| Card Svc | ○ | ● | ○ | - | ○ | ○ | ● | ● | ○ | ● | ● |
| Wealth Svc | ○ | ● | ○ | ○ | - | ○ | ● | ○ | ● | ● | ● |
| KYC Svc | ● | ○ | ○ | ○ | ○ | - | ● | ○ | ○ | ● | ● |
| AML Svc | ○ | ○ | ● | ● | ● | ○ | - | ○ | ○ | ● | ● |
| Fraud Svc | ○ | ○ | ● | ● | ○ | ○ | ○ | - | ○ | ● | ● |
| Treasury Svc | ○ | ● | ● | ○ | ● | ○ | ○ | ○ | - | ● | ● |

**Legend:** ● = Subscribes to Events | ○ = Does Not Subscribe | - = Self

## 6.3 External Integration Summary

| Service | SEPA | SWIFT | FPS | Visa/MC | Onfido | Bloomberg | Global Advisor |
|---------|------|-------|-----|---------|--------|-----------|----------------|
| Payment Svc | ● | ● | ● | ○ | ○ | ○ | ○ |
| Card Svc | ○ | ○ | ○ | ● | ○ | ○ | ○ |
| KYC Svc | ○ | ○ | ○ | ○ | ● | ○ | ○ |
| Treasury Svc | ○ | ○ | ○ | ○ | ○ | ● | ○ |
| Wealth Svc | ○ | ○ | ○ | ○ | ○ | ● | ● |

---

# 7. Summary Statistics

## 7.1 Application Portfolio Summary

| Category | Count | Status |
|----------|-------|--------|
| Channel Applications | 7 | Target |
| BFF Services | 5 | Target |
| Domain Services | 12 | Target |
| Platform Services | 10 | Target |
| Integration Services | 8 | Target |
| Legacy (to retire) | 4 | Sunset |
| **Total Target Portfolio** | **42** | |

## 7.2 Interface Summary

| Category | Count |
|----------|-------|
| External Partner APIs | 6 |
| Channel APIs | 4 |
| Internal Service APIs | 12 |
| Event Interfaces (Kafka) | 10 |
| External System Interfaces | 9 |
| **Total Interfaces** | **41** |

---

**Document End**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Architecture Team | CTO |
| [Date] | [Date] | [Date] |
