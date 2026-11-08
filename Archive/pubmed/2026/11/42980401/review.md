## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors identify a C-terminal Omega-loop (Loop 3) in Candida antarctica lipase A (CALA) as the key structural element governing active pocket opening. They report that truncation or enhanced flexibility of this loop promotes conformational transitions toward the open state, that Loop 3 variants shift the optimal substrate from C16 to C14 without altering regioselectivity, and that immobilization on hydrophobic supports likely restricts Loop 3 conformation, leading to complete inactivation in anhydrous systems.
- **Visible evidence base** Abstract text only; no experimental details, simulation parameters, sequence information, or statistical analyses provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation methodology and validation, enzyme assay protocols, variant construction details, immobilization procedures, and any statistical treatment of data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting structure-function relationship in an industrially relevant enzyme, with a clear narrative connecting computational predictions to experimental validation. However, the evidence base available for review is limited to the abstract, and several claims require substantially more detail to be properly evaluated. The central claim that Loop 3 governs active pocket exposure is plausible but not established from the supplied material. The substrate selectivity shift and the immobilization-related inactivation are intriguing but lack mechanistic depth in the abstract. The work may be of interest to the biocatalysis and enzyme engineering community, but the current evidence does not fully support the strength of the conclusions as stated.
- **Who would be interested in the results, and why** Researchers in enzyme engineering, lipase biocatalysis, and protein dynamics would find these results relevant. The identification of a specific loop as a conformational regulator in CALA could inform rational engineering strategies for substrate specificity modulation and immobilization optimization. Industrial biochemists working on lipid modification or ester synthesis in anhydrous media would also be interested in the inactivation mechanism reported.
- **Major strengths** The study integrates multiscale simulations with protein engineering, which is a powerful combination for structure-function studies. The identification of a specific structural element (Loop 3) as a regulator of active pocket opening provides a concrete target for engineering. The reported shift in optimal substrate from C16 to C14 without altering regioselectivity suggests a degree of specificity control that is practically valuable. The observation regarding immobilization-induced inactivation in anhydrous systems has direct industrial relevance.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail to assess the quality of the simulations, the statistical significance of the enzymatic assay results, or the robustness of the immobilization experiments. The claim that Loop 3 "governs" active pocket exposure is strong and requires direct experimental evidence of conformational states, not just inferred transitions. The mechanism by which truncation or enhanced flexibility promotes the open state is not explained. The relationship between the conformational switching and the observed substrate shift is not mechanistically connected in the abstract.
- **Assessment against Nature-style criteria**  
  Originality: The identification of a specific Omega-loop as a conformational regulator in CALA appears novel, though similar loop-mediated gating mechanisms have been described in other lipases. The originality is moderate rather than exceptional.  
  Scientific importance: The work addresses a genuine gap in understanding CALA structure-function relationships, and the industrial relevance of CALA lends practical importance. However, the conceptual advance is incremental rather than paradigm-shifting.  
  Interdisciplinary readership: The work bridges computational biophysics, protein engineering, and biocatalysis, which could attract readers across these fields. The industrial application angle broadens potential interest.  
  Technical soundness: Cannot be fully assessed from the abstract. The integration of multiscale simulations and experiments is appropriate, but the absence of methodological detail prevents verification of technical rigor.  
  Readability for nonspecialists: The abstract is clearly written and accessible, with technical terms used appropriately. The narrative flow from identification to validation to application is logical and easy to follow.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a coherent story, but the strength of the claims exceeds what can be verified from the supplied material. A supportive posture would require access to the full manuscript to evaluate the experimental and computational evidence.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Truncation or enhancement of flexibility of this loop was found to promote conformational transitions toward the open state."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract states that truncation or enhanced flexibility promotes open-state transitions, but no experimental or computational evidence is described that directly measures conformational states. The term "found to promote" implies a causal relationship, yet the abstract does not specify how conformational transitions were observed or quantified.  
- **Why it matters** The central thesis of the paper rests on this claim. Without direct evidence of conformational state populations or transitions, the conclusion that Loop 3 "governs" active pocket exposure is not supported. Indirect evidence such as activity changes could have alternative explanations.  
- **Resolution test** Provide explicit data showing conformational state distributions for wild-type and variant enzymes, such as from enhanced sampling simulations with validated force fields, or experimental probes like FRET, EPR, or hydrogen-deuterium exchange that directly report on loop conformation and active pocket accessibility.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic clarity  
- **Claim pointer** "Loop 3 variants shift the optimal substrate from C16 to C14 without altering regioselectivity."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract reports a substrate specificity shift but does not explain the mechanistic basis for this shift. How does altering Loop 3 flexibility or length change chain-length preference? Is the effect due to altered active site geometry, substrate channel dimensions, or changes in the conformational equilibrium that favor different substrate binding modes?  
- **Why it matters** Without a mechanistic explanation, the observed substrate shift is an empirical observation rather than a design principle. The paper claims to provide "a structural basis for rational engineering," but the abstract does not articulate how the structural information translates into predictable specificity changes.  
- **Resolution test** Provide structural or simulation data showing how Loop 3 variants alter the active site environment or substrate binding channel. Correlate the degree of loop modification with the magnitude of substrate shift. Discuss whether the effect is generalizable or specific to the particular variants tested.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim overreach  
- **Claim pointer** "Immobilization on hydrophobic supports likely restricts Loop 3 conformation, leading to complete inactivation in anhydrous systems."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The word "likely" indicates uncertainty, yet the claim is presented as a finding. The abstract does not describe any direct evidence that immobilization restricts Loop 3 conformation. Alternative explanations for inactivation in anhydrous systems include solvent-induced denaturation, loss of essential water for catalytic function, or mass transfer limitations.  
- **Why it matters** This claim has direct industrial implications for immobilization strategy design. If the mechanism is incorrectly attributed to Loop 3 restriction, engineering efforts to mitigate inactivation would be misdirected. The claim as stated is speculative and should be clearly framed as a hypothesis rather than a conclusion.  
- **Resolution test** Provide direct evidence of Loop 3 conformational restriction upon immobilization, such as comparative simulation of the immobilized enzyme, or experimental probes that report on loop dynamics in the immobilized state. Alternatively, test the hypothesis by immobilizing Loop 3 variants and comparing their activity profiles in anhydrous systems.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Quantitative rigor  
- **Claim pointer** "Enzymatic assays revealed that Loop 3 variants shift the optimal substrate from C16 to C14."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative information about the magnitude of the shift, the number of variants tested, the reproducibility of the assays, or the statistical significance of the differences. Without these details, it is impossible to assess whether the reported shift is robust or within experimental noise.  
- **Why it matters** Substrate specificity profiles are central to the paper's practical claims. If the shift is small or variable across replicates, the conclusion that Loop 3 controls substrate preference would be weakened. Quantitative rigor is essential for a claim that is intended to guide engineering decisions.  
- **Resolution test** Provide full kinetic parameters (kcat, KM, kcat/KM) for all substrates tested, with error estimates and statistical comparisons. Report the number of independent replicates and the consistency of the shift across multiple variant constructs.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Terminology precision  
- **Affected element** "Omega-loop"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "Omega-loop" is used without definition or structural context. Omega-loops are a specific structural motif, and it is unclear whether Loop 3 meets the canonical definition or whether the term is used loosely.  
- **Required correction** Define the structural characteristics of Loop 3 that qualify it as an Omega-loop, or use a more neutral term such as "C-terminal loop" if the structural classification is not definitive.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Methodological transparency  
- **Affected element** "Multiscale simulations"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "multiscale simulations" without specifying the methods used. Multiscale could refer to QM/MM, coarse-grained, or a combination of approaches, each with different strengths and limitations.  
- **Required correction** Specify the simulation methods used, including the levels of theory, force fields, and timescales, in the abstract or at minimum in the full manuscript with clear justification for the multiscale approach.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Contextual framing  
- **Affected element** "Complete inactivation in anhydrous systems"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not specify what constitutes an "anhydrous system" or how inactivation was measured. Different anhydrous conditions (e.g., organic solvents, supercritical fluids, or vacuum) could have different effects on enzyme structure and function.  
- **Required correction** Define the anhydrous conditions used and describe the activity assay employed. Clarify whether inactivation was complete and irreversible or whether activity could be restored upon rehydration.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Comparative context  
- **Affected element** "Unique substrate selectivity"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract claims CALA has "unique substrate selectivity" but does not specify what makes it unique relative to other lipases. This claim is presented without comparative data.  
- **Required correction** Provide a brief comparative statement in the abstract or full manuscript that contextualizes CALA selectivity against other well-characterized lipases, with appropriate references.

## Risk / unsupported claims
- The claim that Loop 3 "governs" active pocket exposure is not supported by direct conformational evidence in the abstract.
- The claim that immobilization "likely restricts Loop 3 conformation" is speculative and presented without direct evidence.
- The claim that Loop 3 variants "shift the optimal substrate from C16 to C14" lacks quantitative data and statistical validation in the abstract.
- The mechanistic connection between Loop 3 conformational dynamics and substrate chain-length preference is not articulated.
- The generalizability of the findings to other CALA variants or reaction conditions is not addressed.
- The term "multiscale simulations" is used without methodological specification, making the computational evidence unevaluable.