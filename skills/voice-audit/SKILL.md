---
name: voice-audit
description: >
  Evaluate content against the defined voice system. Scores each dimension, identifies
  drift and inconsistencies, and produces a prioritized audit report. Uses reference voices
  from the voice profile as calibration benchmarks. Trigger when the user says things like
  "audit our content", "check if we're on voice", "score our voice maturity", "is this
  on-brand?", "our content quality is slipping", or provides content samples and asks for
  evaluation. Prerequisites: at least voice-profile.md and conventions.md must exist in
  voice/. If they don't, suggest running voice-discover and voice-author first.
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-audit

**Purpose:** Evaluate content against the defined voice system. Score each dimension, identify drift and inconsistencies, and produce a prioritized report with specific recommendations.

---

## Why This Skill Exists

Voice systems decay. New team members, product evolution, shifting market context, and simple drift erode consistency over time. Without periodic audits, a company discovers its voice has drifted only when someone external says "your content doesn't sound like you anymore."

voice-audit is the diagnostic. It takes content samples and evaluates them against the voice system artifacts, producing specific findings rather than vague impressions.

---

## Prerequisites

These artifacts must exist in `voice/`:
- `voice-profile.md` (required -- the primary evaluation benchmark)
- `conventions.md` (required -- the rule checklist)

These enrich the audit if they exist:
- `register-map.md` (enables register-appropriate evaluation)
- `audience-language-bank.md` (enables audience alignment checks)
- `ai-voice-config.md` (enables AI encoding compliance checks)

If the prerequisites don't exist, tell the user and suggest running voice-discover and voice-author first.

---

## Workflow

### Step 1: Load the Voice System

Read all existing voice artifacts from `voice/`. These are the benchmark.

Also read `config/profile.md` for company context (channels, audience, team dynamics).

### Step 2: Collect Content Samples

Ask the user for content to audit. Aim for breadth:

- **Across channels:** LinkedIn posts, blog articles, website copy, emails, product UI
- **Across authors:** If multiple people write content, include samples from each
- **Across time:** Recent and older content (to detect drift over time)
- **Across registers:** Content that should use different registers (marketing vs. client comms vs. product copy)

If URLs are provided, use `WebFetch` to retrieve them.

**Minimum viable audit:** 5 content samples across at least 2 channels. More is better, but don't block on perfection.

### Step 3: Evaluate Against Each Dimension

For each content sample, evaluate against the relevant dimensions. Not every dimension applies to every piece of content.

#### Dim 1: Voice Identity

- Does the content match the personality description in voice-profile.md?
- Are the voice attributes visible in the writing?
- Does it align with or diverge from the reference voice patterns?
- Would someone familiar with the reference voices recognize the resonance?

**Score:** How consistently the content reflects the defined identity.

#### Dim 2: Writing Conventions

- Does the content follow every hard rule? (Binary check per rule)
- Does the content follow the writing principles?
- Does the content contain any banned phrases?
- Does the content match the format template for its type (if one exists)?

**Score:** Compliance rate. This is the most objective dimension to score.

#### Dim 3: Register System

- Is the correct register applied for the content type and channel?
- Does the tone match the register's defined temperature, formality, and energy?
- If the content uses a different register than expected, is there a reason?

**Score:** Register accuracy across samples.

#### Dim 4: Audience Language

- Does the content use audience language or company jargon?
- Are audience phrases from the language bank present?
- Would the target audience recognize themselves in the language?

**Score:** Audience alignment.

#### Dim 5: Content Architecture

- Do the content samples follow the defined format templates?
- Is the structure consistent across samples of the same type?

**Score:** Template adherence.

#### Dim 6: AI Voice Encoding

- If AI-generated content is included, does it match the voice system?
- Are the quality gates from ai-voice-config.md being met?

**Score:** AI output quality.

#### Dim 7: Multilingual Coherence

- If content exists in multiple languages, does the voice feel consistent?
- Are language-specific conventions followed?
- Does translated content feel native or translated?

**Score:** Cross-language voice consistency.

#### Dim 8: Voice Governance

- Is the voice system being actively maintained?
- When was the last update to voice artifacts?
- Is there evidence of the voice system being referenced in content creation?

**Score:** System health.

### Step 4: Reference Voice Calibration

If the voice profile includes reference voices, evaluate the content against those benchmarks:

> "Your recent content scores well on the [specific pattern] you admired in [Reference A], but has drifted from the [specific quality] you identified in [Reference B]."

This is one of the most actionable parts of the audit -- it connects abstract voice drift to the specific qualities the team cares about.

### Step 5: Produce the Audit Report

```markdown
# Voice Audit Report: [Company Name]
Date: YYYY-MM-DD
Content samples reviewed: [N]
Channels covered: [List]

---

## Overall Assessment

[2-3 sentence summary: overall voice health, biggest strength, biggest concern]

---

## Dimension Scores

| # | Dimension | Score | Trend | Key Finding |
|---|-----------|-------|-------|-------------|
| 1 | Voice Identity | X/5 | [↑ ↓ →] | [One sentence] |
| 2 | Writing Conventions | X/5 | [↑ ↓ →] | [One sentence] |
| 3 | Register System | X/5 | [↑ ↓ →] | [One sentence] |
| 4 | Audience Language | X/5 | [↑ ↓ →] | [One sentence] |
| 5 | Content Architecture | X/5 | [↑ ↓ →] | [One sentence] |
| 6 | AI Voice Encoding | X/5 | [↑ ↓ →] | [One sentence] |
| 7 | Multilingual Coherence | X/5 | [↑ ↓ →] | [One sentence] |
| 8 | Voice Governance | X/5 | [↑ ↓ →] | [One sentence] |

Trend: compared to last audit if available, or compared to initial assessment from discovery.

---

## Convention Compliance

### Hard Rules
| Rule | Pass | Fail | Examples |
|------|------|------|----------|
| [Rule from conventions.md] | [N] | [N] | [Specific example of violation if any] |

### Banned Phrases Found
| Phrase | Where | Context |
|--------|-------|---------|
| [Phrase] | [Which sample] | [Surrounding text] |

---

## Reference Voice Calibration

### [Reference A]
- **Pattern we're drawn to:** [From voice-profile.md]
- **Current alignment:** [Strong / Moderate / Drifted]
- **Evidence:** [Specific examples from content samples]

### [Reference B]
[Same structure]

---

## Specific Findings

### Strengths
- [What's working well, with specific examples from content samples]
- [Another strength]

### Drift Areas
- [Where the voice has drifted from the defined system, with specific examples]
- [Another drift area]

### Inconsistencies
- [Where different samples or channels show different voices]
- [Another inconsistency]

---

## Recommended Actions

### Priority 1 (address now)
- [Specific, actionable recommendation targeting the biggest gap]

### Priority 2 (address soon)
- [Next most impactful recommendation]

### Priority 3 (when ready)
- [Lower-urgency improvement]

### Suggested skill
[Which skill to run next: voice-refresh if amendments are needed, voice-author if artifacts need expansion, voice-encode if AI config needs updating]
```

### Step 6: Present and Discuss

Share the audit report with the user. Focus the conversation on:
- Surprises -- scores they didn't expect
- Priority actions -- do they agree with the prioritization?
- Next steps -- do they want to proceed to voice-refresh for amendments?

---

## Quick Audit Mode

For a fast voice check (not a full audit), the user can share a single piece of content and ask "is this on voice?" In this case:

1. Read the voice artifacts
2. Evaluate the content against personality, conventions, and the applicable register
3. Produce a short assessment: what's on voice, what's off, and specific suggestions
4. Skip the full report format

This should take 2-3 minutes, not 30.

---

## Self-check before delivering

- [ ] Every hard rule from conventions.md was checked against every sample
- [ ] Banned phrase scan was run across all samples
- [ ] Reference voice calibration is included (if reference voices exist in the profile)
- [ ] Dimension scores are justified with specific evidence from the samples
- [ ] Findings include specific examples (quoted text), not just impressions
- [ ] Recommendations are actionable and prioritized
- [ ] The report suggests which skill to run next
- [ ] Low scores are framed as starting points, not indictments
