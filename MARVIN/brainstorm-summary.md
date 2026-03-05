# MARVIN Presentation — Brainstorm Summary

**Status:** Brainstorm
**Target audience:** Microsoft FTEs (Cloud Solution Architects, similar technical roles)
**Format:** Internal presentation

---

## Abstract (Draft)

> **Your AI Doesn't Remember Yesterday — Mine Does**
>
> Most AI assistants start every conversation from zero. No memory of what you decided last week, no awareness of your priorities, no continuity across sessions. As a Cloud Solution Architect, I needed something different — an AI that compounds knowledge over time, not one that forgets everything the moment I close the chat window.
>
> MARVIN is a text-based AI agent built on GitHub Copilot Agent mode with a persistent memory system stored as plain markdown files. It tracks my priorities, remembers decisions across engagements, maintains a knowledge base organized by customer and domain, and automates repetitive workflows through reusable prompt-based skills.
>
> In this session, I'll walk through the architecture of a working system: how different types of memory (session state, long-term observations, domain knowledge) serve different purposes; how prompt files and skills eliminate repetitive tasks like session handoffs, weekly reports, and structured thinking; and how managing the context window deliberately — loading only what's needed, when it's needed — keeps the system useful at scale.
>
> This isn't a demo of what's theoretically possible. It's a walkthrough of what I use every working day, and how it changes the quality of output when your AI actually knows who you are.

---

## Baseline Story (Core Talk)

Key themes to cover:
- **Memory types:** session state, long-term observations, domain knowledge — different purposes, different update cadences
- **Prompt-based skills:** automating repetitive workflows (session start/end, checkpoints, reports, structured thinking)
- **Context window management:** lazy-load protocol, index-first navigation, loading only what's needed
- **Actual workflow:** live walkthrough of a working day — `#marvin` → work → `#update` → `#end` → `#commit`

---

## Expansion Directions (Parked)

### Option A: Team-scoped MARVIN
- Shared `state/` and `content/` across a team repo
- Role-based memory; "what did my team decide about X last month?"
- **Fit:** resonates with managers and leads in the audience; "what if your whole team had this?"
- **Risk:** speculative — hasn't been built yet

### Option B: FoundryIQ deployment
- MARVIN as a deployed agent with managed memory, MCP server integrations, enterprise auth
- From personal tool to organizational capability
- **Fit:** ties to Microsoft product strategy; credible given the audience
- **Risk:** narrower; risks becoming a product pitch

### Option C: Deep dive on prompts, agents, and tools in GHCP
- Anatomy of a `.prompt.md` file, skill system as structured tool-use, MCP server wiring
- The lazy-load protocol as context window management
- **Fit:** lowest speculation risk; real artifacts to show; practitioners can replicate
- **Risk:** less visionary; more "tips & tricks"

**Recommendation:** Given the audience (Microsoft FTEs in similar roles), Option C is the strongest expansion — they can go build this themselves next week. Option A is a nice 2-minute "imagine if" closer.

---

## Open Questions
1. Do you want to demo live? A session-start → checkpoint → session-end loop would be compelling and short.
2. Is this presentation also the vehicle for the AI Chief of Staff framework vision, or keep it grounded in personal productivity?
3. Time slot — 20 min? 45 min? Shapes how deep the expansion can go.

---

## Next Actions
- [ ] Decide expansion angle (C recommended, A as closer)
- [ ] Outline 4-5 slides for the baseline story
- [ ] Identify 2-3 concrete before/after examples that show quality improvement
