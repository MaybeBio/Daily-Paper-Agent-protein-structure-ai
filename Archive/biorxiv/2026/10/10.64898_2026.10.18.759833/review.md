## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) for a single-author preprint submitted to bioRxiv.
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims relative to presented evidence, and suitability for a general structural biology audience. No assessment of code functionality or reproducibility beyond what is described in the text.
- **Shared manuscript claim summary** The authors introduce BiHC, a criterion-based protein domain parser that uses Voronoi tessellation-derived contact areas, normalized by fragment size and internal packing, and weighted by residue hydropathy, to define a pairwise self-containment score F and a global partition quality score G. BiHC performs independent top-down and bottom-up hierarchical searches, and is claimed to achieve state-of-the-art performance among criterion-based parsers and comparable performance to deep learning methods on CATH-ECOD consensus benchmarks.
- **Visible evidence base** Abstract, full introduction, results overview (including dataset construction, tuning, benchmark performance, and case studies), discussion, and methods sections. Figures are referenced but not provided. Supplementary files are referenced but not provided.
- **Missing materials affecting confidence** Figures 1-7, all supplementary tables (S1-S7), Supplementary File 1 (including ablation study), Supplementary File 2 (per-chain results), and the actual benchmark datasets. Without these, quantitative claims cannot be independently verified.

## Reviewer

- **Overall assessment** This manuscript presents a conceptually interesting approach to protein domain segmentation, leveraging Voronoi tessellation in a way that has been underexplored in modern domain parsers. The methodological framework is clearly described and the motivation is well-articulated. However, the manuscript as presented has several critical gaps. The results section is largely descriptive without presenting actual numerical data, making it impossible to assess the strength of the claimed performance. The reliance on a single-author submission with no code or data available at the time of review further limits verification. The core claims, while plausible, are not substantiated by the evidence visible in this manuscript. The work has potential, but in its current form, the case is not fully established.

- **Who would be interested in the results, and why** Structural biologists, bioinformaticians, and researchers working on protein structure annotation and classification would be the primary audience. The work is relevant to those interested in criterion-based (non-machine-learning) approaches to domain parsing, as it offers a transparent alternative to deep learning methods. The use of Voronoi tessellation and physical self-containment criteria may also appeal to researchers studying protein geometry and packing. The comparative benchmarking against Chainsaw and Merizo would be of interest to the broader protein structure prediction community.

- **Major Strengths**
  1. The conceptual framing is strong. The authors correctly identify a gap in the field: most modern domain parsers rely on learned representations, and explicit geometric criteria are underrepresented. The use of Voronoi contact areas, normalized for size and packing, is a thoughtful and physically motivated approach.
  2. The methodological design is coherent. The bidirectional search strategy (independent top-down and bottom-up) is a sensible way to explore the partition space, and the use of a single scoring function F throughout both candidate generation and evaluation is a principled improvement over methods like STRUDL that use different criteria at different stages.
  3. The authors are appropriately cautious in their claims. They acknowledge the multi-domain performance gap and the potential for curated annotations to reflect non-geometric information. This balanced perspective is commendable.
  4. The inclusion of a reconstructed STRUDL (STRUDL-R) as a baseline is a useful contribution, as it allows for direct comparison with a historical Voronoi-based method.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that "On the primary CONSENSUS-43 benchmark, BiHC showed a clear class-dependent performance profile" and that "BiHC achieved the strongest performance among all tested criterion-based parsers and was comparable to Chainsaw" under balanced evaluation.
- **Evidence pointer** Results section, "BiHC performance on benchmark datasets"; Figures 4 and 5 are referenced but not provided; Tables S2-S7 are referenced but not provided.
- **Concern** The central quantitative claims of the manuscript are entirely unsupported by the visible text. No numerical results are presented in the body of the manuscript. The reader is told that BiHC performed well, but is not shown any actual performance values, confidence intervals, or statistical comparisons. The figures and supplementary tables that would contain this information are not available for review. This is a fundamental issue, as the entire case for BiHC's utility rests on these benchmark results.
- **Why it matters** Without access to the actual performance numbers, it is impossible to evaluate whether the claims of "strongest among criterion-based parsers" and "comparable to Chainsaw" are justified. The reader cannot assess the magnitude of differences, the variance across protein classes, or the practical significance of the results. This is a blocking issue for any assessment of the manuscript's validity.
- **Resolution test** The authors must provide the actual numerical results in the main text or in accessible supplementary materials. This should include at minimum: exact-K accuracy, K-score, IoU, NDO, CSD, and DBD for all methods on both benchmarks, with appropriate measures of uncertainty. The figures must be made available for review.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript states that "BiHC applies F in two independent hierarchical searches" and that "Intermediate partitions from both searches are ranked by a global partition quality score G, derived on the same principle."
- **Evidence pointer** Results section, "Overview of the BiHC framework"; Materials and Methods, "Pairwise self-containment score" and "Global partition quality score".
- **Concern** The mathematical definitions of the key quantities F and G are not fully specified in the visible text. The methods section describes the components of F (hydropathy-weighted interface, reduced-size term, geometric Voronoi contact density) but the actual equations are not shown. The text refers to equations that are not present in the manuscript. Similarly, the definition of G is described verbally but the exact formula is not given. The threshold t is mentioned but its precise role in the scoring is not fully formalized.
- **Why it matters** The manuscript's central contribution is a novel scoring function. Without the explicit mathematical formulation, the method cannot be reproduced, evaluated for correctness, or compared to alternative approaches. The reader cannot assess whether the normalization is sound, whether the hydropathy weighting is appropriate, or whether the thresholding scheme is principled. This is a fundamental gap in a methods-focused paper.
- **Resolution test** The authors must provide the complete mathematical definitions of F, G, and the thresholding procedure. This should include all equations, definitions of all variables, and a clear statement of how the threshold t is applied. The equations should be numbered and referenced in the text.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark validity
- **Claim pointer** The manuscript claims that CONSENSUS-43 and CONSENSUS-44 are appropriate benchmarks, with CONSENSUS-43 being "the primary benchmark" and CONSENSUS-44 used "to assess the stability of tool performance."
- **Evidence pointer** Results section, "Overview of the dataset construction"; Materials and Methods, "Data preprocessing" and "CATH-ECOD consensus filtering".
- **Concern** The benchmark construction is described in detail, but several aspects raise concerns. First, the CONSENSUS-44 set is derived from CATH v4.4, which the authors acknowledge "is not fully independent of that method" (i.e., Chainsaw) because CATH v4.4 used Chainsaw in its annotation pipeline. This means that the benchmark itself may be biased toward Chainsaw's predictions, making any comparison on this set difficult to interpret. Second, the filtering criteria (CATH-ECOD agreement on domain count and partition IoU ≥ 0.90) may select for "easy" cases where the two databases agree, potentially reducing the difficulty of the benchmark and limiting its ability to discriminate between methods. Third, the number of multi-domain structures in CONSENSUS-43 (200 out of 3231) is small, which may limit the statistical power of the multi-domain comparisons.
- **Why it matters** The validity of the benchmark directly affects the interpretability of the performance claims. If the benchmark is biased or too easy, the reported performance may not generalize to real-world domain parsing tasks. The small number of multi-domain structures is particularly concerning, as this is where the authors acknowledge BiHC struggles.
- **Resolution test** The authors should provide a more detailed analysis of the benchmark characteristics, including the distribution of domain counts, protein lengths, and structural classes. They should also discuss the potential impact of the CATH v4.4 annotation bias on CONSENSUS-44 results and consider whether additional benchmarks (e.g., from ECOD alone or from a manually curated set) would strengthen the evaluation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The manuscript states that "BiHC achieved the strongest performance among all tested criterion-based parsers and was comparable to Chainsaw, the best-performing deep learning method tested."
- **Evidence pointer** Results section, "BiHC performance on benchmark datasets"; Materials and Methods, "Evaluated domain parsers".
- **Concern** The comparison with other methods is described, but the details of how these methods were run are not fully specified. For example, were the deep learning methods (Chainsaw, Merizo) run with their default settings, or were they fine-tuned on the benchmark? Were the criterion-based methods (UniDoc, SWORD2) run with their default parameters, or were they optimized for the benchmark? The manuscript mentions that "All tools were obtained from their official repositories" but does not state the specific versions or configuration used. Additionally, the reconstruction of STRUDL (STRUDL-R) is described as having a "logistic classifier... fitted on the tuning set," which raises the question of whether STRUDL-R was given an advantage by being trained on data from the same distribution as the benchmark.
- **Why it matters** Fair comparison is essential for the validity of the performance claims. If other methods were not given the same opportunity to perform well (e.g., through hyperparameter tuning), the comparison may be biased in favor of BiHC. Conversely, if STRUDL-R was trained on the tuning set, it may have an unfair advantage over methods that were not similarly tuned.
- **Resolution test** The authors should provide a detailed description of how each comparison method was configured and run, including specific versions, parameters, and any tuning procedures. They should also clarify whether the tuning set was used to optimize any aspect of the comparison methods, and if so, how this was done.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Ablation study rigor
- **Claim pointer** The manuscript states that "we conducted an ablation study on the tuning set to assess the contributions of its individual components" and that "most components of F, including hydropathy and size-dependent terms, contributed to the performance."
- **Evidence pointer** Discussion section; Supplementary File 1, "Ablation study" section (not provided).
- **Concern** The ablation study is only mentioned in passing, with no results presented in the main text. The reader is told that removing components led to "a slight decrease in balanced domain-count performance, although the differences were not significant." This is a critical piece of evidence for the design of F, but the details are entirely relegated to a supplementary file that is not available for review. The lack of significance is also concerning, as it suggests that the individual components may not be essential, which would weaken the justification for the specific form of F.
- **Why it matters** The ablation study is the primary evidence that the specific formulation of F is well-justified. If the components do not significantly contribute, the method could potentially be simplified, or the choice of components may be arbitrary. The reader cannot evaluate this without seeing the actual results.
- **Resolution test** The authors should present the ablation study results in the main text or provide the supplementary file for review. They should also discuss the implications of the lack of statistical significance for the design choices.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "Statement of importance"
- **Issue** The statement "This study shows that BiHC addresses both problems using Voronoi-based criteria, providing competitive domain-parsing performance" is somewhat vague. The abstract would benefit from a brief mention of the specific performance metrics and the magnitude of the results.
- **Required correction** Consider adding a sentence with a representative quantitative result (e.g., "BiHC achieved a balanced exact-K accuracy of 81.4% on the CONSENSUS-43 benchmark, comparable to the deep learning method Chainsaw at 82.5%").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The data availability statement says that benchmark manifests and scripts "will be deposited" at Zenodo and GitHub, but no links or accession numbers are provided. This makes it impossible for reviewers or readers to access the data at the time of review.
- **Required correction** Provide the actual URLs or DOIs for the deposited data, or state clearly that they will be made available upon publication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods, "Pairwise self-containment score"
- **Evidence pointer** Materials and Methods, "Pairwise self-containment score"
- **Issue** The term "self-containment" is used throughout, but it is not formally defined. The concept is described as a combination of weak inter-fragment contact and strong intra-fragment packing, but a precise definition would help the reader understand the physical interpretation.
- **Required correction** Provide a brief formal definition of "self-containment" in the methods section, perhaps in terms of the ratio of inter-fragment to intra-fragment contact.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "BiHC performance on benchmark datasets"
- **Evidence pointer** Results section, "BiHC performance on benchmark datasets"
- **Issue** The manuscript reports mean values for metrics but does not provide confidence intervals or measures of variance. Given the small number of multi-domain structures (200 in CONSENSUS-43), the uncertainty in these estimates could be substantial.
- **Required correction** Report confidence intervals or standard errors for the key metrics, particularly for the multi-domain subset.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 6
- **Evidence pointer** Results section, "Representative case studies"
- **Issue** The case studies are described in text, but the actual figures are not available. The selection of cases across four agreement patterns is a good idea, but the reader cannot assess the visual quality of the predictions without seeing the structures.
- **Required correction** Ensure that Figure 6 is of high quality and clearly shows the reference and predicted domain boundaries for each case.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Related work
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction mentions STRUDL as a prior Voronoi-based method, but does not discuss other recent criterion-based approaches in detail. A brief comparison with methods like UniDoc or SWORD2 in the introduction would help position BiHC more clearly.
- **Required correction** Add a sentence or two in the introduction summarizing the key differences between BiHC and other recent criterion-based parsers.

## Risk / unsupported claims
- The claim that BiHC "achieved the strongest performance among all tested criterion-based parsers" is unsupported in the visible text, as no numerical results are presented.
- The claim that BiHC is "comparable to Chainsaw" is unsupported for the same reason.
- The claim that "most components of F, including hydropathy and size-dependent terms, contributed to the performance" is unsupported, as the ablation study results are not visible.
- The claim that "BiHC showed a clear class-dependent performance profile" is unsupported without the actual performance data.
- The claim that the benchmark construction includes "controls for training-set overlap, sequence redundancy, and structural redundancy" is described, but the effectiveness of these controls cannot be assessed without the data.
- The claim that "the Voronoi-based criterion can yield competitive domain parsing" is a reasonable hypothesis but is not established from the provided evidence.