## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and conclusions
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors use MD simulations and QM/MM calculations to propose a water-assisted, stepwise fluorine-elimination mechanism for the irreversible inhibition of human ornithine aminotransferase (hOAT) by the bis-trifluoromethyl inhibitor BCF3, with specific residue contributions identified through electrostatic analysis
- **Visible evidence base** Abstract, full text sections 1-4, figures referenced as Figures 2-9, supplementary figures referenced as Figures S1-S7, methods section with computational details
- **Missing materials affecting confidence** Supplementary Information contents (detailed methods for Fβ− elimination stage, TT-Cluster parameters, VolMap analysis details, Method S1 for Boltzmann weighting), raw trajectory data, convergence criteria for MD simulations, complete QM/MM coordinate sets, validation data for QM region choice

## Reviewer
- **Overall assessment** The manuscript presents a computational investigation of a mechanistically important enzymatic inhibition process. The central proposal of water-mediated proton shuttling during sequential fluorine elimination is chemically plausible and builds on prior experimental work. However, several technical aspects require clarification and additional validation before the mechanistic conclusions can be considered fully established. The electrostatic analysis methodology, in particular, needs more rigorous justification, and the relationship between computed barriers and experimental observations should be addressed more explicitly.
- **Who would be interested in the results, and why** Researchers in computational enzymology, medicinal chemistry, and cancer metabolism would find interest. Those working on PLP-dependent enzymes and mechanism-based inactivators would value the proposed water-assisted elimination pathway. Drug discovery groups targeting hOAT for hepatocellular carcinoma therapy would benefit from the residue-level insights for inhibitor design.
- **Major strengths** The study addresses a clinically relevant target with a clear experimental foundation. The combination of MD and QM/MM methods is appropriate for the questions posed. The identification of specific residues that promote or suppress fluorine elimination provides testable hypotheses. The water-bridge mechanism offers a novel explanation for how the elimination proceeds without high-energy direct proton transfer.
- **Major Concerns** The electrostatic analysis methodology lacks sufficient detail and validation. The relationship between computed free energy barriers and experimental kinetic data is not discussed. The QM region size and level of theory may be insufficient for accurate barrier calculations. The manuscript does not address potential alternative mechanisms or validate the chosen reaction coordinate.
- **Minor Comments** Several figure references appear without adequate in-text explanation. The Boltzmann weighting procedure is not fully described. The manuscript contains some redundancy in the results and discussion sections.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The water-mediated proton-shuttle mechanism for fluorine elimination in hOAT inhibition is a novel proposal that extends prior experimental work. Scientific importance: The work has potential significance for understanding mechanism-based inactivation of PLP enzymes and for designing improved hOAT inhibitors, though the direct therapeutic impact is indirect. Interdisciplinary readership: The topic bridges enzymology, computational chemistry, and cancer biology, but the presentation is heavily computational and may not fully engage experimental or clinical readers. Technical soundness: The QM/MM methodology is standard, but several technical details require clarification and the electrostatic analysis needs stronger validation. Readability for nonspecialists: The manuscript is generally clear but assumes familiarity with QM/MM terminology and would benefit from more contextual explanation of computational methods.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The electrostatic analysis identifies Arg180 and Gly42 as promoting fluorine elimination and Phe177 as suppressing it, with the claim that these effects are significant (|ΔEi−0| > 1 kcal/mol)
- **Evidence pointer** Section 2.2, Figure 4
- **Concern** The electrostatic decomposition method is described only by a single equation with no derivation, no validation against known systems, and no discussion of its limitations. The approach of setting residue charges to zero and recomputing barriers is a crude approximation that may not capture the full electrostatic effect, particularly for charged residues like Arg180 where charge neutralization could cause significant structural reorganization. The manuscript does not specify whether geometries were re-optimized for each residue deletion or whether single-point calculations were used, which substantially affects interpretation. Additionally, the threshold of 1 kcal/mol for significance is not justified, and no error estimates or convergence checks are provided.
- **Why it matters** The residue-specific conclusions are a central deliverable of the paper and are presented as actionable insights for drug design. If the electrostatic analysis is not robust, these conclusions may be misleading. The lack of methodological detail prevents readers from assessing the reliability of these findings.
- **Resolution test** Provide a detailed description of the electrostatic analysis protocol, including whether geometries were re-optimized, how the charge deletion was implemented, and how convergence was assessed. Validate the method on a test system with known electrostatic effects. Include error estimates or replicate calculations to demonstrate robustness.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript reports Boltzmann-weighted average energy barriers of 13.0, 10.8, 16.0, 17.7, and 24.5 kcal/mol for various steps, and states that the overall reaction energies are −10.6 and −29.9 kcal/mol for the two elimination stages
- **Evidence pointer** Sections 2.3, 2.4, 2.5, Figure 5, Figure 7
- **Concern** The Boltzmann weighting procedure is referenced to Method S1 in the Supporting Information, but the main text does not describe how many conformations were sampled, how they were selected, or how the weighting was applied. The manuscript also does not report the range of individual barrier heights across the sampled conformations, which is critical for assessing whether the reported averages are meaningful. Furthermore, the relationship between these computed barriers and the experimental observation that approximately 8% of BCF3 proceeds to irreversible inactivation is not discussed. A computed barrier of 10.8 kcal/mol would imply very rapid reaction kinetics that may be inconsistent with the experimental yield.
- **Why it matters** The quantitative barrier heights are the primary quantitative output of the study. Without understanding the distribution of values and their relationship to experiment, readers cannot assess whether the computed mechanism is kinetically consistent with observed behavior.
- **Resolution test** Report the number of conformations used for Boltzmann averaging, the range of individual barriers, and the weighting scheme. Discuss how the computed barriers relate to the experimentally observed 8% inactivation yield and the time-dependent fluoride accumulation. If the barriers are inconsistent with experiment, explain the discrepancy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The QM/MM calculations use the M06-2x/def2-SVP//CHARMM27 level for geometry optimization and M06-2x/def2-TZVP//CHARMM27 for single-point energies, with a QM region of 87 atoms for the Fα− elimination stage
- **Evidence pointer** Section 3.2
- **Concern** The choice of def2-SVP for geometry optimization is a relatively small basis set for a system involving fluoride elimination, where accurate description of the leaving group and any anionic character is critical. The manuscript does not provide benchmark calculations or comparisons with larger basis sets or alternative functionals to justify this choice. Additionally, the QM region of 87 atoms, while substantial, may not capture all relevant electrostatic effects from the protein environment, particularly for a reaction involving charge separation. The manuscript does not report tests of QM region size effects on the computed barriers.
- **Why it matters** The accuracy of the computed barriers and the proposed mechanism depends critically on the QM level of theory and the size of the QM region. Without validation, the quantitative conclusions are uncertain.
- **Resolution test** Provide benchmark calculations comparing def2-SVP with larger basis sets (e.g., def2-TZVP for optimization) for representative stationary points. Test the sensitivity of the computed barriers to QM region size by including additional residues or using a larger QM region. Report the effect on the key barrier heights.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the water-mediated proton-shuttle mechanism provides an atomistic explanation for the superior inhibitory potency of the bis-trifluoromethyl scaffold compared with monofluorinated or monotrifluoromethyl analogues
- **Evidence pointer** Sections 2.1, 2.3, 2.4, Conclusions
- **Concern** The manuscript does not present any comparative calculations on monofluorinated or monotrifluoromethyl analogues to support this claim. The argument appears to rest on the qualitative observation that two fluorine atoms provide two elimination steps, but no quantitative comparison of barriers or binding affinities is provided. Without such comparative data, the claim that the mechanism explains the superior potency of the bis-trifluoromethyl scaffold is speculative.
- **Why it matters** The comparative potency of different inhibitors is a key experimental observation that the computational model should explain. If the model cannot distinguish between analogues, its predictive value for drug design is limited.
- **Resolution test** Perform QM/MM calculations on the monofluorinated and monotrifluoromethyl analogues to compare their elimination barriers and binding modes with BCF3. If such calculations are not feasible, clearly state this limitation and temper the claim accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1, Figure 3
- **Evidence pointer** Figure 3
- **Issue** The description of interactions in Figure 3a mentions salt-bridge, C–F···X, and hydrophobic interactions, but the text does not clearly define what "C–F···X" represents or how these interactions were identified.
- **Required correction** Define the interaction types and describe the criteria used to identify them in the figure legend or main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The manuscript states that the system comprised 2099 atoms, which is relatively small for a protein simulation. The text does not clarify whether this includes only the active site region or the entire protein, and how the stochastic boundary was defined.
- **Required correction** Clarify the system composition, including the protein size, the definition of the stochastic boundary, and whether the small atom count reflects a truncated system.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.3
- **Evidence pointer** Figure 5, Figure S4a, Figure S6
- **Issue** The text mentions a direct proton-transfer pathway with a barrier of 28.0 kcal/mol but does not explain why this pathway was considered or how it was modeled, beyond referencing supplementary figures.
- **Required correction** Provide a brief description of the direct pathway calculation and its relevance to the proposed water-mediated mechanism.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.4
- **Evidence pointer** Figure 7, Figure S5a, Figure S7
- **Issue** The Fβ− elimination mechanism is described as involving three successive steps, but the text does not clearly delineate the individual steps or their corresponding barriers and transition states.
- **Required correction** Provide a step-by-step description of the Fβ− elimination pathway with clear reference to each transition state and intermediate.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.5, Figure 8, Figure 9
- **Evidence pointer** Figure 8, Figure 9
- **Issue** The ESP and NCI analyses are described qualitatively, but the text does not explain how these analyses support the proposed mechanism beyond general statements about stabilization.
- **Required correction** Provide specific examples of how the ESP features and NCI interactions correlate with the proposed reaction steps and residue contributions.

## Risk / unsupported claims
- The claim that the bis-trifluoromethyl scaffold's superior potency is explained by the proposed mechanism is unsupported without comparative calculations on analogues
- The electrostatic decomposition results identifying specific residues as promoters or suppressors are not validated against experimental mutagenesis data
- The statement that the reaction is "kinetically irreversible" based on computed exothermicity and fluoride release is not fully supported without kinetic analysis
- The water occupancy analysis is referenced but not described in sufficient detail to assess its reliability
- The relationship between the computed barriers and the experimentally observed 8% inactivation yield is not addressed