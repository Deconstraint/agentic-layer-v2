# Observer Ranch — Active Tool Connections

## Confirmed Active
| Tool | Purpose | Status | Notes |
|---|---|---|---|
| Stripe | Retainer invoicing, ACH payments | ✅ Active | Daily automatic payouts to Mercury ••••6598 |
| Email (Resend) | Invoice delivery | ✅ Active | Sends from nathan@deconstraint.com |
| Trello | Project tracking | ✅ Active | Deconstraint Infrastructure board |

## Pending / To Configure
| Tool | Purpose | Status | Notes |
|---|---|---|---|
| Google Workspace | Drive, Docs, Calendar | ⚠️ Pending | Need Kat's service account or OAuth |
| Anthropic API | AI agent inference | ⚠️ Pending | Slot created in GoPass |
| OpenAI API | Fallback inference | ⚠️ Pending | Slot created in GoPass |
| Telegram | Notifications to Kat | ⚠️ Pending | Bot token slot in GoPass |

## Retainer Invoice System
- **Cron job:** `/mnt/c/MC/workspace/clawd/scripts/retainer-invoice-cron.sh`
- **Schedule:** 5th and 20th of every month at 9 AM MST
- **Invoice HTML template:** `/mnt/c/MC/workspace/clawd/RETAINER_INVOICE_HTML_EMAIL.html`
- **Payment link:** `https://buy.stripe.com/6oU14pbsa5Mg8m48H1ejK0b`
- **Fee:** $5 flat (ACH) — no Stripe invoicing module fee

## Active Clusters
- TBD — pending scoping conversation with Kat Davidson
- Likely candidates: Content Production, possibly SEO & Visibility

## Notes
- Observer Ranch is the first external client tenant
- Retainer structure: $5,800/month as two $2,900 installments
- GoPass namespace `observer-ranch/` created 2026-03-20
- Add tools as Kat's needs are scoped
