# Contributing to voice-please

Skills, templates, and the dimension taxonomy are the core of this project. Contributions that improve existing skills, refine templates, expand the challenge-to-dimension mapping, or add example walkthroughs are welcome.

---

## What makes a good contribution

Before submitting, check that your contribution:

1. **Improves specificity.** The system's value comes from being specific enough that someone can act on it. "Be authentic" is not a voice attribute. "Direct without being blunt -- state things plainly, frame as 'here's what I've observed' not 'here's what you're doing wrong'" is.

2. **Respects the single-writer pattern.** Only `voice-author` writes Definition-layer artifacts. Only `voice-encode` writes Encoding-layer artifacts. If your contribution introduces a new skill, it should not overlap with these responsibilities.

3. **Follows existing patterns.** Skills follow the frontmatter + purpose + workflow + self-check structure. Templates follow the section patterns established in the existing artifacts. Read 2-3 existing files before writing.

4. **Produces concrete artifacts.** Every skill should produce a named output. "Better understanding of voice" is not an artifact. "A voice profile with personality, 4 attributes, 3 reference voices, and 8 phrasings" is.

---

## Types of contributions

### Improving existing skills

The most impactful contributions are refinements to existing skills:

- **Better interview questions** in voice-discover (especially for the reference voice and anti-reference lenses)
- **Sharper quality standards** in voice-author (what makes a voice attribute specific enough?)
- **More effective quality gates** in voice-encode (what checks actually catch voice drift in AI output?)
- **Better audit criteria** in voice-audit (how to evaluate register compliance, audience alignment)

### Expanding the challenge-to-dimension mapping

The mapping table in `systems/voice/SYSTEM.md` is the recommendation engine. If you've used voice-recommend and found that a common voice challenge isn't mapped, submit a PR adding it.

Format:
```
| "What the user says" | Primary dimension(s) | Why | Recommended path |
```

### Improving templates

Template improvements that make the output artifacts more useful:

- **New sections** that address common gaps
- **Better scaffolding** that guides voice-author toward more specific output
- **Format refinements** that make artifacts easier to scan and use

### Adding examples

Example walkthroughs in `examples/` that show the full flow for a specific company type. Anonymize real engagements or create fictional ones. A good example:

- Shows the complete flow from discovery through encoding
- Demonstrates how the three-lens interview (current voice, references, anti-references) produces specific artifacts
- Includes realistic content samples and reference voice analysis
- Covers at least dimensions 1-4

### Adding to the tracking system

If you've run voice-please and can share anonymized outcomes, add entries to `tracking/effectiveness-log.md` following the format in `tracking/README.md`.

---

## How to contribute

### Option 1: Use Claude Code

Open this repo in Claude Code and describe what you want to improve. The system will guide you through the relevant files and patterns.

### Option 2: Submit a PR

1. Read the existing files in the area you're changing
2. Follow the established patterns
3. Submit a pull request with a clear description of what changed and why

---

## Review criteria

| Criterion | What we're checking |
|-----------|-------------------|
| **Pattern compliance** | Follows existing skill/template/system structures |
| **Specificity** | Improves actionability, not just coverage |
| **Evidence-based** | Changes are grounded in real usage, not theoretical improvement |
| **Single-writer respected** | No skill overlaps with voice-author or voice-encode responsibilities |
| **Dimension accuracy** | Any dimension references correctly map to the taxonomy in SYSTEM.md |

---

## What's out of scope

- **Content operations** (editorial calendars, publishing workflows, sprint cadences) -- voice-please defines the voice; how content gets produced is a separate system
- **Content generation skills** (write a LinkedIn post, draft an email) -- voice-please produces the system that content generation tools consume, not the content itself
- **Full brand strategy** -- if the company can't define its voice because it doesn't know what it stands for, that's a strategy-please problem, not a voice-please problem

---

## Code of conduct

Be direct, be specific, be helpful. The same principles that make a good voice system make a good contribution: specificity over vagueness, evidence over opinion, concrete over abstract.
