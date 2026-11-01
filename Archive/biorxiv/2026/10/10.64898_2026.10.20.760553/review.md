## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions, availability statements) as provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and presentation as inferable from the supplied text. Figures and tables are referenced but not directly inspected.
- **Shared manuscript claim summary** The authors investigate how protein language models (pLMs) perform on limited protein-protein complex datasets, and whether targeted (distribution-narrowing) ablation and active learning (AL) with generative model (ESM-3) augmentation can improve predictive performance on residue-residue contact map prediction.
- **Visible evidence base** Text descriptions of results, figure and table references, methodological descriptions. No actual figures, tables, or numerical data were provided for direct inspection.
- **Missing materials affecting confidence** All figures (Figures 1–11, S1–S11), tables (Tables 1–3), hyperparameter details, and quantitative results. Statistical significance testing, error bars, and exact numerical values are not directly verifiable.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and practically important question: how to train protein language models when data are scarce. The framing around dataset distribution versus dataset size is conceptually useful, and the use of generative models for augmentation is a relevant direction. However, the evidence as presented is largely qualitative, with key quantitative results and visualizations not directly available for inspection. Several claims about model performance, augmentation benefits, and distributional effects rest on descriptions that are difficult to fully evaluate without the underlying data. The manuscript would benefit from clearer reporting of effect sizes, variability, and statistical comparisons.
- **Who would be interested in the results, and why** Researchers working on protein language models, protein-protein interaction prediction, and machine learning in structural biology. The findings on data augmentation strategies and the interaction between dataset size and distribution are relevant to practitioners developing predictive models for proteins, particularly in low-data regimes. The work may also interest those studying the behavior of generative models in scientific data augmentation.
- **Major strengths** The question is well-motivated and practically relevant. The experimental design includes multiple pLM sizes, two ablation strategies (uniform vs targeted), and a clear AL pipeline. The use of ESM-3 as a generative augmenter is a current and interesting approach. The authors also acknowledge limitations and discuss potential biases in generative models.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The claim that targeted ablation permits an order-of-magnitude decrease in training dataset size while maintaining in-distribution generalization performance.
  - **Evidence pointer** Figure 4, Figure S3, Results section "Effects of Dataset Ablation on Model Performance"
  - **Concern** The central quantitative claim of an order-of-magnitude reduction in dataset size is presented without direct numerical evidence in the text. The described MCC values are qualitative ("struggle to surpass 0.2", "as high as 0.5"), and the comparison between targeted and uniform ablation at matched dataset sizes is not quantified. The claim that targeted ablation to 20% yields train/validation MCCs exceeding those on the full dataset is striking but not supported by visible data.
  - **Why it matters** This is the primary finding of the paper. Without clear quantitative evidence, including effect sizes and variability across the five trials, the claim cannot be assessed for robustness or practical significance.
  - **Resolution test** Provide the actual MCC values (mean and standard error) for all models, ablation types, and dataset sizes, with a direct comparison between targeted and uniform ablation at matched sizes. Include statistical tests or confidence intervals to support the order-of-magnitude claim.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The claim that AL augmentation with ESM-3-generated complexes produces a "small but consistent increase" in both in- and out-of-distribution MCC.
  - **Evidence pointer** Figure 11, Figure S11, Results section "Changes in Model Performance When Ablated Sets are Augmented With Generated Samples"
  - **Concern** The reported improvements are described as "small but consistent," but no numerical values, error bars, or statistical tests are provided in the text. The claim of consistency across trials is not verifiable. Additionally, the observation that 20% ablations fail to improve or even decrease in performance upon augmentation is presented without quantitative detail.
  - **Why it matters** The effectiveness of the proposed AL pipeline is a key contribution. Without quantitative evidence, the practical value of the augmentation strategy cannot be determined.
  - **Resolution test** Report exact MCC values before and after augmentation for each ablation condition, with measures of variability. Include statistical comparisons (e.g., paired tests across trials) to substantiate the "consistent increase" claim.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological clarity
  - **Claim pointer** The claim that CKA scores are a suitable measure of model disagreement for selecting uncertain complexes.
  - **Evidence pointer** Methods section "Measuring the similarity of contact maps", Figure S1
  - **Concern** The choice of CKA over other similarity measures is justified only by a reference to Figure S1, which is not available for inspection. The text states that CKA exhibited "the least overlap between the train, validation, and test sets," but the basis for selecting this criterion is not explained. It is unclear why minimal overlap between sets is the desired property for a similarity measure in this context.
  - **Why it matters** The AL pipeline depends critically on the reliability of the uncertainty measure. If the choice of CKA is not well justified, the validity of the entire augmentation approach is in question.
  - **Resolution test** Provide the comparison of similarity measures (Figure S1) and explain the rationale for selecting CKA. Clarify why minimal overlap between train/validation/test distributions is the appropriate criterion.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The claim that findings are "likely applicable beyond the realm of protein sets to wide varieties of LLMs and datasets."
  - **Evidence pointer** Conclusions section
  - **Concern** This generalization is asserted without supporting evidence or a clear argument for why the results should transfer to other domains. The study uses a single dataset (DIPS-Plus), a specific task (contact map prediction), and a limited set of pLMs. The conditions under which the findings might generalize are not discussed.
  - **Why it matters** Overclaiming generalizability can mislead readers. The scope of the conclusions should match the evidence.
  - **Resolution test** Either temper the claim to reflect the specific conditions studied, or provide a reasoned argument for generalizability based on the mechanisms observed.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Selecting disagreed-upon protein complexes"
  - **Evidence pointer** Table 2
  - **Issue** The text states that complexes are selected from the 20th percentile of CKA scores, but the number of complexes selected is only shown in Table 2, which is not available. The relationship between the percentile threshold and the number of selected complexes is unclear.
  - **Required correction** State the number of selected complexes for each ablation condition in the text, or explain how the percentile threshold translates to a fixed count.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Generating novel protein complexes by unmasking"
  - **Evidence pointer** Methods section
  - **Issue** The generation parameters (temperature 0.3, 3 tokens per step) are stated, but the rationale for these choices is not given. The number of generation steps and the total compute required are not specified.
  - **Required correction** Provide a brief justification for the chosen generation parameters and state the total number of generation steps or compute budget.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Results, "Effects of Dataset Ablation on Model Performance"
  - **Evidence pointer** Figure 4
  - **Issue** The text describes MCC differences between models and ablation types but does not report the actual values. The reader cannot assess the magnitude of the effects described.
  - **Required correction** Include key numerical values in the text or refer to a table with the full results.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, "Changes in Model Performance When Ablated Sets are Augmented With Generated Samples"
  - **Evidence pointer** Figure 11
  - **Issue** The claim of "consistent increase" is not supported by statistical analysis. It is unclear whether the five trials are independent and whether the observed increases are significant.
  - **Required correction** Report the variability across trials and perform a statistical test (e.g., paired t-test or Wilcoxon signed-rank test) to support the claim.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Measuring distances between protein complexes in latent space"
  - **Evidence pointer** Methods section
  - **Issue** The choice of the ESM model with 6 billion parameters for embedding is not justified. It is unclear why this specific model was chosen over other available embedding models.
  - **Required correction** Briefly explain the choice of embedding model and whether the results are sensitive to this choice.
- **Technical failings that need to be addressed before the case is established** The primary quantitative claims (order-of-magnitude dataset reduction, consistent augmentation benefit) are not supported by directly visible numerical evidence. The manuscript relies heavily on figures and tables that were not provided for review. Statistical significance and variability are not reported. The choice of CKA as the uncertainty measure requires clearer justification.
- **Assessment against Nature-style criteria**  
  *Originality*: The combination of dataset distribution control with generative augmentation for pLMs is a reasonable and somewhat novel angle, though the individual components (AL, data augmentation, pLMs) are established. The originality is moderate.  
  *Scientific importance*: The question of data efficiency in protein machine learning is important, and the findings could be useful for practitioners. However, the importance is somewhat limited by the narrow scope (one dataset, one task).  
  *Interdisciplinary readership*: The work sits at the intersection of machine learning, structural biology, and chemistry. The framing is accessible, but the results are likely to appeal mainly to a specialized audience.  
  *Technical soundness*: The experimental design is reasonable, but the lack of visible quantitative results and statistical analysis prevents a full assessment. The CKA choice needs stronger justification.  
  *Readability for nonspecialists*: The manuscript is generally well-written and the concepts are explained clearly. The abstract is accessible. However, some methodological details (e.g., CKA, pTM) may be challenging for readers outside the field.
- **Recommendation posture** Supportive if technical concerns are resolved. The topic is relevant and the approach is sensible, but the evidence as presented is insufficient to fully establish the main claims. The authors should provide the underlying quantitative data, statistical analyses, and clearer justifications for methodological choices.

## Risk / unsupported claims
- The claim of an order-of-magnitude reduction in dataset size with maintained performance is not supported by visible numerical evidence.
- The claim of a "small but consistent increase" in MCC upon augmentation is not supported by visible numerical evidence or statistical analysis.
- The claim that findings generalize beyond protein sets to "wide varieties of LLMs and datasets" is unsupported.
- The statement that CKA is the best measure of model disagreement is not fully justified without the comparison in Figure S1.
- The claim that ESM-3-generated proteins are biased toward the center of ESM-3's training distribution is plausible but not directly demonstrated with quantitative comparisons.