## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of computational workflow, interpretation of results, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors developed a ligand-based pharmacophore model from sulfonamide MMP2 inhibitors, screened an FDA-approved drug library, prioritized hits by docking and MD simulations against MMP2, then profiled the top five candidates against MMP3, proposing Regorafenib and Capmatinib as promising dual MMP2/MMP3 inhibitors for IPF repurposing
- **Visible evidence base** Pharmacophore modeling statistics, docking scores, MD trajectory analyses (RMSD, RMSF, Rg, SASA, H-bonds), MM-PBSA free energy estimates, interaction diagrams, tables of compounds and clinical profiles
- **Missing materials affecting confidence** Supplementary tables and figures referenced but not provided; no experimental validation data; no statistical analysis of MD replicates; no details on force field parameter validation for zinc coordination; no information on compound protonation states or tautomers

## Reviewer
- **Overall assessment** This manuscript presents a straightforward computational repurposing pipeline combining pharmacophore modeling, docking, and MD simulations. The workflow is methodologically conventional and internally consistent, but the scientific advance is incremental. The central claims of "promising candidates" rest entirely on computational predictions without experimental corroboration, and several methodological choices require justification. The near-perfect pharmacophore validation metrics raise overfitting concerns that the authors address only partially. The MMP3 cross-reactivity claim is based on docking and MD alone, which is insufficient to establish even putative cross-activity. The manuscript would benefit from more rigorous validation, clearer presentation of uncertainty, and tempering of conclusions to match the evidence level.

- **Who would be interested in the results, and why** Computational chemists and drug repurposing researchers working on MMP inhibitors may find the workflow of interest as a case study. Researchers focused on IPF therapeutics might note the candidate compounds for future experimental screening. However, the audience is narrow given the purely computational nature and the absence of novel methodological contributions.

- **Major strengths**
  1. The workflow is logically structured, progressing from pharmacophore development through docking to MD and MM-PBSA analysis
  2. The authors acknowledge the computational nature of the study and explicitly state the need for experimental validation
  3. The inclusion of MMP3 as a secondary target is biologically motivated given its role in IPF
  4. The discussion of limitations, including the single-trajectory caveat, shows some scientific caution
  5. The use of multiple complementary computational methods (pharmacophore, docking, MD, MM-PBSA) provides a more comprehensive assessment than any single approach

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of pharmacophore model
- **Claim pointer** The pharmacophore model achieved AUC of 1.00, sensitivity of 1.00, and specificity of 0.997, which the authors attribute to robust discriminatory power rather than overfitting
- **Evidence pointer** Section 2.1, Figure 2, Table S2
- **Concern** Perfect or near-perfect classification metrics on a validation set of 1275 molecules (25 actives, 1250 decoys) are extraordinary and typically indicate overfitting, data leakage, or an overly simplistic decoy set. The authors' rebuttal arguments are not fully convincing. First, the "independent subsets" are derived from the same small dataset of 25 actives, so the chemical diversity is limited. Second, citing literature examples of high AUC does not establish that this specific model is not overfit. Third, the claim that pharmacophore features are "mechanistically interpretable" does not preclude overfitting. The benchmarking of docking (AUC 0.869) on the same set is informative but does not directly validate the pharmacophore model's generalizability. The authors should provide external validation on an independent dataset of known MMP2 inhibitors not used in model building, or demonstrate the model's performance on a more challenging decoy set.
- **Why it matters** If the pharmacophore model is overfit, the screening results and all downstream prioritization are compromised. The validity of the entire pipeline depends on this model's genuine predictive ability.
- **Resolution test** Provide external validation using an independent set of known MMP2 inhibitors and decoys from a different source. Report performance metrics on this external set. Alternatively, demonstrate that the model can retrieve diverse known MMP2 inhibitors from a large drug-like database with acceptable enrichment.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for cross-activity claim
- **Claim pointer** The title and abstract claim "putative MMP3 cross-activity" for the identified compounds, supported by docking and MD simulations against MMP3
- **Evidence pointer** Sections 2.5, 2.6, 2.7, Tables 4-6, Figures 7-9
- **Concern** The MMP3 cross-activity claim is based solely on docking scores and MD stability metrics. Docking scores are notoriously poor predictors of binding affinity across different targets, and the correlation between computational stability and enzymatic inhibition is weak. The authors did not perform any free energy perturbation or alchemical calculations that might provide more reliable relative binding affinities. Moreover, the MMP3 MD analysis is based on a single trajectory per system, which the authors acknowledge. The claim of "cross-activity" implies functional inhibition, which cannot be established from these computational data alone. The title's phrasing "putative MMP3 cross-activity" is appropriately hedged, but the abstract's framing suggests a stronger conclusion than warranted.
- **Why it matters** The dual-targeting rationale is a key selling point of the manuscript. If the MMP3 interaction is not robustly supported, the scientific contribution is substantially diminished.
- **Resolution test** Provide experimental enzyme inhibition data for at least the top two candidates against both MMP2 and MMP3. Alternatively, substantially temper the cross-activity claim and reframe the manuscript as MMP2-focused with preliminary MMP3 docking assessment only.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor of MD simulations
- **Claim pointer** The MD simulations were performed for 200 ns per system, and stability was assessed using RMSD, RMSF, Rg, SASA, and hydrogen bond analyses
- **Evidence pointer** Sections 2.3, 2.6, 4.5, Tables 2, 5, Figures 6, 9
- **Concern** Several methodological details are missing or inadequately justified. (1) The zinc ion was modeled using a non-bonded approach, which is known to be problematic for accurate coordination geometry and can lead to zinc loss or distorted coordination during MD. The authors state that coordination was "preserved by maintaining the geometry obtained from the crystal structure," but this is ambiguous. (2) Only a single 200 ns trajectory was run per system. For binding affinity estimates via MM-PBSA, this is short, and the lack of replicate trajectories prevents any statistical assessment of convergence. (3) The MM-PBSA method is sensitive to the choice of dielectric constants, radii, and entropy estimates, none of which are discussed. (4) The authors do not report whether the ligand parameters were validated or whether the ligand protonation states were appropriate at physiological pH.
- **Why it matters** The MD and MM-PBSA results are used to rank compounds and support the final conclusions. If the simulations are not converged or the zinc model is inaccurate, the rankings may be unreliable.
- **Resolution test** Provide replicate trajectories (at least 3 per system) and show convergence of RMSD and MM-PBSA estimates. Justify the non-bonded zinc model or use a bonded model with validated parameters. Report the dielectric constants and other MM-PBSA parameters used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Selection criteria and compound prioritization
- **Claim pointer** Five compounds were selected based on docking scores better than the lead compound, and two were further prioritized for MMP3 based on docking and MD
- **Evidence pointer** Sections 2.2, 2.5, Tables 1, 4
- **Concern** The selection criteria are not clearly defined. The authors state that compounds with docking scores better than compound 09 were retained, but the threshold is arbitrary and depends on the docking scoring function's accuracy. For MMP3, only two compounds were advanced to MD, but the criteria for this down-selection are not explicitly stated. Additionally, the authors do not discuss whether the selected compounds have any known MMP-related off-target effects or whether their clinical profiles (e.g., as kinase inhibitors) might confound the proposed MMP2/MMP3 mechanism. The clinical safety discussion in Section 3 is brief and does not address potential on-target toxicity from MMP inhibition.
- **Why it matters** The prioritization logic determines which compounds are proposed for experimental validation. If the selection is not transparent or robust, the final recommendations are weakened.
- **Resolution test** Clearly state the selection criteria at each stage. Provide a table showing all 83 hits with their docking scores and the rationale for selecting the top five. Discuss potential off-target effects and the therapeutic window for MMP inhibition.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figures 6 and 9
- **Evidence pointer** Sections 2.3, 2.6
- **Issue** The figures are described as showing RMSD, RMSF, Rg, SASA, and H-bond analyses, but the panels are not described in sufficient detail in the text. It is unclear which panel corresponds to which metric and which color corresponds to which system.
- **Required correction** Add clear panel labels and legends to the figures, and describe each panel explicitly in the figure captions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency of compound naming
- **Affected element** Tables 1, 3, 4, 6
- **Evidence pointer** Sections 2.2, 2.4, 2.5, 2.7
- **Issue** The compounds are referred to by their S-numbers (e.g., S1178) in some places and by generic drug names (e.g., Regorafenib) in others. This is inconsistent and may confuse readers.
- **Required correction** Use a consistent naming convention throughout, preferably with both the S-number and generic name at first mention, then one consistent identifier thereafter.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical treatment of MM-PBSA data
- **Affected element** Tables 3, 6
- **Evidence pointer** Sections 2.4, 2.7
- **Issue** The MM-PBSA values are reported as mean ± standard deviation, but the number of samples (frames) used for the average is not stated. It is also unclear whether the standard deviation reflects temporal variation or block averaging.
- **Required correction** State the number of frames used for the MM-PBSA calculation and describe how the standard deviation was computed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference to supplementary material
- **Affected element** Tables S1-S5, Figures S1-S2
- **Evidence pointer** Throughout
- **Issue** The manuscript references supplementary tables and figures extensively, but these were not provided for review. It is impossible to verify the claims made in the main text without access to this material.
- **Required correction** Ensure all supplementary material is available to reviewers and readers, and cross-check that all referenced items exist.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and grammar
- **Affected element** Throughout
- **Evidence pointer** Various sections
- **Issue** There are several grammatical errors and awkward phrasings (e.g., "The grid-box were set," "the number of binding modes fixed at the default value of 9"). These do not impede understanding but detract from the professional presentation.
- **Required correction** Perform a thorough language edit of the manuscript.

## Risk / unsupported claims
- The claim of "putative MMP3 cross-activity" is unsupported by experimental data and relies on computational predictions with known limitations
- The near-perfect pharmacophore validation metrics (AUC 1.00) are not adequately justified against overfitting concerns
- The MM-PBSA binding free energy rankings are presented as meaningful without experimental calibration or replicate sampling
- The statement that the selected compounds "may contribute to differential recognition of MMP2 and MMP3" is speculative and not directly tested
- The clinical safety discussion implies that established profiles of these drugs are advantageous for repurposing, but the relevance of these profiles to chronic MMP inhibition in IPF is not established
- The claim that the pharmacophore model has "strong validation performance to support its use for virtual screening" is not fully supported given the potential for overfitting on a small congeneric series

## Assessment against Nature-style criteria
- **Originality** Low to moderate. The combination of pharmacophore modeling, docking, and MD for drug repurposing is well-established. The specific application to MMP2/MMP3 in IPF is somewhat novel but does not introduce new methodologies or concepts.
- **Scientific importance** Moderate. Identifying potential repurposing candidates for IPF is clinically relevant, but the purely computational nature and lack of experimental validation limit the immediate impact. The findings are hypothesis-generating rather than conclusive.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to computational chemists and MMP researchers. The clinical relevance to IPF is mentioned but not developed sufficiently to attract a broader pulmonary or clinical audience.
- **Technical soundness** The individual methods are standard and generally applied correctly, but several concerns (pharmacophore overfitting, zinc modeling, single MD trajectories, MM-PBSA parameter choices) undermine confidence in the results. The lack of experimental validation is a fundamental limitation.
- **Readability for nonspecialists** The manuscript is reasonably well-organized and the logic is clear, but the heavy reliance on computational jargon and the absence of clear explanations of key concepts (e.g., pharmacophore features, MM-PBSA) would make it difficult for nonspecialists to follow. The figures are not self-explanatory.

## Recommendation posture
Currently not established from the provided evidence. The computational workflow is conventional and internally consistent, but the central claims of promising dual MMP2/MMP3 inhibitors are not supported by experimental data. The pharmacophore model's validity is questionable given the perfect validation metrics, and the MMP3 cross-activity claim rests on docking and MD alone. The manuscript would require substantial additional work, including external validation of the pharmacophore model, replicate MD simulations with proper zinc modeling, and ideally experimental enzyme inhibition data, before the conclusions could be considered established. The authors should also temper their claims to match the evidence level and more clearly acknowledge the speculative nature of computational predictions.