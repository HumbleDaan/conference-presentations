# Brainstorm Summary: The Fabric Decision Web

## Core Concept Evolution

**Initial Direction:** Session on misconceptions when IT and Business can't collaborate on Fabric

**Reframe:** Not a prescriptive "here's how to do it" but a diagnostic "here's what it depends on"

**Final Frame:** The Decision Web - helping people enter wherever their organization actually is, understand dependencies, and work outward

## Key Insights

### The "It Depends" Reality

Most Fabric guidance presents patterns as if they're universal. Reality: organizational context determines which patterns work. Key dependencies:
- Where you sit on the Business-IT spectrum
- Capability distribution across teams
- Risk appetite and regulatory requirements
- Cultural expectations around control vs autonomy
- Trust levels between teams
- Starting point (greenfield vs existing Power BI)

### Three Entry Points

Organizations typically enter Fabric implementation via one of three forcing functions:
1. **Capacity crisis** - "We've hit Power BI capacity limits"
2. **Architecture needs** - "We need better data engineering"
3. **Governance chaos** - "Control is breaking down"

Your entry point determines which decisions you tackle first, but all eventually need answering.

### Organic vs Locked-In Decisions

Critical distinction: some decisions are hard to change later, others can evolve.

**Hard to change:**
- Capacity topology (centralized vs distributed)
- Workspace boundaries (governance isolation points)
- Fundamental architecture choices (medallion vs not)

**Can iterate:**
- Enablement approaches
- Governance policies
- COE operating model
- Specific workspace patterns within broader topology

## The Six Decision Points

### 1. Capacity Organization
**What it depends on:**
- Organizational maturity with chargeback/showback
- Degree of usage variance across business units
- Trust level between teams
- Appetite for central management overhead

**Common patterns:**
- Single pooled capacity
- Capacity per business unit
- Hybrid approaches

**Pitfall:** One capacity per domain when you have 80 domains (PaaS thinking applied to SaaS)

### 2. Workspace Topology
**What it depends on:**
- Governance boundary needs
- Collaboration patterns
- Skill distribution
- Discoverability requirements

**Common patterns:**
- Per-domain workspaces
- Per-project workspaces
- Layer-based workspaces (Bronze/Silver/Gold)
- Function-based workspaces

**Pitfall:** Workspace-per-X without understanding workspace as governance boundary

### 3. Data Architecture Approach
**What it depends on:**
- Team skill composition (BI analysts vs data engineers)
- Data maturity (operational vs analytical)
- Integration needs (siloed vs cross-domain)

**Common patterns:**
- Source-driven (works for operational reporting)
- Domain-driven medallion
- Selective medallion

**Pitfall:** Source-driven Silver/Gold - applying BI patterns to data engineering, defeating medallion's purpose

### 4. User Enablement
**What it depends on:**
- Starting skill distribution
- Appetite for training investment
- Speed of adoption needed
- Support capacity

**Common patterns:**
- Self-guided learning
- Structured certification
- Graduated autonomy (ABN Amro model)
- Cohort-based rollout

**Pitfall:** Expecting self-service success without enablement investment

### 5. COE Structure & Role
**What it depends on:**
- Where you sit on Business-IT spectrum
- Organizational capability distribution
- Risk appetite
- Chosen enablement approach

**COE role varies:**
- Business-led: Governance + enablement
- Balanced: Platform management + support
- IT-led: Gatekeeper + delivery

**Pitfall:** COE structure that contradicts enablement model or organizational culture

### 6. Governance Philosophy
**What it depends on:**
- Risk profile of data
- Distribution of data skills (outcome of enablement!)
- Cultural appetite for central control

**Spectrum:**
- Full self-service with guardrails
- Approval-based with exceptions
- Central delivery with limited self-service

**Framework:** Spine vs skeleton - adjust spine length to capability × risk appetite

**Pitfall:** Uniform governance regardless of context

## Key Patterns from Zettelkasten

### Anti-patterns
- **PaaS mental models break when applied to SaaS** - Infrastructure thinking doesn't map to SaaS governance
- **Source-driven medallion trap** - Organizing Silver/Gold by source system instead of business domain
- **Skeleton vs spine** - Providing so much structure it prevents contextual adaptation

### Principles
- **Workspace as governance boundary** - The fundamental unit of isolation in Fabric
- **Graduated autonomy** - Capability-based permissions that evolve with user skill
- **Medallion as component not architecture** - It's a structured data management pattern, not the complete solution

## Recognition Patterns

These signal organizational mismatches rather than technical problems:
- Decisions stuck despite technical clarity
- Same questions recurring without resolution
- Proposed solutions don't match problem layer
- Decision-maker backgrounds don't match platform type

## Connection to Microsoft Guidance

Our angle is complementary, not redundant:
- **Microsoft Fabric Adoption Roadmap**: Prescriptive journey "how to succeed"
- **Our session**: Diagnostic tool "here's what it depends on"

Microsoft tells you patterns exist; we help you choose between them based on organizational reality.

## Session Philosophy

Not a linear implementation sequence, but a decision web:
- Enter wherever your organization forces the conversation
- Understand what each decision depends on
- Recognize which decisions are hard to reverse
- Make coherent choices that fit together
- Adapt iterative decisions as you learn

The goal: match implementation patterns to organizational reality, not force organizational change to fit implementation ideals.
