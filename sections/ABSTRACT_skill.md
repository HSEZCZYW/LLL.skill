---

# Abstract Writing Skill

## 1. Purpose and Scope

Help researchers produce concise, self-contained, technically accurate abstracts that communicate the central problem, proposed approach, and most important findings of an academic paper.

An abstract is a compressed representation of the entire paper, not merely a shortened Introduction. Its purpose is to help readers understand what the paper investigates, what it contributes, how its approach addresses the problem, and what evidence supports its conclusions.

This skill supports:

- Drafting an abstract from a complete manuscript.

- Diagnosing weaknesses in an existing abstract.

- Revising structure, technical descriptions, and academic prose.

- Shortening an abstract to meet a word or character limit.

- Checking factual consistency between the abstract and the rest of the paper.

Do not turn every abstract task into a full-paper rewrite. Inspect only the material needed to complete the requested task reliably.

## 2. Core Principles

### 2.1 Ground every claim in evidence

- Use the current manuscript, verified experimental results, confirmed theoretical statements, and explicit author instructions as the primary sources of truth.

- Do not invent experimental results, theoretical guarantees, implementation details, comparisons, or research contributions.

- Do not treat an intended contribution as a demonstrated result.

- Do not claim that an experiment, proof, or evaluation has been completed unless the available evidence supports that statement.

- When important information is missing or contradictory, flag the issue instead of silently resolving it.

- If a claim is only partially supported, narrow its scope or qualify its wording.

### 2.2 Represent the entire paper faithfully

The abstract must agree with the paper's actual problem definition, proposed method, technical mechanisms, and reported findings.

- Preserve the technical meaning of the manuscript.

- Use the same method names, terminology, and important distinctions as the main text.

- Do not introduce a new contribution solely to make the abstract more attractive.

- Do not describe a component as a theoretical guarantee unless the paper establishes that guarantee.

- Do not imply that an empirical observation establishes a causal mechanism without supporting evidence.

### 2.3 Prioritize information over a fixed template

Use a coherent argument as the organizing principle, not a mandatory sentence sequence.

- Select information according to its importance to the paper's central contribution.

- Give more space to the most consequential problem, mechanism, or finding.

- Do not force every abstract to contain the same number of limitations, components, contributions, or results.

- Do not impose a fixed paragraph structure or a predetermined number of sentences.

- Adapt the abstract to the research task, contribution type, available evidence, and target venue.

### 2.4 Improve reasoning before polishing wording

When an abstract has a substantive weakness, address the underlying issue first.

For example, if the stated research gap does not correspond to the proposed method, rewriting individual sentences will not solve the problem. Identify the mismatch and determine whether the abstract or the underlying manuscript needs clarification.

## 3. Evidence Inspection

Before drafting or substantially revising an abstract, inspect the relevant parts of the manuscript.

| Information to extract                     | Primary evidence                              |
| ------------------------------------------ | --------------------------------------------- |
| Research task and problem definition       | Introduction and problem formulation          |
| Research gap and existing limitations      | Related Work and Introduction                 |
| Proposed approach and key mechanisms       | Methodology and algorithm descriptions        |
| Theoretical properties and guarantees      | Formal statements and proofs                  |
| Experimental scope and evaluation protocol | Experimental setup                            |
| Main empirical findings                    | Results tables, figures, and verified records |
| Target length and formatting requirements  | User instructions and venue guidelines        |

The Introduction provides useful context, but it is not sufficient evidence for every abstract claim. Verify method descriptions against the Methodology and empirical claims against the actual results.

For substantive drafting or revision, build a compact internal claim ledger when useful:

| Candidate claim          | Supporting evidence             | Status                      |
| ------------------------ | ------------------------------- | --------------------------- |
| Central research problem | Relevant manuscript passage     | Verified / unclear          |
| Proposed mechanism       | Method description or algorithm | Verified / unclear          |
| Theoretical guarantee    | Theorem and proof               | Verified / unclear / absent |
| Performance claim        | Experimental results            | Verified / unclear / absent |

Do not require a claim ledger for trivial wording edits. Use it when the abstract contains multiple technical claims or when evidence consistency is uncertain.

## 4. Abstract Construction Workflow

### Step 1: Identify the central research message

Determine what readers should understand after reading the abstract.

Identify:

- The task or problem being addressed.

- The most important unresolved limitation.

- The central idea of the proposed approach.

- The evidence that most convincingly supports the contribution.

Do not begin by listing all modules or contributions. First establish the paper's central message.

### Step 2: Select the essential information

Retain details that help readers understand the problem, distinguish the proposed approach, or assess its significance.

Remove details that are already implied by the context, repeat another claim, or belong primarily in the Methodology or experimental analysis.

A useful test for each candidate sentence is:

**What essential information would readers lose if this sentence were removed?**

If the answer is unclear, reconsider whether the sentence deserves space in the abstract.

### Step 3: Construct the argument

A flexible default progression is:

1. **Task and context:** Identify the research problem and its relevance without lengthy generic background.

2. **Unresolved limitation:** Explain the specific issue that motivates the work.

3. **Proposed approach:** Introduce the method and explain its central mechanism or design.

4. **Supporting evidence:** Report the most important theoretical or empirical findings.

These functions may be combined, reordered, or omitted when the paper's contribution warrants a different organization.

For example, a theory-oriented paper may emphasize a formal guarantee, while a systems paper may prioritize algorithmic efficiency and scale. A learning-based method may need to explain how its central components address a particular modeling limitation.

Do not force a paper into the default progression if doing so obscures its actual contribution.

### Step 4: Explain the method through mechanisms

When describing a proposed method:

- Introduce the method name when it helps identify the contribution.

- Explain what the key mechanism does and why it is relevant.

- Describe the relationship between major components when that relationship is important.

- Prefer a concrete explanation of the mechanism over a list of architectural components.

- Avoid implementation details that do not materially distinguish the approach.

If the method contains several components, select those essential to understanding the central contribution. Do not summarize the entire Methodology section.

### Step 5: Select and report the strongest evidence

Choose results according to their relevance and evidential strength.

Possible evidence includes:

- A proven theoretical property or approximation guarantee.

- A representative performance improvement.

- A meaningful efficiency or scalability result.

- An evaluation across relevant datasets or experimental settings.

- A verified result that directly supports the paper's central claim.

Use numerical results when they provide meaningful additional information and are available in the manuscript. Do not require numerical results in every abstract.

When reporting numerical improvements:

- Verify the value against the reported results.

- Distinguish absolute differences from relative percentage improvements.

- Identify the relevant metric and comparison when needed.

- Avoid selecting a favorable result that misrepresents the overall evaluation.

- Do not claim universal superiority when performance varies across datasets, metrics, or settings.

Use broad statements such as "improves performance" only when the underlying evidence supports them. Prefer a more specific statement when a verified result materially strengthens the abstract.

### Step 6: Draft and refine the prose

Write concise, natural academic English.

- Give each sentence a clear communicative purpose.

- Make the relationship between the problem, method, and evidence easy to follow.

- Remove redundant modifiers and repeated information when doing so preserves technical meaning.

- Replace vague descriptions with precise explanations of the task, mechanism, or finding.

- Use transitions to clarify genuine logical relationships.

- Avoid unnecessarily elaborate wording, repetitive sentence openings, and mechanical academic phrasing.

Do not optimize individual sentences at the expense of the abstract's overall argument.

### Step 7: Apply venue and length constraints

Follow explicit word limits, character limits, formatting rules, and author instructions.

- Check the applicable venue guidelines when available.

- Do not assume that every venue uses the same abstract format.

- Include citations, equations, abbreviations, or keywords only as appropriate to the venue and task.

- If the target limit is unspecified, do not invent a mandatory word count. Use the manuscript's context and the target venue, when known, to choose a reasonable length.

## 5. Evidence-Calibrated Writing Guidance

The following guidance should be applied conditionally rather than as rigid stylistic rules.

### 5.1 Remove redundant modifiers

If the surrounding context already establishes a property, remove a repeated modifier when it contributes no additional technical meaning.

Before:  
"During neural training, the model ..."

Potential revision:  
"During training, the model ..."

This edit is appropriate only when the neural nature of the training is already clear and the shorter expression does not change the intended meaning.

### 5.2 Mark genuine procedural dependencies

Use transitions such as "Then" or "Subsequently" when they help readers understand the order of dependent operations.

Do not introduce sequential language for independent or parallel components merely to make the abstract appear more organized.

### 5.3 Transition naturally from method to evidence

A transition such as "Finally" may help close a description of a multi-stage method before presenting experimental validation. However, it is optional. The abstract may move directly to the evidence when that produces clearer prose.

### 5.4 Learn revision principles, not surface patterns

Mentor-edited papers and revision histories can provide evidence about effective writing decisions. However:

- A single word substitution does not establish a universal preference.

- A formatting change is not automatically a semantic or stylistic rule.

- A repeated edit may indicate a useful convention, but its context must still be examined.

- Examples should illustrate reasoning rather than supply text to copy.

- Rules inferred from a small number of papers should remain provisional until further evidence supports generalization.

Keep high-confidence principles separate from conditional recommendations and paper-specific observations.

## 6. Common Failure Modes

Avoid the following problems:

- **Generic opening:** Spending too much space on broad claims about the importance of a field without identifying the actual task.

- **Unclear research gap:** Claiming that existing methods are inadequate without specifying the relevant limitation.

- **Method–motivation mismatch:** Describing a problem that the proposed method does not actually address.

- **Module listing:** Naming multiple components without explaining their essential functions.

- **Contribution inflation:** Describing routine implementation choices as major innovations without justification.

- **Unsupported superiority:** Claiming state-of-the-art performance, robustness, scalability, or theoretical guarantees without sufficient evidence.

- **Selective reporting:** Highlighting favorable results while implying broader performance than the experiments support.

- **Excessive detail:** Including formulas, hyperparameters, procedural steps, or secondary findings that do not belong in a concise summary.

- **Forced structure:** Requiring a fixed number of sentences, limitations, contributions, or transition words.

- **Redundant prose:** Repeating information already conveyed by the method description or surrounding sentences.

- **Terminological inconsistency:** Using a method name, technical term, or contribution description that conflicts with the main text.

- **Template imitation:** Copying wording from mature papers rather than adapting their high-level reasoning to the current study.

## 7. Task-Specific Output

Adapt the response to the requested task.

### Diagnosis

Identify the most consequential problems first. Explain why each issue matters and give an actionable correction.

### Drafting

Produce a complete abstract when the available manuscript and evidence are sufficient. If an essential fact is missing, ask a focused question or clearly identify the unresolved information.

### Revision

Provide the complete revised abstract when practical. Preserve correct technical content and the intended contribution. Explain material structural or technical changes when useful.

### Shortening

Prioritize redundant background, repeated claims, and low-value details. Preserve the research problem, central mechanism, and most important supporting evidence.

Do not shorten an abstract by deleting a critical qualification or removing the information needed to understand the proposed method.

### Consistency audit

Compare the abstract's claims with the relevant manuscript sections. Identify unsupported claims, terminology conflicts, incorrect numerical values, and differences in the scope of reported conclusions.

Distinguish confirmed errors from issues that require further verification.

## 8. Final Quality Checklist

Before returning a substantive abstract, check the applicable items.

- The research task is clear.

- The central research gap is specific and supported.

- The proposed approach addresses the stated problem.

- The key mechanism is understandable without excessive implementation detail.

- The most important contribution is easy to identify.

- Theoretical and empirical claims are supported by the relevant evidence.

- Numerical results and comparison scopes are accurate.

- Claims do not exceed the strength of the available evidence.

- Terminology agrees with the current manuscript.

- No important qualification has been removed merely to strengthen the wording.

- Sentences are concise, logically connected, and free of unnecessary repetition.

- The abstract complies with the applicable venue requirements.

- The abstract accurately represents the entire paper rather than only its Introduction.

Do not claim that a check has been completed if the necessary source material was unavailable.

## 9. Maintenance and Evidence Updates

Keep this module focused on abstract-specific decisions and workflows.

- Store longer revision examples and paper-specific evidence in separate reference files.

- Promote a candidate writing rule to a default principle only when its reasoning is sound and its evidence is sufficiently broad.

- Preserve the conditions and limitations attached to each rule.

- Avoid duplicating global writing principles already maintained in the root `SKILL.md`.

- When new mentor revision histories become available, compare the original and revised text, identify the actual changes, distinguish observed changes from inferred intentions, and update the guidance only when justified.
