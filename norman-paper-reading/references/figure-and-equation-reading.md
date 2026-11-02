# Reading figures, tables, and equations

## Capture and show the original

Each individually explained figure or table must appear as an original source image directly below its own heading, before the explanation. This applies to chat, Markdown notes, and HTML, including focused requests. A source locator or link alone is not a substitute when an image can be obtained. Keep original captions near the image, preserving their scientific wording; translations or commentary must be labeled separately.

For a local PDF, inspect a complete page first to locate the actual figure/table and caption; a textual "Fig." reference is not the figure location. Confirm the bounding box visually before cropping with the platform engine's `render` command selected in SKILL.md, or an available host PDF tool. For composite vector figures, render the full region rather than extracting only the largest embedded raster. Capture multipage figures/tables in ordered parts. Preserve panel letters, axes, units, legends, scale bars, annotations, table headers, footnotes, and captions. If a complete crop is uncertain, show the full page and identify the relevant region.

For web papers, use the actual publisher/source figure or a faithful source screenshot available through the host. Inspect it and retain a traceable locator. Do not generate, redraw, recolor, or reconstruct a figure and label it as the paper's original. If an original is unavailable, state **Original image unavailable** in that item, give the reason and available locator, and limit the explanation to accessible text/captions. Missing visual access must not be labeled verified.

The bundled renderer uses one-based page numbers and unrotated PyMuPDF page coordinates, with a top-left origin and points as units. Confirm coordinates using its full-page output and source-map bounds; for another host tool, check that tool's coordinate convention. Rotation is normalized in memory only; the source PDF is unchanged. The manifest records PDF fingerprint, page, bounding box, DPI, and path; multiple named crops merge into the same manifest. Rendering a PNG does not establish visual inspection: use `not_visual_checked` until it has actually been inspected.

For saved notes, store source images within the output directory and embed them as, for example:

```markdown
### Figure 2 — Does the effect hold in an independent cohort?

![Original Figure 2, panels a–f](assets/figures/fig-2.png)

Source: Figure 2, PDF page 5, panels a–f and original caption; source block P0005.

#### Why was this done?

Explain the question left open by the preceding result.
```

Use the actual paper's numbering, page, coverage, path, and source ID; the example is only a format. In chat, use a native image display or a renderable absolute local path. If a table is too dense to read at once, include a complete original plus useful enlarged regions. An optional transcribed table supplements the original and must be checked against it.

## Efficient image handling

Locate needed figures/tables from available text/source maps, then batch their known page numbers in one engine `render --pages` call. Use the default 144 DPI first; increase it only if labels or details are unreadable. A clear, inspected complete page is a valid original image and avoids an unnecessary render–crop–inspect loop. Crop when surrounding text makes the image hard to read, an enlargement is needed, or the user requests it; confirm the bounding box first.

Reuse matching-source images and inspection records, processing only missing/changed items. A file's presence or manifest state alone is not proof of visual inspection. Pages containing several figures may share one original page image with clear figure locations; link subsequent brief cross-references to it. Every individually explained item still has its original image in its own section. Do not extract all embedded images, rerender completed pages, or refine harmless whitespace just for presentation. Essential labels, captions, coverage, and legibility always take precedence.

## Teach a reading operation

The aim is to let the reader use the figure, not only recognize its labels. Open with the scientific question and the main source-supported answer, then explain how the visual supplies that evidence. Use the reader's stated background and observed difficulties; define prerequisites at the point of use without a mandatory questionnaire or a general textbook detour.

For decisive, unfamiliar, or easily misread visuals, cover the functions below. They are explanation requirements, not mandatory separate headings or a fixed word count. Simple visuals can combine them; quick/focused requests retain their scope. Group repetitive panels by scientific question while naming coverage. Include supplementary evidence when it determines the judgment.

### Establish the question and experimental setup

State the claim or alternative being tested and the figure's role: main effectiveness evidence, failure diagnosis, exploratory behavior, proposed explanation, ablation, robustness, or illustration. Use the role supported by the methods and text. Identify the relevant data, interventions, controls, sample/repeat units, and aggregation. Explain whether a point represents an individual sample, a bin average, a cohort, a separately trained setting, or another unit. Separate training, inference, and evaluation when that distinction matters. Locate missing details in methods or supplements; report unresolved details at the relevant inference.

### Decode an element before describing the pattern

Explain the panels, axes/units, colors, symbols, scales, and the quantity each visual element encodes. Distinguish measured values, model probabilities, counts, and derived metrics. Give a worked reading of a representative cell, point, bar, region, or connection for a decisive or unfamiliar item. State how its position, height, color, or endpoints determine its meaning. Choose an element that resolves the likely confusion; there is no quota of examples.

For a heatmap, make a sentence of the form “at x = ..., y = ..., this color represents ... under ...” using the paper's actual definitions. Explain the grouping or averaging when specified; do not infer normalization from appearance. For dual-axis plots, map each series to its own axis and distinguish overlaid from stacked bars. Explain inset/zoom panels and unusual scales, including scientific notation, before comparing values. For diagrams, trace a meaningful input → operation → output path and define what an arrow denotes. For experimental images, explain the relevant region, scale, condition, and measurement rather than inventing a numerical cell reading.

Use exact paper values where available and mark graph-read values as approximate. Added numerical examples must be explicitly labeled illustrative and kept distinct from paper measurements. If the original is unreadable, improve the view or state the gap; do not invent a value to complete an example.

### Explain reference geometry and special features

When a diagonal, baseline, threshold, shaded band, or highlighted region is central to the explanation, define the relation it represents and why it helps this comparison. A diagonal often means equal coordinate values; its scientific meaning follows from those variables. Distinguish an ideal calibration line, identity line, self-comparison, and other constructions. Explain on-reference versus off-reference positions and what width, distance, or direction means when relevant.

Check whether sorting, selecting an argmax, binning, or normalization creates part of the visible pattern. Separate this expected construction from the informative result. For example, selecting a maximum can make its own position prominent; a claimed neighboring spread requires reading the neighboring values, not just pointing at the maximum. Explain the feature's use before using it as evidence.

### Walk through the comparison and inference

Specify what to hold fixed and what to compare: same x across conditions, matched samples before/after, a row against its baseline, or another valid contrast. Read that comparison concretely, then summarize the relevant panels and any exceptions. Check common color scales, metric directions, denominators, uncertainty, and aggregation. Avoid cross-panel subtraction or ranking when conditions or scales differ.

Connect observation → supported interpretation → consequential boundary. Identify factors changed together and what the controls isolate. A correlation supports an association; a mechanism or component attribution needs its corresponding evidence. Distinguish an author interpretation from a directly observed result and an analyst proposal. Report statistical significance only when established by the paper's analysis.

### Place it in the research argument

Explain what this evidence adds and which question remains. Some figures develop a parallel contribution or an exploratory explanation rather than derive the next method. State that role plainly; do not manufacture a causal sequence to make every figure appear necessary. A composite overview may mix task definitions, observations, and a proposed solution: identify those functions, introduce needed definitions before results, and return to the interpretive parts when supported. Reading order can differ from figure-number order with clear cross-references.

## Tables

Show the original table image first, retaining headers, units, caption, footnotes, and all multipage parts. Start with what the rows and column groups represent. Define abbreviations and metric directions before interpreting rankings; check bold/underline/color rules rather than assuming their meaning.

Reconstruct how a reported number is produced. In a model evaluation, trace training data and objective → trained model/setting → test data → prediction/score → metric and aggregation. Identify which rows denote one shared model, separate models per dataset, or only an aggregate when the source specifies this. In other study types, use the corresponding cohort/intervention/measurement or method/property mapping. Explain a representative row/cell and a matched comparison. Distinguish performance values from parameter counts, training settings from test results, and held-out evaluation from claims about pretraining exposure.

When method labels describe different dimensions, explain their relationship before comparing them: a learning objective, a parameter-update scheme, training-data composition, and output format can be independent choices. Avoid making an artificial hierarchy or treating a change on one dimension as evidence of a change on another.

Inspect the comparison's changed factors. If training data and architecture/output format change together, the result measures their combined configuration; an isolated contribution needs a matched control. Identify such a control only after checking the relevant evidence. When multiple output scores feed one metric, locate the selection, combination, or separate-reporting rule. If unavailable, state that missing link; do not supply an assumed mean, product, minimum, or independence assumption.

State what improves, relative to which baseline, under which conditions, and with what important exception. Best among joint methods, best within a family, and best across all rows are different comparisons. Distinguish percentage points from relative changes; keep task-specific results separate from weighted or macro averages. Differences in budget, units, or uncertainty can limit direct ranking. Explain the affected comparison rather than adding a generic warning.

## Equations

Start with the problem and the concrete operation: what goes in, what the expression computes, what is adjusted or estimated, and why that serves the method. Then map the symbols, indices, units/dimensions, sums/expectations, normalization, and constraints to that operation. For an unfamiliar objective or estimator, walk through a small sample or term when it helps; do not lead with a dense symbol glossary alone.

For example, an explicitly illustrative negative-log-loss calculation can show that a target token assigned probability 0.2 has loss about 1.61, while probability 0.8 gives about 0.22 (natural logarithm). This teaches the incentive; these are demonstration values, not paper results. State what a probability is a probability of: a generated token, a correct answer, or another event. Explain what a summation index ranges over and what is included or masked. Keep observed/target values distinct from model outputs where the equation requires it.

Distinguish learned parameters, chosen hyperparameters, training objectives, estimators, and evaluation metrics. For a regularized loss, explain the base objective and the added term, including what setting its coefficient to zero removes. A masked direct loss and a shared parameter update are different operations; discuss indirect effects when they affect the interpretation. For non-training equations, adapt the operation to the actual estimator, physical relation, or theorem rather than imposing a training story.

Distinguish original transcription, equivalent rearrangement, and added derivation; state additional assumptions. Similar-looking symbols do not prove equivalence. Do not confuse a training objective, estimator, and evaluation metric. Numerical checks are not general proofs.

Use `$...$` / `$$...$$` in Markdown. This bundle's HTML does not typeset LaTeX, so show important equations as original source crops with explanations. If transcription is unclear, retain the image and uncertainty rather than guessing exponents, symbols, or subscripts.

## Reader-transfer completion check

Before delivering an explanation, inspect the actual text as if the reader had to perform the reading unaided:

- Can they decode a representative element and say what population, condition, or computation it represents?
- Can they explain the use of a salient reference feature and distinguish a constructed pattern from the substantive finding?
- Can they repeat the intended comparison, identify the changed factors, and state which conclusion it supports?
- Can they place this evidence in the paper's argument and separate observation, interpretation, and an unresolved link?
- For an equation, can they follow a sample or term through the operation and explain what changing it does?

Apply only relevant questions; this is an internal review, not a compulsory user quiz. If a step is missing, revise that step without redoing successful source work. If the source leaves it unresolved, explain the specific gap and its consequence. A structural validator checks formatting and records; it cannot establish reader understanding. When the reader says an explanation is unclear, identify the missing concept or reading operation and rewrite that passage; repeating the caption or trend is insufficient.
