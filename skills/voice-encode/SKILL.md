---
name: voice-encode
description: >
  Translate voice system artifacts into AI-ready configurations. Produces ai-voice-config.md
  and optionally generates CLAUDE.md voice sections, system prompt snippets, or tool-specific
  configurations. This is the only skill that writes to the Encoding layer. Trigger when the
  user says things like "encode our voice for AI", "generate the AI config", "make this work
  with Claude", "create a system prompt for our voice", or after voice-author has produced
  or updated artifacts. Skip this skill if no Definition-layer artifacts exist yet -- run
  voice-discover and voice-author first.
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-encode

**Purpose:** Translate the Definition-layer voice artifacts into machine-readable configurations that AI tools can consume directly. This is the only skill that writes to the Encoding layer (ai-voice-config.md).

---

## Why This Skill Exists

A voice profile that lives in a markdown document is useful for humans but invisible to AI tools. Most companies that invest in defining their voice still get generic AI output because the voice definition was never translated into a format AI tools can consume.

voice-encode closes this gap. It takes the structured artifacts from voice-author and produces configurations that can be dropped into system prompts, CLAUDE.md files, or any AI writing tool's instructions.

---

## When to Use

- After `voice-author` has produced or updated voice artifacts
- When the user wants AI tools to follow their voice system
- When the user is setting up Claude Code, ChatGPT custom instructions, or any AI writing workflow
- When voice artifacts have been refreshed and the AI config needs updating

## Prerequisites

At minimum, these artifacts must exist in `voice/`:
- `voice-profile.md` (personality, attributes, phrasings, banned phrases)
- `conventions.md` (writing rules, hard rules)

Optional but enriching:
- `register-map.md` (enables register-aware AI output)
- `audience-language-bank.md` (enables audience-calibrated AI output)

If the prerequisites don't exist, tell the user and suggest running voice-author first.

---

## Workflow

### Step 1: Read Voice Artifacts

Load all existing voice artifacts from `voice/`:
1. `voice-profile.md` -- personality, attributes, reference patterns, phrasings, banned phrases
2. `conventions.md` -- writing rules, hard rules, format templates, quality test
3. `register-map.md` -- registers, when each applies, tone shifts (if exists)
4. `audience-language-bank.md` -- audience language patterns (if exists)

Assess completeness. Note which sections are well-defined vs. thin.

### Step 2: Determine Target Formats

Ask the user what AI tools they use or plan to use:

- **Claude Code / CLAUDE.md** -- the primary format. Produces a voice section for CLAUDE.md.
- **System prompt snippet** -- a condensed voice definition for inclusion in any LLM system prompt.
- **Custom instructions** -- for tools like ChatGPT custom instructions, Cursor rules, etc.
- **All of the above** -- produce ai-voice-config.md as the master, with tool-specific sections.

If the user isn't sure, default to producing ai-voice-config.md with a CLAUDE.md section and a generic system prompt snippet. These cover the most common use cases.

### Step 3: Generate the AI Voice Configuration

Produce `voice/ai-voice-config.md` using the template from `templates/ai-voice-config.md`.

**Translation principles:**

**Condense, don't copy.** The full voice profile might be 200 lines. A system prompt voice section should be 30-50 lines. Prioritize: personality (2-3 sentences), the most distinctive attributes (not all of them), hard rules, banned phrases, and the quality test.

**Make rules machine-checkable.** "Be specific" is hard for an AI to self-check. "Before publishing, verify: every claim names a specific example, number, or scenario" is checkable.

**Include examples.** AI tools calibrate better from examples than from rules. Include 2-3 phrasing pairs (how-we-say-it vs. how-we-don't) directly in the system prompt section.

**Encode registers as conditional instructions.** "When writing client emails, shift to the Client Communication register: warmer tone, lead with validation, offer choices not directives."

**Preserve the hierarchy.** If the company uses Claude Code with nested CLAUDE.md files, define which voice instructions go at which level:
- Root CLAUDE.md: universal conventions, personality, core attributes
- Company/project CLAUDE.md: register selection for this context, audience-specific adjustments
- Per-task instructions: specific format templates, channel-specific rules

### Step 4: Generate Tool-Specific Sections

Based on Step 2, produce the relevant sections:

**CLAUDE.md voice section:**
```markdown
## Voice

[2-3 sentence personality summary]

### Voice attributes
[Most distinctive attributes only, condensed to 1-2 sentences each]

### Writing rules
[Hard rules and the most important writing principles]

### Banned phrases
[Full banned phrase list -- AI tools should check every piece of output against this]

### Quality test
[The one-sentence quality test from conventions.md]
```

**System prompt snippet (for any LLM):**
A self-contained block that can be pasted into any system prompt. 30-50 lines maximum. Includes personality, key rules, banned phrases, and the quality test.

**Register-aware instructions (if register-map exists):**
Conditional instructions for register selection based on task context.

### Step 5: Define Quality Gates

Produce a checklist that AI tools should run on their own output before presenting it. Derived from conventions and the voice profile:

- [ ] No banned phrases appear in the output
- [ ] Hard rules are followed (check each one)
- [ ] Sentence length matches the voice profile's rhythm expectations
- [ ] The opening line follows format conventions (no statistics, no "I've been thinking")
- [ ] The output could pass the quality test (read it back -- does it match the one-sentence description?)
- [ ] The correct register is applied for the task context

### Step 6: Present and Confirm

Present `ai-voice-config.md` to the user. Walk through:
- The condensed personality -- does it capture the essence?
- The priority rules -- are the right ones included?
- The quality gates -- are they checkable and complete?
- The tool-specific sections -- do they match the user's workflow?

Save only after confirmation.

---

## Edit Mode

When voice artifacts have been updated (via voice-refresh → voice-author), re-run voice-encode to update the AI configuration:

1. Read the updated voice artifacts
2. Read the existing `ai-voice-config.md`
3. Identify what changed in the source artifacts
4. Update the corresponding sections in the AI config
5. Present changes for confirmation

Don't regenerate from scratch unless the changes are fundamental (new personality, major attribute changes). For incremental updates (new banned phrases, tweaked rules), apply targeted edits.

---

## Self-check before delivering

- [ ] The system prompt section is 30-50 lines (condensed, not a full copy of the voice profile)
- [ ] Every hard rule from conventions.md is represented in the AI config
- [ ] The full banned phrase list is included (AI tools need the complete list, not a summary)
- [ ] 2-3 phrasing pairs are included as calibration examples
- [ ] Quality gates are checkable (binary: pass or fail on each one)
- [ ] If registers exist, conditional instructions cover when to apply each one
- [ ] The configuration works standalone (doesn't require reading other artifacts to function)
- [ ] The hierarchical inheritance is documented if the user has nested CLAUDE.md files
- [ ] Human has reviewed and confirmed before saving
