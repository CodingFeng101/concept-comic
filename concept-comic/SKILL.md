---
name: concept-comic
description: Use when a user asks to turn an abstract or complex concept into comic-style visual explanation images, concept illustrations, educational comic images, or visual comparisons between concepts.
---

# Concept Comic Skill

## Mission

Turn complex concepts into generated comic-style explanatory images.

The skill should work for concepts from many fields: science, economics, computer science, philosophy, education, social science, and everyday reasoning.

The final target is always one or more comic-style explanation images, not a text explanation, not a prompt-only answer, not a website, not a dense infographic, and not an editable diagram.

## Core idea

Do not draw the concept directly.

First translate:

```text
abstract concept → concept structure → visual metaphor → action scene → comic storyboard → image prompt
```

The concept card, storyboard, and prompt are internal preparation. Do not stop at them as the final answer when this skill is invoked.

Choose the number of images from expression points, not from concept size. One comic image should express one clear point. If one point cannot stay simple, readable, and visually direct in one image, split it into multiple separate image files instead of squeezing it into a dense multi-panel image.

## When to use this skill

Use this skill when the user asks to:

- explain a concept with a comic
- turn a complex idea into an interesting visual
- create a concept illustration
- generate comic-style explanation images
- make an abstract concept easier to understand
- design a storyboard for a concept image, where the storyboard is internal preparation for the final image
- compare two concepts visually
- clarify a misconception with dialogue or wrong-vs-right framing
- create mobile-friendly short vertical concept comics

Example requests:

```text
用漫画解释熵增
把机会成本变成一张漫画图
RAG 和知识图谱问答的区别，做成漫画
用四格漫画讲自然选择
把通货膨胀做成概念漫画
```

## Scope

This skill focuses on concepts.

In scope:

- one concept
- two concepts for comparison
- a process
- a mechanism
- a causal chain
- a misconception
- a trade-off
- a system-level idea
- a dialogue clarification
- a mobile-first short explanation

Out of scope:

- large codebase analysis
- website building
- app development
- editable PPT / SVG / Excalidraw export
- pure decorative illustration
- dense corporate infographic
- strict academic diagram
- high-stakes personal advice

## Reference loading

Load only the reference files needed for the current request:

- Final response shape: use `references/response-format.md`.
- Concept analysis: use `references/concept-understanding.md` and `references/concept-types.md`.
- Metaphor selection: use `references/concept-to-metaphor.md` and `references/metaphor-bank.md`.
- Layout and storyboarding: use `references/composition-patterns.md` and `references/storyboard-template.md`.
- Image prompt writing: use `references/prompt-template.md` and `references/visual-style.md`.
- Image generation: use `references/image-generation-workflow.md`; outside Codex also use `references/external-image-api.md`.
- QA or risky domains: use `references/qa-checklist.md`, `references/anti-patterns.md`, and `references/domain-safety.md`.

## Required workflow

Always follow this sequence.

### Step 1: Build a Concept Card

Use `references/concept-understanding.md`.

Identify:

```text
source text or user request
concept name
domain
target audience
channel
risk level
preferred type, if user specified one
style shell, if user specified one
one-sentence explanation
key components
key relationships
common misconception
must-preserve knowledge
metaphor risk
```

### Step 2: Choose the comic taxonomy and primary type

Use `references/concept-types.md`.

Classify the request across five programmable dimensions:

```text
length/form
function
narrative structure
style shell
channel
```

Then choose one primary comic type from the user's question:

```text
Single-panel concept
Comparison explanation
Four-panel process
Dialogue clarification
Cause/process comic
System map
Journey/state transition
Short vertical comic
Misconception correction
```

If multiple types apply, choose the type that best serves the user's explanation goal and channel. Complex concepts may become a short image series where each image uses a different primary type.

### Step 3: Choose a faithful visual metaphor

Use `references/concept-to-metaphor.md` and `references/metaphor-bank.md`.

A good metaphor preserves the concept’s relationship, not just its appearance.

### Step 4: Choose a comic layout

Use `references/composition-patterns.md`.

Common layouts:

```text
single-panel concept
left-right comparison
four-panel process
dialogue clarification
cause/process chain
misconception correction
system map
journey/state transition
short vertical comic
```

### Step 5: Plan image count

Before storyboarding or generating images, always make an explicit image-count decision.

Answer these questions:

```text
How many distinct cognitive points does this concept need?
Can each point be expressed in one image without crowding, tiny text, or misleading simplification?
Does any single point need so much sequence, contrast, or setup that it would become crowded in one image?
Would splitting overloaded points into separate images make the comic clearer?
```

Then choose the smallest useful output:

```text
1 image: one expression point that stays simple in one scene or a light panel layout
N-image series: multiple expression points, or one expression point that would become crowded in one image
```

Do not default to one image just because the user did not specify a count. Do not use a multi-panel image as a way to cram too much into one output. Do not create a series when one clear image can express the point simply. If generating images, use this decision directly without asking for confirmation unless the topic is too broad or unsafe.

When the plan is `N-image series`, generate N separate images. Do not generate one montage, collage, grid, strip, long image, or composite image containing all N images.

### Step 6: Create storyboard

Use `references/storyboard-template.md`.

The storyboard must include:

```text
title
comic taxonomy
primary comic type
channel
risk level
style shell
composition pattern
image count / series plan when needed
reason for image count
panel-by-panel visual action
short Chinese labels
speech bubbles / captions
takeaway
metaphor risk note
analogy limitation note when needed
AIGC label note when public sharing is intended
```

### Step 7: Write image prompt

Use `references/prompt-template.md`.

The prompt should be clear enough for an image model to generate the chosen comic-style explanatory visual or visual series.

### Step 8: QA check

Use `references/qa-checklist.md` and `references/anti-patterns.md`.

Check:

```text
concept accuracy
metaphor faithfulness
type/channel/style fit
comic clarity
visual hierarchy
text length
domain safety
```

### Step 9: Generate images

When this skill is invoked, use the image generation workflow and produce the comic image or image series.

If the user's wording asks for a plan, storyboard, or prompt, treat that as a request for internal preparation and still generate the comic image. Do not output a text-only concept explanation, storyboard-only answer, or prompt-only answer as the final deliverable.

When generating images, first choose the runtime route:

```text
Codex runtime with native image tool → use the editor's built-in image generation tool.
Other editor or no native image tool → use the configured OpenAI Images API route.
```

Do not call the external API from Codex when the native image generation tool is available. Do not pretend to generate images in editors that lack an image tool; require API configuration and save the generated file path.

## Output behavior

### Final output

Internally prepare the concept card, metaphor, mandatory image-count plan, storyboard, prompt, and QA notes. Then generate the requested comic image or image series. For an image series, produce separate image files and return separate paths.

Do not ask for confirmation unless the concept is ambiguous, unsafe, or depends on a specific audience/style the user has not provided.

## Language

Default output language: Chinese.

Image text should usually be Chinese unless the user requests another language.

Keep labels short and readable.

## Non-negotiable rules

1. Choose the number of images adaptively; each image should explain one clear expression point.
2. If one point cannot be explained simply in one image, split it into multiple separate image files.
3. Metaphor must preserve the concept’s core relationship.
4. Characters must perform meaningful actions.
5. Avoid long text inside the image.
6. Avoid copying any existing character IP or unique visual style.
7. Do not imitate a named living artist or copyrighted character style.
8. Do not overstate simplified explanations.
9. Do not give personal medical, legal, or financial advice.
10. The final answer must include the generated comic image or image paths, not a text-only explanation.
11. The final image should feel like a comic explanation, not a PPT page.
12. An N-image series must result in N separate generated image files; a single combined image is a failure.
13. For public-sharing outputs, reserve or report an AIGC label when the publishing context requires it.
