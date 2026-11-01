## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability) as provided.
- **Assessment boundary** Scientific and technical evaluation of the described framework, methodology, experimental design, reported results, and claims. No evaluation of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors present EquiDesign, a deep learning framework for inverse protein folding that uses an Equiformer-enhanced architecture with multistep feature extraction, spatial K-nearest neighbor graph construction, and geometric attention. They claim superior sequence recovery on standard and challenging benchmarks compared to state-of-the-art methods, along with generated sequences exhibiting high structural fidelity, folding stability, and diversity.
- **Visible evidence base** Abstract, introduction, methods (dataset preprocessing, model architecture, training, evaluation metrics, comparison baselines, ablation study, sampling strategy, simulation environment), results (ablation, benchmark comparisons, per-residue accuracy, generalization, de novo design), discussion, conclusion, data availability statement. Tables and figures referenced but not provided in full.
- **Missing materials affecting confidence** Full tables (Tables 1-8), all figures (Figs 1-4), all supplementary materials (Tables S1-S17, Figs S1-S5), detailed hyperparameter configurations, baseline implementation details, statistical test specifications, and the actual numerical results. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript describes a technically plausible architecture for inverse protein folding that combines established components (Equiformer, geometric graph construction, multistep feature extraction) in a coherent manner. The methodological description is largely clear, and the evaluation strategy covers multiple benchmark types. However, the provided text lacks the quantitative results, full tables, and figures necessary to assess whether the claimed improvements are real, substantial, and statistically robust. Several claims in the abstract and results appear stronger than what the visible evidence can support. The relationship to prior work, particularly ProtseqGen, is acknowledged but the incremental contribution needs sharper delineation. The manuscript would benefit from clearer reporting of experimental conditions, baseline fairness, and statistical rigor.

- **Who would be interested in the results, and why** Computational protein designers, researchers working on inverse folding and sequence design, and developers of geometric deep learning methods for biomolecular applications. The framework addresses a recognized bottleneck in de novo protein design, and the equivariant architecture is of general interest to the machine learning for structural biology community. Practitioners seeking improved sequence recovery tools for fixed backbones would also find the work relevant.

- **Major strengths**
  1. The architectural design is well motivated: separating invariant scalar and equivariant vector features is a principled approach for preserving geometric information during message passing.
  2. The evaluation spans multiple benchmark types (standard, disordered, free-modeling), which is more comprehensive than many prior studies.
  3. The ablation study is thoughtfully designed to isolate contributions of specific components.
  4. The authors address important confounds: training-set memorization, compositional bias, and physical energy landscapes.
  5. Code and data availability statements are provided, supporting reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "EquiDesign achieves superior sequence recovery on standard and challenging test sets compared with state-of-the-art methods" (Abstract); "EquiDesign achieved recovery rates of 59.47% on TS50 and 61.08% on TS500, outperforming most SOTA methods" (Results)
- **Evidence pointer** Tables 4, 5, 6; location not provided for actual numerical values
- **Concern** The central quantitative claims of the manuscript cannot be evaluated because the actual results tables are not included in the provided text. The reader is told that EquiDesign outperforms baselines, but the magnitude of improvement, the variance across runs, and the specific comparison values are absent. Without these data, the claim of "superior" performance is unverifiable.
- **Why it matters** The primary contribution of this work is empirical: a new architecture that improves sequence recovery. If the numerical evidence is not presented, the case for the method's utility is not established.
- **Resolution test** Provide full results tables with mean and standard deviation for all methods on all benchmarks, including per-metric breakdowns. State clearly which differences are statistically significant and with what test.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness
- **Claim pointer** "EquiDesign is benchmarked against 16 representative baselines, categorized into five architectural families" (Methods)
- **Evidence pointer** Methods section, "Evaluation metrics" and "EquiDesign model training and calibration"; location not provided for baseline training details
- **Concern** The manuscript does not describe how baselines were trained or configured. Were all models trained on the same data splits? Were hyperparameters optimized per model or fixed? Were the same evaluation protocols used? Unequal training conditions can produce misleading comparisons.
- **Why it matters** Benchmark comparisons are only meaningful if all methods are evaluated under equivalent conditions. Without this information, observed differences could reflect tuning effort rather than architectural merit.
- **Resolution test** Describe the training and evaluation protocol for each baseline, including data splits, hyperparameter selection, and any differences in input features. State whether baselines were run with their default settings or re-tuned.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "EquiDesign significantly outperforms the other four methods across all metrics" (Results, referring to Supplementary Table S3)
- **Evidence pointer** Supplementary Tables S3-S5; location not provided
- **Concern** The claim of statistical significance is made, but the statistical test used is not specified in the visible text. The number of paired comparisons, correction for multiple testing, and the distributional assumptions are not described. With 10 training runs per model, the effective sample size is small, and the choice of test matters.
- **Why it matters** Significance claims require transparent reporting of the test procedure. Without this, the reader cannot assess whether the reported differences are robust or could arise from chance.
- **Resolution test** Specify the statistical test used, whether it was paired or unpaired, how multiple comparisons were handled, and report effect sizes alongside p-values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Validation depth
- **Claim pointer** "the generated sequences exhibit exceptional structural fidelity, folding stability, and sequence diversity" (Abstract); "50%–100% of the generated sequences were predicted to be foldable (scRMSD <2.0 Å) by both ESMFold and AF3" (Results)
- **Evidence pointer** Table 8, Supplementary Table S11, Fig 4; location not provided
- **Concern** The validation of designed sequences relies entirely on computational predictors (ESMFold, AF3, Rosetta). No experimental validation is presented. While this is common in computational papers, the claim of "exceptional" fidelity is strong given that computational predictors can be biased toward their training distributions. The diversity analysis is also limited to sequence-level metrics without functional assays.
- **Why it matters** The ultimate goal of protein design is functional proteins. Computational metrics are necessary but not sufficient evidence of design quality. The strength of the claims should match the evidence level.
- **Resolution test** Soften claims about "exceptional" fidelity, or add experimental validation for at least a subset of designs. If experimental data are not available, clearly state this as a limitation and frame claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty delineation
- **Claim pointer** "The key methodological novelty lies in replacing the conventional Message Passing Neural Network (MPNN) layers with an Equiformer-driven architecture" (Discussion)
- **Evidence pointer** Discussion section; location not provided
- **Concern** The manuscript states that the initial feature extraction is inherited from ProtseqGen, and the novelty is the Equiformer replacement. However, the specific advantages of this replacement are not demonstrated through targeted experiments. The ablation study shows component contributions, but does not directly compare Equiformer against alternative equivariant or attention-based encoders.
- **Why it matters** The contribution of the work depends on showing that the Equiformer architecture provides a meaningful improvement over other possible choices, not just over the specific baselines tested.
- **Resolution test** Add an ablation that replaces Equiformer with an alternative modern encoder (e.g., a standard transformer or another equivariant network) to demonstrate the specific benefit of the chosen architecture.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Dataset collection and preprocessing"
- **Evidence pointer** "This yielded 29 453 training, 1732 validation, and 3466 test structures [25]"
- **Issue** The reference [25] for the data split is not described. It is unclear whether this split is standard in the field or specific to this work.
- **Required correction** Describe the split procedure or cite the original source of the split.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "EquiDesign model training and calibration"
- **Evidence pointer** "Manual hyperparameter tuning (Supplementary Tables S1 and S2) precedes evaluation"
- **Issue** The hyperparameter search space and selection criterion are not described in the main text.
- **Required correction** Briefly describe the hyperparameter ranges explored and the selection criterion used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Simulation environment"
- **Evidence pointer** "EquiDesign was implemented in PyTorch 2.4.1 and Python 3.10.10"
- **Issue** The number of training epochs, batch size, and total training time are not reported.
- **Required correction** Add these training details to the methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and throughout
- **Evidence pointer** "multistep Equiformer-enhanced architecture"
- **Issue** The term "multistep" is not clearly defined. It is unclear whether this refers to multiple Equiformer layers, multiple stages of feature extraction, or something else.
- **Required correction** Define "multistep" in the methods section when the architecture is first described.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results, "Generalization evaluation on canonical benchmarks"
- **Evidence pointer** "After removing all overlapping proteins with the training set, the evaluation comprised 26 and 243 previously unseen samples for TS50 and TS500, respectively"
- **Issue** The original TS50 and TS500 contain 50 and 500 proteins. The reduction to 26 and 243 is substantial, but the filtering criteria are not described in the main text.
- **Required correction** Describe the overlap removal procedure and report results on both the full and filtered sets if possible.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, "Perresidue accuracy and prediction confidence"
- **Evidence pointer** "Fig 2A" and "Fig 2B"
- **Issue** The text describes trends in the figures, but the figures are not available for review. The description is qualitative.
- **Required correction** Provide quantitative summaries of the per-residue accuracy data in the text or tables.

- **Technical failings that need to be addressed before the case is established**
  1. Missing numerical results for all benchmark comparisons (R1-M1).
  2. Undescribed baseline training and evaluation protocol (R1-M2).
  3. Unspecified statistical testing procedure (R1-M3).
  4. No direct comparison of Equiformer against alternative modern encoders (R1-M4).
  5. Computational-only validation with strong claims of "exceptional" fidelity (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The combination of Equiformer with inverse folding is a reasonable extension of existing work, but the core idea of using equivariant networks for protein sequence design is not entirely new. The specific architectural choices and their justification are somewhat incremental.
  - **Scientific importance**: Potentially relevant to the protein design community, but the importance depends on the magnitude of improvement over existing methods, which cannot be assessed from the provided text.
  - **Interdisciplinary readership**: The work sits at the intersection of machine learning and structural biology. The methods section is technical and may be challenging for non-specialists, but the problem framing is accessible.
  - **Technical soundness**: The architecture is plausible, and the evaluation strategy is thoughtful. However, the lack of visible numerical results and statistical details prevents a full assessment of technical soundness.
  - **Readability for nonspecialists**: The abstract and introduction are readable, but the methods section assumes significant familiarity with geometric deep learning and protein design terminology. The manuscript would benefit from a brief explanation of key concepts for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a plausible and potentially useful framework, but the central quantitative claims cannot be verified without the full results tables, figures, and statistical details. The authors should be invited to provide the complete results and address the methodological reporting gaps. If the numerical evidence supports the claims, the work could be of interest to the community.