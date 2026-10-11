## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supplementary material were provided for verification
- **Shared manuscript claim summary** The authors report microsecond-level equilibrium molecular dynamics replicas and well-tempered metadynamics simulations to characterize Phen-DC3 recognition at a G-quadruplex-duplex (Q-D) junction. They claim that ligand binding induces a reorganized bound-state architecture with reduced global structural displacement but a more expanded conformation, junctional opening, redistributed flexibility, a more distinct and less fragmented bound-state ensemble, and a non-monotonic unbinding free-energy profile with a partially bound surface-associated state. They propose a working model coupling junctional opening, ensemble narrowing, correlated-motion reorganization, and multistep dissociation, and suggest design implications for future Q-D junction ligands.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, convergence metrics, free-energy error estimates, or structural analyses are visible
- **Missing materials affecting confidence** Full methods, simulation setup and force-field parameters, convergence and equilibration assessments, free-energy profiles with error bars, PCA and correlation-motion analysis details, contact analysis definitions, system construction and validation, and any figures or tables supporting the stated results

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational study of ligand recognition at a Q-D junction, with a plausible working model that couples structural, dynamical, and energetic features. However, the claims are broad and mechanistically detailed, and none of the supporting quantitative evidence is visible in the supplied material. The abstract alone does not allow verification of the simulation quality, convergence, or statistical robustness of the reported findings. The design implications are reasonable but speculative without comparative or experimental context.
- **Who would be interested in the results, and why** Researchers in nucleic-acid structure and dynamics, computational biophysics, and drug design targeting G-quadruplexes and their junctions would be interested. The proposed multistep dissociation mechanism and the emphasis on junctional geometry and secondary interaction sites could inform ligand design strategies for selective Q-D junction targeting.
- **Major strengths** The study addresses a relevant and under-characterized target class, namely Q-D junctions, and moves beyond simple stacking descriptions. The use of multiple simulation approaches, including equilibrium replicas and well-tempered metadynamics, is appropriate for probing both binding and unbinding. The working model is integrative and offers testable hypotheses for future ligand design.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate, as the application of MD and metadynamics to ligand-Q-D junction systems is not unprecedented, though the specific focus on multistep dissociation and junctional dynamics is a useful contribution. Scientific importance is potentially significant for the nucleic-acid ligand design community, but the current evidence base is insufficient to establish the mechanistic claims. Interdisciplinary readership is plausible, spanning computational chemistry, biophysics, and medicinal chemistry, but the abstract assumes familiarity with specialized terms without sufficient context. Technical soundness cannot be assessed from the abstract alone, as no convergence, error, or validation data are provided. Readability for nonspecialists is limited by dense jargon and the absence of quantitative anchors.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising, but the claims require full methodological and quantitative support. A supportive posture would be possible if the technical concerns are resolved with complete data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that microsecond-level equilibrium molecular dynamics replicas per state and multiple well-tempered metadynamics simulations characterize the structural and energetic features of Phen-DC3 recognition at a Q-D junction.
- **Evidence pointer** Abstract only, location not provided
- **Concern** No simulation details are provided, including force field, water model, ion conditions, temperature and pressure coupling, simulation length per replica, number of replicas, or metadynamics parameters such as collective variables, bias factors, and deposition pace. Without these, the technical adequacy of the simulations cannot be evaluated.
- **Why it matters** The validity of all downstream structural and energetic claims depends on the quality and convergence of the underlying simulations. Inadequate sampling or inappropriate parameters could lead to artifacts that are misinterpreted as biological features.
- **Resolution test** Provide full methods with force-field parameters, simulation lengths, replica counts, equilibration protocols, and metadynamics settings. Show convergence metrics such as time-dependent free-energy estimates, replica overlap, and block-error analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that binding promotes junctional opening with increased geometric separations and angle, and that flexibility is redistributed rather than globally reduced, with specific residues becoming more mobile.
- **Evidence pointer** Abstract only, location not provided
- **Concern** No quantitative values, error estimates, or statistical comparisons are given for the geometric separations, angles, or per-residue mobility changes. The claim of redistribution versus global reduction requires a quantitative comparison of flexibility profiles between bound and unbound states.
- **Why it matters** Without error bars and statistical testing, the reported differences could be within noise, especially given the complexity of nucleic-acid dynamics. The specific residue-level claims are central to the proposed model and must be robustly supported.
- **Resolution test** Provide distributions or averages with standard errors for the geometric parameters and per-residue root-mean-square fluctuations or equivalent mobility metrics, with statistical significance tests between states.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PCA shows a more distinct and less fragmented bound-state ensemble with local minima decreasing from 31 to 14, and that correlated-motion analysis reveals strengthened and weakened couplings.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The PCA and correlation-motion results are presented without methodological detail, such as the atoms or residues included, the covariance matrix construction, or the clustering algorithm used to define local minima. The interpretation of "more distinct" and "less fragmented" is subjective without quantitative descriptors.
- **Why it matters** These claims are used to support the ensemble-narrowing component of the working model. If the analysis is not rigorously defined or the differences are not statistically robust, the model loses a key pillar.
- **Resolution test** Describe the PCA and correlation analysis protocols, including the definition of local minima and the criteria for strengthened or weakened coupling. Provide quantitative measures of ensemble overlap or distinctness with uncertainty estimates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that unbinding free-energy profiles are non-monotonic with a second minimum at larger ligand-site separation, corresponding to a partially bound surface-associated state, and that contact analysis shows progressive loss of peripheral contacts while hydrophobic and van-der-Waals contacts at DG9 and DG14 persist.
- **Evidence pointer** Abstract only, location not provided
- **Concern** No free-energy profile is shown, and no error estimates or convergence assessments for the metadynamics simulations are provided. The identification of a second minimum and the persistence of specific contacts require quantitative support, including the definition of the ligand-active site distance and the contact criteria.
- **Why it matters** The multistep dissociation mechanism is a central novel claim. If the second minimum is an artifact of insufficient sampling or poor collective-variable choice, the proposed mechanism would be unsupported.
- **Resolution test** Show the free-energy profile as a function of the reaction coordinate with error bars, demonstrate convergence via multiple independent runs or reweighting analyses, and provide contact analysis with clear distance and occupancy cutoffs.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract uses specialized terms such as "well-tempered metadynamics," "PCA," and "correlated-motion analysis" without brief explanations, which may limit accessibility for readers outside computational biophysics.
- **Required correction** Add brief parenthetical explanations or contextual phrases for these methods to improve readability for a broader audience.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scientific context
- **Affected element** Design implications
- **Evidence pointer** Abstract, location not provided
- **Issue** The suggestion that future ligands should exploit junctional geometry and secondary interaction sites is presented without comparison to existing ligand design strategies or known Q-D junction ligands beyond Phen-DC3.
- **Required correction** Provide a brief context of how these findings differ from or extend current design principles, or temper the claim to reflect the speculative nature of the implications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Working model
- **Evidence pointer** Abstract, location not provided
- **Issue** The working model lists four coupled features but does not specify the direction or hierarchy of coupling, leaving the mechanistic relationship ambiguous.
- **Required correction** Clarify whether the features are sequential, concurrent, or interdependent, and state the proposed causal ordering if any.

## Risk / unsupported claims
- The claim that binding is associated with a reorganized bound-state architecture with reduced global structural displacement but a more expanded conformation is unsupported without quantitative structural metrics.
- The claim that the junction region contributes most strongly to domain-specific rearrangement is unsupported without per-domain decomposition data.
- The specific residue-level flexibility changes (DG9, DG35, DG36, DT10, DA11, DG14) are unsupported without quantitative fluctuation data.
- The PCA-based claim of local minima decreasing from 31 to 14 is unsupported without methodological detail and error assessment.
- The correlated-motion claims (strengthened DG17-DG35/DG36 coupling and weakened DG7-DG9-associated correlations) are unsupported without quantitative correlation values.
- The non-monotonic free-energy profile and the existence of a second minimum are unsupported without the profile itself and convergence evidence.
- The contact persistence claims at DG9 and DG14 are unsupported without contact analysis definitions and occupancy data.
- The working model coupling junctional opening, ensemble narrowing, correlated-motion reorganization, and multistep dissociation is not established from the provided evidence.
- The design implications for future Q-D junction ligands are speculative and not supported by comparative or experimental data.