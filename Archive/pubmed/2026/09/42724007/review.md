## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** Scientific claims, methodology, experimental design, data analysis, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors propose PromptGPCR, an AlphaFold-based inference framework that uses biologically informed protein sequence prompts (mini-Gs for active states, T4 lysozyme for inactive states) to guide AlphaFold-Multimer and AlphaFold 3 toward predicting state-specific GPCR structures. They claim that PromptGPCR outperforms baseline methods in backbone structure prediction and molecular docking success rates.
- **Visible evidence base** Full manuscript text, figures referenced in text (Fig. 1, 2, 3, 4, 5, A2, A3), tables referenced in text, benchmark dataset description, unseen dataset description, docking test set description
- **Missing materials affecting confidence** The supplementary materials are referenced but not provided. The GitHub repository is mentioned but its contents are not visible. Individual data points for figures are not provided. Statistical significance measures (e.g., p-values, confidence intervals) are absent from all comparisons.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to a well-recognized problem in structural biology: predicting multiple conformational states of GPCRs. The idea of using biologically informed sequence prompts to guide AlphaFold toward specific states is creative and builds on plausible reasoning about the model's training data. However, the manuscript suffers from several significant technical weaknesses that undermine the strength of the claims. The most critical issues are the lack of rigorous statistical evaluation, the absence of proper controls for the inactive-state prompt, the limited scope of the docking validation, and the failure to address the fundamental question of whether the method actually produces state-specific conformations or merely improves overall prediction quality. The conclusions are not fully supported by the evidence presented.
- **Who would be interested in the results, and why** Researchers in computational structural biology, GPCR biology, and structure-based drug design would be interested. The method addresses a practical need for generating state-specific GPCR models, which is relevant for understanding receptor function and for drug discovery efforts targeting specific conformational states.
- **Major strengths** 1. The core idea of using biologically informed sequence prompts to guide AlphaFold toward specific conformational states is novel and well-motivated by structural biology knowledge. 2. The study evaluates the method on both a benchmark dataset and an unseen dataset, providing some assessment of generalizability. 3. The inclusion of molecular docking experiments attempts to connect structure prediction to a downstream application.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental design and controls
    - **Claim pointer** The authors claim that the T4 lysozyme prompt guides AlphaFold toward predicting inactive-state GPCR structures.
    - **Evidence pointer** Section "Multi-state structure prediction via prompts", Figure A3
    - **Concern** The negative control experiment for the inactive-state prompt (T4 lysozyme) uses dihydrofolate reductase (DHFR) as a control sequence. The results show that DHFR produces nearly identical prediction accuracy (average GDT-TS > 90) to the T4 lysozyme prompt. The authors acknowledge this but dismiss it as not indicating "complete nonspecificity." This result fundamentally undermines the claim that the T4 lysozyme is specifically guiding the model toward inactive-state conformations. If a completely unrelated protein sequence produces the same effect, the observed improvement may be an artifact of providing any additional sequence to the model, not a state-specific effect.
    - **Why it matters** The core claim of the method is that specific prompts guide the model toward specific states. If the inactive-state prompt is not specific, then the method's mechanism is not as described, and the results for inactive-state prediction may be coincidental or due to other factors. This weakens the entire framework's conceptual foundation.
    - **Resolution test** The authors must provide a rigorous set of control experiments. This should include: (1) multiple unrelated protein sequences of varying lengths as prompts for both active and inactive states; (2) scrambled or randomized versions of the mini-Gs and T4 lysozyme sequences; (3) a demonstration that the prompt's effect is state-specific, e.g., showing that the T4 lysozyme prompt does not improve active-state prediction and the mini-Gs prompt does not improve inactive-state prediction. The authors should also quantify the effect size and show that the specific prompts produce statistically significantly better results than controls.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Statistical rigor and reproducibility
    - **Claim pointer** The authors claim that PromptGPCR "outperforms the baselines" and "can accurately predict the active and inactive states."
    - **Evidence pointer** Section "Multi-state structure prediction via prompts", Figures 2, 3
    - **Concern** All performance comparisons are presented as mean GDT-TS values or as counts of targets where one method outperforms another. No measures of variance (standard deviation, standard error), confidence intervals, or statistical significance tests (e.g., paired t-tests, Wilcoxon signed-rank tests) are provided. Without these, it is impossible to determine whether the observed differences are meaningful or could be due to random variation. The claim that one method "outperforms" another is not statistically substantiated.
    - **Why it matters** The primary claims of the paper rest on comparative performance. Without statistical validation, the conclusions are not reproducible or reliable. This is a fundamental requirement for any computational method paper.
    - **Resolution test** The authors must provide statistical analysis for all key comparisons. For per-target comparisons (e.g., Figure 2D, 2E, 3A, 3B), a paired statistical test should be performed. For aggregate comparisons (e.g., Figure 2A, 2B, 3C), the mean, standard deviation, and sample size should be reported, and appropriate tests should be used. The authors should also report effect sizes.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Claim-evidence alignment
    - **Claim pointer** The authors claim that PromptGPCR predicts "state-specific" conformations and that the predictions show "an evident tendency to the specific state."
    - **Evidence pointer** Section "Multi-state structure prediction via prompts", Figure A2
    - **Concern** The manuscript does not provide a direct, quantitative demonstration that the predicted structures are state-specific. The only evidence is a qualitative visual comparison in Figure A2 for two GPCRs. The authors do not report any metric that directly measures state-specificity, such as: (1) the RMSD of the predicted active-state structure to the experimental active-state structure versus the experimental inactive-state structure; (2) the distance between the predicted structure and the two reference states in a conformational landscape; (3) the position of key structural features (e.g., the ionic lock, TM6 outward movement) relative to known active and inactive states. The GDT-TS metric measures overall structural similarity but does not distinguish between states. A high GDT-TS to an active-state structure could simply mean the prediction is generally good, not that it is specifically in the active conformation.
    - **Why it matters** The entire premise of the method is to predict multi-state structures. If the method only improves overall prediction quality without actually producing state-specific conformations, it does not solve the stated problem. The claim of state-specificity is central and must be rigorously demonstrated.
    - **Resolution test** The authors must provide a quantitative analysis of state-specificity. This should include: (1) for GPCRs with both active and inactive experimental structures, calculate the RMSD of the prompt-guided prediction to both states and show that the active-state prompt produces structures closer to the active state and vice versa; (2) report state-specific structural metrics (e.g., TM6 tilt angle, distance between key residues in the DRY motif, RMSD of the ligand-binding pocket) for the predicted structures and compare them to the experimental states; (3) perform a principal component analysis or similar dimensionality reduction on the ensemble of predicted and experimental structures to show that the prompt-guided predictions cluster with the intended state.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scope and generalizability of claims
    - **Claim pointer** The authors claim that PromptGPCR "exhibits higher success rates in molecular docking than baselines" and that this "indicates that the predictions of PromptGPCR may have a certain degree of usability in downstream application scenarios."
    - **Evidence pointer** Section "Protein–ligand docking", Section "Application of high-precision multi-state GPCR conformations"
    - **Concern** The molecular docking validation is limited in scope and methodology. It uses only 9 GPCRs from the unseen dataset, all of which are active-state structures with small-molecule ligands. The docking method (CSAlign-Dock) is a guided pose-recovery test that requires the reference ligand from the experimental structure as input. The authors explicitly state that this "differs from scenarios such as blind docking" and "does not support the conclusion that PromptGPCR can achieve excellent performance in virtual screening scenarios." This significantly limits the conclusions that can be drawn about the method's utility in drug discovery. The sample size is small, and no statistical analysis is provided for the docking results.
    - **Why it matters** The docking experiments are presented as evidence of downstream applicability, but the experimental design is too limited to support broad claims about usability in drug design. The authors' own caveat about the limitations of the docking setup is appropriate but should be more prominently reflected in the conclusions.
    - **Resolution test** The authors should either: (1) expand the docking validation to include a larger and more diverse set of GPCRs, including inactive-state structures and antagonists, and use a blind docking protocol; or (2) significantly temper the claims about downstream applicability and clearly state that the docking results are preliminary and only demonstrate pose-recovery capability, not virtual screening performance.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Abstract
    - **Evidence pointer** Abstract
    - **Issue** The abstract states that PromptGPCR "can accurately predict active and inactive structures compared to baselines." This phrasing is ambiguous. It is unclear whether the method is being compared to baselines or whether the prediction accuracy is being evaluated in comparison to experimental structures.
    - **Required correction** Rephrase to clarify: "PromptGPCR predicts active and inactive structures with higher accuracy than baseline methods, as measured by GDT-TS."

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Figures 2, 3, 4
    - **Evidence pointer** Figures 2, 3, 4
    - **Issue** The figures do not show individual data points or error bars. For box plots or bar charts, the number of data points (n) should be clearly stated in the figure legend. The y-axis labels for some panels are not fully descriptive (e.g., "GDT-TS" should be defined in the legend).
    - **Required correction** Add individual data points or error bars to all plots. Clearly state the sample size (n) for each group in the figure legend. Define all abbreviations in the figure legend.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Methodology
    - **Affected element** Section "Data processing"
    - **Evidence pointer** Section "Data processing"
    - **Issue** The authors state that they excluded "all intermediate states" from the benchmark dataset but do not provide a clear definition or criterion for what constitutes an intermediate state. This is a critical detail for reproducibility.
    - **Required correction** Provide a clear, operational definition of "intermediate state" (e.g., based on specific structural features, ligand type, or annotation in GPCRdb). Alternatively, state the criteria used for classification.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Section "Overview of PromptGPCR"
    - **Evidence pointer** Section "Overview of PromptGPCR"
    - **Issue** The description of the AlphaFold 3 inference setup is incomplete. The authors state they used "5 random seeds" and generated "5 structures per seed," but they do not specify which random seeds were used. This is essential for reproducibility.
    - **Required correction** Either specify the random seeds used or state that the seeds were randomly selected and provide the code/script that generates them.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section "Knowledge-guided biological prompts"
    - **Evidence pointer** Section "Knowledge-guided biological prompts"
    - **Issue** The analogy between AlphaFold and large language models (LLMs) is drawn extensively but is not rigorously justified. The authors state that AlphaFold "can be regarded as language models trained on biological data," but this is a loose analogy. The mechanisms of prompt engineering in LLMs (e.g., influencing token probability distributions) are not directly analogous to providing a separate protein sequence to a structure prediction model.
    - **Required correction** Either provide a more rigorous justification for the analogy, or reframe the motivation in terms of AlphaFold's training data and architecture without relying on the LLM analogy. The core idea (providing a binding partner to bias the prediction) is already well-motivated by structural biology.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of proper controls for inactive-state prompt), R1-M2 (lack of statistical rigor), R1-M3 (lack of quantitative demonstration of state-specificity)

- **Assessment against Nature-style criteria** 
  - **Originality**: The concept of using biologically informed sequence prompts to guide AlphaFold toward specific conformational states is moderately original. While the idea of providing binding partners to bias predictions is not entirely new, the systematic application to GPCR multi-state prediction and the specific choice of prompts (mini-Gs, T4 lysozyme) based on structural biology knowledge is a novel contribution.
  - **Scientific importance**: The problem of predicting GPCR multi-state structures is of high importance for structural biology and drug discovery. If the method were rigorously validated, it would be a valuable tool. However, the current evidence is insufficient to establish the method's effectiveness, particularly for state-specific prediction.
  - **Interdisciplinary readership**: The topic is of interest to computational biologists, structural biologists, and pharmacologists. The manuscript is written in a way that is accessible to these audiences, though the LLM analogy may be confusing to some.
  - **Technical soundness**: The technical soundness is currently weak. The major concerns (lack of proper controls, lack of statistical analysis, lack of state-specificity validation) are fundamental flaws that prevent the paper from being considered technically sound.
  - **Readability for nonspecialists**: The manuscript is generally well-written and clear, with a logical structure. The introduction and motivation are well-articulated. However, the technical details of the method and the limitations of the evaluation could be more clearly explained.

- **Recommendation posture** Currently not established from the provided evidence. The core claims of the method are not adequately supported due to critical flaws in experimental design (lack of proper controls for the inactive-state prompt), lack of statistical rigor, and failure to quantitatively demonstrate state-specificity. The manuscript requires major revisions and additional experiments before it can be considered for publication.