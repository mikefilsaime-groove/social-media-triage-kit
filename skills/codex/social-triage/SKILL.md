---
name: social-triage
description: Run a social-media-to-Notion executive triage workflow. Use when the user asks to triage social media, process DMs, review connection requests, moderate groups, route social support issues, or run social-triage.
---

# Social Triage

Use this skill to operate the Social Media Triage Kit.

## Required Context

Before acting, locate the kit root. Prefer the current repo root. Read these files when available:

- `templates/starter-rules.json`
- `templates/notion-social-rules-schema.md`
- `templates/notion-decision-inbox-schema.md`
- `docs/architecture.md`
- `docs/privacy-and-security.md`

If the user has a live Notion rules database, read that as the source of truth before applying starter rules.

## Core Objective

Keep the executive's social inbox quiet while preserving true decisions in Notion.

The social constitution is:

> Eliminate noise by default. Surface only real decisions, high-value relationships, delegated work, or genuine risk.

## Workflow

1. Read active social triage rules.
2. Verify authenticated access for each requested platform.
3. Stop and report any platform that is not authenticated.
4. Check authorized social surfaces only.
5. Classify each item against active rules.
6. Take clear low-risk actions only when authorized.
7. Create or update Notion decision items for true signal.
8. Delegate routine work according to rules.
9. Send urgent notifications only after the Notion item exists.
10. Summarize what changed.

## Browser And Authentication

Use the approved browser/session layer for the user's environment.

For Codex desktop, the in-app Browser is preferred when available.

Do not ask for or expose passwords, one-time codes, recovery codes, cookies, or private credentials.

If authentication blocks a platform, ask the user to complete it directly.

## Decision Item Requirements

Every Notion decision item should include:

- Stable triage ID
- Platform
- Source link
- Last activity date
- Sender or actor
- Exact ask
- Suggested action
- Summary
- Why it matters
- Rule match and confidence

The executive should be able to decide without opening the social platform.

## 911 Items

Treat these as urgent:

- Legal threats
- Regulatory escalation
- Extremely angry customers
- Public reputation risk
- Personal reach-outs the executive would likely want to know about immediately

For urgent items:

1. Create/update the Notion decision item.
2. Set priority to Urgent.
3. Send the configured urgent notification with triage ID, priority, one-line brief, and Notion URL.

## Safety

Allowed without extra confirmation when rules clearly authorize:

- Read social items
- Summarize messages or posts
- Create Notion items
- Ignore obvious spam
- Route support or operations items to delegates

Be careful with:

- Sending outbound social messages
- Deleting comments
- Banning users
- Accepting ambiguous friend or connection requests
- Handling legal, finance, payment, commission, refund, or personal items

If unsure, create a decision item instead of taking an irreversible action.

## Summary Format

End each run with:

- Platforms checked
- Items reviewed
- Low-risk actions taken
- Notion items created or updated
- Delegations made
- Urgent notifications attempted
- Authentication blockers
- Items needing a new rule
