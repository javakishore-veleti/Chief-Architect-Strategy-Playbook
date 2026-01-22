# Architecture Development - Architecture Guidelines and Techniques

- 9 Key techniques

1. Architecture Principles
2. Gap Analsys
3. Architecture Patterns
4. Gap Analysis
5. Migration Planning Techniques
6. Interoperability Requirements
7. Business Transformation Readiness Assessment
8. Risk Management
9. Architecture Alertnatives and Trade-Offs

# Technique 1: Architecture Principles

- An enduring set of general rules and guideliens about how we do architecture
- Not intended to change very often
- Serves as a statement by which you an use to make decisions
- Example Data Architecture Principle says "Data Trustee" - "Each data element has a trustee accountable for data quality"

## Five elements of a Good Principle
1. Understandability
    - easy to understand the principle
    - easy to understand whether others are violating the principle
2. Robustness
    - each principle should be definitive and precise to support consistent decision making during complicating and controversial situations
3. Completeness
    - should be covered every potentiation situation
4. Consistency
5. Stability
    - dont want principle that changes frequently, maybe some refinements but overtime they should be solidified

# Techinque 2: Stakeholder Management

- As an architect, being able to win support for your plans is a skill
- Knowing who the most powerful stakeholders are is very important
- Making things easier for approvals and budgets
- Can establish a communication plan to keep them informed, level of detail give them
- Identify the problems and conflicts early in order to avoid them
- Power vs Level of Interest
    -- High / Low
    -- Keep Satisfied, Key Players
    -- Minimal Effort, Keep Informed

# Technique 3: Architecture Patterns

- Building Blocks can be considered as patterns
- Architecture Pattern is defined as "When, Why, and How you use it" those ABBs and SBBs
- Once you have developed a number of "building blocks", you may want to establish patterns for them


# Technique 3: Gap Analysis

- Highlight beween baseline and target architectures
- Baseline architecture - as it currently exists
- Target architecture - is desired destination
- Gaps are anything added, changed or intentionally omitted
- Will also identify things accidentally omitted
- It should be clear and easy to explain why things were added or removed

# Technique 4: Migration Planning Techniques

1. Implementation Factor Assessment and Deduction Matrix
2. Consolidated Gaps, Solutions, & Dependencies Matrix
3. Architecture Definition Increments Table
4. Transistion Architecture State Evolution Table
5. Business Value Assessment Technique

## Implementation Factor Catalog

Factors typically include:

1. Risks
2. Issues
3. Assumptions
4. Dependencies
5. Actions
6. Impacts

### Implementation Factor Catalog
| Factor | Description | Deduction |
|--------|-------------|-----------|
|<Name of Factor> | <Descriptoin of Factor> | <Impact on Migration Path> |
|--------|-------------|-----------|
|Change in Technology | Shutdown the message centers, saving 700 personnel,, and have them replaced by email | Need for personnedl training, re-assignment. Email has major personnel savings and should be given priority |
|--------|-------------|-----------|
|Consolidation of services |  |  |
|--------|-------------|-----------|
|Introduction of New Customer Service |  |  |
|--------|-------------|-----------|


