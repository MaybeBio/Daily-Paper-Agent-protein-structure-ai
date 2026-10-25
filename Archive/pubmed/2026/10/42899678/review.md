## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present an integrative approach, termed AlphaLink-Modeller, that incorporates cross-linking mass spectrometry (XL-MS) distance constraints into deep-learning-based protein structure prediction. They apply this method to two Encephalitozoon hellem spore wall proteins, Swp1b and EnP1, which lack clear homologs and contain disordered regions. The resulting complex model is reported to be consistent with the cross-links used for modeling and was subsequently confirmed by independent XL-MS data. The authors claim the method is particularly suited to proteins with limited homology and substantial flexibility, provided these adopt a defined structural state in a biological context.
- **Visible evidence base** Abstract text only; no methodological details, quantitative validation metrics, or experimental data are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, XL-MS datasets, model quality metrics, comparison with alternative approaches, and any statistical or reproducibility analyses

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable integrative modeling strategy that addresses a real gap in structural biology for organisms with poorly characterized proteomes. The application to microsporidian spore wall proteins is biologically relevant, and the claim of independent XL-MS validation is encouraging. However, the abstract alone provides insufficient evidence to assess the technical soundness of the method, the quality of the resulting model, or the robustness of the validation. The core claims are plausible but not established from the supplied material.
- **Who would be interested in the results, and why** Structural biologists working on integrative modeling and protein complexes with limited homology would find the method relevant. Researchers studying microsporidia and other obligate intracellular parasites would be interested in the biological application, particularly the spore wall protein interaction. Computational biologists developing deep-learning-based structure prediction tools may also find the incorporation of experimental restraints of interest.
- **Major strengths** The problem addressed is well defined and significant, as many proteins in understudied organisms lack homology to solved structures. The integration of XL-MS data into deep-learning-based modeling is a logical and potentially powerful extension of existing approaches. The biological target is meaningful, and the claim of validation by independent XL-MS data suggests some level of experimental rigor.
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
  Originality: The approach is a variant of existing integrative modeling strategies, and the abstract does not clearly articulate what is conceptually new beyond applying AlphaLink to a new system. Scientific importance: The biological question is important for microsporidia research, but the broader impact on structural biology is not yet demonstrated. Interdisciplinary readership: The work bridges mass spectrometry, computational modeling, and parasitology, which could appeal to multiple communities, but the abstract does not provide enough detail to engage nonspecialists. Technical soundness: Cannot be assessed from the abstract alone; no metrics, controls, or comparisons are provided. Readability for nonspecialists: The abstract is generally clear but uses jargon without sufficient context for a broad audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising, but the technical and validation claims require full manuscript review. A supportive posture would be contingent on resolving the major concerns.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The method "incorporates cross-linking mass spectrometry (XL-MS) data into structure prediction" and "generated a model of two interacting E. hellem spore wall proteins."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not describe how XL-MS data were integrated into the modeling pipeline, what specific algorithmic changes were made to AlphaLink, or how the distance constraints were weighted, filtered, or validated. Without this information, the technical novelty and correctness of the approach cannot be evaluated.  
- **Why it matters** The core claim is that the method improves structure prediction for proteins with limited homology and disordered regions. If the integration strategy is not technically sound, the resulting model and all downstream biological conclusions are compromised.  
- **Resolution test** Provide a detailed methods section describing the modeling pipeline, including input data processing, constraint incorporation, model selection criteria, and any hyperparameters. Include benchmarks on known complexes to demonstrate that the method performs at least as well as existing approaches.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation rigor  
- **Claim pointer** The model "was also subsequently confirmed by independently generated XL-MS data."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract states that independent XL-MS data confirmed the model, but no details are given on how this confirmation was assessed. It is unclear whether the independent data were used to score the model, whether the agreement was quantitative or qualitative, and what threshold was used to define confirmation.  
- **Why it matters** Independent validation is the key evidence supporting the model's reliability. Without a clear definition of what constitutes confirmation, the claim is not falsifiable and could be based on a permissive or subjective assessment.  
- **Resolution test** Specify the number of independent cross-links, the fraction that were satisfied by the model, and the distance tolerance used. Provide a comparison with a null model or a decoy set to show that the agreement is statistically significant.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model quality assessment  
- **Claim pointer** The resulting model is "consistent with the experimental cross-links used to generate the model."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** Consistency with the data used to generate the model is a necessary but weak test. The abstract does not report any model quality metrics, such as per-residue confidence scores, stereochemical quality, or agreement with known structural features. It is also unclear whether the model represents a unique solution or whether multiple models could satisfy the same constraints.  
- **Why it matters** A model that merely fits the input restraints could be overfitted or non-unique. Without additional quality indicators, the biological relevance of the model is uncertain.  
- **Resolution test** Report model confidence scores, such as pLDDT or PAE, and provide an analysis of model ensemble diversity. Show that the model is geometrically reasonable and that the interaction interface is supported by multiple independent restraints.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Biological significance  
- **Claim pointer** The two proteins "previously were not known to interact with one another" and are "important for host cell infection."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract claims a novel interaction between Swp1b and EnP1 and implies biological relevance, but no functional validation is presented. It is not shown whether the predicted interaction has any phenotypic consequence, such as affecting spore wall integrity or host cell invasion.  
- **Why it matters** The biological importance of the model depends on the interaction being functionally meaningful. Without experimental validation, the interaction could be an artifact of the modeling process or a non-functional in vitro association.  
- **Resolution test** Provide experimental evidence, such as co-immunoprecipitation, localization studies, or genetic disruption, to support the interaction and its role in infection. If such experiments are not feasible, clearly state the interaction as a prediction and temper the biological claims.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Method naming  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "AlphaLink-Modeller" is introduced without explanation of what "Modeller" refers to or how it differs from the existing AlphaLink software.  
- **Required correction** Define the name and clarify the relationship to existing tools, or rename to avoid confusion.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Scope of method applicability  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states the method is suited to proteins with limited homology and flexible regions, but it is unclear whether this claim is based on a single example or broader benchmarking.  
- **Required correction** State whether the method was tested on additional systems or clearly indicate that this is a single-case demonstration.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** Terms such as "disordered regions" and "integrative modeling" are used without brief definitions, which may hinder nonspecialist readers.  
- **Required correction** Add a short explanatory phrase for these terms in the abstract or introduction.

## Risk / unsupported claims
- The claim that the method "extends integrative modeling approaches to previously inaccessible targets" is not supported by the abstract, as no comparison with prior methods or broader applicability is shown.
- The claim that the two proteins "previously were not known to interact" is presented as a finding, but the abstract does not provide evidence that a thorough literature search was conducted.
- The claim that the model was "confirmed" by independent XL-MS data is not quantitatively defined and is therefore not fully assessable.
- The biological importance of the interaction for host cell infection is asserted without experimental support.