# Evaluating a Krea 2 Prompt

Score an existing Krea 2 prompt, flag what will hurt the result, and return the
highest-impact fixes. Use this when the user asks you to review, score, critique,
or "check" a prompt rather than write or expand one. The output is a short
diagnostic report, not a single paragraph.

## Procedure

1. Read the prompt as written. Do not rewrite it yet.
2. Score each rubric dimension below against Krea 2 best practice
   (see `best-practices.md` and `prompting.md`).
3. Flag contradictions, negation traps, and missing control explicitly.
4. Return the top fixes, highest impact first.
5. Offer to produce a revised prompt — don't rewrite unless asked.

## Rubric

Score each dimension **1–5**: 5 = follows best practice, 3 = present but weak or
partial, 1 = missing or counterproductive.

| Dimension | What a 5 looks like |
| --- | --- |
| **Medium** | A specific medium leads the prompt ("35mm film photograph", "gouache painting"), not a mood word ("cinematic", "beautiful"). |
| **Subjects** | Every subject is countable and each attribute is bound to its subject — no detached or cross-applied traits. |
| **Composition** | Shot size, angle, subject placement, and negative space are stated where they matter. |
| **Lighting** | Light direction and quality are specified ("hard directional window light"). |
| **Palette & background** | 2–3 named colors (not adjectives) and an explicitly stated background. |
| **Texture & style** | Surface/material language is present ("fine grain", "thick visible brushstrokes"). |
| **Consistency** | No conflicting medium, lighting, count, or aspect ratio; no backfiring negations. |
| **Efficiency** | Under ~300 words, no quality-tag filler ("masterpiece, 8k, best quality"); fits the target variant if one is named. |

## What to flag explicitly

- **Contradictions** — e.g. "wide establishing shot" + "extreme close-up", or two
  competing mediums/styles fighting for the same image.
- **Negation traps** — any "no X" / "without X" phrasing; Krea 2 draws the noun, so
  rewrite as a positive state. On Turbo (CFG 0) there is no reliable negative, so
  exclusions must be positive.
- **Attribute leakage** — traits that could attach to the wrong subject.
- **Missing control** — the biggest unstated gap (usually background or medium).
- **Filler** — generic quality tags and repeated mood adjectives that add no signal.
- **Text risk** — on-image words not in quotes, or critical typography that Krea 2
  will likely garble (note the limitation; see `best-practices.md`).

## Output format

```
Readiness: <Strong | Workable | Needs work>

| Dimension | Score | Note |
|---|---|---|
| Medium | n/5 | ... |
| ... | ... | ... |

Top fixes (highest impact first):
1. ...
2. ...
3. ...
```

Keep the fix list to roughly three — five at most. Add a one-line **Flags:** entry
only when there are real contradictions or negation traps. End by offering to apply
the fixes and return a revised prompt.

## Sources

- `best-practices.md` and `prompting.md` in this skill (the rubric is derived from
  them and the official Krea docs).
- Structural inspiration: `AI-KSK/krea2-prompt-suite` evaluation rubric.
