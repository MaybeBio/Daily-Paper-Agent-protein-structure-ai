## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Methodological claims, validation scope, and applicability as stated in the abstract
- **Shared manuscript claim summary** The authors present a method for determining dynamic domains in proteins from either a pair of conformations or an ensemble, using metric multi-dimensional scaling (MDS) applied to distance-differences or root-mean-square fluctuations of inter-atomic distances (RMSFIDs). The method produces a low-dimensional point representation of residues, enabling top-down clustering. Two implementations, Pair-DD and Ensemble-DD, are demonstrated on idealized rigid-body examples, X-ray-derived conformational pairs and ensembles (monomeric and multimeric), and simulation trajectories. A threshold parameter is proposed for automatic domain assignment. The method is claimed to show excellent correspondence with an established approach and to offer versatility across both input types, with a one-dimensional MDS coordinate sufficient for pairs.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or quantitative results provided
- **Missing materials affecting confidence** Full methods, algorithmic details, validation datasets, comparison metrics, parameter definitions, and all figures or tables

## Reviewer
- **Overall assessment** The abstract describes a conceptually interesting and potentially useful methodological contribution to protein dynamics analysis. The core idea of applying MDS to distance-based metrics for domain identification is plausible and aligns with existing structural biology needs. However, the abstract provides insufficient detail to evaluate the technical soundness, the robustness of the validation, or the claimed superiority over existing methods. The evidence base is too limited to establish the case from the supplied material.
- **Who would be interested in the results, and why** Structural biologists, computational biochemists, and researchers studying protein conformational changes, allostery, or dynamics. The method could be useful for analyzing molecular dynamics simulations, comparing X-ray structures, and understanding functional motions. The potential for automatic domain assignment would appeal to those seeking high-throughput analysis tools.
- **Major strengths** The method addresses a real need in the field, namely a unified approach for both pairwise and ensemble-based domain determination. The use of MDS to create a point-based representation is elegant and could simplify clustering. The proposed threshold parameter for automatic assignment is a practical addition. The demonstration across idealized, experimental, and simulation-derived data suggests broad applicability.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  - Originality: The approach is novel in its specific combination of MDS with distance-difference or RMSFID metrics for domain identification, though the underlying concepts are not entirely new.  
  - Scientific importance: Potentially high for the structural biology community, but the abstract does not demonstrate a significant advance over existing methods beyond versatility.  
  - Interdisciplinary readership: Likely limited to specialists in computational structural biology; the abstract does not make a case for broader appeal.  
  - Technical soundness: Cannot be assessed from the abstract alone; key algorithmic and validation details are missing.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses field-specific jargon (e.g., RMSFIDs, MDS) without sufficient context for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract lacks the detail needed to assess validity, robustness, and comparative performance. A full manuscript with methods and results would be required for a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The method "applies metric multi-dimensional scaling (MDS) to distance-differences or root-mean-square-fluctuations of inter-atomic distances (RMSFIDs)" and "determines points in a low-dimensional space" for domain identification.  
- **Evidence pointer** Abstract, methods description; location not provided  
- **Concern** The abstract does not specify how MDS is configured, what distance metric is used, how the number of dimensions is chosen, or how the clustering is performed. Without these details, the technical validity of the approach cannot be evaluated.  
- **Why it matters** The core claim rests on the correctness and appropriateness of the MDS application. If the configuration is flawed, the resulting domain assignments could be artifacts.  
- **Resolution test** Provide a detailed methods section including the MDS algorithm, distance metric, dimensionality selection criteria, and clustering procedure, with a worked example.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation robustness  
- **Claim pointer** The method "show[s] excellent correspondence with a well-established approach" and is demonstrated on "idealized examples," "X-ray structures both monomeric and multimeric," and "trajectories derived from simulation methods."  
- **Evidence pointer** Abstract, validation section; location not provided  
- **Concern** The abstract provides no quantitative results, no comparison metrics, and no details on the datasets used. The claim of "excellent correspondence" is unsupported without specific correlation coefficients, error measures, or statistical tests.  
- **Why it matters** Without quantitative validation, the reader cannot judge whether the method is accurate, reliable, or superior to existing tools.  
- **Resolution test** Include figures or tables showing quantitative comparisons (e.g., domain overlap, boundary accuracy) against established methods on multiple datasets, with error bars or statistical significance.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Parameter justification  
- **Claim pointer** "A parameter is proposed which can be used as a threshold for acceptance of dynamic domains to enable automatic assignment."  
- **Evidence pointer** Abstract, parameter description; location not provided  
- **Concern** The abstract does not define the parameter, its range, or how it is calibrated. It is unclear whether the threshold is universal or dataset-specific, and how sensitive the results are to its choice.  
- **Why it matters** Automatic assignment is a key claimed advantage. If the threshold is arbitrary or poorly justified, the method's practical utility is compromised.  
- **Resolution test** Define the parameter mathematically, provide a sensitivity analysis, and demonstrate its performance across diverse datasets with a recommended default value.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Comparative advantage  
- **Claim pointer** The method "has the added advantage of being versatile in that it is applicable to both a pair of structures and an ensemble of conformations."  
- **Evidence pointer** Abstract, discussion; location not provided  
- **Concern** The abstract claims versatility as an advantage but does not compare the method's performance or computational cost against existing approaches that may already handle both cases, nor does it discuss limitations.  
- **Why it matters** The claim of advantage is only meaningful if the method is at least as accurate and efficient as alternatives. Without comparison, the added value is unclear.  
- **Resolution test** Provide a benchmark comparing Pair-DD and Ensemble-DD against established methods on the same datasets, including runtime and accuracy metrics.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, terminology  
- **Evidence pointer** Abstract, first sentence; location not provided  
- **Issue** The term "dynamic domains" is not defined. It is unclear whether this refers to rigid-body-like regions or regions of correlated motion.  
- **Required correction** Define "dynamic domains" explicitly in the abstract or introduction.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Abstract, implementation details  
- **Evidence pointer** Abstract, implementations section; location not provided  
- **Issue** The abstract mentions "Pair-DD" and "Ensemble-DD" but does not state whether the code is publicly available or how to access it.  
- **Required correction** State software availability (e.g., open-source repository, license) in the abstract or a data availability statement.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract, visualization claim  
- **Evidence pointer** Abstract, final sentence; location not provided  
- **Issue** The claim that "a one-dimensional MDS coordinate seems to be sufficient" is vague. It is unclear what "sufficient" means in terms of accuracy or interpretability.  
- **Required correction** Clarify the criterion for sufficiency, such as a quantitative measure of domain assignment accuracy or a comparison with higher-dimensional solutions.

## Risk / unsupported claims
- The claim of "excellent correspondence with a well-established approach" is unsupported without quantitative data.
- The claim that a one-dimensional MDS coordinate is "sufficient" for pairs is unsupported without a defined criterion.
- The proposed threshold parameter for automatic assignment is undefined and its effectiveness is not demonstrated.
- The versatility advantage over existing methods is asserted but not substantiated by comparative benchmarks.
- The applicability to "general conformational ensembles" is stated but not validated for diverse ensemble types (e.g., non-Gaussian, highly flexible systems).