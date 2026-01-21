# KVBank

## Phase C: Data Architecture

### Part 3: Diagrams

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Phase C: Data Architecture - Part 3 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Conceptual Data Diagram
2. Logical Data Diagram
3. Data Dissemination Diagram
4. Data Security Diagram
5. Data Migration Diagram
6. Data Lifecycle Diagram

---

# 1. Conceptual Data Diagram

## 1.1 Enterprise Conceptual Data Model

The conceptual data diagram shows the high-level data domains and their relationships without technical implementation details.

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK CONCEPTUAL DATA MODEL                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│                              ┌─────────────────┐                                 │
│                              │    CUSTOMER     │                                 │
│                              │                 │                                 │
│                              │ • Individual    │                                 │
│                              │ • Organization  │                                 │
│                              │ • Profile       │                                 │
│                              │ • Consent       │                                 │
│                              └────────┬────────┘                                 │
│                                       │                                          │
│                    ┌──────────────────┼──────────────────┐                      │
│                    │ owns             │ owns             │ owns                  │
│                    ▼                  ▼                  ▼                       │
│  ┌─────────────────────┐  ┌─────────────────┐  ┌─────────────────────┐         │
│  │      ACCOUNT        │  │      CARD       │  │    INVESTMENT       │         │
│  │                     │  │                 │  │     ACCOUNT         │         │
│  │ • Current           │  │ • Physical      │  │                     │         │
│  │ • Savings           │  │ • Virtual       │  │ • Portfolio         │         │
│  │ • Balance           │  │ • Limit         │  │ • Position          │         │
│  │ • Limit             │  │ • Control       │  │ • Risk Profile      │         │
│  └──────────┬──────────┘  └────────┬────────┘  └──────────┬──────────┘         │
│             │                      │                      │                     │
│             │ generates            │ generates            │ generates           │
│             ▼                      ▼                      ▼                     │
│  ┌─────────────────────┐  ┌─────────────────┐  ┌─────────────────────┐         │
│  │    TRANSACTION      │  │ CARD TRANSACTION│  │       TRADE         │         │
│  │                     │  │                 │  │                     │         │
│  │ • Payment           │  │ • Authorization │  │ • Order             │         │
│  │ • Transfer          │  │ • Settlement    │  │ • Execution         │         │
│  │ • Direct Debit      │  │ • Dispute       │  │ • Settlement        │         │
│  │ • FX                │  │                 │  │                     │         │
│  └──────────┬──────────┘  └─────────────────┘  └──────────┬──────────┘         │
│             │                                             │                     │
│             │ involves                                    │ involves            │
│             ▼                                             ▼                     │
│  ┌─────────────────────┐                      ┌─────────────────────┐          │
│  │     BENEFICIARY     │                      │    INSTRUMENT       │          │
│  │                     │                      │                     │          │
│  │ • External Account  │                      │ • Equity            │          │
│  │ • Payment Details   │                      │ • Fund              │          │
│  └─────────────────────┘                      │ • Bond              │          │
│                                               └─────────────────────┘          │
│                                                                                  │
│  ┌─────────────────────┐  ┌─────────────────┐  ┌─────────────────────┐         │
│  │       RISK          │  │    TREASURY     │  │    REFERENCE        │         │
│  │                     │  │                 │  │                     │         │
│  │ • KYC Record        │  │ • FX Rate       │  │ • Currency          │         │
│  │ • AML Alert/Case    │  │ • FX Position   │  │ • Country           │         │
│  │ • Fraud Alert/Case  │  │ • Liquidity     │  │ • Product           │         │
│  │ • Risk Score        │  │ • Hedge         │  │ • Fee Schedule      │         │
│  │ • Sanction          │  │ • Nostro        │  │ • Bank Directory    │         │
│  └─────────────────────┘  └─────────────────┘  └─────────────────────┘         │
│                                                                                  │
│  ════════════════════════════════════════════════════════════════════════════   │
│                              EVENT STORE                                         │
│  ────────────────────────────────────────────────────────────────────────────   │
│  │ CustomerEvent │ AccountEvent │ TransactionEvent │ TradeEvent │ RiskEvent │  │
│  ════════════════════════════════════════════════════════════════════════════   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 1.2 Domain Relationships Summary

| Source Domain | Relationship | Target Domain | Cardinality |
|---------------|--------------|---------------|-------------|
| Customer | owns | Account | 1:N |
| Customer | owns | Card | 1:N |
| Customer | owns | Investment Account | 1:N |
| Customer | has | Risk Profile | 1:1 |
| Customer | has | KYC Record | 1:1 |
| Account | generates | Transaction | 1:N |
| Card | generates | Card Transaction | 1:N |
| Investment Account | contains | Portfolio | 1:N |
| Portfolio | contains | Position | 1:N |
| Portfolio | generates | Trade | 1:N |
| Trade | involves | Instrument | N:1 |
| Transaction | references | Beneficiary | N:1 |
| Transaction | uses | FX Rate | N:1 |
| All Domains | emit | Event | 1:N |

---

# 2. Logical Data Diagram

## 2.1 Customer Domain Logical Model

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    CUSTOMER DOMAIN - LOGICAL DATA MODEL                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                              CUSTOMER                                      │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  customer_id          UUID           NOT NULL                          │  │
│  │     customer_type        ENUM           NOT NULL  (INDIVIDUAL,ORGANIZATION)│  │
│  │     status               ENUM           NOT NULL  (ACTIVE,SUSPENDED,CLOSED)│  │
│  │     created_at           TIMESTAMP      NOT NULL                          │  │
│  │     updated_at           TIMESTAMP      NOT NULL                          │  │
│  │     version              INTEGER        NOT NULL                          │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│           │                                       │                             │
│           │ 1:1                                   │ 1:1                         │
│           ▼                                       ▼                             │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │      INDIVIDUAL         │          │     ORGANIZATION        │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  individual_id  UUID │          │ PK  organization_id UUID│              │
│  │ FK  customer_id    UUID │          │ FK  customer_id    UUID │              │
│  │     first_name   VARCHAR│          │     legal_name   VARCHAR│              │
│  │     last_name    VARCHAR│          │     trading_name VARCHAR│              │
│  │     date_of_birth  DATE │          │     registration_no     │              │
│  │     nationality  VARCHAR│          │     incorporation_date  │              │
│  │     tax_id       VARCHAR│          │     tax_id       VARCHAR│              │
│  └─────────────────────────┘          │     industry     VARCHAR│              │
│                                       └─────────────────────────┘              │
│                                                                                  │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │     CONTACT_INFO        │          │    IDENTIFICATION       │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  contact_id     UUID │          │ PK  identification_id   │              │
│  │ FK  customer_id    UUID │          │ FK  customer_id    UUID │              │
│  │     type          ENUM  │          │     id_type        ENUM │              │
│  │     value       VARCHAR │          │     id_number    VARCHAR│              │
│  │     is_primary  BOOLEAN │          │     issuing_country     │              │
│  │     verified    BOOLEAN │          │     issue_date     DATE │              │
│  │     verified_at TIMESTAMP│         │     expiry_date    DATE │              │
│  └─────────────────────────┘          │     verified     BOOLEAN│              │
│                                       │     document_url VARCHAR│              │
│  ┌─────────────────────────┐          └─────────────────────────┘              │
│  │       CONSENT           │                                                    │
│  ├─────────────────────────┤          ┌─────────────────────────┐              │
│  │ PK  consent_id     UUID │          │   CUSTOMER_PROFILE      │              │
│  │ FK  customer_id    UUID │          ├─────────────────────────┤              │
│  │     consent_type   ENUM │          │ PK  profile_id     UUID │              │
│  │     granted     BOOLEAN │          │ FK  customer_id    UUID │              │
│  │     granted_at TIMESTAMP│          │     language     VARCHAR│              │
│  │     expires_at TIMESTAMP│          │     timezone     VARCHAR│              │
│  │     source      VARCHAR │          │     preferences   JSONB │              │
│  └─────────────────────────┘          │     segment      VARCHAR│              │
│                                       │     risk_category  ENUM │              │
│                                       └─────────────────────────┘              │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 2.2 Account & Transaction Domain Logical Model

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    ACCOUNT & TRANSACTION - LOGICAL DATA MODEL                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                              ACCOUNT                                       │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  account_id           UUID           NOT NULL                          │  │
│  │ FK  customer_id          UUID           NOT NULL                          │  │
│  │     account_number       VARCHAR(34)    NOT NULL  UNIQUE                  │  │
│  │     iban                 VARCHAR(34)    NULL                              │  │
│  │     account_type         ENUM           NOT NULL  (CURRENT,SAVINGS,...)   │  │
│  │     currency             VARCHAR(3)     NOT NULL                          │  │
│  │     status               ENUM           NOT NULL                          │  │
│  │     opened_at            TIMESTAMP      NOT NULL                          │  │
│  │     closed_at            TIMESTAMP      NULL                              │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│           │                                                                     │
│           │ 1:1                                                                 │
│           ▼                                                                     │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                          ACCOUNT_BALANCE                                   │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  balance_id           UUID           NOT NULL                          │  │
│  │ FK  account_id           UUID           NOT NULL                          │  │
│  │     current_balance      DECIMAL(18,2)  NOT NULL                          │  │
│  │     available_balance    DECIMAL(18,2)  NOT NULL                          │  │
│  │     pending_in           DECIMAL(18,2)  NOT NULL  DEFAULT 0               │  │
│  │     pending_out          DECIMAL(18,2)  NOT NULL  DEFAULT 0               │  │
│  │     updated_at           TIMESTAMP      NOT NULL                          │  │
│  │     version              INTEGER        NOT NULL                          │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                            TRANSACTION                                     │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  transaction_id       UUID           NOT NULL                          │  │
│  │ FK  account_id           UUID           NOT NULL                          │  │
│  │     transaction_type     ENUM           NOT NULL  (PAYMENT,TRANSFER,...)  │  │
│  │     direction            ENUM           NOT NULL  (DEBIT,CREDIT)          │  │
│  │     amount               DECIMAL(18,2)  NOT NULL                          │  │
│  │     currency             VARCHAR(3)     NOT NULL                          │  │
│  │     status               ENUM           NOT NULL                          │  │
│  │     reference            VARCHAR(35)    NOT NULL                          │  │
│  │     description          VARCHAR(140)   NULL                              │  │
│  │     value_date           DATE           NOT NULL                          │  │
│  │     booking_date         DATE           NOT NULL                          │  │
│  │     created_at           TIMESTAMP      NOT NULL                          │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │       PAYMENT           │          │     FX_TRANSACTION      │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  payment_id     UUID │          │ PK  fx_transaction_id   │              │
│  │ FK  transaction_id UUID │          │ FK  transaction_id UUID │              │
│  │ FK  beneficiary_id UUID │          │     sell_currency  VARCHAR│            │
│  │     payment_rail   ENUM │          │     sell_amount   DECIMAL│             │
│  │     end_to_end_id VARCHAR│         │     buy_currency VARCHAR │             │
│  │     instruction_id      │          │     buy_amount   DECIMAL │             │
│  │     charges       DECIMAL│         │     exchange_rate DECIMAL│             │
│  └─────────────────────────┘          │     rate_timestamp       │             │
│                                       └─────────────────────────┘              │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 2.3 Investment/Wealth Domain Logical Model

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    INVESTMENT/WEALTH - LOGICAL DATA MODEL                        │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                        INVESTMENT_ACCOUNT                                  │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  investment_account_id UUID         NOT NULL                           │  │
│  │ FK  customer_id           UUID         NOT NULL                           │  │
│  │     account_type          ENUM         NOT NULL  (GIA,ISA,SIPP)           │  │
│  │     status                ENUM         NOT NULL                           │  │
│  │     opened_at             TIMESTAMP    NOT NULL                           │  │
│  │     tax_wrapper           VARCHAR      NULL                               │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│           │                                       │                             │
│           │ 1:N                                   │ 1:1                         │
│           ▼                                       ▼                             │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │      PORTFOLIO          │          │     RISK_PROFILE        │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  portfolio_id   UUID │          │ PK  risk_profile_id UUID│              │
│  │ FK  investment_acc_id   │          │ FK  customer_id    UUID │              │
│  │     name        VARCHAR │          │     risk_tolerance  ENUM│              │
│  │     strategy       ENUM │          │     investment_horizon  │              │
│  │     benchmark   VARCHAR │          │     experience_level    │              │
│  │     inception_date DATE │          │     income_source       │              │
│  │     is_robo     BOOLEAN │          │     net_worth_range     │              │
│  │     target_allocation   │          │     assessed_at TIMESTAMP│             │
│  └──────────┬──────────────┘          │     valid_until    DATE │              │
│             │                         └─────────────────────────┘              │
│             │ 1:N                                                               │
│             ▼                                                                   │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │       POSITION          │          │     INSTRUMENT          │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  position_id    UUID │          │ PK  instrument_id  UUID │              │
│  │ FK  portfolio_id   UUID │◄─────────│     isin        VARCHAR │              │
│  │ FK  instrument_id  UUID │          │     symbol      VARCHAR │              │
│  │     quantity    DECIMAL │          │     name        VARCHAR │              │
│  │     avg_cost    DECIMAL │          │     asset_class    ENUM │              │
│  │     market_value DECIMAL│          │     currency    VARCHAR │              │
│  │     unrealized_pnl      │          │     exchange    VARCHAR │              │
│  │     weight_pct  DECIMAL │          │     is_active   BOOLEAN │              │
│  │     updated_at TIMESTAMP│          └─────────────────────────┘              │
│  └─────────────────────────┘                                                    │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                              TRADE                                         │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │ PK  trade_id             UUID           NOT NULL                          │  │
│  │ FK  portfolio_id         UUID           NOT NULL                          │  │
│  │ FK  instrument_id        UUID           NOT NULL                          │  │
│  │     trade_type           ENUM           NOT NULL  (BUY,SELL)              │  │
│  │     quantity             DECIMAL(18,6)  NOT NULL                          │  │
│  │     price                DECIMAL(18,6)  NOT NULL                          │  │
│  │     currency             VARCHAR(3)     NOT NULL                          │  │
│  │     gross_amount         DECIMAL(18,2)  NOT NULL                          │  │
│  │     fees                 DECIMAL(18,2)  NOT NULL                          │  │
│  │     net_amount           DECIMAL(18,2)  NOT NULL                          │  │
│  │     status               ENUM           NOT NULL                          │  │
│  │     trade_date           DATE           NOT NULL                          │  │
│  │     settlement_date      DATE           NOT NULL                          │  │
│  │     executed_at          TIMESTAMP      NULL                              │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌─────────────────────────┐          ┌─────────────────────────┐              │
│  │   INVESTMENT_ADVICE     │          │    FINANCIAL_GOAL       │              │
│  ├─────────────────────────┤          ├─────────────────────────┤              │
│  │ PK  advice_id      UUID │          │ PK  goal_id        UUID │              │
│  │ FK  customer_id    UUID │          │ FK  customer_id    UUID │              │
│  │ FK  advisor_id     UUID │          │     goal_type       ENUM│              │
│  │     advice_type    ENUM │          │     target_amount DECIMAL│             │
│  │     recommendation TEXT │          │     target_date     DATE│              │
│  │     rationale      TEXT │          │     current_amount      │              │
│  │     suitability_check   │          │     monthly_contribution│              │
│  │     provided_at TIMESTAMP│         │     priority        ENUM│              │
│  │     accepted    BOOLEAN │          │     status          ENUM│              │
│  └─────────────────────────┘          └─────────────────────────┘              │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

# 3. Data Dissemination Diagram

## 3.1 Real-Time Data Flows (Event Streaming)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA DISSEMINATION - REAL-TIME FLOWS                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  DATA PRODUCERS                                                                  │
│  ══════════════                                                                  │
│                                                                                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐              │
│  │ Customer │ │ Payment  │ │   Card   │ │  Wealth  │ │   Risk   │              │
│  │ Service  │ │ Service  │ │ Service  │ │ Service  │ │ Service  │              │
│  └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘              │
│       │            │            │            │            │                     │
│       │ Events     │ Events     │ Events     │ Events     │ Events              │
│       ▼            ▼            ▼            ▼            ▼                     │
│  ═════════════════════════════════════════════════════════════════════════════  │
│  │                        APACHE KAFKA CLUSTER                               │  │
│  │  ┌────────────────┐ ┌────────────────┐ ┌────────────────┐                │  │
│  │  │ customer.events│ │ payment.events │ │  card.events   │                │  │
│  │  │  • Created     │ │  • Initiated   │ │  • Issued      │                │  │
│  │  │  • Updated     │ │  • Completed   │ │  • Authorized  │                │  │
│  │  │  • Verified    │ │  • Failed      │ │  • Declined    │                │  │
│  │  └────────────────┘ └────────────────┘ └────────────────┘                │  │
│  │  ┌────────────────┐ ┌────────────────┐ ┌────────────────┐                │  │
│  │  │ wealth.events  │ │  risk.events   │ │ market.events  │                │  │
│  │  │  • Trade       │ │  • Alert       │ │  • PriceUpdate │                │  │
│  │  │  • Rebalance   │ │  • Score       │ │  • RateChange  │                │  │
│  │  │  • Advice      │ │  • Case        │ │                │                │  │
│  │  └────────────────┘ └────────────────┘ └────────────────┘                │  │
│  ═════════════════════════════════════════════════════════════════════════════  │
│       │            │            │            │            │                     │
│       ▼            ▼            ▼            ▼            ▼                     │
│  DATA CONSUMERS                                                                  │
│  ══════════════                                                                  │
│                                                                                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐              │
│  │  Event   │ │   Data   │ │  Real-   │ │  Notifi- │ │   Fraud  │              │
│  │  Store   │ │   Lake   │ │  time    │ │  cation  │ │    ML    │              │
│  │(Persist) │ │(Analytics)│ │  Search  │ │ Service  │ │  Engine  │              │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────┘              │
│                                                                                  │
│  LATENCY TARGETS                                                                 │
│  ───────────────                                                                 │
│  │ Flow                        │ Latency Target │ SLA    │                      │
│  │─────────────────────────────│────────────────│────────│                      │
│  │ Producer → Kafka            │ < 10ms         │ P99    │                      │
│  │ Kafka → Event Store         │ < 50ms         │ P99    │                      │
│  │ Kafka → Data Lake           │ < 5 min        │ P95    │                      │
│  │ Kafka → Notification        │ < 100ms        │ P99    │                      │
│  │ Kafka → Fraud ML            │ < 50ms         │ P99    │                      │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 3.2 Batch Data Flows

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA DISSEMINATION - BATCH FLOWS                              │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                          DATA LAKE (S3 + Delta Lake)                     │   │
│  │                                                                          │   │
│  │  ┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐  │   │
│  │  │  RAW ZONE  │───▶│  CURATED   │───▶│  FEATURE   │───▶│ ANALYTICS  │  │   │
│  │  │            │    │   ZONE     │    │   ZONE     │    │    ZONE    │  │   │
│  │  │ • Events   │    │ • Cleaned  │    │ • ML Ready │    │ • Aggregates│ │   │
│  │  │ • Snapshots│    │ • Enriched │    │ • Features │    │ • KPIs     │  │   │
│  │  │ • External │    │ • Validated│    │ • Vectors  │    │ • Reports  │  │   │
│  │  └────────────┘    └────────────┘    └────────────┘    └────────────┘  │   │
│  │                                                                          │   │
│  │  Processing: Apache Spark + dbt                                          │   │
│  │  Schedule: Hourly (curated), Daily (features), Realtime (analytics)     │   │
│  │                                                                          │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                             │                                                   │
│       ┌─────────────────────┼─────────────────────┐                            │
│       │                     │                     │                            │
│       ▼                     ▼                     ▼                            │
│  ┌──────────┐         ┌──────────┐         ┌──────────┐                       │
│  │    BI    │         │    ML    │         │Regulatory│                       │
│  │ Tableau  │         │ Platform │         │ Reporting│                       │
│  │          │         │SageMaker │         │          │                       │
│  │ • Dashbd │         │ • Train  │         │ • FCA    │                       │
│  │ • Reports│         │ • Serve  │         │ • PRA    │                       │
│  │ • Ad-hoc │         │ • Monitor│         │ • ECB    │                       │
│  └──────────┘         └──────────┘         └──────────┘                       │
│                                                                                 │
│  BATCH SCHEDULES                                                                │
│  ───────────────                                                                │
│  │ Pipeline                  │ Schedule      │ Data Volume  │                  │
│  │───────────────────────────│───────────────│──────────────│                  │
│  │ Raw → Curated             │ Hourly        │ ~50 GB/day   │                  │
│  │ Curated → Features        │ Daily 02:00   │ ~10 GB       │                  │
│  │ Features → ML Training    │ Weekly        │ ~100 GB      │                  │
│  │ Regulatory Extract        │ Daily 06:00   │ ~5 GB        │                  │
│  │ BI Refresh                │ Hourly        │ ~20 GB       │                  │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 3.3 Customer 360 Data Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    CUSTOMER 360 - DATA AGGREGATION FLOW                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  SOURCE SYSTEMS                                                                  │
│  ══════════════                                                                  │
│                                                                                  │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐      │
│  │Customer │ │ Account │ │  Card   │ │ Wealth  │ │  Risk   │ │  CRM    │      │
│  │ Service │ │ Service │ │ Service │ │ Service │ │ Service │ │         │      │
│  └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘      │
│       │           │           │           │           │           │            │
│       │ CDC       │ CDC       │ CDC       │ CDC       │ CDC       │ API        │
│       ▼           ▼           ▼           ▼           ▼           ▼            │
│  ═════════════════════════════════════════════════════════════════════════════  │
│  │                     CUSTOMER 360 PLATFORM                                 │  │
│  │                                                                           │  │
│  │  ┌─────────────────────────────────────────────────────────────────────┐ │  │
│  │  │                      ENTITY RESOLUTION                              │ │  │
│  │  │  • Match customer records across systems                            │ │  │
│  │  │  • Deduplicate and merge                                            │ │  │
│  │  │  • Create Golden Record                                             │ │  │
│  │  └─────────────────────────────────────────────────────────────────────┘ │  │
│  │                               │                                          │  │
│  │                               ▼                                          │  │
│  │  ┌─────────────────────────────────────────────────────────────────────┐ │  │
│  │  │                     UNIFIED CUSTOMER VIEW                           │ │  │
│  │  │                                                                     │ │  │
│  │  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │ │  │
│  │  │  │ Profile  │ │ Products │ │ Transact │ │  Wealth  │ │   Risk   │ │ │  │
│  │  │  │          │ │          │ │  History │ │ Holdings │ │  Score   │ │ │  │
│  │  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │ │  │
│  │  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐              │ │  │
│  │  │  │Engagement│ │Preferences│ │ Lifetime │ │ Next Best│              │ │  │
│  │  │  │ Metrics  │ │          │ │  Value   │ │  Action  │              │ │  │
│  │  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘              │ │  │
│  │  └─────────────────────────────────────────────────────────────────────┘ │  │
│  ═════════════════════════════════════════════════════════════════════════════  │
│                               │                                                 │
│       ┌───────────────────────┼───────────────────────┐                        │
│       │                       │                       │                        │
│       ▼                       ▼                       ▼                        │
│  ┌──────────┐           ┌──────────┐           ┌──────────┐                   │
│  │ Customer │           │    ML    │           │   CRM    │                   │
│  │ Service  │           │ Features │           │  Sync    │                   │
│  │   API    │           │          │           │          │                   │
│  └──────────┘           └──────────┘           └──────────┘                   │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

# 4. Data Security Diagram

## 4.1 Data Security Architecture

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA SECURITY ARCHITECTURE                                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  SECURITY LAYERS                                                                 │
│  ═══════════════                                                                 │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ LAYER 1: PERIMETER SECURITY                                              │   │
│  │ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐        │   │
│  │ │   WAF       │ │   DDoS      │ │  API        │ │  Network    │        │   │
│  │ │ Protection  │ │ Protection  │ │  Gateway    │ │  Firewall   │        │   │
│  │ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘        │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                       │                                         │
│                                       ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ LAYER 2: ACCESS CONTROL                                                  │   │
│  │ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐        │   │
│  │ │   IAM       │ │   OAuth     │ │   RBAC      │ │   ABAC      │        │   │
│  │ │ (Identity)  │ │   2.0       │ │  (Roles)    │ │(Attributes) │        │   │
│  │ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘        │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                       │                                         │
│                                       ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ LAYER 3: DATA PROTECTION                                                 │   │
│  │ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐        │   │
│  │ │ Encryption  │ │ Encryption  │ │   Data      │ │   PII       │        │   │
│  │ │ at Rest     │ │ in Transit  │ │  Masking    │ │Tokenization │        │   │
│  │ │ (AES-256)   │ │  (TLS 1.3)  │ │             │ │             │        │   │
│  │ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘        │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                       │                                         │
│                                       ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ LAYER 4: MONITORING & AUDIT                                              │   │
│  │ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐        │   │
│  │ │   Audit     │ │   SIEM      │ │   DLP       │ │  Anomaly    │        │   │
│  │ │   Logging   │ │ (Security)  │ │(Data Loss)  │ │ Detection   │        │   │
│  │ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘        │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 4.2 Data Classification & Controls

| Classification | Description | Examples | Controls |
|----------------|-------------|----------|----------|
| **PII - Critical** | Highly sensitive PII | ID documents, PIN, biometrics | Encryption, tokenization, strict access, full audit |
| **PII - High** | Sensitive personal data | Name, DOB, address, contact | Encryption, masking, RBAC, audit |
| **PII - Medium** | Less sensitive PII | Preferences, segment | Encryption, RBAC |
| **Confidential** | Business sensitive | Balances, transactions | Encryption, RBAC |
| **Internal** | Internal use only | Reports, metrics | RBAC |
| **Public** | Non-sensitive | Currency codes, rates | None |

## 4.3 Access Control Matrix

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA ACCESS CONTROL MATRIX                                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  │ Data Classification │ Customer │ CS Agent │ Advisor │ Analyst │ Admin │     │
│  │─────────────────────│──────────│──────────│─────────│─────────│───────│     │
│  │ PII - Critical      │ Own only │ Masked   │ Masked  │   No    │ Audit │     │
│  │ PII - High          │ Own only │ Full     │ Full    │ Aggreg  │ Full  │     │
│  │ PII - Medium        │ Own only │ Full     │ Full    │ Aggreg  │ Full  │     │
│  │ Confidential        │ Own only │ Full     │ Own Cust│ Aggreg  │ Full  │     │
│  │ Internal            │    No    │ Limited  │ Limited │ Full    │ Full  │     │
│  │ Public              │   Yes    │ Yes      │ Yes     │ Yes     │ Yes   │     │
│                                                                                  │
│  ACCESS RULES                                                                    │
│  ════════════                                                                    │
│  • "Own only" = Customer can only see their own data                            │
│  • "Masked" = PII fields are masked (e.g., ****1234)                            │
│  • "Aggreg" = Aggregated/anonymized data only                                   │
│  • "Own Cust" = Advisor sees only assigned customers                            │
│  • All PII access is logged for audit                                           │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 4.4 Encryption Standards

| Data State | Standard | Key Management | Rotation |
|------------|----------|----------------|----------|
| At Rest (Database) | AES-256 | AWS KMS | Annual |
| At Rest (Data Lake) | AES-256 | AWS KMS | Annual |
| In Transit (Internal) | TLS 1.3 | Certificate Manager | 90 days |
| In Transit (External) | TLS 1.3 | Certificate Manager | 90 days |
| Backup | AES-256 | AWS KMS (separate) | Annual |
| PII Fields | Field-level AES-256 | Application KMS | Annual |

---

# 5. Data Migration Diagram

## 5.1 Migration Strategy Overview

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA MIGRATION STRATEGY                                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  MIGRATION APPROACH: Phased with Parallel Run                                    │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ PHASE 1: Foundation (Months 1-6)                                         │   │
│  │                                                                          │   │
│  │  SOURCE                         TARGET                                   │   │
│  │  ┌──────────┐                  ┌──────────┐                             │   │
│  │  │   Core   │ ─── Extract ───▶ │  Event   │                             │   │
│  │  │ Banking  │ ─── Transform ──▶│  Store   │                             │   │
│  │  │   DB     │ ─── Load ──────▶ │          │                             │   │
│  │  └──────────┘                  └──────────┘                             │   │
│  │                                                                          │   │
│  │  ┌──────────┐                  ┌──────────┐                             │   │
│  │  │   CRM    │ ─── CDC ───────▶ │ Customer │                             │   │
│  │  │Salesforce│                  │   360    │                             │   │
│  │  └──────────┘                  └──────────┘                             │   │
│  │                                                                          │   │
│  │  Data Volume: ~3 TB    Duration: 6 months                               │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ PHASE 2: Data Lake (Months 4-9)                                          │   │
│  │                                                                          │   │
│  │  SOURCE                         TARGET                                   │   │
│  │  ┌──────────┐                  ┌──────────┐                             │   │
│  │  │ Redshift │ ─── Export ────▶ │   Data   │                             │   │
│  │  │    DW    │                  │   Lake   │                             │   │
│  │  └──────────┘                  │ (Delta)  │                             │   │
│  │                                └──────────┘                             │   │
│  │  ┌──────────┐                       │                                   │   │
│  │  │ Event    │ ─── Stream ──────────▶│                                   │   │
│  │  │ Store    │                                                           │   │
│  │  └──────────┘                                                           │   │
│  │                                                                          │   │
│  │  Data Volume: ~2 TB    Duration: 6 months                               │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ PHASE 3: Domain Services (Months 7-15)                                   │   │
│  │                                                                          │   │
│  │  Migrate each domain to dedicated database:                              │   │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐           │   │
│  │  │Customer │ │ Account │ │ Payment │ │  Card   │ │  Risk   │           │   │
│  │  │   DB    │ │   DB    │ │   DB    │ │   DB    │ │   DB    │           │   │
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘           │   │
│  │                                                                          │   │
│  │  Approach: Strangler Fig pattern with dual-write                        │   │
│  │  Data Volume: ~4 TB total   Duration: 9 months                          │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 5.2 Migration Workflow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA MIGRATION WORKFLOW                                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐      │
│  │ EXTRACT │───▶│TRANSFORM│───▶│VALIDATE │───▶│  LOAD   │───▶│ VERIFY  │      │
│  └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘      │
│       │              │              │              │              │            │
│       ▼              ▼              ▼              ▼              ▼            │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐      │
│  │• Full   │    │• Schema │    │• Row    │    │• Bulk   │    │• Count  │      │
│  │  dump   │    │  mapping│    │  counts │    │  insert │    │  match  │      │
│  │• CDC    │    │• Data   │    │• Quality│    │• Upsert │    │• Hash   │      │
│  │• API    │    │  cleanse│    │  rules  │    │• Stream │    │  verify │      │
│  │         │    │• Enrich │    │• Null   │    │         │    │• Sample │      │
│  │         │    │         │    │  checks │    │         │    │  audit  │      │
│  └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘      │
│                                                                                  │
│  ROLLBACK STRATEGY                                                               │
│  ═════════════════                                                               │
│  • All migrations are reversible within 72 hours                                │
│  • Dual-write enabled during transition                                         │
│  • Source systems remain read-only backup                                       │
│  • Point-in-time recovery available                                             │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 5.3 Migration Schedule

| Phase | Domain | Source | Target | Volume | Start | End | Status |
|-------|--------|--------|--------|--------|-------|-----|--------|
| 1.1 | Customer | CRM, Core | Customer 360 | 500 GB | M1 | M4 | Planned |
| 1.2 | Account | Core Banking | Event Store | 2 TB | M2 | M5 | Planned |
| 1.3 | Transaction | Core Banking | Event Store | 2 TB | M3 | M6 | Planned |
| 2.1 | Analytics | Redshift | Data Lake | 1 TB | M4 | M7 | Planned |
| 2.2 | Historical | Archives | Data Lake | 1 TB | M5 | M9 | Planned |
| 3.1 | Customer | Monolith | Customer DB | 500 GB | M7 | M10 | Planned |
| 3.2 | Payment | Monolith | Payment DB | 1 TB | M9 | M12 | Planned |
| 3.3 | Card | External | Card DB | 300 GB | M10 | M13 | Planned |
| 3.4 | Risk | Legacy | Risk DB | 100 GB | M12 | M15 | Planned |

---

# 6. Data Lifecycle Diagram

## 6.1 Data Lifecycle Stages

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DATA LIFECYCLE MANAGEMENT                                     │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐      │
│  │ CREATE  │───▶│  STORE  │───▶│   USE   │───▶│ ARCHIVE │───▶│ DESTROY │      │
│  └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘      │
│       │              │              │              │              │            │
│       ▼              ▼              ▼              ▼              ▼            │
│  ┌─────────────────────────────────────────────────────────────────────────┐  │
│  │                                                                          │  │
│  │  CREATE                                                                  │  │
│  │  • Validate at source                                                    │  │
│  │  • Apply schema                                                          │  │
│  │  • Classify (PII, Confidential, etc.)                                   │  │
│  │  • Assign owner                                                          │  │
│  │  • Generate audit event                                                  │  │
│  │                                                                          │  │
│  │  STORE                                                                   │  │
│  │  • Encrypt at rest                                                       │  │
│  │  • Apply retention policy                                                │  │
│  │  • Replicate (DR)                                                        │  │
│  │  • Index for search                                                      │  │
│  │  • Backup                                                                │  │
│  │                                                                          │  │
│  │  USE                                                                     │  │
│  │  • Enforce access control                                                │  │
│  │  • Log all access (PII)                                                  │  │
│  │  • Apply masking rules                                                   │  │
│  │  • Track lineage                                                         │  │
│  │  • Monitor quality                                                       │  │
│  │                                                                          │  │
│  │  ARCHIVE                                                                 │  │
│  │  • Move to cold storage                                                  │  │
│  │  • Compress                                                              │  │
│  │  • Maintain searchability                                                │  │
│  │  • Reduce access                                                         │  │
│  │                                                                          │  │
│  │  DESTROY                                                                 │  │
│  │  • Verify retention complete                                             │  │
│  │  • Secure deletion                                                       │  │
│  │  • Audit trail                                                           │  │
│  │  • Certificate of destruction                                            │  │
│  │                                                                          │  │
│  └─────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 6.2 Retention Policies

| Data Category | Active Period | Archive Period | Total Retention | Destruction |
|---------------|---------------|----------------|-----------------|-------------|
| Customer PII | Active relationship | 7 years post-closure | 7 years post-closure | Secure delete |
| Transaction Data | 2 years | 5 years | 7 years | Secure delete |
| Card Data | Active + 1 year | 6 years | 7 years post-expiry | Secure delete |
| KYC Documents | Active relationship | 7 years post-closure | 7 years post-closure | Secure delete |
| AML/Fraud Cases | 5 years | 2 years | 7 years | Secure delete |
| Investment Records | Active | 7 years post-closure | 7 years | Secure delete |
| Audit Logs | 1 year | 6 years | 7 years | Secure delete |
| System Logs | 90 days | None | 90 days | Auto-delete |
| Analytics (Aggregated) | Permanent | N/A | Permanent | N/A |
| Reference Data | Permanent | N/A | Permanent | N/A |

## 6.3 Data Lifecycle by Domain

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    CUSTOMER DATA LIFECYCLE                                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  TIMELINE                                                                        │
│  ────────                                                                        │
│                                                                                  │
│  Onboarding        Active Customer         Closure    Retention    Destruction  │
│      │                   │                    │           │             │       │
│      ▼                   ▼                    ▼           ▼             ▼       │
│  ┌───────┐          ┌───────┐           ┌───────┐    ┌───────┐    ┌───────┐   │
│  │ Day 0 │──────────│Active │───────────│Closure│────│Archive│────│Destroy│   │
│  │       │          │ Usage │           │       │    │       │    │       │   │
│  │Create │          │Update │           │Freeze │    │ Cold  │    │Secure │   │
│  │Profile│          │Transact│          │Retain │    │Storage│    │Delete │   │
│  └───────┘          └───────┘           └───────┘    └───────┘    └───────┘   │
│      │                   │                    │           │             │       │
│      │    Active Relationship (variable)     │   7 years post-closure  │       │
│      │◄──────────────────────────────────────►│◄────────────────────────►│     │
│                                                                                  │
│  STORAGE TIERS                                                                   │
│  ─────────────                                                                   │
│  │ Stage          │ Storage         │ Access    │ Cost     │                   │
│  │────────────────│─────────────────│───────────│──────────│                   │
│  │ Active         │ PostgreSQL      │ Real-time │ $$$      │                   │
│  │ Recent (1 yr)  │ PostgreSQL      │ Fast      │ $$$      │                   │
│  │ Historical     │ Data Lake (S3)  │ Query     │ $$       │                   │
│  │ Archive        │ S3 Glacier      │ Hours     │ $        │                   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## 6.4 GDPR Data Subject Rights

| Right | Implementation | SLA |
|-------|----------------|-----|
| Right to Access | Export customer data via API | 30 days |
| Right to Rectification | Update via Customer Service | 72 hours |
| Right to Erasure | Anonymize PII (retain for regulatory) | 30 days |
| Right to Portability | Export in machine-readable format | 30 days |
| Right to Object | Opt-out flags in profile | 24 hours |
| Right to Restrict | Processing freeze flag | 24 hours |

---

# 7. Document Sign-Off

## 7.1 Phase C Diagrams Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Chief Data Officer | | | |
| Chief Architect | | | |
| CTO | | | |
| CISO | | | |
| DPO | | | |
| Head of Compliance | | | |

---

**Document End**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Data Architecture Team | CTO, CDO, CISO |
| [Date] | [Date] | [Date] |
