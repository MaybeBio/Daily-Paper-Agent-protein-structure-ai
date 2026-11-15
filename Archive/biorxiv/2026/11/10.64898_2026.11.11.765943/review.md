## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors use binary patterning, a sequence design strategy for four-helix bundles, as a probe to ask whether the protein language model ESM2 captures the physical rules governing protein folding. They report that ESMFold predictions of synthetic libraries recapitulate experimental trends in helicity, compactness, and topological diversity as a function of sequence length, but do not distinguish successful from unsuccessful individual designs. Principal component analysis of ESM2 embeddings reveals representations of hydrophobic patterning, helix-loop boundaries, and heptad register. Extension to all 128 heptad binary patterns yields a jellyfish-shaped manifold whose dominant axis is hydrophobic composition, with paired components encoding pattern phase. Manifold geometry depends on amino-acid chemistry, repeat number, and linker sequence, and collapses when amino acids are assigned to arbitrary categories. The authors conclude that ESM2 combines general repeat recognition with protein-specific physicochemical information, and propose synthetic sequence libraries as experimentally grounded probes of pLM representations.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were provided
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, methods description, statistical analyses, code repository contents, and supplementary materials

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting approach to probing protein language model representations using a well-established biophysical design principle. The central question, whether ESM2 encodes the physical grammar of protein folding, is timely and relevant. However, the abstract alone provides insufficient detail to evaluate the rigor of the analyses, the validity of the conclusions, or the significance of the findings. Several claims are made without supporting quantitative evidence, and the relationship between the observed embedding geometry and the physical rules of folding remains correlational rather than causal. The manuscript may have merit, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in protein language model interpretability, protein design, and computational biophysics would be interested. The work addresses whether pLMs implicitly learn physical principles, which is relevant to both the machine learning community developing protein models and the biophysics community using them for design and prediction. The use of synthetic sequence libraries as probes is a methodological idea that could be adopted by others studying model representations.
- **Major strengths** The choice of binary patterning as a probe is well motivated, as it is a design principle with known experimental success rates and biophysical rationale. The use of a systematic enumeration of all 128 heptad patterns is a thorough approach. The observation that embedding geometry collapses under arbitrary amino-acid categorization is a potentially informative control. The framing of synthetic libraries as experimentally grounded probes is a useful conceptual contribution.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that ESM2 captures the sequence grammar underlying binary patterning as a design strategy
  - **Evidence pointer** Abstract, results description; location not provided
  - **Concern** The abstract states that ESMFold predictions of synthetic libraries show trends in helicity, compactness, and topological diversity that change with sequence length in the same direction as experimentally characterized libraries. However, no quantitative data are provided, such as correlation coefficients, effect sizes, or statistical significance. The statement that the model did not distinguish successful from unsuccessful individual designs is a negative result that is mentioned but not contextualized. Without numerical evidence, it is impossible to assess the strength of the correspondence between model predictions and experimental observations.
  - **Why it matters** The central claim of the paper rests on the alignment between model behavior and experimental biophysics. If the agreement is weak or only qualitative, the conclusion that ESM2 encodes physical rules is substantially weakened. The negative result on individual design discrimination is particularly important, as it may indicate that the model captures ensemble-level statistics but not the specific physical determinants of folding success.
  - **Resolution test** Provide quantitative comparisons between ESMFold predictions and experimental data, including correlation coefficients, confidence intervals, and statistical tests. Clarify the criteria for successful versus unsuccessful designs and report the model's discrimination performance with appropriate metrics such as AUC or accuracy.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretive validity
  - **Claim pointer** The claim that principal component analysis of ESM2 embeddings reveals representations of hydrophobic patterning, helix-loop boundaries, and heptad register
  - **Evidence pointer** Abstract, results description; location not provided
  - **Concern** The abstract reports that PCA of ESM2 embeddings reveals representations of specific structural features, but no details are given about how these representations were identified or validated. It is unclear whether the PCA components were compared against known sequence features, whether the assignments were made post hoc, or whether any statistical tests were used to confirm the associations. The interpretation of embedding dimensions as encoding specific biophysical features is a strong claim that requires careful validation.
  - **Why it matters** The identification of interpretable axes in embedding space is a central finding. If the assignment of PCA components to features such as heptad register is subjective or not rigorously tested, the conclusion that ESM2 encodes these features is not supported. This concern directly affects the validity of the main interpretive claims.
  - **Resolution test** Describe the methodology for assigning PCA components to specific features, including any correlation analyses, supervised classifiers, or ablation studies. Provide statistical evidence that the identified components are significantly associated with the claimed features and not with confounding variables.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** The claim that ESM2 combines general repeat recognition with protein-specific physicochemical information
  - **Evidence pointer** Abstract, results description; location not provided
  - **Concern** The abstract states that manifold geometry depended on amino-acid chemistry, repeat number, and linker sequence, and collapsed when amino acids were assigned to arbitrary categories. This is presented as evidence that the model uses protein-specific information. However, the abstract does not specify which amino-acid properties were tested, how the arbitrary categories were defined, or whether the collapse was quantitative or qualitative. The distinction between general repeat recognition and protein-specific information is not operationalized.
  - **Why it matters** The conclusion that ESM2 combines general and specific knowledge is a nuanced claim that requires clear operational definitions. Without knowing what was varied and how the effects were measured, the claim cannot be evaluated. The collapse under arbitrary categorization could have multiple explanations, including loss of information rather than loss of physicochemical specificity.
  - **Resolution test** Specify the amino-acid properties tested, the definition of arbitrary categories, and the quantitative metrics used to assess manifold geometry. Provide statistical comparisons between conditions and discuss alternative explanations for the observed collapse.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract, description of the jellyfish-shaped manifold
  - **Evidence pointer** Abstract, results description; location not provided
  - **Issue** The term jellyfish-shaped manifold is evocative but not defined. It is unclear what geometric features justify this description and whether it conveys meaningful information about the embedding structure.
  - **Required correction** Provide a brief geometric description of the manifold, such as the number of dimensions, the arrangement of clusters, or the relationship between axes, so that the reader can understand the structure without relying on the metaphor.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract, mention of experimental libraries
  - **Evidence pointer** Abstract, results description; location not provided
  - **Issue** The abstract refers to experimentally characterized libraries but does not specify which libraries these are, how many sequences they contain, or what experimental properties were measured.
  - **Required correction** Identify the experimental datasets used for comparison and briefly state the measured properties, such as folding yield, stability, or structure, so that the reader can assess the relevance of the comparison.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Abstract, mention of code repository
  - **Evidence pointer** Footnotes, GitHub URL
  - **Issue** The GitHub repository is mentioned in the footnotes, but the abstract does not state what code or data are available there, or whether the repository is publicly accessible at the time of submission.
  - **Required correction** State in the abstract or methods that the code and data are publicly available, and briefly describe what is included in the repository.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative evidence for the alignment between model predictions and experimental data, the lack of validation for the interpretation of PCA components, and the undefined operationalization of general versus protein-specific information collectively prevent the case from being established.
- **Assessment against Nature-style criteria** Originality: The use of binary patterning as a probe of pLM representations is a creative and potentially original approach, though the abstract does not fully distinguish it from prior interpretability studies. Scientific importance: The question of whether pLMs encode physical rules is important for both machine learning and biophysics, but the significance of the findings cannot be fully assessed without quantitative results. Interdisciplinary readership: The work bridges machine learning and protein biophysics, and the abstract is written in a way that is largely accessible to both communities, though some terms such as heptad register may require background knowledge. Technical soundness: Cannot be evaluated from the abstract alone; the lack of methodological detail and quantitative evidence is a major limitation. Readability for nonspecialists: The abstract is generally clear, but the jellyfish-shaped manifold description and the brief treatment of the negative result may confuse readers unfamiliar with embedding analysis.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framing is promising, and the work may be of interest to the community, but the abstract alone does not provide sufficient evidence to support the central claims. A full review of the manuscript with figures, methods, and quantitative analyses would be required to determine whether the case can be made.

## Risk / unsupported claims

- The claim that ESM2 captures the sequence grammar underlying binary patterning is unsupported without quantitative comparisons between model predictions and experimental data.
- The claim that PCA components encode hydrophobic patterning, helix-loop boundaries, and heptad register is unsupported without details on how these assignments were made and validated.
- The claim that manifold geometry depends on amino-acid chemistry, repeat number, and linker sequence is unsupported without specification of the experimental manipulations and quantitative metrics.
- The claim that the manifold collapses under arbitrary amino-acid categorization is unsupported without details on the categorization scheme and the measurement of collapse.
- The claim that ESM2 combines general repeat recognition with protein-specific physicochemical information is not operationalized and cannot be evaluated from the abstract.
- The negative result that the model did not distinguish successful from unsuccessful individual designs is mentioned but not contextualized or quantified, making its significance unclear.