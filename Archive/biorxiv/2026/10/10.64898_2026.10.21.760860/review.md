## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability)
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided text. No supplementary materials, code, or figures were available for inspection beyond those referenced in the text.
- **Shared manuscript claim summary** The authors propose an interpretable machine-learning framework for protein-protein interaction (PPI) prediction using three sequence-derived descriptor families (Auto-Covariance, Conjoint Triad, Local Descriptors) combined with classical classifiers (SVM, RF, XGBoost). They report high cross-validation and independent test-set performance, with Random Forest achieving 99.51% accuracy on an unseen human PPI dataset, and provide feature-importance analyses to support biological interpretability.
- **Visible evidence base** Abstract; Sections 1–4 (Introduction, Materials and Methodology, Results and Discussion, Conclusion); Tables 1–13 referenced; Figures 1–7 referenced; Data availability URLs.
- **Missing materials affecting confidence** Actual tables and figures (including feature-importance plots, ROC/PR curves, dataset statistics) were not provided. No code, hyperparameter settings, or detailed experimental configuration were included. The exact composition of the training and test datasets (e.g., number of positive/negative pairs, species origin) is not fully specified in the text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology with a straightforward, interpretable approach. The reported performance metrics are strong, but several methodological ambiguities and potential data-leakage concerns need to be resolved before the claims can be fully accepted. The work is technically sound in its general design but lacks sufficient detail in key areas, particularly dataset construction, class-balancing procedures, and hyperparameter optimization. The biological interpretation of feature importance is plausible but would benefit from more rigorous validation.
- **Who would be interested in the results, and why** Researchers in bioinformatics, computational biology, and systems biology working on PPI prediction, interactome mapping, and drug-target prioritization would find this work relevant. The emphasis on interpretability and low computational cost may appeal to groups seeking alternatives to deep learning for high-throughput screening applications.
- **Major strengths** 1) Use of well-established, biologically motivated sequence descriptors that are computationally efficient. 2) Evaluation on both cross-validation and an independent unseen dataset, which is a good practice for assessing generalization. 3) Feature-importance analysis provides interpretable insights into which sequence properties drive predictions. 4) Comparison of multiple classical classifiers offers a practical benchmark.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data integrity and leakage prevention
  - **Claim pointer** The authors claim the dataset was designed to minimize information leakage by ensuring proteins assigned to one subset were not present in other subsets, and that the independent Human-PPI test set consists of "completely unseen protein pairs."
  - **Evidence pointer** Section 2.1, Table 1, Table 2
  - **Concern** The description of dataset partitioning is insufficient to verify that no protein-level overlap exists between training and test sets. The text states that the Intra-0 subset was used and that KaHIP-based partitioning minimized sequence similarity, but the exact criteria for "unseen" are not defined. If proteins in the test set share high sequence identity with training proteins, the reported generalization performance could be inflated. Additionally, the class-balancing procedure (hybrid sampling) is described only vaguely; the ratio of positive to negative samples after balancing is not reported, which affects the interpretation of accuracy and F1 scores.
  - **Why it matters** PPI prediction benchmarks are highly sensitive to data leakage. Without explicit verification of sequence-level separation and clear reporting of class distributions, the reported 99.51% accuracy on the unseen test set cannot be taken at face value. This is a core issue that undermines the central claim of robust generalization.
  - **Resolution test** Provide a detailed description of the dataset construction, including the number of unique proteins in training and test sets, the sequence-identity threshold used for separation, and the positive-to-negative ratio before and after balancing. Ideally, provide a supplementary figure showing the sequence-identity distribution between training and test proteins.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological reproducibility
  - **Claim pointer** The authors state that SVM, RF, and XGBoost were trained and evaluated, with RF selected as the final model based on test-set performance.
  - **Evidence pointer** Section 2.4, Section 3.3, Tables 10 and 11
  - **Concern** No hyperparameter values, kernel types (for SVM), number of trees (for RF), learning rates or tree depths (for XGBoost), or any model selection procedure are reported. The text mentions "Scikit-learn" but does not specify whether default parameters were used or if tuning was performed. Without this information, the results cannot be reproduced, and the comparison between classifiers is not fully interpretable.
  - **Why it matters** Reproducibility is a fundamental requirement for computational studies. The lack of model configuration details prevents other researchers from replicating the experiments or assessing whether the reported performance is an artifact of particular settings.
  - **Resolution test** Provide a table or supplementary section listing all hyperparameters for each model, the search space if tuning was performed, and the criterion used for model selection (e.g., cross-validation score vs. test-set score).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evaluation methodology
  - **Claim pointer** The authors report cross-validation accuracy of 97.97% for XGBoost and test-set accuracy of 99.51% for RF, and state that RF "emerged as the top-performing architecture" on the unseen dataset.
  - **Evidence pointer** Section 3.3, Tables 10 and 11
  - **Concern** The selection of RF as the final model is based solely on test-set performance. This is methodologically problematic because the test set should be used only once for final evaluation, not for model selection. If the test set was used to choose between models, the reported test performance is optimistically biased. The authors should clarify whether the test set was used during model development or only for final assessment.
  - **Why it matters** Using the test set for model selection violates standard evaluation protocols and can lead to overfitting to the test set, undermining the claim of generalization to unseen data.
  - **Resolution test** Clarify the model selection procedure. If the test set was used to choose RF over XGBoost, the authors should either use a separate validation set for model selection or report performance with appropriate caveats.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretation
  - **Claim pointer** The authors state that feature-importance analysis revealed that short-range physicochemical correlations, regional amino-acid compositions, and specific triad patterns drive PPI discrimination, and they interpret these as biologically meaningful.
  - **Evidence pointer** Section 3.3, Figures 6 and 7, Tables 12 and 13
  - **Concern** The biological interpretation is speculative and not validated against known PPI structural data or functional annotations. For example, the claim that "short-range polarity organization may contribute substantially to PPI discrimination" is plausible but not tested. The authors do not compare their identified features with known interface properties or perform any external validation (e.g., on independent datasets with known interaction mechanisms).
  - **Why it matters** The interpretability claim is a key selling point of the manuscript. Without validation, the feature-importance analysis remains descriptive rather than biologically informative, weakening the contribution beyond predictive performance.
  - **Resolution test** Perform additional analyses to support the biological interpretation, such as comparing top features with known interface-residue propensities, or testing the model on datasets with annotated interaction types (e.g., transient vs. permanent).
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Section 2.3, feature extraction
  - **Evidence pointer** Section 2.3, Tables 5–8
  - **Issue** The text describes the feature extraction methods but does not provide the actual formulas for normalization and autocovariance computation. The equations are referenced but not shown in the text provided.
  - **Required correction** Include the full equations for normalization and autocovariance, or refer to a supplementary file where they are provided.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 3.3, Tables 10 and 11
  - **Evidence pointer** Section 3.3
  - **Issue** The text reports mean cross-validation accuracy but does not report standard deviations or confidence intervals. Variability across folds is not discussed.
  - **Required correction** Report standard deviations or confidence intervals for all cross-validation metrics.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Comparison with prior work
  - **Affected element** Section 3.4, Discussion
  - **Evidence pointer** Section 3.4
  - **Issue** The discussion mentions DeepPPI as a deep-learning baseline but does not provide a quantitative comparison with the proposed method or with other classical approaches.
  - **Required correction** Include a table comparing the proposed method with at least one or two published baselines on the same or similar datasets.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Language and formatting
  - **Affected element** Abstract, Section 1
  - **Evidence pointer** Abstract, Section 1
  - **Issue** There are minor grammatical issues and inconsistent spacing (e.g., "descriptors,specifically" in the abstract).
  - **Required correction** Proofread the manuscript for grammatical errors and formatting inconsistencies.
- **Technical failings that need to be addressed before the case is established** R1-M1 (data leakage verification) and R1-M2 (reproducibility of model configuration) are the most critical. R1-M3 (test-set-based model selection) also needs clarification. These issues must be resolved before the reported performance can be considered reliable.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The combination of three established descriptor families with classical classifiers is not conceptually novel, though the systematic comparison and feature-importance analysis add some value.  
  *Scientific importance*: Moderate. PPI prediction is an active field, and interpretable methods are useful, but the incremental improvement over existing approaches is not clearly demonstrated.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to bioinformatics specialists; the biological insights are not deep enough to attract a broader structural biology or drug discovery audience.  
  *Technical soundness*: Currently insufficient. The methodological details are incomplete, and the data-leakage concern is unresolved.  
  *Readability for nonspecialists*: Acceptable. The text is generally clear, though some sections (e.g., feature extraction) assume familiarity with the descriptors.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the methodological ambiguities and data-integrity concerns must be addressed. I would be supportive if the authors provide detailed dataset construction information, full model configurations, and clarify the model selection procedure.

## Risk / unsupported claims
- The claim that the model "avoids overfitting" is not fully supported without standard deviation reporting and a clearer description of the test-set construction.
- The biological interpretation of feature importance (e.g., "short-range polarity organization drives PPI discrimination") is speculative and not validated.
- The statement that the framework has "minimal computational overhead" is plausible but not quantified.
- The claim that the model is suitable for "efficient, scalable interactome screening" is not demonstrated with runtime or scalability experiments.