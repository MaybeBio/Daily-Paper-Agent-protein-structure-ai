## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark multiple in silico pathogenicity predictors against clinically curated SYNGAP1 missense variants, identify top performers (folding stability calculations, ESM1b, AlphaMissense), optimize thresholds for improved accuracy, describe structural enrichment patterns of pathogenic variants, propose a link between missense variation and phase separation/phosphoregulation, and present a new web server (SGM) for variant assessment.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1–2.7), Discussion, Conclusions, Methods (Sections 5.1–5.8), Data Availability Statement
- **Missing materials affecting confidence** Figures 1–6, Tables 1 and S1–S12, Supporting Information text and equations, Supplementary Figures S1–S8, benchmark dataset details, server implementation details

## Reviewer
- **Overall assessment** This manuscript addresses a clinically relevant problem, the interpretation of SYNGAP1 missense variants, using a broad panel of computational predictors. The benchmarking approach is systematic, and the development of a publicly accessible server is a valuable community resource. However, the study's core conclusions are limited by the small and potentially biased benchmark set, the lack of experimental validation, and the absence of key methodological details in the provided text. The claims regarding phase separation and phosphoregulation are largely speculative and require further support. The manuscript is technically sound in its computational execution but the clinical utility of the proposed framework remains to be established.
- **Who would be interested in the results, and why** Clinical geneticists and molecular diagnosticians interpreting SYNGAP1 variants, researchers studying SYNGAP1-related disorders, computational biologists developing and benchmarking variant effect predictors, and the broader neurodevelopmental disease community. The SGM server provides a practical tool for variant assessment.
- **Major strengths** 1. Systematic benchmarking of a wide range of predictors, from traditional sequence-based to state-of-the-art deep learning methods. 2. Gene-specific threshold optimization with cross-validation, demonstrating a clear improvement for AlphaMissense. 3. Identification of structural domain enrichment patterns that align with biological expectations. 4. The SGM server is a practical, accessible resource that integrates multiple data types and provides AI-generated summaries. 5. The study highlights important limitations of current predictors for disordered regions.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Benchmark dataset adequacy
  - **Claim pointer** The benchmark set is described as "limited but carefully curated" and is used to draw strong conclusions about predictor performance and to calibrate thresholds for clinical use.
  - **Evidence pointer** Section 5.2, Figure 1d, Tables 1 and S1–S3
  - **Concern** The benchmark set contains only 191 clinically labeled variants (75 benign, 53 likely benign, 21 pathogenic, 42 likely pathogenic). This is a very small sample for evaluating and calibrating predictors, especially for a gene with a high burden of pathogenic missense variation. The set is likely imbalanced and may not represent the full spectrum of SYNGAP1 variants. The inclusion of "conflicting" variants reclassified based on submission counts is a subjective criterion that could introduce bias. The small sample size raises concerns about overfitting during threshold optimization, despite the cross-validation approach.
  - **Why it matters** The clinical utility of the SGM server and the recommended thresholds depend entirely on the quality and representativeness of this benchmark set. If the set is biased or too small, the reported performance metrics and optimized thresholds may not generalize to real-world clinical cases, potentially leading to misclassification.
  - **Resolution test** Provide a detailed breakdown of the benchmark set, including the distribution of variants across protein domains and disorder regions. Justify the reclassification of conflicting variants with explicit criteria. Perform a power analysis to demonstrate that the sample size is sufficient to detect meaningful performance differences. Ideally, validate the optimized thresholds on an independent, larger cohort of SYNGAP1 variants with functional or clinical data.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation of predictions
  - **Claim pointer** The manuscript claims that top-performing predictors, especially optimized AlphaMissense, provide accurate predictions for SYNGAP1 variant pathogenicity.
  - **Evidence pointer** Sections 2.1–2.2, Figure 2, Tables 1 and S3
  - **Concern** The benchmarking is entirely computational, relying on ClinVar labels as ground truth. There is no experimental validation of any predictions, such as functional assays or protein stability measurements. The authors acknowledge that "rigorous testing with any such sets cannot guarantee prediction accuracy" but still present the optimized thresholds as suitable for clinical use. The only experimental dataset mentioned is from a prior study (Meili et al., N = 57), which is not used for validation here.
  - **Why it matters** ClinVar labels themselves can be incorrect or biased, especially for variants in genes with limited functional data. Without experimental validation, the true accuracy of the predictors, and particularly the optimized AlphaMissense thresholds, remains unknown. This limits the confidence with which the SGM server can be used for clinical decision-making.
  - **Resolution test** Validate the predictions against an independent experimental dataset, such as the Meili et al. stability measurements or functional assays for a subset of variants. If experimental data are not available, clearly state this as a major limitation and temper the clinical recommendations accordingly.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Phase separation and phosphoregulation claims
  - **Claim pointer** The manuscript proposes that missense variants in disordered regions, particularly those affecting phosphosites, could alter phase separation behavior and contribute to SYNGAP1-related disorder pathogenesis.
  - **Evidence pointer** Section 2.6, Figure 5, Tables S9–S12
  - **Concern** This section is largely speculative. The identification of 70 PS-impacting variants by PSMutPred is a computational prediction with no experimental validation. The colocalization analysis between phosphosites and PS-impacting variants, while statistically significant, is a correlative observation. The claim that these regions "could act as phase separation-promoting segments" is presented as a plausible mechanism but is not directly tested. The functional significance of the specific variants identified is unknown.
  - **Why it matters** This is a potentially important biological insight, but as presented, it is a hypothesis-generating observation rather than a demonstrated mechanism. Overstating these findings could mislead readers about the established role of these variants in disease.
  - **Resolution test** Soften the language to clearly frame this as a hypothesis. Provide additional computational or experimental support, such as predictions from multiple PS prediction tools, analysis of known phase-separation-promoting sequence features, or preliminary experimental data on variant effects on phase separation.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and transparency
  - **Claim pointer** The SGM server is presented as a comprehensive resource, and the methods are described as reproducible.
  - **Evidence pointer** Sections 5.3–5.7, Data Availability Statement
  - **Concern** The provided text lacks critical details for reproducibility. The exact versions and parameters for all predictors are not specified. The criteria for MD-based classification of variants as "potentially pathogenic, benign, or uncertain" are described as "visually observed structural impacts," which is subjective and not quantifiable. The AI-generated summaries are produced by a model (gpt-oss-20b) whose specific prompt and output validation process are not described in detail.
  - **Why it matters** For a resource intended for clinical use, transparency and reproducibility are essential. Subjective classification criteria and undocumented parameters undermine confidence in the results and prevent others from replicating or independently verifying the findings.
  - **Resolution test** Provide a detailed supplementary methods section with exact software versions, parameters, and analysis pipelines. For MD-based classifications, provide quantitative criteria or a rubric for the visual assessment. Describe the AI prompt and any quality control measures for the generated summaries.

- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of writing
  - **Affected element** Section 2.1, Figure 2
  - **Evidence pointer** "Figure 2 and Tables 1 and S1"
  - **Issue** The text states that "substantial overlap in the bootstrap confidence intervals" indicates similar performance, but this is not a rigorous statistical comparison. The figure and tables are not available for review.
  - **Required correction** Provide a formal statistical test for comparing predictor performance, such as a DeLong test for AUC differences, and report the results clearly.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Section 2.2, "AlphaMissense: Optimized"
  - **Evidence pointer** "the optimized AlphaMissense classification scheme was incorporated into the SGM server as 'AlphaMissense: Optimized'"
  - **Issue** The term "optimized" is used without specifying the exact optimization criterion beyond Youden's J. It is unclear if this refers to a single or dual threshold.
  - **Required correction** Clarify the optimization procedure, including the specific objective function and whether single or dual thresholds were used.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Section 2.5, Figure 4
  - **Evidence pointer** "Figure 4a,b and S5"
  - **Issue** The text mentions "relative enrichment" and "pathogenic density" but the exact calculation methods are not described in the main text.
  - **Required correction** Define these metrics explicitly in the Methods section or refer to the Supporting Information for the formulas.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Section 3, Discussion
  - **Evidence pointer** "To our knowledge, ACMG evidence-strength thresholds have not been calibrated for SYNGAP1 yet"
  - **Issue** This claim is not supported by a citation or a literature search description.
  - **Required correction** Provide a reference or state that a systematic literature search was conducted to support this claim.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Accessibility
  - **Affected element** Section 5.7, SGM server
  - **Evidence pointer** "optimized for laptops or desktop computers"
  - **Issue** The server is not optimized for mobile devices, which may limit its accessibility for some users.
  - **Required correction** Acknowledge this limitation and consider providing a mobile-friendly version or a clear statement about the recommended browsing environment.

- **Technical failings that need to be addressed before the case is established** 1. The benchmark set is too small and potentially biased to support the strong claims about predictor performance and threshold optimization. 2. The lack of experimental validation for any predictions, particularly the optimized AlphaMissense thresholds, is a critical gap. 3. The subjective nature of MD-based variant classification needs to be replaced with quantitative criteria. 4. The phase separation and phosphoregulation claims are speculative and need to be framed as such or supported by additional evidence.

- **Assessment against Nature-style criteria** 
  - **Originality** Moderate. The application of a broad panel of predictors to SYNGAP1 is somewhat novel, but the general approach of benchmarking in silico predictors is well-established. The SGM server is a useful contribution but not conceptually novel.
  - **Scientific importance** High for the SYNGAP1 community. The study addresses a real clinical need for better variant interpretation tools. However, the impact is limited by the lack of experimental validation and the small benchmark set.
  - **Interdisciplinary readership** Moderate. The topic is relevant to clinical genetics, computational biology, and neuroscience. The writing is generally accessible, but the heavy reliance on computational details may limit appeal to a broader audience.
  - **Technical soundness** The computational methods are generally sound, but the small benchmark set and subjective classification criteria are significant weaknesses. The cross-validation approach is appropriate but does not fully mitigate the risk of overfitting.
  - **Readability for nonspecialists** The abstract and introduction are clear, but the results and methods sections are dense and assume familiarity with variant effect prediction. The manuscript would benefit from a more accessible summary of the key findings and their implications.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem and presents a potentially valuable resource. However, the current evidence does not fully support the strength of the claims made. The authors must address the concerns regarding benchmark set size and bias, provide experimental validation or clearly state its absence as a major limitation, and improve the transparency and reproducibility of their methods. If these issues are adequately resolved, the manuscript could make a meaningful contribution to the field.