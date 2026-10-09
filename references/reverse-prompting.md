# Reverse Prompting (Image → Prompt)

How to turn an existing image into a faithful Krea 2 recreate prompt. This needs a
**vision-capable model** — inspect the image directly, don't just paraphrase the
user's words. The goal is to reproduce the *visible result*, not to narrate its
mood.

## 1. Observe before you infer

Keep three layers separate and never collapse them:

1. **Observation** — what is visibly present.
2. **Inference** — what is likely but not certain (an image can look cinematic
   without proving a specific camera, lens, or film stock).
3. **Generation instruction** — how to express high-confidence evidence as prompt
   language.

Only high-confidence observations become firm prompt clauses. Likely-but-unproven
readings are either softened ("appears to be…") or dropped. Never invent.

## 2. Observation checklist

Walk the image top to bottom against these:

- **Medium / image type** — photograph, illustration, animation, 3D, collage,
  print, painting; polished or raw; realistic or stylized; visible grain, brush,
  halftone, paper, scan, CGI, or linework.
- **Subjects** — exact count; primary/secondary hierarchy; apparent adult status
  when relevant; hair, face, silhouette, clothing; pose and gesture geometry; gaze
  and expression; hand-object contact.
- **Composition** — aspect ratio and orientation; shot size (close-up, medium,
  full-body, wide); camera height and angle; perspective distortion; position in
  frame; symmetry, diagonals, negative space; crop points and occlusions.
- **Scene layers** — foreground, middle ground, background, atmosphere, and scale
  relationships between them.
- **Light & color** — source direction; hardness; contrast; rim/fill/backlight;
  dominant and accent colors (name them); saturation and temperature.
- **Material & style** — reflective, matte, translucent, fibrous, wet, rough,
  polished; how surfaces respond to light; production clues.
- **Text** — transcribe exactly when legible, with line breaks, placement, font
  class, color, and effect.

## 3. Reconstruction ordering

Write the prompt in visible-priority order — this beats starting from abstract
mood words, and lines up with the layering order in `prompting.md`:

1. Medium / image type
2. Primary subject and central action
3. Composition and camera
4. Subject appearance and interaction
5. Environment and scale
6. Lighting and palette
7. Material and style
8. Text (in double quotes)

Then apply the usual `best-practices.md` rules: name the medium first, name 2–3
palette colors, state the background explicitly, describe rather than negate.

## 4. Faithfulness rules for reverse

- **Exact subject count.** Two people is two people — don't round to "a group."
- **Bind every attribute to its subject.** Use separate clauses and explicit
  ownership ("her silver gown", "the red heart behind her") so attributes don't
  leak between subjects or props.
- **Transcribe visible text exactly**, wrapped in double quotes; don't paraphrase
  or correct it.
- **Don't invent optics or provenance.** No camera model, focal length, brand,
  film stock, or artist name unless it is genuinely legible or stated.
- **Omit what you can't see.** Drop invisible micro-details and repeated mood
  adjectives rather than guessing.

## 5. Multi-image reference fusion

When several reference images are given, assign each one an explicit role before
writing, and state what must **not** transfer from it:

| Image | Transfer | Do not transfer |
| --- | --- | --- |
| 1 | pose, framing, gaze | clothing, face, background |
| 2 | palette, material | composition, subject identity |
| 3 | background architecture | weather, people |

Roles to choose from: subject identity, pose, composition, clothing, object
design, palette, texture, lighting, style, atmosphere.

Resolve conflicts by the user's stated priority. With none given, default to:
subject/pose → composition → hard text constraints → palette/material →
style/atmosphere. Don't silently average incompatible directions — flag the
conflict. Write the final prompt as one unified scene, not "Image 1 shows…",
unless the target system supports image-reference tokens.

## 6. Close recreation needs more than a prompt

A prompt controls semantic content; it **cannot guarantee a pixel-level match**.
Close reconstruction also needs image conditioning. The following are practical
heuristics, **not official Krea settings** — treat numbers as conservative
starting points and verify against the user's actual workflow:

- **Low denoise / low transformation** — preserve layout and identity-like features.
- **Moderate denoise** — keep broad composition while allowing material/style change.
- **High denoise** — use the source mainly as inspiration.

Possible controls: image-to-image latent init, pose/skeleton control, depth
control, edge/line control, face restoration, and style-reference (IPAdapter-like)
conditioning. Only name a specific node or model as compatible after checking the
user's setup. When close matching is required, say outright that source-image
conditioning is needed — don't promise it from the prompt alone.

## 7. Common errors and fixes

| Error | Fix |
| --- | --- |
| Hallucinated detail | Mark uncertainty; omit unsupported facts |
| Attribute leakage between subjects | Separate clauses with explicit ownership |
| Over-description | Remove invisible micro-details and repeated mood adjectives |
| Style-only reverse prompt | Describe pose, framing, space, and lighting before style adjectives |
| Wrong priority | Put the most important subject/action/composition in the first two sentences |
| Promising pixel match from prompt alone | State that source-image conditioning is required for close recreation |

## Output

Default: one coherent English paragraph, same discipline as every other mode. When
a low-confidence inference materially affects fidelity, you may add a brief
**Uncertain readings:** line after the prompt — keep it to the few readings that
actually matter. Omit it entirely when the image is unambiguous.

## Sources

- Official: `krea-ai/krea-2` docs (natural language, Qwen3-VL encoder, quoted text,
  no reliable in-prompt negative on Turbo).
- General community reverse-prompting practice (observe-before-infer, visible-
  priority ordering).
- Structural inspiration: `AI-KSK/krea2-prompt-suite` (observation checklist,
  evidence layers, role mapping, recreation caveats).
