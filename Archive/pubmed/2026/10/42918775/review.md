## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no figures, methods, or supplementary material were available for evaluation
- **Shared manuscript claim summary** The authors report cryo-EM structures of connexin-46/50 gap junction channels in the presence of calcium, describing calcium-dependent N-terminal domain conformational ensembles, asymmetric pore collapse, and steric occlusion. They compare these with low-pH gating structures to propose a common N-terminal-centered gating mechanism, and use molecular dynamics simulations to identify calcium interaction sites and propose a model of distributed calcium binding reshaping the channel energetic landscape.
- **Visible evidence base** Abstract text only; no structural coordinates, density maps, simulation parameters, or statistical analyses were provided
- **Missing materials affecting confidence** Full manuscript, all figures, methods section, supplementary information, structural validation metrics, simulation convergence criteria, and statistical details

## Reviewer
- **Overall assessment** The abstract presents a potentially significant advance in understanding calcium-dependent gating of connexin channels, with clear claims about structural mechanisms and a unifying model. However, the evidence base available for review is limited to the abstract, which precludes verification of the central structural and computational claims. The conceptual framework is compelling and the comparison with low-pH gating is intellectually attractive, but the strength of the conclusions cannot be assessed without the underlying data.
- **Who would be interested in the results, and why** Structural biologists studying membrane channels and transporters, particularly those focused on gap junctions and connexin family proteins; cell physiologists investigating ischemic injury and calcium signaling; computational biophysicists interested in ion channel gating mechanisms; and researchers studying the structural basis of channel regulation by physiological stimuli.
- **Major strengths** The study addresses a long-standing question in gap junction biology with direct relevance to ischemic pathology. The use of native channels rather than recombinant constructs adds physiological credibility. The proposed unification of calcium and pH gating mechanisms through a common N-terminal-centered model is conceptually elegant and potentially field-advancing. The combination of cryo-EM with long-timescale molecular dynamics provides complementary approaches to a dynamic process.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is high, as the proposed unifying mechanism for calcium and pH gating has not been previously reported. Scientific importance is substantial given the pathophysiological relevance to ischemia and the fundamental question of connexin gating. Interdisciplinary readership is plausible, spanning structural biology, physiology, and computational biophysics. Technical soundness cannot be evaluated from the abstract alone, particularly regarding cryo-EM resolution, model validation, and simulation rigor. Readability for nonspecialists is good, with clear conceptual framing and accessible language, though some structural terminology may require familiarity with the field.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a coherent and interesting model, but the central claims require full manuscript evaluation. A supportive posture could be adopted if the technical concerns regarding structural resolution, ensemble interpretation, and simulation evidence are adequately addressed in the full manuscript.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that cryo-EM defines the calcium-dependent gating mechanism of native Cx46/50 channels, including an ensemble of N-terminal domain conformations spanning destabilized and fully gated states.
- **Evidence pointer** Abstract text; no figures or methods provided
- **Concern** The claim of defining an ensemble of conformations from single-particle cryo-EM requires substantial validation. The abstract does not report resolution values, the number of particles, classification strategies, or how the ensemble was distinguished from conformational heterogeneity that might arise from sample preparation or grid artifacts. The distinction between "destabilized" and "fully gated" states is not operationally defined.
- **Why it matters** The central conclusion of the paper rests on the interpretation of conformational ensembles. Without clear evidence that the observed states are biologically meaningful and not artifacts of the cryo-EM workflow, the mechanistic model cannot be accepted. The field has seen multiple instances where cryo-EM heterogeneity was over-interpreted.
- **Resolution test** The full manuscript must provide resolution estimates (gold-standard FSC), particle numbers per class, and a clear description of how the conformational states were defined and validated. Ideally, the authors would show that the ensemble is reproducible across independent datasets and that the distribution of states is calcium-dependent.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that comparison with low-pH gating structures reveals a common N-terminal-centered gating mechanism involving coupled NT displacement and TM2 hinge motion.
- **Evidence pointer** Abstract text; no structural comparison data provided
- **Concern** The claim of a common mechanism across different stimuli requires rigorous structural comparison. The abstract does not specify which low-pH structures were used, how the comparison was performed (e.g., superposition metrics, RMSD calculations), or whether the observed similarities are statistically significant beyond what would be expected for related channel structures. The term "common mechanism" implies a level of quantitative similarity that cannot be assessed from the abstract.
- **Why it matters** The unifying model is a major selling point of the paper. If the comparison is superficial or based on limited structural features, the claim of convergence on a common mechanism would be overstated. This could mislead the field into assuming a universal gating model without sufficient evidence.
- **Resolution test** The full manuscript must provide quantitative structural comparisons, including specific residues involved in NT displacement and TM2 hinge motion, with clear metrics for similarity. Ideally, the authors would show that the conformational changes are not merely qualitatively similar but quantitatively comparable across stimuli.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that long-timescale molecular dynamics simulations identify multiple calcium interaction sites along the permeation pathway and suggest that transient inter-subunit calcium coordination can promote NT destabilization and displacement.
- **Evidence pointer** Abstract text; no simulation details provided
- **Concern** The simulation claims are not verifiable from the abstract. No information is provided on simulation length, force field parameters, system size, number of replicates, or how calcium binding sites were identified. The phrase "suggest that transient inter-subunit calcium coordination can promote" is appropriately cautious, but the abstract does not indicate whether these simulations are equilibrium or enhanced sampling, or whether the observed events are statistically significant.
- **Why it matters** Molecular dynamics simulations are powerful but can be misleading if not properly validated. The claim of multiple calcium interaction sites and their role in NT destabilization is a key part of the proposed model. Without evidence of convergence, sufficient sampling, and validation against the experimental structures, these claims remain speculative.
- **Resolution test** The full manuscript must provide simulation details including force field, water model, ion parameters, simulation length, number of replicates, and convergence metrics. The calcium binding sites should be validated against the cryo-EM density if possible, and the proposed mechanism should be supported by multiple independent simulations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract text
- **Issue** The phrase "asymmetrically collapse the pore" is potentially ambiguous. It is unclear whether this refers to a symmetric collapse that is asymmetric in terms of subunit contributions, or a genuinely asymmetric pore shape.
- **Required correction** Clarify the meaning of "asymmetric" in the context of pore collapse, either in the abstract or with a brief explanatory phrase.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract claims
- **Evidence pointer** Abstract text
- **Issue** The abstract does not mention the calcium concentrations used in the experiments or whether the observed effects are dose-dependent. This is relevant for physiological interpretation.
- **Required correction** Include the calcium concentration range used and, if available, a statement about dose dependence in the abstract or indicate where this information can be found in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Abstract framing
- **Evidence pointer** Abstract text
- **Issue** The abstract states that the findings "unify previous models of gap junction regulation" but does not specify which previous models are being unified or how they differed.
- **Required correction** Briefly identify the previous models and the specific aspects that are unified, or indicate that this is elaborated in the full manuscript.

## Risk / unsupported claims
- The claim that cryo-EM "defines" the calcium-dependent gating mechanism is not supported by the abstract alone, as no structural validation metrics are provided.
- The claim of a "common N-terminal-centered gating mechanism" across calcium and pH stimuli is not quantitatively supported in the abstract.
- The molecular dynamics simulation results are presented as suggestive, which is appropriate, but the specific claims about calcium interaction sites and their functional role cannot be evaluated without simulation details.
- The statement that the findings "provide a mechanistic basis for calcium-dependent uncoupling during cellular stress" is a reasonable extrapolation but is not directly demonstrated in the abstract.
- The claim that the study uses "native" connexin-46/50 channels is stated but not verifiable from the abstract alone.