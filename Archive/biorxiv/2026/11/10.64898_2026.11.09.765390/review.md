## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion, data availability statement)
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and consistency of evidence presented in the provided text. No external data or code was accessed.
- **Shared manuscript claim summary** The authors present EvoPhi-DDG, a training-free adaptation of the MSAesm_ddG predictor that enforces exact thermodynamic antisymmetry and same-site transitivity by reformulating predictions as differences of a learned potential. They further combine EvoPhi-DDG with the published JanusDDG model via fixed equal-weight averaging, reporting improved predictive accuracy on S669, S96, and PTmul-NR benchmarks, and reduced multisite pathway-closure error.
- **Visible evidence base** Main text figures (Figures 1–6 referenced), Supplementary Figures S1–S3, Supplementary Tables S1–S10, and the Methods section describing datasets, model architectures, and evaluation protocols.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in protein stability prediction: enforcing thermodynamic consistency in learned predictors. The proposed EvoPhi-DDG reformulation is elegant and the theoretical analysis of the ReLU head is a clear strength. The empirical evaluation is reasonably thorough, but several concerns about the strength of the claims, the interpretation of the benchmark results, and the generalizability of the theoretical guarantees need to be addressed. The distinction between predictive gains from averaging and consistency gains from the potential-based reformulation is well articulated, but the practical significance of the consistency improvements is not fully demonstrated.
- **Who would be interested in the results, and why** Researchers in computational protein engineering, biophysics, and machine learning applied to biology. The work is particularly relevant to those developing or using stability predictors, as it offers a principled way to enforce physical constraints without retraining, and to those interested in model ensembling and complementarity analysis.
- **Major strengths**
  1. The theoretical analysis of the MSAesm_ddG head is a significant contribution. The derivation of the exact potential-difference form when hidden biases are zero, and the explicit residual for nonzero biases, provides a clear and testable architectural explanation for the observed near-transitivity.
  2. The separation of predictive accuracy from physical consistency as distinct evaluation criteria is methodologically sound and clearly presented.
  3. The use of fixed, equal-weight averaging without additional training is a parsimonious and well-justified integration strategy, avoiding overfitting concerns.
  4. The residual analysis (Section 2.6) provides a useful statistical framework for understanding when and why ensembling helps, beyond simple model diversity arguments.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim strength vs. evidence
  - **Claim pointer** The abstract and Section 2.3 state that the ensemble "outperforms both components on S669 and S96, achieving Pearson correlations of 0.59 and 0.55, respectively, compared with 0.55 and 0.52 for JanusDDG and 0.53 and 0.48 for EvoPhi-DDG."
  - **Evidence pointer** Section 2.3, Figure 5, Supplementary Table S9
  - **Concern** The reported improvements in Pearson correlation (e.g., 0.55 to 0.59 on S669) are modest. The manuscript does not provide confidence intervals for these point estimates in the main text, nor does it report whether these differences are statistically significant. The bootstrap analysis is mentioned for the multisite RMSE comparison (Section 2.3), but not for the primary single-site accuracy metrics. Without uncertainty quantification, the claim of "outperforming" is not fully supported.
  - **Why it matters** The central claim of the paper is that the ensemble improves predictive accuracy. If the observed gains are within the noise of the evaluation, the practical value of the ensemble for accuracy is questionable, and the paper's contribution would rest solely on the consistency guarantees.
  - **Resolution test** Provide 95% confidence intervals (e.g., via the described protein-bootstrap procedure) for the Pearson correlations on S669, S96, and PTmul-NR for all models compared. Report whether the differences are statistically significant. If the gains are not significant, temper the language in the abstract and results accordingly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability of theoretical guarantee
  - **Claim pointer** Section 2.1 and Methods 3.2.4 state that EvoPhi-DDG "guarantees exact same-site transitivity under fixed alignment contexts."
  - **Evidence pointer** Section 2.1, Methods 3.2.4
  - **Concern** The theoretical guarantee of exact transitivity is derived for a fixed alignment context and a fixed mutation site. The manuscript correctly notes that this does not establish general multisite transitivity. However, the practical utility of the guarantee is unclear. The evaluation of multisite consistency (Section 2.3, Figure 4) shows that the ensemble still has nonzero closure error (RMSE 0.10 kcal/mol at ten intermediates). While this is lower than JanusDDG, it is not zero. The manuscript should more clearly state that the exact guarantee applies only to a narrow set of conditions (same site, same alignment) and that the empirical improvement on multisite paths is a separate, weaker result.
  - **Why it matters** Overstating the scope of the theoretical guarantee could mislead readers into thinking the model is exactly thermodynamically consistent in all practical scenarios. The distinction between the exact guarantee and the empirical improvement is crucial for correct interpretation.
  - **Resolution test** In the abstract and discussion, explicitly state that the exact transitivity guarantee is limited to single-site mutations under a fixed alignment context, and that for multisite mutations, the model only shows empirically reduced, but not eliminated, closure error.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Benchmark interpretation
  - **Claim pointer** Section 2.3 states that on PTmul-NR, the ensemble "achieves a Pearson correlation of 0.66, improving on JanusDDG’s 0.61 and matching the EvoPhi-DDG extension at the reported precision."
  - **Evidence pointer** Section 2.3, Figure 5, Supplementary Table S9
  - **Concern** The PTmul-NR benchmark contains only 82 variants across 13 distinct WT sequences. The manuscript acknowledges this limitation in Section 2.3, but the claim of "matching" the EvoPhi-DDG extension is based on a very small sample. The lack of a clear advantage over the stronger component on this benchmark is not framed as a potential limitation of the ensembling approach for multiple mutations.
  - **Why it matters** The manuscript aims to show that the ensemble is beneficial. If on the multiple-mutation benchmark the ensemble does not improve over the best component, this is an important boundary condition for the method's applicability. The discussion should address this more directly.
  - **Resolution test** Discuss the implications of the PTmul-NR result more thoroughly. Is the lack of improvement due to the small sample size, the nature of the task, or a fundamental limitation of the ensembling approach for multiple mutations? Suggest potential avenues for future work to address this.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1, Figure 1
  - **Evidence pointer** Section 2.1, Figure 1
  - **Issue** The description of the EvoPhi-DDG architecture in Section 2.1 is dense and relies heavily on equations that are not fully introduced in the main text. Figure 1 is referenced but not described in detail.
  - **Required correction** Provide a more accessible, high-level description of the EvoPhi-DDG architecture in the main text, and ensure Figure 1 clearly illustrates the key components (e.g., the shared encoder, the potential-difference head, the background-aware extension).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods 3.1.2
  - **Evidence pointer** Methods 3.1.2
  - **Issue** The description of the alignment construction and filtering is brief. The specific parameters for MMseqs2 and HHfilter are mentioned, but the exact commands or a link to a configuration file are not provided.
  - **Required correction** Provide the exact commands or a configuration file for the alignment generation and filtering steps to ensure reproducibility.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Section 2.4, Supplementary Table S10
  - **Evidence pointer** Section 2.4, Supplementary Table S10
  - **Issue** The classification analysis in Section 2.4 reports ROC-AUC and other metrics, but the manuscript does not state whether the differences between models are statistically significant. Given the small number of positive examples in some benchmarks (e.g., 23 stabilizing variants in S461), this is a concern.
  - **Required correction** Report confidence intervals for the classification metrics, or at least acknowledge the limitations of the small sample sizes in the discussion.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Section 2.6
  - **Evidence pointer** Section 2.6
  - **Issue** The residual analysis in Section 2.6 is interesting but the presentation is somewhat abrupt. The connection between the residual correlation and the ensemble's performance could be explained more intuitively.
  - **Required correction** Add a sentence or two explaining why a high residual correlation with opposite signs for a fraction of variants leads to error cancellation, and what the practical implications are for model ensembling.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of confidence intervals for primary accuracy metrics.
  - R1-M2: Potential overstatement of the scope of the theoretical transitivity guarantee.
- **Assessment against Nature-style criteria**
  - **Originality** The idea of reformulating an existing predictor as a potential difference to enforce thermodynamic consistency is novel and elegant. The theoretical analysis of the ReLU head is a distinct contribution. This is not a simple application of existing methods.
  - **Scientific importance** The problem of physical consistency in learned predictors is important for the field of protein stability prediction. The work provides a clear framework for addressing this, and the separation of consistency from accuracy is a valuable conceptual contribution. The practical impact is currently limited by the modest accuracy gains and the narrow scope of the exact guarantee.
  - **Interdisciplinary readership** The work is relevant to computational biologists, biophysicists, and machine learning researchers. The main text is generally accessible, but the Methods section is highly technical. The potential for broader interest is moderate.
  - **Technical soundness** The theoretical derivations appear sound. The empirical evaluation is reasonable but has limitations in statistical rigor (see R1-M1). The use of fixed, equal-weight averaging is well-justified.
  - **Readability for nonspecialists** The abstract and introduction are clear. The Results section is dense but understandable. The Methods section is for specialists. The distinction between the two benefits (accuracy vs. consistency) is well-communicated.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the theoretical analysis is a strength. However, the strength of the empirical claims needs to be backed by proper uncertainty quantification, and the scope of the theoretical guarantee needs to be stated more carefully. Once these are addressed, the manuscript would be a solid contribution.

## Risk / unsupported claims
- The claim that the ensemble "outperforms" both components on S669 and S96 is not fully supported without confidence intervals or significance testing.
- The claim of "exact same-site transitivity" is technically correct but could be misinterpreted as applying more broadly; the manuscript should be more explicit about its limited scope.
- The statement that the ensemble "matching the EvoPhi-DDG extension at the reported precision" on PTmul-NR is based on a very small benchmark and should be interpreted with caution.
- The manuscript states that the ensemble "reduces multisite pathway-closure RMSE relative to JanusDDG across all evaluated path lengths." While this is reported, the practical significance of a reduction from, e.g., 0.16 to 0.10 kcal/mol is not discussed. Is this level of error acceptable for practical applications?