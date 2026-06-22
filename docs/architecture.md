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

Decision item titles should identify the exact surface first, for example:

- `Facebook Messenger: refund request from customer [SOC-ABCDE]`
- `LinkedIn Message: partnership invitation from operator [SOC-FGHIJ]`
- `Facebook Group: pending post about support issue [SOC-KLMNO]`

The Notion page body should not be blank. It should include the sender or actor, observed timestamp, source channel, source link, and the full relevant message, post, or comment text before the agent's summary or recommendation.

For direct messages, preserve the full relevant inbound transcript with sender names and timestamps when available.

After creating or updating a decision item, the agent should fetch the card back and verify that the body contains readable context before it marks the run complete.

## 4. Executive Response Handling

The decision inbox is also the command layer after the executive responds.

When the executive comments, changes status, or marks an item handled, a responder should route the action by the decision item's `Source Channel` and `Source Thread Link`.

Examples:

- `Facebook Messenger` goes back to the linked Messenger conversation.
- `LinkedIn Message` goes back to the linked LinkedIn conversation.
- `LinkedIn Connection Request` goes back to the linked request.
- `Facebook Group` goes back to the linked post, comment, member request, or moderation item.

The responder should not treat the decision inbox as email-only. If the source link or authentication is missing, it should leave the item active and add a clear blocker note instead of guessing.

## 5. Agent Runtime

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
Check executive responses in Notion
Route each response back to the linked source
```

## Failure Mode

If authentication is missing for a platform, the agent should stop that platform's triage and report the blocker.

It should not guess from public pages, cached browser state, screenshots from old runs, or search results.
