# Prompt Template

Use this template for the final image prompt or prompt series.

For an image series, write one prompt per image and generate each prompt separately. Do not ask the image model to generate the full series in one prompt.

## Full template

```text
Generate one 16:9 horizontal Chinese comic-style explanatory illustration.

Series position:
Image {image_index} of {image_count}. Generate this image only.

Topic:
{concept_name}

Source text:
{source_text}

Audience:
{target_audience}

Channel:
{channel}

Risk level:
{risk_level}

Preferred type:
{preferred_type_or_auto}

Style shell:
{style_shell_or_auto}

Core idea:
{one_sentence_explanation}

Comic taxonomy:
Length/form: {length_form}
Function: {function}
Narrative structure: {narrative_structure}
Style shell: {style_shell}
Channel: {channel}

Primary comic type:
{primary_comic_type}

Visual metaphor:
{visual_metaphor}

Comic layout:
{composition_pattern}

Output scale:
{single image / image series}

Image count plan:
Count: {image_count}
Reason: {why this count is enough}
Per-image focus: {per_image_focus}

Storyboard:
{panel_script}

Chinese text in the image:
Title: {short_title}
Labels: {short_labels}
Captions / speech bubbles: {short_captions}
Takeaway: {takeaway}

Metaphor risk note:
{metaphor_risk_note}

Analogy limitation note:
{analogy_limitation_note_if_needed}

AIGC label / public sharing note:
{aigc_label_note_if_needed}

Visual style:
{style_shell}. Clean, modern, playful educational comic.
Light background.
Clear linework.
Expressive characters.
Simple but meaningful scenes.
Strong visual hierarchy.
Readable Chinese labels.
Use 2–4 colors to highlight the main relationship.

Important constraints:
Each image should explain one clear expression point.
If one expression point cannot stay simple in one image, split it into multiple images.
Generate only one standalone image for this prompt.
Do not include other images from the series.
Do not create a montage, collage, grid, strip, contact sheet, combined series poster, or multi-image layout.
Use visual action instead of long text.
Keep the metaphor faithful to the concept.
Do not exaggerate beyond the concept.
Do not create a dense corporate infographic.
Do not create a text-heavy PowerPoint slide.
Do not copy any existing character IP.
Do not imitate a named living artist or copyrighted character style.
If this is a public-sharing image, leave room for an AIGC label or footer note.
```

## Compact template

```text
Create one 16:9 Chinese educational comic image explaining {concept}.
This is image {image_index} of {image_count}; generate this image only.
Core idea: {core_idea}.
Audience: {audience}. Channel: {channel}. Risk level: {risk_level}.
Comic type: {primary_comic_type}. Style shell: {style_shell}.
Use the metaphor of {metaphor}.
Layout: {layout}.
Panels: {panels}.
Chinese labels: {labels}.
Style: clean modern comic, light background, readable text, expressive actions.
Avoid: long text, dense infographic, misleading metaphor, copied IP, named artist imitation, montage, collage, grid, strip, combined series poster.
```

## Prompt rules

1. Put the core idea before the scene description.
2. State the image count plan before the storyboard.
3. State the intended output scale: single image or image series.
4. Include channel, risk level, primary comic type, and style shell.
5. Describe images and panels in reading order.
6. Use short Chinese labels.
7. Explain visual relationships with actions.
8. Include constraints to prevent PPT-like output.
9. For a series, make one image-generation call per prompt.
10. Do not include unnecessary decorative details.
