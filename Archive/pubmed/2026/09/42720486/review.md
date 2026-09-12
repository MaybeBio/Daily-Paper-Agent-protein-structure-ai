## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors present HighMorph, an AI framework integrating Monte Carlo tree search with a Transformer-based policy-value network and explicit hydrogen bond constraints from protein-protein interactions, for de novo cyclic peptide sequence design. The framework is validated on PD-L1 and KLK4 targets, achieving 33.3% and 40% hit rates with micromolar binding affinities.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, experimental methods, binding assay details, sequence data, computational validation, comparison with existing methods, and all supporting figures/tables

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach that combines established AI techniques (MCTS, Transformer) with structure-guided constraints for cyclic peptide design. The reported hit rates (33.3% and 40%) and micromolar affinities are promising for a proof-of-concept study. However, the abstract lacks critical methodological details, experimental validation depth, and comparative benchmarks necessary to assess the novelty, robustness, and generalizability of the framework. The claims cannot be properly evaluated from the abstract alone.

- **Who would be interested in the results, and why** Researchers in computational drug design, peptide therapeutics, and protein interface targeting would be interested. The approach addresses a recognized challenge in de novo cyclic peptide design, and the integration of protein-protein interaction information with AI search is a potentially useful strategy for generating candidate binders.

- **Major strengths**
    - Addresses a relevant and challenging problem in drug discovery: de novo design of target-binding cyclic peptides.
    - The combination of Monte Carlo tree search with a Transformer-based policy-value network and explicit hydrogen bond constraints is a reasonable and potentially novel integration of existing techniques.
    - Validation on two clinically relevant targets (PD-L1, KLK4) with reported hit rates and affinity data provides initial experimental support.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness and reproducibility
- **Claim pointer** "HighMorph integrates Monte Carlo tree search with a Transformer-based policy-value network to efficiently explore cyclic peptide sequence space, while incorporating explicit atomic-level hydrogen bond constraints extracted from reference protein-protein complexes to guide sequence optimization."
- **Evidence pointer** Abstract (location not provided)
- **Concern** The abstract provides no details on the Transformer architecture, training data, or how the hydrogen bond constraints are derived and incorporated. The "reference protein-protein complexes" are not specified. Without this information, the method cannot be reproduced or critically evaluated.
- **Why it matters** Reproducibility and methodological transparency are fundamental to scientific claims. The novelty of the approach hinges on the specific implementation details, which are entirely absent.
- **Resolution test** Provide a clear description of the Transformer model (size, training data, loss function), the source and processing of protein-protein interaction data, and the algorithm for integrating hydrogen bond constraints into the MCTS search.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation and data completeness
- **Claim pointer** "Notably, 33.3% and 40% of the generated candidates are active against PD-L1 and KLK4, respectively, with active cyclic peptides exhibiting micromolar binding affinities (approximately 10-6 M)."
- **Evidence pointer** Abstract (location not provided)
- **Concern** The abstract does not specify the number of candidates tested, the assay used (e.g., SPR, ITC, fluorescence polarization), the exact affinity values (range, mean, standard deviation), or the criteria for "active." The micromolar affinity (10⁻⁶ M) is modest and may not be sufficient for therapeutic relevance. No negative controls or comparison to random sequences are mentioned.
- **Why it matters** Without these details, the hit rate and affinity claims are uninterpretable. A 33.3% hit rate on a small number of candidates (e.g., 3 out of 9) is very different from the same rate on 100 candidates. The lack of controls prevents assessment of whether the method outperforms random design.
- **Resolution test** Report the total number of candidates tested per target, the specific binding assay and its conditions, the exact affinity values (with errors), the definition of "active," and include a comparison to a baseline (e.g., random sequences or a known negative control).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and comparison to existing methods
- **Claim pointer** "These results validate our approach for cyclic peptide design."
- **Evidence pointer** Abstract (location not provided)
- **Concern** Validation on only two targets, both of which have known binding partners or inhibitors, is insufficient to claim general validity. The abstract does not compare HighMorph to any existing cyclic peptide design methods (e.g., computational docking, phage display, other AI-based approaches).
- **Why it matters** The field already has established methods for cyclic peptide discovery. Without a comparative benchmark, it is unclear whether HighMorph offers a meaningful advantage in hit rate, affinity, or speed.
- **Resolution test** Validate on additional, structurally diverse targets (e.g., protein-protein interfaces with no known cyclic peptide binders). Include a direct comparison to at least one state-of-the-art computational or experimental method on the same targets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Title and abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The term "De Novo Cyclic Peptide Sequence Design via Protein-Protein Interaction Recapitulation" is somewhat ambiguous. "Recapitulation" could imply reproducing an existing interaction, but the method appears to use PPI information as a guide for design, not recapitulation.
- **Required correction** Clarify the meaning of "recapitulation" in the context of the method, or consider rephrasing to "guided by" or "informed by" protein-protein interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The phrase "approximately 10-6 M" is imprecise. A range or specific values (e.g., 1-10 µM) would be more informative.
- **Required correction** Provide the exact range or mean ± SD of binding affinities for the active cyclic peptides.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope of claims
- **Affected element** Abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The final sentence, "interaction analysis provides insights for developing therapeutics targeting challenging protein interfaces," is a broad claim that is not supported by any evidence presented in the abstract.
- **Required correction** Either provide a specific example of such an insight from the study, or temper the claim to reflect the preliminary nature of the analysis.

## Risk / unsupported claims
- The claim that HighMorph is "validated" for cyclic peptide design is unsupported by the abstract alone, given the limited target scope and lack of comparative benchmarks.
- The claim that the approach provides "insights for developing therapeutics targeting challenging protein interfaces" is unsupported by any data presented.
- The novelty of the AI framework (MCTS + Transformer + H-bond constraints) cannot be assessed without methodological details and comparison to prior work.