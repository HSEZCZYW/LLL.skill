---
description: Guidance for drafting, restructuring, revising, and
  auditing the Related Work section of an academic paper. Organize
  literature by meaningful research paradigms, verify citations, cover
  relevant baselines, and align limitations with the paper's actual
  research gap.
name: related-work
---

# Related Work --- Section Skill

## 1. Purpose and Scope

The Related Work section positions the paper within existing literature.
It synthesizes the most relevant research, clarifies how research
directions differ, and establishes a fair, evidence-based connection
between prior work and the problem addressed by the current paper.

Related Work is **not** an exhaustive survey of the entire field. It
should not duplicate the Introduction's full motivation, reproduce the
Method section's technical details, or become a sequence of disconnected
paper summaries.

Follow the global principles in the root `SKILL.md`: preserve technical
meaning, ground claims in evidence, avoid overclaiming, and adapt the
structure to the current paper rather than imposing a fixed template.

## 2. Required Context and Evidence

Before drafting or making substantial revisions, inspect the relevant
materials available:

-   The current Related Work draft and bibliography.
-   The paper's Introduction, especially its stated research gap and
    principal limitations of existing work.
-   The Method section, to understand what the proposed method actually
    addresses.
-   The experimental setup and baseline list, where available.
-   Relevant cited papers, their verified content, and any explicit
    mentor or venue instructions.

Use the current manuscript, verified literature, and researcher-provided
constraints as primary evidence. Do not assume access to Overleaf, a
repository, a reference manager, or external files unless they are
actually available.

If evidence is incomplete, continue where possible and mark what needs
verification. Do not invent citations, publication details, claims about
prior methods, or statements that a method has never been studied.

## 3. Recommended Workflow

### Step 1: Identify the requested operation

Determine whether the user wants a diagnosis, taxonomy, rewrite, new
draft, citation audit, or consistency check. Keep the response
proportional to the request. A narrow wording edit does not require a
full literature review.

### Step 2: Establish the section's argument

Summarize, for internal use, the paper's task, main contribution,
research gap, and the limitations it claims to address. Check that these
points are supported by the current manuscript and evidence. Do not
formulate the literature taxonomy around a contribution that the paper
does not actually make.

### Step 3: Design a paper-specific taxonomy

Group prior work by a meaningful research distinction, such as:

-   Research task or problem formulation.
-   Methodological paradigm or learning strategy.
-   Representation or structural assumption.
-   Optimization objective or central mechanism.
-   Another distinction that is technically meaningful for the current
    paper.

Choose the criterion that best explains the field and the paper's
position. Avoid mixing unrelated classification criteria at the same
level unless the literature genuinely requires it.

The mentor-derived default is **two or three subsections**, with each
subsection corresponding to a relevant research category. Treat this as
a preference, not a universal limit: use fewer or more only when the
paper's scope and literature justify it. Do not create artificial
categories just to satisfy a fixed count.

### Step 4: Check literature and baseline coverage

Create a working coverage map when useful. For each relevant method or
paper, track:

-   Its research category.
-   Its central idea or distinguishing mechanism.
-   The claim for which it is cited.
-   Its relevance to the current paper.
-   Whether it is an experimental baseline.
-   Whether the cited details have been verified.

Ensure experimental baselines are appropriately covered in Related Work.
This does **not** mean every baseline needs a separate paragraph;
related methods can be discussed together when their principles
genuinely overlap.

Check for both foundational work and recent, directly relevant studies.
Do not add papers merely to increase citation counts, and do not omit
relevant methods just because they are difficult to reproduce. If a
baseline or paper is missing, distinguish an actual omission from a case
where its relevance or evidence remains uncertain.

### Step 5: Synthesize each category

Write around research ideas and relationships, not a paper-by-paper
inventory. A useful category discussion normally does the following:

1.  Defines the category's goal or central idea.
2.  Synthesizes representative approaches that share a meaningful
    principle.
3.  Explains important differences between approaches when those
    differences matter.
4.  Identifies a limitation relevant to the current paper, supported by
    the literature.
5.  Connects that limitation to the paper's research positioning without
    prematurely repeating the full Introduction.

These are reasoning functions, not a mandatory sentence-by-sentence
template. Use the number of paragraphs required by the content.

### Step 6: Align the section with the rest of the paper

Check that the limitations discussed in Related Work match the paper's
stated research gap and the actual capabilities of its method. The
Introduction may explain in greater depth why those limitations matter;
Related Work should establish the literature context fairly and
concisely.

### Step 7: Audit claims, citations, and presentation

Verify that each citation supports the claim attached to it, the
references are correctly represented, and the section does not overstate
novelty or inadequacy of prior work. Preserve existing citation keys and
bibliography conventions unless the user authorizes changes.

## 4. Core Writing Rules

### 4.1 Organize by paradigm, not by paper

Avoid a structure in which every paper receives an isolated sentence
with no synthesis. Group methods that share a research objective or
technical principle, then explain their meaningful similarities and
differences.

Chronological organization is appropriate only when evolution over time
is itself important to the argument. Do not use chronology as a
substitute for a clear taxonomy.

### 4.2 Keep the scope focused

Include work that helps readers understand the task, relevant
methodological alternatives, the paper's positioning, or the
experimental comparison. Avoid broad background that belongs in the
Introduction and technical derivations that belong in the Method or
Preliminaries.

The section should be concise, but not at the cost of omitting essential
research directions or relevant baselines.

### 4.3 End categories with relevant, fair limitations

A category should normally close by identifying a limitation that
matters to the current paper. Keep the limitation at the category level
rather than delivering a long critique of each cited work.

Criticism must be specific and defensible. Prefer qualified wording such
as "often focuses on," "may be less suitable when," or "does not
explicitly model" when the evidence supports only a scoped claim. Avoid
absolute statements such as "cannot solve" unless the claim is
demonstrably true under the stated conditions.

Do not portray previous methods as weaker than they are, conflate their
assumptions, or infer a limitation merely because a method does not use
the proposed paper's design.

### 4.4 Make citation use meaningful

Citations should support specific technical or historical claims.
Cluster citations when several works support the same point, but explain
the shared idea rather than leaving a citation list to carry the
argument.

Do not assume a paper supports a claim from its title, venue, or
abstract alone when the claim requires details from the full text. If a
source cannot be checked, mark the claim for verification rather than
presenting it as confirmed.

Never fabricate author names, titles, years, venues, citation keys, or
findings. If the user requests a draft before references are available,
use clearly marked citation placeholders or identify the evidence still
needed.

### 4.5 Avoid duplication across sections

-   **Introduction:** concise background, problem importance, core
    limitations, research gap, and contributions.
-   **Related Work:** classification and synthesis of existing research,
    with fair category-level limitations.
-   **Method:** the proposed method's design, formalization, and
    technical details.
-   **Experiments:** comparative evidence, including which baselines are
    evaluated and how.

These roles can overlap in subject matter, but should not repeat the
same explanation without a clear purpose.

### 4.6 Do not impose a domain-specific taxonomy

Do not automatically use categories such as graph clustering, attributed
graph clustering, hypergraph learning, graph structure learning, or
robust clustering. These are examples suitable for some papers, not
global requirements.

Likewise, do not import a specific paper's technical terminology,
failure mode, or research gap into another paper. Reuse the reasoning
pattern only when it fits the current task and evidence.

## 5. Cross-Section Consistency Checks

### Introduction ↔ Related Work

The research gap should follow from a fair synthesis of prior work.
Ensure that the Introduction's principal limitations are actually
supported by the Related Work discussion.

### Related Work ↔ Method

Do not criticize a limitation that the proposed method does not address.
Conversely, ensure that Related Work provides enough context for readers
to understand why the paper's actual design is relevant.

### Related Work ↔ Experiments

Check that the major baseline families used in experiments are
represented appropriately. Do not claim comprehensive coverage if
relevant categories or recent methods have not been checked.

### Related Work ↔ References

Ensure each cited method is correctly identified and each citation
supports the statement it accompanies. Preserve citation keys and
formatting conventions unless a change is required and authorized.

## 6. Common Failure Modes

Avoid the following:

-   Listing papers one by one without comparing or synthesizing them.
-   Creating too many subsections or using a taxonomy unrelated to the
    paper's research question.
-   Using a fixed taxonomy copied from an unrelated paper.
-   Giving broad field background that belongs in the Introduction.
-   Repeating the same research gap at the end of every paragraph.
-   Making absolute or unfair criticisms of previous methods.
-   Claiming that no prior work exists without adequate literature
    verification.
-   Omitting important or recent baselines from the discussion.
-   Adding citations that do not substantiate the associated claim.
-   Treating citation quantity as a substitute for a coherent argument.
-   Describing the proposed method as the inevitable solution before the
    literature has been fairly analyzed.
-   Polishing prose while leaving the taxonomy or reasoning defective.

## 7. Output Modes

Adapt the deliverable to the user's request:

-   **Diagnosis:** identify the most consequential structural, coverage,
    citation, and argument problems, then propose concrete fixes.
-   **Taxonomy design:** recommend subsection headings and explain the
    classification criterion and how each category supports the paper's
    positioning.
-   **Rewrite or drafting:** provide the complete revised section when
    practical; preserve verified claims and existing citation keys.
-   **Citation or baseline audit:** report missing coverage, unsupported
    statements, and items requiring verification. Do not silently invent
    replacement references.
-   **Consistency review:** identify mismatches with the Introduction,
    Method, or experimental baseline list without expanding the scope
    into an unnecessary full-paper rewrite.

When a change depends on a new literature search or an unverified claim,
state that dependency explicitly. Do not claim to have checked sources,
updated a bibliography, or modified external files unless that work was
actually performed.

## 8. Final Quality Checklist

Before returning substantive Related Work work, check:

-   [ ] The taxonomy fits the current paper rather than a fixed domain
    template.
-   [ ] The number and scope of subsections are justified.
-   [ ] The section synthesizes research paradigms instead of listing
    papers individually.
-   [ ] Relevant foundational and recent work has been considered.
-   [ ] Experimental baselines are appropriately covered.
-   [ ] Representative methods are described accurately and meaningfully
    compared.
-   [ ] Each category's limitation is relevant, fair, and
    evidence-based.
-   [ ] The limitations align with the Introduction's research gap.
-   [ ] The proposed method is not credited with addressing problems it
    does not solve.
-   [ ] Citations support the claims attached to them; unverified items
    are flagged.
-   [ ] No citations, findings, or novelty claims have been invented.
-   [ ] The section avoids unnecessary repetition of the Introduction
    and Method.
-   [ ] Terminology, citation keys, and bibliography style remain
    consistent.
-   [ ] The final output matches the user's requested format and scope.

## 9. Mentor-Derived Guidance and Example Boundaries

The main mentor-derived rules for this module are:

-   Keep Related Work focused and classified rather than turning it into
    a broad survey.
-   Prefer two or three paradigm-based subsections when appropriate.
-   Ensure experimental baselines are covered.
-   End each category with a concise limitation relevant to the paper.
-   Keep those limitations aligned with the Introduction's main
    motivation.
-   Reserve deeper motivation and criticism for the Introduction.

These rules are grounded primarily in
`Longlong_Lin_wechat_advice_notes(6).md`, especially Advice 20, and are
supplemented by `Longlong_Lin_style_HGSC_Codex_Guide(6).md`. The five
reviewed papers provide examples of task-based and paradigm-based
organization. Their specific taxonomies and technical claims are
illustrative only: they must not be copied as universal rules or
transferred to a new paper without checking relevance and evidence.
