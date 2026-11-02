# Research lineage, readable reasoning, and limitations

Use this reference for whole-paper deep/extend analysis. Adapt to the study type and the user's requested depth. A short summary or focused explanation needs only the lineage and scope necessary to understand its result; do not expand it into a literature review.

## 1. Establish the background and related-work lineage

Read the supplied paper's Introduction and Related Work, including related-work discussion in an appendix when relevant. Identify the earlier approaches that explain the present paper's choices. Organize them by scientific problem or methodological route; chronology is useful only when it explains a change in ideas.

For each consequential route, explain:

- What question or bottleneck it addresses and how the approach works in plain language.
- Which representative cited work anchors it, using the paper's reference identity and a source locator.
- What capability or finding it established, and which remaining condition, assumption, or failure matters here.
- What the current paper inherits, changes, combines, or challenges, and how that relationship motivates a concrete design choice.

Use as many routes and works as the argument requires, with no fixed quota. A compact comparison may help:

| Prior route / representative work | Core idea and what it achieved | Remaining issue relevant here | Relationship to the present paper |
|---|---|---|---|

Explain the mechanism alongside the citation; a list of authors and years is insufficient. Do not describe all prior research as unsuccessful just to create a gap. Distinguish an inherited component, a changed assumption, a new combination, a new empirical finding, and an optimization change.

### Source discipline

Start with the supplied paper's account of prior work. When the cited original has not been read, make that status clear once and attribute substantive comparisons to the supplied paper. Do not present that account as independently verified literature consensus. Broader novelty verification and exhaustive discovery remain outside an ordinary single-paper reading task. Consult a cited original when understanding or checking it is necessary for a requested conclusion; preserve uncertainty if access fails.

If the paper has no separate Related Work heading, reconstruct the lineage from its introduction, discussion, and relevant references. If available text does not establish the lineage, identify the specific missing link rather than inventing predecessors or author intent.

## 2. Explain how the idea follows from the gap

Before detailing modules or equations, connect the prior approach, its relevant limitation, the paper's question, its central idea, and the design that tests it. Explain why the proposed change could address that particular gap. An idea need not follow uniquely from the gap; identify meaningful alternatives when they help explain the authors' choice.

Keep three kinds of explanation distinct: the authors' stated motivation, an analyst reconstruction supported by the design, and an untested hypothesis. A plausible rationale is not evidence of the authors' actual thought process.

For the research storyline, connect each important experiment to a question left by the preceding evidence: whether the method works, where the gain comes from, which alternative explanation is tested, or where transfer fails. Explain a change in research level, such as moving from a mechanism to the downstream value of generated data. State what that later evaluation can establish.

Represent the actual argument, including branches. Distinguish central tests from auxiliary behavioral observations, exploratory mechanisms, and implementation ablations. An interesting intermediate result need not derive the proposed solution; explain its contribution without turning its position in the paper into causal evidence. If a composite figure combines definitions, failure observations, and a proposed method, introduce the definitions when needed and interpret the remaining parts alongside their evidence. A readable teaching order can differ from figure-number order, with explicit cross-references. Where several design factors change together, describe the combined result and locate the control needed for component attribution.

## 3. Write for understanding

Lead with a brief, understandable account of the paper's question, main idea, decisive finding, and consequential boundary. The reader should understand the core argument before encountering extensive evidence records.

- Explain the needed concept at the point of use, preferably through a short concrete example when the concept is unfamiliar. Label added examples as demonstrations.
- Explain method inputs, operations, and outputs before expanding notation. Introduce symbols and assumptions alongside the formula they serve.
- Use a transition when the research question or evidence level changes; do not add a formulaic transition to every paragraph.
- Use diagrams or route comparisons when they clarify dependencies. Distinguish original paper visuals from explanatory reconstructions, and retain the original-image rules.
- Explain each result once, then use concise cross-references. Put hashes, parsing logs, environment inventories, and other operational detail in sources or an audit appendix unless they affect interpretation.

Keep the main narrative proportionate to the reading goal. Detailed figures, formulas, evidence cards, and future plans should develop the argument without replacing its explanation.

## 4. Discuss scientific limitations and applicability separately

After the results and evidence, include an identifiable section on research limitations and applicability. Use the paper's Limitations, Discussion, conclusion, and relevant supplementary material where present, then assess what the actual design supports.

Distinguish:

1. **Author-stated limitations:** summarize what the authors acknowledge, with locations. If no explicit limitation is found in the read material, say that rather than inventing admissions.
2. **Evidence-based analyst assessment:** identify supported concerns about assumptions, controls, measurement, uncertainty, generalization, cost, or validity. Label the source of the judgment and distinguish established problems from unresolved alternatives.
3. **Reading and reproduction gaps:** unavailable code, unread supplements, unclear parsing, missing configuration, or visual-access failures belong in sources/reading records. Promote one into the scientific discussion only when its consequence for a claim or application is explained.

For each consequential scientific limitation, connect **source or observation → affected claim → effect on interpretation or use → needed check**. Explain the condition under which the result is supported and where the extrapolation remains untested. If magnitude or direction is unknown, state what remains unresolved.

For example, missing repeats can limit confidence in a small performance difference; they do not by themselves show that the method is worse. An unavailable implementation limits verification but does not establish a flaw in the algorithm. A missing control matters when it prevents attributing a gain to the claimed component. A narrow data setting constrains a specified transfer claim, rather than making the whole paper invalid.

A table is useful when several issues need comparison:

| Limitation and origin | Evidence / source | Affected conclusion or condition of use | What would resolve the uncertainty |
|---|---|---|---|

Do not fill a quota, force criticism, or repeat generic caveats. Retain real boundaries even when using concise, contribution-led writing. Critique an inference at the level its evidence warrants. Keep the supported contribution clear alongside the conditions needed to use it.

## 5. Semantic completion check

Before delivering a whole-paper deep/extend analysis, inspect the actual explanation, not only its headings:

- Can the reader explain the relevant prior routes, their established value, and the specific unresolved issue?
- Is the connection from that issue to the current hypothesis or design explicit and source-grounded?
- Can the reader explain how the main modules work and why the experiments follow in their stated order?
- Are author-stated limitations distinguishable from analyst assessment and unavailable reading material?
- Does each consequential limitation identify an affected claim or condition of use, rather than only list something missing?
- Are prior-work statements, original findings, analyst reconstructions, and proposed future work clearly distinguished?

Repair missing reasoning, not just missing section titles. If a source cannot establish a needed link, disclose that link as unresolved. The bundled structural validator checks records and formatting, not these semantic requirements.
