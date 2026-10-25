## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary information
- **Shared manuscript claim summary** The authors present a computational pipeline using REST2 enhanced-sampling MD simulations to design cooperative molecular glues for the FKBP12-MAPRE1 system. They claim identification of a "stabilized configurational space" enabling ternary-complex formation via conformational selection and induced-fit, development of a simulation-derived model correlating with experimental cooperativity, prospective compound ranking, and experimental validation with three of five synthesized compounds showing cooperativity equal to or greater than prior best variants.
- **Visible evidence base** Abstract text only; no quantitative data, simulation details, model parameters, or experimental measurements are provided
- **Missing materials affecting confidence** Full methods, simulation parameters, model construction and validation details, compound structures, experimental cooperativity values, statistical analyses, and comparison with prior variants

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable computational approach to molecular glue design, addressing a real limitation in the field. However, the claims as stated cannot be evaluated for technical soundness or reproducibility because no quantitative evidence, methodological detail, or validation metrics are presented. The central assertion of a predictive model linking simulation data to experimental cooperativity is plausible but unsupported in the abstract alone. The work may be of interest to computational chemists and chemical biologists, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Computational chemists developing enhanced-sampling methods for protein-protein interaction modulation; chemical biologists and medicinal chemists working on molecular glues and induced proximity; researchers interested in conformational ensembles as a design basis for small-molecule therapeutics.
- **Major strengths** The problem addressed is timely and relevant, as rational molecular glue design remains challenging. The use of enhanced-sampling MD to move beyond static structures is conceptually sound. The prospective validation component, with experimental testing of computationally selected compounds, is a strong design element that strengthens the practical relevance of the work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: the concept of using enhanced-sampling MD to identify shared configurational states for molecular glue design appears novel, though the abstract does not clarify how this differs from prior computational approaches to PPI stabilization. Scientific importance: if validated, the approach could advance rational design of molecular glues, a topic of growing therapeutic interest. Interdisciplinary readership: the work bridges computational chemistry, structural biology, and medicinal chemistry, which could appeal to a broad audience, but the abstract is too sparse to convey the depth required for such a readership. Technical soundness: not assessable from the abstract; no simulation parameters, convergence criteria, model validation, or statistical measures are provided. Readability for nonspecialists: the abstract is concise and generally clear, but terms such as "stabilized configurational space" and "apparent cooperativity" are used without definition, which may hinder accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising concept and a validation strategy, but the absence of quantitative results and methodological detail prevents assessment of whether the claims are supported. A full manuscript with detailed methods, model performance metrics, and experimental data would be required to evaluate the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that a model correlating PPI induction information from simulations with experimental cooperativity was developed and used to select and rank compounds prospectively.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that a model was developed to correlate simulation-derived information with experimental cooperativity, but no details are given on the model type, input features, training data, validation approach, or predictive performance. Without this information, it is impossible to assess whether the model is statistically sound, generalizable, or merely overfitted to the limited set of known compounds.
- **Why it matters** The predictive model is the core methodological contribution and the basis for prospective compound selection. If the model is not rigorously validated, the subsequent experimental results cannot be attributed to the computational approach with confidence.
- **Resolution test** Provide model description, feature definitions, training and test set composition, cross-validation or leave-one-out performance metrics, and a clear statement of how the model was used to rank the five selected compounds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that three of five synthesized compounds exhibited apparent cooperativity equal to or greater than that of the best previously known variants.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports experimental outcomes without any quantitative values, error estimates, or statistical significance. "Apparent cooperativity" is not defined, and no comparison metrics are given. It is unclear how many replicates were performed, what assay was used, and whether the differences are meaningful beyond experimental noise.
- **Why it matters** The experimental validation is the key evidence that the computational pipeline has practical utility. Without quantitative data and statistical analysis, the claim of successful validation is not supported.
- **Resolution test** Provide cooperativity values with uncertainties for all tested compounds and prior variants, specify the assay and conditions, and include statistical tests or confidence intervals to support the claim of equality or superiority.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim that REST2 enhanced-sampling MD simulations identified a "stabilized configurational space" that facilitates ternary-complex formation.
- **Evidence pointer** Abstract, location not provided
- **Concern** No simulation details are provided, including system setup, force field, simulation length, number of replicas, REST2 parameters, convergence criteria, or analysis methods. The concept of a "stabilized configurational space" is introduced without a clear operational definition or quantitative characterization.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without sufficient methodological detail, other researchers cannot replicate the simulations or verify the existence and significance of the proposed configurational space.
- **Resolution test** Provide complete simulation protocols, convergence assessments, and a quantitative definition of the "stabilized configurational space" with supporting analyses such as free energy surfaces or population shifts.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "stabilized configurational space" is used without definition or context, making it difficult for readers to understand what specifically was identified or measured.
- **Required correction** Define the term explicitly and describe how it was derived from the simulation data.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Compound library description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions a "small library of compounds" but gives no information on library size, chemical diversity, or selection criteria beyond the model ranking.
- **Required correction** Specify the library size and provide a brief description of the chemical space covered and the selection rationale.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison to prior work
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract references "previously known variants" but does not identify them or describe their properties, limiting the reader's ability to contextualize the claimed improvement.
- **Required correction** Briefly identify the prior variants and their reported cooperativity values to enable direct comparison.

## Risk / unsupported claims
- The claim that a "stabilized configurational space" facilitates ternary-complex formation via conformational selection and induced-fit is unsupported in the abstract, as no mechanistic evidence or quantitative analysis is presented.
- The claim that the simulation-derived model correlates with experimental cooperativity is unsupported, as no model details or performance metrics are given.
- The claim that three of five compounds exhibited cooperativity equal to or greater than prior best variants is unsupported, as no quantitative data or statistical analysis is provided.
- The overall assertion that the study demonstrates a viable strategy for rational optimization of cooperative molecular glues is not established from the abstract alone, given the lack of methodological and quantitative evidence.