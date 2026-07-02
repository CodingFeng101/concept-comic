# QA Checklist

## 1. Concept accuracy

- Is the concept correct?
- Does the comic preserve the core relationship?
- Does the metaphor imply anything false?
- Does it avoid overclaiming?
- Does it avoid false agency?
- Does it avoid turning probabilistic concepts into deterministic ones?

## 2. Metaphor quality

- Is the metaphor concrete?
- Does the metaphor preserve the concept structure?
- Is it easy for beginners?
- Does the metaphor require less explanation than the concept itself?

## 3. Image count planning

- Was image count planned before storyboard or prompt writing?
- Does the plan state count, output scale, reason, and per-image focus?
- Is the chosen image count appropriate for the concept?
- Does each image explain exactly one clear expression point?
- If the output is one image, can that point stay simple, readable, and uncrowded?
- If one point is visually overloaded, was it split into multiple images?
- If the output is a series, does each image have a distinct focus instead of repeating the same idea?
- If the plan says N images, are there N separate generated image files?

## 4. Type, channel, and style fit

- Did it classify the request across length/form, function, narrative structure, style shell, and channel?
- Is the selected primary comic type aligned with the user's question?
- If the input is A vs B, did it use comparison unless another type is clearly better?
- If the input is FAQ or misconception-heavy, did it consider dialogue clarification?
- If the process is long or mobile-first, did it consider short vertical comic?
- Is the style shell chosen after type and channel, not before?
- Does the style avoid named artist imitation and copyrighted characters?
- Does the channel choice affect canvas, text length, and reading order?

## 5. Generation route

- If running in Codex, did it use the native image generation tool instead of the external API?
- If running outside Codex without a native image tool, did it require `OPENAI_API_KEY` and call the Images API route?
- Does the external API route default to `gpt-image-2` without silent fallback?
- Did the final response include the saved image path or paths?
- Does the number of saved image paths match the planned image count?
- Did the final response avoid text-only concept explanation, storyboard-only output, and prompt-only output?
- Did it avoid returning one montage, collage, grid, strip, long image, or combined series poster when the plan required multiple images?

## 6. Comic clarity

- Does each image have one clear expression point?
- Is the reading order clear?
- Does each panel advance understanding?
- Are characters doing meaningful actions?
- Is there conflict, choice, transformation, or discovery?
- Is the takeaway memorable?

## 7. Visual quality

- Is each image not crowded?
- Are labels readable?
- Is the main subject obvious?
- Is there strong visual hierarchy?
- Does it look like a comic rather than a PPT slide?

## 8. Text quality

- Are labels short?
- Is the title clear?
- Are captions short?
- Is Chinese text readable?
- Are there no long paragraphs inside the image?

## 9. Domain safety

- Is the explanation educational only?
- Does it avoid medical, legal, financial, or safety advice?
- Does it avoid dangerous operational instructions?
- If the topic is high risk, did it mark the output as needing source/review context?
- If the metaphor is partial, did it include a limitation note outside the image?
- If the output is intended for public sharing, did it include or reserve room for AIGC labeling?

## QA score

Optional score:

```text
Accuracy: /5
Metaphor: /5
Comic clarity: /5
Visual simplicity: /5
Safety: /5
```

Revise if any score is below 4.
