# Architecture — Agentic Layer V2

The system is not complex. But it has to be deliberate. This document explains the design decisions that make it work.

---

## Why Specialists Beat Generalists

BCG (2024) studied multi-agent AI systems across enterprise deployments. The finding: narrow specialists outperform generalists by **3x on task accuracy** and **2.8x on output quality** when tasks are domain-specific.

The intuition is obvious once you see it. A generalist agent has to maintain mental models for SEO, copywriting, paid media, CRM operations, and analytics simultaneously. A specialist agent has one job. Its entire context window is dedicated to that job. It makes fewer errors, uses fewer tokens, and produces better output.

This is why we run 28 specialists across 6 clusters instead of 6 generalists doing everything.

---

## The 4 Inter-Cluster Communication Patterns

Clusters don't talk to each other directly. They communicate through Morpheus or through defined pub/sub channels. There are four patterns:

### 1. Supervisor / Worker

Morpheus receives a goal from a founder and dispatches it to a Cluster Manager. The Cluster Manager breaks it into tasks and routes each task to the right specialist.

```
Founder → Morpheus → Cluster Manager → Specialist Agent
                                     → Specialist Agent
                                     → Specialist Agent
```

Used for: Most task execution. A founder says "write a post about MCP for SMBs." Morpheus routes to SEO Cluster Manager. Cluster Manager routes to Content SEO (brief), then Content Writer (draft), then Content Editor (QA).

### 2. Pub/Sub (Publish / Subscribe)

The Intelligence Cluster publishes a weekly briefing every Monday at 8 AM. Every other Cluster Manager is subscribed. They receive it automatically and adjust their weekly plans.

```
Intelligence Cluster → [publishes briefing] → SEO Cluster Manager
                                             → Growth Cluster Manager
                                             → Sales Cluster Manager
```

Used for: The weekly intelligence briefing. Trend alerts. Competitive changes.

### 3. Sequential Pipeline

Output from one cluster becomes input for the next. The Intelligence Cluster produces a competitive analysis. The SEO Cluster uses it to write content that positions against identified gaps. The Growth Cluster distributes that content.

```
Intelligence → brief → SEO Cluster → content → Growth Cluster → distribution
```

Used for: Content production pipeline. Research → write → distribute.

### 4. Parallel Dispatch

Morpheus fires tasks at multiple clusters simultaneously when they don't depend on each other.

```
Morpheus → SEO Cluster [keyword research]
         → Intelligence Cluster [competitor audit]
         → Sales Cluster [ICP refresh]
         [all three running concurrently]
```

Used for: Weekly initialization. Monthly audits. Any work that can parallelize.

---

## Morpheus — The Meta-Orchestrator

Morpheus is not an agent with a domain. It's the coordinator. It has one job: **get the right task to the right cluster with the right context.**

Morpheus:
- Receives goals from founders (Telegram, direct prompt)
- Identifies which cluster(s) to activate
- Loads the appropriate tenant context before dispatching
- Tracks cross-cluster project state
- Runs the pub/sub subscriptions (Intelligence → all clusters)
- Escalates to founders when a decision is needed
- Synthesizes multi-cluster outputs into a single founder briefing

Morpheus does not execute tasks. It routes and coordinates. The Cluster Manager executes.

See: [orchestration/MORPHEUS.md](./orchestration/MORPHEUS.md)

---

## The Tenant Configuration Model

The same agent logic runs for every client. The tenant config is what makes it client-specific.

### What Lives in Tenant Config

```
/tenants/[client]/
├── TENANT.md           ← Who the client is, what clusters are active, founders, goals
├── brand.md            ← Voice, forbidden words, tone rules, content pillars
├── credentials-map.md  ← All GoPass paths for this client's credentials
├── tools.md            ← Active tool connections and account IDs
└── priorities.md       ← Current focus: what matters this week/month
```

### How Agents Load Tenant Config

Before any task execution, the Cluster Manager loads:
1. `TENANT.md` — knows who they're working for, what clusters are active
2. `brand.md` — every content agent inherits these rules
3. `credentials-map.md` — knows where to get API keys, tokens, etc.
4. `tools.md` — knows which integrations are live
5. `priorities.md` — knows the current strategic focus

An agent running for Observer Ranch loads Observer Ranch's brand rules. An agent running for Deconstraint loads Deconstraint's brand rules. Same agent. Different tenant. Different output.

---

## The Brief as the Core Handoff Artifact

Content production in the SEO cluster flows through a structured brief. The brief is the handoff artifact — it's what the Content SEO agent produces and what the Content Writer agent consumes.

Without a brief, the writer guesses at intent, structure, and SEO requirements. With a brief, the writer executes. Zero ambiguity.

The canonical brief format is at: [orchestration/handoff-protocols/brief-template.md](./orchestration/handoff-protocols/brief-template.md)

The brief contains:
- Target keyword and search intent
- Current ranking position
- Title and meta description (pre-written, 50-60 / 150-160 chars)
- H2 structure (mapped to PAA questions)
- FAQ questions (3-5)
- Internal link targets
- Brand rules reminder
- CTA specification
- Schema type

The Content Editor uses the brief as the QA checklist. Every item in the brief gets verified before approval.

---

## Inter-Cluster Communication Protocols

Full documentation of all four patterns with worked examples is at: [orchestration/handoff-protocols/inter-cluster-handoff.md](./orchestration/handoff-protocols/inter-cluster-handoff.md)

---

## The RSI Learning Layer

RSI (Reinforcement from Session Intelligence) is the feedback loop that makes the system smarter over time.

How it works:
1. Every agent session produces outcomes — rankings, conversions, open rates, etc.
2. RSI captures which strategies produced good outcomes and which didn't
3. Insights are distilled into the agent's SOUL.md files (updated periodically)
4. The next run of the agent benefits from the accumulated learning

This is not a technical ML system. It's a human-in-the-loop feedback process. Travis or Nathan review outcomes, distill lessons, and update SOUL.md files. The SOUL.md is the agent's long-term memory.

### RSI Update Cadence
- Weekly: Analytics agent produces performance summary → founders review
- Monthly: Cluster Managers update their agent SOUL.md files with lessons learned
- Quarterly: Architecture review — are clusters producing the right outcomes? Do any SOULs need rebuilding?

---

## Security Model

- All credentials live in GoPass under `deconstraint/` or `observer-ranch/` namespaces
- No credentials are ever hardcoded in agent SOUL.md files
- Agents reference GoPass paths, not values
- All outreach (email, social posts, journalist pitches) requires human approval before sending
- The only exception is GSC data pulls and Trello board writes — these are fully autonomous

---

## Data Flow Summary

```
Founders
    ↓ (goal)
Morpheus + Tenant Config
    ↓ (dispatches with context)
Cluster Manager
    ↓ (routes to specialists)
Specialist Agents
    ↓ (produce outputs)
Cluster Manager
    ↓ (synthesizes)
Morpheus
    ↓ (reports)
Founders
```

Intelligence Cluster runs in parallel and feeds all clusters via pub/sub. It's the ambient signal layer — not blocking, always enriching.

---

*Architecture validated against BCG "Specialist vs. Generalist AI Agent" research, 2024.*
*Updated: 2026-03*
