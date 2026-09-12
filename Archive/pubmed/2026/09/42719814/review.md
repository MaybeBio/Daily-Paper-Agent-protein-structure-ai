# Review setup
- **Input scope** Full manuscript (including main text, figures, methods, and supplementary information)
- **Assessment boundary** Evaluation of computational benchmarking methodology, statistical rigor, dataset construction, and conclusions drawn from the presented evidence
- **Shared manuscript claim summary** The authors benchmark five computational tools (ImmuneBuilder/ABB2, IgFold, AlphaFold3, GRAMM, dyMEAN) for antibody Fv structure prediction, antibody-antigen complex docking, and paratope-epitope interface analysis on a non-redundant set of 50 humanized antibody-antigen complexes, finding that AlphaFold3 outperforms the other methods across all tasks but still shows limited accuracy for fine-grained interface features.
- **Visible evidence base** Main text (Sections 1–5), Methods (Section 2), Results (Section 3), Discussion (Section 4), Figures 1–6, Supplementary Tables S1–S4, Supplementary Data 1–2
- **Missing materials affecting confidence** The actual supplementary material files (Supplementary Data 1–2, Tables S1–S4) are not provided; only their descriptions are visible. The Zenodo repository (record 20710876) is referenced but not accessible for verification. Figure contents are described but the figures themselves are not visible.

# Reviewer

- **Overall assessment** This manuscript presents a timely and practically useful benchmarking study of computational antibody modeling tools. The experimental design is generally sound, with careful attention to dataset construction, statistical testing, and multi-level evaluation. The finding that AlphaFold3 outperforms antibody-specific tools even for CDR-H3 prediction is noteworthy and challenges prevailing assumptions in the field. However, several methodological concerns reduce confidence in the conclusions: the dataset size (n=50) is modest for the number of comparisons performed, the exclusion of recently published methods (particularly DeepSCFold) limits the study's currency, and the interface recovery analysis is conditional on docking success in a way that may introduce selection bias. The manuscript would benefit from clearer justification of the dataset size, discussion of statistical power, and inclusion of additional methods or a clear rationale for their exclusion.

- **Who would be interested in the results, and why** Computational antibody engineers, structural biologists working on therapeutic antibody design, and developers of protein structure prediction methods. The study provides practical guidance for tool selection across the antibody modeling workflow and identifies specific limitations (CDR-H3 accuracy, fine-grained interface prediction) that define clear targets for method development.

- **Major strengths**
  1. Controlled, statistically grounded comparison using paired statistical testing with multiple-testing correction, which is more rigorous than typical benchmarks in this field.
  2. Multi-level evaluation spanning Fv structure, complex docking, and interface recovery, providing a complete workflow assessment rather than isolated metric comparisons.
  3. Careful dataset construction with temporal separation from training data and sequence redundancy analysis, reducing the risk of training-test leakage.
  4. Practical guidance for tool selection with clear identification of trade-offs (AF3 accuracy vs. ABB2/IgFold reproducibility and speed).

- **Major Concerns**

**Concern ID** R1-M1
**Severity** Major
**Blocking** No
**Axis** Statistical rigor / dataset adequacy
**Claim pointer** The study evaluates five tools on 50 complexes and reports statistically significant differences between methods.
**Evidence pointer** Section 2.1, Section 2.5, Section 3.1–3.2
**Concern** The dataset of 50 complexes is modest for the number of comparisons performed (multiple tools, multiple metrics, multiple stratification levels). The authors use paired Wilcoxon tests with Benjamini-Hochberg correction, but do not report effect sizes or confidence intervals for the differences between methods beyond the bootstrap CIs for individual methods. For the CDR-H3 comparison (Section 3.1), the adjusted P-values are reported as 0.026 and 0.017, which are only marginally significant after correction. With n=50, the statistical power to detect moderate effect sizes is limited, and the study may be underpowered for some of the subgroup analyses (e.g., interface recovery stratified by DockQ threshold, where n=23 for the reliable docking subset).
**Why it matters** Without adequate statistical power, the reported "significant" differences may be unreliable, and the absence of significant differences between ABB2 and IgFold (adjusted P=0.75) could reflect insufficient power rather than true equivalence. The study's conclusions about tool rankings depend on these statistical comparisons.
**Resolution test** Provide a power analysis or justification that n=50 is sufficient for the planned comparisons. Report effect sizes (e.g., Cohen's d or rank-biserial correlation) alongside P-values for all pairwise comparisons. For the CDR-H3 comparison, consider whether the marginal significance (adjusted P=0.026, 0.017) supports the strong claim that "AF3 achieved the lowest CDR-H3 RMSD, significantly lower than both ABB2 and IgFold."

**Concern ID** R1-M2
**Severity** Major
**Blocking** No
**Axis** Methodological completeness / currency
**Claim pointer** The study evaluates "current publicly available computational tools" and provides "practical guidance for tool selection in antibody-modeling workflows" (Section 5).
**Evidence pointer** Section 2.4, Section 4.2, Section 5
**Concern** The study explicitly mentions DeepSCFold (Hou et al. 2025) in the Introduction and Discussion as a recently developed method that "was reported to achieve competitive interface DockQ relative to AF3 and a 12.4% improvement in prediction success rate at DockQ > 0.23," yet DeepSCFold is not included in the benchmark. The authors state this is because it was "not included in the predefined experimental framework" (Section 4.2). Given that the manuscript is being submitted in 2026 and DeepSCFold was published in 2025, its exclusion is a significant gap that undermines the claim of providing comprehensive practical guidance. The study also does not include other recent methods such as ABlooper, DeepAb, or ESMFold-based antibody predictors.
**Why it matters** The practical value of the benchmark for tool selection is substantially reduced if a method that reportedly outperforms AF3 on the same task is not evaluated. Readers cannot determine whether AF3 remains the best choice or whether DeepSCFold (or other recent methods) would be preferable.
**Resolution test** Either include DeepSCFold and other recent methods in the benchmark, or provide a clear, justified rationale for their exclusion (e.g., unavailability of public code, inability to run at scale, or fundamental incompatibility with the evaluation framework). If exclusion is justified, temper the claims about providing comprehensive guidance.

**Concern ID** R1-M3
**Severity** Major
**Blocking** No
**Axis** Selection bias / conditional analysis
**Claim pointer** "When docking was reliable, AF3 accurately recovered epitope and paratope residues, salt bridges, and non-bonded contacts" (Abstract, Section 3.3).
**Evidence pointer** Section 3.3, Figure 6
**Concern** The interface recovery analysis is restricted to the 23/50 complexes where AF3 achieved DockQ ≥ 0.49 (medium or high quality). This conditional analysis introduces potential selection bias: the 23 "successful" complexes may systematically differ from the 27 "failed" complexes in ways that affect interface recovery metrics. For example, complexes with simpler interfaces, less conformational flexibility, or more canonical binding modes may be both easier to dock and easier to analyze for interface features. The authors report that "when docking failed (DockQ < 0.23), the predicted and experimental contacts barely overlapped (mean residue-pair F1 = 0.04)," but this does not address whether the 23 successful cases are representative of antibody-antigen complexes generally.
**Why it matters** The study's key practical conclusion—that AF3 is "well suited to identifying epitope and paratope regions in correctly docked complexes"—is based on a non-random subset of complexes. If the successful subset is biased toward easier cases, the reported interface recovery metrics may overestimate AF3's general performance.
**Resolution test** Compare the characteristics of the 23 successful and 27 failed complexes (e.g., interface size, number of CDR contacts, antigen type, conformational change magnitude) to assess whether selection bias is present. Report interface recovery metrics for all 50 complexes (as is partially done in Figure 6A) and discuss how the conditional analysis affects generalizability.

**Concern ID** R1-M4
**Severity** Major
**Blocking** No
**Axis** Reproducibility / methodology transparency
**Claim pointer** "Data, structural predictions, evaluation results, and analysis code are available from Zenodo under record 20710876" (Availability and implementation).
**Evidence pointer** Data availability statement, Section 2.4.6
**Concern** The Zenodo repository is referenced but not accessible for verification. More critically, several methodological details that affect reproducibility are unclear: (1) For AF3, the authors used the "official AlphaFold3 web server" but do not specify which version or whether the server's model weights were updated during the study period. (2) For GRAMM, the "public GRAMM web server" was used in "free docking mode" but the specific version and parameter settings are not reported beyond this description. (3) For dyMEAN, "antigen epitope information used for dyMEAN input was obtained from HDOCK-based docking results" (Section 2.4.5), but the HDOCK parameters and how epitope information was extracted are not described. (4) The "five repeated local prediction runs" for ABB2 and IgFold used "different random seeds where seed control was available" (Section 2.4.6), but it is unclear which tools support seed control and what seeds were used.
**Why it matters** Without precise methodological details, other researchers cannot reproduce the results or apply the same evaluation framework to new methods. The use of web servers (AF3, GRAMM) that may have changed between the study period and any attempted replication is particularly problematic.
**Resolution test** Provide version numbers and specific parameters for all web servers and software tools. Describe the HDOCK procedure and epitope extraction method in sufficient detail for replication. Report whether seed control was available for each tool and what seeds were used. If possible, provide a frozen software environment (e.g., Docker container) for locally deployed tools.

- **Minor Comments**

**Concern ID** R1-m1
**Severity** Minor
**Axis** Presentation / clarity
**Affected element** Section 2.2.4 (DockQ description)
**Evidence pointer** Section 2.2.4
**Issue** The description of DockQ computation for Fv prediction states "DockQ was computed for the heavy–light variable-domain interface," but the standard DockQ metric is designed for protein-protein complexes, not intra-complex domain interfaces. It is unclear whether the same thresholds (High ≥ 0.8, Medium ≥ 0.49, Acceptable ≥ 0.23) are appropriate for evaluating Fv domain packing.
**Required correction** Clarify whether standard DockQ thresholds were used for Fv evaluation and justify their applicability, or report whether alternative thresholds were considered.

**Concern ID** R1-m2
**Severity** Minor
**Axis** Data presentation
**Affected element** Figure 2, Figure 3, Figure 4
**Evidence pointer** Section 3.1, Section 3.2
**Issue** The figures are described in the text but not visible. From the descriptions, it appears that individual data points are shown in some plots (e.g., Figure 3A showing CDR-H3 RMSD distributions) but not others. For small datasets (n=50), showing individual points alongside summary statistics is important for assessing distribution shape and identifying outliers.
**Required correction** Ensure all box plots or bar plots showing per-complex metrics include individual data points (e.g., as strip plots or jittered points) to allow readers to assess data distribution and identify potential outliers.

**Concern ID** R1-m3
**Severity** Minor
**Axis** Methodological clarity
**Affected element** Section 2.1 (Dataset)
**Evidence pointer** Section 2.1
**Issue** The dataset is described as "non-redundant" based on MMseqs2 clustering at 90% and 95% sequence identity thresholds. However, the authors note that "only the light chains showed mild redundancy, forming 43–46 clusters" at these thresholds. It is unclear whether this mild redundancy could affect the statistical analysis, particularly for comparisons involving light chain-specific metrics.
**Required correction** Discuss whether the mild light chain redundancy could affect the results and whether any sensitivity analyses were performed (e.g., removing redundant light chains and re-running key comparisons).

**Concern ID** R1-m4
**Severity** Minor
**Axis** Interpretation / nuance
**Affected element** Section 4.1 (Discussion)
**Evidence pointer** Section 4.1
**Issue** The authors state that "AF3's strong performance on CDR-H3 is noteworthy because this hypervariable loop has traditionally been regarded as the regime in which antibody-specific models...would be expected to hold an advantage." However, they do not discuss the possibility that AF3's training data may include antibody structures that overlap with the test set, despite the temporal separation. The cutoff date (19 December 2023) ensures test structures were deposited after AF3's training cutoff, but AF3 may have been trained on other antibody structures that are structurally similar to the test set.
**Required correction** Acknowledge the limitation that temporal separation does not guarantee structural non-redundancy with training data, and discuss whether any additional measures were taken to assess potential training-test similarity (e.g., structural clustering against known AF3 training structures).

**Concern ID** R1-m5
**Severity** Minor
**Axis** Completeness
**Affected element** Section 2.5 (Statistical analysis)
**Evidence pointer** Section 2.5
**Issue** The authors use bootstrap resampling with 10,000 resamples to estimate 95% confidence intervals for group-level performance. However, they do not specify the bootstrap method (e.g., percentile, BCa, or basic bootstrap) or whether they accounted for the paired nature of the data in the bootstrap procedure.
**Required correction** Specify the bootstrap method used and confirm that the paired structure of the data was preserved during resampling.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical power), R1-M2 (methodological completeness), R1-M3 (selection bias), R1-M4 (reproducibility)

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The study provides a controlled comparison that is more rigorous than typical benchmarks, but the individual findings (AF3 outperforms antibody-specific tools, docking remains challenging) are largely consistent with existing literature. The multi-level evaluation framework is a strength but not entirely novel.
  - **Scientific importance**: Moderate to high. The practical guidance for tool selection is valuable for the antibody engineering community, and the identification of persistent limitations (CDR-H3 accuracy, fine-grained interface prediction) provides clear targets for method development.
  - **Interdisciplinary readership**: Moderate. The study is primarily of interest to computational biologists and antibody engineers. The methods and results are presented with sufficient clarity for nonspecialists in structural biology, but the narrow focus on antibody modeling limits broader appeal.
  - **Technical soundness**: Moderate. The experimental design is generally sound, but concerns about statistical power, selection bias, and methodological completeness reduce confidence. The statistical methods are appropriate but their application could be more rigorous.
  - **Readability for nonspecialists**: Good. The manuscript is well-structured with clear motivation, methods, and results. Technical terms are defined, and the figures (as described) appear to effectively communicate key findings. The Discussion provides helpful context and practical guidance.

- **Recommendation posture** Supportive if technical concerns are resolved. The study addresses a practical need and provides useful guidance, but the methodological concerns (particularly statistical power, exclusion of recent methods, and selection bias in the interface analysis) must be addressed before the conclusions can be considered robust. The authors should either strengthen the statistical analysis, include additional methods, or temper their claims to match the evidence provided.