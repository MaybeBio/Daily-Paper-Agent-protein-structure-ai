## Review setup
- **Input scope** Full manuscript (including Introduction, Materials and methods, Results and discussion, Conclusions, and Supplementary Information)
- **Assessment boundary** Computational predictions only; no experimental validation data are provided
- **Shared manuscript claim summary** The authors identify three antimicrobial peptides (33,035, 17,047, and 58,620) from a library of 6,615 sequences as computational candidates for inhibiting SARS-CoV-2 papain-like protease (PLpro) through protein-peptide docking, molecular dynamics simulations, and MM/PBSA binding energy analysis.
- **Visible evidence base** Docking scores, MD trajectories (RMSD, RMSF, Rg, H-bond occupancy), MM/PBSA energy components, toxicity predictions, and comparative analyses with known inhibitors (VIR251, p18, p28, salinomycin, ouabain)
- **Missing materials affecting confidence** No experimental validation (enzymatic assays, antiviral activity, cytotoxicity); no raw trajectory files or force field parameter files; no explicit convergence analysis for MD simulations; no code or configuration files for reproducibility

## Reviewer
- **Overall assessment** This manuscript presents a computational screening workflow to identify antimicrobial peptides as potential inhibitors of SARS-CoV-2 PLpro. The study is methodologically sound in its use of established computational tools (HPEPDOCK, GROMACS, MM/PBSA) and includes appropriate controls (VIR251 redocking, p18/p28 benchmarks). However, the work is entirely computational, and the claims of "candidates" and "inhibitory potential" are not supported by experimental evidence. The manuscript would benefit from clearer framing as a computational prediction study, with explicit acknowledgment that all findings require experimental validation. The normalized energy metrics are a useful addition but do not overcome the fundamental limitation of lacking experimental confirmation.
- **Who would be interested in the results, and why** Computational chemists and structural biologists working on antiviral drug discovery, particularly those interested in peptide-based inhibitors of SARS-CoV-2 targets. The workflow and normalized energy metrics may be of methodological interest. The specific peptide candidates may be of interest to experimental groups seeking starting points for PLpro inhibitor development.
- **Major strengths** 1. Systematic computational workflow integrating docking, MD, and MM/PBSA with triplicate simulations for statistical robustness. 2. Inclusion of known inhibitors (VIR251, p18, p28) as benchmarks for comparison. 3. Normalization of binding energies by molecular weight to enable cross-molecular comparisons. 4. Explicit discussion of computational limitations and translational challenges.
- **Major Concerns** 
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence mismatch
- **Claim pointer** "peptide 17,047 emerged as the most promising scaffold" and "peptide 33,035 showed the strongest computational binding profile" (Conclusions)
- **Evidence pointer** Tables 1-5, Figures 2-9
- **Concern** The manuscript presents these peptides as "candidates" and "promising scaffolds" for PLpro inhibition, but all evidence is computational. No experimental validation (enzymatic inhibition assays, antiviral activity, cytotoxicity) is provided. The MM/PBSA binding energies, while negative, are not calibrated against experimental binding affinities for any of the tested peptides. The authors acknowledge this limitation in the "Limitations of computational predictions" section but the Conclusions and Abstract frame the results as if the candidates have been established.
- **Why it matters** Without experimental validation, the claim that these peptides are "candidates" for PLpro inhibition is unsupported. Computational predictions can have high false-positive rates, and the field requires experimental confirmation before any peptide can be considered a genuine candidate. The current framing may mislead readers about the maturity of the findings.
- **Resolution test** Provide experimental evidence (e.g., enzymatic inhibition IC50 values, binding affinity measurements by SPR or ITC, antiviral activity in cell culture) for at least the top candidate peptides. Alternatively, reframe the manuscript explicitly as a computational prediction study and remove all language implying established inhibitory activity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** "The catalytic site, comprising the conserved catalytic triad Cys111–His272–Asp286, was used as a reference for molecular modeling analyses" (Materials and methods)
- **Evidence pointer** Section "Protein-peptide docking and in silico toxicity"
- **Concern** The docking protocol uses HPEPDOCK with modeled peptide structures from the BioPep pipeline. The authors state that the modeled structures "should not be interpreted as a prediction of the bound conformation adopted upon interaction with the target." However, the docking results and subsequent MD simulations are based entirely on these modeled conformations. The use of pre-generated conformations in HPEPDOCK does not guarantee that the correct binding mode is sampled, especially for peptides that may undergo significant conformational changes upon binding. The validation using VIR251 redocking (RMSD 1.218 Å) is for a small peptidomimetic, not for the larger peptides studied.
- **Why it matters** If the initial docking poses are incorrect, the entire downstream analysis (MD, MM/PBSA) may be based on non-physiological binding modes. The lack of experimental validation means there is no way to assess whether the predicted binding modes are correct.
- **Resolution test** Provide evidence that the docking protocol can correctly predict binding modes for peptide ligands of similar size and flexibility to the studied peptides. This could include cross-docking of known peptide-PLpro complexes (if available) or comparison with alternative docking methods. Alternatively, perform ensemble docking or induced-fit docking to account for receptor flexibility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** "peptide 17,047 emerged as the most promising scaffold, demonstrating non-toxic predictions, robust hydrogen bond occupancy with catalytic residues, and stable binding dynamics" (Conclusions)
- **Evidence pointer** Table 4, Figure 6
- **Concern** The hydrogen bond occupancy data (Table 4) show significant variability across the three independent replicates. For pep17047, the His272–Leu4 occupancy ranges from 72.53% to 89.18% in two replicates but is only 12.62% in the third. Similarly, Asp286–Phe7 occupancy is 11.64% in one replicate but not reported in others. The authors acknowledge this variability but still conclude "robust" occupancy. The criteria for "robust" are not defined, and the variability undermines confidence in the binding mode.
- **Why it matters** If the hydrogen bond network is not reproducible across replicates, the predicted binding mode may not be stable or specific. This is critical for a computational study where reproducibility is a key indicator of reliability.
- **Resolution test** Provide a statistical analysis of the occupancy data across replicates (e.g., mean ± SD for each interaction) and define a threshold for "robust" occupancy. Alternatively, perform longer simulations or additional replicates to assess convergence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological completeness
- **Claim pointer** "The stability and binding energies of PLpro-peptide complexes were evaluated in triplicate using GROMACS 2024 for a 500-nanosecond (ns) molecular dynamics simulation" (Materials and methods)
- **Evidence pointer** Section "Molecular dynamics simulations and structural stability analysis"
- **Concern** The manuscript does not report whether the 500 ns simulations reached equilibrium. No block averaging, autocorrelation time analysis, or convergence diagnostics are provided for RMSD, Rg, or energy components. The RMSD plots (Figure 2) show that some systems (e.g., pep58620) may not have fully equilibrated within the simulation time. Without convergence analysis, the MM/PBSA calculations may be based on non-equilibrium trajectories.
- **Why it matters** MM/PBSA calculations are sensitive to the conformational ensemble used. If the simulations are not converged, the calculated binding energies may not be reliable. This is particularly important given the authors' own acknowledgment that MM/PBSA "frequently overestimates absolute binding free energies."
- **Resolution test** Provide convergence diagnostics (e.g., RMSD block averaging, autocorrelation times, or cumulative average plots) for all systems. If simulations are not converged, extend the simulation time or justify the current length with appropriate analysis.

- **Minor Comments**
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The column "Score" is labeled as "docking scores" but the units are not specified. The DL Score column is labeled "deep learning Score (indicating probability of toxicity)" but the range (0-1) is not explicitly stated. The PPV column is defined but the interpretation of values (e.g., 0.925 for peptide 33,035) is not explained in the table or legend.
- **Required correction** Add units to the Score column (presumably kcal/mol or arbitrary units). Specify the range and interpretation of DL Score and PPV in the table legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The RMSD plot (Figure 2) uses colors that may be difficult to distinguish for color-blind readers (green, blue, red, indigo, black). The legend is not embedded in the figure.
- **Required correction** Use a color-blind friendly palette (e.g., ColorBrewer) and add a legend within the figure or in the caption.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 4
- **Evidence pointer** Table 4
- **Issue** The hydrogen bond occupancy table includes interactions with occupancy as low as 0.02%. These are likely noise and should be excluded or reported with a threshold (e.g., >5%).
- **Required correction** Apply a minimum occupancy threshold (e.g., 5%) and report only interactions above this threshold. Alternatively, explain why such low-occupancy interactions are included.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section "Translational considerations: delivery strategies and pharmacokinetic challenges"
- **Evidence pointer** Location not provided
- **Issue** The term "Cell-propelled pemphigoids (CPPs)" appears to be a typographical error. The correct term is "cell-penetrating peptides (CPPs)."
- **Required correction** Correct the terminology throughout the section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "Molecular dynamics simulations and structural stability analysis"
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that "the video generated from the molecular dynamics trajectory (accessible at https://doi.org/10.5281/zenodo.19899151)" is available. However, the DOI is not resolved in the manuscript and the link should be verified. Additionally, the video is mentioned only for pep17047; videos for other systems would be useful.
- **Required correction** Verify the DOI and ensure it is accessible. Consider providing videos for all candidate systems or explain why only one is shown.

- **Technical failings that need to be addressed before the case is established** R1-M1 (experimental validation), R1-M2 (docking protocol validation), R1-M3 (reproducibility of hydrogen bond occupancy), R1-M4 (convergence of MD simulations)

- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The application of antimicrobial peptide libraries to PLpro is relatively novel, but the computational workflow (docking + MD + MM/PBSA) is standard and has been applied to many other targets.
  - **Scientific importance**: Low to moderate. PLpro is a valid antiviral target, but the study is entirely computational and does not provide experimental validation. The importance of the findings is contingent on future experimental confirmation.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to computational chemists and structural biologists. The lack of experimental data reduces its appeal to a broader biomedical audience.
  - **Technical soundness**: Adequate but with significant gaps. The triplicate simulation strategy and normalized energy metrics are strengths, but the lack of docking validation for peptide ligands, convergence analysis, and experimental confirmation are major weaknesses.
  - **Readability for nonspecialists**: Good. The manuscript is well-written and explains the rationale and methods clearly. However, the technical details may be challenging for readers without a computational background.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a computational prediction study that may be of interest to specialists, but the claims of "candidates" and "promising scaffolds" are not supported without experimental validation. The authors should either provide experimental data or reframe the manuscript as a purely computational prediction study with appropriate caveats.