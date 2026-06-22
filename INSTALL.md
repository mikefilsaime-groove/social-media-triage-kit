# Install Guide

This package is designed to be installed locally by a founder, operator, or technical assistant.

The setup works with Codex or Claude Code, as long as the agent has:

- Safe authenticated access to the social platforms you want triaged
- Notion access
- Permission to create or update decision inbox items
- Optional notification-channel access for urgent alerts

## Prerequisites

- A Notion workspace
- Codex or Claude Code
- Authenticated browser/session access for the social platforms you choose
- Optional text, iMessage, Slack, or chat notification bridge for urgent alerts

Recommended social surfaces:

- LinkedIn connection requests and DMs
- Facebook friend requests
- Messenger DMs
- Facebook Groups moderation queues

## Step 1: Create Notion Databases

Create two Notion databases from these schemas:

- [templates/notion-social-rules-schema.md](templates/notion-social-rules-schema.md)
- [templates/notion-decision-inbox-schema.md](templates/notion-decision-inbox-schema.md)

The rules database is the live control plane. The decision inbox is where the agent places items that need executive judgment.

## Step 2: Import Starter Rules

Start from:

- [templates/starter-rules.json](templates/starter-rules.json)

Import them manually or recreate them in Notion.

Then edit the fictional roles and addresses:

```text
Executive
Support Lead
Operations Lead
Partnership Lead
Finance Lead
Community Manager
Legal/Ops Lead
```

Replace all `example.com` values with your own local delegates. Do not commit private names or contact details to GitHub.

## Step 3: Authenticate Social Accounts

Authenticate each social platform in the approved browser/session layer for your agent.

For Codex, the in-app Browser is recommended when available because it keeps the flow visible and local.

For Claude Code, use the browser/session access pattern available in your environment, or use official platform APIs where appropriate.

Do not paste passwords, one-time codes, recovery codes, or session cookies into chat or repo files.

## Step 4: Install The Codex Skill

Copy or symlink:

```text
skills/codex/social-triage
```

into your Codex skills directory.

Then ask Codex:

```text
Run social-triage.
```

For scheduled runs, create a local Codex automation that points to your kit folder and tells Codex to read the rules database each run.

Suggested schedule:

```text
11:00 AM, 1:00 PM, and 5:00 PM local time
```

## Step 5: Install The Claude Code Skill

Copy or symlink:

```text
skills/claude/social-triage
```

into your Claude Code skills directory.

Then ask Claude Code:

```text
Run social-triage.
```

If Claude Code does not have browser access, run the workflow with official APIs or ask it to produce a triage checklist instead of taking platform actions.

## Step 6: First Dry Run

Run a dry run before allowing account-affecting actions.

Ask the agent to:

```text
Review social triage surfaces and create a run summary, but do not send messages, approve requests, reject requests, delete comments, or ban users.
```

Review:

- Which platforms were accessible
- Which rules matched
- Which items would have gone to Notion
- Which items would have been delegated
- Which items would have triggered urgent notifications

## Step 7: Enable Limited Actions

After the dry run, enable low-risk actions first:

- Ignore obvious spam
- Create Notion decision items
- Route support requests to a support delegate
- Route partnership requests to a partnership delegate

Be more careful with:

- Sending social replies
- Accepting connection requests
- Approving member requests
- Deleting comments
- Banning users

## Step 8: Configure Urgent Notifications

Urgent notifications are optional.

Use them only for 911 items, such as:

- Legal threats
- Extremely angry customers
- Public reputation risk
- Personal reach-outs the executive should know about immediately

Recommended format:

```text
Triage ID
Priority
One-line brief
Notion decision item URL
```

Keep the full sensitive context in Notion, not in the text message.

## Step 9: Improve Rules Over Time

The best rule updates come from corrections:

```text
This should not have reached me. Suppress this next time.
```

```text
Always escalate messages like this.
```

```text
Route this type of request to the support lead.
```

The Notion rules database should remain the live source of truth.
