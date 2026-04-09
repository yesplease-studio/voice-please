---
name: voice-refresh
description: >
  Propose targeted amendments to voice system artifacts based on audit findings, market
  shifts, product evolution, or new context. Does not write artifacts directly -- all
  amendments are routed through voice-author for application. Trigger when the user says
  things like "update our voice", "our product has changed", "the audit found drift",
  "our voice needs to evolve", "incorporate these findings", or after voice-audit produces
  a report with recommendations. Prerequisites: voice artifacts must exist in voice/.
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-refresh

**Purpose:** Propose targeted amendments to voice system artifacts based on new context. This skill analyzes, recommends, and drafts amendment proposals. It does not write to voice artifacts directly -- all changes route through `voice-author`.

---

## Why This Skill Exists

Voice systems are living documents, not one-time deliverables. Companies evolve: products change, audiences shift, teams grow, markets move. A voice system that was perfect 12 months ago may not fit the company today.

voice-refresh is the controlled evolution mechanism. It prevents two failure modes:
1. **Voice drift** -- the voice evolves unintentionally through accumulated small changes
2. **Voice fossilization** -- the voice stays frozen while the company changes around it

The skill proposes amendments with rationale, so voice-author can apply them with full context.

---

## When to Use

- After a voice-audit identifies drift or gaps
- When the company's product, audience, or market has changed meaningfully
- When the team has grown and the voice needs to accommodate new contributors
- When the user says the voice "doesn't feel right anymore"
- On a scheduled cadence (every 6-12 months is typical)

## Prerequisites

Voice artifacts must exist in `voice/`. You can't refresh what doesn't exist.

If an audit report exists, it's the preferred input. If not, the skill can work from the user's description of what's changed.

---

## Workflow

### Step 1: Load Current State

Read all voice artifacts from `voice/`:
- `voice-profile.md`
- `conventions.md`
- `register-map.md` (if exists)
- `audience-language-bank.md` (if exists)
- `ai-voice-config.md` (if exists)

Read `config/profile.md` for company context.

If an audit report exists, read it for dimension scores and findings.

### Step 2: Understand What's Changed

Determine the refresh trigger. This shapes which artifacts need amendments.

**If triggered by an audit report:**
- Review the dimension scores and drift areas
- Focus amendments on the weakest dimensions and specific findings
- Cross-reference audit recommendations with the current artifacts

**If triggered by company evolution:**
Ask the user (batch 2-4 questions):
- What has changed about your company in the last 6-12 months? (Product, audience, market, team, positioning)
- Are there new content channels or contexts that the voice system doesn't cover?
- Has anyone on the team flagged that the voice doesn't feel right? What specifically?
- Are there new reference voices or anti-references that feel more relevant now?

**If triggered by a feeling that something is off:**
- Ask for specific examples of content that felt wrong
- Compare those examples against the current voice artifacts
- Identify the gap between what the artifacts define and what the content reflects

### Step 3: Identify Amendment Candidates

For each voice artifact, identify sections that need updating. Categorize each candidate:

**Update:** The section exists but the content is outdated or incomplete.
Example: A voice attribute that described the company at an earlier stage.

**Add:** A new section or element is needed.
Example: A new register for a channel that didn't exist when the voice was defined.

**Remove:** A section is no longer relevant.
Example: A banned phrase that no longer applies after a rebrand.

**Sharpen:** The section is directionally correct but not specific enough.
Example: A voice attribute that has become generic as the team grew.

### Step 4: Draft Amendment Proposals

For each amendment candidate, produce a structured proposal:

```markdown
## Amendment: [Short title]

**Artifact:** [Which file]
**Section:** [Which section]
**Type:** [Update | Add | Remove | Sharpen]

### Current
[The current text, quoted]

### Proposed
[The proposed replacement or addition]

### Rationale
[Why this change is needed. Reference audit findings, company evolution, or specific examples.]

### Impact
[What this change affects: other artifacts, AI config, team behavior]
```

### Step 5: Prioritize and Present

Group amendments by priority:

**Critical:** Amendments that fix active voice drift or address the audit's priority 1 findings. These should be applied soon.

**Recommended:** Amendments that improve the voice system but aren't urgent. Apply when convenient.

**Optional:** Nice-to-have refinements. Apply during scheduled maintenance.

Present the full set of amendment proposals to the user. For each one:
- Show current vs. proposed text
- Explain the rationale
- Note any dependencies between amendments

### Step 6: Hand Off to voice-author

After the user approves amendments:

1. Pass the approved amendment proposals to `voice-author` (edit mode)
2. voice-author applies the changes to the relevant artifacts
3. After artifacts are updated, suggest running `voice-encode` to update the AI configuration

If the user rejects an amendment, note the reason. This prevents re-proposing the same change in future refreshes.

---

## Refresh Report Format

```markdown
# Voice Refresh Report: [Company Name]
Date: YYYY-MM-DD
Trigger: [Audit findings | Company evolution | Scheduled review | User request]

---

## What Changed

[2-3 sentence summary of what prompted the refresh and the main evolution]

---

## Amendment Proposals

### Critical

#### [Amendment 1 title]
- **Artifact:** [file]
- **Section:** [section]
- **Type:** [Update/Add/Remove/Sharpen]
- **Current:** [quoted text]
- **Proposed:** [new text]
- **Rationale:** [why]

### Recommended

#### [Amendment 2 title]
[Same structure]

### Optional

#### [Amendment 3 title]
[Same structure]

---

## Artifacts Affected

| Artifact | Amendments | Status |
|----------|-----------|--------|
| voice-profile.md | [N] | Pending approval |
| conventions.md | [N] | Pending approval |
| register-map.md | [N] | Pending approval |
| audience-language-bank.md | [N] | Pending approval |
| ai-voice-config.md | Needs re-encoding after changes | Pending |

---

## Next Steps

1. Review and approve/reject each amendment above
2. Run voice-author (edit mode) to apply approved amendments
3. Run voice-encode to update AI configurations
4. [Any other follow-ups specific to this refresh]
```

---

## Self-check before delivering

- [ ] Every amendment proposal has current text, proposed text, and a rationale
- [ ] Amendments reference specific evidence (audit findings, content examples, company changes)
- [ ] Priorities are justified (critical vs. recommended vs. optional)
- [ ] Dependencies between amendments are noted
- [ ] The report identifies which artifacts need re-encoding after changes
- [ ] No amendments are proposed without evidence or user input (don't fix what isn't broken)
- [ ] Amendments improve specificity, not reduce it (never propose making an attribute more generic)
