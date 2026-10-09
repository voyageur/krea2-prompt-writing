---
name: krea2-prompt-writing
version: 0.1.0
description: Write and expand text-to-image prompts for the Krea 2 model (RAW/Turbo). Use when creating a new Krea 2 image prompt from a short idea, polishing an existing Krea 2 prompt, or converting a tag-style/keyword prompt into Krea 2's natural-language format.
---

# Krea 2 Prompt Writing

Krea 2 is a natural-language text-to-image model. It is not a tag/keyword model: prompts read as coherent visual description, not comma-separated tag piles.

## Workflow

1. Read `references/prompting.md` for the model's format rules and calibration examples.
2. If the user gives a short idea that needs expanding into a full prompt, read `references/expansion-system.txt` and follow its 9 rules exactly.
3. If the user already supplies a detailed prompt, lightly polish it rather than rewriting it (rule 7 in `expansion-system.txt`) — preserve their phrasing, subjects, and intent.
4. If the input is a tag/keyword-style prompt (e.g. Danbooru tags, SDXL-style comma lists), rewrite it into one cohesive natural-language paragraph, preserving every subject, attribute, and action; do not drop or invent content.
5. Output exactly **one paragraph** of prompt text. No bullet points, no JSON, no markdown, no step labels in the final output.

## Key Rules

- **Prose, not tags.** Group each subject with its own attributes and actions in natural sentences.
- **Text rendering.** Wrap any word(s) that must render as visible on-image text in double quotes.
- **Faithfulness first.** Preserve the user's stated subjects, colors, actions, and spatial relationships. Do not add new objects, characters, or props unless clearly implied.
- **Preserve stated medium.** If the user says "photo of", "painting of", "3D render of", etc., honor it rather than substituting an easier medium.
- **Avoid over-specification.** Do not invent highly specific clothing, materials, or details the user's input doesn't support.
- **Respect the human form.** Assume clothing covers genitals and intimate anatomy in any depiction of people.
- **Resolution.** Krea 2 Turbo can generate up to 2k resolution; long, detailed prompts generally yield the best results, but the model also performs well with minimal prompt engineering.

## Output Rules

- Write the final prompt in English as a single continuous paragraph.
- Do not emit internal reasoning, planning tags, or wrapper text in the visible answer — think through subject/mood/style/composition silently, then output only the finished prompt paragraph.
- Do not append negative prompts, settings, or metadata unless the user explicitly asks for them.
