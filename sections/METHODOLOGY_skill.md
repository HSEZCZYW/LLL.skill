---
description: Guidance for structuring, drafting, revising, and auditing
  an academic paper's methodology. Connect design motivation to
  mechanisms and formalization, preserve technical correctness, and
  include algorithms, theory, complexity, and figures only when
  justified.
name: methodology
---

# Methodology --- Section Skill

## 1. Purpose and Scope

This skill guides the drafting, restructuring, revision, and technical
review of the Methodology section of an academic paper.

The goal is to explain the proposed method as a coherent technical
system. Readers should understand why each major design is needed, how
it works, how its components interact, and what formal or empirical
evidence supports the associated claims.

A strong Methodology section combines intuitive explanation with precise
formalization. It should not be a collection of disconnected modules,
equations, implementation details, or decorative theoretical statements.

Follow the root `SKILL.md` and the current manuscript's technical
content. Preserve the intended method, equations, assumptions, and
claims unless the user explicitly authorizes a technical change. Do not
invent mechanisms, theoretical guarantees, or experimental evidence.

## 2. Required Context and Evidence

Before drafting or making substantial revisions, inspect the available
materials relevant to the task:

-   The current Methodology draft, equations, algorithms, and figures.
-   The Introduction's motivation and stated contributions.
-   Preliminaries and Problem Definition, including notation and
    assumptions.
-   The experimental setup and the claims that experiments are intended
    to validate.
-   Relevant implementation details when they are necessary to verify
    the formal description.
-   Explicit author, mentor, and venue requirements.

Use the current manuscript and verified technical evidence as the
primary sources of truth. Reference papers may provide structural
examples, but their technical content must not be transferred to the
current paper without checking that it applies.

If the implementation and manuscript disagree, identify the discrepancy.
Do not silently change the paper to match the code, or the code to match
the paper. State what needs confirmation.

## 3. Recommended Workflow

### Step 1: Identify the requested operation

Determine whether the user wants a new method draft, structural
redesign, language revision, equation audit, theory review, algorithm
description, complexity analysis, or figure planning. Keep the response
proportional to the request.

A local wording edit should not trigger an unnecessary redesign of the
method. A structural problem should not be hidden by polishing sentences
alone.

### Step 2: Recover the method's technical argument

Before writing, summarize the method's actual logic:

1.  What problem or limitation motivates the design?
2.  What is the proposed mechanism?
3.  What information does it use and produce?
4.  How does it connect to the next component?
5.  What objective, algorithm, or formal property governs it?
6.  Which claims are theoretically derived, empirically tested, or
    merely design intuitions?

Ensure the method addresses the research gap stated in the Introduction.
Do not invent a motivation that is disconnected from the actual method.

### Step 3: Design the section architecture

Organize the Methodology according to the dependencies among its
components. A possible structure is:

-   Problem definition and notation, if not already handled elsewhere.
-   Overall framework and method pipeline.
-   Core components or mechanisms.
-   Objective function and optimization.
-   Training or inference procedure.
-   Theoretical analysis and complexity, where justified.

This is an adaptable menu, not a mandatory template. Merge or reorder
parts when the method is simpler, and add a subsection only when it
serves a distinct technical purpose.

Each subsection should have a clear responsibility. Avoid repeating the
same explanation in the framework overview, component descriptions,
objective formulation, and algorithm.

If small headings fragment one mechanism, merge them under a heading
covering the complete mechanism. Recheck coverage, dependencies, and
paragraph transitions after merging; retain separate headings when they
help readers locate distinct functions.

### Step 4: Write each component from motivation to mechanism

For each major module, use the following reasoning sequence when
appropriate:

1.  **Motivation:** identify the specific problem this component
    addresses.
2.  **Design:** explain the core idea and why it is suitable.
3.  **Mechanism:** describe the operation, information flow, and
    relevant equations.
4.  **Role in the whole method:** explain how its output is used by
    later components.
5.  **Supported implication:** state what follows from the design, and
    distinguish formal results from intuition or empirical expectations.

Do not force every component into five separate paragraphs. The sequence
is a reasoning guide. Keep the prose concise and use formulas where they
clarify the mechanism.

Lead with the core operation and its object, then identify input sources,
outputs, and downstream use. For coupled modules, describe the information
or optimization feedback in each direction instead of relying on words
such as joint or unified.

### Step 5: Formalize the method precisely

For each important equation or objective:

-   Define symbols before or at their first meaningful use.
-   Explain the equation's role in the proposed method.
-   Check domains, dimensions, constraints, and dependencies.
-   Ensure the written formula matches the intended algorithm and
    implementation.
-   Distinguish the main theoretical objective from implementation-level
    numerical stabilization.
-   Preserve existing equation meaning and numbering unless a change is
    authorized.

A formula should do real explanatory work. Avoid introducing equations
that merely restate prose, and do not omit a necessary explanation after
presenting a complex expression.

For learned structures, distinguish the admissible variable domain,
candidate support, current nonzero support, and learned weights. Specify
which remain fixed and which can change. As a general technical check,
trace discrete selection separately from continuous updates: learning
weights does not imply that every selection step is differentiable.

### Step 6: Describe algorithms and training procedures when useful

Use pseudocode or an algorithm environment when the method involves a
nontrivial sequence of operations, iterative updates, conditional
branches, or interactions that are difficult to reconstruct from prose.

Clarify: - Inputs and outputs. - Initialization and required
preprocessing. - Main operations and update order. - Stopping criteria
or iteration limits, if applicable. - How the output is used by the next
stage.

Do not add an algorithm merely for appearance. Ensure the pseudocode
agrees with the equations and actual procedure.

Move lengthy implementation detail to a locatable appendix when it
interrupts the explanation. Keep the training objective, essential update
logic, constraints, and conditions needed to understand the method in the
main account; verify the promised detail using root §5.

### Step 7: Assess theoretical claims and complexity

Identify which claims genuinely require formal analysis. A lemma,
proposition, or theorem is useful only if it establishes a meaningful
property of the method.

For each formal result: - State the assumptions and conditions. - Define
all quantities used in the statement. - Ensure the conclusion follows
from the assumptions. - Provide a valid proof or a precise proof sketch
when appropriate. - Explain why the result matters to the method or its
claims.

For complexity analysis, specify the dominant operations, relevant
dimensions, and assumptions. Account for the actual computation pipeline
rather than reporting only the complexity of a convenient sub-operation.

Do not fabricate a proof, infer a guarantee from empirical results, or
present an intuitive expectation as a theorem. If correctness cannot be
established from the available information, identify the missing
argument or request the necessary details.

### Step 8: Plan figures and technical presentation

Consider whether the reader would benefit from:

-   A framework figure showing the complete pipeline and component
    dependencies.
-   A mechanism figure explaining a non-obvious operation.
-   A running example illustrating an important transformation or
    decision.
-   An algorithm block for a nontrivial procedure.

Use figures only when they clarify information that is difficult to
communicate in prose alone. Keep labels, symbols, arrows, and component
names consistent with the manuscript.

When editing LaTeX manuscripts, follow the venue's formatting
requirements. Mentor guidance prefers top placement (`[t]`) for figures,
tables, and algorithms unless there is a clear reason otherwise. Prefer
vector figures, such as PDF, when suitable; ensure fonts, line weights,
and labels remain readable at publication size.

### Step 9: Perform a technical consistency audit

Compare the Methodology against: - The problem definition and
notation. - The Introduction's claimed contributions. - Equations,
algorithms, and theoretical results. - The actual implementation, when
available. - Experiments and ablations that are meant to validate
particular design choices.

Report mismatches explicitly. Do not silently resolve a substantive
contradiction by changing only one location.

## 4. Core Writing Rules

### 4.1 Connect every major design to a concrete motivation

Begin each major method module with a concise motivation when the
purpose is not already clear from the preceding discussion.

Explain the problem the module addresses and why its mechanism is
appropriate. Avoid generic claims such as "to improve performance"
unless the manuscript specifies what aspect of performance is targeted
and why the design is expected to affect it.

Distinguish: - **Motivation:** why a design is proposed. -
**Mechanism:** what the design actually does. - **Theoretical
guarantee:** what has been formally established. - **Empirical
finding:** what experiments demonstrate.

Do not present one category as another.

### 4.2 Pair important ideas with useful formalization

Use equations and definitions to clarify important mechanisms,
objectives, or constraints. Define symbols before using them and explain
non-obvious terms.

Do not add formulas solely to make the method appear technical.
Conversely, do not leave a mathematically essential operation vague when
a formal expression is needed to make it reproducible or verifiable.

### 4.3 Protect the meaning of equations and objectives

Treat equations as technical content, not merely prose that can be
freely polished.

-   Do not silently change an objective, loss, constraint,
    normalization, or update rule.
-   Do not change equation meaning while improving notation or grammar.
-   Do not add numerical stabilizers such as epsilon or tau to the main
    theoretical objective unless they are genuinely part of the method.
-   If a stabilizer is used only in implementation, describe it as an
    implementation detail when appropriate.
-   If a formula appears inconsistent, explain the suspected issue and
    its consequences before proposing a correction.

A technical modification requires evidence and, where the intended
meaning is ambiguous, confirmation from the researcher.

### 4.4 Keep theory useful and defensible

Add definitions, lemmas, propositions, theorems, and proofs only when
they clarify the method or support a meaningful claim.

Every theoretical statement must have a clear purpose. Avoid decorative
proofs, irrelevant mathematical formalism, unsupported convergence
claims, and claims that are stronger than the proof establishes.

State assumptions explicitly and ensure that the conclusion does not
exceed their scope. If a claim is supported only by experiments,
describe it as an empirical observation rather than a theoretical
guarantee.

### 4.5 Make the algorithm match the formal description

Equations, prose, pseudocode, figures, and implementation should
describe the same procedure.

Check operation order, input and output definitions, iterative updates,
hyperparameters, stopping conditions, and special cases. If the
manuscript intentionally abstracts away implementation details, make
sure the abstraction does not change the algorithm's meaning.

Do not claim reproducibility merely because pseudocode is present.
Important choices must be specified or referenced clearly enough for the
intended audience.

### 4.6 Analyze complexity using the actual computation pipeline

When complexity is relevant, identify the dominant operations and
express costs in terms of clearly defined quantities, such as the number
of nodes, edges, features, clusters, or iterations, as applicable.

Include the costs of preprocessing, matrix operations, graph or
structure construction, iterative refinement, and optimization when they
materially affect total complexity. State assumptions such as sparsity
or dense representations when they change the result.

Do not report the complexity of one component as the complexity of the
entire method. Distinguish time and space complexity when both are
relevant.

When several cost terms obscure the result, state the total and its main
components before deriving each term. A reordered expression must retain
the same assumptions and cost; it does not establish a stronger bound.

### 4.7 Use figures to explain, not decorate

The framework figure should communicate the main pipeline and the
relationship among components. A local figure should explain a mechanism
that is otherwise difficult to understand. An example figure should make
a non-obvious transformation or behavior concrete.

Avoid duplicating the same information in a figure, algorithm, and
paragraph without a clear reason. Verify that all figure labels and
symbols agree with the equations and prose.

In a framework caption, describe each module's function, key output,
downstream use, and text location where needed, using comparable detail
across modules. Keep low-level operations in the body. Apply root §5 to
names and formal-result references when revising the overview or figure.

### 4.8 Maintain natural academic prose

Use precise, direct academic language. Avoid inflated claims, repetitive
transitions, excessive colon-based explanations, and frequent em dashes
used for parenthetical explanations.

Prefer clear sentences that explain the relationship between a design
choice and its role. Do not rely on formula introductions such as "The
key idea is:" as a repeated writing pattern.

### 4.9 Separate method description from experimental evidence

Methodology should explain what the method does and why its design is
reasonable. Experimental claims about superiority, robustness, or
practical effectiveness belong primarily in Experiments unless a brief
preview is necessary and supported.

Do not state that a component "significantly improves" performance
unless the manuscript provides evidence for that claim. In Methodology,
use appropriately scoped language such as "is designed to," "aims to,"
or "enables" only when the mechanism supports that description.

## 5. Cross-Section Consistency Checks

### Methodology ↔ Introduction

Every major contribution claimed in the Introduction should correspond
to an identifiable method component or formal result. Do not claim a
contribution that the method does not implement.

### Methodology ↔ Preliminaries and Problem Definition

Use established symbols, domains, and assumptions consistently. Define
local quantities near their first use, and avoid redefining global
notation.

### Methodology ↔ Experiments

Ablation studies and experiments should correspond to meaningful design
choices or claims. Do not imply that an experiment validates a property
it does not measure.

### Methodology ↔ Implementation

Where code is available, check that the mathematical description,
pseudocode, and implementation agree. Distinguish theoretical
definitions from numerical approximations or implementation-only
safeguards.

### Methodology ↔ Figures and Algorithms

Verify that the same components, operations, symbols, and dependencies
appear consistently in text, equations, figures, and pseudocode.

## 6. Common Failure Modes

Avoid the following:

-   Listing method components without explaining why each is needed.
-   Introducing a design without connecting it to the research gap.
-   Presenting equations without defining symbols or explaining their
    role.
-   Using a formula that does not match the described or implemented
    procedure.
-   Silently modifying a core objective or constraint during language
    revision.
-   Adding epsilon, tau, or other numerical stabilizers to the
    theoretical objective without justification.
-   Adding theorems or proofs that do not establish a meaningful
    property.
-   Claiming convergence, optimality, robustness, or avoidance of
    degenerate solutions without sufficient proof or evidence.
-   Giving complexity for one operation while ignoring other dominant
    costs.
-   Providing pseudocode that conflicts with the equations or
    implementation.
-   Creating a framework figure that does not match the actual method.
-   Repeating the same description in the overview, module subsections,
    and algorithm.
-   Treating experimental observations as formal guarantees.
-   Importing another paper's technical mechanism or proof into the
    current method without verification.
-   Polishing the prose while leaving a substantive technical
    contradiction unresolved.

## 7. Output Modes

Adapt the deliverable to the user's request:

-   **Architecture design:** propose the order and responsibilities of
    method subsections based on the actual technical dependencies.
-   **Drafting:** produce a complete method description grounded in the
    confirmed design, equations, and assumptions.
-   **Language revision:** improve clarity and academic style while
    preserving the method's technical meaning.
-   **Equation audit:** identify undefined symbols, inconsistent
    notation, unsupported transformations, and possible formula errors.
-   **Theory review:** assess assumptions, theorem statements, proof
    steps, and the scope of the conclusions. Clearly distinguish
    verified issues from suspected issues.
-   **Algorithm review:** compare pseudocode with the equations and
    implementation.
-   **Complexity analysis:** derive or audit time and space complexity
    using the actual operations and stated assumptions.
-   **Figure planning:** recommend framework, mechanism, or example
    figures that address specific comprehension needs.
-   **Cross-section audit:** identify mismatches among the Methodology,
    Introduction, Problem Definition, Experiments, figures, and code.

If a technical conclusion cannot be verified from the available
materials, state what evidence or derivation is missing. Do not claim to
have executed code, checked a proof, or inspected implementation details
unless that work was actually performed.

## 8. Final Quality Checklist

Before returning substantive Methodology work, check the applicable
items:

-   [ ] The method architecture follows the technical dependencies of
    the actual approach.
-   [ ] Each major component has a clear role and motivation.
-   [ ] The explanation connects design motivation, mechanism,
    formalization, and downstream use.
-   [ ] Important symbols are defined and used consistently.
-   [ ] Equations match the intended objective and procedure.
-   [ ] No technical formula has been silently changed.
-   [ ] Numerical stabilizers are distinguished from the theoretical
    objective.
-   [ ] Assumptions and constraints are explicit where needed.
-   [ ] Theoretical claims are justified and do not exceed the evidence.
-   [ ] Proofs support meaningful claims rather than serving as
    decoration.
-   [ ] Complexity accounts for the relevant computation pipeline.
-   [ ] Pseudocode, equations, prose, figures, and implementation agree.
-   [ ] Figures clarify the method and remain consistent with the text.
-   [ ] Methodological claims align with the Introduction's
    contributions.
-   [ ] Experimental claims are not presented as theoretical guarantees.
-   [ ] Redundant explanations and unnecessary formulas have been
    removed.
-   [ ] Unresolved technical contradictions are reported rather than
    silently patched.
-   [ ] The output matches the user's requested scope and format.

Do not mark an item as verified if the necessary manuscript, code, or
derivation was unavailable.

## 9. Mentor-Derived Guidance and Evidence Boundaries

The primary mentor-derived guidance for this module comes from
`Longlong_Lin_wechat_advice_notes(6).md`, especially Advice 22 and the
formula-writing guidance in Advice 15. The key principles are:

-   Combine intuitive explanation with formalization.
-   Begin each method module with a concise motivation when appropriate.
-   Use formulas or formal definitions to clarify important ideas.
-   Add lemmas, propositions, theorems, and proofs only when technically
    justified.
-   Use framework and example figures when they genuinely improve
    understanding.
-   Ensure every proof supports an actual claim.
-   Avoid unnecessary numerical stabilizers in the main theoretical
    objective when they are implementation-only details.

`Longlong_Lin_style_HGSC_Codex_Guide(6).md` provides a domain-specific
example of organizing the method from problem definition and notation
through framework, core mechanisms, objective, training, and complexity.
This order is illustrative rather than mandatory.

The five reviewed papers can be used as structural and technical
examples only where their methods are relevant. Their specific graph
types, objective functions, equations, assumptions, and theoretical
claims must not be copied into another paper without independent
verification.

The supplied summary adds M1–M5 (E65; E10/E47/E57/E69; E42/E74;
E64/E28; E22/E32/E41). M1 and M4 include reported direct remarks;
module naming, mechanism exposition, and result-first analysis are
conditional revision inferences. The detailed support/gradient checks
and appendix-completeness checks are general technical checks, not
mentor-specific preferences. See root §7 for source limits.
