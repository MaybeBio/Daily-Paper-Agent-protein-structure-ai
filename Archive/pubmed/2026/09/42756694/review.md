## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, results, discussion, conclusion) without figures, tables, or supplementary material
- **Assessment boundary** Computational design and evaluation of RNA aptamers targeting miR-10b using T-SELEX, docking, QM calculations, MD simulations, and MM-PBSA analysis
- **Shared manuscript claim summary** The authors propose a multiscale computational workflow (T-SELEX) integrating sequence generation, RNA folding, docking, QM calculations, MD simulations, and MM-PBSA analysis to design and evaluate RNA aptamer candidates targeting oncogenic miR-10b and its mature 5p and 3p arms. They identify specific aptamers (e.g., aptamer557 for miR-10b-3p, aptamer899 for miR-10b-5p) as top candidates and introduce a composite stability metric (mμ) combining RMSD area integration and changepoint detection for assessing RNA complex stability.
- **Visible evidence base** Text descriptions of results; references to figures (Figures 1-8 approximately), tables (Table 1), and supplementary materials (Tables S1-S10, Figures S1-S7, S12-S13) that were not provided
- **Missing materials affecting confidence** All figures, tables, and supplementary information; specific numerical data for docking scores beyond top candidates; MD simulation parameters and convergence criteria; QM calculation details; validation metrics for the stability metric algorithm

## Reviewer

- **Overall assessment** This manuscript presents a computationally intensive pipeline for RNA aptamer design targeting miR-10b, an oncogenic microRNA of clinical relevance. The integration of multiple computational methods is commendable in scope, and the introduction of a composite stability metric (mμ) for RNA complex analysis represents a potentially useful methodological contribution. However, the manuscript suffers from several critical issues that undermine confidence in the conclusions. First, the abstract contains a significant internal inconsistency: it states that the library was screened against miR-10b targets, yet the results section reports the strongest interactions with hsa-miR-25-5p, hsa-miR-122-5p, and hsa-miR-155-5p, which are not the stated targets. This discrepancy is not adequately explained. Second, the validation of the computational predictions is entirely absent; no experimental data, benchmarking against known aptamer-target pairs, or comparison with alternative computational methods is provided. Third, the novelty of the approach is overstated, as the individual components (RNAfold, RNAComposer, HDOCK, GFN2-xTB, GROMACS, MM-PBSA) are all established methods, and the claimed novelty of the T-SELEX framework and mμ metric requires more rigorous benchmarking and comparison with existing approaches. The manuscript would benefit from substantial revision, including clarification of the target selection rationale, addition of validation studies, and more careful interpretation of results relative to the stated aims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on RNA-targeted drug discovery would find the integrated pipeline of interest, particularly the methodological aspects of combining docking, QM calculations, and MD simulations with a novel stability metric. Researchers focused on microRNA therapeutics, especially those targeting miR-10b in cancer contexts, may find the identified aptamer candidates worth pursuing for experimental validation. Methodologists developing computational tools for RNA-RNA interaction analysis would be interested in the mμ stability metric, provided it is properly validated and benchmarked.

- **Major strengths**
  1. The integration of multiple computational methods (sequence generation, folding, docking, QM, MD, MM-PBSA) into a unified pipeline is comprehensive and reflects current best practices in computational drug discovery.
  2. The introduction of a composite stability metric (mμ) combining RMSD area integration with changepoint detection addresses a real need in RNA dynamics analysis, where conventional RMSD interpretation is often insufficient.
  3. The authors acknowledge limitations of individual methods (e.g., MFE structure as approximation, HDOCK scoring function limitations) and appropriately frame results as computational predictions requiring experimental validation.
  4. The study addresses a clinically relevant target (miR-10b) with established roles in cancer metastasis, increasing the translational relevance of the work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency and claim-target alignment
- **Claim pointer** The abstract states the study aims to design aptamers targeting miR-10b and its mature 5p and 3p arms, and the introduction reiterates this focus. However, the results section reports that "hsa-miR-25-5p consistently shows the most favorable interaction profile" and identifies hsa-miR-25-5p, hsa-miR-122-5p, and hsa-miR-155-5p as top candidates based on interaction energy analysis.
- **Evidence pointer** Abstract; Results and Discussion, "RNA-RNA Interaction Predictions" section
- **Concern** The manuscript presents a fundamental inconsistency between the stated target (miR-10b) and the reported findings. The interaction energy analysis identifies hsa-miR-25-5p, hsa-miR-122-5p, and hsa-miR-155-5p as having the strongest interactions, yet these are not the targets the study claims to address. This discrepancy is not explained or discussed. If the aptamer library was screened against 13 oncogenic miRNAs including miR-10b, the rationale for including these additional targets and the implications of finding stronger interactions with non-target miRNAs must be addressed. This issue fundamentally affects the interpretation of the results and the validity of the stated conclusions about miR-10b targeting.
- **Why it matters** The central claim of the manuscript is the design of aptamers targeting miR-10b. If the computational screening identifies stronger interactions with other miRNAs, this either (a) undermines the specificity of the designed aptamers for miR-10b, or (b) indicates that the screening was broader than stated, requiring reinterpretation of the results. Without clarification, the reader cannot assess whether the identified aptamers are genuinely selective for miR-10b or whether they might have off-target effects on other miRNAs.
- **Resolution test** The authors must clarify the scope of the screening (was it against 13 miRNAs or only miR-10b targets?) and provide a discussion of the specificity of the top aptamer candidates. If other miRNAs show stronger interactions, the authors should either explain why the focus remains on miR-10b or acknowledge that the aptamers may not be selective. Ideally, the authors should provide a comparative analysis of aptamer binding to miR-10b versus the other identified miRNAs to assess selectivity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and benchmarking
- **Claim pointer** The manuscript claims the T-SELEX workflow "identifies computationally promising aptamer candidates" and that the stability metric mμ provides a "robust post-MD analytical tool for RNA-RNA interaction studies."
- **Evidence pointer** Abstract; Methodology, "Stability Metrics" section; Conclusion
- **Concern** The manuscript provides no validation of the computational predictions against experimental data or established benchmarks. No known aptamer-target pairs are used as positive controls to assess whether the docking scores, interaction energies, or stability metrics correlate with experimentally measured binding affinities. The mμ metric is introduced without benchmarking against existing stability measures or demonstrating its superiority over conventional RMSD analysis. The authors do not compare their results with those obtained from alternative computational methods (e.g., other docking tools, different force fields, or established RNA-RNA interaction prediction algorithms).
- **Why it matters** Without validation, the reader cannot assess whether the computational predictions are reliable. The field of computational drug discovery is replete with examples where in silico predictions do not translate to experimental activity. The introduction of a new metric (mμ) without benchmarking is particularly problematic, as its interpretation and utility remain unclear. The claim that the workflow "identifies computationally promising aptamer candidates" is weakened by the absence of any evidence that the computational rankings correlate with actual binding affinity.
- **Resolution test** The authors should include a validation section demonstrating that their pipeline can correctly identify known aptamer-target interactions (e.g., using experimentally validated aptamer-miRNA pairs as positive controls). The mμ metric should be benchmarked against existing stability measures (e.g., conventional RMSD, RMSF, radius of gyration) and its added value demonstrated. Ideally, the authors should also compare their docking and scoring results with those from alternative methods to show consistency or explain discrepancies.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor and reproducibility
- **Claim pointer** The methodology describes MD simulations using an "in-house PySMQM workflow" implemented within GROMACS, described as "a statistical mechanics and quantum mechanics extension we developed for RNA studies."
- **Evidence pointer** Methodology, "Molecular Dynamics Simulations" section
- **Concern** The description of the MD simulation protocol is insufficient for reproducibility. Key parameters are missing, including: the specific Amber force field version used, the salt concentration and ion type for neutralization, the temperature and pressure coupling algorithms and parameters, the integration time step, the cutoff schemes for nonbonded interactions, and the treatment of long-range electrostatics. The "PySMQM workflow" is mentioned but not described in sufficient detail for others to implement or evaluate it. The criteria for selecting the "best five models from the top four aptamer-miRNA complexes" for QM calculations are not clearly defined. Additionally, the manuscript states that 40 complexes were simulated, but the selection criteria for these 40 from the larger pool of candidates are not specified.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without complete methodological details, other researchers cannot replicate the simulations or assess the validity of the results. The use of an in-house workflow that is not fully described raises concerns about the transparency and generalizability of the approach. The lack of clarity on complex selection criteria introduces potential selection bias that could affect the conclusions.
- **Resolution test** The authors should provide complete simulation parameters in the methodology or supplementary information, including force field version, water model, ion concentration, ensemble parameters, and integration settings. The PySMQM workflow should be described in sufficient detail or made available. The criteria for selecting complexes for QM calculations and MD simulations should be explicitly stated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of results and biological relevance
- **Claim pointer** The manuscript concludes that "aptamer331 and aptamer274 consistently formed the most stable complexes with miR-10b-5p and miR-10b-3p, respectively" based on MD simulations and stability metrics, while also noting that "partial Watson-Crick interactions were observed" suggesting a "hybrid binding mechanism."
- **Evidence pointer** Results and Discussion, "Molecular Dynamics" and "MM-PBSA" sections; Conclusion
- **Concern** The biological interpretation of the results is underdeveloped. The manuscript does not discuss whether the predicted binding modes are biologically plausible given the known structure and function of miR-10b. The observation of "partial Watson-Crick interactions" is presented as a novel finding, but the functional implications of this hybrid binding mechanism are not explored. The manuscript does not address whether the identified aptamers would be expected to inhibit miR-10b function in cellular contexts, nor does it discuss potential off-target effects given the sequence similarity between miR-10b and other miRNAs. The discrepancy between the docking rankings (aptamer557 for miR-10b-3p, aptamer899 for miR-10b-5p) and the MD-based stability rankings (aptamer274 for miR-10b-3p, aptamer331 for miR-10b-5p) is not reconciled.
- **Why it matters** The ultimate goal of the study is to identify aptamers that could therapeutically target miR-10b. The biological relevance of the computational predictions is critical for this goal. The lack of discussion about how the predicted binding would translate to functional inhibition, and the unresolved discrepancy between different computational rankings, leaves the reader uncertain about which aptamers to prioritize for experimental validation.
- **Resolution test** The authors should provide a more detailed discussion of the biological implications of their findings, including how the predicted binding modes relate to miR-10b function. The discrepancy between docking and MD rankings should be addressed, with a clear recommendation on which aptamers should be prioritized for experimental testing and why. The authors should also discuss potential off-target effects and specificity considerations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Abstract; Methodology
- **Evidence pointer** Abstract; Methodology, "Data Generation and Virtual Screening" section
- **Issue** The manuscript uses the term "T-SELEX" and "T_SELEX" interchangeably. The abstract uses "T-SELEX" while the methodology uses "T_SELEX." This inconsistency in terminology is confusing and should be standardized throughout.
- **Required correction** Standardize the terminology to a single form (e.g., "T-SELEX") and use it consistently throughout the manuscript, including the abstract, methodology, results, and conclusion.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results and Discussion, "Virtual Screening" section
- **Evidence pointer** Results and Discussion, "Virtual Screening" section; Table 1
- **Issue** The manuscript states that "the top-scoring aptamer achieved a docking score of approximately -550 against miR-10b_3p and approximately -500 against miR-10b_5p" but does not specify which aptamer achieved these scores in the text. The specific aptamer identities are only available in Table 1, which was not provided for review.
- **Required correction** The text should explicitly identify the aptamers corresponding to the top docking scores for each target, even if the full data are presented in the table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results and Discussion, "MM-PBSA" section
- **Evidence pointer** Results and Discussion, "MM-PBSA" section
- **Issue** The MM-PBSA results are presented as comparative indicators, but no statistical analysis (e.g., standard deviations, confidence intervals, or significance testing) is reported. Given that MM-PBSA calculations are known to be sensitive to simulation length and conformational sampling, the absence of error estimates limits the interpretation of differences between aptamers.
- **Required correction** Provide standard deviations or other measures of uncertainty for the MM-PBSA binding energies, and indicate whether differences between aptamers are statistically significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction provides a general overview of aptamers and their advantages but does not adequately situate the work within the existing literature on computational aptamer design against miRNAs. The authors mention their previous introduction of T-SELEX but do not cite or discuss other computational approaches for RNA aptamer design, nor do they discuss previous attempts to target miR-10b with nucleic acid therapeutics.
- **Required correction** Expand the introduction to include a brief review of existing computational methods for RNA aptamer design and previous therapeutic approaches targeting miR-10b, to better establish the novelty and significance of the present work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Results and Discussion, all sections
- **Evidence pointer** Figures 1-8 (not provided)
- **Issue** The manuscript references multiple figures, but their content and quality cannot be assessed from the text alone. The figure captions are not included in the text, making it difficult to understand what each figure displays.
- **Required correction** Ensure that figure captions are comprehensive and self-explanatory, and that all figures are of sufficient resolution and quality for publication.

- **Technical failings that need to be addressed before the case is established**
  1. The internal inconsistency between the stated target (miR-10b) and the reported strongest interactions (hsa-miR-25-5p, hsa-miR-122-5p, hsa-miR-155-5p) must be resolved (R1-M1).
  2. The absence of any experimental validation or benchmarking against known aptamer-target pairs undermines confidence in the computational predictions (R1-M2).
  3. The MD simulation protocol is insufficiently described for reproducibility, and the selection criteria for complexes subjected to QM calculations and MD simulations are not specified (R1-M3).
  4. The discrepancy between docking-based and MD-based aptamer rankings is not reconciled, leaving uncertainty about which candidates should be prioritized (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The integration of multiple computational methods into a unified pipeline is not entirely novel, as similar multiscale approaches have been reported for RNA-targeting drug design. The introduction of the mμ stability metric is a potentially original contribution, but its novelty and utility are not adequately demonstrated without benchmarking.
  - **Scientific importance**: Moderate. miR-10b is a clinically relevant oncogenic miRNA, and computational approaches to identify RNA aptamers against it could have translational value. However, the study is purely computational, and the lack of experimental validation limits the immediate scientific impact.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians specializing in RNA structure and drug design. The clinical relevance to cancer researchers is acknowledged but not developed sufficiently to attract a broader readership.
  - **Technical soundness**: Questionable. While the individual computational methods are established, the lack of validation, incomplete methodological details, and internal inconsistencies in the results undermine confidence in the technical rigor of the study.
  - **Readability for nonspecialists**: Acceptable. The manuscript is generally well-written and accessible, with clear explanations of the computational methods. However, the technical details of the stability metric and the significance of the results may be challenging for nonspecialists to fully appreciate.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a computationally intensive pipeline with potentially useful methodological contributions, but the internal inconsistency regarding target selection, the absence of validation, and the incomplete methodological details prevent the conclusions from being supported by the evidence presented. Substantial revision and additional work, including benchmarking and clarification of the target selection rationale, would be required before the case for the computational aptamer candidates is established.

## Risk / unsupported claims
- The claim that the T-SELEX workflow "identifies computationally promising aptamer candidates" is unsupported without validation against experimental data or known aptamer-target pairs.
- The claim that the mμ stability metric provides a "robust post-MD analytical tool" is unsupported without benchmarking against existing stability measures.
- The identification of aptamer557 and aptamer899 as top binders to miR-10b-3p and miR-10b-5p, respectively, is based solely on docking scores and cannot be assessed for reliability without experimental validation.
- The conclusion that "aptamer331 and aptamer274 consistently formed the most stable complexes" is based on MD simulations and stability metrics, but the discrepancy with docking rankings is not resolved, and the biological significance of these findings is not established.
- The statement that "partial Watson-Crick interactions were observed" suggesting a "hybrid binding mechanism" is presented as a finding, but the evidence for this mechanism is not clearly presented in the text provided.
- The claim that the workflow "enables large-scale identification and structural evaluation of computationally promising RNA aptamer candidates" is not supported by any comparison with alternative methods or demonstration of scalability beyond the 1100-aptamer library.