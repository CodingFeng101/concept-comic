# Concept Comic

<p align="center">
  <strong>English</strong> | <a href="./README.zh-CN.md">简体中文</a>
</p>

**Concept Comic** is an AI skill for turning complex ideas into comic-style explanation images.

## ✨ What Makes It Different

**🎯 Expression-point planning**  
Concept Comic plans by expression point, not by topic title. A complex concept is split into the smallest visual steps that can still be read quickly.

**🧭 Five-dimensional comic taxonomy**  
The skill does not pick a comic type from a flat genre list. It classifies each request across length/form, function, narrative structure, style shell, and channel before writing the storyboard.

**🧠 Automatic type routing**  
Concept Comic can route a request to single-panel concept, comparison explanation, four-panel process, dialogue clarification, cause/process comic, system map, journey/state transition, or short vertical comic.

**🧩 Structure before style**  
The workflow turns a concept into a concept card, chooses a visual metaphor, writes a storyboard, and only then generates the comic. This keeps the image explanatory instead of decorative.

**🛡️ Channel, style, and risk aware**  
Prompts carry audience, channel, risk level, preferred type, and style shell. High-risk topics stay educational, metaphor limits are checked, and public-sharing outputs can reserve AIGC labeling space.

**📚 Built from proven visual-explanation practice**  
The skill combines comics, multimedia learning, dual coding, icon usability, and image-prompt practice into one repeatable workflow.

**🔌 Editor-agnostic generation path**  
In Codex, use the host image-generation capability directly. In other editors, configure an image API endpoint and key. The default model target is `gpt-image-2`.

```text
OPENAI_API_KEY      required outside native image hosts
OPENAI_BASE_URL     optional, default: https://api.openai.com/v1
OPENAI_IMAGE_MODEL  optional, default: gpt-image-2
```

For a multi-image explanation, make one image request per planned comic image. Do not ask the image model to create the whole series as one combined poster.

## 🧠 Method Sources

Concept Comic packages practical visual-explanation habits from several public bodies of work:

- **Comics and sequential art**: Scott McCloud's work on comics as communication, especially simplification toward meaning. See [Understanding Comics overview](https://www.ebsco.com/research-starters/literature-and-writing/understanding-comics-invisible-art-scott-mccloud) and the [Cleveland Public Library toolkit](https://cpl.org/wp-content/uploads/comic-discussion-guide-Understanding-Comics-Toolkit-11x17-Booklet.pdf).
- **Multimedia learning**: Richard Mayer's principles support removing irrelevant detail, keeping labels close to visuals, and using cues to guide attention. See the Cambridge Handbook chapter on [coherence, signaling, redundancy, and spatial contiguity](https://www.cambridge.org/core/books/cambridge-handbook-of-multimedia-learning/principles-for-reducing-extraneous-processing-in-multimedia-learning-coherence-signaling-redundancy-spatial-contiguity-and-temporal-contiguity-principles/CD5B7AE1279A9AB81F8EEBB53DBEC86E).
- **Dual coding**: Paivio's dual coding theory motivates pairing short verbal labels with strong visual representation. See [Dual Coding Theory and Education](https://nschwartz.yourweb.csuchico.edu/Clark%20%26%20Paivio.pdf).
- **Icon and label usability**: NN/g guidance supports short labels, recognizable icons, and avoiding unlabeled symbolic UI. See [Icon Usability](https://www.nngroup.com/articles/icon-usability/) and [Yes, Icons Need Text Labels](https://www.nngroup.com/videos/icon-text-labels/).
- **Image-prompt practice**: the skill turns those ideas into prompt rules such as short labels, visible action, metaphor-first composition, and no dense infographic or PPT-style layout.

## 🖼️ Real Generated Examples

### RAG vs Knowledge Graph QA

Four points: evidence retrieval, relationship traversal, failure modes, and hybrid use.

![RAG vs Knowledge Graph QA four-comic grid](concept-comic/assets/examples/rag-vs-kgqa-grid.png)

### Inflation As A System

Four points: demand surge, supply shock, money versus goods, and purchasing power.

![Inflation system four-comic grid](concept-comic/assets/examples/inflation-system-grid.png)

### Natural Selection

Four points: variation, selection pressure, reproduction, and population change.

![Natural selection four-comic grid](concept-comic/assets/examples/natural-selection-grid.png)

## 🚀 Use

```text
Use Concept Comic to explain RAG vs Knowledge Graph QA.
```

Expected behavior:

```text
1. Plan how many comic images are needed.
2. Generate separate comic image files.
3. Return image paths.
```

Output contract:

```text
One point = one comic image.
If one point does not fit clearly, split it.
N planned images = N separate generated image files.
Final output is comic imagery, not a text-only explanation.
```

## 📦 Skill Contents

```text
concept-comic/
├─ SKILL.md                         # Main skill instructions and trigger metadata.
├─ agents/                          # UI metadata for skill lists and quick starts.
│  └─ openai.yaml                   # Display name, short description, and default prompt.
├─ references/                      # Load-on-demand guidance used by the skill workflow.
│  ├─ concept-understanding.md      # How to extract the core concept and explanation goal.
│  ├─ concept-types.md              # Five-dimensional taxonomy and auto-routing rules.
│  ├─ concept-to-metaphor.md        # Rules for turning abstract structure into visual metaphor.
│  ├─ metaphor-bank.md              # Reusable metaphor patterns.
│  ├─ comic-grammar.md              # Comic framing, characters, action, labels, and pacing.
│  ├─ composition-patterns.md       # Visual structures, style shells, and channel-aware layouts.
│  ├─ storyboard-template.md        # Storyboard fields for each planned comic image.
│  ├─ prompt-template.md            # Prompt fields for taxonomy, channel, risk, and style.
│  ├─ image-generation-workflow.md  # Native generation route, count planning, and format handling.
│  ├─ external-image-api.md         # API fallback for editors without built-in image generation.
│  ├─ qa-checklist.md               # Checks for concept, taxonomy, channel, style, safety, and output count.
│  ├─ anti-patterns.md              # Common failures such as dense infographics or merged series.
│  ├─ domain-safety.md              # High-risk mode, analogy limits, AIGC labels, and IP/style safety.
│  ├─ response-format.md            # Final response shape and image path reporting.
│  └─ visual-style.md               # Visual style defaults for readable comic images.
├─ examples/                        # Text example briefs for common concept requests.
│  ├─ black-hole.md                 # Example brief for a science concept.
│  ├─ entropy.md                    # Example brief for entropy.
│  ├─ immune-system.md              # Example brief for an analogy-heavy process.
│  ├─ inflation.md                  # Example brief for an economic system.
│  ├─ natural-selection.md          # Example brief for evolution over generations.
│  ├─ opportunity-cost.md           # Example brief for a decision concept.
│  ├─ path-dependence.md            # Example brief for historical lock-in.
│  ├─ prisoner-dilemma.md           # Example brief for game theory.
│  ├─ rag-vs-kgqa.md                # Example brief for an AI architecture comparison.
│  └─ water-cycle.md                # Example brief for a physical process.
├─ tests/                           # Sample pressure prompts for checking skill behavior.
│  └─ sample-prompts.md             # Requests that exercise image count and output rules.
├─ docs/                            # Repository-facing documentation pages.
│  ├─ gallery.md                    # Gallery notes for example outputs.
│  ├─ showcase.md                   # Showcase notes for generated examples.
│  └─ usage.md                      # Additional usage notes.
└─ assets/                          # Images used by README, docs, and examples.
   ├─ cover.png                     # Cover graphic asset.
   ├─ previews/                     # Small preview images for older example topics.
   │  ├─ entropy-preview.png        # Entropy preview image.
   │  └─ opportunity-cost-preview.png # Opportunity cost preview image.
   └─ examples/                     # Generated comic examples and README grids.
      ├─ .gitkeep                   # Keeps the examples directory present before assets exist.
      ├─ rag-vs-kgqa-grid.png       # Four-comic grid preview.
      ├─ inflation-system-grid.png  # Four-comic grid preview.
      ├─ natural-selection-grid.png # Four-comic grid preview.
      ├─ rag-vs-kgqa/               # Four independent RAG vs KGQA comic images.
      │  ├─ 01-rag-find-evidence.png
      │  ├─ 02-kgqa-follow-relations.png
      │  ├─ 03-different-failure-modes.png
      │  └─ 04-hybrid-map-evidence.png
      ├─ inflation-system/          # Four independent inflation system comic images.
      │  ├─ 01-demand-surge.png
      │  ├─ 02-supply-shock.png
      │  ├─ 03-money-vs-goods.png
      │  └─ 04-purchasing-power.png
      └─ natural-selection/         # Four independent natural selection comic images.
         ├─ 01-variation.png
         ├─ 02-selection-pressure.png
         ├─ 03-reproduction.png
         └─ 04-population-changes.png
```

## License

MIT
