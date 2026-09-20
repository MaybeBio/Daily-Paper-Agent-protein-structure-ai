## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use molecular dynamics simulations, enhanced sampling, and deep learning-assisted network analysis to investigate the prereactive stage of amorphous PET adsorption and substrate binding in the LCC PET hydrolase system. They identify three mechanistic origins for the enhanced activity of the LCC-LANL variant relative to LCC-WT, propose a region-specific cooperative optimization strategy, and distill six design principles for efficient PETases.
- **Visible evidence base** Abstract text only; no quantitative data, simulation details, or methodological descriptions are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation protocols, force field parameters, convergence criteria, statistical analyses, and any validation or experimental corroboration

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable computational study aimed at explaining the enhanced activity of the LCC-LANL PET hydrolase variant. The proposed mechanistic origins are coherent and internally consistent, and the integration of multiple computational approaches is commendable. However, the abstract alone provides insufficient detail to evaluate the technical rigor, statistical robustness, or generalizability of the findings. The claims are stated with high confidence but lack the quantitative support and methodological transparency required to assess their validity. The work may be of interest to the enzyme engineering and plastic biodegradation communities, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in enzyme engineering, protein dynamics, and plastic biodegradation would be interested. The study addresses a pressing environmental problem and offers mechanistic insights that could guide rational design of improved PETases. Computational biophysicists interested in allosteric communication and deep learning applications to protein dynamics may also find the methodological integration appealing.
- **Major strengths** The study addresses a relevant and timely problem with clear practical implications. The integration of multiple computational techniques is ambitious and potentially powerful. The identification of three distinct mechanistic origins provides a structured framework for understanding variant activity. The proposal of design principles and a region-specific optimization strategy adds translational value.
- **Major Concerns** The abstract lacks quantitative evidence for all three mechanistic claims. The relationship between the prereactive state and actual catalytic activity is asserted but not demonstrated. The generalizability of the findings beyond the LCC system is unclear. The deep learning component is mentioned but its specific role and contribution are not described.
- **Minor Comments** The abstract would benefit from clearer definitions of the "W" and coiled conformations. The phrase "region-specific cooperative optimization strategy" is vague without specifics. The six design principles are mentioned but not enumerated or summarized.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The combination of approaches and the focus on the prereactive stage may offer novel insights, but the abstract does not clearly differentiate this work from prior computational studies on PETases. Scientific importance: The topic is important, and the potential to guide enzyme design is significant, but the abstract does not demonstrate that the findings advance fundamental understanding beyond what is already known. Interdisciplinary readership: The work bridges computational biophysics, enzymology, and environmental science, which could appeal to a broad audience, but the abstract is written in a specialized manner that may limit accessibility. Technical soundness: Cannot be assessed from the abstract alone; no methodological details or validation are provided. Readability for nonspecialists: The abstract is dense and assumes familiarity with PETase biology and computational methods, limiting its accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting framework, but the lack of quantitative support and methodological transparency prevents a supportive recommendation. A full manuscript with detailed methods, results, and validation would be required to assess the claims properly.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that LCC-LANL exhibits enhanced interaction strength and closer proximity to the amorphous PET surface than LCC-WT, promoting substrate recruitment.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states this as a finding but provides no quantitative measures of interaction strength, distances, or statistical significance. No simulation data, error bars, or comparative metrics are presented.
- **Why it matters** Without quantitative support, the reader cannot assess whether the observed differences are meaningful or within simulation noise. The claim is central to the first proposed mechanistic origin.
- **Resolution test** Provide quantitative interaction energies, distance distributions, and statistical comparisons between LCC-LANL and LCC-WT, with appropriate error estimates and convergence assessments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that higher occupancy of the PET ester bond near the catalytic triad, coupled with dynamic interchange between "W" and coiled conformations, forms the basis for catalysis.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract asserts a link between prereactive conformational features and catalytic competence, but no data are shown to support this causal relationship. The occupancy and conformational dynamics are described qualitatively.
- **Why it matters** The central thesis is that prereactive organization explains enhanced activity. Without demonstrating a quantitative link between these features and catalytic outcomes, the claim remains speculative.
- **Resolution test** Provide occupancy values, conformational populations, and transition rates, and relate them to experimentally known or computationally predicted catalytic activities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors claim that long-range allosteric communication by distal mutations enhances prereactive organization in LCC-LANL.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract mentions "deep learning-assisted network analysis" but does not describe how this method was used to infer allosteric communication. No network metrics, communication pathways, or mutational effects are quantified.
- **Why it matters** Allosteric claims require rigorous demonstration of communication pathways and their functional relevance. Without methodological detail and quantitative results, this claim cannot be evaluated.
- **Resolution test** Describe the deep learning approach, present network analysis results such as communication scores or pathway identifications, and show how distal mutations alter these properties.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope and generalizability
- **Claim pointer** The authors propose a region-specific cooperative optimization strategy and distill six design principles for efficient PETases.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract introduces these as outcomes but provides no details on the strategy, the principles, or the evidence supporting their validity. It is unclear whether these are derived from the LCC system alone or tested across other PETases.
- **Why it matters** Design principles and optimization strategies are only useful if they are generalizable and validated. Without evidence of broader applicability, these claims may be overreaching.
- **Resolution test** Enumerate the six principles, describe the optimization strategy, and provide evidence of their applicability beyond the LCC system, such as validation on other PETase variants or experimental confirmation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of conformational states
- **Evidence pointer** Abstract, location not provided
- **Issue** The terms "W" and "coiled" conformations are introduced without definition or structural context.
- **Required correction** Define these conformations with reference to specific structural features or provide a brief description of their characteristics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Specificity
- **Affected element** Optimization strategy description
- **Evidence pointer** Abstract, location not provided
- **Issue** The "region-specific cooperative optimization strategy" is mentioned but not explained, leaving the reader uncertain about its nature.
- **Required correction** Provide a concise description of the strategy, including which regions are targeted and how cooperation is achieved.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Design principles enumeration
- **Evidence pointer** Abstract, location not provided
- **Issue** The six design principles are referenced but not listed or summarized, making it impossible to assess their value.
- **Required correction** Briefly enumerate or summarize the six principles in the abstract or indicate where they are presented in the full manuscript.

## Risk / unsupported claims
- The claim that LCC-LANL maintains closer proximity to the amorphous PET surface than LCC-WT is unsupported by quantitative data in the abstract.
- The claim that higher ester bond occupancy near the catalytic triad forms the basis for catalysis is asserted without evidence linking occupancy to catalytic outcomes.
- The claim of long-range allosteric communication by distal mutations is unsupported by any network analysis results or methodological details.
- The proposal of a region-specific cooperative optimization strategy and six design principles is presented without supporting evidence or validation.
- The overall assertion that the prereactive origins explain enhanced activity is not substantiated by data in the abstract.