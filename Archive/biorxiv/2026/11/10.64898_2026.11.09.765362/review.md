## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary information)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the supplied text
- **Shared manuscript claim summary** The authors propose PULSE, a context-aware activation steering method for protein sequence optimization that constructs steering vectors from similarity-matched positive-negative protein pairs rather than global population contrasts. They report improved optimization outcomes across solubility, immunogenicity, and toxicity, and introduce Local Directional Support (LDS) as a trajectory-level reliability metric enabling predictor-free candidate prioritization.
- **Visible evidence base** Main text figures (Figs. 2–7), Table 1, Table 2, Supplementary Tables 3–5, Appendix A–C
- **Missing materials affecting confidence** Figure images not provided; exact numerical values for many reported results not given in text; full algorithm pseudocode not provided; dataset composition details partially described; code repository not inspected

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in controllable protein sequence generation and proposes a conceptually interesting alternative to global steering vector construction. The motivation for context-aware steering is well articulated and supported by the background-dependence analysis. However, the evidence as presented has several gaps that prevent full assessment of the method's validity and generalizability. The reliance on predictor-based outcomes without experimental validation, the limited model scope, and the absence of key methodological details (e.g., exact hyperparameter values, computational costs, sensitivity analyses) temper enthusiasm. The LDS metric is a useful conceptual contribution, but its practical utility requires stronger validation.
- **Who would be interested in the results, and why** Researchers in protein engineering, computational protein design, and machine learning for biology would be interested. The work speaks to those developing controllable generation methods for protein language models and those seeking reliability metrics for iterative sequence optimization. The predictor-free prioritization aspect may appeal to experimental groups with limited screening capacity.
- **Major strengths** The core idea of moving from global to local, context-dependent steering is well motivated and timely. The pairing strategy using representation similarity is methodologically clean. The introduction of LDS as a trajectory-level diagnostic addresses a genuine gap in evaluating iterative optimization. The evaluation across three distinct protein properties provides breadth. The authors are transparent about limitations, including the lack of experimental validation.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (predictor dependence), R1-M2 (limited model scope), R1-M3 (missing methodological details), R1-M4 (LDS validation gap)
- **Assessment against Nature-style criteria** Originality: The paired-unit steering concept is a meaningful departure from existing global contrast methods, and LDS is a novel diagnostic. Scientific importance: The problem of context-aware steering is significant for the field, but the current evidence does not yet establish broad impact. Interdisciplinary readership: The work bridges machine learning and protein engineering, but the presentation assumes familiarity with both fields without sufficient scaffolding. Technical soundness: The core methodology is reasonable, but several implementation details and validation choices weaken the current case. Readability for nonspecialists: The abstract and introduction are accessible, but the methods section is dense and would benefit from clearer exposition of the mathematical notation.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, but the current evidence base is insufficient to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "PULSE consistently outperforms global population-centroid steering in both final predicted property scores and optimization success rates" (Abstract; Section 3.2)
- **Evidence pointer** Section 3.2, Fig. 2, Table 2
- **Concern** All performance claims rest on predictor-based outcomes. The predictors used for solubility, immunogenicity, and toxicity are themselves models with unknown accuracy for the specific target proteins tested. Without experimental validation or at least a demonstration that predictor scores correlate with known experimental measurements for a held-out set, the reported improvements may reflect artifacts of the predictors rather than genuine property improvements.
- **Why it matters** The central claim of the paper is that PULSE produces better protein optimizations. If the evaluation oracle is unreliable, the claim is not established. The authors acknowledge this limitation in Section 4.2, but the acknowledgment does not mitigate the evidentiary gap.
- **Resolution test** Provide experimental validation on a small set of designed proteins, or demonstrate that the predictors used have been benchmarked against experimental data for the relevant property and sequence space, with quantified accuracy.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "PULSE consistently outperforms global population-centroid steering" (Abstract; Section 3.2)
- **Evidence pointer** Section 3.1, Section 4.2
- **Concern** All experiments use a single model backbone (ESMC-600M). The authors acknowledge this in Section 4.2, but the claim of consistent outperformance is only demonstrated for one architecture. It is unknown whether the paired-unit steering advantage persists with other protein language models of different sizes or architectures.
- **Why it matters** The method's utility depends on its generalizability across the diverse landscape of protein language models. A single-backbone evaluation is insufficient to support the strength of the stated claim.
- **Resolution test** Repeat key experiments with at least one additional model backbone (e.g., ESM-2 of comparable size, or a smaller model) and report whether the performance advantage holds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "PULSE adpots the same site selection and decoding as ASPO; only the construction of v(l) differs" (Section 2.1)
- **Evidence pointer** Section 2.1, Section 2.2, Appendix C
- **Concern** Several methodological details required for reproduction are missing or incompletely specified. The exact values of α (steering intensity) are said to be in Table 5, but the table is not provided in the supplied text. The site selection procedure references a ranking and masking step, but the precise criterion (e.g., lowest-scoring by what measure) is not fully defined. The decoding procedure is described in words but not with sufficient mathematical precision to implement without guessing.
- **Why it matters** Reproducibility is a core requirement for scientific claims. Without complete methodological specification, independent verification is impossible.
- **Resolution test** Provide complete pseudocode for the optimization loop, exact hyperparameter values in the main text or a fully specified appendix, and clarify the site selection and decoding equations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual validation
- **Claim pointer** "LDS captures differences in trajectory reliability and enables predictor-free candidate prioritization" (Abstract; Section 3.6)
- **Evidence pointer** Section 3.5, Section 3.6, Fig. 5, Fig. 6
- **Concern** The claim that LDS enables predictor-free prioritization is supported by AUROC comparisons, but the analysis does not establish that LDS provides information beyond what could be obtained from simpler metrics (e.g., final property score change, or trajectory length). No comparison against alternative prioritization strategies is provided.
- **Why it matters** The practical value of LDS depends on its incremental utility over existing or simpler approaches. Without such comparison, the contribution of LDS as a prioritization tool is unclear.
- **Resolution test** Compare LDS-based ranking against ranking by final predicted score, by total trajectory displacement, or by random selection, and report AUROC and enrichment for each.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, pairing procedure
- **Evidence pointer** Section 2.2
- **Issue** The description of the Hungarian algorithm application states that K = min(N+, N−) disjoint pairs are obtained, but it is unclear how ties in similarity are broken and whether the matching is performed once on the full dataset or per target.
- **Required correction** Clarify the matching procedure, including tie-breaking and whether matching is global or target-specific.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.2, Table 2
- **Evidence pointer** Section 3.2, Table 2
- **Issue** The text states that paired comparisons were statistically significant after multiple-testing correction, but effect sizes and confidence intervals are not reported in the main text.
- **Required correction** Report effect sizes and confidence intervals for the paired differences alongside p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Notation consistency
- **Affected element** Section 2.1, Section 2.2
- **Evidence pointer** Section 2.1, Section 2.2
- **Issue** The notation for representations is introduced as h(l)x for the representation of residue r at layer l, but the subscript r is not defined in the text. The mean over residues is denoted h̄(l)x, but the averaging operation is not explicitly stated.
- **Required correction** Define all notation explicitly, including the residue index and the averaging operation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Computational cost
- **Affected element** Section 2.2, Hungarian algorithm
- **Evidence pointer** Section 2.2
- **Issue** The computational cost of the Hungarian algorithm for large datasets is not discussed. For protein datasets with tens of thousands of sequences, this could be a practical bottleneck.
- **Required correction** Report the computational time for the pairing step and discuss scalability.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Robustness
- **Affected element** Section 3.5, Fig. 5
- **Evidence pointer** Section 3.5
- **Issue** The sensitivity analysis uses 10 independently sampled reference pools, but the variance across these pools is not reported beyond the claim that the advantage was robust.
- **Required correction** Report the distribution of LDS differences across reference pools (e.g., mean and standard deviation).

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.3, Table 1
- **Evidence pointer** Section 3.3, Table 1
- **Issue** The Spearman correlations are reported, but the corresponding scatter plots or binned summaries are only referenced in supplementary material.
- **Required correction** Include representative scatter plots in the main text or supplementary for visual inspection.

## Risk / unsupported claims
- The claim that PULSE "consistently outperforms" global steering is not fully supported given the single model backbone and predictor-based evaluation.
- The claim that LDS "enables predictor-free candidate prioritization" is not supported by comparison against alternative prioritization methods.
- The claim that "property-improving directions vary across different protein sequence backgrounds" is supported by correlational evidence, but the causal interpretation is not established.
- The statement that PULSE's advantage is due to "retaining pair-specific information prior to aggregation" is a plausible interpretation but not directly tested (e.g., via ablation of the weighting scheme).
- The generalizability of findings to other protein properties beyond the three tested is not established.
- The practical utility of the method for experimental workflows is asserted but not demonstrated with wet-lab data.