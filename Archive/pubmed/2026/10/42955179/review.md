## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors present PNPShift, an artificial neural network-based chemical shift predictor that incorporates a correction term (PNPShift-X(PN)) to improve (1)H(N) chemical shift prediction for purine nucleotide-bound proteins, with reported error reductions of up to ~30% in nucleotide-binding regions across 28 tested proteins and ~6% RMSE reduction for unliganded proteins across 60 proteins. The program is further claimed to outperform other leading programs in maximum-entropy-based ensemble refinement and native-state discrimination from decoys.
- **Visible evidence base** Abstract text only; no quantitative data, statistical details, benchmark definitions, or methodological descriptions are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, training and test set compositions, benchmark definitions, comparison baselines, and code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a potentially useful contribution to the field of protein NMR chemical shift prediction, addressing a genuine gap for purine nucleotide-bound proteins. However, the evidence base available for this review is limited to the abstract, which precludes verification of the central claims. The reported improvements are plausible but not independently assessable without methodological detail and benchmark transparency. The general framework claim is intriguing but under-supported at this level of description.
- **Who would be interested in the results, and why** Researchers in NMR spectroscopy, structural biology, and computational biophysics who use chemical shift prediction for protein structure determination, ensemble modeling, and dynamics studies. Those working on nucleotide-binding proteins or other liganded systems would find the extension beyond unliganded proteins particularly relevant. Developers of machine learning-based predictors for biomolecular NMR parameters would also be interested in the proposed correction framework.
- **Major strengths** The problem addressed is well-defined and of practical importance, as most existing predictors are limited to unliganded proteins. The reported improvements, if reproducible, would be meaningful for both liganded and unliganded systems. The demonstration of utility in ensemble refinement and decoy discrimination suggests practical relevance beyond raw prediction accuracy.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient methodological detail to assess the validity of the correction approach, the statistical significance of the reported improvements, or the fairness of comparisons with other programs. The lack of information on training and test set separation, cross-validation procedures, and potential data leakage prevents assessment of generalizability.
- **Assessment against Nature-style criteria** Originality: the extension to purine nucleotide-bound proteins is a novel contribution, though the underlying neural network approach is not itself new. Scientific importance: the work addresses a real gap with potential impact on NMR-based studies of a protein class relevant to human biology. Interdisciplinary readership: the topic is of interest to NMR spectroscopists, structural biologists, and computational chemists, but the abstract is written in a way that is accessible to these groups. Technical soundness: cannot be assessed from the abstract alone; the reported metrics lack statistical context and methodological transparency. Readability for nonspecialists: the abstract is concise and understandable, though some terms (e.g., MEM-based ensemble refinement) assume domain familiarity.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the reported results are potentially significant, but the current evidence base is insufficient to establish the case. Full manuscript review with access to methods and data is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** PNPShift reduces (1)H(N) prediction errors in nucleotide-binding regions by up to ~30% across 28 tested purine nucleotide-bound proteins.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports a reduction of "up to ~30%" in prediction errors, but no statistical details are provided. It is unclear whether this figure represents a mean improvement, a best-case scenario, or a median across the 28 proteins. The variability across proteins, the error bars, and the significance of the improvement relative to baseline predictors are not reported.
- **Why it matters** Without measures of central tendency, dispersion, and statistical significance, the reader cannot determine whether the improvement is consistent and reliable or driven by a few favorable cases. This is critical for assessing the practical utility of the predictor.
- **Resolution test** Provide per-protein error reductions with mean, median, and standard deviation, along with paired statistical tests (e.g., Wilcoxon signed-rank) comparing PNPShift to baseline predictors. Report the distribution of improvements across the 28 proteins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** PNPShift also improves (1)H(N) predictions for unliganded proteins, achieving a ~6% reduction in RMSE across an independent test set of 60 proteins.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The claim of a ~6% RMSE reduction for unliganded proteins is presented without context. It is unclear what the baseline RMSE is, which predictor is used as the reference, and whether the improvement is statistically significant. The term "independent test set" is used, but the relationship of this set to the training data is not described.
- **Why it matters** The improvement for unliganded proteins is a secondary but important claim, as it suggests the method does not sacrifice performance on the original domain. Without baseline values and significance testing, the magnitude of the improvement cannot be interpreted.
- **Resolution test** Report absolute RMSE values for PNPShift and the baseline predictor on the 60-protein test set, along with confidence intervals or p-values. Clarify the composition of the test set and its non-overlap with training data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** PNPShift demonstrates superior performance in maximum-entropy (MEM)-based ensemble refinement and greater ability to discriminate native states from decoy conformations compared with other leading programs.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims superiority over "other leading programs" in two distinct applications, but no details are given on which programs were compared, what metrics were used, how the decoy sets were generated, or how the MEM refinement was evaluated. The criteria for "superior" and "greater ability" are not defined.
- **Why it matters** These application-based claims are central to demonstrating the practical value of PNPShift. Without clear benchmarks and comparison protocols, the claims are not falsifiable and cannot be independently verified.
- **Resolution test** Specify the comparison programs, the evaluation metrics (e.g., ensemble RMSD to reference, discrimination power as area under the ROC curve), the decoy generation protocol, and the statistical significance of the performance differences.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "PNPShift-X(PN) correction" is introduced without explanation of what "X" and "PN" denote or how the correction is computed.
- **Required correction** Define the correction term explicitly in the abstract or provide a brief description of its functional form.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Scope of evaluation
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract reports improvements only for (1)H(N) shifts. It is unclear whether PNPShift predicts other nuclei (e.g., (13)C, (15)N) and whether similar improvements are observed.
- **Required correction** State explicitly which nuclei are predicted and whether the reported improvements are specific to (1)H(N) or general.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Availability
- **Evidence pointer** Abstract; location not provided
- **Issue** No mention is made of the availability of PNPShift (e.g., open-source code, web server, or executable) or the training data.
- **Required correction** Include a statement on code and data availability, as is standard for computational tools.

## Risk / unsupported claims
- The claim of "up to ~30%" error reduction is not supported by statistical evidence in the abstract.
- The claim of "~6% RMSE reduction" for unliganded proteins lacks baseline values and significance testing.
- The claim of "superior performance" in MEM-based ensemble refinement and decoy discrimination is not supported by defined benchmarks or comparison protocols.
- The general framework claim for developing predictors for other liganded protein systems is plausible but not evidenced in the abstract.
- The statement that purine nucleotide-binding proteins are "encoded by approximately 10% of the human genome" is presented without citation and cannot be verified from the abstract.