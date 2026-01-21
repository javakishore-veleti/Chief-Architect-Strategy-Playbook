# KVBank

## Phase C: Data Architecture

### Part 2: Catalogs and Matrices

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Phase C: Data Architecture - Part 2 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Data Entity/Data Component Catalog
2. Data Entity/Business Function Matrix
3. Application/Data Matrix

---

# 1. Data Entity/Data Component Catalog

## 1.1 Customer Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-C001 | Customer | Core customer record | Head of Retail | PII - High | 7 years post-closure |
| DE-C002 | Individual | Natural person details | Head of Retail | PII - High | 7 years post-closure |
| DE-C003 | Organization | Legal entity details | Head of Business | Confidential | 7 years post-closure |
| DE-C004 | CustomerProfile | Preferences, settings | Head of Retail | PII - Medium | Active + 2 years |
| DE-C005 | CustomerSegment | Segment classification | Head of Marketing | Internal | Active |
| DE-C006 | ContactInfo | Address, phone, email | Head of Retail | PII - High | 7 years post-closure |
| DE-C007 | Identification | ID documents, KYC data | Head of Compliance | PII - Critical | 7 years post-closure |
| DE-C008 | Consent | GDPR consent records | DPO | PII - High | 7 years |
| DE-C009 | CustomerRelationship | Customer-to-customer links | Head of Business | Confidential | Active + 2 years |
| DE-C010 | Beneficiary | Payment beneficiaries | Head of Payments | PII - Medium | Active + 2 years |

## 1.2 Account Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-A001 | Account | Core account record | Head of Operations | Confidential | 7 years post-closure |
| DE-A002 | CurrentAccount | Current/checking account | Head of Operations | Confidential | 7 years post-closure |
| DE-A003 | SavingsAccount | Savings account | Head of Operations | Confidential | 7 years post-closure |
| DE-A004 | AccountHolder | Account ownership | Head of Operations | Confidential | 7 years post-closure |
| DE-A005 | AccountBalance | Current and available balance | Head of Operations | Confidential | Real-time + 7 years |
| DE-A006 | AccountLimit | Overdraft, spending limits | Head of Operations | Confidential | Active + 2 years |
| DE-A007 | AccountStatement | Periodic statements | Head of Operations | Confidential | 7 years |
| DE-A008 | AccountClosure | Closure records | Head of Operations | Confidential | 7 years post-closure |
| DE-A009 | InterestRate | Applied interest rates | Head of Treasury | Internal | 7 years |
| DE-A010 | AccountFee | Fee schedules applied | Head of Product | Internal | 7 years |

## 1.3 Transaction Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-T001 | Transaction | Core transaction record | Head of Payments | Confidential | 7 years |
| DE-T002 | Payment | Outbound payment | Head of Payments | Confidential | 7 years |
| DE-T003 | Transfer | Internal transfer | Head of Payments | Confidential | 7 years |
| DE-T004 | DirectDebit | Direct debit transaction | Head of Payments | Confidential | 7 years |
| DE-T005 | StandingOrder | Recurring payment instruction | Head of Payments | Confidential | Active + 7 years |
| DE-T006 | FXTransaction | Foreign exchange transaction | Head of Treasury | Confidential | 7 years |
| DE-T007 | TransactionStatus | Status and state history | Head of Payments | Internal | 7 years |
| DE-T008 | PaymentInstruction | Payment request details | Head of Payments | Confidential | 7 years |
| DE-T009 | Settlement | Settlement records | Head of Operations | Confidential | 7 years |
| DE-T010 | Reconciliation | Reconciliation records | Head of Operations | Internal | 7 years |

## 1.4 Card Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-CD001 | Card | Core card record | Head of Cards | PII - High | 7 years post-expiry |
| DE-CD002 | PhysicalCard | Physical card details | Head of Cards | PII - High | 7 years post-expiry |
| DE-CD003 | VirtualCard | Virtual card details | Head of Cards | PII - High | 7 years post-expiry |
| DE-CD004 | CardAuthorization | Authorization records | Head of Cards | Confidential | 7 years |
| DE-CD005 | CardTransaction | Card transaction | Head of Cards | Confidential | 7 years |
| DE-CD006 | CardLimit | Card spending limits | Head of Cards | Confidential | Active |
| DE-CD007 | CardControl | Card controls (freeze, etc.) | Head of Cards | Confidential | Active + 2 years |
| DE-CD008 | PIN | Encrypted PIN data | CISO | PII - Critical | Active |
| DE-CD009 | CardDispute | Dispute records | Head of Cards | Confidential | 7 years |
| DE-CD010 | MerchantCategory | MCC codes | Head of Cards | Public | Active |

## 1.5 Investment/Wealth Domain Entities (NEW)

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-I001 | InvestmentAccount | Investment account record | Head of Wealth | Confidential | 7 years post-closure |
| DE-I002 | Portfolio | Portfolio container | Head of Wealth | Confidential | 7 years post-closure |
| DE-I003 | Position | Security position | Head of Wealth | Confidential | 7 years |
| DE-I004 | Trade | Trade/order record | Head of Wealth | Confidential | 7 years |
| DE-I005 | Instrument | Financial instrument | Head of Wealth | Public | Active |
| DE-I006 | RiskProfile | Customer risk profile | Head of Wealth | PII - High | 7 years post-closure |
| DE-I007 | SuitabilityAssessment | MiFID suitability | Head of Compliance | PII - High | 7 years |
| DE-I008 | InvestmentAdvice | Advice records | Head of Wealth | Confidential | 7 years |
| DE-I009 | PortfolioValuation | Point-in-time valuation | Head of Wealth | Confidential | 7 years |
| DE-I010 | Dividend | Dividend records | Head of Wealth | Confidential | 7 years |
| DE-I011 | RoboAllocation | Robo-advisory allocation | Head of Wealth | Confidential | 7 years |
| DE-I012 | FinancialGoal | Customer financial goals | Head of Wealth | PII - Medium | Active + 2 years |

## 1.6 Risk & Compliance Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-R001 | KYCRecord | KYC verification record | Head of Compliance | PII - Critical | 7 years post-closure |
| DE-R002 | AMLAlert | AML screening alert | MLRO | Confidential | 7 years |
| DE-R003 | AMLCase | AML investigation case | MLRO | Confidential | 7 years |
| DE-R004 | SAR | Suspicious Activity Report | MLRO | Confidential | 7 years |
| DE-R005 | FraudAlert | Fraud detection alert | Head of Fraud | Confidential | 7 years |
| DE-R006 | FraudCase | Fraud investigation case | Head of Fraud | Confidential | 7 years |
| DE-R007 | RiskScore | Customer/transaction risk score | CRO | Confidential | 7 years |
| DE-R008 | Sanction | Sanctions screening result | Head of Compliance | Confidential | 7 years |
| DE-R009 | PEPRecord | PEP identification | Head of Compliance | Confidential | 7 years |
| DE-R010 | RegulatoryReport | Regulatory submission | Head of Compliance | Confidential | 7 years |
| DE-R011 | AuditLog | System audit trail | CISO | Internal | 7 years |
| DE-R012 | ControlTestResult | Control testing results | CRO | Internal | 7 years |

## 1.7 Treasury Domain Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-TR001 | FXRate | Foreign exchange rate | Head of Treasury | Public | 7 years |
| DE-TR002 | FXPosition | Currency position | Head of Treasury | Confidential | 7 years |
| DE-TR003 | LiquidityPosition | Liquidity status | Head of Treasury | Confidential | 7 years |
| DE-TR004 | HedgeTransaction | Hedge trade | Head of Treasury | Confidential | 7 years |
| DE-TR005 | NostroAccount | Nostro account balance | Head of Treasury | Confidential | 7 years |
| DE-TR006 | InterestRateCurve | Interest rate curves | Head of Treasury | Internal | 7 years |
| DE-TR007 | FundingSource | Funding arrangements | CFO | Confidential | 7 years |
| DE-TR008 | Counterparty | Trading counterparty | Head of Treasury | Confidential | Active + 7 years |

## 1.8 Reference Data Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-RF001 | Currency | Currency master | Data Governance | Public | Permanent |
| DE-RF002 | Country | Country master | Data Governance | Public | Permanent |
| DE-RF003 | Language | Language master | Data Governance | Public | Permanent |
| DE-RF004 | ProductCatalog | Product definitions | Head of Product | Internal | Active |
| DE-RF005 | FeeSchedule | Fee definitions | Head of Product | Internal | 7 years |
| DE-RF006 | ExchangeRate | Historical FX rates | Head of Treasury | Public | 7 years |
| DE-RF007 | BankDirectory | SWIFT/BIC directory | Head of Payments | Public | Active |
| DE-RF008 | HolidayCalendar | Market holidays | Data Governance | Public | Active |
| DE-RF009 | RegulatoryRule | Compliance rules | Head of Compliance | Internal | Active + 7 years |
| DE-RF010 | GLAccount | General ledger accounts | CFO | Internal | Permanent |

## 1.9 Event/Audit Entities

| Entity ID | Entity Name | Description | Owner | Classification | Retention |
|-----------|-------------|-------------|-------|----------------|-----------|
| DE-E001 | DomainEvent | All domain events | CTO | Varies | 7 years |
| DE-E002 | CustomerEvent | Customer lifecycle events | Head of Retail | PII - Medium | 7 years |
| DE-E003 | AccountEvent | Account lifecycle events | Head of Operations | Confidential | 7 years |
| DE-E004 | TransactionEvent | Transaction events | Head of Payments | Confidential | 7 years |
| DE-E005 | SecurityEvent | Security/access events | CISO | Internal | 7 years |
| DE-E006 | SystemEvent | Technical events | CTO | Internal | 1 year |
| DE-E007 | ChangeEvent | Data change events | Data Governance | Internal | 7 years |

---

# 2. Data Entity/Business Function Matrix

## 2.1 Customer Management Functions

| Data Entity | Acquire Customers | Onboard Customers | Serve Customers | Support Customers | Retain Customers |
|-------------|-------------------|-------------------|-----------------|-------------------|------------------|
| DE-C001 Customer | C | C | R | R | R |
| DE-C002 Individual | C | C | R | R | R |
| DE-C003 Organization | C | C | R | R | R |
| DE-C004 CustomerProfile | - | C | RU | RU | RU |
| DE-C005 CustomerSegment | C | - | R | R | RU |
| DE-C006 ContactInfo | C | C | R | RU | R |
| DE-C007 Identification | - | C | R | R | - |
| DE-C008 Consent | C | C | R | RU | R |
| DE-C009 CustomerRelationship | - | C | R | R | R |
| DE-C010 Beneficiary | - | - | C | RU | - |

**Legend:** C = Create | R = Read | U = Update | D = Delete | - = No Access

## 2.2 Banking Services Functions

| Data Entity | Manage Accounts | Process Payments | Issue Cards | Lend Money | Accept Deposits |
|-------------|-----------------|------------------|-------------|------------|-----------------|
| DE-A001 Account | CRU | R | R | R | R |
| DE-A002 CurrentAccount | CRU | R | R | R | R |
| DE-A003 SavingsAccount | CRU | R | - | - | RU |
| DE-A004 AccountHolder | CRU | R | R | R | R |
| DE-A005 AccountBalance | RU | RU | R | RU | RU |
| DE-A006 AccountLimit | CRU | R | - | CRU | - |
| DE-T001 Transaction | R | CRU | R | R | R |
| DE-T002 Payment | - | CRU | - | - | - |
| DE-T003 Transfer | - | CRU | - | - | - |
| DE-T006 FXTransaction | - | CRU | - | - | - |
| DE-CD001 Card | R | - | CRU | - | - |
| DE-CD004 CardAuthorization | - | - | CRU | - | - |
| DE-CD005 CardTransaction | - | R | CRU | - | - |

## 2.3 Treasury Functions

| Data Entity | Exchange Currencies | Manage Liquidity | Hedge Risk | Source Market Data |
|-------------|---------------------|------------------|------------|-------------------|
| DE-TR001 FXRate | R | R | R | CRU |
| DE-TR002 FXPosition | RU | R | RU | - |
| DE-TR003 LiquidityPosition | R | CRU | R | - |
| DE-TR004 HedgeTransaction | - | - | CRU | - |
| DE-TR005 NostroAccount | R | RU | R | - |
| DE-TR006 InterestRateCurve | R | R | R | CRU |
| DE-T006 FXTransaction | CRU | R | R | - |
| DE-A005 AccountBalance | R | R | R | - |

## 2.4 Wealth Management Functions (NEW)

| Data Entity | Advise on Investments | Manage Portfolios | Robo-Advise | Plan Finances | Report to Clients |
|-------------|----------------------|-------------------|-------------|---------------|-------------------|
| DE-I001 InvestmentAccount | C | RU | RU | R | R |
| DE-I002 Portfolio | C | CRU | CRU | R | R |
| DE-I003 Position | R | CRU | CRU | R | R |
| DE-I004 Trade | R | CRU | CRU | - | R |
| DE-I005 Instrument | R | R | R | R | R |
| DE-I006 RiskProfile | CRU | R | CRU | R | R |
| DE-I007 SuitabilityAssessment | CRU | R | CRU | R | R |
| DE-I008 InvestmentAdvice | CRU | R | C | R | R |
| DE-I009 PortfolioValuation | R | CRU | CRU | R | R |
| DE-I011 RoboAllocation | - | R | CRU | R | R |
| DE-I012 FinancialGoal | R | R | RU | CRU | R |
| DE-C001 Customer | R | R | R | R | R |

## 2.5 Risk & Compliance Functions

| Data Entity | Verify Identities | Monitor AML | Prevent Fraud | Manage Risk | Report to Regulators |
|-------------|-------------------|-------------|---------------|-------------|---------------------|
| DE-R001 KYCRecord | CRU | R | R | R | R |
| DE-R002 AMLAlert | - | CRU | R | R | R |
| DE-R003 AMLCase | - | CRU | R | R | R |
| DE-R004 SAR | - | CRU | - | R | CRU |
| DE-R005 FraudAlert | - | R | CRU | R | R |
| DE-R006 FraudCase | - | R | CRU | R | R |
| DE-R007 RiskScore | R | CRU | CRU | CRU | R |
| DE-R008 Sanction | CRU | R | R | R | R |
| DE-R009 PEPRecord | CRU | R | R | R | R |
| DE-R010 RegulatoryReport | - | R | R | R | CRU |
| DE-C007 Identification | CRU | R | R | R | R |
| DE-T001 Transaction | R | R | R | R | R |

## 2.6 Operations Functions

| Data Entity | Record in Ledger | Track P&L | Reconcile & Settle | Run Batch Jobs | Manage Partners |
|-------------|------------------|-----------|-------------------|----------------|-----------------|
| DE-T001 Transaction | CRU | R | R | R | - |
| DE-T009 Settlement | CRU | R | CRU | R | R |
| DE-T010 Reconciliation | - | R | CRU | CRU | - |
| DE-A005 AccountBalance | RU | R | R | RU | - |
| DE-A007 AccountStatement | CRU | R | - | CRU | - |
| DE-RF010 GLAccount | R | CRU | R | R | - |
| DE-TR005 NostroAccount | R | R | RU | R | R |
| DE-E001 DomainEvent | C | R | R | R | - |

---

# 3. Application/Data Matrix

## 3.1 Customer Domain Applications

| Data Entity | Customer Service | CRM | Mobile App | Web App | Partner API | KYC Service |
|-------------|------------------|-----|------------|---------|-------------|-------------|
| DE-C001 Customer | CRUD | RU | R | R | R | R |
| DE-C002 Individual | CRUD | RU | R | R | R | CRU |
| DE-C003 Organization | CRUD | RU | R | R | R | CRU |
| DE-C004 CustomerProfile | CRUD | RU | RU | RU | R | - |
| DE-C005 CustomerSegment | R | CRU | R | R | - | - |
| DE-C006 ContactInfo | CRUD | RU | RU | RU | R | R |
| DE-C007 Identification | R | R | R | R | - | CRUD |
| DE-C008 Consent | CRUD | R | RU | RU | - | R |
| DE-C010 Beneficiary | CRUD | R | CRU | CRU | R | - |

## 3.2 Account & Transaction Applications

| Data Entity | Ledger Service | Payment Service | Card Service | Mobile App | Web App | Partner API |
|-------------|----------------|-----------------|--------------|------------|---------|-------------|
| DE-A001 Account | CRUD | R | R | R | R | R |
| DE-A002 CurrentAccount | CRUD | R | R | R | R | R |
| DE-A005 AccountBalance | CRUD | RU | R | R | R | R |
| DE-A006 AccountLimit | CRUD | R | R | R | R | - |
| DE-A007 AccountStatement | CRUD | R | - | R | R | R |
| DE-T001 Transaction | CRUD | CRUD | R | R | R | R |
| DE-T002 Payment | R | CRUD | - | CRU | CRU | CRU |
| DE-T003 Transfer | R | CRUD | - | CRU | CRU | CRU |
| DE-T006 FXTransaction | RU | CRUD | - | CRU | CRU | CRU |
| DE-CD001 Card | R | - | CRUD | R | R | - |
| DE-CD004 CardAuthorization | - | - | CRUD | R | R | - |
| DE-CD005 CardTransaction | R | R | CRUD | R | R | - |

## 3.3 Wealth Applications (NEW)

| Data Entity | Wealth Service | Advisory Portal | Robo Engine | Mobile App | Web App | Reporting |
|-------------|----------------|-----------------|-------------|------------|---------|-----------|
| DE-I001 InvestmentAccount | CRUD | RU | RU | R | R | R |
| DE-I002 Portfolio | CRUD | RU | CRUD | R | R | R |
| DE-I003 Position | CRUD | R | RU | R | R | R |
| DE-I004 Trade | CRUD | CRU | CRU | R | R | R |
| DE-I005 Instrument | R | R | R | R | R | R |
| DE-I006 RiskProfile | CRUD | CRU | CRU | RU | RU | R |
| DE-I007 SuitabilityAssessment | CRUD | CRU | CRU | R | R | R |
| DE-I008 InvestmentAdvice | CRUD | CRU | C | R | R | R |
| DE-I009 PortfolioValuation | CRUD | R | RU | R | R | R |
| DE-I011 RoboAllocation | CRUD | R | CRUD | R | R | R |
| DE-I012 FinancialGoal | CRUD | RU | RU | CRU | CRU | R |

## 3.4 Risk & Compliance Applications

| Data Entity | Risk Service | AML Service | Fraud Service | KYC Service | Regulatory Reporting | Case Mgmt |
|-------------|--------------|-------------|---------------|-------------|---------------------|-----------|
| DE-R001 KYCRecord | R | R | R | CRUD | R | R |
| DE-R002 AMLAlert | R | CRUD | R | - | R | RU |
| DE-R003 AMLCase | R | CRUD | R | - | R | CRUD |
| DE-R004 SAR | R | CRUD | - | - | R | R |
| DE-R005 FraudAlert | R | R | CRUD | - | R | RU |
| DE-R006 FraudCase | R | R | CRUD | - | R | CRUD |
| DE-R007 RiskScore | CRUD | RU | RU | RU | R | R |
| DE-R008 Sanction | R | R | R | CRUD | R | R |
| DE-R010 RegulatoryReport | R | R | R | R | CRUD | - |
| DE-E011 AuditLog | R | R | R | R | R | R |

## 3.5 Treasury Applications

| Data Entity | Treasury Service | Market Data Service | Hedge Engine | Liquidity Mgmt | Reporting |
|-------------|------------------|--------------------|--------------| ---------------|-----------|
| DE-TR001 FXRate | R | CRUD | R | R | R |
| DE-TR002 FXPosition | CRUD | - | RU | R | R |
| DE-TR003 LiquidityPosition | RU | - | R | CRUD | R |
| DE-TR004 HedgeTransaction | CRUD | - | CRUD | R | R |
| DE-TR005 NostroAccount | RU | - | R | RU | R |
| DE-TR006 InterestRateCurve | R | CRUD | R | R | R |
| DE-T006 FXTransaction | CRUD | - | R | R | R |

## 3.6 Analytics & ML Applications

| Data Entity | Data Lake | ML Platform | BI/Tableau | Feature Store | Customer 360 |
|-------------|-----------|-------------|------------|---------------|--------------|
| DE-C001 Customer | R | R | R | R | CRUD |
| DE-C002 Individual | R | R | R | R | CRUD |
| DE-C004 CustomerProfile | R | R | R | R | CRUD |
| DE-A001 Account | R | R | R | R | R |
| DE-A005 AccountBalance | R | R | R | R | R |
| DE-T001 Transaction | R | R | R | CRU | R |
| DE-I002 Portfolio | R | R | R | R | R |
| DE-R007 RiskScore | R | CRU | R | CRU | R |
| DE-E001 DomainEvent | R | R | R | R | R |

## 3.7 Data Platform Applications

| Data Entity | Event Store | Data Catalog | Quality Monitor | Lineage Tracker | MDM |
|-------------|-------------|--------------|-----------------|-----------------|-----|
| DE-E001 DomainEvent | CRUD | R | R | R | - |
| DE-E002 CustomerEvent | CRUD | R | R | R | - |
| DE-E003 AccountEvent | CRUD | R | R | R | - |
| DE-E004 TransactionEvent | CRUD | R | R | R | - |
| DE-RF001 Currency | R | R | R | R | CRUD |
| DE-RF002 Country | R | R | R | R | CRUD |
| DE-RF004 ProductCatalog | R | R | R | R | CRUD |
| All Entities (Metadata) | - | CRUD | R | CRUD | R |

---

# 4. Data Access Summary

## 4.1 CRUD Operations by Domain

| Domain | Total Entities | Create | Read | Update | Delete |
|--------|----------------|--------|------|--------|--------|
| Customer | 10 | Customer Service | All apps | Customer Service, Apps | Customer Service |
| Account | 10 | Ledger Service | All apps | Ledger, Payment | Ledger Service |
| Transaction | 10 | Payment Service | All apps | Payment Service | Archive only |
| Card | 10 | Card Service | All apps | Card Service | Card Service |
| Investment | 12 | Wealth Service | All apps | Wealth, Robo | Wealth Service |
| Risk | 12 | KYC, AML, Fraud | All apps | Risk Services | Archive only |
| Treasury | 8 | Treasury Service | All apps | Treasury Service | Archive only |
| Reference | 10 | MDM | All apps | MDM | MDM |
| Event | 7 | All Services | All apps | Immutable | Never |

## 4.2 Data Ownership Summary

| Owner | Entities Owned | Primary Applications |
|-------|----------------|---------------------|
| Head of Retail | 8 | Customer Service, Mobile, Web |
| Head of Operations | 10 | Ledger Service |
| Head of Payments | 8 | Payment Service |
| Head of Cards | 10 | Card Service |
| Head of Wealth | 12 | Wealth Service, Advisory Portal |
| Head of Compliance | 6 | KYC Service, Regulatory Reporting |
| MLRO | 4 | AML Service |
| Head of Fraud | 2 | Fraud Service |
| CRO | 3 | Risk Service |
| Head of Treasury | 8 | Treasury Service |
| CISO | 2 | Security Services |
| Data Governance | 10 | MDM, Data Catalog |
| CTO | 7 | Event Store, Data Platform |

---

**Document End**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Data Architecture Team | CTO, CDO |
| [Date] | [Date] | [Date] |
