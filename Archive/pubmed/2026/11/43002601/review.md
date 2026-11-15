## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, conclusions) without supplementary figures or tables
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to provided evidence, and clarity of presentation
- **Shared manuscript claim summary** The authors systematically investigate how training data composition affects the performance of three deep learning-based RNA 3D structure quality assessment models (ARES, lociPARSE, RNA3DCNN). They introduce a new dataset, RNA3DQA, retrain each model on nonnative datasets, and evaluate on an independent RNA-Puzzles-derived benchmark. They report that training data characteristics can dominate architectural differences, with RNA3DQA-trained lociPARSE achieving the best overall performance.
- **Visible evidence base** Main text tables (Tables 1–6), figures referenced (Figs 1–4), and statistical results described in text; supplementary materials referenced but not provided
- **Missing materials affecting confidence** Supplementary tables (S1–S5), supplementary figures (S1–S16), actual figure content, detailed hyperparameter settings, and the RNA3DCNN reimplementation code were not available for verification

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important question in RNA structural bioinformatics: how training data influence deep learning-based quality assessment models. The cross-training experimental design is conceptually sound and the introduction of a new dataset (RNA3DQA) is a valuable contribution. However, several methodological details and statistical analyses are incompletely described, and some claims appear stronger than the visible evidence supports. The manuscript would benefit from clearer reporting of benchmark construction, model reimplementation fidelity, and the practical significance of observed performance differences.

- **Who would be interested in the results, and why** Researchers developing deep learning methods for RNA 3D structure prediction and quality assessment, computational structural biologists working on RNA modeling pipelines, and methodologists interested in dataset design for structure prediction benchmarks. The findings on training data dominance over architecture could inform future dataset construction efforts across biomolecular structure prediction fields.

- **Major strengths**  
  1. Systematic cross-training design that directly addresses a previously undercharacterized question  
  2. Introduction of a new, publicly available dataset (RNA3DQA) with clear construction criteria  
  3. Use of an independent benchmark (RNA-Puzzles) with explicit efforts to prevent data leakage  
  4. Multi-faceted evaluation including aggregate scoring schemes and per-target statistical analysis  
  5. Practical recommendations for dataset design grounded in observed results

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that RNA3DCNN was reimplemented based on the original description, and that retrained models faithfully reproduce the original architectures.  
- **Evidence pointer** Section "Cross-dataset training protocol", Table 2  
- **Concern** The RNA3DCNN reimplementation is a critical component of the study, yet no verification of reimplementation fidelity is provided. The original RNA3DCNN paper may contain ambiguities in architecture details, training procedures, or preprocessing steps that could lead to behavioral differences. Without demonstrating that the reimplemented model reproduces the original model's performance on the original training data, the validity of all RNA3DCNN-related conclusions is uncertain.  
- **Why it matters** If the reimplementation differs from the original in meaningful ways, the cross-training comparisons involving RNA3DCNN may reflect implementation artifacts rather than genuine training data effects. This would undermine a core conclusion of the study.  
- **Resolution test** Provide quantitative evidence that the reimplemented RNA3DCNN reproduces the original model's performance on the original training/validation split, or clearly state the limitations of the reimplementation and temper conclusions accordingly.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that the benchmark dataset "contains neither PDB IDs from the training sets nor any Rfam families in common" with training data.  
- **Evidence pointer** Section "Benchmark set for independent evaluation"  
- **Concern** The exclusion criteria are described only at the level of Rfam family membership and PDB identifiers. However, structural similarity can exist across different Rfam families, and sequence similarity below the CD-HIT thresholds used (85–88.46%) could still lead to informative leakage. Additionally, the RNA-Puzzles targets themselves may have been used in the development of some prediction methods whose outputs are included in the benchmark, potentially introducing indirect biases. The authors do not report sequence identity checks between benchmark targets and training set sequences beyond Rfam family assignment.  
- **Why it matters** Incomplete leakage prevention could inflate performance estimates and weaken the claim that the benchmark provides an unbiased assessment of generalization.  
- **Resolution test** Report pairwise sequence identity distributions between benchmark targets and all training set sequences, and discuss any targets with unexpectedly high similarity. If such similarity exists, either exclude those targets or demonstrate that results are robust to their removal.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors conclude that "RNA3DQA yielding the overall best accuracy and ranking stability results specifically for the ARES model" and that "the best-performing model across both evaluation protocols uses IPA and was trained on the RNA3DQA dataset."  
- **Evidence pointer** Section "Results of cross-training experiment", Tables 4 and 5  
- **Concern** The aggregate scoring schemes (Top-3 and Correlation) are described only in general terms. The exact formulas, weighting schemes, and thresholds for "top-three finishes" are not fully specified in the visible text. Furthermore, the reported differences between top configurations (e.g., 26 versus 27 points in Table 5) are small, and no confidence intervals or significance tests are reported for the aggregate scores. The claim that one configuration is "best" may not be statistically distinguishable from others.  
- **Why it matters** Without uncertainty quantification on the aggregate scores, the ranking of configurations may not be robust, and the central conclusion about which training dataset is most effective could be overstated.  
- **Resolution test** Provide formal definitions of both scoring schemes, report bootstrap confidence intervals for aggregate scores, and perform pairwise significance tests between top configurations. If differences are not significant, state this explicitly and adjust the strength of conclusions.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Reproducibility  
- **Claim pointer** The authors state that "all datasets, trained models, and analysis scripts supporting this study are available in the RNA3DQA repository at Zenodo."  
- **Evidence pointer** Section "Data availability"  
- **Concern** While data availability is commendable, the manuscript does not specify the software versions, environment configurations, or exact commands needed to reproduce the training and evaluation pipeline. Given the known dependency issues with ARES (acknowledged by the authors), reproducibility may be challenging without a containerized environment or detailed setup instructions.  
- **Why it matters** Reproducibility is a core expectation for computational studies, and incomplete documentation could prevent others from building on this work.  
- **Resolution test** Provide a Dockerfile or equivalent container definition, a requirements file with pinned versions, and a step-by-step reproduction guide in the repository or supplementary materials.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section "Evaluation protocols"  
- **Evidence pointer** Location not provided  
- **Issue** The two scoring schemes are introduced but their exact definitions are not fully described in the main text. The reader is left to infer how "Top-3" and "Correlation" scores are computed from the brief description.  
- **Required correction** Provide explicit mathematical definitions of both scoring schemes in the main text or refer clearly to a supplementary section where they are fully specified.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Figure 3 and associated text  
- **Evidence pointer** Section "Training data impact on model performance"  
- **Issue** The text states that "the strongest positive effects are observed under maximum-based aggregation," but the figure is not available for verification. The description of aggregation methods (mean-, median-, minimum-, maximum-based) is not fully explained.  
- **Required correction** Clarify what is being aggregated (e.g., per-target Spearman correlations) and how each aggregation method is computed. Ensure figure captions are self-contained.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section "Case study: cross-training effect for benchmark unit PZ37"  
- **Evidence pointer** Figure 4  
- **Issue** The case study is presented as illustrative, but the selection of PZ37 as the case study target is not justified. It is unclear whether PZ37 was chosen because it is representative, exceptional, or convenient.  
- **Required correction** Briefly justify the selection of PZ37 or state that it was chosen as an illustrative example.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Technical detail  
- **Affected element** Section "Training sets for RNA quality assessment"  
- **Evidence pointer** Table 1  
- **Issue** The RNA3DCNN training set is stated to be unavailable, which limits the completeness of the cross-training analysis. The authors do not discuss the potential impact of this missing component on their conclusions.  
- **Required correction** Add a sentence acknowledging this limitation and discuss how it might affect the generalizability of the findings.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (RNA3DCNN reimplementation verification), R1-M2 (leakage prevention completeness), R1-M3 (statistical significance of aggregate scores)

- **Assessment against Nature-style criteria**  
  **Originality** The question of training data influence on RNA 3D structure quality assessment is relatively underexplored, and the systematic cross-training approach is a novel contribution. However, the individual components (the three models, the datasets, the benchmark) are all previously published, and the novelty lies primarily in their combination.  
  **Scientific importance** The findings have practical implications for dataset design in RNA structure prediction and quality assessment, which is a growing field. The conclusion that training data can outweigh architecture is potentially important but needs stronger statistical support.  
  **Interdisciplinary readership** The topic sits at the intersection of structural biology, machine learning, and bioinformatics. The manuscript is likely to appeal to a specialized audience within these fields, but the broader significance for general structural biology or machine learning audiences is not fully articulated.  
  **Technical soundness** The experimental design is generally sound, but the concerns above regarding reimplementation fidelity, leakage prevention, and statistical rigor need to be addressed. The lack of supplementary materials for verification limits confidence.  
  **Readability for nonspecialists** The manuscript is clearly written and the main concepts are accessible. However, some methodological details (e.g., scoring schemes, aggregation methods) could be explained more explicitly for readers outside the immediate subfield.

- **Recommendation posture** Supportive if technical concerns are resolved. The core question is important, the experimental design is appropriate, and the new dataset is a valuable resource. However, the manuscript cannot be accepted in its current form due to the unresolved concerns about RNA3DCNN reimplementation fidelity, potential data leakage, and insufficient statistical support for the central claims.

## Risk / unsupported claims
- The claim that RNA3DQA yields "the overall best accuracy and ranking stability results specifically for the ARES model" is not fully supported without confidence intervals or significance tests on aggregate scores.
- The claim that "training data characteristics play a dominant, model-dependent role" is supported by the data but may be overstated given the small differences between top configurations and the lack of uncertainty quantification.
- The assertion that the benchmark is fully independent of training data is not fully verifiable from the provided information, as sequence-level similarity checks beyond Rfam family assignment are not reported.
- The performance of the reimplemented RNA3DCNN relative to the original model is unverified, making all RNA3DCNN-related conclusions uncertain.
- The statement that "no significant difference observed in the remaining 11 contests" in the Wilcoxon test is reported without showing the actual p-values or effect sizes for those cases.