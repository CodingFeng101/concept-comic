# Concept Types

Classify comic requests with a layered taxonomy, not a single genre list.

Commercial genres, publishing traditions, and visual styles are useful context, but they should not drive this skill. For concept explanation, route by five programmable dimensions:

```text
length/form + function + narrative structure + style shell + channel
```

## Five dimensions

| Dimension | What to decide | Common values |
| --- | --- | --- |
| Length/form | How much canvas or sequence is needed? | single panel, four-panel, short series, short vertical comic |
| Function | What job must the comic do? | explain, compare, correct, teach, warn, clarify |
| Narrative structure | How does understanding move? | single scene, contrast, question-answer, cause/process, system, journey |
| Style shell | What visual surface fits audience/channel? | clean color, whiteboard sketch, flat illustration, light manga, sticker-like |
| Channel | Where will it be read? | chat, social image, WeChat article, slide, mobile scroll |

Use these dimensions as labels for planning. The final selected type should be the best structure for the user's concept, not the most stylish category.

## Primary V1 types

| User intent or signal | Primary type | Default form |
| --- | --- | --- |
| "What is this?" | Single-panel concept | one 16:9 image |
| "Difference / A vs B / before vs after" | Comparison explanation | left-right or before-after image |
| "Small concept with setup and turn" | Four-panel process | one four-panel image if readable |
| "FAQ / is it true / why not?" | Dialogue clarification | short character Q&A comic |
| "Why / how / steps / mechanism" | Cause/process comic | chain, pipeline, or short series |
| "Many parts / modules / ecosystem" | System map | comic-like system scene |
| "From A to B / learning path / state change" | Journey/state transition | path or staged transformation |
| "Long flow for mobile / WeChat long image" | Short vertical comic | vertical screens, one point per screen |

Trade-offs do not need a separate top-level type. Route them as comparison explanation, system map, or journey/state transition, then use balance scale, tug-of-war, two doors, or split road as the visual metaphor.

## Auto-routing rules

Use these rules before choosing style.

```text
If the input has difference, compare, versus, A/B, before/after, old/new, wrong/right:
  choose comparison explanation.

If the input has steps, flow, first, then, how, from...to..., trigger, lead to, result:
  choose cause/process comic.
  If there are more than 4 steps and the channel is mobile or WeChat long image:
    upgrade to short vertical comic.

If the input has FAQ, is it true, why not, misconception, user asks, teacher says, doctor says:
  choose dialogue clarification or misconception correction.

If the input has five or more explicit objects, or dense relation words such as dependency, module, ecosystem, upstream, downstream, link, platform, layer:
  choose system map.

If the input has beginner to expert, onboarding, journey, transformation, stage, state, path:
  choose journey/state transition.

If none of the above applies and there is one core concept:
  choose single-panel concept.
```

## 1. Single-panel concept

Use for definition-style or abstract concepts where one visual metaphor can carry the explanation.

Best for:

- "what is it?"
- one core mechanism
- one memorable mental model
- default fallback when other routes do not match

Structure:

```text
one core scene + one main metaphor + 1-3 labels + one takeaway
```

Prompt focus:

```text
one core claim
one visual metaphor
one action moment
no second storyline
```

## 2. Comparison explanation

Use for A vs B, old vs new, wrong vs right, before vs after, or strategy differences.

Structure:

```text
left/right or before/after
shared comparison axis
2 short features per side
one bottom takeaway
```

Prompt focus:

```text
comparison axis: cost, speed, risk, accuracy, workflow, user experience, or mental model
```

If the comparison axis is unclear, ask only if necessary; otherwise infer the most educational axis.

## 3. Four-panel process

Use when a concept has a compact sequence and each panel can stay simple.

Structure:

```text
Panel 1: setup
Panel 2: pressure/change
Panel 3: key turn or mechanism
Panel 4: result/takeaway
```

This is useful for light education and memory. Do not use it for long workflows. If the four panels become crowded, split the process into separate images or use a short vertical comic.

## 4. Dialogue clarification

Use when the concept is best explained through a realistic question and correction.

Best for:

- FAQ
- common misconception
- user training
- customer education
- "Isn't X just Y?"

Structure:

```text
questioner asks a real misunderstanding
explainer corrects one point
small example or visual proof
short takeaway
```

Prompt focus:

```text
speaker roles
misconception sentence
correction sentence
visual example
```

Avoid pure text bubbles. Each exchange should have visible action or a concrete object.

## 5. Cause/process comic

Use when the concept is about why something happens or how to do something.

Structure:

```text
condition/trigger -> mechanism -> result
```

Prompt focus:

```text
start state
step count limit
visible action per step
end state or completion signal
```

If the flow has 3-6 steps, one image may work. If it has more steps, use an image series or short vertical comic.

## 6. System map

Use when multiple parts interact.

Best for:

- architecture
- organizations
- ecosystems
- platforms
- markets
- immune system or other role-based systems

Structure:

```text
central system + 3-7 nodes + main path + simple arrows + visible bottleneck
```

Prompt focus:

```text
node limit
main path
side path
blocked point
role of each character/module
```

Keep this comic-like. If it becomes a dense architecture diagram or PPT infographic, split it into multiple images.

## 7. Journey/state transition

Use when the concept is a change over time or a path toward a conclusion.

Structure:

```text
starting state -> trigger/obstacle -> tool/clue -> end state
```

Prompt focus:

```text
starting state
turning point
ending state
emotion or confidence curve
```

If the concept only has start and end with no transition trigger, route to comparison explanation instead.

## 8. Short vertical comic

Use for mobile-first long explanations, WeChat-style long images, or workflows that need more than four beats.

Structure:

```text
screen 1: hook
screen 2..N-1: one point per screen
final screen: takeaway
```

Prompt focus:

```text
total screens
one point per screen
pause or reveal position
mobile readability
```

Do not use this as the default. Use it only when the channel or step count justifies a vertical scroll format.

## Misconception correction

Misconception correction can be implemented as either comparison explanation, dialogue clarification, or four-panel process.

Choose by form:

```text
wrong vs right model -> comparison explanation
user asks and teacher corrects -> dialogue clarification
wrong use leads to problem -> four-panel process
```

## Selection order

Use this order when auto mode is needed:

```text
1. High-risk domain check
2. User-specified channel and format
3. Core concept count
4. Routing trigger words
5. Step count or node count
6. Style shell
```

Default priority when several options are plausible:

```text
single-panel concept
comparison explanation
dialogue clarification
cause/process comic
four-panel process
system map
journey/state transition
short vertical comic
```

The selected type does not decide image count by itself. Image count still follows the rule: one expression point per image, split when crowded.
