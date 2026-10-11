## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present Zephyr, an SE(3) equivariant diffusion model trained on simulated IDP ensembles, which generates protein structures in two phases (coarse-grained sampling followed by heavy-atom denoising). They claim the model reproduces key geometric and energetic metrics of MD ensembles across five test systems while sampling at least 63 times faster than MD.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, or methodological descriptions beyond the two-phase generation scheme
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, training data specifications, test system identities, evaluation metrics, and baseline comparisons

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing approach that combines the speed of generative models with the accuracy of MD simulations for IDP conformational sampling. The two-phase generation strategy is a reasonable design choice. However, the abstract provides insufficient quantitative detail to evaluate the strength of the claims. Key metrics, test system descriptions, and comparison baselines are absent. The claim of reproducing "key geometric and energetic metrics" is vague without specifying which metrics, with what error margins, and against which reference standards. The speedup factor of 63 is presented without context regarding hardware, simulation length, or convergence criteria.
- **Who would be interested in the results, and why** Researchers in computational biophysics and structural biology, particularly those studying intrinsically disordered proteins and conformational ensembles. The work may also interest developers of generative models for biomolecular structures and researchers seeking efficient alternatives to MD for ensemble sampling.
- **Major strengths** The problem addressed is timely and important, as IDP conformational sampling remains a computational bottleneck. The two-phase generation approach (coarse-grained then heavy-atom refinement) is a sensible architectural choice that mirrors hierarchical assembly strategies. The explicit focus on ensemble accuracy rather than single-structure prediction is appropriate for the IDP context. The reported speedup, if robust, would be practically significant.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: the combination of diffusion models with MD-derived training data for IDP ensembles is a novel contribution, though the individual components are established. Scientific importance: the potential to accelerate IDP ensemble sampling is significant for the field. Interdisciplinary readership: the work bridges machine learning and biophysics, which could attract broad interest, but the abstract currently lacks sufficient detail for nonspecialists to assess the claims. Technical soundness: cannot be evaluated from the abstract alone; the absence of methodological detail and quantitative results prevents assessment. Readability for nonspecialists: the abstract is generally clear but uses field-specific terms (SE(3) equivariant, coarse-grained) without sufficient explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a promising approach, but the claims cannot be verified without the full manuscript and quantitative results.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "the model reproduces key geometric and energetic metrics of the MD ensembles"
- **Evidence pointer** location not provided
- **Concern** The abstract does not specify which geometric and energetic metrics were evaluated, the numerical agreement between model and MD results, or the statistical significance of any differences. Without this information, the claim of reproduction cannot be assessed.
- **Why it matters** The central claim of the work is that Zephyr produces ensembles that match MD accuracy. If the metrics are not defined or the agreement is not quantified, the scientific contribution cannot be evaluated or reproduced.
- **Resolution test** Provide a table or figure listing the specific metrics (e.g., radius of gyration, secondary structure propensities, contact maps, potential energies) with quantitative comparisons between Zephyr and MD ensembles, including error bars and statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "an SE(3) equivariant diffusion model trained on simulated IDP ensembles"
- **Evidence pointer** location not provided
- **Concern** The abstract does not describe the training data generation protocol, the simulation force field, the number of systems used for training, the sequence diversity, or the model architecture details beyond the two-phase generation. The relationship between training data quality and model performance is therefore unclear.
- **Why it matters** The model's performance is fundamentally dependent on the quality and diversity of the training ensembles. Without details on the simulation protocol and training set composition, the generalizability of the approach cannot be assessed.
- **Resolution test** Describe the MD simulation protocol (force field, water model, temperature, simulation length, number of replicas), the number and identity of training systems, and the model architecture in the methods section.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative rigor
- **Claim pointer** "sampling at least 63 times faster"
- **Evidence pointer** location not provided
- **Concern** The speedup claim lacks context. It is unclear whether the comparison is against the MD simulations used to generate training data, against independent MD runs, or against other generative models. Hardware specifications, wall-clock time definitions, and whether the comparison includes the time required to generate training data are not stated.
- **Why it matters** A speedup claim without a well-defined baseline and hardware context is not interpretable. The practical utility of Zephyr depends on the total time to obtain a usable ensemble, including any training or data generation overhead.
- **Resolution test** Specify the exact comparison protocol, including hardware, software versions, MD simulation parameters, and whether the 63-fold speedup refers to inference only or includes all preprocessing steps. Provide a benchmark table comparing Zephyr against MD and, ideally, other generative baselines.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** "two phases: a coarse-grained structure is first sampled and heavy atoms are subsequently denoised onto this structure"
- **Evidence pointer** location not provided
- **Issue** The description of the two-phase generation is brief and does not clarify how the coarse-grained representation is defined or how the heavy-atom denoising is conditioned on the coarse-grained structure.
- **Required correction** Provide a brief description of the coarse-grained representation (e.g., C-alpha only or backbone beads) and the conditioning mechanism in the abstract or methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** "Across five test systems"
- **Evidence pointer** location not provided
- **Issue** The identity and diversity of the five test systems are not described. It is unclear whether they represent a range of IDP lengths, sequence compositions, or degrees of disorder.
- **Required correction** List the five test systems with their sequence lengths and relevant biophysical properties, or state that this information is in the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "key geometric and energetic metrics"
- **Evidence pointer** location not provided
- **Issue** The phrase "key" is subjective and does not indicate which metrics are most important for validating IDP ensembles.
- **Required correction** Replace "key" with a specific list of metrics or state that the metrics are defined in the main text.

## Risk / unsupported claims
- The claim that Zephyr "reproduces key geometric and energetic metrics of the MD ensembles" is unsupported in the abstract due to the absence of specific metrics, numerical values, and statistical analyses.
- The claim of "sampling at least 63 times faster" is unsupported without a defined comparison baseline, hardware context, and methodology.
- The generalizability of the model beyond the five test systems is not assessable from the abstract.
- The statement that the model "leverages the speed of generative models and the accuracy of MD" implies a level of accuracy equivalence that is not demonstrated in the abstract.