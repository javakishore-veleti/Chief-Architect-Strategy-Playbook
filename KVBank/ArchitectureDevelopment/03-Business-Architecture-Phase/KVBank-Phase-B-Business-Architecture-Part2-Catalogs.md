# KVBank Phase B: Business Architecture

## Part 2: Artifacts - Catalogs

---

# 11. Artifacts: Catalogs

## 11.1 Value Stream Catalog

| VS ID | Value Stream Name | Description | Trigger | Outcome | Customer Segment | Owner |
|-------|-------------------|-------------|---------|---------|------------------|-------|
| VS-01 | Acquire to Active | From prospect awareness to active customer | Marketing touchpoint | Active account | All | Head of Marketing |
| VS-02 | Transact to Settle | From payment initiation to settlement | Payment request | Funds transferred | All | Head of Payments |
| VS-03 | Issue to Use | From card request to active card usage | Card application | Card activated | Retail, Business | Head of Cards |
| VS-04 | Lend to Collect | From credit application to full repayment | Credit request | Loan repaid | Retail, Business | Head of Credit |
| VS-05 | Inquire to Resolve | From customer inquiry to resolution | Customer contact | Issue resolved | All | Head of CS |
| VS-06 | Onboard to Serve | From application to ongoing service | Account application | Services available | Business | Head of Business |
| VS-07 | Invest to Return | From investment decision to returns delivery | Investment decision | Returns realized | Wealth | Head of Wealth |
| VS-08 | Trade to Settle (FX) | From FX trade to settlement | FX order | Trade settled | Business, Treasury | Head of Treasury |
| VS-09 | Detect to Prevent | From threat detection to prevention | Risk signal | Threat mitigated | All | CRO |
| VS-10 | Report to Comply | From data capture to regulatory submission | Regulatory deadline | Report submitted | All | CCO |

---

## 11.2 Value Stream Stages Catalog

### VS-01: Acquire to Active

| Stage ID | Stage Name | Description | Entry Criteria | Exit Criteria | SLA |
|----------|------------|-------------|----------------|---------------|-----|
| VS01-S1 | Discover | Prospect becomes aware of KVBank | Marketing exposure | Intent to learn more | - |
| VS01-S2 | Consider | Prospect evaluates KVBank offering | Visit website/app | Decision to apply | - |
| VS01-S3 | Apply | Prospect submits application | Start application | Application submitted | 5 min |
| VS01-S4 | Verify | Identity verification | Application received | Identity confirmed | 2 min |
| VS01-S5 | Approve | Application decision | Identity confirmed | Account approved | 1 min |
| VS01-S6 | Activate | Account setup and first use | Account approved | First transaction | 2 min |

### VS-02: Transact to Settle

| Stage ID | Stage Name | Description | Entry Criteria | Exit Criteria | SLA |
|----------|------------|-------------|----------------|---------------|-----|
| VS02-S1 | Initiate | Customer initiates payment | Payment request | Details captured | 10 sec |
| VS02-S2 | Validate | Payment validation | Details captured | Validation passed | 1 sec |
| VS02-S3 | Screen | AML/Fraud screening | Validation passed | Screening passed | 2 sec |
| VS02-S4 | Authorize | Debit authorization | Screening passed | Funds reserved | 1 sec |
| VS02-S5 | Execute | Payment execution | Funds reserved | Payment sent | 2 sec |
| VS02-S6 | Notify | Customer notification | Payment sent | Customer notified | 1 sec |
| VS02-S7 | Settle | Final settlement | Payment sent | Settlement complete | Same day |

### VS-07: Invest to Return (NEW)

| Stage ID | Stage Name | Description | Entry Criteria | Exit Criteria | SLA |
|----------|------------|-------------|----------------|---------------|-----|
| VS07-S1 | Profile | Understand customer profile | Customer interest | Profile complete | 10 min |
| VS07-S2 | Assess | Risk assessment | Profile complete | Risk level assigned | 5 min |
| VS07-S3 | Recommend | Generate recommendations | Risk level assigned | Options presented | 2 min |
| VS07-S4 | Select | Customer selection | Options presented | Selection confirmed | Customer-driven |
| VS07-S5 | Execute | Trade execution | Selection confirmed | Orders executed | 1 min |
| VS07-S6 | Confirm | Confirmation | Orders executed | Customer confirmed | 1 min |
| VS07-S7 | Monitor | Ongoing monitoring | Position established | Alerts as needed | Continuous |
| VS07-S8 | Report | Performance reporting | Reporting period end | Report delivered | Daily/Monthly |

---

## 11.3 Business Capabilities Catalog

### Level 1-3 Capability Hierarchy

| L1 ID | L1 Capability | L2 ID | L2 Capability | L3 ID | L3 Capability | Owner |
|-------|---------------|-------|---------------|-------|---------------|-------|
| **CAP-1** | **Customer Management** | | | | | **Head of Retail** |
| | | CAP-1.1 | Acquire Customers | CAP-1.1.1 | Market to Prospects | Marketing |
| | | | | CAP-1.1.2 | Manage Referrals | Marketing |
| | | | | CAP-1.1.3 | Manage Partner Channels | Partnerships |
| | | CAP-1.2 | Onboard Customers | CAP-1.2.1 | Collect Information | Onboarding |
| | | | | CAP-1.2.2 | Verify Identity | KYC Team |
| | | | | CAP-1.2.3 | Open Accounts | Onboarding |
| | | | | CAP-1.2.4 | Issue Credentials | Security |
| | | CAP-1.3 | Serve Customers | CAP-1.3.1 | Provide Mobile Banking | Product |
| | | | | CAP-1.3.2 | Provide Web Banking | Product |
| | | | | CAP-1.3.3 | Provide API Access | Platform |
| | | | | CAP-1.3.4 | Send Notifications | Platform |
| | | CAP-1.4 | Support Customers | CAP-1.4.1 | Handle Inquiries | CS |
| | | | | CAP-1.4.2 | Resolve Complaints | CS |
| | | | | CAP-1.4.3 | Provide Self-Service | Product |
| | | CAP-1.5 | Retain Customers | CAP-1.5.1 | Identify At-Risk | Analytics |
| | | | | CAP-1.5.2 | Execute Retention | Marketing |
| **CAP-2** | **Banking Services** | | | | | **Head of Payments** |
| | | CAP-2.1 | Manage Accounts | CAP-2.1.1 | Open Accounts | Operations |
| | | | | CAP-2.1.2 | Maintain Accounts | Operations |
| | | | | CAP-2.1.3 | Close Accounts | Operations |
| | | | | CAP-2.1.4 | Manage Multi-Currency | Treasury |
| | | CAP-2.2 | Process Payments | CAP-2.2.1 | Execute SEPA Payments | Payments |
| | | | | CAP-2.2.2 | Execute SWIFT Payments | Payments |
| | | | | CAP-2.2.3 | Process Instant Payments | Payments |
| | | | | CAP-2.2.4 | Manage Direct Debits | Payments |
| | | | | CAP-2.2.5 | Execute Internal Transfers | Payments |
| | | CAP-2.3 | Issue & Process Cards | CAP-2.3.1 | Issue Physical Cards | Cards |
| | | | | CAP-2.3.2 | Issue Virtual Cards | Cards |
| | | | | CAP-2.3.3 | Process Card Transactions | Cards |
| | | | | CAP-2.3.4 | Manage Card Controls | Cards |
| | | CAP-2.4 | Lend Money | CAP-2.4.1 | Assess Creditworthiness | Credit |
| | | | | CAP-2.4.2 | Originate Loans | Credit |
| | | | | CAP-2.4.3 | Service Loans | Credit |
| | | | | CAP-2.4.4 | Provide Overdrafts | Credit |
| | | CAP-2.5 | Accept Deposits | CAP-2.5.1 | Hold Funds | Treasury |
| | | | | CAP-2.5.2 | Calculate Interest | Operations |
| | | | | CAP-2.5.3 | Manage Savings Products | Product |
| **CAP-3** | **Treasury Management** | | | | | **Head of Treasury** |
| | | CAP-3.1 | Exchange Currencies | CAP-3.1.1 | Quote FX Rates | Treasury |
| | | | | CAP-3.1.2 | Execute FX Trades | Treasury |
| | | | | CAP-3.1.3 | Manage FX Positions | Treasury |
| | | CAP-3.2 | Manage Liquidity | CAP-3.2.1 | Forecast Cash Flows | Treasury |
| | | | | CAP-3.2.2 | Manage Funding | Treasury |
| | | | | CAP-3.2.3 | Report Liquidity | Treasury |
| | | CAP-3.3 | Hedge Risk | CAP-3.3.1 | Identify Exposures | Risk |
| | | | | CAP-3.3.2 | Execute Hedges | Treasury |
| | | | | CAP-3.3.3 | Monitor Hedge Effectiveness | Risk |
| | | CAP-3.4 | Source Market Data | CAP-3.4.1 | Ingest Market Data | Platform |
| | | | | CAP-3.4.2 | Distribute Market Data | Platform |
| | | | | CAP-3.4.3 | Monitor Data Quality | Platform |
| **CAP-4** | **Wealth Management** | | | | | **Head of Wealth** |
| | | CAP-4.1 | Advise on Investments | CAP-4.1.1 | Profile Customers | Advisory |
| | | | | CAP-4.1.2 | Assess Risk Tolerance | Advisory |
| | | | | CAP-4.1.3 | Generate Recommendations | Advisory |
| | | | | CAP-4.1.4 | Document Advice | Compliance |
| | | CAP-4.2 | Manage Portfolios | CAP-4.2.1 | Construct Portfolios | Portfolio Mgmt |
| | | | | CAP-4.2.2 | Execute Orders | Trading |
| | | | | CAP-4.2.3 | Rebalance Portfolios | Portfolio Mgmt |
| | | | | CAP-4.2.4 | Monitor Performance | Portfolio Mgmt |
| | | CAP-4.3 | Robo-Advise | CAP-4.3.1 | Automate Profiling | Robo |
| | | | | CAP-4.3.2 | Automate Allocation | Robo |
| | | | | CAP-4.3.3 | Automate Rebalancing | Robo |
| | | CAP-4.4 | Plan Finances | CAP-4.4.1 | Set Financial Goals | Planning |
| | | | | CAP-4.4.2 | Project Scenarios | Planning |
| | | | | CAP-4.4.3 | Track Progress | Planning |
| | | CAP-4.5 | Report to Clients | CAP-4.5.1 | Generate Statements | Reporting |
| | | | | CAP-4.5.2 | Produce Tax Reports | Reporting |
| | | | | CAP-4.5.3 | Deliver Insights | Analytics |
| **CAP-5** | **Risk & Compliance** | | | | | **CRO** |
| | | CAP-5.1 | Verify Identities | CAP-5.1.1 | Collect Documents | KYC |
| | | | | CAP-5.1.2 | Verify Documents | KYC |
| | | | | CAP-5.1.3 | Screen Against Lists | KYC |
| | | | | CAP-5.1.4 | Perform Ongoing Due Diligence | KYC |
| | | CAP-5.2 | Monitor AML | CAP-5.2.1 | Screen Transactions | AML |
| | | | | CAP-5.2.2 | Investigate Alerts | AML |
| | | | | CAP-5.2.3 | File SARs | AML |
| | | CAP-5.3 | Prevent Fraud | CAP-5.3.1 | Detect Fraud Patterns | Fraud |
| | | | | CAP-5.3.2 | Block Suspicious Transactions | Fraud |
| | | | | CAP-5.3.3 | Manage Fraud Cases | Fraud |
| | | CAP-5.4 | Manage Risk | CAP-5.4.1 | Identify Risks | Risk |
| | | | | CAP-5.4.2 | Assess Risks | Risk |
| | | | | CAP-5.4.3 | Monitor Risks | Risk |
| | | | | CAP-5.4.4 | Report Risks | Risk |
| | | CAP-5.5 | Report to Regulators | CAP-5.5.1 | Generate Reports | Regulatory |
| | | | | CAP-5.5.2 | Submit Reports | Regulatory |
| | | | | CAP-5.5.3 | Respond to Inquiries | Regulatory |
| **CAP-6** | **Operations Management** | | | | | **COO** |
| | | CAP-6.1 | Record in Ledger | CAP-6.1.1 | Post Transactions | Ledger |
| | | | | CAP-6.1.2 | Maintain Balances | Ledger |
| | | | | CAP-6.1.3 | Generate Statements | Ledger |
| | | CAP-6.2 | Track P&L | CAP-6.2.1 | Calculate P&L | Finance |
| | | | | CAP-6.2.2 | Allocate Costs | Finance |
| | | | | CAP-6.2.3 | Report P&L | Finance |
| | | CAP-6.3 | Reconcile & Settle | CAP-6.3.1 | Match Transactions | Recon |
| | | | | CAP-6.3.2 | Identify Breaks | Recon |
| | | | | CAP-6.3.3 | Resolve Breaks | Recon |
| | | CAP-6.4 | Run Batch Jobs | CAP-6.4.1 | Schedule Jobs | Operations |
| | | | | CAP-6.4.2 | Monitor Jobs | Operations |
| | | | | CAP-6.4.3 | Handle Exceptions | Operations |
| | | CAP-6.5 | Manage Partners | CAP-6.5.1 | Onboard Partners | Partnerships |
| | | | | CAP-6.5.2 | Monitor SLAs | Partnerships |
| | | | | CAP-6.5.3 | Manage Contracts | Partnerships |
| **CAP-7** | **Technology Enablement** | | | | | **CTO** |
| | | CAP-7.1 | Manage Identities | CAP-7.1.1 | Authenticate Users | Security |
| | | | | CAP-7.1.2 | Authorize Access | Security |
| | | | | CAP-7.1.3 | Manage Credentials | Security |
| | | CAP-7.2 | Manage Data | CAP-7.2.1 | Store Data | Platform |
| | | | | CAP-7.2.2 | Govern Data | Data Governance |
| | | | | CAP-7.2.3 | Protect Data | Security |
| | | CAP-7.3 | Analyze Data | CAP-7.3.1 | Generate Reports | Analytics |
| | | | | CAP-7.3.2 | Perform Ad-hoc Analysis | Analytics |
| | | | | CAP-7.3.3 | Deliver Dashboards | Analytics |
| | | CAP-7.4 | Run ML | CAP-7.4.1 | Train Models | Data Science |
| | | | | CAP-7.4.2 | Deploy Models | ML Ops |
| | | | | CAP-7.4.3 | Monitor Models | ML Ops |
| | | CAP-7.5 | Integrate with Partners | CAP-7.5.1 | Manage APIs | Platform |
| | | | | CAP-7.5.2 | Orchestrate Services | Platform |
| | | | | CAP-7.5.3 | Monitor Integrations | Platform |

---

## 11.4 Organization/Actor Catalog

| Actor ID | Actor Name | Type | Description | Location | Capabilities Supported |
|----------|------------|------|-------------|----------|----------------------|
| ORG-01 | Executive Committee | Internal | C-suite leadership team | London | All (governance) |
| ORG-02 | Retail Banking | Internal | Retail customer business unit | London | CAP-1, CAP-2 |
| ORG-03 | Business Banking | Internal | Business customer unit | London | CAP-1, CAP-2 |
| ORG-04 | Wealth Management | Internal | Wealth services unit | London | CAP-4 |
| ORG-05 | Engineering | Internal | Technology delivery | London, Lisbon | CAP-7 |
| ORG-06 | Product | Internal | Product management | London | CAP-1, CAP-2, CAP-4 |
| ORG-07 | Operations | Internal | Banking operations | London, Lisbon | CAP-6 |
| ORG-08 | Risk | Internal | Risk management | London | CAP-5 |
| ORG-09 | Compliance | Internal | Regulatory compliance | London | CAP-5 |
| ORG-10 | Customer Service | Internal | Customer support | Lisbon | CAP-1.4 |
| ORG-11 | Treasury | Internal | Treasury operations | London | CAP-3 |
| ORG-12 | Finance | Internal | Financial management | London | CAP-6.2 |
| ORG-13 | Legal | Internal | Legal counsel | London | Contracts |
| ORG-14 | HR | Internal | Human resources | London | Support |
| ACT-01 | Retail Customer | External | Individual banking customer | UK, EU | All customer-facing |
| ACT-02 | Business Customer | External | Business/SME customer | UK, EU | All customer-facing |
| ACT-03 | Wealth Client | External | Investment customer | UK, EU | CAP-4 |
| ACT-04 | Visa | External | Card network partner | Global | CAP-2.3 |
| ACT-05 | Mastercard | External | Card network partner | Global | CAP-2.3 |
| ACT-06 | SWIFT | External | Payment network partner | Global | CAP-2.2 |
| ACT-07 | SEPA | External | Payment scheme | EU | CAP-2.2 |
| ACT-08 | Onfido | External | KYC verification partner | UK | CAP-5.1 |
| ACT-09 | ComplyAdvantage | External | AML screening partner | UK | CAP-5.2 |
| ACT-10 | AWS | External | Cloud provider | EU regions | CAP-7 |
| ACT-11 | Reuters | External | Market data provider | Global | CAP-3.4 |
| ACT-12 | FCA | External | UK regulator | UK | CAP-5.5 |
| ACT-13 | BaFin | External | German regulator | Germany | CAP-5.5 |
| ACT-14 | Auditors | External | External audit firm | UK | CAP-5 |

---

## 11.5 Driver/Goal/Objective Catalog

| ID | Type | Name | Description | Measure | Target | Timeline | Owner |
|----|------|------|-------------|---------|--------|----------|-------|
| D-01 | Driver | Competitive Pressure | Competitors releasing features weekly | Feature velocity | Match/exceed | 24 months | CPO |
| D-02 | Driver | Customer Expectations | Demand for real-time, personalized | NPS, churn | NPS 55+, churn <5% | 24 months | CPO |
| D-03 | Driver | Regulatory Evolution | Increasing compliance requirements | Compliance status | 100% compliant | Ongoing | CCO |
| D-04 | Driver | Economic Pressure | Need for sustainable unit economics | Cost per customer | €5/month | 36 months | CFO |
| D-05 | Driver | Growth Imperative | Board mandate for 10x growth | Customer count | 1.05M | 36 months | CEO |
| G-01 | Goal | Customer Growth | Grow retail and business customers | Active customers | 1.05M total | 36 months | CEO |
| G-02 | Goal | Revenue Diversification | Launch wealth management | AUM | €500M | 36 months | Head of Wealth |
| G-03 | Goal | Market Expansion | Expand to 5 European markets | Markets live | 5 | 36 months | CEO |
| G-04 | Goal | Cost Efficiency | Reduce unit economics | Cost/customer | €5/month | 36 months | CFO |
| G-05 | Goal | Platform Excellence | Industry-leading availability | Uptime | 99.99% | 18 months | CTO |
| O-01 | Objective | Instant Payments | Enable SEPA Instant and FPS | Coverage | 100% | 12 months | Head of Payments |
| O-02 | Objective | Fraud Prevention | Reduce fraud losses | Fraud rate | 0.02% | 24 months | CRO |
| O-03 | Objective | STP Improvement | Increase automation | STP rate | 95% | 36 months | COO |
| O-04 | Objective | Customer 360 | Unified customer view | Deployment | Live | 6 months | CTO |
| O-05 | Objective | Wealth MVP | Launch basic wealth services | MVP live | Complete | 18 months | Head of Wealth |
| O-06 | Objective | Germany Launch | Enter German market | Market live | Complete | 18 months | CEO |
| O-07 | Objective | France Launch | Enter French market | Market live | Complete | 21 months | CEO |
| O-08 | Objective | Robo-Advisory | Automated investment service | Service live | Complete | 30 months | Head of Wealth |

---

## 11.6 Role Catalog

| Role ID | Role Name | Description | Organization | Responsibilities |
|---------|-----------|-------------|--------------|------------------|
| R-01 | Chief Executive Officer | Overall leadership | Executive | Strategy, Board, P&L |
| R-02 | Chief Financial Officer | Financial leadership | Finance | Budget, treasury oversight, reporting |
| R-03 | Chief Technology Officer | Technology leadership | Engineering | Technology strategy, delivery |
| R-04 | Chief Risk Officer | Risk leadership | Risk | Enterprise risk management |
| R-05 | Chief Operating Officer | Operations leadership | Operations | Operational excellence |
| R-06 | Chief Product Officer | Product leadership | Product | Product strategy, roadmap |
| R-07 | Chief Compliance Officer | Compliance leadership | Compliance | Regulatory compliance |
| R-08 | CISO | Security leadership | Security | Information security |
| R-09 | Chief Wealth Officer | Wealth business leadership | Wealth | Wealth P&L, strategy |
| R-10 | Head of Retail Banking | Retail business | Retail | Retail P&L, products |
| R-11 | Head of Business Banking | Business banking | Business | Business P&L, products |
| R-12 | Head of Customer Service | Customer support | CS | Service quality, efficiency |
| R-13 | Head of Treasury | Treasury operations | Treasury | Liquidity, FX, hedging |
| R-14 | Chief Architect | Architecture leadership | Architecture | Enterprise architecture |
| R-15 | VP Engineering | Engineering delivery | Engineering | Development, DevOps |
| R-16 | Data Protection Officer | Data privacy | Compliance | GDPR compliance |
| R-17 | MLRO | AML reporting | Compliance | AML/CTF compliance |
| R-18 | Investment Advisor | Wealth advisory | Wealth | Client advisory |
| R-19 | Portfolio Manager | Portfolio management | Wealth | Portfolio construction |
| R-20 | Customer Service Agent | Customer support | CS | Handle inquiries |
| R-21 | KYC Analyst | Identity verification | KYC | Customer verification |
| R-22 | AML Analyst | AML investigation | AML | Alert investigation |
| R-23 | Fraud Analyst | Fraud investigation | Fraud | Fraud detection/prevention |
| R-24 | Software Engineer | Development | Engineering | Build software |
| R-25 | Data Scientist | ML/Analytics | Data Science | Build models |
| R-26 | Product Manager | Product ownership | Product | Feature definition |
| R-27 | Market Lead | Regional leadership | Regional | Market P&L |

---

## 11.7 Business Service/Function Catalog

| Service ID | Service Name | Description | Type | Provider | Consumer | SLA |
|------------|--------------|-------------|------|----------|----------|-----|
| BS-01 | Account Opening | Open new customer accounts | Core | Banking Services | Customers | 5 min |
| BS-02 | Payment Execution | Execute customer payments | Core | Payments | Customers | Real-time |
| BS-03 | Card Issuance | Issue debit/credit cards | Core | Cards | Customers | Virtual: instant |
| BS-04 | Balance Inquiry | Provide account balances | Core | Ledger | Customers | Real-time |
| BS-05 | Transaction History | Provide transaction records | Core | Ledger | Customers | Real-time |
| BS-06 | FX Conversion | Convert between currencies | Core | Treasury | Customers | Real-time |
| BS-07 | Investment Advisory | Provide investment advice | Wealth | Wealth | Wealth Clients | 10 min |
| BS-08 | Portfolio Management | Manage investment portfolios | Wealth | Wealth | Wealth Clients | Daily |
| BS-09 | Robo-Advisory | Automated investment | Wealth | Wealth | All Customers | Real-time |
| BS-10 | Customer Support | Handle customer inquiries | Support | CS | Customers | 4 hr response |
| BS-11 | KYC Verification | Verify customer identity | Compliance | KYC | Customers | 2 min |
| BS-12 | AML Screening | Screen for AML risks | Compliance | AML | Internal | Real-time |
| BS-13 | Fraud Detection | Detect fraudulent activity | Risk | Fraud | Internal | Real-time |
| BS-14 | Regulatory Reporting | Submit regulatory reports | Compliance | Regulatory | Regulators | As required |
| BS-15 | Partner API | API services for partners | Platform | Platform | Partners | 99.9% |
| BS-16 | Authentication | Authenticate users | Security | IAM | All | Real-time |
| BS-17 | Notifications | Send customer notifications | Platform | Platform | Customers | Near real-time |
| BS-18 | Analytics | Business intelligence | Analytics | Analytics | Internal | Daily refresh |

---

## 11.8 Location Catalog

| Location ID | Location Name | Type | Country | Region | Functions | Status |
|-------------|---------------|------|---------|--------|-----------|--------|
| LOC-01 | London HQ | Office | UK | EMEA | Corporate, Tech, Product, Wealth | Current |
| LOC-02 | Lisbon Tech Hub | Office | Portugal | EMEA | Engineering, Support | Current |
| LOC-03 | Berlin Office | Office | Germany | EMEA | DE Operations, Engineering | Planned (M12) |
| LOC-04 | Paris Office | Office | France | EMEA | FR Operations | Planned (M18) |
| LOC-05 | Madrid Office | Office | Spain | EMEA | ES Operations | Planned (M24) |
| LOC-06 | Amsterdam Office | Office | Netherlands | EMEA | NL Operations | Planned (M30) |
| LOC-07 | AWS EU-WEST-1 | Data Center | Ireland | EMEA | Primary Cloud | Current |
| LOC-08 | AWS EU-WEST-2 | Data Center | UK | EMEA | UK Data Residency | Current |
| LOC-09 | AWS EU-CENTRAL-1 | Data Center | Germany | EMEA | DE Data Residency | Planned (M12) |

---

## 11.9 Process/Event/Control/Product Catalog

### Process Catalog

| Process ID | Process Name | Type | Description | Owner | Trigger | Outcome |
|------------|--------------|------|-------------|-------|---------|---------|
| P-01 | Customer Onboarding | Core | Onboard new customers | Onboarding | Application | Active account |
| P-02 | Payment Processing | Core | Process all payment types | Payments | Payment request | Settlement |
| P-03 | Card Issuance | Core | Issue and manage cards | Cards | Card request | Card active |
| P-04 | Credit Assessment | Core | Assess creditworthiness | Credit | Credit application | Decision |
| P-05 | KYC Verification | Compliance | Verify customer identity | KYC | Customer data | Verified/Rejected |
| P-06 | AML Monitoring | Compliance | Monitor for AML risks | AML | Transaction | Alert/Clear |
| P-07 | Fraud Detection | Risk | Detect fraudulent activity | Fraud | Transaction | Block/Allow |
| P-08 | Complaint Handling | Support | Resolve customer complaints | CS | Complaint | Resolution |
| P-09 | Account Closure | Core | Close customer accounts | Operations | Closure request | Account closed |
| P-10 | Investment Advice | Wealth | Provide investment recommendations | Advisory | Client meeting | Advice delivered |
| P-11 | Portfolio Rebalancing | Wealth | Rebalance portfolios | Portfolio Mgmt | Trigger event | Rebalanced |
| P-12 | Regulatory Reporting | Compliance | Generate and submit reports | Regulatory | Schedule | Report submitted |
| P-13 | Reconciliation | Operations | Reconcile transactions | Recon | Daily | Matched/Breaks |
| P-14 | FX Trading | Treasury | Execute FX trades | Treasury | Trade request | Trade settled |
| P-15 | Liquidity Management | Treasury | Manage daily liquidity | Treasury | Daily | Positions balanced |

### Event Catalog

| Event ID | Event Name | Description | Producer | Consumers | Frequency |
|----------|------------|-------------|----------|-----------|-----------|
| E-01 | CustomerCreated | New customer registered | Onboarding | CRM, KYC, Marketing | ~2000/day target |
| E-02 | AccountOpened | New account opened | Accounts | Ledger, Cards, Notifications | ~3000/day target |
| E-03 | PaymentInitiated | Payment request received | Payments | AML, Fraud, Ledger | ~500K/day target |
| E-04 | PaymentCompleted | Payment settled | Payments | Ledger, Notifications | ~500K/day target |
| E-05 | CardIssued | Card issued to customer | Cards | Notifications, CRM | ~1000/day target |
| E-06 | FraudAlertRaised | Suspicious activity detected | Fraud | Operations, Notifications | ~500/day target |
| E-07 | AMLAlertRaised | AML screening alert | AML | Investigations | ~200/day target |
| E-08 | TradeExecuted | Investment trade completed | Trading | Portfolio, Ledger | ~10K/day target |
| E-09 | PortfolioRebalanced | Portfolio rebalancing complete | Portfolio | Reporting, Notifications | Daily |
| E-10 | ComplianceBreached | Compliance rule violated | Compliance | Risk, Legal | As needed |

### Control Catalog

| Control ID | Control Name | Description | Type | Risk Addressed | Owner |
|------------|--------------|-------------|------|----------------|-------|
| C-01 | KYC Verification | Verify customer identity before onboarding | Preventive | Identity fraud | KYC |
| C-02 | AML Screening | Screen transactions for money laundering | Detective | AML | AML |
| C-03 | Fraud Scoring | ML-based transaction fraud scoring | Detective | Transaction fraud | Fraud |
| C-04 | Payment Limits | Enforce transaction limits | Preventive | Unauthorized transactions | Payments |
| C-05 | Multi-Factor Auth | Require MFA for sensitive operations | Preventive | Account takeover | Security |
| C-06 | Segregation of Duties | Separate critical functions | Preventive | Internal fraud | Operations |
| C-07 | Four-Eyes Approval | Dual approval for large transactions | Preventive | Error, fraud | Operations |
| C-08 | Audit Logging | Log all system activities | Detective | All | Security |
| C-09 | Data Encryption | Encrypt data at rest and in transit | Preventive | Data breach | Security |
| C-10 | Access Reviews | Periodic access certification | Detective | Unauthorized access | Security |

### Product Catalog

| Product ID | Product Name | Segment | Description | Revenue Model | Status |
|------------|--------------|---------|-------------|---------------|--------|
| PRD-01 | Personal Account | Retail | Basic current account | FX, interchange | Live |
| PRD-02 | Premium Account | Retail | Premium current account | Monthly fee + FX | Live |
| PRD-03 | Business Account | Business | Business current account | Monthly fee + transactions | Live |
| PRD-04 | Multi-Currency Account | All | Hold multiple currencies | FX spread | Live |
| PRD-05 | Debit Card | All | Visa/Mastercard debit | Interchange | Live |
| PRD-06 | Virtual Card | All | Instant virtual card | Interchange | Live |
| PRD-07 | Credit Card | Retail | Visa credit card | Interest + interchange | Planned |
| PRD-08 | Personal Loan | Retail | Unsecured lending | Interest | Live |
| PRD-09 | Business Loan | Business | Business lending | Interest | Live |
| PRD-10 | Overdraft | All | Account overdraft | Interest | Live |
| PRD-11 | Savings Account | Retail | Interest-bearing savings | Interest spread | Live |
| PRD-12 | Investment Account | Wealth | General investment account | Advisory fee | Planned |
| PRD-13 | ISA | Wealth | Tax-advantaged ISA | Advisory fee | Planned |
| PRD-14 | Robo-Portfolio | Wealth | Automated portfolio | Management fee | Planned |
| PRD-15 | Partner API | Partners | API access for partners | API fees | Planned |

---

## 11.10 Contract/Measure Catalog

### Contract Catalog

| Contract ID | Contract Name | Parties | Type | Value | Start | End | Owner |
|-------------|---------------|---------|------|-------|-------|-----|-------|
| CON-01 | Visa Network | KVBank, Visa | Service | Volume-based | 2022 | 2027 | Partnerships |
| CON-02 | Mastercard Network | KVBank, MC | Service | Volume-based | 2022 | 2027 | Partnerships |
| CON-03 | SWIFT Membership | KVBank, SWIFT | Membership | €200K/yr | 2021 | 2026 | Treasury |
| CON-04 | AWS Cloud | KVBank, AWS | Service | €3M/yr | 2023 | 2026 | IT |
| CON-05 | Onfido KYC | KVBank, Onfido | Service | Per-verification | 2022 | 2025 | KYC |
| CON-06 | ComplyAdvantage | KVBank, ComplyAdv | Service | Per-screening | 2022 | 2025 | AML |
| CON-07 | Reuters Market Data | KVBank, Reuters | Data | €500K/yr | 2023 | 2026 | Treasury |
| CON-08 | Global Advisor | KVBank, GA | Platform | €2M/yr | TBD | TBD | Wealth |

### Measure Catalog

| Measure ID | Measure Name | Description | Type | Current | Target | Owner |
|------------|--------------|-------------|------|---------|--------|-------|
| M-01 | Active Customers | Total active customers | Outcome | 105K | 1.05M | CEO |
| M-02 | Cost per Customer | Monthly cost per customer | Efficiency | €12 | €5 | CFO |
| M-03 | NPS | Net Promoter Score | Experience | 35 | 55 | CPO |
| M-04 | STP Rate | Straight-through processing rate | Efficiency | 60% | 95% | COO |
| M-05 | Platform Availability | System uptime | Reliability | 95% | 99.99% | CTO |
| M-06 | Fraud Loss Rate | Fraud as % of transaction volume | Risk | 0.05% | 0.02% | CRO |
| M-07 | Feature Velocity | Features released per year | Delivery | 6 | 52 | CPO |
| M-08 | Onboarding Time | Time to active account | Experience | 15 min | 5 min | Head of Retail |
| M-09 | AUM | Assets under management | Revenue | €0 | €500M | Head of Wealth |
| M-10 | Markets | Active European markets | Growth | 1 | 5 | CEO |
| M-11 | Incident Count | P1/P2 incidents per month | Reliability | 50 | 10 | COO |
| M-12 | First Contact Resolution | Issues resolved first contact | Service | 65% | 85% | Head of CS |
| M-13 | KYC Auto-Verification | Auto-verification rate | Efficiency | 80% | 95% | KYC |
| M-14 | Employee NPS | Employee satisfaction | HR | 40 | 60 | HR |
| M-15 | Revenue per Customer | Monthly revenue per customer | Revenue | €5 | €7 | CFO |

---

*[Continued in Part 3: Matrices and Diagrams]*
