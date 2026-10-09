# Krea 2 Prompting Guidelines

Condensed from `krea-ai/krea-2/docs/prompting.md`.

- Use natural language prompts, not tag/keyword lists.
- The Turbo model can generate up to 2k resolution images.
- Long, detailed prompts yield the best results, but the model is capable of generating high-quality images with minimal prompt engineering too.
- For text rendering, put the exact words to be rendered in double quotes.
- For LLM-assisted expansion of a short idea into a longer prompt, Krea publishes an official system prompt — see `expansion-system.txt` (mirrored from the docs' `expansion.txt`).

## Calibration Examples

These illustrate the expected density and paragraph style (all real examples from the official docs, generated at 2k resolution with the Turbo model):

```text
immense rocket launch exhaust as seen from extremely close up
```

```text
3D rendered matte black designer toy figure, stylized round anthropomorphic shape, backward black baseball cap, oversized gold-rimmed aviator sunglasses, white traditional line-art tattoos of tiger and bird on torso, black studded belt with gold buckle, smooth vinyl texture, studio lighting, solid vibrant blue background, high contrast minimal composition
```

```text
vintage analog collage, central irregularly shaped snowy mountain range with a section featuring distinct wavy edges, structured within a 12x16 grid of square tiles, composition fragments the subject by alternating tiles with solid azure blue background squares, thin white grid lines, grainy paper texture, retro aesthetic of mid-century print, vibrant cyan and warm neutral tones, experimental layout, tactile quality, high-contrast graphic composition
```

```text
close-up anime portrait of a young woman, large amber-brown eyes with intricate sparkling reflections, index finger delicately touching a subtle smile, messy dark blue hair with loose strands crossing her face, white and navy school uniform, bright high-key lighting, luminous shadows with cool blue undertones, detailed digital painting, dynamic tilted framing, shallow depth of field on hand
```

```text
1990s vintage anime style cel animation, densely packed crowd of teenagers in summer uniforms, central boy with short black hair raising a clenched right fist, squinting one eye with a determined expression, wearing a white short-sleeve shirt and solid green necktie, surrounding students looking in various directions, girls in white sailor blouses with green striped collars and neckerchiefs, light blue skirts and trousers, tightly framed medium shot, flat shading, soft muted retro.
```

```text
A minimalist flat-color illustration of a person wading through expansive shallow ocean waves beneath a pale peach sky. The dark-skinned figure, wearing an orange swim cap, light blue top, and bright green shorts, steps carefully through knee-deep water. The ocean is rendered in muted mint green with delicate, thin black linework detailing the continuous ripples and gentle whitecaps. Soft pinkish-peach reflections echo the sky on the water's surface. A dark, jagged rock rests in the lower left foreground near a pale grey shoreline. The horizon features a solid purplish-blue landmass and a stylized, layered yellow and blue cloud. The high-angle wide perspective emphasizes the vast negative space of the water, utilizing a clean ligne claire drawing aesthetic with a subtle paper texture.
```

```text
A close-up portrait of a young East Asian woman with straight black hair, loose strands sweeping across her fair skin, and an intense gaze. She wears a light grey collared shirt with a black tie. A vibrant bouquet of pink and orange lilies with lush green leaves sits in the blurred right foreground. The background is a solid, striking crimson red. Soft, directional studio lighting highlights her facial features, creating a high-contrast composition with a shallow depth of field.
```

```text
high-fashion editorial portrait of a young East Asian woman, short choppy platinum blonde bob with heavy bangs, looking over her bare shoulder to the right, lips playfully pursed, wearing a structured black top with an architectural protruding bust detail and thin straps, delicate gold hoop earrings, arm bent with hand resting on hip, warm skin tones, solid striking crimson red background, soft directional studio lighting, cinematic color palette, medium close-up shot
```

```text
A tiny, russet-brown harvest mouse clings to a slender diagonal branch amid vibrant green lobed leaves and small round buds. The mouse has soft textured fur, glossy black eyes, a pink nose, fine whiskers, and delicate pink paws firmly gripping the wood. In this macro photograph, an extremely shallow depth of field sharply focuses on the animal's face. The deep green background dissolves into a smooth, creamy bokeh, illuminated by soft, diffused natural lighting that highlights the intricate details of the fur and foliage.
```

```text
stylized digital painting of a dark convertible on a winding coastal cliff road, high-angle perspective, blocky painterly brushstrokes, golden hour sunlight hitting rocky orange terrain and green vegetation, flock of white abstract birds flying in foreground, blinding bright sun reflection on vast ocean, vibrant warm color palette, sharp graphic shadows
```

## Takeaways for Writing New Prompts

- A prompt can be as short as a single evocative phrase (see the rocket example) or a dense multi-sentence paragraph (see the mouse/woman examples) — match density to how much control the user wants.
- Dense prompts typically layer, in roughly this order: subject + identity/appearance details → pose/action → immediate props or interacting objects → background/environment → lighting → color palette → medium/style → composition/framing/depth-of-field notes.
- Prefer full sentences over comma-spliced tag fragments when writing anything beyond a short exploratory prompt; the official examples mix both styles, but the longer ones read as prose, not tags.
- Always keep subject attributes attached to their subject (e.g. "her light grey collared shirt", not a detached "grey shirt" tag floating in a list) so the model doesn't cross-apply attributes to the wrong subject.
