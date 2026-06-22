# Social Media Triage Kit

A local-first AI social inbox operating system for founders, executives, creators, and small teams who want social platforms checked without letting DMs, comments, connection requests, and group moderation become a second full-time inbox.

This is a signal-to-noise ratio tuner for social media. It treats social platforms as streams of attention requests, filters routine noise, escalates true risk, routes routine work, and preserves only the messages that deserve human judgment.

All names, companies, groups, contacts, and rules in this repo are fictional examples. Replace them with your own local configuration during install.

## What This Creates

- A Notion **Social Triage Rules** database that acts like a live policy table.
- A Notion **Decision Inbox** database for social items that need the executive.
- Starter rules for DMs, connection requests, group moderation, support, partnerships, commission disputes, legal threats, angry customers, and personal reach-outs.
- Portable Codex and Claude Code skill folders.
- A white paper explaining the operating model and signal-to-noise philosophy.
- Install documentation for both Codex and Claude Code.

## Recommended Stack

Recommended:

- Codex desktop or Codex CLI
- In-app Browser or another approved authenticated browser/session layer
- Notion MCP/plugin or Notion API credentials
- Optional text/iMessage notification bridge for urgent alerts

Also supported conceptually:

- Claude Code with equivalent browser/account access and Notion access
- Platform APIs where available and compliant with platform terms

## Quick Start

1. Read [WHITEPAPER.md](WHITEPAPER.md).
2. Review [INSTALL.md](INSTALL.md).
3. Create the Notion databases from the schemas in [templates/](templates/).
4. Import or recreate the starter rules from [templates/starter-rules.json](templates/starter-rules.json).
5. Install the relevant skill folder for Codex or Claude Code.
6. Authenticate each social platform in the approved browser/session layer.
7. Run a manual dry run before scheduling automation.

## Repo Map

```text
docs/          Architecture and privacy notes
examples/      Sanitized fictional examples for teaching
skills/        Portable Codex and Claude Code skill folders
templates/     Notion schemas and starter rules
```

## Important Reality Check

There is no honest one-click setup for social media triage because each user must authenticate their own accounts and decide what the agent is allowed to do. This kit provides the pattern, schemas, starter rules, and skills. You still need to connect your own Notion workspace and social accounts.

## Privacy Promise

This repo should never include real executive names, employee names, client names, phone numbers, OAuth tokens, browser session secrets, personal accounts, private groups, real message examples, or private business rules.

## License

MIT open source. See [LICENSE](LICENSE).
