# Longlong Lin-style Academic Writing Skill for HGSC Papers

> Intended use: give this file to Codex / ChatGPT / an AI coding-writing agent when revising an attributed hypergraph clustering, graph clustering, or community search paper.
>
> Goal: imitate the **writing logic and paper-organization skill** distilled from a series of Longlong Lin first-author papers, not to copy technical content.

---

## 0. Scope and Target Paper Type

This writing skill is designed for papers in:

- attributed graph clustering;
- attributed hypergraph clustering;
- graph / hypergraph structure learning;
- deep graph clustering;
- high-order graph clustering;
- robust graph / hypergraph clustering.

The target paper in this project is an **attributed hypergraph clustering / graph clustering** paper. The preferred framing is:

> Existing attributed graph clustering methods either rely on pairwise structures, which cannot fully capture high-order relations, or adopt fixed hypergraph structures, which may repeatedly propagate noisy incidence relations. More importantly, directly learning a dense adaptive graph may destroy the original high-order semantics encoded in the hypergraph. To address these issues, we propose a clustering-oriented and structure-preserving hypergraph refinement framework. The proposed method treats the initial incidence matrix as a structural prior and dynamically reweights node-hyperedge associations, thereby preserving informative high-order semantics while suppressing noisy or task-irrelevant relations.

---

## 1. Core Writing Philosophy

Longlong Lin-style writing does **not** usually start from:

> We propose a new model.

It usually starts from:

> Existing methods follow a certain paradigm. This paradigm is useful but incomplete. Under the target setting, it produces a systematic limitation. We therefore formulate a new problem / metric / framework / algorithm to fix the missing dimension.

For HGSC-style papers, the key transformation should be:

> fixed-structure clustering paradigm  
> → clustering-oriented adaptive hypergraph structure refinement paradigm

Avoid presenting the method as just another module. Present it as a response to a structural limitation of an existing paradigm.

---

## 2. Main Distilled Patterns from the Paper Series

### 2.1 Paradigm-level Critique

Do not only criticize individual methods. Criticize the shared paradigm behind them.

Examples of useful paradigm critiques:

- Existing methods are limited by a fixed-structure learning paradigm.
- Existing methods rely on an intermediate structure that is not directly optimized for the final clustering objective.
- Existing methods exploit high-order relations, but they assume the constructed high-order structure is reliable.
- Existing methods learn adaptive structures, but they are mainly designed for pairwise graphs and may destroy hyperedge-level semantics.

HGSC version:

> Most existing attributed hypergraph clustering methods follow a fixed-structure paradigm: they first construct an incidence matrix from the input data and then perform representation learning or clustering on this fixed structure. However, the constructed incidence matrix may contain noisy or task-irrelevant node-hyperedge associations, which are repeatedly used during message passing and may mislead the clustering objective.

---

### 2.2 Two-fold Limitations

A common structure is:

> Existing methods suffer from two major limitations.

Use this instead of vague criticism.

HGSC version:

> Existing attributed hypergraph clustering methods suffer from two major limitations. First, most of them rely on a fixed incidence matrix constructed before training, causing noisy high-order relations to be repeatedly propagated during message passing. Second, existing graph structure learning methods are mainly designed for pairwise graphs and may fail to preserve hyperedge-level semantics.

Alternative version:

> Existing attributed clustering methods either fail to fully exploit high-order relations, or heavily rely on a fixed hypergraph structure whose noisy node-hyperedge associations may compromise clustering quality.

---

### 2.3 Failure-mode Naming

A strong Longlong Lin-style move is to name the failure mode.

Recommended failure-mode for HGSC:

## incidence noise propagation issue

Definition-style writing:

> Fixed hypergraph clustering methods assume that the constructed incidence matrix is reliable throughout training. However, real-world attributed hypergraphs may contain noisy or task-irrelevant node-hyperedge associations. When such an incidence matrix is repeatedly used for message passing, noisy high-order signals may be propagated and amplified, thereby misleading the clustering objective. We refer to this phenomenon as the **incidence noise propagation issue**.

Use this concept to connect:

- motivation;
- method design;
- robustness experiment;
- ablation study;
- discussion of incidence noise / attribute noise / mixed noise.

---

### 2.4 Classic Metric + Missing Dimension

Another stable pattern is:

> A classic metric is useful because it captures an important property. However, it misses a key dimension in the current setting. We extend or adapt it.

HGSC version:

> Normalized cut provides a principled way to encourage compact intra-cluster structures and sparse inter-cluster separations. However, directly applying it to a fixed hypergraph may make the clustering process sensitive to noisy incidence relations. To address this issue, we optimize the cut-based objective on a dynamically refined high-order structure.

---

### 2.5 Basic Solution → Limitation → Advanced Framework

Longlong Lin papers often introduce a straightforward solution first, then explain why it is insufficient, then present the full framework.

HGSC method flow:

1. Basic fixed-structure hypergraph clustering.
2. Limitation of fixed incidence matrix.
3. Structure-preserving dynamic refinement.
4. Clustering-oriented objective.
5. Experiments verifying the necessity of each component.

Template:

> A straightforward solution is to perform hypergraph neural clustering on the pre-constructed incidence matrix. However, this fixed-structure solution has two limitations. First, noisy incidence relations are repeatedly used during message passing. Second, the structure cannot be adjusted according to the clustering objective. Therefore, it may produce suboptimal clusters when the initial hypergraph is noisy or incomplete. Motivated by this observation, we propose a clustering-oriented and structure-preserving hypergraph refinement framework.

---

### 2.6 Failed Attempt Writing

Use this to justify design decisions.

Template:

> A straightforward solution is to learn a fully adaptive graph from node embeddings. However, this strategy has two drawbacks. First, it may destroy the original high-order semantics encoded in the hypergraph. Second, it may introduce dense pairwise noise and increase computational cost. Therefore, we treat the initial hypergraph as a structural prior and refine it in a controlled, clustering-oriented manner.

This is useful when explaining why the method does not simply learn a dense graph.

---

## 3. Introduction Writing Template

### 3.1 Recommended Introduction Structure

Use the following order:

1. Introduce graph clustering / attributed graph clustering as a fundamental task.
2. Explain why high-order relations matter.
3. Explain why hypergraph clustering is useful.
4. Point out the limitation of fixed hypergraph structure.
5. Name or describe the incidence noise propagation issue.
6. Present the proposed framework.
7. Summarize contributions.

---

### 3.2 Full Introduction Draft Skeleton

```text
Attributed graph clustering is a fundamental task in graph data mining, aiming to partition nodes into meaningful groups by jointly exploiting graph topology and node attributes. It has been widely used in many practical applications, such as citation network analysis, social network mining, and multimedia data understanding.

Despite the significant progress of existing attributed graph clustering methods, most of them are built upon pairwise graphs, where edges are treated as the basic structural unit. Such lower-order relations may be insufficient to characterize complex group-wise interactions that naturally exist in real-world attributed networks. Hypergraph clustering provides a natural way to model such high-order relations by connecting multiple nodes through hyperedges.

However, most existing attributed hypergraph clustering methods follow a fixed-structure paradigm. They first construct an incidence matrix from the input data and then perform representation learning or clustering on this fixed structure. This paradigm may suffer from two major limitations. First, the pre-constructed incidence matrix may contain noisy or task-irrelevant node-hyperedge associations. Second, the fixed structure cannot be adaptively refined according to the clustering objective during training. As a result, noisy high-order signals may be repeatedly propagated through hypergraph message passing and compromise clustering quality.

To address these limitations, we propose a clustering-oriented and structure-preserving hypergraph refinement framework. Instead of directly learning a dense graph from scratch, the proposed method treats the initial incidence matrix as a structural prior and dynamically reweights node-hyperedge associations. In this way, informative high-order semantics can be preserved, while noisy or cluster-irrelevant incidence relations can be suppressed.

Our main contributions are summarized as follows.
```

---

### 3.3 Contribution Template

Use 3 contributions. Avoid too many small points.

```text
- A clustering-oriented hypergraph refinement framework.
  We formulate attributed hypergraph clustering from a structure-refinement perspective and propose a framework that dynamically refines node-hyperedge associations under the guidance of the initial hypergraph structure.

- A structure-preserving dynamic learning strategy.
  We design a dynamic refinement module that preserves informative high-order semantics while suppressing noisy or task-irrelevant incidence relations, alleviating the incidence noise propagation issue.

- Comprehensive experiments.
  We conduct extensive experiments on multiple attributed graph and hypergraph datasets. The results demonstrate the effectiveness, robustness, and stability of the proposed method through overall comparison, ablation study, sensitivity analysis, and robustness evaluation.
```

Use stronger language only when results justify it:

```text
- Extensive experiments show that the proposed method achieves the best or competitive performance on most datasets and consistently improves robustness under attribute noise, incidence noise, and mixed noise.
```

---

## 4. Method Writing Template

### 4.1 Recommended Method Section Order

```text
3. Methodology
  3.1 Problem Definition and Notation
  3.2 Basic Fixed-Structure Hypergraph Clustering
  3.3 Overview of the Proposed Framework
  3.4 Structure-preserving Dynamic Hypergraph Refinement
  3.5 Clustering-oriented Optimization Objective
  3.6 Training Strategy and Complexity Discussion
```

---

### 4.2 Notation Writing

Define symbols before using formulas.

Suggested notation:

- attributed hypergraph: \( \mathcal{G}=(\mathcal{V},\mathcal{E},X,H) \)
- nodes: \( \mathcal{V} \)
- hyperedges: \( \mathcal{E} \)
- node attribute matrix: \( X \in \mathbb{R}^{n \times d} \)
- incidence matrix: \( H \in \mathbb{R}^{n \times m} \)
- base structure: \( A_{\mathrm{base}} \)
- dynamic structure: \( A_{\mathrm{dyn}} \)
- used structure: \( A_{\mathrm{used}} \)
- cluster assignment: \( Q \) or \( Z \)
- learned representation: \( Z \)

Problem statement:

```text
The goal of attributed hypergraph clustering is to learn a cluster assignment matrix that preserves both attribute consistency and high-order structural compactness.
```

---

### 4.3 Framework Overview Template

```text
The proposed framework consists of three stages. First, we construct an initial hypergraph to preserve high-order relations among nodes. Second, instead of treating the incidence matrix as fixed, we dynamically refine node-hyperedge associations in a structure-preserving manner. Third, the refined structure is used to guide clustering-oriented representation learning through multiple complementary objectives, including structural compactness, attribute reconstruction, cluster balance, and contrastive discrimination.
```

---

### 4.4 Dynamic Structure Refinement Template

```text
Fixed hypergraph structures may contain noisy or redundant incidence relations, which can mislead clustering optimization. To alleviate this issue, we introduce a dynamic node-hyperedge scoring function to adaptively evaluate the contribution of each incidence relation during training. The refined structure is not learned from scratch. Instead, it is guided by the initial incidence matrix, so that the original high-order semantics can be preserved while unreliable associations are down-weighted.
```

If using base-dynamic fusion:

```text
To avoid over-refinement and preserve the original high-order prior, we combine the base structure and the dynamic structure as follows:
\[
A_{\mathrm{used}} = \alpha A_{\mathrm{base}} + (1-\alpha)A_{\mathrm{dyn}},
\]
where \( \alpha \) controls the contribution of the initial hypergraph structure. A larger \( \alpha \) makes the model rely more on the original structure, while a smaller \( \alpha \) encourages stronger adaptive refinement.
```

---

### 4.5 Objective Function Writing

Use motivation before formula and interpretation after formula.

Bad style:

```text
The loss is ...
```

Preferred style:

```text
To make the refined structure directly serve the clustering task, we jointly optimize several complementary objectives.
```

Template:

```text
The overall objective is defined as:
\[
\mathcal{L} =
\lambda_1 \mathcal{L}_{\mathrm{ncut}}
+ \lambda_2 \mathcal{L}_{\mathrm{balance}}
+ \lambda_3 \mathcal{L}_{\mathrm{rec}}
+ \lambda_4 \mathcal{L}_{\mathrm{con}}.
\]

Here, \( \mathcal{L}_{\mathrm{ncut}} \) encourages compact intra-cluster structures and sparse inter-cluster separations, \( \mathcal{L}_{\mathrm{balance}} \) prevents degenerate cluster assignments, \( \mathcal{L}_{\mathrm{rec}} \) preserves attribute information, and \( \mathcal{L}_{\mathrm{con}} \) enhances the discriminative ability of learned representations. These objectives are complementary: the structural losses guide clustering compactness, while the attribute and contrastive losses improve representation quality.
```

---

## 5. Related Work Writing Template

Do not list papers one by one. Organize by research evolution.

### 5.1 Recommended Categories

```text
2. Related Work
  2.1 Graph Clustering
  2.2 Attributed Graph Clustering
  2.3 Hypergraph Learning and Hypergraph Clustering
  2.4 Graph Structure Learning
  2.5 Robust Graph Clustering
```

---

### 5.2 Category-level Writing

#### Attributed Graph Clustering

```text
Attributed graph clustering aims to group nodes by jointly exploiting graph topology and node attributes. Existing methods have achieved promising performance by designing graph neural encoders, autoencoder-based objectives, or contrastive learning strategies. However, most of them are built upon pairwise graphs and therefore may fail to fully capture high-order relations among multiple nodes.
```

#### Hypergraph Learning and Hypergraph Clustering

```text
Hypergraph learning provides a natural way to model high-order relations through hyperedges. Compared with ordinary graphs, hypergraphs can represent group-wise interactions more directly. However, many hypergraph clustering methods rely on a fixed incidence matrix constructed before training. Once the initial structure contains noisy or task-irrelevant node-hyperedge associations, such fixed-structure methods cannot adaptively correct them during clustering optimization.
```

#### Graph Structure Learning

```text
Graph structure learning methods attempt to refine or learn graph topology for downstream tasks. Although these methods can alleviate the limitation of fixed graphs, most of them are designed for pairwise relations. Directly applying them to hypergraph clustering may destroy the original hyperedge-level semantics or introduce dense pairwise noise.
```

#### Robust Graph Clustering

```text
Robust graph clustering studies how to maintain stable performance under noisy attributes or corrupted graph structures. However, existing studies mainly focus on pairwise edges, while the robustness of incidence-level high-order relations remains less explored. In this work, we explicitly evaluate robustness under attribute noise, incidence noise, and mixed noise.
```

---

## 6. Experiment Writing Template

### 6.1 Recommended Experiment Section Order

```text
4. Experiments
  4.1 Experimental Setup
  4.2 Overall Clustering Performance
  4.3 Ablation Study
  4.4 Sensitivity Analysis
  4.5 Robustness Analysis
  4.6 Structure Quality / Visualization
  4.7 Efficiency Analysis
```

If space is limited, use:

```text
4. Experiments
  4.1 Experimental Setup
  4.2 Main Results
  4.3 Ablation Study
  4.4 Sensitivity and Robustness Analysis
```

---

### 6.2 Overall Results Template

```text
From Table X, we have the following observations. First, HGSC achieves the best or competitive performance on most datasets, demonstrating the effectiveness of adaptive high-order structure learning. Second, the improvement is more evident on datasets with complex structural patterns, indicating that fixed pairwise graphs or fixed hypergraphs may be insufficient for attributed clustering. Third, HGSC remains stable across different metrics, showing that the proposed structure refinement strategy improves overall clustering quality rather than optimizing a single metric.
```

If not all datasets are SOTA:

```text
Although HGSC does not achieve the best result on every dataset, it consistently obtains competitive performance across all metrics. This suggests that the proposed adaptive structure learning strategy improves the overall robustness of attributed hypergraph clustering rather than overfitting to a specific dataset.
```

---

### 6.3 Ablation Study Template

```text
The ablation results show that each component contributes to the final performance. Removing the dynamic structure refinement module leads to a clear performance degradation, which confirms that the fixed hypergraph may contain noisy or task-irrelevant incidence relations. Removing the reconstruction objective weakens attribute preservation, while removing the contrastive objective reduces the discriminative ability of learned representations. These results indicate that the proposed components are complementary rather than redundant.
```

For unexpected result:

```text
A possible explanation is that the initial hypergraph of this dataset already provides relatively reliable high-order relations, leaving less room for dynamic refinement.
```

---

### 6.4 Sensitivity Analysis Template

```text
The sensitivity results show that HGSC achieves relatively stable performance within a reasonable parameter range. This indicates that the proposed framework is not overly dependent on a specific hyperparameter setting. When the parameter becomes too large or too small, the performance decreases because the model either overemphasizes the refined structure or relies excessively on the initial hypergraph.
```

For `graph_alpha`:

```text
When \( \alpha \) is too large, the model relies heavily on the initial hypergraph and cannot sufficiently correct noisy incidence relations. When \( \alpha \) is too small, the model may overemphasize the dynamic structure and weaken the original high-order prior. Therefore, a moderate value of \( \alpha \) provides a better trade-off between structure preservation and adaptive refinement.
```

For `gamma_ncut`:

```text
A small value of \( \gamma_{\mathrm{ncut}} \) weakens the structural compactness constraint, while an excessively large value may dominate the representation learning objective. The results suggest that a moderate value can better balance clustering compactness and representation quality.
```

---

### 6.5 Robustness Analysis Template

```text
The robustness results show that HGSC degrades more slowly under attribute noise, incidence noise, and mixed noise. This indicates that the proposed dynamic refinement module can suppress unreliable node-hyperedge associations and alleviate the incidence noise propagation issue. Therefore, the proposed method is not only effective under clean settings, but also robust to corrupted high-order structures.
```

For incidence noise:

```text
Under incidence noise, the performance of fixed-structure methods drops more significantly because corrupted node-hyperedge associations are directly used during message passing. In contrast, HGSC adaptively reweights the incidence relations, preventing noisy hyperedges from dominating the clustering objective.
```

For attribute noise:

```text
Under attribute noise, the reconstruction and contrastive objectives help maintain discriminative representations, while the refined high-order structure provides complementary structural guidance.
```

For mixed noise:

```text
The mixed-noise setting is more challenging because both attributes and incidence relations are corrupted. The relatively stable performance of HGSC demonstrates that the proposed framework can jointly benefit from adaptive structure refinement and robust representation learning.
```

---

### 6.6 Efficiency Analysis Template

```text
Although HGSC introduces additional structure refinement, the computational overhead is acceptable because the refinement is guided by the initial hypergraph rather than performed over a fully dense graph. This design avoids unnecessary structure expansion and preserves the scalability of the model.
```

If slower than some baselines:

```text
Although HGSC is not always the fastest method due to the additional structure refinement process, it achieves a better balance between clustering quality and robustness. This trade-off is reasonable because the refinement module is designed to suppress noisy high-order relations rather than merely accelerate message passing.
```

---

## 7. Tone and Expression Bank

### 7.1 Strong Expressions

Use only when results are clearly strong.

- significantly outperforms
- achieves substantial improvement
- consistently outperforms
- demonstrates superior robustness
- achieves remarkable scalability
- provides strong evidence that ...

### 7.2 Moderate Expressions

Recommended for most cases.

- achieves promising performance
- obtains favorable results
- achieves the best or competitive performance
- demonstrates the effectiveness of ...
- confirms the contribution of ...
- shows stable performance

### 7.3 Weak / Careful Expressions

Use when not all datasets improve.

- remains competitive
- obtains comparable performance
- improves in most cases
- slightly improves
- a possible explanation is that ...
- may be attributed to ...

### 7.4 Criticism Expressions

Use these to avoid overly aggressive claims.

- may fail to fully capture ...
- are limited by ...
- usually rely on ...
- are sensitive to ...
- may introduce ...
- cannot adaptively refine ...
- overlook the unique properties of ...

### 7.5 Causal Explanation Expressions

- This is because ...
- This can be attributed to ...
- A possible explanation is that ...
- The reason is that ...
- These results indicate that ...
- These results confirm that ...
- These observations suggest that ...

---

## 8. Codex Rewrite Instructions

When using Codex to revise the paper, give it the following instruction.

```text
You are helping revise an attributed hypergraph clustering paper. Follow the Longlong Lin-style writing skill described in this file.

Do not simply polish grammar. Improve the paper's research narrative.

Main principles:
1. Frame the method as a paradigm-level improvement, not just a new model.
2. Criticize existing methods by identifying their shared paradigm and missing dimension.
3. Use two-fold limitations when writing the gap.
4. Introduce the incidence noise propagation issue as the key failure mode of fixed hypergraph clustering.
5. Present the method as clustering-oriented and structure-preserving hypergraph refinement.
6. In Method, first explain the basic fixed-structure solution and its limitation, then introduce the proposed adaptive framework.
7. Before every important formula, add a motivation sentence. After every formula, explain its role.
8. In experiments, use observation + reason + implication.
9. Use moderate academic tone. Do not overclaim if the method is not best on every dataset.
10. Preserve technical correctness and do not invent unreported results.
```

---

## 9. Codex Section-specific Prompts

### 9.1 Rewrite Introduction

```text
Rewrite the Introduction of this attributed hypergraph clustering paper using the following narrative:

- Start from attributed graph clustering as a fundamental task.
- Explain why pairwise graph structures are insufficient for high-order relations.
- Introduce hypergraph clustering as a natural solution.
- Point out the fixed-structure paradigm of existing hypergraph clustering methods.
- Define or describe the incidence noise propagation issue.
- Present our method as a clustering-oriented and structure-preserving hypergraph refinement framework.
- Use two-fold limitations.
- Use moderate academic tone and avoid exaggerated claims.
- Keep all technical claims consistent with the current method and experiments.
```

### 9.2 Rewrite Method

```text
Rewrite the Method section with a framework-first structure:

1. Problem definition and notation.
2. Basic fixed-structure hypergraph clustering and its limitation.
3. Overview of the proposed framework.
4. Dynamic hypergraph structure refinement.
5. Clustering-oriented objective.
6. Training strategy.

For each module:
- Add a motivation sentence before formulas.
- Explain the meaning and role of each formula after it.
- Emphasize that the method preserves the initial hypergraph as a structural prior.
- Avoid presenting modules as unrelated components.
```

### 9.3 Rewrite Related Work

```text
Rewrite the Related Work section by organizing it into research paradigms instead of listing papers one by one.

Use the following categories:
1. Graph clustering.
2. Attributed graph clustering.
3. Hypergraph learning and hypergraph clustering.
4. Graph / hypergraph structure learning.
5. Robust graph clustering.

For each category:
- Summarize the main idea.
- Mention representative methods if available.
- Point out the limitation related to our work.
- End by naturally motivating our clustering-oriented adaptive hypergraph refinement framework.
```

### 9.4 Rewrite Experiments

```text
Rewrite the Experiment Analysis section using the observation + reason + implication style.

For each table or figure:
- First state the main observations.
- Then explain why the results happen.
- Finally connect the observations to a specific design of our method.

Do not simply repeat numbers.
Use careful wording if our method is not best on every dataset:
"best or competitive", "favorable", "remains competitive", "in most cases".

For robustness experiments, explicitly connect the results to the incidence noise propagation issue.
```

### 9.5 Rewrite Ablation

```text
Rewrite the Ablation Study section.

For each removed component:
- Explain what the component is designed to do.
- State what happens after removing it.
- Interpret the result.
- Explain whether components are complementary.

Use this logic:
Removing dynamic structure refinement tests whether fixed hypergraphs are sufficient.
Removing reconstruction tests whether attribute preservation matters.
Removing contrastive learning tests whether discriminative representation learning matters.
Removing balance loss tests whether the model avoids degenerate clusters.
```

### 9.6 Rewrite Robustness

```text
Rewrite the Robustness Analysis section.

Use the following narrative:
- Attribute noise corrupts node features.
- Incidence noise corrupts node-hyperedge associations.
- Mixed noise corrupts both, making it the most challenging setting.
- Fixed-structure methods are more sensitive to incidence noise because corrupted relations are repeatedly propagated.
- Our method alleviates this through dynamic structure refinement.

Use moderate tone and do not overclaim.
```

---

## 10. Final Checklist Before Submission

Use this checklist to review the paper.

### Introduction

- [ ] Does the Introduction start from a broad task and narrow down to the target problem?
- [ ] Does it identify a shared paradigm of existing methods?
- [ ] Does it describe two-fold limitations?
- [ ] Does it define or clearly explain the incidence noise propagation issue?
- [ ] Does it present the method as a new framework, not just a module?
- [ ] Are contributions aligned with the challenges?

### Method

- [ ] Are notation and problem definition clear?
- [ ] Is there a basic solution / limitation discussion?
- [ ] Is the framework explained before detailed formulas?
- [ ] Does each formula have motivation before it and explanation after it?
- [ ] Is dynamic refinement described as structure-preserving?
- [ ] Is the loss function explained as complementary objectives?

### Related Work

- [ ] Is Related Work organized by paradigm rather than paper list?
- [ ] Does each category end with a limitation relevant to this paper?
- [ ] Is the criticism moderate and fair?

### Experiments

- [ ] Are baselines grouped logically?
- [ ] Does each result analysis include observation, reason, and implication?
- [ ] Does ablation map each component to its design purpose?
- [ ] Does robustness analysis connect to incidence noise propagation?
- [ ] Is non-SOTA performance described honestly and carefully?
- [ ] Are sensitivity results explained rather than only plotted?

### Tone

- [ ] Avoid overclaiming.
- [ ] Use "best or competitive" if not best everywhere.
- [ ] Use "may fail to" instead of "cannot" when criticism is not absolute.
- [ ] Use "a possible explanation is" for uncertain interpretation.
- [ ] Do not invent theoretical guarantees if none are proved.

---

## 11. One-page Core Prompt for Codex

Use this short prompt when you only want to give Codex a compact instruction.

```text
Revise this attributed hypergraph clustering paper following Longlong Lin-style academic writing.

Core narrative:
Existing attributed graph clustering methods either rely on pairwise structures, which cannot fully capture high-order relations, or adopt fixed hypergraph structures, which may repeatedly propagate noisy incidence relations. Directly learning a dense adaptive graph may also destroy original high-order semantics. Therefore, our method should be framed as a clustering-oriented and structure-preserving hypergraph refinement framework that treats the initial incidence matrix as a structural prior and dynamically reweights node-hyperedge associations.

Writing rules:
- Criticize paradigms, not individual papers.
- Use two-fold limitations in Introduction.
- Introduce the incidence noise propagation issue.
- Present Method as basic fixed-structure solution → limitation → proposed adaptive framework.
- Explain every formula with motivation and role.
- In experiments, use observation + reason + implication.
- For non-SOTA results, use careful wording such as "best or competitive" and "remains competitive".
- Do not invent results, proofs, or claims.
```
