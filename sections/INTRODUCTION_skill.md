---
name: introduction-writing
description: Diagnose, outline, draft, or revise the Introduction of an academic paper. Use when a researcher asks to improve the paper's motivation, research gap, positioning, method overview, or contribution statements.
---

# Introduction Writing Skill

## 1. Purpose and Scope

Help researchers produce an Introduction that explains **what problem matters, what existing approaches leave unresolved, why the proposed approach is needed, and what the paper contributes**.

Do not merely polish sentences. Improve the research narrative and the logic connecting the problem, research gap, method, and contributions.

This module covers:
- diagnosing and organizing the Introduction;
- motivating the research problem and identifying the research gap;
- describing limitations of existing approaches fairly;
- explaining why a straightforward solution may be insufficient;
- presenting the proposed approach at a high level;
- drafting and checking contribution statements.

Detailed literature synthesis belongs primarily to Related Work. Formal method definitions, equations, and proofs belong to Methodology. Detailed result interpretation belongs to Experiments. The Introduction should preview these elements only as needed to establish the paper's argument.

## 2. Required Inputs and Context Inspection

Before a substantial rewrite, inspect the available materials in this order:

1. The current Introduction or the user's stated research idea.
2. The Methodology or method summary, to understand what the paper actually proposes.
3. The main experimental findings, if available, to ensure the motivation and contribution claims are supported.
4. Related Work and the relevant cited papers, when available, to check how existing methods are characterized.
5. The optional `paper_writing_context_template.md`, if provided.

Do not ask the researcher to repeat information already present in the manuscript or conversation. Do not assume access to files, repositories, Overleaf, or external literature unless they are actually available.

If the user asks for a rewrite and the available materials are sufficient, proceed directly. If a missing fact materially affects the validity of the research gap or the method claim, ask a focused question or clearly mark the unresolved point.

## 3. Research Positioning: Derive the Gap from Evidence

### 3.1 Identify the shared paradigm

When relevant, group existing approaches by their underlying research paradigm rather than listing method names one by one. For each category, identify:
- the problem it is designed to solve;
- the main capability it provides;
- the limitation that matters for the current task;
- the evidence supporting that characterization.

Critique a shared paradigm when the evidence supports a systematic limitation. Do not claim that all methods in a category share a weakness if the evidence only applies to selected methods.

A property-comparison table may help when several method families differ along clear, relevant dimensions. Include one only when its dimensions and entries can be supported and the table makes the gap easier to understand.

### 3.2 Focus on a small number of important limitations

A useful default is to organize the motivation around **two major limitations** rather than scattering many minor complaints throughout the Introduction. State each limitation clearly and reuse the same concepts consistently in the method overview and contribution statements.

This is a writing heuristic, not a mandatory count. Use one limitation or a different number when that more accurately reflects the paper's evidence and contribution.

For each proposed limitation, check:
- Is it important to the target task?
- Is it supported by relevant literature, theory, or observed evidence?
- Does it remain unresolved by the methods being discussed?
- Does the proposed method actually address it?

Avoid vague statements such as “existing methods have several limitations” without explaining what they are. Avoid overstating the limitation with absolute wording such as “cannot” when “may fail to” or “does not explicitly address” is more accurate.

### 3.3 Do not confuse a stronger backbone with the research contribution

A stronger encoder or backbone can improve performance, but the Introduction should not present the choice of a stronger backbone alone as the central novelty.

Explain the substantive research contribution beyond representation learning when one exists, such as a new problem formulation, objective, structure-refinement strategy, robustness mechanism, theoretical insight, or other task-relevant advance. Do not invent an additional contribution if the paper does not contain one.

Use baselines and examples appropriate to the paper's actual graph or data type. Do not assume that a particular architecture or graph structure is relevant to every paper.

### 3.4 Explain why a straightforward solution is insufficient when useful

When a reviewer is likely to ask why an easier solution is not enough, consider a short argument with this logic:

**Straightforward solution → specific limitation → why that limitation matters → proposed alternative.**

Use this only when the alternative is genuinely relevant and its limitations can be supported. Do not invent a failed experiment or claim that a baseline fails unless the evidence supports that statement.

### 3.5 Name a failure mode only when it adds precision

A concise name for a recurring failure mode can help connect the motivation, method, and experiments. Introduce such a term only if the phenomenon is clearly defined and supported. Use it consistently after introduction.

Do not create a named “issue” merely to make the contribution sound novel, and do not transfer a paper-specific term into unrelated tasks.

## 4. Default Introduction Narrative

Use the following as a flexible outline, not a rigid paragraph template.

1. **Task and significance.** Introduce the broad task and why it matters. Keep familiar background concise.
2. **Target setting and current paradigm.** Narrow to the specific problem and summarize the relevant family or families of approaches.
3. **Key limitations and research gap.** Explain the small number of important limitations and why they matter in the target setting.
4. **Straightforward alternative, if needed.** Explain why an obvious fix is insufficient, when this is a likely reviewer concern.
5. **Proposed approach.** Present the core idea as a direct response to the stated limitations. Explain the high-level mechanism and design rationale, not every implementation detail.
6. **Contributions.** State the paper's concrete contributions and how they follow from the preceding argument.

The number of paragraphs can vary. Do not force a paper into this order if a different order better communicates its actual contribution.

### 4.1 Keep the opening concise

Avoid spending too much space on generic claims about the importance of AI, graphs, data mining, or a broad application area. Move quickly toward the specific task and the unresolved problem.

### 4.2 Keep detailed literature comparison in the right place

The Introduction should provide enough context to establish the gap, but should not become a long catalogue of method names or paper-by-paper descriptions. Put detailed taxonomy, representative methods, and citation-heavy comparisons in Related Work.

### 4.3 Give the proposed approach enough explanation

Do not spend several paragraphs on background and then introduce the method in one vague sentence. Explain what the method changes relative to the identified limitations and why that design is relevant. Keep formulas and implementation details for Methodology.

## 5. Contribution Statements

A useful default is **three contributions**, but the count must follow the actual work.

A common organization is:
1. **Problem or methodological contribution:** the framework, formulation, or central idea.
2. **Technical contribution:** the specific mechanism or analysis that addresses the main limitation(s).
3. **Empirical or theoretical validation:** the evidence establishing what the paper demonstrates.

When the Introduction is organized around two major limitations, the first two contributions can correspond to those limitations, while the final contribution summarizes the validation. This alignment is a useful default, not a rule to force when the paper's contributions differ.

For each contribution, verify that it is:
- concrete rather than a broad claim of being “novel” or “effective”;
- distinct from the other contributions;
- actually present in the method, theory, or experiments;
- stated at a strength supported by the evidence.

Do not list routine implementation choices as major contributions unless they create a meaningful and substantiated advance. Do not claim comprehensive experiments, theoretical guarantees, robustness, or superior performance unless the paper actually provides the corresponding evidence.

## 6. Drafting and Revision Procedure

For substantial Introduction work, follow this procedure.

### Step 1: Build an argument map

Write a compact internal outline with:
- target task and setting;
- relevant method paradigms;
- key limitation(s) and supporting evidence;
- intended research gap;
- proposed response to each limitation;
- contributions and their supporting evidence.

Do not start by polishing individual sentences before checking whether this argument map is coherent.

### Step 2: Check the logic

Verify the following chain:

**Existing approach and capability → evidence-backed limitation → consequence for the target task → design requirement → proposed approach.**

If one link is missing, repair the reasoning or flag the missing evidence. Do not bridge a logical gap with rhetorical language.

### Step 3: Draft or revise the prose

- Use natural, precise academic English.
- Give each paragraph a clear purpose.
- Spend writing effort on the central motivation and method rationale rather than familiar background.
- Avoid repetitive method-name lists and empty transition sentences.
- Avoid mechanical prose patterns, including excessive colons, semicolons, and em dashes used for explanatory asides. Use them when appropriate, not as a blanket prohibition.
- Use mature papers as references for paragraph function and organization only; do not copy their text or transfer their technical claims.

### Step 4: Align the Introduction with the rest of the paper

Check that:
- the method described is the method actually implemented;
- the stated limitations correspond to the design choices;
- contribution statements match the Methodology and experiments;
- empirical claims are consistent with the reported results;
- terms and symbols agree with the rest of the manuscript.

### Step 5: Deliver the requested output

Adapt to the user's request:
- **Diagnosis:** list the highest-impact logical and evidence problems, with specific fixes.
- **Outline:** provide the argument flow and the purpose of each paragraph.
- **Rewrite:** provide a complete revised Introduction or requested passage when the supplied materials permit it.
- **Review of an existing draft:** distinguish necessary corrections from optional stylistic changes.

When useful, briefly summarize the material changes. Do not provide a long explanation if the user asked only for a ready-to-use passage.

## 7. Common Failure Modes to Avoid

- **Motivation by assertion:** claiming a research gap without checking the relevant literature or evidence.
- **Method-first writing:** introducing a model before explaining the problem that makes it necessary.
- **Overgeneralized criticism:** attributing one method's limitation to an entire research field.
- **Contribution inflation:** describing an ordinary component, stronger backbone, or routine combination as a major innovation without justification.
- **Template forcing:** requiring exactly two limitations, three contributions, a named failure mode, or a failed-solution paragraph regardless of the paper.
- **Unsupported causal claims:** asserting why a method performs poorly without evidence.
- **Overloaded Introduction:** including full literature review, equations, implementation details, and lengthy result analysis.
- **Method–motivation mismatch:** motivating one problem while the proposed method addresses another.
- **Overclaiming:** claiming universal superiority, robustness, or theoretical guarantees beyond what the paper demonstrates.
- **Paper-specific leakage:** carrying a technical issue, terminology, or method description from one paper into an unrelated paper.
- **Copied structure or wording:** borrowing another paper's prose instead of adapting its high-level organization to the current research.

## 8. Final Checklist

Before returning a substantial revision, check:

- [ ] Is the target task clear and the opening concise?
- [ ] Does the Introduction move from broad context to the specific problem?
- [ ] Are existing approaches characterized fairly and by relevant paradigms where useful?
- [ ] Is each stated limitation important, specific, and supported?
- [ ] Is the research gap a logical consequence of those limitations?
- [ ] Is a straightforward solution discussed when that comparison is genuinely useful?
- [ ] Does the proposed approach directly respond to the stated gap?
- [ ] Are contributions concrete, distinct, and supported by the paper?
- [ ] Are claims consistent with the method and available results?
- [ ] Are detailed literature comparisons and technical derivations left to the appropriate sections?
- [ ] Is the language concise, natural, and appropriately cautious?
- [ ] Have paper-specific assumptions or terminology been kept out of generic rules?

## 9. Source-Derived Guidance

This module consolidates the following guidance from the provided source files:

- `Longlong_Lin_style_HGSC_Codex_Guide(6).md`: Core Writing Philosophy; §2.1 Paradigm-level Critique; §2.2 Two-fold Limitations; §2.5 Basic Solution → Limitation → Advanced Framework; §2.6 Failed Attempt Writing; §3.1 Recommended Introduction Structure; §3.3 Contribution Template; §9.1 Rewrite Introduction; Introduction checklist in §10.
- `Longlong_Lin_wechat_advice_notes(6).md`: Advice 8 (strong backbones are not enough for motivation); Advice 9 (use mature paper structures without copying content); Advice 13 (focus writing effort on key arguments); Advice 23 (structure the Introduction around two limitations).

HGSC-specific examples and wording in the source guide are not treated as universal rules. Only the underlying writing principles are generalized here.
