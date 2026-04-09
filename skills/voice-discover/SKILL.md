---
name: voice-discover
description: >
  Run a structured content audit and interview to surface how a company actually sounds,
  what voice patterns they're drawn to, and what they want to avoid. Produces a Discovery
  Brief that voice-author ingests as its primary input. Use this skill before voice-author
  on any new engagement or when the input material is thin. Trigger when the user says
  things like "help us figure out our voice", "we need to define our voice", "here's our
  website", "audit our current content", or "let's figure out what we sound like". Skip
  this skill if the user already has rich voice artifacts and wants to go straight to
  editing or encoding.
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-discover

**Purpose:** Run a structured content audit and interview that surfaces how a company actually sounds, what voice patterns they admire, and what they want to avoid. Produces a Discovery Brief that `voice-author` ingests as its primary source material.

---

## Why This Skill Exists

Most companies can't articulate their voice from scratch. Ask a founder "what does your brand sound like?" and you'll get "professional but approachable" -- which describes every company and distinguishes none.

Discovery solves this by working through three lenses:

1. **Where you are today** -- analyzing existing content for actual voice patterns
2. **Reference voices** -- identifying companies and people whose communication style resonates, then extracting what specifically resonates
3. **Anti-references** -- identifying who you don't want to sound like, which is often more revealing than the positive references

The synthesis step -- combining reference voice patterns into something distinctly the company's own -- is where the real value lands. This is also where a human facilitator adds the most value, but the skill produces useful output independently.

---

## When to Use vs. Skip

**Use voice-discover when:**
- Starting a new voice engagement (no existing voice artifacts)
- The user has limited voice documentation (vague brand adjectives, no formal system)
- The user wants to understand their current voice before defining a new one
- Content quality or consistency is the presenting problem

**Skip voice-discover when:**
- The user already has rich, specific voice artifacts and wants to edit them
- They're doing a targeted update to an existing voice system (use voice-refresh)
- They want to encode an existing voice system for AI (use voice-encode directly)

---

## Workflow

### Phase 1: Collect Existing Content

Ask the user for content samples. Accept any format:
- LinkedIn posts (personal or company page)
- Blog articles or newsletter pieces
- Website copy (homepage, about page, product pages)
- Email communications (newsletters, onboarding sequences, sales emails)
- Product UI copy (onboarding flows, error messages, feature descriptions)
- Internal docs (if relevant to external voice)
- Pitch decks or investor materials

If a URL is provided, use `WebFetch` to retrieve and read it.

**Aim for 3-5 representative samples across different channels.** More is better, but don't let perfect be the enemy of good. Even one LinkedIn post and a homepage give you something to work with.

**Analyze what you have.** Before asking questions, take stock:

For each content sample, note:
- **Sentence length patterns** -- short and punchy, or long and flowing?
- **Formality level** -- casual, conversational, professional, academic?
- **Energy** -- high (enthusiastic, urgent) or low (measured, calm)?
- **Specificity** -- concrete examples and data, or abstract claims?
- **Humor** -- present or absent? What kind (dry, playful, irreverent)?
- **Structure** -- heavy formatting (headers, bullets) or flowing prose?
- **Person** -- first person, second person, third person? Singular or plural?
- **Jargon level** -- insider language or accessible to outsiders?

Note patterns and inconsistencies across samples. Inconsistency is information -- it tells you the voice isn't defined.

---

### Phase 2: Reference Voice Interview

This is the core of discovery. Work through three lenses using `AskUserQuestion`. Batch 2-4 questions per call. Adapt based on what Phase 1 revealed.

---

#### Lens 1: Where You Are Today

Start with what you observed in the content analysis. Share your observations and ask for confirmation:

> "Looking at your content, I notice [specific pattern]. Is that intentional, or is that just how things ended up?"

Key questions:
- Does anyone on the team currently "carry" the voice? If so, how would you describe how they write?
- When you read your own content back, what feels right about it? What makes you cringe?
- Is there a piece of content you've published that you think nails your voice? Which one, and what about it works?

**Listen for:** The gap between how they think they sound and how they actually sound. This gap is the most valuable insight discovery produces.

---

#### Lens 2: Reference Voices

This is where most founders light up. Most people can't describe their ideal voice from scratch, but they can immediately point to companies, founders, or creators whose communication style resonates.

> "Which companies, founders, or creators do you admire for how they communicate? Not necessarily in your industry -- anyone whose content makes you think 'I wish we sounded like that.'"

For each reference they provide:
- **What specifically resonates?** "I like how Stripe communicates" isn't enough. Push for specifics: "Is it the precision? The calm confidence? The way they explain complex things simply?"
- **What would you borrow vs. what's uniquely them?** Not everything about a reference voice is transferable. The user might love Basecamp's irreverence but know it wouldn't work in their industry.

If the user provides URLs or names, fetch and analyze the referenced content. Extract specific patterns:
- Voice attributes you can name (directness, warmth, precision, wit)
- Structural patterns (sentence length, paragraph rhythm, use of questions)
- Tonal qualities (energy level, confidence, formality)

**Produce a reference voice map:** For each reference, document what specifically the user is drawn to and what pattern it represents.

> "From [Reference A], you're drawn to their [specific pattern]. From [Reference B], it's the [specific quality]. Together, this suggests a voice that's [synthesis]."

---

#### Lens 3: Anti-References

Often more revealing than positive references. Anti-references define the boundaries.

> "Who do you NOT want to sound like? What kind of content makes you cringe in your space?"

Key questions:
- Are there competitors whose content you find generic, corporate, or off-putting? What specifically bothers you?
- What content trends in your industry do you want to avoid?
- Are there words or phrases that feel wrong for your company?

**Extract specific patterns to avoid.** Anti-references feed directly into banned phrases, convention hard rules, and voice attribute boundaries.

---

#### Lens 4: Audience Perspective

If time and context allow, probe for audience language:

- How do your customers or users describe what you do? (Their words, not yours)
- What language do they use when they're frustrated with the problem you solve?
- Are there common phrases from support tickets, sales calls, or reviews that capture how they talk?

This feeds the Audience Language Bank. If the user doesn't have this information readily available, note it as a gap to fill later.

---

### Phase 3: Dimension Assessment

Based on everything gathered, assess the company's current maturity across all 8 dimensions. Use the maturity levels from SYSTEM.md.

For each dimension, provide:
- **Score (1-5)** with brief justification
- **Evidence** -- what you observed or learned that supports the score
- **Key gap** -- the most important thing missing at this dimension

---

### Phase 4: Produce the Discovery Brief

Synthesize everything into a Discovery Brief. This is the handoff artifact to `voice-author`.

```markdown
# Voice Discovery Brief: [Company Name]
Date: YYYY-MM-DD

---

## Content Analysis

### Patterns Observed
[Summary of voice patterns found across content samples: sentence length, formality, energy, specificity, humor, structure, person, jargon level]

### Inconsistencies
[Where the voice varies across samples or channels -- this is information, not criticism]

### Strongest Existing Content
[Which sample(s) best represent the voice the company seems to be reaching for, and why]

---

## Reference Voice Map

### [Reference 1: Company/Person Name]
- **What resonates:** [Specific quality the user is drawn to]
- **Pattern:** [The extractable voice attribute]
- **Source:** [URL or description]

### [Reference 2: Company/Person Name]
[Same structure]

### [Reference 3: Company/Person Name]
[Same structure]

### Synthesis
[How the reference patterns combine into something distinctly this company's own. This is the most important paragraph in the brief.]

---

## Anti-References

### Patterns to Avoid
- [Specific pattern] -- [Why it doesn't fit]
- [Specific pattern] -- [Why it doesn't fit]

### Candidate Banned Phrases
[Words or phrases identified through anti-reference discussion]

---

## Audience Language

### What We Know
[Audience language patterns, if gathered]

### Gaps
[What's missing and where to find it -- support tickets, sales calls, reviews, etc.]

---

## Dimension Assessment

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Voice Identity | X/5 | [One sentence] |
| 2 | Writing Conventions | X/5 | [One sentence] |
| 3 | Register System | X/5 | [One sentence] |
| 4 | Audience Language | X/5 | [One sentence] |
| 5 | Content Architecture | X/5 | [One sentence] |
| 6 | AI Voice Encoding | X/5 | [One sentence] |
| 7 | Multilingual Coherence | X/5 | [One sentence] |
| 8 | Voice Governance | X/5 | [One sentence] |

---

## Recommended Next Steps

### Immediate (voice-author)
[Which artifacts to create first, based on dimension assessment and user priorities]

### Follow-up
[What comes after the initial authoring -- encoding, templates, multilingual, governance]

---

## Open Questions

| Question | Domain | Notes |
|----------|--------|-------|
| [Question] | [Dimension] | [Context or who needs to answer] |
```

---

### Phase 5: Present and Hand Off

Share the Discovery Brief with the user. Walk through:

- The reference voice synthesis -- does the combination feel right?
- The dimension assessment -- any surprises?
- The recommended next steps -- does the sequencing make sense?
- The open questions -- can any be answered now?

If the user is ready to proceed: pass the Discovery Brief as the primary source input to `voice-author`. The brief replaces the need for voice-author to re-interview from scratch.

If critical open questions remain: document them and note which voice artifacts can be drafted now vs. which need more input.

---

## Quality Standards

A good Discovery Brief:

- **Distinguishes actual voice from aspirational voice.** The content analysis shows where they are. The reference voices show where they want to be. The gap between them is the work.
- **Extracts specific patterns from references, not just names.** "Like Stripe" is not useful. "Stripe's calm precision when explaining complex infrastructure" is.
- **Names anti-references with equal specificity.** "Not corporate" isn't a boundary. "Not the kind of SaaS company that calls everything 'seamless' and 'robust'" is.
- **Is honest about maturity.** Low scores aren't failures. Most companies start at 1-2 across most dimensions. The brief should make that feel like a starting point, not an indictment.
- **Produces a synthesis that feels distinctly like this company.** The reference voice map should combine into something that isn't just a mashup of other voices. The synthesis paragraph is the hardest and most valuable part of the brief.
