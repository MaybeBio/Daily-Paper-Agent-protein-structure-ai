## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a global competition, Bits to Binders, in which 12,000 de novo 80-amino acid minibinders targeting human CD20 were designed by teams from 42 countries and screened as CAR binding domains in T cells. Pooled CAR-T proliferation screening identified 707 designs with significant CD20-specific enrichment, with team hit rates ranging from 0.6% to 38.4%. Top candidates were validated individually for CD20-specific proliferation, expansion, cytokine production, and targeted cell lysis. The authors identify design methodologies and factors correlated with DNA synthesis, expression, and target-specific T cell activation, which when applied as a retrospective filter nearly double success rates. The dataset is released as an open resource with practical recommendations.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, methods, all figures and tables, statistical details, dataset description, and supplementary information; without these, quantitative claims and methodological rigor cannot be independently assessed

## Reviewer
- **Overall assessment** The abstract describes a large-scale, community-driven effort to evaluate AI-designed minibinders in a functional cellular context, which is a valuable and timely contribution. The scale of the dataset and the use of a functional readout (CAR-T proliferation) rather than binding affinity alone are notable strengths. However, the abstract alone provides insufficient detail to evaluate the rigor of the screening pipeline, the statistical methods used to define "significant" enrichment, the validation criteria, or the robustness of the retrospective filter. Several claims are plausible but currently not verifiable from the supplied material.
- **Who would be interested in the results, and why** Researchers in AI-driven protein design, computational biology, and immunotherapy would be interested. The dataset and recommendations could serve as a benchmark for de novo binder design and functional validation, and the competition format may inform future community-based evaluation efforts. Clinically oriented groups working on CAR-T therapies may also find the functional screening approach relevant.
- **Major strengths** The use of a functional cellular assay (CAR-T proliferation) as the primary screening readout is a meaningful advance over affinity-only evaluations. The scale of the competition (12,000 designs, 42 countries) provides a substantial dataset. The identification of design factors that correlate with functional success, and the release of the dataset as an open resource, are valuable contributions to the field.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The definition and statistical threshold for "significant CD20-specific enrichment" are not provided. The criteria for selecting "top-performing candidates" for individual validation are unclear. The nature and validation of the "retrospective filter" are not described, and the claim that it "nearly double[s] the success rates" requires statistical context. The relationship between the pooled screening results and the individual validation outcomes is not specified.
- **Assessment against Nature-style criteria** 
  - Originality: The competition format and the focus on functional screening in a therapeutic context are original relative to typical binder design evaluations, which emphasize affinity. However, the abstract does not clarify how the design methods or the analysis framework are novel beyond the scale.
  - Scientific importance: The potential to improve de novo binder design for functional applications is important, and the open dataset could be a significant community resource. The importance is currently plausible but not fully established from the abstract alone.
  - Interdisciplinary readership: The work bridges AI, protein engineering, and cellular immunotherapy, which should appeal to a broad readership. The abstract is written in accessible language, though some terms (e.g., "minibinders," "pooled CAR-T proliferation") may require prior knowledge.
  - Technical soundness: Not assessable from the abstract. The absence of methods, statistical details, and validation protocols prevents evaluation of technical rigor.
  - Readability for nonspecialists: The abstract is generally clear, but the significance of the hit rates and the retrospective filter would benefit from brief contextual explanation.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims are plausible and potentially valuable, but the abstract alone does not provide sufficient evidence to establish the case. A full review of the manuscript with methods and results is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "707 designs exhibiting significant CD20-specific enrichment, with team hit rates from 0.6% to 38.4%"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not define the statistical threshold or method used to determine "significant CD20-specific enrichment." It is unclear whether this was based on a fold-change cutoff, a statistical test, a false discovery rate, or another criterion. The wide range of team hit rates (0.6% to 38.4%) suggests variability in design quality, but without a clear definition of significance, the hit rate values are not interpretable.
- **Why it matters** The central quantitative claim of the competition depends on the definition of a "hit." If the threshold is arbitrary or overly permissive, the reported hit rates and the subsequent analysis of design factors could be misleading. The reproducibility of the screening pipeline also hinges on a transparent statistical framework.
- **Resolution test** Provide the exact statistical method, threshold, and multiple-testing correction used to define significant enrichment. Include a description of the control conditions and how CD20 specificity was established. Report the number of replicates and the variability of the screening assay.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and generalizability
- **Claim pointer** "Top-performing candidates were validated as individual constructs, measuring CD20-specific proliferation, expansion, cytokine production, and targeted cell lysis"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not specify how many candidates were selected for individual validation, what criteria defined "top-performing," or how the validation results compared to the pooled screening outcomes. It is also unclear whether the validation assays were performed in a consistent manner across candidates and whether the results were reproducible.
- **Why it matters** The transition from pooled screening to individual validation is a critical step in establishing that the screening approach reliably identifies functional binders. Without details on the selection criteria and the concordance between pooled and individual results, the validity of the screening pipeline is not established.
- **Resolution test** Report the number of candidates validated, the selection criteria, and the concordance between pooled enrichment and individual validation outcomes. Provide details on the assays, including controls, replicates, and statistical analysis of the validation data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data analysis and reproducibility
- **Claim pointer** "We identified common design methodologies and factors correlated with DNA synthesis, expression, and target-specific T cell activation which nearly double the success rates when applied as a retrospective filter"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not describe the nature of the "design methodologies and factors," how they were identified, or how the "retrospective filter" was constructed and applied. The claim that the filter "nearly double[s] the success rates" lacks statistical context, such as the baseline success rate, the confidence intervals, and whether the improvement was validated on an independent set of designs or only on the same data used to derive the filter.
- **Why it matters** The retrospective filter is presented as a practical recommendation, but if it is overfitted to the competition data, it may not generalize to future design efforts. The lack of methodological detail prevents assessment of the filter's robustness and utility.
- **Resolution test** Describe the specific factors and methods identified, the statistical approach used to correlate them with success, and the construction of the filter. Provide the baseline and filtered success rates with appropriate statistical measures, and report whether the filter was tested on held-out or independent data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "minibinders"
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "minibinders" is used without definition. It is unclear whether these are a specific class of de novo designed proteins or a general term for small binding proteins.
- **Required correction** Provide a brief definition or reference for "minibinders" in the abstract or introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Baseline comparison
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not state how the success rates of the competition designs compare to existing or conventional binder design approaches. Without a baseline, the significance of the reported hit rates is difficult to gauge.
- **Required correction** Include a brief comparison to prior de novo binder design efforts or to a standard benchmark, if available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Dataset description
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that the dataset is released as an open resource, but it does not specify the format, the level of annotation, or the access mechanism.
- **Required correction** Provide a brief description of the dataset contents, format, and how to access it.

## Risk / unsupported claims
- The claim that 707 designs exhibited "significant CD20-specific enrichment" is unsupported without a defined statistical threshold and control conditions.
- The claim that the retrospective filter "nearly double[s] the success rates" is unsupported without baseline rates, statistical context, and evidence of generalizability.
- The claim that "top-performing candidates" were validated is unsupported without specifying the number of candidates, selection criteria, and concordance with pooled results.
- The overall effectiveness of the competition in improving AI-driven binder design is not assessable from the abstract alone.