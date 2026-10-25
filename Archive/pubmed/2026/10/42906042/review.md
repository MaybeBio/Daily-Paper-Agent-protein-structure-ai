## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present MultiRSF, a multimodal deep learning framework that integrates molecular surface fingerprints, contextual sequence embeddings from a pretrained RNA language model, and dot bracket secondary structure encoding to predict RNA-small-molecule binding sites at nucleotide resolution. The model reportedly outperforms state-of-the-art methods on independent benchmark sets TE18 and APO8, with reported precision, recall, and Matthews correlation coefficient values, and demonstrates robustness to moderate RNA flexibility in case studies.
- **Visible evidence base** Abstract text only; no quantitative methodology, benchmark definitions, baseline comparisons, or case study details are available
- **Missing materials affecting confidence** Full manuscript, methods section, model architecture details, training and evaluation protocols, benchmark construction and composition, baseline method descriptions, statistical significance testing, case study descriptions, and all figures and tables

## Reviewer
- **Overall assessment** The abstract describes a potentially useful application of multimodal deep learning to RNA-small-molecule binding site prediction. The integration of surface fingerprints with sequence and structure features is a reasonable direction given the acknowledged limitations of prior methods. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the approach, the validity of the benchmark comparisons, or the robustness claims. The reported performance metrics are promising but cannot be assessed without knowing the evaluation protocol, the composition of the benchmark sets, and the statistical context. The case studies are mentioned but not described in sufficient detail to support the robustness claim. The work may be of interest to the RNA-targeted drug discovery community, but the evidence base is too limited to establish the case from the supplied material.
- **Who would be interested in the results, and why** Researchers in RNA-targeted drug discovery, computational RNA biology, and machine learning applied to biomolecular interaction prediction would be interested. The potential to predict binding sites on apo RNA structures without requiring accurate holo structures addresses a practical bottleneck in early-stage drug discovery. The multimodal fusion approach may also interest those working on integrating heterogeneous biomolecular representations.
- **Major strengths** The problem is well motivated and practically relevant. The proposed integration of molecular surface fingerprints with sequence and secondary structure information is a sensible response to the identified gap in existing methods. The reported performance on independent benchmarks, if reproducible, would represent a meaningful advance. The attention to apo RNA structures and flexibility is a practical consideration that strengthens the potential utility.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The combination of surface fingerprints with language model embeddings and secondary structure encoding appears novel in this application space, though the abstract does not allow verification of the degree of novelty relative to prior work.  
  - Scientific importance: The problem is important for RNA-targeted drug discovery, and a robust apo-structure-based predictor would be valuable. The importance is clear from the abstract.  
  - Interdisciplinary readership: The work bridges computational biology, machine learning, and medicinal chemistry. The abstract is written accessibly, but the likely readership is specialized rather than broad.  
  - Technical soundness: Cannot be assessed from the abstract. The architecture, training, evaluation, and statistical rigor are not described.  
  - Readability for nonspecialists: The abstract is clear and well structured, with technical terms defined in context. It is readable for a scientifically literate audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising, but the technical and statistical claims cannot be evaluated without the full manuscript. A supportive posture would require the methods and results to withstand scrutiny.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that MultiRSF "demonstrates robust predictive performance" and "outperforms state-of-the-art methods" on TE18 and APO8.  
- **Evidence pointer** Abstract only; benchmark definitions and baseline comparisons not provided  
- **Concern** The abstract reports precision, recall, and MCC values for two benchmark sets but provides no information on how these benchmarks were constructed, what the baseline methods were, how hyperparameters were selected, or whether the performance differences are statistically significant.  
- **Why it matters** Without this information, the reported performance cannot be interpreted. The difference between the TE18 and APO8 results, particularly the low recall of 0.286 on APO8, suggests that performance on apo structures may be substantially weaker, which would temper the claim of robustness.  
- **Resolution test** Provide full benchmark descriptions, baseline method details, hyperparameter selection procedures, and statistical significance testing in the manuscript.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that MultiRSF "fuses these features through a hierarchical Transformer encoder" and that this architecture is effective.  
- **Evidence pointer** Abstract only; architecture details not provided  
- **Concern** No details are given on the architecture, including the number of layers, attention heads, feature dimensions, fusion mechanism, training objective, or regularization. The term "hierarchical Transformer encoder" is not defined.  
- **Why it matters** The core methodological contribution is the multimodal fusion architecture. Without architectural details, the approach cannot be reproduced or compared with alternative fusion strategies.  
- **Resolution test** Provide a full methods section with architecture diagrams, hyperparameter values, and ablation studies that justify the design choices.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that case studies on "a ligand-induced riboswitch conformational change and an NMR conformational ensemble" illustrate "robustness to moderate RNA flexibility."  
- **Evidence pointer** Abstract only; case study details not provided  
- **Concern** The case studies are mentioned but not described. No information is given on the specific RNAs, the nature of the conformational changes, the evaluation metrics used, or how "moderate flexibility" was defined.  
- **Why it matters** The robustness claim is a key differentiator of the method, particularly for apo RNA structures. Without details, the claim is unverifiable and may not generalize beyond the specific cases chosen.  
- **Resolution test** Provide full case study descriptions, including the systems studied, the conformational ensembles used, the evaluation protocol, and quantitative results.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The abstract implies that MultiRSF is a usable tool for nucleotide-resolution binding site prediction.  
- **Evidence pointer** Abstract only; no code or data availability statement  
- **Concern** No information is provided on code availability, trained model weights, or access to the benchmark datasets.  
- **Why it matters** For a computational method to be adopted by the community, the code and data must be available. Without this, the claims cannot be independently verified.  
- **Resolution test** Include a data and code availability statement in the manuscript, with a link to a public repository.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "critical first step" is somewhat overstated; binding site identification is important but not necessarily the first step in all RNA-targeted drug discovery workflows.  
- **Required correction** Rephrase to "an important early step" or similar.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, results sentence  
- **Issue** The phrase "robust predictive performance" is vague. The reported metrics vary substantially between TE18 and APO8, which may not support the word "robust" without qualification.  
- **Required correction** Qualify the claim, for example by noting that performance is stronger on holo structures and weaker but still competitive on apo structures.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, conclusion  
- **Issue** The abstract does not mention any limitations of the method, such as dependence on secondary structure prediction quality or computational cost.  
- **Required correction** Add a sentence acknowledging limitations in the abstract or ensure they are discussed in the manuscript.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, methods description  
- **Issue** The term "pretrained RNA language model" is not specified. The specific model used should be named.  
- **Required correction** Name the specific pretrained model in the abstract or methods.

## Risk / unsupported claims
- The claim that MultiRSF "outperforms state-of-the-art methods" is unsupported without baseline details and statistical testing.
- The claim of "robustness to moderate RNA flexibility" is unsupported without case study details.
- The claim that the method is "accurate and generalizable" is unsupported without cross-validation or external validation details.
- The reported performance metrics cannot be evaluated without benchmark construction details.
- The novelty of the approach relative to prior work cannot be assessed from the abstract alone.