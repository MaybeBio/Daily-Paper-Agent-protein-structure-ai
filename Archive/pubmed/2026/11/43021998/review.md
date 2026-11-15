## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, data availability, author contributions, conflict of interest, generative AI statement, publisher's note, supplementary material link, acknowledgments)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality of the manuscript as provided. No external data or code were accessed.
- **Shared manuscript claim summary** The authors evaluate how the choice of structural scaffold (experimental vs. AlphaFold 3 predicted) and conformational sampling affect the performance of four structure-based ΔΔG prediction tools (RDE-PPI, Prompt-DDG, BA-DDG, H3-DDG) for prioritizing TCR–pMHC CDR mutations. They report that experimental structures yield the best performance, that Prompt-DDG and RDE-PPI are relatively robust to AF3 wild-type scaffolds, that AF3-mutant scaffolds with inversion–negation scoring improve BA-DDG and H3-DDG, and that AF3-mutant scaffolds give the highest mean top-10 recovery among AF3-based inputs across four templates.
- **Visible evidence base** Main text figures (Figures 1, 2, 3), main text tables (Tables 1, 3, 4), and references to supplementary tables and figures (Supplementary Tables S1–S22, Supplementary Figures S1, S2). Supplementary material content was not provided.
- **Missing materials affecting confidence** Supplementary material (Tables S1–S22, Figures S1, S2) is referenced extensively but not provided. This includes detailed per-template results, bootstrap confidence intervals, saturation analysis details, and sensitivity analyses. The GitHub repository link is provided but was not accessed. The exact version of AlphaFold 3 and its configuration parameters are not fully specified.

## Reviewer
- **Overall assessment** This manuscript addresses a practically important question in computational TCR engineering: how reliable are ΔΔG-based mutation prioritization tools when experimental structures are unavailable and AlphaFold 3 predictions must be used instead. The study design is thoughtful, combining a curated experimental dataset (ATLAS) with multiple structural scaffolds and four diverse prediction tools. The finding that experimental structures remain superior, and that model-specific responses to scaffold choice vary, is useful and actionable. However, the manuscript has several significant weaknesses. The statistical analysis is underpowered for the main claims, particularly the candidate-prioritization analysis which relies on only four templates. The structural error-feature analysis is largely negative, and the authors appropriately refrain from over-interpreting it, but this limits its contribution. The discussion of why AF3-mutant scaffolds help some models but not others is speculative. The manuscript would benefit from a clearer articulation of the practical decision framework it aims to provide, and from a more rigorous treatment of uncertainty in the headline results. The writing is generally clear, though some sections are dense and the use of "Equation 2.5" as a section reference is confusing.
- **Who would be interested in the results, and why** Researchers in computational protein design, specifically those working on TCR and antibody engineering, will find this study directly relevant. Practitioners who use AlphaFold 3 for structure prediction and ΔΔG tools for variant prioritization will benefit from the practical guidance on scaffold selection. The study also contributes to the broader literature on the reliability of machine learning-based affinity prediction when input structures are predicted rather than experimental. The negative results on structural correlates of error are of interest to method developers seeking to build confidence metrics for predicted structures.
- **Major strengths**
  - The study addresses a timely and practically important question with a well-designed evaluation framework.
  - The use of a curated experimental dataset (ATLAS) with measured ΔΔG values provides a solid benchmark.
  - The inclusion of multiple prediction tools with different architectures (flow-based, inverse-folding, prompt-based) allows for a comparative analysis of model-specific behaviors.
  - The distinction between global correlation metrics and top-K recovery metrics is appropriate and highlights the different practical goals of ΔΔG prediction.
  - The authors are appropriately cautious in interpreting negative results and in acknowledging the limitations of their analysis.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and generalizability of candidate-prioritization claims
  - **Claim pointer** The claim that "Across four templates, AF3-mutant scaffolds gave the highest mean top-10 recovery among the AF3-based inputs for all four predictors" (Abstract) and the related conclusion that AF3-mutant scaffolds should be used for top-ranked CDR candidate recovery when experimental structures are unavailable.
  - **Evidence pointer** Section "Candidate-prioritization performance depends on structure input, model, and template" (Results), Table 3, Supplementary Table S18
  - **Concern** The candidate-prioritization analysis is based on only four templates. This is a very small sample size for making a generalizable recommendation. The authors acknowledge this in the Discussion, but the strength of the claim in the Abstract and the practical recommendation in the Discussion ("suggest using AF3-mutant scaffolds for recovering top-ranked CDR candidates when only predicted structures are available") is not commensurate with the evidence. The variability across templates is likely to be high, and the mean top-10 recovery could be driven by one or two templates. The authors should either temper the claim, provide a more detailed per-template breakdown in the main text, or perform a more robust analysis (e.g., leave-one-template-out cross-validation) to assess the stability of the finding.
  - **Why it matters** The primary practical takeaway of the manuscript is the recommendation to use AF3-mutant scaffolds for candidate prioritization. If this recommendation is based on a small and potentially unrepresentative sample, it could mislead practitioners. The claim needs to be supported by a more robust analysis or presented with more caveats.
  - **Resolution test** The authors should provide a per-template breakdown of top-K recovery for all four templates in the main text or a clearly referenced supplementary table. They should also perform a sensitivity analysis, such as jackknifing the templates, to show that the conclusion is not driven by a single template. If the conclusion is not robust, the claim should be revised to reflect the uncertainty.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological clarity and reproducibility of the AF3-mutant scaffold generation
  - **Claim pointer** The description of the "mutant_af3_single" and "mutant_af3_multi" regimes, where AF3 generates a structure from each mutant sequence and the ΔΔG predictor scores the reverse mutation with sign inversion.
  - **Evidence pointer** Section "ΔΔG prediction across models and structure-input regimes" (Materials and Methods)
  - **Concern** The Materials and Methods section does not provide sufficient detail on how the AF3-mutant scaffolds were generated. Specifically, it is unclear whether the full mutant sequence was used as input to AF3, or whether the mutation was introduced into the wild-type structure and then relaxed. The description of "shared-WT-MSA/mutant-query patching" is mentioned but not explained. This is a critical methodological detail because the performance of the ΔΔG predictor in the inversion–negation regime depends on the quality and nature of the mutant scaffold. Without this detail, the results are difficult to reproduce and interpret.
  - **Why it matters** Reproducibility is a core requirement for a methods-focused study. If the mutant scaffold generation protocol is not clearly described, other researchers cannot replicate the workflow or assess whether the results are specific to the authors' implementation.
  - **Resolution test** The authors should provide a detailed step-by-step description of the AF3-mutant scaffold generation, including the exact input sequences, any template or MSA handling, and the number of AF3 samples generated per mutant. A pseudocode or flowchart would be helpful.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of the structural error-feature analysis
  - **Claim pointer** The statement that "None of these global features provided a reliable failure indicator" and the related discussion that local contact disagreement is a "candidate warning signal" for BA-DDG and H3-DDG.
  - **Evidence pointer** Section "Structural correlates of AF3-WT prediction error" (Results), Figure 3, Supplementary Tables S15-17
  - **Concern** The structural error-feature analysis is largely negative, with no features surviving multiple-testing correction. The authors appropriately describe the results as descriptive, but the interpretation of the local contact disagreement as a "candidate warning signal" is based on unadjusted correlations and is not supported by a validated threshold. The authors should be more explicit that this is a hypothesis-generating observation, not a validated finding. Additionally, the analysis is performed at the level of individual mutations, but the practical unit of decision-making is the template or the candidate list. The authors should clarify whether the mutation-level analysis is appropriate for the conclusions they draw.
  - **Why it matters** The manuscript's contribution to the practical question of when to trust AF3-based predictions is weakened if the proposed warning signal is not validated. Overstating the strength of this finding could lead to inappropriate use of the proposed signal.
  - **Resolution test** The authors should clearly state that the local contact disagreement finding is exploratory and requires validation in independent datasets. They should also consider whether a template-level analysis of the relationship between contact disagreement and prediction error would be more appropriate for the practical question.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Completeness of the evaluation of the sequence-only baseline
  - **Claim pointer** The use of PPAC as a sequence-only reference and the statement that "All four structure-based predictors had higher point correlations with experimental PDB scaffolds" than PPAC.
  - **Evidence pointer** Section "Structure-input choice and model choice both determine ΔΔG prediction accuracy" (Results), Table 2
  - **Concern** The comparison to PPAC is presented as a single point of reference, but the authors do not discuss the variability of PPAC's performance or whether the advantage of structure-based models is statistically significant. The comparison is also made only on the full 438-mutation cohort, not on the four-template candidate-prioritization cohort. The authors should provide confidence intervals for the PPAC performance and test whether the difference between PPAC and the best structure-based model is significant.
  - **Why it matters** The claim that structure-based models retain an advantage over sequence-only models is an important part of the motivation for using structural scaffolds. If this advantage is not statistically robust, the practical value of the structural approach is less clear.
  - **Resolution test** The authors should provide bootstrap confidence intervals for PPAC's performance and perform a statistical test (e.g., a paired test on the per-template correlations) to assess whether the difference between PPAC and the best structure-based model is significant.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Section numbering and cross-references
  - **Evidence pointer** Section "Candidate-prioritization performance depends on structure input, model, and template" (Results) is referred to as "Section Equation 2.5" in the text
  - **Issue** The cross-reference "Section Equation 2.5" is confusing and appears to be a formatting error.
  - **Required correction** Correct the cross-reference to the proper section number or name.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity of terminology
  - **Affected element** The term "inversion–negation"
  - **Evidence pointer** Section "ΔΔG prediction across models and structure-input regimes" (Materials and Methods)
  - **Issue** The term "inversion–negation" is used to describe the process of scoring the reverse mutation and negating the result. This term is not standard and may be unclear to readers.
  - **Required correction** Define the term clearly on first use and consider using a more descriptive phrase, such as "reverse-mutation scoring with sign inversion."

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness of reporting
  - **Affected element** The description of the AlphaFold 3 local installation
  - **Evidence pointer** Section "AlphaFold server structure prediction of TCR–pMHC complexes" (Materials and Methods)
  - **Issue** The manuscript states that a "local AlphaFold three installation" was used but does not specify the version or the specific configuration parameters (e.g., number of recycles, MSA depth).
  - **Required correction** Provide the exact version and configuration parameters used for the local AlphaFold 3 installation.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** The reporting of the Williams test results
  - **Evidence pointer** Section "ΔΔG prediction across models and structure-input regimes" (Materials and Methods)
  - **Issue** The manuscript reports p-values for the Williams test but does not report the test statistic or the direction of the difference for each comparison.
  - **Required correction** Report the test statistic and the direction of the difference (e.g., ensemble > single) for each significant comparison.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** The GitHub repository link
  - **Evidence pointer** Data availability statement
  - **Issue** The repository link is provided, but it is not clear whether the code is versioned and whether the exact scripts used for the analysis are included.
  - **Required correction** Provide a versioned release of the code and a clear description of the contents of the repository.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The generalizability of the candidate-prioritization claim based on only four templates is not established.
  - R1-M2: The AF3-mutant scaffold generation protocol is not described in sufficient detail for reproducibility.
  - R1-M3: The proposed "candidate warning signal" from the structural error-feature analysis is not validated and is over-interpreted.
  - R1-M4: The statistical significance of the advantage of structure-based models over the sequence-only baseline is not established.

- **Assessment against Nature-style criteria**
  - **Originality** The study is not conceptually novel, as the question of predicted structure reliability for ΔΔG prediction has been raised before. However, the specific focus on TCR–pMHC complexes and the systematic comparison of multiple scaffolds and models is a useful and somewhat original contribution to this specific application area.
  - **Scientific importance** The question addressed is of practical importance for TCR engineering, a field with growing therapeutic relevance. The finding that model-specific responses to scaffold choice vary is important and highlights the need for careful validation in practical applications. However, the small sample size for the key practical recommendation limits the immediate impact.
  - **Interdisciplinary readership** The study is primarily of interest to computational biologists and protein engineers. The methods and findings are unlikely to attract a broad interdisciplinary audience beyond these fields.
  - **Technical soundness** The overall study design is sound, but the statistical rigor is insufficient for some of the headline claims. The lack of detail on the AF3-mutant scaffold generation is a technical weakness that needs to be addressed.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible to readers with a background in computational biology. The use of jargon is appropriate, and the key concepts are explained clearly. However, the dense presentation of statistical results in the text could be improved with more visual aids.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant question and provides useful data, but the strength of the main practical claim (AF3-mutant scaffolds for candidate prioritization) is not commensurate with the evidence. The authors need to either provide a more robust analysis or temper the claim. The methodological details for the AF3-mutant scaffold generation also need to be clarified.

## Risk / unsupported claims
- The claim that "AF3-mutant scaffolds gave the highest mean top-10 recovery among the AF3-based inputs for all four predictors" is based on only four templates and is not robustly supported.
- The claim that "local contact disagreement is a candidate warning signal" is based on unadjusted correlations and is not validated.
- The claim that "All four structure-based predictors had higher point correlations with experimental PDB scaffolds" than PPAC is not supported by a statistical test.
- The statement that "AF3 generally recovered bound-like TCR conformations" is based on a comparison with experimental bound structures, but the manuscript does not discuss the potential for AF3 to predict conformations that are not representative of the true bound state.
- The manuscript does not discuss the potential for overfitting of the ΔΔG predictors to the training data (SKEMPI v2) and how this might affect their performance on the ATLAS test set.