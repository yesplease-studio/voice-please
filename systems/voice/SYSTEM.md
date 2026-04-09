# Voice System

A system for defining, encoding, and maintaining a company's voice and language infrastructure so that humans write with coherence and AI tools produce on-brand output. Humans provide judgment, taste, and approval. AI handles analysis, synthesis, and artifact generation.

---

## 1. Core Concepts

### 1.1 What the System Does

The Voice System is the translation layer between how a company thinks it sounds and how it actually sounds. It takes messy inputs -- existing content, reference voices, team conversations, brand docs -- and produces structured artifacts that both humans and AI tools can use to write consistently.

It solves three problems:

1. **Definition.** Converts vague brand adjectives ("professional but approachable") into specific, actionable voice attributes with examples, conventions, and guardrails.
2. **Encoding.** Produces machine-readable voice configurations so AI tools generate on-brand content without manual correction.
3. **Maintenance.** Provides a feedback loop (audit, refresh, re-encode) so the voice system evolves with the company rather than gathering dust.

### 1.2 The Three Layers

Every voice engagement produces artifacts at three layers:

| Layer | Artifacts | Audience | Lifespan | Authored by |
| --- | --- | --- | --- | --- |
| **Definition** | Voice Profile, Conventions, Register Map, Audience Language Bank | Team, writers, AI tools | Long-lived, updated periodically | `voice-author` skill |
| **Encoding** | AI Voice Configuration | AI tools, system prompts, CLAUDE.md files | Derived from Definition layer | `voice-encode` skill |
| **Maintenance** | Audit Reports, Amendment Proposals | Voice owner, team leads | Short-lived, per-cycle | `voice-audit` + `voice-refresh` skills |

The Definition layer is the source of truth. Everything at the Encoding and Maintenance layers is derived from it. One source of truth, multiple projections.

### 1.3 The Six Skills

| Skill | Role | When used |
| --- | --- | --- |
| `voice-recommend` | Maps a challenge or situation to the right skill and dimensions | Entry point when unsure where to start |
| `voice-discover` | Structured content audit and interview that surfaces the company's real voice | Before authoring, especially when starting fresh or when input is thin |
| `voice-author` | Create and edit all voice system artifacts | Start of engagement; after discovery; when the voice needs updating |
| `voice-encode` | Translate voice artifacts into AI-ready configurations | After voice-author produces or updates artifacts |
| `voice-audit` | Evaluate content against the defined voice system | Periodically; when content quality feels inconsistent |
| `voice-refresh` | Propose amendments based on audits, market shifts, or product evolution | After an audit; when the company has changed meaningfully |

Skills are invoked independently and compose into workflows. They never overlap in responsibility: `voice-discover` interviews and analyzes but never writes voice artifacts; only `voice-author` writes Definition-layer artifacts; only `voice-encode` generates Encoding-layer artifacts.

---

## 2. The Eight Dimensions

The Voice System measures voice maturity across eight dimensions. Each dimension answers a core question about whether a specific aspect of the voice system is working.

| # | Dimension | Core question |
|---|-----------|--------------|
| 1 | Voice Identity | Who do we sound like, and is it intentional? |
| 2 | Writing Conventions | Do we have enforceable rules for how we write? |
| 3 | Register System | Can we shift tone for different contexts without losing coherence? |
| 4 | Audience Language | Do we speak in our audience's words or our own? |
| 5 | Content Architecture | Do we have structured templates and formats that encode our voice? |
| 6 | AI Voice Encoding | Can our AI tools produce on-brand output without manual correction? |
| 7 | Multilingual Coherence | Does our voice survive translation across languages and markets? |
| 8 | Voice Governance | Do we have a system for maintaining, evolving, and enforcing our voice? |

### 2.1 Dimension Descriptions

**Dim 1: Voice Identity**
The foundational dimension. Covers whether the company has a defined personality, specific voice attributes, reference voices, and anti-references. Without this, everything else is building on sand. A company at level 1 has no intentional voice. A company at level 5 has a voice so distinctive that readers recognize it before seeing the company name.

**Dim 2: Writing Conventions**
The enforceable layer. Covers hard rules (structural constraints like "no em dashes"), writing principles (quality standards like "specific over vague"), banned phrases, and format standards. The distinction from Dim 1: Voice Identity is descriptive (who we sound like), Writing Conventions is prescriptive (what rules we always follow). A team can have a clear identity but no conventions, or detailed conventions but a generic identity.

**Dim 3: Register System**
Most companies need more than one voice. Marketing content sounds different from client emails, which sound different from product UI copy, which sounds different from investor updates. A register system defines these variations intentionally rather than letting them diverge randomly. Each register has a name, when it's used, how it differs from the default, and example phrasings.

**Dim 4: Audience Language**
The gap between how a company talks and how its audience talks. Covers collecting real customer language (from support tickets, sales calls, reviews, forums), mapping the gap between company-speak and audience-speak, and feeding audience language back into content. A company at level 1 uses internal jargon exclusively. A company at level 5 writes in the audience's words so naturally that customers feel like the company understands them.

**Dim 5: Content Architecture**
Structured templates and formats that encode the voice into repeatable patterns. A LinkedIn post template with hook/body/close structure. An email sequence framework. A landing page format. These bridge voice definition and voice execution -- templates are how voice scales beyond one writer. Without them, every piece of content starts from a blank page and the voice depends entirely on whoever is writing that day.

**Dim 6: AI Voice Encoding**
Whether the voice system is machine-readable. Most companies define their voice in a PDF or slide deck that no AI tool can consume. This dimension measures whether the voice system has been translated into formats AI tools can use: system prompts, CLAUDE.md configurations, writing instructions with quality gates. A company at level 5 has AI tools producing first-draft content that needs minimal human editing for voice consistency.

**Dim 7: Multilingual Coherence**
Whether the voice survives translation across languages and markets. Not just translation accuracy but voice preservation. A company might sound direct and warm in English but formal and distant in Norwegian because nobody defined how the voice adapts across languages. Covers: which conventions are universal vs. language-specific, language-specific registers, cultural adaptation, and per-language quality standards.

**Dim 8: Voice Governance**
The operational system for maintaining the voice over time. Who owns it. How new team members learn it. How violations are caught. How the voice evolves intentionally rather than drifting. How feedback loops work. A company at level 1 has no voice owner. A company at level 5 has an active governance loop: regular audits, a defined refresh cadence, and a process for incorporating learnings.

### 2.2 Dimension Dependencies

Dimensions have dependencies that affect sequencing. Working on a downstream dimension before its dependencies are in place produces fragile results.

```
Dim 1 (Voice Identity) ← upstream of everything
    ↓
Dim 2 (Writing Conventions) ← needs identity to contextualize rules
    ↓
Dim 5 (Content Architecture) ← needs conventions to encode into templates
    
Dim 4 (Audience Language) → feeds Dim 3 (Register System)
    Need to know how the audience talks before designing registers that speak to them.

Dim 6 (AI Voice Encoding) ← depends on Dims 1, 2, 3
    Cannot encode what has not been defined.

Dim 7 (Multilingual Coherence) ← productive after Dims 1-3 in the primary language
    Can be addressed at any point, but yields most when the primary voice is established.

Dim 8 (Voice Governance) ← late-stage
    Makes sense once there are enough voice components to govern.
```

**Foundation dimensions (1-4):** Most companies should establish these before investing in Dims 5-8. The foundation answers: who do we sound like, what rules do we follow, how do we adapt across contexts, and do we speak our audience's language?

**Execution dimensions (5-6):** These operationalize the foundation into templates and AI configurations.

**Maturation dimensions (7-8):** These extend and sustain the system over time and across languages.

### 2.3 Maturity Levels

Each dimension is scored on a 1-5 scale:

| Level | Label | What it looks like |
|-------|-------|--------------------|
| 1 | Not started | No intentional voice work. Content sounds however whoever wrote it happened to write that day. Different team members produce noticeably different voices. |
| 2 | Aware | Recognizes voice matters. May have brand adjectives ("friendly, professional, innovative") but nothing actionable. The best writer carries the voice intuitively. |
| 3 | Developing | Initial voice artifacts exist: a personality description, some writing rules, maybe a list of banned phrases. Used inconsistently. Not encoded for AI tools. |
| 4 | Established | Clear, documented voice system with personality, conventions, registers, and content templates. Actively used by the team. AI tools produce on-brand output with moderate supervision. |
| 5 | Leading | Voice system is a genuine competitive advantage. Fully encoded for AI, multilingual support works, governance loop is active, voice is recognizable across all touchpoints without manual intervention. |

**Scoring principles:**
- Be honest. If you don't have evidence for a level, score lower.
- A single workshop or session rarely moves a dimension more than 1 point.
- Movement only counts when artifacts exist and are actively used, not when the topic was discussed.
- Adjacent dimensions may shift as side effects (defining voice identity often improves conventions awareness).

---

## 3. Challenge-to-Dimension Mapping

When a user describes a problem, map it to dimensions before recommending a skill. This table is the recommendation engine.

| What they say | Primary dimension(s) | Why | Recommended path |
|--------------|---------------------|-----|-----------------|
| "Our content sounds generic" | 1 (Identity), 2 (Conventions) | Generic content is usually an identity problem. No defined voice means everything defaults to safe and bland. | voice-discover → voice-author |
| "Everyone writes differently" | 1 (Identity), 8 (Governance) | Inconsistency is either a definition problem or an enforcement problem. | voice-discover → voice-author |
| "Nobody follows our brand guidelines" | 8 (Governance), 2 (Conventions) | Guidelines that aren't followed are usually too vague or there's no enforcement system. | voice-audit → voice-refresh |
| "Our website sounds corporate" | 1 (Identity), 4 (Audience Language) | Corporate-sounding content signals writing for the company, not the audience. | voice-discover (audience focus) |
| "AI tools produce off-brand content" | 6 (AI Encoding) | The voice exists in human-readable form but isn't encoded for machines. | voice-encode |
| "Our blog sounds different from our emails" | 3 (Registers) | Inconsistency across channels means registers aren't defined. | voice-author (register focus) |
| "We use our own jargon and customers don't get it" | 4 (Audience Language) | The gap between company language and audience language. | voice-discover (audience focus) |
| "New hires can't write in our voice" | 5 (Content Architecture), 8 (Governance) | Onboarding writers requires templates and a governance system, not just guidelines. | voice-audit → voice-author (templates) |
| "Our Norwegian content sounds like bad English translation" | 7 (Multilingual) | Voice doesn't survive language transfer. | voice-discover → voice-author (multilingual) |
| "We need to figure out our voice" | 1 (Identity) | Starting from scratch. | voice-discover → voice-author |
| "We're rebranding and need a new voice" | 1 (Identity), 3 (Registers) | Rebrand means identity needs redefining, and registers often need restructuring. | voice-discover → voice-author |
| "Our founder needs a LinkedIn voice" | 1 (Identity) -- person level | Individual voice definition, distinct from company voice. | voice-discover → voice-author (person voice) |
| "Content is fine but nothing is memorable" | 1 (Identity), 2 (Conventions) | "Fine but forgettable" means the voice lacks distinctiveness. Conventions are safe, not sharp. | voice-discover → voice-refresh |
| "Expanding internationally, voice needs to work in multiple languages" | 7 (Multilingual) | But check Dims 1-3 first. You can't translate a voice you haven't defined. | voice-discover → voice-author (multilingual) |
| "Voice guidelines are in a PDF nobody reads" | 6 (AI Encoding), 8 (Governance) | The voice exists but isn't operationalized. Encode it for AI, build the enforcement loop. | voice-encode |
| "Multiple things feel broken about our content" | Start with audit | When everything feels broken, run the diagnostic first. | voice-audit |

---

## 4. Sequencing Principles

When a company needs work across multiple dimensions, sequence the work to respect dependencies and maximize impact.

### 4.1 Default sequence for companies starting from scratch

```
1. voice-discover (assess all 8 dimensions, collect references)
2. voice-author: Voice Identity (Dim 1) + Writing Conventions (Dim 2)
3. voice-author: Register System (Dim 3) + Audience Language (Dim 4)
4. voice-encode: AI Voice Encoding (Dim 6)
5. voice-author: Content Architecture (Dim 5) -- if needed
6. voice-author: Multilingual (Dim 7) -- if applicable
7. Establish Voice Governance (Dim 8)
```

Steps 2-3 are the foundation. Most companies get significant value from just these. Steps 4-7 are where the system becomes self-sustaining.

### 4.2 Default sequence for companies with existing voice work

```
1. voice-audit (score all 8 dimensions against existing artifacts)
2. voice-refresh (propose amendments for the weakest dimensions)
3. voice-author (apply amendments, fill gaps)
4. voice-encode (update AI configurations)
```

### 4.3 Sequencing rules

- **Dim 1 first, always.** Identity is upstream of everything. Don't define conventions without knowing who you sound like.
- **Dim 4 before Dim 3.** Audience language informs register design. Know how your audience talks before designing how you adapt your voice for them.
- **Dim 2 before Dim 5.** Conventions inform templates. Templates encode conventions, not the other way around.
- **Dims 1-3 before Dim 6.** Don't encode what hasn't been defined.
- **Dim 7 after primary language is established.** Multilingual work is most productive when the primary voice is clear.
- **Dim 8 is ongoing.** Governance isn't a one-time step. Introduce it once there are enough artifacts to govern, then maintain it.

---

## 5. The Voice System Artifacts

The Definition layer produces five structured artifacts. Each has a template in `templates/` and is created or edited exclusively by `voice-author`.

### 5.1 Voice Profile (`voice-profile.md`)

The anchor document. Defines who the company sounds like.

**Contains:**
- Personality description (how the company actually sounds, not aspirational adjectives)
- Voice attributes (3-5 specific characteristics with descriptions and examples)
- Reference voices (companies, founders, or creators whose communication style resonates, with specific patterns extracted from each)
- Anti-references (who the company does NOT want to sound like, with specific patterns to avoid)
- Phrasings to use (company-specific language patterns, how-we-say-it vs. how-we-don't pairs)
- Banned phrases (company-specific prohibitions beyond any universal list, each with a reason)

**Dimensions addressed:** Primarily Dim 1 (Voice Identity). Informs all other dimensions.

### 5.2 Conventions (`conventions.md`)

The enforceable rules.

**Contains:**
- Writing rules (principles that guide all content, each with a brief rationale)
- Hard rules (non-negotiable structural constraints -- the "always" and "never" rules)
- Banned phrases (universal list applicable across all content)
- Format templates (per-format structure guides for key content types)
- Quality test (one-sentence description of what good content sounds like for this company)

**Dimensions addressed:** Dim 2 (Writing Conventions). Feeds into Dim 5 (Content Architecture).

**Note on defaults:** The conventions template includes an opinionated starter set of writing rules and banned phrases. Companies should adopt, modify, or replace these based on their own judgment. The starter set is clearly labeled as optional.

### 5.3 Register Map (`register-map.md`)

The system for shifting tone across contexts.

**Contains:**
- Named registers (each with: when to use, relationship to base voice, temperature/formality/energy shifts, example phrasings, convention overrides)
- Default register (which register applies when none is specified)
- Register selection guide (how to determine which register to use for a given task)

**Dimensions addressed:** Dim 3 (Register System).

### 5.4 Audience Language Bank (`audience-language-bank.md`)

The bridge between company-speak and audience-speak.

**Contains:**
- How they describe the problem (verbatim phrases from the audience)
- How they describe us (verbatim phrases about the company from reviews, testimonials, support)
- Words they use that we don't (language gaps)
- Words we use that they don't (internal jargon that doesn't land)
- Trigger phrases (words and framings that signal someone is in the ICP)

**Dimensions addressed:** Dim 4 (Audience Language). Feeds into Dim 3 (Register System).

### 5.5 AI Voice Configuration (`ai-voice-config.md`)

The machine-readable voice system.

**Contains:**
- Voice loading instructions (what an AI tool should read at the start of every conversation)
- System prompt voice section (condensed voice definition for inclusion in system prompts)
- Register selection rules (how AI determines which register to use based on task context)
- Quality gates (checks AI should run on its own output: banned phrase scan, convention compliance, voice attribute alignment)
- Language/region overrides (per-language adaptations)
- Hierarchical inheritance rules (how voice configurations compose: root defaults → company overrides → project overrides → per-person overrides)

**Dimensions addressed:** Dim 6 (AI Voice Encoding).

---

## 6. Where a Facilitator Adds Value

voice-please is designed to be self-serve usable. Every skill produces useful output when run independently. But some dimensions benefit significantly from having an experienced facilitator in the room.

| Dimension | Self-serve quality | With facilitator |
|-----------|-------------------|-----------------|
| 1 (Voice Identity) | Solid framework; may default to generic adjectives | Facilitator hears what's actually distinctive, pushes past "professional but approachable" to specific attributes |
| 2 (Conventions) | Good; rules are relatively objective | Facilitator brings cross-company pattern recognition for which rules actually stick |
| 3 (Registers) | Adequate; may miss registers the team takes for granted | Facilitator identifies implicit registers the team uses but hasn't named |
| 4 (Audience Language) | Strong if the team has direct customer contact | Facilitator brings ICP expertise and can spot when teams describe their ideal customer vs. their actual customer |
| 5 (Content Architecture) | Good; template creation is systematic | Facilitator brings format expertise from seeing what works across companies |
| 6 (AI Encoding) | Good; systematic translation | Facilitator brings AI tooling expertise for optimal encoding |
| 7 (Multilingual) | Adequate for basic translation guidelines | Facilitator with cross-cultural experience catches voice shifts that native speakers miss |
| 8 (Governance) | Solid; process design is systematic | Facilitator brings org design experience for who owns what and how to make it stick |

The highest-value facilitation is on Dim 1 (Voice Identity) and Dim 3 (Registers). These require taste and judgment that AI can support but not replace. The synthesis step in `voice-discover` -- combining reference voices into something distinctly the company's own -- is where a facilitator earns the most value.

---

## 7. Design Principles

**Voice is observed, not invented.** A company already has a voice. Discovery surfaces what it actually is, rather than inventing an aspirational version. The best voice profiles describe how the company sounds at its best, not how it wishes it sounded.

**Specific over generic.** "Sounds like a thoughtful friend who has actually read the thing" is a voice. "Professional but approachable" is not. Every voice attribute should be specific enough that a stranger could read it and write recognizably on-brand content.

**Reference voices are the fastest path to specificity.** Most founders can't articulate their voice from scratch. But they can immediately point to 3-4 companies or people whose communication style resonates. Analyzing what specifically resonates -- and combining those patterns -- is faster and more specific than starting from adjectives.

**Conventions must be enforceable.** A rule that can't be checked (by a human or an AI tool) isn't a convention, it's a wish. Good conventions are binary: did this piece of content follow the rule or not?

**Registers are how voice scales.** One voice definition for all contexts guarantees that it will sound wrong in half of them. Naming the registers and defining how they differ is what allows a company to sound consistent without sounding monotone.

**AI encoding is not an afterthought.** If the voice system can't be consumed by AI tools, it will be ignored as soon as AI-generated content becomes the default. Encoding is a first-class output, not a nice-to-have.

**Multilingual is not translation.** Voice doesn't translate. It adapts. A company that sounds direct and warm in English might sound cold and formal in Norwegian if the translation is literal. Multilingual voice work defines how the voice adapts per language, not just how the words translate.

**Voice systems decay.** Without governance, a voice system has a half-life of about 6 months. New team members, product evolution, market shifts, and simple drift all erode consistency. The maintenance cycle (audit → refresh → re-encode) is what keeps the system alive.
