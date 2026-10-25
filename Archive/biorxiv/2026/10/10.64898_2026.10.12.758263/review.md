## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the proposed method, experimental design, results, and claims. No assessment of code availability, reproducibility scripts, or peer review status.
- **Shared manuscript claim summary** The authors propose RA-GHN, a graph–hypergraph neural network for antibody CDR sequence–structure co-design. They claim state-of-the-art performance across sequence recovery, structure prediction, CDR-H3 generation, and affinity optimization, and introduce a new evaluation metric (SSDI) to balance structural reliability and sequence novelty.
- **Visible evidence base** Tables 1–3 (referenced), Figures 1–6 (referenced), ablation study, sensitivity analysis, dataset descriptions (SAbDab, RAbD, SKEMPI V2.0)
- **Missing materials affecting confidence** Actual table data, figure contents, baseline implementation details, statistical significance tests, hyperparameter search results, and any supplementary information were not provided. The manuscript text alone does not allow quantitative verification of the reported improvements.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant and timely problem in antibody design, and the proposed architecture is conceptually interesting. The combination of graph-based pairwise modeling with hypergraph-based higher-order interactions is a reasonable and potentially valuable direction. However, the evidence provided in the text is insufficient to fully evaluate the claims. Key quantitative results are referenced but not shown, and several methodological details are either underspecified or presented in a way that raises questions about rigor. The introduction of the SSDI metric is thoughtful, but its validation is incomplete. The manuscript would benefit from clearer reporting of experimental protocols, statistical analyses, and direct comparisons with baselines.

- **Who would be interested in the results, and why** Computational biologists, protein engineers, and researchers in machine learning for drug discovery would be interested. The work targets a practical problem (antibody CDR design) with a novel architectural contribution, and the proposed metric addresses a known evaluation gap. The results, if fully validated, could inform future generative models for antibody and protein design.

- **Major strengths**  
  1. The problem is well-motivated and practically important.  
  2. The architectural design is novel in its explicit combination of graph and hypergraph modeling with SE(3)-equivariance.  
  3. The introduction of SSDI as a composite metric is a useful conceptual contribution.  
  4. The ablation study and sensitivity analysis are appropriate and informative in principle.

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The manuscript claims that RA-GHN "significantly outperforms state-of-the-art baselines across standard benchmarks and affinity optimization tasks."  
  - **Evidence pointer** Tables 1–3, Section 5.1–5.3  
  - **Concern** The actual numerical results are not provided in the manuscript text. Tables are referenced but their contents are absent from the supplied material. Without the data, the central performance claims cannot be verified.  
  - **Why it matters** The core contribution of the paper is empirical. If the reported improvements are not shown, the case for the method's effectiveness is not established.  
  - **Resolution test** Provide the full tables with all baseline comparisons, including standard deviations and statistical significance tests (e.g., paired t-tests or confidence intervals).

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological rigor  
  - **Claim pointer** The authors state that the hypergraph construction is "biophysically grounded" and that the three hyperedge types capture "high-order cooperative effects."  
  - **Evidence pointer** Section 2.2, Algorithm 1  
  - **Concern** The biophysical justification for the hyperedge types is qualitative. No quantitative analysis is provided to show that these hyperedges actually capture meaningful cooperative effects beyond what pairwise graphs already encode. The choice of thresholds (e.g., δ_int = 6.0 Å, K_patch = 5, K_min, K_size) is described as "empirically set" but no sensitivity analysis for these parameters is shown.  
  - **Why it matters** The novelty of the method rests on the claim that hypergraphs add value over graphs. Without evidence that the hypergraph components contribute to performance, the architectural contribution is not substantiated.  
  - **Resolution test** Include an ablation that isolates the contribution of each hyperedge type, and report sensitivity to key hyperparameters.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evaluation metric validity  
  - **Claim pointer** The SSDI metric is introduced to "address the limitations of existing evaluation metrics, specifically the risks of folding hallucination and sequence overfitting."  
  - **Evidence pointer** Section 5.2, Table 2  
  - **Concern** The SSDI is defined as a harmonic mean of structural reliability and sequence novelty, but the manuscript does not provide a formal validation of this metric. It is unclear whether SSDI correlates with experimentally measured binding affinity or stability. The choice of the 2.0 Å threshold and the parameter k = 3 are not justified beyond a brief statement.  
  - **Why it matters** If SSDI is to be adopted by the community, it must be shown to be a reliable and discriminative metric. Without validation, its use as a primary evaluation criterion is questionable.  
  - **Resolution test** Provide a correlation analysis between SSDI and experimental or computational binding affinity measurements, and justify the threshold and steepness parameters with data.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Baseline fairness  
  - **Claim pointer** The authors compare against "state-of-the-art baselines" including LSTM, RefineGNN, HERN, DiffAb, AbDiffuser, MEAN, dyMEAN, RAAD, and ADesigner.  
  - **Evidence pointer** Section 4.4, Tables 1–3  
  - **Concern** The manuscript states that some baselines were extended (C-LSTM, C-RefineGNN, C-HERN) to provide full complex context, but the details of these extensions are not described. It is unclear whether the baselines were retrained under the same data splits, hyperparameter tuning protocols, and computational budgets.  
  - **Why it matters** Unfair or inconsistent baseline comparisons can lead to inflated performance claims.  
  - **Resolution test** Describe the exact training and evaluation protocols for all baselines, including any modifications, and ensure identical data splits and evaluation criteria.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Section 2.2, hyperedge construction  
  - **Evidence pointer** Section 2.2  
  - **Issue** The description of the hyperedge construction is dense and contains some typographical errors (e.g., "where x_u and x_v denote the three-dimensional atomic coordinates (e.g., Cα or side-chain centroids) of residues u and respectively" appears to be missing a variable).  
  - **Required correction** Proofread and clarify the mathematical definitions and variable names.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Section 4.3, implementation details  
  - **Evidence pointer** Section 4.3  
  - **Issue** The hyperparameter search is described as using the AutoML toolkit NNI, but the final selected values are not reported.  
  - **Required correction** Report the final hyperparameter values used for the reported results.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Statistical reporting  
  - **Affected element** Section 5.1, Table 1  
  - **Evidence pointer** Section 5.1  
  - **Issue** The manuscript reports results based on 10-fold cross-validation but does not state whether the reported metrics are averages, medians, or include variance.  
  - **Required correction** Report mean and standard deviation (or confidence intervals) for all metrics.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Interpretation  
  - **Affected element** Section 5.3, Table 3  
  - **Evidence pointer** Section 5.3  
  - **Issue** The affinity optimization results are reported as average ΔΔG values, but the units and the method of calculation (e.g., using which scoring function) are not specified.  
  - **Required correction** Specify the scoring function and the exact definition of ΔΔG used.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (missing quantitative results), R1-M2 (lack of evidence for hypergraph contribution), R1-M3 (unvalidated SSDI metric), R1-M4 (baseline fairness).

- **Assessment against Nature-style criteria**  
  - **Originality** The combination of graph and hypergraph modeling with SE(3)-equivariance for antibody design is a novel contribution. The SSDI metric is also a new idea. However, the originality is somewhat tempered by the fact that the individual components (equivariant GNNs, hypergraph networks) are established; the novelty lies in their integration.  
  - **Scientific importance** Antibody design is a high-impact area, and improving co-design methods is of clear practical value. If the claims are fully substantiated, the work could be important.  
  - **Interdisciplinary readership** The work sits at the intersection of machine learning, structural biology, and immunology. It would appeal to a broad readership if the presentation is accessible.  
  - **Technical soundness** The architecture is plausible, but the lack of quantitative evidence and incomplete methodological details prevent a full assessment of technical soundness.  
  - **Readability for nonspecialists** The manuscript is generally well-written but contains dense technical sections that may be challenging for nonspecialists. The abstract is clear, but the methods section assumes significant prior knowledge.

- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is interesting, but the manuscript as supplied does not contain the necessary quantitative results or methodological details to support the central claims. The authors should provide full tables, statistical analyses, and additional validation of the SSDI metric before the case can be made.

## Risk / unsupported claims
- The claim of "significant outperformance" over baselines is unsupported because the actual results are not provided.
- The claim that hypergraphs capture "high-order cooperative effects" is not empirically demonstrated.
- The SSDI metric is presented as a solution to evaluation limitations, but its validity is not established.
- The claim that RA-GHN generates "physically feasible and functionally innovative antibodies" is not supported by any experimental validation.
- The statement that the method "significantly reduces the risk of aggregation and instability" is speculative and not backed by data.