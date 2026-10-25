## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present MP4, a transformer-based model that translates natural language prompts into de novo protein sequences. They claim state-of-the-art performance on a benchmark of 96 prompts across three metrics, experimental validation of two designs showing expression, thermostability, high-resolution crystal structures including a novel fold, and in vitro ATP binding and hydrolysis.
- **Visible evidence base** Abstract text only; no numerical data, statistical analyses, structural coordinates, or experimental protocols are available
- **Missing materials affecting confidence** Full methods, model architecture details, training data description, benchmark construction and evaluation protocol, experimental procedures, crystallographic statistics, functional assay data, and all figures and tables

## Reviewer
- **Overall assessment** The abstract describes an ambitious and potentially impactful approach to protein design via natural language. However, the evidence provided is insufficient to evaluate the core claims. Key performance metrics are presented without numerical values, the benchmark is not described in sufficient detail, and the experimental validation is summarized without supporting data. The claim of a "paradigm-shifting novel fold" is particularly strong and cannot be assessed without structural evidence and comparison to known folds. The work is interesting and timely, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Researchers in protein design, computational biology, and machine learning would be interested in the model architecture and benchmark results. Structural biologists would be interested in the novel fold claim. Synthetic biologists and molecular engineers would be interested in the potential for natural-language-driven design. The broader AI community may also find the text-to-sequence mapping approach of interest.
- **Major strengths** The concept of translating natural language directly to functional proteins is novel and addresses a real limitation in current protein design approaches. The combination of computational prediction with experimental validation, including crystallography and functional assays, is commendable. The reported resolution of the crystal structures (1.30 A and 1.77 A) suggests careful experimental work.
- **Major Concerns** 
  - R1-M1: The benchmark performance claims are not supported by any numerical data.
  - R1-M2: The "paradigm-shifting novel fold" claim is not substantiated.
  - R1-M3: The functional claims (ATP binding and hydrolysis) are not supported by quantitative data.
  - R1-M4: The training dataset description is insufficient to evaluate model validity.
- **Minor Comments** 
  - R1-m1: The abstract does not specify how the 96 prompts were selected or whether they are representative.
  - R1-m2: The relationship between the two experimentally validated designs and the benchmark prompts is unclear.
  - R1-m3: The statement "incomplete coverage and controllability" is vague and not quantified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: High. The concept of natural-language-to-protein translation appears novel and distinct from existing sequence- or structure-based design methods.
  - Scientific importance: Potentially high, but not established from the abstract alone. The impact depends on the robustness of the benchmark and the validity of the novel fold claim.
  - Interdisciplinary readership: The work would appeal to multiple communities, but the abstract lacks sufficient detail for nonspecialists to evaluate the significance.
  - Technical soundness: Cannot be assessed. No methods, statistics, or experimental details are provided.
  - Readability for nonspecialists: The abstract is generally clear, but terms like "sequence realism" and "predicted fold quality" are not defined.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising and the work may be significant, but the abstract alone does not provide sufficient support for the core claims. A full manuscript with detailed methods, data, and analyses would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "MP4 excelled by simultaneously improving on three key metrics: sequence realism, predicted fold quality, and alignment to the requested function."
- **Evidence pointer** Benchmark of 96 prompts; location not provided
- **Concern** The abstract claims that MP4 improved on three metrics but provides no numerical values, no comparison baselines, and no statistical significance. It is impossible to determine the magnitude of the improvement or whether it is meaningful.
- **Why it matters** The central computational claim of the paper rests on this benchmark. Without quantitative results, the reader cannot evaluate whether MP4 actually outperforms existing methods or by how much.
- **Resolution test** Provide the benchmark results in a table or figure with clear metrics, baselines, and statistical analyses. Include the full list of 96 prompts and the evaluation protocol.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** "high-resolution crystallography (1.30 A and 1.77 A) ultimately revealing one to possess a paradigm-shifting novel fold"
- **Evidence pointer** Crystallography results; location not provided
- **Concern** The claim of a "paradigm-shifting novel fold" is extraordinary and requires rigorous structural evidence. The abstract provides no information on how the fold was determined to be novel, what comparison was made against known folds, or what structural features make it paradigm-shifting.
- **Why it matters** A novel fold claim is a major scientific assertion that would attract significant attention. If not properly substantiated, it could mislead the field and damage the credibility of the work.
- **Resolution test** Provide the crystal structures with detailed structural analysis, including a comparison against the PDB and a clear definition of what constitutes a "novel fold" in this context. Include structural figures and a discussion of the fold's features.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "the designs were also active, demonstrating both ATP binding and hydrolysis in vitro"
- **Evidence pointer** Functional assays; location not provided
- **Concern** The abstract claims ATP binding and hydrolysis but provides no quantitative data, no assay conditions, no controls, and no comparison to known ATPases. The reader cannot assess the specificity or efficiency of the activity.
- **Why it matters** Functional activity is a key claim that distinguishes this work from purely computational studies. Without proper evidence, the functional significance of the designs cannot be evaluated.
- **Resolution test** Provide detailed assay data, including kinetic parameters, controls, and a comparison to known ATP-binding proteins. Include the experimental protocols and statistical analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "trained MP4, a transformer-based model that maps natural language prompts to protein sequences, on a dataset of 3.2 billion points and 138k tokens"
- **Evidence pointer** Training dataset; location not provided
- **Concern** The description of the training data is insufficient. "3.2 billion points" is ambiguous, and the relationship between "points" and "tokens" is unclear. The source and nature of the data are not described, nor is the preprocessing or the potential for bias.
- **Why it matters** The validity of the model depends on the quality and composition of the training data. Without a clear description, the reader cannot assess whether the model is learning meaningful relationships or artifacts.
- **Resolution test** Provide a detailed description of the training data, including sources, preprocessing, and a breakdown of the "points" and "tokens." Discuss potential biases and how they were addressed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Benchmark representativeness
- **Affected element** Benchmark of 96 prompts
- **Evidence pointer** Benchmark description; location not provided
- **Issue** The abstract does not describe how the 96 prompts were selected, whether they cover a diverse range of protein functions, or whether they are representative of real-world use cases.
- **Required correction** Describe the prompt selection process and provide a categorization of the prompts by function and complexity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental-computational linkage
- **Affected element** Experimental validation
- **Evidence pointer** Experimental results; location not provided
- **Issue** It is unclear whether the two experimentally validated designs were part of the 96-prompt benchmark or were selected separately. This affects the interpretation of the validation.
- **Required correction** Clarify the relationship between the benchmark designs and the experimentally validated designs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope definition
- **Affected element** Model limitations
- **Evidence pointer** Abstract text
- **Issue** The statement "incomplete coverage and controllability" is vague and does not specify the nature or extent of these limitations.
- **Required correction** Provide a more specific description of the model's limitations, including examples of prompts that fail and the types of proteins that cannot be designed.

## Risk / unsupported claims
- The claim of simultaneous improvement on three metrics is unsupported without numerical data.
- The claim of a "paradigm-shifting novel fold" is unsupported without structural evidence and comparison to known folds.
- The claim of ATP binding and hydrolysis is unsupported without quantitative assay data.
- The claim of "lowering the barrier to protein design" is an extrapolation that is not directly supported by the presented evidence.
- The overall performance of MP4 relative to existing methods cannot be assessed from the abstract alone.