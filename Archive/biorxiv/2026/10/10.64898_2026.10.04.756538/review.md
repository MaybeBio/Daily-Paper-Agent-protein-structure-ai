## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods) as provided
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact general audience
- **Shared manuscript claim summary** The authors present CHORUS, a sequence-only deep learning framework that predicts residue-level protein-protein interaction (PPI) interfaces in alpha-helical transmembrane proteins. The method uses an ensemble of six predictors spanning three protein language model families and three neural architectures, and is claimed to outperform 18 existing methods on a large independent test set. The authors also present a proteome-scale atlas of predictions for 80,619 reviewed transmembrane proteins.
- **Visible evidence base** Abstract, Results sections (narrative only, no figures or tables visible), Methods sections, supplementary table references
- **Missing materials affecting confidence** All figures, all supplementary tables, all supplementary figures, benchmark dataset details, training/validation/test split compositions, hyperparameter tables, and the actual web resource contents

## Reviewer

- **Overall assessment** This manuscript presents a potentially valuable contribution to the field of membrane protein interaction prediction. The core idea of leveraging cross-pLM ensemble diversity for sequence-only interface prediction is timely and the reported performance gains are notable. However, the manuscript as provided is incomplete in critical ways. The Results section is presented as narrative without any of the referenced figures or tables, making it impossible to verify the central claims. The methods are described in detail, but key validation steps, ablation study results, and statistical comparisons cannot be assessed. The claims of superiority over 18 existing methods rest entirely on data that are not visible. The proteome-scale atlas is a significant resource claim, but its utility and quality cannot be evaluated from the provided material. The manuscript has potential, but the evidence base is insufficient for a definitive assessment.

- **Who would be interested in the results, and why** Computational biologists working on protein-protein interaction prediction, particularly those focused on membrane proteins, would be the primary audience. Researchers studying membrane protein structure, function, and assembly would also find the atlas resource valuable. The methodological approach of cross-pLM ensembling may interest the broader deep learning for biology community. The potential application to allosteric drug design targeting membrane proteins could attract pharmaceutical researchers. The work addresses a genuine gap, as membrane protein interfaces remain poorly characterized compared to soluble proteins.

- **Major strengths**
  1. The problem is well-motivated and important. Membrane protein interactions are understudied and experimentally challenging.
  2. The sequence-only, partner-agnostic formulation is elegant and practically useful, removing dependencies on structures, MSAs, and partner identification.
  3. The systematic exploration of the pLM family-layer-architecture space is methodologically sound and thorough.
  4. The construction of a large, leakage-controlled benchmark with strict sequence identity thresholds is commendable.
  5. The proteome-scale atlas is a potentially valuable community resource.
  6. The biological analyses (BioLiP orthogonality, FunFam conservation) address important questions about what the model actually learns.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** "CHORUS outperforms 18 established sequence- and structure-based methods across 4,655 homology-isolated test contexts (average precision: 0.643)"
  - **Evidence pointer** Figure 3, Supplementary Tables 10 and 11, location not provided
  - **Concern** The central performance claim cannot be verified. The manuscript references Figure 3 and supplementary tables for the benchmark comparison, but none of these are visible in the provided material. The comparison methodology, the specific configurations of the 18 baseline methods, the statistical significance of the 0.030 improvement over ScanNet-MSA, and the handling of methods with incomplete coverage are all unassessable.
  - **Why it matters** This is the core claim of the paper. Without the actual benchmark results, the reader cannot determine whether CHORUS genuinely advances the state of the art or whether the improvement is marginal, method-specific, or an artifact of evaluation choices.
  - **Resolution test** Provide the full benchmark results table with per-method AP, AUROC, F1, MCC values, coverage statistics, and confidence intervals. Show the PR and ROC curves for all methods. Detail the exact input configurations for each baseline method and justify any deviations from their native pipelines.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** "an optimal ensemble that systematically synthesizes complementary latent representations extracted across different model families (ESM-2, ESM-C, and ProtT5) and layer depths"
  - **Evidence pointer** Figure 2, Supplementary Figures 1 and 2, Supplementary Tables 1-9, location not provided
  - **Concern** The ensemble construction and its claimed optimality are not demonstrated. The selection of the six constituent models (two per family) is described as based on validation performance, but the full 57-model comparison, the ablation studies, and the control experiments (random seeds, coordinate transforms, depth variations, uniform duplication) are all referenced but not visible. The claim that cross-family diversity provides orthogonal value beyond intra-family variation requires the actual ablation data.
  - **Why it matters** The methodological contribution of the paper rests on the demonstration that cross-pLM ensembling is superior to simpler alternatives. Without the ablation and control data, the reader cannot determine whether the performance gain comes from ensembling per se, from the specific model choices, or from increased parameter count.
  - **Resolution test** Show the full 57-model performance landscape, the ablation results for each control condition, the pairwise model correlation matrix, and the leave-one-out ensemble results. Demonstrate that the six-model ensemble is statistically superior to each control.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** External validation
  - **Claim pointer** "we first evaluated CHORUS on three established benchmarks specialized for transmembrane proteins: CompData101 (101 chains), TestData36 (36 chains), and IndepData30 (30 chains)"
  - **Evidence pointer** Supplementary Tables 12 and 13, location not provided
  - **Concern** The external validation results are not visible. The retraining protocol (excluding sequences with ≥30% identity to external sets) is described, but the actual performance numbers, the comparison to published results on these benchmarks, and the behavior of the model under the retrained versus released weights are all unassessable.
  - **Why it matters** External benchmarks are critical for establishing generalizability beyond the internal test split. The choice of these specific benchmarks, their overlap with the training data, and the performance relative to published baselines on these datasets are essential for contextualizing the method's contribution.
  - **Resolution test** Provide the full external benchmark results with per-dataset AP, AUROC, and comparison to published state-of-the-art on these specific benchmarks. Clarify the overlap between external benchmarks and training data.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretation
  - **Claim pointer** "CHORUS-predicted interaction sites do not preferentially overlap annotated protein-ligand binding sites" and "modest but reproducible association between predicted PPI sites and evolutionary conservation"
  - **Evidence pointer** Supplementary Figure 1, Figure 6, location not provided
  - **Concern** The biological analyses are described in the text but the results are not visible. The BioLiP orthogonality analysis and the FunFam conservation analysis are important for establishing that the model learns PPI-specific features rather than generic binding-site or conservation signals. The observed-to-expected ratios and their confidence intervals are stated in text but the underlying distributions, the sensitivity analyses, and the robustness of these findings cannot be evaluated.
  - **Why it matters** These analyses address the interpretability and specificity of the model. They are important for convincing readers that the model captures genuine PPI interface properties and for guiding future applications.
  - **Resolution test** Show the full distributions of observed and expected overlaps, the bootstrap confidence intervals, the stratification by membrane region, and the sensitivity of results to thresholds and annotation sources.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Resource validation
  - **Claim pointer** "we deliver the CHORUS Atlas, providing precomputed, residue-resolved interaction landscapes for 80,619 reviewed transmembrane proteins spanning 4,918 species and 33.7 million residues"
  - **Evidence pointer** Figure 8, Supplementary Table 15, web resource, location not provided
  - **Concern** The atlas is a major deliverable but its quality and utility cannot be assessed. The validation of atlas predictions against known complexes, the consistency of predictions across homologous proteins, the handling of isoforms and fragments, and the practical usability of the web interface are all unverifiable from the provided material.
  - **Why it matters** A proteome-scale resource must be reliable and usable. Errors in the atlas could propagate to many downstream studies. The validation of the atlas as a resource is as important as the validation of the underlying model.
  - **Resolution test** Provide case studies of known complexes with experimental interface data, show consistency checks across homologous proteins, and demonstrate the web interface functionality.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract states "amplified predictive capacity within the lipid-embedded core (0.746)" but does not specify the comparison baseline for this amplification. Is this the same metric (AP) as the overall result? What is the comparable value for the best baseline method in this region?
  - **Required correction** Clarify the metric and provide the baseline comparison in the abstract or specify that full details are in the results.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, Dataset construction
  - **Evidence pointer** Methods, location not provided
  - **Concern** The dataset construction section mentions filtering based on sequence coverage and identity but does not specify the exact thresholds for excluding structures with poor quality or the criteria for selecting representative chains from multi-chain complexes.
  - **Required correction** Provide the exact filtering thresholds and the criteria for chain selection in the dataset construction.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, Optimization
  - **Evidence pointer** Methods, location not provided
  - **Concern** The learning rate is described as "constant" but the specific value is not stated in the text. The batch size and number of training steps are also not explicitly given.
  - **Required correction** Provide the exact learning rate, batch size, and training duration in the optimization section or in a hyperparameter table.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, Performance evaluation
  - **Evidence pointer** Results, location not provided
  - **Concern** The manuscript reports point estimates for AP and other metrics but does not describe the variability across the 55 test clusters. The cluster bootstrap is mentioned in Methods but the resulting confidence intervals are not reported in the Results text.
  - **Required correction** Report confidence intervals for the main performance metrics and for the comparison to baseline methods.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results, External validation
  - **Evidence pointer** Results, location not provided
  - **Concern** The text mentions 15 general-protein datasets or docking views from literature but does not describe the results on these datasets in the Results section.
  - **Required correction** Either report the results on these additional datasets or clarify that they are only used in supplementary analyses.

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Accessibility
  - **Affected element** Atlas
  - **Evidence pointer** Data availability, location not provided
  - **Concern** The atlas URL is provided but there is no description of the download options, API access, or licensing terms for the resource.
  - **Required correction** Add a description of the atlas access options, including bulk download and any programmatic access.

- **Technical failings that need to be addressed before the case is established**
  1. The central benchmark comparison (R1-M1) is not visible and must be provided in full.
  2. The ensemble construction and ablation studies (R1-M2) are not visible and must be provided.
  3. The external validation results (R1-M3) are not visible and must be provided.
  4. The biological analyses (R1-M4) are not visible and must be provided.
  5. The atlas validation (R1-M5) is not visible and must be provided.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of cross-pLM ensemble diversity for membrane protein interface prediction is a reasonable extension of existing work, but the field is moving rapidly and the specific contribution needs to be positioned against recent developments. The partner-agnostic formulation is not entirely new, but the systematic exploration of the model space is thorough. The originality is moderate and depends on the demonstrated performance gains.
  - **Scientific importance** Membrane protein interactions are of high biological and therapeutic importance. A reliable sequence-only predictor would be valuable. The atlas resource could be impactful. However, the importance is contingent on the demonstrated reliability and utility of the predictions.
  - **Interdisciplinary readership** The topic bridges computational biology, structural biology, and membrane biochemistry. The writing is accessible to a computational audience but may be dense for experimentalists. The potential applications to drug discovery broaden the appeal.
  - **Technical soundness** The methodological framework is well-conceived, with careful attention to data leakage, cluster-based evaluation, and ensemble construction. However, the technical soundness cannot be fully assessed without the missing results. The statistical methods described are appropriate, but their application cannot be verified.
  - **Readability for nonspecialists** The abstract is clear and the motivation is well-articulated. The Results section is dense and assumes familiarity with PPI prediction methods. The manuscript would benefit from a figure that visually summarizes the workflow and key results for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript has a sound methodological framework and addresses an important problem, but the central claims cannot be verified without the missing figures, tables, and supplementary materials. The authors should be invited to resubmit with the complete evidence base. If the benchmark results, ablation studies, and external validations support the claims as stated, the work could be a valuable contribution. The decision should be reconsidered after the full evidence is available.