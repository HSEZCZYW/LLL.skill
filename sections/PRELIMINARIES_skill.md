---
description: Guidance for drafting, revising, and auditing a paper's
  preliminaries, notation, assumptions, and problem definition. Keep
  global notation minimal, formalize the actual task precisely, and
  maintain consistency with the method and experiments.
name: preliminaries-problem-definition
---

# Preliminaries & Problem Definition --- Section Skill

## 1. Purpose and Scope

This skill helps researchers prepare and review the preliminaries,
notation, assumptions, and problem definition of an academic paper.

The goal is to establish only the concepts and formal details that
readers need to understand the paper's problem and follow its subsequent
technical development. The section should be mathematically precise
without becoming a repository for every symbol, background concept, or
implementation detail.

The appropriate organization depends on the paper. Preliminaries and
Problem Definition may appear as separate sections, as subsections, or
partly at the beginning of Methodology. This skill guides the writing
decisions; it does not require a fixed manuscript structure.

Follow the root `SKILL.md` and preserve the current manuscript's
technical meaning. Do not invent assumptions, constraints, objectives,
definitions, or mathematical guarantees to make the paper appear more
formal.

## 2. Required Context and Evidence

Before drafting or making substantial revisions, inspect the available
materials relevant to the task:

-   The current manuscript, especially the Introduction, Methodology,
    and Experiments.
-   Existing definitions, notation tables, equations, algorithms, and
    theorem statements.
-   The research task and its input/output requirements.
-   Explicit assumptions, constraints, and evaluation settings.
-   Author instructions and relevant venue requirements.

Use the current manuscript and verified technical details as the primary
sources of truth. If a symbol's intended meaning or a problem constraint
is unclear, flag the ambiguity rather than guessing.

A paper that studies an established problem generally needs less
background formalization than a paper introducing a new task, problem
variant, or evaluation setting.

## 3. Recommended Workflow

### Step 1: Identify the requested operation

Determine whether the task is to draft definitions, reorganize
preliminaries, audit notation, formalize a problem, revise equations, or
check consistency. Keep the scope proportional to the request.

Do not rewrite unrelated parts of the paper when the user asks for a
localized notation or definition fix.

### Step 2: Determine what belongs in preliminaries

Include a concept or notation item when readers need it to understand
multiple later parts of the paper or when it establishes the formal
setting for the problem.

Prefer to define locally: - Symbols used only in one method
subsection. - Intermediate variables introduced for a specific equation
or algorithm. - Implementation-specific quantities that do not affect
the formal problem statement. - Background facts that are unnecessary
for understanding the paper's actual contribution.

Do not move material into Preliminaries merely because it is
mathematical.

### Step 3: Build a notation inventory

When useful, create an internal inventory of symbols and their meanings.
Record:

-   Symbol.
-   Meaning and mathematical type.
-   Shape or dimensionality, where applicable.
-   First occurrence.
-   Later uses.
-   Whether the symbol is global or local.

Use this inventory to identify undefined symbols, duplicate definitions,
overloaded notation, inconsistent dimensions, and symbols that are
defined but never used.

A notation table is optional. Include one only when it improves
readability or is appropriate for the manuscript's complexity and venue.

### Step 4: Formalize the problem

A problem definition should make the task unambiguous. Depending on the
research setting, specify the relevant elements:

-   Input objects and their representations.
-   Output or target object.
-   Objective to be optimized or property to be achieved.
-   Constraints and assumptions.
-   Relevant parameters or query conditions.
-   Evaluation setting, if it is part of the problem being defined.

Do not force every problem definition to contain all these elements.
Include what is necessary for the particular task.

For an established problem, state the formal definition concisely and
cite the appropriate source when needed. For a new or modified problem,
explain what is new and distinguish the proposed formulation from the
established one.

### Step 5: Check mathematical precision

Verify that:

-   Every symbol is defined before or at its first meaningful use.
-   Sets, vectors, matrices, scalars, indices, and mappings are
    distinguishable.
-   Dimensions and domains are compatible with the equations.
-   Assumptions are explicit when later reasoning depends on them.
-   Quantifiers and constraints are stated clearly when needed.
-   Each definition is consistent with the algorithm and objective that
    use it.
-   No equation silently changes the meaning of a previously defined
    symbol.

Do not change a formula merely to make notation look more conventional.
If a formula appears inconsistent, explain the issue and request
confirmation when the intended meaning cannot be determined reliably.

### Step 6: Integrate with Methodology

Check whether the problem definition and notation provide the right
foundation for the method.

-   Keep globally reused notation in the shared preliminaries or
    notation section.
-   Define module-specific symbols close to the module where they first
    matter.
-   Avoid repeating a complete definition in multiple sections.
-   Ensure that the method's equations, algorithms, and theoretical
    statements use the established notation consistently.
-   If a problem definition is more naturally introduced with the
    method, allow it to appear at the beginning of Methodology rather
    than forcing an independent section.

### Step 7: Audit cross-section consistency

Compare the definitions and assumptions against the Introduction,
Methodology, and Experiments. Verify that the formal task matches what
the method actually solves and what the experiments actually evaluate.

If the manuscript contains a mismatch, identify the conflicting
statements. Do not silently change the problem definition to make the
sections appear consistent.

## 4. Core Writing Rules

### 4.1 Keep preliminaries concise

When the paper studies an established problem, introduce only the
background and notation required for the subsequent discussion.

Expand the section when the paper introduces a new problem, a meaningful
problem variant, or a nonstandard evaluation setting that requires
formal clarification.

Conciseness must not come at the expense of a necessary definition or
assumption.

### 4.2 Define symbols once and use them consistently

Give each symbol one clear meaning within the paper unless the
manuscript explicitly distinguishes context-dependent meanings.

Avoid: - Reusing a symbol for unrelated quantities. - Defining the same
object differently in different sections. - Introducing a second
notation for an existing concept without a clear reason. - Defining
symbols that are never used. - Leaving the dimensions or domains of
important quantities ambiguous.

If notation must change during revision, search for all affected
occurrences and update them consistently.

### 4.3 Separate global and local notation

A symbol belongs in the shared preliminaries when it is needed across
the paper or is essential to understanding the formal problem.

A symbol used only in one method module should usually be defined
locally. This keeps the preliminaries compact and allows each module to
introduce its own intermediate quantities in context.

Do not place all equations' symbols into a global notation table by
default.

### 4.4 State assumptions only when justified

Include assumptions that are required to define the task, derive a
result, or interpret the method correctly.

-   Explain assumptions that are nonstandard or consequential.
-   Ensure theoretical claims rely only on assumptions actually stated
    or established.
-   Do not add assumptions merely to simplify the exposition.
-   Do not imply that an empirical condition is a theoretical guarantee.
-   Distinguish the formal problem setting from choices made only for
    experiments.

### 4.5 Make the problem definition operational

A reader should be able to identify what the method receives, what it is
expected to produce, and what makes a solution valid or desirable.

Use precise mathematical language when it clarifies the task. Avoid a
formula that merely restates vague prose without specifying the
objective, domain, or constraints.

For a learning problem, distinguish the task definition from the
particular model or optimization strategy used to solve it. The problem
should not be defined so narrowly that it assumes the proposed method's
own design unless that restriction is intrinsic to the task.

### 4.6 Explain mathematical objects without overexplaining standard facts

Provide enough context for readers to interpret definitions and
equations. Do not spend substantial space explaining widely known
concepts unless the paper uses them in a nonstandard way or the target
audience requires clarification.

When a formal definition is followed by a method, briefly clarify how
the definition will be used if that relationship is not self-evident.

## 5. Problem Definition and Methodology Placement

Choose the manuscript structure according to the role of the
formalization.

### Use a separate Preliminaries section when:

-   Several shared concepts or symbols are required throughout the
    paper.
-   The problem relies on nontrivial background definitions.
-   A common notation system will simplify multiple method modules.

### Use a separate Problem Definition subsection when:

-   The task formulation is substantial or central to the contribution.
-   The paper introduces a new problem or a meaningful variant.
-   Input, output, constraints, or evaluation assumptions need explicit
    treatment.

### Place the definition at the beginning of Methodology when:

-   The formalization is tightly coupled to the proposed method.
-   Only a small amount of shared background is needed.
-   Separating it would create repetition or an unnecessarily short
    section.

These are organizational options, not rigid rules. Follow the paper's
logical flow and target venue conventions.

## 6. Common Failure Modes

Avoid the following:

-   Treating Preliminaries as a dumping ground for all mathematical
    notation.
-   Defining symbols that never appear again.
-   Defining local intermediate variables globally without a reason.
-   Reusing symbols with conflicting meanings.
-   Introducing a formula before defining its important symbols.
-   Omitting domains, dimensions, constraints, or assumptions needed to
    interpret an equation.
-   Formalizing an established problem at excessive length.
-   Giving a vague problem statement that does not identify the input,
    output, or objective.
-   Defining the problem in terms of the proposed model's implementation
    rather than the underlying task.
-   Adding assumptions or theoretical properties not supported by the
    manuscript.
-   Repeating the same definitions in Preliminaries and Methodology.
-   Silently changing technical formulas or symbol meanings during
    language editing.
-   Fixing an inconsistency in one section while leaving conflicting
    notation elsewhere.
-   Forcing a standalone Preliminaries section when the content is more
    naturally integrated into Methodology.

## 7. Output Modes

Adapt the response to the user's requested task.

-   **Drafting:** produce definitions and a problem statement grounded
    in the available manuscript and confirmed task details.
-   **Notation audit:** list undefined, overloaded, inconsistent,
    unused, or dimensionally ambiguous symbols and suggest specific
    fixes.
-   **Problem-definition review:** assess whether inputs, outputs,
    objectives, assumptions, and constraints are sufficiently clear.
-   **Structural revision:** recommend what should remain global, what
    should move into Methodology, and what can be removed.
-   **Equation consistency check:** identify conflicts between formulas
    and surrounding definitions without silently altering technical
    meaning.
-   **Cross-section audit:** compare the formal problem against the
    method and experimental setup and report mismatches.

When essential information is missing, ask a focused question or mark
the unresolved issue. Do not fill gaps with invented technical
assumptions.

## 8. Final Quality Checklist

Before returning substantive work, check the applicable items:

-   [ ] The section contains only background and notation needed for the
    paper.
-   [ ] The amount of preliminaries is appropriate for an established or
    newly formulated problem.
-   [ ] Each important symbol is defined before or at its first
    meaningful use.
-   [ ] Each symbol has one consistent meaning.
-   [ ] Global notation is separated from module-specific notation.
-   [ ] Domains, types, and dimensions are clear where necessary.
-   [ ] Required assumptions and constraints are stated explicitly.
-   [ ] The problem definition identifies the necessary inputs, outputs,
    and objectives.
-   [ ] The formalization matches the actual research task.
-   [ ] No unsupported assumptions, definitions, or guarantees have been
    introduced.
-   [ ] Definitions and formulas agree with the Methodology.
-   [ ] The formal task matches the experimental setup where relevant.
-   [ ] Repeated definitions and unused symbols have been removed or
    justified.
-   [ ] No technical formula or symbol has been changed without
    authorization.
-   [ ] The organization is appropriate for the paper and target venue.

Do not claim that a check has been completed if the necessary manuscript
or evidence was unavailable.

## 9. Mentor-Derived Guidance and Evidence Boundaries

The primary mentor-derived guidance for this module is:

-   Keep Preliminaries limited to globally used notation.
-   Keep it concise when studying an established problem.
-   Expand it when introducing a new problem or evaluation setting.
-   Define symbols once and use them consistently.
-   Move notation used only in one later subsection into that
    subsection.
-   Check whether every symbol introduced in Preliminaries is used
    later.
-   Audit for symbol overload and ensure that the same symbol has one
    meaning throughout the paper.

These rules are based primarily on
`Longlong_Lin_wechat_advice_notes(6).md`, especially Advice 21 and its
associated Codex instruction. The
`Longlong_Lin_style_HGSC_Codex_Guide(6).md` provides a domain-specific
example of placing problem definition and notation at the beginning of
Methodology. Treat that placement as an example, not a universal
requirement.

The five reviewed papers may provide additional examples of
formalization, but their domain-specific definitions, graph structures,
objectives, and symbols must not be transferred to another paper without
checking relevance and correctness.
