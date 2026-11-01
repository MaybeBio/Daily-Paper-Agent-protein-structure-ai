## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and references to supplementary material
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to evidence presented, and suitability for the stated journal context
- **Shared manuscript claim summary** The authors compare structure-based homology modeling (FoldX) and sequence-based machine learning (THPLM) for predicting protein folding stability across simulated mutational trajectories and natural sequence variants of four viral proteins. They report that both approaches exhibit inherent methodological limitations that distort stability predictions for sequences diverging from reference datasets, and argue that marginal stability should not be viewed as a fixed universal limit.
- **Visible evidence base** Main text figures 1-5, table 1, references to supplementary figures and tables (Figure S1, Table S1), and descriptions of methods and results
- **Missing materials affecting confidence** Supplementary material (Table S1 with accession codes, Figure S1) not provided; raw data and statistical analyses not provided; no quantitative error metrics or validation against experimental data shown in main text

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question regarding the reliability of computational protein stability prediction methods, particularly in the context of marginal stability and viral protein evolution. The comparison between structure-based and sequence-based approaches across simulated and natural sequence datasets is conceptually valuable. However, the evidence presented is largely qualitative and descriptive, with no quantitative benchmarking against experimental data, no statistical treatment of differences, and no clear validation of the central claim that methodological limitations fundamentally undermine current stability predictions. The conclusions extend beyond what the presented data can support.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying protein stability prediction tools; evolutionary biophysicists studying marginal stability and fitness landscapes; virologists interested in viral protein evolution and drug resistance; researchers using computational mutagenesis for protein engineering or variant interpretation in disease contexts.
- **Major strengths** The manuscript identifies a genuine and underappreciated problem: the potential for methodological artifacts to masquerade as biological signal in computational stability predictions. The choice of rapidly evolving viral proteins is well justified for probing the limits of prediction methods. The parallel analysis of simulated trajectories and natural sequences is a useful design. The discussion of template sensitivity in FoldX and training-space limitations in THLPM is thoughtful and well contextualized within the broader literature.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
  - R1-M5
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The observation that computational methods have limitations is not new, but the specific comparative framing across two methodological paradigms applied to viral proteins offers a somewhat fresh angle.
  - Scientific importance: Potentially high if the claims were rigorously supported, as the reliability of stability predictions underpins many downstream applications. However, the current evidence does not establish the importance of the specific findings.
  - Interdisciplinary readership: The topic bridges computational biology, evolutionary biophysics, and virology, which could attract broad interest. The writing is accessible to nonspecialists in each field.
  - Technical soundness: Insufficient. The analysis lacks quantitative rigor, validation against experimental benchmarks, and statistical treatment. Several claims are not supported by the presented evidence.
  - Readability for nonspecialists: Generally clear and well organized, though some methodological details are dense. The figures are informative but would benefit from quantitative annotations.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting hypothesis and preliminary observations, but the core claims require substantial additional analysis and validation before the case is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "protein folding stability landscapes predicted using current computational approaches are inherently shaped by technical limitations, leading to uncertainty in the evaluation of marginal stability and stability changes associated with biological processes."
- **Evidence pointer** Figures 1-5, Results section
- **Concern** The central claim of inherent methodological limitation is supported only by qualitative observations of trends in predicted stability values. No quantitative comparison is made between predicted and experimentally measured stability for any of the four viral proteins. Without benchmarking against experimental data, it is impossible to determine whether the observed patterns reflect genuine biological properties, methodological artifacts, or a combination of both. The claim of "inherent" limitation requires demonstration that the methods fail even in cases where ground truth is known.
- **Why it matters** The manuscript's primary contribution is the assertion that current methods are unreliable for assessing marginal stability. This claim cannot be evaluated without reference to experimental ground truth. If the methods perform adequately on experimentally characterized variants, the observed patterns in simulated trajectories may be biologically meaningful rather than artifactual.
- **Resolution test** Provide a quantitative comparison of predicted stability values against experimentally measured stability for a set of variants of at least one of the four viral proteins. Report correlation coefficients, mean absolute errors, and classification accuracy for stabilizing versus destabilizing mutations. If such data are unavailable, clearly state this limitation and temper the conclusions accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors state that "as random mutations accumulated, structure-based methods predicted a progressive decline in stability toward collapse, a pattern driven by the enforced conservation of protein structure."
- **Evidence pointer** Figures 1 and 2, Results section
- **Concern** The interpretation that the decline in predicted stability is "driven by the enforced conservation of protein structure" is presented as a conclusion but is not directly tested. The RMSD values shown in Figure 2 remain below 1.5 Å, which is consistent with the rigid-backbone assumption of FoldX, but this does not demonstrate that the decline is caused by this assumption. A control experiment using a method that allows backbone flexibility, or an analysis correlating predicted stability changes with the structural context of mutations, would be needed to support this causal claim.
- **Why it matters** The manuscript attributes observed patterns to specific methodological mechanisms. If these attributions are incorrect, the conclusions about the limitations of each approach would be misdirected, potentially leading to incorrect recommendations for method selection or development.
- **Resolution test** Perform a control analysis using a flexible-backbone method (e.g., Rosetta with backbone relaxation) on a subset of the simulated trajectories and compare the predicted stability trends with those from FoldX. Alternatively, analyze whether the magnitude of predicted destabilization correlates with the structural location of mutations (e.g., core versus surface) in a way that would be expected under the rigid-backbone hypothesis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that "sequence-based methods failed as sequences moved into uncharted regions of parameter space" and that "the performance of the method appears to be constrained more by the characteristics of the training data than by the level of sequence divergence itself."
- **Evidence pointer** Figures 4 and 5, Results section
- **Concern** The claim that THLPM "failed" is not supported by any quantitative criterion for failure. The predicted stability values for simulated sequences plateau after an initial decline, but this could reflect genuine biophysical properties of highly mutated sequences rather than method failure. The assertion that training data characteristics are the limiting factor is speculative, as no analysis of the training data composition or its relationship to the viral protein families is presented. The pTM scores are used as a proxy for prediction confidence, but the relationship between pTM and the reliability of stability predictions is not established.
- **Why it matters** The manuscript's comparison between methods is only meaningful if the criteria for success or failure are clearly defined and applied consistently. Without such criteria, the reader cannot assess whether the observed differences between methods are substantive or within expected variation.
- **Resolution test** Define explicit criteria for prediction success (e.g., agreement with experimental data, consistency across related sequences, or convergence of predicted values). Apply these criteria to both methods across all four proteins. Provide an analysis of the training data composition for THLPM, including sequence identity between training sequences and the viral proteins studied, to support claims about training-data limitations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors conclude that "marginal stability should not be regarded as a fixed universal limit, such as 7.4 kcal/mol. Rather, its range may vary among protein families and according to the assumptions underlying the prediction methodologies employed."
- **Evidence pointer** Discussion section, Table 1
- **Concern** This conclusion conflates two distinct issues. The observation that different prediction methods yield different stability ranges for the same proteins is a statement about method agreement, not about the true biological range of marginal stability. The authors do not provide any evidence that the true marginal stability range varies among protein families, as they have no experimental measurements of stability for the proteins studied. The discussion of the theoretical upper bound of 7.4 kcal/mol is presented without critical evaluation of the assumptions underlying that theory.
- **Why it matters** The conclusion as stated could be misinterpreted as a biological finding when it is actually a methodological observation. This distinction is critical for readers who may use this manuscript to inform their understanding of protein stability or to guide experimental design.
- **Resolution test** Separate the methodological observation (methods disagree) from the biological claim (marginal stability varies among families). For the biological claim, provide experimental stability measurements for at least one protein family showing variation in stability ranges, or clearly label this as a hypothesis requiring experimental validation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scope justification
- **Claim pointer** The authors state that "considering that rapidly evolving viral proteins provide a useful system for understanding thermodynamic tolerance under the competing demands of structural integrity and adaptive flexibility, we compared predicted protein stability from both approaches."
- **Evidence pointer** Introduction, Materials and methods
- **Concern** The choice of four viral proteins is justified by their biomedical interest and rapid evolution, but no explicit criteria are given for why these specific proteins were selected or whether they are representative of viral proteins more broadly. The number of natural sequences retrieved (100 per protein) and the selection criteria for these sequences are not described in sufficient detail to assess potential sampling biases.
- **Why it matters** The generalizability of the findings depends on the representativeness of the protein set and sequence sampling. If the selected proteins or sequences are not representative, the conclusions may not extend beyond the specific cases studied.
- **Resolution test** Provide explicit inclusion criteria for protein selection and sequence retrieval. Describe the sequence diversity of the retrieved sets (e.g., pairwise identity distributions) and justify the sample size. Discuss how the four proteins differ in structural and functional properties and how this might affect the generalizability of the findings.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract states the stability range as "approximately 5-15 kcal/mol" but the Discussion cites a theoretical upper bound of 7.4 kcal/mol. The relationship between these two values is not explained.
- **Required correction** Clarify whether the 5-15 kcal/mol range is an empirical observation, a theoretical prediction, or a consensus estimate, and explain how it relates to the 7.4 kcal/mol theoretical bound.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods
- **Evidence pointer** Materials and methods section
- **Issue** The description of the mutational simulation procedure is incomplete. The statement "we simulated 50 independent mutational trajectories where each residue of the sequence was replaced by a random amino acid and iterating it until every position was mutated at least once" does not specify whether mutations were introduced sequentially or simultaneously, whether stop codons were excluded, or how many total mutations were accumulated per trajectory.
- **Required correction** Provide a complete description of the simulation protocol, including the number of mutations per step, the total number of mutations per trajectory, and any filters applied to exclude invalid sequences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Figures 1-5
- **Issue** The figures show trends and distributions but no statistical analyses. It is unclear whether the observed differences between methods, or between simulated and real sequences, are statistically significant.
- **Required correction** Add appropriate statistical tests (e.g., permutation tests, confidence intervals) to support claims of differences between conditions or methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, paragraph on "Prediction of protein folding stability using sequence-based ML approaches"
- **Issue** The discussion of the "random neighbor score" from reference [64] is presented as if it directly applies to the THLPM framework, but THLPM and ESM-2 are different models. The relevance of this metric to the specific embeddings used by THLPM is not established.
- **Required correction** Clarify whether the random neighbor score analysis was performed on THLPM embeddings or on ESM-2 embeddings, and discuss the implications for interpreting the pTM scores in this study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section, "Marginal stability as a consequence of evolutionary adaptation and biophysical constraints"
- **Issue** The discussion of the two theories of marginal stability (mutation-selection-drift versus universal biophysical constraint) is presented in a binary fashion, but the authors do not discuss how their results might discriminate between these theories or whether the theories make distinct predictions that could be tested with their data.
- **Required correction** Add a brief discussion of whether the observed patterns in predicted stability are consistent with one theory over the other, or explain why the current data cannot discriminate between them.

## Risk / unsupported claims
- The claim that "protein folding stability landscapes predicted using current computational approaches are inherently shaped by technical limitations" is not supported by quantitative evidence, as no comparison to experimental stability data is provided.
- The assertion that "sequence-based methods failed" for divergent sequences is not supported by any defined failure criterion.
- The conclusion that "marginal stability should not be regarded as a fixed universal limit" conflates methodological disagreement with biological evidence and is not supported by experimental measurements.
- The attribution of declining FoldX-predicted stability to "enforced conservation of protein structure" is presented as causal without a control experiment.
- The claim that THLPM performance is "constrained more by the characteristics of the training data than by the level of sequence divergence itself" is speculative, as no training data analysis is presented.
- The relevance of the "random neighbor score" from reference [64] to THLPM embeddings is asserted without demonstration.
- The representativeness of the four selected viral proteins and the retrieved natural sequence sets is not established, limiting the generalizability of the findings.