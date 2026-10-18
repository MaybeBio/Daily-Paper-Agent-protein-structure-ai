## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, reproducibility, and alignment with stated aims; no assessment of formatting or editorial compliance
- **Shared manuscript claim summary** The manuscript proposes that multi-model AI-driven pipelines integrating discriminative classifiers, generative models, potency and toxicity predictors, novelty filters, stability screens, and molecular docking can overcome key bottlenecks in antimicrobial peptide (AMP) discovery, reduce late-stage attrition, and accelerate translation from in silico prediction to wet-lab validation.
- **Visible evidence base** Narrative review with cited literature; tables summarizing model performance (Tables 1–10); figures illustrating pipeline architecture (Figures 1–15); no primary experimental data or code provided
- **Missing materials affecting confidence** No code, datasets, or benchmark implementations; no quantitative comparison of proposed pipelines against existing methods; no wet-lab validation data; figure contents not fully described in text; table details (e.g., exact metrics, dataset versions) not fully specified

## Reviewer
- **Overall assessment** This manuscript provides a broad, well-structured narrative review of AI-driven AMP discovery, with a useful emphasis on multi-objective, closed-loop pipeline design. The authors correctly identify key limitations in current approaches, including dataset bias, negative-set construction, and over-generalization. However, the manuscript is largely descriptive and does not provide a concrete, reproducible pipeline architecture, benchmark evaluation, or comparative analysis. The central claim that such pipelines "overcome key bottlenecks" is asserted rather than demonstrated. The review would benefit from a more critical, quantitative treatment of existing methods and a clearer articulation of what is novel relative to prior reviews.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on antimicrobial peptide discovery, machine learning practitioners interested in drug design applications, and microbiologists seeking an overview of AI tools for AMP development. The review may also be of interest to researchers in AMR policy and translational medicine who want a high-level understanding of computational approaches in this space.
- **Major strengths** 
  - Comprehensive coverage of AI model types (discriminative, generative, structural, stability, toxicity) relevant to AMP design
  - Emphasis on multi-objective optimization and closed-loop design, which is a timely and important perspective
  - Good discussion of dataset bias, negative-set construction, and benchmarking challenges
  - Inclusion of recent tools (e.g., AlphaFold3, DiffDock, ESM-2-based models) and clear tables summarizing model capabilities
  - Clear articulation of the gap between in silico prediction and wet-lab/clinical translation
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
  - **R1-m6**
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide a concrete, testable pipeline architecture; no code, data, or benchmark results are presented; the claimed advantages of multi-model pipelines over single-model approaches are not quantitatively demonstrated; the review does not critically compare the proposed framework with existing published pipelines (e.g., AMPGAN, DeepAMP, etc.) in a systematic way.
- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The review synthesizes existing work but does not present a novel conceptual framework or new methodological contribution. The emphasis on closed-loop, multi-objective design is not entirely new and has been discussed in prior literature.
  - **Scientific importance**: High. AMP discovery is a critical area given the AMR crisis, and AI-driven approaches are of significant interest. However, the manuscript does not provide new evidence or a validated framework that would advance the field beyond existing reviews.
  - **Interdisciplinary readership**: Moderate. The manuscript is accessible to computational biologists and microbiologists, but may be too technical for clinicians or policy makers without a computational background.
  - **Technical soundness**: Weak. The review is descriptive and lacks quantitative benchmarking, reproducibility details, or critical evaluation of model limitations. Claims of "reproducible and generalizable blueprints" are not supported by provided evidence.
  - **Readability for nonspecialists**: Good. The text is clearly written, with helpful tables and figures, though some sections (e.g., molecular docking) assume prior knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript is a useful narrative review but does not substantiate its central claims of a reproducible, generalizable, multi-model pipeline that reduces attrition. Major revisions are required to provide concrete implementation details, benchmark comparisons, or a more critical and quantitative synthesis of existing evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** The manuscript claims to provide "reproducible and generalizable blueprints" for multi-model AI-driven AMP design pipelines.
- **Evidence pointer** Abstract; Section "Current AI-based approaches"; Figure 3; Tables 1–10
- **Concern** The manuscript does not provide any concrete implementation details, such as model architectures, hyperparameters, training data versions, or code availability. The tables summarize reported performance from cited studies but do not specify how these models were integrated into the proposed pipeline. Without these details, the claimed "blueprints" cannot be reproduced or evaluated by independent researchers.
- **Why it matters** Reproducibility is a core requirement for scientific claims, especially in computational biology where model performance is highly sensitive to data splits, preprocessing, and hyperparameters. The absence of implementation details undermines the practical utility of the proposed framework.
- **Resolution test** Provide a detailed pipeline specification, including model choices, data sources, preprocessing steps, and evaluation protocols. Ideally, include a public repository with code and example datasets, or at minimum a step-by-step algorithmic description.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for claimed outcomes
- **Claim pointer** The manuscript states that multi-model pipelines "overcome key bottlenecks" and "reduce late-stage attrition" in AMP development.
- **Evidence pointer** Abstract; Section "Current AI-based approaches"; Section "Future directives"; Table 10
- **Concern** The review does not present any quantitative evidence, case studies, or comparative analyses demonstrating that multi-model pipelines outperform single-model approaches or traditional discovery methods. The cited examples (e.g., AMPGen, EBAMP) are described qualitatively, and no success rates, hit rates, or translational outcomes are systematically compared. The claim of reduced attrition is speculative and not supported by data.
- **Why it matters** The central value proposition of the manuscript is that multi-model integration improves outcomes. Without empirical or at least systematic comparative evidence, this claim remains an assertion, not a demonstrated finding.
- **Resolution test** Include a comparative table or meta-analysis of published pipelines, showing metrics such as hit rates, validation success, and translational progress. If such data are unavailable, clearly state this as a limitation and reframe the claims as hypotheses rather than demonstrated outcomes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Critical evaluation of limitations
- **Claim pointer** The manuscript discusses dataset bias and over-generalization as limitations but does not critically evaluate how these issues affect the proposed pipeline.
- **Evidence pointer** Section "Dataset overlapping, negative-set construction and over-generalization"; Section "Current barriers and limitations"
- **Concern** While the authors correctly identify dataset bias and negative-set construction as key challenges, they do not propose concrete solutions or evaluate how their multi-model framework mitigates these issues. The discussion remains at a high level and does not engage with specific technical solutions (e.g., cluster-based splitting, temporal validation, or external benchmarking).
- **Why it matters** A review that identifies limitations without proposing or evaluating solutions does not advance the field. The manuscript would be stronger if it critically assessed which existing methods address these challenges and how the proposed pipeline could incorporate them.
- **Resolution test** Add a subsection that critically evaluates proposed solutions to dataset bias (e.g., redundancy-controlled splitting, external validation) and discusses how the multi-model framework could implement these. Provide examples from the literature where such approaches have been successfully applied.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty relative to existing reviews
- **Claim pointer** The manuscript positions itself as a novel contribution to AI-driven AMP discovery.
- **Evidence pointer** Introduction; Section "Current AI-based approaches"
- **Concern** Several recent reviews have covered AI-driven AMP discovery, including discussions of generative models, toxicity prediction, and pipeline integration. The manuscript does not clearly articulate what is new relative to these prior reviews, nor does it provide a systematic comparison of existing pipelines. The novelty appears to be primarily in the emphasis on multi-objective, closed-loop design, but this is not developed into a distinct framework.
- **Why it matters** For a review to be publishable, it must offer a new synthesis, critical perspective, or actionable framework. Without a clear statement of novelty, the manuscript risks being seen as redundant with existing literature.
- **Resolution test** Add a section that explicitly compares the proposed multi-model framework with 2–3 existing reviews or pipelines, highlighting specific differences in scope, methodology, or recommendations. Clearly state what this review adds beyond prior work.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Figure and table quality
- **Claim pointer** Figures 1–15 and Tables 1–10 are used to support the narrative.
- **Evidence pointer** Figures 1–15; Tables 1–10
- **Concern** The figures are not described in sufficient detail in the text, and their content is not fully explained. For example, Figure 3 is referenced as the pipeline architecture but the specific components and their interactions are not described in the text. Tables summarize model performance but do not include confidence intervals, dataset versions, or evaluation protocols, limiting their interpretability.
- **Why it matters** Figures and tables should be self-explanatory and fully integrated with the text. In their current form, they do not provide the level of detail needed for readers to assess the validity of the claims.
- **Resolution test** Revise figure captions to include detailed descriptions of all components and data flows. Expand table footnotes to specify dataset versions, evaluation metrics, and any preprocessing steps. Ensure each figure and table is explicitly referenced and discussed in the text.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract; Section "AI, as the first stage of stability, efficacy, and safety validation"
- **Evidence pointer** Abstract; Section 1.3
- **Issue** The term "multimodel" is used throughout but is not clearly defined. It could refer to multiple model types, multiple datasets, or multiple objectives. The manuscript would benefit from an explicit definition early in the text.
- **Required correction** Define "multimodel" at first use, specifying whether it refers to multiple model architectures, multiple data modalities, or multiple prediction tasks.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Citation accuracy
- **Affected element** Section "Discriminative AMP classifiers"
- **Evidence pointer** Section 1.3.1; Table 1
- **Issue** Some citations appear to be used generically without specifying which model or dataset they refer to. For example, "AmPEP" is cited but the specific version and training data are not described.
- **Required correction** Ensure each cited tool or model is accompanied by a brief description of its architecture, training data, and reported performance, as appropriate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency of claims
- **Affected element** Section "Current barriers and limitations"
- **Evidence pointer** Section 1.3.3; Section 2.1
- **Issue** The manuscript states that "computational performance cannot equate with therapeutic performance" but earlier sections imply that high in silico metrics are sufficient for prioritization. This tension should be resolved or explicitly discussed.
- **Required correction** Clarify the relationship between in silico metrics and translational success, and discuss how the proposed pipeline addresses this gap.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Missing discussion of computational cost
- **Affected element** Section "Future directives"
- **Evidence pointer** Section 2.2
- **Issue** The manuscript does not discuss the computational resources required for the proposed multi-model pipelines, which may be substantial. This is relevant for reproducibility and practical adoption.
- **Required correction** Add a brief discussion of computational cost and resource requirements, including any trade-offs between model complexity and performance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and readability
- **Affected element** Throughout
- **Evidence pointer** Abstract; Section 1.3.2
- **Issue** Some sentences are overly long and contain multiple clauses, which reduces readability. For example, the sentence beginning "The proposed architectural frameworks combine..." in the abstract is difficult to parse.
- **Required correction** Revise for clarity by breaking long sentences into shorter, more direct statements.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures 1–15
- **Evidence pointer** Figures 1–15
- **Issue** The figures are not accessible to color-blind readers, as they appear to rely on color coding without alternative markers or labels.
- **Required correction** Ensure all figures use patterns, labels, or other non-color cues to convey information.

## Risk / unsupported claims
- The claim that multi-model pipelines "reduce late-stage attrition" is not supported by any quantitative or case-based evidence in the manuscript.
- The claim that the proposed framework is "reproducible and generalizable" is not supported, as no implementation details, code, or datasets are provided.
- The statement that "computational performance cannot equate with therapeutic performance" is acknowledged but not integrated into the proposed pipeline design, leaving a gap between the stated limitation and the proposed solution.
- The performance metrics summarized in Tables 1–10 are presented without critical assessment of their comparability, dataset overlap, or potential for information leakage, which the manuscript itself identifies as a key issue.
- The manuscript's assertion that "no single AI framework is optimal" is reasonable but is not developed into a concrete recommendation for how to select or combine models in practice.