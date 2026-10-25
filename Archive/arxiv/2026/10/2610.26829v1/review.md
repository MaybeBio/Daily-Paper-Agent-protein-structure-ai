## Review setup

- **Input scope** Title, author list, journal/platform, date, DOI/ID, URL, and the visible abstract text only. The body text of the manuscript was not provided.
- **Assessment boundary** This review is limited to the title, the abstract as displayed, and the bibliographic metadata. No figures, tables, methods, results, or supplementary materials were available for inspection.
- **Shared manuscript claim summary** The work introduces a benchmark, ProteinGeoBench, for evaluating structural-biology agents. The title asserts that frontier agents perform well on lookup tasks but poorly on geometry-related tasks. The abstract text was not provided beyond the title and submission metadata.
- **Visible evidence base** Title, author list, submission date, arXiv identifier, and the statement that the paper is categorized under Computer Science, Artificial Intelligence. No abstract body, no figures, no tables, no methods, no results, and no supplementary information were supplied.
- **Missing materials affecting confidence** The full abstract, the main text, all figures, all tables, the benchmark construction details, the agent evaluation protocols, the datasets used, the statistical analyses, and any code or data availability statements. Without these, the core claims cannot be assessed.

## Reviewer

- **Overall assessment** The title presents a potentially interesting claim about the limitations of structural-biology agents, but the supplied material is insufficient to evaluate the work. Only the title and bibliographic metadata are visible. No abstract, methods, results, or supporting evidence are available. The claim that agents are "fluent at lookup but lost in geometry" is not substantiated by any visible data. The manuscript cannot be assessed for scientific validity, technical soundness, or significance from the provided material.
- **Who would be interested in the results, and why** Based on the title alone, researchers in computational biology, protein structure prediction, and AI agents for scientific discovery would likely be interested. The claim that frontier agents fail at geometric reasoning in structural biology, if substantiated, would be relevant to those developing or deploying such agents. However, the lack of visible content prevents any meaningful assessment of the potential audience or impact.
- **Major strengths** None can be identified from the supplied material. The title is clear and provocative, but no content is available to evaluate strengths in methodology, analysis, or presentation.
- **Major Concerns** The absence of the abstract and full text is a fundamental issue. The core claim is unverifiable. The benchmark design, evaluation metrics, agent selection, and comparison baselines are all unknown. The statistical rigor of any reported results cannot be assessed. The novelty of the benchmark relative to existing resources cannot be determined.
- **Minor Comments** None can be identified from the supplied material.
- **Technical failings that need to be addressed before the case is established** The manuscript body, including the abstract, must be provided for any technical assessment. Without the methods and results, no technical failing can be identified, but equally no technical claim can be supported.
- **Assessment against Nature-style criteria** Originality cannot be assessed without the full text. Scientific importance cannot be assessed without evidence of the benchmark's utility and the validity of the reported agent failures. Interdisciplinary readership cannot be assessed without knowing how the work bridges AI and structural biology. Technical soundness cannot be assessed without methods and results. Readability for nonspecialists cannot be assessed without the abstract and main text. The title is accessible, but that is insufficient.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript cannot be evaluated in its present form. A substantive review requires the full abstract and manuscript text.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The title claims that frontier structural-biology agents are "fluent at lookup but lost in geometry."
- **Evidence pointer** Location not provided. No abstract, figures, tables, or results were supplied.
- **Concern** The central claim of the manuscript is presented in the title, but no supporting evidence is available. The abstract is missing, and the full text is not provided. There is no way to verify the claim, understand the benchmark design, or evaluate the agent performance data.
- **Why it matters** The claim is specific and potentially impactful. Without evidence, the claim is unsubstantiated. A reader cannot determine whether the benchmark is well-constructed, whether the agents were fairly evaluated, or whether the conclusion is statistically supported.
- **Resolution test** Provide the full abstract and manuscript text, including the benchmark description, agent evaluation protocols, datasets, and results. The claim must be supported by quantitative evidence and appropriate statistical analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark validity
- **Claim pointer** The work introduces a benchmark called ProteinGeoBench for evaluating structural-biology agents.
- **Evidence pointer** Location not provided. No description of the benchmark is available.
- **Concern** The benchmark design is entirely unknown. The tasks, the datasets, the evaluation metrics, the baseline methods, and the selection of agents are not described. Without this information, the validity and utility of the benchmark cannot be assessed.
- **Why it matters** A benchmark is only useful if it is well-designed, reproducible, and covers meaningful tasks. The absence of any description prevents assessment of whether the benchmark is novel, comprehensive, or fair.
- **Resolution test** Provide a detailed description of the benchmark, including task definitions, dataset sources, evaluation metrics, and the rationale for task selection. Include information on how the benchmark was validated and how it compares to existing resources.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Result substantiation
- **Claim pointer** The title implies that frontier agents perform well on lookup tasks but poorly on geometry tasks.
- **Evidence pointer** Location not provided. No results are available.
- **Concern** No quantitative results are provided. The performance of the agents on lookup versus geometry tasks is not shown. There is no data on accuracy, error rates, or any other metric. The claim of a performance gap is unsupported.
- **Why it matters** The distinction between lookup and geometry performance is the core finding of the work. Without results, the finding cannot be evaluated. The claim could be an artifact of task design, agent selection, or evaluation methodology.
- **Resolution test** Provide the full results section, including tables and figures showing agent performance on all tasks. Include statistical tests that demonstrate the significance of any performance differences between lookup and geometry tasks.

### Minor Comments

None identified from the supplied material.

## Risk / unsupported claims

- The claim that frontier structural-biology agents are "fluent at lookup but lost in geometry" is unsupported. No evidence is provided.
- The existence and validity of the ProteinGeoBench benchmark are unverifiable. No description is provided.
- Any implication that the benchmark is novel or useful is unassessable. No comparison to existing benchmarks is available.
- Any claim about the performance of specific agents is unverifiable. No agent names, versions, or evaluation results are provided.