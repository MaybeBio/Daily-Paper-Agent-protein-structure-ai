## Review setup
- **Input scope** Full manuscript text (protocol article)
- **Assessment boundary** Scientific and technical soundness of the protocol as described, clarity and reproducibility of the procedures, and alignment with the stated claims. No assessment of the underlying MViewEMA method's performance beyond what is stated in the protocol.
- **Shared manuscript claim summary** The manuscript presents a step-by-step protocol for using MViewEMA, a single-model deep learning framework, to estimate the global accuracy (TM-score-based confidence) of protein complex structural models from a single input structure. The protocol claims efficiency, independence from prediction pipelines, and applicability to large-scale model ranking and selection.
- **Visible evidence base** Full protocol text including Abstract, Background, Equipment, Software and datasets, Procedure, Validation of protocol, General notes and troubleshooting, and Acknowledgements. No figures, tables, or supplementary data were provided.
- **Missing materials affecting confidence** The "Validation of protocol" section is empty; no reference to the original research article is provided. No benchmark results, performance metrics, or comparative analyses are included. Figures referenced in the Procedure (Figures 1–6) are not available. The Graphical overview is mentioned but not shown.

## Reviewer
- **Overall assessment** This protocol describes a practical workflow for a potentially useful tool in protein structure model quality assessment. The writing is clear and the procedural steps are logically organized. However, the manuscript lacks any validation data or performance benchmarks, which is a critical omission for a protocol claiming efficiency and accuracy. The empty "Validation of protocol" section and the absence of any quantitative evidence make it impossible to assess whether the protocol delivers on its stated claims. The protocol is technically plausible but currently not established from the provided evidence.
- **Who would be interested in the results, and why** Computational structural biologists, bioinformaticians, and researchers involved in protein structure prediction and model selection. The protocol offers a potentially fast, pipeline-independent method for ranking protein complex models, which would be valuable in high-throughput settings and for downstream functional annotation.
- **Major strengths** The protocol is clearly written with a logical step-by-step structure. The distinction between local and web-server execution is practical. The troubleshooting section addresses common user issues. The claim of independence from MSAs, templates, and language models is a potentially significant advantage in terms of computational cost.
- **Major Concerns** The absence of any validation data or performance benchmarks is a major issue. The protocol cannot be assessed for its claimed efficiency or accuracy without quantitative evidence. The empty "Validation of protocol" section is a critical gap. Additionally, the protocol does not provide any guidance on expected runtime, accuracy ranges, or how to interpret the output scores in practice.
- **Minor Comments** The Equipment section could benefit from more specific hardware recommendations. The Procedure section would be improved by including example input/output files. The troubleshooting section could be expanded to cover common errors in the local execution workflow.
- **Technical failings that need to be addressed before the case is established** The lack of validation data and performance benchmarks is the primary technical failing. Without this, the protocol's claims of efficiency and accuracy cannot be verified.
- **Assessment against Nature-style criteria**  
  - Originality: The multi-view representation learning approach is a novel contribution to the EMA field, but the protocol itself does not present new scientific findings.  
  - Scientific importance: The topic is relevant and timely, but the importance cannot be fully assessed without validation data.  
  - Interdisciplinary readership: The protocol is primarily of interest to computational biologists and bioinformaticians; broader interdisciplinary appeal is limited.  
  - Technical soundness: The described workflow is technically plausible, but the lack of validation undermines confidence in its soundness.  
  - Readability for nonspecialists: The protocol is generally readable, but some sections assume familiarity with deep learning and structural biology terminology.
- **Recommendation posture** Currently not established from the provided evidence. The protocol requires the addition of validation data and performance benchmarks before it can be considered for publication.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence
- **Claim pointer** The protocol claims to provide an "efficient and accurate" method for global accuracy estimation of protein complex models.
- **Evidence pointer** "Validation of protocol" section; location not provided
- **Concern** The "Validation of protocol" section is empty. No benchmark results, performance metrics, or comparisons with existing methods are provided. The protocol's claims of efficiency and accuracy are therefore unsupported.
- **Why it matters** A protocol for a computational method must demonstrate that the method works as described. Without validation data, readers cannot assess the reliability of the output scores or the practical utility of the protocol.
- **Resolution test** Provide a summary of the validation results from the original research article, including benchmark datasets, performance metrics (e.g., correlation with true TM-scores), and comparisons with existing EMA methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The protocol states that MViewEMA "extracts residue–residue interaction features from complementary micro-, meso-, and macro-environmental perspectives" and integrates them via "multi-view representation learning."
- **Evidence pointer** "Procedure" section; location not provided
- **Concern** The protocol does not provide any details on the feature extraction algorithms, the neural network architectures, or the training procedure. A user following the protocol would not be able to understand or modify the underlying method.
- **Why it matters** For a protocol to be reproducible and adaptable, it must provide sufficient technical detail. The current description is too high-level for a user to troubleshoot or extend the method.
- **Resolution test** Add a detailed description of the feature extraction and model architecture, or provide a reference to a peer-reviewed publication that contains these details.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness
- **Claim pointer** The protocol states that it "enables large-scale evaluation and selection of predicted models."
- **Evidence pointer** "Procedure" section, "General notes and troubleshooting" section; location not provided
- **Concern** The protocol does not provide any information on expected runtime, memory usage, or scalability. The troubleshooting section mentions "long waiting time" and "memory or sequence-length limitations" but does not quantify these or provide guidance on system requirements for large-scale use.
- **Why it matters** The claim of large-scale applicability cannot be assessed without information on computational requirements. Users need to know whether the method is feasible for their hardware and dataset sizes.
- **Resolution test** Provide benchmark runtime and memory usage for representative protein complex sizes, and specify minimum and recommended hardware requirements.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equipment section
- **Evidence pointer** "Equipment" section; location not provided
- **Issue** The hardware recommendations are vague. For example, "x86-64 architecture CPU (≥8 cores)" does not specify clock speed or generation, and "NVIDIA GPU with CUDA support (≥16 GB VRAM)" does not specify a minimum compute capability.
- **Required correction** Provide more specific hardware recommendations, including minimum and recommended specifications.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Usability
- **Affected element** Procedure section, Step A.2.a
- **Evidence pointer** "Procedure" section; location not provided
- **Issue** The protocol states that input files must be in "standard PDB format" but does not provide an example or a link to the PDB format specification.
- **Required correction** Include a link to the PDB format specification or provide a minimal example PDB file.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Procedure section, Step B.1.b
- **Evidence pointer** "Procedure" section; location not provided
- **Issue** The protocol mentions that the web server accepts "up to 10 models per submission" but does not specify a maximum file size or total size limit for ZIP uploads.
- **Required correction** Specify file size limits for individual files and ZIP archives.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Output format, Step A.5
- **Evidence pointer** "Procedure" section; location not provided
- **Issue** The protocol states that the output is a "TM-score-based confidence" but does not explain how this score should be interpreted or what range of values is expected.
- **Required correction** Add a brief explanation of the output score, including its range and how to interpret it for model ranking.

## Risk / unsupported claims
- The claim of "efficient and accurate" estimation is unsupported due to the absence of validation data.
- The claim of "large-scale evaluation" is unsupported due to the lack of runtime and scalability benchmarks.
- The claim of independence from "MSAs, templates, protein language models, or consensus information" is stated but not demonstrated with comparative data.
- The "Validation of protocol" section is empty, making it impossible to verify that the protocol has been used successfully in any research context.