# Credentials Map — Deconstraint

All credentials live in GoPass under the `deconstraint/` namespace. No credentials hardcoded anywhere. Agents reference GoPass paths.

---

## Google Workspace (GSC, Gmail, Sheets, Docs)

**Account:** travis@deconstraint.com (primary), sure.not.secure@gmail.com (MCTravis isolated)

**GSC Credentials:**
- CLIENT_ID: `gopass show -o deconstraint/google/gsc-client-id`
- CLIENT_SECRET: `gopass show -o deconstraint/google/gsc-client-secret`
- REFRESH_TOKEN: `gopass show -o deconstraint/google/gsc-refresh-token`

**Gmail (MCTravis agent):**
- Account: sure.not.secure@gmail.com
- Keyring password: `gopass show -o deconstraint/gog-keyring/password`

**Google Drive:**
- Primary workspace folder: https://drive.google.com/drive/folders/1FE6H_AeKNVJXHCI3PSpkcqytWHx0g0oP
- CRM Sheet: `1sV9pvnrt4w7C06vXaHo-ajw_SKZa1j688Ox7k2xKNp0`

**Google Calendar:**
- Primary: travis@deconstraint.com
- Shared: Check with Travis for collaborators

---

## GitHub

**Organization:** Deconstraint (https://github.com/Deconstraint)

**API Token:** `gopass show -o deconstraint/github/api-token`

**Repos:**
- agentic-layer-v2 (this one)
- seo-department
- deconstraint-site (main website repo)
- zeusops-grid (infrastructure)

---

## Vercel

**Project:** deconstraint-solutions
**Token:** `gopass show -o deconstraint/vercel/token`

Handles: deconstraint.com site deployments, Astro builds, environment variables

---

## Anthropic API

**Primary key:** `gopass show -o deconstraint/anthropic/primary`
**Backup key:** `gopass show -o deconstraint/anthropic/backup`

Used for: Claude API calls, agent context processing, embeddings

---

## Stripe (Payments)

**Key:** Already configured in Vercel environment
**Testing mode:** Use test keys for sandboxed testing before production

---

## Resend (Email Service)

**Send-only key:** `gopass show -o deconstraint/resend/send-only-key`
**Admin key:** `gopass show -o deconstraint/resend/admin-key`

**Sending email:** noreply@deconstraint.com

Used for: Automated emails from Cluster 02 (Growth/Email Marketer)

---

## Trello

**API Key:** `gopass show -o deconstraint/trello/api-key`
**Token:** `gopass show -o deconstraint/trello/token`

**Board:** Deconstraint (main project board)
- Columns: Backlog, Active, SEO, Growth, Sales, Intelligence, Done
- Each cluster updates their column weekly

---

## Other Services

**Ahrefs:** Access via shared account (check with Travis)
**Semrush:** Access via shared account (check with Travis)
**Google Trends:** Free, no auth needed
**Google Keyword Planner:** Tied to Google Ads account (access with marketing account)

---

## Access Control

All three co-founders (Travis, Nathan, Britton) have access to:
- All GoPass credentials
- GitHub organization
- Google Drive and Gmail
- Vercel
- Trello

**Agent access:** Agents reference GoPass paths, not hardcoded credentials. Never commit `.env` files with secrets.

---

## Security Rules

1. Never hardcode credentials in SOUL.md, config files, or code
2. All external service access uses GoPass as single source of truth
3. Never commit `.env` files or credential files to Git
4. Rotate sensitive keys quarterly
5. Use OAuth2 / service accounts where possible (avoid static API keys)
6. All outreach (email, social, API calls) logs are auditable

---

*Credential security = trust. Treat this seriously.*
