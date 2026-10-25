## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplemental information references.
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided evidence. No assessment of editorial fit or scope beyond the stated journal context.
- **Shared manuscript claim summary** The authors present DGMPNN, a message-passing neural network pre-trained on an inverse protein folding task, for predicting mutation-induced changes in protein-protein interaction binding affinity. They claim state-of-the-art performance on benchmark datasets (S1131, S4169) and deep mutational scanning data, and demonstrate experimental validation of computationally selected multi-site variants in the SARS-CoV-2 RBD-hACE2 complex.
- **Visible evidence base** Main text figures (Figures 1–7), tables (Tables 1–2), supplemental figures and tables (Figures S1–S5, Tables S1–S13), and method descriptions in the STAR Methods section.
- **Missing materials affecting confidence** The full supplemental information files (Figures S1–S5, Tables S1–S13) are referenced but not provided in the submitted material. The source data files (Data S1, Data S2) are also not available. The code repository is cited but not accessible for review. The manuscript does not include a detailed description of the pre-training dataset composition beyond a reference to a prior filtering procedure.

## Reviewer

- **Overall assessment** The manuscript presents a potentially useful deep learning framework for predicting mutational effects on protein-protein interactions. The core idea of leveraging inverse protein folding pre-training for downstream binding affinity prediction is reasonable and aligns with current trends in protein representation learning. However, the evidence provided is insufficient to fully evaluate the claims of state-of-the-art performance and the generalizability of the model. Several methodological details are unclear, and the experimental validation, while promising, is limited in scope. The manuscript would benefit from more rigorous benchmarking, clearer reporting of statistical significance, and a more thorough discussion of limitations.

- **Who would be interested in the results, and why** Researchers in computational protein engineering, protein design, and structural bioinformatics would be the primary audience. The work is also relevant to those studying viral evolution, particularly SARS-CoV-2, given the application to RBD-hACE2 interactions. The potential for accelerating antibody and therapeutic protein design would interest a broader biotechnology audience.

- **Major strengths**
  - The use of inverse protein folding as a pre-training task is a sensible and potentially powerful approach for learning protein representations that are sensitive to local chemical environment.
  - The model architecture is relatively simple and does not rely on pre-computed biophysical features, which is a practical advantage.
  - The inclusion of experimental validation for computationally selected multi-site variants is a strong point, demonstrating a real-world application.
  - The analysis of attention scores to identify key interaction residues and correlated mutational effects is an interesting and potentially valuable interpretability feature.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The model achieves state-of-the-art performance on multiple benchmark datasets and deep mutational scanning datasets.
- **Evidence pointer** Table 1, Table 2, Results section "Model performance on non-standard data"
- **Concern** The claim of state-of-the-art performance is not fully substantiated. The comparison in Table 1 is made against a set of methods with reported performance from the literature, but the data partitioning details for these methods are not available. The authors state they repeated their evaluation with three random seeds, but it is unclear if the reported values for other methods are averages or single runs. A rigorous comparison requires a standardized evaluation protocol, including identical data splits and statistical testing for significance. The performance on the SARS-CoV-2 dataset (Table 2) is compared against a limited set of methods, and the improvement over the best baseline (FEP) is not demonstrated to be statistically significant. The PCC values for the woDMS model are low (0.45), which raises questions about the model's practical utility for this specific application without fine-tuning.
- **Why it matters** Without a rigorous and statistically sound comparison, the central claim of the paper cannot be verified. The lack of standardized evaluation protocols makes it difficult to assess whether DGMPNN is genuinely superior to existing methods or merely competitive under different conditions.
- **Resolution test** The authors should provide a detailed comparison using identical data splits for all methods, report confidence intervals or p-values for the performance differences, and include a statistical test (e.g., Steiger's test, which is mentioned in the methods) for the correlation coefficients. They should also clarify the evaluation protocol for the methods cited from the literature.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The model is pre-trained on an inverse protein folding task and fine-tuned for predicting mutation-induced changes in binding affinity.
- **Evidence pointer** STAR Methods, "The pretraining procedure" and "Finetune for the downstream PPI affinity prediction task"
- **Concern** The description of the pre-training and fine-tuning procedures is insufficient for reproduction. The exact composition of the pre-training dataset (number of protein complexes, redundancy filtering, etc.) is not described in detail. The hyperparameters for fine-tuning (learning rate, number of epochs, batch size) are not fully specified. The method for calculating ΔΔG from predicted ln(KD) values is mentioned but not detailed. The manuscript states that the model predicts ln(KD) directly, but the relationship between the predicted ln(KD) for the mutant and wild-type and the final ΔΔG value needs to be explicitly defined. The use of a fixed data partition for the S2462 dataset is mentioned, but the details of this partition are not provided.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without a complete and unambiguous description of the training and evaluation procedures, other researchers cannot build upon this work or verify its findings.
- **Resolution test** The authors should provide a complete description of the pre-training dataset, all hyperparameters, the exact formula for ΔΔG calculation, and the data splitting strategy. Ideally, the code and trained model weights should be made publicly available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Validity of claims
- **Claim pointer** Experimental validation using computationally selected multi-site variants of the SARS-CoV-2 RBD-hACE2 complex showed strong agreement between predicted and experimentally measured binding affinities.
- **Evidence pointer** Results section "Validation of the multisite mutation predictions using RBD-hACE2", Figures 6 and 7
- **Concern** The experimental validation is a key strength, but the analysis is incomplete. The authors report that 5 out of 9 selected variants maintain binding affinity, but they do not provide a clear statistical measure of the agreement between predicted and experimental values for all tested variants. The correlation coefficients (PCC = 0.726, Spearman = 0.886) are reported for a subset of 6 variants, but the criteria for excluding the other 3 variants (7M, 8M-B, 14M) from this correlation analysis are not clearly justified. The authors state these variants are in an "abnormal oligomeric state," but this is a post-hoc observation that may not be a valid reason for exclusion from the predictive performance assessment. The selection of variants for experimental testing is not described in detail, and the criteria for choosing these specific 9 variants from the large library are unclear.
- **Why it matters** The experimental validation is the most direct evidence for the model's practical utility. If the analysis is not rigorous or the selection criteria are biased, the strength of this claim is significantly weakened. The exclusion of data points that do not fit the model's predictions is a serious concern.
- **Resolution test** The authors should report the predicted and experimental ΔΔG values for all 9 tested variants, including those that failed to fold. They should provide a clear rationale for any data exclusion and perform a correlation analysis on the full dataset. The selection criteria for the 9 variants should be described in detail.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The model is capable of gaining generalizable knowledge of PPIs from the training data, as evidenced by its ability to identify key residues and predict effects on non-homologous complexes.
- **Evidence pointer** Results section "The gaining knowledge ability of DGMPNN", Figure 3, Table S5
- **Concern** The claim of generalizability is only weakly supported. The attention-based identification of known key residues (Q493, N498, etc.) is a qualitative observation and does not constitute a quantitative validation of the model's interpretability. The performance on the Clostridium thermocellum complex (Table S5) is modest (PCC = 0.514 for interface residues) and is only compared against FoldX. The authors acknowledge a "systematic bias" between measurement techniques, but this is not explored in detail. The claim that the model can "gain generalizable knowledge" is an overstatement based on the limited evidence presented.
- **Why it matters** The generalizability of the model is a key selling point. If the model only works well on complexes similar to those in the training set, its utility is limited. The current evidence is not sufficient to support the strong claim of generalizability.
- **Resolution test** The authors should provide a more quantitative analysis of the attention scores, perhaps by comparing them to known functional data or alanine scanning mutagenesis results. They should also test the model on a more diverse set of non-homologous complexes and compare its performance against a wider range of baselines.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure is complex and the flow of information is not immediately clear. The distinction between the pre-training and fine-tuning stages could be more explicitly illustrated.
- **Required correction** Consider simplifying the figure or adding a clearer schematic that separates the pre-training and fine-tuning phases.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table lists performance values for many methods, but it is not clear which values are taken from the original publications and which are reproduced by the authors. The footnote mentions "PCC values of DGMPNN are expressed as the mean value across three independent repeats," but this is not stated for the other methods.
- **Required correction** Clarify the source of each performance value in the table, and specify whether the values for other methods are from a single run or an average.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Model performance on the benchmark dataset"
- **Evidence pointer** Figures 2C–2H
- **Issue** The authors report different PCC values for different categories of mutations (e.g., polar/charged vs. hydrophobic). It is unclear if these differences are statistically significant.
- **Required correction** Perform and report a statistical test (e.g., a test for comparing correlation coefficients) to determine if the performance differences across mutation categories are significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** STAR Methods, "Featurization of protein complex"
- **Evidence pointer** STAR Methods
- **Issue** The description of the graph featurization mentions 25 atom pairs and 16 Gaussian kernels, resulting in a 400-dimensional vector. The calculation (25 * 16 = 400) is correct, but it is unclear if the relative position embeddings are concatenated to this vector or handled separately.
- **Required correction** Clarify how the relative position embeddings are incorporated into the edge features.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the model's limitations is brief and does not fully address the potential impact of the temporal gap in training data on the model's performance for emerging variants.
- **Required correction** Expand the discussion on this limitation and suggest potential strategies to mitigate it.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of rigorous, statistically sound benchmarking against existing methods.
  - R1-M2: Insufficient methodological detail for reproduction.
  - R1-M3: Incomplete and potentially biased analysis of experimental validation data.

- **Assessment against Nature-style criteria**
  - **Originality:** The application of inverse protein folding pre-training to the specific task of predicting mutational effects on PPI binding affinity is a reasonable and somewhat novel combination, though the individual components are established. The attention-based interpretability analysis adds a unique element.
  - **Scientific importance:** The problem addressed is of high importance for protein engineering and drug discovery. However, the demonstrated improvement over existing methods is not yet convincing, which limits the immediate scientific impact.
  - **Interdisciplinary readership:** The work is primarily of interest to computational biologists and bioinformaticians. The experimental validation may attract a slightly broader audience, but the technical nature of the manuscript limits its accessibility.
  - **Technical soundness:** The core methodology is plausible, but the evaluation and validation are not sufficiently rigorous to establish technical soundness. The lack of detail on training procedures and the incomplete experimental analysis are significant concerns.
  - **Readability for nonspecialists:** The manuscript is written in a technical style that would be challenging for a non-specialist. The abstract and introduction are relatively clear, but the results and methods sections assume significant background knowledge.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising approach, but the central claims of state-of-the-art performance and robust experimental validation are not adequately supported. The authors must address the major concerns regarding benchmarking rigor, methodological detail, and experimental data analysis before the case for this work can be considered established.

## Risk / unsupported claims
- The claim of "state-of-the-art performance" is not supported by a rigorous, statistically sound comparison.
- The claim that the model can "gain generalizable knowledge" is an overstatement based on the limited evidence presented.
- The claim of "strong agreement" between predictions and experimental data is not fully supported by the analysis, particularly given the exclusion of three variants from the correlation analysis.
- The generalizability of the model to non-homologous complexes is not well established, as it is only tested on a single additional complex.
- The interpretability of the attention scores is only qualitatively demonstrated and not quantitatively validated.