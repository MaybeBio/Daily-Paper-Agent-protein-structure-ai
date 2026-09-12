## Review setup
- **Input scope** Full manuscript (including main text, figures, and supplementary information reference)
- **Assessment boundary** The manuscript as provided; supplementary material not accessible for review
- **Shared manuscript claim summary** The authors use molecular dynamics simulations to compare two cyclic peptide inhibitors (CP1 and CP2) of the Zika virus NS2B/NS3 protease, showing that CP2 preserves key intramolecular contacts upon binding, exhibits a more focused interaction network, and has more favorable binding free-energy estimates than CP1, providing a structural rationale for the experimentally observed potency difference.
- **Visible evidence base** Molecular dynamics trajectories (3 × 500 ns per system), RMSD/RMSF analyses, DSSP secondary-structure assignments, intramolecular distance distributions, residue-level interaction maps, MM/PBSA and MM/GBSA binding free-energy calculations, computational alanine scanning
- **Missing materials affecting confidence** Supplementary material (Figs. S1–S6, Tables S1–S2) is referenced but not provided; these contain essential data supporting RMSD profiles, clustering, and entropy-corrected binding energies

## Reviewer
- **Overall assessment** This is a competent computational study that uses molecular dynamics to rationalize the experimentally observed potency difference between two cyclic peptide inhibitors of the ZIKV NS2B/NS3 protease. The work is clearly presented and the methodological choices are appropriate for the stated goals. However, the study is largely descriptive and confirmatory of known experimental data, and several technical aspects limit the strength of the conclusions. The absence of the supplementary material prevents full evaluation of the evidence base.
- **Who would be interested in the results, and why** Researchers working on flaviviral protease inhibitors, particularly those interested in macrocyclic peptide design and structure-activity relationships. The study provides atomistic insight into how linker modifications affect conformational preorganization and binding, which may inform future inhibitor optimization.
- **Major strengths** 1. Clear comparative design with two structurally related inhibitors that differ only in the linker region, allowing focused investigation of linker effects. 2. Use of multiple independent replicas (3 × 500 ns) to assess reproducibility, which is appropriate for cyclic peptide systems with rugged conformational landscapes. 3. Integration of multiple analysis methods (distance distributions, interaction fingerprints, binding free energies, alanine scanning) to support the main conclusions.
- **Major Concerns** R1-M1, R1-M2, R1-M3
- **Minor Comments** R1-m1, R1-m2, R1-m3, R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (force field validation), R1-M2 (sampling convergence), R1-M3 (binding free-energy methodology)
- **Assessment against Nature-style criteria** Originality: Moderate. The study applies established computational methods to a known system and does not introduce new concepts or methodologies. Scientific importance: Moderate. The ZIKV protease is a relevant target, and understanding linker effects in cyclic peptides is of general interest, but the study is confirmatory of known experimental data rather than predictive. Interdisciplinary readership: Low. The work is specialized for computational chemists and structural biologists working on protease inhibitors. Technical soundness: Adequate but with notable concerns regarding force field validation, sampling convergence, and binding free-energy methodology. Readability for nonspecialists: Good. The manuscript is clearly written and the figures are well-designed.
- **Recommendation posture** Supportive if technical concerns are resolved, but the study would benefit from additional validation and a more critical assessment of the limitations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Force field validation
- **Claim pointer** The authors claim that the MD simulations provide a reliable atomistic description of the conformational behavior of CP1 and CP2 in solution and bound to the protease.
- **Evidence pointer** Methodology section
- **Concern** The cyclic peptides are parameterized with GAFF2, but no validation of the force field parameters for these specific macrocyclic compounds is provided. Macrocyclic peptides can have complex ring strain and torsional preferences that are not well captured by general force fields. The authors do not report whether the crystallographic geometries are stable in short test simulations, nor do they compare simulated conformational ensembles with any experimental data (e.g., NMR-derived distances or J-couplings) for validation.
- **Why it matters** Without validation, it is unclear whether the observed differences between CP1 and CP2 reflect genuine physical behavior or force field artifacts. The central claim that CP2 preserves a specific intramolecular contact while CP1 does not could be an artifact of inadequate parameterization.
- **Resolution test** Provide evidence that the GAFF2 parameters reproduce known experimental observables for these or similar macrocyclic peptides. This could include: (1) short MD simulations starting from the crystallographic structure to verify stability, (2) comparison of simulated NMR parameters (e.g., NOE distances, 3J-couplings) with experimental data if available, or (3) quantum mechanical (QM) validation of key torsional profiles in the linker region.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Sampling convergence
- **Claim pointer** The authors claim that CP2 preserves a short intramolecular contact (d1) upon binding, while CP1 loses its crystallographic contact (d2) and samples a broader bound-state ensemble.
- **Evidence pointer** Results and discussion, Fig. 4
- **Concern** The total simulation time per system is 1.5 µs (3 × 500 ns). For cyclic peptides, which can have slow conformational transitions, this may be insufficient to achieve converged sampling of the bound-state ensemble. The authors do not provide any convergence analysis (e.g., block averaging, time-evolution of key distances, or assessment of whether the d1/d2 distributions are stable over the last portion of each trajectory). The observation that CP1 loses its crystallographic d2 contact could reflect insufficient sampling rather than a genuine difference in bound-state behavior.
- **Why it matters** The central structural conclusion of the paper—that CP2 is more preorganized in the bound state—depends on the reliability of the distance distributions. If sampling is not converged, the reported distributions may be misleading.
- **Resolution test** Provide convergence diagnostics for the key intramolecular distances (d1, d2). This could include: (1) time-evolution plots showing the distance as a function of simulation time for each replica, (2) cumulative averages to assess when the distributions stabilize, or (3) extended simulations (e.g., to 1 µs per replica) to verify that the observed differences are robust.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Binding free-energy methodology
- **Claim pointer** The authors claim that CP2 has more favorable binding free-energy estimates than CP1, consistent with the experimental potency difference.
- **Evidence pointer** Results and discussion, Fig. 5, Table S2
- **Concern** The MM/PBSA and MM/GBSA calculations yield absolute binding free energies that are substantially more negative than the experimental values (e.g., MM/GBSA: −83.3 kcal/mol for CP2 vs. ΔGexp of −11.6 kcal/mol). While the authors acknowledge this discrepancy, the large systematic error raises questions about the reliability of the relative ranking. The normal-mode entropy correction reduces the magnitude but the corrected values are not reported in the main text (only in Table S2, which is not provided). Additionally, the MM/PBSA calculation uses a non-standard "CHAGB" optimization of atomic radii that is not widely validated, and the rationale for this choice is not explained.
- **Why it matters** The binding free-energy calculations are used to support the structural conclusions and to argue that CP2 achieves "more effective recognition" of the protease. If the methodology is unreliable, this claim is weakened.
- **Resolution test** (1) Report the entropy-corrected binding free energies in the main text, not just in the supplementary material. (2) Provide a sensitivity analysis showing how the relative ranking changes with different GB models (e.g., igb=5, igb=8) or PB parameters. (3) Discuss why the CHAGB model was chosen and how it affects the results compared to standard approaches. (4) Consider using a more rigorous free-energy method (e.g., FEP, TI) for the relative binding affinity, or at least acknowledge the limitations of the end-point approach more explicitly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 5
- **Issue** The description of the two inhibitors is confusing. The text states that CP1 (compound 15) has an L-valine residue in the linker, while CP2 (compound 26) has a D-homocyclohexylalanine residue. However, the figure caption (Fig. 1) describes the linker fragments differently. The relationship between the "linker region" and the "P4 substituent" is not clearly defined.
- **Required correction** Clarify the chemical structures of CP1 and CP2, explicitly defining what constitutes the "linker" versus the "macrocyclic core." Consider adding a table comparing the key structural features of the two compounds.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results and discussion
- **Evidence pointer** Fig. 4
- **Issue** The y-axis labels in Fig. 4 are not visible in the provided manuscript. The figure caption describes the distance distributions but does not specify what the y-axis represents (probability density, frequency, etc.).
- **Required correction** Ensure that all axis labels are clearly visible and defined in the figure caption.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results and discussion
- **Evidence pointer** Fig. 5
- **Issue** The per-residue energetic decomposition (Fig. 5b) shows error bars representing standard deviation across three replicas. However, with only three replicas, the standard deviation is a poor estimator of uncertainty. The authors should consider reporting the individual replica values or using a more robust measure (e.g., standard error of the mean).
- **Required correction** Report individual replica values in a supplementary table, or use a more appropriate measure of uncertainty given the small number of replicas.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The conclusions are appropriately cautious but could be strengthened by explicitly stating the limitations of the study, particularly regarding force field accuracy, sampling convergence, and the correlative nature of the findings.
- **Required correction** Add a "Limitations" paragraph to the Conclusions section, discussing the caveats mentioned above and suggesting how future work (e.g., enhanced sampling, QM/MM, experimental validation) could address them.

## Risk / unsupported claims
- The claim that CP2 "preserves a short intramolecular contact compatible with its crystallographic arrangement" while CP1 "lost its crystallographic d2 contact" is supported by the distance distributions but requires convergence analysis (R1-M2) to be fully established.
- The claim that CP2 has "more favorable binding free-energy estimates" is supported by the MM/PBSA and MM/GBSA calculations, but the large systematic error and non-standard methodology (R1-M3) mean that the quantitative ranking should be interpreted with caution.
- The claim that the NS2B segment shows "greater local conformational plasticity" in the CP2 complex (based on 5.2% bend vs. 4.0% in CP1) is based on very small differences in secondary-structure populations and may not be statistically significant.