# Example: Aurora Analytics — Full Voice System Flow

A fictional walkthrough showing the complete voice-please flow for a Norwegian B2B SaaS company. Aurora Analytics is a 12-person data analytics platform for mid-market logistics companies, Series A, based in Oslo.

---

## Starting Point

Aurora's CEO, Kari, opens voice-please in Claude Code and says:

> "Our content sounds generic. We've been writing LinkedIn posts and blog articles for a year but nothing sounds like us. It sounds like every other SaaS company."

### voice-recommend maps the challenge

**Challenge:** "Our content sounds generic"
**Primary dimensions:** Dim 1 (Voice Identity), Dim 2 (Writing Conventions)
**Recommended path:** voice-discover → voice-author

> "Generic content is usually an identity problem before it's a writing problem. You don't have a defined voice, so everything defaults to safe and bland. Let's start with voice-discover to figure out what you actually sound like at your best, and what you're drawn to."

---

## Phase 1: voice-discover

### Content Analysis

Kari shares 5 pieces of existing content:
- 3 LinkedIn posts from the company page
- 1 blog article on logistics optimization
- The Aurora homepage

**Patterns observed:**

| Pattern | Finding |
|---------|---------|
| Sentence length | Medium-to-long. Few short punchy sentences. |
| Formality | Professional-corporate. Reads like it was written for a board deck. |
| Energy | Low. Measured and careful. No moments of genuine enthusiasm. |
| Specificity | Moderate. Some logistics-specific examples, but many generic claims ("powerful analytics", "actionable insights"). |
| Humor | Absent entirely. |
| Structure | Heavy on bullet points. Almost no flowing prose. |
| Person | Third person ("Aurora provides..."). Never first person. |
| Jargon | High internal jargon ("supply chain visibility layer", "predictive routing matrix"). |

**Inconsistencies:** The homepage is more corporate than the LinkedIn posts. The blog article sounds like a different company -- more technical, more specific, written by the CTO rather than marketing.

**Strongest existing content:** The CTO's blog article. It's specific, uses real numbers, and explains complex logistics concepts in a way that feels like talking to someone who has actually worked in a warehouse. This is closer to a real voice than anything on the marketing side.

### Reference Voice Interview

**Lens 2: Reference voices**

Kari identifies three:

1. **Varda (Norwegian fintech startup)**
   - What resonates: "They explain complex financial infrastructure without dumbing it down. It feels like talking to a smart friend who happens to work in banking."
   - Extracted pattern: Technical precision without academic distance.

2. **PostHog (open-source analytics)**
   - What resonates: "They're honest about what their product does and doesn't do. And they're funny without trying too hard."
   - Extracted pattern: Challenger honesty with understated humor.

3. **Sindre Sorhus (open-source developer)**
   - What resonates: "Everything he writes is concise. No filler. You read a sentence and it's exactly what he means."
   - Extracted pattern: Radical conciseness.

**Synthesis:** Aurora's voice wants to combine technical precision (Varda) with honest directness (PostHog) and radical conciseness (Sindre). The result should feel like talking to the smartest logistics person in the room -- someone who has actually loaded a truck, not just built dashboards about trucks.

**Lens 3: Anti-references**

- "Every SaaS company that calls their product 'powerful' and 'seamless'. We are definitely that."
- "LinkedIn thought leaders who post inspirational content about 'the future of logistics'. Empty calories."
- "Enterprise software companies that use 30 words where 10 would do."

**Extracted patterns to avoid:** Generic SaaS language, aspirational thought leadership, verbosity.

**Candidate banned phrases:** powerful, seamless, actionable insights, leverage, supply chain visibility (their own jargon that customers don't use), "the future of logistics."

### Lens 4: Audience Perspective

Kari shares some language from sales calls:

- Customers say "I need to know where my stuff is" not "supply chain visibility"
- Customers say "we're guessing" when they mean their forecasting is broken
- Customers say "the data is there but nobody can use it" about their current analytics

### Dimension Assessment

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Voice Identity | 1/5 | No defined voice. Best content (CTO blog) is accidental, not systematic. |
| 2 | Writing Conventions | 1/5 | No rules. Each piece of content follows whatever the writer felt that day. |
| 3 | Register System | 1/5 | No defined registers. Marketing and technical content sound like different companies. |
| 4 | Audience Language | 2/5 | Some awareness of customer language from sales calls, but not documented or used in content. |
| 5 | Content Architecture | 1/5 | No templates. Every post starts from scratch. |
| 6 | AI Voice Encoding | 1/5 | Not using AI for content; no voice system to encode. |
| 7 | Multilingual Coherence | N/A | English-only content for now. |
| 8 | Voice Governance | 1/5 | No voice owner. No review process. |

---

## Phase 2: voice-author

### Outline confirmed with Kari

**Proposed personality:** "Aurora sounds like the person in the logistics meeting who has actually been in the warehouse. Technical precision without academic distance. Direct enough to say 'your forecasting is broken' but specific enough to explain why and what to do about it. Concise -- if it can be said in 5 words, don't use 15."

**Proposed attributes:**
1. Warehouse-floor credibility
2. Concise and specific
3. Honestly direct
4. Understated dry humor

Kari confirms: "Yes. That's what the CTO's blog sounded like, and that's what we should all sound like."

### Voice Profile produced

```markdown
# Voice Profile: Aurora Analytics

## Personality

Aurora sounds like the smartest logistics person in the room who happens to
build software. Not a SaaS company that read about logistics -- a team that
has stood on warehouse floors, watched dispatchers juggle spreadsheets, and
built the tool they wished existed. The voice comes from having done this
work, not from observing it from a dashboard.

Technical without being academic. Direct without being dismissive. The kind
of person who says "your forecasting is broken" and then shows you exactly
where and why.

## Voice Attributes

### Warehouse-floor credibility
Write from inside the logistics experience. Reference real scenarios:
shift changes, delayed shipments, the dispatcher who keeps a backup
spreadsheet because she doesn't trust the system. Credibility is
established through specific operational knowledge, not credentials
or company size.

### Concise and specific
Every sentence earns its place. "Your fleet data shows 23% idle time
between 2-4pm on Tuesdays" beats "our powerful analytics platform
provides actionable insights into fleet utilization." Name the number,
the time, the specific problem. If it can be said in fewer words, use
fewer words.

### Honestly direct
Name what's broken without sugarcoating it. "Most logistics companies
are guessing their demand forecasts" is a true observation that earns
trust. But always follow the diagnosis with something useful -- what
to do about it, where to look, how others have solved it.

### Understated dry humor
The occasional wry observation about the absurdity of logistics
technology. Not jokes. Not LinkedIn-style "what if I told you" setups.
The kind of humor that makes a logistics manager smile at their desk
because they recognize the situation.

## Reference Voices

### Varda (Norwegian fintech)
- What we take: Technical precision when explaining complex systems.
  Financial infrastructure explained like a conversation, not a textbook.
- How it shows up: When we explain analytics concepts, we use the same
  "smart friend explains it" register. No dumbing down, no academic distance.

### PostHog (open-source analytics)
- What we take: Challenger honesty about what the product does and doesn't do.
  Willingness to name industry problems directly.
- How it shows up: We'll say "most logistics analytics tools show you
  what happened last week. That's a report, not intelligence." Direct
  comparison without being smug.

### Sindre Sorhus (developer)
- What we take: Radical conciseness. Every word matters. No filler.
- How it shows up: Our sentences are short. Our paragraphs are short.
  We trust the reader to follow without hand-holding.

## Anti-References

- Generic SaaS language ("powerful", "seamless", "actionable insights") --
  because it's what every company says and it means nothing.
- Aspirational thought leadership ("the future of logistics") -- because
  our customers care about today's shipment, not a 2030 vision.
- Enterprise verbosity (30 words where 10 would do) -- because our
  readers are busy and we respect their time.

## Phrasings

| How we say it | Not like this |
|--------------|--------------|
| "Your forecasting is broken" | "There may be opportunities to optimize your demand planning" |
| "Know where your stuff is" | "Supply chain visibility layer" |
| "Most companies are guessing" | "Many organizations face challenges in predictive accuracy" |
| "Here's what the data shows" | "Our powerful analytics reveal actionable insights" |
| "That's a report, not intelligence" | "Traditional reporting solutions have limitations" |

## Banned Phrases

| Phrase | Reason |
|--------|--------|
| powerful | Every SaaS product claims this. It says nothing. |
| seamless | Describes a wish, not a reality. |
| actionable insights | Corporate filler. Say what the insight actually is. |
| supply chain visibility | Our jargon. Customers say "know where my stuff is." |
| the future of logistics | Aspirational thought leadership we explicitly avoid. |
| leverage (verb) | Use "use." |
| end-to-end | Specify what ends. |
```

### Conventions produced

```markdown
# Writing Conventions: Aurora Analytics

## Writing Rules

**Short sentences. Use them.**
If a sentence needs a comma to survive, it's probably two sentences.
Aurora's voice is built on conciseness.

**Specific over vague.**
"23% idle time on Tuesdays between 2-4pm" not "fleet utilization
challenges." Every claim should have a number, a name, or a scenario
attached to it.

**Name the problem first.**
Start with what's broken. The reader should recognize their own
situation before hearing about a solution.

**Write from the warehouse floor.**
Reference real logistics scenarios. Shift changes, delayed shipments,
overloaded dispatchers. The reader should feel like the writer has
done this work.

## Hard Rules

- No sentences longer than 25 words. If you need more, split it.
- Never open a piece of content with a statistic.
- No em dashes. Rewrite the sentence.
- No exclamation marks in published content.

## Banned Phrases

[Full list from voice profile, plus:]

| Phrase | Reason |
|--------|--------|
| best-in-class | Unverifiable claim. |
| game-changer | Meaningless superlative. |
| robust | Technical filler. |
| holistic | Says nothing. |
| revolutionize | Almost never true. |
| thrilled/excited/delighted to announce | Performative enthusiasm. |

## Format Templates

### LinkedIn Post
- Hook: One sentence. A specific logistics problem or observation.
  Not a question. Not a statistic.
- Body: 3-5 short paragraphs, 1-2 lines each.
- Close: A quiet observation that lands. No CTA, no "what do you think?",
  no "follow for more."
- Length: 100-150 words.
- Register: Default (published content).

## Quality Test

> "The best Aurora content sounds like it was written by someone who
> just walked off a warehouse floor and sat down to tell you exactly
> what they saw."
```

---

## Phase 3: voice-encode

voice-encode condenses the voice system into a CLAUDE.md section and system prompt snippet.

**CLAUDE.md voice section produced:**

```markdown
## Voice

Aurora sounds like the smartest logistics person in the room who happens to
build software. Technical precision without academic distance. Direct enough
to say "your forecasting is broken" but specific enough to explain why.
Concise -- fewer words, always.

Full voice definition: voice/voice-profile.md
Writing conventions: voice/conventions.md

### Quick reference

**Attributes:** Warehouse-floor credibility, concise and specific,
honestly direct, understated dry humor.

**Hard rules:**
- No sentences longer than 25 words
- Never open with a statistic
- No em dashes
- No exclamation marks

**Banned phrases:** powerful, seamless, actionable insights, supply chain
visibility, the future of logistics, leverage, end-to-end, best-in-class,
game-changer, robust, holistic, revolutionize, thrilled/excited/delighted
to announce

**Quality test:** "Sounds like someone who just walked off a warehouse
floor and sat down to tell you exactly what they saw."
```

**Quality gates:**

- [ ] No banned phrases in the output
- [ ] All sentences under 25 words
- [ ] Opening line is not a statistic
- [ ] No em dashes
- [ ] No exclamation marks
- [ ] At least one specific number, scenario, or logistics reference
- [ ] Passes the quality test (warehouse-floor energy)

---

## Outcome

**Time invested:** ~2 hours total
**Artifacts produced:** voice-profile.md, conventions.md, ai-voice-config.md
**Dimensions moved:**

| Dimension | Before | After | Delta |
|-----------|--------|-------|-------|
| 1 (Voice Identity) | 1 | 3 | +2 |
| 2 (Writing Conventions) | 1 | 3 | +2 |
| 3 (Register System) | 1 | 1 | -- |
| 4 (Audience Language) | 2 | 2 | -- |
| 6 (AI Voice Encoding) | 1 | 3 | +2 |

**What came next:** Kari used the voice system for 6 weeks, then ran voice-audit on her team's recent content. The audit found strong identity compliance but inconsistent conciseness (new team members wrote longer sentences). She ran voice-refresh to add an onboarding checklist to the governance section, and voice-encode to update the AI config.

Register mapping (Dim 3) and audience language bank (Dim 4) were added in a follow-up session after Aurora hired a content writer who needed more structured guidance.
