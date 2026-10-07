---
name: ir-intro-email
description: Write a Turiya Capital intro email to a listed company's Investor Relations team asking for an IR call. Use when the user gives a company name (optionally with their thesis) and asks for an intro, reach-out or IR-call email, or invokes /ir-intro-email.
argument-hint: <company name> [optional: your thesis or angle]
---

# IR intro email (Turiya Capital)

The user is an investor at Turiya Capital. Given a company name, produce a
warm, short intro email to that company's IR team requesting a 45-minute
call, in the fixed house format below.

## Input

- `$ARGUMENTS`: the company name, optionally followed by the user's thesis.
- If the user supplied a thesis, build paragraph 3 around it. Otherwise
  derive the thesis from research (step 1).

## Step 1: Research and verify (do this before writing)

The user wants credible, verified information only.

1. Run `WebSearch` (mode `standard`; send the searches in one turn) for:
   - the company's latest quarterly / annual results and outlook
     (prefer the company's own IR releases and results presentations),
   - its key technology or product shift right now,
   - the AI / scale-up / structural demand angle relevant to it.
2. From the results, identify:
   - **Key shift**: the technology or business moving from one stage to
     the next (e.g. hybrid bonding: "promising" -> "in production").
   - **Core story**: the narrative the market already knows (e.g. HBM).
   - **Underappreciated angle**: the bigger or longer-term market the
     user thinks is underestimated (default lens: AI scale-up, and why
     the company's equipment/product adds more value over time).
   - **Mechanism**: one or two plain sentences on *why* the company's
     role becomes more valuable as that market grows.
3. Only state things the sources support. If the company does not look
   like it is at an inflection point, still write the email but flag it
   to the user in the notes.

## Step 2: Write the email in the house format

Follow this template exactly. Keep the fixed sentences word for word;
fill only the `{...}` slots. Use the company's common short name
(e.g. "Besi", "AIXTRON"). Plain, warm, conversational English; short
sentences; no jargon without a plain-word explanation.

```
Subject: Turiya Capital: long-term interest in {Company} and request for an IR call

Dear {Company} Investor Relations team,

I hope this finds you well. My name is [Name], and I'm a [role] at Turiya Capital, a $3bn hedge fund based in Hong Kong.

We look for companies at a fundamental turning point. Unusually for a hedge fund, we tend to hold for 2–3 years, because we want to go through the growth journey together with the companies we back. We believe {Company} is at exactly that kind of point today.

{Key shift} seems to be moving from "{earlier stage}" to "{next stage}." Besides the {core story} story, we think the market for {underappreciated angle} is still underestimated. {Mechanism: 1–2 sentences on why the company's role becomes more valuable as that market grows.} I think {Company} is in an unusually strong position as that happens. I'd love to test that view with you.

Would you have 45 minutes in the coming weeks? I'm happy to work around your schedule.

Thank you for your time. We look forward to the conversation, and hopefully to a long relationship.
```

### Format rules

- Paragraph 3 is the only company-specific paragraph. Keep it to 4–6
  sentences.
- No numbered list of questions, no statistics or figures in the email,
  no signature block. Leave `[Name]` and `[role]` as placeholders.
- Always 45 minutes; no extra scheduling details.

### Reference example (Besi)

> Hybrid bonding seems to be moving from "promising" to "in production." Besides the HBM story, we think the market for AI scale-up is still underestimated. As compute moves toward denser chiplet designs and taller HBM stacks, how chips are connected becomes the limit on performance. That means the bonding step adds more value with each new device generation. I think Besi is in an unusually strong position as that happens. I'd love to test that view with you.

## Step 3: Output

1. The complete email (subject + body) in one block, ready to paste.
2. Below it, a short **Thesis check** table showing each claim in
   paragraph 3 and the source that supports it:

   | Claim in the email | What the source says | Source |
   |---|---|---|

3. A **Sources** list of the URLs used, as markdown links.
4. Any flags (e.g. weak evidence of an inflection point, recent negative
   news, a pending result date the user may want to time the email around).
