## Review setup
- **Input scope** Full manuscript text (abstract, introduction, overview, platform description, pipeline description, benchmarking, results, conclusions) and supplementary material reference list. No figures, tables, or supplementary files were provided.
- **Assessment boundary** Technical soundness of the described platform, validity of benchmarking claims, and adequacy of evidence for stated conclusions. No assessment of code functionality or reproducibility beyond what is described in text.
- **Shared manuscript claim summary** The authors present GDEE, an automated, modular Python platform for structure-based enzyme engineering and gene discovery. The platform integrates sequence generation, homology modeling (Modeller), docking (AutoDock Vina or Smina), and scoring, with optional machine learning-based re-scoring. The authors benchmark scoring functions on PDBBind v2020 and on 260 protein pairs, and report that a stacking ensemble metamodel outperforms individual scoring functions in affinity prediction, though its advantage diminishes within the full pipeline. The authors conclude that the most effective protocol is Vina for pose selection followed by ML re-scoring for affinity ranking.
- **Visible evidence base** Text descriptions of benchmarking procedures and results. Reference to Supporting Information Sections S1, S2, S3, S3.1, and Figures S5, S6, S16, S18. No actual data, figures, or tables were provided in the submitted material.
- **Missing materials affecting confidence** All figures, tables, and Supporting Information files. The manuscript references Figure 1 (platform architecture), Figure 2 (database schema), Figure 3 (scoring function success rates), Figure 4 (histograms and mutation analysis), Table 1 (metamodel weights), and multiple supplementary figures. None of these were available for review. The two published case studies referenced in the text were not provided.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful and extensible platform for structure-based enzyme engineering. The modular architecture and the integration of established tools (Modeller, AutoDock Vina, Smina) are sensible. The benchmarking effort, particularly the evaluation of ML scoring functions within the full pipeline context, addresses an important gap in the literature. However, the core claims regarding the platform's utility and the superiority of the proposed re-scoring approach are not verifiable from the provided material, as all quantitative results are contained in inaccessible figures and supplementary files. The reported performance of the best scoring function in the full pipeline (approximately 54% correct sign prediction) is modest and the authors appropriately acknowledge this limitation. The manuscript would benefit from clearer articulation of the novelty relative to existing enzyme engineering platforms and from a more critical discussion of the proxy relationship between binding affinity and catalytic efficiency.
- **Who would be interested in the results, and why** Researchers in enzyme engineering, protein engineering, and metabolic engineering who require accessible, automated tools for variant prioritization. Computational biologists developing or benchmarking scoring functions for protein-ligand interactions would also find the comparative evaluation of interest. The platform's modular design may appeal to groups seeking to integrate structure-based workflows into their own pipelines.
- **Major strengths** 1. The platform addresses a real bottleneck in enzyme engineering: the need for automated, high-throughput variant prioritization. 2. The modular, object-oriented architecture with MPI support for distributed computing is a practical design choice. 3. The benchmarking includes a realistic full-pipeline evaluation, not just isolated scoring function tests. 4. The authors are transparent about the limitations of binding affinity as a proxy for catalytic efficiency and about the modest performance in the full pipeline. 5. The integration of ML-based re-scoring as an optional, configurable step is a thoughtful addition.
- **Major Concerns** 1. The central quantitative claims are entirely unsupported in the provided material. All figures and tables are missing, making it impossible to assess the validity of the benchmarking results, the statistical significance of differences between scoring functions, or the claimed superiority of the metamodel. 2. The novelty of the platform relative to existing tools is not clearly established. The authors state that GDEE has been "developed for some years" and applied to published case studies, but the specific innovations or advantages over existing platforms are not articulated. 3. The relationship between the benchmarking results and the platform's practical utility is unclear. The reported 54% success rate in the full pipeline is barely above chance, and the authors do not provide a clear decision framework for how users should interpret and act on the platform's rankings. 4. The manuscript lacks a critical discussion of the assumptions underlying the platform, particularly the use of rigid-receptor docking and the proxy relationship between binding affinity and catalytic activity. 5. The description of the "gene discovery" mode is underdeveloped. The text mentions BLAST-based pre-selection but does not explain how the platform handles sequence diversity, phylogenetic relationships, or the risk of selecting orthologs with different catalytic mechanisms.
- **Minor Comments** 1. The abstract would benefit from a quantitative summary of the platform's performance. 2. The introduction could more explicitly position GDEE relative to other automated enzyme engineering platforms (e.g., Rosetta, PROSS, FuncLib). 3. The description of the "Vina error range" in the context of ΔΔG predictions is vague. The authors should specify what error range they refer to and how it was determined. 4. The statement that "binding affinity indicates how strongly an enzyme can bind to its target molecule" is trivially true but does not address the more relevant question of how binding affinity relates to catalytic efficiency for different types of reactions (e.g., substrate binding vs. product release). 5. The manuscript would benefit from a discussion of computational cost and runtime for typical use cases. 6. The authors mention "less successful outcomes" from case studies but do not describe what these were or what lessons were learned. 7. The conclusions section overstates the platform's capabilities relative to the evidence presented, particularly the claim that it can "rapidly identify and optimize enzyme variants" without quantitative evidence of speed or success rate.
- **Technical failings that need to be addressed before the case is established** 1. All quantitative benchmarking results are inaccessible. The authors must provide the actual data, figures, and statistical analyses. 2. The claim that the metamodel "outperformed all individual scoring functions" requires statistical testing (e.g., confidence intervals or significance tests) that is not described. 3. The full-pipeline evaluation is based on homology models, but the authors do not describe how model quality varies across the 187 reference proteins or whether model quality correlates with scoring performance. 4. The authors do not describe how the 260 protein pairs were selected or whether they represent a diverse and unbiased sample. 5. The manuscript does not specify how the "success" criterion (correct sign of ΔΔG) accounts for the magnitude of the predicted effect. A method that correctly predicts a tiny positive ΔΔG is counted the same as one that correctly predicts a large positive ΔΔG.
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of existing tools into an automated pipeline is useful but not conceptually novel. The benchmarking of ML scoring functions within a full enzyme engineering pipeline is a valuable contribution. Scientific importance: Moderate. The platform addresses a practical need, but the modest performance in the full pipeline limits its immediate impact. Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational enzymologists and protein engineers. Technical soundness: Not assessable from the provided material. The benchmarking methodology is described, but the results are not visible. Readability for nonspecialists: Acceptable. The text is generally clear, though some sections assume familiarity with docking and scoring terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a potentially useful platform, but the core quantitative claims cannot be evaluated without the missing figures, tables, and supplementary material. The authors should be invited to resubmit with the complete data and with additional analysis addressing the concerns above.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The manuscript claims that the stacking ensemble metamodel outperforms all individual scoring functions in affinity prediction, and that the best individual function (Rf-Score v2) achieves approximately 72% success in predicting mutation effects on binding from X-ray structures.
- **Evidence pointer** Figures 3, 4, Table 1, Supporting Information Figures S5, S6, S16, S18. Location not provided.
- **Concern** All quantitative results supporting the central claims are contained in figures and tables that were not provided for review. Without access to the actual data, it is impossible to verify the reported performance metrics, assess the statistical significance of differences between scoring functions, or evaluate the validity of the benchmarking methodology.
- **Why it matters** The manuscript's contribution rests on the claim that the proposed re-scoring approach improves prediction accuracy. If the underlying data are not available, the scientific community cannot assess the reliability of these claims or reproduce the results.
- **Resolution test** Provide all figures, tables, and supplementary material. Include statistical analyses (e.g., confidence intervals, significance tests) for the reported performance differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript states that the platform "finds and optimizes enzymes responsible for rate-limiting steps in biosynthetic pathways" and that it has been applied to multiple case studies with "several successes."
- **Evidence pointer** Introduction, Conclusions. Location not provided.
- **Concern** The manuscript references two published case studies but does not describe them in any detail. The claim that the platform can identify rate-limiting steps and optimize enzymes for real biosynthetic pathways is not supported by any in-text results or case study descriptions. The "less successful outcomes" are mentioned but not described.
- **Why it matters** The practical utility of the platform depends on demonstrated success in real applications. Without case study details, the reader cannot assess whether the platform works in practice or only in retrospective benchmarks.
- **Resolution test** Include a dedicated case study section with at least one fully described application, including the biological problem, the enzyme targets, the mutations proposed, and the experimental validation results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** The manuscript states that "binding affinity indicates how strongly an enzyme can bind to its target molecule" and uses predicted binding affinity as a proxy for catalytic efficiency.
- **Evidence pointer** Introduction, Overview. Location not provided.
- **Concern** The relationship between binding affinity and catalytic efficiency is complex and reaction-dependent. For some enzymes, strong substrate binding can reduce catalytic turnover. The manuscript acknowledges this limitation in the Introduction but does not discuss how the platform's rankings should be interpreted given this complexity. The benchmarking evaluates the ability to predict binding affinity changes, not catalytic improvements.
- **Why it matters** Users of the platform may misinterpret improved predicted binding as improved catalytic performance. The manuscript should provide clearer guidance on the scope and limitations of the platform's predictions.
- **Resolution test** Add a discussion section that explicitly addresses the conditions under which binding affinity is a reliable proxy for catalytic efficiency and provide guidance on when the platform's predictions should be treated with caution.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** The manuscript describes the full-pipeline evaluation using 260 protein pairs and reports that the best scoring function achieves approximately 54% correct sign prediction for mutation effects on binding.
- **Evidence pointer** Figure 3, Supporting Information Section S2. Location not provided.
- **Concern** The reported success rate of approximately 54% is barely above random chance (50%). The authors acknowledge this is "modest" but do not discuss whether this level of accuracy is practically useful for enzyme engineering. A 54% success rate means that nearly half of the prioritized variants would be expected to have the opposite effect on binding.
- **Why it matters** The practical value of the platform depends on whether its rankings are sufficiently accurate to reduce the experimental burden. A 54% success rate provides minimal advantage over random selection.
- **Resolution test** Provide a more detailed analysis of the distribution of predicted ΔΔG values, including the magnitude of correctly and incorrectly predicted effects. Discuss the practical implications of the observed accuracy for experimental prioritization.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract. Location not provided.
- **Issue** The abstract states that the platform "finds and optimizes enzymes responsible for rate-limiting steps in biosynthetic pathways" but does not explain how the platform identifies rate-limiting steps. This is a significant claim that is not elaborated in the main text.
- **Required correction** Clarify in the abstract or introduction how the platform identifies rate-limiting steps, or revise the claim to reflect the platform's actual scope.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods description
- **Evidence pointer** GDEE Platform section. Location not provided.
- **Issue** The manuscript states that GDEE is "developed as a Python package" but does not provide information on availability, versioning, or installation instructions. No repository or documentation link is given.
- **Required correction** Provide a statement on software availability, including a repository URL or distribution channel, and specify the supported Python versions and dependencies.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Benchmarking description
- **Evidence pointer** Re-scoring of Docking Poses with Machine Learning Scoring Functions section. Location not provided.
- **Issue** The manuscript states that the PDBBind v2020 refined set was used for benchmarking but does not specify the data split methodology beyond referencing a "leak-proof split version." The criteria for the leak-proof split are not described.
- **Required correction** Describe the leak-proof split criteria in the main text or provide a reference to the original publication describing this split.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results discussion
- **Evidence pointer** Stacking Ensemble of Scoring Models section. Location not provided.
- **Issue** The manuscript reports that the metamodel achieved higher R² but comparable MSE to Rf-Score v2, and that its performance was "within the error range" of Rf-Score v2. The practical significance of the R² improvement is not discussed.
- **Required correction** Discuss whether the R² improvement translates into meaningful differences in variant prioritization, given the comparable MSE.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction
- **Evidence pointer** Introduction. Location not provided.
- **Issue** The term "gene discovery" is used to describe the identification of natural enzyme variants with improved binding. This terminology is potentially confusing, as "gene discovery" typically refers to identifying genes associated with phenotypes or functions, not to screening natural variants of a known enzyme.
- **Required correction** Consider using a more precise term such as "natural variant screening" or "ortholog discovery" to avoid confusion.

## Risk / unsupported claims
- The claim that GDEE "finds and optimizes enzymes responsible for rate-limiting steps in biosynthetic pathways" is unsupported by any in-text evidence or case study description.
- The claim that the platform has been applied to "multiple case studies, with several successes" is unsupported, as no case study details are provided.
- The reported performance metrics (e.g., 72% success for Rf-Score v2 on X-ray structures, 54% in the full pipeline) cannot be verified without the missing figures and tables.
- The claim that the metamodel "outperformed all individual scoring functions" is unsupported without statistical testing.
- The statement that the platform "significantly enhances the accuracy of predicting the effect of mutations on binding" (from the abstract) is not supported by the reported full-pipeline results, which show only modest improvement over chance.
- The relationship between predicted binding affinity and catalytic efficiency is acknowledged as a proxy but the limitations of this proxy are not adequately discussed in the context of the platform's practical utility.