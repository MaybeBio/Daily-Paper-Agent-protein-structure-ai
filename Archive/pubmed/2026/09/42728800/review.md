## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided. Figures, tables, and supplementary materials referenced but not fully available.
- **Assessment boundary** Scientific and technical evaluation of the proposed UFold-X model, its experimental design, reported results, and claims. No assessment of code correctness or web server functionality beyond what is described.
- **Shared manuscript claim summary** The authors present UFold-X, a dual-branch deep learning framework combining convolutional and Mamba-based (VSSM) encoders with a dynamic gating mechanism for long-range RNA secondary structure prediction. They claim state-of-the-art performance among deep learning methods on long RNAs, competitive performance with classical approaches, robust generalization under cross-clan evaluation, biological consistency via a SHAPE-based reactivity variant (UFold-X-R) and a new metric (HRPS), and high computational efficiency.
- **Visible evidence base** Text descriptions of benchmark datasets (RNAstralign, ArchiveII, RCSB, BGSU, Rfam), reported F1 scores, precision, recall, HRPS values, inference times, and statistical test results. References to Figures 1–9 and Supplementary Figures/Tables, none of which were provided in full.
- **Missing materials affecting confidence** All figures, tables (including Table 1 and 2), and supplementary materials are referenced but not included. This prevents verification of numerical results, visual comparisons, ablation studies, and detailed statistical outputs. The exact model architecture hyperparameters, training details, and data preprocessing code are not fully described.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in RNA bioinformatics: accurate secondary structure prediction for long sequences. The proposed architecture is a reasonable extension of prior work (UFold) with a clear motivation for incorporating long-range modeling via Mamba-based modules. The evaluation strategy, particularly the introduction of cross-clan benchmarks, is thoughtful and addresses a known limitation in the field. However, the manuscript as presented has several significant issues. The most critical is the lack of a clear, quantitative comparison of the proposed dynamic gating mechanism against simpler alternatives (e.g., fixed weighting, learned scalar weighting) and against the individual branches alone. The claim of "state-of-the-art among deep learning methods" is made but the comparison set is limited and the significance of improvements is not always established. The HRPS metric is introduced but its validation and the interpretation of its components require more rigorous justification. The biological consistency analysis relies on a model (UFold-X-R) trained on short sequences and applied to long ones, and the validity of this transfer is not thoroughly discussed. The computational efficiency claim is based on a single benchmark and lacks comparison with other efficient methods. Overall, the work has potential but the current evidence does not fully establish the superiority or novelty of the proposed approach over existing methods, especially given the missing figures and tables.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on RNA structure prediction, particularly those interested in deep learning approaches for long non-coding RNAs, viral genomes, and ribosomal RNAs. The work may also be of interest to researchers developing Mamba-based architectures for biological sequence analysis, as it demonstrates an application of this architecture to a structured prediction problem. The web server and open-source code could be useful for practitioners needing a fast and accessible prediction tool.
- **Major strengths**
  1. The problem addressed is important and the focus on long-range interactions is well-motivated.
  2. The dual-branch architecture with dynamic gating is a sensible and potentially effective design.
  3. The introduction of cross-clan evaluation is a significant methodological contribution, addressing a critical gap in the field's evaluation practices.
  4. The development of a reactivity prediction variant and the HRPS metric attempts to bridge structural prediction with biochemical interpretability.
  5. The reported computational efficiency is a practical advantage.
- **Major Concerns**
  - **R1-M1**
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The claim that the dynamic gating mechanism (Approach I) is superior to Approach II and to static fusion methods is not sufficiently supported.
    - **Evidence pointer** Section "Dynamic gating mechanism for range-aware feature fusion", Results section (referenced but not fully provided), Supplementary Fig. S3.
    - **Concern** The manuscript states that "Empirical results show that Approach I generally yields better performance on test sets" but provides no quantitative data in the text. The comparison is relegated to a supplementary figure. More importantly, there is no ablation study comparing the full model against (a) the convolutional branch alone, (b) the VSSM branch alone, and (c) a version with fixed (non-dynamic) fusion weights. Without these, it is impossible to determine whether the dynamic gating mechanism is the source of the reported improvements, or whether the improvements come simply from having a larger, more complex model.
    - **Why it matters** The dynamic gating mechanism is a core novelty of the proposed architecture. If its contribution is not rigorously demonstrated, the added complexity of the model cannot be justified. The claim of a "dynamic" and "adaptive" mechanism requires evidence that it outperforms simpler, static alternatives.
    - **Resolution test** Provide a full ablation study in the main text or a clearly referenced supplementary table, showing F1 scores (and other metrics) for: (1) UFold-X with Approach I gating, (2) UFold-X with Approach II gating, (3) UFold-X with fixed weights (e.g., α=β=0.5), (4) convolutional branch only, (5) VSSM branch only. Statistical significance tests should be performed for the key comparisons.
  - **R1-M2**
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The claim that UFold-X achieves "state-of-the-art" performance among deep learning methods and is "comparable" to classical approaches.
    - **Evidence pointer** Results section, Figures 3–5, Tables 1–2 (all referenced but not provided).
    - **Concern** The comparison set is limited to a few methods (RNAstructure, Mfold, LinearFold, EternaFold, CONTRAfold, SPOT-RNA, e2efold, UFold). Several recent deep learning methods for RNA secondary structure prediction (e.g., E2Efold-2, RNAformer, MXfold2 are mentioned but not consistently included in all benchmarks) are missing. The claim of "state-of-the-art" requires a more comprehensive and up-to-date comparison. Furthermore, the statistical significance of the improvements over the second-best method is only reported for some comparisons (e.g., cross-clan), and it is unclear if the improvements on other benchmarks are significant.
    - **Why it matters** The primary contribution of the paper is a new model with claimed superior performance. Without a comprehensive and statistically rigorous comparison, the central claim of the paper is not established.
    - **Resolution test** Expand the baseline set to include all recently published deep learning methods with available code. Perform statistical significance tests (e.g., paired bootstrap or Wilcoxon signed-rank test) for all key comparisons across all benchmarks and report the results clearly.
  - **R1-M3**
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Scientific importance
    - **Claim pointer** The claim that the HRPS metric provides a "biologically meaningful" and "quantitatively balanced" evaluation that is superior to using F1 score alone.
    - **Evidence pointer** Section "Hybrid Reactivity-Pairing Score", Results section, Figure 5C–D, Table 1.
    - **Concern** The HRPS is a weighted combination of F1 and Spearman correlation. The weights (α=0.4, β=0.3, γ=0.1, δ=0.2) appear arbitrary and are not justified. The metric's behavior is not analyzed: how sensitive is the ranking of methods to the choice of weights? Is the Spearman correlation term measuring something that is not already captured by F1? The validation of UFold-X-R is limited to a short-sequence dataset, and its application to long sequences is based on the assumption that the learned reactivity patterns generalize, which is not directly tested. The claim that HRPS is "biologically meaningful" requires a demonstration that it correlates with some independent biological readout or that it provides information beyond what F1 provides.
    - **Why it matters** Introducing a new metric is a significant contribution only if it is well-justified, validated, and shown to provide unique and useful information. If the metric is arbitrary, its use in the paper's main conclusions weakens the overall argument.
    - **Resolution test** Provide a sensitivity analysis of HRPS to its weights. Show that the ranking of methods is robust to reasonable variations in the weights. Validate UFold-X-R on a held-out long RNA dataset with experimental reactivity data, if available. Justify the choice of weights based on a principled argument or empirical optimization.
  - **R1-M4**
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness
    - **Claim pointer** The claim that the cross-clan benchmark is a "stringent" and "homology-independent" evaluation setting.
    - **Evidence pointer** Section "Redundancy reduction and data leakage prevention", Section "Cross-clan evaluation".
    - **Concern** The construction of the cross-clan benchmark is not fully described. The manuscript states that 227 sequences from 12 families were obtained, and 66 sequences from 11 families were retained for testing. The criteria for selecting these specific families and sequences are not given. The use of computationally predicted structures (from CONTRAfold) as training labels for the augmented data is a potential source of bias, as the model is trained on the same type of predictions it is being evaluated against. The manuscript does not discuss the potential impact of this circularity.
    - **Why it matters** The validity of the cross-clan benchmark is central to the paper's claim of robust generalization. If the benchmark construction is flawed or biased, the conclusions drawn from it are weakened.
    - **Resolution test** Provide a detailed description of the benchmark construction, including the list of families, the number of sequences per family, and the criteria for inclusion. Discuss the potential bias introduced by using computationally predicted labels for training and how this might affect the results. Consider evaluating on a subset of the test set with experimentally validated structures, if available.
- **Minor Comments**
  - **R1-m1**
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Introduction and Methods
    - **Evidence pointer** Section "Introduction", Section "Overview of the UFold-X framework"
    - **Issue** The manuscript assumes significant familiarity with both RNA structure prediction and deep learning architectures. Terms like "Mamba," "VSSM," "state space model," and "selective scanning" are introduced without sufficient background for a general reader.
    - **Required correction** Add a brief, accessible explanation of Mamba/SSM concepts and why they are advantageous for long-range dependency modeling in the context of RNA. Consider a short paragraph in the Introduction or a "Background" subsection.
  - **R1-m2**
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methods, "Training" section
    - **Evidence pointer** Section "Training" (not fully provided)
    - **Issue** The training details are incomplete. The manuscript mentions SGD and ReLU but does not specify learning rate, batch size, number of epochs, learning rate schedule, weight decay, or the hardware used. The loss function is described as BCE, but the handling of class imbalance (most base pairs are unpaired) is not discussed.
    - **Required correction** Provide a complete description of the training hyperparameters and any techniques used to address class imbalance (e.g., weighted loss, focal loss).
  - **R1-m3**
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methods, "Data preprocessing" section
    - **Evidence pointer** Section "Data preprocessing"
    - **Issue** The manuscript states that the model supports variable-length RNA sequences "without the need for input padding." This is a strong claim that needs clarification. How is the variable-length input handled in the convolutional and VSSM branches, which typically require fixed-size inputs? Is there a maximum length? How are the outputs for different lengths handled?
    - **Required correction** Clarify the mechanism for handling variable-length inputs. If padding is used internally, state this. If the model is fully convolutional and can handle arbitrary sizes, explain how the VSSM component, which may have learned positional parameters, adapts.
  - **R1-m4**
    - **Severity** Minor
    - **Axis** Scientific importance
    - **Affected element** Results, "Biological correlation analysis" section
    - **Evidence pointer** Section "Biological correlation analysis", Table 1
    - **Issue** The manuscript reports that UFold-X and UFold achieve identical Spearman correlation (0.293) with pseudo-reactivity. This is a suspicious result that suggests the reactivity prediction is not sensitive to the structural differences between the two models. The authors do not comment on this.
    - **Required correction** Discuss why the Spearman correlation is identical for both models. If the reactivity prediction is dominated by sequence features rather than predicted structure, this should be acknowledged and its implications for the HRPS metric discussed.
  - **R1-m5**
    - **Severity** Minor
    - **Axis** Interdisciplinary readership
    - **Affected element** Discussion
    - **Evidence pointer** Section "Discussion"
    - **Issue** The discussion of limitations is brief and does not address the potential for overfitting to the training distribution, the sensitivity of the results to the choice of training data, or the performance on pseudoknotted structures, which are known to be challenging.
    - **Required correction** Expand the discussion to include these points. Specifically, address the model's performance on pseudoknotted structures, as the manuscript mentions pseudoknots in the introduction but does not provide a detailed analysis of the model's ability to predict them.
- **Technical failings that need to be addressed before the case is established**
  1. Lack of a complete ablation study for the dynamic gating mechanism (R1-M1).
  2. Incomplete and potentially outdated baseline comparison (R1-M2).
  3. Unjustified and unvalidated new metric (HRPS) (R1-M3).
  4. Potential bias in the cross-clan benchmark construction (R1-M4).
  5. Incomplete training details and unclear handling of variable-length inputs (R1-m2, R1-m3).
- **Assessment against Nature-style criteria**
  - **Originality** The combination of a convolutional encoder with a Mamba-based VSSM in a dual-branch architecture for RNA secondary structure prediction is a novel application of recent architectural innovations. The introduction of the cross-clan benchmark is a valuable methodological contribution. However, the core idea of combining local and global models is not entirely new, and the novelty is primarily in the specific implementation.
  - **Scientific importance** The problem of long-range RNA structure prediction is of high importance. The paper addresses a real limitation of existing deep learning methods. However, the importance of the contribution is diminished by the lack of rigorous validation of the key components (gating, HRPS) and the limited baseline comparison. The cross-clan benchmark, if properly constructed, could be a significant resource for the community.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The methods section is technical and may be challenging for experimental biologists. The potential biological applications (e.g., lncRNA, viral genomes) are mentioned but not deeply explored. The paper is unlikely to appeal to a broad interdisciplinary audience in its current form.
  - **Technical soundness** The technical soundness is currently not fully established. The main issues are the missing ablation study, the potential bias in the benchmark, and the lack of detail in the training and architecture description. The reported results are promising but require more rigorous validation.
  - **Readability for nonspecialists** The abstract is clear, but the main text is dense and assumes significant background knowledge. The introduction of Mamba/SSM concepts is not accessible to a general reader. The paper would benefit from a clearer explanation of the core ideas and their significance.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem and presents a plausible and potentially effective solution. However, the current evidence is insufficient to fully support the central claims. The authors must provide a complete ablation study, a more comprehensive and up-to-date baseline comparison, a rigorous justification and validation of the HRPS metric, and a detailed description of the benchmark construction and training procedures. If these concerns are adequately addressed, the paper could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that UFold-X is "state-of-the-art" among deep learning methods is not fully supported due to the limited baseline set and lack of statistical significance testing for all comparisons.
- The claim that the dynamic gating mechanism is superior to static alternatives is unsupported without a full ablation study.
- The claim that the HRPS metric is "biologically meaningful" is not validated.
- The claim that the cross-clan benchmark is "homology-independent" is not fully supported due to the potential for remote homology and the use of computationally predicted labels.
- The claim of "excellent computational efficiency" is based on a single benchmark and lacks comparison with other efficient methods.
- The claim that the model handles variable-length sequences "without the need for input padding" is unclear and requires clarification.
- The reported Spearman correlation of 0.89 for UFold-X-R on the held-out test set is presented without details on the test set size, composition, or the variance of this estimate.