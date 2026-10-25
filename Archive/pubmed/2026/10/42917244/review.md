## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report all-atom molecular dynamics simulations of seven keratin-derived antimicrobial peptides (KAMPs) and Pw-Antibac123, examining conformational dynamics, aggregation behavior in aqueous solution, and membrane interactions of KAMP-18C with model Gram-positive lipid bilayers. They report verification of noncanonical KAMP structure, validation of the Pw-Antibac123 model, concentration-dependent self-assembly driven by interpeptide hydrogen bonds and electrostatics, identification of synergistic amino acid pairs, and assessment of artificial pore stability in lipid bilayers.
- **Visible evidence base** Abstract text only; no simulation details, force field parameters, system sizes, simulation timescales, convergence criteria, or quantitative results are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation methodology, force field validation, system preparation details, analysis protocols, and any quantitative data supporting the stated findings

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational study of a class of antimicrobial peptides that deviate from canonical AMP characteristics. The scope is broad, covering conformational dynamics, aggregation, and membrane interactions, which may be too ambitious for a single study to address with sufficient depth. The key claims regarding structural verification, aggregation mechanisms, and membrane pore stability cannot be evaluated from the abstract alone. The connection to proposed mechanisms of action for AMPs is mentioned but not substantiated. The work may be of interest to the computational biophysics and antimicrobial peptide communities, but the evidence base provided is insufficient to assess technical soundness or the strength of the conclusions.
- **Who would be interested in the results, and why** Computational biophysicists studying peptide self-assembly and membrane interactions would find the methodological approach relevant. Researchers in antimicrobial peptide discovery and mechanism elucidation would be interested in the noncanonical KAMP behavior, particularly the absence of net positive charge and ordered secondary structure. The glycine-rich sequence analysis and amino acid pair synergies may interest those studying sequence-structure-function relationships in AMPs. The Pw-Antibac123 model validation could be relevant to researchers working on keratin-derived peptides from agricultural waste.
- **Major strengths** The study addresses a genuinely under-explored class of antimicrobial peptides with noncanonical features, which could provide new insights into AMP mechanisms. The use of unbiased all-atom MD simulations is appropriate for studying conformational dynamics and aggregation. The inclusion of multiple KAMP family members plus a distinct keratin-derived peptide provides some breadth. The explicit consideration of concentration-dependent aggregation and membrane interaction mechanisms addresses important questions in AMP biophysics.
- **Major Concerns** The following concerns are identified from the supplied material.
- **Minor Comments** The following comments are identified from the supplied material.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The focus on noncanonical AMPs is a point of interest, but the abstract does not establish what is conceptually novel beyond applying standard MD approaches to a new peptide family. Scientific importance: The potential importance for understanding AMP mechanisms is real, but the abstract does not demonstrate that the findings change current understanding. Interdisciplinary readership: The topic could appeal to biophysicists, microbiologists, and materials scientists, but the abstract is written in a specialized manner that may limit broader accessibility. Technical soundness: Cannot be assessed from the abstract; no methodological details or validation are provided. Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with MD simulations and AMP terminology; the significance of the findings is not framed for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a potentially valuable study, but the absence of quantitative results, methodological details, and clear mechanistic conclusions prevents assessment of whether the claims are supported. A full manuscript review would be required to determine if the technical concerns can be resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their simulations "verify the noncanonical structure of KAMPs" and "validate the molecular model of Pw-Antibac123."
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract provides no quantitative criteria for what constitutes verification or validation. No comparison to experimental data, no reference structures, no metrics such as RMSD, secondary structure populations, or free energy estimates are presented. The term "validate" implies comparison against an external reference, but no such reference is described.
- **Why it matters** Verification and validation claims are foundational to the entire study. If the structural claims are not rigorously established against appropriate references, all subsequent analysis of aggregation and membrane interactions rests on an unvalidated model.
- **Resolution test** The full manuscript must provide explicit validation metrics, including comparison to experimental structural data where available, convergence analysis, and statistical uncertainty estimates for the structural observables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "increasing the peptide concentration in the aqueous solution leads to self-assembly and peptide aggregation, due to the development of interpeptide hydrogen bonds and the strong effect of electrostatic interactions."
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract states a causal mechanism for aggregation but provides no quantitative evidence. No cluster size distributions, aggregation free energies, hydrogen bond statistics, or electrostatic energy decomposition are reported. The claim that electrostatics are "strong" is particularly problematic given that KAMPs are described as lacking a net positive charge, which raises questions about what electrostatic interactions are being referenced.
- **Why it matters** The aggregation mechanism is a central finding of the study. Without quantitative support, the causal attribution to hydrogen bonding and electrostatics is speculative. The apparent contradiction between the lack of net charge and strong electrostatic effects needs explicit resolution.
- **Resolution test** The full manuscript must provide quantitative aggregation metrics, including cluster size distributions as a function of concentration, hydrogen bond lifetimes and occupancies, and electrostatic interaction energies with appropriate error bars. The role of electrostatics must be reconciled with the reported lack of net charge.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to "identify strong synergies between specific amino acid pairs, such as serine and glycine, valine and leucine, and arginine and isoleucine."
- **Evidence pointer** Abstract; location not provided
- **Concern** The concept of "synergy" between amino acid pairs is not defined in the abstract. No statistical measure, interaction energy calculation, or co-variation analysis is described. It is unclear whether this refers to correlated conformational preferences, favorable interaction energies, or some other property. The selection of these specific pairs appears arbitrary without a systematic analysis framework.
- **Why it matters** This claim suggests a sequence-structure relationship that could be mechanistically important, but without a clear definition and quantitative support, it cannot be evaluated or reproduced.
- **Resolution test** The full manuscript must define the synergy metric, describe the statistical or energetic analysis used, and provide quantitative results with significance testing for all amino acid pairs, not just the highlighted examples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "since spontaneous aggregation is not observed, we construct artificial pores and embed peptides within the membrane to assess the stability of these systems."
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract reports a negative result (no spontaneous aggregation) and then describes a strategy of constructing artificial pores. However, no results from these simulations are reported. The stability of the constructed pores is not described, and the correlation with "proposed mechanisms of action for AMPs" is mentioned but not elaborated.
- **Why it matters** The membrane interaction component is a major part of the study, yet the abstract provides no findings. The reader cannot assess whether the artificial pore approach was successful, whether the pores were stable, or what mechanistic insights were obtained.
- **Resolution test** The full manuscript must report quantitative results on pore stability, including structural metrics over simulation time, comparison to control simulations, and a clear articulation of how these results relate to specific proposed AMP mechanisms of action.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Study scope
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract covers three distinct topics (conformational dynamics, aggregation, membrane interactions) in a single study, but the connections between these topics are not made explicit. The reader is left to infer how the dilute solution behavior relates to the membrane interaction studies.
- **Required correction** Provide a sentence in the abstract that explicitly links the three components of the study and explains the logical progression from solution behavior to membrane interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Simulation details
- **Evidence pointer** Abstract; location not provided
- **Issue** No simulation timescales, system sizes, or force field details are mentioned. For a computational study, these details are essential for the reader to assess the adequacy of sampling and the reliability of the results.
- **Required correction** Include key simulation parameters in the abstract, such as total simulation time per system, number of peptides per simulation box, and the force field used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Biological relevance
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not explain why the specific model membranes chosen (Gram-positive lipid bilayers) are relevant to the biological function of KAMPs, nor does it address whether the simulation conditions are physiologically relevant.
- **Required correction** Add a brief statement justifying the choice of model membranes and discussing the physiological relevance of the simulation conditions.

## Risk / unsupported claims
- The claim that KAMP structures are "verified" as noncanonical is unsupported without quantitative comparison to reference data.
- The claim that Pw-Antibac123 model is "validated" is unsupported without specification of the validation reference.
- The causal mechanism for aggregation (hydrogen bonds and electrostatics) is unsupported without quantitative energy or interaction analysis.
- The identification of "strong synergies" between specific amino acid pairs is unsupported without a defined metric or statistical analysis.
- The statement that spontaneous aggregation is not observed is a negative result that cannot be evaluated without knowledge of simulation timescales and concentrations tested.
- The correlation of findings with "proposed mechanisms of action for AMPs" is mentioned but not substantiated with any specific mechanistic conclusions.
- All quantitative results, including any numerical values for structural properties, aggregation metrics, or pore stability, are absent from the abstract and therefore cannot be assessed.