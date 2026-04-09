# Setup Guide

This guide walks you through creating a company profile so voice-please can give you tailored voice work. Claude follows this flow during your first conversation.

The whole process takes 5-10 minutes.

---

## How onboarding works

### Step 1: Check for existing context

Ask the user:

> "Do you have any existing voice or brand documents you can share? A website, brand guidelines, pitch deck, or content examples?"

If they provide something:
- Read and extract what you can: what the company does, how it sounds, who it's for, existing voice work
- Note what's covered and what's still missing
- Move to Step 2 to fill gaps

If they provide a URL, use `WebFetch` to retrieve and analyze the content for voice patterns.

If they don't have anything, move straight to Step 2.

### Step 2: Fill gaps conversationally

Based on what's missing from Step 1, ask about:

**What the company does and who it's for**
- What does the company do, in plain language?
- Who are the customers or audience? (Be specific: role, context, the problem they have)
- What stage is the company at?

**Current voice situation**
- Does anyone on the team currently "carry" the voice? (Often one person writes most of the content and everyone else tries to match them.)
- Have you defined your voice before? (Brand guidelines, tone of voice doc, even informal notes?)
- What content channels do you actively use? (LinkedIn, blog, email, product UI, social media, etc.)

**Language and market**
- What's the primary language for content? Any additional languages?
- If multilingual: do you have the same voice across languages, or does it shift?

**Team writing dynamics**
- How many people write content for the company?
- Is there a review process for content, or does it go out unreviewed?
- What's the biggest pain point around content quality or consistency right now?

Don't ask all of these as a list. Have a conversation. Skip questions where the answer is already clear from Step 1. Follow up on interesting answers.

### Step 3: Write the profile

Once you have enough context, generate `config/profile.md` using the template from `config/_template.md`.

Before saving:
1. Show the user the complete profile
2. Ask if anything needs adjusting
3. Save only after confirmation

A useful profile beats a complete profile. Mark missing fields as "Unknown" or "Not discussed" rather than guessing.

### Step 4: Suggest next steps

After the profile is saved, suggest the natural next step based on what you've learned:

- **If they have no voice work at all:** "Want to start with voice discovery? I'll analyze your existing content and walk through some questions to surface your voice."
- **If they have some existing voice work:** "Want me to audit your current voice system against the 8 dimensions? That'll show you where you're strong and where to focus."
- **If they know what they want:** Route to the appropriate skill directly.

---

## Notes for Claude

- The goal is a useful profile, not a complete one. Missing fields are fine.
- If the user provides a website, analyze it for voice patterns (sentence length, formality, energy, specificity, humor) but don't treat the website as ground truth. Many websites were written once and don't reflect current voice intentions.
- Keep the conversation natural. This is a getting-to-know-you session, not a form.
- If the user clearly knows what they want and doesn't need a profile, skip onboarding and go straight to the skill.
