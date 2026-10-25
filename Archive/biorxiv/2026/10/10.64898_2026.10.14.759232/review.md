## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Supplementary Material descriptions, Author Contributions, Funding, Data Availability, AI Disclosure)
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and claims as presented in the provided text. Figures, tables, and supplementary materials are referenced but not directly examined.
- **Shared manuscript claim summary** The authors present Distance-AF Multimer (Distance-AFM), a training-free, post-hoc refinement method that extends their earlier single-chain Distance-AF approach to protein complexes. The method uses user-provided inter-chain residue-residue distance constraints to correct and refine AlphaFold-Multimer predictions through a three-phase pipeline: (1) initial AFM prediction, (2) a coarse-tuning phase generating diverse starting conformations via rigid-body translational and rotational searches, and (3) a fine-tuning phase optimizing a composite loss function that includes distance constraints, center-of-mass, clash, angle, and modified FAPE terms. The authors claim competitive or superior performance against Chai-1, Protenix, and AlphaLink2 on a 27-target benchmark, robustness to sparse constraints (1-6 constraints sufficient for most gains), successful modeling of peptide-receptor complexes with five distinct failure modes, and scalability to assemblies of 5-10 chains.
- **Visible evidence base** Abstract, Introduction, Results sections (Three-Phase Architecture, Docking model improvement, Distance Constraint Density, Case studies, Model Selection, Peptide-receptor docking, Large protein complexes), Discussion, and manuscript metadata. Figures 1-6 and Supplementary Tables 1-8 are referenced but not directly viewable.
- **Missing materials affecting confidence** All figures, all supplementary tables, the supplementary document describing algorithmic details, and the source code. Statistical details (exact p-values, confidence intervals, per-target data) are not directly verifiable. The benchmark selection criteria and the nature of the "user-defined" constraints in practical scenarios are not fully specified.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing and practically relevant extension of a training-free constraint-based refinement paradigm to protein complex modeling. The core idea, using a coarse-to-fine strategy to overcome the rotational failure modes that plague direct distance-based refinement of multimer predictions, is well motivated and addresses a genuine gap in the field. The reported results, if fully supported by the supplementary data, suggest that the method is effective across a range of complex sizes and error types. However, the current manuscript text leaves several critical technical details underspecified, particularly regarding the loss function formulation, the constraint generation process, and the statistical robustness of the benchmark comparisons. The claims of "competitive or superior" performance and scalability to 10 chains require careful scrutiny of the underlying data, which are not fully visible in the provided text. The manuscript is well-written and accessible, but the evidence base as presented is insufficient to fully establish all claims without access to the supplementary materials.
- **Who would be interested in the results, and why** Computational structural biologists developing or using protein-protein docking and complex prediction tools; experimental biologists who have sparse distance information (e.g., from XL-MS, FRET, or mutagenesis) and need to generate or validate complex models; researchers interested in integrative modeling approaches that combine AI-based prediction with experimental restraints. The training-free nature of the method makes it particularly attractive for users who lack the resources to retrain large models.
- **Major strengths**
  1. The problem addressed is timely and important: integrating experimental restraints into state-of-the-art deep learning predictors without retraining.
  2. The two-step coarse-to-fine strategy is a logical and well-reasoned solution to the specific challenge of large rotational errors in multimer predictions, a limitation that is acknowledged but often not addressed by other methods.
  3. The evaluation is broad, covering dimers, higher-order complexes, peptide-receptor systems with distinct failure modes, and large assemblies, which strengthens the generalizability claims.
  4. The ablation studies on constraint density and distance uncertainty directly address practical usability, which is a significant strength.
  5. The manuscript is clearly written and the figures, as described, appear to illustrate the key concepts and results effectively.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that the loss function includes a "modified FAPE loss" where "the FAPE-loss is only computed within user-defined domains" and that "all inter-domain FAPE contributions are masked out and set to zero." This is claimed to "preserve local geometry and prevent the structure module from distorting well-formed intra-domain structures during iterative updates, while allowing the inter-domain (inter-chain) orientation to be primarily optimized by the distance loss."
- **Evidence pointer** Results, "Three-Phase Architecture of Distance-AF Multimer" section, equations 1 and 2 (not fully shown in text)
- **Concern** The description of the loss function is incomplete and potentially problematic. The text mentions a "modified FAPE loss" but does not provide the full mathematical formulation. The key claim is that masking inter-domain FAPE is beneficial. However, FAPE is a distance-based metric in local frames. Masking it entirely between domains means that the only inter-domain attractive/repulsive forces come from the distance constraints and the clash violation loss. This could lead to a situation where, in the absence of sufficient constraints, the domains are not held together properly, or where the clash loss dominates and prevents proper interface formation. The authors need to clarify whether the center-of-mass loss (Lcom) acts as a global attractor, and how the balance between these terms is maintained. Furthermore, the claim that this masking "prevents distortion" needs to be supported by a comparison against a version of the method without the mask. The current text does not provide this ablation, making the specific design choice difficult to evaluate.
- **Why it matters** The loss function is the core of the fine-tuning phase. If the formulation is not fully specified or the design choice is not rigorously justified, the method cannot be reproduced or its performance properly contextualized. The interaction between the masked FAPE, the distance loss, and the clash loss is critical for understanding why the method works and when it might fail.
- **Resolution test** The authors must provide the complete mathematical formulation of all loss terms in the main text or supplementary. They should also include an ablation study comparing the full method against a version where the FAPE mask is not applied, to demonstrate the specific contribution of this design choice to the final accuracy and the preservation of intra-domain structure.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims "competitive or superior performance compared to other existing deep-learning-based structure prediction methods" based on a 27-target benchmark, and that "D-AFM consistently demonstrates superior or near-superior performance across all metrics."
- **Evidence pointer** Results, "Docking model improvement by Distance-AFM" section, Figure 2, Table 1, Supplementary Table 2
- **Concern** The benchmark comparison is described only in aggregate terms. The text states that D-AFM "wins" against AFM on "every target across every metric with a single exception," but the specific metrics (DockQ, RMSD, iRMSD, lRMSD, Fnat) are not defined in the text, and the statistical significance of these wins is not reported. For example, a "win" in DockQ from 0.10 to 0.12 is not as meaningful as a win from 0.10 to 0.60. The manuscript needs to provide a per-target breakdown of the scores for all methods, and an analysis of whether the improvements are statistically significant (e.g., using a paired test). The selection of the 27 targets is also a potential source of bias. The authors state these were chosen because AFM "failed to generate accurate models," which is a reasonable criterion for a rescue method, but it does not represent a general benchmark. The comparison against Chai-1 and Protenix is described as "closest overall," but the text does not clarify if these methods were given the same distance constraints. If they were not, the comparison is not entirely fair, as the other methods are being evaluated in an unconstrained mode.
- **Why it matters** The central claim of the paper is that the method improves upon existing tools. Without a clear, statistically robust, and fair comparison, this claim is not established. The reader cannot assess the practical significance of the improvements from the current text.
- **Resolution test** The authors should provide a supplementary table with per-target scores for all methods and all metrics. They should perform and report a statistical test (e.g., Wilcoxon signed-rank test) comparing D-AFM to each baseline. They must also clarify whether the baseline methods (Chai-1, Protenix, AlphaLink2) were provided with the same distance constraints, and if not, discuss the implications of this difference in evaluation protocol.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript states that "Up to 12 distance constraints were used per interacting chain pair; fewer were used when fewer residue pairs were successfully matched during constraint generation." and that "All constrained residue pairs and target distances are listed in Supplementary Table 1."
- **Evidence pointer** Results, "Docking model improvement by Distance-AFM" section, Supplementary Table 1
- **Concern** The process of "constraint generation" is not described in the main text. It is unclear how the distance constraints are derived from the native structure in the benchmark. Are they all Cα-Cα distances? Are they randomly selected, or are they chosen to be informative (e.g., at the interface)? The manuscript mentions an ablation on constraint density, but the method for selecting which residues to constrain is a critical part of the pipeline. If the constraints are derived from the native structure, this is a "cheating" scenario that is not realistic for a practical application where the native structure is unknown. The authors need to clarify the source of the constraints in the benchmark and discuss how a user would obtain these constraints in a real-world scenario (e.g., from XL-MS, which gives specific lysine-lysine distances, not arbitrary Cα-Cα distances).
- **Why it matters** The method's utility depends on the availability and quality of distance constraints. If the benchmark uses idealized constraints that are not representative of experimental data, the reported performance may be overly optimistic. The paper's practical impact hinges on this point.
- **Resolution test** The authors must explicitly describe the constraint generation process in the main text. They should clarify whether the constraints are derived from the native structure and discuss the implications of this for practical use. Ideally, they would include a test case using experimentally-derived constraints (e.g., from XL-MS) to demonstrate real-world applicability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims the method "scales effectively to large assemblies, successfully modeling systems with up to 10 chains."
- **Evidence pointer** Results, "Modeling large protein complexes" section, Figure 6, Supplementary Table 8
- **Concern** The results for large complexes are presented as case studies (five examples). While these are valuable, the text does not provide a systematic evaluation of performance on large complexes. The claim of "scales effectively" is based on a small number of examples. The computational cost of the coarse-to-fine search, which involves an exhaustive rotational sweep, is likely to scale poorly with the number of chains. The text mentions that "Typically, 10³–10⁴ docking conformations are generated for a complex of two proteins," but does not state the number for a 10-chain complex. If the number of conformations grows combinatorially, the method may not be practical for very large assemblies.
- **Why it matters** The scalability claim is a key differentiator for the method. If the computational cost is prohibitive for large complexes, the practical utility is limited. The current evidence is anecdotal and does not address the computational scaling.
- **Resolution test** The authors should provide a plot or table showing the number of starting conformations generated and the total computational time as a function of the number of chains. They should also discuss the scaling behavior of the algorithm and its practical limits.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, "Three-Phase Architecture of Distance-AF Multimer" section
- **Evidence pointer** Equations 1 and 2 are referenced but not fully displayed in the text provided.
- **Issue** The loss function equations are not fully presented in the text. The description is fragmented, making it difficult to follow the exact composition of the total loss.
- **Required correction** The full equations for the distance loss and the total loss function should be displayed prominently in the main text, with all terms clearly defined.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Model Selection Using Consensus-Based Scoring" section
- **Evidence pointer** Figure 4, Supplementary Tables 5 and 6
- **Issue** The consensus-based scoring method is introduced as a tool for model selection, but it is not clear if this is a novel contribution of the paper or an application of an existing method. The text mentions "VoroIF-jury in the FTDMP framework" and "LZerD ranksum scoring" but does not provide sufficient context for readers unfamiliar with these tools.
- **Required correction** Provide a brief description of the scoring functions used and clarify whether the modified VoroIF-jury is a new development or a re-implementation of an existing approach.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, "Modeling peptide-receptor docking" section
- **Evidence pointer** Figure 5
- **Issue** The text states that "D-AFM uses DistPepFold-derived weights in the peptide setting." This is an important detail, but it is not explained. What are these weights, and how do they differ from the standard weights?
- **Required correction** Briefly explain the origin and nature of the DistPepFold-derived weights and how they are integrated into the D-AFM framework.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Data Availability Statement"
- **Evidence pointer** Data Availability Statement
- **Issue** The statement says the source code is available at a GitHub URL, but the specific version of the code used for the benchmark is not indicated. This makes it difficult to reproduce the exact results.
- **Required correction** Provide a version tag or commit hash for the code used in the study, or state that the code is available in a specific release.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction cites several references (e.g., Lu et al., 2025; Kagaya et al., 2026) that appear to be from the future relative to the manuscript date. This is unusual and may be a typographical error or a preprint-specific issue.
- **Required correction** Verify the publication years of all cited references and correct any errors.

## Risk / unsupported claims
- The claim of "competitive or superior performance" is not fully supported by the visible text, as the statistical significance and per-target data are not provided.
- The claim that the method "scales effectively" to 10-chain complexes is based on a small number of case studies and lacks a systematic analysis of computational cost scaling.
- The claim that the modified FAPE loss "prevents distortion" is not supported by a direct ablation study.
- The practical utility of the method is unclear because the source and nature of the "user-defined" distance constraints in a real-world scenario are not discussed.
- The claim that the method can "guide and refine" predictions is well-supported by the case studies, but the generalizability of this claim to a broader range of complexes is not established from the provided evidence.