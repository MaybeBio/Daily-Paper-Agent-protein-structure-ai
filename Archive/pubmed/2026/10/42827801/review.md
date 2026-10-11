## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) and metadata
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency as presented in the supplied material
- **Shared manuscript claim summary** The authors propose that site-specific phosphorylation of Ser352 in the Tau R4 domain acts as a pH-sensitive molecular switch, driving a condensate-to-fibril transition specifically under acidosis conditions (pH drop from ~7.1 to ~6.5), via protonation of the phosphoserine that stabilizes a compact β-hairpin conformation.
- **Visible evidence base** Peptide library screening with fluorescence microscopy; ThT fluorescence assay; FRAP; 1H and 31P NMR titrations; MD simulations; SEM imaging
- **Missing materials affecting confidence** Raw spectra, full microscopy images, statistical analysis details, MD simulation parameters and convergence data, exact sample sizes, replicate numbers, and error analysis are not fully provided in the supplied text

## Reviewer
- **Overall assessment** The manuscript addresses an interesting and potentially important question regarding the coupling between site-specific phosphorylation and pH-dependent Tau aggregation. The central claim, that Ser352 phosphorylation uniquely enables acid-triggered fibril formation through a protonation-dependent mechanism, is plausible and mechanistically appealing. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. The NMR titrations were performed at concentrations and conditions that differ from the microscopy experiments, and the relationship between the molecular events reported by NMR and the macroscopic phase transition observed by microscopy is not fully established. The MD simulations, while supportive, are not sufficiently described to assess their validity. The claim of site-specificity rests on a single phosphoserine position, but the mechanistic explanation for why other phosphorylation sites do not show similar behavior is largely speculative. The manuscript would benefit from additional quantitative analysis and clearer presentation of controls.
- **Who would be interested in the results, and why** Researchers studying Tau aggregation mechanisms, phase separation in neurodegeneration, post-translational modification effects on protein aggregation, and the role of cellular pH in disease. The work may also interest those developing therapeutic strategies targeting phosphorylation-dependent aggregation.
- **Major strengths** The systematic screening of all phosphorylation patterns in the R4 domain is a rigorous approach. The combination of experimental and computational methods provides complementary perspectives. The identification of a single phosphorylation site with a unique pH-dependent aggregation phenotype is a clear and testable finding. The use of multiple biophysical techniques strengthens the phenomenological description.
- **Major Concerns**
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** The quantitative relationship between NMR-derived pKa values and the macroscopic phase transition pH is not rigorously established. The MD simulation methodology is underdescribed. The claim of irreversibility is based on a single experimental condition.
- **Assessment against Nature-style criteria** Originality: The concept of a single phosphorylation site acting as a pH-dependent switch is novel and potentially significant. Scientific importance: The work addresses a clinically relevant question and may have implications for understanding Tau pathology. Interdisciplinary readership: The work bridges biophysics, cell biology, and neurochemistry, which could attract broad interest. Technical soundness: The experimental design is generally sound, but several technical details and controls are missing. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume specialized knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative consistency
- **Claim pointer** The authors claim that the protonation of pSer352, with an apparent pKa of 6.53 ± 0.02, is responsible for the condensate-to-fibril transition observed between pH 6.7 and 6.5.
- **Evidence pointer** Results section, Figures 3a, 6b, 8b; location not provided
- **Concern** The NMR titrations were performed at 2 mM peptide concentration, while the microscopy experiments were performed at 50 µM. The relationship between the molecular pKa measured by NMR and the macroscopic phase transition pH observed by microscopy is not quantitatively established. The authors report a critical pH of 6.80 ± 0.02 for droplet diameter and 6.81 ± 0.02 for Hα chemical shift, but the 31P pKa is 6.53 ± 0.02. These values differ by approximately 0.3 pH units, and the manuscript does not explain whether this difference is expected or significant. Furthermore, the NMR experiments were conducted in the presence of 0.002% PEG, while the microscopy experiments used 5% PEG, which could affect the phase behavior.
- **Why it matters** The central mechanistic claim is that protonation of pSer352 drives the phase transition. If the pKa values from different methods do not align, the causal link between protonation and aggregation is weakened. The concentration difference between NMR and microscopy experiments could mean that the molecular events observed by NMR are not directly relevant to the phase transition observed at lower concentrations.
- **Resolution test** The authors should perform NMR titrations at concentrations closer to those used in microscopy, or provide a quantitative model that accounts for the concentration difference. They should also explain the 0.3 pH unit discrepancy between the 31P pKa and the Hα/droplet diameter midpoints.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations show that protonation of pSer352 stabilizes the β-hairpin and reduces inter-sheet distance, supporting the experimental findings.
- **Evidence pointer** Methods section, Molecular dynamics simulations; Results section, Figures 5, 6d, 7c-d; location not provided
- **Concern** The MD simulation methodology is underdescribed. The authors state that simulations were performed for 100 ns for each oligomer model, but do not provide details on the number of replicates, the equilibration protocol, the choice of force field parameters for the phosphorylated residues, or the criteria for assessing convergence. The RMSD analysis is mentioned but not shown. The simulations were performed at 330 K, which is above physiological temperature, and the rationale for this choice is not explained. The structural analyses (RMSF, DSSP, inter-sheet distances) are described but the results are only partially presented. The authors also do not discuss the limitations of using a minimal octamer model to represent the full fibril structure.
- **Why it matters** The MD simulations are a key component of the mechanistic argument. Without adequate description of the methodology and validation, the reliability of the simulation results cannot be assessed. The choice of 330 K is unusual and could affect the conclusions about stability.
- **Resolution test** The authors should provide full details of the simulation setup, including force field parameters for phosphoserine, equilibration protocol, number of replicates, and convergence criteria. They should justify the choice of 330 K and provide RMSD plots to demonstrate convergence. Ideally, they should also perform simulations at 310 K to confirm that the results are not temperature-dependent.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the condensate-to-fibril transition is irreversible, based on the observation that aggregates formed at pH 6.5 did not revert to condensates when pH was restored to 7.1.
- **Evidence pointer** Results section, Figure 3c; location not provided
- **Concern** The irreversibility claim is based on a single experimental condition. The authors restored pH to 7.1 in a single step and observed no reversion, but they do not report the timescale of observation, whether the samples were monitored for extended periods, or whether any intermediate states were observed. The claim of irreversibility has significant implications for the proposed mechanism, as it suggests a kinetic trap rather than a thermodynamically driven transition. The authors do not discuss whether the irreversibility is due to the formation of kinetically stable fibrils or to the loss of some component required for reversion.
- **Why it matters** The irreversibility of the transition is a key feature of the proposed mechanism and has implications for understanding the progression of Tau pathology. If the transition is reversible on longer timescales, the interpretation of the data would change.
- **Resolution test** The authors should provide a more detailed analysis of the reversibility, including longer observation times, multiple pH cycling experiments, and possibly seeding experiments to test whether the aggregates can nucleate new fibril formation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive rigor
- **Claim pointer** The authors claim that the position of pSer352 within the β-hairpin core is unique among the three phosphorylation sites, explaining why only this site drives aggregation.
- **Evidence pointer** Discussion section; location not provided
- **Concern** The explanation for site-specificity is largely based on structural reasoning from the MD simulations, but the authors do not provide direct experimental evidence that the other phosphorylation sites (Ser341, Ser356) are positioned differently relative to the hydrophobic core. The claim that dual phosphorylation involving pSer352 prevents condensation is based on the observation that 2P341,352 and 2P352,356 did not condense, but the authors do not provide a mechanistic explanation for this observation. The possibility that the effects are due to changes in net charge rather than specific structural positioning is not fully explored.
- **Why it matters** The site-specificity of the effect is a central claim of the manuscript. Without direct evidence for the structural basis of this specificity, the explanation remains speculative.
- **Resolution test** The authors should provide additional experimental data, such as mutagenesis studies replacing Ser352 with other residues, or comparative structural analysis of the different phosphopeptides, to support the claim of unique positioning.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that "a specific phosphorylation event in the Tau R4 domain is coupled to this pH drop to drive a defined phase transition from condensates to fibrils." This is clear, but the abstract could benefit from a brief mention of the methodological approach used to establish this, as the combination of experimental and computational methods is a strength of the work.
- **Required correction** Consider adding a sentence in the abstract summarizing the key methods used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, screening data
- **Evidence pointer** Results section, Figure 1b; location not provided
- **Issue** The screening results are presented as a summary, but the full data for all peptides in the library are not shown. The authors state that "only 1P352 gave a significantly high ThT fluorescence" but do not provide the quantitative values for the other peptides.
- **Required correction** Provide a supplementary figure or table showing the ThT fluorescence values for all peptides in the library.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Droplet diameter measurements
- **Evidence pointer** Results section, Figure 3a; location not provided
- **Issue** The droplet diameter measurements are reported with standard deviations, but the number of measurements and the statistical test used to determine the critical pH are not stated.
- **Required correction** Report the number of droplets measured per condition and the statistical method used for the sigmoidal fit.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** NMR experiments
- **Evidence pointer** Methods section, NMR experiments; location not provided
- **Issue** The NMR experiments were performed at 2 mM peptide concentration, which is significantly higher than the concentration used in the microscopy experiments. The authors do not discuss whether the aggregation state of the peptide at this concentration could affect the NMR measurements.
- **Required correction** Add a brief discussion of the potential effects of concentration on the NMR results and whether the peptide remains monomeric or oligomeric under the NMR conditions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion section
- **Evidence pointer** Discussion section; location not provided
- **Issue** The term "glass-like conglomerated droplets" is used to describe the state at pH 6.7. This is a descriptive term that may not be well-defined for all readers.
- **Required correction** Consider providing a more precise definition or a reference for this term.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** SEM analysis
- **Evidence pointer** Results section, Figure 4; location not provided
- **Issue** The SEM analysis shows filament morphology, but the authors do not provide a quantitative comparison of filament widths between conditions or a statistical analysis.
- **Required correction** Provide quantitative measurements of filament widths and statistical comparison if applicable.

## Risk / unsupported claims
- The claim that the observed pKa of 6.53 ± 0.02 for pSer352 directly corresponds to the pH at which the phase transition occurs is not fully supported, given the 0.3 pH unit discrepancy with the Hα and droplet diameter midpoints.
- The claim that the condensate-to-fibril transition is irreversible is based on limited experimental evidence.
- The mechanistic explanation for why other phosphorylation sites do not drive aggregation is speculative and not directly tested.
- The MD simulation results are presented as supportive evidence, but the methodology is insufficiently described to assess their validity.
- The relationship between the minimal R4 peptide system and full-length Tau in cellular contexts is not discussed, and the authors do not address whether the observed behavior would be expected in the context of the full protein.