## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure legends as provided.
- **Assessment boundary** Evaluation is limited to the scientific content, methodology, data interpretation, and claims presented in the supplied manuscript text. No external data, unpublished results, or additional literature beyond what is cited within the text were consulted.
- **Shared manuscript claim summary** The manuscript reports cryo-EM structures of the yeast tRNA methyltransferase Trm10 bound to tRNAGly-GCC in three distinct states, including two monomeric complexes with different tRNA conformations and a minor dimeric complex. The authors propose that these structures, together with MD simulations and biochemical experiments, reveal the molecular basis of tRNA substrate recognition, G9 nucleotide flipping, guanosine selectivity, and a potential functional role for a tRNA-dependent Trm10 dimer in the modification mechanism.
- **Visible evidence base** Cryo-EM density maps and structural models (PDB 9XZQ, 9XZR, 9XZS; EMD-72368, EMD-72369, EMD-72370), in vitro methyltransferase activity assays, fluorescence anisotropy binding assays, BS3 crosslinking experiments, RNase T1 footprinting, MD simulations, and sequence conservation analyses. Table 1 provides cryo-EM data collection and refinement statistics. Supplementary figures S1–S18 and Supplementary Table S1 are referenced.
- **Missing materials affecting confidence** The manuscript text references supplementary figures and tables that were not provided in the submitted material. These include Supplementary Figures S1–S18 and Supplementary Table S1, which contain critical supporting data such as the native gel electrophoresis showing complex formation, cryo-EM processing workflows, local resolution maps, sequence alignments, activity data for Trm10 variants, and MD simulation details. Without these materials, the completeness of the evidence base cannot be fully assessed.

## Reviewer
- **Overall assessment** This manuscript presents a substantial advance in understanding how the atypical monomeric SPOUT methyltransferase Trm10 recognizes and modifies its tRNA substrates. The cryo-EM structures of Trm10 bound to tRNAGly-GCC in multiple conformational states are novel and provide the first high-resolution views of a stand-alone Trm10 enzyme in complex with its substrate. The identification of a tRNA-dependent dimeric complex is unexpected and potentially significant. However, several technical concerns regarding the cryo-EM density quality, the interpretation of the dimeric state, and the functional relevance of the observed conformations need to be addressed before the conclusions are fully supported. The manuscript is well-written and the logical flow is clear, but the absence of key supplementary data limits the ability to fully evaluate the claims.
- **Who would be interested in the results, and why** Researchers studying RNA modification enzymes, particularly tRNA methyltransferases, will find this work of high interest. The structures provide mechanistic insight into substrate recognition by a monomeric SPOUT enzyme, which contrasts with the dimeric architecture of most other SPOUT family members. The findings are also relevant to those investigating the molecular basis of human diseases linked to TRMT10A mutations, as the structural data help rationalize the effects of pathogenic variants. Additionally, the work contributes to the broader understanding of how RNA-modifying enzymes achieve substrate specificity through induced fit and conformational selection mechanisms.
- **Major strengths** The manuscript presents the first cryo-EM structures of a stand-alone Trm10 enzyme bound to its tRNA substrate, filling a significant gap in the field. The use of a SAM analog to trap a post-catalytic state is a clever and effective strategy. The observation of two distinct monomeric complexes with different tRNA conformations, along with a minor dimeric complex, provides a rich structural dataset that supports a dynamic model of substrate recognition. The combination of structural, biochemical, and computational approaches strengthens the conclusions. The authors also make a commendable effort to connect their findings to disease-associated mutations in human TRMT10A.
- **Major Concerns** Several concerns are detailed below. The most significant relate to the interpretation of the dimeric complex, the functional relevance of the open and closed tRNA conformations, and the lack of quantitative validation for some structural claims.
- **Minor Comments** Several minor issues regarding presentation, statistical reporting, and clarity are noted below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dimeric complex interpretation), R1-M2 (functional relevance of open/closed states), R1-M3 (MD simulation validation), R1-M4 (quantitative binding data).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The structures are novel and provide the first view of a stand-alone Trm10 enzyme in complex with tRNA. The dimeric complex is an unexpected finding that challenges the prevailing view of Trm10 as a strictly monomeric enzyme.  
  *Scientific importance*: High. The work addresses a long-standing question in the field regarding how Trm10 achieves substrate specificity without the dimeric architecture common to other SPOUT enzymes. The findings have implications for understanding tRNA modification mechanisms across species and for interpreting disease-associated mutations.  
  *Interdisciplinary readership*: Moderate. The work will primarily appeal to structural biologists, RNA biochemists, and researchers in the tRNA modification field. The broader cell biology and genetics communities may find the disease connections interesting, but the technical nature of the structural analysis may limit wider appeal.  
  *Technical soundness*: Generally sound, but with concerns. The cryo-EM maps are reported at reasonable resolutions, but the quality of the density for key regions, particularly in the dimeric complex, needs careful evaluation. The MD simulations are used to support conclusions but lack sufficient validation details.  
  *Readability for nonspecialists*: The manuscript is clearly written and the figures are well-referenced in the text. However, the level of detail in the structural analysis and the reliance on specialized terminology may make it challenging for nonspecialists to fully appreciate the significance of the findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural findings are likely to be of significant interest, but the interpretation of the dimeric complex and the functional relevance of the conformational states require additional experimental support and clarification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of structural data
- **Claim pointer** The manuscript claims that the (Trm10)2–tRNA complex represents a functionally relevant state, with the second Trm10 (Trm10′) positioned near the anticodon stem-loop and potentially involved in promoting conformational transitions during tRNA modification.
- **Evidence pointer** Results section "A subpopulation of complexes containing two Trm10 enzymes is observed with a single tRNA"; Figure 6; Supplementary Figures S2A, S3G–I, S7, S14–S17
- **Concern** The dimeric complex is described as a "minor" population comprising only 5.2% of particles. The map resolution for this complex is 3.89 Å, which is lower than the monomeric complexes. The authors acknowledge that the map quality limits identification of specific contacts. The functional significance of this dimeric state is largely inferred from MD simulations and crosslinking experiments, but the crosslinking data are not shown in the provided text (referenced as Supplementary Figure S6D). The MD simulations suggest that Trm10′ influences tRNA dynamics, but the simulations are performed on a model that may not accurately represent the physiological state. The claim that this dimeric complex is functionally important requires stronger experimental validation, such as mutagenesis of the proposed Trm10′ interface residues followed by activity assays, or demonstration that the dimeric state is required for efficient methylation under physiological conditions.
- **Why it matters** The dimeric complex is presented as a novel and significant finding. If the interpretation is not well-supported, the central message of the manuscript is weakened. The claim that Trm10 functions via a transient dimeric mechanism is a major departure from the current understanding of this enzyme as a monomer, and therefore requires robust evidence.
- **Resolution test** Provide the crosslinking data showing tRNA-dependent dimer formation. Perform mutagenesis of residues at the proposed Trm10′–tRNA interface and test the effects on methylation activity and dimer formation. Alternatively, use techniques such as mass photometry or size-exclusion chromatography coupled with multi-angle light scattering to demonstrate the existence of the dimeric complex in solution under conditions relevant to catalysis. If the dimeric complex is a minor species, its functional relevance should be demonstrated through kinetic assays that correlate dimer formation with methylation activity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance of conformational states
- **Claim pointer** The manuscript proposes that the open and closed tRNA conformations represent distinct functional states, with the open conformation being a product-release state and the closed conformation being catalytically competent.
- **Evidence pointer** Results section "Trm10 induces structural changes throughout the bound tRNA"; Figures 1, 2; Supplementary Figures S3, S8, S9
- **Concern** The assignment of the open conformation as a product-release state is speculative. The manuscript states that the open conformation weakens protein-tRNA contacts, but no direct experimental evidence links this conformation to product release. The closed conformation is assumed to be the catalytically active state, but the structures are of a post-catalytic complex with NM6 covalently attached to G9. The relevance of these conformations to the catalytic cycle is not directly demonstrated. The manuscript does not provide kinetic or thermodynamic data showing that the open conformation has a lower affinity for the modified tRNA or that the closed conformation is required for catalysis. The proposal that the open conformation represents a product-release state is plausible but not proven.
- **Why it matters** The conformational states are central to the proposed mechanism of Trm10 function. If the assignment of these states to specific steps in the catalytic cycle is incorrect, the mechanistic model presented in the manuscript is not supported.
- **Resolution test** Perform stopped-flow or rapid-quench kinetic experiments to correlate the conformational states with catalytic steps. Alternatively, use FRET or other spectroscopic methods to monitor conformational changes in real time during the methylation reaction. If the open conformation is a product-release state, mutations that stabilize the open conformation should accelerate product release, while mutations that stabilize the closed conformation should slow it down.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology
- **Claim pointer** The manuscript uses MD simulations to support the conclusion that Q118 selectively stabilizes G9 over A9, and to analyze the effects of 6A substitutions on the dimeric complex.
- **Evidence pointer** Results section "Q118 mediates selective stabilization of G9 for methylation"; Figures 5, 7; Supplementary Figures S15–S17
- **Concern** The MD simulation methods are described only briefly. The manuscript states that simulations were performed using the OPLS4 force field and Desmond, but does not provide details on the system setup, equilibration protocol, or the number of replicates beyond stating that three independent replicates were performed. The simulation time is not stated. The convergence of the simulations is not demonstrated. The distance distributions shown in Figure 5C are used to conclude that Q118 interacts more stably with G9 than A9, but the statistical significance of the difference is not assessed. The energy calculations in Figure 5D are presented as average values without error bars or statistical analysis. The MD simulations of the dimeric complex with 6A substitutions are used to draw conclusions about the role of specific residues, but the validity of the simulation model is not established.
- **Why it matters** The MD simulations are used to support key conclusions about substrate selectivity and the role of the dimeric complex. If the simulations are not well-validated or statistically robust, these conclusions are weakened.
- **Resolution test** Provide full details of the MD simulation setup, including simulation time, equilibration protocol, and convergence criteria. Perform statistical analysis of the distance and energy distributions, such as bootstrapping or block averaging, to assess the significance of the differences between G9 and A9. Validate the simulation results against experimental data, such as the effects of Q118 mutations on activity and selectivity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative data reporting
- **Claim pointer** The manuscript reports binding affinities (KD,app) and Hill coefficients for Trm10 variants, and methylation activities for various constructs.
- **Evidence pointer** Materials and methods section "Trm10 in vitro methyltransferase activity" and "Trm10–tRNA binding"; Supplementary Figures S6B, S6C
- **Concern** The binding data are reported as KD,app values with errors propagated from three independent measurements, but the actual values are not stated in the text. The activity data are described qualitatively (e.g., "retained essentially wild-type binding affinity", "near wild-type level activity") without providing quantitative values or statistical comparisons. The manuscript states that Trm10-Δ47 and Trm10-Δ63 showed "intermediate and essentially no activity", respectively, but the specific activities are not given. The lack of quantitative data makes it difficult to assess the magnitude of the effects and whether the differences are statistically significant.
- **Why it matters** Quantitative data are essential for evaluating the functional significance of the structural observations. Without specific values and statistical analysis, the claims about the importance of particular residues or domains are not fully supported.
- **Resolution test** Provide the KD,app values and Hill coefficients for all variants in a table or in the text, with appropriate statistical analysis. Report the specific activity values for all variants, with error bars and statistical comparisons to wild-type. Include the number of replicates and the statistical tests used.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 and its legend
- **Issue** The figure legend is not provided in the manuscript text. The description of the structures in the text refers to "Figure 1A and B" and "Figure 1C" but without the legend, it is difficult to understand what is shown in each panel.
- **Required correction** Provide the figure legends for all figures, either in the main text or as a separate section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** MD simulation results
- **Evidence pointer** Figure 5C and 5D
- **Issue** The distance distributions in Figure 5C are shown as histograms or density plots, but the number of data points and the method of calculation are not described. The energy values in Figure 5D are shown as averages without error bars.
- **Required correction** Describe how the distance distributions were calculated and how many frames were used. Add error bars or confidence intervals to the energy values and describe the statistical analysis used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Cryo-EM data processing
- **Evidence pointer** Materials and methods section "Cryo-EM image collection, processing, and analysis"
- **Issue** The manuscript states that 26,656 micrographs were collected, but does not provide details on the final number of particles used for each reconstruction, the resolution estimation method (gold-standard FSC is mentioned), or the local resolution variation. The manuscript mentions "Sampling Compensation Factor values" but does not explain what these are or how they were used.
- **Required correction** Provide the number of particles for each final reconstruction, a description of the resolution estimation and local resolution analysis, and an explanation of the Sampling Compensation Factor.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of sequence conservation
- **Affected element** Results section "Contacts made by multiple conserved Trm10 residues direct tRNA binding"; Supplementary Figure S4; Supplementary Table S1
- **Issue** The manuscript states that certain residues are "highly conserved" or "moderately conserved" but does not provide a quantitative definition of these categories. The sequence analysis methods are described only briefly.
- **Required correction** Define the conservation categories used in the analysis and provide the full sequence alignment or a clear description of how conservation was calculated.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Issue** The manuscript does not explicitly discuss the limitations of the study, such as the use of a non-physiological tRNA substrate (in vitro transcribed tRNAGly-GCC), the absence of post-transcriptional modifications on the tRNA, and the potential effects of the NM6 crosslink on the conformational states observed.
- **Required correction** Add a paragraph discussing the limitations of the study and how they might affect the interpretation of the results.

## Risk / unsupported claims
- The claim that the (Trm10)2–tRNA complex represents a functionally relevant intermediate in the methylation pathway is not fully supported by the data presented. The complex is a minor species, and the functional significance is inferred from MD simulations and crosslinking experiments that are not shown in the provided text.
- The assignment of the open conformation as a product-release state is speculative and not directly tested experimentally.
- The conclusion that Q118 selectively stabilizes G9 over A9 is based on MD simulations that lack statistical validation and are not corroborated by experimental mutagenesis data in this manuscript.
- The statement that the Trm10–tRNA contacts observed in the structures are "likely the major drivers of complex formation" is not directly tested, as the binding data for the variants are not quantitatively reported.
- The claim that the N-terminal domain (NTD) is "dispensable for tRNA binding" is based on qualitative activity data and is not supported by quantitative binding measurements for the truncated variants.