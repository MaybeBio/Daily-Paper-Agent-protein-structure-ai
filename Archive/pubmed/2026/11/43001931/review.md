## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors present two de novo protein binder design campaigns targeting the SARS-CoV-2 RBD, identify two distinct failure modes (insufficient interface stability vs. excessive surface hydrophobicity leading to self-association), develop a computational framework integrating AlphaFold, MD simulations, docking, and SAP analysis to diagnose these failure modes, and demonstrate prospective rescue of a failed binder through targeted surface redesign
- **Visible evidence base** Computational design outputs, AlphaFold2/2-Multimer/3 predictions, MD simulation trajectories, SAP calculations, LightDock docking results, SEC-MALS, SPR, CD spectroscopy, ELISA data
- **Missing materials affecting confidence** Supplementary figures S1–S12 and Tables S1–S2 referenced but not provided; raw MD trajectory data not available; detailed sequence information for all 22 designs not shown; negative control binding data for ELISA not fully described; statistical analysis details for comparing computational metrics across groups not provided

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important problem in de novo protein binder design: understanding why computational designs fail and how to diagnose and correct specific failure modes. The authors present a well-structured study combining computational prediction with experimental validation, and the central finding that surface hydrophobicity represents a critical trade-off axis is mechanistically plausible and practically useful. However, the evidence base is incomplete in several respects. The most significant concern is that the central claim of "rescue" rests on only two redesigned variants, both showing modest low-micromolar affinity, without demonstration that these affinities are sufficient for practical applications or that the redesign strategy generalizes beyond this single case. The computational framework is thoughtfully assembled, but the discriminative power of individual metrics is not rigorously quantified, and the authors do not establish clear thresholds or decision rules that would allow others to apply their diagnostic approach prospectively. The manuscript would be strengthened by additional experimental replicates, a broader set of rescued variants, and more systematic benchmarking of the computational metrics against each other.

- **Who would be interested in the results, and why** Computational protein designers and engineers will find the failure mode analysis and the SAP-based diagnostic framework directly applicable to their own design pipelines. Researchers working on SARS-CoV-2 therapeutics may be interested in the specific binders generated, though the modest affinities limit immediate translational relevance. The broader protein engineering community will value the demonstration that multi-objective optimization, rather than single-metric maximization, is required for successful binder design. Methodologists developing AI-based protein design tools may use the identified failure modes to inform training objectives and filtering strategies.

- **Major strengths**
  1. The study addresses a genuinely important and understudied problem: systematic analysis of why de novo designed binders fail, rather than only reporting successes.
  2. The two design campaigns provide a natural experimental contrast that cleanly separates the two failure modes, strengthening the causal interpretation.
  3. The integration of multiple complementary computational methods (AF2, AFM, AF3, MD, docking, SAP) is thoughtful and reflects best practices in the field.
  4. The prospective rescue experiment provides direct experimental validation of the diagnostic framework, which is a significant strength.
  5. The writing is clear and accessible, with appropriate caveats about limitations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "Guided by these insights, we prospectively redesigned a representative failed binder... Experimental characterization confirmed that the redesigned variants were stable monomers and acquired low μM binding affinities."
- **Evidence pointer** Results section "Computational Design Rescue of Protein Binders"; Figure 3; Table S2
- **Concern** The rescue claim rests on only two variants (R2-6.1 and R2-6.2) derived from a single parent design (R2-6). Both show KD values of 1.4 and 1.7 μM, respectively. While these represent clear improvements over the non-binding parent, the authors do not demonstrate that this approach generalizes. The manuscript would be substantially strengthened by rescuing additional Round 2 designs or by showing that the same principles apply to Round 1 designs. Furthermore, the authors do not report the affinity of the original R2-6 design in the same assay, making it difficult to quantify the magnitude of improvement. The claim that this constitutes a "rescue" implies functional utility, but low-micromolar affinity may be insufficient for most practical applications.
- **Why it matters** The central practical claim of the manuscript is that the diagnostic framework can guide successful redesign. With only two variants from one parent, the evidence for generalizability is weak. If the approach only works for this specific case, its utility as a general framework is limited.
- **Resolution test** Provide rescue data for at least 3-5 additional failed designs from both Round 1 and Round 2, or provide a clear statistical demonstration that the success rate is significantly better than chance. Report the affinity of the parent R2-6 design under identical assay conditions to enable direct comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of metric discrimination
- **Claim pointer** "we establish complementary computational signatures that distinguish these failure modes and reveal their underlying structural determinants"
- **Evidence pointer** Results section "Retrospective Analysis of the Designed Binders"; Figures 1-2
- **Concern** The authors present multiple computational metrics (AF2 confidence, AFM scores, MD stability, docking quality, SAP) but do not provide a systematic quantitative comparison of how well each metric, or combinations of metrics, discriminates between successful and failed designs. The narrative describes qualitative differences (e.g., "Round 1 designs displayed substantially larger L-RMSD values") but does not report effect sizes, confidence intervals, or statistical tests. It is unclear whether any single metric would be sufficient for diagnosis or whether the full multi-metric framework is necessary.
- **Why it matters** For the framework to be practically useful, users need to know which metrics are most informative and how to weight them. Without quantitative benchmarking, the relative importance of each computational tool remains unclear.
- **Resolution test** Perform a systematic comparison of all metrics across the three groups (active controls, Round 1, Round 2), reporting appropriate statistics (e.g., Mann-Whitney U tests with multiple testing correction). Consider a simple classifier (e.g., logistic regression or decision tree) to identify which metrics are most predictive of experimental success.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Control group appropriateness
- **Claim pointer** "benchmarked them against a set of experimentally validated binders"
- **Evidence pointer** Results section "Computational Design of Protein Binders"; Figure 1
- **Concern** The control set consists of binders that underwent yeast display selection and affinity maturation, as acknowledged in the Discussion. This means the controls are not directly comparable to the de novo designs, which were not subjected to any experimental selection. The authors note this limitation but do not fully address its implications. Specifically, the affinity-matured controls may have evolved to reduce surface hydrophobicity through selection pressures that are absent in the computational designs, potentially biasing the comparison.
- **Why it matters** If the controls are systematically different from the designs in ways beyond binding affinity, the conclusions about what distinguishes successful from failed designs may not be generalizable to purely computational design pipelines.
- **Resolution test** Include additional controls that are computationally designed and experimentally validated without affinity maturation, if available. Alternatively, explicitly discuss how the selection history of the controls might affect each metric and whether the conclusions remain valid.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and methodological detail
- **Claim pointer** "The redesign combined two complementary strategies... Among the redesigned variants, R2-6.1 was selected for experimental characterization."
- **Evidence pointer** Results section "Computational Design Rescue of Protein Binders"; Methods section
- **Concern** The selection criteria for choosing R2-6.1 among the redesigned variants are not clearly specified. The authors state that R2-6.1 was "selected" but do not describe how many variants were generated, what the range of predicted properties was, or why R2-6.1 was chosen over others. Similarly, the criteria for selecting R2-6.2 after loop remodeling are not stated. This lack of transparency makes it difficult to assess potential selection bias.
- **Why it matters** If the authors cherry-picked the best-performing variant from a large pool, the success rate of the redesign strategy would be much lower than implied. Transparent reporting of the full design space and selection criteria is essential for evaluating the approach.
- **Resolution test** Report the total number of redesign variants generated, the distribution of their predicted properties (SAP, binding energy, etc.), and the specific criteria used to select R2-6.1 and R2-6.2 for experimental testing.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Results section "Computational Design of Protein Binders"
- **Issue** The description of Figure 1 is minimal and does not clearly explain what is shown in each panel. Given that this figure introduces the design strategies and the control set, a more detailed legend would help readers understand the experimental design.
- **Required correction** Expand the Figure 1 legend to describe each panel explicitly, including the design strategy, the number of designs, and the key features being illustrated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** MD simulation analysis
- **Evidence pointer** Results section "Retrospective Analysis of the Designed Binders"; Figure 2c
- **Issue** The manuscript reports median values for L-RMSD and RMSF across groups but does not provide measures of variability (e.g., interquartile ranges) or the number of independent simulations contributing to each median. This makes it difficult to assess the robustness of the reported differences.
- **Required correction** Add measures of variability (e.g., error bars or shaded regions) to the relevant figures and report the number of replicates in the figure legends or text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** SPR experimental details
- **Evidence pointer** Methods section "Surface Plasmon Resonance"
- **Issue** The SPR methods do not specify the number of independent experiments performed, how the kinetic parameters were averaged across replicates, or whether the reported KD values include confidence intervals. This limits the ability to assess the reliability of the binding measurements.
- **Required correction** Report the number of independent SPR experiments, the variability across replicates, and provide confidence intervals for the reported KD values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of AF3 results
- **Evidence pointer** Results section "Retrospective Analysis of the Designed Binders"; Figure S7b
- **Issue** The authors note that AF3 failed to accurately predict the redesigned variants R2-6.1 and R2-6.2 but do not discuss possible reasons for this failure or its implications for using AF3 as a screening tool.
- **Required correction** Add a brief discussion of why AF3 might fail for these designs and whether this limitation affects the general applicability of the framework.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Generalizability of SAP threshold
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph on SAP
- **Issue** The authors suggest that total SAP values between approximately 30 and 45 were associated with well-behaved binders, but this range is derived from a small dataset and may not generalize to other targets or scaffold types.
- **Required correction** Explicitly state that this range is empirical and target-specific, and recommend that users calibrate SAP thresholds for their own systems.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (insufficient evidence for generalizable rescue), R1-M2 (lack of quantitative metric comparison), R1-M3 (control group comparability), R1-M4 (selection criteria transparency)

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript addresses a relatively underexplored question in protein design, and the systematic analysis of failure modes is a valuable contribution. However, the individual computational methods used are all established, and the novelty lies primarily in their integration and application to this specific problem.
  - **Scientific importance**: Understanding why de novo designs fail is of high importance to the protein design community, and the proposed framework could improve design success rates. The specific application to SARS-CoV-2 RBD is of moderate interest given the availability of many existing binders.
  - **Interdisciplinary readership**: The work bridges computational protein design, biophysics, and experimental biochemistry. The writing is accessible, but the depth of computational detail may limit appeal to purely experimental audiences.
  - **Technical soundness**: The computational methods are appropriate and well-executed, but the lack of quantitative benchmarking and limited experimental validation of the rescue strategy weaken the technical case.
  - **Readability for nonspecialists**: The manuscript is generally well-written with clear explanations of key concepts. However, some sections assume familiarity with protein design terminology and would benefit from brief definitions.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is sound and the framework is potentially valuable, but the evidence for the central rescue claim needs strengthening, and the quantitative rigor of the metric comparison needs improvement. If the authors can address these concerns, the manuscript would make a useful contribution to the protein design literature.

## Risk / unsupported claims
- The claim that the two failure modes are "distinct" and mutually exclusive is not fully supported; some designs may exhibit both insufficient interface stability and excessive hydrophobicity.
- The assertion that "successful binders appear to occupy a relatively narrow window of total interface hydrophobicity" is based on a small number of examples and lacks statistical support.
- The statement that "SolubleMLPNN can mitigate, but not fully eliminate, the problem of exposed hydrophobicity" is based on computational predictions only, without experimental validation of the redesigned sequences.
- The claim that the framework provides "practical criteria for prioritizing candidates before experimental characterization" is not demonstrated with a prospective test on an independent set of designs.
- The relationship between the "false membrane" constraint used in LightDock and the actual experimental conditions is not fully justified.