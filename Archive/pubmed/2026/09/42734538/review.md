## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statements. Figures and tables are referenced but not provided. Supplementary materials are referenced but not provided.
- **Assessment boundary** The scientific content, methodology, statistical analyses, and conclusions as presented in the text. Assessment is limited by the absence of figures, tables, and supplementary information.
- **Shared manuscript claim summary** The authors evaluate nine protein structure comparison scores (RMSD, TM-score, GDT, lDDT, SphereGrinder, QCS, CAD, FlexE, MolProbity) applied to MD simulation outputs, finding high redundancy among reference-based scores, proposing that one global and one local score suffice for most applications, and reporting that the Amber ff19sb force field yields systematically different (higher-similarity) scores than CHARMM36m-based setups.
- **Visible evidence base** Text descriptions of results including correlation coefficients, PCA variance percentages, R² values for score combinations, within-protein versus between-protein variability percentages, and statistical test outcomes. Specific numerical values are reported for key findings.
- **Missing materials affecting confidence** All figures and tables, all supplementary information sections (S1–S8), the data repository contents, and the Jupyter notebooks. These are essential for verifying statistical claims, distribution shapes, PCA loadings, and the trajectory analysis.

## Reviewer

- **Overall assessment** This manuscript addresses a practical and timely question in computational structural biology: which protein structure comparison metrics are redundant, and which combinations are most informative for MD simulation analysis. The study design is sensible, the dataset is substantial (268 proteins, 1 μs simulations), and the analysis pipeline is clearly described. The finding that reference-based scores are highly correlated for MD-generated structures, consistent with prior observations for prediction models, is useful and credible. The force-field comparison, while limited in scope, provides a valuable cautionary observation. However, the manuscript has several weaknesses that need to be addressed. The statistical framework for selecting "optimal" score combinations is somewhat circular, the treatment of MolProbity as a distinct information source is underdeveloped, the force-field comparison is confounded by multiple simultaneous parameter changes, and the practical recommendations are not sufficiently qualified. The writing is generally clear but the manuscript would benefit from more precise language around causal claims. The work is likely of interest to practitioners in MD simulation and structural bioinformatics, though its novelty is incremental rather than transformative.

- **Who would be interested in the results, and why** Researchers who use MD simulations to study protein conformational changes, particularly those working in high-throughput settings or developing automated analysis pipelines, would find this work directly useful. The recommendation that one global and one local score suffice could simplify analysis workflows. Developers of structure comparison tools and scoring functions may also be interested in the redundancy analysis. The force-field comparison results are relevant to anyone choosing between Amber ff19sb and CHARMM36m for protein simulations. The work may also be of interest to the CASP community, given the overlap in scoring metrics.

- **Major strengths** The study addresses a practical question with a reasonably large and diverse dataset. The analysis is systematic, covering distribution shapes, pairwise correlations, PCA, predictive modeling, and statistical testing. The inclusion of MolProbity as a quality metric distinct from reference-based comparison scores is thoughtful. The authors are appropriately cautious about the limitations of their force-field comparison and acknowledge the need for further work. The data and code availability statement is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The authors claim that "one global score (or QCS), one local score, and FlexE together capture the maximum information contained across all scores" and that "a combination of one global and one local score is sufficient for most practical applications."
- **Evidence pointer** Section "Selection of Optimal Score Combinations", Figure 3 (not provided), Tables 1–3 (not provided)
- **Concern** The selection of "optimal" score combinations is based on predicting the remaining scores using ordinary least squares regression. This approach is inherently circular: the best predictors are those most correlated with the other scores, which is a mathematical consequence of the correlation structure rather than an independent measure of information content. The claim that a particular combination "captures the maximum information" is therefore tautological. Furthermore, the choice of R² as the criterion, and the decision to focus on R²_all rather than R²_pred, needs justification. The authors do not discuss whether the goal is to reconstruct all scores (which favors redundant, highly correlated scores) or to capture distinct structural features (which would favor diverse scores). The practical recommendation that "one global and one local score is sufficient" is a reasonable heuristic, but it is not directly supported by the analysis as presented.
- **Why it matters** The central practical recommendation of the paper rests on this analysis. If the statistical framework is circular or the criterion is not aligned with the stated goal, the recommendation may be misleading. Practitioners may adopt a reduced score set based on this work, so the basis for the recommendation must be sound.
- **Resolution test** The authors should clarify the objective of the score combination analysis. If the goal is to predict all scores from a subset, they should justify why this is the relevant objective. If the goal is to capture distinct structural information, they should use a different criterion, such as the variance explained in the original score space or the ability to distinguish known conformational states. They should also report the performance of all possible pairs and triples, not just the best and worst, and discuss the distribution of performance across combinations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and confounding
- **Claim pointer** The authors claim that "the setup using the Amber ff19sb force field yields systematically different scores than all CHARMM36m-based setups" and suggest that "the force field itself might be the dominant factor."
- **Evidence pointer** Section "Comparison of Scores across Simulation Setups", Figure 4 (not provided), Figure 5 (not provided), Table 4 (not provided)
- **Concern** The four simulation setups differ in multiple parameters simultaneously: force field (CHARMM36m vs Amber ff19sb), van der Waals treatment (force-switch vs potential-switch vs potential-shift), and water model (CHARMM TIP3P vs TIP4P vs OPC). The authors acknowledge this confounding but do not adequately address it. The claim that "the force field itself might be the dominant factor" is speculative and not supported by the experimental design. To isolate the force-field effect, one would need to vary the force field while holding the vdW treatment and water model constant, or use a factorial design. The authors state that their goal is not to "pinpoint the exact origins of any observed discrepancies," but the claim about the force field being dominant goes beyond what the data can support.
- **Why it matters** The force-field comparison is a secondary but potentially influential finding. If readers interpret this as evidence that Amber ff19sb produces different conformational ensembles than CHARMM36m, they may make choices about force-field selection based on this work. The confounding makes such an interpretation unsupported.
- **Resolution test** The authors should either (a) soften the claim to state that the A19sb setup, which differs in force field, vdW treatment, and water model, yields different scores, without attributing the difference to any single factor, or (b) perform additional simulations that isolate the force-field effect, or (c) provide a clear argument, based on prior literature or additional analysis, for why the force field is likely the dominant factor.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of MolProbity results
- **Claim pointer** The authors state that "MolProbity exhibits a distinct pattern, showing no meaningful correlation with any other score" and later argue that "MolProbity is primarily useful as a rapid sanity check and during the development of new force fields, but provides limited additional value when evaluating simulations performed with established force fields."
- **Evidence pointer** Section "Correlation between Scores", Section "Discussion and Conclusions"
- **Concern** The lack of correlation between MolProbity and reference-based scores is interpreted as evidence that MolProbity captures unique information, but the authors then conclude that this unique information is of limited value. This interpretation is not well justified. The high within-protein variability of MolProbity (39.2% of total variability) suggests that MolProbity may be noisy rather than informative. However, the authors do not explore whether the MolProbity subscores (clash score, Ramachandran outliers, etc.) might be differentially informative, or whether MolProbity might be more useful for detecting specific types of structural problems rather than global conformational changes. The conclusion that MolProbity has "limited additional value" is presented without a clear framework for what "value" means in this context.
- **Why it matters** The authors are making a recommendation about whether practitioners should include MolProbity in their analysis pipelines. This recommendation should be based on a clear understanding of what MolProbity measures and when it might be useful, not just on its correlation with other scores.
- **Resolution test** The authors should either provide a more nuanced discussion of when MolProbity might be informative (e.g., for detecting local structural distortions that do not affect global scores), or present additional analysis of the MolProbity subscores, or temper their conclusion about its limited value.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The authors state that "two and three scores account for up to 79.3% and 86.6% of the total variance" and recommend that "a combination of one global and one local score is sufficient for most practical applications."
- **Evidence pointer** Section "Selection of Optimal Score Combinations", Section "Discussion and Conclusions"
- **Concern** The analysis is based on 268 proteins simulated for 1 μs each, with scores computed only on the final snapshot. The generalizability of the findings to other simulation lengths, other protein types, or other scoring protocols is not discussed. The authors note that a trajectory-based analysis is beyond the scope of the study, but the practical recommendation is made without qualification regarding the temporal dimension. It is possible that different scores are more or less informative at different stages of a simulation, or that the redundancy structure changes over time.
- **Why it matters** The practical recommendation is intended for use in MD simulation analysis, which is inherently temporal. If the redundancy structure is time-dependent, the recommendation may not hold for analyses that consider trajectories rather than endpoints.
- **Resolution test** The authors should either qualify their recommendation to apply specifically to endpoint analysis, or provide some evidence (even preliminary) that the redundancy structure is stable over time, or discuss the limitations of their endpoint-only analysis more explicitly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section "Comparison of Scores across Simulation Setups"
- **Evidence pointer** Text: "We manually selected 31 proteins with diverse properties from Set268, simulated them with the four simulation setups C36m, C36mPs3P, C36mPs3P, and A19sb"
- **Issue** There is a typographical error: "C36mPs3P" is listed twice. The second instance should presumably be "C36mPs4P" based on the setup descriptions in the Methods section.
- **Required correction** Correct the typo to read "C36m, C36mPs3P, C36mPs4P, and A19sb".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section "Friedman and Post-Hoc Wilcoxon Signed-Rank Test"
- **Evidence pointer** Text: "The Friedman tests are significant for every score except RMSD and MolProbity"
- **Issue** The authors report significance but do not provide effect sizes or the magnitude of the differences. Given that the differences between setups are described as "relatively small," it would be helpful to report the actual p-values and, more importantly, the magnitude of the differences in a standardized metric.
- **Required correction** Report the p-values (or a range) and provide a measure of effect size, such as the median difference or a standardized effect size, to help readers assess the practical significance of the findings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "Data and Software Availability"
- **Evidence pointer** Text: "The following data are available in the repository https: 10.18419/DARUS-5853"
- **Issue** The URL appears to be malformed. It reads "https: 10.18419/DARUS-5853" which is not a valid URL format. It should likely be "https://doi.org/10.18419/DARUS-5853" or similar.
- **Required correction** Correct the URL format to ensure the repository is accessible.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of PCA
- **Affected element** Section "Principal Component Analysis of Reference-Based Scores"
- **Evidence pointer** Text: "the first PC explains a predominant proportion of the total variance (78.9%)"
- **Issue** The authors do not discuss the interpretation of the first principal component. Given that all scores load similarly on PC1, this component likely represents an overall "similarity" factor. The authors should state this interpretation explicitly, as it is central to their claim that scores are redundant.
- **Required correction** Add a sentence interpreting PC1 as a general similarity factor and discuss the implications for score redundancy.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section "Introduction"
- **Evidence pointer** Text: "a study by Olechnovič et al. showed for a slightly different set of scores that they are highly correlated with Spearman's rank correlation coefficients of 0.7 or higher based on data from CASP10–12"
- **Issue** The authors do not discuss how their findings extend or differ from this prior work beyond noting consistency. A more explicit comparison would help position the novelty of the current study.
- **Required correction** Add a sentence or two discussing the specific similarities and differences between the current findings and those of Olechnovič et al., particularly regarding the recommended score combinations.

- **Technical failings that need to be addressed before the case is established** The primary technical issue is the confounding in the force-field comparison, which prevents the authors from making the claim that "the force field itself might be the dominant factor." This claim is not supported by the experimental design. Additionally, the circularity in the score combination selection needs to be addressed by clarifying the objective of the analysis. The absence of figures and tables in the provided material prevents full verification of the statistical claims, but the text descriptions are generally consistent.

- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The question of score redundancy has been partially addressed in the protein structure prediction literature, but the application to MD simulation outputs and the systematic comparison of force-field effects on scores is a useful extension. The work is not conceptually novel but fills a practical gap.  
  *Scientific importance*: Moderate. The findings are useful for practitioners but do not fundamentally change our understanding of protein structure comparison or MD simulation. The recommendation to use one global and one local score is practical but not transformative.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to computational structural biologists and MD simulation practitioners. The methods and findings are unlikely to attract readers from outside these fields.  
  *Technical soundness*: Generally sound with caveats. The statistical methods are appropriate for the questions asked, but the confounding in the force-field comparison and the circularity in the score selection analysis are concerns. The dataset is substantial and the analysis is systematic.  
  *Readability for nonspecialists*: The manuscript is written in a clear and accessible style. The introduction provides sufficient context, and the methods are described in a way that is understandable to a broad scientific audience. The use of acronyms is heavy but standard for the field.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a useful question with a substantial dataset and generally sound methodology. The main issues are the confounding in the force-field comparison, which requires either additional experiments or softened claims, and the circularity in the score combination analysis, which requires clarification of the objective. If these are addressed, the manuscript would be a valuable contribution to the field. The practical recommendations, while needing qualification, are likely to be useful to practitioners.

## Risk / unsupported claims
- The claim that "the force field itself might be the dominant factor" in explaining score differences between A19sb and CHARMM36m-based setups is unsupported due to confounding with vdW treatment and water model changes.
- The claim that "one global score (or QCS), one local score, and FlexE together capture the maximum information contained across all scores" is circular given the OLS-based selection criterion.
- The claim that "a combination of one global and one local score is sufficient for most practical applications" is a reasonable heuristic but is not directly supported by the analysis, which does not establish what "sufficient" means in terms of capturing relevant structural information.
- The statement that "MolProbity is primarily useful as a rapid sanity check and during the development of new force fields, but provides limited additional value when evaluating simulations performed with established force fields" is an interpretation that goes beyond the presented data, as the authors do not demonstrate what "value" means in this context.
- The generalizability of the findings to trajectory-based analysis is not established, as only final snapshots were analyzed.