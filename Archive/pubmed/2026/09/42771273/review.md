## Review setup
- **Input scope** Full manuscript text (Introduction, Materials and methods, Results and discussion, Conclusion) with figure legends; supplementary information referenced but not provided.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the evidence presented, and alignment with Nature-style criteria. No assessment of grammar or stylistic polish beyond readability for nonspecialists.
- **Shared manuscript claim summary** The authors use microsecond-scale molecular dynamics simulations, PCA, and Markov State Modeling to compare the conformational dynamics of Trypanosoma brucei alternative oxidase bound to the substrate analogue ubiquinone-2 versus the inhibitors ascofuranone and ferulenol. They report that inhibitor binding induces a "dynamic restriction" of the conformational free energy landscape, trapping the enzyme in a single dominant macrostate, and propose this as the mechanistic basis for high-affinity inhibition and prolonged residence time.
- **Visible evidence base** Main text figures 1–6 (figure legends only, no actual figure panels provided), Supplementary Tables S1 and Supplementary Figures S1–S2 (referenced but not provided), docking scores (values not reported in text), RMSD/RMSF/Rg values (partially reported), MSM populations (reported), hydrogen bond analysis (qualitative).
- **Missing materials affecting confidence** Actual figure panels, supplementary information (Figures S1–S2, Table S1), docking score values, MSM validation details, convergence criteria, error estimates, force field parameters for ligands, and any raw trajectory statistics. Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses an interesting and timely question: whether high-affinity inhibition of T. brucei AOX can be understood through ligand-induced reshaping of the conformational free energy landscape rather than static steric occlusion. The conceptual framework is appealing and aligns with emerging views of enzyme inhibition as a dynamic phenomenon. However, the evidence presented is insufficient to establish the central claim. The analysis relies heavily on qualitative descriptions of PCA projections and MSM populations, with limited quantitative validation. The treatment of the ferulenol system is inconsistent: it is included in the RMSD analysis but excluded from the MSM and PCA analyses, weakening the claim that both inhibitors share a unified mechanism. The "local locking, distal whipping" interpretation is intriguing but is supported only by RMSF profiles without statistical testing or a mechanistic model. The manuscript would benefit from clearer reporting of convergence, error analysis, and a more rigorous comparison between systems. The writing is generally clear, though some sections are repetitive and the distinction between PCA and tICA could be better explained for nonspecialists.

- **Who would be interested in the results, and why** Researchers in computational enzymology, drug discovery for neglected tropical diseases, and those studying conformational dynamics of membrane proteins. The conceptual framework of "dynamic restriction" as a mechanism of inhibition could interest a broader audience in chemical biology and biophysics, particularly those working on residence time as a drug design parameter. The methodological approach combining MD, PCA, and MSM is of general interest to the computational chemistry community.

- **Major Strengths**
  1. The conceptual framing is novel and timely: reframing inhibition as a dynamic, landscape-level phenomenon rather than static binding is a valuable contribution to the field.
  2. The use of microsecond-scale MD simulations with multiple replicates (3 × 1 µs per system) represents a reasonable sampling effort for a membrane protein system.
  3. The comparison between substrate analogue and inhibitor binding provides a useful internal control for isolating ligand-specific effects.
  4. The "local locking, distal whipping" observation, if validated, offers a testable mechanistic hypothesis with implications for drug design.
  5. The authors acknowledge key limitations (no explicit chemical step, no absolute koff or binding free energies) and propose appropriate future directions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "inhibitor binding caused a significant restriction of the free energy landscape into a single, constrained spatial variance" and "ASCO funnels 98.5% of the conformational ensemble into a single, deeply stabilized energy basin"
- **Evidence pointer** Figure 5, Results section "Markov state modeling and dynamic restriction"; location not provided
- **Concern** The central quantitative claim of the paper, that ASCO binding funnels 98.5% of the population into a single macrostate, is presented without any measure of statistical uncertainty. No error bars, confidence intervals, or bootstrap analyses are reported for the MSM stationary distributions. Given that the MSM is constructed from only 3 µs of total sampling per system, the statistical reliability of a 98.5% population estimate is questionable. Furthermore, the MSM analysis is performed only for UQ2 and ASCO, not for ferulenol, despite the abstract and conclusion claiming both inhibitors share a unified mechanism. The ferulenol system is excluded from the MSM, PCA, and hydrogen bond analyses, making the claim of a shared mechanism unsupported.
- **Why it matters** The 98.5% population figure is the quantitative cornerstone of the paper's central thesis. If this value is not statistically robust, the entire "dynamic restriction" mechanism is called into question. Additionally, the exclusion of ferulenol from the key analyses directly contradicts the stated conclusion that both inhibitors act via the same mechanism.
- **Resolution test** Provide uncertainty estimates for MSM populations (e.g., bootstrap or Bayesian credible intervals). Include ferulenol in the MSM and PCA analyses, or explicitly justify its exclusion and temper the claims about a unified mechanism. Report the number of transition counts and effective sample sizes per macrostate.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** "a Markovian lag time of 5.0 ns (50 steps) was selected for the transition matrix estimation" and "the C-K test exhibits minor deviations from ideal Markovian behavior for the UQ2-bound system"
- **Evidence pointer** Materials and methods, "Markov state modeling" section; Supplementary Figures S1–S2; location not provided
- **Concern** The manuscript acknowledges that the Chapman-Kolmogorov test shows deviations from Markovian behavior for the UQ2 system, yet the MSM is still used to draw quantitative conclusions about that system. The authors attribute the deviation to "unresolved hidden slow degrees of freedom" but do not demonstrate that the chosen lag time is appropriate despite this. The implied timescale spectrum is referenced but not shown in the main text. Without a clear demonstration that the MSM is a valid kinetic model for the UQ2 system, the comparison between UQ2 and ASCO dynamics is compromised.
- **Why it matters** A non-Markovian model can produce misleading stationary distributions and transition timescales. If the UQ2 MSM is unreliable, the contrast between the "broad, connected" UQ2 landscape and the "localized" ASCO landscape may be an artifact of model misspecification rather than a real biophysical difference.
- **Resolution test** Show the implied timescale spectrum and demonstrate that the chosen lag time is in a plateau region. Provide a more detailed analysis of the C-K test deviations, including whether additional tICA components or different featurizations resolve the non-Markovianity. If the UQ2 system cannot be made Markovian, acknowledge this limitation and temper the quantitative claims about its landscape.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "ASCO establishes a tighter persistent interaction network with specific anchoring residues deeply within the pocket" and "ASCO forms more frequent and sustained hydrogen bonds than UQ2 and ferulenol"
- **Evidence pointer** Figure 3C, Results section "Ligand-dependent structural dynamics"; location not provided
- **Concern** The hydrogen bond analysis is presented qualitatively. No quantitative values (e.g., average number of hydrogen bonds, occupancy percentages, lifetimes) are reported in the text. The claim that ASCO forms "more frequent and sustained" hydrogen bonds is not supported by any numerical data. Additionally, the relationship between hydrogen bond persistence and the proposed "dynamic restriction" mechanism is not explicitly established. It is unclear whether the hydrogen bond network is a cause or a consequence of the conformational restriction.
- **Why it matters** The persistent hydrogen bond network is presented as the structural basis for the dynamic restriction. Without quantitative data, this claim is anecdotal. The direction of causality is also important for the proposed mechanism: does the hydrogen bond network drive the conformational restriction, or does the restricted conformation simply stabilize pre-existing hydrogen bonds?
- **Resolution test** Report quantitative hydrogen bond statistics (average counts, occupancies, lifetimes) with standard deviations across replicates. Perform a correlation analysis between hydrogen bond persistence and conformational restriction metrics. Consider a control analysis where hydrogen bonds are disrupted (e.g., mutation or ligand modification) to test causality.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** "This 'local locking, distal whipping' behaviour suggests a mechanism of entropic compensation, where the energetic penalty of rigidifying the active site is offset by increased disorder in the C-terminal tail"
- **Evidence pointer** Figure 3B, Results section "Ligand-dependent structural dynamics"; location not provided
- **Concern** The interpretation of increased C-terminal flexibility as "entropic compensation" is speculative. No free energy decomposition is performed to demonstrate that the entropic gain from the C-terminal tail actually compensates for the entropic loss from active site rigidification. The RMSF data show increased fluctuations, but this does not necessarily translate to a favorable entropic contribution to binding. The analogy to calmodulin is suggestive but not quantitatively supported.
- **Why it matters** The entropic compensation mechanism is presented as a key insight of the study. If this claim is not supported by thermodynamic analysis, it should be framed as a hypothesis rather than a finding. Overinterpretation of RMSF data as evidence of entropic compensation could mislead future drug design efforts.
- **Resolution test** Perform an entropy decomposition analysis (e.g., quasi-harmonic or mutual information-based) to estimate the configurational entropy changes in the active site versus the C-terminus. Alternatively, frame this as a testable hypothesis and soften the language accordingly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Initial structural modeling of the apo-protein and preliminary complexes was generated using the Boltz-1 deep learning model" and "the structural alignment of the predicted complexes was performed to the 5ZDP reference"
- **Evidence pointer** Materials and methods, "Complex prediction and docking validation" section; location not provided
- **Concern** The use of Boltz-1, a deep learning model, to generate initial complexes for UQ2 and ASCO is a significant methodological choice that is not adequately justified or validated. The manuscript does not report the confidence scores from Boltz-1, the RMSD between the predicted and crystal structures (where available), or any validation of the predicted binding poses against known structure-activity relationships. The docking scores from AutoDock Vina are mentioned but not reported numerically. Without this information, the quality of the initial structures, which form the basis for all subsequent MD simulations, cannot be assessed.
- **Why it matters** If the initial predicted poses are incorrect, the entire MD simulation trajectory and all downstream analyses are compromised. The validity of the "dynamic restriction" mechanism depends on the accuracy of the starting structures.
- **Resolution test** Report Boltz-1 confidence metrics and the RMSD between predicted and crystal structures for the ferulenol system (which has a known crystal structure). Report docking scores for all ligands. Consider a cross-validation where MD simulations are initiated from multiple docking poses to ensure the results are not dependent on a single starting configuration.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3A description
- **Evidence pointer** Results section "Ligand-dependent structural dynamics"; location not provided
- **Issue** The text states "The UQ2 and ASOX systems reached an early equilibration plateau (< 100 ns) in all the replicates" but the ferulenol system is described as exhibiting "a larger initial structural readjustment before plateauing at a higher average RMSD." The figure legend does not specify which replicates are shown or how the average and standard deviation were computed across replicates.
- **Required correction** Clarify in the figure legend how the average and standard deviation were computed across the three replicates. Specify whether the ferulenol system also reached equilibration and at what time.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Docking validation
- **Evidence pointer** Materials and methods, "Complex prediction and docking validation" section; location not provided
- **Issue** The docking section mentions "evaluated based on their AutoDock Vina scoring (kcal/mol), conformational clustering, and consistency with known interactions" but no scores, cluster sizes, or interaction details are reported anywhere in the text or figures.
- **Required correction** Report the docking scores for UQ2, ASCO, and ferulenol in a table or in the text. Describe the key interactions used to validate the poses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Figure 5C and 5D
- **Evidence pointer** Figure 5 legend; location not provided
- **Issue** The figure legend describes MFPT network plots for UQ2 (5C) and ASCO (5D), but the main text only discusses the UQ2 MFPT network. The ASCO MFPT network is not described in the text, and no quantitative MFPT values are reported for either system.
- **Required correction** Describe the ASCO MFPT network in the text and report representative MFPT values for both systems. If the ASCO network is not discussed, remove it from the figure or explain its purpose.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction, paragraph 3
- **Evidence pointer** Introduction; location not provided
- **Issue** The sentence "From a hypothesis by Tonge and Pan, high-affinity inhibitors function by kinetically trapping the enzyme in non-productive binding poses which effectively decouple it from the thermal fluctuations required for catalytic turnover" is presented without a citation number, making it difficult to trace the source.
- **Required correction** Add the appropriate citation for Tonge and Pan's hypothesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Methods, "Dimensionality reduction and discretization"
- **Evidence pointer** Materials and methods, "Markov state modeling" section; location not provided
- **Issue** The text states "the components were truncated to retain 95% of the cumulative kinetic variance" but does not report how many tICA components were retained. Similarly, the number of k-means clusters (200) is stated but the justification for this specific number is only briefly mentioned.
- **Required correction** Report the number of tICA components retained and provide a more detailed justification for the choice of 200 microstates, including any sensitivity analysis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary information
- **Evidence pointer** Multiple references to Supplementary Figures S1–S2 and Table S1; location not provided
- **Issue** The supplementary material is referenced throughout but was not provided for review. Key validation data (implied timescale spectrum, C-K test results, RMSD statistics) are only available in the supplementary files.
- **Required correction** Ensure the supplementary material is complete and accessible. Consider moving the most critical validation data (e.g., implied timescale spectrum) to the main text.

## Risk / unsupported claims
- The claim that ASCO funnels 98.5% of the conformational ensemble into a single macrostate is unsupported without uncertainty estimates or validation of the MSM for the ASCO system.
- The claim that ferulenol shares the same "dynamic restriction" mechanism as ASCO is unsupported because ferulenol is excluded from the MSM, PCA, and hydrogen bond analyses.
- The claim of "entropic compensation" via the C-terminal tail is speculative and not supported by thermodynamic analysis.
- The claim that the observed "dynamic restriction" explains the picomolar affinity and prolonged residence time of ASCO is an extrapolation, as no direct residence time measurements or free energy calculations are presented.
- The quality of the initial structures generated by Boltz-1 cannot be assessed without confidence scores or validation against known structures.
- The docking results are referenced but no numerical scores are reported, making the validation of binding modes unverifiable.