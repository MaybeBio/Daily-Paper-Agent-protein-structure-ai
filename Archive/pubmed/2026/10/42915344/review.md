## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report conventional molecular dynamics (MD) and ligand Gaussian accelerated molecular dynamics (LiGaMD) simulations of NDM-1 in free form and in complex with three inhibitors (SFC, SPC, CAP). They claim that inhibitor binding perturbs a distant loop L7 via the Zn-binding residue His-165, suggesting a potential allosteric site. LiGaMD replica simulations are claimed to sample rare conformational states and provide ligand binding and unbinding kinetics, with loop L7 highlighted as a transiently accessible binding region. The SFC/NDM-1 complex is claimed to be the most optimal based on a favorable balance of binding thermodynamics and kinetics.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, convergence metrics, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation setup details, force field parameters, system preparation protocols, convergence assessments, error bars, and any supporting information

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study of NDM-1 inhibitor binding using established MD and LiGaMD methodologies. The scientific question is relevant to antimicrobial resistance research. However, the abstract lacks quantitative results, methodological details, and validation metrics necessary to assess the robustness of the claims. The identification of a potential allosteric site and the ranking of the SFC complex as optimal are interesting but currently under-supported by the evidence presented. The study may be of interest to computational chemists and medicinal chemists working on beta-lactamase inhibitors, but the case is not fully established from the abstract alone.
- **Who would be interested in the results, and why** Computational biophysicists and medicinal chemists focused on antimicrobial resistance, particularly those studying metallo-beta-lactamases and inhibitor design. The proposed allosteric site and kinetic characterization of ligand binding could inform structure-based drug discovery efforts targeting NDM-1.
- **Major strengths** The combination of conventional MD and LiGaMD is appropriate for studying both equilibrium dynamics and rare conformational events. The focus on binding kinetics in addition to thermodynamics is a valuable addition to the field. The identification of a potential allosteric site through long-range communication is an interesting hypothesis that could open new avenues for inhibitor design.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: moderate. The application of LiGaMD to NDM-1 is not entirely novel, but the focus on allosteric communication and kinetics adds some originality. Scientific importance: high for the antimicrobial resistance field, but the impact depends on the robustness of the findings. Interdisciplinary readership: limited to computational and medicinal chemistry communities. Technical soundness: cannot be fully assessed from the abstract; key methodological details and validation are missing. Readability for nonspecialists: the abstract is accessible but uses field-specific terminology without sufficient context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valuable study, but the lack of quantitative data and methodological transparency prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that LiGaMD simulations provided insights into ligand binding and unbinding kinetics and that the SFC/NDM-1 complex was found to be the most optimal based on the most favorable balance of binding thermodynamics and kinetics.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No quantitative kinetic or thermodynamic values are reported. The abstract does not provide binding free energies, residence times, association or dissociation rate constants, or any comparison metrics that would support the ranking of the SFC complex as optimal.
- **Why it matters** The central conclusion of the study, namely the identification of the most promising inhibitor scaffold, rests on a comparative ranking that cannot be evaluated without numerical data. Without these values, the claim is unverifiable and the practical utility of the study for inhibitor design is unclear.
- **Resolution test** Provide quantitative values for binding free energies (e.g., MM-PBSA or LiGaMD-derived) and kinetic parameters (e.g., k_on, k_off, residence times) for all three complexes, with appropriate error estimates and statistical significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that LiGaMD simulations were applied in the form of a replica that enabled sampling of rare conformational states.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not specify the number of replicas, simulation lengths, convergence criteria, or how the replica approach was implemented. It is unclear whether the simulations reached equilibrium and whether the sampling of rare states was statistically robust.
- **Why it matters** LiGaMD is a specialized enhanced sampling method whose results are highly sensitive to simulation setup and convergence. Without these details, the reliability of the kinetic and conformational findings cannot be assessed, and the claim of sampling rare states remains unsupported.
- **Resolution test** Describe the LiGaMD simulation protocol in detail, including the number of replicas, simulation time per replica, boost parameters, and convergence metrics (e.g., time series of relevant observables, replicate reproducibility). Provide evidence that the sampled states are converged and reproducible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that a distant loop L7 was perturbed by the Zn-binding residue His-165, suggesting a potential allosteric site, and that LiGaMD highlighted L7 as a transiently accessible binding region.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no structural or dynamical data, such as RMSF values, correlation maps, or free energy landscapes, to support the claim of allosteric communication between His-165 and loop L7. The assertion that L7 is a transiently accessible binding region is not backed by any binding site analysis or ligand occupancy data.
- **Why it matters** The proposed allosteric site is a key novel finding of the study. If not supported by robust evidence, the claim could mislead future drug design efforts. The distinction between a transiently accessible region and a bona fide binding site requires rigorous validation.
- **Resolution test** Provide quantitative evidence of allosteric communication, such as dynamic cross-correlation matrices, principal component analysis, or perturbation response scanning. For the L7 binding site claim, show ligand occupancy maps, binding free energy profiles, or kinetic evidence of ligand binding at that site from LiGaMD simulations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "ligand network analysis" is used without definition or context. It is unclear what this analysis entails and how it differs from standard protein-ligand interaction analysis.
- **Required correction** Define "ligand network analysis" and briefly describe the method and its purpose in the abstract or methods section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Inhibitor details
- **Evidence pointer** Abstract text; location not provided
- **Issue** The inhibitors SFC, SPC, and CAP are mentioned by acronym only. No chemical names, structures, or known activities are provided, which limits the reader's ability to contextualize the findings.
- **Required correction** Provide full chemical names or structures of the inhibitors, and if available, a brief statement of their known inhibitory activity against NDM-1.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation parameters
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not mention the force field, water model, or simulation temperature used in the conventional MD simulations. These are essential for reproducibility.
- **Required correction** Include force field, water model, and simulation conditions in the methods summary or abstract.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Allosteric site claim
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that further investigation was required to establish L7 as a potential binding site, yet the conclusion suggests the findings may be implicated in rational drug design. This creates a slight inconsistency in the strength of the claim.
- **Required correction** Clarify whether L7 is presented as a confirmed allosteric site or as a hypothesis requiring further validation, and align the conclusion with that level of certainty.

## Risk / unsupported claims
- The claim that the SFC/NDM-1 complex is the most optimal is unsupported without quantitative thermodynamic and kinetic data.
- The claim of a potential allosteric site involving His-165 and loop L7 is unsupported without structural or dynamical evidence.
- The claim that LiGaMD provided insights into ligand binding and unbinding kinetics is unverifiable without kinetic parameters or convergence metrics.
- The claim that L7 is a transiently accessible binding region is unsupported without binding site analysis or occupancy data.