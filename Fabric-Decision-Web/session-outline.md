# Session Outline: The Fabric Decision Web

## Structure Overview

**Part 1: Diagnosis (20%)** - Where is your organization forcing the conversation?
**Part 2: The Decision Web (60%)** - Six decision points with dependencies
**Part 3: Coherence Check (20%)** - Do your decisions fit together?

---

## Part 1: Diagnosis (~10-15 minutes)

### Opening: Three Entry Points

Most organizations enter via one of three forcing functions:

1. **"We've hit Power BI capacity limits"** → Enters via capacity/cost concerns
2. **"We need better data engineering"** → Enters via architecture/medallion
3. **"Governance is chaos"** → Enters via COE/control concerns

**Key message:** Your entry point determines which decisions you tackle first, but all decisions eventually need answering - and they constrain each other.

### The Business-IT Spectrum

Where does your organization sit?

- **Business-led:** Power BI culture, self-service first, IT enables
- **Balanced:** Collaboration between business and IT, shared ownership
- **IT-led:** Infrastructure first, governance-heavy, controlled delivery

**Key message:** Neither end is "wrong" - but your position determines which patterns make sense. The trap is applying patterns from the wrong end of the spectrum.

---

## Part 2: The Decision Web (~35-45 minutes)

For each decision point:
1. What forces this decision?
2. What does it depend on?
3. Common patterns for different org types
4. Dependencies on other decisions
5. Which choices lock you in vs can evolve
6. Pitfall example

### Decision 1: Capacity Organization

**What forces this decision:**
- Cost visibility requirements
- Capacity throttling issues
- Political budget ownership

**What it depends on:**
- Organizational maturity with chargeback/showback
- Degree of usage variance across business units
- Trust level between teams
- Appetite for central management overhead

**Common patterns:**
- Single pooled capacity (high trust, variable usage, sophisticated chargeback)
- Capacity per business unit (low trust, predictable usage, simple cost allocation)
- Hybrid (dev/test pooled, production separated)

**Dependencies:**
- ← Workspace topology (determines capacity assignment granularity)
- ← COE structure (determines who manages/allocates)
- → Governance philosophy (pooled = trust needed)

**Lock-in factor:** HIGH - Changing capacity topology after deployment is organizationally and technically painful

**Pitfall:** One capacity per domain when you have 80 domains (KPN example) - PaaS thinking applied to SaaS

---

### Decision 2: Workspace Topology

**What forces this decision:**
- Collaboration friction
- Security/isolation requirements
- Discoverability problems

**What it depends on:**
- Governance boundary needs (what must be isolated vs what benefits from sharing)
- Collaboration patterns (within-team vs cross-team)
- Skill distribution (centralized data eng vs distributed analysts)
- Discoverability requirements

**Common patterns:**
- Per-domain workspaces (data mesh, high autonomy)
- Per-project workspaces (campaign-based work, temporary teams)
- Layer-based workspaces (Bronze/Silver/Gold separation)
- Function-based workspaces (centralized data eng + distributed consumption)

**Dependencies:**
- ← Data architecture (medallion layers might drive workspace separation)
- ← Existing org structure (mirroring domains/teams/functions)
- → User enablement (affects who can create/manage workspaces)

**Lock-in factor:** MEDIUM-HIGH - Workspace boundaries are governance boundaries; restructuring later is painful

**Pitfall:** Workspace-per-[X] without understanding workspace as governance boundary. Trying to enforce governance WITHIN workspaces instead of THROUGH workspace design.

---

### Decision 3: Data Architecture Approach

**What forces this decision:**
- Integration needs across sources
- Skill gaps showing up in delivery
- Data quality issues

**What it depends on:**
- Team skill composition (BI analysts vs data engineers)
- Data maturity (operational reports vs analytical platform)
- Integration needs (siloed vs cross-domain analytics)

**Common patterns:**
- Source-driven (works for operational reporting, not analytical integration)
- Domain-driven medallion (Silver organized by business domain, not source)
- Selective medallion (only where domain modeling adds value)

**Dependencies:**
- ← Existing team skills (BI analysts vs data engineers)
- → Workspace topology (where do Bronze/Silver/Gold live?)
- ← COE capability (who can guide/review architecture?)

**Lock-in factor:** MEDIUM - Fundamental approach is hard to change, but implementation details can evolve

**Pitfall:** Source-driven Silver and Gold - 25 sources = 25 parallel pipelines. Applying BI thinking (connect to sources, transform) to data engineering. Defeats medallion's purpose of progressive domain modeling.

---

### Decision 4: User Enablement

**What forces this decision:**
- Failed self-service attempts
- Skill gaps blocking adoption
- Support burden overwhelming team

**What it depends on:**
- Starting skill distribution
- Appetite for training investment
- Speed of adoption needed
- Support capacity

**Common patterns:**

| Approach | Works when | Looks like |
|---|---|---|
| Self-guided learning | High baseline skills, low risk data | Documentation, examples, community |
| Structured certification | Variable skills, need to verify capability | Training paths, assessments, progression |
| Graduated autonomy | Want to match freedom to capability | ABN Amro model - certification unlocks features |
| Cohort-based rollout | Need controlled adoption | Wave 1 (power users) → Wave 2 → Wave 3 |

**Dependencies:**
- ← Current skill distribution (starting point)
- → Governance philosophy (capability determines freedom)
- ← COE structure (who delivers enablement?)

**Lock-in factor:** LOW - Enablement approaches can and should evolve

**Pitfall:** Expecting self-service success without enablement investment. Or: enablement model that contradicts governance philosophy (training people for autonomy while maintaining gatekeeper governance).

---

### Decision 5: COE Structure & Role

**What forces this decision:**
- Existing Power BI COE insufficient
- Delivery bottlenecks
- Governance failures

**What it depends on:**
- Where you sit on Business-IT spectrum (determines natural COE role)
- Organizational capability distribution
- Risk appetite
- Chosen enablement approach (COE often owns this)

**COE role varies:**

| Organization Type | COE Primary Role | Key Activities |
|---|---|---|
| Business-led | Governance + enablement | Standards, training, capability building |
| Balanced | Platform management + support | Architecture patterns, troubleshooting, reviews |
| IT-led | Gatekeeper + delivery | Requirements, development, deployment |

**The graduated autonomy bridge:** COE role can shift based on team capability - heavy support for beginners, light governance for advanced users.

**Dependencies:**
- ← Business-IT spectrum position
- → User enablement (COE owns or supports)
- → Governance philosophy (COE enforces or enables?)

**Lock-in factor:** LOW-MEDIUM - COE structure can evolve, but cultural expectations are sticky

**Pitfall:** IT-led gatekeeper COE in a self-service culture (or vice versa). COE structure that contradicts enablement model.

---

### Decision 6: Governance Philosophy

**What forces this decision:**
- Compliance requirements
- Data incidents
- Cultural tension between control and autonomy

**What it depends on:**
- Risk profile (regulatory, competitive, reputational)
- User enablement maturity (can't have light governance without capability)
- Cultural appetite for central control

**Spectrum:**
- Full self-service with guardrails (high skill, low risk, high trust)
- Approval-based with exceptions (mixed skill, moderate risk)
- Central delivery with limited self-service (low skill, high risk)

**Framework: Spine vs Skeleton**

Provide enough structure to enable coherence without so much rigidity that you prevent contextual adaptation.

- **Spine:** Supports multiple approaches, allows flexibility at edges
- **Skeleton:** Locks you into one specific form

Spine length is variable, determined by: risk appetite × capability

**Dependencies:**
- ← Risk profile
- ← User enablement maturity
- → All other decisions (governance is the "why" behind most choices)

**Lock-in factor:** LOW - Governance policies should evolve with capability and understanding

**Pitfall:** Uniform governance regardless of context. Treating graduated autonomy as "all or nothing" instead of capability-based progression.

---

## Part 3: Coherence Check (~10-15 minutes)

### Do Your Decisions Fit Together?

**Examples of incoherent combinations:**
- IT-led gatekeeper COE + expectation of viral self-service adoption
- Graduated autonomy enablement + uniform restrictive governance
- Pooled capacity + zero trust between business units
- Source-driven architecture + goal of cross-domain analytics

**Examples of coherent patterns:**

**Business-led organization:**
- Single pooled capacity with sophisticated chargeback
- Function-based workspaces (data eng + distributed consumption)
- Domain-driven medallion for integration
- Graduated autonomy enablement
- COE focused on governance + enablement
- Self-service with guardrails governance

**IT-led organization:**
- Capacity per business unit for clear cost attribution
- Layer-based workspaces (Bronze/Silver/Gold separation)
- Centrally-managed medallion architecture
- Structured certification enablement
- COE as gatekeeper + delivery
- Approval-based governance with exceptions

### The Hard Truth

You can't optimize for everything. Business-led and IT-led make different tradeoffs - both valid.

Most organizations can't articulate specific outcomes beyond "we should use data more." That's fine - but it means your implementation choices should optimize for **organizational fit and learning capacity**, not some theoretical end-state.

Build what matches how your organization actually works, then evolve.

### Key Recognition Patterns

These signal organizational mismatches, not technical problems:
- Decisions stuck despite technical clarity
- Same questions recurring without resolution
- Proposed solutions don't match problem layer
- Decision-maker backgrounds don't match platform type

### Wrap-up Message

Stop debating universal "best practices." Start making choices that:
1. Match your organizational reality
2. Are coherent across decision points
3. Distinguish what locks you in from what can evolve
4. Build learning into your implementation approach

---

## Appendix: Time Allocation for Different Session Lengths

**45-minute session:**
- Part 1 (Diagnosis): 10 min
- Part 2 (Decision Web): 25 min (~4 min per decision)
- Part 3 (Coherence): 10 min

**60-minute session:**
- Part 1 (Diagnosis): 12 min
- Part 2 (Decision Web): 38 min (~6 min per decision)
- Part 3 (Coherence): 10 min

**75-minute session:**
- Part 1 (Diagnosis): 15 min
- Part 2 (Decision Web): 45 min (~7-8 min per decision)
- Part 3 (Coherence): 15 min
