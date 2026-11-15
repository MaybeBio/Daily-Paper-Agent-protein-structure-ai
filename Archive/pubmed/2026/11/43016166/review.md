## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table references. No supplementary files were provided for review.
- **Assessment boundary** Assessment is limited to the claims and evidence presented in the provided manuscript text. Supplementary materials, figures, and tables are referenced but were not available for direct inspection.
- **Shared manuscript claim summary** The authors present CRAFT, a decoupled encoder-decoder generative model for antigen-specific TCR CDR3β sequence design. The model combines a BERT-based antigen encoder (PrimeBERT) with a GPT-2-based autoregressive receptor decoder (PrimeTCR), coupled via cross-attention and augmented with Atchley factor physicochemical embeddings. The authors claim competitive performance in sequence naturalness, conditional specificity, diversity, and predicted structural plausibility across common, rare, and novel epitope settings.
- **Visible evidence base** Results sections describing statistical naturalness (length distributions, p_gen, K-mer analysis), fidelity metrics (Char-BLEU, NSR), conditional separation (Jaccard similarity), structural prediction (pLDDT, pTM, RMSD), ablation studies, and attention analysis. Materials and methods sections describing datasets, model architecture, training strategy, and inference procedures.
- **Missing materials affecting confidence** All figures, supplementary tables, and supplementary notes were referenced but not provided. This includes Fig. 1-6, Supplementary Figs S1-S20, and Supplementary Tables S1-S14. Without these, quantitative results, statistical comparisons, and architectural details cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a technically sound and well-motivated approach to a challenging problem in computational immunology. The decoupled architecture with explicit physicochemical constraints is a reasonable design choice, and the evaluation framework is comprehensive in scope. However, the absence of all figures and supplementary materials severely limits the ability to assess the validity of the reported results. The claims of competitive performance are plausible but not verifiable from the provided text alone. The manuscript would benefit from clearer reporting of baseline comparisons, statistical significance, and experimental validation pathways.
- **Who would be interested in the results, and why** Researchers in computational immunology, TCR engineering, and protein design would find this work relevant. The model addresses a practical need for generating antigen-specific TCR candidates, which is of interest to those developing TCR-based immunotherapies. The methodological contributions around conditional generation with physicochemical constraints may also appeal to the broader generative protein model community.
- **Major strengths** The problem is well-defined and clinically relevant. The decoupled architecture is a thoughtful response to the data scarcity challenge in TCR design. The evaluation framework spans multiple levels (sequence, structure, representation), which is more comprehensive than many comparable studies. The authors are appropriately cautious in their claims, explicitly acknowledging the computational nature of their structural and functional assessments.
- **Major Concerns** The most significant concern is the complete absence of all figures and supplementary materials, making the reported quantitative results unverifiable. Additionally, the manuscript lacks experimental validation, which the authors acknowledge but which limits the practical significance of the claims. The comparison with baseline methods is described but the specific implementation details and hyperparameters for baselines are not fully specified. The clinical relevance claims, while reasonable, are speculative without functional data.
- **Technical failings that need to be addressed before the case is established** The manuscript cannot be fully evaluated without the figures and supplementary materials. The statistical methods for comparing distributions across models are not described in sufficient detail. The choice of λ = 0.5 is stated to be based on a sensitivity sweep, but the criteria for "most balanced performance" are not quantified. The attention analysis, while interesting, is presented as supportive rather than causal, which is appropriate but limits its interpretive value.
- **Assessment against Nature-style criteria** Originality: The decoupled architecture with explicit physicochemical constraints is a novel contribution, though it builds on established transformer and protein language model approaches. Scientific importance: The problem is important, and the approach has potential utility, but the lack of experimental validation limits the immediate impact. Interdisciplinary readership: The work bridges machine learning, immunology, and structural biology, which could attract a broad audience. Technical soundness: The architecture and training strategy are reasonable, but the missing supplementary materials prevent full assessment. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with TCR biology and transformer architectures.
- **Recommendation posture** Supportive if technical concerns are resolved. The approach is promising and the evaluation framework is thoughtful, but the manuscript cannot be accepted in its current form without the full figures and supplementary materials, and without clearer reporting of statistical methods and baseline implementations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript reports quantitative results for sequence naturalness, fidelity, specificity, diversity, and structural plausibility across multiple evaluation settings.
- **Evidence pointer** Figures 1-6, Supplementary Figures S1-S20, Supplementary Tables S1-S14 (location not provided)
- **Concern** All figures and supplementary materials are referenced but were not provided for review. This includes the main architectural diagram (Fig. 1), all quantitative comparisons (Figs. 2-6), and all supplementary data tables. Without these, the reported numerical results (e.g., p_gen values, JS divergences, pLDDT scores, RMSD values) cannot be verified, and the architectural details cannot be confirmed.
- **Why it matters** The core claims of the manuscript rest on quantitative comparisons and architectural descriptions that are entirely contained in the missing materials. A reviewer cannot assess whether the reported performance is accurate, whether the comparisons are fair, or whether the architecture is implemented as described.
- **Resolution test** Provide all figures and supplementary materials for review. Ensure that all quantitative claims in the main text are traceable to specific figures or tables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim** The manuscript reports statistically significant differences between CRAFT and baseline methods (e.g., p-values from Welch's t-tests with Holm-Bonferroni correction).
- **Evidence pointer** Results section "Benchmark evaluation of antigen-conditioned sequence specificity and plausibility" (location not provided)
- **Concern** The statistical methods are mentioned but not described in sufficient detail. The specific tests, sample sizes, effect sizes, and confidence intervals are not reported in the text. The choice of two-sided Welch's t-tests is appropriate for unequal variances, but the assumptions and limitations are not discussed. The Holm-Bonferroni correction is mentioned but the number of comparisons and the family-wise error rate are not specified.
- **Why it matters** Without detailed statistical reporting, the reader cannot assess the robustness of the claimed differences between CRAFT and baselines. This is particularly important given the high variability often observed in generative model outputs.
- **Resolution test** Provide complete statistical reporting for all comparisons, including test statistics, degrees of freedom, effect sizes, confidence intervals, and the full correction procedure. Justify the choice of statistical tests and discuss their assumptions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness
- **Claim** CRAFT demonstrates competitive or superior performance compared to TCR-epiDiff, GRATCR, TcrDesign, and TCR-T5.
- **Evidence pointer** Results section "CRAFT generates statistically natural and combinatorially consistent receptor libraries" and "Benchmark evaluation of antigen-conditioned sequence specificity and plausibility" (location not provided)
- **Concern** The implementation details for the baseline methods are not provided. It is unclear whether the baselines were run using their original code and hyperparameters, or whether they were reimplemented. The training data, preprocessing steps, and evaluation protocols for baselines are not specified. This makes it difficult to determine whether the comparisons are fair.
- **Why it matters** Unfair or inconsistent baseline implementations can lead to misleading conclusions about relative performance. The reader needs to know that all methods were evaluated under identical conditions.
- **Resolution test** Provide detailed descriptions of baseline implementations, including source code availability, hyperparameter settings, training data, and any modifications made. Ideally, provide a table summarizing the experimental setup for each method.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** External validation
- **Claim** CRAFT generates antigen-specific TCR CDR3β sequences with predicted structural plausibility and potential clinical relevance.
- **Evidence pointer** Results section "Structural characterization and interface distribution analysis of CRAFT-generated TCR candidates for clinically relevant cancer epitopes" (location not provided)
- **Concern** All structural and functional assessments are based on computational predictions. No experimental validation is presented, such as binding assays, T-cell activation assays, or structural characterization. The authors acknowledge this limitation, but the lack of any wet-lab validation significantly limits the strength of the claims regarding clinical relevance.
- **Why it matters** Computational predictions of binding and structure are known to have high false-positive rates. Without experimental validation, it is unclear whether the generated sequences would function as intended in biological systems.
- **Resolution test** Provide at least preliminary experimental validation for a small number of generated sequences, or clearly frame the work as purely computational with explicit statements about the need for experimental follow-up.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model architecture description
- **Evidence pointer** Materials and methods, "Model architecture of CRAFT" (location not provided)
- **Issue** The description of the cross-attention mechanism and residual fusion is somewhat brief. The equations for the attention computation and fusion step are referenced but not fully explained in the text.
- **Required correction** Provide a more detailed description of the cross-attention mechanism, including the exact computation steps and how the residual fusion is implemented. Consider including a pseudocode or algorithm box.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Hyperparameter settings
- **Evidence pointer** Materials and methods, "Training strategy" (location not provided)
- **Issue** The manuscript does not report key hyperparameters such as learning rate, batch size, number of layers, hidden dimensions, and optimizer settings for the pretraining and fine-tuning stages.
- **Required correction** Provide a table or list of all hyperparameters used in the experiments, including those for pretraining, fine-tuning, and inference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Attention analysis
- **Evidence pointer** Results section "Attention in CRAFT aligns with putative TCR contact regions" (location not provided)
- **Issue** The attention analysis is presented as supportive evidence, but the interpretation is somewhat speculative. The manuscript states that attention is "not an exclusive proxy for direct physical contacts" but does not discuss alternative explanations in detail.
- **Required correction** Expand the discussion of the attention analysis to consider alternative interpretations, such as attention reflecting sequence context or longer-range dependencies, and discuss the limitations of using attention as evidence for functional relevance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Dataset description
- **Evidence pointer** Materials and methods, "Datasets and preprocessing" (location not provided)
- **Issue** The manuscript states that the training and validation sets were segregated at the epitope level, but does not provide details on the number of unique epitopes, the distribution of epitope frequencies, or the potential for epitope overlap between training and validation sets.
- **Required correction** Provide a more detailed description of the dataset composition, including the number of unique epitopes, the distribution of epitope frequencies, and any filtering criteria applied.

## Risk / unsupported claims
- The claim that CRAFT "demonstrates competitive sequence naturalness" is not verifiable without the figures and supplementary tables showing the actual distributions and comparisons.
- The claim that CRAFT achieves "favorable performance in specific binding" relies entirely on the TCRBinder prediction tool, which is itself a computational model with known limitations. The manuscript does not discuss the accuracy or limitations of TCRBinder.
- The claim that CRAFT "holds potential to support clinical translation" is speculative and not supported by any experimental evidence.
- The claim that the attention analysis provides evidence that CRAFT "captures structurally relevant patterns" is presented as supportive but is not rigorously quantified or compared to random attention patterns.
- The novelty rates reported in the evaluation overview (0.622, 0.713, 0.805, 0.884) are presented without confidence intervals or comparison to baseline methods, making it difficult to assess their significance.