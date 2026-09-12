## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no experimental details, figures, or supporting data were provided for evaluation
- **Shared manuscript claim summary** The authors report that lactone ring-opening in macrocyclic peptides can be used to generate differentiated conformations. Under kinetic control, the reaction is highly atroposelective; under thermodynamic control, reversible ring-opening equilibrates atropisomers. NMR/MD studies show the resulting atropisomers adopt markedly different conformations, from a 310-helix to noncanonical structures. In an RGD-containing macrocycle, the kinetic atropisomer mimics the integrin-binding geometry, while the thermodynamic atropisomer adopts a previously undescribed conformation. The authors claim this establishes a new strategy for controlling macrocyclic peptide conformational states.
- **Visible evidence base** Abstract text only; no figures, tables, experimental procedures, characterization data, or computational details were provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, NMR data, computational parameters, atroposelectivity values, thermodynamic data, and structural coordinates

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to conformational control in macrocyclic peptides, a topic of significant current interest in medicinal chemistry and chemical biology. The central idea, using lactone ring-opening under kinetic versus thermodynamic control to access distinct atropisomeric conformations, is potentially valuable. However, the abstract alone provides insufficient evidence to evaluate the strength of the claims. Key quantitative data, experimental validation, and structural evidence are absent. The claim that the kinetic atropisomer "recapitulates" the integrin-binding geometry is particularly consequential and would require direct structural comparison, which cannot be assessed from the abstract.
- **Who would be interested in the results, and why** Medicinal chemists working on constrained peptide therapeutics, chemical biologists studying peptide conformation, and synthetic organic chemists interested in atroposelective reactions. The potential to access distinct conformations of the same macrocyclic sequence could be relevant for structure-activity relationship studies and for designing peptides with tailored biological activities.
- **Major strengths** The conceptual framework is clear and compelling. The use of kinetic versus thermodynamic control to access different atropisomeric states of a macrocyclic peptide is an elegant idea that could have broad applicability. The inclusion of an RGD-containing macrocycle with relevance to integrin binding provides a potentially impactful demonstration. The combination of NMR and molecular dynamics to characterize conformations suggests a rigorous structural approach.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "the lactone opening is highly atroposelective across macrocyclic precursors tested"
  - **Evidence pointer** location not provided
  - **Concern** The abstract claims high atroposelectivity "across macrocyclic precursors tested" but provides no quantitative data. No diastereomeric ratios, percent yields, or number of substrates are given. The scope of "across" is undefined.
  - **Why it matters** Atroposelectivity is the central claim of the kinetic control strategy. Without quantitative selectivity data and defined substrate scope, the generality of the approach cannot be evaluated. This is the foundational claim upon which the entire strategy rests.
  - **Resolution test** Provide diastereomeric ratios for each substrate tested, the number of substrates, and the structural diversity represented. Ideally, show that selectivity is consistently high across a range of ring sizes, amino acid compositions, and lactone positions.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "the kinetic atropisomer recapitulates the 3D geometry involved in integrin binding"
  - **Evidence pointer** location not provided
  - **Concern** This is a strong structural claim. "Recapitulates" implies a direct comparison between the kinetic atropisomer conformation and the known integrin-bound conformation of RGD peptides. No evidence for this comparison is presented in the abstract.
  - **Why it matters** This claim elevates the work from a synthetic curiosity to a potentially biologically relevant finding. If the kinetic atropisomer truly mimics the bioactive conformation, this has implications for designing integrin-targeting macrocycles. However, without structural overlay, binding data, or at minimum a detailed conformational comparison, this claim is unsupported.
  - **Resolution test** Provide a structural overlay of the kinetic atropisomer with a known integrin-bound RGD conformation, or present binding affinity data for both atropisomers against integrin receptors. At minimum, show the key distances and angles of the RGD motif in the kinetic atropisomer compared to the bioactive conformation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "A combined NMR/molecular dynamics study reveals that the atropisomers arising from lactone opening can adopt markedly different conformations"
  - **Evidence pointer** location not provided
  - **Concern** The abstract states that NMR/MD studies reveal different conformations but provides no details on the number of compounds studied, the quality of the NMR data, the force fields used, the simulation lengths, or the convergence criteria. The range from "310-helix to various noncanonical conformations" is mentioned but not contextualized.
  - **Why it matters** The conformational analysis is the mechanistic foundation for the entire strategy. If the NMR assignments are ambiguous or the MD simulations are not converged, the conformational conclusions could be unreliable. The reader cannot assess the rigor of the structural characterization.
  - **Resolution test** Provide representative NMR data showing key NOE constraints, chemical shift assignments, and the agreement between experimental and calculated structures. Detail the MD protocol, including force field, water model, simulation time, and convergence metrics. Show that the conformational differences are robust across multiple independent simulations or experimental replicates.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Conceptual novelty
  - **Claim pointer** "these results establish a new strategy to control the conformational states of macrocyclic peptides"
  - **Evidence pointer** location not provided
  - **Concern** The abstract does not discuss prior art. Atroposelective synthesis of macrocycles and conformational control of peptides are both active areas. The claim of a "new strategy" requires contextualization against existing methods such as N-methylation, proline substitution, or other conformational locking strategies.
  - **Why it matters** The novelty claim is central to the paper's significance. If similar approaches have been reported, the contribution is incremental rather than transformative. The authors need to clearly articulate what is genuinely new about this approach.
  - **Resolution test** Include a discussion of prior approaches to conformational control in macrocyclic peptides and explicitly state what distinguishes this lactone ring-opening strategy from existing methods. If possible, provide a direct comparison with an established method on the same or similar substrate.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The term "differentiated conformations" is vague. It is unclear whether this means distinct stable conformations, different populations, or something else.
  - **Required correction** Define what is meant by "differentiated" in this context, perhaps as "distinct, isolable atropisomeric conformations with measurably different 3D structures."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Scope of thermodynamic control
  - **Evidence pointer** Abstract, second sentence
  - **Issue** The abstract states that reversible lactone opening "equilibrates the atropisomers" but does not indicate whether this equilibration is complete, partial, or tunable. The ratio at equilibrium is not mentioned.
  - **Required correction** Provide the equilibrium ratio or state whether the ratio can be tuned by conditions. If the equilibrium strongly favors one atropisomer, this should be stated.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Precision
  - **Affected element** Conformational description
  - **Evidence pointer** Abstract, third sentence
  - **Issue** "various noncanonical conformations" is imprecise. Without specific structural descriptors, the reader cannot gauge the significance of these conformations.
  - **Required correction** Provide specific structural descriptors for at least the key noncanonical conformations, such as turn types, backbone dihedral angles, or hydrogen bonding patterns.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Biological relevance
  - **Affected element** RGD example
  - **Evidence pointer** Abstract, fourth sentence
  - **Issue** The abstract does not state whether the RGD-containing macrocycle was tested for integrin binding. The claim is limited to geometric recapitulation, which is weaker than functional validation.
  - **Required correction** If binding data exist, include them. If not, state explicitly that the geometric similarity is computational/structural only and that functional studies are ongoing or planned.

## Risk / unsupported claims
- The claim of "high atroposelectivity across macrocyclic precursors tested" is unsupported without quantitative selectivity data and substrate scope details.
- The claim that the kinetic atropisomer "recapitulates the 3D geometry involved in integrin binding" is unsupported without structural comparison or binding data.
- The claim of "markedly different conformations" ranging from 310-helix to noncanonical structures is unverifiable without NMR data and MD details.
- The claim of establishing a "new strategy" is unverifiable without contextualization against prior art.
- The overall conclusion that this approach "control[s] the conformational states of macrocyclic peptides" is plausible but not established from the abstract alone.

## Assessment against Nature-style criteria
- **Originality** The concept of using lactone ring-opening under kinetic versus thermodynamic control to access distinct atropisomeric conformations of macrocyclic peptides appears conceptually original, though prior art cannot be assessed from the abstract alone. The idea of using the same chemical handle to access both kinetic and thermodynamic conformational states is elegant.
- **Scientific importance** If the claims hold, this could be a valuable addition to the toolkit for conformational control in macrocyclic peptides, which is directly relevant to peptide drug discovery. The RGD example, if functionally validated, would enhance importance. However, the importance is currently potential rather than demonstrated.
- **Interdisciplinary readership** The work would appeal to synthetic organic chemists, peptide chemists, structural biologists, and medicinal chemists. The conceptual framework is accessible across these disciplines, though the abstract is written in a fairly specialized language.
- **Technical soundness** Cannot be assessed from the abstract. The key technical claims, atroposelectivity and conformational characterization, require experimental data that were not provided. The rigor of the NMR/MD analysis is entirely unverifiable.
- **Readability for nonspecialists** The abstract is concise and the core concept is understandable, but terms like "atroposelective," "atropisomers," and "310-helix" assume a level of chemical sophistication. The significance of the findings for a broader audience is not articulated.

## Recommendation posture
Currently not established from the provided evidence. The conceptual framework is promising and the work could be significant, but the abstract alone does not provide sufficient evidence to evaluate the core claims. A full manuscript with experimental data, quantitative selectivity values, structural characterization, and contextualization against prior art would be required to assess whether the claims are supported. The recommendation is conditional on the quality of the full data package.