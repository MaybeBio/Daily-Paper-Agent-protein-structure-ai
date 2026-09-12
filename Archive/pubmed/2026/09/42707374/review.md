## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims made in the abstract
- **Shared manuscript claim summary** The authors report a computational screening pipeline that identified three flavonoid phytochemicals (with Rutin as the top candidate) as potential inhibitors of the IBV spike protein, based on docking, MD simulations, MM-GBSA, and ADMET analyses.
- **Visible evidence base** Abstract text only; no figures, tables, or supplementary material provided
- **Missing materials affecting confidence** Full manuscript, all figures, tables, supplementary data, simulation parameter details, and validation datasets

## Reviewer
- **Overall assessment** The abstract presents a standard computational drug discovery workflow applied to a relevant veterinary virology problem. The topic is timely given the need for alternatives to antibiotics in poultry. However, the abstract lacks critical quantitative details (e.g., docking scores, RMSD/RMSF values, convergence metrics) and does not provide any statistical comparison to known inhibitors or positive controls. Without the full manuscript, the robustness of the computational predictions cannot be evaluated. The claim of "potential" is appropriately cautious, but the evidence base visible in the abstract is insufficient to assess technical soundness.

- **Who would be interested in the results, and why** Poultry virologists and veterinary pharmacologists interested in natural product-based antiviral strategies; computational chemists working on phytochemical screening pipelines; poultry industry stakeholders seeking alternatives to antibiotics.

- **Major strengths** 1. Addresses a practical problem (IBV control in poultry) with a clear computational strategy. 2. Uses a curated phytochemical library (PCLibVer2) specific to poultry-safe botanicals, which is a novel resource. 3. Employs multiple independent MD simulations (3 × 100 ns) and trajectory-based MM-GBSA, which is a reasonable computational validation approach.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness – missing quantitative validation
  - **Claim pointer** "All three phytochemicals exhibited favourable docking scores and stable protein-ligand interactions throughout the simulations."
  - **Evidence pointer** Abstract only; no numerical values provided
  - **Concern** The abstract does not report any docking scores, RMSD, RMSF, or hydrogen bond occupancy values. Without these numbers, the claim of "favourable" and "stable" is unverifiable. The reader cannot assess whether the interactions are physically realistic or merely artefactual.
  - **Why it matters** In computational drug discovery, quantitative metrics are essential to distinguish genuine binding from false positives. The absence of any numerical data makes the core computational claims untestable.
  - **Resolution test** Provide docking scores (Glide score, G-score), average RMSD, RMSF per residue, and hydrogen bond occupancy for each complex in the full manuscript.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance – lack of comparator
  - **Claim pointer** "Rutin exhibited the strongest binding affinity at both binding pockets (-50.07 ± 13.14 and -55.14 ± 20.22 kcal/mol)."
  - **Evidence pointer** Abstract only
  - **Concern** The MM-GBSA values are reported without any comparator (e.g., a known inhibitor, a decoy, or the apo protein). The large standard deviations (±13–20 kcal/mol) suggest high variability, which may indicate poor convergence or non-specific binding. Without a control, it is impossible to know whether these values are meaningful.
  - **Why it matters** MM-GBSA is a relative scoring method; absolute values are not interpretable without a reference. The claim of "strongest binding affinity" is meaningless without a baseline.
  - **Resolution test** Include MM-GBSA values for a known IBV spike inhibitor (if available) or a negative control (e.g., a non-binding compound). Report convergence of MM-GBSA over the simulation trajectory.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness – simulation quality
  - **Claim pointer** "Three independent 100 ns molecular dynamics simulations"
  - **Evidence pointer** Abstract only
  - **Concern** The abstract does not state whether the three simulations are replicates (same starting structure, different seeds) or independent runs (different initial velocities). It also does not report whether the systems reached equilibrium (e.g., RMSD plateau, energy convergence). Without this information, the reliability of the 100 ns trajectories is unknown.
  - **Why it matters** Inadequate equilibration or insufficient sampling can lead to artefactual conclusions about stability and binding.
  - **Resolution test** Provide RMSD vs. time plots for all three replicates, state equilibration criteria, and report whether the three runs converged to similar structural ensembles.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract
  - **Issue** The phrase "reduced conformational sampling relative to the apo protein" is ambiguous. It could mean the ligand-bound protein explores fewer conformations (i.e., is stabilised) or that the simulation sampled less of phase space (a technical limitation).
  - **Required correction** Clarify: "the ligand-bound protein exhibited reduced conformational flexibility compared to the apo protein, as indicated by lower RMSF values."

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Scientific importance – scope
  - **Affected element** Abstract conclusion
  - **Evidence pointer** Abstract
  - **Issue** The abstract claims the study "provides a computational framework for the development of phytochemical-based interventions," but the pipeline is standard (docking → MD → MM-GBSA → ADMET). The novelty of the framework itself is not evident.
  - **Required correction** Either highlight a novel methodological aspect (e.g., the poultry-specific library) or temper the claim to "applies an established computational framework to a new target and library."

- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative validation), R1-M2 (lack of comparator), R1-M3 (simulation quality not reported)

- **Assessment against Nature-style criteria** 
  - **Originality**: Low. The workflow is standard; the poultry-specific phytochemical library is a minor novelty.
  - **Scientific importance**: Moderate. IBV is a significant poultry pathogen, and natural product inhibitors are of practical interest, but the abstract does not demonstrate that the identified compounds are likely to be effective in vivo.
  - **Interdisciplinary readership**: Low. The abstract is written for a specialist computational chemistry / virology audience; it does not frame the problem in a way that would attract a broader readership.
  - **Technical soundness**: Not assessable from the abstract alone. The missing quantitative data and lack of controls prevent evaluation.
  - **Readability for nonspecialists**: Adequate for a specialist journal; the abstract uses appropriate terminology but could be clearer (see minor comment R1-m1).

- **Recommendation posture** Currently not established from the provided evidence. The abstract lacks the quantitative detail and controls necessary to assess the validity of the computational predictions. A full manuscript with docking scores, simulation convergence metrics, and appropriate comparators would be required for a meaningful evaluation. The work may be suitable for a specialised computational pharmacology journal, but it does not meet the standards of a high-impact general journal like Nature.