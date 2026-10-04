## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material provided
- **Shared manuscript claim summary** The authors propose Protein eXplosion Imaging (PXI), a method to retrieve low-resolution structural information of single proteins from the distribution of ion trajectories produced by laser-driven explosions. Using molecular-dynamics simulations and machine learning, they report prediction errors of 1.2 Å for radius of gyration and 1.5 Å for ellipsoidal semi-axes, with an analytical model performing best for globular structures. They further claim that higher-level structural information and symmetries can be extrapolated, supporting structural determination without large-scale X-ray facilities.
- **Visible evidence base** Abstract text only; no simulation details, dataset descriptions, model architectures, error metrics, or comparative benchmarks are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation parameters, training and validation protocols, statistical analyses, and any discussion of limitations or comparison to existing techniques

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting idea with potentially broad implications for single-molecule structural biology. However, the evidence provided is insufficient to evaluate the technical soundness or the validity of the central claims. The reported prediction errors are stated without context regarding dataset size, variability, or baseline comparisons. The claim that higher-level structural information can be extrapolated is vague and unsupported. The feasibility of the approach for real experimental conditions, where initial ionization states and explosion dynamics are far more complex than typical simulations, is not addressed. The manuscript may have merit, but the current abstract alone does not establish the case.
- **Who would be interested in the results, and why** Structural biologists seeking alternatives to X-ray free-electron lasers and synchrotrons for single-particle imaging; researchers in computational biophysics and molecular dynamics; scientists developing machine-learning approaches for inverse problems in structural biology; and the broader community interested in label-free, high-intensity laser-based imaging methods.
- **Major strengths** The idea of using explosion ion trajectories for structural retrieval is novel and potentially disruptive. The combination of molecular-dynamics simulations, machine learning, and an analytical model provides a multi-pronged validation strategy. The reported accuracy, if reproducible, would be useful for low-resolution envelope determination. The potential to avoid large-scale facilities is an important practical advantage.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: High. The concept of retrieving structure from explosion ion distributions appears novel and not a straightforward extension of existing methods.  
  - Scientific importance: Potentially high if the method proves experimentally feasible, but the current evidence does not demonstrate this.  
  - Interdisciplinary readership: The topic bridges physics, chemistry, biology, and machine learning, which could attract a broad audience.  
  - Technical soundness: Not assessable from the abstract alone. Critical details on simulations, training, and validation are missing.  
  - Readability for nonspecialists: The abstract is concise and generally clear, though terms like "spherical ion maps" and "ellipsoidal molecular envelope" may require some background.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract does not provide sufficient detail to assess the validity of the claims. A full manuscript with methods and results would be required for a supportive posture.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that an ensemble of convolutional neural networks recovers the radius of gyration and the three semi-axes of an ellipsoidal molecular envelope with prediction errors of 1.2 Å and 1.5 Å, respectively.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract reports prediction errors without any indication of the test set size, the diversity of protein structures used, the range of target values, or the uncertainty in the estimates. It is unclear whether these errors are averaged over many conditions or represent best-case scenarios.  
- **Why it matters** Without this context, the reported accuracy cannot be interpreted. A 1.2 Å error on the radius of gyration may be trivial if the target values span a wide range, or it may be misleading if the test set is small or biased.  
- **Resolution test** Provide the full methods and results, including the distribution of prediction errors, the number of test cases, the range of protein sizes and shapes, and a comparison to a null model or baseline predictor.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that an analytical ellipsoid charge model returns similar estimates and performs best for globular structures.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The analytical model is mentioned but not described. There is no information on its assumptions, its input parameters, or how it was benchmarked against the neural network approach. The claim that it "performs best for globular structures" is not quantified.  
- **Why it matters** The analytical model is presented as a key validation of the machine-learning results. Without a description of the model and its performance metrics, the reader cannot assess whether the two approaches are truly consistent or whether the comparison is meaningful.  
- **Resolution test** Describe the analytical model in detail, including its derivation and assumptions, and provide quantitative comparisons to the neural network results across a range of protein shapes.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The authors claim that "higher-level structural information and symmetries can be extrapolated from ion measurements."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** This is a broad and vague claim. No specific examples of higher-level information or symmetries are given, and no evidence is presented to support the extrapolation. It is unclear what is meant by "higher-level" and how this would be achieved.  
- **Why it matters** This claim suggests the method has capabilities beyond low-resolution envelope determination, which would significantly increase its impact. However, without evidence, it remains speculative and could overstate the method's potential.  
- **Resolution test** Provide specific examples of higher-level structural features or symmetries that were recovered, with quantitative results and a clear description of the methodology used.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The authors conclude that the study "supports the viability for structural determination of single proteins without large-scale X-ray facilities."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract is based entirely on simulations. There is no discussion of how the simulated conditions relate to real experimental scenarios, such as the initial charge state of the protein, the laser pulse parameters, the detection efficiency, or the noise in ion trajectory measurements. The leap from simulation to experimental viability is not justified.  
- **Why it matters** The central motivation of the work is to provide an alternative to large-scale facilities. If the method only works under idealized simulation conditions, its practical relevance is limited. The claim of viability is therefore premature.  
- **Resolution test** Include a discussion of experimental feasibility, including known challenges and how they might be addressed, or temper the claim to reflect the simulation-based nature of the study.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "spherical ion maps" is used without definition. It is unclear whether this refers to a specific representation of the ion trajectories or a general concept.  
- **Required correction** Define "spherical ion maps" in the abstract or provide a brief explanation of how the ion trajectories are represented.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not specify the type of proteins used in the simulations (e.g., size range, fold classes, or number of residues). This limits the generalizability of the results.  
- **Required correction** Add a brief description of the protein dataset used in the simulations, including the range of sizes and structural diversity.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "benchmarked against an analytical approach" is vague. It is not clear what the benchmarking involved or what metrics were used.  
- **Required correction** Clarify the benchmarking procedure, such as comparing predictions to known ground-truth values or comparing the two methods' outputs on the same test set.

## Risk / unsupported claims
- The claim that "higher-level structural information and symmetries can be extrapolated from ion measurements" is unsupported by any evidence in the abstract.
- The claim that the study "supports the viability for structural determination of single proteins without large-scale X-ray facilities" is not supported, as the abstract provides no experimental validation or discussion of real-world feasibility.
- The reported prediction errors (1.2 Å and 1.5 Å) are uninterpretable without context on the test set and target value ranges.
- The performance comparison between the neural network ensemble and the analytical model is not quantifiable from the abstract.