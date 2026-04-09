# Effectiveness Tracking

Track outcomes from voice-please engagements to improve the system over time. Every engagement is a hypothesis ("this skill, applied to this dimension, at this maturity level, produces this outcome"). Tracking validates or refutes those hypotheses.

---

## How it works

After completing a voice engagement (or a significant skill run), log an entry in `effectiveness-log.md`. The log captures what was done, what it produced, and whether the outcome matched expectations.

Over time, patterns emerge:
- Which skills produce the most value at which maturity levels
- Which dimensions are hardest to move
- Where facilitation makes the biggest difference vs. self-serve
- Which reference voice patterns lead to the most distinctive profiles
- Common pitfalls and how to avoid them

---

## Log entry format

Each entry follows this structure:

```markdown
## [Date] -- [Company descriptor] -- [Skill(s) run]

- **Company type:** [Industry, stage, team size -- anonymized]
- **Skill(s):** [voice-discover, voice-author, etc.]
- **Dimensions targeted:** [Dim 1, Dim 2, etc.]
- **Maturity before:** [Dim X: score, Dim Y: score]
- **Maturity after:** [Dim X: score, Dim Y: score]
- **Delta:** [Dim X: +N, Dim Y: +N]
- **Facilitation:** [Self-serve / Guided / Expert]
- **Artifacts produced:** [voice-profile.md, conventions.md, etc.]
- **Time invested:** [Approximate total time]
- **Key insight:** [One sentence -- the most important thing learned]
- **What worked well:** [Specific observation]
- **What was difficult:** [Specific observation]
- **Would recommend this approach again:** [Yes / Yes with adjustments / No]
- **Adjustments noted:** [If applicable -- what to do differently next time]
```

---

## Anonymization

Company names are replaced with descriptive labels:

- "8-person Norwegian fintech, seed stage"
- "50-person B2B SaaS, Series A, English-only content"
- "Solo founder, consumer app, pre-revenue"

The label should give enough context to make the entry useful for pattern recognition without identifying the company.

---

## What to track

**After every full engagement** (new-engagement or voice-foundations workflow):
- Full entry with before/after dimension scores

**After audits:**
- Dimension scores and key findings
- Whether the audit triggered a refresh

**After refreshes:**
- Which amendments were proposed vs. accepted vs. rejected
- Whether the refresh changed the maturity scores

**Periodically:**
- Cross-engagement patterns (which dimensions are hardest to move, which skills produce the most value)

---

## How this feeds improvement

The tracking data drives updates to:
- **SYSTEM.md** -- maturity level descriptions, challenge-to-dimension mapping accuracy, sequencing principles
- **Skills** -- workflow steps, interview questions, quality standards
- **Templates** -- artifact structure, section usefulness, common gaps
- **Facilitation guidance** -- where self-serve works vs. where facilitation adds value
