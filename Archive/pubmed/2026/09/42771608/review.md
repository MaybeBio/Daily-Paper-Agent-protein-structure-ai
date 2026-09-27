## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary material
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and interpretation of results as presented in the text
- **Shared manuscript claim summary** The authors report that 100 ns all-atom MD simulations of apo CypA and CypA-SangfA complex reveal that SangfA binding induces local rigidification of the β2-β3 loop (residues 100-102, 108-111) with a coil-to-β-strand transition, increased flexibility in distal loops, a 1.1-fold expansion of conformational ensemble, redistribution of PCA modes, and a binding free energy of -20.45 ± 3.07 kcal/mol, supporting a conformational selection mechanism of inhibition.
- **Visible evidence base** Text descriptions of results from RMSD, RMSF, SASA, hydrogen bonding, clustering, DSSP secondary structure, PCA, and LIE binding free energy analyses
- **Missing materials affecting confidence** Figures 1-15, Table 1, Table 2, Table 3, Table 4, Supplementary S1 Data, Supplementary S1 Video, and all equations (Equations 1-3 and the LIE equation) were not provided

## Reviewer
- **Overall assessment** This manuscript presents a molecular dynamics study of CypA in complex with SangfA, a topic of potential interest to the drug discovery community. The authors report a number of interesting observations, including a coil-to-β-strand transition in the β2-β3 loop and a redistribution of conformational dynamics upon ligand binding. However, the manuscript has several significant issues that prevent a positive assessment. The most serious concern is a direct internal contradiction: the abstract and conclusion state that Arg55 anchors the ligand via hydrogen bonds, while the results section explicitly states that Arg55 shows no contact (0% occupancy) and "remains uninvolved." This contradiction is not resolved anywhere in the text. Additionally, the reported binding free energy of -20.45 kcal/mol is inconsistent with the stated picomolar potency, and the LIE method with the parameters used is not appropriate for a ligand of this size. The manuscript also contains numerous typographical errors, unclear statements, and missing methodological details that undermine confidence in the results. The claim of conformational selection is not well supported by the data presented, as the authors themselves note that the holo state explores a broader conformational space, which is more consistent with an induced-fit or population-shift model that is not clearly distinguished from conformational selection. The manuscript requires major revisions and additional analyses before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers in computational drug discovery and structural biology, particularly those working on cyclophilin inhibitors for antiviral and anticancer applications. The study addresses a clinically relevant target and provides a dynamic perspective on inhibitor binding that could inform future drug design efforts. The methodological approach, combining MD simulation with essential dynamics and clustering analyses, may also be of interest to computational chemists studying protein-ligand interactions.

- **Major strengths**
  1. The study addresses a clinically relevant target (CypA) with a known potent inhibitor (SangfA), and the dynamic perspective offered by MD simulation is a valuable complement to static structural studies.
  2. The authors employ a range of complementary analytical techniques (RMSD, RMSF, SASA, hydrogen bonding, clustering, DSSP, PCA, LIE) to characterize the binding effects.
  3. The observation of a coil-to-β-strand transition in the β2-β3 loop is a specific, testable prediction that could guide future experimental validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The abstract states that the ligand forms a hydrogen-bond network "anchored by Arg55," and the conclusion repeats that the ligand is "anchored persistently by Arg55." However, the results section states that "ARG residues were never within the cutoff distance, averaging 16.67 nm away" and that "Arg55 remains uninvolved."
- **Evidence pointer** Abstract; Results section "The binding interface is characterized by a specific ionic interaction rather than distributed salt bridges"; Conclusion
- **Concern** This is a direct and unresolved contradiction. The abstract and conclusion claim Arg55 anchors the ligand via hydrogen bonds, while the results explicitly report that Arg55 has 0% contact occupancy and is never within the cutoff distance. The authors cannot have it both ways. Either the results are wrong, or the abstract and conclusion are wrong. This contradiction fundamentally undermines the reliability of the reported findings.
- **Why it matters** The role of Arg55 is a key mechanistic claim of the paper. Arg55 is a known catalytically important residue in CypA, and whether SangfA engages it or not has implications for the proposed mechanism of inhibition. A reader cannot trust the conclusions if the central results contradict them.
- **Resolution test** The authors must reconcile this contradiction. If Arg55 is not in contact, the abstract and conclusion must be corrected. If Arg55 is in contact, the results section must be corrected with appropriate evidence (e.g., distance plots, occupancy data). The corrected text must be internally consistent.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The computed binding free energy is reported as ΔG = -20.45 ± 3.07 kcal/mol, and the authors state this "accords with picomolar potency."
- **Evidence pointer** Abstract; Results section "Binding free energy analysis using LIE method"
- **Concern** A binding free energy of -20.45 kcal/mol corresponds to a dissociation constant (Kd) of approximately 10^-15 M (femtomolar), not picomolar (10^-12 M). The relationship ΔG = RT ln(Kd) at 300 K gives ΔG = -16.4 kcal/mol for 1 pM. The reported value is far too negative to be consistent with picomolar potency. Furthermore, the LIE method with α = 0.18 and β = 0.50 is calibrated for relatively small, drug-like molecules, and applying it to a large macrocyclic natural product like SangfA (molecular weight ~1000 Da) without validation is questionable. The authors also do not report the individual van der Waals and electrostatic energy components, nor do they provide any error estimate beyond the standard deviation.
- **Why it matters** The binding free energy is a central quantitative result of the paper. If it is inconsistent with the known experimental potency, the validity of the computational protocol is called into question. This affects the credibility of all other quantitative claims in the paper.
- **Resolution test** The authors must either (a) recalculate the binding free energy using a more appropriate method (e.g., MM-PBSA with a suitable force field, or a validated LIE parameter set for macrocycles), or (b) provide a clear explanation for why the LIE result deviates from the experimental potency. The reported value must be consistent with the known picomolar affinity of SangfA.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The methods section describes the simulation protocol, but several critical details are missing or unclear.
- **Evidence pointer** Materials and methods section "Molecular dynamics simulation"
- **Concern** The following details are not provided: (a) the specific force field parameters for SangfA (how were partial charges derived? what parameterization approach was used?); (b) the protonation states of ionizable residues; (c) the water model details beyond "simple point charge"; (d) the equilibration protocol specifics (number of steps, convergence criteria); (e) the temperature and pressure coupling details are given but the barostat coupling type is not specified; (f) the total number of atoms and system size; (g) the simulation box dimensions and shape; (h) the method for generating the initial complex structure (the authors state "as described before" but do not provide sufficient detail for reproduction). Additionally, the authors state the topology was generated using "GROMACS utilities" for the protein, but the specific GROMACS version is inconsistent (v2023 in the abstract, 5.1.4 in the methods).
- **Why it matters** Reproducibility is a cornerstone of computational research. Without complete methodological details, other researchers cannot replicate the simulations or assess the validity of the results. The version inconsistency is also concerning.
- **Resolution test** The authors must provide a complete description of the simulation setup, including all force field parameters, system composition, and a consistent software version. A detailed methods section or a link to a repository with input files and parameter files would be acceptable.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report a chi-square test (χ² = 17776.30, p < 0.001) for secondary structure comparison and t-tests for SASA differences, but no effect sizes or confidence intervals are reported for most comparisons.
- **Evidence pointer** Results section "Ligand binding induces a statistically significant reorganization of secondary structure"; Materials and methods section "Statistical analysis"
- **Concern** The chi-square test on a full 8-state secondary structure count table with such a large χ² value is almost certainly trivially significant given the large number of frames (8000+ per system). The authors do not report Cramér's V or any other effect size measure. Similarly, the t-test for SASA (78.42 vs 76.58 nm²) reports p < 0.001 but the difference is only 2.4%, and no effect size (Cohen's d) is reported despite the methods section claiming it would be computed. The biological significance of such small differences is unclear.
- **Why it matters** Statistical significance does not imply biological significance. Without effect sizes, the reader cannot judge whether the reported differences are meaningful. The large sample sizes in MD simulations make trivial differences statistically significant.
- **Resolution test** The authors must report effect sizes (e.g., Cramér's V for chi-square, Cohen's d for t-tests) and confidence intervals for all statistical comparisons. They should also discuss the biological relevance of the observed differences.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of results
- **Claim pointer** The authors claim that "SangfA acts via conformational selection, stabilizing a pre-existing CypA substate with augmented β-structure and broader dynamics."
- **Evidence pointer** Abstract; Discussion section
- **Concern** The data presented do not clearly distinguish conformational selection from induced fit. The authors show that the holo state has a broader conformational ensemble (more clusters, more distributed PCA modes), which is actually more consistent with induced fit or a population-shift model where the ligand stabilizes a higher-energy state. Conformational selection typically involves the ligand binding to a pre-existing conformation that is already populated in the apo state, which would predict a narrowing of the ensemble, not an expansion. The authors do not provide any evidence (e.g., apo-state pre-population of the bound conformation, transition path analysis) to support their claim.
- **Why it matters** The proposed mechanism is a central conclusion of the paper. If the data do not support the conformational selection model, the interpretation is incorrect and could mislead future drug design efforts.
- **Resolution test** The authors must either (a) provide additional analysis to support the conformational selection claim (e.g., showing that the bound conformation is populated in the apo ensemble), or (b) revise their interpretation to be consistent with the data, such as describing the mechanism as induced fit or a hybrid model.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "Arg55 remains uninvolved" in one sentence while also claiming the ligand is "anchored by Arg55" in the same paragraph. This is confusing and appears to be a typographical error.
- **Required correction** Clarify the role of Arg55. If Arg55 is not involved, remove the "anchored by Arg55" claim. If it is involved, correct the "remains uninvolved" statement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section "Binding free energy analysis using LIE method"
- **Evidence pointer** Results section
- **Issue** The text states "Lenard-Jones" and "Ciulombic" which are misspellings of "Lennard-Jones" and "Coulombic."
- **Required correction** Correct the spelling errors.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The sentence "Future NMR and X-ray crystallographic experiments can be conducted to validate the predicted conformational switch in the β2-β3 loop on the CypA-SangfA complex would be invaluable" is grammatically incorrect and unclear.
- **Required correction** Rewrite the sentence, e.g., "Future NMR and X-ray crystallographic experiments to validate the predicted conformational switch in the β2-β3 loop of the CypA-SangfA complex would be invaluable."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusion
- **Evidence pointer** Conclusion
- **Issue** The sentence "the increased CypA's conformational upun SangfA bonding" contains a typo ("upun" should be "upon") and is grammatically awkward.
- **Required correction** Rewrite, e.g., "the increased conformational dynamics of CypA upon SangfA binding."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Materials and methods section
- **Evidence pointer** Materials and methods section "Molecular dynamics simulation"
- **Issue** The abstract states GROMACS v2023 was used, while the methods section states GROMACS 5.1.4. This inconsistency must be resolved.
- **Required correction** Use a consistent GROMACS version throughout the manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "The catalytic site shows partial engagement while the canonical hydrophobic pocket is largely bypassed"
- **Evidence pointer** Results section
- **Issue** The text mentions "PHE102, GLU103, ALA104, LYS105, ALA106" as a cluster with 100% contact occupancy, but the relationship between these residues and the previously mentioned β2-β3 loop (residues 100-111) is not clearly explained. The text also refers to "PHE46 (β5, 100%)" and "LYS64, LYS66, THR63 (β7, 90-94%)" but the secondary structure assignments are not defined.
- **Required correction** Clarify the secondary structure assignments and the relationship between the identified clusters and the β2-β3 loop.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Ligand binding increases conformational diversity and reduces structural convergence"
- **Evidence pointer** Results section
- **Issue** The text states "the number of effective conformations, calculated as total frames divided by the average cluster size, increased by 124% upon ligand binding (Holo: 75.0; Apo: 66.0)." However, 75/66 = 1.136, which is a 13.6% increase, not 124%. The calculation method is also unclear.
- **Required correction** Clarify the calculation method and correct the percentage increase.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Ligand binding increases conformational diversity and reduces structural convergence"
- **Evidence pointer** Results section
- **Issue** The text reports "a 26% greater standard deviation (Holo: 374,970 nm; Apo: 298,466 nm)" for inter-cluster RMSD values. These values are implausibly large for RMSD in nanometers (374,970 nm = 374.97 μm). This appears to be a unit error or a misreporting of the data.
- **Required correction** Correct the units or the reported values.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Ligand binding induces subtle shifts in backbone dihedral distributions and secondary structure propensity"
- **Evidence pointer** Results section
- **Issue** The text states "The proportion of residues in the core α-helical region increased by 1.9 percentage points upon ligand binding. Concurrently, the population of the core β-strand region decreased by 2.1% points." These changes are small and the text does not report whether they are statistically significant.
- **Required correction** Report statistical significance and effect sizes for these comparisons.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and methods section "Calculation of linear interaction energy (LIE)"
- **Evidence pointer** Materials and methods section
- **Issue** The LIE equation is mentioned but not shown. The text states "the binding free energy is given by" but the equation is missing. The parameters α and β are stated, but the derivation of the equation and the specific implementation are not described.
- **Required correction** Include the full LIE equation and describe the implementation details.

## Risk / unsupported claims
- The claim that Arg55 anchors the ligand via hydrogen bonds (abstract, conclusion) is directly contradicted by the results section, which reports 0% contact occupancy for Arg55. This claim is unsupported and internally inconsistent.
- The claim that the binding free energy of -20.45 ± 3.07 kcal/mol "accords with picomolar potency" is quantitatively incorrect. The reported value corresponds to femtomolar affinity, not picomolar.
- The claim of a conformational selection mechanism is not well supported by the data. The observed broadening of the conformational ensemble in the holo state is more consistent with induced fit or population shift, and no direct evidence for conformational selection is provided.
- The claim that the β2-β3 loop undergoes a coil-to-β-strand transition is based on DSSP analysis, but the statistical significance and magnitude of this change are not fully reported. The text reports mean β-sheet occupancy values for clusters but does not provide a clear comparison with the apo state.
- The claim that "SangfA increases CypA's conformational entropy" is inferred from PCA and clustering results, but no direct entropy calculation is performed. The relationship between the observed changes and thermodynamic entropy is not established.
- The claim that "the ligand remains tightly bound" is based on a 100 ns simulation, which may not be sufficient to observe dissociation events for a high-affinity ligand. The absence of dissociation in 100 ns does not establish stable binding.
- The reported inter-cluster RMSD values (374,970 nm and 298,466 nm) are physically implausible and suggest a unit error or data misreporting. Any conclusions based on these values are unreliable.
- The claim that "the ligand induces a conformational adjustment that increases the protein's overall solvent exposure" is based on a 2.4% SASA increase. The biological significance of this small change is not established, and the text does not report which specific residues contribute to the change.
- The claim that "SangfA's effector domain leaves the catalytic machinery only partially occluded" is speculative and not directly supported by the data presented.