## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors predict that 28 emerging coronaviruses may bind human ACE2 using AlphaFold structural predictions, static docking programs (AlphaFold, ClusPro, HADDOCK), and molecular dynamics simulations. They report that less restrained static predictions distinguish binders from non-binders, whereas heavily restrained docking does not. They identify Zhejiang2013 as a potential ACE2 binder and conclude that its dynamic interaction patterns are consistent with ACE2 binding.
- **Visible evidence base** Abstract text only; no quantitative results, statistical measures, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, simulation parameters, docking scores, contact analysis definitions, and validation datasets

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable computational framework for discriminating betacoronavirus receptor usage, with clear public health motivation. However, the current evidence base is insufficient to evaluate the validity of the central claims. The key conclusion regarding Zhejiang2013 rests on qualitative statements about "dynamic interaction patterns" without quantitative support. The discriminative power of the static methods is asserted but not demonstrated with numbers. The manuscript may have merit, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Virologists studying coronavirus emergence and host range, computational biologists developing protein-protein interaction prediction pipelines, and public health researchers focused on pandemic preparedness and zoonotic spillover risk assessment. The methodological comparison of docking approaches would interest structural biologists who use these tools for screening.
- **Major strengths** The study addresses a timely and important question with direct relevance to pandemic preparedness. The use of positive and negative controls to threshold predicted binding is a sound conceptual approach. The comparison of multiple prediction methods with varying restraint levels is a thoughtful design that could reveal methodological biases. The integration of static predictions with molecular dynamics simulations represents a reasonable multi-scale strategy.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "Zhejiang2013 exhibits dynamic interaction patterns consistent with ACE2 binding"
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The central conclusion about Zhejiang2013 is supported only by a qualitative statement about "dynamic interaction patterns." No quantitative metrics are reported, such as binding free energies, contact persistence, hydrogen bond occupancy, or root-mean-square deviation/stability measures from the molecular dynamics simulations. The abstract does not state how many replicates were performed, what force field was used, or how "consistent with ACE2 binding" was operationally defined.
  - **Why it matters** Without quantitative criteria, the claim that Zhejiang2013 is a potential ACE2 binder cannot be independently assessed or reproduced. The threshold for "consistent with" is undefined, and the reader cannot distinguish a robust signal from a subjective interpretation of simulation trajectories.
  - **Resolution test** Provide quantitative metrics from molecular dynamics simulations (e.g., binding free energy estimates, contact frequencies, or stability measures) with defined thresholds for what constitutes ACE2-binding-consistent behavior, and show that Zhejiang2013 meets these thresholds while negative controls do not.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** "Less restrained static predictions separated binders from non-binders, whereas heavily restrained docking did not"
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract claims differential discriminative power among prediction methods but provides no quantitative comparison. No sensitivity, specificity, accuracy, or area-under-the-curve values are reported. The number of positive and negative controls is not stated, and the criteria for "separated" versus "did not separate" are not defined.
  - **Why it matters** The methodological comparison is a central contribution of the work. Without quantitative performance metrics, the claim that one method outperforms another is anecdotal. The reader cannot assess whether the observed differences are meaningful or within expected variability for these tools.
  - **Resolution test** Report a quantitative performance comparison (e.g., classification accuracy, ROC curves, or enrichment scores) for each method against the control set, with clear definitions of binding thresholds and statistical significance.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Control adequacy
  - **Claim pointer** "We used known ACE2-binding sarbecoviruses as positive controls and coronaviruses that bind other receptors as negative controls to threshold predicted binding"
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not specify how many positive and negative controls were used, which specific viruses were included, or how the negative controls were selected. The statement "coronaviruses that bind other receptors" is vague, and it is unclear whether these negative controls are structurally similar enough to provide a meaningful contrast.
  - **Why it matters** The validity of the entire screening approach depends on the quality and representativeness of the control set. If negative controls are too dissimilar or too few, the thresholding may be biased. If positive controls are too few, the sensitivity of the approach cannot be established.
  - **Resolution test** List the specific viruses used as positive and negative controls, justify their selection, and demonstrate that the control set is sufficiently large and diverse to support the thresholding approach.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Study scope
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract states "28 emerging coronaviruses" but does not clarify how "emerging" was defined or how these viruses were selected from the broader coronavirus family.
  - **Required correction** Provide a brief statement on the selection criteria for the 28 viruses, including their subgenera distribution and source database.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Simulation details
  - **Evidence pointer** Abstract, location not provided
  - **Issue** No information is given about the molecular dynamics simulation length, force field, or system setup. This prevents assessment of whether the simulations were sufficiently converged.
  - **Required correction** Include simulation length, force field, and equilibration protocol in the methods or abstract.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Heavily restrained docking"
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "heavily restrained" is not defined. It is unclear whether this refers to HADDOCK's ambiguous interaction restraints, ClusPro's filtering, or something else.
  - **Required correction** Define what "heavily restrained" means in the context of each docking method.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results for the central claim, the lack of performance metrics for the method comparison, and the underspecified control set collectively prevent the case from being established.
- **Assessment against Nature-style criteria**  
  Originality: The combination of AlphaFold predictions with multiple docking tools and molecular dynamics for screening unstudied coronaviruses is a reasonable approach, but the abstract does not demonstrate a novel methodological contribution beyond what is already published in the structural prediction literature.  
  Scientific importance: The question of predicting receptor usage in emerging coronaviruses is highly important for pandemic preparedness, and the public health motivation is clear.  
  Interdisciplinary readership: The work bridges virology, structural biology, and computational biology, which could attract a broad audience if the results are quantitatively robust.  
  Technical soundness: Cannot be assessed from the abstract. The lack of quantitative metrics and methodological details prevents evaluation of technical rigor.  
  Readability for nonspecialists: The abstract is generally readable, but terms like "subgenera" and "sarbecoviruses" may require background knowledge. The logic from screening to simulation to conclusion is clear at a high level.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a potentially valuable study, but the absence of quantitative results, defined thresholds, and control details means the central claims cannot be evaluated. The authors should be encouraged to resubmit with the full manuscript and quantitative support.

## Risk / unsupported claims
- The claim that Zhejiang2013 is a potential ACE2 binder is unsupported without quantitative molecular dynamics metrics.
- The claim that less restrained static predictions outperform heavily restrained docking is unsupported without performance statistics.
- The claim that the screening approach can "discriminate" receptor usage is not established without defined thresholds and validation metrics.
- The general statement that "two ACE2-binding coronaviruses have caused global pandemics" is a factual claim that is not substantiated within the abstract, though it is likely well-known background knowledge.