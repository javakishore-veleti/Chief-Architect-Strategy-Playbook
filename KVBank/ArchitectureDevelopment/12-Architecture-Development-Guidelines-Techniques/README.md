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

## Consolidated Gaps, Solutions, & Dependencies Matrix

- Gaps identified during phase B, C and D
- This matrix can be used as a planning tool when creating work packages
- Work packages identified during phase E and F

## Architecture Definition Increments Table

- Architecture Definition Increments table allows the architect to plan a series of Transistion Architecturs

- Lists the projects and then assigning their incremental deliverables across the Transistion Architectures

## Target Architecture State Evolution Table

- Show the proposed state of the architectures at various levels
- At a glance, anyone can see that after Phase 1 of implementation, the new services that will be available even if they are not fully transistioned to the final target architecture yet
- Can also use a color coding matrix, with green, yellow and red showing the state of various services after each transistion architecture is implemented

## Business Value Assessment Technique

- A technique to assess business value based on risk versus value
- Another "at-a-glance" way to see the status of the overall implementation project on the overall architecture implementation value
- Some projects that are at risk might be low value, which is better than high value projects being at risk

# Technique 5: Interoperability Requirements

- Definition of "Interoperability" means "the ability to share information and services"
- Business Interoperability - how business teams work together
- Information Interoperability - how data is shared
- Technical Interoperability - how technical services are connected to one another
- Ease of the architecture definition phases has elements of interoperability
- Architects think about how what they do interacts with the "outside world" during the process

