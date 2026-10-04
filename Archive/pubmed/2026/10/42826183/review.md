## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary materials description
- **Assessment boundary** Scientific content, technical validity, structural and computational evidence, claims versus data support, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors report cryo-EM structures and MD simulations of KCNQ1 potassium channels bound to the inhibitor UCL2077 in two activation states (intermediate E1R/R2E and activated WT). They propose that UCL2077 binds in a peripheral pocket between S5-S6 of one protomer and S6 of an adjacent protomer, breaking fourfold symmetry with two diagonally opposed ligands, and that binding induces S6 conformational changes leading to pore collapse and dehydration. They further propose kinetic and structural bases for state-dependent selectivity favoring the intermediate state.
- **Visible evidence base** Cryo-EM reconstructions at 3.95 Å (intermediate) and 3.81 Å (activated), MD simulations (multiple systems, 500 ns to 1 μs), electrophysiology (patch clamp, n = 3), mutagenesis data, docking calculations, pore radius analyses
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided in the submitted text; specific IC50 values for the activated state not stated numerically; no negative-stain or alternative biochemical validation; no binding affinity measurements beyond single-concentration electrophysiology; no raw MD trajectory statistics beyond RMSD; no statistical analysis details for electrophysiology beyond SEM

## Reviewer

- **Overall assessment** This manuscript presents a substantial advance in understanding state-dependent inhibition of KCNQ1 channels. The structural data are novel and the proposed mechanism is plausible and well-supported by the combination of cryo-EM, MD, and functional validation. The claim of asymmetric ligand binding breaking fourfold symmetry is intriguing and potentially important. However, several technical concerns regarding resolution limitations, the interpretation of weak density, and the quantitative basis for state-dependent selectivity require careful attention before the case is fully established.

- **Who would be interested in the results, and why** Structural biologists studying ion channels, pharmacologists interested in state-dependent drug action, cardiac electrophysiologists focused on arrhythmia mechanisms, and drug discovery groups targeting KCNQ channels for atrial fibrillation and short QT syndrome. The work provides the first inhibitor-bound KCNQ1 structures and a new paradigm for allosteric pore collapse distinct from direct pore occlusion.

- **Major strengths** 1) First cryo-EM structures of KCNQ1 with an inhibitor bound, filling a significant gap in the field. 2) The asymmetric binding mode with two diagonally opposed ligands is unexpected and mechanistically interesting. 3) The combination of structural, computational, and functional data provides multi-pronged support for the proposed mechanism. 4) The comparison between intermediate and activated states offers a structural rationale for state-dependent pharmacology. 5) The identification of a peripheral binding site rather than a pore-occluding site is novel for KCNQ channels.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity of structural interpretation
- **Claim pointer** The authors claim that UCL2077 binds in two diagonally opposed protomers and that this asymmetric binding is a genuine feature of the complex, not an artifact of reconstruction or occupancy variation.
- **Evidence pointer** Results section "Binding of UCL2077 in the xE1R/R2E intermediate state breaks fourfold symmetry"; Figures 2 and 3; fig. S1
- **Concern** The intermediate-state reconstruction was obtained at 3.95 Å with C2 symmetry imposed. At this resolution, distinguishing a genuine asymmetric ligand distribution from partial occupancy or reconstruction artifacts is challenging. The authors state that C1 reconstructions revealed a binding mode consistent with twofold symmetry, but the details of how this was assessed are not provided in the main text. The absence of quantitative occupancy refinement or validation of the asymmetric binding model against a symmetric alternative is a significant gap. For the activated state at 3.81 Å, the ligand density for the pyridyl group was absent, which weakens the claim of a well-defined binding mode in this state.
- **Why it matters** The central claim of the paper is the asymmetric binding mode and its mechanistic consequences. If the asymmetry is an artifact of limited resolution or partial occupancy, the proposed mechanism of state-dependent inhibition would require substantial revision. The absence of the pyridyl group density in the activated state further complicates interpretation of state-dependent differences.
- **Resolution test** Provide quantitative occupancy refinement for the ligand in each protomer, compare C1 and C2 models with appropriate statistical measures (e.g., Fourier shell correlation, model-map correlation), and demonstrate that the asymmetric binding model is statistically preferred over a symmetric alternative. For the activated state, either improve the local resolution at the ligand site or temper claims about the binding mode in this state.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for state-dependent selectivity
- **Claim pointer** The authors claim that UCL2077 displays higher potency for the intermediate state over the activated state and that this is explained by structural and kinetic differences revealed in their study.
- **Evidence pointer** Abstract; Introduction; Results section "Structural and kinetic determinants of intermediate-state selectivity"; Figure 8
- **Concern** The electrophysiology data presented show 57 ± 7% inhibition at 10 pM for the intermediate state construct, but no comparable data are shown for the activated state in this manuscript. The claim of state-dependent selectivity relies on previously published work (reference 19) rather than on data presented here. The MD simulations provide kinetic insight into xF330 flipping frequencies, but the connection between these simulations and the macroscopic potency difference is not quantitatively established. The statement that the intermediate state is a "better target" is supported by occupancy arguments, but no free energy calculations or binding affinity estimates are provided.
- **Why it matters** The title and abstract emphasize state-dependent inhibition as a central finding. Without direct functional comparison between states in this study, the structural data alone cannot establish the mechanistic basis for differential potency. The MD simulations are suggestive but do not provide quantitative energetic or kinetic parameters that would explain the reported potency difference.
- **Resolution test** Include electrophysiological comparison of UCL2077 potency between intermediate and activated constructs under identical conditions, or provide binding free energy calculations from MD that quantitatively reproduce the selectivity. At minimum, clearly separate previously published functional data from new data presented in this study.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation of pore collapse
- **Claim pointer** The authors claim that UCL2077 binding induces S6 conformational changes that collapse the pore and dehydrate the permeation pathway, and that this represents the inhibitory mechanism.
- **Evidence pointer** Results section "The binding of UCL2077 in the intermediate state induces PD conformational collapse"; Figures 5 and 7
- **Concern** The comparison between native and UCL2077-bound structures is complicated by the fact that the native intermediate structure was solved in a different condition (without ligand) and the UCL2077-bound structure required C2 symmetry imposition. The observed differences in pore radius and S6 conformation could reflect intrinsic conformational variability rather than ligand-induced changes. The MD simulations show that the pore narrows over time, but the simulations were started from the ligand-bound cryo-EM structure, which may bias the results. The claim of dehydration is based on water occupancy analysis, but the details of this analysis are not fully described.
- **Why it matters** The proposed allosteric mechanism of pore collapse is a key conceptual advance. If the conformational differences between native and ligand-bound states are within the range of intrinsic dynamics, the causal role of UCL2077 in inducing collapse would be weakened. The directionality of the effect (ligand binding causes collapse, rather than collapse enabling ligand binding) is not definitively established.
- **Resolution test** Perform MD simulations starting from the native structure with UCL207H7 docked into the predicted binding site to test whether collapse occurs spontaneously. Provide quantitative comparison of conformational ensembles (e.g., principal component analysis) between native and ligand-bound states to demonstrate that the differences exceed intrinsic thermal fluctuations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed mechanism
- **Claim pointer** The authors suggest that the mechanism of UCL2077 inhibition may be applicable to other KCNQ family channels and provide structural templates for drug discovery.
- **Evidence pointer** Discussion section "UCL2077 binding" and "VSD-PD coupling"
- **Concern** The selectivity of UCL2077 for KCNQ1 over other KCNQ subtypes is stated but not structurally explained in detail. The comparison with KCNQ2 and KCNQ4 structures is qualitative, and the claim that differences in the S1-S2 region and S6 flexibility explain subtype selectivity is not supported by quantitative analysis. The suggestion that this mechanism could inform drug discovery for gain-of-function KCNQ1 pathologies is reasonable but speculative without demonstration that the identified binding site is druggable in a therapeutic context.
- **Why it matters** The broader implications of the work depend on the generalizability of the mechanism. If the proposed mechanism is specific to the particular constructs and conditions used here, the translational relevance would be more limited.
- **Resolution test** Provide sequence and structural alignment of the binding site across KCNQ subtypes with quantitative assessment of how the identified differences would affect ligand binding. If possible, test UCL2077 analogs or other ligands in the same structural system to demonstrate the utility of the template.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Electrophysiology data
- **Evidence pointer** Results section "Binding of UCL2077 in the xE1R/R2E intermediate state breaks fourfold symmetry"; Figure 1E
- **Issue** The electrophysiology data are reported as mean ± SEM with n = 3, but no statistical test is described for comparing inhibition between conditions or constructs. The variability across cells is not shown.
- **Required correction** Provide individual data points, specify the statistical test used, and report effect sizes or confidence intervals.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** MD simulation details
- **Evidence pointer** Materials and Methods section "MD simulations methods"
- **Issue** The description of the MD simulation protocol is incomplete. The force field parameters for UCL2077 are mentioned as obtained from CGenFF, but the charge derivation method, the specific CGenFF version, and the validation of the ligand parameters are not described. The temperature and pressure coupling schemes are not specified.
- **Required correction** Provide complete simulation parameters including thermostat/barostat algorithms, coupling constants, and any ligand parameter validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Structural figures
- **Evidence pointer** Figures 2, 3, 5, 7
- **Issue** The figures are described in the text but not shown in the provided manuscript. The quality of density maps, the clarity of the ligand binding site, and the visualization of conformational changes cannot be assessed.
- **Required correction** Ensure figures are included in the final submission with clear labels, appropriate contour levels for density maps, and scale bars where relevant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** "State-dependent" terminology
- **Evidence pointer** Throughout
- **Issue** The term "state-dependent" is used to describe both the differential potency between intermediate and activated states and the conformational changes induced by ligand binding. These are related but distinct concepts that could be confused.
- **Required correction** Clarify whether "state-dependent" refers to preferential binding to a particular conformational state or to state-specific effects of binding, and use consistent terminology throughout.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of alternative mechanisms
- **Evidence pointer** Discussion section
- **Issue** The discussion does not adequately address alternative interpretations, such as the possibility that UCL2077 acts through allosteric modulation of voltage sensor movement rather than direct pore collapse, or that the observed conformational changes are secondary to detergent effects.
- **Required correction** Add a paragraph discussing alternative mechanisms and how the current data distinguish between them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** MD trajectories
- **Evidence pointer** Data availability statement
- **Issue** The data availability statement indicates that MD simulation data are available at a Zenodo link, but the specific contents and format are not described. The cryo-EM maps and models are deposited in the PDB and EMDB, but the associated validation reports are not mentioned.
- **Required correction** Provide a clear description of what is included in the Zenodo deposition and reference the EMDB accession numbers for the maps.

## Risk / unsupported claims
- The claim that UCL2077 binding "drives" conformational changes in S6 implies causality, but the structural data are static snapshots and cannot establish directionality without time-resolved experiments or perturbation studies.
- The statement that the intermediate state is a "better target" for UCL2077 is supported by occupancy arguments from MD but lacks quantitative binding free energy calculations.
- The claim that the observed mechanism "may be applicable to neuronal KCNQ family channels" is speculative and not directly supported by data presented in this study.
- The suggestion that the structures provide "structural templates for drug discovery" is reasonable but not validated by any medicinal chemistry or ligand design efforts.
- The functional significance of the asymmetric binding mode (two versus four ligands) is not experimentally tested; the authors do not address whether partial occupancy would produce partial inhibition or whether the asymmetry is required for the inhibitory effect.
- The statement that the intermediate state "appears to show greater PD flexibility" is inferred from a single structure and MD simulations, but no quantitative comparison of flexibility (e.g., B-factors, ensemble analysis) is provided.