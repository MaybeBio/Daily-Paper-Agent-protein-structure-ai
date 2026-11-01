## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present RNA-SyntHub, a pipeline for curating synthetic RNA 3D structure datasets. The workflow integrates multiple structure-generation approaches with a meta-scoring function to filter low-quality models. As a proof of concept, they applied the pipeline to 447,402 RFDiffusion-predicted structures, yielding a curated subset of approximately 16,000 structures, further complemented by Boltz-1 and RNAComposer predictions. The authors claim this provides both a methodological framework and a concrete dataset for downstream applications.
- **Visible evidence base** Abstract text only; no quantitative validation metrics, benchmark comparisons, or dataset quality assessments are reported
- **Missing materials affecting confidence** Full methods, scoring function details, validation benchmarks, dataset composition statistics, comparison with existing RNA structure curation tools, and any downstream application demonstrations

## Reviewer
- **Overall assessment** The abstract describes a potentially useful pipeline for curating synthetic RNA 3D structures, addressing a genuine need in the field. However, the evidence presented is insufficient to evaluate the technical soundness of the meta-scoring approach, the quality of the curated dataset, or the claimed utility for downstream applications. The core claims are plausible but currently unsubstantiated from the supplied material.
- **Who would be interested in the results, and why** Researchers in RNA structural biology, computational RNA design, and deep learning for biomolecular structure prediction would be interested. The dataset could serve as training or benchmarking data for RNA structure prediction models, and the curation methodology may be relevant to those building large structural datasets for protein or RNA applications.
- **Major strengths** The problem addressed is timely and relevant, given the growing demand for large RNA structural datasets. The proposed pipeline integrates multiple generation approaches, which is a sensible strategy. The scale of the proof-of-concept application (447,402 structures) is substantial.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The meta-scoring function is not described in sufficient detail to assess its validity. No validation of the curated subset against known RNA structures or experimental data is reported. The criteria for "low-quality" and "high-confidence" are not defined. The complementarity of Boltz-1 and RNAComposer predictions is asserted but not demonstrated.
- **Assessment against Nature-style criteria** 
  - Originality: The concept of meta-scoring for RNA structure curation is not entirely novel, but the specific application to synthetic RNA datasets may offer a new contribution. The abstract does not clearly differentiate this approach from existing curation methods.
  - Scientific importance: The need for curated RNA structural datasets is real and growing. If the method is validated, it could be valuable. However, the abstract does not demonstrate that the curated dataset is superior to existing alternatives.
  - Interdisciplinary readership: The topic bridges computational biology, structural biology, and machine learning, which could attract a broad audience. The abstract is written in accessible language.
  - Technical soundness: Cannot be assessed from the abstract alone. The meta-scoring approach, validation strategy, and quality metrics are not described.
  - Readability for nonspecialists: The abstract is clear and well-structured, with technical terms appropriately introduced.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a reasonable framework, but the absence of validation details and quality metrics prevents a supportive recommendation. A revised version with concrete validation results and methodological clarity could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The meta-scoring function identifies low-quality models and selects high-confidence candidates.
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not describe the meta-scoring function, its inputs, weights, or how it was calibrated. No evidence is presented that the scoring function accurately distinguishes high-quality from low-quality RNA structures.
- **Why it matters** The entire pipeline's utility depends on the validity of the meta-scoring approach. Without a description of the scoring methodology or validation against known structures, the curated dataset's reliability cannot be established.
- **Resolution test** Provide a detailed description of the meta-scoring function, including its components, training or calibration data, and validation against experimentally determined RNA structures or established quality metrics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The curated subset of approximately 16,000 structures is of high quality and suitable for downstream applications.
- **Evidence pointer** Abstract; location not provided
- **Concern** No quantitative metrics are provided to support the quality of the curated subset. The abstract does not report any benchmarks, comparisons with experimental structures, or independent validation of the selected models.
- **Why it matters** The claim that the dataset supports "methodological development, exploratory analyses, decoy-based applications, and selected deep learning workflows" requires evidence that the structures are accurate and representative. Without such evidence, the dataset's practical value is unsubstantiated.
- **Resolution test** Include validation results such as RMSD comparisons to known structures, assessment using established RNA quality metrics (e.g., MolProbity scores, RNA-specific scoring functions), or performance benchmarks in downstream tasks.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The workflow integrates data from multiple structure-generation approaches.
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not specify how the outputs from RFDiffusion, Boltz-1, and RNAComposer are integrated, how conflicts are resolved, or whether the complementarity of these methods was systematically assessed. The criteria for including Boltz-1 and RNAComposer predictions are not stated.
- **Why it matters** Reproducibility and transparency are essential for a methodological pipeline. Without clear integration rules and inclusion criteria, other researchers cannot apply or evaluate the method.
- **Resolution test** Provide a step-by-step description of the integration workflow, including data preprocessing, scoring, filtering thresholds, and the rationale for combining multiple generation methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "synthetic RNA structures"
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "synthetic RNA structures" is used without explicit definition. It is unclear whether this refers to computationally generated models, chemically synthesized RNA molecules, or both.
- **Required correction** Define "synthetic RNA structures" explicitly in the abstract or introduction to avoid ambiguity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Dataset availability
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not state where the curated dataset will be made available or in what format.
- **Required correction** Include a statement on data availability, including repository links and access conditions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with existing methods
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not compare RNA-SyntHub with existing RNA structure curation tools or datasets, making it difficult to assess the novelty or advantage of the proposed approach.
- **Required correction** Add a brief comparison with existing curation methods or datasets in the abstract or introduction.

## Risk / unsupported claims
- The claim that the curated dataset supports "selected deep learning workflows" is unsupported, as no demonstration or benchmark is provided.
- The claim that the pipeline "systematically constructs curated synthetic RNA datasets" is plausible but not verifiable from the abstract alone.
- The assertion that the curated subset is "high-confidence" is unsupported without defined quality criteria or validation metrics.
- The complementarity of Boltz-1 and RNAComposer predictions is asserted but not demonstrated.