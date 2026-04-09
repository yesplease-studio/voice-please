---
name: voice-recommend
description: >
  The entry point for users who don't know where to start. Maps a voice or content challenge
  to the right dimensions and recommends which skill to run. Trigger when the user describes a
  problem ("our content sounds generic", "AI tools produce off-brand content"), asks "where do
  we start?", "what should we work on?", or provides a general complaint about content quality
  or consistency. Skip this skill if the user already knows what they want (e.g., "define our
  voice" maps directly to voice-discover).
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-recommend

**Purpose:** Given a voice or content challenge, recommend which skill to run and which dimensions to focus on. The output is a clear recommendation with rationale, not just a skill name.

---

## Step 0: Load context

1. Read `systems/voice/SYSTEM.md` for the dimension taxonomy, challenge-to-dimension mapping, and sequencing principles.
2. Read `config/profile.md` if it exists (company context, current dimension estimates).
3. If voice artifacts exist in `voice/`, scan the directory to understand what's already been built.

---

## Step 1: Understand the challenge

The recommendation can be triggered by:

**A problem description:**
The user describes a content or voice problem. Examples:
- "Our content sounds generic"
- "Nobody follows our brand guidelines"
- "Our AI tools produce off-brand content"
- "Our blog sounds different from our emails"

**A general request for direction:**
- "Where should we start?"
- "What should we work on?"
- "We need to figure out our voice"

**A maturity assessment request:**
- "How mature is our voice system?"
- "Score our voice"

If the input is vague, ask 1-2 clarifying questions before recommending. Keep it tight -- this skill should be fast, not a deep interview.

**Clarifying questions to consider:**
- "What's the most visible pain right now -- is it inconsistency across writers, generic-sounding content, or something else?"
- "Do you have any existing voice or brand documentation, even informal?"
- "What content channels matter most to you right now?"

---

## Step 2: Map to dimensions

Using the challenge-to-dimension mapping in SYSTEM.md:

1. Identify the primary dimension(s) the challenge maps to.
2. Check dimension dependencies -- if the recommended dimension has upstream dependencies that aren't met, flag it.
3. If a profile exists with dimension estimates, factor those into the recommendation.
4. If voice artifacts exist, check which dimensions already have coverage.

---

## Step 3: Recommend a path

Produce a recommendation with this structure:

### Challenge
[One sentence restatement of what the user described]

### Primary dimension(s)
[Which dimensions this maps to and why -- be specific about the connection]

### Current state
[If profile or artifacts exist: what's already in place. If not: note that this is a cold start.]

### Recommended skill
[Which skill to run, with rationale]

- **What it will do:** [One sentence on the skill's purpose]
- **What you'll walk away with:** [Concrete output -- an artifact, a score, a set of recommendations]
- **What you'll need to provide:** [Input the user needs to bring -- content samples, time, team members]
- **Time investment:** [Rough estimate: 15 minutes, an hour, a half-day session]

### Why not the alternatives
[1-2 sentences each on why other skills aren't the right starting point. Only include skills that a reasonable person might consider.]

### What comes after
[The natural next step after the recommended skill completes]

---

## Self-check before delivering

- [ ] The recommendation maps to specific dimensions with clear reasoning
- [ ] Dimension dependencies are respected (not recommending Dim 6 work when Dims 1-3 are undefined)
- [ ] The recommendation accounts for existing voice artifacts (if any)
- [ ] Concrete outputs are named, not vague ("a voice profile with personality, attributes, and conventions" not "clarity on your voice")
- [ ] The user has enough information to decide whether to proceed
- [ ] Alternative paths are addressed, not just ignored
