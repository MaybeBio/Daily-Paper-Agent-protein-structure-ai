## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusion, and data availability statements
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, and claims substantiation based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present VLPIM, a computational pipeline integrating NetMHCIIpan, ProteinMPNN, AlphaFold3, and Rosetta to modulate CD4+ T cell epitope immunogenicity in virus-like particles while preserving structural integrity, with experimental validation on hepatitis B core VLPs demonstrating both immunogenicity reduction and enhancement
- **Visible evidence base** In silico predictions (NetMHCIIpan IC50 values, AF3 structural models, Rosetta interface metrics), SDS-PAGE, TEM, DSF, DSC, and IL-2 ELISA from human PBMC assays
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided (Fig. S1, S2, Table S1), raw numerical data for IC50 predictions, statistical analysis details, HLA typing data, negative controls for immunogenicity assays, and quantitative TEM particle size distributions

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful computational workflow for modulating VLP immunogenicity, with a logical integration of established tools. The core concept of bidirectional immunogenicity modulation in multimeric assemblies addresses a genuine gap. However, the experimental validation is limited in scope and depth, with only two successfully assembled mutants characterized immunologically. The claim of "precise" immunogenicity modulation is not fully supported by the data presented, particularly given the small number of validated variants and the absence of mechanistic experiments demonstrating MHC-II-restricted presentation. The manuscript would benefit from more comprehensive validation, including quantitative dose-response analyses, additional structural characterization, and clearer evidence linking predicted epitope changes to observed T cell responses.

- **Who would be interested in the results, and why** Vaccine developers and researchers in protein engineering would find this workflow relevant, as VLP immunogenicity tuning is a practical challenge in vaccine design and drug delivery. Computational biologists working on immunogenicity prediction and deimmunization of therapeutic proteins may also be interested in the integrated pipeline. The web server and standalone tool availability increases potential utility for applied researchers without deep computational expertise.

- **Major strengths** 
  1. Addresses a relevant problem: immunogenicity modulation of multimeric assemblies, which is underexplored compared to monomeric proteins
  2. Integrates multiple state-of-the-art computational tools into a coherent, accessible pipeline
  3. Bidirectional design capability (both reduction and enhancement) is a useful innovation
  4. Experimental validation, while limited, does demonstrate proof of concept with two successfully assembled mutants
  5. The multimer-aware structural filtering strategy is a thoughtful consideration often missing in deimmunization approaches

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "VLPIM permits precise immunogenicity modulation of VLPs and other multimers"
- **Evidence pointer** Results section, Fig. 6K
- **Concern** The claim of "precise" modulation is based on IL-2 secretion data from only 6 donors, with no dose-response curves, no time-course analysis, and no assessment of whether observed differences are statistically significant. The IL-2 data show substantial donor variability, with PMD-02 showing lower secretion than WT in some donors but the manuscript does not report statistical testing. Furthermore, only 2 of 4 designed mutants successfully assembled into VLPs, and only these 2 were tested immunologically. This limited dataset does not support the strong claim of precise modulation.
- **Why it matters** The central conclusion of the paper rests on the demonstration that the computational predictions translate into predictable immunological outcomes. Without robust statistical analysis and a larger validation set, the precision of the approach cannot be established. The 50% success rate for assembly competence, while acknowledged, also tempers the claim of reliable structural preservation.
- **Resolution test** Provide statistical analysis of IL-2 data (e.g., mixed-effects models accounting for donor variability), include dose-response experiments, and either increase the number of validated mutants or temper the language to reflect proof-of-concept rather than established precision.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** "epitope substitutions could either suppress or enhance CD4+ T cell activation"
- **Evidence pointer** Results section, Fig. 6K
- **Concern** The manuscript attributes observed IL-2 differences to altered CD4+ T cell epitope recognition, but no direct evidence for MHC-II-restricted presentation is provided. IL-2 secretion from PBMCs could reflect multiple mechanisms, including differential uptake, processing, or innate immune activation. The discussion acknowledges this limitation but does not resolve it. The claim that reduced structural stability of PMD-02 would facilitate degradation and therefore the reduced IL-2 is due to epitope changes is speculative and not directly tested.
- **Why it matters** The mechanistic interpretation is central to the claim that the approach modulates immunogenicity through epitope-specific effects. Without blocking antibodies against MHC-II, CD4-depletion experiments, or antigen-presentation assays, alternative explanations cannot be excluded. This weakens the scientific foundation for the proposed mechanism.
- **Resolution test** Include MHC-II blocking experiments, CD4+ T cell depletion or enrichment assays, or use antigen-presenting cells with defined HLA types to demonstrate epitope-specific effects. Alternatively, present data showing that the mutated epitopes are no longer recognized by epitope-specific T cell lines or clones.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation
- **Claim pointer** "VLPIM generated VLP variants that preserved the native virus-like morphology"
- **Evidence pointer** Results section, Fig. 6A to D
- **Concern** TEM images are shown for the assembled mutants, but quantitative analysis of particle size distribution is limited. PMD-02 shows a broader size distribution around 50 nm compared to WT at approximately 28 nm, which is a substantial difference. The manuscript does not discuss whether this size difference affects the validity of comparing these particles as "native-like" or whether the larger size reflects aberrant assembly. No cryo-EM or other high-resolution structural validation is provided.
- **Why it matters** The claim of preserved native morphology is important for the utility of the approach. A 22 nm difference in diameter is significant and may affect immunogenicity through altered antigen display density or particle geometry. Without more detailed structural characterization, the relationship between the computational structural predictions and actual assembled particles remains unclear.
- **Resolution test** Provide quantitative particle size analysis with statistical comparison to WT, and ideally higher-resolution structural data (cryo-EM or negative-stain EM with 2D class averaging) to confirm icosahedral symmetry and T-number preservation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "VLPIM permits precise immunogenicity modulation of VLPs and other multimers"
- **Evidence pointer** Discussion section
- **Concern** The claim of generalizability to "other multimers" is not supported by any data. The workflow was applied to a single VLP system (HBc) with a limited set of mutations. The scaffold-agnostic claim is plausible given the tool integration, but no evidence is presented for application to other systems. The discussion acknowledges this but the abstract and conclusion state it as a capability.
- **Why it matters** Overstating generalizability without evidence could mislead potential users. The performance of the pipeline on other scaffolds with different symmetries, sizes, or assembly mechanisms is unknown. The claim should be framed as a design principle rather than an established capability.
- **Resolution test** Either provide additional examples of application to other VLP systems or multimeric proteins, or revise the language to indicate that the framework is designed to be scaffold-agnostic but has only been validated on HBc VLPs to date.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Scoring function (Eq. 1)
- **Evidence pointer** Materials and Methods, Results section
- **Issue** The Sim score equation is described with a subscript "i" in the text but the equation shows "Siim" which appears to be a typographical error. The description of the normalization is somewhat confusing: it states "lower IC50 values receive lower rank values" but then describes min-max normalization without clearly specifying whether ranks or raw IC50 values are normalized. The equation notation is unclear.
- **Required correction** Clarify the equation notation, correct the typographical error, and provide a clear worked example of how the Sim score is calculated for a hypothetical variant.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 4A and B
- **Evidence pointer** Results section
- **Issue** The manuscript states that the optimal PMD mutant showed a "~19-fold" decrease in antigen affinity and the PMI mutants showed "~33- and ~52-fold" increases. However, the figure panels are not described in sufficient detail to understand what exactly is plotted (predicted IC50 values? fold changes? individual alleles or averaged?). The y-axis labels are not described.
- **Required correction** Provide clear figure legends describing the exact metric plotted, the units, and whether data represent individual alleles or summary statistics. Include error bars or confidence intervals where applicable.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** PBMC immunogenicity assay
- **Evidence pointer** Materials and Methods, Results section
- **Issue** The manuscript states PBMCs were obtained from 6 independent donors but does not report donor demographics, HLA typing, or whether the same donors were used across all experimental conditions. The concentration of VLP used (10 μg/ml) is stated but no justification or dose-response data are provided. The choice of IL-2 as the sole readout is not justified.
- **Required correction** Report donor characteristics and HLA types if available, justify the VLP concentration used, and consider additional readouts (e.g., proliferation, other cytokines) or at minimum discuss the rationale for IL-2 as the primary endpoint.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All experimental data
- **Evidence pointer** Results section
- **Issue** No statistical methods are described in the Materials and Methods. The manuscript reports differences in IL-2 secretion and Tm values without indicating whether these differences are statistically significant or providing measures of variability (SD, SEM, confidence intervals).
- **Required correction** Add a statistical analysis subsection describing the tests used, and report measures of variability and significance levels for all quantitative comparisons.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The introduction cites references for VLP applications and immunogenicity prediction tools but does not adequately contextualize prior deimmunization approaches for multimeric assemblies. The discussion mentions that most applications have focused on therapeutic proteins but does not cite specific prior work on VLP immunogenicity engineering beyond epitope insertion strategies.
- **Required correction** Add citations to prior computational deimmunization efforts for multimeric systems and discuss how VLPIM differs from or improves upon these approaches.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Software availability
- **Evidence pointer** Data Availability, Materials and Methods
- **Issue** The manuscript states the standalone tool is available on GitHub and the web server is accessible, but does not provide a version number, DOI, or specific instructions for installation beyond the pip command. The dependencies and system requirements are not fully specified.
- **Required correction** Provide a versioned release with a DOI, list all dependencies with versions, and include a brief usage example or link to documentation.

## Risk / unsupported claims
- The claim of "precise immunogenicity modulation" is not supported by the limited experimental dataset (2 successfully assembled mutants, 6 donors, single readout)
- The assertion that reduced IL-2 secretion in PMD-02 is attributable to altered epitope recognition rather than structural instability is not directly tested
- The generalizability claim to "other multimers" is asserted without supporting evidence
- The statement that "the success rate of deep-learning-designed mutants (PMI/PMD series, 50%) was remarkably high" lacks statistical context or comparison to baseline success rates from other approaches
- The claim that VLPIM "permits" bidirectional modulation is supported only for the specific HBc VLP system tested, not as a general capability
- The discussion of "cross-presentation via MHC-II molecules" is not directly demonstrated by the experimental data presented