---
description: Guidance for drafting, revising, and auditing the
  Conclusion section of an academic paper. Synthesize the actual
  contribution and findings, preserve evidence boundaries, and avoid
  repeating the Introduction or introducing unsupported claims.
name: conclusion
---

# Conclusion --- Section Skill

## 1. Purpose and Scope

This skill guides the drafting, revision, and review of the Conclusion
section of an academic paper.

The Conclusion should leave readers with a precise understanding of what
the paper contributes, what the results establish, and what remains
unresolved. It is a synthesis of the completed work, not a second
Introduction, an additional Related Work section, or a place to
introduce new technical details.

Write the Conclusion after the Methodology and Experiments are
sufficiently stable. Follow the root `SKILL.md` and preserve the current
manuscript's actual contributions, results, and limitations.

Do not invent findings, strengthen claims beyond the evidence, or add a
new contribution that was not established in the paper.

## 2. Required Context and Evidence

Before drafting or revising the Conclusion, inspect the available
materials:

-   The final or latest Introduction and its contribution statements.
-   The Methodology and the actual technical components proposed.
-   The main experimental results and relevant supporting analyses.
-   Any limitations that are acknowledged or clearly demonstrated.
-   The target venue's length and formatting requirements.

Use the manuscript's verified content as the primary source. The
Conclusion should reflect the final method and final results, not an
earlier plan or an abandoned design.

If the experiments are incomplete or key results remain uncertain, do
not present them as established findings. Ask for the missing
information or mark the relevant claim as unresolved.

## 3. Recommended Workflow

### Step 1: Recover the paper's central message

Summarize, for internal use:

-   The problem addressed.
-   The principal methodological contribution.
-   The most important empirical findings.
-   The main qualification or limitation, if material.

Keep this summary consistent with the final manuscript. Do not simply
copy the Introduction's wording.

### Step 2: Select the findings worth retaining

Prioritize findings that answer the paper's main research question and
support its stated contributions.

Use the main results and, where relevant, ablations or additional
analyses. Do not enumerate every dataset, metric, module, or experiment.
Select only the evidence needed to convey the paper's overall outcome.

### Step 3: Draft a concise synthesis

A common structure is:

1.  Restate the problem and the proposed approach briefly.
2.  Summarize the central contribution without repeating the full
    contribution list.
3.  Report the main empirical or theoretical takeaway at the level
    supported by the evidence.
4.  Mention a meaningful limitation or future direction when
    appropriate.

This is a flexible guide, not a mandatory four-sentence template. Adapt
it to the paper's contribution type, findings, and venue conventions.

### Step 4: Check every claim against the manuscript

For each statement, identify its support in the Methodology, theorem or
analysis, experiment, or explicitly stated limitation.

Distinguish: - What the method is designed to do. - What is formally
established. - What experiments demonstrate. - What remains a hypothesis
or future direction.

Remove or qualify claims that cannot be traced to the paper's evidence.

### Step 5: Remove duplication and unnecessary detail

Avoid repeating the full background, literature taxonomy, derivations,
implementation details, or table-by-table results. The Conclusion should
synthesize their implications rather than reproduce them.

Preserve a key qualification when omitting it would make the conclusion
misleading.

### Step 6: Audit consistency with the Abstract and Introduction

The Conclusion, Abstract, and Introduction should describe the same
problem, method, and contribution. Their wording and level of detail may
differ, but they must not make conflicting claims.

The Conclusion can reflect the final experimental evidence more directly
than an early Introduction draft. If the main results changed during
revision, update the summary claims accordingly.

## 4. Core Writing Rules

### 4.1 Summarize the completed work, not the original plan

Describe the method and results that are actually present in the final
paper. Do not preserve planned contributions that were later removed,
failed to materialize, or were not evaluated.

If the final method differs from the original proposal, summarize the
final method.

### 4.2 Be concise but substantive

Avoid generic endings such as "The results are promising and future work
is needed" when they do not convey what was learned.

A concise Conclusion should still identify the central technical
contribution and the most important supported outcome. Remove details
that readers can easily retrieve from the preceding sections unless they
are essential to the overall takeaway.

### 4.3 Do not overstate empirical or theoretical findings

Match the strength of the wording to the evidence.

-   A result observed on tested datasets supports a conclusion scoped to
    those experiments, not universal superiority.
-   An ablation supports a claim about the tested variant and setting,
    not necessarily a universal causal explanation.
-   Empirical performance does not establish a theoretical guarantee.
-   A theorem supports only the conclusion implied by its assumptions
    and proof.
-   A favorable aggregate ranking does not mean the method wins on every
    dataset or metric.

Use precise qualifiers when results vary across conditions. Do not hide
meaningful negative or mixed findings if their omission would
misrepresent the work.

### 4.4 Do not introduce new results or technical claims

The Conclusion should not introduce an experiment, theorem, numerical
result, mechanism, or contribution that has not been established
elsewhere in the manuscript.

If an important finding is missing from the body, revise the relevant
section and verify the evidence before including it in the Conclusion.

### 4.5 Handle limitations and future work deliberately

Include limitations or future directions when they are meaningful and
appropriate for the paper. They should follow from the current method,
experiments, or clearly identified scope boundaries.

Avoid generic future-work statements that could be attached to any
paper. Do not frame an unaddressed core requirement as a completed
achievement.

Do not add speculative limitations merely to appear cautious. State
known limitations accurately and keep future directions realistic and
connected to the current work.

### 4.6 Avoid repeating the Introduction

The Introduction establishes the problem's importance, reviews key
limitations, motivates the work, and previews the contributions.

The Conclusion looks backward at the completed work and synthesizes what
it contributes and what the evidence shows. Reuse essential terminology
for consistency, but do not repeat the Introduction paragraph by
paragraph.

### 4.7 Keep the tone measured and specific

Use direct academic language. Avoid promotional adjectives, broad claims
of novelty, and phrases such as "revolutionary," "solves the problem
completely," or "achieves universal superiority" unless an unusually
strong and clearly established basis exists.

Prefer a precise description of the contribution and findings over
self-evaluative language.

## 5. Cross-Section Consistency Checks

### Conclusion ↔ Introduction

The central problem and contributions should match. Do not claim a
contribution in the Conclusion that the Introduction or Methodology does
not establish.

### Conclusion ↔ Methodology

Describe the method accurately. Do not summarize a planned or abandoned
mechanism as part of the final approach.

### Conclusion ↔ Experiments

Every empirical statement must match the reported results. Preserve
important qualifications about datasets, metrics, comparisons, and
limitations.

### Conclusion ↔ Abstract

Both sections should summarize the same final contribution and main
findings. The Abstract may be more structured around problem, method,
and results; the Conclusion may offer a broader synthesis, but their
claims must remain consistent.

## 6. Common Failure Modes

Avoid the following:

-   Repeating the Introduction instead of synthesizing the completed
    work.
-   Restating the contribution list without explaining the overall
    takeaway.
-   Repeating detailed numerical results from every table.
-   Claiming universal superiority from limited experimental evidence.
-   Introducing new results, proofs, or technical claims.
-   Describing planned work as completed work.
-   Presenting empirical observations as theoretical guarantees.
-   Omitting a material qualification that changes the interpretation of
    the findings.
-   Adding generic future work unrelated to the paper's actual
    limitations.
-   Using inflated or promotional language.
-   Allowing the Conclusion to contradict the final Abstract,
    Methodology, or Experiments.
-   Writing the Conclusion before the results are stable and failing to
    update it afterward.

## 7. Output Modes

Adapt the deliverable to the user's request:

-   **Drafting:** produce a concise Conclusion based on the final method
    and verified results.
-   **Revision:** improve clarity, synthesis, and academic tone while
    preserving the claims and evidence.
-   **Claim audit:** map each conclusion statement to its supporting
    section, result, or theoretical argument.
-   **Consistency review:** compare the Conclusion against the Abstract,
    Introduction, Methodology, and Experiments.
-   **Compression:** shorten the Conclusion without removing essential
    contributions, findings, or qualifications.
-   **Limitations and future work:** identify defensible limitations and
    realistic future directions grounded in the current paper.

If key results or final design decisions are unavailable, state what is
needed. Do not fill gaps with assumed findings.

## 8. Final Quality Checklist

Before returning substantive Conclusion work, check the applicable
items:

-   [ ] The Conclusion reflects the final version of the method and
    experiments.
-   [ ] The central problem and contribution are stated accurately.
-   [ ] The main findings are selected for relevance rather than
    exhaustiveness.
-   [ ] Every empirical claim is supported by reported results.
-   [ ] Every theoretical claim stays within the scope of its
    assumptions and proof.
-   [ ] Mixed or qualified findings are not misleadingly presented as
    universal wins.
-   [ ] No new result, proof, mechanism, or contribution has been
    introduced.
-   [ ] The section synthesizes rather than repeats the Introduction.
-   [ ] Limitations and future directions are specific and justified
    when included.
-   [ ] The wording is concise, measured, and technically precise.
-   [ ] The Conclusion agrees with the Abstract, Introduction,
    Methodology, and Experiments.
-   [ ] The length and structure fit the target venue.

Do not mark a claim as verified if the relevant manuscript section or
evidence was unavailable.

## 9. Mentor-Derived Guidance and Evidence Boundaries

The primary source-derived guidance for this module is
`Longlong_Lin_wechat_advice_notes(6).md`, especially Advice 19, which
recommends writing the Abstract and Conclusion after the technically
constrained sections and the Experiments. It advises compressing the
Introduction and the main experimental findings rather than drafting
these summary sections from an early plan.

Advice 9 also emphasizes that reference papers may be used to learn
section structure and paragraph function, but their technical claims,
experiments, and conclusions must be replaced with the current paper's
own content.

These notes do not prescribe a universal sentence count or a fixed
Conclusion template. The workflow and checklists in this skill
operationalize those principles; adapt them to the paper's actual
contribution, evidence, and venue.
