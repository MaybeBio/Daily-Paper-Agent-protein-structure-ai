## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors used microsecond-scale molecular dynamics simulations of the human GAT-1 inward-open apo state (PDB 7Y7V) to compare the wild-type transporter with three variants (R211C, A305T, A346S). They report that these mutations do not globally destabilize the protein but instead induce specific local rearrangements: R211C abolishes a hydrogen bond at the EL2-TM4 interface, A305T alters the TM1-TM6 interface near the sodium-binding site, and A346S strengthens TM1/TM6-EL4 interactions. The authors propose these structural shifts explain how pathogenic mutations remodel the GAT-1 interaction network and alter conformational dynamics, providing a basis for future docking and transport-cycle modeling.
- **Visible evidence base** Abstract text only; no methodological details, simulation parameters, convergence criteria, statistical analyses, or structural figures are available
- **Missing materials affecting confidence** Full methods, simulation validation (e.g., RMSD/RMSF profiles, convergence checks), replicate information, force field parameters, system setup details, structural figures, quantitative interaction analyses, and any comparison with experimental functional data

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful computational study addressing a clinically relevant question, namely the structural consequences of schizophrenia-associated SLC6A1 variants. The choice of the inward-open apo state and the focus on local interaction networks rather than global destabilization is scientifically reasonable. However, the abstract alone provides insufficient evidence to evaluate the technical rigor of the simulations, the statistical robustness of the reported differences, or the biological significance of the observed local rearrangements. The claims are qualitatively stated and lack quantitative support. The study may be of interest to the GABA transporter and neuropsychiatric genetics communities, but the current evidence base does not establish the case.
- **Who would be interested in the results, and why** Researchers studying GABA transporter structure and function, computational biologists working on membrane protein dynamics, and geneticists investigating the molecular mechanisms of neuropsychiatric disorder-associated variants. The findings could inform future drug repurposing efforts targeting GAT-1 and provide a framework for interpreting additional SLC6A1 variants.
- **Major strengths** The study addresses a clinically relevant gap by linking schizophrenia-associated variants to specific structural mechanisms. The focus on local interaction networks rather than global stability is a thoughtful approach. The inclusion of a deep learning-based variant selection adds a comparative dimension. The stated goal of providing a foundation for docking and transport-cycle modeling is appropriate and potentially impactful.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The absence of any methodological detail or quantitative results in the provided material means that the central claims cannot be verified. Specifically, the simulation setup, convergence, replicate handling, and statistical significance of the reported interaction changes are all unassessable. The claim that mutations "do not globally destabilize" requires quantitative comparison of structural stability metrics. The claim that specific rearrangements "suggest how pathogenic mutations remodel" the interaction network requires evidence that the observed changes are robust across replicates and not artifacts of limited sampling.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of MD to SLC6A1 variants is not unprecedented, but the specific focus on schizophrenia-associated variants and the local interaction network perspective adds some novelty.
  - Scientific importance: Moderate. The findings could inform understanding of GAT-1 dysfunction, but the clinical relevance is indirect and the abstract does not establish a clear mechanistic link to schizophrenia pathology.
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational structural biologists and GABA transporter specialists; the abstract does not frame the findings in a way that would attract a broader neuroscience or genetics audience.
  - Technical soundness: Not assessable from the abstract. No methodological details or validation data are provided.
  - Readability for nonspecialists: The abstract is clearly written and accessible, with appropriate use of domain terminology.
- **Recommendation posture** Currently not established from the provided evidence. The study may be supportable if the full manuscript provides rigorous simulation validation, quantitative interaction analyses, and appropriate statistical treatment, but the abstract alone does not substantiate the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the mutations "do not globally destabilize the protein structure" and that they "induce specific rearrangements within local contact networks."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract provides no quantitative data on structural stability (e.g., RMSD, RMSF, radius of gyration) or on interaction network changes (e.g., hydrogen bond occupancy, contact maps, free energy estimates). Without such data, the central claims of local versus global effects cannot be evaluated.
- **Why it matters** The distinction between global destabilization and local rearrangement is the core scientific message. If the simulations are underconverged, under-replicated, or analyzed with insufficient statistical rigor, the observed differences may be noise rather than genuine mutation effects.
- **Resolution test** Provide quantitative stability metrics with error bars across multiple independent replicates, and show that the reported interaction changes are statistically significant and reproducible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "R211C abolishes a hydrogen bond at the interface of EL2 and TM4," "A305T alters the TM1-TM6 interface adjacent to the sodium ion-binding site," and "A346S strengthens TM1/TM6-EL4 interactions."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No methodological details are given regarding simulation length, number of replicates, force field, water model, membrane representation, temperature/pressure coupling, or equilibration protocol. The choice of the inward-open apo state (PDB 7Y7V) is stated, but the rationale and the handling of missing residues, protonation states, and ions are not described. The specific interaction changes are reported qualitatively without occupancy values, distances, or energy contributions.
- **Why it matters** Molecular dynamics results are highly sensitive to simulation setup and analysis choices. Without these details, the reported structural consequences cannot be reproduced or independently verified, and the biological interpretation may be premature.
- **Resolution test** Provide a complete methods section including simulation parameters, system construction, equilibration, production run lengths, replicate counts, and a detailed description of the interaction analysis with quantitative metrics and statistical tests.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "the identified structural shifts suggest how pathogenic mutations remodel the GAT-1 interaction network and alter its conformational dynamics" and that these findings "provide a foundation for subsequent molecular docking aimed at drug repurposing."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not connect the observed structural changes to functional outcomes, such as altered GABA transport kinetics, substrate binding affinity, or conformational transition rates. The link to schizophrenia pathology is asserted but not mechanistically developed. The claim that the findings enable drug repurposing is speculative without docking results or functional validation.
- **Why it matters** For the study to have scientific importance beyond a descriptive structural analysis, the authors must demonstrate that the observed local rearrangements have functional consequences. Without this link, the clinical relevance and translational potential remain unsubstantiated.
- **Resolution test** Include functional correlation, such as comparison with experimental transport assay data, or perform additional simulations (e.g., substrate-bound states, transition path sampling) that link the observed structural changes to altered transport function.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Variant selection rationale
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract states that A346S was "selected via deep learning-based pathogenicity predictors" but does not explain why this variant was chosen for comparison with the schizophrenia-associated variants R211C and A305T.
- **Required correction** Briefly state the predicted pathogenicity score or the rationale for including A346S as a comparator, and clarify whether it is also associated with schizophrenia or serves as a general pathogenic variant control.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Simulation scope
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract mentions "microsecond-scale" simulations but does not specify the total simulation time per system or whether multiple independent trajectories were generated.
- **Required correction** Specify the total simulation time per variant and the number of replicates in the abstract or methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Functional implications
- **Evidence pointer** Abstract only; location not provided
- **Issue** The phrase "alter its conformational dynamics" is vague and does not specify which dynamic property (e.g., domain motion, helix tilting, channel opening) is affected.
- **Required correction** Describe the specific dynamic changes observed, such as altered interdomain correlations or changes in the distribution of conformational states.

## Risk / unsupported claims
- The claim that the mutations "do not globally destabilize the protein structure" is unsupported without quantitative stability data.
- The specific interaction changes attributed to each variant (R211C, A305T, A346S) are unsupported without quantitative interaction analysis.
- The claim that the findings "suggest how pathogenic mutations remodel the GAT-1 interaction network" is not established from the abstract alone.
- The statement that the results "provide a foundation for subsequent molecular docking aimed at drug repurposing" is speculative and not supported by any docking or functional data in the provided material.
- The biological relevance to schizophrenia is asserted but not mechanistically demonstrated in the abstract.