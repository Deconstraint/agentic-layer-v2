# Inter-Cluster Communication Protocols

Four patterns for how clusters communicate and hand off work.

---

## Pattern 1: Supervisor / Worker

**When used:** Most task execution. A founder or Morpheus dispatches work to a Cluster Manager, who breaks it into tasks and routes each to specialists.

**Flow:**
```
Founder/Morpheus → Cluster Manager → Specialist 1
                                  → Specialist 2
                                  → Specialist 3
```

**Deconstraint example: "Rank 'what is MCP for SMBs' in top 3"**

```
Nathan (founder) → SEO Cluster Manager

Cluster Manager breaks into subtasks:
1. Content SEO → Keyword research, brief production (Tuesday)
2. Content Writer → Draft from brief (Wednesday)
3. Content Editor → QA, approve (Thursday)
4. Technical SEO → Schema, page speed, crawl test (Friday)
5. AI SEO → Optimize for AI citation (Friday)
6. Link Builder → Identify outreach opportunities (Friday)

Cluster Manager tracks all subtasks.
Cluster Manager reports status to Nathan weekly.
When content ranks top 3, Cluster Manager notifies Nathan.
```

**Handoff artifact:** Content Brief (Content SEO → Content Writer), QA Checklist (Content Writer → Content Editor), Published article + metrics (Cluster Manager → founder)

**Success:** Task completed on time, to spec, with measurable outcome

---

## Pattern 2: Pub/Sub (Publish / Subscribe)

**When used:** The Intelligence Cluster publishes information that all other clusters should see and act on (or ignore). Subscribers pull what's relevant to them.

**Flow:**
```
Intelligence Cluster (publishes every Monday 8 AM)
         ↓
    [Intelligence Briefing]
         ↓
    ┌────┬─────┬──────┐
    ↓    ↓     ↓      ↓
   SEO Growth Sales Morpheus
 (Cluster 01-04)
```

**What's in the Intelligence briefing:**
1. Competitive activity (who moved, what did they publish, gaps identified)
2. Keyword trends (new opportunities, search volume shifts)
3. AI search updates (ChatGPT, Perplexity, Google AIO changes)
4. Industry news and signals
5. 2-3 actionable recommendations for other clusters

**How other clusters consume it:**

**SEO Cluster Manager:** "New AI search feature on Perplexity — affects citation strategy. Forwarding to AI SEO agent for review. Adding to Wednesday priorities."

**Growth Cluster Manager:** "Emerging trend: [trending topic]. Recommending 3 social posts on this angle. Assigning to Social Strategist."

**Sales Cluster Manager:** "Competitor launched new positioning. Worth mentioning in discovery calls as differentiation. Adding to objection-handling docs."

**Handoff artifact:** The briefing itself (markdown doc, Trello card, or Slack message)

**Success:** Briefing published on time, 80%+ of recommendations actioned by other clusters

---

## Pattern 3: Sequential Pipeline

**When used:** Output from one cluster becomes input for the next. Work is sequential by design — later stages depend on earlier stages completing.

**Flow:**
```
Cluster A (produces output)
         ↓
    [Handoff artifact]
         ↓
     Cluster B (consumes, transforms)
         ↓
    [New output]
         ↓
     Cluster C (consumes, executes)
```

**Deconstraint example: Full content launch → distribution → sales capture**

```
Week 1-2: Intelligence Cluster
   - Competitive research
   - Keyword trends
   - Market opportunity analysis
   - Produces: Intelligence briefing + research doc

      ↓ (Briefing feeds into...)

Week 2-4: SEO Cluster
   - Content SEO reads briefing
   - Identifies priority keywords
   - Produces content brief
   - Content Writer drafts
   - Content Editor approves
   - Produces: Published blog post

      ↓ (Publishes, then...)

Week 4-5: Growth Cluster
   - Receives published article
   - Plans distribution via X, LinkedIn, email
   - Creates social clips, email sequences
   - Distributes to audience
   - Produces: Social posts, email broadcasts, web traffic

      ↓ (Drives traffic that generates...)

Week 5+: Sales Cluster
   - Receives inbound from content + distribution
   - Qualifies leads
   - Sends targeted follow-up sequences
   - Converts to customers
   - Produces: Closed deals
```

**Handoff artifacts:**
1. Intelligence briefing → SEO Cluster Manager
2. Published article → Growth Cluster Manager
3. Prospect list from content traffic → Sales Cluster Manager
4. Deal closed → Morpheus → Founders

**Success:** Content ranks, gets distributed, generates inbound, converts to customers

---

## Pattern 4: Parallel Dispatch

**When used:** Multiple clusters execute simultaneously when their work doesn't depend on each other.

**Flow:**
```
            Morpheus
              ↓
    ┌─────────┼─────────┐
    ↓         ↓         ↓
 Cluster A  Cluster B  Cluster C
[task 1]    [task 2]   [task 3]
    ↓         ↓         ↓
  Results  Results  Results
    └─────────┼─────────┘
              ↓
         Synthesized output
              ↓
           Founders
```

**Deconstraint example: Weekly initialization**

```
Monday 8:00 AM: Morpheus starts the week

Parallel execution:
1. Intelligence Cluster → Produce weekly briefing
2. Analytics Agent → Pull GSC data, calculate position changes
3. SEO Cluster Manager → Read briefing, set week's priorities
4. Growth Cluster Manager → Read briefing, adjust social calendar

By Monday 10:00 AM:
- Briefing complete
- Analytics data ready
- SEO priorities set
- Growth calendar updated

Morpheus compiles weekly summary for founders by 10:30 AM.
All clusters are synchronized and moving forward.
```

**Another example: Competitive audit across multiple dimensions**

```
Dispatch simultaneously:
1. SEO Cluster → Analyze competitor rankings and content
2. Growth Cluster → Analyze competitor social strategy
3. Sales Cluster → Analyze competitor positioning and messaging
4. Intelligence Cluster → Compile into holistic competitive report

Results feed into strategic planning.
```

**Handoff artifacts:** Each cluster produces its output on the normal schedule. Morpheus synthesizes.

**Success:** Multiple parallel workstreams complete within the same time window, with no waiting or blocking

---

## Communication Standards

### All Handoff Artifacts Must Include:

1. **Owner/sender:** Who produced this?
2. **Date:** When was this produced?
3. **Status:** Is this ready for consumption or still in draft?
4. **Receiver/next action:** Who should receive this? What should they do with it?
5. **Deadline:** When does the receiver need to act?
6. **Success criteria:** How do we know this handoff worked?

### Example handoff format:

```
FROM: Content SEO Agent
TO: Content Writer
DATE: 2026-03-21
STATUS: ✅ Ready for draft

BRIEF: "What is MCP for small business owners"
TARGET KEYWORD: "what is mcp for small business owners"
DEADLINE: Draft due Thursday EOD

SUCCESS CRITERIA: Writer produces 2000-2500 word draft that
- Follows brief exactly
- Has keyword in first 100 words
- Includes all H2s from brief
- Includes all 4 FAQ questions
- Zero AI writing signals
- Passes read-aloud test

NEXT STEP: Writer produces draft. Editor reviews. Publish Friday.
```

---

## Failure Modes & Recovery

**Failure: Handoff artifact unclear or incomplete**
- Result: Receiver has to ask clarifying questions. Work is delayed.
- Recovery: Sender produces complete replacement artifact within 2 hours. Include all missing information.

**Failure: Receiver misses deadline**
- Result: Next cluster can't start. Pipeline delays.
- Recovery: Escalate to Morpheus/founders immediately. Reassign work if needed. Don't wait silently.

**Failure: Output doesn't meet brief/spec**
- Result: Waste of time. Rework. Delays compound.
- Recovery: Content Editor (for SEO) or Cluster Manager (for others) returns work with specific notes. Sender revises within 4 hours.

**Failure: Clusters working at cross-purposes**
- Result: Conflicting strategy, wasted effort.
- Recovery: Morpheus intervenes. Clarify intent to both clusters. Get them synchronized.

---

*Clear handoffs = predictable flow. Ambiguous handoffs = chaos. Write them down.*
