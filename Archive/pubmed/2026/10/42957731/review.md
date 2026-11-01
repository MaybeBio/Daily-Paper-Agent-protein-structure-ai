## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific claims, methodology, evaluation design, and interpretation as presented in the text; statistical analyses and figure data not independently verifiable from the provided material
- **Shared manuscript claim summary** The authors introduce MolGenBench, a benchmark for evaluating generative models in structure-based drug discovery, covering both de novo design and hit-to-lead optimization. They evaluate 17 methods across multiple dimensions including basic molecular properties, chemical safety, scaffold diversity, conformational quality, target awareness, active compound rediscovery, screening efficiency, and interaction fidelity. They report that current models show limited ability to rediscover active molecules, generate high-risk motifs, exhibit poor target awareness, and generalize poorly to unseen proteins.
- **Visible evidence base** Results sections describing Figures 1-9, Supplementary Figures 1-15, Supplementary Tables 1-5, and Methods section with formal definitions of metrics
- **Missing materials affecting confidence** Figures and their underlying data, Supplementary Information contents, statistical analysis details, exact model configurations, dataset composition details, and code availability

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important problem: the lack of realistic, comprehensive benchmarks for structure-based drug design generative models. The authors have assembled a substantial evaluation framework with 120 protein targets, 600 compound series, and 17 methods spanning diverse architectures. The introduction of the H2L optimization benchmark and the Target-Aware Score are valuable contributions. However, several methodological concerns need to be addressed, particularly regarding the interpretation of the rediscovery metrics, the handling of training data leakage, and the statistical rigor of the comparisons. The manuscript is well-written and the evaluation framework is thoughtfully designed, but the conclusions about model limitations would be strengthened by more careful consideration of confounding factors.

- **Who would be interested in the results, and why** Researchers developing generative models for drug discovery, computational chemists working on structure-based design, and methodologists interested in benchmark design for AI-driven scientific discovery. The benchmark itself and the associated evaluation framework would be a useful resource for the community, and the findings about model limitations should inform future method development.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim that "current methods remain limited in rediscovering active molecules" and use this as a central finding of the benchmark.
- **Evidence pointer** Results section "Limited screening efficiency of current molecular generative models", Figures 5-6
- **Concern** The rediscovery metric is fundamentally limited by the fact that the reference active compounds in ChEMBL represent only a small, biased sample of the true bioactive chemical space for each target. The authors acknowledge this in the Discussion but do not adequately address how this affects the interpretation of their results. A model could generate a genuinely potent, drug-like molecule that is simply not in the reference set, and it would be counted as a failure. The authors state that "failure to recover known actives for a given target may reflect both the incompleteness of existing reference data and the exploration limitations of current generative models," but this caveat is not reflected in the strength of the conclusions drawn elsewhere in the manuscript. The abstract states that models "struggle to produce active molecules reliably" without this important qualification.
- **Why it matters** The central claim of the paper is that current generative models are inadequate for drug discovery. If the evaluation metric systematically underestimates model performance due to incomplete reference data, the conclusions may be overly pessimistic. This affects the practical guidance the field takes from this work.
- **Resolution test** The authors should provide a quantitative analysis of the coverage of the reference active space, perhaps by comparing the chemical diversity of reference actives to the full known bioactive space for a subset of targets. They should also discuss how the choice of the 10 micromolar activity cutoff affects the results, and consider whether a more lenient or structure-based similarity threshold would change the conclusions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that "architecture-related trends are interpreted primarily from comparisons among models trained on CrossDock, whereas comparisons across the full model panel reflect the combined effects of architecture, training data, and incorporated inductive biases."
- **Evidence pointer** Results section "MolGenBench dataset construction and baseline model selection", Figure 2
- **Concern** This statement acknowledges a fundamental confounding in the evaluation design, but the manuscript does not systematically separate these factors in the results. For example, when comparing TamGen (trained on large-scale active molecule data) with models trained only on CrossDock, it is unclear whether performance differences reflect architectural superiority or simply the benefit of broader training data. The authors mention this in the Discussion but do not provide a systematic analysis that would allow readers to disentangle these effects. A more rigorous approach would involve controlled comparisons where architecture is varied while training data is held constant, or vice versa.
- **Why it matters** The stated goal of the benchmark is to provide guidance for future model development. Without separating the effects of architecture, training data, and inductive biases, the guidance is ambiguous. Readers cannot determine whether to invest in new architectures, better training data, or different priors.
- **Resolution test** The authors should either (a) provide additional controlled experiments that isolate these factors, or (b) restructure the analysis to explicitly categorize models by training data and architecture, presenting results in a way that allows readers to make these distinctions. At minimum, the Discussion should provide a more detailed and structured analysis of these confounds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report performance differences between models across multiple metrics, including statements such as "PocketFlow demonstrated the most consistent performance" and "DiffDec emerged as the top performer."
- **Evidence pointer** Results sections on screening efficiency, H2L optimization, and TAScore; Figures 5-9
- **Concern** The manuscript does not report any statistical significance testing for the observed differences between models. With three independent repeats, the authors have some information about variability, but they do not report confidence intervals or statistical comparisons. Given the stochastic nature of generative models and the variability in docking outcomes, it is unclear whether the reported differences between models are meaningful or within the range of random variation.
- **Why it matters** The benchmark aims to provide reliable guidance on model selection and development. Without statistical rigor, readers may over-interpret small differences between models that are not actually significant, leading to poor decisions about which methods to adopt or build upon.
- **Resolution test** The authors should provide appropriate statistical tests (e.g., paired tests across targets, bootstrap confidence intervals) for the key comparisons, or at minimum report effect sizes with confidence intervals. They should also clarify whether the three repeats are sufficient to capture the variability in model performance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** The authors introduce the TAScore metric to assess "whether a model can generate target-enriched chemotypes rather than pan-target chemotypes that lack discrimination across pockets."
- **Evidence pointer** Results section "Insufficient utilization of protein structural information", Figure 6e-f, Methods section on TAScore
- **Concern** The TAScore as defined in Equation 7 compares the ratio of target-specific recovery to background recovery. However, this metric may be confounded by the overall quality of generated molecules. A model that generates very few active molecules overall might have a high TAScore simply because the few actives it does generate happen to be target-specific, while a model that generates many actives across many targets might have a lower TAScore despite being more useful in practice. The authors should discuss this trade-off and consider whether a metric that accounts for both target specificity and overall hit rate would be more informative.
- **Why it matters** The TAScore is presented as a novel contribution of this work. If the metric is not well-calibrated or is easily gameable, it could mislead the community about which models are truly target-aware.
- **Resolution test** The authors should provide a more detailed analysis of the relationship between TAScore and other metrics, and discuss the potential trade-offs. They should also validate the metric on synthetic or controlled cases where the ground truth target-awareness is known.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "Evaluation of 17 leading methods reveals persistent limitations" but does not specify which methods were evaluated or provide any quantitative summary of the findings. This makes it difficult for readers to assess the significance of the work from the abstract alone.
- **Required correction** Consider adding a brief summary of the key quantitative findings, such as the range of hit rates observed or the best-performing method categories.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Dataset construction
- **Evidence pointer** Results section "MolGenBench dataset construction and baseline model selection"
- **Issue** The authors state that a lenient activity cutoff of 10 micromolar was used to "maximize the retention of positive molecules." However, this cutoff is quite permissive and may include compounds with weak or nonspecific binding. The authors should discuss whether this choice affects the interpretation of the rediscovery results.
- **Required correction** Add a brief discussion of the rationale for the 10 micromolar cutoff and its potential limitations, possibly with a sensitivity analysis using a stricter cutoff.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2c
- **Evidence pointer** Results section "Assessment of basic generative capabilities"
- **Issue** The description of Figure 2c states that "all metrics are normalized to a 0-1 scale, where higher values indicate better performance." However, it is unclear how the normalization was performed and whether the relative ranking of models is preserved under different normalization schemes.
- **Required correction** Provide details on the normalization procedure in the Methods section, and consider reporting raw values in supplementary materials.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** H2L evaluation
- **Evidence pointer** Results section "Evaluating H2L optimization models"
- **Issue** The authors note that DiffDec requires predefined atomic anchors, which is a significant inductive bias. However, the manuscript does not discuss how this requirement affects the practical applicability of the method or how it compares to methods that do not require such anchors.
- **Required correction** Add a discussion of the practical implications of the anchor requirement and whether it limits the generalizability of DiffDec to novel targets.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Molecule generation"
- **Issue** The authors state that models were run with default configurations, but do not provide the specific versions of the software packages or the exact commands used. This limits the reproducibility of the benchmark results.
- **Required correction** Provide a detailed configuration file or a link to a repository with the exact settings used for each model.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion states that "training data quality, especially the use of crystal-derived complexes, has a substantial impact on conformational performance." This is an important finding, but the manuscript does not provide a detailed analysis of which specific aspects of training data quality matter most.
- **Required correction** Consider adding a more detailed analysis of the relationship between training data characteristics and model performance, possibly in the supplementary materials.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Metric definitions
- **Evidence pointer** Methods section "Evaluation metrics"
- **Issue** The definition of the interaction score in Equation 4 uses a threshold of 0.1 for feature frequency, but the rationale for this threshold is not provided.
- **Required correction** Justify the choice of threshold or provide a sensitivity analysis.

- **Technical failings that need to be addressed before the case is established** R1-M1 (rediscovery metric interpretation), R1-M2 (confounding of architecture and training data), R1-M3 (lack of statistical testing)

- **Assessment against Nature-style criteria** 
  - Originality: The work is original in its scope and design. While individual components (e.g., PoseBusters, interaction fingerprints) have been used before, the integration into a unified benchmark covering both de novo design and H2L optimization, with a focus on target awareness and generalization, is novel. The introduction of the H2L benchmark and the TAScore metric are genuine contributions.
  - Scientific importance: The question of how well generative models perform in realistic drug discovery scenarios is of high importance to the field. The findings that current models have limited ability to rediscover active molecules, generate high-risk motifs, and generalize poorly to unseen proteins are significant and should influence future research directions.
  - Interdisciplinary readership: The manuscript is likely to appeal to researchers in computational chemistry, medicinal chemistry, and AI for science. The writing is generally accessible, though some sections assume familiarity with drug discovery terminology. The benchmark and evaluation framework would be of interest to a broad audience.
  - Technical soundness: The evaluation framework is thoughtfully designed, but the lack of statistical testing and the confounding of architecture and training data are significant weaknesses. The rediscovery metric interpretation also needs more careful treatment. These issues need to be addressed before the conclusions can be fully accepted.
  - Readability for nonspecialists: The manuscript is well-structured and the key concepts are explained clearly. However, the Methods section is dense and may be challenging for readers without a computational chemistry background. The figures would likely help, but they were not available for review.

- **Recommendation posture** Supportive if technical concerns are resolved. The benchmark and evaluation framework are valuable contributions, and the findings are likely to be of significant interest to the community. However, the concerns about metric interpretation, confounding factors, and statistical rigor need to be addressed before the conclusions can be fully supported.