## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present PREpiBind, a dual-stream joint-attention framework for peptide–MHC class II binding prediction, and systematically compare ten protein representations under a fixed downstream architecture across three dataset types. They report that protein language model representations generally outperform reference methods on Qualitative and mass spectrometry datasets, while NetMHCIIpan-4.3 performs best on thresholded IC50 datasets. They further report that representation ranking shifts across evaluation scenarios, including allele-wise, leave-one-molecule-out, and cross-species transfer settings, and conclude that representation choice should be scenario-dependent.
- **Visible evidence base** Abstract text only; no quantitative results beyond a single AUC value for ESM3 Large on the Qualitative dataset, no dataset descriptions, no architecture details, no statistical methods, no code availability statement
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, dataset construction and preprocessing details, evaluation protocol specifications, baseline implementation details, statistical significance testing, code and data availability information

## Reviewer
- **Overall assessment** The abstract presents a well-motivated and timely question regarding the choice of protein representations for pMHC-II binding prediction, and the proposed framework with modular representation integration is conceptually appealing. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the approach, the validity of the comparisons, or the robustness of the reported conclusions. The central claim that representation choice should depend on the prediction scenario is plausible but not adequately supported by the limited quantitative information provided. The work addresses an important problem in immunoinformatics, and the systematic comparison across ten representations is a potentially valuable contribution, but the current evidence base is too thin to assess whether the case is established.
- **Who would be interested in the results, and why** Computational immunologists and bioinformaticians developing or applying peptide–MHC binding prediction tools would be the primary audience. Researchers working on T-cell epitope discovery, vaccine design, and neoantigen prediction would also be interested in guidance on representation selection. The systematic comparison of protein language models, structure-prediction-derived embeddings, and substitution-matrix features under a controlled architecture could inform tool selection in both research and clinical translation contexts.
- **Major strengths** The study addresses a clearly defined and practically important question, namely which protein representation family is most effective for pMHC-II binding prediction when the downstream model is held fixed. The design of a dual-stream joint-attention framework that can accommodate diverse representation types is a sensible methodological choice. The evaluation across multiple dataset types, including qualitative binding labels, mass spectrometry data, and thresholded IC50 values, and across multiple evaluation scenarios, including allele-wise, leave-one-molecule-out, and cross-species transfer, reflects a thoughtful attempt to assess generalizability. The finding that representation ranking is scenario-dependent, rather than globally consistent, is a nuanced and potentially useful insight.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that PREpiBind with PLM representations yielded higher performance than the evaluated reference methods in the Qualitative and MS datasets, and that NetMHCIIpan-4.3 was higher on the thresholded IC50 datasets.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract reports only a single performance value, namely an AUC of 0.927 ± 0.002 for ESM3 Large on the Qualitative dataset. No performance values are provided for the MS or thresholded IC50 datasets, no comparisons with reference methods are quantified, and no statistical significance testing is described. The claim of superiority for PLM representations on two dataset types and for NetMHCIIpan-4.3 on a third cannot be assessed without the underlying numbers, error bars, and significance tests.
  - **Why it matters** The central comparative claims of the paper rest on quantitative differences between methods and representations. Without reporting the actual performance metrics, confidence intervals, and statistical tests, the reader cannot determine whether the reported differences are meaningful or within noise. This is particularly important given the authors' own statement that the small H2 panel did not support a stable ordering, which suggests that some comparisons may be underpowered.
  - **Resolution test** Provide full performance tables for all representations and reference methods across all three dataset types, including means, standard deviations, and appropriate statistical significance tests. Report effect sizes and confidence intervals for the key comparisons, and specify the number of independent replicates or cross-validation folds used.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The authors claim that PREpiBind is an openly available pMHC-II prediction framework with modular and flexible protein representations.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that the framework is openly available but provides no code repository URL, no license information, no documentation of dependencies, and no description of how the modular representation integration is implemented. The claim of open availability cannot be verified from the supplied material.
  - **Why it matters** Reproducibility and usability are central to the value proposition of a computational tool. If the code is not accessible or not adequately documented, the contribution is substantially diminished regardless of the reported performance. The abstract's claim of open availability is a concrete promise that must be verifiable.
  - **Resolution test** Provide the code repository URL, license, installation instructions, and a clear description of the software architecture. If the code is not yet available, state the expected release timeline and any access restrictions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that the results indicate that protein representation choice should depend on the intended prediction scenario rather than on a single global ranking.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract describes scenario-dependent rankings, including allele-wise, leave-one-molecule-out, and cross-species H2-out transfer evaluations, but provides no quantitative results for any of these scenarios. The claim that Chai-1 was competitive with leading PLM representations in allele-wise and leave-one-molecule-out settings, and that Chai-1 led when H2 molecules were weighted equally in cross-species transfer, is presented without supporting numbers. The statement that the small H2 panel did not support a stable ordering further complicates the interpretation.
  - **Why it matters** The conclusion that representation choice should be scenario-dependent is the main takeaway message of the abstract. If the underlying comparisons are underpowered or the differences are not statistically robust, this conclusion may be premature. The authors themselves acknowledge instability in the H2 panel, which raises questions about the reliability of the cross-species findings.
  - **Resolution test** Provide full quantitative results for all evaluation scenarios, including performance metrics, variability estimates, and statistical tests. Clearly state which comparisons are statistically significant and which are not. Discuss the power limitations of the H2 panel and how they affect the strength of the conclusions.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Dataset description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract refers to Qualitative, mass spectrometry, and thresholded IC50 datasets but does not describe their sizes, sources, or how they were split. The term "Qualitative" is ambiguous and could refer to binary binding labels from different assays.
  - **Required correction** Provide a brief description of each dataset, including the number of peptides, the number of MHC alleles, the source of the data, and the nature of the labels. Clarify what "Qualitative" means in this context.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Reference methods
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "evaluated reference methods" but only names NetMHCIIpan-4.3. The identity and number of other reference methods are not specified.
  - **Required correction** List all reference methods compared in the study and briefly justify their selection.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Performance variability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** Only one AUC value with a standard deviation is reported. No information is provided on how variability was estimated, whether across folds or across random seeds, or whether the reported standard deviation reflects a meaningful measure of uncertainty.
  - **Required correction** Describe the procedure for estimating variability, including the number of replicates, the cross-validation scheme, and whether the reported standard deviation is across folds or across independent runs.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Protein representation-integrated"
  - **Evidence pointer** Title; location not provided
  - **Issue** The title uses the term "Protein Representation-integrated" which is somewhat unusual. It is not immediately clear whether this refers to the integration of multiple representations within a single model or to the use of protein representations as input features.
  - **Required correction** Consider clarifying the terminology in the title or abstract to avoid ambiguity, for example by specifying that the framework integrates multiple representation types.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results for most comparisons, the lack of verifiable code availability, and the insufficient evidence for the scenario-dependent conclusion collectively prevent the case from being established from the supplied material.

## Risk / unsupported claims
- The claim that PLM representations yielded higher performance than reference methods on Qualitative and MS datasets is unsupported because no performance values or statistical tests are reported for these comparisons.
- The claim that NetMHCIIpan-4.3 was higher on thresholded IC50 datasets is unsupported for the same reason.
- The claim that Chai-1 was competitive with leading PLM representations in allele-wise and leave-one-molecule-out evaluations is unsupported because no quantitative results are provided.
- The claim that Chai-1 led when H2 molecules were weighted equally in cross-species transfer is unsupported.
- The claim that the small H2 panel did not support a stable ordering is unverifiable without details on the panel size and the variability of the results.
- The claim that PREpiBind is openly available is unverifiable without a code repository or access information.
- The overall conclusion that representation choice should depend on the intended prediction scenario is not adequately supported by the evidence presented in the abstract.

## Assessment against Nature-style criteria
- **Originality** The question of which protein representation is most effective for pMHC-II binding prediction under a controlled architecture is a reasonable and timely one, but the abstract does not demonstrate that the proposed framework or the comparison itself is methodologically novel beyond what is already known in the field. The dual-stream joint-attention architecture is not described in sufficient detail to assess its novelty.
- **Scientific importance** The problem of pMHC-II binding prediction is of clear importance for immunology and vaccine design, and guidance on representation selection could be practically valuable. However, the abstract does not establish that the findings would change current practice or resolve a long-standing debate.
- **Interdisciplinary readership** The topic sits at the intersection of computational biology, immunology, and machine learning. The abstract is written in a way that is accessible to specialists in these areas, but the lack of quantitative detail limits its usefulness to a broader readership.
- **Technical soundness** The technical soundness cannot be assessed from the abstract alone. The evaluation design is described at a high level, but the absence of methods details, performance numbers, and statistical tests prevents any judgment on the validity of the comparisons.
- **Readability for nonspecialists** The abstract is generally readable, but terms such as "dual-stream, joint-attention framework" and "leave-one-molecule-out" may be opaque to nonspecialists. The key message, that representation choice is scenario-dependent, is clearly stated.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents a plausible and potentially valuable study, but the absence of quantitative results, statistical analyses, and code availability means that the central claims cannot be verified. The authors should be encouraged to provide the full manuscript with complete results, methods, and code access for a proper evaluation. If the full manuscript addresses the concerns raised above, the work could be a useful contribution to the field.