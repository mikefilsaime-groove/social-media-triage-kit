# Notion Social Rules Schema

Create a Notion database named `Social Triage Rules`.

## Properties

| Property | Type | Purpose |
| --- | --- | --- |
| Category | Title | Rule name |
| Platform | Multi-select | Social surface this rule applies to |
| Active | Checkbox | Whether the rule is active |
| Social Outcome | Select | Accept, Reject, Ignore, Delegate, Needs Executive, etc. |
| Executive Visibility | Select | Immediate, Decision Queue, Digest, Review, None |
| Notify Method | Multi-select | Notion Inbox, Text, Chat, Email, None |
| Delegate Name(s) | Text | Delegate roles or names |
| Delegate Contact(s) | Text | Delegate email, handle, or internal channel |
| When To Use | Text | Matching guidance |
| Default Handling | Text | What the agent should do |
| Examples / Notes | Text | Edge cases and examples |
| Source Section | Text | Optional source or policy section |

## Suggested Select Options

Platform:

- All Social
- LinkedIn
- Facebook
- Messenger
- Facebook Groups
- Community Platform

Social Outcome:

- Accept
- Reject
- Delete / Ban
- Ignore
- Reply / Qualify
- Delegate / Loop In
- Flag in Decision Inbox
- Needs Executive
- Leave for Human Mods
- Approve
- Notify Team
- No Action / Review

Executive Visibility:

- Immediate notification
- Decision queue
- Digest unless urgent
- Digest unless high-value or urgent
- Review queue
- No notification

Notify Method:

- Notion Inbox
- Text
- Chat
- Email
- None
- Not Applicable

## Notes

The rule database is the live control plane. Do not hard-code private rules into skills if they can live in Notion.
