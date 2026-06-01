# Sponsor Outreach Agent
**GVSU Men's Club Soccer — Golf Outing Sponsorship Pipeline**
AI 502 | Project 2 | Ben Grob

---

## Overview

<!-- 2-3 sentences: what the app does, who it's for, and what problem it solves. -->
<!-- Example: "This is an agentic system that automates the sponsorship prospecting and outreach process for the GVSU Men's Club Soccer Golf Outing. It finds local businesses, researches contact information, and drafts personalized emails — replacing 10+ hours of manual work with a single user interaction." -->

**Live demo:** [link here]
**GitHub:** [link here]

---

## Problem

<!-- 1 short paragraph on the real-world pain point this solves. -->
<!-- Pull from your prd.md — the "I don't know where to send them" quote is good here. -->

---

## Agentic Architecture

<!-- Describe your 6-agent pipeline. A short paragraph + the table below works well. -->

This project uses a 6-agent pipeline with a model waterfall design:

| Agent | Role | Model Temp |
|---|---|---|
| Orchestrator | Plans, delegates, assembles output | 0.7 |
| Prospector | Finds local businesses by category + location | 0.3 |
| Researcher | Enriches prospects with contact info | 0.3 |
| Copywriter | Writes short personalized email intro | 0.6 |
| Reviewer | Factual QA — flags errors before output | 0.0 |
| Persona Evaluator | Scores email from business owner's POV | 0.5 |

<!-- Add 1-2 sentences on how the feedback loop works: flagged emails routed back to Copywriter. -->

---

## Tech Stack

| Layer | Tool |
|---|---|
| Frontend | React + Tailwind CSS |
| Agent runtime | Anthropic Claude API (claude-sonnet-4-6) |
| Deployment | Lovable |
| Code hosting | GitHub |

---

## Features

<!-- Short bulleted list of what the app actually does. Keep it to what's built, not what's planned. -->

- [ ] Business prospecting by category and location
- [ ] Contact enrichment (owner name + email)
- [ ] Personalized email drafting with PDF attachment instruction
- [ ] Reviewer quality gate (PASS / FLAG per email)
- [ ] Persona evaluation score (1–5) with improvement note
- [ ] Copy-to-clipboard per email
- [ ] CSV export of full prospect list

---

## How to Use

1. Enter your Anthropic API key in the key field
2. Type a business category (e.g. `restaurants`, `auto repair shops`)
3. Confirm or edit the location (default: Allendale, MI)
4. Click **Run agent pipeline** and watch each agent's status update
5. Review prospect cards — each shows the drafted email, pass/flag status, and persona score
6. Click **Copy email**, paste into Gmail, and attach `ClubSoccerLetterTemplate.pdf`

---

## Multi-Model Design

<!-- Required for AI 502 graduate tier. -->
<!-- Describe how you compared models on the same task and what you found. -->
<!-- Example: "The Copywriter agent prompt was run on both Claude Sonnet and Gemini Flash. Claude produced more natural, specific openers — Gemini tended toward more formal language. Both preserved required contact info correctly." -->

**Models compared:** Claude Sonnet 4.6 vs. [second model]
**Task:** Copywriter agent — personalized email intro
**Finding:** [your honest comparison — 2-3 sentences]

---

## Evaluation

<!-- Required rubric item. Document what you tested and what you found. -->

### Tests Run

| Test | Expected | Result |
|---|---|---|
| Prospector — returns local businesses | 8–12 results | [fill in] |
| Copywriter — no generic placeholders | 0 generic openers | [fill in] |
| Reviewer — catches planted bad email | FLAG returned | [fill in] |
| Persona Evaluator — scores correlate with quality | Low scores on generic emails | [fill in] |
| End-to-end runtime | Under 3 minutes | [fill in] |
| Human spot-check — would you send this? | 4/5 emails usable | [fill in] |

### Failure Analysis

<!-- Honest assessment of what doesn't work well yet. This is a rubric item — don't skip it. -->
<!-- Current known limitation: prospecting uses AI-generated business data, not live web search. -->

**Known limitations:**
- Prospecting is currently simulated (Claude generates plausible businesses from training data rather than searching the live web). Contact details may not be accurate and should be verified before sending.
- [any other limitations you observed]

**What I would do differently:**
- [your honest answer — e.g. "Run the backend on a server to enable real web search calls"]

---

## Build Log

<!-- Required rubric item: "a build log of the prompts used." -->
<!-- Document the key prompts and decisions that shaped the build. Be specific — this shows AI-assisted development. -->

### Session 1 — Problem Definition & Architecture
**Tool:** Claude.ai
**Key prompt:** *"I'm building a project for AI 502. I'm the fundraising chair for a club soccer team. I need to find and email 30–100 local businesses for golf outing sponsorships. Help me design an agentic pipeline."*
**Output:** 6-agent architecture, PRD, copilot-instructions.md, evaluation criteria
**Decision made:** Short email intro + PDF attachment approach instead of full letter in email body

### Session 2 — Agent Harness
**Tool:** Claude.ai
**Key prompt:** *[paste the main prompt you used to generate the React artifact]*
**Output:** Full React app with all 6 agents implemented as API calls
**Decision made:** Used Anthropic API instead of Gemini due to CORS limitations in browser-based artifacts

### Session 3 — Deployment
**Tool:** Lovable
**Key prompt:** *[paste what you told Lovable]*
**Output:** [describe what deployed successfully]
**Decision made:** [anything you had to adjust for deployment]

<!-- Add more sessions as you continue building -->

---

## Ethical & Practical Limits

<!-- Required rubric item for AI 502. 3-5 sentences is enough. -->

- **Human in the loop:** The agent drafts emails but does not send them. The user reviews every email before sending, preserving human judgment on outreach decisions.
- **Data accuracy:** Contact information is AI-generated and unverified in the current prototype. Users should verify emails before sending to avoid misdirected outreach.
- **Scope:** This tool is designed for a specific, low-stakes outreach context. It should not be used for high-volume cold email campaigns without a real web search backend and compliance review.
- [add any other limits you observed]

---

## Project Files

```
sponsor-outreach-agent/
├── README.md                    ← this file
├── architecture.md              ← system design and agent diagram
├── prd.md                       ← product requirements
├── copilot-instructions.md      ← master rules for all agents
├── evaluation.md                ← success metrics and test results
├── development-checklist.md     ← phased build plan
├── project-phases-reference.md  ← phase-by-phase guide
└── src/
    └── SponsorOutreachAgent.jsx ← main application
```

---

## What's Next

<!-- Optional but good to include — shows forward thinking. -->

- Replace simulated prospecting with real web search via a server-side backend
- Add response tracking (mark businesses as contacted, replied, or passed)
- Expand to multiple business categories in one session
- Test against real outreach to measure actual sponsor conversion rate
