# KVBank

## Requirements Management Phase

### Part 2: Change Control, Governance & Metrics

### *Continuous Change Management Throughout the ADM*

### Chief Architect Office

---

**Document Control**

| Field | Value |
|-------|-------|
| Document | Requirements Management Phase - Part 2 |
| Version | 1.0 |
| Classification | Internal - Executive |
| Author | Chief Architect |
| Status | Approved |
| Date | [Date] |

---

# Table of Contents

1. Requirements Change Control
2. Requirements Baseline Management
3. Impact Assessment Process
4. Requirements Governance
5. Requirements Management Tools
6. Requirements Metrics and Reporting
7. Summary

---

# 1. Requirements Change Control

## 1.1 Change Control Overview

Requirements change control is the continuous process of managing changes to requirements throughout the ADM cycle. Because change can occur at any time, a robust change control process is essential for maintaining architecture integrity while remaining responsive to business needs.

**KEY PRINCIPLE: Being able to handle change at any time is crucial for the ADM to succeed.**

## 1.2 Change Control Process

**REQUIREMENTS CHANGE CONTROL FLOW:**

```
REQUEST → EVALUATE → ANALYZE IMPACT → APPROVE/REJECT → IMPLEMENT → VERIFY → CLOSE
```

| Step | Activity | Owner | Output | SLA |
|------|----------|-------|--------|-----|
| 1 | Submit change request | Requestor | RFC form completed | - |
| 2 | Initial evaluation | Requirements Manager | Classification, priority | 1 day |
| 3 | Impact analysis | Business Analyst | Impact assessment | 3 days |
| 4 | Technical review | Domain Architect | Feasibility assessment | 2 days |
| 5 | Approval decision | Change Board | Approved/Rejected/Deferred | 2 days |
| 6 | Update repository | Requirements Manager | Updated requirements | 1 day |
| 7 | Communicate change | Requirements Manager | Stakeholder notification | 1 day |
| 8 | Implement change | Delivery Team | Updated deliverables | Varies |
| 9 | Verify implementation | QA Team | Verification report | Varies |
| 10 | Close change request | Requirements Manager | Closure record | 1 day |

## 1.3 Change Request Categories

| Category | Description | Approval Level | Timeline |
|----------|-------------|----------------|----------|
| Minor | Clarification, typo fix, no impact | Requirements Manager | 1-2 days |
| Standard | Single requirement change, limited impact | Domain Lead | 3-5 days |
| Significant | Multiple requirements, moderate impact | Requirements Board | 5-10 days |
| Major | Scope change, high impact, cost implications | Architecture Board | 10-20 days |
| Emergency | Critical issue, regulatory, security | Chief Architect | 1 day |

## 1.4 Change Request Register

| RFC ID | Title | Category | Status | Impact | Decision | Date |
|--------|-------|----------|--------|--------|----------|------|
| RFC-001 | Add biometric authentication | Significant | ✅ Approved | WP-04, WP-11 | Approved | M5 |
| RFC-002 | Increase API rate limits | Standard | ✅ Approved | WP-01 | Approved | M5 |
| RFC-003 | Add cryptocurrency support | Major | ⏸️ Deferred | All WPs | New ADM cycle | M6 |
| RFC-004 | GDPR consent enhancement | Emergency | ✅ Closed | WP-02, WP-04 | Approved | M4 |
| RFC-005 | Real-time fraud scoring | Significant | 🔄 In Review | WP-06 | Pending | M7 |
| RFC-006 | Multi-currency accounts | Significant | ✅ Approved | WP-02, WP-05 | Approved | M6 |
| RFC-007 | Carbon footprint tracking | Standard | ❌ Rejected | WP-04 | Out of scope | M6 |
| RFC-008 | PSD3 compliance updates | Major | 📝 Draft | WP-02, WP-05, WP-06 | Pending | M7 |

## 1.5 Change Request Detail: RFC-001

| Field | Value |
|-------|-------|
| RFC ID | RFC-001 |
| Title | Add Biometric Authentication to Mobile App |
| Description | Enable fingerprint and Face ID authentication for mobile banking app login and transaction authorization |
| Requestor | Head of Digital Channels |
| Business Justification | Improve security and user experience; 78% of competitors offer biometrics; customer survey shows 85% demand |
| Category | Significant |
| Priority | High |
| Affected Requirements | REQ-SEC-015, REQ-NFR-022, REQ-BUS-045 |
| Affected Work Packages | WP-04 Digital Channels, WP-11 Security |
| Impact Assessment | Medium - 3 sprints effort, SDK integration required, security review needed |
| Cost Impact | €85K (SDK licensing + development) |
| Schedule Impact | 2 weeks extension to WP-04 Phase 2 |
| Risk Assessment | Low - proven technology, clear requirements |
| Decision | **APPROVED** by Architecture Board |
| Decision Date | M5 Week 2 |
| Implementation Status | In Progress - 60% complete |

## 1.6 Change Types by ADM Phase

| ADM Phase | Typical Change Types | Change Frequency | Handling |
|-----------|----------------------|------------------|----------|
| Preliminary | Principle refinements, scope adjustments | Rare | Board approval |
| Phase A | Vision updates, stakeholder changes | Occasional | Sponsor approval |
| Phase B | Process changes, capability updates | Moderate | Domain review |
| Phase C | Application/data requirement changes | Frequent | Standard process |
| Phase D | Technology changes, NFR updates | Frequent | Technical review |
| Phase E | Project scope, dependency changes | Moderate | PMO coordination |
| Phase F | Timeline, sequencing adjustments | Moderate | Planning review |
| Phase G | Implementation issues, defects | Frequent | Rapid response |
| Phase H | New requirements, enhancements | Continuous | Full process |

---

# 2. Requirements Baseline Management

## 2.1 Baseline Overview

A requirements baseline is a formally approved snapshot of requirements at a specific point in time. Baselines provide a stable reference point for architecture development while still allowing controlled changes.

## 2.2 Baseline Types

| Baseline Type | Description | Created At | Approval |
|---------------|-------------|------------|----------|
| Vision Baseline | Initial business requirements from Phase A | End Phase A | Sponsor |
| Architecture Baseline | Full requirements after Phase D | End Phase D | Architecture Board |
| Implementation Baseline | Requirements for each work package | WP Start | Domain Lead |
| Release Baseline | Requirements for each release | Release Planning | Release Manager |
| Operational Baseline | Requirements for production | Go-Live | Operations |

## 2.3 KVBank Requirements Baselines

| Baseline ID | Name | Requirements | Date | Status | Changes Since |
|-------------|------|--------------|------|--------|---------------|
| BL-001 | Vision Baseline v1.0 | 45 | M1 | Superseded | +12 / -2 / ~8 |
| BL-002 | Architecture Baseline v1.0 | 587 | M4 | Superseded | +45 / -5 / ~32 |
| BL-003 | Architecture Baseline v1.1 | 625 | M6 | **Current** | +18 / -0 / ~12 |
| BL-004 | WP-01 Implementation v1.0 | 89 | M2 | Current | +5 / -0 / ~3 |
| BL-005 | WP-02 Implementation v1.0 | 124 | M4 | Current | +8 / -1 / ~6 |
| BL-006 | Phase 1 Release v1.0 | 213 | M5 | Current | +3 / -0 / ~2 |

**Legend:** +Added / -Removed / ~Modified

## 2.4 Baseline Change Control

| Action | Trigger | Process | Approval |
|--------|---------|---------|----------|
| Create Baseline | Phase completion, release planning | Snapshot requirements | Baseline owner |
| Modify Baseline | Approved RFC | Update + version | Change Board |
| Supersede Baseline | Major phase change | Create new baseline | Architecture Board |
| Retire Baseline | No longer needed | Archive baseline | Requirements Manager |
| Compare Baselines | Impact analysis, audit | Generate delta report | Self-service |

## 2.5 Baseline Comparison: BL-002 vs BL-003

| Category | BL-002 (M4) | BL-003 (M6) | Added | Removed | Modified |
|----------|-------------|-------------|-------|---------|----------|
| Business Requirements | 165 | 172 | +10 | -3 | ~8 |
| Data Architecture | 112 | 118 | +8 | -2 | ~6 |
| Application Architecture | 178 | 189 | +15 | -4 | ~10 |
| Technology Architecture | 132 | 146 | +12 | -0 | ~8 |
| **TOTAL** | **587** | **625** | **+45** | **-9** | **~32** |

**Net Change:** +38 requirements (6.5% growth)

---

# 3. Impact Assessment Process

## 3.1 Impact Assessment Overview

Every requirements change must be assessed for its impact on the architecture, implementation, and operations. This ensures that changes are understood before approval and that appropriate stakeholders are informed.

## 3.2 Impact Assessment Framework

| Impact Dimension | Assessment Questions | Assessed By |
|------------------|----------------------|-------------|
| Architecture Impact | Which architecture domains affected? New patterns needed? | Domain Architect |
| Scope Impact | Which work packages affected? New work packages needed? | Program Manager |
| Schedule Impact | Timeline changes? Critical path affected? | Project Manager |
| Cost Impact | Budget implications? Additional resources needed? | Finance |
| Resource Impact | Skills available? Additional hiring needed? | Resource Manager |
| Risk Impact | New risks introduced? Risk mitigation needed? | Risk Manager |
| Quality Impact | Testing implications? Quality standards affected? | QA Lead |
| Dependency Impact | Other requirements affected? External dependencies? | Business Analyst |

## 3.3 Impact Assessment Matrix

| Impact Level | Scope | Schedule | Cost | Response |
|--------------|-------|----------|------|----------|
| None | No change | No change | No change | Proceed |
| Low | 1 work package | < 1 week | < €10K | Standard |
| Medium | 2-3 work packages | 1-4 weeks | €10K-€100K | Board review |
| High | 4+ work packages | 1-3 months | €100K-€500K | Exec approval |
| Critical | Program-wide | > 3 months | > €500K | Steering |

## 3.4 Impact Assessment Template

### 3.4.1 Assessment for RFC-006: Multi-Currency Accounts

| Dimension | Impact Level | Details |
|-----------|--------------|---------|
| Architecture Impact | Medium | Account domain model changes, FX service addition, reporting updates |
| Scope Impact | Medium | WP-02 Core Banking, WP-05 Payments affected |
| Schedule Impact | Low | 2 weeks additional effort, non-critical path |
| Cost Impact | Low | €45K additional development, €15K FX data feed |
| Resource Impact | Low | Existing team can absorb, no hiring needed |
| Risk Impact | Medium | FX rate accuracy, regulatory reporting complexity |
| Quality Impact | Low | Additional test scenarios for currency conversion |
| Dependency Impact | Medium | REQ-BUS-023, REQ-DAT-015, REQ-APP-034 affected |

| Overall Impact | **MEDIUM** 🟡 |
|----------------|---------------|
| Recommendation | Approve with conditions: Complete FX provider selection before M8 |
| Decision Authority | Requirements Board |

## 3.5 Dependency Impact Analysis

### 3.5.1 Requirements Dependency Map

| Requirement | Depends On | Depended By | Dependency Type |
|-------------|------------|-------------|-----------------|
| REQ-BUS-001 | REQ-NFR-015, REQ-SEC-008 | REQ-BUS-045, REQ-APP-012 | Functional |
| REQ-NFR-015 | REQ-TECH-003 | REQ-BUS-001, REQ-APP-008 | Technical |
| REQ-SEC-021 | REQ-TECH-015 | REQ-BUS-012, REQ-APP-023 | Security |
| REQ-DAT-008 | REQ-TECH-008 | REQ-APP-034, REQ-BUS-056 | Data |

## 3.6 Ripple Effect Analysis

When a requirement changes, the ripple effect must be analyzed:

```
Changed Requirement
       │
       ▼
Dependent Requirements (Direct Impact)
       │
       ▼
Architecture Components (Design Impact)
       │
       ▼
Work Packages (Implementation Impact)
       │
       ▼
Test Cases (Verification Impact)
```

| Changed Requirement | Direct Dependents | Indirect Dependents | Arch Components | Test Cases | Total Impact |
|---------------------|-------------------|---------------------|-----------------|------------|--------------|
| REQ-BUS-001 | 4 | 8 | 3 | 12 | 27 items |
| REQ-NFR-015 | 6 | 15 | 5 | 18 | 44 items |
| REQ-SEC-021 | 8 | 22 | 7 | 25 | 62 items |

---

# 4. Requirements Governance

## 4.1 Governance Framework

Requirements governance ensures that requirements are managed consistently, changes are controlled appropriately, and stakeholders have visibility into requirements status.

## 4.2 Governance Bodies

| Body | Scope | Members | Frequency |
|------|-------|---------|-----------|
| Requirements Board | Significant requirement changes | Req Manager, Domain Leads, BAs | Weekly |
| Architecture Board | Major changes, cross-domain | Chief Architect, Domain Architects | Bi-weekly |
| Change Advisory Board | Implementation changes | Release Mgr, Ops, Architecture | Daily |
| Steering Committee | Critical changes, program scope | Sponsor, CTO, Program Director | Monthly |

## 4.3 Decision Authority Matrix

| Change Type | Requirements Manager | Domain Lead | Req Board | Arch Board | Steering |
|-------------|---------------------|-------------|-----------|------------|----------|
| Minor (clarification) | **Approve** | Inform | - | - | - |
| Standard (single req) | Recommend | **Approve** | Inform | - | - |
| Significant (multiple) | Analyze | Review | **Approve** | Inform | - |
| Major (scope change) | Analyze | Review | Recommend | **Approve** | Inform |
| Critical (program) | Analyze | Review | Review | Recommend | **Approve** |

## 4.4 Requirements Quality Gates

| Gate | Checkpoint | Quality Criteria | Gate Keeper |
|------|------------|------------------|-------------|
| Gate 1 | Requirements Capture | Complete, clear, unambiguous, testable | Business Analyst |
| Gate 2 | Requirements Review | Consistent, feasible, prioritized, traced | Domain Lead |
| Gate 3 | Baseline Approval | Stakeholder sign-off, conflicts resolved | Requirements Board |
| Gate 4 | Implementation Ready | Detailed enough for development | Tech Lead |
| Gate 5 | Verification Complete | All acceptance criteria met | QA Lead |

## 4.5 Escalation Path

| Issue Type | First Escalation | Second Escalation | Final Escalation |
|------------|------------------|-------------------|------------------|
| Requirement conflict | Domain Lead | Requirements Board | Architecture Board |
| Stakeholder disagreement | Requirements Manager | Program Director | Steering Committee |
| Scope dispute | Domain Lead | Architecture Board | Steering Committee |
| Priority conflict | Product Owner | Requirements Board | Program Director |
| Resource constraint | Project Manager | Program Director | Steering Committee |

## 4.6 Requirements Audit

### 4.6.1 Audit Schedule

| Audit Type | Scope | Frequency | Auditor |
|------------|-------|-----------|---------|
| Process Audit | Requirements management process compliance | Quarterly | QA Team |
| Quality Audit | Requirements quality and completeness | Per baseline | Domain Lead |
| Traceability Audit | Traceability coverage and accuracy | Monthly | BA Team |
| Compliance Audit | Regulatory requirements coverage | Quarterly | Compliance |

### 4.6.2 Latest Audit Results

| Audit Area | Score | Findings | Actions |
|------------|-------|----------|---------|
| Process Compliance | 92% | 2 RFCs missing impact assessment | Training scheduled |
| Requirements Quality | 88% | 15% lack acceptance criteria | Backlog grooming |
| Traceability Coverage | 94% | 50 reqs missing arch links | Update in progress |
| Regulatory Coverage | 100% | All regulatory reqs traced | Maintain |

---

# 5. Requirements Management Tools

## 5.1 Tool Landscape

| Tool | Purpose | Users | Integration |
|------|---------|-------|-------------|
| Jira | Requirements tracking, work items, sprints | All teams | Confluence, GitHub |
| Confluence | Requirements documentation, specifications | BAs, Architects | Jira |
| Enterprise Architect | Architecture modeling, traceability | Architects | Jira API |
| TestRail | Test case management, requirements linking | QA Team | Jira |
| Power BI | Requirements reporting, dashboards | Management | Jira, SQL |

## 5.2 Jira Configuration

### 5.2.1 Issue Types

| Issue Type | Purpose | Fields |
|------------|---------|--------|
| Requirement | Capture and track requirements | ID, Description, Category, Priority, Owner |
| RFC (Change Request) | Track requirement changes | Impact, Cost, Schedule, Decision |
| Epic | Group related requirements | Business Goal, Work Package |
| Story | Implementable requirement units | Acceptance Criteria, Story Points |
| Test Case | Link tests to requirements | Test Steps, Expected Results |

### 5.2.2 Workflow

```
REQUIREMENT WORKFLOW IN JIRA:

Draft → Proposed → In Review → Approved → In Progress → Implemented → Verified → Closed
              │                    │
              ▼                    ▼
          Rejected              Deferred
```

## 5.3 Reporting Dashboards

### 5.3.1 Requirements Dashboard

| Widget | Metric | Refresh | Audience |
|--------|--------|---------|----------|
| Status Distribution | Requirements by status (pie chart) | Real-time | All |
| Priority Breakdown | Requirements by priority | Real-time | All |
| Burndown | Requirements completion over time | Daily | Management |
| Change Trend | RFCs submitted/approved over time | Weekly | Management |
| Traceability Heat Map | Coverage by work package | Daily | Architects |
| Quality Score | Requirements meeting quality criteria | Weekly | QA |

---

# 6. Requirements Metrics and Reporting

## 6.1 Key Performance Indicators

| KPI | Target | Current | Status | Trend |
|-----|--------|---------|--------|-------|
| Requirements Stability | < 5% change/month | 3.2% | ✅ On Target | ↓ Improving |
| Traceability Coverage | > 95% | 94% | 🟡 Near Target | ↑ Improving |
| Requirements Quality | > 90% | 88% | 🟡 Below Target | ↑ Improving |
| Change Cycle Time | < 10 days | 8 days | ✅ On Target | → Stable |
| Defects from Requirements | < 10% | 8% | ✅ On Target | ↓ Improving |
| Stakeholder Satisfaction | > 4.0/5.0 | 4.2 | ✅ On Target | → Stable |

## 6.2 Requirements Status Summary

| Status | Count | Percentage | Previous Month | Change |
|--------|-------|------------|----------------|--------|
| Draft | 53 | 7% | 68 | -15 |
| Approved | 205 | 25% | 198 | +7 |
| In Progress | 349 | 43% | 332 | +17 |
| Closed | 164 | 20% | 148 | +16 |
| Deferred | 35 | 5% | 32 | +3 |
| **TOTAL** | **806** | **100%** | **778** | **+28** |

## 6.3 Change Request Metrics

| Metric | This Month | Last Month | YTD |
|--------|------------|------------|-----|
| RFCs Submitted | 12 | 15 | 68 |
| RFCs Approved | 8 | 11 | 52 |
| RFCs Rejected | 2 | 3 | 12 |
| RFCs Deferred | 2 | 1 | 4 |
| Approval Rate | 67% | 73% | 76% |
| Average Cycle Time | 8 days | 9 days | 8.5 days |

## 6.4 Reporting Schedule

| Report | Audience | Frequency | Delivery |
|--------|----------|-----------|----------|
| Requirements Status Dashboard | All stakeholders | Real-time | Jira/Confluence |
| Weekly Requirements Summary | Project teams | Weekly | Email + Slack |
| Change Request Report | Requirements Board | Weekly | Email |
| Traceability Report | Architecture team | Monthly | Confluence |
| Executive Requirements Report | Steering Committee | Monthly | PowerPoint |
| Audit Report | Quality team | Quarterly | Document |

---

# 7. Summary

## 7.1 Part 2 Deliverables

| Deliverable | Status | Section |
|-------------|--------|---------|
| Requirements Change Control Process | ✅ Complete | Section 1 |
| Change Request Register | ✅ Complete | Section 1.4 |
| Requirements Baseline Management | ✅ Complete | Section 2 |
| Impact Assessment Framework | ✅ Complete | Section 3 |
| Requirements Governance Framework | ✅ Complete | Section 4 |
| Decision Authority Matrix | ✅ Complete | Section 4.3 |
| Requirements Management Tools | ✅ Complete | Section 5 |
| Requirements Metrics & KPIs | ✅ Complete | Section 6 |

## 7.2 Key Metrics Summary

| Metric | Value |
|--------|-------|
| Total Requirements | 806 |
| Active Change Requests | 8 |
| Current Baseline | BL-003 (v1.1) |
| Requirements Stability | 3.2% change/month |
| Change Cycle Time | 8 days average |
| Traceability Coverage | 94% |
| Process Compliance | 92% |

## 7.3 Requirements Management Phase Summary

The Requirements Management phase operates continuously at the center of the ADM, ensuring:

- All **806 requirements** are captured, classified, and tracked
- Changes are managed through a controlled process (**8 RFCs active**)
- Baselines provide stable reference points (**6 baselines maintained**)
- Impact assessment ensures informed decision-making
- Governance ensures appropriate oversight and control
- Tools support efficient requirements management
- Metrics provide visibility into requirements health

**KEY OUTCOME:** The ability to handle change at any time while maintaining architecture integrity.

---

**Requirements Management Phase Complete**

**Continuous Process | Central to ADM | Enabling Change**

| Prepared By | Reviewed By | Approved By |
|-------------|-------------|-------------|
| Chief Architect | Program Director | CTO |
| [Date] | [Date] | [Date] |
