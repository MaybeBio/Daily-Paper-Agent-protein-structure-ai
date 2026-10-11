## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no figures, methods, or supplementary material were provided
- **Shared manuscript claim summary** The authors report a computational structural analysis of an 89-kDa periplasmic protein from the endonuclear symbiont *Holospora obtusa*, proposing that pH-dependent conformational change, driven by vacuolar acidification, may facilitate host invasion.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, AlphaFold2 confidence metrics, molecular dynamics simulation parameters, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational hypothesis linking pH change to conformational reorientation in a symbiont invasion protein. However, the evidence base is limited to sequence analysis and two simulation conditions, and the authors explicitly state that no specific pH-dependent interaction was identified. The proposed mechanism therefore remains speculative. The work may interest researchers in symbiosis, microbial invasion, and computational structural biology, but the current abstract does not establish the functional relevance of the observed conformational difference.
- **Who would be interested in the results, and why** Researchers studying intracellular symbiosis, particularly the molecular mechanisms of host invasion by bacterial endosymbionts, will find the structural characterization of a novel protein family relevant. Computational biologists interested in pH-dependent conformational dynamics and AlphaFold2-based structure prediction may also find the methodological approach of interest.
- **Major strengths** The study applies state-of-the-art computational methods (AlphaFold2, molecular dynamics, DynDom) to a biologically important but understudied system. The authors are appropriately cautious in framing the pH-dependent conformational change as a testable hypothesis rather than a demonstrated mechanism. The explicit reporting of the absence of a specific protonation-dependent interaction is scientifically honest.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that "acidification of the digestive vacuole may promote this reorientation, thereby repositioning the N-terminal membrane-anchoring module at the bacterial surface as an early step toward escape from the vacuole."
  - **Evidence pointer** Abstract, final sentence; location not provided
  - **Concern** The proposed biological mechanism is presented as a hypothesis, but the abstract provides no evidence connecting the simulated conformational change to actual vacuolar acidification or to the functional process of vacuole escape. The simulations show a pH-dependent charge difference and a rigid-body rotation, but the authors state that no specific protonation-dependent interaction was identified. Without a mechanistic link or experimental validation, the connection between the computational observation and the proposed biological role is unsupported.
  - **Why it matters** The central claim of the paper, as stated in the title and abstract, is that the predicted structure suggests a pH-dependent conformational change with functional relevance. If the conformational change cannot be mechanistically linked to pH sensing or to the invasion process, the biological significance of the structural observation remains unclear.
  - **Resolution test** Provide experimental evidence (for example, pH-dependent conformational assays, mutagenesis of candidate residues, or functional assays in *Paramecium*) or identify a specific protonation-dependent interaction that can be tested. Alternatively, clearly reframe the claim as purely structural without functional inference.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical validation
  - **Claim pointer** The abstract claims that "AlphaFold2 modeling followed by molecular dynamics indicated that the C-terminal region forms an antiparallel, spectrin-repeat-like helical solenoid containing a localized three-helix coiled-coil."
  - **Evidence pointer** Abstract, methods description; location not provided
  - **Concern** No confidence metrics for the AlphaFold2 prediction are reported. The abstract does not state the predicted local distance difference test (pLDDT) scores, the predicted aligned error (PAE) values, or whether the model was validated against any experimental data. The reliability of the predicted structure, particularly for the C-terminal region, is therefore unknown.
  - **Why it matters** AlphaFold2 predictions can be unreliable for regions with low sequence coverage or for novel protein folds. The claim of a spectrin-repeat-like solenoid is a specific structural assertion that requires confidence assessment. Without this information, the structural basis of the entire study is not verifiable.
  - **Resolution test** Report pLDDT and PAE scores for the model, and discuss regions of low confidence. If available, provide any experimental validation (for example, circular dichroism, small-angle X-ray scattering, or cross-linking data) supporting the predicted secondary and tertiary structure.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Simulation robustness
  - **Claim pointer** The abstract claims that "Independent simulations at these pH values differed mainly in the relative orientation of the N-terminal core and C-terminal rod, described by DynDom as an approximately 35 degrees rigid-body rotation about a hinge centered on Gly291."
  - **Evidence pointer** Abstract, simulation description; location not provided
  - **Concern** The abstract reports only two simulation conditions (pH 4 and pH 7) and does not describe the number of replicates, simulation length, force field, or convergence criteria. The observation of a single conformational difference between two conditions could be a sampling artifact rather than a robust pH-dependent effect.
  - **Why it matters** Molecular dynamics simulations are sensitive to initial conditions and sampling length. A single pair of simulations is insufficient to establish a reproducible pH-dependent conformational change, particularly when no specific protonation-dependent interaction is identified.
  - **Resolution test** Provide details on simulation replicates, length, and convergence. Show that the observed conformational difference is reproducible across independent simulations and is not dependent on initial model coordinates.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, charge difference statement
  - **Evidence pointer** Abstract, "becoming 55 units more positive at pH 4 than at pH 7"; location not provided
  - **Issue** The statement "55 units more positive" is ambiguous. It is unclear whether this refers to a net charge difference of +55 elementary charges, a change in electrostatic potential, or another metric.
  - **Required correction** Specify the exact metric used (for example, net protein charge in elementary charge units) and the method of calculation (for example, PROPKA or constant-pH molecular dynamics).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Abstract, "invasion-tip protein"
  - **Evidence pointer** Abstract, title and first sentence; location not provided
  - **Issue** The term "invasion-tip protein" is used without definition or context. It is unclear whether this is an established term in the *Holospora* literature or a new designation introduced by the authors.
  - **Required correction** Define the term on first use and clarify whether it refers to a structural feature, a functional role, or both.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract, sequence-based analysis
  - **Evidence pointer** Abstract, "Sequence-based analyses placed this protein within a Holospora-specific family"; location not provided
  - **Issue** The abstract does not specify what sequence-based analyses were performed (for example, hidden Markov model searches, phylogenetic analysis, or domain prediction) or the significance of the family assignment.
  - **Required correction** Briefly describe the method used for family assignment and the confidence of the placement.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no mechanistic link between pH change and conformational reorientation), R1-M2 (no confidence metrics for the structural prediction), R1-M3 (insufficient simulation details to establish robustness)
- **Assessment against Nature-style criteria**  
  *Originality*: The study addresses a novel protein in an understudied symbiosis system, and the application of AlphaFold2 to a pH-dependent conformational hypothesis is not routine. However, the abstract does not demonstrate that the findings are conceptually novel beyond the specific system.  
  *Scientific importance*: The potential importance lies in understanding how bacterial endosymbionts invade host nuclei. The current abstract does not establish that the proposed mechanism is generalizable or that it advances fundamental understanding beyond this specific case.  
  *Interdisciplinary readership*: The work may appeal to microbiologists, cell biologists, and computational structural biologists. The abstract is written in a way that is accessible to these groups, but the lack of mechanistic detail limits broader appeal.  
  *Technical soundness*: The computational approach is appropriate, but the absence of confidence metrics and simulation details prevents assessment of technical rigor.  
  *Readability for nonspecialists*: The abstract is generally clear, but terms such as "spectrin-repeat-like helical solenoid" and "DynDom" are used without explanation, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible but unverified hypothesis. The authors should address the technical concerns (confidence metrics, simulation robustness) and either provide a mechanistic link or reframe the claims as purely structural before the case for a pH-dependent functional mechanism can be considered.

## Risk / unsupported claims
- The claim that vacuolar acidification promotes the conformational reorientation is unsupported, as no specific pH-dependent interaction was identified and no experimental evidence links the simulated change to the biological process.
- The claim that the protein is "implicated in escape from the host digestive vacuole and macronuclear invasion" is presented without supporting evidence in the abstract; the basis for this implication is not described.
- The functional significance of the predicted conformational change is not established; the abstract states it as a hypothesis, but the framing in the title implies a stronger connection than the evidence supports.