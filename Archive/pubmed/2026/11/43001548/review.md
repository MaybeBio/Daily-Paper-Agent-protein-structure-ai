## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, with no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that the peptide DX600 inhibits ACE2 by stabilizing the receptor in an open conformation, reducing local residue fluctuations as shown by molecular dynamics simulations and RMSF analysis, and propose this mechanism is distinct from that of small-molecule inhibitors such as MLN-4760, with implications for blocking SARS-CoV-2 spike engagement and for rational design of ACE2-targeted therapeutics.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, experimental validation, or statistical measures are provided
- **Missing materials affecting confidence** Full manuscript, methods section, simulation details, biophysical experimental data, figures, tables, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting mechanistic hypothesis for DX600-mediated ACE2 inhibition, contrasting with the conformational change mechanism attributed to MLN-4760. However, the evidence base visible in the abstract is insufficient to evaluate the validity of the central claims. No quantitative results, simulation validation, or experimental corroboration are presented. The claim of a "distinct mechanism" is not supported by direct comparative data in the abstract. The work may be of interest to structural biologists and drug designers, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Structural biologists studying ACE2 conformational dynamics, computational chemists developing peptide inhibitors, and medicinal chemists targeting ACE2 for therapeutic intervention in conditions such as hypertension or viral entry blockade. The proposed mechanism could inform design of allosteric or stabilizing inhibitors, which is a topic of broad interest in drug discovery.
- **Major strengths** The hypothesis is clearly articulated and mechanistically distinct from known small-molecule inhibitors. The use of molecular dynamics and RMSF analysis is appropriate for probing conformational stability. The potential translational relevance to SARS-CoV-2 spike engagement is timely and conceptually appealing.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** No quantitative simulation data, no validation of force field or simulation convergence, no experimental biophysical data to support the computational predictions, and no direct comparison with MLN-4760 under identical conditions are visible in the abstract. The claim of steric hindrance impeding spike engagement is speculative without binding or functional assays.
- **Assessment against Nature-style criteria** 
  - Originality: The proposed stabilizing mechanism is potentially novel, but the abstract does not demonstrate how it advances beyond existing knowledge of ACE2 inhibitors.
  - Scientific importance: The topic is relevant, but the significance is not established without quantitative evidence of functional impact.
  - Interdisciplinary readership: The work bridges computational and biophysical domains, which could appeal to a broad audience, but the abstract lacks sufficient detail to engage nonspecialists.
  - Technical soundness: Cannot be assessed from the abstract alone; no methodological details or error estimates are provided.
  - Readability for nonspecialists: The abstract is generally clear, but terms such as RMSF and conformational states are used without brief explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting, but the abstract alone does not provide sufficient support for the central claims. A revised version with quantitative data and experimental validation could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that DX600 binding stabilizes ACE2 in an open conformation and reduces local residue mobility, based on molecular dynamics simulations and RMSF analysis.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no quantitative data, such as RMSF values, free energy calculations, or comparison of conformational ensembles, to support the claim of stabilization. No simulation parameters, convergence criteria, or replicate information are given.
- **Why it matters** Without quantitative evidence, the reader cannot assess whether the observed effects are statistically significant or an artifact of the simulation setup. The central mechanistic claim rests entirely on this analysis.
- **Resolution test** Provide specific RMSF values with error bars, comparison of conformational distributions between bound and unbound states, and details of simulation length, replicates, and force field validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors state that the stabilization produces steric hindrance that may impede viral protein engagement, such as the SARS-CoV-2 spike protein.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract mentions "biophysical analysis" in the title but presents no experimental data, such as binding assays, surface plasmon resonance, or cellular infection models, to support the functional consequence of the proposed mechanism.
- **Why it matters** The claim of impeded spike engagement is a functional prediction that cannot be established by simulation alone. Without experimental corroboration, the translational relevance remains speculative.
- **Resolution test** Include experimental binding or neutralization assays demonstrating that DX600 reduces spike-ACE2 interaction, with appropriate controls and quantitative measures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative claim
- **Claim pointer** The authors claim that DX600's mechanism is "distinct" from that of MLN-4760, which induces a transition from open to closed conformation.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No direct comparative simulation or experimental data for MLN-4760 under the same conditions are presented in the abstract. The distinction is asserted but not demonstrated.
- **Why it matters** The claim of mechanistic novelty is a key selling point of the work. Without a head-to-head comparison, the reader cannot verify that the difference is real rather than an artifact of different simulation protocols or conditions.
- **Resolution test** Provide comparative simulations or experiments with MLN-4760 using identical methods, and show quantitative differences in conformational dynamics and functional outcomes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "opened to closed conformation" is used without defining the structural basis of these states, which may confuse readers unfamiliar with ACE2 dynamics.
- **Required correction** Briefly define the conformational states in terms of domain movements or key structural features.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Nonspecialist accessibility
- **Evidence pointer** Abstract text; location not provided
- **Issue** "RMSF analysis" is mentioned without explanation, which may hinder comprehension for readers outside computational biophysics.
- **Required correction** Add a brief parenthetical explanation, such as "root mean square fluctuation, a measure of residue-level mobility."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope
- **Affected element** Therapeutic implications
- **Evidence pointer** Abstract text; location not provided
- **Issue** The final sentence claims insights for "rational design of ACE2-targeted small molecule therapeutics," but the study focuses on a peptide, and the link to small molecule design is not elaborated.
- **Required correction** Clarify how the peptide-based findings translate to small molecule design, or temper the claim to match the scope of the study.

## Risk / unsupported claims
- The claim that DX600 locks ACE2 in an open conformation is unsupported by quantitative data in the abstract.
- The claim that this stabilization impedes SARS-CoV-2 spike engagement is speculative without functional assays.
- The claim of a distinct mechanism from MLN-4760 is not supported by comparative evidence.
- The title's reference to "biophysical analysis" is not substantiated by any experimental data in the abstract.