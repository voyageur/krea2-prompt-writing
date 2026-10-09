# Krea 2 Model Variants

Krea 2 is a family, not a single model. Which variant the user targets changes the
best prompt length, the available controls, and the settings. When the user names
a surface (ComfyUI, fal, the hosted Krea app) or asks about settings, consult this.

## Open-weight variants (local / ComfyUI)

**Krea 2 RAW** — the undistilled base model.

- ~52 steps, CFG ~3.5, up to ~1024px.
- More malleable; best for experimentation and for training LoRAs.
- LoRAs trained on RAW transfer to Turbo.

**Krea 2 Turbo** — the distilled, fast model.

- ~8 steps, CFG 0/1 (guidance effectively disabled), timestep-shift (mu) ~1.15,
  native 1024–2048px. Official sample prompts are generated at 2K.
- Because CFG is disabled there is **no working negative prompt** — steer with
  positive description, not negations.

## Hosted + API variants (Krea app, fal.ai)

**Krea 2 Medium** — smaller, faster, more post-trained and stable. Strongest for
illustration, anime, painting, and expressive artistic styles. A good default.

**Krea 2 Large** — more than twice Medium's size, softer post-training, rawer and
more textured. Best for photorealism and "raw" looks (motion blur, film grain, low
dynamic range).

When to use which:

- **Medium** → illustration, animation, painting, concept art.
- **Large** → photorealism, editorial photography, gritty/textured aesthetics.

## The draft → commit workflow

Krea 2 explores rather than converges, so the fastest route to a strong image:

1. **Start vague on the fast model** (Turbo/Medium) — a subject and a medium only.
   Generate a few and see which direction has life.
2. **Tighten one attribute at a time** — add palette, then lighting, then framing.
   Change one thing per draft so you know what moved the result.
3. **Fix the seed** once a draft is close, for controlled comparison.
4. **Commit on the higher-fidelity model.** Expect the framing to shift slightly —
   the variants are different models, so a shared seed keeps them in the same lane
   rather than producing identical frames.

## Hosted controls worth knowing

The hosted product and API expose controls that don't exist in a local prompt:

- **Style references** — up to several images with per-image strength (0–100%);
  Krea 2 extracts and blends their style.
- **Creativity parameter** — higher values let the model add aesthetic depth
  beyond what you describe; lower values execute the prompt more literally.
- **Generative sliders** — Intensity, Complexity, Movement.
- **Moodboards** and **Krea Styles** (LoRAs).

When these are available, they often beat trying to force the same effect through
prompt wording alone.

## Don't confuse it with FLUX.1 Krea [dev]

Krea 2 is Krea's own foundation model, trained from scratch. It is a different
model from **FLUX.1 Krea [dev]** (a Black Forest Labs / Krea collaboration). Prompt
guidance here is for Krea 2, not FLUX.

## Sources

- Official: `krea-ai/krea-2` README and `docs/prompting.md`; Krea user docs;
  ComfyUI Krea 2 tutorial.
- fal.ai — "Krea 2 Prompting Guide + Examples" (Medium vs Large).
- Ambience AI — "Write Better Prompts for Krea 2 Images" (draft → commit).
