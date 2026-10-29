---
description: Guidance for designing, writing, revising, and auditing
  academic experiments. Ensure fair comparisons, traceable evidence,
  clear result interpretation, and conclusions that do not exceed the
  reported results.
name: experiments
---

# Experiments --- Section Skill

## 1. Purpose and Scope

This skill guides the planning, drafting, revision, and audit of an
academic paper's Experiments section.

The goal is to establish whether the proposed method works, under which
conditions it works, how it compares with relevant alternatives, and
whether the evidence supports the paper's methodological claims.

A strong Experiments section is not a collection of tables and plots.
Each experiment should answer a clear research question, use an
appropriate protocol, report results transparently, and connect the
observations to the method's actual design.

Follow the root `SKILL.md` and preserve the reported data and
experimental facts. Never invent results, claim an experiment was run
when it was not, hide inconvenient outcomes, or strengthen a conclusion
beyond the available evidence.

## 2. Required Context and Evidence

Before drafting or substantially revising the Experiments section,
inspect the available materials:

-   The current manuscript, especially the Introduction, Methodology,
    and claimed contributions.
-   Dataset descriptions, preprocessing steps, data splits, and
    ground-truth semantics.
-   Baseline implementations, versions, hyperparameters, and tuning
    protocols.
-   Evaluation metrics and the exact evaluation procedure.
-   Raw results, logs, seeds, tables, plots, and scripts when available.
-   Runtime, memory, hardware, and failure records for efficiency or
    scalability claims.
-   Explicit author, mentor, and venue requirements.

Use actual experiment outputs and verified protocol details as the
primary evidence. Do not infer unreported values from a plot when exact
values are required, and do not claim to have inspected logs or code
unless they were available.

If an important detail is missing, flag it or ask for it. Distinguish
clearly between experiments that were completed but not reported,
experiments that are reported in an appendix, and experiments that were
not conducted.

## 3. Recommended Workflow

### Step 1: Identify the requested operation

Determine whether the task is experimental planning, setup writing,
baseline audit, result interpretation, ablation analysis, sensitivity
analysis, robustness analysis, efficiency analysis, visualization, or a
final evidence audit.

Keep the response proportional to the request. Do not rewrite the whole
section when the user requests a focused paragraph revision.

### Step 2: Map claims to experiments

Build an internal claim-to-evidence map before drafting. For each major
claim, identify the experiment that supports it and the relevant result.

Typical relationships include:

-   Overall effectiveness -\> comparison with relevant baselines on
    appropriate datasets and metrics.
-   Component necessity -\> ablation or controlled replacement
    experiments.
-   Parameter stability -\> sensitivity analysis.
-   Noise tolerance or missing-information handling -\> controlled
    robustness experiments.
-   Efficiency or scalability -\> runtime, memory, and scaling
    measurements.
-   A learned structural property -\> a suitable structure-quality
    measure, controlled analysis, or case study.

This list is illustrative, not a mandatory experiment checklist. Include
experiments that answer the paper's actual research questions. If a
claim has no supporting experiment, flag the evidence gap rather than
writing as though it were verified.

### Step 3: Audit the experimental setup

Check that the setup explains the information readers need to understand
and reproduce the experiments:

-   Datasets and relevant characteristics.
-   Baselines and why they represent relevant alternatives.
-   Evaluation metrics and their interpretation.
-   Data preprocessing and evaluation protocol.
-   Hyperparameters and tuning procedures.
-   Implementation details, software, hardware, and relevant runtime
    settings.
-   Random seeds, number of runs, and aggregation method, when
    applicable.

Include the details required by the actual method and venue. Do not add
irrelevant implementation trivia, but do not omit a setting that
materially affects the comparison.

### Step 4: Audit baseline coverage and fairness

Check whether the baseline set covers the main relevant research
paradigms and includes recent, directly relevant methods where
available.

For each baseline, verify: - Its identity and implementation or
publication source. - Whether official code or validated
dataset-specific defaults are available. - Which hyperparameters were
tuned and under what protocol. - Whether its evaluation conditions match
those of the proposed method. - Whether failures, timeouts, or memory
limitations are documented.

Do not silently remove a relevant baseline because it is difficult to
reproduce or computationally expensive. Report a failure transparently
using an accurate status such as `Timeout`, `OOM`, or `--`, with a clear
explanation where appropriate.

### Step 5: Analyze the main results

Use a reasoning sequence such as:

1.  State the main overall observation.
2.  Support it with a small number of representative values or patterns.
3.  Explain plausible reasons, grounded in the method and evidence.
4.  Connect the observation to the paper's research claims.
5.  State limitations or exceptions when they materially affect the
    conclusion.

Do not rewrite every cell of a result table in prose. Select evidence
that supports the key observations.

If the proposed method is not best on every dataset or metric, describe
its actual pattern of strengths and weaknesses. Consider average rank or
another justified aggregate summary when multiple datasets and metrics
make an overall comparison useful. Explain the aggregation protocol and
do not use rank as a substitute for inspecting the underlying results.

### Step 6: Analyze ablations

Each ablation should test a specific design choice or claim. For each
ablation:

-   State what component or choice is removed, replaced, or changed.
-   Clarify what hypothesis the experiment tests.
-   Report the observed difference.
-   Interpret the result without treating correlation as definitive
    causal proof.
-   Explain what the result supports and what it does not establish.

Prefer controlled comparisons in which the intended component is the
principal change. If several settings change simultaneously, acknowledge
that the result cannot isolate the contribution of one component.

Do not automatically conclude that every component is necessary or
complementary. Those conclusions must follow from the observed evidence
and the experiment design.

### Step 7: Analyze sensitivity and robustness separately

Sensitivity analysis studies how performance changes as selected
hyperparameters or design settings vary. State which parameter is
varied, which settings are held fixed, and what trend is observed.

Robustness analysis studies performance under defined changes to the
data or experimental conditions, such as noise, missing information,
perturbations, or scale changes. State the perturbation procedure and
intensity clearly, and compare methods under consistent conditions.

Do not use "robust" as a generic synonym for "good performance." A
robustness claim must be tied to the perturbation or uncertainty
actually tested.

### Step 8: Analyze efficiency and scalability

For runtime, memory, and scalability claims, specify the relevant
hardware, software, data scale, measurement procedure, and whether
preprocessing or repeated runs are included.

Distinguish: - Theoretical time or space complexity. - Measured runtime
or memory usage. - Performance as the dataset size or another scale
variable changes.

Use comparable measurement conditions for baselines whenever possible.
Explain deviations that materially affect fairness. Do not infer
large-scale scalability from a single small dataset or report the cost
of one subroutine as the cost of the whole method.

### Step 9: Audit figures, tables, and statistics

For each table and figure, check: - The title, caption, labels, units,
and notation are clear. - Reported values match the underlying
results. - The meaning of boldface, underlining, error bars, and
missing-value markers is defined. - The same metric and evaluation
protocol are used in comparisons. - Rounding does not change rankings or
imply unsupported precision. - Any reported averages, ranks, confidence
intervals, or significance tests use a stated and appropriate procedure.

Use statistical significance language only when an appropriate test or
interval supports it. Do not infer significance from a small numerical
difference, overlapping or non-overlapping error bars without checking
the relevant method, or visual inspection alone.

### Step 10: Explain omissions and anomalies

Inspect whether relevant datasets, metrics, parameters, baselines, or
experiment types are omitted.

For every material omission, distinguish among: - Results completed but
omitted for space. - Results reported in the appendix or supplementary
material. - Experiments not conducted. - Experiments that failed due to
a documented technical limitation.

Do not claim that omitted experiments show similar trends unless those
experiments were actually conducted. If a baseline times out or runs out
of memory, report the limitation accurately. If results are unexpected
or inconsistent, investigate them or describe the uncertainty rather
than inventing a convenient explanation.

### Step 11: Perform the final evidence audit

Check every empirical claim against the actual table, plot, log, or
result file. Verify that conclusions align with the Introduction's
claims and the Methodology's intended mechanisms.

Report contradictions explicitly. Do not silently edit a number, discard
an unfavorable result, or change the experimental interpretation to fit
the desired narrative.

## 4. Core Writing Rules

### 4.1 Use observation, interpretation, and implication

Organize result analysis around three distinct functions:

-   **Observation:** what the reported results show.
-   **Interpretation:** why the pattern may occur, based on the method
    or additional evidence.
-   **Implication:** what the evidence supports about the research
    question.

These functions need not appear as three separate sentences. They should
remain logically distinguishable.

Do not confuse an observed result with its explanation. If the reason
for a result has not been tested, present it as a possible explanation,
not as a proven mechanism.

### 4.2 Be comprehensive without making unsupported coverage claims

Include enough datasets, metrics, and baselines to make the evaluation
credible for the task and venue. Relevant recent methods should not be
omitted merely because they are inconvenient to reproduce.

Mentor guidance gives six or more datasets and eight or more baselines
as useful targets for many graph-clustering submissions. Treat these as
context-dependent heuristics, not universal requirements. The correct
scope depends on the research problem, available benchmarks, paper type,
and evaluation conventions.

Do not write "comprehensive comparison" or "extensive experiments"
unless the actual coverage supports that description.

### 4.3 Describe baseline tuning transparently

Use a fair and explicit tuning protocol.

-   When an official implementation provides validated dataset-specific
    default parameters, use them when appropriate and state that choice.
-   When relevant defaults are unavailable, tune key hyperparameters
    under a reasonable and consistent protocol.
-   Explain the tuning procedure for reimplemented or non-open-source
    baselines.
-   Report the protocol actually used, not an idealized one.
-   Do not claim Bayesian optimization, grid search, or another
    procedure unless it was actually used.

Do not selectively report a weak baseline configuration while giving the
proposed method extensive tuning. If protocols differ for a justified
reason, disclose the difference.

### 4.4 Report overall performance without hiding exceptions

When results span multiple datasets and metrics, an average-rank summary
may help communicate overall competitiveness. Define how ranks are
computed, how ties are handled if relevant, and how metric-level ranks
are aggregated.

Do not claim that the method wins on every dataset or metric unless the
table confirms it. Distinguish best individual scores, aggregate rank,
consistency, and statistical evidence. An overall rank does not erase
meaningful weaknesses on particular datasets.

### 4.5 Use metrics that match the task

Confirm that metrics are suitable for the target problem and
ground-truth semantics.

For clustering or community-related tasks, verify whether the ground
truth is single-label or overlapping and whether the method's output
matches the evaluation protocol. State any relevant conversion or
evaluation assumptions. If standard metrics do not fully capture the
task, consider whether a complementary measure is needed and justified.

Define nonstandard metrics and explain their interpretation. Do not
report a metric simply because it is common if it does not support the
claim being made.

### 4.6 Handle missing, failed, and omitted results honestly

Use consistent markers for unavailable results and define them in a
caption or footnote. Distinguish a method that was not evaluated from
one that failed to complete.

-   `OOM` should mean an observed out-of-memory failure.
-   `Timeout` or `>24h` should match the actual time limit.
-   `--` should have a clearly stated meaning.
-   Missing results should not be silently treated as zero or excluded
    from aggregate statistics without explanation.

If space is limited, place complete results in an appendix when
appropriate and explain the main-text selection. Do not claim similar
trends for unrun experiments.

### 4.7 Make ablation conclusions proportional to the design

Ablations are strongest when they isolate a clear design decision.
Explain what each variant changes and which claim it tests.

A performance decrease after removing a component supports the
usefulness of that component under the tested setup. It does not
automatically prove that the component is universally necessary, that
its proposed mechanism is the only cause, or that it generalizes to
every dataset.

For unexpected outcomes, discuss plausible explanations only when
grounded in evidence. Do not force every ablation to confirm the
original hypothesis.

### 4.8 Keep sensitivity analysis precise

State the range and values tested, the parameter being varied, and which
other settings remain fixed. If multiple parameters interact, a
one-at-a-time study may not reveal those interactions; acknowledge this
limitation when relevant.

Use "stable within the tested range" rather than broad claims of
parameter insensitivity. Do not extrapolate beyond the settings actually
evaluated.

### 4.9 Define robustness conditions explicitly

Report the source, type, and intensity of the perturbation, along with
how it is generated and whether the same perturbations are applied to
competing methods.

Separate robustness to input noise from random-seed stability, parameter
sensitivity, missing-data tolerance, and scalability. These are
different properties and should not be conflated.

### 4.10 Use careful statistical language

Report the number of runs, aggregation method, and variability measure
where applicable. If significance is claimed, identify the statistical
procedure and ensure it matches the experimental design.

Avoid claims such as "significantly better" when only a raw score
difference is available. A confidence interval, standard deviation,
standard error, or p-value must be interpreted according to what it
actually measures.

Do not invent seeds, confidence intervals, p-values, or significance
results. If the evidence is insufficient, use descriptive language and
identify what additional analysis would be needed.

### 4.11 Keep tables and figures readable and consistent

Use consistent precision, metric names, dataset names, method names, and
notation. Define symbols and result markers in captions or footnotes.

Make each table or figure serve a clear purpose. Avoid repeating the
same results in several forms unless the different presentation reveals
a distinct pattern. Check that claims in the prose match the values and
the highlighted entries.

### 4.12 Connect evidence to the paper's claims without overclaiming

The Experiments section should evaluate the method's stated
contributions, not manufacture new contributions after observing
favorable results.

Use appropriately scoped language such as "supports," "suggests," "is
consistent with," or "under the evaluated settings" when that is the
strength of the evidence. Reserve stronger claims for results that
justify them.

## 5. Cross-Section Consistency Checks

### Experiments ↔ Introduction

Each major claimed benefit should have an appropriate experimental test
where empirical validation is required. Do not present an untested
motivation as an established experimental finding.

### Experiments ↔ Methodology

Ablations should correspond to actual method components or design
choices. Robustness tests should match the claimed robustness mechanism.
Efficiency measurements should correspond to the actual computation
pipeline.

### Experiments ↔ Related Work

The baseline set should be consistent with the paper's literature
positioning. Flag relevant methods discussed in Related Work that are
absent from evaluation, and explain when a method is not a suitable or
feasible baseline.

### Experiments ↔ Conclusion and Abstract

The Abstract and Conclusion must summarize the actual results, including
important qualifications. Do not use stronger performance claims in the
summary than the experiments support.

### Experiments ↔ Code and Logs

Where source code and raw records are available, verify that reported
numbers, settings, seeds, and failure statuses match them. If the
artifacts are unavailable, state that the results could not be
independently checked rather than implying verification.

## 6. Common Failure Modes

Avoid the following:

-   Reporting results without explaining their significance to the
    research question.
-   Repeating table entries instead of synthesizing the main
    observations.
-   Claiming state-of-the-art performance when the method is not best
    under the reported comparison.
-   Omitting relevant recent baselines because they are difficult to
    reproduce.
-   Using inconsistent or undisclosed tuning protocols.
-   Hiding timeouts, out-of-memory failures, or unrun experiments.
-   Claiming untested omitted results follow the same trend.
-   Treating one ablation as proof of a universal mechanism.
-   Describing parameter stability without stating the tested range.
-   Claiming robustness without specifying the perturbation.
-   Claiming statistical significance without an appropriate analysis.
-   Using metrics that do not match the task or ground-truth semantics.
-   Reporting runtime without comparable hardware or measurement
    conditions.
-   Inferring scalability from insufficient scale experiments.
-   Explaining unexpected results with unsupported speculation.
-   Using average rank to obscure important weaknesses.
-   Allowing table values, captions, and prose to contradict one
    another.
-   Claiming that experiments prove a theoretical guarantee they do not
    test.
-   Writing "comprehensive" or "extensive" without evidence of
    sufficient coverage.

## 7. Output Modes

Adapt the deliverable to the user's request:

-   **Experimental plan:** map each research claim to a testable
    question, protocol, metric, and evidence requirement.
-   **Setup drafting:** write the dataset, baseline, metric, parameter,
    and implementation descriptions from verified information.
-   **Baseline audit:** identify missing relevant methods, tuning
    inconsistencies, and undocumented failures.
-   **Main-result analysis:** synthesize the strongest observations,
    representative values, exceptions, and supported implications.
-   **Ablation analysis:** connect each variant to the hypothesis it
    tests and interpret the observed differences.
-   **Sensitivity or robustness review:** audit the tested ranges or
    perturbation protocol and ensure claims remain within scope.
-   **Efficiency analysis:** examine complexity claims, runtime, memory,
    and scale measurements.
-   **Table or figure audit:** check labels, values, captions,
    formatting, missing-value markers, and consistency with prose.
-   **Statistical audit:** review the number of runs, variability
    summaries, rank calculations, and significance claims.
-   **Final evidence audit:** map empirical statements to the underlying
    evidence and list unsupported or unresolved claims.

If the necessary raw results or experimental details are missing,
identify the specific gap. Do not fill it with invented values or claim
that an experiment was run.

## 8. Final Quality Checklist

Before returning substantive Experiments work, check the applicable
items:

-   [ ] Each major empirical claim maps to a suitable experiment.
-   [ ] Dataset selection and evaluation protocol are clear.
-   [ ] Relevant classical and recent baselines have been considered.
-   [ ] Baseline tuning is fair, consistent, and transparently
    described.
-   [ ] Metrics match the task and ground-truth semantics.
-   [ ] The number of runs and aggregation procedure are stated where
    relevant.
-   [ ] Main-result analysis emphasizes patterns rather than listing
    numbers.
-   [ ] Claims accurately describe per-dataset and overall performance.
-   [ ] Average rank or other aggregate summaries are correctly computed
    and interpreted.
-   [ ] Each ablation tests a clear design choice.
-   [ ] Sensitivity ranges and fixed settings are explicit.
-   [ ] Robustness perturbations and intensities are specified.
-   [ ] Efficiency measurements use clear and comparable conditions.
-   [ ] Statistical claims are supported by appropriate analyses.
-   [ ] Tables, figures, captions, and prose agree.
-   [ ] Missing, omitted, failed, and unrun experiments are
    distinguished.
-   [ ] No result, seed, statistic, or experiment has been invented.
-   [ ] Explanations of unexpected outcomes are evidence-grounded or
    explicitly tentative.
-   [ ] Conclusions do not exceed the experimental evidence.
-   [ ] Experimental claims are consistent with the Methodology,
    Introduction, Abstract, and Conclusion.

Do not mark a check as complete if the necessary result files, logs, or
protocol details were unavailable.

## 9. Mentor-Derived Guidance and Evidence Boundaries

The primary mentor-derived guidance for this module comes from
`Longlong_Lin_wechat_advice_notes(6).md`, especially:

-   **Advice 1:** consider `Avg.Rank` or `Overall Avg.Rank` when useful
    for summarizing performance across datasets and metrics; do not
    claim universal wins if the results do not show them.
-   **Advice 2:** explain omitted datasets, metrics, parameters, or
    baselines honestly; distinguish completed-but-omitted results from
    experiments not conducted.
-   **Advice 3:** include relevant recent baselines and report timeout
    or memory failures transparently.
-   **Advice 4:** state the baseline tuning protocol in Experimental
    Setup and describe only the tuning procedure actually used.
-   **Advice 24:** provide an experimental setup that covers datasets,
    baselines, parameters, and implementation details; use appropriate
    combinations of main results, ablations, sensitivity, robustness,
    scalability, visualization, and structural analysis.

The suggestion that six or more datasets and eight or more baselines can
be useful for many graph-clustering submissions is a mentor-provided
heuristic, not a universal threshold.

`Longlong_Lin_style_HGSC_Codex_Guide(6).md` provides domain-specific
examples for organizing experiment subsections and analyzing main
results, ablations, sensitivity, and robustness. Treat its
hypergraph-specific hypotheses and sample explanations as examples only.
Do not reuse a sample explanation unless the current method and results
support it.

The five reviewed papers may be used to study experimental organization
and evidence presentation. Their datasets, baselines, numbers,
conclusions, and task-specific protocols must not be copied into a new
paper without independent verification.
