## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided for review
- **Shared manuscript claim summary** The authors present a curated NMR chemical shift dataset to benchmark protein foundation models on backbone 15N chemical shift prediction. They report that the largest prediction errors occur in core residues with evidence of fast-timescale dynamics, investigate this mechanistically with molecular dynamics simulations, and introduce SLAE-ERR, a model trained to predict its own error, achieving a mean absolute error of 0.76 ppm.
- **Visible evidence base** Abstract text only; no dataset description, benchmark results, simulation details, or model architecture information are available
- **Missing materials affecting confidence** Full manuscript, dataset curation details, benchmark methodology, model architecture and training details, molecular dynamics simulation parameters, all figures and tables, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract presents a potentially valuable resource and an interesting observation about protein foundation model limitations. The concept of using NMR chemical shifts as a fine-grained probe of model-learned biochemistry is well motivated and could be of broad interest. However, the abstract alone provides insufficient evidence to evaluate the validity of the central claims. The reported error analysis, mechanistic investigation, and the performance of SLAE-ERR cannot be assessed without access to the underlying data and methodology. The claim that the largest errors occur in dynamic core residues is intriguing but requires statistical support and clear definitions of "core" and "fast-timescale dynamics" that are not available in the abstract.
- **Who would be interested in the results, and why** Computational biologists and protein engineers developing or using protein foundation models would be interested in understanding model limitations and failure modes. NMR spectroscopists and structural biologists may value the curated chemical shift dataset as a community resource. Researchers working on protein dynamics and its functional implications could find the connection between model errors and dynamic regions biologically meaningful. Machine learning researchers focused on uncertainty quantification in biomolecular prediction tasks may also find the error-prediction approach relevant.
- **Major strengths** The use of NMR chemical shifts as per-atom reporters of local chemical environment is a well-reasoned choice for exposing model failure modes. The focus on dynamic core residues connects model limitations to biologically relevant phenomena. The development of an error-prediction model is a practical contribution that could guide model improvement efforts.
- **Major Concerns** The abstract does not provide enough information to evaluate the dataset curation quality, the benchmark methodology, the statistical significance of the error patterns, or the validity of the mechanistic interpretation. The performance metric for SLAE-ERR is reported without context, making it impossible to judge whether 0.76 ppm is a meaningful improvement over baselines.
- **Minor Comments** The abstract would benefit from clarifying what "systematically curated" means in terms of experimental confounders. The choice of 15N chemical shifts specifically, rather than other nuclei, is mentioned but not justified in the abstract. The relationship between the error-prediction model and potential downstream use for protein design is stated but not elaborated.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The approach of using NMR chemical shifts to probe foundation model limitations appears novel, though the abstract alone cannot confirm this. Scientific importance: The question of what biochemistry these models have learned is timely and important for the field. Interdisciplinary readership: The work bridges machine learning, structural biology, and NMR spectroscopy, which could appeal to a broad audience. Technical soundness: Cannot be evaluated from the abstract; the reported error analysis and mechanistic claims require full methodological detail. Readability for nonspecialists: The abstract is generally accessible, though terms like "fast-timescale dynamics" and "per-atom reporters" may require domain knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising direction, but the central claims cannot be verified without the full manuscript and supporting data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the largest error across all models is in core residues with evidence of fast-timescale dynamics.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports this as a central finding but provides no quantitative data, statistical analysis, or comparison across models to support the claim. The definitions of "core residues" and "evidence of fast-timescale dynamics" are not specified, and no error distributions or effect sizes are presented.
- **Why it matters** This claim is the primary scientific observation of the work and motivates the subsequent mechanistic investigation and the development of SLAE-ERR. Without statistical support and clear operational definitions, the claim cannot be evaluated or reproduced.
- **Resolution test** Provide error distributions for core versus non-core residues across all benchmarked models, with appropriate statistical tests. Define the criteria for "core" and for "evidence of fast-timescale dynamics" operationally, and show that the observed pattern is consistent across models and datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that they investigate the mechanistic basis of the error pattern using molecular dynamics simulations.
- **Evidence pointer** Abstract only; location not provided
- **Concern** No details are given about the simulation system, force field, sampling protocol, or how the simulations connect to the observed chemical shift prediction errors. The mechanistic link between simulated dynamics and model errors is asserted but not demonstrated.
- **Why it matters** The mechanistic interpretation is a key contribution that elevates the work beyond a benchmark study. Without methodological detail and a clear logical chain from simulations to error patterns, the interpretation remains speculative.
- **Resolution test** Describe the simulation setup and analysis pipeline. Show that the simulated dynamic properties correlate with prediction errors in a statistically meaningful way, and rule out alternative explanations such as sequence-based biases or structural annotation errors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that SLAE-ERR achieves a mean absolute error of 0.76 ppm for predicting its own error.
- **Evidence pointer** Abstract only; location not provided
- **Concern** A single mean absolute error value is reported without context. No baseline comparisons, cross-validation procedures, or error distributions are provided. It is unclear whether 0.76 ppm represents a meaningful improvement over trivial baselines such as predicting the mean error or using simpler features.
- **Why it matters** The utility of SLAE-ERR depends on its predictive performance relative to existing methods. Without comparative evaluation, the contribution of this model cannot be assessed.
- **Resolution test** Report SLAE-ERR performance against appropriate baselines, including feature ablation and comparison to simpler models. Provide cross-validated metrics and error distributions to demonstrate robust predictive performance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim to present a systematically curated chemical shift dataset designed to minimize experimental confounders.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The curation criteria, filtering steps, and quality control measures are not described. The scope of the dataset, including the number of proteins, sequence diversity, and experimental conditions, is not stated. The claim of systematic curation cannot be verified.
- **Why it matters** The dataset is a primary contribution of the work and underpins all benchmark results. If the curation is not transparent and reproducible, the validity of the downstream analyses is compromised.
- **Resolution test** Provide a detailed description of the curation pipeline, including inclusion and exclusion criteria, quality metrics, and validation against known chemical shift trends. Make the dataset and curation scripts publicly available.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract, "systematically curated chemical shift dataset designed to minimize experimental confounders"
- **Issue** The phrase "systematically curated" is vague and does not convey what specific confounders were addressed or how.
- **Required correction** Specify the types of experimental confounders considered, such as temperature, pH, or referencing inconsistencies, and briefly indicate the curation strategy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Justification
- **Affected element** Abstract text
- **Evidence pointer** Abstract, "backbone 15N chemical shifts, atoms that are known to be sensitive to many effects"
- **Issue** The choice of 15N chemical shifts is stated but not justified in the abstract. The reader is left to infer why this nucleus is the most informative probe for the stated purpose.
- **Required correction** Add a brief justification for why 15N chemical shifts are particularly suited for exposing model limitations, such as their sensitivity to hydrogen bonding, backbone conformation, and dynamics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract, "SLAE-ERR achieves a mean absolute error of 0.76 ppm for predicting error"
- **Issue** The sentence is ambiguous regarding whether 0.76 ppm refers to the error in predicting chemical shifts or the error in predicting the model's own prediction error. The intended meaning is likely the latter, but the phrasing is unclear.
- **Required correction** Rephrase to explicitly state that SLAE-ERR predicts the per-residue error of the base model, and that the mean absolute error of this error prediction is 0.76 ppm.

## Risk / unsupported claims

- The claim that the largest prediction errors occur in core residues with fast-timescale dynamics is unsupported without quantitative data and statistical analysis.
- The mechanistic interpretation based on molecular dynamics simulations is unverifiable from the abstract alone.
- The performance of SLAE-ERR at 0.76 ppm mean absolute error is uninterpretable without baseline comparisons and evaluation details.
- The claim of a systematically curated dataset is unverifiable without a description of the curation methodology.
- The general statement that the work provides "sources of guidance for protein design model improvement" is a forward-looking assertion that cannot be evaluated from the abstract.