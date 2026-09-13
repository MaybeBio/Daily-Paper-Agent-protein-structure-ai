## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** The manuscript as provided, including main text, figures, tables, and references. Supplementary information was not provided.
- **Shared manuscript claim summary** The authors present an integrated computational workflow (2D-QSAR, molecular docking, MD simulations, MM/GBSA, ADMET) to characterize phenyl-dihydropyrazolone derivatives with reported antitrypanosomal activity and to investigate their putative interaction with cruzain (Cz). Four new derivatives (LMM1–LMM4) were designed based on the QSAR model. The study concludes that these compounds are promising antitrypanosomal scaffolds with computationally predicted Cz-binding modes, but that the observed whole-cell activity cannot be directly attributed to Cz inhibition without biochemical validation.
- **Visible evidence base** Main text, 8 figures, 11 tables, 114 references.
- **Missing materials affecting confidence** Supplementary information (ZIP and PDF files) was not provided. This includes the structures of the 35 original compounds (Table S1), regression coefficients before/after outlier removal (Table S2), 3D conformations of docked poses (Fig. S2), per-replica ligand RMSD time series (Fig. S3), and apo Cz force-field sensitivity analysis (Fig. S1). The absence of these materials limits the ability to independently verify key aspects of the QSAR dataset, docking poses, and MD convergence.

## Reviewer
- **Overall assessment** This manuscript presents a thorough and methodologically sound computational investigation of pyrazolone derivatives as potential antitrypanosomal agents targeting cruzain. The work is notable for its integration of multiple computational techniques and its appropriately cautious interpretation of results, particularly the acknowledged discrepancy between MM/GBSA predictions and whole-cell activity data. However, several technical concerns regarding the QSAR model construction, docking validation, and MD simulation setup require clarification. The absence of supplementary materials prevents full evaluation of some claims.
- **Who would be interested in the results, and why** Researchers in computational drug discovery for neglected tropical diseases, particularly those working on Chagas disease and cysteine protease inhibitors. The study provides a practical example of integrating ligand-based and structure-based methods, and the cautious interpretation of computational predictions in the absence of biochemical data is a useful methodological lesson.
- **Major strengths** 1) Comprehensive and well-integrated computational workflow covering QSAR, docking, MD, and free energy calculations. 2) Appropriate and transparent acknowledgment of limitations, particularly the discrepancy between MM/GBSA and phenotypic activity, and the caveat that whole-cell activity does not necessarily imply Cz inhibition. 3) Detailed reporting of QSAR validation metrics, including multiple external validation parameters. 4) The design of new compounds (LMM1-LMM4) is based on the QSAR model and is presented as exploratory rather than as a claim of superior potency.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness – QSAR model construction
    - **Claim pointer** The QSAR model was built using 33 compounds after removing CP3 and CP132 as outliers. The model uses 5 descriptors and 3 latent variables.
    - **Evidence pointer** Section "2D-QSAR model: construction, validation, and molecular design", Tables 1-3, Equation 1.
    - **Concern** The QSAR model uses 5 descriptors for only 23 training compounds, yielding a ratio of approximately 4.6 compounds per descriptor. While the authors report 3 latent variables, the initial descriptor selection process (4700 descriptors reduced to 342, then to 12 via OPS, then to 5 via GA) is described in a way that makes it difficult to assess the risk of overfitting. The y-randomization test is presented, but the specific R² and Q² values for the randomized models are not reported numerically, only shown in a figure. The claim that the model has "good explanatory power" (R²=0.892) and "good predictive performance" (Q²LOO=0.805) needs to be evaluated in the context of this low sample-to-descriptor ratio.
    - **Why it matters** A QSAR model with a high descriptor-to-compound ratio, even with cross-validation, is at risk of overfitting and may not generalize to new compounds. The external validation (R²pred=0.701) is acceptable but not strong. If the model is overfitted, the design of LMM1-LMM4 and the interpretation of the descriptors may be unreliable.
    - **Resolution test** Provide the numerical R² and Q² values for all 50 y-randomization runs (e.g., as a supplementary table). Justify the descriptor-to-compound ratio more explicitly, perhaps by reporting the Akaike Information Criterion (AIC) or Bayesian Information Criterion (BIC) for models with different numbers of latent variables. Demonstrate that the model's predictive performance on the test set is robust to the specific choice of training/test split, for example by performing multiple random splits and reporting the distribution of R²pred values.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness – Docking validation and protocol
    - **Claim pointer** The FITTED docking protocol was selected because it reproduced the crystallographic binding mode of B95 with an RMSD of 1.017 Å. This protocol was then applied to dock CP3, CP98, and LMM1-LMM4.
    - **Evidence pointer** Section "Molecular docking", Table 6, Table 7.
    - **Concern** The redocking validation was performed by Barbosa et al. [27] and is cited as methodological support. However, the current manuscript does not present the redocking results directly, nor does it demonstrate that the FITTED protocol is appropriate for the specific pyrazolone derivatives studied here. The pyrazolones are structurally distinct from the crystallographic ligand B95. A successful redocking of B95 does not guarantee that the protocol will correctly predict the binding mode of a different chemotype. Furthermore, the docking results for CP3 show "No interactions" (Table 7), which is unusual for a compound with high phenotypic activity and raises questions about the docking protocol's ability to capture relevant binding.
    - **Why it matters** The entire structure-based analysis (MD, MM/GBSA) depends on the initial docking poses. If the docking protocol is not validated for the pyrazolone series, the subsequent simulations may be exploring incorrect binding modes, rendering the structural and energetic interpretations unreliable.
    - **Resolution test** Perform cross-docking or self-docking of at least one representative pyrazolone derivative (e.g., CP3 or CP98) if a co-crystal structure exists. If not, provide a more rigorous justification for the transferability of the B95 redocking protocol. Discuss the "No interactions" result for CP3 and explain why this does not invalidate the docking approach. Consider using multiple docking programs and consensus scoring to increase confidence in the predicted poses.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness – MD simulation setup
    - **Claim pointer** MD simulations were performed with neutralizing counterions only (13 Na⁺) and no additional NaCl, thus not reproducing physiological ionic strength.
    - **Evidence pointer** Section "Molecular dynamics (MD) simulations and structural analysis".
    - **Concern** The absence of physiological salt (e.g., 150 mM NaCl) is a significant simplification. Ionic strength can affect protein stability, ligand binding, and the conformational sampling of flexible loops, particularly the Asp57-Gly65 and Glu95-Gly105 regions identified as flexible. The authors acknowledge this in the methods but do not discuss its potential impact on the results. The apo Cz simulations with ff14SB/TIP3P and ff19SB/OPC (Fig. S1, not provided) are a good step, but they do not address the effect of ionic strength on the ligand-bound systems.
    - **Why it matters** The structural and energetic conclusions (RMSF, PCA, FEL, MM/GBSA) are drawn from simulations at non-physiological ionic strength. The observed ligand-dependent conformational behavior and the computed binding free energies could be artifacts of this simplified solvent model.
    - **Resolution test** Acknowledge this limitation more prominently in the discussion. If feasible, repeat one or two key simulations (e.g., CP3 and LMM2) with physiological salt (e.g., 150 mM NaCl) to assess the sensitivity of the results. If not feasible, provide a clear justification for why the neutralizing-only condition is expected to be adequate for the specific conclusions drawn.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific importance – Interpretation of results
    - **Claim pointer** The MM/GBSA ranking did not reproduce the phenotypic activity trend. The authors interpret this as a limitation of the method and suggest that Cz may not be the sole target.
    - **Evidence pointer** Section "MM/GBSA binding free energy estimates and per-residue energy decomposition", Table 11.
    - **Concern** The authors correctly identify the discrepancy between MM/GBSA and phenotypic data. However, the subsequent discussion and conclusions still heavily emphasize the structural hypotheses about Cz recognition (S2/S3 subsites, conformational adaptability) based on the MD and MM/GBSA analyses. Given that the primary computational model (MM/GBSA) fails to rank the compounds correctly, the confidence in the more detailed structural interpretations (per-residue decomposition, FEL) is substantially weakened. The paper would be strengthened by a more explicit discussion of what the MM/GBSA failure implies for the validity of the entire structure-based modeling approach for this series.
    - **Why it matters** The core scientific claim of the paper is that these pyrazolones are "antitrypanosomal scaffolds" with a "putative interaction with Cz." If the computational evidence for Cz interaction is weak (docking not validated for the series, MD at non-physiological conditions, MM/GBSA fails to rank), then the paper's main contribution is primarily the QSAR model and the design of LMM1-LMM4, with the structure-based part being a speculative hypothesis.
    - **Resolution test** Reframe the conclusions to more clearly separate the validated (QSAR, ADMET) from the speculative (Cz binding mode). Explicitly state that the MM/GBSA results do not support a direct relationship between computed Cz binding affinity and whole-cell activity for this series, and that the structural hypotheses about Cz recognition are tentative and require experimental testing. Consider whether the structure-based sections could be shortened or presented as a secondary, exploratory analysis.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Introduction
    - **Evidence pointer** Section "Introduction", paragraph 4.
    - **Issue** The introduction is well-written but could be more concise. The justification for choosing Cz as the target is repeated in multiple paragraphs.
    - **Required correction** Consolidate the discussion of Cz as a target into a single, focused paragraph.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical soundness – Reporting
    - **Affected element** Methods
    - **Evidence pointer** Section "Molecular dynamics (MD) simulations and structural analysis".
    - **Issue** The authors state that "No additional NaCl was added; thus, the explicit-solvent MD simulations were performed with neutralizing counterions only and do not reproduce physiological ionic strength." This is a clear and honest statement, but it is buried in the methods. The potential impact of this choice should be discussed in the results or discussion.
    - **Required correction** Add a brief sentence in the Discussion section acknowledging the limitation of the non-physiological ionic strength and its potential impact on the observed conformational behavior and binding energetics.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical soundness – Data presentation
    - **Affected element** Results
    - **Evidence pointer** Table 7.
    - **Issue** Table 7 shows that CP3 has "No interactions" in the docking analysis. This is a striking result for the most active compound and is not discussed in the text.
    - **Required correction** Add a brief explanation in the "Molecular docking calculations" section. For example, does this mean the pose was not well-resolved, or that the PoseView server failed to detect interactions? This is important for the reader's confidence in the docking results.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Scientific importance – Claims
    - **Affected element** Conclusions
    - **Evidence pointer** Section "Conclusions".
    - **Issue** The conclusion states that the study "provides a computational framework for prioritizing antitrypanosomal pyrazolone derivatives." This is a reasonable claim, but the framework's utility is limited by the failure of the structure-based component to explain the activity data.
    - **Required correction** Qualify this statement to reflect that the framework is primarily useful for QSAR-based design and ADMET profiling, while the structure-based component generates hypotheses that require experimental validation.

- **Technical failings that need to be addressed before the case is established** R1-M1 (QSAR overfitting risk), R1-M2 (docking validation for the pyrazolone series). These are blocking concerns because they directly affect the validity of the core computational models that underpin the design of LMM1-LMM4 and the structural interpretation of their binding.

- **Assessment against Nature-style criteria**
    - **Originality:** Moderate. The integration of methods is standard, but the application to this specific pyrazolone series and the candid discussion of the MM/GBSA-phenotypic activity discrepancy are valuable.
    - **Scientific importance:** Moderate. The work addresses a relevant problem (Chagas disease drug discovery) but does not provide a breakthrough. The main value is as a case study in computational drug design, highlighting both the potential and the pitfalls of these methods.
    - **Interdisciplinary readership:** Low. The paper is highly specialized and will primarily interest computational chemists and medicinal chemists working on Chagas disease. The technical detail and lack of experimental validation limit its appeal to a broader biological or clinical audience.
    - **Technical soundness:** Moderate. The methods are generally appropriate and well-described, but there are significant concerns about the QSAR model's robustness and the docking protocol's validation for the specific compounds studied. The MD setup has a notable limitation (no physiological salt).
    - **Readability for nonspecialists:** Good. The paper is well-structured and clearly written, with a logical flow. The authors do a good job of explaining the rationale for each step.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a substantial amount of work and the authors' cautious interpretation of their own results is commendable. However, the blocking concerns regarding QSAR overfitting and docking validation must be addressed convincingly. The paper would be significantly strengthened by addressing these issues and by more clearly separating the validated QSAR/ADMET findings from the more speculative structure-based hypotheses. In its current form, the evidence for the central claim of a "putative interaction with Cz" is not fully established from the provided evidence.

## Risk / unsupported claims
- The claim that the FITTED docking protocol is validated for the pyrazolone series is unsupported, as the validation was performed on a different ligand (B95).
- The claim that the MD simulations provide a reliable description of Cz-ligand interactions is weakened by the non-physiological ionic strength.
- The claim that the per-residue decomposition and FEL analyses provide meaningful structural hypotheses for Cz recognition is not fully supported, given the failure of the MM/GBSA ranking to match the phenotypic data. These are presented as qualitative, which is appropriate, but their value is diminished by the lack of correlation with the primary experimental endpoint.