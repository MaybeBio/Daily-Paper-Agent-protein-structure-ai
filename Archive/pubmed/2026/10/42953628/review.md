## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Materials and Methods, Results, Discussion, Acknowledgements). Supplementary figures, tables, and sections are referenced but not included.
- **Assessment boundary** Assessment is limited to the supplied manuscript text. All claims that depend on Supporting Information (Figures S1–S9, Supplementary Methods Sections 1–3, Supplementary Results) cannot be independently verified from the material provided.
- **Shared manuscript claim summary** The authors present 3M-BSIP, a multimodal deep learning framework that integrates a protein language model (SaProt), a geometric graph neural network, and a surface pointcloud encoder via cross-attention to predict, from a DBP structure alone, (i) DNA-binding interface residues, (ii) contact-strength ranking, and (iii) residue-level base preference over A/T/C/G. The authors claim state-of-the-art performance on interface and base-preference tasks, robustness to computationally modeled and conformationally flexible (apo) structures, and two real-world applications: motif prediction for an uncharacterized Streptomyces TF (51910) and computational reprogramming of BsaXI base specificity.
- **Visible evidence base** Main-text figures (Figure 1–Figure 6 and unnumbered inline references), Methods descriptions of data curation, feature extraction, model architecture, training, and evaluation metrics, and reported quantitative results in the Results section. No supplementary figures, tables, or source data files are included in the supplied material.
- **Missing materials affecting confidence** Figures S1–S9; Supplementary Methods Sections 1–3; Supplementary Results; the ntM reconstruction procedure; details of the AF3_Test_apo/holo construction; the 54-protein experimental apo/holo set composition; per-family performance breakdowns; statistical tests; code/data availability statement; and any independent validation of the BsaXI and 51910 predictions beyond the reported assays.

## Reviewer
- **Overall assessment** The manuscript describes a technically ambitious multimodal framework for a genuinely difficult problem, namely residue-level base preference prediction from a protein structure alone. The conceptual framing, the three-modality design, and the two application case studies are attractive. However, from the supplied material, several central claims are not yet fully established. The most consequential issues are (i) the absence of a direct, quantitative comparison against the methods the authors position as the closest prior art (DeepPBS, NA-MPNN) on the base-preference task, (ii) reliance on a self-defined supervisory signal whose relationship to experimental base specificity is not independently validated, (iii) incomplete reporting of data-splitting and leakage controls, and (iv) dependence on supplementary material that is not available for verification. The work is potentially publishable if these technical concerns are resolved, but the current evidence base does not yet support the strongest claims.
- **Who would be interested in the results, and why** Computational structural biologists and protein–DNA recognition researchers interested in specificity codes; machine-learning method developers working on multimodal and geometric deep learning for biomolecular interfaces; protein engineers and synthetic biologists interested in reprogramming DNA-binding specificity; and groups curating binding motifs for uncharacterized transcription factors. The residue-level base-preference formulation, if validated, would be of broad interest because most existing methods predict at the motif or interface level rather than at the per-residue base level.
- **Major strengths**
  - The problem is well motivated and the gap in residue-level base-preference prediction is real and clearly articulated.
  - The multimodal design is principled, and the ablation study (Figure 4D–F) provides a coherent argument that sequence, structure, and surface modalities contribute complementary information.
  - The inclusion of apo versus holo robustness testing (Figure 5D–E) addresses a practically important failure mode for structure-based predictors.
  - The two application case studies, particularly the BsaXI reprogramming with SPR validation, are a meaningful attempt to move beyond benchmark metrics toward functional validation.
  - The manuscript is generally well organized and the methods are described at a level of detail that permits partial reproduction.
- **Major Concerns**

  - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Benchmarking and comparative claims
    - **Claim pointer** The manuscript claims "SOTA performance on both interface-residue identification and base-preference predictions" and states that 3M-BSIP "consistently outperforms the existing methods."
    - **Evidence pointer** Results section "3M-BSIP Outperforms the GeoBind Method on Interface-Residue Prediction," Figure 6A–C; Introduction positioning of DeepPBS and NA-MPNN.
    - **Concern** The only head-to-head quantitative comparison reported is against GeoBind, which the authors themselves note does not provide base-preference prediction. DeepPBS and NA-MPNN, which are the methods that actually predict base or motif preferences, are discussed in the Introduction but are not benchmarked against 3M-BSIP on the base-preference task in the supplied text. The SOTA claim for base-preference prediction is therefore not supported by a direct comparison.
    - **Why it matters** The central novelty claim is residue-level base-preference prediction. Without a direct comparison to the closest prior methods on the same test set and the same metric, the SOTA claim is unsubstantiated and the reader cannot judge the actual advance.
    - **Resolution test** Provide a head-to-head evaluation of 3M-BSIP against DeepPBS and NA-MPNN on a common, nonredundant test set using a common metric for base or motif preference, with the same input constraints (protein-only versus protein–DNA complex) clearly stated.

  - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Validity of the supervisory signal
    - **Claim pointer** The model is trained to predict a "residue-level base-preference heatmap" derived from a chemical-aware distance and a hand-designed logit formulation, and this heatmap is treated as ground truth for base preference.
    - **Evidence pointer** Materials and Methods "Generation of Supervisory Signals," "Derivation of Residue Score and Base Allocation Coefficient," and "Generation of Residue-Level Base Preference Heatmap"; Results "Structural Characterizations of Protein–DNA Interface for DBPs."
    - **Concern** The target label is not an experimental measurement of base preference but a deterministic function of the crystal structure geometry, with several arbitrary hyperparameters (discount factors 0.85/0.82/0.80, σ = 3.0 Å, the specific logit formulas, the 4.5 Å cutoff). The manuscript does not demonstrate that this constructed heatmap correlates with experimentally measured base preferences (for example, from PBM, SELEX, or mutation-based affinity data). The model may therefore be learning to reproduce a geometric proxy rather than biological specificity.
    - **Why it matters** If the label is a proxy, all reported base-preference accuracies measure agreement with the proxy, not with biological base preference. This directly affects the interpretation of the benchmark results and the two application claims.
    - **Resolution test** Show that the constructed heatmap correlates with at least one independent experimental measure of base preference on a held-out set, and report the sensitivity of the reported accuracies to the arbitrary hyperparameters in the label construction.

  - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Data splitting and leakage control
    - **Claim pointer** The model "has learned the generalizable biophysical principles of protein–DNA recognition rather than merely overfitting," supported by the deredundancy procedure and hierarchical clustering-based splitting.
    - **Evidence pointer** Materials and Methods "Data Sets and Benchmarks," "Structure Preprocessing and Data Set Partitioning"; Results "Ablation Studies Validate the Necessity of Multimodal Integration," Figure 4A–C.
    - **Concern** The deredundancy criterion removes structures only when both protein and DNA sequences are identical and DNA backbone RMSD is below 1.5 Å. This is a permissive criterion that can retain near-duplicate proteins with different DNA sequences. The splitting is then performed by TM-score clustering with 80/10/10 allocation within each cluster, which places structurally similar proteins in both training and test sets by design. The manuscript does not report sequence-identity-based leakage analysis between training and test sets, nor does it report performance under a strict sequence-identity or fold-level holdout.
    - **Why it matters** The reported test performance, including the high MCC values at low Levenshtein distance, may be inflated by structural and sequence similarity between training and test proteins. The generalization claim depends on ruling this out.
    - **Resolution test** Report a strict holdout evaluation with a defined sequence identity threshold (for example, 30 percent) and a fold-level holdout, and report the corresponding metrics alongside the current numbers.

  - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Reproducibility and reporting completeness
    - **Claim pointer** Multiple results and methodological steps are stated to be detailed in Supporting Information, including the fusion strategy comparison, the ntM reconstruction, the integrated gradient attribution, and the screening pipeline.
    - **Evidence pointer** References to Figure S1, Figure S2, Figure S3, Figure S4, Figure S5, Figure S6, Figure S7, Figure S8, Figure S9, Supporting Information Section 1, Supplementary Methods Sections 2–3, and Supplementary Results.
    - **Concern** The supplied material does not include any supplementary content, and no code or data availability statement is present in the provided text. Several claims, including the fusion strategy comparison and the structural reconstruction that converts the heatmap into the "TTAxT" motif, cannot be evaluated.
    - **Why it matters** The ntM reconstruction is the bridge between the residue-level prediction and the experimentally tested motif. Without it, the 51910 application cannot be fully assessed.
    - **Resolution test** Provide all supplementary figures, tables, and methods, and include a code and data availability statement with repository identifiers.

  - **Concern ID** R1-M5
    - **Severity** Major
    - **Blocking** No
    - **Axis** Statistical rigor of comparative and application claims
    - **Claim pointer** 3M-BSIP "surpasses GeoBind on the majority of tested samples," and the BsaXI screening is described as having a "high success rate (2/3)."
    - **Evidence pointer** Results "3M-BSIP Outperforms the GeoBind Method on Interface-Residue Prediction," Figure 6A–B; Results "Reprogramming the DNA Binding Specificity of a Type IIB Restriction Endonuclease," Figure 6C–D.
    - **Concern** The reported differences are small in several cases (for example, interface MCC 0.545 versus 0.523 on the full test set, and 0.518 versus 0.512 at Levenshtein distance above 5). No confidence intervals, significance tests, or per-sample paired statistics are reported. The BsaXI success rate is based on three candidates, of which one did not achieve reversal, and the specificity ratio changes are reported without error estimates or replicate numbers.
    - **Why it matters** Small metric differences without uncertainty quantification cannot support a superiority claim, and a 2/3 success rate on three candidates is too small to support a general claim about the method's success rate.
    - **Resolution test** Report confidence intervals or paired significance tests for all comparative metrics, and report replicate numbers and error estimates for the SPR measurements.

- **Minor Comments**

  - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Terminology consistency
    - **Affected element** Use of "base preference," "base-specific interaction," and "specificity" across Abstract, Results, and Discussion.
    - **Evidence pointer** Abstract; Results "Reprogramming the DNA Binding Specificity of a Type IIB Restriction Endonuclease."
    - **Issue** The terms are used interchangeably without a stated operational definition distinguishing residue-level base preference from motif-level specificity.
    - **Required correction** Provide a single explicit definition of each term at first use and apply it consistently.

  - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Metric definition
    - **Affected element** "Base-preference accuracy" reported throughout the Results.
    - **Evidence pointer** Results "Ablation Studies," Figure 4D and 4H; Results "3M-BSIP Outperforms the GeoBind Method," Figure 6C.
    - **Issue** The metric is reported as a single accuracy value but its exact definition (per residue, per residue–nucleotide pair, threshold, treatment of noninterface residues) is not fully specified in the supplied text.
    - **Required correction** State the exact formula and the treatment of noninterface residues and ties.

  - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data set description
    - **Affected element** The 54-protein experimental apo/holo set.
    - **Evidence pointer** Results "Well-Tolerance to 3M-BSIP toward the Structurally Flexible DBPs," Figure 5D.
    - **Issue** The composition, source, and redundancy control of this set relative to the training data are not described.
    - **Required correction** Describe how the 54 proteins were selected and confirm no overlap with training data.

  - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Figure and text consistency
    - **Affected element** Reference to "Figure" without a number in the Model Architecture section.
    - **Evidence pointer** Materials and Methods "3M-BSIP Model Architecture," first paragraph.
    - **Issue** The text refers to "(Figure )" with no figure number, and several inline figure references in the Results are unnumbered in the supplied text.
    - **Required correction** Ensure all figure callouts are correctly numbered and consistent with the final figure set.

  - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Claim scope
    - **Affected element** Statement that 3M-BSIP "holds great potential in annotating the binding motifs of all DBPs."
    - **Evidence pointer** Abstract; Discussion.
    - **Issue** The claim of "all DBPs" is broader than the evidence, which covers a curated structural data set and two case studies.
    - **Required correction** Restrict the claim to the tested scope or provide a systematic coverage analysis across DBP families.

- **Technical failings that need to be addressed before the case is established** R1-M1 (absence of direct comparison to DeepPBS and NA-MPNN on base preference), R1-M2 (unvalidated proxy label for base preference), R1-M3 (permissive deredundancy and similarity-based splitting without strict holdout), R1-M4 (missing supplementary material and no code/data availability), R1-M5 (no uncertainty quantification for comparative and application claims).

- **Assessment against Nature-style criteria**
  - **Originality** The residue-level base-preference formulation and the three-modality fusion are a reasonable methodological contribution. However, the originality relative to DeepPBS and NA-MPNN is not demonstrated because no direct comparison is provided.
  - **Scientific importance** The problem is important and the potential impact on motif annotation and protein engineering is significant. The importance claim is weakened by the unvalidated supervisory signal and the small-scale application validation.
  - **Interdisciplinary readership** The topic would interest computational biologists, protein engineers, and synthetic biologists. The current presentation assumes substantial familiarity with geometric deep learning terminology, which limits accessibility.
  - **Technical soundness** The architecture and training pipeline are described in reasonable detail, but the label construction, data splitting, and comparative evaluation have unresolved issues as detailed in R1-M1 through R1-M5.
  - **Readability for nonspecialists** The Abstract and Introduction are accessible. The Methods and Results contain dense jargon and several undefined metrics, which would hinder a nonspecialist reader.

- **Recommendation posture** Currently not established from the provided evidence. The work is potentially supportive if the technical concerns R1-M1 through R1-M5 are resolved, in particular a direct benchmark against DeepPBS and NA-MPNN on base preference, validation of the supervisory signal against experimental base-preference data, and a strict holdout evaluation.

## Risk / unsupported claims
- The claim of SOTA performance on base-preference prediction is unsupported because no direct comparison to DeepPBS or NA-MPNN is provided in the supplied material.
- The claim that the model learns "generalizable biophysical principles" is weakened by the permissive deredundancy criterion and the similarity-based data splitting, with no strict sequence-identity or fold-level holdout reported.
- The claim that the residue-level base-preference heatmap represents biological base preference is not supported by any comparison to experimental base-preference measurements in the supplied text.
- The claim of a "high success rate (2/3)" for BsaXI reprogramming is based on three candidates and lacks replicate numbers and error estimates.
- The claim that 3M-BSIP can "annotate the binding motifs of all DBPs" is broader than the evidence provided.
- The claim that the model is robust to "profound structural rearrangements" is supported by a single detailed example (ZnF456) plus aggregate R2 values, and the aggregate analysis depends on supplementary material not provided.
- The claim that the ntM reconstruction reliably converts residue-level predictions into contiguous motifs cannot be evaluated because the method is in Supplementary Methods Sections 2–3, which are not supplied.
- The claim that the model outperforms GeoBind on "the majority of tested samples" is reported without per-sample paired statistics or confidence intervals.