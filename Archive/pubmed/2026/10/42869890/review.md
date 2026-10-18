## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and figure legends.
- **Assessment boundary** Scientific content, technical soundness, and support of claims by the presented evidence. Editorial or stylistic issues are noted only where they affect clarity or interpretation.
- **Shared manuscript claim summary** The authors report cryoEM structures of full-length wild-type E. coli MscL in closed (DMPC and DOPC nanodiscs) and expanded (DSPC nanodiscs) conformations, and use PELDOR/DEER spectroscopy, HDX-MS, and MD simulations to propose a gating mechanism involving lipid-dependent stabilization of distinct states.
- **Visible evidence base** CryoEM density maps and models at 4.1 Å (closed) and 7.0 Å (expanded); PELDOR distance distributions for two spin-labelled sites under multiple lipid conditions; HDX-MS differential uptake data; MD simulations of bilayer and nanodisc systems; pore analysis and lipid contact calculations.
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; PDB validation reports not available; specific MD simulation parameters and convergence metrics not fully described; statistical details for HDX-MS comparisons not fully reported.

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing question in mechanosensation: the structural basis of MscL gating. The authors present the first full-length wild-type E. coli MscL structures in two distinct conformations, which is a significant technical achievement given the small size and dynamic nature of this channel. The combination of cryoEM, PELDOR, HDX-MS, and MD is commendable and provides complementary views of the conformational landscape. However, the expanded-state structure is at modest resolution (7.0 Å), and the authors' interpretation of the gating mechanism relies heavily on this map and on MD simulations that may be sensitive to force field and setup choices. The claim that DSPC lipids stabilize an expanded state is supported by PELDOR and cryoEM, but the mechanistic details, particularly the role of specific residues and the relationship to the fully open state, require further validation. The manuscript is well-written and will be of interest to the mechanosensation and membrane protein communities, but several technical concerns must be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers studying mechanosensitive channels, membrane protein structure and dynamics, lipid-protein interactions, and the application of integrative structural biology approaches. The work also has relevance for those interested in bacterial osmoregulation and the development of MscL-based biotechnological applications.

- **Major strengths** 1) First full-length wild-type E. coli MscL structures in closed and expanded states without stabilizing antibodies or mutations. 2) Integrative use of multiple biophysical techniques (cryoEM, PELDOR, HDX-MS, MD) to cross-validate findings. 3) Identification of a lipid environment (DSPC) that stabilizes an expanded state, providing a new tool for studying MscL gating. 4) The observation that the CTD remains intact during expansion, challenging earlier models of CTD dissociation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural interpretation
- **Claim pointer** The authors claim to have solved the structure of MscL in an "expanded/open-like state" at 7.0 Å resolution and use this to propose a gating mechanism.
- **Evidence pointer** Results section "The structure of EcMscL in an expanded/open-like state"; Figure 3; Supplementary Figure 9
- **Concern** At 7.0 Å resolution, the assignment of secondary structure and the precise positioning of side chains is not reliable. The authors state that residues 50–73 (the periplasmic loop) were omitted due to insufficient resolution, yet this region is critical for gating. The interpretation of TM helix tilts (23° and 35°) and the claim that the CTD moves as a rigid body depend on accurate model building at this resolution. The authors should provide a detailed validation of the model, including map-to-model fit statistics, and discuss the limitations of interpreting conformational changes at this resolution. It is also unclear how the model was built and refined at 7.0 Å, and whether the observed differences between closed and expanded states are statistically significant given the resolution.
- **Why it matters** The central claim of the paper is the structural basis of gating. If the expanded-state model is not reliable at 7.0 Å, the proposed mechanism is not established. The resolution is insufficient to support detailed claims about helix tilts and specific residue interactions.
- **Resolution test** Provide a detailed validation report for the 7.0 Å map, including FSC curves, local resolution estimates, and model-to-map correlation. Demonstrate that the observed conformational differences are robust to model building choices (e.g., by building alternative models and showing they converge). If possible, obtain a higher-resolution structure of the expanded state, or provide additional experimental evidence (e.g., cross-linking, FRET) that supports the proposed conformational changes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for the gating mechanism claim
- **Claim pointer** The authors propose that DSPC lipids stabilize an expanded state by a "lipid-moves-first" mechanism, where lipid depletion from hydrophobic pockets drives channel expansion.
- **Evidence pointer** Results sections "Protein–lipid interactions and critical residues in EcMscL gating" and "Bilayer thickness and interdigitation in EcMscL gating"; Figures 4 and 5
- **Concern** The MD simulations are used to support the mechanism, but the setup and analysis have potential issues. The simulations are relatively short (400 ns) and may not sample the relevant conformational transitions. The use of a single lipid composition (POPE/POPG/cardiolipin) for the closed state and DSPC for the expanded state confounds lipid composition with conformational state. The authors should clarify whether the observed differences in lipid contacts and bilayer properties are due to the protein conformation or the lipid composition itself. Additionally, the claim that "temperature and the associated changes in lipid phase behaviour strongly influence EcMscL hydration" is based on simulations at 30 °C and 87 °C, but the experimental cryoEM and PELDOR data were collected at different temperatures. The link between the simulation results and the experimental observations needs to be made more explicit.
- **Why it matters** The proposed mechanism depends on the MD simulations to provide a causal link between lipid properties and channel conformation. If the simulations are not set up or analyzed appropriately, the mechanism is not supported.
- **Resolution test** Perform additional simulations with matched lipid compositions (e.g., DMPC vs DSPC with the same protein conformation) to isolate the effect of lipid composition. Extend simulation times and provide convergence metrics. Clearly state the temperature of the simulations and how they relate to the experimental conditions. If possible, perform experimental validation of the proposed lipid-protein interactions (e.g., mutagenesis of key residues followed by functional assays).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of evidence for the expanded state
- **Claim pointer** The authors state that "open-like states are present" in DSPC based on PELDOR data, and that the cryoEM structure represents an expanded state.
- **Evidence pointer** Results section "Monitoring the EcMscL conformational ensemble in membranes by PELDOR"; Figure 2; Supplementary Figures 5–8
- **Concern** The PELDOR data show broad distance distributions, indicating conformational heterogeneity. The authors interpret this as a shift away from the closed state, but the data do not clearly demonstrate that a specific expanded state is populated. The cryoEM structure in DSPC was solved from a subset of particles (17,211) that may represent only a minor population. The authors should provide a quantitative analysis of the PELDOR data, including the fraction of expanded states, and discuss how the cryoEM structure relates to the ensemble observed by PELDOR. It is also unclear whether the expanded state observed in DSPC is the same as the open state observed in electrophysiology, or a sub-conducting state.
- **Why it matters** The claim that the structure represents an "open-like state" is central to the paper. If the expanded state is a minor population or a sub-conducting state, the conclusions about the gating mechanism may need to be revised.
- **Resolution test** Provide a quantitative decomposition of the PELDOR distance distributions into closed and expanded components, with uncertainties. Compare the pore dimensions of the expanded state to those estimated from electrophysiology for the open and sub-conducting states. Discuss the relationship between the cryoEM structure and the ensemble observed by PELDOR.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** MD simulation setup
- **Evidence pointer** Methods section "Atomistic MD simulations"
- **Issue** The description of the MD simulations is brief. The authors state that "CHARMM-GUI's membrane builder tool was used to build the nanodisc and bilayer systems" but do not provide details on the number of lipids, water molecules, ions, or the equilibration protocol. The force field and water model are mentioned, but not the specific versions or parameters.
- **Required correction** Provide a more detailed description of the simulation setup, including system composition, equilibration protocol, and production run lengths. Include a table summarizing all simulated systems and their key parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** HDX-MS analysis
- **Evidence pointer** Results section "Hydrogen-deuterium exchange mass spectrometry"; Figure 3h
- **Issue** The HDX-MS data are presented as a single time point (30 s) in Figure 3h, with other time points mentioned in the text but not shown. The statistical analysis is described as using a "98% confidence limit, p value < 0.05", but the number of replicates and the method for multiple testing correction are not stated.
- **Required correction** Show data for all time points, either in the main figure or supplementary material. Provide details on the number of biological and technical replicates, and the statistical test used. Clarify whether the confidence limit is a p-value threshold or a confidence interval.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of CTD movement
- **Affected element** Discussion of CTD position
- **Evidence pointer** Results section "The structure of EcMscL in an expanded/open-like state"; Figure 3e
- **Issue** The authors state that the CTD moves 5 Å closer to the membrane during expansion, but it is unclear whether this is a significant change given the resolution of the expanded-state map. The authors also state that the CTD does not dissociate, but this is based on the cryoEM structure, which may not capture the full ensemble.
- **Required correction** Discuss the uncertainty in the CTD position given the resolution of the expanded-state map. If possible, provide additional evidence (e.g., from HDX-MS or MD) that supports the CTD movement and lack of dissociation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The density map in Figure 1a appears to be shown at a single contour level, and it is unclear how well the model fits the density. The authors should show the map at multiple contour levels and provide a figure showing the fit of the model to the density for key regions.
- **Required correction** Add panels showing the map-model fit for representative regions, and indicate the contour level used for display.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility of data
- **Affected element** Data availability
- **Evidence pointer** Methods section "Data availability" (not explicitly provided in the manuscript text)
- **Issue** The manuscript does not include a Data Availability statement. Given the importance of the cryoEM maps and models, these should be deposited in a public repository (e.g., EMDB, PDB) and the accession numbers provided.
- **Required correction** Add a Data Availability statement with accession numbers for the cryoEM maps and models, and for the HDX-MS data if applicable.

## Risk / unsupported claims
- The claim that the expanded state represents an "open-like state" is not fully supported by the data, as the resolution is limited and the relationship to the electrophysiologically defined open state is not established.
- The proposed "lipid-moves-first" mechanism is inferred from MD simulations that may not be fully converged and that confound lipid composition with protein conformation.
- The statement that "the CTD does not dissociate during channel expansion" is based on a single cryoEM structure and may not reflect the full conformational ensemble.
- The claim that DSPC lipids "compensate for the bilayer thickness mismatch by locally thinning the bilayer" is based on MD simulations and requires experimental validation.
- The PELDOR data are interpreted as showing a shift away from the closed state, but the quantitative composition of the ensemble is not provided.