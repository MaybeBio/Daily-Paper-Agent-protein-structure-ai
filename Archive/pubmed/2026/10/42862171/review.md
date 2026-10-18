## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors prospectively evaluate three co-folding methods (AlphaFold3, Chai-1, Boltz-2) on 551 previously unpublished SARS-CoV-2 Mac1-ligand crystal structures and on three large-scale docking hit lists (AmpC β-lactamase, σ2 receptor, dopamine D4 receptor). They report that co-folding methods reproduce ligand poses with >50% accuracy at 2 Å RMSD, that confidence scores weakly track affinity, and that co-folding does not outperform docking in distinguishing true ligands from false positives in virtual screening hit lists.
- **Visible evidence base** Full text including results narrative, figure references, supplementary file references, methods section, and data availability statement
- **Missing materials affecting confidence** Figures, tables, and supplementary files referenced but not provided; specific numerical values for many reported statistics; details of statistical test implementations; complete crystallographic data

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: whether deep-learning co-folding methods can be applied prospectively to ligand pose prediction and virtual screening hit prioritization. The Mac1 dataset of 551 previously unpublished complexes is a substantial and valuable resource, and the prospective nature of the evaluation is a genuine strength. However, the manuscript's central claims are only partially supported by the evidence presented. The pose prediction results are convincing, but the affinity correlation analyses are weakened by the limited dynamic range of the dataset and the absence of key statistical details. The virtual screening results, while interesting, are presented in a way that makes it difficult to assess whether the conclusions are robust. The manuscript would benefit from clearer presentation of the statistical methods, additional analyses to support the claim of complementarity between docking and co-folding, and a more nuanced discussion of the limitations of the affinity predictions.

- **Who would be interested in the results, and why** Computational chemists and structural biologists working on ligand-protein complex prediction and virtual screening will find this study directly relevant. Drug discovery scientists using structure-based methods will be interested in the practical implications for hit prioritization workflows. Developers of deep-learning methods for molecular modeling will find the prospective evaluation valuable for understanding the strengths and limitations of current approaches. The Mac1 dataset itself will be a useful benchmark for future method development.

- **Major strengths** The prospective design of the study is a significant strength, as it avoids the circularity that plagues many retrospective evaluations. The Mac1 dataset is large and previously unpublished, providing a genuinely independent test set. The comparison across three co-folding methods and three different targets in the virtual screening component adds breadth. The authors are appropriately cautious in their interpretation of the affinity correlations, acknowledging the limited dynamic range. The discussion of complementarity between physics-based and deep-learning approaches is thoughtful and well-framed.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The authors report that Boltz-2 affinity predictions showed the strongest correlation with measured potency and achieved lower mean absolute error than a baseline predictor after calibration.
  - **Evidence pointer** Results section, Figure 4a; Methods, Statistical analysis
  - **Concern** The claim that Boltz-2 affinity predictions outperform a baseline predictor is based on a comparison to the mean pIC50 of the dataset. However, the dataset has a limited dynamic range (sub-micromolar to >500 µM), and the baseline predictor is not clearly defined. The manuscript does not report confidence intervals for the MAE values, nor does it specify how many compounds were used in the calibration. The statistical comparison between Boltz-2 and the baseline is not described with sufficient detail to assess its validity.
  - **Why it matters** The claim that Boltz-2 provides meaningful affinity predictions is a key finding of the study. If the comparison to baseline is not statistically robust, the conclusion that co-folding methods can predict affinity is weakened. The limited dynamic range of the dataset may also inflate the apparent performance of the baseline predictor, making the comparison less meaningful.
  - **Resolution test** The authors should provide a clear definition of the baseline predictor, report confidence intervals for all MAE values, and describe the statistical test used to compare Boltz-2 to the baseline. They should also report the distribution of pIC50 values in the dataset and discuss how the limited dynamic range affects the interpretation of the results.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors state that co-folding methods did not meaningfully outperform docking in distinguishing true ligands from false positives in the three virtual screening hit lists.
  - **Evidence pointer** Results section, Figure 5; Methods, Benchmarking co-folding on experimentally validated compounds
  - **Concern** The virtual screening analysis is presented with limited methodological detail. The manuscript does not specify how the hit lists were constructed, how many compounds were in each list, or how the thresholds for true hits and non-binders were defined for each target. The AUC values are reported, but the authors do not provide confidence intervals or statistical tests to determine whether the differences between methods are significant. The claim that co-folding methods "struggle" to re-rank hit lists is based on a comparison that may not be statistically powered.
  - **Why it matters** The virtual screening results are a central component of the manuscript's conclusions about the limitations of co-folding methods. Without clear methodological details and statistical analysis, it is not possible to determine whether the findings are robust or whether they reflect the specific choices made in this study.
  - **Resolution test** The authors should provide a detailed description of the hit list construction, including the number of compounds and the criteria for selecting them. They should report confidence intervals for all AUC values and perform statistical tests to compare the performance of different methods. They should also describe the thresholds used to define true hits and non-binders for each target.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation
  - **Claim pointer** The authors suggest that the weak correlation between docking and co-folding errors indicates complementarity between the two approaches.
  - **Evidence pointer** Results section, Figure 3—figure supplement 3; Discussion
  - **Concern** The claim of complementarity is based on the observation that errors between methods are not highly correlated. However, the manuscript does not provide a quantitative analysis of this complementarity, nor does it demonstrate that combining the methods would improve performance. The suggestion that integrating the methods "may help" is speculative and not supported by direct evidence.
  - **Why it matters** The claim of complementarity is a key takeaway of the manuscript and has practical implications for how these methods might be used in drug discovery. Without a direct demonstration that combining methods improves performance, the claim remains an interesting hypothesis rather than a supported conclusion.
  - **Resolution test** The authors should perform an analysis that directly tests whether combining docking and co-folding scores improves hit prioritization compared to either method alone. This could be done using a simple ensemble approach or a more sophisticated machine learning model.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, Mac1 X-ray crystallography
  - **Evidence pointer** Methods section
  - **Issue** The text states "nominal conentrations" which appears to be a typo for "nominal concentrations."
  - **Required correction** Correct the typo.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, Statistical analysis
  - **Evidence pointer** Methods section
  - **Issue** The statistical analysis section mentions "Friedman and post hoc Conover tests" and "Holm–Bonferroni correction" but does not specify the software or packages used for these analyses.
  - **Required correction** Specify the software and version used for statistical analyses.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, Model confidence and energy scores
  - **Evidence pointer** Results section, Figure 4
  - **Issue** The text states "the correlation was best for the Boltz-2 pIC50 (r = 0.6)" but does not specify whether this is Pearson or Spearman correlation.
  - **Required correction** Specify the correlation coefficient used.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Data availability
  - **Evidence pointer** Data availability section
  - **Issue** The data availability statement mentions that 468 accession codes are listed in Supplementary file 1, but the total number of complexes is stated as 551. The discrepancy between 468 and 551 is not explained.
  - **Required correction** Clarify the relationship between the 468 deposited structures and the 551 complexes analyzed.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, Co-folding struggles to reliably re-rank docking hit lists
  - **Evidence pointer** Results section, Figure 5
  - **Issue** The text states "the AF3 correlation with binders pKi was not much worse than docking's (r = 0.183)" but does not report the corresponding correlation for docking.
  - **Required correction** Report the docking correlation value for comparison.

- **Technical failings that need to be addressed before the case is established** The statistical analysis of the affinity predictions (R1-M1) and the virtual screening results (R1-M2) need to be strengthened with additional details and analyses. The claim of complementarity (R1-M3) needs direct evidence. These issues must be addressed before the manuscript's central conclusions can be considered fully supported.

## Risk / unsupported claims
- The claim that Boltz-2 affinity predictions outperform a baseline predictor is not fully supported due to unclear baseline definition and lack of statistical details.
- The claim that co-folding methods "struggle" to re-rank docking hit lists is not fully supported due to limited methodological detail and lack of statistical analysis.
- The claim of complementarity between docking and co-folding is speculative and not directly demonstrated.
- The statement that "co-folding can accurately reproduce poses of ligands dissimilar to those on which it trained" is supported by the RMSD data, but the analysis of similarity to training data relies on a single fingerprint method and may not capture all relevant chemical similarity.
- The claim that "co-folding reliably recapitulates dominant ligand-binding interactions" is based on analysis of a subset of interactions and may not generalize to all interaction types.