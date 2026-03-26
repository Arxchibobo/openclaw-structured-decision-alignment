# openclaw-structured-decision-alignment

An [OpenClaw](https://github.com/Arxchibobo/openclaw) skill that acts as a structured facilitator for multi-stakeholder technical decision-making — guiding discussions from preparation through closure and producing a traceable decision document.

## Overview

When engineering teams need to align multiple people on a technical proposal, the process often devolves into unfocused threads, unresolved debates, and decisions that nobody can find later. This skill gives your AI agent a complete playbook for running that alignment session: it parses the proposal, structures the open questions, guides the discussion one issue at a time, and generates a signed-off decision document at the end.

It is designed to be triggered when a user says something like:

- "Help me organize a technical proposal discussion"
- "I need multi-person sign-off on this plan"
- "Pull together a thread and confirm each of these questions one by one"
- "This project needs cross-team alignment"

## Features

- **Four-phase facilitation playbook** — Prepare → Kick-off → Facilitate → Close
- **Automated question structuring** — extracts decision points from any input document, ranks them by priority, and maps each to the relevant stakeholders
- **Pre-built option analysis** — for each decision point, generates 2–3 candidate options with pros and cons
- **Real-time conclusion tracking** — marks each question resolved (✅), deferred (⏳), or open (⚖️) as the discussion progresses
- **Divergence handling** — when participants disagree, surfaces the core trade-off neutrally and suggests a path to resolution
- **Pacing controls** — redirects off-topic threads, breaks deadlocks after 5 minutes, and flags when the session is running long
- **Structured decision document** — produces a timestamped output with confirmed decisions, rationale, a TODO table with owners and due dates, deferred items, and topics for follow-up discussion
- **Skill integrations** — can hand off action items to `team-tasks`, surface blockers via `bottleneck-reporting`, and store the decision document via `notion`

## Requirements

- [OpenClaw](https://github.com/Arxchibobo/openclaw) agent framework

## Installation

Copy `SKILL.md` into your OpenClaw skills directory and restart the agent, or follow your OpenClaw installation's skill-loading convention.

```bash
cp SKILL.md /path/to/your/openclaw/skills/structured-decision-alignment.md
```

## Usage

Provide the skill with at minimum:

1. A document describing the proposal or problem (any format)
2. A list of participants

**Optional but recommended:**

- Known constraints
- A pre-identified list of open questions
- Each participant's area of responsibility
- A deadline

### Example trigger

> "Help me organize an alignment discussion. Here's the RFC: [doc]. Participants: @alice (backend), @bob (infra), @carol (product)."

### What the skill produces

**Phase 1 — Prepare**: The agent reads all materials, extracts and prioritizes decision points, drafts a structured Playbook, and confirms it with you before proceeding.

**Phase 2 — Kick-off**: Posts an opening message in the designated channel or thread with background context, goals, participants, and ground rules, then presents the first question.

**Phase 3 — Facilitate**: Guides the discussion question by question — summarizing conclusions, adjusting order on the fly, handling disagreements, and logging anything that can't be resolved on the spot.

**Phase 4 — Close**: Posts a full discussion summary and generates a decision document:

```
📄 Decision Document: [Topic]
Date: YYYY-MM-DD
Participants: @alice, @bob, @carol

✅ Confirmed Decisions
1. [Decision] — Conclusion: ... — Rationale: ...

📋 TODO List
| # | Task | Owner | Due   | Status |
|---|------|-------|-------|--------|
| 1 | ...  | @alice | MM-DD | ⬜    |

⏳ Pending Items
1. [Open question] — Owner: @bob — Expected by: MM-DD

📝 Follow-up Topics (not covered this session)
- [Item 1]
```

## Configuration

No additional configuration is required beyond loading the skill. The skill's behavior (discussion rules, output format, integration points) is defined entirely within `SKILL.md` and can be customized by editing that file directly.

## License

No license file is included in this repository. All rights reserved by Bobo Zhou (Arxchibobo).
