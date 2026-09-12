# Review setup
- **Input scope** Full manuscript (including abstract, methods, results, discussion, conclusions, and supplementary information reference)
- **Assessment boundary** Manuscript as submitted; no supplementary material was provided for independent verification
- **Shared manuscript claim summary** The authors present an integrated computational workflow (2D-QSAR, molecular docking, MD simulations, MM/GBSA, ADMET) to characterize phenyl-dihydropyrazolone derivatives with reported antitrypanosomal activity and to design four new candidates (LMM1–LMM4) predicted to interact with cruzain (Cz). The study concludes that pyrazolones are promising antitrypanosomal scaffolds and provides structural hypotheses for future experimental validation.
- **Visible evidence base** Full text with figures (Fig. 1–8) and tables (Table 1–11); supplementary material referenced but not provided
- **Missing materials affecting confidence** Supplementary material (ESM 1 and ESM 2, including Fig. S1–S3, Table S1–S2) was not provided for review. This material is essential for evaluating: (1) the full compound dataset (Table S1), (2) regression coefficients before/after outlier removal (Table S2), (3) apo Cz force-field sensitivity tests (Fig. S1), (4) representative 3D docking poses (Fig. S2), and (5) per-replica ligand RMSD time series (Fig. S3).

# Reviewer
- **Overall assessment** This manuscript presents a technically competent computational study that applies a standard CADD pipeline to a relevant neglected disease target. The work is methodologically sound in its individual components, and the authors demonstrate appropriate caution in interpreting their results, particularly regarding the limitations of MM/GBSA and the disconnect between computed binding energies and phenotypic activity. However, the study's impact is substantially limited by: (1) the absence of any experimental validation, (2) the acknowledged inability of the computational models to reproduce the phenotypic activity ranking, and (3) the lack of biochemical Cz inhibition data for the proposed compounds. The manuscript reads more as a methodological demonstration than as a discovery study that would meet the novelty and scientific importance thresholds expected for a high-impact journal.
- **Who would be interested in the results, and why** Researchers in computational medicinal chemistry and neglected tropical disease drug discovery would find this work relevant as a case study of integrated CADD applied to Chagas disease. The detailed QSAR validation and MD analysis protocols may serve as a reference for similar studies. However, the audience is primarily specialists in computational chemistry rather than the broad interdisciplinary readership of a general-interest journal.
- **Major strengths** 1. Comprehensive and well-documented computational workflow integrating ligand-based and structure-based methods. 2. Appropriate use of multiple validation metrics for QSAR (internal, external, y-randomization, LNO, applicability domain). 3. Honest and transparent discussion of limitations, particularly the discrepancy between MM/GBSA ranking and phenotypic activity, and the caveat that whole-cell activity does not necessarily reflect Cz inhibition. 4. Extended MD sampling (3 × 250 ns per system, 4.5 μs total) is adequate for assessing complex stability.
- **Major Concerns**
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / novelty
- **Claim pointer** The manuscript claims to provide "structural hypotheses for future experimental validation" and that the findings "support pyrazolones as antitrypanosomal scaffolds." The designed compounds LMM1–LMM4 are presented as candidates for further evaluation.
- **Evidence pointer** Conclusions section; Abstract; Introduction
- **Concern** The study is entirely computational, with no experimental validation of any kind. The QSAR model is based on whole-cell phenotypic data (not Cz inhibition), and the MM/GBSA ranking does not reproduce the phenotypic activity trend. The authors themselves acknowledge that "phenotypic antitrypanosomal potency cannot be directly assigned to Cz inhibition without biochemical validation" and that the proposed compounds should be regarded as "computationally predicted Cz-binding modes, rather than experimentally validated Cz inhibitors." Without experimental data (e.g., biochemical Cz inhibition assays, cellular activity of LMM1–LMM4), the study remains a computational exercise that does not advance beyond hypothesis generation.
- **Why it matters** For a journal targeting broad scientific impact, computational predictions without experimental validation, especially when the computational models themselves show internal inconsistencies (MM/GBSA vs. phenotypic activity), do not constitute a sufficiently novel or impactful contribution. The field of CADD for Chagas disease already contains numerous similar studies; this work does not introduce new methodology or provide experimentally validated compounds.
- **Resolution test** Provide experimental validation, such as: (1) biochemical Cz inhibition assays for key compounds (CP3, CP98, and at least 2 LMM compounds), (2) cellular antitrypanosomal activity data for LMM1–LMM4, or (3) demonstrate that the computational predictions can be used to prioritize compounds that are subsequently confirmed experimentally.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / claim support
- **Claim pointer** The manuscript claims that the designed compounds LMM1–LMM4 have "intermediate predicted antitrypanosomal activity" and that the QSAR model guided their design.
- **Evidence pointer** Table 5; Results section "2D-QSAR model: construction, validation, and molecular design"
- **Concern** The rationale for designing LMM1–LMM4 is insufficiently justified. The authors state that these compounds were "not proposed because they were predicted to exceed the most potent compounds in the original dataset but because they combine structural novelty, acceptable predicted antitrypanosomal activity, and favorable preliminary drug-likeness/ADMET profiles." However, the predicted pIC50 values for LMM1–LMM4 (5.3–5.8) are all below the most active compounds in the dataset (CP99: pIC50 = 6.3; CP123: pIC50 = 6.2). The structural novelty is not clearly defined or quantified (e.g., Tanimoto similarity to known compounds). The ADMET profiles, while favorable, are not compared systematically against the most active known compounds to demonstrate improvement. The design strategy appears to be: select descriptor values that yield intermediate activity, without a clear optimization objective.
- **Why it matters** The central claim of the paper—that the computational workflow can guide the design of new candidates—is weakened if the designed compounds are not predicted to be more potent than existing ones and if the design rationale is not clearly articulated. This undermines the practical utility of the proposed framework.
- **Resolution test** Clearly state the optimization objective (e.g., improved ADMET while maintaining activity, or exploration of novel chemical space). Provide quantitative measures of structural novelty (e.g., Tanimoto similarity to training set compounds). Alternatively, design compounds predicted to exceed the potency of known actives, or provide experimental data showing that LMM compounds have advantages over existing ones.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript uses MM/GBSA to estimate binding free energies and interprets per-residue decomposition to suggest that "contacts with Gly66, Leu67, and Leu160 may be relevant for Cz recognition."
- **Evidence pointer** Table 11; Figure 8; Results section "MM/GBSA binding free energy estimates and per-residue energy decomposition"
- **Concern** The MM/GBSA calculations omit the entropic term (TΔS), which the authors acknowledge. However, the per-residue decomposition analysis is then used to draw qualitative conclusions about binding determinants, despite the fact that: (1) several ligands showed significant rearrangements (RMSD up to 3.2 Å) relative to initial docking poses, (2) the decomposition was performed on MD-relaxed structures that may differ substantially from the binding mode used for interpretation, and (3) the differences in per-residue contributions between compounds are small (often <1 kcal/mol) and within the expected uncertainty of the method. The authors state that "the magnitude of this difference is small and within the expected uncertainty of endpoint decomposition methods" but then proceed to interpret these differences as structurally relevant.
- **Why it matters** The per-residue decomposition analysis is used to support claims about specific residue interactions (Gly66, Leu67, Leu160) that are presented as "plausible structural features to consider in future optimization." If the analysis is not quantitatively reliable, these claims may mislead future research efforts. The manuscript needs to either provide error estimates that justify the interpretation or explicitly state that the differences are not statistically significant.
- **Resolution test** Provide standard deviations or confidence intervals for per-residue decomposition values. Perform statistical testing (e.g., bootstrapping) to determine whether observed differences between compounds are significant. Alternatively, explicitly state that all per-residue differences are within the noise of the method and cannot be used to distinguish between compounds.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility / completeness
- **Claim pointer** The manuscript references supplementary material (Fig. S1–S3, Table S1–S2) that is essential for evaluating key claims, including the force-field sensitivity test for apo Cz, per-replica ligand RMSD time series, and the full compound dataset.
- **Evidence pointer** Methods section; Results section; Supplementary information
- **Concern** The supplementary material was not provided for review. This is a critical omission because: (1) Fig. S1 (apo Cz force-field comparison) is needed to assess whether the simulation protocol is appropriate, (2) Fig. S3 (per-replica ligand RMSD) is essential for evaluating whether the 3 × 250 ns replicas are consistent and whether the ligand binding mode is stable, and (3) Table S1 (full compound dataset) is needed to verify the QSAR data curation. Without these materials, the reproducibility and robustness of the computational results cannot be fully assessed.
- **Why it matters** The inability to verify key supporting data undermines confidence in the study's conclusions. For a computational study, full transparency of all data and analysis is essential for reproducibility.
- **Resolution test** Provide the supplementary material for review. Ensure that all figures and tables referenced in the main text are included and clearly labeled.

- **Minor Comments**
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / presentation
- **Affected element** Figure 4 (Williams plot)
- **Evidence pointer** Results section
- **Issue** The Williams plot (Fig. 4) shows compound labels using CP nomenclature, but the figure resolution appears low and many labels overlap, making it difficult to identify individual compounds. The warning leverage threshold (h* = 0.783) is mentioned but not visually indicated on the plot.
- **Required correction** Improve figure resolution and label placement to ensure all compound identifiers are readable. Add a vertical dashed line at h* = 0.783 to clearly indicate the warning leverage threshold.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Table 3
- **Evidence pointer** Results section
- **Issue** Table 3 reports "Pearson correlation coefficient (r)" values for each descriptor with pIC50. However, the text states that "descriptors with low linear correlation with biological activity (|r| < 0.3 relative to pIC50) were discarded." The reported r values for GATS8c (0.236) and RDFC24 (−0.273) are below 0.3, which appears to contradict the stated filtering criterion. The authors should clarify whether the filtering was applied before or after the OPS/GA selection, or whether the reported r values are from the final model rather than the initial filtering step.
- **Required correction** Clarify the descriptor selection workflow and explain why GATS8c and RDFC24, with |r| < 0.3, were retained. If the filtering was applied to a different descriptor set, state this explicitly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Computational methods
- **Issue** The MD simulation methods state that "no additional NaCl was added; thus, the explicit-solvent MD simulations were performed with neutralizing counterions only and do not reproduce physiological ionic strength." This is a significant limitation for studying protein-ligand interactions, as electrostatic screening effects are absent. The authors should discuss how this might affect the MM/GBSA results, particularly the electrostatic and polar solvation components.
- **Required correction** Add a brief discussion of how the absence of physiological ionic strength may affect the computed binding energies and whether this could contribute to the discrepancy between MM/GBSA and phenotypic activity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Table 10
- **Evidence pointer** Results section
- **Issue** Table 10 reports PC1 and PC2 as percentages, but the text states that these are "projected variance along the global principal component axes" from a concatenated trajectory. The sum of PC1 + PC2 varies substantially across systems (e.g., LMM2: 24.90 + 50.60 = 75.50%; LMM4: 58.46 + 17.14 = 75.60%; CP3: 47.70 + 36.85 = 84.55%). The authors should clarify whether these values represent the fraction of total variance explained by the first two global PCs for each system, or the projection of each system's variance onto the global PCs.
- **Required correction** Clarify the interpretation of PC1 and PC2 values in Table 10 and the associated text. If these are projections onto global PCs, state that the values represent the percentage of each system's variance captured by the first two global components.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 7 (FEL)
- **Evidence pointer** Results section
- **Issue** The FEL plots (Fig. 7) are described as having a color scale from 0 (blue) to 3 kcal mol⁻¹ (red), but the figure appears to be in grayscale in the provided manuscript, making it impossible to distinguish energy levels. The local minima (min1, min2, min3) are mentioned in the text but are not clearly marked on the figure.
- **Required correction** Ensure the FEL plots are in color or use grayscale patterns that are distinguishable. Clearly label the local minima discussed in the text (min1, min2, min3) on each panel.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation), R1-M2 (insufficient design rationale), R1-M4 (missing supplementary material)

- **Assessment against Nature-style criteria** 
  - **Originality**: Low. The study applies well-established computational methods (QSAR, docking, MD, MM/GBSA) to a known compound class (pyrazolones) and a well-studied target (cruzain). No new methodology is introduced. Similar integrated CADD studies for Chagas disease have been published previously by the same group (refs 25–27) and others.
  - **Scientific importance**: Moderate. Chagas disease is an important neglected tropical disease, and the identification of new antitrypanosomal agents is a valid goal. However, the study does not provide experimentally validated compounds or new biological insights. The computational predictions are not confirmed, and the authors acknowledge that the models do not reproduce the phenotypic activity ranking.
  - **Interdisciplinary readership**: Low. The manuscript is written for computational chemistry specialists. The extensive technical detail on QSAR validation metrics, force-field parameters, and MD analysis protocols would be inaccessible to most biologists, chemists, or clinicians interested in Chagas disease.
  - **Technical soundness**: Moderate. Individual computational methods are applied correctly and with appropriate validation. However, the disconnect between MM/GBSA and phenotypic activity, the omission of entropy in binding calculations, and the absence of physiological ionic strength in MD simulations raise concerns about the reliability of the quantitative conclusions.
  - **Readability for nonspecialists**: Low. The manuscript is dense with technical jargon and assumes familiarity with computational chemistry concepts. The abstract and conclusions are accessible, but the main text would be challenging for readers without a background in molecular modeling.

- **Recommendation posture** Currently not established from the provided evidence. The study is technically competent but lacks the experimental validation, novelty, and broad impact required for a high-profile journal. The manuscript would be more suitable for a specialized computational chemistry or medicinal chemistry journal. If the authors can provide experimental validation (e.g., biochemical Cz inhibition assays, cellular activity of LMM compounds) and address the major concerns, the work could be reconsidered.

# Risk / unsupported claims
1. The claim that LMM1–LMM4 are "promising antitrypanosomal candidates" is unsupported without experimental activity data. The QSAR-predicted pIC50 values (5.3–5.8) are intermediate and below the most active known compounds.
2. The claim that "contacts with S2/S3 subsite residues... may contribute to Cz recognition" is based on per-residue decomposition with differences within the noise of the method and cannot be considered established.
3. The claim that the FEL analysis reveals "ligand-dependent conformational sampling" that is biologically relevant is unsupported, as the authors acknowledge that "the small number of systems analyzed does not allow a robust statistical relationship... to be established."
4. The claim that the ADMET profiles "strengthen their candidacy for further experimental evaluation" is overstated, as ADMET predictions are based on computational models with known limitations and do not constitute experimental validation.