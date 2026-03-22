# Cluster 01 — SEO & Visibility

**Job:** Get deconstraint.com ranked. Produce content that climbs to page 1 and gets cited in AI answers.

This cluster is the top of the funnel. Everything else — leads, sales, revenue — depends on search visibility and AI brand presence. It runs first. It runs hardest.

---

## Current Mission

- Climb "what is mcp for small business owners" from position 5.0 to position 1-3
- Build topical authority around: AI adoption for SMBs, MCP for small business, Company Intelligence OS
- Get deconstraint.com cited in ChatGPT, Perplexity, and Google AI Overviews for category queries
- Grow Domain Rating by building legitimate editorial links
- Maintain 100/95 PageSpeed scores on the Astro site

---

## The 8-Agent Pipeline

```
Morpheus / Founders
         ↓
[Cluster Manager] — receives task, routes, tracks, reports
         ↓
[Technical SEO] ←→ [Content SEO] ←→ [AI SEO]
         ↓                ↓
[Content Writer] ← [brief from Content SEO]
         ↓
[Content Editor] ← quality gate, approves or returns
         ↓
[Link Builder] — earn authority for published content
         ↓
[Analytics] — measure everything, report weekly
```

### Agent Roster

| Agent | File | Primary Job |
|---|---|---|
| Cluster Manager | cluster-manager/SOUL.md | Receive, route, track, report |
| Technical SEO | technical-seo/SOUL.md | Crawlability, speed, schema, indexing |
| Content SEO | content-seo/SOUL.md | Keyword research, briefs, topical authority |
| AI SEO | ai-seo/SOUL.md | LLM brand audits, GEO, llms.txt, citation tracking |
| Content Writer | content-writer/SOUL.md | Produce content from brief |
| Content Editor | content-editor/SOUL.md | QA gate — AI signal removal, brand voice, SEO check |
| Link Builder | link-builder/SOUL.md | HARO, Digital PR, outreach |
| Analytics | analytics/SOUL.md | GSC pulls, rank tracking, weekly reports |

---

## The Content Brief — Core Handoff Artifact

The brief is what makes this pipeline work. Content SEO produces it. Content Writer executes it. Content Editor checks against it.

Without a brief, writers guess. With a brief, they execute. Every piece of content in this cluster starts with a brief.

**Brief location:** [orchestration/handoff-protocols/brief-template.md](../../orchestration/handoff-protocols/brief-template.md)

---

## Success Metrics

| Metric | Baseline | 90-Day Target |
|---|---|---|
| "what is mcp for small business owners" | Position 5.0, 26 impr | Position 1-3, 200+ impr |
| AI citation rate (target queries) | ~0% | >20% across ChatGPT/Perplexity/AIO |
| Total GSC impressions | Measure at start | +40% in 90 days |
| Domain Rating (Ahrefs) | Measure at start | +5 points in 6 months |
| Blog posts published | Measure | 8-12 posts in 90 days |
| Technical health score | 100/95 PageSpeed | Maintain 100/95 |

---

## Deconstraint Site Context

- **Platform:** Astro static site
- **Host:** Vercel (project: `deconstraint-solutions`)
- **Domain:** deconstraint.com
- **GSC property:** sc-domain:deconstraint.com + sc-domain:deconstraint.ai
- **PageSpeed:** Currently 100/95 — maintain these scores, never degrade
- **Content format:** Markdown → Astro components → static HTML
- **Blog directory:** /blog/[slug]

---

## Playbook References

All tactical playbooks live in the `Deconstraint/seo-department` repo:

| Topic | Path |
|---|---|
| Technical SEO | `/SEO/Technical_SEO/PLAYBOOK.md` |
| Content SEO | `/SEO/Content_SEO/PLAYBOOK.md` |
| Topical Authority | `/SEO/Content_SEO/Topical_Authority/PLAYBOOK.md` |
| Keyword Research | `/SEO/Research/Keyword_Research/PLAYBOOK.md` |
| Search Intent | `/SEO/Research/Search_Intent/PLAYBOOK.md` |
| AI SEO Overview | `/SEO/AI_SEO/OVERVIEW.md` |
| LLM Optimization | `/SEO/AI_SEO/LLM_Optimization/PLAYBOOK.md` |
| GEO | `/SEO/AI_SEO/Generative_Engine_Optimization/PLAYBOOK.md` |
| Prompt SEO | `/SEO/AI_SEO/Prompt_SEO/PLAYBOOK.md` |
| HARO | `/SEO/Link_Building/HARO/PLAYBOOK.md` |
| Digital PR | `/SEO/Link_Building/Digital_PR/PLAYBOOK.md` |
| Backlink Outreach | `/SEO/Link_Building/Backlink_Outreach/PLAYBOOK.md` |
| Analytics | `/SEO/Analytics/PLAYBOOK.md` |

---

## Weekly Operating Rhythm

| Day | Activity |
|---|---|
| Monday | Receive Intelligence Cluster briefing. Cluster Manager sets weekly content priorities. |
| Monday | Analytics agent pulls GSC data. Cluster Manager reviews performance vs. last week. |
| Tuesday | Content SEO produces 1-2 briefs based on keyword priorities. |
| Wednesday | Content Writer drafts content from brief. |
| Thursday | Content Editor reviews and approves or returns with notes. |
| Friday | Approved content published. Link Builder reviews new content for outreach opportunities. |
| Friday | Cluster Manager sends weekly report to founders via Telegram. |

---

## Approval Gates

- All outreach (journalist pitches, HARO responses, link requests) requires Nathan approval via Telegram before sending
- Content is published by the dev team after editor approval — agents don't push to production directly
- Schema changes and robots.txt updates require Travis review

---

*Cluster 01 is the foundation. Build it right before expanding to Clusters 02-04.*
