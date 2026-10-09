# Krea 2 Best Practices (Community)

These are community-tested conventions, **not** the official docs. The official
ground truth lives in `prompting.md` and `expansion-system.txt`. Where this file
and the official docs agree, follow it with confidence; where it goes further,
treat it as well-supported guidance distilled from the sources listed at the end.

## 1. Name the medium first

Krea 2 commits hard to whichever medium it infers, and it infers one every time.
Leave the medium out and the model picks a different one on each generation; name
it and everything else in the prompt is interpreted through that lens. Lead with a
**specific** medium and be concrete about the process that made the image.

Specific mediums that work:

- "35mm film photograph", "macro photograph", "medium format portrait"
- "anime illustration, cel shading"
- "gouache painting on textured paper", "impasto oil painting"
- "risograph print", "linocut", "ligne claire illustration"
- "3D render", "claymation still"
- "extremely grainy lo-fi VHS still"

Vague labels that drift (they describe how you *feel*, not how the image was made):

- "beautiful", "high quality", "artistic"
- "realistic" or "photorealistic" on its own
- "digital art" with no technique
- "cinematic" with no film reference

## 2. The five-attribute stack

After the medium, state these five things outright. Krea 2 fills any gap you
leave, and not always the way you intended.

1. **Color palette** — name two or three colors ("muted green and amber",
   "fluorescent pink and navy"), not adjectives ("vibrant", "colorful").
2. **Lighting** — direction and quality ("hard directional window light",
   "soft backlight through fog").
3. **Texture** — what the surface is made of ("fine grain", "condensation
   droplets", "grainy ink texture").
4. **Framing** — distance and angle ("wide shot", "macro", "low angle",
   "shallow depth of field").
5. **Background** — say what it *is* ("solid cream background", "empty platform").
   An unmentioned background is where Krea 2 invents the most.

## 3. Describe what you want, don't negate

Krea 2 treats every noun as something to draw, so a negation can summon the exact
thing you were trying to avoid. There is no reliable in-prompt negative.

- Say "shallow depth of field", not "background not sharp".
- Say "solid flat background", not "no clutter behind".
- Say "empty street at dawn", not "street with no people".

## 4. Keep palettes to two or three named colors

Named colors hold ("warm ochre and teal"); adjectives do not ("vibrant colors").
Two or three is the sweet spot. Let the subject carry color when it already does
(marble, coffee, a dark background) and add named colors only when it doesn't.

## 5. Mind the length ceiling

Long, detailed prompts are good, but past roughly **300 words** extra words stop
adding signal and start diluting everything else. Prefer density over volume:
every clause should earn its place. Flowing sentences and comma-separated
attribute stacks both parse well — a comma stack is easier to edit one attribute
at a time during iteration.

## 6. Text rendering is limited

Official guidance is to wrap on-image words in double quotes, and this helps. But
in practice Krea 2 often garbles headlines, labels, and signage even when quoted,
especially on the smaller/faster variants. For posters, packaging, or UI mockups
where the text must be correct, prefer the larger/hosted variants, keep the text
short, or route the job to a dedicated typography model. Keep words out of the
prompt entirely when the composition can carry the message instead.

## 7. Why natural language works

Krea 2's text encoder is **Qwen3-VL**, a language model — not CLIP or T5. It
parses sentences and grounded spatial phrasing, which is why prose outperforms tag
soup and why attributes should stay attached to their subject ("her light grey
collared shirt", not a detached "grey shirt"). Comma-separated keyword lists still
work, but you leave capability on the table.

## Sources

- Official: `krea-ai/krea-2` — `docs/prompting.md`, `docs/expansion.txt`
- fal.ai — "Krea 2 Prompting Guide + Examples"
- Ambience AI — "Write Better Prompts for Krea 2 Images"
- cicalooo — "Krea 2 Prompting Guide" (GitHub Gist)
