## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, methods, and figure legends.
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and interpretation of results as presented. No assessment of editorial fit or scope for the specific journal.
- **Shared manuscript claim summary** The authors present a standardized benchmark of five co-folding models (AlphaFold 3, Protenix-v2, ESMFold2, ESMFold2-fast, OpenDDE) for antibody-antigen complex prediction, using a newly curated dataset (SAbDab2-Bench) combined with a reconstructed subset of FoldBench (Ab-FoldBench). They evaluate docking accuracy, confidence-based selection, inference-time scaling, and sensitivity to interface mutations and non-cognate antigen shuffling. They report that OpenDDE achieves the highest median DockQ and pass rate, followed by Protenix-v2, with both outperforming AlphaFold 3. They also find that confidence metrics are generally informative but require model-specific calibration, and that all models show stronger rejection of non-cognate antigens than of interface mutations.
- **Visible evidence base** Full text with results, figures (Figure 1-4), tables (Table 1-4), and methods sections. Supplementary figures and tables are referenced but not fully provided.
- **Missing materials affecting confidence** Supplementary figures (S1-S13), supplementary tables (S1-S6), and the full dataset details are referenced but not included in the provided material. This limits full verification of some analyses, particularly the stratified analyses and extended configurations.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and practically important question: how do recently released open-source co-folding models compare to AlphaFold 3 for antibody-antigen complex prediction under standardized conditions? The authors have made a commendable effort to control for confounding variables by standardizing input preparation, sampling, and evaluation. The inclusion of decoy-based specificity testing is a valuable addition beyond simple docking accuracy benchmarks. However, several methodological choices and interpretations require clarification or additional analysis before the conclusions can be fully supported. The statistical approach, while appropriate in parts, has some limitations that should be addressed. The practical guidance provided is useful but would benefit from more explicit consideration of the trade-offs involved.
- **Who would be interested in the results, and why** Researchers in antibody engineering, structural biology, and computational protein design would find this benchmark highly relevant. The practical comparison of model performance, including runtime and licensing considerations, is directly useful for practitioners selecting tools for epitope mapping, candidate triage, and structure-guided design. The analysis of confidence calibration and specificity testing is also relevant to the broader protein-protein interaction prediction community.
- **Major strengths**
  1. The standardization of input preparation, sampling, and evaluation across models is a significant strength, addressing a common limitation in prior benchmarks.
  2. The construction of a new, curated dataset (SAbDab2-Bench) with post-training structures and sequence-diversity filtering is valuable and extends the evaluation beyond existing benchmarks.
  3. The inclusion of decoy-based specificity testing (mutations and antigen shuffling) goes beyond simple accuracy metrics and addresses a critical practical need.
  4. The analysis of confidence-based selection and the reporting of model-specific calibration is practically useful.
  5. The release of code, data, and generated structures is commendable and supports reproducibility.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that OpenDDE achieved the highest median DockQ and pass rate, followed by Protexin-v2, and that both outperformed AlphaFold 3 on these measures.
- **Evidence pointer** Figure 2b-c, Table 2
- **Concern** The statistical comparison between models relies on paired tests (McNemar for pass rates, permutation for medians) that are appropriate for paired data. However, the manuscript does not adequately address the issue of multiple testing across the 10 pairwise model comparisons. While the Benjamini-Hochberg correction is applied, the power of these tests to detect meaningful differences, particularly between adjacent models in the ranking, is not discussed. The statement that "some of these differences, and notably all differences between ranking-adjacent models, did not reach the threshold for statistical significance" is important, but the manuscript does not provide effect sizes or confidence intervals for the differences in median DockQ. This makes it difficult to assess whether the lack of significance reflects a true lack of difference or insufficient power. The authors should report effect sizes and confidence intervals for the key comparisons, and discuss the practical significance of the observed differences.
- **Why it matters** The central claim of the paper is the relative performance ranking of the models. Without a clear assessment of the magnitude and uncertainty of the differences, the ranking may be over-interpreted. The practical guidance provided in the conclusions depends on this ranking being reliable.
- **Resolution test** Provide effect sizes (e.g., median difference with 95% confidence intervals) for the key pairwise comparisons. Discuss the statistical power of the tests given the sample size of 200 complexes. Consider whether a non-inferiority or equivalence framework might be more appropriate for comparing adjacent models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript states that "Providing the antigen in the conformation observed in its cognate antibody-bound structure increased docking pass rates for AF3, Protenix-v2 and OpenDDE" and that "non-cognate templates produced more modest gains in high-quality predictions."
- **Evidence pointer** Figure S2, Figure S3
- **Concern** The analysis of template contribution is confounded by the fact that the cognate-bound antigen structure is, by definition, the target structure being predicted. Supplying this structure provides the model with information about the bound conformation that would not be available in a real prospective scenario. The comparison between cognate-bound and non-cognate templates is useful, but the manuscript does not clearly distinguish between the value of having any template versus the value of having the exact bound conformation. The authors should clarify that the cognate-bound template condition represents an upper bound on template utility, and the non-cognate template condition is more representative of real-world use. The practical recommendation to supply antigen structures should be framed in this context.
- **Why it matters** The practical guidance for users depends on understanding the realistic benefit of template usage. Overstating the benefit of cognate-bound templates could mislead users into expecting similar gains in prospective applications where such structures are unavailable.
- **Resolution test** Clearly label the cognate-bound template condition as an oracle or upper-bound scenario. Discuss the implications of the non-cognate template results for practical use. Consider analyzing the subset of cases where the non-cognate template is structurally similar to the cognate-bound antigen to better understand the source of the benefit.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript reports that "Under default settings, ipTM and pTM varied across runs in a complex-dependent manner, showing that fixed seeds alone do not guarantee reproducibility."
- **Evidence pointer** Table S6, Methods Section 3.9
- **Concern** The finding of non-determinism in Protenix-v2 is important, but the manuscript does not fully explore its implications. The primary analysis uses ten seeds and reports results averaged across all subsets of five seeds. If the model is non-deterministic even with fixed seeds, then the results from a single run with a given seed may not be reproducible. The manuscript should clarify whether the non-determinism is due to non-deterministic PyTorch operations that can be controlled by setting a deterministic flag, or whether it is inherent to the model architecture. The practical guidance should include a recommendation for users to enable deterministic execution when reproducibility is critical.
- **Why it matters** Reproducibility is a core principle of scientific benchmarking. If the results cannot be reproduced by other researchers, the benchmark's value is significantly diminished. The manuscript should provide clear guidance on how to obtain reproducible results.
- **Resolution test** Provide a detailed analysis of the sources of non-determinism. Recommend a specific configuration (e.g., setting the deterministic flag) that users should adopt for reproducible results. Report the impact of this configuration on runtime and performance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The manuscript concludes that "current models appear better at rejecting clearly non-cognate partners than at recognizing sequence changes that disrupt or diminish binding."
- **Evidence pointer** Figure 4, Tables 4, S2, S3
- **Concern** The decoy analysis is a valuable addition, but the interpretation is limited by the nature of the decoys. The interface mutations are designed to be disruptive, but their actual effect on binding is not experimentally verified. The manuscript acknowledges this ("these decoys are expected, rather than experimentally shown, to bind weakly or not at all"), but the discussion could be more nuanced. The finding that OpenDDE retains high confidence for many mutated interfaces could be interpreted as a limitation, but it could also reflect that some mutations do not significantly disrupt the overall binding mode. The authors should discuss alternative interpretations and the need for experimental validation.
- **Why it matters** The conclusion about specificity is a key finding of the paper. If the decoys are not representative of real non-binding pairs, the conclusion may not generalize. The practical implications for screening and design depend on this conclusion.
- **Resolution test** Discuss the limitations of the decoy design more thoroughly. Consider analyzing the relationship between the magnitude of the predicted binding affinity change and the confidence score. Suggest future work with experimentally validated non-binding pairs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "OpenDDE achieved the highest median DockQ and docking pass rate, followed by Protenix-v2, although their difference was not statistically significant." This is slightly confusing as it implies a ranking that is not statistically supported. It would be clearer to state that OpenDDE and Protenix-v2 performed similarly and both outperformed the other models.
- **Required correction** Rephrase to avoid implying a definitive ranking where statistical significance is lacking. For example: "OpenDDE and Protenix-v2 achieved the highest median DockQ and docking pass rates, with no statistically significant difference between them, and both outperformed AlphaFold 3."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Section "Standardised inference and evaluation"
- **Evidence pointer** Table 1
- **Issue** The table lists "Seeds ∣ Samples" as "10 ∣ 5" for all models. It is unclear whether this means 10 seeds with 5 samples per seed, or 5 seeds with 10 samples per seed. The text later clarifies "five samples for each of ten seeds," but the table notation is ambiguous.
- **Required correction** Clarify the notation in the table legend or use a more explicit format, such as "10 seeds × 5 samples."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, Section "Model implementation and compute specifications"
- **Evidence pointer** Methods Section 3.4
- **Issue** The manuscript mentions that ESMFold2 was "slower than its competitor in this study" and attributes this to "the absence of optional acceleration libraries." However, it is not clear whether this is a limitation of the model or the specific installation. The authors should clarify whether the reported runtimes are representative of typical usage.
- **Required correction** Add a sentence clarifying that the ESMFold2 runtimes may be improved by installing the optional acceleration libraries, and that the reported times are specific to the authors' installation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Section "Performance in antibody-antigen complex prediction"
- **Evidence pointer** Figure 2g
- **Issue** The correlation between H-CDR3 sequence novelty and DockQ is weak, but the manuscript does not discuss potential reasons for this. For example, the diversity of the benchmark set or the specific metric used for sequence novelty could influence the result.
- **Required correction** Add a brief discussion of why the relationship might be weak, and consider whether alternative measures of novelty (e.g., structural novelty) might be more relevant.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The conclusion that "Protenix-v2 offers a useful balance for antibody-design campaigns" is based on the benchmark results, but the manuscript does not explicitly discuss the trade-offs between accuracy, speed, and licensing for different use cases. A more explicit decision framework would be helpful.
- **Required correction** Add a brief paragraph in the conclusions that summarizes the key trade-offs (accuracy vs. speed vs. licensing) and provides guidance on model selection for different scenarios (e.g., high-throughput screening vs. high-accuracy design).

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of effect sizes and confidence intervals for key performance comparisons.
  - R1-M2: Confounded interpretation of template benefit without clear distinction between oracle and realistic scenarios.
  - R1-M3: Insufficient guidance on achieving reproducible results given the observed non-determinism.

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its comprehensive, standardized comparison of recently released open-source models, including a novel decoy-based specificity analysis. However, the individual components (benchmarking, confidence analysis) are not entirely new.
  - **Scientific importance**: The findings are practically important for the antibody engineering community, providing guidance on model selection and highlighting limitations in specificity testing. The release of a new benchmark dataset is a valuable contribution.
  - **Interdisciplinary readership**: The topic is of interest to structural biologists, computational biologists, and antibody engineers. The manuscript is written in a way that is largely accessible to these groups, though some methodological details may be challenging for non-specialists.
  - **Technical soundness**: The overall methodology is sound, with careful standardization. However, the statistical analysis could be strengthened (R1-M1), and the interpretation of the template analysis needs clarification (R1-M2). The reproducibility issue (R1-M3) is a concern.
  - **Readability for nonspecialists**: The manuscript is generally well-written and clear. The figures are informative. However, the methods section is dense and may be difficult for non-experts to follow. The abstract and conclusions are accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question with a well-designed benchmark. The major concerns regarding statistical rigor, interpretation of template benefits, and reproducibility guidance need to be addressed before the conclusions can be fully supported. The minor comments are mostly clarifications that would improve readability.