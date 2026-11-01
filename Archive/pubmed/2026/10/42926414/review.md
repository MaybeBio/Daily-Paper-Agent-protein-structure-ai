## Review setup
- **Input scope** Full manuscript text (abstract, introduction, experimental section, results and discussion, conclusions, acknowledgments) as provided in the review request. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific content, technical soundness, and internal consistency of the reported claims based solely on the supplied manuscript text. No external literature verification or independent data analysis performed.
- **Shared manuscript claim summary** The authors report that graft-through polymerization of trpzip2-derived peptide monomers into brush polymers disrupts the β-hairpin fold, as evidenced by loss of CD exciton signal, IR spectral changes, and globular collapse observed by SAXS. Molecular dynamics simulations of a 15-mer polymer system support a thermodynamic shift away from the native folded state, attributed to steric constraints imposed by polymer backbone collapse.
- **Visible evidence base** Main text figures (Figures 1–8) and tables (Table 1) are referenced but not provided in the supplied material. Experimental methods for CD, IR, and MD simulations are described. Supporting information is referenced extensively but not available for review.
- **Missing materials affecting confidence** All figures, tables, and supporting information (including synthetic procedures, characterization data, SAXS fits, and simulation details) are absent from the supplied material. This substantially limits the ability to verify quantitative claims, assess data quality, or evaluate the robustness of the simulation analyses.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in the design of protein-like polymer architectures: how does dense grafting onto a polymer backbone affect the folding of β-hairpin peptide side chains? The combination of experimental spectroscopy (CD, IR, SAXS) with extensive molecular dynamics simulations is a strong approach, and the central finding, that polymerization disrupts the trpzip2 fold, is clearly stated and mechanistically plausible. However, the absence of all primary data (figures, tables, supporting information) in the supplied material prevents a full assessment of the evidence quality. Several claims, particularly regarding the quantitative extent of fold disruption and the interpretation of the simulation results, require closer scrutiny. The comparison to prior work on α-helical brush polymers is interesting but would benefit from more explicit discussion of the structural differences that lead to opposite outcomes.
- **Who would be interested in the results, and why** Researchers in the fields of peptide-polymer conjugates, protein mimetics, biomaterials, and drug delivery would find these results relevant. The work provides design rules for brush polymer systems where controlling peptide secondary structure is critical, and the finding that β-sheet formation is suppressed could inform the development of therapeutic candidates targeting protein aggregation. The methodological combination of experiment and simulation may also interest computational chemists studying confined peptide folding.
- **Major Strengths**
  1. The research question is well-defined and of clear significance to the peptide-polymer community.
  2. The multi-technique experimental approach (CD, IR, SAXS) provides complementary views of the structural changes.
  3. The use of extensive MD simulations (1.736 ms for monomer, 100 μs for polymer) with MSM analysis is ambitious and appropriate for probing conformational landscapes.
  4. The comparison between monomeric and polymer-conjugated forms allows direct attribution of observed changes to the polymer context.
  5. The manuscript is generally well-written and logically organized, with a clear narrative from experimental observation to mechanistic explanation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and reproducibility
  - **Claim pointer** The authors claim that "a loss of the β-hairpin structure of the monomer is observed regardless of polymer composition" and that this is quantified by "approximately 40% of the original beta monomer intensity" in CD.
  - **Evidence pointer** Figure 2, Figures S23–S26, location not provided
  - **Concern** The central experimental claim rests entirely on CD and IR data presented in figures that are not available in the supplied material. The quantitative statement of "approximately 40%" intensity loss cannot be verified without the actual spectra and the method used to calculate this value (e.g., molar ellipticity normalization, baseline correction). Furthermore, the claim that this loss is "regardless of polymer composition" requires comparison across all polymer variants, which is not possible without the figures.
  - **Why it matters** The entire conclusion of the paper, that polymerization disrupts β-hairpin folding, depends on the reliability and correct interpretation of these spectroscopic data. Without access to the primary spectra and the analysis details, the core claim is not independently verifiable.
  - **Resolution test** Provide the CD spectra for all monomers and polymers with clear labeling of the trpzip2 content normalization. Specify the exact method for quantifying the intensity loss (e.g., comparison at a specific wavelength, integration of the exciton band). Show that the observed changes are not due to concentration errors, light scattering from aggregated polymer, or other artifacts.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Simulation methodology and interpretation
  - **Claim pointer** The authors state that "polymer conjugation substantially alters the folding behavior, favoring extended or misfolded states over the native fold" and that this "arises from the collapse of the polymer into a compact globular architecture, which creates steric crowding and geometric constraints."
  - **Evidence pointer** Figures 6–8, Supporting Information Section 7, location not provided
  - **Concern** The simulation results are presented as a key mechanistic explanation, but critical details are missing. The force field parameters for the non-natural norbornene linker and the polymer backbone are not described in the main text. The construction of the 15-mer polymer system, including the initial configuration, the treatment of counterions, and the equilibration protocol, is not specified. The MSM construction relies on hyperparameters (tICA lag time, number of clusters, etc.) that are only referenced to the Supporting Information. Without these details, the validity of the free energy landscapes and the claim of a "thermodynamic shift" cannot be assessed.
  - **Why it matters** The simulation component is presented as providing "a mechanistic explanation for the experimentally observed loss of β-hairpin character." If the simulation methodology is flawed or the system setup is unrealistic, the mechanistic interpretation could be incorrect, undermining the paper's main contribution.
  - **Resolution test** Provide full details of the force field parameterization for the non-standard residues, the polymer construction protocol, and the MSM hyperparameters in the main text or a clearly accessible Supporting Information. Show convergence of the free energy estimates (e.g., via Chapman-Kolmogorov tests, which are referenced but not shown). Demonstrate that the observed shift in conformational preference is robust to changes in simulation length and analysis parameters.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of SAXS data
  - **Claim pointer** The authors state that "SAXS data corroborate globular collapse in aqueous solution" and that the polymers adopt "compact globular objects" based on Guinier-Porod fits with dimension variable s ≤ 0.26 and Porod exponents > 3.
  - **Evidence pointer** Figure 5, Tables S1–S4, Figures S38–S45, location not provided
  - **Concern** The SAXS analysis is used to support the claim of globular collapse, which is then linked to the steric constraints that disrupt β-hairpin folding. However, the interpretation of the SAXS data is not straightforward. The Guinier-Porod model is empirical, and a dimension variable s of 0.26 could indicate a range of shapes, not necessarily a compact sphere. The Porod exponent > 3 suggests a smooth surface, but this could also be consistent with aggregated or partially folded states. The authors also mention fits to a flexible cylinder model, which seems contradictory to a compact globule. The relationship between the SAXS-derived radius of gyration (2.4–3.0 nm) and the expected size of a collapsed 15-mer brush polymer is not discussed in detail.
  - **Why it matters** The SAXS data are used to support the physical picture of a collapsed polymer that constrains the peptide side chains. If the SAXS interpretation is ambiguous, the link between polymer conformation and peptide folding disruption is weakened.
  - **Resolution test** Provide the full SAXS profiles with fits overlaid, and discuss the relative quality of the Guinier-Porod versus flexible cylinder fits. Justify the choice of model and explain what the fitted parameters physically mean in the context of a brush polymer. Consider alternative interpretations, such as partially collapsed or anisotropic structures, and explain why they are excluded.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison to prior work and generalizability
  - **Claim pointer** The authors state that "in the case of helicity, it is hypothesized that the locally hydrophobic environment of the polymer promotes folding... in contrast to the destabilization observed in the case of trpzip2."
  - **Evidence pointer** Reference 12, Discussion section, location not provided
  - **Concern** The comparison to α-helical brush polymers is used to highlight the specificity of the observed β-hairpin destabilization. However, the structural and physicochemical differences between α-helices and β-hairpins are not systematically discussed. For example, α-helices are stabilized primarily by local backbone hydrogen bonds (i+4 to i), whereas β-hairpins require long-range contacts between distant backbone segments. The steric constraints imposed by a collapsed polymer would be expected to affect these two motifs differently. A more detailed comparison would strengthen the claim that the observed effect is specific to β-sheet-like folding and not a general feature of peptide brushes.
  - **Why it matters** The paper's broader significance lies in providing design rules for peptide brush polymers. If the comparison to α-helices is superficial, the rules may be incomplete or misleading.
  - **Resolution test** Expand the discussion to explicitly compare the hydrogen bonding patterns, side-chain packing, and conformational entropy of α-helices versus β-hairpins in the context of a dense brush. Discuss whether the observed destabilization is specific to the trpzip2 sequence or likely to apply to other β-hairpin and β-sheet systems.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of experimental details
  - **Affected element** CD spectroscopy methods
  - **Evidence pointer** Experimental Section, location not provided
  - **Issue** The CD methods state that samples were at "approximately 100 μM with respect to peptide monomer concentration" and that concentration was corrected using extinction coefficients at 205 nm. However, the pathlength, the exact temperature for the wavelength scans, and the number of accumulations are not specified. The variable temperature scans monitored ellipticity at 229 nm, but the rationale for this specific wavelength is not given.
  - **Required correction** Specify the pathlength, temperature, and accumulation parameters for the CD measurements. Justify the choice of 229 nm for monitoring thermal denaturation, or state that this wavelength corresponds to the exciton band maximum.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Nomenclature consistency
  - **Affected element** Polymer naming conventions
  - **Evidence pointer** Results and Discussion, Table 1, location not provided
  - **Issue** The polymer names (e.g., beta5, beta15, beta30, beta45) are used to denote degree of polymerization, but the naming convention is not explicitly defined. For copolymers, the naming (e.g., ran15beta15, OEG30-r-beta15) is not intuitive, and the meaning of the numbers and the "r" designation is not explained in the main text.
  - **Required correction** Define the naming convention clearly in the text or in a table footnote. For example, state that the number indicates the degree of polymerization and that "r" denotes a random copolymer.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Conclusions section
  - **Evidence pointer** Conclusions, location not provided
  - **Issue** The authors suggest that the observed inhibition of β-sheet character "may thus be useful to impede the progression of harmful protein folding, for example in tau-derived fibrillization processes." This is a speculative claim that is not supported by any data in the manuscript. While such speculation is acceptable in a conclusions section, it should be clearly framed as a hypothesis.
  - **Required correction** Soften the language to indicate that this is a potential future application that would require dedicated studies, rather than a direct implication of the current results.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Simulation analyses
  - **Evidence pointer** Figures 6–8, location not provided
  - **Issue** The free energy landscapes are presented as qualitative surfaces, but no error estimates or confidence intervals are provided. Given the stochastic nature of MD simulations, it is important to know whether the observed differences between monomer and polymer systems are statistically significant.
  - **Required correction** Provide error estimates for the free energy surfaces (e.g., via block averaging or bootstrapping) or state that the differences are robust across independent replicates.

## Risk / unsupported claims
- The quantitative claim of "approximately 40%" CD intensity loss is unverifiable without the actual spectra and analysis details.
- The claim that fold disruption occurs "regardless of polymer composition" is not assessable without the full dataset for all polymer variants.
- The mechanistic conclusion that steric constraints from polymer collapse cause the thermodynamic shift is plausible but depends on simulation details that are not fully provided.
- The comparison to α-helical brush polymers (Reference 12) is made without sufficient discussion of the structural differences that would explain the opposite outcomes.
- The potential application to tau-derived fibrillization is speculative and not supported by data in this manuscript.
- The claim of "excellent pharmacokinetic and pharmacodynamic properties" for PLPs in the introduction is referenced but not substantiated within this work.