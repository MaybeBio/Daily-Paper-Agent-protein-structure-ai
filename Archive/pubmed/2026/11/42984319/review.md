## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, conclusion, and materials and methods.
- **Assessment boundary** Scientific soundness, validity of the computational and experimental workflow, support of claims by presented evidence, and clarity of presentation. No assessment of grammar or style beyond what affects scientific comprehension.
- **Shared manuscript claim summary** The authors report the use of a machine learning-guided virtual screening workflow, combined with molecular docking, to identify four compounds (Q9, Q11, Q12, Q13) with in vitro inhibitory activity against *E. coli* MurB (IC50 values 25.08–34.44 µM), low cytotoxicity in HepG2 cells, and computationally predicted stable binding modes.
- **Visible evidence base** Abstract, full text, tables (Tables 1–4), figures (Figures 1–9), supplementary figure references (Figure S1, S2). No raw data, model files, or supplementary material were provided for independent verification.
- **Missing materials affecting confidence** Supplementary figures (S1, S2) referenced but not provided. Raw data for enzyme inhibition assays, IC50 curve fits, and cytotoxicity data are not available. Details of the in-house compound library composition and the specific compounds Q9, Q11, Q12, Q13 (SMILES or structures) are not provided. Model training/test set splits and hyperparameters are not fully described.

## Reviewer

- **Overall assessment** The manuscript presents a straightforward application of established computational methods (machine learning, docking, MD, MM-GBSA) combined with a limited set of experimental validation assays. The identification of four micromolar inhibitors of MurB is a modest but potentially useful contribution. However, the study has several significant weaknesses that currently prevent the claims from being fully established. The most critical issues are the small training dataset (84 compounds), the lack of structural information for the hit compounds, the absence of a positive control in the enzyme assay, the unexplained discrepancy between the reported 100 ns and 200 ns MD simulations, and the lack of any attempt to demonstrate target engagement or mechanism of action beyond computational prediction. The manuscript would benefit from a more critical interpretation of the results and a clearer statement of the limitations.
- **Who would be interested in the results, and why** Researchers in antibacterial drug discovery, particularly those focused on cell wall biosynthesis inhibitors, computational chemists applying machine learning to virtual screening, and medicinal chemists interested in novel scaffolds for MurB inhibition. The work may also be of interest to the broader community developing ML-guided screening workflows, although the methodological novelty is limited.
- **Major strengths**
  - The study integrates a reasonable pipeline of computational and experimental methods, from ML-based screening to in vitro validation.
  - The authors are transparent about the lack of antibacterial activity of the identified compounds, which is an important negative result.
  - The use of multiple computational techniques (docking, MD, MM-GBSA, PCA) provides a multi-faceted view of the predicted binding modes.
  - The manuscript is generally clearly written and the workflow is easy to follow.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "Model_2 was selected as the optimal activity-prediction model for virtual screening" based on predefined criteria (MCC > 0.5 and AUROC > 0.7).
- **Evidence pointer** Table 1, Section "Model Construction and Evaluation"
- **Concern** The training dataset consists of only 84 compounds after preprocessing. This is a very small dataset for training a robust ML classification model, especially with the "best quality" preset in AutoGluon, which is prone to overfitting. The manuscript does not report cross-validation strategies (e.g., k-fold) or external validation on a separate test set. The reported test set metrics (Table 1) are based on a single random 80/20 split, which is insufficient to demonstrate generalizability. The selection of Model_2 over Model_1 is not justified beyond the reported metrics, and the difference in performance may not be statistically significant given the small dataset size.
- **Why it matters** The entire virtual screening pipeline depends on the predictive quality of the selected ML model. If the model is overfitted or not generalizable, the prioritization of the 238 compounds is unreliable, and the subsequent experimental hits may be fortuitous. The lack of robust model validation undermines the core methodological claim of the paper.
- **Resolution test** The authors should provide a more rigorous model evaluation, including cross-validation (e.g., 5-fold or 10-fold) and, ideally, an external test set. They should also report the distribution of prediction scores and the confidence intervals for the performance metrics. If the dataset is too small for robust ML, this limitation should be explicitly acknowledged and the model selection criteria should be justified more carefully.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "16 candidate compounds were selected based on their hydrogen-bond interactions with the key active-site residue ASN A:233" and that these were subsequently tested experimentally.
- **Evidence pointer** Section "Molecular Docking", Table 2
- **Concern** The manuscript does not provide the chemical structures or identifiers (e.g., SMILES, PubChem CID) for the 16 selected compounds, nor for the four active hits (Q9, Q11, Q12, Q13). Without this information, the results are not reproducible, and the reader cannot assess the chemical novelty or drug-likeness of the identified scaffolds. Furthermore, the selection criteria for the 16 compounds are not fully described. The manuscript mentions "FCFP_6 fingerprint-based clustering to ensure structural diversity" but does not specify the clustering algorithm, similarity threshold, or how the final 16 were chosen from the 238 ML-predicted hits. The docking score cutoffs and the visual inspection criteria are also not defined.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publication. The lack of compound structures and detailed selection criteria prevents other researchers from replicating the study or building upon it. The claim that these are "novel inhibitors" cannot be evaluated without knowing their structures.
- **Resolution test** The authors must provide the chemical structures (as SMILES or in a supplementary table) for all 16 tested compounds and the four active hits. They should also provide a detailed, step-by-step description of the selection process, including the clustering parameters and the docking score thresholds used.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report IC50 values of 34.44, 31.45, 25.08, and 25.94 µM for Q9, Q11, Q12, and Q13, respectively, and state that these compounds "exhibited inhibition rates exceeding 50%" at 50 µM.
- **Evidence pointer** Section "Identification of Hits", Figure 4, Table 2
- **Concern** The enzyme inhibition assay methodology is described in the Materials and Methods, but critical details are missing. The assay couples MurA and MurB reactions, but the authors do not specify the concentrations of MurA, MurB, UNAG, PEP, and NADPH in the final reaction. The ratio of MurA to MurB is particularly important because the assay measures NADPH consumption, which is dependent on both enzymes. The authors also do not report a positive control inhibitor (e.g., a known MurB inhibitor) to validate the assay's dynamic range and sensitivity. The IC50 values are reported with standard errors, but the number of independent experiments (stated as three) is low for a reliable estimate. Furthermore, the manuscript does not report the maximum inhibition achieved at saturating concentrations, which is important for assessing the efficacy of the compounds.
- **Why it matters** Without a properly validated assay and appropriate controls, the reported IC50 values may not accurately reflect the true inhibitory potency of the compounds. The lack of a positive control makes it difficult to compare these results with other studies. The potential for assay artifacts (e.g., compound precipitation, interference with the coupled enzyme system) cannot be ruled out.
- **Resolution test** The authors should provide a detailed description of the assay conditions, including all reagent concentrations. They should include a positive control inhibitor and report the maximum inhibition and Hill slope for each compound. Ideally, they should also confirm the inhibitory activity using an orthogonal assay (e.g., a direct binding assay or a MurB-specific assay that does not rely on MurA coupling).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "200-ns molecular dynamics simulations were performed" in the Materials and Methods, but in the Results section, they refer to "100 ns MD simulations."
- **Evidence pointer** Section "Plausible Binding Modes From Molecular Dynamics Simulations" vs. Section "Molecular Dynamics Simulation" in Materials and Methods
- **Concern** There is a direct contradiction between the simulation length reported in the Results (100 ns) and that in the Methods (200 ns). This is a critical discrepancy that affects the interpretation of the MD results. If the simulations were only 100 ns, the convergence of the systems may not have been achieved, and the conclusions about binding stability may be premature. If they were 200 ns, the Results section is incorrect.
- **Why it matters** The MD simulation results are used to support the claim that the compounds form stable complexes with MurB. An incorrect simulation length undermines the credibility of these results and raises questions about the rigor of the computational analysis.
- **Resolution test** The authors must correct this discrepancy and clearly state the actual simulation length used. They should also provide evidence of convergence (e.g., RMSD vs. time plots for the full simulation length) to support their conclusions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that the identified compounds "offer promising scaffolds for further mechanistic investigation and structural optimization."
- **Evidence pointer** Conclusion, Abstract
- **Concern** The identified compounds have IC50 values in the high micromolar range (25–34 µM) and show no antibacterial activity against *E. coli* ATCC 25922 (MIC > 64 µg/mL). While the authors acknowledge this limitation, the claim that these are "promising scaffolds" is not strongly supported. The lack of antibacterial activity suggests poor cellular penetration or efflux, which are significant hurdles that are not addressed. The manuscript does not discuss the physicochemical properties of the compounds (e.g., LogP, molecular weight, polar surface area) that might explain the lack of whole-cell activity. The structural novelty of the scaffolds is also not discussed in the context of known MurB inhibitors.
- **Why it matters** The significance of the work depends on the potential of the identified compounds to be developed into useful antibacterial agents. Without a clear path to improving potency and cellular activity, the "promising scaffolds" claim is overstated.
- **Resolution test** The authors should temper their conclusions and provide a more critical assessment of the compounds' potential. They should discuss the physicochemical properties of the hits and propose specific medicinal chemistry strategies to improve their antibacterial activity. Alternatively, they could reposition the work as a proof-of-concept for the ML screening workflow rather than a source of drug candidates.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Dataset description
- **Evidence pointer** Section "Dataset Compilation"
- **Issue** The authors state that 112 compounds were retrieved from ChEMBL and 84 remained after preprocessing. The criteria for classifying compounds as "active" or "inactive" (IC50 threshold of 50 µM) are mentioned, but the distribution of active vs. inactive compounds in the final dataset is not reported. This is important for understanding the model's performance and potential class imbalance.
- **Required correction** Report the number of active and inactive compounds in the training and test sets.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** MM-GBSA calculations
- **Evidence pointer** Section "MM-GBSA Binding Free Energy Analysis", Table 4
- **Concern** The MM-GBSA results are presented as a single value per compound without error estimates. It is unclear how many frames were used for the calculation and whether the results are statistically meaningful. The ranking of compounds by MM-GBSA does not correlate with the experimental IC50 values (Q9 has the most favorable ΔG bind but is not the most potent inhibitor).
- **Required correction** Provide the standard deviation or standard error of the MM-GBSA calculations and discuss the lack of correlation with experimental potency.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Cytotoxicity assay
- **Evidence pointer** Section "Cytotoxicity Evaluation", Figure 5
- **Concern** The authors report cell viability data but do not state the concentration of DMSO in the assay. High DMSO concentrations can affect cell viability. The positive control (e.g., a known cytotoxic agent) is not mentioned.
- **Required correction** Specify the DMSO concentration and include a positive control in the cytotoxicity assay.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Section "Introduction"
- **Concern** The introduction is brief and does not provide sufficient background on the MurB enzyme, its role in peptidoglycan biosynthesis, and the structural features of its active site. A reader unfamiliar with the field may struggle to understand the significance of the ASN A:233 interaction.
- **Required correction** Expand the introduction to provide more context on MurB as a drug target and the rationale for targeting ASN A:233.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Insufficient ML model validation (small dataset, no cross-validation).
  - R1-M2: Missing chemical structures of the hit compounds and incomplete selection criteria.
  - R1-M3: Incomplete enzyme assay validation (no positive control, unclear coupling conditions).
  - R1-M4: Contradictory MD simulation lengths (100 ns vs. 200 ns).

- **Assessment against Nature-style criteria**
  - **Originality**: Low to moderate. The application of ML to virtual screening is not new, and the specific target (MurB) has been studied before. The combination of methods is standard. The identification of four new micromolar inhibitors is a modest incremental advance.
  - **Scientific importance**: Low to moderate. MurB is a validated target, but the identified compounds are weak inhibitors with no antibacterial activity. The work does not provide significant new insights into MurB inhibition or the ML methods used.
  - **Interdisciplinary readership**: Limited. The work is primarily of interest to computational chemists and antibacterial drug discovery researchers. The methods are not novel enough to attract a broader audience.
  - **Technical soundness**: Currently not established. The ML model validation is inadequate, the experimental assay lacks key controls, and there is a critical inconsistency in the MD simulation length. These issues must be resolved before the conclusions can be accepted.
  - **Readability for nonspecialists**: The manuscript is generally readable, but the introduction is too brief and the methods section is dense. The figures are not provided for review, which limits the assessment of clarity.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript has a logical workflow and the authors are transparent about the lack of antibacterial activity, which is commendable. However, the technical issues outlined above, particularly the ML model validation, the missing compound structures, the incomplete assay validation, and the MD simulation inconsistency, prevent the main claims from being supported. The authors should be encouraged to revise the manuscript to address these concerns. If the technical issues are resolved, the work could be a useful contribution to the field of computational antibacterial drug discovery, but it would likely be more suitable for a specialized journal rather than a high-impact general journal.