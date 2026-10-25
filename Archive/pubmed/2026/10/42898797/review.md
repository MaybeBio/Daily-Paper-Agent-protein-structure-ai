## Review setup
- **Input scope** Full manuscript text, including Introduction, Methods, Results, Discussion, and supplementary references
- **Assessment boundary** Computational predictions only; no experimental validation data provided
- **Shared manuscript claim summary** The authors present a hybrid computational pipeline integrating the ESM3 protein language model with molecular docking, Monte Carlo simulation, molecular dynamics, MM-GBSA/PBSA binding free energy calculations, and DFT to engineer a hemoglobin variant (esmHb) with a single His45Arg mutation. They claim this variant shows enhanced thermodynamic stability, increased heme-binding affinity, and greater thermodynamic favorability of oxidation compared to wild-type hemoglobin, benchmarking against the clinically characterized Hb Fort de France mutation.
- **Visible evidence base** Figures 1–9, Tables 1–2, Supplementary Figure S1, Supplementary Table S1 (referenced but not provided in the supplied text)
- **Missing materials affecting confidence** Supplementary Table S1 (DFT coordinates), Supplementary Figure S1 (block convergence analysis), raw MD trajectory data, ESM3 generation parameters beyond temperature, statistical test details, and any experimental validation data

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive pipeline for hemoglobin engineering, combining a state-of-the-art protein language model with multiple biophysical simulation methods. The work addresses a relevant problem in therapeutic protein design, and the integration of ESM3 with traditional computational validation is timely. However, the manuscript suffers from several critical weaknesses: the central claims rest entirely on computational predictions without any experimental validation, the statistical framework is inconsistently applied, and some methodological details are insufficiently described to assess reproducibility. The comparison to Hb Fort de France is used as a benchmark but the manuscript does not clearly establish whether the esmHb variant reproduces the experimentally known properties of this mutation beyond qualitative agreement. The DFT methodology, while described in detail, relies on heavily truncated models that may not capture the full electrostatic environment of the heme pocket. The manuscript would benefit from clearer presentation of the novelty relative to existing computational protein engineering approaches and a more rigorous treatment of uncertainty in the computational predictions.

- **Who would be interested in the results, and why** Researchers in computational protein design and engineering, particularly those working with protein language models for therapeutic protein optimization. The work may also interest the hemoglobin research community, specifically those studying oxygen carriers and blood substitute development. The methodological framework could be relevant to computational biologists developing hybrid AI-physics pipelines for protein engineering. However, the lack of experimental validation limits the immediate utility for translational researchers.

- **Major strengths** 
  1. The integration of ESM3 with multiple orthogonal computational validation methods (docking, MD, MM-GBSA/PBSA, DFT) represents a comprehensive in silico pipeline.
  2. The use of a clinically characterized mutation (Hb Fort de France) as a benchmark provides a meaningful reference point for evaluating the pLM's predictive capability.
  3. The authors appropriately acknowledge limitations in their statistical interpretation, particularly for MM-GBSA results.
  4. The detailed description of DFT model construction, including spin states and truncation strategies, demonstrates methodological rigor.
  5. The work addresses a challenging problem (modifying a ligand-binding site) that is often avoided in AI-driven protein design.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims esmHb exhibits "improved thermodynamic stability (ΔG: −18.48 vs. −12.22 kcal/mol), increased heme-binding affinity (ΔGbind: −11.79 vs. −8.42 kcal/mol), and greater thermodynamic favorability of oxidation according to DFT calculations (ΔE: −173.1 vs. −149.9 kcal/mol)."
- **Evidence pointer** Results sections "Protein stability analysis," "Protein–ligand interaction analysis," and "DFT analysis"; Figures 5, 7, 9; Tables 1–2
- **Concern** All central claims of enhanced stability, binding affinity, and oxidation favorability are based exclusively on computational predictions. No experimental validation is provided, such as spectroscopic binding assays, thermal denaturation measurements, or oxygen equilibrium curves. The manuscript acknowledges this in the Discussion but does not temper the strength of the claims in the Abstract or Results accordingly.
- **Why it matters** Computational predictions of protein stability and binding affinity are known to have significant error rates. Without experimental confirmation, the claim that esmHb is a viable therapeutic candidate with "enhanced stability and oxygen affinity" is not established. The Nature readership expects either experimental validation or substantially more cautious language.
- **Resolution test** Provide experimental validation of at least one key claim (e.g., heme binding affinity via spectrophotometric titration, thermal stability via circular dichroism, or oxygen affinity via tonometry). Alternatively, substantially revise the claims to clearly state these are computational predictions requiring experimental confirmation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states "Statistical significance (p < 0.05) was reached for protein–protein interactions via both methods and for protein–heme interactions via MM-PBSA."
- **Evidence pointer** Results section "Molecular dynamics simulations"; Figure 7
- **Concern** The statistical analysis is inadequately described. The manuscript does not specify what statistical test was used, how many independent samples were compared, what the degrees of freedom were, or how the triplicate MD simulations were treated in the statistical comparison. The use of a Student's t-test (mentioned in Methods) for comparing binding free energies derived from MD simulations is questionable, as these values are not independent measurements but rather derived from correlated trajectory data.
- **Why it matters** The claim of statistical significance is central to the manuscript's assertion that esmHb is improved over wtHb. If the statistical framework is flawed, the significance claims are unsupported, undermining the core conclusion.
- **Resolution test** Provide a detailed description of the statistical methodology, including the exact test used, the number of samples, how the triplicate simulations were handled, and justification for the chosen test given the correlated nature of MD-derived data. If the test is inappropriate, reanalyze the data with a suitable method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological completeness
- **Claim pointer** The manuscript describes the ESM3-based generation of esmHb and claims "the optimized prompting strategy yielded a variant with exactly one mutation (His45Arg), achieving 100% sequence identity to the wild-type α-chain outside the targeted site."
- **Evidence pointer** Results section "Optimization of ESM3 parameters for esmHb modeling"; Figure 4
- **Concern** The ESM3 generation process is not fully described. The manuscript mentions two prompting strategies and reports r² values for nonlinear regressions, but does not provide sufficient detail on the ESM3 model version, the exact tokenization scheme, the number of generation attempts, the selection criteria for the final model, or how the "deterministic refolding step" was implemented. The definition of RT50 is provided but its biological or structural significance is not discussed.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete methodological details, other researchers cannot replicate the ESM3 generation process or verify the claims about the pipeline's effectiveness.
- **Resolution test** Provide a complete description of the ESM3 generation protocol, including model version, all hyperparameters, generation attempts, selection criteria, and the code or pseudocode for the prompting strategy. Consider making the generation script available in the repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretational validity
- **Claim pointer** The manuscript states "the optimized prompting strategy yielded a variant with exactly one mutation (His45Arg)" and later claims this variant shows "greater thermodynamic favorability of oxidation according to DFT calculations (ΔE: −173.1 vs. −149.9 kcal/mol)."
- **Evidence pointer** Results sections "Optimization of ESM3 parameters for esmHb modeling" and "DFT analysis"; Tables 1–2; Figure 9
- **Concern** The DFT calculations are performed on heavily truncated models containing only the heme and residues within 5 Å, with the His45Arg mutation retained but all other residues beyond the first coordination shell removed. The reported energy difference of 23.2 kcal/mol between wtHb and esmHb oxidation is attributed to the His45Arg mutation. However, the truncation strategy may not adequately capture long-range electrostatic effects, protein dynamics, or solvation effects that could substantially influence the oxidation thermodynamics. The manuscript does not discuss the sensitivity of the DFT results to the truncation radius or model size.
- **Why it matters** The DFT claim is a key piece of evidence for the functional advantage of esmHb. If the truncated model introduces artifacts, the 23.2 kcal/mol difference may not reflect the true thermodynamic difference in the full protein context.
- **Resolution test** Perform convergence tests with increasing truncation radii, or use a QM/MM approach that includes the full protein environment. Alternatively, temper the DFT claim to acknowledge the limitations of the truncated model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparative analysis
- **Claim pointer** The manuscript benchmarks against the Hb Fort de France mutation and claims "ESM3 accurately assessed the fitness effect of the Hb Fort de France mutation."
- **Evidence pointer** Results section "ESM3 mutation analysis"; Figure 3
- **Concern** The benchmarking claim is not rigorously established. The manuscript shows that ESM3 assigns a high fitness score to the His45Arg mutation, which is consistent with the known phenotype of Hb Fort de France. However, this is a single data point. The manuscript does not compare ESM3's performance against other prediction methods (e.g., Rosetta, FoldX, or other pLMs) for this specific mutation, nor does it test whether ESM3 correctly identifies the experimentally known destabilizing or neutral mutations at other positions in hemoglobin.
- **Why it matters** The claim that ESM3 "accurately assessed" the fitness effect is based on a single positive example. A more rigorous benchmark would strengthen the case that ESM3 is a reliable tool for this type of mutation analysis.
- **Resolution test** Expand the benchmarking to include multiple known hemoglobin mutations with experimentally characterized effects on stability and oxygen affinity. Compare ESM3 predictions against other computational methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "ESM3 accurately assessed the fitness effect of the Hb Fort de France mutation" without qualification. Given that this is based on a single mutation and no experimental validation, this overstates the evidence.
- **Required correction** Revise to "ESM3 predicted a high fitness score for the Hb Fort de France mutation, consistent with its known phenotype."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Sequence analysis and pLM-based structure prediction"
- **Evidence pointer** Methods section
- **Issue** The manuscript states "The output tokens were converted into three-dimensional backbone coordinates" but does not specify the software or algorithm used for this conversion, nor the version of ESM3 employed.
- **Required correction** Specify the ESM3 model version and the software used for token-to-structure conversion.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results, "Molecular dynamics simulations"
- **Evidence pointer** Results section
- **Issue** The manuscript reports "mean RMSD" values but does not specify whether these are averaged over the three replicate simulations or over time for a single simulation. The presentation of error bars in Figure 6 is not described.
- **Required correction** Clarify how the mean values and error bars were computed from the triplicate simulations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "DFT analysis"
- **Evidence pointer** Results section; Tables 1–2
- **Issue** The manuscript reports ΔE values for oxidation but does not provide the absolute energies or the components of the energy decomposition. The reader cannot assess whether the 23.2 kcal/mol difference arises from electronic effects, electrostatic interactions, or other contributions.
- **Required correction** Provide a breakdown of the energy components contributing to the ΔE difference between wtHb and esmHb.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion references "molecular doorstop" mechanism and other biophysical concepts without sufficient explanation for a general readership.
- **Required correction** Briefly explain the "molecular doorstop" mechanism or provide a citation that does so.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability statement
- **Issue** The GitHub repository is referenced but its contents are not described. It is unclear whether the repository contains code, data, or both.
- **Required correction** Describe the contents of the repository and provide a DOI or version identifier.

## Risk / unsupported claims
- The claim that esmHb has "enhanced stability and oxygen affinity" is unsupported by experimental evidence; all supporting data are computational predictions.
- The claim that "ESM3 accurately assessed the fitness effect of the Hb Fort de France mutation" is based on a single mutation and lacks comparative benchmarking.
- The DFT-derived 23.2 kcal/mol difference in oxidation favorability is based on heavily truncated models and may not be representative of the full protein system.
- The statistical significance claims for MM-GBSA/PBSA results are not supported by adequate methodological description.
- The claim that esmHb is "applicable to hemoglobinopathies, artificial blood substitutes, and more" is speculative given the absence of experimental validation.
- The statement that the pipeline is "generalizable" is not supported by demonstration on multiple protein systems.