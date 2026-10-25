## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full methods, figures, or simulation details
- **Shared manuscript claim summary** The authors use multiscale molecular dynamics simulations to characterize lipid binding dynamics and sodium ion coordination in the TRAP transporter HiSiaQM from Haemophilus influenzae. They report validation of an experimentally known lipid-binding site (BS1) with preferential POPG occupancy, discovery of a novel POPE-selective site (BS2), and differential stability of two sodium binding sites (Na1 stable, Na2 less stable), with tunnel analysis suggesting distinct functional roles for Na1 and Na2.
- **Visible evidence base** Abstract text only. No figures, tables, methods, or supplementary materials were provided.
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, structural coordinates, lipid composition details, ion concentration settings, tunnel analysis methodology, and experimental validation data are all unavailable.

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting computational study of lipid and ion dynamics in a membrane transporter of biological relevance. The findings are internally coherent and the proposed mechanistic distinction between Na1 and Na2 is intellectually appealing. However, the abstract alone provides insufficient evidence to evaluate the technical rigor of the simulations, the statistical significance of the observed differences, or the robustness of the conclusions. Several claims are presented as definitive without visible quantitative support. The work may be of interest to the membrane transporter and molecular simulation communities, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying TRAP transporters and other secondary active transporters would be interested in the proposed mechanistic roles of sodium binding sites. Computational biophysicists and molecular dynamics practitioners would be interested in the multiscale simulation approach and the identification of lipid binding dynamics. Structural biologists working on membrane proteins could find the lipid interaction data useful for understanding native-like environments. The potential link between lipid composition and transporter function may also appeal to microbiologists studying Haemophilus influenzae pathogenesis.
- **Major strengths** The study addresses a relevant and under-explored aspect of TRAP transporter function, namely the dynamic behavior of lipids and ions rather than static structures. The use of multiscale simulations is appropriate for capturing both local interactions and larger-scale dynamics. The authors explicitly acknowledge that the distinct lipid-binding behaviors remain to be tested experimentally, which is an appropriate level of caution. The proposed functional asymmetry between Na1 and Na2 provides a testable hypothesis that could guide future experimental work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation validation and convergence), R1-M2 (quantitative support for lipid selectivity), R1-M3 (sodium site stability comparison)
- **Assessment against Nature-style criteria** Originality: The study offers a novel perspective on TRAP transporter dynamics by focusing on lipid and ion behavior rather than static structure, which is a reasonable contribution to the field. Scientific importance: The findings could inform understanding of ion-coupled transport mechanisms, but the significance is moderate and largely hypothesis-generating at this stage. Interdisciplinary readership: The topic bridges structural biology, computational biophysics, and microbiology, which could attract a broad audience if the evidence is robust. Technical soundness: Cannot be adequately assessed from the abstract alone. The absence of methodological details and quantitative results prevents verification of simulation quality, sampling adequacy, or statistical rigor. Readability for nonspecialists: The abstract is clearly written and accessible, with appropriate use of terminology and a logical flow from background to findings to implications.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a coherent narrative, but the lack of visible quantitative data and methodological detail means the core claims cannot be verified. A supportive posture would require access to the full manuscript demonstrating simulation convergence, statistical robustness, and appropriate controls.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The simulations validated an experimentally identified lipid-binding site (BS1) and provided insight into its lipid-binding dynamics.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that BS1 was validated and that its dynamics were characterized, but no information is provided about simulation length, number of replicates, force field parameters, lipid bilayer composition, or convergence criteria. Without these details, it is impossible to assess whether the simulations adequately sampled the relevant conformational space or whether the observed lipid binding events are statistically meaningful rather than stochastic artifacts.
- **Why it matters** Molecular dynamics simulations of membrane proteins are highly sensitive to system setup and sampling. Claims of validation and dynamic characterization require evidence that the simulations reached equilibrium, that multiple independent runs produced consistent results, and that the chosen force field and membrane model are appropriate for the system. The absence of this information undermines confidence in the central findings.
- **Resolution test** Provide simulation protocols including system size, simulation time per replicate, number of replicates, force field and water model, lipid composition, ion concentration, and temperature/pressure coupling schemes. Show convergence metrics such as root-mean-square deviation over time, lipid occupancy as a function of simulation time, and replicate-to-replicate variability.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** BS1 is preferentially occupied by the anionic POPG, which is stabilized through persistent hydrogen bonds involving residues H100, R104, and R181. A novel, less stable lipid-binding site (BS2) is selectively occupied by POPE.
- **Evidence pointer** Abstract, location not provided
- **Concern** The claims of preferential and selective lipid occupancy are presented without quantitative data. No occupancy percentages, free energy estimates, residence times, or statistical comparisons between lipid types are provided. The statement that POPG forms more persistent interactions at BS1 and POPE engages more transiently at BS2 is qualitative and lacks supporting numbers. It is unclear how selectivity was determined and whether the observed preferences are statistically significant given the simulation time and lipid concentrations used.
- **Why it matters** Lipid selectivity in membrane protein simulations can be influenced by initial conditions, lipid composition, and simulation length. Without quantitative occupancy data and appropriate statistical tests, the claim of preferential binding cannot be distinguished from random fluctuation or setup bias. This is a core finding of the study and must be rigorously supported.
- **Resolution test** Report occupancy fractions for each lipid type at each site, residence time distributions, and statistical comparisons (e.g., standard errors across replicates or bootstrapped confidence intervals). If possible, provide potential of mean force calculations or free energy estimates for lipid binding at each site.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Na1 exhibited stable ion retention through backbone carbonyl coordination, while Na2 displayed lower stability due to involvement of the flexible side chain of T561. Geometric tunnel analysis identified possible sodium-exit pathways, supporting a working hypothesis that Na1 may act as a stable anchoring site and Na2 may function as a transient ion-exchange point.
- **Evidence pointer** Abstract, location not provided
- **Concern** The differential stability of Na1 and Na2 is described qualitatively, with no quantitative measures such as ion occupancy over time, coordination bond lifetimes, or root-mean-square fluctuations of coordinating residues. The role of T561 in destabilizing Na2 is asserted but not demonstrated with data. The tunnel analysis is mentioned without any description of the method, the criteria for identifying tunnels, or the statistical significance of the proposed exit pathways.
- **Why it matters** The proposed functional asymmetry between Na1 and Na2 is a central mechanistic claim. Without quantitative evidence of differential ion retention and a rigorous tunnel analysis, the hypothesis remains speculative. The involvement of T561 in particular requires demonstration that its flexibility correlates with reduced ion occupancy or increased coordination bond breaking events.
- **Resolution test** Provide ion occupancy time series for both sites, coordination bond lifetime distributions, and fluctuation analysis of T561 compared to other coordinating residues. Describe the tunnel analysis method (e.g., CAVER or similar), the parameters used, and the frequency and persistence of the identified exit pathways across simulation replicates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "HiSiaQM horizontal line a membrane-embedded TRAP subunit" appears to contain a formatting artifact where "horizontal line" is used in place of an em dash or similar separator. This is likely a typesetting error but should be corrected for clarity.
- **Required correction** Replace "horizontal line" with the appropriate punctuation or rephrase the sentence to avoid the artifact.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Experimental validation statement
- **Evidence pointer** Abstract, location not provided
- **Issue** The authors state that the distinct lipid-binding behaviors "remain to be tested experimentally," which is appropriate. However, it is unclear whether any experimental data already exist that could partially support or contradict the simulation findings, such as mutagenesis studies on H100, R104, R181, or T561.
- **Required correction** Clarify whether any prior experimental data on these residues exist and, if so, briefly state how the simulation results relate to them.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "multiscale molecular dynamics simulations" is used, but the abstract does not specify which scales were combined or how. This could mean coarse-grained and atomistic simulations, or it could refer to different time-scale approaches. The term is ambiguous without further detail.
- **Required correction** Specify the types of simulations used (e.g., coarse-grained and atomistic) and briefly indicate how they were integrated in the study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Mechanistic hypothesis
- **Evidence pointer** Abstract, location not provided
- **Issue** The proposed roles of Na1 as a "stable anchoring site" and Na2 as a "transient ion-exchange point" are presented as a working hypothesis, which is appropriate. However, the abstract does not explain how these roles would mechanistically couple to substrate transport or the overall transport cycle.
- **Required correction** Add one or two sentences connecting the proposed sodium site functions to the broader transport mechanism, or explicitly state that this connection remains to be established.

## Risk / unsupported claims
- The claim that BS1 is "preferentially occupied" by POPG is unsupported without quantitative occupancy data or statistical analysis.
- The claim that BS2 is "selectively occupied" by POPE is unsupported for the same reason.
- The assertion that POPG forms "persistent" interactions and POPE engages "transiently" is qualitative and lacks residence time or bond lifetime data.
- The differential stability of Na1 versus Na2 is asserted without quantitative ion occupancy or coordination dynamics data.
- The role of T561 in reducing Na2 stability is stated as fact but not demonstrated with fluctuation or coordination analysis.
- The tunnel analysis and proposed sodium-exit pathways are mentioned without methodological detail or statistical support.
- The overall mechanistic conclusion that lipid interactions and sodium coordination "could modulate" transporter function is appropriately framed as a possibility, but the strength of the underlying evidence cannot be evaluated from the abstract alone.