---
name: norman-paper-reading
description: "Summarize or closely read specified scientific papers, reconstruct study design, inspect original figures and equations, and connect evidence to future research insights and prioritized plans. Use for PDFs, DOIs, arXiv links, supplied paper text, or a small set of named papers; supports quick summaries, deep analysis, research extension, and requested guided reading or parallel translation."
metadata:
  version: "1.4.0"
  author: "N同学"
---

# norman-paper-reading

Explain how prior research leads to the paper's question and design, what its evidence establishes, and where its conclusions apply. Whole-paper analysis normally includes future research insights and a prioritized next-step plan, after the paper itself is understood. Follow the user's language, scope, and delivery location; English instructions do not require English reports. Use Chinese only when language cannot otherwise be inferred or configured. Start from the supplied paper without a questionnaire; use relevant known background or assume research experience with limited familiarity with this field.

## Select the engine for the current system

This fork supplies the updated workflow as readable files and keeps the upstream compiled helpers unchanged. Read this SKILL.md and its linked local references/templates directly; these files take precedence over the older instructions embedded in guide/read. Derive the skill root from this file. Use norman-paper-reading.exe on Windows x64, norman-paper-reading-macos-arm64 on Apple Silicon, or norman-paper-reading-macos-x64 on Intel Mac, with a quoted absolute path. Use PowerShell's & on Windows. The native helpers include their runtime; no system Python or first-launch dependency install is needed.

Windows examples:

```powershell
& "<skill-root>/norman-paper-reading.exe" version
& "<skill-root>/norman-paper-reading.exe" extract "<paper.pdf>" --out "<output>/source"
& "<skill-root>/norman-paper-reading.exe" render "<paper.pdf>" --pages 1,3-5 --out "<output>/assets/pages"
& "<skill-root>/norman-paper-reading.exe" validate "<output>/reading-note.md" --mode deep --evidence "<output>/evidence.json" --source-map "<output>/source/source_map.json"
& "<skill-root>/norman-paper-reading.exe" reader "<output>/reading-note.md" --lang zh-CN --out "<output>/reader.html"
```

macOS Apple Silicon examples (use `norman-paper-reading-macos-x64` for Intel):

```bash
"<skill-root>/norman-paper-reading-macos-arm64" version
"<skill-root>/norman-paper-reading-macos-arm64" extract "<paper.pdf>" --out "<output>/source"
"<skill-root>/norman-paper-reading-macos-arm64" render "<paper.pdf>" --pages 1,3-5 --out "<output>/assets/pages"
"<skill-root>/norman-paper-reading-macos-arm64" validate "<output>/reading-note.md" --mode deep --evidence "<output>/evidence.json" --source-map "<output>/source/source_map.json"
"<skill-root>/norman-paper-reading-macos-arm64" reader "<output>/reading-note.md" --lang zh-CN --out "<output>/reader.html"
```

Each subcommand accepts `--help`. Use `render --pages N --bbox x0,y0,x1,y1 --name fig-N` for a checked crop. A nonzero exit code means failure. Preserve the source PDF and retain the source, figure, evidence and output-attribution rules below. Native helpers supply deterministic work; the model supplies scientific judgment. This documentation update claims no new native runtime verification.

## Choose the mode

| Intent | Mode | Major report headings |
|---|---|---|
| Summarize, main points, worth reading, quick overview | quick | Research question; Core design; Key results; Evidence gaps; Future research insights and next steps; Reading priority |
| Analyze this paper, close reading, detailed explanation, journal club, whole-paper understanding | deep | Core assessment and scope; Research background, related work and motivation; Full research storyline; Key design decisions; Figures/tables or key theorems; Necessary equations; Evidence cards; Research limitations and applicability; Future research insights; Next-step research plan; Sources and reading gaps |
| Reproduce, apply to my project, future research planning | extend | Necessary deep evidence; Future research insights; Transfer conditions; Reproduction checklist; Research action cards; Prioritized research roadmap |
| One figure, equation, or passage | focused | Requested item; Necessary context; Explanation; Evidence boundary |

An unqualified summary uses quick; an unqualified whole-paper analysis (including “分析这篇文章”) or close reading uses deep. Include a compact insight and next step in quick, and distinct future-insights and research-plan sections in deep. Explicit research planning uses extend. Respect requests for summary only, no extensions, or strict brevity; focused explanations do not automatically acquire a whole-paper plan. Preserve explicit or established mode/coverage in follow-ups. Speed changes execution, not requested completeness. Guided reading, full parallel translation, and paper comparison are additions only on request. General literature discovery and unspecified field reviews do not trigger full close reading.

## Fast start and selective loading

Quick text-only summaries need only this entry point. Do not pre-load every reference, template, example, or script source, inspect unrelated folders, or create a profile. Read each applicable reference once:

- [reading-workflow.md](references/reading-workflow.md): deep/extend workflow and input fallbacks.
- [research-story-and-limitations.md](references/research-story-and-limitations.md): required for whole-paper deep/extend; reconstruct related-work lineage, explain the origin of the idea, and distinguish scientific limitations from reading gaps.
- [figure-and-equation-reading.md](references/figure-and-equation-reading.md): explaining original visuals or equations.
- [evidence-and-research-cards.md](references/evidence-and-research-cards.md): saved evidence JSON or research actions.
- [future-research-planning.md](references/future-research-planning.md): default future insights and plans for deep analysis; detailed roadmaps for extend. Quick uses the compact guidance below without loading this reference.
- [paper-types.md](references/paper-types.md): specialized study-type checks.
- [output-and-brand.md](references/output-and-brand.md): saved reports, HTML, and detailed output rules.
- [teaching-and-comparison.md](references/teaching-and-comparison.md): requested teaching, parallel translation, or comparison.

Reuse extracted text, source maps, inspected images, and evidence only after checking source identity/version, fingerprint where available, and coverage. File existence proves neither freshness nor inspection. Process missing/changed material and keep stable IDs. Extract required PDF coverage once; locate passages from text/source maps rather than repeatedly dumping the full extraction. quick/focused can use selected pages; whole-paper deep requires the relevant full main text.

Batch independent reads/tools where supported, keeping dependencies sequential. Batch known figure pages in one render at default 144 DPI; use a readable, inspected full-page original before spending time on crops. Render only needed pages; increase DPI/crop to solve an actual readability issue. Do not export all embedded images or render every text-readable page by default.

Use the supplied source before external searches. Read supplements or code when they affect the requested conclusion, not as a universal startup task. Broader novelty searches, repository audits, unrelated OCR, full translation, and reproduction runs require a task need or request.

For lengthy deep/extend work, give a brief source-grounded overview in commentary once sufficient text is read: question, approach, main reported result, and scope. Label results not yet visually checked as author-reported. Continue the required analysis in the same task without waiting for confirmation; the overview is not completion. Do not delay it for image refinement, JSON serialization, or HTML packaging.

## Sources and workspace

Confirm title, version, accessible coverage, and relevant supplements. Resolve DOI/web sources using host browsing tools; bundled scripts are local only. Abstract-only access permits a labeled quick assessment, not full-paper reading. Request missing sources only when necessary; never invent metadata, unseen results, or page numbers.

Chat needs no output bundle. Save when requested or already authorized, protecting existing user edits. Use [reader-profile-template.yaml](assets/reader-profile-template.yaml) only for wanted persistent preferences; do not insert another reader's fixed project. Use the bundled platform engine and quoted path arguments; dependencies are included.

`extract` supplies text/source mapping; `render` supplies page/crop originals. Existing host capabilities may already provide what is needed. Preserve the source PDF.

## Analysis

Connect question → design → evidence → boundary rather than paraphrasing every section. Select units by contribution: experiments/figures, method modules/validation, theory assumptions/proofs, or review scope/literature. deep covers the full main storyline, relevant main figures, and decisive method details. quick needs decisive summary checks, not a full figure report or derivation.

For whole-paper deep/extend, explain **research background, related work and motivation before the methods**, then give a distinct **research limitations and applicability** discussion after the evidence. A generic background sentence, reference list, or list of missing implementation details does not complete these tasks. Follow [research-story-and-limitations.md](references/research-story-and-limitations.md); scope explicit brevity/summary-only requests accordingly. Quick/focused explanations use only the context and limitations needed for their requested conclusion.

Make the reasoning readable: explain what a mechanism does before introducing its name or equation; define unfamiliar terms when first needed; connect a major design choice to the gap it addresses and a major experiment to the claim it tests. A short flow or comparison can clarify the main thread, labeled as an analyst reconstruction when appropriate. Keep detailed evidence IDs and operational audit records from interrupting that thread. Compact future plans should build on, and not crowd out, understanding of the paper.

- **Design decisions (D01):** problem, choice, sourced author rationale or labeled analyst inference, feasible alternative, possible effect. Do not invent motives or fill quotas.
- **Claims/evidence (C01/E01):** source, observation, conditions, support, limits. Connections support, limit, contradict, or give mixed support. Separate facts, author interpretations, analyst inferences, and hypotheses. Venue/citation counts do not establish truth or novelty.
- **Actions (A01, deep/extend):** grounded gap, question, hypothesis, method/data, controls, supporting/weakening outcomes, resources, priority, and a concrete deliverable. Unknown thresholds/sample sizes require estimation. Reuse necessary deep evidence rather than repeat a report. Proposed experiments and virtual reconstruction are not completed reproduction.

Record locations, observations, and IDs while reading; use the same checked records for notes/JSON/HTML. Explain results fully once, then cross-reference their IDs. Define terms at first use and expand only when needed. Explain decisive methods clearly; add pseudocode or derivations when necessary or requested.

## Future research insights and planning

Turn supported contributions and consequential evidence gaps into a small set of useful research directions. Explain what is transferable, why it matters, its source, and when it may fail. Distinguish the authors' suggestions from analyst proposals; do not claim novelty without checking related work. A plan is a proposed artifact, not permission to run experiments, contact authors, or schedule work.

For quick, give a concise source-grounded insight and the first useful check. For deep/extend, follow [future-research-planning.md](references/future-research-planning.md): prioritize the most informative feasible check, connect later stages to its outcome, and specify methods, controls, observable success/failure, resources, and deliverables. Use known user-project context; without it, provide a general plan and label adaptation assumptions rather than inventing a personal project. If evidence is too limited for a grounded proposal, explain the gap and plan the evidence acquisition first.

## Original figures, tables, and equations

Every individually explained figure/table gets its **original image directly below its heading**, before analysis, plus source locator and panel coverage. Inspect a full page before cropping. Preserve panels, axes/units, legends, scale bars, annotations, captions, table headers/footnotes, and multipage parts. Recreated charts are not originals. If an image cannot be obtained or viewed, disclose that locally; rendering alone is not verification.

For figures: why → method → reading cues → observations → support/boundary → next question. Cover relevant panels and explain omissions; group repetitive panels with explicit coverage. Use compact explanations for simple items and detail for decisive ones.

For necessary equations: purpose, symbols/units, operations, intuition, assumptions, method role, limits. Separate original transcription, rearrangement, and added derivation. Preserve unclear formulas as source crops instead of guessing. Numerical checks are not general proofs.

## Deliver and verify

Use one `#` title, prominent `##` mode sections, `###` figures/tables/cards, and `####` substantial subquestions. Translate headings into the report language. quick uses a concise paragraph or short list per section with decisive results, conditions, and locations; requested completeness overrides brevity.

For saved deep/extend, adapt [reading-note-template.md](assets/reading-note-template.md), retain relevant sections, and include evidence JSON grounded in source-map blocks. Saved images live inside the output directory with relative links; chat uses native display or renderable absolute paths. Default to Markdown. Build HTML via the bundled `reader` command only when requested and content/assets are ready; set `--lang` to the report language. Navigation is English and LaTeX is not typeset; important formulas need original crops or clear text.

Check key numbers, formulas, statistical units, image completeness, and inference boundaries while reading/writing. At completion, reconcile scope and unresolved/high-risk claims. Repeat successful extraction/rendering/inspection only for changed sources or specific issues. Run the bundled `validate` command once after saved content/assets are ready, repairing and rerunning affected checks as necessary. Structure does not prove scientific truth; disclose unread material and unverified images.

For whole-paper deep/extend, also apply the semantic completion check in [research-story-and-limitations.md](references/research-story-and-limitations.md): the reader must be able to trace prior approaches to the gap, the proposed idea, its tests, and its supported scope. A structural validator passing does not establish this coverage.

Package provenance: **Norman Paper Reading / norman-paper-reading**; creator **N同学**, also known as **耐心的N同学**. Keep this provenance in the skill documentation. Preserve the original papers' authors, affiliations, captions, references, and methods.

## Output attribution

Do not append skill-author credits, social-media accounts, promotional signatures, or bilingual watermarks to chat responses, reading reports, Markdown, or HTML by default. Add an attribution footer only when the user explicitly requests one, following their requested wording and language. This applies to every analysis mode and conceptual follow-up.

The reading-note template and reader profile default to no attribution footer. If the legacy bundled HTML reader adds a creator footer automatically, remove that footer from the generated HTML before delivery; use `--no-brand` where available and inspect the resulting file because the old engine may still append its bilingual footer. Keep paper citations and source attribution intact.

Legacy package metadata and validation records describe the original distribution, not the current output policy. If a bundled validator objects only to the missing creator watermark, treat that specific check as obsolete; do not reinsert the footer to satisfy it. Address all unrelated validation findings normally.
