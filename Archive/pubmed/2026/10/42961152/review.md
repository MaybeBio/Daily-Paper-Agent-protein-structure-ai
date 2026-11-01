## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present TRAILS-MD, an engine-agnostic adaptive sampling framework that preserves trajectory lineage to reconstruct connected transition pathways from parallelized short trajectory ensembles. They claim demonstration across peptide isomerization, protein folding (Trp-cage and WW domain), ligand unbinding (HSP90), and adenylate kinase conformational change, and further claim that lineage-aware ensembles can seed unbiased production runs for Markov state model construction.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or validation metrics are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methodological descriptions, simulation parameters, convergence criteria, comparison baselines, and MSM validation details

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing framework that addresses a genuine limitation in adaptive sampling, namely the loss of dynamical connectivity information during parallelized exploration. The lineage preservation idea is sensible and potentially useful. However, the abstract provides no quantitative evidence, no comparison against existing methods, and no methodological detail sufficient to assess technical soundness. The claims of broad applicability across four distinct molecular systems are stated without supporting data. The manuscript cannot be evaluated for scientific rigor from the supplied material.
- **Who would be interested in the results, and why** Computational biophysicists and cheminformaticians working on enhanced sampling, Markov state model construction, and rare event simulation would be the primary audience. Researchers developing machine-learned collective variables and those applying adaptive sampling to drug discovery or protein dynamics would also find the framework relevant if the claims are substantiated.
- **Major strengths** The conceptual framing is clear and addresses a real gap in the field. The engine-agnostic design and the explicit focus on lineage preservation as a means to reconstruct pathways from disjointed exploration stages is a sensible and potentially impactful idea. The stated goal of bridging ML-driven coordinate discovery with rigorous trajectory tracking is timely.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: the lineage preservation concept appears novel in the adaptive sampling context, though prior work on trajectory stitching and path sampling exists. Scientific importance: potentially high if the framework demonstrably improves pathway reconstruction efficiency and accuracy, but this is not established from the abstract. Interdisciplinary readership: the work would appeal to a specialized computational chemistry and biophysics audience; broader interest would depend on demonstrated impact on biological discovery. Technical soundness: cannot be assessed from the abstract alone. Readability for nonspecialists: the abstract is reasonably clear but uses jargon that would limit accessibility to a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is promising, but the absence of quantitative results and methodological detail precludes any assessment of validity. A supportive posture would require the full manuscript to demonstrate rigorous validation, comparative benchmarks, and convergence analyses.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim demonstration of the framework across peptide isomerization, Trp-cage and WW domain folding, HSP90 ligand unbinding, and adenylate kinase conformational change.
- **Evidence pointer** Abstract only; no figures, tables, or quantitative results provided
- **Concern** The abstract asserts successful application to four distinct molecular systems but provides no quantitative outcomes, no comparison to conventional adaptive sampling or other enhanced sampling methods, and no metrics of success such as convergence times, pathway fluxes, or free energy profiles.
- **Why it matters** Without quantitative evidence, the reader cannot assess whether the framework actually works, how well it performs relative to existing approaches, or whether the claimed demonstrations are meaningful. The core scientific contribution of the paper rests on these results.
- **Resolution test** The full manuscript must provide quantitative results for each system, including convergence metrics, comparison against appropriate baselines, and statistical uncertainty estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that lineage preservation allows rigorous reconstruction of connected pathways from highly parallelized, disjointed exploration stages.
- **Evidence pointer** Abstract only; methodological details not provided
- **Concern** The abstract does not describe how lineage information is stored, propagated, or used to reconstruct pathways. It is unclear how trajectories launched from different states are connected, how the framework handles branching and merging of lineages, and how the reconstruction avoids artifacts from the adaptive selection process.
- **Why it matters** The central methodological claim of the paper is the lineage-aware pathway reconstruction. Without a clear description of the algorithm, its computational overhead, and its limitations, the technical validity of the approach cannot be evaluated.
- **Resolution test** The full manuscript must provide a detailed algorithmic description, pseudocode or formal specification, complexity analysis, and validation of the reconstruction procedure on systems with known pathways.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The authors claim that lineage-aware exploratory ensembles can seamlessly seed unbiased production trajectories for Markov state model construction.
- **Evidence pointer** Abstract only; no MSM validation results provided
- **Concern** The abstract states that the framework can seed MSM construction but provides no evidence that the resulting MSMs are statistically valid, that the seeding improves MSM quality relative to standard approaches, or that the lineage information is correctly propagated into the MSM framework.
- **Why it matters** The MSM application is presented as a key outcome of the framework. Without validation of the MSMs, including implied timescale tests, Chapman-Kolmogorov checks, and comparison to reference simulations, the claim of seamless integration is unsupported.
- **Resolution test** The full manuscript must include MSM validation metrics, comparison to MSMs built from conventional adaptive sampling or unbiased simulations, and a demonstration that lineage-aware seeding improves model quality or statistical efficiency.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "lightweight" is used in the title and abstract but is not defined. It is unclear whether this refers to computational cost, memory footprint, implementation complexity, or something else.
- **Required correction** Define "lightweight" with specific metrics, such as wall-clock time overhead, memory usage, or number of parameters relative to existing methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Engine-agnostic claim
- **Evidence pointer** Abstract, "engine-agnostic" statement
- **Issue** The abstract claims the framework is engine-agnostic but does not specify which MD engines were tested or whether the implementation is publicly available.
- **Required correction** List the tested MD engines and provide information on code availability, including repository location and license.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Related work
- **Evidence pointer** Abstract, overall
- **Issue** The abstract does not situate the work relative to existing adaptive sampling methods that also address pathway reconstruction, such as weighted ensemble, transition path sampling, or milestoning.
- **Required correction** Add a brief statement in the abstract or introduction that distinguishes TRAILS-MD from these existing approaches and clarifies the specific advantage of lineage preservation.

## Risk / unsupported claims
- The claim of successful demonstration across four molecular systems is unsupported without quantitative results.
- The claim of rigorous pathway reconstruction from parallelized exploration is unverifiable without algorithmic details.
- The claim of seamless seeding of MSM construction is unsupported without MSM validation data.
- The claim that the framework "democratizes advanced data-driven sampling" is an editorial statement without supporting evidence.
- The relative performance of TRAILS-MD compared to existing adaptive sampling methods is not assessable from the abstract.