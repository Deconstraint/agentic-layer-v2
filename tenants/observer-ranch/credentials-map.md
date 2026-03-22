# Observer Ranch — Credentials Map

All credentials stored in GoPass under `observer-ranch/` namespace.

## GoPass Namespace
```
observer-ranch/
├── anthropic/api-key
├── google/service-account
├── openai/api-key
├── stripe/secret-key
├── stripe/webhook-secret
└── telegram/bot-token
```

## Access Pattern
```bash
# Get any credential
gopass show -o observer-ranch/<path>

# Examples
gopass show -o observer-ranch/stripe/secret-key
gopass show -o observer-ranch/anthropic/api-key
```

## Retainer / Billing
- **Stripe secret key:** `gopass show -o observer-ranch/stripe/secret-key`
- **Stripe webhook secret:** `gopass show -o observer-ranch/stripe/webhook-secret`
- **Payment link (ACH $2,900):** `https://buy.stripe.com/6oU14pbsa5Mg8m48H1ejK0b`
- **Invoice prefix:** INV-NNN (INV-001 = March 5, INV-002 = March 20, etc.)
- **Billing contact:** Kat Davidson — kat@observerranch.com
- **Invoice sender:** Nathan Beckham — nathan@deconstraint.com

## Communication
- **Primary contact:** Kat Davidson (kat@observerranch.com)
- **Telegram bot token:** `gopass show -o observer-ranch/telegram/bot-token` (if configured)

## AI / Automation
- **Anthropic API key:** `gopass show -o observer-ranch/anthropic/api-key`
- **OpenAI API key:** `gopass show -o observer-ranch/openai/api-key`

## Google
- **Service account:** `gopass show -o observer-ranch/google/service-account`
- Google Workspace scope: TBD — needs confirmation from Kat

## Status Notes
- GoPass namespace created 2026-03-20
- Most slots are placeholders — populate as Kat provides credentials
- Stripe payment link confirmed active (INV-001 and INV-002 sent)
- All other credentials pending client onboarding
