# Composition Patterns

Use composition patterns as visual structures for the selected type in `concept-types.md`.

Keep the distinction clear:

```text
comic type = explanation job
composition pattern = visual structure
style shell = surface look
channel = canvas and reading constraints
```

## Priority patterns

The most stable V1 patterns are:

```text
single-panel concept
left-right comparison
dialogue clarification
cause/process chain
four-panel process
system map
journey/state transition
short vertical comic
```

## 1. Single-panel concept

Use when one metaphor can explain one concept.

Structure:

```text
one central scene
one main character or object
1-3 short labels
one takeaway
```

Prompt guardrails:

```text
no second storyline
no dense labels
no table
```

## 2. Left-right comparison

Use for A vs B, old vs new, wrong vs right, or before vs after.

Structure:

```text
left scene
right scene
shared visual axis
bottom takeaway
```

Do not turn the comparison into a table. Use two scenes, two character actions, or two states.

Trade-off variants:

```text
balance scale
tug-of-war
two doors
forked road
```

## 3. Four-panel process

Use when the concept has four clean beats.

Structure:

```text
Panel 1: setup
Panel 2: pressure/change
Panel 3: key turn/mechanism
Panel 4: result/takeaway
```

Use this only when each panel can stay readable. If one process needs too many actors, arrows, or labels, split it into multiple separate images.

## 4. Dialogue clarification

Use when a realistic question and correction would teach faster than a diagram.

Structure:

```text
questioner: common misunderstanding
explainer: concise correction
visual proof or example
takeaway
```

Guardrails:

```text
every speech bubble must be short
dialogue must not replace visual action
speaker roles must be clear
```

## 5. Cause/process chain

Use for causal concepts, tutorials, mechanisms, or operating flows.

Structure:

```text
trigger -> visible mechanism -> consequence
```

Good visual forms:

- domino chain
- conveyor belt
- snowball
- chain links
- pipeline
- before-and-after path

If there are more than 4-6 steps, use a series or short vertical comic.

## 6. System map

Use for concepts with interacting parts.

Structure:

```text
central system + 3-7 roles/modules + main path + simple arrows
```

Comic controls:

```text
use characters or objects to represent roles
show one main path first
mark the bottleneck or dependency
limit node count
```

Risk:

```text
system map can become a PPT infographic
```

If it starts looking like an architecture poster, reduce parts or split into multiple images.

## 7. Journey/state transition

Use for reasoning, learning, onboarding, or state changes.

Structure:

```text
start state -> obstacle/trigger -> tool/clue -> end state
```

If there is no transition trigger, choose comparison instead.

## 8. Short vertical comic

Use for mobile-first long explanations or WeChat-style long images.

Structure:

```text
screen 1: hook
screen 2: point 1
screen 3: point 2
screen N: takeaway
```

Rules:

```text
one point per screen
few words per screen
clear scroll rhythm
do not imitate paper page layout
```

Use this only when the channel or step count requires it.

## Style shells

Choose style after type and composition.

Common style shells:

```text
clean color educational comic
whiteboard sketch
flat illustration comic
light manga screen-tone
sticker-like expressive comic
```

Do not imitate a named living artist or copyrighted character style. Describe formal qualities instead.

## Pattern selection

Choose by user intent:

```text
What is it? -> single-panel concept
A vs B? -> left-right comparison
FAQ or "isn't it..."? -> dialogue clarification
How or why? -> cause/process chain
Four compact beats? -> four-panel process
Many interacting parts? -> system map
State change or learning path? -> journey/state transition
Mobile long flow? -> short vertical comic
```

Do not choose a multi-panel pattern just to cram more content into one image. The image-count rule still wins: one clear expression point per image; split when crowded.
