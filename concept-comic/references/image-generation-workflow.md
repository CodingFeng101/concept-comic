# Image Generation Workflow

Use this whenever this skill is invoked.

## Runtime route

Before generating, decide which runtime is available:

```text
Codex with native image generation tool:
  Use the built-in image generation tool directly.

Other editor or no native image generation tool:
  Use references/external-image-api.md and call the configured OpenAI Images API.
```

Do not use the external Images API from Codex when the native image tool is available. Do not stop at a prompt-only answer when this skill is invoked and image generation is available.

## Internal preparation

Before image generation, silently prepare:

1. Concept Card
2. Comic Taxonomy
3. Visual Metaphor
4. Composition Pattern
5. Image Count Plan
6. Storyboard
7. Chinese Labels
8. Image Prompt
9. QA Notes

## Mandatory image count plan

Before writing the storyboard or prompt, decide the image count explicitly.

Use this decision table:

| Explanation shape | Output |
| --- | --- |
| one expression point that stays visually simple | 1 image |
| one expression point that would require dense panels, small labels, or too many arrows | split into N images |
| multiple expression points, sub-ideas, layers, mechanisms, misconceptions, or use cases | N-image series |

The plan must include:

```text
image_count:
output_scale:
channel:
primary_comic_type:
reason:
per_image_focus:
```

If the user requests a specific count, follow it unless it would make the explanation inaccurate or unreadable.

If the user does not request a count, do not default to one image. Choose the smallest count that keeps every image simple and clear.

Rules:

```text
One image = one expression point.
If one point does not fit cleanly in one image, split it.
Do not use a multi-panel image to hide overcrowding.
Use multiple images when clarity improves, even for one original point.
N-image series = N separate generated image files.
```

## Series generation

When `image_count` is greater than 1, generate each image separately.

In Codex:

```text
Call the native image generation tool once per planned image.
Do not make one tool call that asks for all images at once.
```

Outside Codex:

```text
Send one Images API request per planned image.
Use n: 1 for each request.
```

Each per-image prompt must say:

```text
Generate image {i} of {N} only.
This is one standalone comic image.
Use 16:9 horizontal format unless the selected channel is short vertical comic / mobile scroll.
Do not include image {other numbers}.
Do not create a montage, collage, grid, strip, contact sheet, combined series poster, or multi-image layout.
```

The number of saved image paths must equal `image_count`. If the result is one combined image containing multiple planned images, treat it as failed and regenerate separately.

Examples:

```text
Immune system
1. What it does
2. How it detects invaders
3. Why overreaction can be harmful
```

```text
Inflation
1. Single-panel concept
2. Cause/process comic
3. Misconception correction
```

## Default output

Default:

```text
the smallest number of comic images that explains the concept clearly
16:9 horizontal unless channel/form requires a short vertical comic
```

## Image quality checks

Regenerate or revise if:

- Chinese text is unreadable
- labels are wrong
- image contains too much text
- metaphor is visually confusing
- the generated image adds misleading concepts
- layout looks like a PPT infographic
- reading order is unclear
- too many panels are squeezed into one image
- one expression point is overloaded inside a single image
- multiple planned images are combined into one montage, collage, grid, strip, long image, or series poster
- a series repeats the same idea instead of splitting real sub-ideas

## Response after generation

After image generation, keep the response minimal.  
Include the saved image path or paths. Do not explain every detail unless the user asks.
