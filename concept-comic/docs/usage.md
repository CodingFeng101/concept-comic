# Usage

## Generate by default

```text
Use $concept-comic to explain “entropy” as a comic.
```

Expected output:

```text
Generated comic image or image series.
Saved image path or paths.
```

## Internal planning

```text
Use $concept-comic to generate a 16:9 comic image explaining “opportunity cost”.
```

Expected behavior:

```text
The assistant internally creates the concept card, metaphor, output scale, storyboard, prompt, QA notes, chooses the runtime route, then generates the image or image series.
Codex uses the native image tool. Other editors without native image generation use OPENAI_API_KEY, optional OPENAI_BASE_URL, and optional OPENAI_IMAGE_MODEL (default: gpt-image-2).
Do not output the concept card, storyboard, or prompt as the final deliverable unless the user is explicitly editing the skill documentation itself.
```

## Compare two concepts

```text
Use $concept-comic to create a left-right comic comparing RAG and Knowledge Graph QA.
```

Recommended layout:

```text
Left-right comparison
```

## Explain a process

```text
Use $concept-comic to make a four-panel comic explaining natural selection.
```

Recommended layout:

```text
Four-panel process only if it stays readable; otherwise split into an image series.
```

## Explain a misconception

```text
Use $concept-comic to explain why “natural selection means animals choose to evolve” is wrong.
```

Recommended layout:

```text
Misconception correction
```
