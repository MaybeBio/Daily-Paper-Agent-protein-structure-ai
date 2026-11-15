## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, with reference to the linked repository as a supporting resource
- **Shared manuscript claim summary** The authors introduce sparse autoencoders (SAEs) into ProteinMPNN to expand its latent space, uncover correlations between sparse activations and protein features (secondary structure, residue volume, residue shape, disulfide bridges, ligand coordination), and demonstrate that manipulating sparse activations yields a Brolucizumab variant with improved thermostability relative to variants from traditional machine learning methods, as assessed by high temperature molecular dynamics simulations.
- **Visible evidence base** Abstract text; repository URL (https://github.com/neelmukkavilli/SAEProteinMPNN) mentioned but not inspected
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, methods descriptions, quantitative results, statistical analyses, and simulation details are not provided. The repository is referenced but its contents were not available for review.

## Reviewer

- **Overall assessment** The abstract presents an ambitious and potentially valuable application of sparse autoencoders to a widely used protein design model. The core idea, that SAEs can render polysemantic activations in ProteinMPNN more interpretable and manipulable, is timely and of broad interest. However, the abstract alone provides insufficient evidence to evaluate the validity of the central claims. Key quantitative outcomes, methodological details, and validation procedures are absent. The claim of improved thermostability over traditional methods is particularly consequential and cannot be assessed without detailed simulation protocols and comparative baselines. The work is promising in concept but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in protein design, machine learning interpretability, and computational biology would be interested. The work addresses a recognized limitation of black-box protein sequence models and proposes a concrete interpretability tool. Those developing or using ProteinMPNN and related models would value mechanistic insights and a pathway to targeted sequence modification. The thermostability application is relevant to therapeutic protein engineering, particularly for antibody fragments.
- **Major strengths** The choice of ProteinMPNN as a target is well motivated given its widespread adoption. The use of SAEs is a current and technically appropriate approach for addressing polysemanticity. The abstract identifies a specific set of protein features for correlation analysis, which provides a concrete framework for interpretability. The demonstration of a practical application, thermostability improvement, elevates the work beyond descriptive analysis.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that sparse activations can be manipulated to produce a Brolucizumab variant that is more thermostable than variants produced by traditional machine learning methods.
  - **Evidence pointer** Abstract, thermostability statement; location not provided
  - **Concern** The abstract states that the SAE-derived variant is more thermostable than variants from traditional machine learning methods, but no quantitative data, simulation parameters, or comparative statistics are provided. The basis for this comparison is unclear, including which traditional methods were used, how thermostability was measured, and whether the comparison was controlled for sequence context or computational cost.
  - **Why it matters** This is the most consequential claim in the abstract. If the thermostability improvement is not rigorously demonstrated with appropriate controls and error estimates, the practical utility of the SAE approach is not established. Overstated claims of improvement over existing methods could mislead downstream users.
  - **Resolution test** Provide quantitative thermostability metrics (for example, melting temperature estimates or free energy differences) for the SAE-derived variant, for variants from the traditional methods, and for the wild type, with uncertainty estimates. Specify the molecular dynamics protocol, force field, simulation length, and analysis methods. Demonstrate that the comparison is fair, for example by using identical simulation conditions and comparable sequence diversity.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that SAEs uncover correlations between sparse activations and protein features such as secondary structure, residue volume, residue shape, disulfide bridges, and coordination to ligands.
  - **Evidence pointer** Abstract, feature correlation statement; location not provided
  - **Concern** The abstract lists several protein features but provides no information on the strength, significance, or specificity of the reported correlations. It is unclear whether these correlations are robust across protein families, whether they are causal or merely associative, and whether the SAE dimensions are consistently interpretable or only in a subset of cases.
  - **Why it matters** The interpretability claim is the foundation of the paper. Without quantitative measures of correlation quality, such as correlation coefficients, significance thresholds, or validation on held-out proteins, the reader cannot judge whether the SAE features are genuinely meaningful or an artifact of the expansion procedure.
  - **Resolution test** Report correlation coefficients and significance values for each protein feature against the relevant sparse dimensions. Show that the correlations generalize across a diverse test set of proteins not used in training the SAE. Provide examples of dimensions that are interpretable and quantify the fraction of dimensions that are not.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that SAEs expand the latent space of ProteinMPNN and that this expansion uncovers correlations between activations and protein features.
  - **Evidence pointer** Abstract, SAE introduction statement; location not provided
  - **Concern** The abstract does not describe the SAE architecture, training procedure, or how the SAE was integrated with ProteinMPNN. Key details such as the size of the expanded latent space, the sparsity penalty, the training data, and the reconstruction fidelity of the SAE are absent. Without these, the technical validity of the approach cannot be assessed.
  - **Why it matters** Sparse autoencoders are sensitive to hyperparameter choices and training protocols. If the SAE is poorly trained or the expansion is not faithful to the original activations, the subsequent interpretability and manipulation claims are compromised. The technical setup determines whether the results are reproducible and meaningful.
  - **Resolution test** Provide a full description of the SAE architecture, including layer sizes, activation functions, sparsity regularization, and training data. Report reconstruction error or fidelity metrics for the SAE on held-out activations. Describe how the SAE was inserted into the ProteinMPNN pipeline and whether the original model outputs are preserved.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, feature list
  - **Evidence pointer** Abstract, feature correlation statement; location not provided
  - **Issue** The list of protein features is presented without any indication of how each feature was defined or computed. For example, residue volume and residue shape are related but distinct concepts, and their operational definitions matter for interpretation.
  - **Required correction** Define each feature and specify the computational method used to assign it to residues or positions in the protein structure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Abstract, repository reference
  - **Evidence pointer** Abstract, repository URL; location not provided
  - **Issue** The repository is mentioned but no version, license, or usage instructions are given. The abstract does not state whether the code and data are sufficient to reproduce the reported results.
  - **Required correction** Provide a clear statement on code availability, including versioning, dependencies, and instructions for reproducing the key figures and results.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scope
  - **Affected element** Abstract, thermostability claim
  - **Evidence pointer** Abstract, thermostability statement; location not provided
  - **Issue** The abstract claims improvement over traditional machine learning methods but does not specify which methods were compared. This makes the claim difficult to contextualize.
  - **Required correction** Name the traditional methods used for comparison and briefly describe why they were chosen as baselines.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results, methodological detail, and validation protocols means that none of the three central claims (interpretability, manipulability, thermostability improvement) can be verified from the supplied material.
- **Assessment against Nature-style criteria** Originality is high. Applying SAEs to a protein sequence model for interpretability and targeted manipulation is a novel contribution that extends prior interpretability work in language models to a new domain. Scientific importance is potentially high, given the broad use of ProteinMPNN and the general need for interpretable protein design tools. Interdisciplinary readership is plausible, as the work bridges machine learning, structural biology, and protein engineering. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is adequate in the abstract, though the feature list and the thermostability claim would benefit from more explicit explanation. Overall, the work has strong potential but the current evidence base is insufficient to support the claims.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising and the direction is worthwhile, but the abstract does not provide the quantitative and methodological support needed to validate the central claims. A full manuscript with detailed methods, results, and validation would be required to assess whether the case can be made.

## Risk / unsupported claims

- The claim that SAE-derived Brolucizumab variants are more thermostable than variants from traditional machine learning methods is unsupported. No quantitative data, simulation details, or comparative baselines are provided.
- The claim that SAEs uncover correlations between sparse activations and protein features is unsupported. No correlation coefficients, significance values, or validation on held-out data are provided.
- The claim that sparse activations can be manipulated to produce a desired variant is unsupported. The mechanism of manipulation and the success rate or specificity of the manipulation are not described.
- The general claim that SAEs provide mechanistic understanding of protein design models is not established. The abstract demonstrates correlation, not causation, and the depth of mechanistic insight is unclear.
- The reproducibility of the work cannot be assessed. The repository is referenced but its contents, version, and completeness were not available for review.