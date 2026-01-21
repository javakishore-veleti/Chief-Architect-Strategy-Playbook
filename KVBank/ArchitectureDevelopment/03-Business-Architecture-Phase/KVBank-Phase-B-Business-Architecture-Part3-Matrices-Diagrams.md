# KVBank Phase B: Business Architecture

## Part 3: Artifacts - Matrices and Diagrams

---

# 12. Matrices

## 12.1 Value Stream/Capability Matrix

| Value Stream | CAP-1 Customer | CAP-2 Banking | CAP-3 Treasury | CAP-4 Wealth | CAP-5 Risk | CAP-6 Ops | CAP-7 Tech |
|--------------|----------------|---------------|----------------|--------------|------------|-----------|------------|
| VS-01: Acquire to Active | ●●● | ●●○ | ○ | ○ | ●●● | ●○ | ●●● |
| VS-02: Transact to Settle | ●○ | ●●● | ●●○ | ○ | ●●● | ●●● | ●●● |
| VS-03: Issue to Use | ●●○ | ●●● | ○ | ○ | ●●○ | ●●○ | ●●○ |
| VS-04: Lend to Collect | ●●○ | ●●● | ○ | ○ | ●●● | ●●○ | ●●○ |
| VS-05: Inquire to Resolve | ●●● | ●○ | ○ | ●○ | ●○ | ●●○ | ●●○ |
| VS-07: Invest to Return | ●●○ | ●○ | ●○ | ●●● | ●●● | ●●○ | ●●● |
| VS-08: Trade to Settle (FX) | ○ | ●●○ | ●●● | ○ | ●●○ | ●●● | ●●○ |

**Legend:** ●●● = Primary | ●●○ = Secondary | ●○ = Minimal | ○ = Not involved

---

## 12.2 Strategy/Capability Matrix

| Strategic Goal | CAP-1 | CAP-2 | CAP-3 | CAP-4 | CAP-5 | CAP-6 | CAP-7 |
|----------------|-------|-------|-------|-------|-------|-------|-------|
| G-01: 1M Customers | ●●● | ●●○ | ●○ | ○ | ●●○ | ●●○ | ●●● |
| G-02: €500M AUM | ●●○ | ●○ | ●○ | ●●● | ●●○ | ●○ | ●●● |
| G-03: 5 Markets | ●●○ | ●●● | ●●○ | ●○ | ●●● | ●●○ | ●●● |
| G-04: €5 Cost/Customer | ●●○ | ●●○ | ●●○ | ○ | ●●○ | ●●● | ●●● |
| G-05: 99.99% Availability | ●○ | ●●● | ●●○ | ●●○ | ●●○ | ●●● | ●●● |

---

## 12.3 Capability/Organization Matrix

| Capability | Retail | Business | Wealth | Engineering | Operations | Risk | Compliance |
|------------|--------|----------|--------|-------------|------------|------|------------|
| CAP-1: Customer Mgmt | ●●● | ●●● | ●●○ | ●○ | ●○ | ○ | ○ |
| CAP-2: Banking Services | ●●● | ●●● | ●○ | ●●○ | ●●● | ●●○ | ●○ |
| CAP-3: Treasury Mgmt | ○ | ●○ | ○ | ●○ | ●○ | ●●○ | ●○ |
| CAP-4: Wealth Mgmt | ○ | ○ | ●●● | ●●○ | ●○ | ●●○ | ●●○ |
| CAP-5: Risk & Compliance | ●○ | ●○ | ●●○ | ●○ | ●●○ | ●●● | ●●● |
| CAP-6: Operations Mgmt | ●○ | ●○ | ●○ | ●●○ | ●●● | ●○ | ●○ |
| CAP-7: Technology | ●○ | ●○ | ●●○ | ●●● | ●●○ | ●○ | ●○ |

---

## 12.4 Business Interaction Matrix

| Actor | Retail Cust | Business Cust | Wealth Client | Card Networks | Payment Rails | Regulators |
|-------|-------------|---------------|---------------|---------------|---------------|------------|
| Retail Customer | - | ○ | ○ | ● | ● | ○ |
| Business Customer | ○ | - | ○ | ● | ● | ○ |
| Wealth Client | ○ | ○ | - | ● | ● | ○ |
| Operations | ● | ● | ● | ● | ● | ● |
| Risk/Compliance | ● | ● | ● | ○ | ○ | ● |

---

## 12.5 Actor/Role Matrix

| Actor | CEO | CTO | COO | Head Retail | Head Wealth | CS Agent | Engineer |
|-------|-----|-----|-----|-------------|-------------|----------|----------|
| Retail Customer | ○ | ○ | ○ | ● | ○ | ● | ○ |
| Business Customer | ○ | ○ | ○ | ○ | ○ | ● | ○ |
| Wealth Client | ○ | ○ | ○ | ○ | ● | ● | ○ |
| Regulators | ● | ○ | ● | ○ | ○ | ○ | ○ |
| Partners (Visa, SWIFT) | ○ | ● | ● | ○ | ○ | ○ | ● |

---

# 13. Diagrams

## 13.1 Business Model Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK BUSINESS MODEL (TARGET - 36 MONTHS)                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  KEY PARTNERS           KEY ACTIVITIES         VALUE PROPOSITIONS               │
│  ─────────────          ──────────────         ───────────────────              │
│  • Visa/Mastercard      • Customer Acquisition  RETAIL (1M):                    │
│  • SWIFT/SEPA Instant   • Payment Processing    • 5-min onboarding              │
│  • Faster Payments      • Risk Management       • Real-time everything          │
│  • Onfido/ComplyAdv     • Investment Advisory   • No FX fees, 30+ currencies    │
│  • AWS Cloud            • Platform Operations                                   │
│  • Reuters/Bloomberg                            BUSINESS (50K):                  │
│  • Global Advisor       KEY RESOURCES           • Team management               │
│                         ─────────────           • Bulk payments                  │
│                         • Banking License       • Accounting integrations        │
│                         • Digital Platform                                       │
│                         • 150 Engineers         WEALTH (100K):                   │
│                         • Global Advisor        • Investment advisory            │
│                         • Customer Data         • Portfolio management           │
│                                                 • Robo-advisory                  │
│                                                                                  │
│  REVENUE STREAMS (€77.5M Target)             COST STRUCTURE (€5/customer)       │
│  ───────────────────────────────             ────────────────────────────        │
│  • FX Margin (€25M)                          • Cloud Infrastructure (€8M)       │
│  • Card Interchange (€20M)                   • Engineering Team (€20M)          │
│  • Subscriptions (€15M)                      • Operations (€10M)                │
│  • Interest Income (€10M)                    • Compliance/Risk (€5M)            │
│  • Wealth Fees (€2.5M)                       • Variable: KYC, Support, Fraud    │
│  • API Platform (€5M)                                                           │
│                                                                                  │
│  CUSTOMER SEGMENTS                           CHANNELS                            │
│  ─────────────────                           ────────                            │
│  • Retail: Digital-first, 18-45             • Mobile App (80%)                  │
│  • Business: SMEs, Startups                 • Web Application (15%)             │
│  • Wealth: Mass affluent, HNW              • Partner APIs                       │
│  • 5 Markets: UK, DE, FR, ES, NL           • Advisor Portal (Wealth)           │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.2 Business Capability Map

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK CAPABILITY MAP (TARGET STATE)                          │
│                    ████ = Target 4-5  ▓▓▓ = Level 3  ░░░ = Gap/Build            │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  CAP-1: CUSTOMER MANAGEMENT                                  Owner: Head Retail │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │   ACQUIRE   │ │   ONBOARD   │ │    SERVE    │ │   SUPPORT   │               │
│  │    ▓▓▓▓     │ │    ████     │ │    ████     │ │    ████     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                                                                  │
│  CAP-2: BANKING SERVICES                                   Owner: Head Payments │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │  ACCOUNTS   │ │  PAYMENTS   │ │    CARDS    │ │   LENDING   │               │
│  │    ████     │ │ ████ +░░░   │ │    ████     │ │    ▓▓▓▓     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                  (Instant=Build)                                                 │
│                                                                                  │
│  CAP-3: TREASURY MANAGEMENT                                Owner: Head Treasury │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │     FX      │ │  LIQUIDITY  │ │   HEDGING   │ │ MARKET DATA │               │
│  │    ████     │ │    ████     │ │    ████     │ │    ████     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                                                                  │
│  CAP-4: WEALTH MANAGEMENT (ALL NEW - BUILD)                  Owner: Head Wealth │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │  ADVISORY   │ │ PORTFOLIOS  │ │    ROBO     │ │  PLANNING   │               │
│  │    ░░░░     │ │    ░░░░     │ │    ░░░░     │ │    ░░░░     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                                                                  │
│  CAP-5: RISK & COMPLIANCE                                            Owner: CRO │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │     KYC     │ │     AML     │ │    FRAUD    │ │  REPORTING  │               │
│  │    ████     │ │    ████     │ │ ████ +░░░   │ │    ████     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                  (ML=Build)                                      │
│                                                                                  │
│  CAP-6: OPERATIONS MANAGEMENT                                        Owner: COO │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │   LEDGER    │ │     P&L     │ │   RECON     │ │    BATCH    │               │
│  │    ████     │ │    ████     │ │    ████     │ │    ████     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                                                                  │
│  CAP-7: TECHNOLOGY ENABLEMENT                                        Owner: CTO │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │
│  │     IAM     │ │    DATA     │ │  ANALYTICS  │ │     ML      │               │
│  │    ████     │ │    ████     │ │ ████ +░░░   │ │    ░░░░     │               │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘               │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.3 Value Stream Map: Acquire to Active

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    VALUE STREAM: ACQUIRE TO ACTIVE                               │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐           │
│  │DISCOVER │──▶│CONSIDER │──▶│  APPLY  │──▶│ VERIFY  │──▶│ACTIVATE │           │
│  │         │   │         │   │         │   │         │   │         │           │
│  │Marketing│   │ Evaluate│   │ Submit  │   │Identity │   │ First   │           │
│  │Awareness│   │ Options │   │   App   │   │  Check  │   │  Use    │           │
│  └─────────┘   └─────────┘   └─────────┘   └─────────┘   └─────────┘           │
│                                                                                  │
│  METRICS:                                                                        │
│  │ Stage      │ Current │ Target │ Improvement │                                │
│  │────────────│─────────│────────│─────────────│                                │
│  │ Apply      │ 3 min   │ 2 min  │ 33% faster  │                                │
│  │ Verify     │ 8 min   │ 2 min  │ 75% faster  │                                │
│  │ Activate   │ 4 min   │ 1 min  │ 75% faster  │                                │
│  │ TOTAL      │ 15 min  │ 5 min  │ 67% faster  │                                │
│  │ Drop-off   │ 35%     │ 15%    │ -20pp       │                                │
│  │ Auto-verify│ 80%     │ 95%    │ +15pp       │                                │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.4 Value Stream Map: Invest to Return (NEW)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    VALUE STREAM: INVEST TO RETURN (NEW)                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐        │
│  │PROFILE │─▶│ ASSESS │─▶│RECOMMEND│─▶│ SELECT │─▶│EXECUTE │─▶│ REPORT │        │
│  │        │  │  RISK  │  │        │  │        │  │        │  │        │        │
│  │Financial│ │Tolerance│ │Options │  │Products│  │Trades  │  │Perform.│        │
│  │Situation│ │Capacity │ │Advice  │  │Confirm │  │Orders  │  │Returns │        │
│  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘        │
│                                                                                  │
│  ROBO-ADVISORY PATH (Automated):                                                 │
│  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐                    │
│  │ GOALS  │─▶│  RISK  │─▶│  AUTO  │─▶│  AUTO  │─▶│  AUTO  │                    │
│  │ SETUP  │  │PROFILE │  │ALLOCATE│  │INVEST  │  │REBALANCE│                    │
│  │ 5 min  │  │ 3 min  │  │ Instant│  │ 1 min  │  │ Daily  │                    │
│  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘                    │
│                                                                                  │
│  TARGET: Time to first investment < 10 min (Robo path)                          │
│  TARGET: 100% MiFID compliance documentation                                    │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.5 Organization Map

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK ORGANIZATION MAP (TARGET - 560 FTE)                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│                              ┌─────────────────┐                                 │
│                              │       CEO       │                                 │
│                              └────────┬────────┘                                 │
│                                       │                                          │
│     ┌───────┬───────┬───────┬────────┼────────┬───────┬───────┬───────┐        │
│     │       │       │       │        │        │       │       │       │        │
│  ┌──┴──┐ ┌──┴──┐ ┌──┴──┐ ┌──┴──┐ ┌───┴───┐ ┌──┴──┐ ┌──┴──┐ ┌──┴──┐ ┌──┴──┐   │
│  │ CFO │ │ CTO │ │ CRO │ │ COO │ │  CPO  │ │ CCO │ │CISO │ │ CWO │ │ CMO │   │
│  │(20) │ │(150)│ │(30) │ │(60) │ │ (40)  │ │(20) │ │(15) │ │(50) │ │(25) │   │
│  └─────┘ └──┬──┘ └─────┘ └──┬──┘ └───────┘ └─────┘ └─────┘ └──┬──┘ └─────┘   │
│             │               │                                  │               │
│    ┌────────┴────────┐   ┌──┴──┐                         ┌────┴────┐          │
│    │   Engineering   │   │ CS  │                         │ Advisory│          │
│    │    (150 FTE)    │   │(35) │                         │  (25)   │          │
│    ├─────────────────┤   └─────┘                         └─────────┘          │
│    │• Platform (50)  │                                                         │
│    │• Domain (80)    │                                                         │
│    │• Data (20)      │                                                         │
│    └─────────────────┘                                                         │
│                                                                                  │
│  REGIONAL: UK │ Germany (M12) │ France (M18) │ Spain (M24) │ Netherlands (M30) │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.6 Business Footprint Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK BUSINESS FOOTPRINT                                     │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  GEOGRAPHIC FOOTPRINT                        SEGMENT FOOTPRINT                   │
│  ────────────────────                        ─────────────────                   │
│                                                                                  │
│  ┌─────────────────────────┐                ┌───────────┐                       │
│  │       EUROPE            │                │  RETAIL   │ 1M Customers          │
│  │                         │                │ • Personal Account                │
│  │    NL (M30)   DE (M12)  │                │ • Premium Account                 │
│  │         UK (LIVE)       │                │ • Cards, Lending                  │
│  │                         │                └───────────┘                       │
│  │    FR (M18)             │                ┌───────────┐                       │
│  │              ES (M24)   │                │ BUSINESS  │ 50K Customers         │
│  │    PT (LIVE - Tech Hub) │                │ • Business Account                │
│  │                         │                │ • Multi-user, Bulk Pay            │
│  └─────────────────────────┘                └───────────┘                       │
│                                             ┌───────────┐                       │
│  CHANNEL FOOTPRINT                          │  WEALTH   │ 100K Clients          │
│  ─────────────────                          │ • Advisory (NEW)                  │
│  ┌─────────┬─────────┬─────────┬─────────┐ │ • Robo (NEW)                      │
│  │ Mobile  │   Web   │ Partner │ Advisor │ └───────────┘                       │
│  │  (80%)  │  (15%)  │   API   │ Portal  │                                     │
│  └─────────┴─────────┴─────────┴─────────┘                                     │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.7 Solution Concept Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    KVBANK SOLUTION CONCEPT                                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  CUSTOMERS                                                        PARTNERS      │
│  ─────────                                                        ────────      │
│  ┌────┐ ┌────┐ ┌────┐                                        ┌────┐ ┌────┐    │
│  │Ret │ │Bus │ │Wlth│                                        │Fin │ │Ent │    │
│  └──┬─┘ └──┬─┘ └──┬─┘                                        └──┬─┘ └──┬─┘    │
│     └──────┴──────┴─────────────────┬────────────────────────────┴─────┘       │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                      DIGITAL CHANNELS                                    │   │
│  │   Mobile App │ Web App │ Partner API │ Advisor Portal │ Notifications   │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                       API GATEWAY                                        │   │
│  │           Authentication │ Authorization │ Rate Limiting                 │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                     BUSINESS SERVICES                                    │   │
│  │                                                                          │   │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐                 │   │
│  │  │ CUSTOMER │  │ BANKING  │  │   RISK   │  │  WEALTH  │                 │   │
│  │  │   CRM    │  │  Ledger  │  │   KYC    │  │ Advisory │                 │   │
│  │  │   IAM    │  │ Payments │  │   AML    │  │ Portfolio│                 │   │
│  │  │   APIs   │  │  Cards   │  │  Fraud   │  │   Robo   │                 │   │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘                 │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                      EVENT BACKBONE (Kafka)                              │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                        DATA LAYER                                        │   │
│  │   Event Store │ PostgreSQL │ Redis │ Data Lake │ ML Platform             │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                   PARTNER INTEGRATIONS                                   │   │
│  │    Visa/MC │ SWIFT/SEPA │ Onfido │ ComplyAdv │ Reuters │ Global Advisor │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                     │                                           │
│                                     ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                   CLOUD INFRASTRUCTURE (AWS)                             │   │
│  │        Multi-Region │ Auto-Scaling │ 99.99% Availability │ DR            │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.8 Goal/Objective/Service Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    GOAL → OBJECTIVE → SERVICE ALIGNMENT                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────────┐│
│  │                        G-01: 1M CUSTOMERS                                    ││
│  └──────────────────────────────────┬──────────────────────────────────────────┘│
│                                     │                                            │
│       ┌─────────────────────────────┼─────────────────────────────┐             │
│       │                             │                             │             │
│       ▼                             ▼                             ▼             │
│  ┌─────────────┐            ┌─────────────┐            ┌─────────────┐          │
│  │ O-04:       │            │ O-01:       │            │ O-05:       │          │
│  │Customer 360 │            │ Instant Pay │            │ Wealth MVP  │          │
│  └──────┬──────┘            └──────┬──────┘            └──────┬──────┘          │
│         │                          │                          │                 │
│         ▼                          ▼                          ▼                 │
│  BS-04: Balance             BS-02: Payment             BS-07: Advisory          │
│  BS-05: History             BS-17: Notify              BS-08: Portfolio         │
│  BS-10: Support             (SEPA Instant)             BS-09: Robo              │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────────┐│
│  │                        G-04: €5 COST/CUSTOMER                                ││
│  └──────────────────────────────────┬──────────────────────────────────────────┘│
│                                     │                                            │
│       ┌─────────────────────────────┼─────────────────────────────┐             │
│       │                             │                             │             │
│       ▼                             ▼                             ▼             │
│  ┌─────────────┐            ┌─────────────┐            ┌─────────────┐          │
│  │ O-03:       │            │ O-02:       │            │ Platform    │          │
│  │ 95% STP     │            │ 0.02% Fraud │            │ Automation  │          │
│  └──────┬──────┘            └──────┬──────┘            └──────┬──────┘          │
│         │                          │                          │                 │
│         ▼                          ▼                          ▼                 │
│  BS-02: Payments            BS-13: Fraud               BS-18: Analytics         │
│  BS-12: AML (Auto)          Detection (ML)             Event-Driven Ops         │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.9 Process Flow Diagram: Payment Processing

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    PROCESS FLOW: PAYMENT (TARGET - 95% STP)                      │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────┐                                                                     │
│  │ START   │                                                                     │
│  └────┬────┘                                                                     │
│       ▼                                                                          │
│  ┌─────────────────┐     No    ┌─────────────────┐                              │
│  │    Validate     │──────────▶│  Return Error   │                              │
│  │    Request      │           └─────────────────┘                              │
│  └────────┬────────┘                                                            │
│           │ Yes                                                                  │
│           ▼                                                                      │
│  ┌─────────────────┐     No    ┌─────────────────┐                              │
│  │   Check Funds   │──────────▶│ Insufficient    │                              │
│  └────────┬────────┘           └─────────────────┘                              │
│           │ Yes                                                                  │
│           ▼                                                                      │
│  ┌─────────────────┐   Alert   ┌─────────────────┐                              │
│  │  AML/Fraud ML   │──────────▶│   Investigate   │◀─── 5% Manual Path          │
│  │   Screening     │           │   (Manual)      │                              │
│  └────────┬────────┘           └────────┬────────┘                              │
│           │ Clear (95%)        Approve/Reject                                   │
│           ▼                             │                                        │
│  ┌─────────────────┐◀───────────────────┘                                       │
│  │  Route & Execute│                                                            │
│  │  (SEPA/SWIFT/   │                                                            │
│  │   Instant/Int)  │                                                            │
│  └────────┬────────┘                                                            │
│           ▼                                                                      │
│  ┌─────────────────┐                                                            │
│  │ Update Ledger & │                                                            │
│  │ Notify Customer │                                                            │
│  └────────┬────────┘                                                            │
│           ▼                                                                      │
│       ┌─────────┐                                                               │
│       │   END   │  Target: 95% STP, <11 sec                                     │
│       └─────────┘                                                               │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 13.10 Function Decomposition: Wealth Management

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    FUNCTION DECOMPOSITION: WEALTH MANAGEMENT                     │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│                     ┌─────────────────────────────────┐                          │
│                     │    WEALTH MANAGEMENT (CAP-4)    │                          │
│                     └────────────────┬────────────────┘                          │
│                                      │                                           │
│     ┌───────────────┬────────────────┼────────────────┬───────────────┐         │
│     │               │                │                │               │         │
│     ▼               ▼                ▼                ▼               ▼         │
│ ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐          │
│ │  ADVISE   │ │  MANAGE   │ │   ROBO-   │ │   PLAN    │ │  REPORT   │          │
│ │(CAP-4.1)  │ │PORTFOLIOS │ │  ADVISE   │ │ FINANCES  │ │(CAP-4.5)  │          │
│ │           │ │(CAP-4.2)  │ │(CAP-4.3)  │ │(CAP-4.4)  │ │           │          │
│ └─────┬─────┘ └─────┬─────┘ └─────┬─────┘ └─────┬─────┘ └─────┬─────┘          │
│       │             │             │             │             │                 │
│       ▼             ▼             ▼             ▼             ▼                 │
│ ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐          │
│ │• Profile  │ │• Construct│ │• Auto     │ │• Set Goals│ │• Generate │          │
│ │• Risk Tol │ │• Execute  │ │  Profile  │ │• Project  │ │  Statements│         │
│ │• Recommend│ │• Rebalance│ │• Auto     │ │• Track    │ │• Tax Report│         │
│ │• Document │ │• Monitor  │ │  Allocate │ │  Progress │ │• Insights │          │
│ │  (MiFID)  │ │           │ │• Auto     │ │           │ │           │          │
│ │           │ │           │ │  Rebalance│ │           │ │           │          │
│ └───────────┘ └───────────┘ └───────────┘ └───────────┘ └───────────┘          │
│                                                                                  │
│ ALL CAPABILITIES: Build from scratch using Global Advisor platform               │
│ Timeline: MVP M18, Robo M30                                                      │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

# 14. Document Sign-Off

## 14.1 Phase B Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Chief Architect | | | |
| CTO | | | |
| COO | | | |
| CPO | | | |
| Head of Wealth | | | |
| CRO | | | |
| CCO | | | |

---

**Document End**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Architecture Team | CTO, COO |
| [Date] | [Date] | [Date] |
