# Krea 2 Troubleshooting

Common failure modes and the prompt-level fix. Most problems trace back to leaving
something unstated — Krea 2 fills gaps, and not always the way you intended.

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Every draft comes back in a different style | No medium named, or a mood word used instead of a medium | Put a specific medium at the front ("35mm film photograph", not "cinematic") |
| Image looks like generic stock photography | "photo" / "photorealistic" alone lands in the bland middle | Name the camera format and its artifacts: "35mm film, fine grain", "disposable camera flash", "medium format, shallow depth of field" |
| Background is busy or wrong | Background left unspecified | State what the background *is* ("solid cream background", "empty platform"), not what it is not |
| Colors aren't what you asked for | Palette given as adjectives | Name 2–3 colors ("warm ochre and teal"); "vibrant colors" does not hold |
| The thing you excluded shows up anyway | Negation ("no people", "without a hat") | Describe the positive state instead ("empty street at dawn") |
| Text in the image is gibberish | Known Krea 2 limitation; smaller variants are worst | Keep text short and quoted, prefer a larger/hosted variant, or route typography to a dedicated model |
| Prompt feels detailed but output is flat/mushy | Prompt over ~300 words; signal diluted | Trim to the clauses that earn their place; density beats volume |
| Style and subject fight each other | Two style descriptions stacked, or style longer than subject | One style per prompt; make the subject the longest part |
| Turbo draft and final render don't match | Different models share a seed | Expect a reframe; settle the prompt on the fast model, accept the final model's version |

## Sources

- Ambience AI — "Write Better Prompts for Krea 2 Images" (troubleshooting).
- fal.ai — "Krea 2 Prompting Guide + Examples".
- cicalooo — "Krea 2 Prompting Guide" (GitHub Gist).
