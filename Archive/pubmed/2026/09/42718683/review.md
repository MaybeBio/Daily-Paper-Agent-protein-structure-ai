# Review

## Review setup
- **Input scope** Full manuscript (abstract, introduction, related work, proposed method, results and discussion, conclusion)
- **Assessment boundary** Scientific content, methodology, experimental design, claims, and evidence as presented in the manuscript
- **Shared manuscript claim summary** The authors propose a probabilistic gradient boosting framework (PROBC-VP) that integrates DNA-level and protein-level features to predict variant pathogenicity with explicit uncertainty quantification, achieving ROC AUC values of 0.9293, 0.9610, and 0.9646 on ClinVar 2020, GRCh37, and GRCh38 datasets respectively, outperforming existing methods.
- **Visible evidence base** Tables 1-7, Figures 1-16, performance metrics, ablation study, calibration analysis, feature importance analysis, VUS prediction results
- **Missing materials affecting confidence** Code repository not provided; trained model weights not available; no independent validation cohort; no re-implementation of baseline methods for direct comparison; no supplementary material with detailed feature lists or hyperparameter search logs

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in clinical genomics—variant pathogenicity prediction with uncertainty quantification. The integration of DNA- and protein-level features within a probabilistic gradient boosting framework is conceptually sound. However, the manuscript suffers from several critical methodological weaknesses that undermine confidence in the reported results. The comparative analysis relies entirely on literature-reported values rather than re-implemented baselines, making direct performance comparisons invalid. The dataset construction and train/test splitting procedures are inadequately described, raising concerns about data leakage. The claimed novelty is overstated given existing probabilistic approaches in the field. The mutation generation module lacks any experimental or biological validation. These issues must be resolved before the case for this framework can be established.

- **Who would be interested in the results, and why** Clinical geneticists and bioinformaticians working on variant interpretation pipelines would be interested in a method that provides calibrated uncertainty estimates alongside pathogenicity predictions. Researchers developing machine learning approaches for genomic medicine would find the feature engineering strategy and probabilistic formulation relevant. However, the current presentation does not provide sufficient evidence that the framework is ready for clinical deployment.

- **Major strengths** 1. The probabilistic gradient boosting formulation with heteroscedastic variance estimation is a principled approach to uncertainty quantification in variant classification. 2. The integration of both DNA-level and protein-level features is comprehensive and biologically motivated. 3. The ablation study systematically evaluates the contribution of different feature groups. 4. The evaluation on VUS variants demonstrates potential clinical utility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design / Comparative analysis
- **Claim pointer** The model outperforms existing methods (AlphaMissense, EVE, PrimateAI, etc.) across all three datasets.
- **Evidence pointer** Table 4, Figures 11-13
- **Concern** The comparative analysis uses ROC AUC values reported in previous publications rather than re-implementing baseline methods under identical conditions. The authors acknowledge this limitation but still present the comparison as evidence of superiority. Different studies use different dataset versions, preprocessing pipelines, train/test splits, and evaluation protocols. For example, AlphaMissense (Cheng et al., 2023) was evaluated on a different ClinVar release with different filtering criteria. The reported 0.94 for AlphaMissense on GRCh38 may not be comparable to the authors' 0.9646.
- **Why it matters** Without controlled head-to-head comparison, the claim of outperforming existing methods is not supported. The reported performance differences could be entirely due to dataset composition, label quality, or evaluation methodology rather than model superiority.
- **Resolution test** Re-implement at least 3-5 baseline methods (e.g., AlphaMissense, EVE, PrimateAI, REVEL) using the same training data, same test splits, and same evaluation metrics. Report results in a table with confidence intervals and statistical significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage / Experimental design
- **Claim pointer** The model generalizes well across ClinVar 2020, GRCh37, and GRCh38 datasets.
- **Evidence pointer** Section "Data acquisition and preprocessing", Section "Dataset description"
- **Concern** The description of train/test splitting is insufficient to rule out data leakage. The authors state a 70/15/15 split with stratification but do not specify how variants that appear in multiple datasets (e.g., the same variant in both GRCh37 and GRCh38) are handled. The deduplication protocol mentions coordinate-level deduplication within each dataset but does not clarify whether the same variant mapped to different genome builds is kept in separate experiments or could appear in training of one build and testing of another. Furthermore, the total dataset size (520,378 variants) and the split into ClinVar 2020, GRCh37, and GRCh38 subsets are not clearly defined—are these three independent datasets or overlapping?
- **Why it matters** Data leakage is a well-known pitfall in genomic machine learning that can inflate performance metrics by 10-20%. If the same variant appears in training and test sets (even across different genome builds), the reported ROC AUC values may not reflect true generalization.
- **Resolution test** Provide a clear description of how many unique variants exist across all three datasets, how overlapping variants are handled, and confirm that no variant in any test set appears in any training set (including across genome builds). Provide variant-level deduplication statistics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility / Methodology
- **Claim pointer** The framework achieves ROC AUC of 0.9293, 0.9610, and 0.9646 on ClinVar 2020, GRCh37, and GRCh38 respectively.
- **Evidence pointer** Table 2, Section "Performance results"
- **Concern** The reported performance metrics are suspiciously high, especially for GRCh37 and GRCh38 (0.9610 and 0.9646). Most state-of-the-art methods report ROC AUC in the range of 0.85-0.95 on similar benchmarks. The authors do not report standard deviations or confidence intervals for the main performance metrics (Table 2), only for the bootstrap analysis (Table 3). The bootstrap confidence intervals are extremely narrow (±0.003), which is unusual for genomic datasets with inherent label noise and class imbalance. The 5-fold cross-validation standard deviations (0.0009-0.0020) are also remarkably low.
- **Why it matters** Extremely narrow confidence intervals and near-perfect performance may indicate overfitting, data leakage, or label contamination. Without independent validation on a held-out cohort from a different source (e.g., a different ClinVar release or a clinical dataset), the reported performance cannot be trusted.
- **Resolution test** Validate the model on an independent dataset not used in any way during development (e.g., ClinVar 2024 release, or a clinical cohort). Report performance with 95% confidence intervals. Show calibration plots for the independent test set.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty / Related work
- **Claim pointer** The novelty lies in "systematic combination of multi-layered DNA-level and protein-level features with clinically-oriented uncertainty quantification, implemented around the framework of gradient boosting."
- **Evidence pointer** Introduction, Related work
- **Concern** The claimed novelty is overstated. Probabilistic gradient boosting for variant classification has been explored previously (e.g., CNVscore by Requena et al. [15] uses uncertainty estimates; the authors themselves cite methods that combine multiple feature types). The use of heteroscedastic likelihood for variance estimation in gradient boosting is standard in the machine learning literature (e.g., NGBoost, PGBM). The feature set (GC content, Shannon entropy, BLOSUM scores, conservation scores) is standard in the field. The authors do not clearly articulate what is novel beyond the specific implementation.
- **Why it matters** For a methods paper, the novelty must be clearly defined and distinguished from existing work. If the contribution is primarily the specific combination of existing techniques, this should be stated honestly and the evaluation should focus on demonstrating practical advantages over simpler alternatives.
- **Resolution test** Clearly state which components are novel and which are adopted from existing work. Provide a comparison with a simpler baseline (e.g., standard gradient boosting without probabilistic output, or logistic regression with the same features) to demonstrate the value of the probabilistic formulation. Discuss how the approach differs from CNVscore and other uncertainty-aware methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Clinical validity / Mutation generation module
- **Claim pointer** The mutation generation module "identifies sequence modifications that are predicted by the computational model to be associated with lower pathogenicity scores" and "even highly pathogenic variants can be transformed into benign provided suitable mutations are applied."
- **Evidence pointer** Section "Mutation generation module", Section "Performance results"
- **Concern** The mutation generation module is presented as a key contribution but lacks any experimental or biological validation. The example provided (GTC and ATC substitutions increasing benign probability to 91.5%) is a single anecdotal case. The authors explicitly state these are "in-silico hypotheses" but then make strong claims about "transforming pathogenic variants into benign." This language could be misinterpreted by readers as suggesting therapeutic potential.
- **Why it matters** In a clinical genomics context, suggesting that mutations can "correct" pathogenicity without any experimental evidence is potentially misleading. The module's utility for hypothesis generation is reasonable, but the claims need to be appropriately scoped.
- **Resolution test** Remove or substantially soften claims about "transforming" variants. Clearly state that these are computational predictions with no demonstrated biological effect. Provide systematic evaluation of the mutation generation module (e.g., how many proposed mutations are synonymous? How many are in known functional domains?).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Writing / Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract contains grammatical errors and unclear phrasing: "The suggested framework applies biological characteristics at both level of DNA and protein levels while also scaling the level of uncertainty in clinical decision making." The phrase "scaling the level of uncertainty" is unclear.
- **Required correction** Revise for clarity: "The framework integrates biological features at both the DNA and protein levels while providing calibrated uncertainty estimates for clinical decision-making."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology / Reproducibility
- **Affected element** Section "Data acquisition and preprocessing"
- **Evidence pointer** Location not provided
- **Issue** The authors state that "variants from several genome builds were analyzed separately, and variants were never moved between experimental data sets." However, it is unclear whether the same variant (e.g., rsID) that appears in both GRCh37 and GRCh38 is treated as the same variant or as independent instances.
- **Required correction** Clarify whether variants are tracked by rsID or genomic coordinates across genome builds, and how cross-build duplicates are handled.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Results / Reporting
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** The table reports Precision, Recall, F1-Score, ROC AUC, and PR AUC but does not report the threshold used for binary classification. The decision boundary θ is mentioned as 0.5 by default but it is unclear if this was used for all reported metrics.
- **Required correction** Report the threshold used for computing Precision, Recall, and F1-Score. If threshold tuning was performed, describe the procedure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology / Feature engineering
- **Affected element** Section "Feature engineering"
- **Evidence pointer** Location not provided
- **Issue** The feature engineering section describes 20 features (listed in Section "Dataset description") but the derivation of several features is unclear. For example, "FI_Mutation_composite" and "FI_General_Stability" are not defined in the feature engineering subsections.
- **Required correction** Provide clear definitions and formulas for all 20 features. Ensure consistency between the feature list in the dataset description and the features described in the feature engineering section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Results / VUS analysis
- **Affected element** Section "Predicting pathogenicity of variants of uncertain significance"
- **Evidence pointer** Table 7
- **Issue** The VUS analysis uses "likely benign" and "likely pathogenic" variants as ground truth for evaluating VUS predictions. However, these labels are themselves uncertain (hence "likely"). The model's agreement with these labels does not necessarily indicate correctness.
- **Required correction** Acknowledge the limitation that "likely" labels are not definitive ground truth. Consider using only variants with "Pathogenic" or "Benign" (without "likely") for validation, or discuss the implications of label uncertainty.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Writing / References
- **Affected element** Section "Related work"
- **Evidence pointer** Location not provided
- **Issue** The related work section is overly long (approximately 30 paragraphs) and includes tangential references (e.g., PROBC [28] and Eralp and Sefer [29] are about Hi-C analysis, not variant pathogenicity). The connection to the proposed method is tenuous.
- **Required correction** Condense the related work section to focus on methods directly relevant to variant pathogenicity prediction. Move or remove the Hi-C discussion unless it directly informs the feature set.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Methodology / Hyperparameter optimization
- **Affected element** Section "Machine learning pipeline"
- **Evidence pointer** Location not provided
- **Issue** The hyperparameter search space and optimal values are reported in detail, but it is unclear whether the same hyperparameters were used for all three datasets or if separate optimization was performed for each.
- **Required correction** Clarify whether hyperparameter tuning was performed separately for each dataset or once on a combined/representative dataset.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Results / Calibration
- **Affected element** Section "Calibration analysis"
- **Evidence pointer** Figure 10
- **Issue** The calibration curves are described but the figure is not provided in the manuscript text. The Brier scores (0.1141, 0.0907, 0.0909) are relatively high for well-calibrated models (ideal is 0 for perfect calibration, random guessing gives ~0.25 for balanced classes).
- **Required correction** Include the calibration plot figure. Discuss whether the Brier scores are acceptable given the class imbalance and provide context from the literature.

## Risk / unsupported claims
1. "The proposed model demonstrates strong performance across all three datasets... outperforming existing methods" — Not supported due to lack of controlled head-to-head comparison.
2. "Even highly pathogenic variants can be transformed into benign provided suitable mutations are applied" — Not supported; based on a single anecdotal example with no experimental validation.
3. "The model is not sensitive to the partition of the data" — The reported cross-validation standard deviations are implausibly low and may indicate data leakage.
4. "The framework possesses the flexibility to be applied to targeted genomic subsets, such as those specific to diverse population sub-groups" — No evidence of evaluation on diverse populations is provided.
5. "The model could be adapted to rare diseases having limited variant data" — No evidence or methodology for few-shot or transfer learning is presented.