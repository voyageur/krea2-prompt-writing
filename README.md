# krea2-prompt-writing

An agent skill that writes and expands text-to-image prompts for the **Krea 2** model (RAW/Turbo).

Krea 2 is a natural-language model — it wants coherent visual description, not tag piles. This skill teaches an agent to produce exactly that: one clean paragraph of prompt text, calibrated to Krea 2's documented style.

## What it does

- **Expands short ideas** — turns "a mouse on a branch" into a full, well-structured Krea 2 prompt using a 9-rule expansion system (faithfulness first, no invented details, medium preserved).
- **Polishes existing prompts** — if you already have a detailed prompt, it lightly finalizes rather than rewriting.
- **Converts tag lists** — rewrites Danbooru/SDXL-style comma-separated tags into one cohesive natural-language paragraph without dropping or inventing content.

## How it works

The skill is written for agents (OpenCode and compatible harnesses):

```
SKILL.md                      # entry point: workflow, key rules, output format
references/
├── prompting.md              # Krea 2 format rules + official calibration examples
└── expansion-system.txt      # the 9-rule system used to expand short ideas
```

The agent reads `SKILL.md`, then pulls in the references it needs for the specific task. Final output is always a single English paragraph — no bullets, no JSON, no negative prompts or settings unless explicitly requested.

## Install

Clone into your skills directory:

```sh
git clone https://github.com/voyageur/krea2-prompt-writing.git ~/.agents/skills/krea2-prompt-writing
```

(Adjust the path to match wherever your harness looks for skills.)

## Example

**Input:**

> a harvest mouse on a branch in autumn

**Output (what the agent produces):**

> A tiny, russet-brown harvest mouse clings to a slender diagonal branch amid vibrant green lobed leaves and small round buds. The mouse has soft textured fur, glossy black eyes, a pink nose, fine whiskers, and delicate pink paws firmly gripping the wood. In this macro photograph, an extremely shallow depth of field sharply focuses on the animal's face. The deep green background dissolves into a smooth, creamy bokeh, illuminated by soft, diffused natural lighting that highlights the intricate details of the fur and foliage.

## Attribution

Prompting guidelines in `references/prompting.md` are condensed from the official [`krea-ai/krea-2`](https://github.com/krea-ai/krea-2) documentation, including its calibration examples.

## License

[MIT](LICENSE)
