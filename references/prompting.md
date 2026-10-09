# Krea 2 Prompting Guidelines

Condensed from `krea-ai/krea-2/docs/prompting.md`.

- Use natural language prompts, not tag/keyword lists.
- The Turbo model can generate up to 2k resolution images.
- Long, detailed prompts yield the best results, but the model is capable of generating high-quality images with minimal prompt engineering too.
- For text rendering, put the exact words to be rendered in double quotes.

## Calibration Examples

These illustrate the expected density and paragraph style (all real examples from the official docs, generated at 2k resolution with the Turbo model):

```text
immense rocket launch exhaust as seen from extremely close up
```

```text
3D rendered matte black designer toy figure, stylized round anthropomorphic shape, backward black baseball cap, oversized gold-rimmed aviator sunglasses, white traditional line-art tattoos of tiger and bird on torso, black studded belt with gold buckle, smooth vinyl texture, studio lighting, solid vibrant blue background, high contrast minimal composition
```

```text
close-up anime portrait of a young woman, large amber-brown eyes with intricate sparkling reflections, index finger delicately touching a subtle smile, messy dark blue hair with loose strands crossing her face, white and navy school uniform, bright high-key lighting, luminous shadows with cool blue undertones, detailed digital painting, dynamic tilted framing, shallow depth of field on hand
```

```text
A close-up portrait of a young East Asian woman with straight black hair, loose strands sweeping across her fair skin, and an intense gaze. She wears a light grey collared shirt with a black tie. A vibrant bouquet of pink and orange lilies with lush green leaves sits in the blurred right foreground. The background is a solid, striking crimson red. Soft, directional studio lighting highlights her facial features, creating a high-contrast composition with a shallow depth of field.
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
