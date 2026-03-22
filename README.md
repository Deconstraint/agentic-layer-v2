# Agentic Layer V2 — Company Intelligence OS

This is the operating brain of Deconstraint. It replaces 136 stub agents across 12 corporate departments with a leaner, smarter architecture: 6 functional clusters, ~28 fully-specified agents, designed to produce real outcomes from day one.

---

## What This Is

The Agentic Layer V2 is a cluster-based AI agent system. Every agent in this repo has a job, a workflow, and a clear handoff protocol. There are no generalist agents. There are no stubs.

The system is built around one principle: **narrow specialists beat generalists by 3x on accuracy** (BCG, 2024). An agent that only does keyword research does it better than one that also writes copy, manages ads, and files invoices.

---

## Philosophy

**Cluster-based.** Six clusters, each owning a functional domain. Agents inside a cluster specialize. Clusters communicate through defined protocols — not ad hoc prompts.

**Outcome-driven.** Every cluster has a measurable job. Cluster 1 gets deconstraint.com ranked. Cluster 3 closes deals. Not "assist with SEO tasks." Ranked. Closed.

**Tenant-configured.** The same agent architecture runs for Deconstraint and for clients like Observer Ranch. The agent logic doesn't change. The tenant config does. Brand voice, credentials, priorities, tools — all in `/tenants/[client]/`.

**Multi-client from day one.** We built this to scale to 10+ tenants. The tenant model isn't an afterthought.

---

## Clusters

| # | Cluster | Status | Job |
|---|---|---|---|
| 01 | SEO & Visibility | 🟢 Active | Rank deconstraint.com. Get cited in AI answers. |
| 02 | Growth & Demand | 🟡 Active | Drive qualified leads via paid, email, and social. |
| 03 | Sales | 🟡 Active | Convert leads to $5,800/mo+ retainer clients. |
| 04 | Intelligence | 🟡 Active | Weekly briefings that feed all other clusters. |
| 05 | Customer Success | ⚪ Stub | Build when first 5 clients are live. |
| 06 | Engineering | ⚪ Stub | ZeusOps already handles this. |

---

## How to Use

### 1. Load tenant config
Every agent session starts by loading the tenant:

```
Load: /tenants/deconstraint/TENANT.md
Load: /tenants/deconstraint/brand.md
Load: /tenants/deconstraint/credentials-map.md
Load: /tenants/deconstraint/tools.md
Load: /tenants/deconstraint/priorities.md
```

### 2. Load the cluster
Then load the cluster context:

```
Load: /clusters/01-seo-visibility/CLUSTER.md
```

### 3. Load the agent
Then load the specific agent SOUL.md:

```
Load: /clusters/01-seo-visibility/content-seo/SOUL.md
```

### 4. Give it a task
The agent has everything it needs. Give it a specific task and it executes.

---

## Build Order

We're not building all six clusters at once. That's how you get 136 stubs.

**Phase 1 (Now):** Cluster 01 — SEO & Visibility. This is the one that builds the top of the funnel. Every other cluster depends on traffic and authority. Get this working first.

**Phase 2:** Cluster 04 — Intelligence. Weekly briefings that make every other cluster smarter. Should be running within 30 days of Cluster 01.

**Phase 3:** Cluster 02 — Growth & Demand. Launch content calendar on X and LinkedIn. Start email nurture.

**Phase 4:** Cluster 03 — Sales. When leads are flowing, automate the qualification and outreach pipeline.

**Phase 5:** Cluster 05 — Customer Success. When we have 5+ paying clients, build the retention and expansion system.

---

## Architecture

See [ARCHITECTURE.md](./ARCHITECTURE.md) for the full technical architecture — communication patterns, Morpheus orchestration, tenant model, and the RSI learning layer.

---

## Tenants

| Tenant | Status | Monthly Value |
|---|---|---|
| deconstraint | Internal (owner) | — |
| observer-ranch | Active client | $5,800/mo |

---

## Repo Structure

```
agentic-layer-v2/
├── README.md                    ← You are here
├── ARCHITECTURE.md              ← Technical architecture
├── clusters/                    ← All agent clusters
│   ├── 01-seo-visibility/       ← 8 agents
│   ├── 02-growth-demand/        ← 5 agents
│   ← 03-sales/                  ← 5 agents
│   ├── 04-intelligence/         ← 5 agents
│   ├── 05-customer-success/     ← Stub
│   └── 06-engineering/          ← Stub (ZeusOps)
├── tenants/                     ← Per-client configuration
│   ├── deconstraint/
│   └── observer-ranch/
└── orchestration/               ← Morpheus + handoff protocols
    ├── MORPHEUS.md
    └── handoff-protocols/
```

---

*Built by Deconstraint. Architecture validated by BCG research on specialist vs. generalist agent performance.*
*Last updated: 2026-03*
