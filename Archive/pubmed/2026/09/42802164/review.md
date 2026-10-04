## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, interpretation of cryoEM and MD data, and support for stated conclusions
- **Shared manuscript claim summary** The authors present a 1.9 Å cryoEM structure of HPV16 quasivirus bound to heparin, identify the heparin-binding site at the interface between pentavalent and hexavalent capsomers, describe local conformational changes and reduced capsid flexibility upon heparin binding, and use MD simulations to support the electrostatic basis of heparin recognition and the presence of inter-capsomer N-terminal hydrogen bonds contributing to capsid stability.
- **Visible evidence base** Main text figures 1-4, supplementary figures 1-16, supplementary table 1, table 1 (data collection and refinement statistics)
- **Missing materials affecting confidence** Electron density maps and model coordinates not deposited or accessible for independent verification; no validation metrics for the heparin fit; no FSC curve figures shown; no local resolution maps displayed; no PDB validation report; no details on MD simulation convergence beyond JSD values; no information on how heparin occupancy was quantified

## Reviewer
- **Overall assessment** This manuscript presents a technically impressive cryoEM structure of HPV16 quasivirus bound to heparin at 1.9 Å resolution, representing a significant improvement over the previous 4.3 Å structure. The identification of the heparin-binding site and the integration of MD simulations to support the experimental findings are commendable. However, several concerns regarding the interpretation of the heparin density, the statistical robustness of the flexibility analysis, and the strength of the MD support for specific claims need to be addressed. The manuscript is potentially suitable for publication in Nature Communications if these concerns are adequately resolved.

- **Who would be interested in the results, and why** Structural virologists studying papillomavirus entry mechanisms, researchers investigating virus-glycan interactions, computational biologists using MD to interpret cryoEM data, and those interested in the molecular basis of HPV infection and potential therapeutic targeting of the heparin-binding site.

- **Major strengths** The 1.9 Å resolution represents a substantial technical achievement for a large icosahedral virus-glycan complex. The use of subparticle extraction and refinement to overcome capsid flexibility is well-executed. The integration of MD simulations to provide mechanistic insight into the electrostatic basis of heparin binding is innovative. The identification of specific residues involved in heparin recognition provides a foundation for future mutagenesis studies. The observation of N-terminal hydrogen bonds between capsomers offers new insight into capsid stability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of heparin model
- **Claim pointer** The authors state that "a model for heparin was fit into the density, but couldn't be confidently built into the density" and identify specific residues interacting with heparin
- **Evidence pointer** Results section "Heparin was visualized bound to the HPV capsid", Figure 3, Supplementary Figure 8
- **Concern** The authors acknowledge that heparin could not be confidently built into the density, yet they identify specific contact residues and describe the binding site in detail. The heparin density is described as "amorphous but continuous and distinct from L1 density." This raises the question of how the authors can confidently assign specific residue contacts when the ligand model itself is uncertain. The manuscript lacks a quantitative assessment of the confidence in the heparin placement, such as correlation coefficients, occupancy refinement, or alternative ligand placements.
- **Why it matters** The central claim of the manuscript is the identification of the heparin-binding site. If the heparin model is not confidently built, the specific residue assignments become speculative, undermining the primary conclusion and any downstream applications such as mutagenesis or drug design.
- **Resolution test** Provide a quantitative measure of confidence in the heparin placement, such as real-space correlation coefficients for the heparin density, comparison of alternative heparin conformations or chain lengths, and a clear description of how the heparin model was generated and validated. If the heparin density is truly ambiguous, the authors should temper their claims about specific contact residues.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness of flexibility analysis
- **Claim pointer** The authors claim "reduced flexibility in all arm connections of the HPV-heparin complex compared to HPV alone" based on standard deviation differences of 2% versus 4%
- **Evidence pointer** Results section "The HPV capsid is inherently flexible due to capsomer movement conferred by arm connections", Supplementary Figures 6-7
- **Concern** The flexibility analysis compares standard deviations of capsomer positions between the HPV-heparin complex and HPV alone. The authors report average standard deviations of 2% and 4% but do not provide error bars, confidence intervals, or statistical tests to determine whether this difference is significant. The analysis appears to be based on a single structure each, and the number of particles contributing to each measurement is not clearly stated. Additionally, the comparison may be confounded by the different resolutions of the two maps.
- **Why it matters** The claim of reduced flexibility upon heparin binding is a key finding that supports the model of heparin stabilizing the capsid. Without statistical rigor, this conclusion is not firmly established and could be an artifact of differences in data quality or processing.
- **Resolution test** Provide a statistical analysis of the flexibility measurements, including the number of particles analyzed, bootstrapped confidence intervals, or a permutation test to establish significance. If the comparison is not statistically robust, the claim should be softened or additional data should be collected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** MD simulation support for hydrogen bonds
- **Claim pointer** The authors state that MD simulations "support the presence of inter-capsomer hydrogen bonds predicted by cryoEM" and that the N-terminal hydrogen bonds "likely both play an important role in capsid assembly and stability"
- **Evidence pointer** Results section "L1 N-terminal hydrogen bonds predicted between neighboring capsomers", Figure 5, Supplementary Figures 11-12
- **Concern** The MD simulations were performed on the empty capsid in the absence of heparin, yet they are used to support hydrogen bonds identified in the heparin-bound cryoEM structure. The authors do not clearly explain how simulations of the apo-capsid inform the interpretation of the ligand-bound state. Furthermore, the hydrogen bond frequencies reported are aggregated over all 60 quasi-equivalent chains, but the authors do not discuss the variability between chains or whether the specific hydrogen bonds identified in the cryoEM model are the same ones that are stable in the MD simulations.
- **Why it matters** The MD simulations are presented as independent support for the cryoEM findings, but the connection between the two is not clearly established. If the simulations were performed on a different state, their relevance to the heparin-bound structure needs to be justified.
- **Resolution test** Clarify the relationship between the MD simulations and the cryoEM structure. If the simulations are meant to support the hydrogen bonds in the heparin-bound state, simulations should be performed on the complex. Alternatively, the authors should clearly state that the MD simulations characterize the intrinsic dynamics of the empty capsid and that the hydrogen bonds observed in the cryoEM structure are consistent with the conformational ensemble sampled in the simulations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of unfilled densities
- **Claim pointer** The authors state that two unfilled densities at the inner surface of the capsid "could not be attributed to L1" and suggest they may be attributed to interactions between the HPV16 genome and the L1 C-terminus
- **Evidence pointer** Results section "Within the map, two cryoEM densities were observed at the inner surface of the capsid", Supplementary Figures 13-15
- **Concern** The authors speculate that the unfilled densities may represent the viral genome interacting with the L1 C-terminus, but this is presented without direct evidence. The MD simulations show that the C-termini of chains B and C sample the space corresponding to these densities, but the authors acknowledge that the simulated density accounts for only 18% of the experimental density volume. The remaining density is attributed to DNA, but no DNA model is built or validated.
- **Why it matters** The interpretation of these densities as DNA is speculative and could be incorrect. Other possibilities include ordered water molecules, ions, or other small molecules. Overinterpretation of unmodeled density can mislead readers and future studies.
- **Resolution test** Either build a DNA model into the density and validate it, or clearly label this interpretation as speculative and discuss alternative explanations. The authors should also consider whether the density could represent a mixture of states or partial occupancy.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section "Subparticle extraction"
- **Evidence pointer** Methods section, Results section "The resolution improved further with subparticle extraction and refinement"
- **Issue** The description of the "starfish" subparticle approach is somewhat confusing. The authors describe two different strategies: one using 380 Å diameter subparticles for the first dataset and 760 Å diameter subparticles for the second dataset. The relationship between these approaches and the final resolution improvement is not entirely clear.
- **Required correction** Clarify the relationship between the two subparticle strategies and provide a more detailed schematic or description of the starfish approach, including why the larger subparticles were needed for the second dataset.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4
- **Issue** The MD simulation figure (Figure 4) is difficult to interpret. The chloride density is shown in cyan, but the contour levels and the relationship to the protein surface are not clearly labeled. The figure legend does not fully explain the panels.
- **Required correction** Improve the figure labeling and legend to clearly indicate what each panel shows, including the contour levels used for the chloride density and the protein regions shown.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors do not explicitly discuss the limitations of using heparin as a surrogate for heparan sulfate, despite noting that heparin is more homogeneous and more highly sulfated. The implications of this difference for the physiological relevance of the findings should be addressed.
- **Required correction** Add a brief discussion of the limitations of using heparin as a surrogate for heparan sulfate and how the differences might affect the interpretation of the binding site.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not explicitly provided in the manuscript text
- **Issue** The manuscript does not include a clear data availability statement indicating where the cryoEM maps and model coordinates have been deposited.
- **Required correction** Add a data availability statement with accession codes for the deposited maps and models.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Results section, Discussion section
- **Issue** The authors use both "quasivirus" and "pseudovirus" terminology. While these are related concepts, the distinction should be clarified, and consistent terminology should be used throughout.
- **Required correction** Define the terms and use them consistently throughout the manuscript.

## Risk / unsupported claims
- The specific heparin contact residues identified in Figure 3 are not confidently supported given the authors' own admission that heparin could not be confidently built into the density
- The claim of "reduced flexibility in all arm connections" is not statistically validated
- The interpretation of unfilled densities as DNA is speculative and not directly supported by the data
- The MD simulations of the empty capsid are used to support findings in the heparin-bound state without clear justification of their relevance
- The claim that N-terminal hydrogen bonds "likely both play an important role in capsid assembly and stability" extends beyond the direct evidence presented