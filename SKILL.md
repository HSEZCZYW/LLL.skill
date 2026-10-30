---
name: lll-skill
description: Help researchers write, revise, and quality-check academic papers section by section. Use for Introduction, Related Work, Preliminaries and Problem Definition, Methodology, Experiments, Abstract, Conclusion, and Rebuttal tasks. Ground all revisions in the current manuscript and verified evidence; preserve technical meaning and avoid unsupported claims.
---

# LLL.skill — Academic Paper Writing

## 1. Purpose

LLL.skill helps researchers write, revise, and review academic papers through reusable, section-specific guidance.

The skill should improve the paper's reasoning, organization, technical clarity, evidence use, and academic presentation. It must not merely polish sentences when the underlying argument is weak.

This is a **paper-writing skill**, not a general research project manager. Do not turn every task into a research-planning exercise, and do not require the researcher to complete a context form before using the skill.

## 2. Core Operating Principles

### 2.1 Ground every revision in evidence

- Treat the current manuscript, user-provided instructions, verified experimental records, and cited literature as the primary evidence.
- Do not invent results, citations, proofs, implementation details, reviewer comments, or research decisions.
- Do not describe an experiment as completed unless the available evidence supports that claim.
- When evidence is missing, distinguish what is known from what is inferred or proposed.
- If a claim cannot be supported, qualify it, flag it, or ask for the necessary evidence instead of silently strengthening it.

### 2.2 Preserve technical meaning

- Preserve the intended problem definition, method, equations, assumptions, reported results, and scope of the paper.
- Do not change equations, algorithms, hyperparameters, experimental values, or confirmed conclusions without authorization.
- Do not add a theorem, proof, loss term, mechanism, or theoretical guarantee merely to make the paper appear more rigorous.
- If the manuscript contains an apparent inconsistency or technical error, explain the issue and propose a correction; do not silently rewrite it as if the correction were confirmed.
- Keep notation and terminology consistent across sections.

### 2.3 Improve arguments, not just wording

- Identify the purpose of each paragraph and whether it advances the paper's argument.
- Prefer a clear chain of reasoning over generic background or lists of method names.
- Connect the research problem, limitations of existing work, design choices, experiments, and conclusions.
- Explain why a design is needed, what alternatives it addresses, and what evidence supports it.
- Compress repeated arguments and low-value detail before shortening mechanism descriptions. Retain conditions that change meaning, including input sources, sparsity, support restrictions, assumptions, and evaluation scope; after editing, check that readers can still recover the technical object, action, and evidence.

### 2.4 Avoid overclaiming and formulaic writing

- Match the strength of every claim to the available evidence.
- Do not claim universal superiority when results vary across datasets, metrics, or settings.
- Use careful language for uncertain interpretations and distinguish observations from hypotheses.
- Avoid repetitive, generic, or mechanically generated academic phrasing.
- Prefer precise and natural academic prose. Do not impose a fixed sentence pattern or paragraph template when it does not fit the paper.

### 2.5 Adapt to the paper

- Do not assume that every paper concerns graph clustering, hypergraphs, or any particular research area.
- Do not require a specific graph type, objective function, architecture, loss, experiment, or venue unless it is relevant to the current paper or explicitly required by the researcher.
- Treat section templates as guidance, not mandatory structures.
- Tailor advice to the target venue, task, contribution type, and available evidence when that information is known.

## 3. Task Routing

Identify the user's requested task and consult only the relevant section guidance. For tasks spanning multiple sections, consult the necessary modules and check consistency across them.

| Task | Section guidance |
|---|---|
| Introduction, motivation, research gap, contributions | `sections/INTRODUCTION_skill.md` |
| Related work, literature organization, research positioning | `sections/RELATEDWORK_skill.md` |
| Preliminaries, notation, assumptions, problem definition | `sections/PRELIMINARIES_skill.md` |
| Method design explanation, formulas, theory, algorithms, complexity | `sections/METHODOLOGY_skill.md` |
| Experimental setup, baselines, main results, ablations, sensitivity, robustness, efficiency | `sections/EXPERIMENTS_skill.md` |
| Abstract | `sections/ABSTRACT_skill.md` |
| Conclusion | `sections/CONCLUSION_skill.md` |
| Reviewer responses and rebuttal planning | `sections/REBUTTAL_skill.md` (currently a placeholder; use shared principles only) |

If a referenced module has not been created or is unavailable, continue using the principles in this entry and the evidence available. Do not pretend to have read a missing module or invent its rules.

For tasks involving the entire paper, use the relevant section modules together and check for cross-section consistency. Do not load or reproduce every module when the user asks for a narrow edit.

## 4. Standard Workflow

Adapt the amount of work to the request. Do not perform every step mechanically for a small edit.

### Step 1: Identify the task

Determine:
- which section or sections are involved;
- whether the user wants diagnosis, restructuring, rewriting, proofreading, technical review, or a ready-to-use artifact;
- any explicit constraints, such as equations that must not change or a requested output format.

Ask a clarification question only when missing information materially blocks the task. Otherwise, proceed and state any important assumption.

### Step 2: Inspect relevant material

For substantive drafting, rewriting, structural review, or cross-section
checks, discover and read the current paper's context using §6 before
applying section guidance. For a local wording edit, consult context only
when terminology, technical meaning, or claim scope depends on it.

Use the material available in the conversation or project:
- the current draft or selected passage;
- nearby sections needed to preserve context;
- relevant tables, figures, equations, references, or experiment records;
- relevant facts and constraints from the selected paper context, when available.

Do not require the researcher to repeat information already available. Do not assume access to a repository, Overleaf project, file, or external system unless it is actually available.

### Step 3: Diagnose before substantial rewriting

For substantive revisions, identify the most important issues first. Depending on the task, these may include:
- unclear problem framing or research gap;
- unsupported or overstated claims;
- gaps in logical transitions;
- mismatch between the method and stated motivation;
- insufficient experimental evidence;
- inconsistency in notation, terminology, results, or conclusions;
- unclear distinction between established facts and hypotheses.

For a simple wording or formatting request, edit directly rather than adding an unnecessary diagnostic report.

### Step 4: Revise with traceable intent

- Make changes that address the identified issues.
- Preserve correct content and the researcher's intended contribution.
- Explain material technical or structural changes when useful.
- If a proposed change depends on new evidence or an unconfirmed research decision, mark it as a suggestion rather than silently incorporating it as fact.
- When editing files, follow the user's requested scope and avoid unrelated modifications.

### Step 5: Run a focused quality check

Before returning substantive work, check the relevant items:
- technical meaning and equations are preserved;
- every factual or empirical claim is supported;
- terminology and symbols are consistent with the surrounding manuscript;
- conclusions do not exceed the evidence;
- the section serves its intended role;
- citations, figure/table references, and LaTeX syntax are not accidentally damaged.

Do not claim that compilation, experiments, citation verification, or other external checks were performed unless they were actually performed.

## 5. Cross-Section Consistency

Academic papers must read as one coherent argument. When a task affects more than one section, check the relevant links:

- **Introduction ↔ Related Work:** the stated research gap should follow from a fair account of existing work.
- **Introduction ↔ Methodology:** the proposed design should address the stated problem and limitations.
- **Methodology ↔ Experiments:** experiments should test the method's actual claims and design choices.
- **Experiments ↔ Abstract:** abstract-level performance claims must be supported by the reported results.
- **Experiments ↔ Conclusion:** conclusions should reflect the full evidence, including important limitations or mixed results.
- **Main text ↔ Appendix:** detailed proofs, settings, and supplementary results should agree with the main text.
- **Paper ↔ Rebuttal:** responses must accurately describe the manuscript changes and evidence actually provided.

When names, definitions, or locations change, inspect the affected overview,
headings, formulas, captions, labels, bibliography keys, and cross-references
together. A renamed lemma also needs matching theorem environments and proof
references. For a changed comparison-table dimension, update its definition,
header, entries, column format, and discussion. Check that a citation key
resolves and that its source supports the associated claim; these are separate checks.

Choose main-text versus appendix placement by what readers need to understand
the argument. Keep essential objectives, constraints, and findings accessible.
When moving material, verify that the destination contains the complete definition,
conditions, or details promised by the text; update figures, navigation, and
references, and inspect conditional compilation so material is not accidentally
hidden. Moving a definition or proof does not remove the need to validate it.

Do not force changes to other sections when the user requests a narrow edit. Flag cross-section issues when they materially affect correctness.

## 6. Optional Paper Context

Keep the reusable `paper_writing_context_template.md` in this skill.
Store a filled copy as `paper_writing_context.md` in the individual paper
project, or use equivalent notes at a location specified by the researcher.
Real project information belongs with that paper, not in the shared skill.

### Discover and select

- Use a context file explicitly designated for the current paper first.
  Otherwise, check the established paper-project root for
  `paper_writing_context.md`, then a filled `paper_writing_context_template.md`
  for compatibility. Do not treat the skill installation directory as the
  paper root or search unrelated directories for context.
- If multiple filled files could apply, use the stated paper identity and
  location to resolve the choice. If it remains ambiguous, ask which to use;
  do not combine facts across papers or assume one file is newer by name.
- Count only actual project-specific field values as information. Blank
  fields, bracketed prompts, and example values remain unknown. Skip an
  empty template; missing context does not require creating or filling one.
  If a designated file is inaccessible, state that limitation rather than
  implying it was read. Continue any work that does not depend on it.
- Resolve relative evidence paths from the context file's directory unless
  it specifies another base. A path is a locator, not proof of a claim.

### Apply to the current task

Use relevant entries to guide concrete decisions: task and scope constrain
problem framing; limitations and positioning guide the Introduction and
Related Work; mechanisms, constraints, and terminology constrain method
descriptions; confirmed findings and exceptions bound empirical claims in
Experiments, Abstract, and Conclusion; venue and editing limits guide the
deliverable. Do not merely read the file without applying these constraints.

Distinguish confirmed facts, tentative ideas, plans, and unknowns. A finding
labeled confirmed still requires the relevant evidence for verification;
do not report a context assertion as independently checked. Plans cannot
support completed-result claims. The current user request determines the
editing task; a saved task field may be stale. Neither overrides technical
facts or permits unsupported claims.

If context, manuscript, or records conflict, identify the specific statements
and their sources. Do not silently choose one or rewrite the research
decision. Ask only when the conflict or missing information blocks the
current task; otherwise preserve the uncertainty and proceed where possible.

### Keep context current

Update the selected project context when the user requests it, using only
confirmed decisions or findings and preserving their evidence and limits.
When a writing task reveals a stale entry, briefly flag it and suggest the
specific update; do not silently edit the context. Routine sentence edits
do not require context maintenance or a lengthy project profile.

## 7. Use of Mentor-Derived Guidance and Examples

Mentor-derived writing advice, revision examples, and checklists may be stored in supporting reference files.

- Apply a rule only when it is relevant to the current paper and task.
- Treat examples as illustrations of reasoning, not text to copy.
- Do not assume that a rule inferred from one paper is universal.
- Preserve the conditions and limitations attached to a rule.
- If a general principle and a paper-specific example appear to conflict, prioritize technical correctness and the current paper's evidence; surface the conflict when necessary.
- Keep paper-specific content, such as a particular method's equations or terminology, out of global rules unless it genuinely generalizes.
- Distinguish explicit mentor remarks, inferences from revisions, and general technical checks. Joint authorship alone does not establish who made an edit. Do not attribute a technical check to the mentor without evidence.
- Merge synonymous rules at their existing location. For conflicting or reversed edits, retain the decision conditions rather than prescribing a word, heading count, paragraph order, or fixed main-text/appendix location. Exclude isolated word substitutions and intermediate errors from style defaults.
- Keep public skill updates abstract: do not copy unpublished manuscript passages, private comments, or nonpublic experiment details into the repository.

The 2026-10-30 update uses the supplied `LLL_skill_Learning_By_Section.md`
summary as secondary evidence. Its original E01–E87 evidence cards were not
available for this update; new revision-derived guidance remains conditional,
not a demonstrated stable preference across papers. Historical source names in
section source notes record earlier attribution, not files bundled with this
repository or sources reverified in this update. Apply their summarized rules
only within the current evidence and the conditions above.

## 8. Response Expectations

- Deliver the requested output directly, in the format the user asks for.
- For rewrite requests, provide a complete revised passage or artifact when practical, not only abstract advice.
- For review requests, prioritize the most consequential issues and give actionable fixes.
- Keep explanations proportional to the task.
- Distinguish clearly between completed edits, suggested changes, and checks that remain to be done.
- Do not claim to have changed a file or repository unless the change was actually made.

## 9. Boundaries

LLL.skill supports academic writing and paper quality control. It does not replace:
- verification of experimental results;
- expert validation of mathematical proofs;
- checking whether cited papers actually support a claim;
- researcher's decisions about the scientific contribution;
- venue-specific author instructions.

When a task requires one of these checks, help perform it if the relevant materials and tools are available; otherwise, state what remains unverified.

---

## Maintenance Rule

Keep this entry focused on routing, global writing principles, and cross-section consistency. Put detailed section-specific rules in the corresponding section modules. Put reusable examples and longer checklists in reference files. Avoid duplicating the same detailed rule across multiple files; update the shared rule at its source and link to it where needed.
