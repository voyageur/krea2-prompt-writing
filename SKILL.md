---
name: krea2-prompt-writing
version: 0.3.0
description: Write and expand text-to-image prompts for the Krea 2 model (RAW/Turbo/Medium/Large). Use when creating a new Krea 2 image prompt from a short idea, polishing an existing Krea 2 prompt, converting a tag-style/keyword prompt into Krea 2's natural-language format, or reverse-engineering a recreate prompt from an existing image.
---

# Krea 2 Prompt Writing

Krea 2 is a natural-language text-to-image model. It is not a tag/keyword model: prompts read as coherent visual description, not comma-separated tag piles.

## Workflow

1. Read `references/prompting.md` for the model's official format rules and calibration examples.
2. Read `references/best-practices.md` for the community conventions that make prompts land — especially naming the medium first and the five-attribute stack. Apply these whenever composing or expanding.
3. If the user gives a short idea that needs expanding into a full prompt, read `references/expansion-system.txt` and follow its 9 rules exactly.
4. If the user already supplies a detailed prompt, lightly polish it rather than rewriting it (rule 7 in `expansion-system.txt`) — preserve their phrasing, subjects, and intent.
5. If the input is a tag/keyword-style prompt (e.g. Danbooru tags, SDXL-style comma lists), rewrite it into one cohesive natural-language paragraph, preserving every subject, attribute, and action; do not drop or invent content.
6. If the user supplies an image to recreate (reverse prompting), read `references/reverse-prompting.md` and follow its observe-before-infer procedure. This needs a vision-capable model.
7. When the user wants a specific look, consult `references/styles.md` for trigger phrasing and example lines. When they name a surface (ComfyUI, fal, the hosted app) or ask about settings or variants, consult `references/model-variants.md`. When a generation came back wrong and they want it fixed, consult `references/troubleshooting.md`.
8. Output exactly **one paragraph** of prompt text. No bullet points, no JSON, no markdown, no step labels in the final output.

## Key Rules

- **Prose, not tags.** Group each subject with its own attributes and actions in natural sentences.
- **Name the medium first.** Lead with a specific medium ("35mm film photograph", "gouache painting", "anime illustration, cel shading") rather than a mood word ("cinematic", "beautiful"). Krea 2 commits hard to whichever medium it infers. See `best-practices.md`.
- **Describe, don't negate.** Krea 2 draws every noun it sees, so negations summon the thing — write "empty street at dawn", not "street with no people".
- **Name 2–3 palette colors.** Use named colors ("warm ochre and teal"), not adjectives ("vibrant"); state the background explicitly or Krea 2 invents it.
- **Text rendering.** Wrap any word(s) that must render as visible on-image text in double quotes — but note Krea 2 often garbles text in practice (see `best-practices.md`).
- **Faithfulness first.** Preserve the user's stated subjects, colors, actions, and spatial relationships. Do not add new objects, characters, or props unless clearly implied.
- **Observe, don't invent (reverse).** When recreating an image, describe only what is visibly present; mark uncertain readings rather than guessing optics, brands, or identities. See `reverse-prompting.md`.
- **Preserve stated medium.** If the user says "photo of", "painting of", "3D render of", etc., honor it rather than substituting an easier medium.
- **Avoid over-specification.** Do not invent highly specific clothing, materials, or details the user's input doesn't support.
- **Respect the human form.** Assume clothing covers genitals and intimate anatomy in any depiction of people.
- **Resolution & length.** Krea 2 Turbo can generate up to 2k resolution; long, detailed prompts generally yield the best results, but keep them under ~300 words and the model also performs well with minimal prompt engineering.

## Output Rules

- Write the final prompt in English as a single continuous paragraph.
- Do not emit internal reasoning, planning tags, or wrapper text in the visible answer — think through subject/mood/style/composition silently, then output only the finished prompt paragraph.
- Do not append negative prompts, settings, or metadata unless the user explicitly asks for them.
- Exception for reverse prompting: after the paragraph you may add a brief **Uncertain readings:** line when a low-confidence inference materially affects fidelity. Keep it to the few readings that matter, and omit it when the image is unambiguous.
