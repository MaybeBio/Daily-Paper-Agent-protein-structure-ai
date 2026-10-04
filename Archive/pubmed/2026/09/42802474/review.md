## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or data tables were available for inspection
- **Shared manuscript claim summary** The authors present a coarse-grained, structure-based model of the metamorphic protein XCL1, aiming to reproduce experimentally observed temperature-dependent fold populations, introduce a sequence-dependent treatment of salt effects, map a temperature-salt phase diagram, characterize kinetic pathways of the chemokine-to-alternate fold transition, and examine how charge patterning in ancestral variants modulates fold population balance.
- **Visible evidence base** Abstract text only; no figures, tables, methods section, or supplementary materials provided
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, validation against experimental data, kinetic simulation protocols, ancestral sequence information, and all quantitative results

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable computational study of a biologically and biophysically interesting system. The metamorphic behavior of XCL1 is well established experimentally, and a structure-based model that captures both thermodynamic and kinetic aspects of the fold switch would be of interest to the protein folding and biophysics communities. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the model, the robustness of the conclusions, or the significance of the findings relative to existing work. Several claims are made without supporting quantitative evidence, and the relationship between model parameters and experimental observables is not specified. The work may be publishable in a specialized journal, but the case is not established from the provided material.
- **Who would be interested in the results, and why** Researchers in protein folding, metamorphic proteins, coarse-grained modeling, and biophysics would be interested. The study addresses a fundamental question about how environmental conditions control conformational switching in a single polypeptide, which has implications for understanding protein evolution, function, and misfolding. The introduction of a sequence-dependent salt treatment in a structure-based model could also be of methodological interest to computational biophysicists.
- **Major strengths** The study targets a well-characterized experimental system with clear biological relevance. The combination of thermodynamic and kinetic analyses within a single modeling framework is ambitious and potentially informative. The explicit treatment of salt effects and ancestral variants suggests a systematic exploration of factors controlling the fold switch.
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
- **Assessment against Nature-style criteria** Originality: moderate. While the system is of interest, structure-based models of metamorphic proteins have been reported previously, and the abstract does not clearly articulate a novel methodological advance beyond the salt treatment. Scientific importance: moderate. The findings could inform understanding of fold switching, but the abstract does not demonstrate broad implications beyond the specific system. Interdisciplinary readership: limited. The work is likely to appeal primarily to biophysicists and computational biologists rather than a broad scientific audience. Technical soundness: not assessable from the abstract alone. Readability for nonspecialists: the abstract is reasonably clear but uses jargon without sufficient context for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible study, but the absence of quantitative results, validation details, and methodological specifics prevents a supportive recommendation. A full manuscript with figures and methods would be required for proper evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model "qualitatively reproduces the experimentally observed temperature dependence of XCL1 fold populations, including an increasing alternate-fold population with increasing temperature."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that the model reproduces experimental temperature dependence, but no quantitative comparison is shown. It is unclear what metric was used to assess agreement, how the model parameters were tuned to achieve this agreement, and whether the agreement is robust to parameter variation.
- **Why it matters** Without a clear demonstration of quantitative or at least systematic qualitative agreement with experimental data, the predictive value of the model cannot be assessed. The claim of reproduction is central to the study's validity.
- **Resolution test** Provide a figure comparing model-predicted fold populations to experimental measurements across the relevant temperature range, with error estimates and a description of the fitting procedure.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We introduce a sequence-dependent treatment of salt effects, which reveals a strong sensitivity of the fold equilibrium to salt concentration and yields a temperature-salt phase diagram with a broad coexistence region."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The sequence-dependent salt treatment is a key methodological innovation, but the abstract provides no details on how this treatment is implemented, what parameters are used, or how it is validated against experimental salt-dependent data. The claim of a "broad coexistence region" is not supported by any quantitative description.
- **Why it matters** The salt treatment is presented as a novel contribution. Without details on its formulation and validation, readers cannot judge whether the approach is physically reasonable or whether the predicted phase diagram is reliable.
- **Resolution test** Describe the salt treatment in the methods, show validation against experimental salt-dependent population data if available, and present the phase diagram with clear axes and error estimates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Kinetic simulations of the chemokine-to-alternate fold transition show that productive dimerization tends to occur when both chains are at least partially unfolded, and that formation of the final alternate dimer may proceed via an intermediate state characterized by a partially formed dimer interface."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The kinetic claims are qualitative and lack supporting details. No information is provided on the simulation protocol, the number of trajectories, the time scales probed, or how the intermediate state was identified and characterized. The phrase "tends to occur" and "may proceed" are vague and not backed by quantitative measures.
- **Why it matters** Kinetic mechanisms are difficult to establish reliably, and the abstract does not provide sufficient evidence to distinguish a robust finding from a simulation artifact or a rare event.
- **Resolution test** Provide a detailed description of the kinetic simulation setup, show representative trajectories or ensemble statistics, and quantify the population of the proposed intermediate state and its lifetime.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "We use the model to examine how charge patterning in ancestral variants of XCL1 modulates the population balance between the two folds."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract mentions ancestral variants but provides no information on how these variants were identified, what charge patterning changes were made, or what the predicted effects on fold population were. The significance of this analysis for understanding XCL1 evolution is not articulated.
- **Why it matters** This claim suggests an evolutionary dimension to the study, but without results or context, it is impossible to assess whether the analysis is meaningful or merely speculative.
- **Resolution test** Present the ancestral variant sequences, the charge patterning differences, and the predicted population shifts, and discuss the implications for the evolution of metamorphic behavior.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "metamorphic proteins" is used without definition. While specialists will understand it, a brief clarification would improve accessibility.
- **Required correction** Add a short parenthetical definition, such as "proteins that reversibly switch between two distinct folded states."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not state the model resolution or the specific coarse-graining approach used, which is important for assessing the model's limitations.
- **Required correction** Include a brief statement of the model type, such as the number of beads per residue or the functional form of the potential.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "tuning the relative interaction strength of native contacts in the two folds" is ambiguous. It is unclear whether this tuning is a free parameter fit to experiment or a physically motivated adjustment.
- **Required correction** Clarify whether the interaction strengths are derived from experimental data, estimated from structural considerations, or treated as adjustable parameters.

## Risk / unsupported claims
- The claim of qualitative reproduction of experimental temperature dependence is unsupported without quantitative comparison.
- The claim of a "broad coexistence region" in the temperature-salt phase diagram is unsupported without a figure or numerical description.
- The kinetic mechanism claims, including the role of partial unfolding and the proposed intermediate state, are unsupported without simulation details and statistics.
- The ancestral variant analysis is entirely unevaluable from the abstract; no results are presented.
- The overall predictive accuracy and transferability of the model cannot be assessed without validation details.