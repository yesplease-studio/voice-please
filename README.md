<img width="1584" height="396" alt="Github-voice-please" src="https://github.com/user-attachments/assets/282bb773-70c3-481d-a2ac-659654020a96" />

# voice-please

An open-source, AI-native framework for defining, encoding, and maintaining a company's voice and language system.

Takes existing content, reference voices, and team input as raw material. Produces operational voice artifacts: a voice profile, writing conventions, register map, audience language bank, and AI voice configuration. Built to be used with [Claude Code](https://claude.ai/code).

Part of the [please family](https://github.com/yesplease-studio) of open-source frameworks from [Yes Please Studio](https://yesplease.studio).

## How it works

Most voice and brand guidelines are PDFs that nobody reads. voice-please produces **operational artifacts** -- structured documents that humans can follow and AI tools can consume directly.

The system works through three phases:

1. **Discover.** Analyze existing content. Interview for reference voices and anti-references. Assess maturity across 8 dimensions. The key insight: most founders can't describe their ideal voice from scratch, but they can immediately point to companies and people whose communication style resonates.

2. **Author.** Synthesize discovery into structured voice artifacts. The voice profile, conventions, register map, and audience language bank are the source of truth for how the company communicates.

3. **Encode.** Translate the voice system into AI-ready configurations. System prompts, CLAUDE.md files, quality gates. This is what makes the voice system operational rather than aspirational.

Then maintain: **audit** content against the system, **refresh** when the company evolves, **re-encode** after changes.

## Who this is for

- **Founders and teams** who know their content sounds generic but can't articulate what it should sound like instead
- **Content leads** who need a system that scales voice consistency beyond one person's intuition
- **Consultants and facilitators** who help companies define their voice and want a structured framework
- **Anyone using AI for content** who wants AI output that sounds like their company, not like default ChatGPT

## Quickstart

1. Open this repo in [Claude Code](https://claude.ai/code)
2. Claude will detect `CLAUDE.md.template` and load the system
3. If this is your first time, say **"help me set up"** and Claude will walk you through creating a company profile
4. Once your profile exists, try: **"help us figure out our voice"** or **"our content sounds generic"**

Or skip the profile and go straight to a skill: **"run voice-discover on our website"** with a URL.

## The eight dimensions

voice-please measures voice maturity across eight dimensions. Each answers a core question.

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

Each dimension is scored 1-5 (Not started → Leading). Most companies start at 1-2 across most dimensions. That's normal. The framework helps you move intentionally.

## Skills

| Skill | What it does | When to use |
|-------|-------------|-------------|
| `voice-recommend` | Maps a challenge to dimensions and recommends the right skill | "Where do we start?" |
| `voice-discover` | Content audit + structured interview | Starting fresh, or need to understand current voice |
| `voice-author` | Creates and edits voice system artifacts | Defining the voice system, making changes |
| `voice-encode` | Translates voice artifacts into AI configurations | Making voice work with AI tools |
| `voice-audit` | Evaluates content against the voice system | Checking consistency, identifying drift |
| `voice-refresh` | Proposes amendments based on new context | Company has evolved, audit found issues |

## Voice system artifacts

Skills produce structured artifacts that live in `voice/`:

| Artifact | What it contains | Dimension |
|----------|-----------------|-----------|
| `voice-profile.md` | Personality, attributes, reference voices, phrasings, banned phrases | Dim 1 |
| `conventions.md` | Writing rules, hard rules, format templates, quality test | Dim 2 |
| `register-map.md` | Named registers with tone shifts and examples | Dim 3 |
| `audience-language-bank.md` | Verbatim audience language, company vs. audience gaps | Dim 4 |
| `ai-voice-config.md` | System prompt sections, quality gates, inheritance rules | Dim 6 |

Not every engagement produces all five. A minimal engagement produces voice-profile.md and conventions.md.

## Directory structure

```
voice-please/
├── CLAUDE.md.template     # How Claude operates in this system
├── SETUP.md               # Onboarding flow
├── README.md              # This file
├── config/
│   └── _template.md       # Company profile template
├── systems/
│   └── voice/
│       └── SYSTEM.md      # Core methodology (dimensions, maturity, sequencing)
├── skills/                # Executable skills
│   ├── voice-recommend/
│   ├── voice-discover/
│   ├── voice-author/
│   ├── voice-encode/
│   ├── voice-audit/
│   └── voice-refresh/
├── templates/             # Output artifact templates
│   ├── voice-profile.md
│   ├── conventions.md
│   ├── register-map.md
│   ├── audience-language-bank.md
│   └── ai-voice-config.md
├── workflows/             # Composed skill sequences
│   ├── new-engagement.yaml
│   ├── voice-foundations.yaml
│   └── voice-maintenance.yaml
├── tracking/              # Effectiveness tracking
└── examples/              # Walkthroughs
```

## The please family

voice-please is one of four open-source frameworks:

| Framework | What it does | Core question |
|-----------|-------------|---------------|
| [strategy-please](https://github.com/yesplease-studio/strategy-please) | Strategic workshop recommendation engine | "Where should we focus?" |
| [prd-please](https://github.com/yesplease-studio/prd-please) | Product requirements authoring and validation | "How do we build it reliably?" |
| [sales-please](https://github.com/yesplease-studio/sales-please) | Deal qualification and pipeline management | "Is this deal worth pursuing?" |
| **voice-please** | Voice system definition and encoding | "What should we sound like?" |

Each framework is standalone. They share design patterns (AI-native, human-gated, structured artifacts) but operate independently.

## Self-serve vs. facilitated

Every skill in voice-please produces useful output when run independently. You don't need a consultant to use this.

That said, some dimensions benefit significantly from having an experienced facilitator in the room -- especially Voice Identity (Dim 1) and Register System (Dim 3). The difference between "professional but approachable" and a genuinely distinctive voice profile is usually a person with taste and pattern recognition pushing past the first answer.

The framework is honest about this: `systems/voice/SYSTEM.md` documents where facilitation adds value for each dimension.

## License

MIT
