## Review setup
- **Input scope**: Abstract only (no full text, figures, tables, or supplementary material provided)
- **Assessment boundary**: Claims and evidence as presented in the abstract; technical details of the method, experimental protocols, and statistical analyses are not assessable from the supplied material
- **Shared manuscript claim summary**: The authors present Inverse FoldDir, a Dirichlet flow matching-based method for structure-conditioned protein sequence design (inverse folding). The method performs iterative denoising on the amino acid probability simplex, jointly updating all positions. Claims include: (1) state-of-the-art or competitive structural recovery on CATH 4.2 (TM-score 84.5, Cα RMSD 1.76Å vs. ESM-IF1 at 83.3 and 1.86Å); (2) controllable generation supporting full-sequence design, fixed-residue inpainting, and soft priors; (3) denoising trajectory analyses revealing non-uniform position commitment and late-stage residue identity changes; (4) experimental validation in an anti-GFP nanobody redesign task with 2/35 sequences retaining reproducible binding at ~43% sequence divergence.
- **Visible evidence base**: Abstract text only. No figures, tables, methods section, supplementary information, or code repository referenced in the supplied material.
- **Missing materials affecting confidence**: Full manuscript, all figures and tables, methods details (architecture, training data, hyperparameters), baseline comparison protocols, experimental assay details, statistical significance tests, and supplementary information. The abstract reports numerical results without confidence intervals or significance testing.

## Reviewer

- **Overall assessment**: The abstract describes a method that addresses a relevant problem in protein engineering with a technically interesting approach (Dirichlet flow matching on the probability simplex). The reported structural recovery metrics are marginally better than a strong baseline (ESM-IF1), and the experimental validation, while limited in hit rate, provides some evidence of practical utility. However, the abstract alone does not permit assessment of the method's novelty relative to existing flow-based inverse folding approaches, the robustness of the reported improvements, or the statistical and experimental rigor of the validation. The claims are plausible but not fully established from the supplied material.

- **Who would be interested in the results, and why**: Computational protein design researchers, particularly those working on inverse folding and generative models for biomolecular design. Protein engineers and synthetic biologists interested in tools for sequence redesign with experimental validation would also find the nanobody redesign results relevant. The controllability features (fixed-residue inpainting, soft priors) may appeal to practitioners needing constrained design.

- **Major strengths**: 
  1. The method addresses a practically important problem with a technically sound formulation (Dirichlet flow matching on the simplex is a natural fit for categorical sequence generation).
  2. The inclusion of experimental validation in a real protein engineering task strengthens the practical relevance beyond purely computational benchmarks.
  3. The controllability features (inpainting, soft priors) address real needs in protein redesign workflows.
  4. The trajectory analysis provides mechanistic insight into the generation process, distinguishing the method from one-shot or autoregressive approaches.

- **Major Concerns**:

- **Concern ID**: R1-M1
- **Severity**: Major
- **Blocking**: Yes
- **Axis**: Evidence sufficiency for performance claims
- **Claim pointer**: "Inverse FoldDir achieved a mean TM-score of 84.5 (on a 0-100 scale) and a mean Cα RMSD of 1.76Å, compared with 83.3 and 1.86Å, respectively, for ESM-IF1, the strongest evaluated baseline on both metrics."
- **Evidence pointer**: Abstract, no figure or table reference provided
- **Concern**: The reported improvement over ESM-IF1 is small (TM-score +1.2 points, RMSD -0.1Å). The abstract does not report variance, confidence intervals, or statistical significance for these differences. It is unclear whether the improvement is consistent across protein classes, fold types, or sequence lengths, or whether it reflects a few favorable cases.
- **Why it matters**: Without measures of dispersion or significance testing, the claimed superiority over the strongest baseline cannot be distinguished from noise. The protein design community requires robust benchmarks with error bars to assess whether a new method genuinely advances the state of the art.
- **Resolution test**: Provide per-protein distributions, confidence intervals, paired significance tests (e.g., Wilcoxon signed-rank), and stratification by CATH class or sequence length. If the improvement is not significant, the claim should be moderated accordingly.

- **Concern ID**: R1-M2
- **Severity**: Major
- **Blocking**: Yes
- **Axis**: Novelty and positioning relative to prior work
- **Claim pointer**: The method is described as "a controllable inverse-folding method that performs iterative denoising on the amino acid probability simplex" using "a learned Dirichlet flow."
- **Evidence pointer**: Abstract, no related work section provided
- **Concern**: The abstract does not situate Inverse FoldDir relative to existing flow-based or diffusion-based inverse folding methods. Given the rapid proliferation of generative models for protein design, it is essential to clarify what is conceptually new here. Is the Dirichlet flow formulation distinct from prior categorical diffusion or flow matching approaches applied to proteins? What specific limitations of existing methods does this approach overcome?
- **Why it matters**: The scientific contribution of the paper depends on clear differentiation from prior art. Without this positioning, the novelty claim cannot be evaluated, and the paper risks being seen as an incremental application of an existing framework.
- **Resolution test**: Add a related work section that explicitly compares the methodological formulation with prior categorical diffusion models (e.g., ProteinMPNN variants, diffusion-based inverse folding, other flow matching approaches) and articulates the specific advantages of the Dirichlet flow formulation.

- **Concern ID**: R1-M3
- **Severity**: Major
- **Blocking**: Yes
- **Axis**: Experimental validation rigor
- **Claim pointer**: "Two of 35 redesigned sequences retained reproducible sfGFP-binding signal across independent assay runs with approximately 43% sequence divergence from the native nanobody."
- **Evidence pointer**: Abstract, no experimental methods or figures provided
- **Concern**: The experimental validation reports a 5.7% hit rate (2/35) in a single design task. The abstract does not describe the assay format, the threshold for "reproducible binding signal," the expression and purification protocol, or how the 35 sequences were selected. It is also unclear whether the two hits were characterized for affinity, specificity, or biophysical properties beyond binding signal.
- **Why it matters**: For a paper claiming experimental validation, the reader needs sufficient detail to assess whether the assay is meaningful and whether the hit rate reflects genuine design capability or permissive assay conditions. A single task with a low hit rate is weak evidence for general utility.
- **Resolution test**: Provide full experimental methods, including assay details, hit criteria, replicate information, and ideally dose-response or affinity measurements for the two hits. If available, include additional design tasks or negative controls to demonstrate that the method's success is not task-specific.

- **Concern ID**: R1-M4
- **Severity**: Major
- **Blocking**: No
- **Axis**: Controllability claims
- **Claim pointer**: "supporting full sequence generation, fixed-residue inpainting, and user-defined soft residue priors"
- **Evidence pointer**: Abstract, no dedicated evaluation described
- **Concern**: The abstract claims three modes of controllability but does not describe how each was evaluated. For fixed-residue inpainting, what fraction of positions can be fixed while maintaining structural recovery? For soft priors, how are they encoded and what is their effect on sequence diversity and recovery?
- **Why it matters**: Controllability is a key selling point of the method. Without quantitative evaluation of each mode, the claims remain qualitative and cannot be compared with other methods that offer similar features.
- **Resolution test**: Include dedicated experiments for each controllability mode, with metrics such as recovery rate as a function of fixed position fraction, and demonstrate that soft priors are respected without compromising structural fidelity.

- **Minor Comments**:

- **Concern ID**: R1-m1
- **Severity**: Minor
- **Axis**: Clarity of terminology
- **Affected element**: "mean TM-score of 84.5 (on a 0-100 scale)"
- **Evidence pointer**: Abstract
- **Issue**: TM-score is conventionally reported on a 0-1 scale. The parenthetical clarification is helpful, but the choice of a 0-100 scale should be justified or aligned with community conventions to avoid confusion.
- **Required correction**: Either report TM-score on the standard 0-1 scale or explicitly state the scaling convention in the methods.

- **Concern ID**: R1-m2
- **Severity**: Minor
- **Axis**: Completeness of baseline comparison
- **Affected element**: "the strongest evaluated baseline on both metrics"
- **Evidence pointer**: Abstract
- **Issue**: The abstract mentions ESM-IF1 as the strongest baseline but does not list other baselines evaluated. The reader cannot assess the breadth of comparison.
- **Required correction**: List all evaluated baselines in the abstract or indicate that a full comparison is provided in the main text.

- **Concern ID**: R1-m3
- **Severity**: Minor
- **Axis**: Reproducibility
- **Affected element**: Method description
- **Evidence pointer**: Abstract
- **Issue**: No mention of code availability, model weights, or data availability. For a computational method, reproducibility is a key expectation.
- **Required correction**: Add a data and code availability statement.

- **Concern ID**: R1-m4
- **Severity**: Minor
- **Axis**: Interpretation of trajectory analysis
- **Affected element**: "positions commit at different rates and that some residues change identity late in generation"
- **Evidence pointer**: Abstract
- **Issue**: This observation is presented as a feature ("whole-sequence refinement rather than one-shot prediction or irreversible sequential decoding"), but it is unclear whether late-stage residue changes are beneficial or could indicate instability in the generation process.
- **Required correction**: Clarify whether the trajectory analysis is presented as evidence of a desirable property and, if so, connect it to improved outcomes.

- **Technical failings that need to be addressed before the case is established**: R1-M1 (statistical rigor of performance claims), R1-M2 (novelty positioning), R1-M3 (experimental validation detail). These are the primary barriers to establishing the paper's claims.

- **Assessment against Nature-style criteria**: 
  - **Originality**: Not assessable from the abstract alone. The Dirichlet flow matching formulation may be novel, but the abstract does not differentiate it from prior flow-based or diffusion-based inverse folding methods. The originality claim requires a full comparison with prior art.
  - **Scientific importance**: The problem is important, and the combination of controllability with experimental validation is valuable. However, the demonstrated improvement over existing methods is marginal, and the experimental hit rate is low. The importance of the contribution depends on whether the controllability features and the trajectory insights translate into practically meaningful advantages.
  - **Interdisciplinary readership**: The work bridges machine learning and protein engineering, which is of interest to both communities. The abstract is written accessibly, though the trajectory analysis may be of greater interest to the ML community than to experimentalists.
  - **Technical soundness**: The core idea is plausible, but the abstract does not provide enough detail to assess the soundness of the implementation, training procedure, or evaluation protocol. The small performance margin over ESM-IF1 raises questions about robustness.
  - **Readability for nonspecialists**: The abstract is clear and well-structured. The motivation is accessible, and the key results are stated without excessive jargon. The trajectory analysis concept is explained in accessible terms.

- **Recommendation posture**: Currently not established from the provided evidence. The abstract presents a plausible and potentially useful method, but the key claims require the full manuscript to verify. The performance improvement over the baseline is small and lacks statistical support, the novelty relative to prior flow-based methods is unclear, and the experimental validation is limited in scope. A revised assessment would require the full text, figures, and supplementary material.