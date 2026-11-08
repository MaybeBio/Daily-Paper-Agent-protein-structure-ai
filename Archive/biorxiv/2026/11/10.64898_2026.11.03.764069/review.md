## Review setup
- **Input scope** Full manuscript text, including summary, introduction, results, discussion, resource availability, and STAR methods.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence. Not assessed: code functionality, GUI usability, or reproducibility of software installation.
- **Shared manuscript claim summary** The authors present cryoID2, a deep learning-enhanced pipeline for identifying proteins and RNA from cryoEM maps. The method integrates three 3D U-Nets for feature prediction, sequence-based candidate ranking, and structural evaluation. Claims include high-recall feature prediction, resolution-dependent atom clustering, near-reference fitting quality in a 52-case benchmark, and successful end-to-end identification of PfA-M17 from a 166-protein mass-spectrometry pool and Ca-raiA RNA from a genome-derived non-coding sequence set.
- **Visible evidence base** Main text figures (Figs 1–6), supplementary figures (Supplementary Figs 1–2), supplementary tables (Supplementary Tables 1–4), and method descriptions in STAR Methods.
- **Missing materials affecting confidence** The manuscript does not provide quantitative results for the 52-case benchmark beyond mean and median Q-score differences. No per-case Q-score values are shown in the main text. The RNA proof-of-concept relies on a single case. No comparison against existing tools (e.g., ModelAngelo, DeepTracer, cryoID1) is provided. The training dataset composition and quality-control criteria are only summarized in a supplementary table without detailed statistics. The manuscript does not report runtime or computational cost. The claim of "high-recall feature prediction" is not supported by quantitative recall values in the main text.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful extension of the cryoID approach, integrating deep learning-based feature prediction with sequence and structural ranking for both protein and RNA identification. The modular benchmarking strategy is thoughtful, and the two end-to-end cases are illustrative. However, the evidence presented is insufficient to establish the method's general utility or superiority over existing approaches. Key quantitative results are missing or underreported, and the single-case RNA demonstration limits confidence in the RNA branch. The manuscript would benefit from more rigorous benchmarking, including comparisons to existing tools and a more detailed analysis of failure cases.
- **Who would be interested in the results, and why** Structural biologists using cryoEM/cryoET to characterize endogenous complexes or poorly characterized samples would be the primary audience. Researchers developing computational tools for cryoEM map interpretation would also be interested in the methodological contributions, particularly the integration of sequence and structural evidence. The RNA identification component may appeal to the growing cryoET community studying native RNA-protein assemblies.
- **Major strengths** The modular design of the pipeline is clear and logical, separating feature prediction, sequence ranking, and structural evaluation. The use of reduced amino acid and nucleotide alphabets is a sensible strategy for tolerating prediction uncertainty. The inclusion of a structural evaluation stage after sequence ranking is a valuable addition that can discriminate among closely related candidates. The authors are appropriately cautious in distinguishing their method from de novo model building and in acknowledging the need for direct comparisons.
- **Major Concerns** The quantitative evidence for the 52-case benchmark is thin. Only mean and median Q-score differences are reported, without per-case distributions, failure analysis, or comparison to a baseline. The RNA proof-of-concept is a single case with a heavily constrained candidate pool, limiting its generalizability. The claim of "high-recall feature prediction" is not substantiated with numbers in the main text. No comparison to existing tools (e.g., ModelAngelo, DeepTracer, cryoID1) is provided, making it difficult to assess the method's added value. The structural evaluation stage is limited to rigid-body fitting, which may not be adequate for cases with conformational differences.
- **Minor Comments** The manuscript would benefit from a more detailed description of the U-Net training data, including the distribution of resolutions and molecular weights. The choice of the 50% threshold for RNA candidate selection in the proof-of-concept is not justified. The description of the maximin scoring method could be clearer. The authors should clarify whether the 52-case benchmark includes any RNA cases. The discussion of limitations is honest but could be expanded with a more explicit statement of what the method cannot do.
- **Technical failings that need to be addressed before the case is established** The lack of quantitative feature prediction metrics in the main text. The absence of per-case results or failure analysis for the 52-case benchmark. The lack of comparison to existing methods. The single-case RNA demonstration with a length-constrained candidate pool.
- **Assessment against Nature-style criteria** Originality: Moderate. The integration of deep learning feature prediction with sequence and structural ranking is a reasonable extension of prior work, but the individual components are not novel. Scientific importance: Moderate. The problem of molecular identification in cryoEM maps is important, but the evidence does not yet demonstrate a major advance over existing tools. Interdisciplinary readership: Limited. The manuscript is primarily of interest to cryoEM method developers and practitioners. Technical soundness: The modular benchmarking is sound in principle, but the reporting is incomplete. The lack of comparisons and quantitative details weakens the technical case. Readability for nonspecialists: The manuscript is generally well written and accessible, though some method details are dense.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a plausible and potentially useful method, but the evidence presented is insufficient to support the claims of high-recall feature prediction, near-reference fitting quality, and successful end-to-end identification. Substantial additional benchmarking and reporting are needed.

### Major Concerns
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "a 52-case benchmark recovers near-reference fitting quality"
- **Evidence pointer** Figure 3d, Supplementary Tables 1–2
- **Concern** The 52-case benchmark is summarized only by mean and median Q-score differences. No per-case results, distribution plots, or failure analysis are provided. The claim of "near-reference fitting quality" is based on a mean difference of −0.0346 and a median difference of −0.0001, but the reader cannot assess how many cases had large Q-score losses or whether these correlate with resolution, molecular weight, or other factors.
- **Why it matters** Without per-case data, the reader cannot evaluate the robustness of the method or identify conditions under which it fails. The mean difference is dominated by a small number of failures, but the manuscript does not characterize these failures. This limits the ability to assess whether the method is suitable for general use.
- **Resolution test** Provide per-case Q-score differences, a histogram or scatter plot of Q-score differences versus map resolution, and a discussion of cases with large Q-score losses. If possible, compare the fitted Q-scores to those obtained by a simple baseline (e.g., fitting the deposited model without sequence ranking).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** "CryoID2 addresses this by integrating deep learning-based feature prediction with sequence prioritization and structural evaluation"
- **Evidence pointer** Discussion, Introduction
- **Concern** The manuscript does not compare cryoID2 to existing tools for molecular identification or model building, such as ModelAngelo, DeepTracer, or the original cryoID. The authors acknowledge this in the Discussion ("Direct comparisons under matched candidate-pool and map conditions would be needed"), but the absence of any comparative data makes it impossible to assess whether cryoID2 offers a meaningful improvement.
- **Why it matters** The field already has several automated tools for map interpretation. Without a direct comparison, the reader cannot determine whether cryoID2 is a significant advance or a marginal improvement. The claim of "addressing" the bottleneck implies a solution that is at least competitive with existing approaches.
- **Resolution test** Run cryoID2 and at least one existing tool (e.g., ModelAngelo or cryoID1) on the same set of benchmark maps and candidate pools, and report identification accuracy, runtime, and Q-scores. If a direct comparison is not feasible, clearly state the limitations and provide a qualitative comparison of features and expected performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of RNA branch
- **Claim pointer** "the unannotated Ca-raiA RNA from a genome-derived non-coding sequence set, demonstrating a unified sequence-plus-structure route to molecular identification in cryoEM maps"
- **Evidence pointer** Figure 6, Methods
- **Concern** The RNA proof-of-concept is a single case. The candidate pool was constructed by excluding annotated CDS regions and further constrained by the known 204-nucleotide reference length (±50%). This is a substantial prior constraint that may not be available in a real discovery scenario. The manuscript does not report how the method would perform without this length constraint or on a more diverse set of RNA structures.
- **Why it matters** The RNA branch is a key novelty of cryoID2. A single case with a heavily constrained candidate pool does not establish that the method can identify RNA in general. The length constraint, in particular, may be unrealistic for many applications.
- **Resolution test** Test the RNA branch on additional RNA cryoEM maps with different lengths, structures, and candidate pool compositions. Report performance with and without the length constraint. If additional cases are not available, clearly state this limitation and temper the claim of a "unified" route.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative feature prediction metrics
- **Claim pointer** "Module-level tests show high-recall feature prediction"
- **Evidence pointer** Figure 3a–c, Methods
- **Concern** The claim of "high-recall feature prediction" is not supported by quantitative metrics in the main text. The manuscript reports voxel-wise accuracy, precision, recall, and F1 scores for the three U-Net models, but the values are only described qualitatively. The reader cannot assess whether the recall is genuinely high or whether the precision is acceptable.
- **Why it matters** Feature prediction is the foundation of the entire pipeline. If the U-Net models have low precision, the downstream steps may be overwhelmed by false positives. The manuscript should report the actual numbers and discuss the trade-off between precision and recall.
- **Resolution test** Report the numerical values for accuracy, precision, recall, and F1 for each U-Net model in the main text or a clearly referenced table. Discuss the implications of the precision-recall trade-off for downstream performance.

### Minor Comments
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3d
- **Evidence pointer** Figure 3d
- **Issue** The figure shows the 52-case benchmark results, but the axes and units are not described in the main text. It is unclear what is plotted and how the Q-score difference is calculated.
- **Required correction** Add a clear figure legend describing the axes, the calculation of Q-score differences, and the meaning of the plotted values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** RNA candidate pool construction
- **Evidence pointer** Methods
- **Issue** The manuscript states that the RNA candidate pool was constructed from the genome by excluding CDS regions, but it does not specify how the 50-nucleotide minimum length was chosen or how overlapping intervals were handled.
- **Required correction** Provide additional detail on the interval definition, including how overlapping intervals were merged or resolved, and justify the 50-nucleotide minimum.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** U-Net training
- **Evidence pointer** Methods
- **Issue** The manuscript states that 92,014 subvolumes were used for training, but does not report the number of unique maps or the distribution of resolutions in the training set.
- **Required correction** Report the number of unique maps, the resolution range, and the distribution of molecular weights in the training set.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The Discussion states that "the structural benchmark should not be interpreted as an evaluation of end-to-end molecular identification across all 52 cases." This is an important caveat, but it is not reflected in the Results section, where the benchmark is presented as evidence of performance.
- **Required correction** Move or repeat this caveat in the Results section where the benchmark is first described, so that readers are not misled.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary Table 4
- **Evidence pointer** Supplementary Table 4
- **Issue** The illustrative example in Supplementary Table 4 is helpful, but it is not clear how the percentile scores are calculated when there are tied values.
- **Required correction** Add a brief description of the tie-handling procedure in the table legend or in the Methods section.

## Risk / unsupported claims
- The claim of "high-recall feature prediction" is not supported by quantitative metrics in the main text.
- The claim of "near-reference fitting quality" in the 52-case benchmark is based on summary statistics only, without per-case data or failure analysis.
- The claim of a "unified sequence-plus-structure route to molecular identification" is based on a single RNA proof-of-concept case with a heavily constrained candidate pool.
- The claim that cryoID2 "addresses" the identification bottleneck is not supported by comparisons to existing tools.
- The statement that "the average decrease was dominated by a small number of failure cases" is an interpretation that is not backed by per-case data.
- The claim that "query sequence identity showed only a weak relationship with map resolution" is based on an R² of 0.137, but the manuscript does not report the number of data points or the confidence interval for this estimate.