## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, without access to full methods, data, or figures
- **Shared manuscript claim summary** The authors benchmark molecular docking tools across three paradigms (physics-based, hybrid rescoring, co-folding) and report that co-folding methods perform well on training-like targets but degrade to 20-40% success on novel dissimilar systems, while physics-based and hybrid methods maintain >60% success on out-of-distribution targets, suggesting memorization in co-folding and complementarity between AI and physics-based approaches.
- **Visible evidence base** Abstract text only; no figures, tables, or methodological details provided
- **Missing materials affecting confidence** Full methods, dataset composition, target and ligand selection criteria, similarity metrics, success rate definitions, statistical analyses, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a timely and potentially important comparative benchmark of docking paradigms, with a clear and provocative central claim regarding memorization in co-folding models. However, the abstract alone provides insufficient detail to evaluate the rigor of the benchmark design, the validity of the similarity metrics, or the statistical robustness of the reported success rates. The conclusions are plausible but not fully established from the supplied material.
- **Who would be interested in the results, and why** Computational chemists, medicinal chemists, and developers of deep learning-based drug discovery tools would be interested. The results directly address the practical question of when AI-based docking can be trusted for novel targets, which is central to the adoption of these methods in industrial and academic screening pipelines.
- **Major strengths** The study addresses a critical and current question in the field, namely the generalizability of co-folding models beyond training distributions. The comparison across three paradigms is well motivated and the reported contrast in performance is striking and potentially actionable. The framing around memorization versus physical sampling is conceptually clear and likely to stimulate further work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate to high, as the comparative angle across paradigms is not entirely new but the specific focus on memorization versus robustness is valuable. Scientific importance is high given the rapid adoption of co-folding methods. Interdisciplinary readership is plausible, spanning machine learning and structural biology. Technical soundness cannot be fully assessed from the abstract alone, and the lack of methodological detail is a concern. Readability for nonspecialists is adequate, though terms such as "co-folding" and "hybrid rescoring" would benefit from brief definition.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The claim that co-folding approaches "deteriorate sharply to unacceptably low 20-40% success rates on novel dissimilar systems" is central to the paper's thesis.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not define how "novel dissimilar systems" are identified or quantified. Without a clear and objective measure of dissimilarity between test targets and training data, the claim of memorization cannot be distinguished from legitimate generalization failure due to genuinely harder targets.
- **Why it matters** The central conclusion hinges on the interpretation that poor performance on dissimilar systems is due to memorization rather than other factors such as target difficulty, ligand complexity, or scoring function limitations. If the dissimilarity metric is not robust or is confounded with other variables, the conclusion is not supported.
- **Resolution test** Provide a detailed description of the dissimilarity metric, including how it is computed (e.g., sequence identity, structural similarity, ligand property distributions), and demonstrate that the "dissimilar" test set is not systematically harder for reasons unrelated to training distribution shift.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The reported success rates (20-40% for co-folding, >60% for physics-based and hybrid) are presented as definitive comparative results.
- **Evidence pointer** Abstract only; location not provided
- **Concern** No confidence intervals, sample sizes, or statistical tests are reported. The abstract does not indicate how many targets and ligands were used, whether the differences between paradigms are statistically significant, or whether the results are robust to the choice of test set.
- **Why it matters** Without statistical context, the reported percentages could be within noise, especially if the test set is small. The strength of the comparative claim requires evidence that the observed differences are not due to chance.
- **Resolution test** Report the number of test systems, per-paradigm success rates with confidence intervals, and appropriate statistical comparisons (e.g., paired tests across the same targets). Show that the differences are significant and consistent across multiple random splits if applicable.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The benchmark covers "several molecular docking tools representing these paradigms," but the specific tools and their versions are not named in the abstract.
- **Evidence pointer** Abstract only; location not provided
- **Concern** Without naming the exact tools, versions, and any parameter settings, the benchmark cannot be reproduced or compared to other studies. The choice of tools may also bias the results, as some co-folding models may be more or less prone to memorization.
- **Why it matters** Reproducibility is a core requirement for a benchmark study. If the tool set is not fully specified, the results cannot be independently verified, and the generalizability of the conclusions to other tools in each paradigm is unclear.
- **Resolution test** List all tools, versions, and key hyperparameters in the full manuscript. Justify the selection of tools as representative of each paradigm and discuss potential limitations of the chosen set.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The terms "co-folding," "hybrid rescoring," and "physics-based" are used without definition, which may confuse nonspecialist readers.
- **Required correction** Provide brief definitions or examples of each paradigm in the abstract or introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Related work
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract cites Runs-n-Poses but does not clearly state how this benchmark differs from or extends that work.
- **Required correction** Explicitly state the novel contribution relative to Runs-n-Poses, such as the inclusion of hybrid models or a different dissimilarity metric.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Conclusion
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "argue for the benefits of tighter integration" is vague and does not specify what form such integration might take.
- **Required correction** Provide a concrete example or direction for integration, such as using physics-based scoring as a post-filter for co-folding outputs.

## Risk / unsupported claims
- The claim that co-folding performance decline is "consistent with memorization" is not supported by the abstract alone, as no direct evidence of memorization (e.g., training set overlap analysis) is presented.
- The claim that physics-based and hybrid methods show "greater out-of-distribution robustness" is not supported without details on the distribution shift and the comparability of test sets across paradigms.
- The generalizability of the findings to all tools within each paradigm is not assessable from the abstract, as the specific tools are not named.