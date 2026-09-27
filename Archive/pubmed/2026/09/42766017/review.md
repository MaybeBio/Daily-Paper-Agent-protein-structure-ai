## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report an AI-driven framework (DeepTM-Bind) using a multi-channel convolutional neural network to design and screen binders targeting the transmembrane domain of BamA in Gram-negative bacteria. They claim high predictive accuracy, successful generation of binders targeting the lateral gate of BamA, and confirmation of structural stability and strong binding via all-atom molecular dynamics simulations and multiscale mechanistic analyses, including a previously unrecognized binding mode.
- **Visible evidence base** Abstract text only; no quantitative results, model performance metrics, simulation details, or experimental validation are provided
- **Missing materials affecting confidence** Full manuscript, methods section, figures, tables, simulation parameters, model training and validation data, and any experimental corroboration

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational approach to a challenging problem, namely targeting the transmembrane domain of an outer membrane protein. However, the claims are largely qualitative and lack the quantitative detail necessary to assess technical soundness or reproducibility. The novelty of the AI framework and the biological significance of the proposed binding mode are not sufficiently established from the provided material. The abstract reads as a high-level summary, but the evidence base is too thin to support the strong conclusions drawn.
- **Who would be interested in the results, and why** Researchers in antimicrobial drug discovery, computational biology, and membrane protein biophysics would be interested. The work addresses a clinically relevant problem (AMR in Gram-negative bacteria) and proposes a novel computational pipeline that could be adapted to other membrane protein targets. Those working on AI-driven protein design and molecular dynamics simulations of membrane proteins may also find the approach relevant.
- **Major strengths** The problem is well motivated and clinically important. The integration of deep learning with molecular dynamics simulations is a sensible and modern approach. The focus on transmembrane domains, which are often neglected in drug design, is a notable strength. The claim of a previously unrecognized binding mode, if substantiated, could be of significant interest.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract lacks any quantitative evidence for the predictive accuracy of DeepTM-Bind, the criteria used in the multidimensional evaluation system, the stability metrics from MD simulations, and the binding affinity estimates. Without these, the core claims are not verifiable.
- **Assessment against Nature-style criteria** Originality: The combination of deep learning and MD for TM domain targeting is not entirely new, but the specific application to BamA may offer some novelty. Scientific importance: The problem is important, but the significance of the findings cannot be assessed without data. Interdisciplinary readership: The work could appeal to a broad audience, but the abstract is too technical and lacks context for nonspecialists. Technical soundness: Not assessable from the abstract. Readability for nonspecialists: The abstract is dense and assumes familiarity with AI and membrane biology; it does not clearly explain the approach or its implications for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises substantial results, but the lack of quantitative detail and validation means the case is not made. I would be supportive if the full manuscript provides the missing evidence and addresses the concerns below.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The framework employs a multi-channel convolutional neural network (DeepTM-Bind), which integrates heterogeneous protein features to achieve high predictive accuracy.
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of high predictive accuracy is made without any supporting metrics, such as area under the curve, precision, recall, or comparison to existing methods. No details are given on the training data, feature encoding, or validation strategy.
- **Why it matters** Predictive accuracy is the foundation of the entire framework. Without quantitative evidence, the reader cannot judge whether the model is reliable or whether the subsequent design steps are meaningful.
- **Resolution test** Provide model performance metrics on a held-out test set, benchmark against existing state-of-the-art methods, and describe the training and validation data in the full manuscript.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** All-atom molecular dynamics simulations within a membrane environment, combined with multiscale mechanistic analyses, confirmed the structural stability and strong binding potential of the candidate molecules, and revealed a previously unrecognized binding mode.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that MD simulations confirmed stability and binding potential, but no quantitative data are provided, such as root-mean-square deviation, binding free energies, or contact analyses. The claim of a previously unrecognized binding mode is intriguing but unsupported without structural or mechanistic details.
- **Why it matters** The biological relevance of the candidates hinges on these simulations. Without quantitative metrics and a clear description of the binding mode, the claim of strong binding and novelty cannot be evaluated.
- **Resolution test** Include simulation parameters, convergence criteria, binding free energy calculations, and a detailed description of the proposed binding mode with supporting figures in the full manuscript.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** Using this integrated approach, binders targeting the lateral gate of BamA were successfully generated.
- **Evidence pointer** Abstract, location not provided
- **Concern** The term successfully generated is vague. It is unclear whether the binders were validated experimentally or only computationally. No information is given on the number of candidates, their sequences, or any experimental validation.
- **Why it matters** Computational predictions without experimental validation are insufficient to establish the practical utility of the approach. The claim of success is ambiguous and could mislead readers.
- **Resolution test** Clarify whether the binders were experimentally tested and, if so, provide experimental data. If only computational, state this explicitly and provide criteria for what constitutes success.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract uses terms such as multidimensional evaluation system and multiscale mechanistic analyses without defining them. This reduces readability and makes it difficult to understand the methodology.
- **Required correction** Briefly define these terms or provide a concise explanation of what they entail in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention any existing approaches for targeting BamA or TM domains, so the novelty of the framework is not contextualized.
- **Required correction** Add a sentence comparing the proposed approach to existing methods or highlighting the gap it addresses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is dense and may be difficult for nonspecialists to follow, particularly the transition from the AI framework to the MD simulations.
- **Required correction** Consider restructuring the abstract to clearly separate the design phase from the validation phase and use simpler language where possible.

## Risk / unsupported claims
- The claim of high predictive accuracy for DeepTM-Bind is unsupported without performance metrics.
- The claim that MD simulations confirmed structural stability and strong binding potential is unsupported without quantitative data.
- The claim of a previously unrecognized binding mode is unsupported without structural or mechanistic details.
- The claim that binders were successfully generated is ambiguous and unsupported without experimental validation or clear success criteria.
- The overall statement that the study provides a promising strategy to combat multidrug-resistant Gram-negative pathogens is an extrapolation not supported by the abstract's evidence.