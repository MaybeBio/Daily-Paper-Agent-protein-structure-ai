## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present a computational protocol that integrates DEER distance measurements with deep learning-based structure prediction and molecular dynamics simulations to reconstruct all-atom models of the TRV026-bound AT1R. They report a new clustering method that identifies ligand-receptor interactions, localized receptor flexibility, and ligand bias, and they propose the framework as a means to validate neural-network predictions and capture rare signaling states.
- **Visible evidence base** Abstract text only; no quantitative results, validation metrics, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, DEER data, simulation parameters, clustering algorithm details, validation statistics, and any comparison with experimental structures or functional assays

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable integrative approach for modeling GPCR conformational states using DEER restraints combined with deep learning and molecular dynamics. The biological context, focusing on intra-transducer bias at AT1R, is timely and of interest to the GPCR community. However, the abstract provides no quantitative evidence, no validation of the reconstructed models, and no demonstration that the protocol outperforms existing approaches. The central claims regarding the identification of key interactions and the framework's utility for therapeutic design are not supported by any visible data. The work may be of interest if the full manuscript provides rigorous validation, but from the abstract alone the case is not established.
- **Who would be interested in the results, and why** Structural biologists studying GPCR conformational dynamics, computational chemists developing integrative modeling pipelines, and pharmacologists interested in biased agonism and structure-based drug design. The potential to link DEER-derived distance restraints with deep learning predictions could appeal to researchers working on membrane proteins where conformational heterogeneity limits traditional structural methods.
- **Major strengths** The integration of experimental DEER restraints with deep learning and molecular dynamics is a sensible strategy to address the challenge of capturing rare or transient GPCR states. The focus on intra-transducer bias is a nuanced and current topic that extends beyond conventional ligand bias. The stated goal of validating neural-network predictions against experimental data is a worthwhile objective.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  - Originality: The combination of DEER data with deep learning and MD is not entirely new, but the specific application to intra-transducer bias at AT1R may offer a novel angle. The abstract does not clarify what is methodologically distinct from prior integrative modeling efforts.  
  - Scientific importance: The topic is important for understanding GPCR signaling and biased agonism, but the abstract does not demonstrate that the findings advance fundamental understanding beyond what is already known about TRV026 and AT1R.  
  - Interdisciplinary readership: The work could appeal to structural biology, computational chemistry, and pharmacology audiences, but the abstract is written at a level that assumes familiarity with DEER, deep learning, and GPCR signaling, which may limit broader accessibility.  
  - Technical soundness: Cannot be assessed from the abstract. No validation metrics, error analysis, or comparison with experimental structures are provided.  
  - Readability for nonspecialists: The abstract is concise but uses field-specific jargon without sufficient context. Terms such as "intra-transducer bias" and "DEER" are not explained for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient support for the central claims. A supportive posture would require the full manuscript to demonstrate rigorous validation of the reconstructed models, quantitative comparison with experimental data, and clear evidence that the clustering method yields biologically meaningful insights.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The protocol "reconstruct[s] all-atom models of TRV026-bound AT1R" and the clustering method "identif[ies] key ligand-receptor interactions underlying high-affinity binding, localized receptor flexibility, and ligand bias."  
- **Evidence pointer** Abstract only; no figures, tables, or methods provided  
- **Concern** The abstract claims successful reconstruction of all-atom models and identification of key interactions, but no validation data are presented. There is no indication of how model accuracy was assessed, whether the models were compared with experimental structures, or what the uncertainty in the DEER-derived restraints was.  
- **Why it matters** Without validation, the reconstructed models could be artifacts of the computational pipeline. The claim that specific interactions underlie high-affinity binding and bias requires experimental or structural corroboration.  
- **Resolution test** Provide in the full manuscript a comparison of the reconstructed models with available experimental structures of AT1R, cross-validation of DEER restraints, and metrics such as root-mean-square deviation or distance error distributions. Show that the identified interactions are supported by mutagenesis or functional data.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The "new clustering method" identifies localized receptor flexibility and ligand bias.  
- **Evidence pointer** Abstract only; no methodological description provided  
- **Concern** The abstract introduces a new clustering method but provides no details on its algorithm, parameters, or how it differs from existing approaches. There is no evidence that the clustering results are robust or reproducible.  
- **Why it matters** A new method must be described with sufficient detail to be evaluated and reproduced. Without this, the claim that it identifies meaningful features is unverifiable.  
- **Resolution test** Describe the clustering algorithm in the methods section, including input features, distance metrics, and validation against known conformational states. Demonstrate reproducibility across independent simulations or bootstrapped datasets.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The framework "provid[es] a framework for validating neural-network predictions and physics-based simulations to capture rare signaling states."  
- **Evidence pointer** Abstract only; no comparative data provided  
- **Concern** The abstract asserts that the framework can validate neural-network predictions and capture rare states, but no evidence is shown that the protocol successfully captured a state that other methods missed, or that the validation approach is superior to existing benchmarks.  
- **Why it matters** The broader significance of the work depends on demonstrating that the integrative approach adds value beyond standard MD or deep learning alone. Without a comparative analysis, the claim is speculative.  
- **Resolution test** Include a benchmark against conventional MD simulations or existing GPCR structure prediction methods, showing that the DEER-restrained approach improves accuracy or captures states not accessible otherwise.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Scientific importance  
- **Claim pointer** The results "identify key ligand-receptor interactions underlying high-affinity binding, localized receptor flexibility, and ligand bias."  
- **Evidence pointer** Abstract only; no functional or experimental data provided  
- **Concern** The abstract implies that the identified interactions are mechanistically linked to ligand bias, but no experimental validation such as mutagenesis, functional assays, or binding affinity measurements is mentioned.  
- **Why it matters** Computational predictions of interaction hotspots require experimental confirmation to establish biological relevance. Without this, the mechanistic claims remain speculative.  
- **Resolution test** Provide experimental data in the full manuscript, such as site-directed mutagenesis of predicted contact residues followed by binding or signaling assays, to confirm the functional role of the identified interactions.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The term "intra-transducer bias" is used without definition or context, which may confuse readers unfamiliar with recent GPCR signaling literature.  
- **Required correction** Add a brief explanatory phrase, for example "a mechanism where ligand efficacy is determined by the architecture of the receptor-transducer complex rather than the transducer subtype alone."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, sentence describing the clustering method  
- **Issue** The abstract states "using a new clustering method" but does not name the method or indicate whether it is a modification of an existing algorithm.  
- **Required correction** Provide the method name or a brief description in the abstract, or clarify that full details are in the methods section.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, final sentence  
- **Issue** The claim that the framework can "identify target conformations for designing more functionally selective, efficacious therapeutics" is presented without any example or proof-of-concept application.  
- **Required correction** Either temper the claim to reflect the methodological nature of the work or include a brief example of how the identified conformations could inform drug design.

## Risk / unsupported claims
- The claim that the protocol "reconstruct[s] all-atom models" of TRV026-bound AT1R is unsupported without validation data.
- The claim that the clustering method identifies "key ligand-receptor interactions underlying high-affinity binding" is unsupported without experimental or structural corroboration.
- The claim that the framework "provid[es] a framework for validating neural-network predictions" is unverifiable without comparative benchmarks.
- The claim that the results "identify ... ligand bias" is unsupported without functional assays linking specific conformations to biased signaling outcomes.
- The overall utility for therapeutic design is asserted but not demonstrated with any example or case study.