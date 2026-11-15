## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The author reports development of an interpretable, gene-specific random-forest classifier for ACVRL1 missense variants, using protein-stability estimates, a conservation score, and structural context, achieving performance comparable to AlphaMissense while providing transparent evidence for each call.
- **Visible evidence base** Abstract text only; no data, code, or detailed methodology
- **Missing materials affecting confidence** Full methods, training/validation data splits, variant lists, ClinVar accession details, publication traceability criteria, cross-validation procedure, confidence intervals, calibration metrics, and any code or reproducibility information

## Reviewer
- **Overall assessment** The abstract presents a potentially useful contribution to variant classification in ACVRL1, addressing a real gap in interpretability of black-box predictors. However, the evidence provided is insufficient to evaluate the validity of the performance claims, the robustness of the methodology, or the generalizability of the findings. Several technical details are missing, and the reported equivalence to AlphaMissense is only partially supported. The work is of interest to the HHT and PAH genetics community, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Clinical geneticists and molecular diagnosticians working on hereditary hemorrhagic telangiectasia and pulmonary arterial hypertension, as well as researchers developing interpretable machine-learning tools for variant classification. The gene-specific, evidence-transparent approach could aid VUS prioritization for functional testing.
- **Major strengths** The problem is well-defined and clinically relevant. The focus on interpretability addresses a genuine limitation of AlphaMissense. The use of multiple evidence types (stability, conservation, structure) is reasonable. The inclusion of a temporal validation set (2025-2026 variants) is a positive feature.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "A structural/conservation-only classifier (Model 1b) reached a cross-validated ROC-AUC of 0.954 (95% CI 0.916-0.984), and a model adding sequence-based predictors (Model 1) reached 0.979, versus 0.983 for AlphaMissense on the same variants."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract reports cross-validated AUC values but does not describe the cross-validation scheme, the number of folds, the stratification strategy, or whether the same folds were used for all models. The 95% confidence intervals are presented without specifying the method of calculation. The comparison to AlphaMissense is made "on the same variants," but it is unclear whether AlphaMissense scores were obtained from the public database or recomputed, and whether the same variant set was used for all comparisons.
  - **Why it matters** Without a clear description of the validation protocol, the reported performance metrics cannot be independently assessed. Overfitting or data leakage in the training procedure could inflate AUC values. The equivalence claim depends critically on the comparability of the evaluation conditions.
  - **Resolution test** Provide a detailed methods section describing the cross-validation procedure, the exact variant sets used for training and testing, the source and version of AlphaMissense scores, and the statistical test used to support the equivalence claim.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Benign variants were the main weakness: Model 1b correctly classified 10/15, against 14/15 for AlphaMissense."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The benign variant set is extremely small (n=15), and the abstract does not state how these were selected, whether they were balanced across the structural or functional categories, or whether the same 15 variants were used for all models. The difference between 10/15 and 14/15 is based on a very small sample and may not be statistically meaningful.
  - **Why it matters** The claim that benign variants are the main weakness is a key finding, but with only 15 examples, the estimate is highly uncertain. The abstract does not report sensitivity, specificity, or precision-recall metrics, which are more informative for imbalanced clinical datasets.
  - **Resolution test** Report the full confusion matrix for each model, provide the benign variant selection criteria, and include confidence intervals or a statistical test for the difference in benign classification performance.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "I annotated 899 ACVRL1 missense variants with protein-stability estimates (FoldX, DynaMut2), a GREMLIN-style conservation score, and structural context."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not specify the source of the 899 variants, the version of the protein structure used, the parameters for FoldX and DynaMut2, the exact definition of the GREMLIN-style conservation score, or the criteria for assigning structural context. No code, data, or supplementary material is mentioned.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without these details, other researchers cannot replicate the annotation pipeline or the classifier. The gene-specific nature of the model also means that the approach cannot be generalized without a clear description of the feature engineering.
  - **Resolution test** Provide a detailed methods section with all software versions, parameters, and data sources, and make the code and annotated variant list available in a public repository.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** "I then trained random-forest classifiers on 311 variants with labels traceable to ClinVar or a publication (296 pathogenic-like, 15 benign-like)."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The label source is described as "traceable to ClinVar or a publication," but the abstract does not specify the ClinVar review status (e.g., criteria provided, multiple submitters, expert panel), the publication criteria for labeling, or how conflicting labels were resolved. The class imbalance (296 vs 15) is extreme and may affect model training and evaluation.
  - **Why it matters** The quality of the training labels is the foundation of the classifier. If labels are derived from sources with varying evidence standards, the model may learn biases rather than true pathogenic signals. The extreme class imbalance also raises concerns about the reliability of the reported AUC, which can be optimistic in such settings.
  - **Resolution test** Provide a detailed label curation protocol, including ClinVar star ratings, publication inclusion criteria, and conflict resolution rules. Report performance metrics that are robust to class imbalance, such as precision-recall AUC or balanced accuracy.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The phrase "equivalence within +/-0.05 AUC was supported for Model 1 only" is ambiguous. It is unclear what statistical test was used and whether the equivalence margin was pre-specified.
  - **Required correction** Specify the statistical test (e.g., two one-sided tests) and the pre-registered equivalence margin, or rephrase to describe the observed difference and its uncertainty.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not report any measure of calibration or uncertainty for individual variant calls, which is important for clinical use.
  - **Required correction** Add a statement on calibration or provide a reference to where this information can be found in the full manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretability
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The claim that the classifier "shows the structural or evolutionary evidence behind each call" is not substantiated with an example or a description of the interpretability mechanism (e.g., feature importance, SHAP values).
  - **Required correction** Provide a brief example of an interpretable output or describe the feature attribution method used.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scope
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not discuss the potential impact of the extreme class imbalance on the practical utility of the classifier for VUS prioritization.
  - **Required correction** Add a sentence acknowledging the limitation and describing how the classifier should be used in practice given the imbalance.

## Technical failings that need to be addressed before the case is established
- R1-M1 (validation protocol and equivalence testing)
- R1-M2 (benign variant set size and statistical robustness)
- R1-M3 (reproducibility of annotation pipeline)
- R1-M4 (label curation and class imbalance)

## Risk / unsupported claims
- The claim that the classifier "can approach AlphaMissense for ACVRL1" is only partially supported, as equivalence was demonstrated for Model 1 only, and the benign variant performance was notably worse.
- The claim that the classifier "shows the structural or evolutionary evidence behind each call" is not supported by any example or description of the interpretability mechanism in the abstract.
- The generalizability of the classifier to other genes or to variants outside the training distribution is not addressed and cannot be assessed from the abstract.
- The clinical utility of the classifier for VUS prioritization is stated as a potential use but is not supported by any prospective or functional validation data.

## Assessment against Nature-style criteria
- **Originality** Moderate. The application of interpretable machine learning to a specific gene with multiple evidence types is not entirely novel, but the focus on ACVRL1 and the explicit comparison to AlphaMissense with interpretability as a goal is a reasonable contribution.
- **Scientific importance** Moderate. Variant classification in ACVRL1 is clinically relevant, and improving interpretability of computational predictors could aid clinical decision-making. However, the impact is limited to a single gene and the abstract does not demonstrate a clear advance over existing tools beyond interpretability.
- **Interdisciplinary readership** Limited. The work is primarily of interest to computational biologists and clinical geneticists in the HHT/PAH field. The abstract does not frame the findings in a way that would attract a broader readership.
- **Technical soundness** Not established from the supplied material. The abstract lacks sufficient methodological detail to assess the validity of the performance claims, the robustness of the validation, or the reproducibility of the approach.
- **Readability for nonspecialists** The abstract is reasonably clear but uses technical terms (e.g., ROC-AUC, GREMLIN-style) without sufficient explanation for a general scientific audience. The clinical context is introduced adequately.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents a potentially useful approach, but the lack of methodological detail, the small benign variant set, and the incomplete equivalence testing prevent a positive recommendation. The author should provide the full methods, data, and code, and address the specific concerns raised above before the case can be considered.