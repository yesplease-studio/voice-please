---
name: voice-author
description: >
  Create and edit voice system artifacts: voice-profile.md, conventions.md, register-map.md,
  and audience-language-bank.md. This is the only skill authorized to write or modify
  Definition-layer voice artifacts. Use this skill whenever you need to create a new voice
  system from scratch, revise existing voice artifacts, incorporate amendments proposed by
  voice-refresh, or make any changes to the voice system. Trigger when the user says things
  like "define our voice", "write our conventions", "build the voice system", "update the
  voice profile", "add a new register", or "incorporate these changes". Always use this skill
  when voice artifacts are the output.
system: voice
integrations:
  required: []
  optional: []
---

# Skill: voice-author

**Purpose:** Create and edit all Definition-layer voice system artifacts. This is the only skill authorized to write or modify voice-profile.md, conventions.md, register-map.md, and audience-language-bank.md.

---

## When to Use

- Starting a new voice engagement (create mode).
- The company's voice needs updating (edit mode).
- `voice-refresh` has proposed amendments that need to be applied (edit mode).
- The user requests changes to any voice artifact (edit mode).

## Two Modes

### Create Mode

Takes a Discovery Brief or direct user input and produces voice system artifacts. Works conversationally in phases to ensure quality and alignment before writing.

### Edit Mode

Takes existing voice artifacts and applies targeted changes. Preserves unchanged sections. Never weakens specificity without explicit human instruction (e.g., don't replace a specific attribute with a generic one).

---

## Create Mode Workflow

### Phase 1: Gather and Assess Input

**If a Discovery Brief exists:** Read it as the primary source. The brief contains content analysis, reference voice map, anti-references, dimension assessment, and recommended next steps. Use it as the foundation -- don't re-interview what discovery already covered.

**If no Discovery Brief exists:** Collect available input:
- Content samples (existing posts, articles, emails, website copy)
- Brand documents (guidelines, tone docs, style guides)
- Reference voices (companies, founders, creators the user admires)
- Verbal descriptions from the user
- URLs to analyze

**Assess what you have.** Before proceeding, determine:
- Is the voice identity clear enough to define personality and attributes?
- Are there enough reference voices to synthesize a distinctive combination?
- Are conventions identifiable from the content samples?
- Which artifacts can be produced with current input, and which need more?

If critical gaps exist, surface them in Phase 2 rather than guessing.

### Phase 2: Interview (if needed)

If starting without a Discovery Brief, or if the brief has gaps, fill them conversationally. Use `AskUserQuestion` to batch 2-4 questions per call.

**For Voice Identity gaps:**
- Share content analysis observations and ask for confirmation
- Ask for reference voices and what specifically resonates
- Ask for anti-references and what specifically to avoid

**For Conventions gaps:**
- Ask about existing writing rules (formal or informal)
- Ask about content pet peeves ("what do you always correct in other people's writing?")
- Propose the starter set from the conventions template and ask what resonates

**For Register gaps:**
- Ask what channels they write for
- Ask whether the tone shifts across contexts (it almost always does)
- Identify implicit registers the team uses but hasn't named

**For Audience Language gaps:**
- Ask how customers describe their product
- Ask what language shows up in support tickets, sales calls, reviews

### Phase 3: Outline and Confirm

Before writing full artifacts, present an outline of what you'll produce. This prevents wasted work.

**Voice Profile outline:**
- Personality (1-2 sentence summary)
- Proposed voice attributes (3-5, with one-line descriptions)
- Reference voices (which ones, what patterns from each)
- Anti-references (key patterns to avoid)

**Conventions outline:**
- Proposed writing rules (list of principles)
- Proposed hard rules (structural constraints)
- Proposed banned phrases (company-specific)

**Register Map outline (if producing):**
- Named registers and when each applies
- How each differs from the default

Present this outline and ask: "Does this direction feel right before I write the full artifacts?"

Incorporate feedback. This is where the user's taste and judgment matter most. If they push back on a proposed attribute or rule, understand why before adjusting.

### Phase 4: Write Artifacts

Produce the voice artifacts using the templates in `templates/`. Write to `voice/`.

**Artifact writing order:**
1. **voice-profile.md** first (the anchor document, everything references it)
2. **conventions.md** second (the enforceable rules)
3. **register-map.md** third (if the engagement includes registers)
4. **audience-language-bank.md** fourth (if audience language data exists)

For each artifact:
- Use the corresponding template from `templates/` as the scaffold
- Fill in every section with specific, evidence-based content
- Reference the Discovery Brief or user input as source material
- Flag sections where input was insufficient with `[Needs more input: <what's missing>]`

### Phase 5: Present and Confirm

Present each artifact to the user before saving. Walk through:

- **Voice Profile:** Read the personality description aloud (mentally). Does it sound like this company? Are the attributes specific enough that a stranger could write on-brand content?
- **Conventions:** Are the rules enforceable? Could you check each one against a piece of content?
- **Register Map:** Do the registers cover the contexts the company actually writes in?
- **Audience Language Bank:** Does the language feel like real audience words, not company projections?

Save only after confirmation on each artifact.

---

## Edit Mode Workflow

### Step 1: Understand the Change

Read the existing artifact(s) being modified. Determine:
- What specifically needs to change and why
- Whether the change comes from voice-refresh amendments, user request, or new context
- Which sections are affected

### Step 2: Propose Changes

Present the proposed changes in context:
- Show the current text
- Show the proposed replacement
- Explain the rationale

For changes proposed by voice-refresh, include the amendment rationale from the refresh report.

### Step 3: Apply and Confirm

Apply approved changes. Preserve unchanged sections exactly. After editing, show the user the updated artifact and confirm.

---

## Artifact Quality Standards

### Voice Profile

- **Personality is a paragraph, not adjectives.** "Writes like someone who has sat in the chair" is specific. "Professional but approachable" is not.
- **Each voice attribute has a name and a description paragraph.** The description includes what it means in practice, not just what it is.
- **Reference voices include specific extracted patterns.** "Like Stripe" is insufficient. "Stripe's calm precision when explaining complex infrastructure" is usable.
- **Anti-references are equally specific.** "Not corporate" isn't a boundary. Name the specific patterns to avoid.
- **Phrasings include how-we-say-it vs. how-we-don't pairs.** These are the fastest way for a new writer to calibrate.
- **Banned phrases each have a reason.** The reason prevents someone from reintroducing a banned phrase with slightly different wording.

### Conventions

- **Every rule is enforceable.** A rule that can't be checked (by a human or AI) isn't a convention.
- **Hard rules are binary.** "No em dashes" is enforceable. "Use em dashes sparingly" is not.
- **The quality test is one sentence.** It captures what good content sounds like for this company. If you can't say it in one sentence, it's not sharp enough.
- **Format templates are concrete.** A LinkedIn post template should specify hook structure, body rhythm, and close style -- not just "write a LinkedIn post."

### Register Map

- **Each register has a name that the team will actually use.** "Published content register" works. "Register A" does not.
- **Relationships to the base voice are specific.** "Warmer than default" is vague. "Temperature runs warmer: genuine enthusiasm about the work is genuine. 'Good morning!' is not filler" is specific.
- **Example phrasings show the same idea in different registers.** This is the fastest way to understand what a register means in practice.

### Audience Language Bank

- **Language is verbatim, not paraphrased.** The value is hearing the audience's actual words.
- **Gaps between company-speak and audience-speak are named.** "We say 'recruitment intelligence platform'; they say 'that tool that finds old candidates'" is actionable.

---

## Self-check before delivering

- [ ] Every voice attribute is specific enough that a stranger could write on-brand content using it
- [ ] Reference voices include extracted patterns, not just names
- [ ] Anti-references include specific patterns to avoid, not just "don't be corporate"
- [ ] Conventions are enforceable (binary: did the content follow the rule or not?)
- [ ] The quality test is one sentence
- [ ] Phrasings include how-we-say-it vs. how-we-don't pairs
- [ ] Banned phrases each have a reason
- [ ] Register names are ones the team would actually use in conversation
- [ ] All artifacts reference the Discovery Brief or user input as evidence (not invented)
- [ ] Human has reviewed and confirmed before saving
