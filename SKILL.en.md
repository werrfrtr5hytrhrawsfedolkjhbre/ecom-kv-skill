---
name: ecom-kv-designer
description: "Ecommerce product campaign key visuals: three-dimensional selling-point scoring, design rules P1–P10, category scenarios, copy templates, prohibited-word checks, platform specifications and delivery self-checks. A two-stage workflow (proposal, then generation and inspection) for merchants without design experience."
---

# Ecommerce Product Key Visual Design Skill

English translation of the complete main SKILL.md supplied for this test. The original Chinese main file and all referenced knowledge/platform documents are retained in this package. Reference documents remain in their original language; this is not a translation of the entire knowledge library. The Chinese original is the authoritative test source. Observed conflicts and execution differences are recorded separately, not silently repaired here.

The core workflow is platform-independent. Load platform differences from `platforms/` as directed below.

## 0. Platform adaptation: required once before starting

1. Identify the current host from a reliable signal:

| Platform | Identification signal | Document |
|---|---|---|
| Doubao Work | Skill under `.user_skills/` or `.doubaowork/` | `platforms/doubao-work.md` |
| WorkBuddy / CodeBuddy | Under `.codebuddy/` or `codebuddy/skills`, or supports `@references` | `platforms/workbuddy.md` |
| Qwen Work / Qwen Code | Under `.qwen/skills` or `~/.qwen/skills`, or `$QWEN_SKILL_ROOT` exists | `platforms/qwenwork.md` |
| ChatGPT / Codex | Located in an OpenAI Skills directory | `platforms/agent-cli.md` |
| Claude Code | Under `~/.claude/skills/` or project `.claude/skills/` | `platforms/agent-cli.md` |
| Gemini CLI / Cursor and other CLI hosts | Use the general CLI profile | `platforms/agent-cli.md` |

2. Open the corresponding platform document and follow it strictly. Platform instructions take precedence over this main file where they conflict. General domain knowledge is in `knowledge/`.
3. If the platform cannot be reliably identified, ask the user rather than guessing. If the user also cannot identify it, skip platform adaptation and use the core workflow: export prompts and do not embed symbols.

## 1. Core workflow: two stages in strict order

### Stage one: design proposals

1. Collect information using `knowledge/08-intake-questions.md`. Output a Product Information Card and obtain user confirmation. Ask about uncertain product recognition; do not guess.
2. Extract selling points using `knowledge/02-selling-point-rules.md`: three-dimensional scoring and FAB rewriting. Select one main selling point and at most two supporting points.
3. Build the strategy using all P1–P10 rules in `knowledge/01-design-hard-rules.md`, target audiences and scenarios in `knowledge/03-kv-scenario-library.md`, and canvas specifications in `knowledge/06-platform-specs.md`.
4. Generate copy using `knowledge/04-copywriting-templates.md`. Check every word against `knowledge/05-ad-law-prohibited-words.md`.
5. Present two or three differentiated proposals in the format below, append outstanding questions, and wait for the user to select or revise a proposal.

### Stage two: finished output

6. Generate images using the method in the current platform document.
7. Run every check in `knowledge/07-self-check-list.md`; deliver the Self-check Report with the output.
8. Iterate directly for visual-only changes. Return to the relevant proposal step if selling points or copy change. Limit each image to two revision rounds.

## 2. Fixed proposal format

```text
Proposal N: {name}
- Main selling-point claim: one sentence
- Visual strategy: composition / palette / style / scenario
- Copy: headline (8–15 characters) / subheading / offer / CTA
- Layout: ASCII wireframe showing product, copy and offer positions
- Image-generation prompts: Chinese and English
- Design rationale: explicitly reference applicable rules P1–P10
```

The source uses a Chinese character-count convention and provides no separate English counting method. This translation preserves that requirement rather than inventing one.

## 3. Core rules at a glance

| Rule | Requirement |
|---|---|
| P1 | Three-second clarity: product first, main selling point second, price/offer third, CTA last. Reduce an oversized product if needed to leave room for copy. |
| P2 | One main selling point; at most two supporting points with lower visual weight. |
| P3 | Consumer benefits through FAB; no isolated technical parameters without explaining their benefit. |
| P4 | Clear hierarchy, contrast and readable type. Align evenly; center text inside shapes, maintain equal margins and regular spacing, and avoid overlapping button text. |
| P5 | Text covers at most 30% of the canvas, or 20% for feed placements. At most three core copy blocks plus an information area of at most five lines. Where no platform is specified, show as much supplied product information as practical. |
| P6 | Use relevant scenarios and category-appropriate material and lighting quality; avoid crude flat-color compositions. |
| P7 | Compliance takes priority. |
| P8 | Complete AIDA: attention, interest, desire and action. |
| P9 | Fit platform dimensions and safe areas. |
| P10 | Use the user's actual product photograph, cut out or with its background replaced. Never regenerate the product. Preserve authorization marks and logos. Integrate edges, shadows and reflections with the background. |

Conflict priority: P7 and P10, then P9, P1, P2, P8, P4/P5/P6, and finally P3.

Selling-point scoring: demand strength, differentiation and perceptibility, each from 1 to 5. Totals of 12–15 qualify as lead candidates (at most two), 9–11 as secondary points, and 8 or less are discarded. Differentiation of 1 or perceptibility of 1 disqualifies a point.

The four-layer self-check contains 24 items: A1–A6 for selling points/copy; B1–B10 for visuals, including text accuracy, alignment and cutout integration; C1–C4 for compliance, including product authenticity; D1–D4 for delivery. The source's full-pass wording is “Passed (24/24).”

## 4. Mandatory rules

1. Never enter image generation before stage-one user confirmation.
2. Zero tolerance for prohibited words: rewrite any hit and explain the reason.
3. Every delivery must include a Self-check Report. Do not deliver a finished output if any required check fails.
4. Design rationale must cite actual rule numbers P1–P10. Do not invent rules.
5. Change only affected parts rather than restarting the design. At most two revision rounds per image.
6. If the user says “I don't know” or “you decide,” apply category defaults from the scenario library and explicitly label assumptions.
7. If the user's request conflicts with a design rule, explain the rule before carrying out the user's request.
8. Use concise text. If a platform lacks table or code-block support, use aligned plain text without omitting content.
9. P10 has no exceptions: use the user's product photograph through cutout or subject-preserving background replacement. Do not regenerate the product. Keep authorization marks and brand logos intact. Request a clearer photo if needed; never guess or invent missing details.
10. Text rendering: only the main headline and offer numerals may be embedded during generation. Include “Render the text exactly, character by character: {copy}.” Verify all characters afterwards; regenerate or switch to a text-free image plus later typesetting if errors occur. Do not embed subheadings or CTAs; provide typesetting instructions for them.
11. Copyright and authorization marks containing Japanese or decorative symbols such as ©®™★ must never be rendered by the image model. Preserve them pixel-for-pixel from the source or have the user add them later with a layout tool. Include this instruction in generation/edit requests: “Text in the image may contain only Simplified Chinese, English, numerals and common symbols such as ¥ % + - ×. Do not render Japanese or decorative symbols such as ©®™★. Keep all original product lettering pixel-for-pixel unchanged.”
12. Embedded symbols must come from the current platform's stable renderable-symbol list under `platforms/assets/`. Move unstable or unsupported symbols to later typesetting and explain this in the layout guide. Check symbols with text after generation; compare product details against the original after editing.
13. Alignment and spacing: text inside frames or colored shapes must be horizontally and vertically centered, with equal distances to all four sides. Keep paragraph gaps regular; avoid overlapping or cramped buttons and badges; use consistent line spacing in information lists.

## 5. Knowledge-document index

| File | Document | Contents |
|---|---|---|
| `knowledge/01-design-hard-rules.md` | Design hard rules | P1–P10 and conflict priority |
| `knowledge/02-selling-point-rules.md` | Selling-point extraction | Candidate pool, three-dimensional scoring, six FAB templates, examples including anime merchandise |
| `knowledge/03-kv-scenario-library.md` | Category scenarios | Eleven major categories and subcategories: audience, scenarios and visual advice; prompt assembly appendix |
| `knowledge/04-copywriting-templates.md` | Copy templates | General headline/subheading/offer/CTA patterns, information lines, eleven category templates and five campaign scenarios |
| `knowledge/05-ad-law-prohibited-words.md` | Prohibited-word list | Six word families and frequently asked questions |
| `knowledge/06-platform-specs.md` | Ecommerce specifications | Taobao, JD, Pinduoduo, Douyin and Xiaohongshu dimensions, file sizes, restrictions and safe areas |
| `knowledge/07-self-check-list.md` | Self-check checklist | Four layers, 24 items, report template and 15 quick visual checks |
| `knowledge/08-intake-questions.md` | Intake questions | Product Information Card, introduction and three-round question script |

