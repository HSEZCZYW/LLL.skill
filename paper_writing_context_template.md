# Paper Writing Context Template

> **Purpose:** Provide LLL.skill with the minimum context needed to assist with writing a specific paper.
>
> **Use:** Keep this reusable template in LLL.skill. Save a filled copy as
> `paper_writing_context.md` in your paper-project root, or tell LLL.skill its
> location. A filled copy with the original filename is also supported.
> Keep real paper information in that project's appropriate private location.
>
> **Guidelines:**
> - Include only the paper's positioning, key facts, and writing constraints. Do not paste the entire manuscript here.
> - Leave uncertain fields blank. A blank field means “unknown”; it does not authorize the AI to fill in the answer on its own.
> - Distinguish confirmed facts from ideas that still need validation.
> - Do not include passwords, access tokens, or other confidential information.
> - Fill only what is useful and known. Examples and bracketed prompts are not facts.
> - For key claims, optionally give a supporting section, figure, or record path.
>   Relative paths are based on this file's directory unless stated otherwise.

## 1. Paper Information

- **Working title:** [Fill in]
- **Research task:** [e.g., community detection, community search, node classification]
- **Data / graph type:** [e.g., attributed graph, temporal graph, bipartite graph, hypergraph]
- **Brief paper description (1–3 sentences):**
  [What problem does this paper investigate?]

## 2. Motivation and Positioning

- **Core problem to address:** [Fill in]
- **Key limitations of existing methods:** [Fill in; provide literature or experimental evidence where possible]
- **Research gap this paper aims to address:** [Fill in]
- **Target audience or venue:** [Fill in, or leave blank if undecided]

## 3. Method and Contributions

- **Method overview:** [Describe the core idea in a few sentences]
- **Key design choices and their purposes:** [Fill in]
- **Essential inputs, outputs, module connections, and constraints:** [Fill in where needed to preserve technical meaning]
- **Confirmed contributions and supporting evidence:** [Fill in; include a source location when useful]
- **Tentative ideas or contribution candidates:** [Not yet established; leave blank if none]
- **Terminology or notation that must remain consistent:** [Fill in]

## 4. Experimental Evidence and Open Validation

- **Completed, evidence-supported findings:** [Include only conclusions supported by available evidence]
- **Results that can be emphasized:** [Fill in]
- **Results that require cautious interpretation or must not be overstated:** [Fill in]
- **Locations of relevant tables, figures, or result files:** [Provide paths or names, if applicable]
- **Validation not yet completed:** [Planned, pending, or inconclusive; do not use as confirmed findings]

> You do not need to duplicate all experimental data here. Use the manuscript, tables, or experiment records as the source of detailed values.

## 5. Writing Constraints

- **Preferred writing style or reference papers:** [Fill in]
- **Equations, technical facts, or conclusions that must not be changed without approval:** [Fill in]
- **Wording to avoid or known issues to address:** [Fill in]
- **Current writing task (optional; may become stale):** [e.g., revise the Introduction; the current conversation takes precedence]

---

## Instructions for LLL.skill

1. Use the shared discovery, application, conflict, and maintenance rules in the root LLL.skill `SKILL.md` §6. Missing or empty context must not prevent otherwise feasible writing work.
2. Apply relevant entries to the requested section while checking factual claims against the manuscript and evidence. If they conflict with this file, identify the specific inconsistency instead of silently choosing one or overwriting the other.
3. Do not invent experimental results, citations, technical details, or contributions that the researcher has not confirmed.
4. Distinguish confirmed facts, tentative hypotheses, and writing recommendations.
5. Do not force the paper's technical content or argumentation into a template merely to follow a preferred writing pattern.
6. Ask the researcher for clarification only when missing information materially affects the current writing task.
7. Update this file when requested, using confirmed information. Otherwise flag stale entries and suggest corrections without silently changing project decisions.
