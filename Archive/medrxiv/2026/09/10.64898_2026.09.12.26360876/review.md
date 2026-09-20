## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, supplementary information, and data/code availability statements
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and completeness of evidence as presented in the provided material
- **Shared manuscript claim summary** The authors present a systematic mapping and bibliometric analysis of 4,143 PubMed-indexed publications (2015–2025) on AI-based synthetic data in biomedicine, using a combination of expert annotation and LLM-assisted classification across five facets (paper type, medical domain, synthetic data type, practicality, stance). They report continuous growth in publication volume, dominance of medical imaging (37.8%), a strong positive stance distribution (77.8% strongly supportive, <1% critical), a concentration of high citation impact in molecular/pharmaceutical applications, and only 27 papers reporting operational use. They interpret these findings as evidence of a translation gap and propose theoretical explanations based on invariance structures across data modalities.
- **Visible evidence base** Abstract; full main text sections (Motivation and contributions, Results, Discussion, Methods); supplementary information on facet definitions, inter-rater reliability, and top cited papers; data availability and code availability statements
- **Missing materials affecting confidence** Figures 1–6 are referenced but not provided; Table 1 (facet definitions), Table 3 (facet full list), Table 4 (bootstrap test results), and Table 5 (top cited papers) are referenced but not shown; Supplementary Material is referenced but not provided; the full search query string is described but not reproduced verbatim; the annotation guidelines are summarized but not fully detailed

## Reviewer

### Overall assessment
This manuscript addresses a timely and important question: to what extent has AI-based synthetic data translated from methodological development into practical biomedical application? The authors have assembled a substantial corpus and applied a novel combination of expert annotation and LLM-assisted classification. The core descriptive findings, particularly the volume-impact asymmetry between imaging and molecular/pharmaceutical domains and the extremely low number of papers reporting operational deployment, are potentially valuable contributions to the field. However, the manuscript as presented has several significant limitations that prevent full assessment of the claims. The absence of all figures and tables makes it impossible to evaluate the primary evidence. The methodological description, while detailed in parts, leaves important questions unanswered regarding the validity of the LLM-based annotation approach, the handling of ambiguous cases, and the robustness of the statistical analyses. The theoretical framing around invariance structures, while interesting, is presented as interpretation rather than as a tested hypothesis, and the connection between the empirical findings and this framework is not rigorously established. The manuscript would benefit from clearer articulation of what is novel relative to existing reviews and bibliometric analyses, and from a more careful treatment of the limitations of the corpus construction and annotation methodology.

### Who would be interested in the results, and why
Researchers and practitioners in biomedical AI, including those working on synthetic data generation, data augmentation, and generative models for medical imaging and drug discovery, would find the descriptive landscape useful for understanding where the field has concentrated its efforts. Funders and journal editors in biomedical informatics and AI would be interested in the evidence of a translation gap and the proposed priorities for evaluation standards and deployment reporting. Methodologists studying the use of LLMs for systematic review and bibliometric analysis would find the annotation approach of interest. However, the broad interdisciplinary readership that Nature-style publications typically target may find the manuscript too narrowly focused on a bibliometric description without deeper methodological or conceptual advances.

### Major Strengths
1. The corpus size (4,143 papers) and the systematic approach to classification across five facets represent a substantial effort and provide a useful descriptive resource.
2. The finding that only 27 of 4,143 papers report operational use is a striking and potentially important observation that challenges the enthusiasm surrounding synthetic data in biomedicine.
3. The volume-impact asymmetry between imaging and molecular/pharmaceutical domains is an interesting and non-obvious finding that could stimulate further investigation.
4. The use of LLM-based annotation with human validation is a contemporary methodological choice that, if properly validated, could be of interest to the bibliometrics community.
5. The discussion of invariance structures as a potential explanatory framework for modality differences is conceptually interesting and connects the empirical findings to a broader theoretical literature.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims to present a systematic mapping and bibliometric analysis with specific quantitative findings, including facet distributions, temporal trends, and citation analyses.
- **Evidence pointer** Figures 1–6, Tables 1, 3, 4, 5; location not provided
- **Concern** All figures and most tables are referenced but not provided in the submitted material. The quantitative claims (e.g., 37.8% imaging, 77.8% strongly supportive, interaction coefficients, kappa values) cannot be verified against the underlying data visualizations or tabulated results. The reader cannot assess the distribution of papers across categories, the temporal patterns claimed, or the citation analyses.
- **Why it matters** The core contribution of this manuscript is empirical description. Without access to the figures and tables, the evidence base for the central claims is absent. The reader cannot evaluate whether the reported percentages are correctly derived, whether the temporal trends are visually supported, or whether the citation analyses are appropriately presented. This is a fundamental barrier to assessment.
- **Resolution test** Provide all figures and tables in a revised submission. The quantitative claims should be directly traceable to the displayed data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript claims that annotation combined multi-round expert labeling with LLM-assisted classification, validated against a held-out set of human annotated papers, with agreement of kappa = 0.57 ± 0.08 between human and LLM labels.
- **Evidence pointer** Methods section, "Annotation, validation, and citation analysis"; Supplementary information, "Inter-Rater Reliability and Annotation Refinement"; location not provided
- **Concern** The validation of the LLM-based annotation approach is described with a single kappa value (0.57 ± 0.08) for human-LLM agreement on the held-out Batch 3 test set. This level of agreement is moderate at best and raises questions about the reliability of the corpus-wide labels. The manuscript does not report per-facet agreement, which is critical given that some facets (e.g., stance) may be more subjective than others. The use of majority vote across three LLMs is described, but the agreement among the LLMs themselves is not reported. The manuscript also does not describe how the LLM prompts were validated, whether the few-shot examples were representative, or whether there was any calibration of the LLM outputs against human judgment beyond the single kappa value. The decision to use majority vote with a fixed priority order for three-way disagreements (affecting 1.4% of decisions) is described but the potential bias introduced by this resolution method is not discussed.
- **Why it matters** The entire corpus classification rests on the validity of the LLM-based annotation. If the labels are unreliable, all downstream analyses (facet distributions, temporal trends, citation analyses) are compromised. A kappa of 0.57 indicates substantial disagreement between human and machine labels, and the manuscript does not adequately address what this means for the confidence in the reported percentages. The lack of per-facet reliability data makes it impossible to know which facets are trustworthy.
- **Resolution test** Report per-facet human-LLM agreement, LLM-LLM agreement, and a confusion matrix or error analysis for the held-out test set. Discuss the implications of the observed agreement levels for the reliability of the corpus-wide labels. Consider whether a higher agreement threshold should be required for inclusion of a label in the analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript claims that "only 27 of 4,143 papers in our corpus report a system in operational use" and that this "profound practicality gap" is a central finding.
- **Evidence pointer** Results section, "Discussion and future directions"; location not provided
- **Concern** The identification of only 27 papers with an "In use" label is a striking claim, but the manuscript provides no detail on how this label was operationalized. What specific criteria were used to determine that a paper reports operational use? Was this based on explicit statements in the abstract, or was it inferred? How was inter-annotator agreement for this specific facet? Given that the overall human-LLM agreement is only moderate (kappa = 0.57), the reliability of this specific and consequential label is unclear. The manuscript also acknowledges that "even this small number overstates genuine deployment" but does not provide a breakdown of how many of the 27 are validation studies versus routine operational systems. The claim that this represents a "translation gap" depends entirely on the reliability of this label.
- **Why it matters** The "translation gap" is presented as one of the most important findings of the manuscript. If the "In use" label is unreliable or was applied too conservatively, the central conclusion could be an artifact of the annotation methodology. The reader needs to understand exactly how this label was defined and applied, and what confidence can be placed in it.
- **Resolution test** Provide the specific criteria for the "In use" label, report per-facet agreement for this label, and provide a detailed breakdown of the 27 papers, including how many are validation studies versus operational systems. Consider whether a more nuanced categorization of deployment status would be more informative.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** The manuscript proposes that the volume-impact asymmetry between imaging and molecular/pharmaceutical domains can be explained by "well-characterized transformation-group invariances" in imaging and "SE(3)-equivariant architectures and structure-prediction models" in molecular applications.
- **Evidence pointer** Abstract; "Motivation and contributions" section; "Discussion and future directions" section; location not provided
- **Concern** The theoretical interpretation linking the empirical findings to invariance structures is presented as a post-hoc explanation without direct evidence. The manuscript does not test whether papers in the imaging domain actually rely on transformation-group invariances, nor whether molecular papers actually use SE(3)-equivariant architectures. The connection between the citation analysis and these theoretical constructs is asserted rather than demonstrated. The manuscript also does not consider alternative explanations for the observed patterns, such as differences in data availability, regulatory pathways, or funding priorities across domains.
- **Why it matters** The theoretical framing is presented as a significant contribution, but it is not empirically supported within the manuscript. If the interpretation is speculative, it should be clearly labeled as such. If it is intended as a testable hypothesis, the manuscript should provide some evidence or at least a clear research design for testing it. As presented, the interpretation risks overreaching beyond what the data can support.
- **Resolution test** Either clearly label the invariance-based interpretation as a speculative hypothesis requiring further testing, or provide empirical evidence linking the citation patterns to the use of specific architectural or methodological approaches in the cited papers.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparative contribution
- **Claim pointer** The manuscript claims its contribution is complementary to prior reviews, specifically citing Breugel et al. (2024) as the most direct comparator, and claims to offer "the first corpus-level quantification of how the field has distributed its effort across modalities, paper types, deployment status, and citation impact across a full decade."
- **Evidence pointer** "Motivation and contributions" section; location not provided
- **Concern** The manuscript does not provide a systematic comparison with prior bibliometric analyses or reviews of synthetic data in biomedicine. The claim of being "the first" corpus-level quantification is strong and requires careful verification against existing literature. The manuscript mentions Breugel et al. but does not systematically compare findings, methodologies, or coverage. There may be other bibliometric studies of synthetic data or generative AI in healthcare that are not addressed.
- **Why it matters** The novelty claim is central to the manuscript's contribution. If similar analyses have been published, the manuscript's contribution is incremental rather than novel. The reader cannot assess the novelty claim without a more thorough review of related work.
- **Resolution test** Provide a systematic comparison with prior bibliometric analyses and reviews of synthetic data in biomedicine, including a clear statement of what is new in this analysis relative to each prior work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "77.8% of papers were strongly supportive while critical work remained below 1%." The term "strongly supportive" is not defined in the abstract, and the reader is left to infer what this means. The abstract also does not mention the kappa values or the validation of the LLM-based annotation, which are important for assessing the reliability of these percentages.
- **Required correction** Briefly define the stance categories in the abstract or refer to the methods for definitions. Consider adding a sentence about the validation of the annotation approach.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Methods, "Literature search and corpus construction"
- **Evidence pointer** Methods section; location not provided
- **Issue** The search query is described in terms of three clusters of terms combined with AND, plus a disjunctive arm for "virtual patient" work. However, the exact query string is not reproduced. The manuscript states that step-by-step retrieval instructions are given in Protocol A, but this protocol is not provided in the submitted material. The choice of terms within each cluster is not justified, and it is unclear whether the query was validated for sensitivity and specificity.
- **Required correction** Reproduce the full query string in the main text or supplementary material. Justify the choice of terms and describe any validation of the search strategy.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Methods, "Annotation, validation, and citation analysis"
- **Evidence pointer** Methods section; location not provided
- **Issue** The manuscript reports interaction coefficients for temporal trends (e.g., -0.025, +0.021, -0.027) with q-values but does not report confidence intervals or effect sizes in a way that allows the reader to assess the magnitude of these effects. The choice of Poisson regression is stated but the model diagnostics are not described.
- **Required correction** Report confidence intervals for the interaction coefficients and describe model diagnostics. Consider whether the effect sizes are practically meaningful in addition to statistically significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Main text; location not provided
- **Issue** The term "synthetic data" is used broadly, and the manuscript acknowledges in the discussion that the boundary of what constitutes synthetic data is unsettled. However, the operational definition used for corpus inclusion is only briefly stated in the methods. The manuscript includes digital twins and structure-prediction outputs (e.g., AlphaFold predictions) as synthetic data, which is a broad interpretation that may not be shared by all readers.
- **Required correction** Provide a more detailed operational definition of synthetic data as used for corpus inclusion, with examples and exclusions. Discuss the implications of this broad definition for the interpretation of the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion, limitations
- **Evidence pointer** "Discussion and future directions" section; location not provided
- **Issue** The manuscript lists several limitations but does not discuss the potential for publication bias, the exclusion of non-English literature, or the restriction to PubMed-indexed records as potential sources of bias in the corpus. The decision to exclude arXiv and other preprint servers is acknowledged but the implications for the completeness of the methodological literature are not discussed.
- **Required correction** Add a discussion of these potential biases and their implications for the generalizability of the findings.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and code availability
- **Evidence pointer** Data availability section; location not provided
- **Issue** The data availability statement indicates that the annotated corpus and code are deposited in Zenodo, but the specific DOI is not provided in the submitted material. The statement also does not specify the license under which the data and code are released.
- **Required correction** Provide the specific DOI and license information in the data availability statement.

### Technical failings that need to be addressed before the case is established
1. Absence of all figures and tables, which are essential for evaluating the empirical claims (R1-M1).
2. Insufficient reporting of per-facet inter-rater agreement and LLM validation details, which undermines confidence in the corpus labels (R1-M2).
3. Lack of operationalization of the "In use" label, which is central to the "translation gap" claim (R1-M3).
4. Post-hoc theoretical interpretation without empirical support (R1-M4).
5. Incomplete comparison with prior work, leaving the novelty claim unverified (R1-M5).

### Assessment against Nature-style criteria
**Originality:** The manuscript offers a corpus-level quantification of the synthetic data field in biomedicine, which is a useful descriptive contribution. However, the originality is moderate, as the approach builds on established bibliometric methods and the findings largely confirm expectations about the dominance of imaging and the early stage of deployment. The theoretical framing around invariance structures is interesting but not original in itself, and its application here is speculative.

**Scientific importance:** The finding that only 27 of 4,143 papers report operational use is potentially important and could influence research priorities and funding decisions. The volume-impact asymmetry is also a notable observation. However, the importance is tempered by the methodological limitations and the lack of a rigorous connection between the empirical findings and the proposed theoretical explanations.

**Interdisciplinary readership:** The topic is relevant to researchers in biomedical informatics, AI, and clinical translation. However, the manuscript is written primarily for a specialized audience familiar with bibliometric methods and generative AI terminology. The theoretical discussion of invariance structures may be accessible to a broader readership, but the overall presentation is not optimized for interdisciplinary appeal.

**Technical soundness:** The methodological approach is reasonable in principle, but the reporting is incomplete. The lack of figures and tables, the insufficient detail on LLM validation, and the absence of per-facet reliability data are significant technical shortcomings. The statistical analysis is described but not fully documented.

**Readability for nonspecialists:** The manuscript is generally well-written and the main findings are clearly stated. However, the methods section assumes familiarity with bibliometric and LLM-based annotation techniques. The discussion of invariance structures and SE(3)-equivariant architectures may be challenging for readers outside the AI field. The abstract is accessible but could benefit from clearer definitions of key terms.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a timely and potentially important question, and the descriptive findings could be valuable. However, the absence of all figures and tables, the incomplete reporting of the annotation methodology and validation, and the lack of operationalization of the central "In use" label prevent a full assessment of the claims. The theoretical interpretation is speculative and not empirically supported. The manuscript would require substantial revision, including provision of all visual and tabular evidence, detailed reporting of per-facet reliability, a clear operational definition of the deployment label, and a more rigorous treatment of the theoretical framework, before the case for its findings can be established.

## Risk / unsupported claims
- The claim that "only 27 of 4,143 papers report operational use" is unsupported without a clear operational definition of the "In use" label and evidence of its reliable application.
- The claim that the volume-impact asymmetry can be explained by "well-characterized transformation-group invariances" and "SE(3)-equivariant architectures" is unsupported, as no empirical evidence linking the citation patterns to these specific methodological features is provided.
- The claim that the corpus provides "the first corpus-level quantification" of this field is unverifiable without a systematic comparison with prior bibliometric analyses.
- The quantitative percentages reported in the abstract and main text (e.g., 37.8%, 77.8%, 8.6%, <1%) cannot be verified without access to the underlying figures and tables.
- The claim that the annotation approach was "validated" is only weakly supported by a single kappa value, and the implications of the moderate agreement level for the reliability of the corpus labels are not discussed.
- The statement that "the peer reviewed record captures the early stages of the research pipeline far better than the late ones" is presented as a finding but is an interpretation that goes beyond the data presented.