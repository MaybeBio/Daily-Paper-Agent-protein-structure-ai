## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present CDSM, a collagen-specific deterministic structure modeler built on the THeBuScr empirical geometric parameterization, and claim that it achieves high coverage and competitive accuracy on a benchmark of 80 collagen triple-helical structures when compared against AlphaFold 3, Boltz-2, Chai-1, and Protenix-v1, at substantially lower computational cost.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full methods, benchmark construction details, training-data cutoff definitions, per-method configuration and cost calculations, statistical analyses, and all supporting figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting and practically valuable contribution to protein structure prediction for a constrained structural class. The central idea, that explicit encoding of geometric constraints can yield a compact and highly efficient predictor for collagen, is conceptually appealing and aligns with ongoing discussions about complementing large learned models with mechanistic or rule-based approaches. However, the evidence as presented in the abstract is insufficient to fully evaluate the robustness of the claims. Key details regarding benchmark construction, evaluation protocols, cost calculations, and statistical significance are missing. The reported performance comparisons, particularly the win-rate analyses on post-cutoff structures, are intriguing but require careful scrutiny of how cutoffs were defined and applied. The computational cost advantage is striking but needs verification of the cost model. Overall, the work appears promising and likely of interest to the structural biology and protein design communities, but the current abstract alone does not establish the case with sufficient rigor.
- **Who would be interested in the results, and why** Structural biologists studying collagen and other fibrous proteins, computational biologists developing structure prediction methods, researchers interested in hybrid approaches combining empirical knowledge with machine learning, and developers of lightweight prediction tools for high-throughput or resource-constrained applications. The cost and speed advantages could also appeal to industrial users and those performing large-scale screening.
- **Major strengths** The conceptual framing is clear and compelling, positioning the work within a broader discussion of model complexity versus structural constraints. The reported coverage improvement from 8.8% to 93.8% is substantial and suggests a meaningful methodological advance. The inclusion of post-training-cutoff evaluation is a thoughtful attempt to address generalization concerns. The computational cost advantage, if accurately reported, is remarkable and practically significant.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to high, as the idea of encoding empirical geometric constraints into a deterministic modeler for a specific protein class is not entirely new but the specific application and systematic benchmarking appear novel. Scientific importance is potentially high for the collagen community and for the broader discussion of efficient structure prediction, though the generalizability beyond collagen remains speculative. Interdisciplinary readership is plausible, spanning structural biology, computational biology, and machine learning. Technical soundness cannot be fully assessed from the abstract alone, as critical methodological details are missing. Readability for nonspecialists is good, with clear motivation and accessible language, though some technical terms such as THeBuScr and training-data cutoff may require additional context.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the reported results are intriguing, but the evidence base provided is insufficient to fully establish the claims. A complete manuscript with detailed methods, benchmark descriptions, and statistical analyses would be needed to assess technical soundness.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark construction and evaluation protocol
- **Claim pointer** The claim that CDSM was benchmarked against AlphaFold 3, Boltz-2, Chai-1, and Protenix-v1 on 80 experimentally resolved collagen triple-helical structures, with coverage increasing from 8.8% to 93.8%.
- **Evidence pointer** Abstract, benchmark description; location not provided
- **Concern** The abstract does not describe how the 80 benchmark structures were selected, how the coverage metric was defined, or how the 75 structures successfully predicted by all methods were determined. The criteria for successful prediction, the handling of partial predictions, and the potential for selection bias in the benchmark are not addressed.
- **Why it matters** Without a clear and unbiased benchmark construction, the reported coverage and accuracy comparisons may not be representative or reproducible. Selection bias in benchmark structures could inflate or deflate the apparent performance of any method.
- **Resolution test** Provide a detailed description of benchmark construction, including structure selection criteria, redundancy removal, resolution thresholds, and the definition of successful prediction. Report coverage metrics with clear denominators and describe how partial predictions were handled.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalization evaluation and training-data cutoff definition
- **Claim pointer** The claim that when evaluated only on structures deposited after each learned model's training-data cutoff, CDSM becomes more competitive, with aggregate win rates increasing from 29% to 55% for TM-score and from 40% to 65% for backbone RMSD.
- **Evidence pointer** Abstract, post-cutoff evaluation; location not provided
- **Concern** The abstract does not specify how training-data cutoffs were determined for each learned model, how the post-cutoff subset was defined, or how many structures fell into this subset. The statistical significance of the win-rate differences is not reported, and the stability of CDSM performance across subsets is stated without supporting data.
- **Why it matters** The post-cutoff analysis is central to the claim that CDSM generalizes better to novel structures. If the subset is small or the cutoff definitions are inconsistent, the win-rate comparisons may be statistically underpowered or biased.
- **Resolution test** Report the number of post-cutoff structures for each model, the exact cutoff dates used, and confidence intervals or significance tests for the win-rate comparisons. Provide per-structure performance data to allow independent verification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational cost comparison methodology
- **Claim pointer** The claim that CDSM generates structures in 2.4 s on a single CPU core at approximately $3 × 10 −5 per structure, making it 400 to 790× cheaper than the learned methods even when each is run on its lowest-cost compatible GPU.
- **Evidence pointer** Abstract, cost comparison; location not provided
- **Concern** The abstract does not describe how the cost per structure was calculated for each method, including hardware assumptions, cloud pricing models, amortization of model training costs, or whether inference-only costs were considered. The range of 400 to 790× suggests variability across methods, but the basis for this range is not explained.
- **Why it matters** The cost advantage is a major selling point of the work. If the cost model is incomplete or inconsistent across methods, the claimed advantage may be overstated or misleading.
- **Resolution test** Provide a detailed cost model for each method, including hardware specifications, pricing sources, inference time measurements, and whether training or development costs were included. Justify the range of cost ratios reported.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Accuracy metrics and statistical rigor
- **Claim pointer** The claim that CDSM closely reproduces experimental backbone and global geometry, with fewer large-error predictions, while the learned models achieve modestly higher local and side-chain accuracy.
- **Evidence pointer** Abstract, accuracy comparison; location not provided
- **Concern** The abstract reports qualitative differences in accuracy without providing quantitative metrics, error distributions, or statistical tests. The terms "closely reproduces," "fewer large-error predictions," and "modestly higher" are vague and do not allow assessment of the magnitude or significance of the differences.
- **Why it matters** The relative accuracy of CDSM versus learned models is a central claim. Without quantitative metrics and statistical analysis, the reader cannot determine whether the differences are meaningful or within noise.
- **Resolution test** Report specific metrics for backbone RMSD, TM-score, and side-chain accuracy for all methods, with error bars or confidence intervals. Provide error distributions and statistical tests for pairwise comparisons.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology clarity
- **Affected element** THeBuScr reference
- **Evidence pointer** Abstract, first paragraph; location not provided
- **Issue** The abstract references THeBuScr as the basis for the empirical geometric parameterization but does not provide a citation or brief description of what THeBuScr is, which may confuse readers unfamiliar with this tool.
- **Required correction** Add a citation for THeBuScr and a one-sentence description of its role in the parameterization.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scope of generalizability claim
- **Affected element** Final sentence on broader applicability
- **Evidence pointer** Abstract, final sentence; location not provided
- **Issue** The claim that the approach "motivates future AI-driven searches over algorithms, representations, and empirical parameterizations" for other structural protein domains is speculative and not supported by evidence in the abstract.
- **Required correction** Soften the language to indicate this is a future direction or hypothesis rather than a demonstrated outcome.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility of cost figure
- **Affected element** Cost per structure figure
- **Evidence pointer** Abstract, cost comparison; location not provided
- **Issue** The cost figure of approximately $3 × 10 −5 per structure is presented without context on how this was derived or whether it includes any overhead.
- **Required correction** Provide a brief note on the assumptions underlying this figure, such as cloud instance type and utilization assumptions.

## Risk / unsupported claims
- The claim that CDSM "closely reproduces experimental backbone and global geometry" is unsupported without quantitative metrics.
- The claim that CDSM becomes "more competitive" on post-cutoff structures is unsupported without details on subset size and statistical significance.
- The claim that the approach "motivates future AI-driven searches" for other domains is speculative and not supported by evidence in the abstract.
- The generalizability of the approach beyond collagen is not demonstrated and should not be implied.
- The cost advantage range of 400 to 790× is not verifiable without a detailed cost model.