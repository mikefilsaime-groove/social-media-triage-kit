# Architecture

The Social Media Triage Kit uses four layers.

## 1. Social Sources

Authenticated social platforms provide the input stream.

Examples:

- LinkedIn DMs
- LinkedIn connection requests
- Facebook friend requests
- Messenger DMs
- Facebook Groups member requests
- Facebook Groups pending posts
- Community comments

The agent should only use accounts and groups explicitly authorized by the user.

## 2. Notion Rules Database

The rules database is the control plane.

The agent reads active rules at the start of each run and uses those rules to classify social items.

Rules should remain editable by a non-technical operator.

## 3. Notion Decision Inbox

The decision inbox is where true signal goes.

It is not a full social digest. It is a short queue of items that need judgment.

Each item should include enough context for the executive to decide without opening the social platform.

## 4. Agent Runtime

The runtime can be Codex, Claude Code, or another local agent.

The agent:

- Checks authenticated social surfaces
- Classifies items against Notion rules
- Takes low-risk actions when authorized
- Creates decision inbox items
- Delegates work
- Sends urgent notifications when configured
- Summarizes each run

## Run Loop

```text
Load config
Read Notion rules
Verify authenticated platform access
Check social surfaces
Classify each item
Take allowed low-risk actions
Create/update decision inbox items
Send urgent notifications only after Notion item exists
Summarize run
```

## Failure Mode

If authentication is missing for a platform, the agent should stop that platform's triage and report the blocker.

It should not guess from public pages, cached browser state, screenshots from old runs, or search results.
