## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** Scientific content, methodology, results, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The manuscript benchmarks five computational tools (ImmuneBuilder/ABB2, IgFold, AlphaFold3, GRAMM, dyMEAN) for antibody Fv structure prediction, antibody-antigen complex docking, and paratope-epitope interface analysis on a non-redundant set of 50 humanized antibody-antigen complexes, finding that AlphaFold3 is the most accurate across all tasks but still shows limited performance in fine-grained interface prediction.
- **Visible evidence base** Full text, figures (referenced as Fig. 1-6), tables (referenced as Table S1-S4), methods section, results section, discussion, conclusion, data availability statement
- **Missing materials affecting confidence** Supplementary Data 1, Supplementary Data 2, Supplementary Tables S1-S4, and all supplementary figures are not provided. The Zenodo repository (record 20710876) is not accessible for verification. Figure 1 (workflow diagram) is not visible. Individual per-complex results are not shown.

## Reviewer
- **Overall assessment** This manuscript presents a timely and practically relevant benchmark of antibody modeling tools across the complete workflow from Fv structure prediction to interface analysis. The study design is generally sound, with a non-redundant dataset, multiple retained predictions, and paired statistical testing. The finding that AlphaFold3 outperforms antibody-specific tools and docking methods is noteworthy, as is the conditional nature of interface recovery on docking success. However, several methodological details and analytical choices require clarification or strengthening before the conclusions can be fully supported. The most significant concerns relate to the dataset construction, the handling of AlphaFold3's training data cutoff, the statistical analysis framework, and the generalizability of the interface recovery analysis.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on antibody engineering, structural biologists studying antigen-antibody recognition, and developers of protein structure prediction methods. The results provide practical guidance for tool selection in antibody modeling workflows and identify persistent limitations that can inform future method development.
- **Major strengths** 1) The study addresses a clear gap in the literature by comparing tools across the complete antibody modeling workflow under a controlled design. 2) The use of multiple retained predictions and paired statistical testing is methodologically rigorous. 3) The analysis of paratope-epitope interface recovery conditional on docking quality provides practical insights. 4) The dataset is designed to be non-redundant and temporally separated from training data.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Dataset construction and temporal separation
    - **Claim pointer** "To avoid overlap with the training data of the evaluated models, we restricted the set to structures released after the cutoff date of the most recent method (AF3; 19 December 2023)"
    - **Evidence pointer** Section 2.1
    - **Concern** The claim of temporal separation from training data is not adequately supported. The manuscript states that structures were restricted to those released after the AF3 cutoff date (19 December 2023), but does not provide the actual deposition dates for the 50 complexes. The cutoff dates for ABB2, IgFold, GRAMM, and dyMEAN are not stated, and it is unclear whether the dataset is also temporally separated from these methods. Furthermore, the PDB release date is not necessarily the same as the training data cutoff date used by each method, and the authors do not discuss how they verified that none of the 50 complexes were used in training any of the evaluated models.
    - **Why it matters** If any of the benchmark complexes were included in the training data of the evaluated methods, the performance comparisons would be biased in favor of those methods, undermining the validity of the conclusions about relative accuracy.
    - **Resolution test** Provide the deposition date for each of the 50 complexes (e.g., in a supplementary table). State the training data cutoff dates for ABB2, IgFold, GRAMM, and dyMEAN, and confirm that all 50 complexes were released after these dates. Describe the procedure used to verify non-overlap with training data for each method.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Statistical analysis and reporting
    - **Claim pointer** "Group-level performance was reported as the mean across targets with a 95% confidence interval estimated by bootstrap resampling with 10,000 resamples. Pairwise comparisons between tools for a given metric were performed using two-sided Wilcoxon signed-rank tests on paired per-target values, with Benjamini–Hochberg correction across tool pairs"
    - **Evidence pointer** Section 2.5
    - **Concern** The statistical analysis has several issues. First, the use of the mean of five predictions per target as the unit of analysis discards within-target variability and may inflate the effective sample size. Second, the bootstrap confidence intervals are computed on the mean across targets, but the manuscript does not specify whether the bootstrap resamples at the target level or the prediction level. Third, the Wilcoxon signed-rank test is applied to paired per-target values, but the pairing is not clearly justified—are the same 50 targets used for all tools? Fourth, the Benjamini-Hochberg correction is applied across tool pairs, but the number of comparisons and the specific pairs tested are not stated. Fifth, the manuscript reports adjusted P values but does not provide the raw test statistics or effect sizes.
    - **Why it matters** Inadequate statistical reporting makes it impossible to assess the robustness of the claimed performance differences. The conclusions about which tools are significantly better than others depend on the validity of the statistical framework.
    - **Resolution test** Clarify the statistical unit and the resampling procedure. Justify the use of the mean of five predictions as the unit of analysis, or use a hierarchical model that accounts for within-target variability. Report the number of pairwise comparisons, the specific pairs tested, and the raw test statistics (e.g., W statistic) alongside adjusted P values. Provide effect sizes (e.g., median difference with 95% CI) for key comparisons.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Interface recovery analysis scope and generalizability
    - **Claim pointer** "When docking was reliable, AlphaFold3 accurately recovered epitope and paratope residues, salt bridges, and non-bonded contacts, but reproduced hydrogen bonds and fine-grained contact strengths less consistently."
    - **Evidence pointer** Section 3.3, Figure 6
    - **Concern** The interface recovery analysis is restricted to AF3 predictions only, with the justification that only AF3 produced a substantial fraction of correctly docked complexes. This is a reasonable approach, but it limits the generalizability of the findings. The analysis is performed on only 23 complexes (those with DockQ >= 0.49), which is a small sample for drawing robust conclusions about interface recovery patterns. Furthermore, the analysis uses PDBsum for contact extraction, but the manuscript does not discuss the sensitivity of the results to the choice of contact definition or the PDBsum parameters. The Spearman correlation for contact-multiplicity agreement (rho = 0.57) is reported without a confidence interval or a discussion of what constitutes a meaningful level of agreement.
    - **Why it matters** The conclusions about AF3's interface recovery capabilities are based on a small and potentially non-representative subset of complexes. Without a sensitivity analysis or a discussion of the limitations of the contact definition, the generalizability of these findings to other antibody-antigen complexes is unclear.
    - **Resolution test** Report the number of complexes with DockQ >= 0.49 for each of the three docking-quality strata (High, Medium, Acceptable) and consider analyzing these strata separately. Discuss the potential for selection bias in the 23-complex subset. Perform a sensitivity analysis using alternative contact definitions or parameters. Report the 95% confidence interval for the Spearman correlation.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Comparison with existing benchmarks and missing methods
    - **Claim pointer** "These tools have rarely been compared directly under a controlled, statistically grounded setup"
    - **Evidence pointer** Section 1, Section 4.2
    - **Concern** The manuscript acknowledges that DeepSCFold was not included in the benchmark but does not discuss other relevant methods or existing benchmarks. For example, the Critical Assessment of PRediction of Interactions (CAPRI) experiment regularly evaluates docking methods, including antibody-antigen complexes. The manuscript does not compare its findings with CAPRI results or other published benchmarks. Additionally, the choice of GRAMM as the representative classical docking method is not justified—other widely used docking tools (e.g., ZDOCK, HADDOCK, ClusPro) are not mentioned.
    - **Why it matters** The claim that this is a uniquely controlled comparison is weakened by the lack of discussion of existing benchmarks. The choice of GRAMM as the sole representative of classical docking may not be representative of the state of the art in this category.
    - **Resolution test** Discuss how the present benchmark relates to existing evaluations such as CAPRI. Justify the choice of GRAMM over other docking methods, or include additional docking tools. Acknowledge the limitations of the method selection and discuss how the findings might generalize to other tools.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Reporting clarity
    - **Affected element** Section 2.4.5
    - **Evidence pointer** "The antigen epitope information used for dyMEAN input was obtained from HDOCK-based docking results (Yan et al. 2020)."
    - **Issue** The use of HDOCK to generate epitope information for dyMEAN introduces a potential circularity or dependency that is not discussed. If HDOCK is itself a docking method, using its output as input to dyMEAN may bias the comparison.
    - **Required correction** Clarify whether HDOCK was used only to identify epitope residues (not to generate a full docking pose) and discuss whether this introduces any bias. If possible, use an independent method for epitope identification.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Section 2.4.6
    - **Evidence pointer** "For ABB2/ImmuneBuilder and IgFold, five repeated local prediction runs were performed for each target using different random seeds where seed control was available."
    - **Issue** The phrase "where seed control was available" is vague. It is unclear whether seed control was available for both ABB2 and IgFold, and if not, how the five predictions were generated.
    - **Required correction** Specify for each tool whether random seed control was available and, if not, describe the method used to generate multiple predictions (e.g., different random seeds for the random number generator, different initializations).

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Figure 2, Figure 3, Figure 4, Figure 5, Figure 6
    - **Evidence pointer** Figures are referenced but not provided in the manuscript text.
    - **Issue** The figures are essential for evaluating the results, but they are not included in the provided manuscript. The text describes the figures in detail, but without seeing the actual plots, it is impossible to assess the validity of the visual claims.
    - **Required correction** Provide the figures as part of the manuscript submission.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Section 2.2.4
    - **Evidence pointer** "For Fv prediction, DockQ was computed for the heavy–light variable-domain interface."
    - **Issue** DockQ is designed for protein-protein complexes, not for intra-chain domain interfaces. Using DockQ to assess the heavy-light chain interface within an Fv is unconventional and may not be appropriate, as DockQ's thresholds and interpretation are calibrated for inter-chain complexes.
    - **Required correction** Justify the use of DockQ for the heavy-light chain interface, or use a more standard metric for this assessment (e.g., interface RMSD, fraction of native contacts). If DockQ is retained, discuss how its interpretation differs for intra-chain versus inter-chain interfaces.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Section 2.1
    - **Evidence pointer** "To characterize sequence redundancy, we clustered the 50 antibodies at the heavy-chain, light-chain, paired-Fv, and CDR-H3 levels using MMseqs2 (Steinegger and Söding 2017) at 90% and 95% sequence-identity thresholds."
    - **Issue** The clustering analysis is described but the results are only summarized in the text. The full clustering results are in Supplementary Data 2, which is not provided. The text states that the set is "essentially non-redundant," but the light chains show "mild redundancy" (43-46 clusters out of 50). The potential impact of this mild redundancy on the results is not discussed.
    - **Required correction** Provide the full clustering results. Discuss whether the mild redundancy in light chains could affect the performance comparisons, particularly for methods that may be sensitive to light chain sequence diversity.

- **Technical failings that need to be addressed before the case is established** R1-M1 (temporal separation from training data), R1-M2 (statistical analysis framework), R1-M3 (interface recovery analysis scope and generalizability)
- **Assessment against Nature-style criteria** **Originality:** Moderate. The study provides a useful benchmark, but the individual tools and metrics are well-established. The novelty lies in the controlled comparison across the complete workflow. **Scientific importance:** High. Antibody engineering is a rapidly growing field, and reliable guidance for tool selection is of practical importance. The identification of persistent limitations in fine-grained interface prediction is valuable. **Interdisciplinary readership:** Moderate. The manuscript is primarily of interest to computational biologists and structural biologists. The practical implications for antibody engineering may attract a broader audience. **Technical soundness:** Requires improvement. The concerns about dataset construction, statistical analysis, and interface recovery analysis need to be addressed. **Readability for nonspecialists:** Good. The manuscript is well-structured and clearly written, with appropriate background and explanations of key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a timely and important question, and the core findings are potentially valuable. However, the concerns about dataset construction, statistical analysis, and interface recovery analysis must be addressed before the conclusions can be fully supported. The authors should provide the missing supplementary materials, clarify the statistical framework, and strengthen the interface recovery analysis.

## Risk / unsupported claims
- The claim that the dataset is temporally separated from the training data of all evaluated methods is not adequately supported (R1-M1).
- The claim that AF3 is "the most accurate method across all three levels" is based on a statistical analysis that requires clarification and strengthening (R1-M2).
- The claim that AF3 "accurately recovered epitope and paratope residues, salt bridges, and non-bonded contacts" is based on a small subset of complexes and may not be generalizable (R1-M3).
- The claim that the benchmark is "controlled and statistically grounded" is weakened by the lack of discussion of existing benchmarks and the choice of GRAMM as the sole classical docking method (R1-M4).