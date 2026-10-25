# Longlong Lin WeChat Advice Notes for Codex

> Intended use: give this file to Codex / ChatGPT / an AI writing assistant when revising an AAAI / KDD / WWW-style graph clustering, hypergraph clustering, or attributed hypergraph clustering paper.
>
> Scope: this file summarizes practical writing, experiment, rebuttal, formatting, and submission advice distilled from LLLin@swu's WeChat comments.
>
> Important: use these notes as **paper-writing and quality-control guidance**, not as text to copy into the paper. Preserve technical correctness and do not invent results.

---

## 0. Core Principle

A paper should not only have good experimental results. It must also avoid obvious reviewer attack points.

The main risks are:

1. incomplete or outdated baselines;
2. unclear baseline tuning protocol;
3. missing explanation for omitted results;
4. weak or selective metric reporting;
5. unclear motivation due to poor baseline taxonomy;
6. mismatch between ground truth and clustering protocol;
7. AI-like writing style;
8. poor figure/table appearance;
9. formula or implementation details creating unnecessary theoretical loopholes;
10. anonymity violations in code or supplementary materials.

When revising a paper, Codex should check these risks explicitly.

---

# Part I. Experiment Presentation and Reviewer Defense

## Advice 1: Add average rank to the main result table

Reviewers often ask why the proposed method performs worse on some datasets or metrics. To reduce this concern, add an `Avg.Rank` column or row to the main comparison table.

This helps show that even if the method is not best everywhere, its overall ranking is strong.

### Rules

1. Add `Avg.Rank` or `Overall Avg.Rank` to the main comparison table whenever possible.
2. If multiple metrics are used, consider reporting metric-level ranks and overall rank.
3. Do not claim the method is best on every dataset unless it is true.
4. Use overall rank to support claims about stability and competitiveness.
5. In analysis, state that the method achieves strong overall performance rather than overfitting to a single dataset.

### Recommended expressions

```text
Although HGSC does not achieve the best result on every dataset, it obtains the best overall average rank across all metrics. This indicates that HGSC provides consistently competitive performance rather than overfitting to a specific dataset.
```

```text
The average rank further confirms the overall superiority of HGSC.
```

If the method is not first overall:

```text
The average rank shows that HGSC remains highly competitive across different datasets and metrics.
```

### Codex instruction

```text
Check the main result table. If the proposed method is not best on every dataset, suggest adding an Avg.Rank column or row. Revise the analysis to emphasize overall ranking, stability, and competitiveness without overclaiming.
```

---

## Advice 2: Explain omitted experiments to avoid writing loopholes

If some datasets, metrics, parameters, or baselines are not reported, briefly explain the reason. This avoids the impression of selective reporting.

### Common cases

1. The omitted results were tested and show similar trends.
2. The table or figure would be too large.
3. A baseline cannot finish due to time or memory cost.
4. The omitted results are provided in the appendix.

### Recommended expressions

For similar trends:

```text
We report the results on representative datasets, while similar trends can be observed on the remaining datasets.
```

```text
The results under other evaluation metrics are consistent with the reported observations and are omitted for brevity.
```

For parameter studies:

```text
For clarity, we vary one parameter at a time and keep the others fixed. Similar trends are observed under other settings.
```

For timeout:

```text
On large-scale datasets, several baselines fail to produce results within 24 hours due to excessive time or memory costs. We mark these cases as "--" in the table.
```

For out-of-memory:

```text
Some baselines run out of memory on large datasets, so their results are marked as OOM.
```

### Rules

1. Do not claim similar trends unless the experiments were actually conducted.
2. If the experiment was not conducted because of cost, state the computational limitation honestly.
3. Use `similar trend` or `similar trends`, not `similar tread`.
4. Prefer appendix for complete results when main text is limited.

### Codex instruction

```text
Check whether any datasets, metrics, parameters, or baselines are omitted. Add a short explanation for each omission. If the omitted results were conducted, mention similar trends or appendix. If not conducted due to cost, state timeout or memory limitation honestly.
```

---

## Advice 3: Recent and comprehensive baselines are critical

Reviewers usually do not care how difficult it is to reproduce baselines or how time-consuming it is to run large-scale experiments. They mainly check whether the comparison is sufficiently recent and comprehensive.

If recent methods are missing, some reviewers may directly reject the paper.

### Rules

1. Include recent baselines, especially methods from the last two years if they are relevant.
2. Do not omit baselines simply because they are slow on large datasets.
3. If a baseline cannot finish, report it as `Timeout`, `OOM`, `>24h`, or `--` with a clear footnote.
4. Avoid using reproduction difficulty as the main written excuse.
5. Before submission, check whether reviewers can attack the paper by saying "recent methods are missing" or "the comparison is incomplete".

### Recommended expressions

```text
We compare with representative and recently published baselines.
```

```text
"--" indicates that the method fails to produce results within 24 hours.
```

```text
Some baselines cannot scale to large datasets due to excessive time or memory costs.
```

```text
We include both classical and recent methods to ensure a comprehensive comparison.
```

### Codex instruction

```text
Check whether the baseline list includes both classical and recent methods. If a relevant recent baseline is missing, flag it. If a baseline is too slow or runs out of memory, keep it in the table and mark it as Timeout, OOM, or "--" rather than removing it silently.
```

---

## Advice 4: State the baseline tuning protocol before reviewers ask

Reviewers often question whether baselines are fairly tuned. This should be addressed in the Experimental Setup rather than only in rebuttal.

### Rules

1. If a baseline provides official dataset-specific default parameters, use those validated defaults.
2. If a baseline has no default parameters for the current datasets, tune its key hyperparameters fairly.
3. If a method is not open-source and requires reimplementation, state how its parameters are tuned.
4. Report the best achieved baseline results under the same evaluation protocol.
5. Do not claim Bayesian optimization unless it was actually used.
6. Add this explanation in the Experimental Setup / Parameter Settings section.

### Recommended expression

```text
For fair comparison, we tune all baselines under a consistent protocol. If the official implementation of a baseline provides dataset-specific default parameters, we directly use these validated settings. For baselines without default parameters on our datasets, or for methods that require reimplementation, we tune their key hyperparameters and report the best achieved results.
```

If Bayesian optimization was actually used:

```text
For baselines without default parameters on our datasets, or for methods that are not publicly available and require reimplementation, we employ Bayesian hyperparameter optimization to tune their key parameters and report the best achieved results.
```

### Codex instruction

```text
Check the Experimental Setup section and add a clear baseline tuning protocol. Explain how official default parameters are used and how baselines without dataset-specific defaults or open-source implementations are tuned. Make the description transparent and fair. Do not claim Bayesian optimization unless it was actually used.
```

---

## Advice 5: Select the most suitable main metric and move other metrics to appendix

When different metrics show different levels of improvement, the main text can focus on the metric that best reflects the method's advantage. However, the remaining metrics should still be evaluated and provided in the appendix to avoid selective reporting concerns.

### Rules

1. If one metric is clearly more favorable and more aligned with the task, use it as the main metric in the main text.
2. Still run the remaining metrics and place them in the appendix.
3. Do not claim improvements on all metrics if this is not true.
4. In result analysis, emphasize clear and explainable improvements.
5. Do not over-explain minor or unclear improvements unless they are abnormal or reviewer-sensitive.
6. If some results are not strong, use careful wording such as `competitive`, `comparable`, or `remains stable`.
7. Use `Avg.Rank` to support overall performance when individual metrics vary.

### Recommended expressions

```text
Due to space limitations, complete results under all metrics are provided in Appendix X.
```

```text
HGSC achieves the best or competitive performance on most datasets.
```

```text
HGSC shows clear advantages on F1 while remaining competitive on other metrics.
```

```text
A possible explanation is that ...
```

### Codex instruction

```text
When revising the experiment section, do not force the analysis to claim that all metrics improve. Identify the metrics where the proposed method performs clearly and consistently well, and use them as the main discussion focus. If other metrics are less favorable, report them in the appendix or describe them carefully as comparable or competitive.
```

---

## Advice 6: Explain metric trade-offs when not all metrics are best

It is often unrealistic for one method to achieve the best performance on all datasets and all metrics. If the proposed method is not the best on some metrics, do not ignore this issue. Add a short remark to explain the trade-off.

### Writing logic

1. Different metrics may emphasize different aspects of clustering quality.
2. Some baselines perform well on a specific metric because their objectives are related to that metric.
3. The proposed method should be framed as achieving stronger overall performance or a better trade-off.
4. Use `Avg.Rank` to support the claim if possible.

### Recommended expression

```text
Remark. Optimizing all evaluation metrics simultaneously is challenging, since different metrics may emphasize different aspects of clustering quality. Some baselines may achieve strong performance on a specific metric because their objectives are closely related to that metric. In contrast, HGSC aims to improve the overall clustering quality by jointly considering high-order structure refinement, attribute preservation, and clustering compactness. Therefore, although HGSC may not achieve the best result on every single metric or dataset, it obtains the best overall average rank and shows consistently competitive performance across different metrics.
```

If there is no best overall rank:

```text
Therefore, although HGSC may not achieve the best result on every single metric or dataset, it remains competitive across different metrics and provides a favorable trade-off between clustering accuracy and robustness.
```

### Codex instruction

```text
If the proposed method is not best on every metric, add a concise trade-off explanation. Clarify that different metrics emphasize different clustering properties and use average rank or overall competitiveness to support the claim. Avoid pretending that all metrics improve.
```

---

# Part II. Motivation, Baseline Taxonomy, and Contribution Design

## Advice 7: Classify baselines before writing motivation

Before writing the Introduction and Related Work, first classify the baselines by their technical paradigms. Only after understanding what each category can and cannot do can the real motivation of the paper be identified.

### Rules

1. Do not treat baselines only as experimental competitors.
2. Classify them into method categories, such as attributed graph clustering, hypergraph clustering, graph structure learning, and robust graph clustering.
3. For each category, identify what it captures and what it misses.
4. Use the missing but important capabilities as the motivations of the paper.
5. In the Introduction, try to extract two clear motivations.
6. Add a property comparison table if possible to show that existing methods lack some important abilities that the proposed method considers.

### For HGSC, two suitable motivations

1. Pairwise graph clustering cannot fully capture high-order relations.
2. Fixed hypergraph clustering cannot adaptively suppress noisy incidence relations.

### Possible property comparison table

| Method Category | Attribute Information | High-order Relation | Adaptive Structure | Incidence Noise Handling | Clustering-oriented Refinement |
|---|---|---|---|---|---|
| Attributed graph clustering | ✓ | × | × / partial | × | × |
| Hypergraph clustering | ✓ / partial | ✓ | × | × | × |
| Graph structure learning | ✓ | × | ✓ | × | partial |
| Robust graph clustering | ✓ | × / partial | partial | partial | × |
| HGSC | ✓ | ✓ | ✓ | ✓ | ✓ |

### Codex instruction

```text
Before rewriting the Introduction, first classify all baselines into method categories. For each category, summarize its main capability and limitation. Then derive two motivations for the proposed method from the missing but important capabilities of existing methods. If suitable, add a property comparison table showing which categories support attribute information, high-order relation modeling, adaptive structure learning, incidence noise handling, and clustering-oriented refinement.
```

---

## Advice 8: Strong backbones improve performance but are not enough for motivation

For each graph type, first check the corresponding strong GNN models. For example, temporal graph papers should consider temporal GNNs, heterogeneous graph papers should consider heterogeneous GNNs, and hypergraph clustering papers should consider hypergraph neural networks.

However, using a stronger GNN backbone and then applying KMeans may improve performance, but this alone is not a publishable contribution. It should be treated as a performance-enhancing baseline or implementation choice, not as the core motivation.

### Rules

1. Select baselines and backbones that match the target graph type.
2. Do not frame the contribution as merely using a stronger encoder.
3. Use strong backbone + KMeans as a sanity baseline if appropriate.
4. The paper must add its own contribution beyond representation learning, such as structure refinement, new objective design, robustness analysis, or theoretical insight.
5. Avoid focusing only on performance. Explain what problem the method solves and why the design is necessary.

### For HGSC

The motivation should not be:

```text
We use a stronger hypergraph encoder.
```

Instead, use:

```text
Existing hypergraph encoders rely on fixed incidence matrices, which may propagate noisy high-order relations. Therefore, we refine the hypergraph structure in a clustering-oriented and structure-preserving manner.
```

### Codex instruction

```text
When revising the paper, make sure the motivation is not merely based on using a stronger GNN backbone. Check whether the paper clearly distinguishes between backbone-level performance improvement and the actual research contribution. For HGSC, emphasize that strong hypergraph encoders still rely on fixed incidence matrices, while the contribution is clustering-oriented and structure-preserving hypergraph refinement.
```

---

## Advice 9: Build the first draft from a mature paper structure, but rewrite with strict content replacement

A practical way to form the first draft is to start from a mature paper with a similar topic or venue style. Keep the useful structure and paragraph functions, remove content that does not belong to the current work, and replace the remaining parts with the current paper's own problem, method, experiments, and conclusions.

This means using a mature paper as a structural reference, not copying its text.

### Rules

1. Use the reference paper as a structural template, not as text to copy.
2. Preserve section organization, paragraph function, experiment layout, and writing rhythm if they fit the paper.
3. Delete content that is not related to the method.
4. Replace all technical claims, motivations, formulas, experiments, and conclusions with the current paper's own content.
5. After forming the first draft, use GPT/Codex to rewrite it in KDD/WWW style.
6. The prompt must explicitly require the model to preserve the original meaning and not delete important content.
7. Do not rely on AI to "avoid plagiarism" by superficial paraphrasing. The final text must be genuinely based on the current paper's own contribution and results.

### Recommended prompt

```text
Revise this section following KDD/WWW academic writing style. Preserve the original meaning, technical claims, equations, citations, and experimental results. Do not remove important content unless it is clearly redundant. Improve clarity, logic, and academic tone. Avoid AI-like expressions and overuse of colons, semicolons, and em dashes.
```

### Codex instruction

```text
Use the provided mature paper only as a structural reference. Keep useful section organization and paragraph functions, but rewrite all content based on our own HGSC problem, method, and experiments. Remove unrelated content. Preserve all technical meaning, equations, citations, and experimental results from our draft. Do not delete important content without explanation. Revise the writing according to KDD/WWW style, improve clarity and logic, and reduce AI-like expressions.
```

---

# Part III. Evaluation Protocol and Ground-truth Semantics

## Advice 10: Check whether ground-truth clusters are overlapping

Before reporting F1, NMI, ACC, or ARI, check whether the ground-truth clusters are overlapping. If the ground truth allows one node to belong to multiple communities while the method outputs a non-overlapping partition, standard clustering metrics may be unfavorable or not fully aligned with the task.

### Rules

1. Check whether each dataset has single-label or multi-label ground truth.
2. If the proposed method outputs non-overlapping clusters, state the evaluation protocol clearly.
3. If overlapping ground truth exists, explain that the reported metrics are computed under the standard non-overlapping evaluation protocol.
4. Consider adding complementary analyses such as structure quality, robustness, visualization, or average rank.
5. Do not ignore this issue, because reviewers may question whether the evaluation is fair.

### Recommended expression

```text
Some ground-truth communities may contain overlapping nodes, while the evaluated clustering methods output non-overlapping partitions. Therefore, the reported F1 and NMI scores should be interpreted under this non-overlapping evaluation protocol.
```

### Codex instruction

```text
Check the experimental setup and dataset descriptions. Determine whether the ground-truth clusters are single-label or overlapping. If any dataset contains overlapping ground-truth communities while our method outputs non-overlapping clusters, add a clear explanation of the evaluation protocol. Make sure F1, NMI, ACC, and ARI are not presented as fully fair without clarification.
```

---

## Advice 11: Check whether the ground truth matches the graph structure

Some datasets define ground-truth clusters by communities, while others define them by semantic class labels. In class-label datasets, nodes from the same class may be far apart in the original graph. In this case, local graph clustering objectives such as Ncut may be less effective, because the evaluation target is not purely local community structure.

### Rules

1. Check whether ground-truth labels are community-based or class-based.
2. Use visualization or distance statistics to examine whether nodes from the same class are structurally close.
3. If same-class nodes are far apart, explain that local graph objectives may be disadvantaged.
4. PPR/RWR-based graph construction can help capture long-range dependencies and alleviate the long-term relation problem.
5. Tune PPR hop number or teleport probability carefully, because they control how far the constructed proximity can reach.
6. Be careful when explaining alpha, since its meaning depends on the exact PPR formulation.

### Recommended expressions

```text
The PPR-based auxiliary graph helps capture long-range structural dependencies that are difficult to preserve with purely local message passing.
```

```text
Some datasets use semantic class labels as ground truth, where nodes from the same class may be structurally distant. This makes purely local graph objectives less aligned with the evaluation protocol.
```

### Note on PPR alpha

For the common PPR formulation:

```math
\pi = \alpha s + (1-\alpha)P\pi
```

- larger `alpha` means stronger restart, more local proximity;
- smaller `alpha` means longer random walks, more long-range information.

If the implementation defines alpha differently, adjust the explanation accordingly.

### Codex instruction

```text
Check whether the experimental datasets use community-based ground truth or class-based ground truth. If some datasets use class labels where same-class nodes may be far apart, add a short discussion explaining why purely local graph objectives may be less aligned with the evaluation protocol. If the method uses PPR/RWR or auxiliary graph construction, explain how it helps capture long-range dependencies. Check the definition of alpha carefully before describing whether larger or smaller alpha makes PPR more local.
```

---

# Part IV. Writing Style and Anti-AI Trace Control

## Advice 12: Avoid ChatGPT-style punctuation patterns

In academic writing, avoid overusing colons, semicolons, and em dashes in explanatory sentences. A common ChatGPT-style pattern is:

```text
A key advantage of X is Y: ...
```

This pattern looks mechanical and should be rewritten in a more natural academic style.

### Bad

```text
A key advantage of HGSC is its lightweight design: it introduces no additional generative modules and remains highly efficient.
```

### Better

```text
HGSC is lightweight since it does not introduce additional generative modules, which helps maintain high efficiency.
```

### Rules

1. Do not overuse colon-based explanatory structures in the main text.
2. Avoid frequent em dashes for inserted explanations.
3. Prefer natural academic connectors such as `because`, `since`, `therefore`, `which`, and `thus`.
4. Split sentences when needed.
5. Colons can still be used in titles, tables, definitions, and formal lists when necessary, but avoid using them repeatedly in prose.
6. Before submission, scan the manuscript for AI-like patterns such as `The key idea is:`, `A key advantage is:`, and `This brings two benefits:`.

### Codex instruction

```text
Revise the manuscript to reduce ChatGPT-style punctuation patterns. In the main prose, avoid overusing colons, semicolons, and em dashes, especially patterns like "A key advantage of X is Y: ...". Rewrite such sentences using natural academic connectors or split them into separate sentences. Keep colons only when they are necessary for definitions, tables, titles, or formal lists.
```

---

## Advice 13: Spend writing effort on key arguments

Do not over-write familiar background while briefly passing over the key argument. Background can be concise, but the central motivation, method design, and reviewer-sensitive explanations must be carefully written.

Every sentence should have a clear function.

### Rules

1. Keep general background concise.
2. Expand the key motivation and technical rationale.
3. Directly answer potential reviewer concerns.
4. Remove repeated or empty sentences.
5. Make every sentence contribute to the paper's argument.

### For HGSC, key arguments include

1. Why fixed hypergraph structure is insufficient.
2. Why dynamic refinement is necessary.
3. Why the method is robust to incidence noise.
4. Why the method may not be best on every metric but is strong overall.
5. Why the baseline comparison is fair.

### Codex instruction

```text
Revise the writing so that familiar background is concise and key arguments are fully explained. Remove repeated or empty sentences. Make sure the motivation, method rationale, and reviewer-sensitive explanations are not passed over too quickly.
```

---

## Advice 14: Use AI for pre-submission review and quality control

Before submission, the paper should be reviewed by a strong AI model under AAAI/KDD/WWW reviewing standards. The goal is to repeatedly revise the paper until it reaches at least a weak accept or borderline level in simulated review.

### Rules

1. Prepare a sufficiently complete manuscript. For AAAI/KDD-style papers, the main text is usually around 7-8 pages excluding references, and the appendix can include extra proofs, experiments, and detailed settings.
2. Use AI to strengthen theoretical analysis, proof organization, and experiment interpretation, but verify all claims carefully.
3. Before submission, check hallucination issues, especially references and unsupported claims.
4. Remove AI-like writing patterns and polish grammar, wording, and typos.
5. Make the framework figure and experimental figures professional. Figures are the first impression of the paper and should not be neglected.
6. Do not focus only on technical details while ignoring presentation quality.

### Codex instruction

```text
Simulate an AAAI/KDD/WWW reviewer. Review this paper strictly and identify weaknesses in novelty, motivation, baseline comparison, experimental design, clarity, writing quality, figures, and reproducibility. Then suggest revisions aimed at reaching at least a borderline or weak accept level. Do not invent results or references.
```

---

# Part V. Formula, Loss Function, and Method Writing Precision

## Advice 15: Do not expose numerical stabilizers in main mathematical formulas

Avoid adding unnecessary epsilon, tau, or other small constants directly in the main formulas of the paper. Such terms often come from implementation-level numerical stabilization, such as avoiding division by zero, singular matrices, or overflow.

If they are written into the paper formula, reviewers may question whether the objective function has changed or whether the theoretical derivation still holds.

### Rules

1. Keep the main mathematical objective clean.
2. Do not write `+\epsilon` or `+\tau` in formulas unless it is essential to the method.
3. If the stabilizer is only used in code, mention it briefly in implementation details.
4. Do not let code-level tricks become theory-level claims.
5. If a stabilizer must appear in the formula, explain its role, default value, and whether it affects the objective.

### Recommended expression

```text
For numerical stability, we add a small constant to denominators in implementation.
```

### Codex instruction

```text
Check all mathematical formulas in the manuscript. If there are unnecessary epsilon, tau, or small stabilizer terms such as +1e-6 in denominators, remove them from the main paper formulas unless they are part of the actual theoretical objective. Treat these terms as implementation-level numerical stabilizers. If needed, mention them briefly in implementation details rather than in the main formula.
```

---

## Advice 16: Clarify the level of reconstruction loss in graph clustering

In graph clustering papers, reconstruction loss should not be vaguely described as autoencoder reconstruction. Reconstruction can happen at different levels, such as node level, edge level, incidence level, and cluster level.

### Rules

1. Before defining a reconstruction loss, specify what is reconstructed.
2. Node-level reconstruction usually preserves node attributes or node embeddings.
3. Edge-level reconstruction usually reconstructs adjacency or pairwise structural proximity, such as \(H_iH_j^\top - A_{ij}\).
4. Incidence-level reconstruction preserves node-hyperedge associations or high-order structure.
5. Cluster-level reconstruction aligns node embeddings with cluster prototypes or cluster-level representations.
6. Do not confuse graph reconstruction loss with ordinary autoencoder feature reconstruction.

### Recommended expressions

```text
We introduce a node-level reconstruction loss to preserve attribute information.
```

```text
We introduce an edge-level reconstruction loss to preserve pairwise structural proximity.
```

```text
We introduce an incidence-level reconstruction loss to preserve high-order node-hyperedge associations.
```

```text
We introduce a cluster-level reconstruction loss to align node embeddings with cluster prototypes.
```

### Codex instruction

```text
Check every occurrence of "reconstruction loss" in the manuscript. Make sure the paper clearly states what is reconstructed. Distinguish node-level reconstruction, edge-level structure reconstruction, incidence-level high-order reconstruction, and cluster-level reconstruction. Do not describe all reconstruction losses as generic autoencoder reconstruction. If the loss reconstructs A_ij or node-pair similarity, call it edge-level structure reconstruction. If it reconstructs node-hyperedge associations, call it incidence-level high-order reconstruction.
```

---

# Part VI. Formatting, Figures, and Submission Safety

## Advice 17: Use publication-quality figure and table formatting

Figures, tables, and algorithms should be placed at the top of the page whenever possible. In LaTeX, prefer `[t]` for floating environments instead of using `[htbp]` indiscriminately.

### Rules

1. Use `\begin{figure}[t]`, `\begin{table}[t]`, and `\begin{algorithm}[t]` for main figures, tables, and algorithms.
2. Avoid PNG figures in the manuscript. Use vector formats such as PDF or SVG whenever possible.
3. Export matplotlib figures as PDF:

```python
plt.savefig("figure.pdf", bbox_inches="tight")
```

4. Use large and readable fonts in figures. Default plotting fonts are usually too small for double-column papers.
5. Check every figure after inserting it into the compiled PDF, not only in the original image viewer.
6. Make sure axis labels, legends, tick labels, and annotations are readable after scaling.
7. Framework figures and experimental figures are the first impression of the paper and must look professional.

### Codex instruction

```text
Check all LaTeX figures, tables, and algorithms. Prefer [t] placement for floating environments. Replace [htbp] with [t] unless there is a clear reason not to. Check whether figures are included as PNG files. If so, suggest replacing them with vector formats such as PDF or SVG. Also check figure readability and remind the user to enlarge axis labels, tick labels, legends, and annotations for double-column paper formatting.
```

---

## Advice 18: Check anonymity in code and supplementary materials

For anonymous submission, anonymity must be preserved not only in the paper but also in code, comments, README files, paths, logs, and supplementary materials. Do not include Chinese comments, author names, institution names, country information, personal paths, emails, or any metadata that may reveal the authors' identities.

### Rules

1. Use English for all code comments and public files.
2. Remove author names, institution names, country information, and emails.
3. Avoid personal local paths in scripts, logs, and configuration files.
4. Check README, filenames, commit history, notebooks, generated figures, and metadata.
5. Before submission, run an anonymity audit over the whole artifact package.

### Risk examples

```text
/home/dxd/...
D:/...
Southwest University
China
Chinese comments
Author names
Emails
Personal server paths
```

### Codex instruction

```text
Perform an anonymity audit over the paper, supplementary materials, code comments, README files, configuration files, logs, paths, filenames, notebooks, and generated figures. Remove Chinese comments, author names, institution names, country information, emails, and personal paths.
```

---

# Part VII. Practical Drafting Workflow And LaTeX Hygiene

## Advice 19: Write sections in a productive order

When building a first complete draft, do not necessarily write from Abstract to Conclusion. A more efficient order is to write the technically constrained sections first and then write the Introduction around the real method and results.

### Recommended order

1. Related Work.
2. Preliminaries.
3. Method.
4. Introduction.
5. Experiments.
6. Abstract and Conclusion.

### Rules

1. Write Related Work early to clarify the baseline taxonomy and the paper's positioning.
2. Write Preliminaries before Method only for notation needed across the whole paper.
3. Write Method before Introduction so that the claimed contributions match the actual technical design.
4. Write Abstract and Conclusion last by compressing the Introduction and main experimental findings.
5. Use a mature, closely related paper only as a structural reference. Replace all content with the current paper's own motivation, method, and results.
6. For conference-style submissions, prepare a complete draft first, then move secondary proofs and extra experiments to the appendix according to page limits.

### Codex instruction

```text
When drafting or restructuring the manuscript, prefer the order Related Work -> Preliminaries -> Method -> Introduction -> Experiments -> Abstract/Conclusion. Use existing papers only as structural references, not as text sources. Keep the Introduction aligned with the final Method and experiments.
```

---

## Advice 20: Keep Related Work short, classified, and baseline-complete

Related Work should support the motivation rather than become a broad survey. It should usually contain two subsections and at most three. Each subsection should correspond to a method category that appears in the baseline comparison or is essential to the motivation.

### Rules

1. Avoid excessive background because the Introduction already provides the problem context.
2. Group papers by paradigm rather than listing them one by one.
3. Make sure methods compared in experiments are covered in Related Work.
4. End each subsection with a concise category-level limitation.
5. Keep the limitations aligned with the two major limitations stated in the Introduction.
6. Avoid over-detailed criticism in Related Work. Put the deeper motivation in the Introduction.

### Recommended pattern

```text
Existing rule-based methods usually rely on predefined structural constraints, which may produce inflexible results when the graph structure is noisy or when users lack prior knowledge of the network. Existing learning-based methods improve representation learning, but many of them still rely on pairwise or fixed structures and therefore may fail to adaptively refine noisy high-order relations.
```

### Codex instruction

```text
Revise Related Work into two or three paradigm-based subsections. Ensure all experimental baselines are mentioned. End each subsection with a concise limitation that directly supports the Introduction's main gap.
```

---

## Advice 21: Use Preliminaries only for global notation

Preliminaries should not become a dumping ground for symbols. Define only concepts and notation used throughout the paper.

### Rules

1. Keep Preliminaries concise when the paper studies an existing problem.
2. Expand Preliminaries only when the paper defines a new problem or evaluation setting.
3. Define symbols once and use them consistently.
4. Do not define notation that is only used in one later subsection. Define such notation locally.
5. Check whether every symbol introduced in Preliminaries is used later.

### Codex instruction

```text
Audit Preliminaries for symbol overload. Keep only globally used notation, move local notation to the relevant method subsection, and ensure the same symbol has one meaning throughout the paper.
```

---

## Advice 22: Make Method look formal and technically grounded

The Method section should combine intuitive explanation with formalization. A graph clustering paper usually benefits from clear definitions, lemmas, propositions, theorems, algorithms, and complexity analysis when they are technically justified.

### Rules

1. Start each method module with a short motivation sentence.
2. Follow important ideas with clean formulas or formal definitions.
3. Add proof-style results only when the statement is true and useful.
4. Include a framework figure and, when helpful, a running example figure.
5. Use vector figures, preferably PDF, with readable fonts and thick enough lines.
6. Use top placement `[t]` for figures, tables, and algorithms unless there is a clear reason not to.
7. Do not let proofs become decorative. Each theorem or lemma should support a claim made in the paper.

### Codex instruction

```text
Revise Method to pair each important design with formal notation, equations, and justified theoretical statements. Add or suggest definitions, lemmas, theorems, algorithms, framework figures, and example figures only when they genuinely clarify the method.
```

---

## Advice 23: Structure the Introduction around two limitations

The Introduction often determines the reviewer's first judgment. It should be concise on general background and detailed on the paper's actual gap and solution.

### Recommended structure

1. General task background in about one compact paragraph.
2. Narrow down to the target subproblem and classify recent solutions.
3. State two major limitations of existing methods and avoid scattering the motivation.
4. Explain why straightforward fixes are insufficient when useful.
5. Present the proposed method as a direct response to the two limitations.
6. List three contributions, where the first two match the two limitations and the third covers experiments.

### Rules

1. Keep the first background paragraph short.
2. Do not overuse method names in Introduction; keep detailed citations in Related Work.
3. State the two limitations clearly and reuse them throughout the paper.
4. If adding a motivation figure or table, make sure it is unambiguous. Omit it if the message is unclear.
5. Give enough space to the proposed solution. Do not introduce it in one thin paragraph.
6. Use a "straightforward solution -> why insufficient -> our solution" paragraph when reviewers may naturally ask why an easier fix is not enough.

### Codex instruction

```text
Rewrite the Introduction with a compact background, a focused target-problem paragraph, two clearly named limitations, an optional failed-straightforward-solution paragraph, a high-level method paragraph, and three aligned contributions.
```

---

## Advice 24: Make the experiment section look complete

Experiments should convince reviewers that the method is effective, robust, and fairly compared. A typical strong experiment section includes enough datasets, baselines, parameter settings, implementation details, main results, ablations, sensitivity analysis, scalability, and visualizations.

### Rules

1. In Experimental Setup, include Datasets, Baselines, Parameters, and Implementation Details.
2. Use at least several benchmark datasets when available. For many graph clustering papers, six or more datasets is a useful target.
3. Include enough baselines to cover the main paradigms. For many submissions, eight or more baselines and several recent baselines reduce reviewer risk.
4. In main results, start with one or two background sentences and then write observations from tables or figures.
5. Report selected strong numbers as examples, but do not turn the paragraph into a number list.
6. Use multiple experiment types, such as overall performance, ablation, sensitivity, robustness, scalability, visualization, and structure-quality analysis.
7. Connect the empirical conclusion back to the theoretical or methodological motivation without overclaiming.

### Recommended main-result pattern

```text
As shown in Table X, we have the following observations. First, ... For example, ... Second, ... Third, ... These results suggest that ..., which is consistent with the motivation of ...
```

### Codex instruction

```text
Check whether the experiment section includes datasets, baselines, parameters, implementation details, main results, ablations, sensitivity, scalability, and visualization or structure analysis. Strengthen missing parts or explain omissions honestly.
```

---

## Advice 25: Enforce LaTeX spacing and citation hygiene

Small LaTeX style mistakes can make a paper look unpolished.

### Rules

1. Put a normal space before citations, such as `method~\cite{key}` or `method \cite{key}`.
2. Put spaces around inline mathematical symbols when they are embedded in prose, unless the symbol ends the sentence.
3. Avoid orphaned punctuation around citations.
4. Keep figure, table, and equation references consistent, such as `Figure~\ref{...}`, `Table~\ref{...}`, and `Eq.~\eqref{...}`.
5. Prefer nonbreaking spaces before references in LaTeX.
6. Check capitalization of method names, datasets, and metrics.

### Codex instruction

```text
Scan the manuscript for LaTeX spacing and citation hygiene. Add spaces before citations and references, normalize Figure/Table/Eq. references, and fix inconsistent capitalization.
```

---

## Advice 26: Clean BibTeX entries before submission

BibTeX entries should be concise, consistent, and compatible with the venue template. Avoid messy copied metadata.

### Rules

1. Keep all references in one `.bib` file unless the venue template requires otherwise.
2. Use BibTeX from reliable sources such as DBLP or Google Scholar, then clean it manually.
3. For conference papers, keep essential fields such as `author`, `title`, `booktitle`, `pages` when available, and `year`.
4. For journal papers, keep essential fields such as `author`, `title`, `journal`, `volume`, `number`, `pages` when available, and `year`.
5. Remove unnecessary fields such as `editor`, `publisher`, `address`, `month`, `url`, `doi`, `timestamp`, `biburl`, `bibsource`, and `abstract`, unless the venue explicitly requires them.
6. Use common conference abbreviations in `booktitle` when appropriate, such as `KDD`, `SIGMOD`, `WWW`, `ICDE`, `NeurIPS`, `ICML`, `ICLR`, and `AAAI`.
7. Preserve braces needed for capitalization, such as `{GNN}`, `{HGNN}`, `{Ncut}`, or dataset names.
8. Never invent or alter bibliographic facts. If uncertain, verify the entry.

### Codex instruction

```text
Audit the `.bib` file. Remove noisy metadata, normalize conference abbreviations, preserve necessary capitalization with braces, and keep only venue-required fields. Do not invent missing pages, volumes, or venues.
```

---

## Advice 27: Use LLM review as a final stress test

After the manuscript is complete, use a strict review pass to identify weaknesses before submission.

### Rules

1. Ask the reviewer model to evaluate the manuscript as the target venue.
2. Treat weak accept as the minimum desired simulated-review level when possible.
3. If the simulated review is reject or clearly weak reject, revise motivation, novelty, experiments, and writing before submission.
4. Check all LLM-suggested proofs, claims, and references manually.
5. Do not add impressive-looking formulas or proofs unless they are correct and connected to the method.

### Codex instruction

```text
After producing a near-final draft, simulate a strict target-venue review. Identify weaknesses in novelty, motivation, theory, experiments, writing, figures, and reproducibility. Revise the manuscript, but manually verify every new claim, proof, and reference.
```

---

# Part VIII. Compact Codex Prompt

Use this prompt when giving Codex a paper draft and this notes file.

```text
You are revising an AAAI/KDD/WWW-style graph clustering or attributed hypergraph clustering paper. Follow the Longlong Lin WeChat advice notes.

Main goals:
1. Strengthen reviewer defense before reviewers ask.
2. Ensure recent and comprehensive baselines.
3. Add baseline tuning protocol.
4. Add Avg.Rank if single-dataset results are uneven.
5. Explain omitted results, timeout, OOM, and appendix placement.
6. Do not overclaim when not all metrics are best.
7. Classify baselines before writing motivation.
8. Derive two motivations from missing but important capabilities.
9. Ensure the method is not just a stronger backbone plus KMeans.
10. Check ground-truth overlap and whether labels are community-based or class-based.
11. Avoid AI-like writing patterns, especially excessive colons and em dashes.
12. Spend more writing effort on key arguments than generic background.
13. Keep main formulas clean and do not expose code-level epsilon tricks.
14. Clarify whether reconstruction loss is node-level, edge-level, incidence-level, or cluster-level.
15. Check figure/table quality, vector formats, readable fonts, and [t] placement.
16. Check anonymity in paper, code, supplementary materials, logs, paths, and metadata.
17. Use the productive drafting order: Related Work, Preliminaries, Method, Introduction, Experiments, Abstract, and Conclusion.
18. Keep Related Work to two or three paradigm-based subsections and make sure it covers all experimental baselines.
19. Keep Preliminaries limited to globally used notation.
20. Structure Introduction around two major limitations and align the first two contributions with them.
21. Clean LaTeX spacing, citation formatting, figure/table/equation references, and BibTeX entries.

Do not invent results, proofs, or references. Preserve technical meaning and experimental values. Improve clarity, logic, fairness, and reviewer robustness.
```

---

# Part IX. Pre-submission Checklist

## Baselines and Experiments

- [ ] Are recent baselines included?
- [ ] Are baseline categories clear?
- [ ] Does Related Work cover all methods compared in experiments?
- [ ] Are baseline tuning protocols explained?
- [ ] Are timeout/OOM cases marked rather than hidden?
- [ ] Are omitted datasets/metrics/parameters explained?
- [ ] Is Avg.Rank added if useful?
- [ ] Are non-best metrics described carefully?
- [ ] Are full metrics placed in appendix if not in main text?

## Motivation and Related Work

- [ ] Are baselines classified by paradigm?
- [ ] Is Related Work limited to two or three focused subsections unless there is a clear reason?
- [ ] Are two clear motivations derived from baseline limitations?
- [ ] Does the paper avoid framing the contribution as merely using a stronger backbone?
- [ ] Is there a property comparison table if suitable?

## Evaluation Protocol

- [ ] Are ground-truth labels single-label or overlapping?
- [ ] Are community-based and class-based labels distinguished if relevant?
- [ ] Is PPR/RWR long-range behavior explained correctly?
- [ ] Is alpha interpreted according to the actual formula?

## Method and Formula

- [ ] Does Preliminaries define only globally used notation?
- [ ] Are symbols consistent across Preliminaries, Method, and Experiments?
- [ ] Does Method combine intuitive explanation with formal definitions, equations, algorithms, and justified theory?
- [ ] Are numerical stabilizers removed from main formulas unless essential?
- [ ] Are implementation-level stabilizers mentioned only briefly?
- [ ] Is reconstruction loss clearly described by level?
- [ ] Are loss functions explained before and after formulas?

## Writing Style

- [ ] Is the first Introduction paragraph concise?
- [ ] Does the Introduction clearly state two major limitations?
- [ ] Are straightforward solutions discussed when reviewers may naturally ask about them?
- [ ] Is generic background concise?
- [ ] Are key arguments fully explained?
- [ ] Are colon/em-dash AI-style patterns reduced?
- [ ] Are grammar, typos, and wording checked?
- [ ] Are references real and relevant?
- [ ] Are LaTeX spaces before citations and cross-references correct?
- [ ] Are BibTeX entries cleaned and venue-compatible?

## Formatting and Submission

- [ ] Are figures and tables placed with `[t]` where suitable?
- [ ] Are figures vectorized as PDF/SVG instead of PNG?
- [ ] Are figure fonts large enough in the compiled PDF?
- [ ] Is the framework figure professional?
- [ ] Is the artifact package anonymous?
- [ ] Are code comments and public files in English?
