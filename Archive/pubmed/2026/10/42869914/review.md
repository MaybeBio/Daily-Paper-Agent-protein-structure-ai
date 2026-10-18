## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary figure/table legends as embedded in text)
- **Assessment boundary** Scientific claims, methodological soundness, evidence consistency, and alignment with Nature Communications scope. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report the discovery and characterization of phenyl-glutarimide-based CRBN molecular glues that selectively degrade VAV1 via a non-canonical RT-loop degron (RDxS motif, residues 796–799). They introduce GluePlex, an AI/physics-based pipeline for ternary complex prediction, and validate it with mutagenesis, SAR, FEP calculations, and dose-response proteomics. They also identify LIMD1 as an off-target with a canonical G-loop degron.
- **Visible evidence base** Main text figures (Figs 1–7), supplementary figures (S1–S12 as referenced), supplementary tables (S1), methods section, and source data statements. No raw proteomics data, no uncropped blots, no structural coordinates, no compound characterization data (NMR/HRMS/purity) were provided in the submitted material.
- **Missing materials affecting confidence** Raw mass spectrometry data and analysis outputs; uncropped Western blots; compound synthesis and characterization data (purity, NMR, HRMS); ternary complex structural coordinates (PDB files); FEP convergence metrics and perturbation maps; LIMD1 mutagenesis data; statistical analysis details for proteomics (number of replicates per condition, variance estimates); details on the "high-throughput" nature of the proteomics workflow (sample throughput, multiplexing strategy).

## Reviewer
- **Overall assessment** This manuscript presents a compelling and timely contribution to the molecular glue degrader field. The discovery of a non-canonical RT-loop degron in VAV1, the development of the GluePlex pipeline, and the identification of LIMD1 as an off-target are all significant findings. The integration of unbiased proteomics, AI-based structural prediction, and medicinal chemistry is exemplary and aligns well with the scope of Nature Communications. However, several technical concerns, particularly around the validation of the computational predictions, the quantitative rigor of the proteomics data, and the incomplete characterization of the off-target effects, need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in targeted protein degradation, chemical biology, medicinal chemistry, and structural biology. The work is also relevant to those studying VAV1 biology in hematological malignancies and autoimmune diseases. The GluePlex pipeline will be of interest to computational chemists and AI practitioners in drug discovery.
- **Major strengths**
  1. The identification and validation of a non-canonical RDxS degron in the VAV1 SH3-2 domain is a novel and important finding that expands the known substrate recognition repertoire of CRBN.
  2. The GluePlex pipeline, integrating PeSTo, HADDOCK, and Boltz-2, is a well-conceived and reproducible approach that addresses a critical bottleneck in molecular glue discovery.
  3. The use of unbiased dose-response proteomics to identify both the on-target (VAV1) and an off-target (LIMD1) is rigorous and highlights the importance of global profiling in degrader development.
  4. The medicinal chemistry principle of conformational restriction via halogen substitution, rationalized by DFT calculations, is a valuable and generalizable strategy.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Applying Free Energy Perturbation (FEP) to predicted ternary structures yields cooperativity metrics that correlate with degradation potency, overcoming limitations of standard docking and enabling prospective ranking of analogs—even from weak initial binders."
  - **Evidence pointer** Figure 6, Methods (FEP+ section)
  - **Concern** The correlation between FEP-derived cooperativity metrics and experimental degradation potency is presented as a key validation of the computational approach. However, the manuscript does not report the statistical significance of these correlations (e.g., p-values for Pearson r values are given, but the confidence intervals are wide given n=10). More critically, the FEP calculations are performed on predicted ternary structures from GluePlex, not on experimentally determined structures. The accuracy of FEP is highly sensitive to the starting structure, and the manuscript does not provide a rigorous assessment of the uncertainty in the predicted structures or how this propagates to the FEP results. The claim of "prospective ranking" is not fully supported, as the FEP calculations appear to be retrospective on a small set of analogs.
  - **Why it matters** The central premise of the paper is that the GluePlex/FEP workflow can accelerate molecular glue discovery. If the FEP predictions are not robustly validated, the utility of the pipeline for prospective design is questionable. The lack of structural validation (e.g., co-crystal structure) for the predicted ternary complex is a significant gap.
  - **Resolution test** Provide a more detailed statistical analysis of the FEP correlations, including confidence intervals and cross-validation. Ideally, validate the predicted ternary complex structure with an experimentally determined structure (e.g., X-ray or Cryo-EM) for at least one compound. If not possible, provide a rigorous error analysis of the FEP predictions, including convergence checks and sensitivity to the starting structure.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Dose-response proteomics confirms VAV1 as the primary target and reveals LIMD1, bearing a canonical G-loop, as an off-target, showing that one glue can engage disparate degrons."
  - **Evidence pointer** Figure 7, Methods (proteomics section)
  - **Concern** The identification of LIMD1 as an off-target is a significant finding, but the manuscript does not provide sufficient quantitative detail on the proteomics data. The heatmap in Figure 7A is qualitative. The authors do not report the number of replicates, the magnitude of LIMD1 degradation (e.g., percentage change at specific concentrations), or the statistical significance of the changes. Furthermore, the functional consequences of LIMD1 degradation are not explored. The claim that LIMD1 degradation is "off-target" is based on the presence of a G-loop, but the potential implications for toxicity or efficacy are not discussed.
  - **Why it matters** The identification of off-targets is critical for assessing the therapeutic window and safety of the compounds. Without quantitative data, the reader cannot assess the selectivity of the compounds. The lack of functional data on LIMD1 degradation leaves the biological significance of this off-target activity unclear.
  - **Resolution test** Provide quantitative proteomics data (e.g., log2 fold-changes, adjusted p-values) for VAV1 and LIMD1 across all compounds and concentrations tested. Include a discussion of the potential functional consequences of LIMD1 degradation. If possible, include a simple functional assay (e.g., proliferation or signaling) to assess the impact of LIMD1 loss.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "We further show that conformational restriction via halogen substitution (e.g., NGT-201-17, NGT-201-18) potentiates degradation, a principle rationalized by DFT calculations."
  - **Evidence pointer** Figure 4, Methods (DFT section)
  - **Concern** The DFT calculations are used to rationalize the observed potency differences, but the manuscript does not provide a clear link between the calculated rotational barriers and the experimental degradation data. The DFT calculations are performed on isolated molecules in the gas phase (or with implicit solvent), which may not accurately represent the conformational preferences in the bound state. The manuscript does not report the calculated barriers for all compounds, only a representative example. The claim that conformational restriction "potentiates degradation" is based on a limited set of analogs.
  - **Why it matters** The medicinal chemistry hypothesis is interesting, but the evidence is not fully convincing. A more rigorous analysis would involve calculating the conformational energy landscape in the context of the ternary complex, or at least correlating the calculated barriers with the experimental potencies across a larger set of compounds.
  - **Resolution test** Provide a table correlating the calculated rotational barriers (or energy differences between conformers) with the experimental DC50 and Dmax values for all compounds tested. Discuss the limitations of the DFT approach in the context of the bound state.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction
  - **Evidence pointer** Introduction, paragraph 3
  - **Issue** The introduction mentions "YDS-GlueFold" and "FEP+" without sufficient context for a general reader. The sentence "Computational tools like YDS-GlueFold is combining diffusion model with statistic mechanics for predicting ternary complex structures and guiding molecular design25, while FEP+ binding free energy calculation in the ternary system for explaining cooperativity and target selectivity26" is grammatically awkward and lacks a clear explanation of what these tools do and why they are relevant.
  - **Required correction** Rewrite this sentence to be clearer and more accessible. For example: "Recent computational approaches, such as YDS-GlueFold, combine diffusion models with statistical mechanics to predict ternary complex structures, while alchemical free energy perturbation (FEP) methods can be used to estimate binding cooperativity and selectivity."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods (proteomics)
  - **Evidence pointer** Methods, "High-throughput global proteomics" section
  - **Issue** The methods state that "at least two biological replicates with two MS technical replicates were analyzed for each treatment condition." This is a relatively low number of replicates for a quantitative proteomics experiment, especially for a dose-response analysis. The authors should justify this choice and discuss the potential impact on the statistical power of the analysis.
  - **Required correction** Add a sentence justifying the number of replicates and discussing the statistical power. If possible, include a supplementary figure showing the reproducibility of the replicates.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Figure 3E
  - **Evidence pointer** Figure 3E
  - **Issue** The dose-response curves in Figure 3E are presented as mean ± SD from two independent experiments. Two independent experiments are generally insufficient for a robust statistical analysis. The authors should provide more replicates or acknowledge this limitation.
  - **Required correction** Provide additional replicates or clearly state the limitation in the figure legend.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods (FEP+)
  - **Evidence pointer** Methods, "Schrodinger Glide Docking and FEP+" section
  - **Issue** The FEP+ methods section is brief and lacks details on the perturbation map, the number of lambda windows, the simulation length, and the convergence criteria. This makes it difficult to assess the reliability of the FEP results.
  - **Required correction** Provide a more detailed description of the FEP+ setup, including the perturbation map, simulation parameters, and convergence assessment.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results (SAR sections)
  - **Evidence pointer** Results, "Structure-activity relationship studies" sections
  - **Issue** The SAR sections are dense and difficult to follow for a reader not deeply familiar with medicinal chemistry. The authors should consider adding a summary table or a more accessible description of the key findings.
  - **Required correction** Consider adding a summary paragraph at the end of each SAR section that highlights the key takeaways in plain language.

## Risk / unsupported claims
- The claim that GluePlex can "prospectively rank" analogs is not fully supported, as the FEP calculations appear to be retrospective on a small set of compounds.
- The claim that conformational restriction "potentiates degradation" is based on a limited set of analogs and a simplified DFT analysis.
- The identification of LIMD1 as an off-target is not supported by quantitative proteomics data.
- The claim that the VAV1 RT-loop degron is "non-canonical" is supported by mutagenesis, but the manuscript does not provide a direct comparison to known G-loop degrons in the same experimental system.
- The statement that "the recent independent report by Petzold et al.19 highlights the versatility of CRIN" (as quoted in the Discussion) is not verifiable from the provided text, as reference 19 is not described in detail.