## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors present a computational method (WEMD + normal mode driving) that can predict cryptic pockets from apo protein structures, and demonstrate its performance on a diverse protein dataset, achieving 57% success in sampling pockets within 2 Å of holo conformation. They also show that pocket ligandability can be ranked using their Target X model.
- **Visible evidence base** Abstract text only; no figures, tables, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, dataset composition, detailed methodology, statistical analysis, comparison to existing methods, Target X model details, and all figures/tables

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable computational approach for cryptic pocket detection, a problem of high relevance to drug discovery. The reported success rates (57% for structural sampling, 92% for volume overlap at 20% threshold) are promising. However, the abstract alone provides insufficient detail to evaluate the robustness of the method, the diversity and size of the test set, the statistical significance of results, and the practical utility of the ligandability ranking. The claims are interesting but not yet established from the provided material.

- **Who would be interested in the results, and why** Computational chemists, structural biologists, and drug discovery researchers interested in targeting challenging proteins (e.g., KRAS, Werner helicase) where cryptic pockets are critical for inhibitor design. The method could reduce experimental costs and time in early-stage target assessment.

- **Major strengths** 1. Addresses a significant problem in drug discovery: identifying cryptic pockets without prior ligand knowledge. 2. Reports quantitative success metrics (57% structural sampling, 92% volume overlap at 20% threshold). 3. Integrates pocket detection with ligandability prediction (Target X), adding practical utility.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "evaluate this cryptic pocket detection technique on a data set of diverse proteins and show that it successfully samples cryptic pockets within 2 A of the known holo conformation 57% of the time"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not specify the size, composition, or selection criteria of the "diverse protein dataset." Without knowing how many proteins were tested, their structural diversity, and whether they represent a fair challenge set, the 57% success rate cannot be interpreted meaningfully. A small or biased dataset could inflate performance.
  - **Why it matters** Generalizability is the core claim. If the dataset is small or cherry-picked, the method's utility for novel targets is unsubstantiated.
  - **Resolution test** Provide the full dataset (number of proteins, names, PDB IDs, cryptic pocket characteristics) and justify its diversity. Report per-protein results to show variance.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** "successfully samples cryptic pockets within 2 A of the known holo conformation 57% of the time, starting with just the apo structure"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The metric "within 2 A of the known holo conformation" is ambiguous. Does this refer to RMSD of the pocket residues, the ligand binding site, or the entire protein? The abstract also reports volume overlap metrics (20%, 50%, 80%) with success rates of 92%, 84%, and 46%, but the relationship between these two metrics is unclear. Are they measuring the same thing? How are "success" and "sampling" defined?
  - **Why it matters** Without clear, reproducible definitions, the reported numbers cannot be independently verified or compared to other methods.
  - **Resolution test** Define all metrics precisely (e.g., pocket RMSD, volume overlap calculation method, threshold for "sampled"). Show how the two metrics correlate for individual cases.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison to existing methods
  - **Claim pointer** "Time-consuming and expensive experiments currently used to uncover these biologically rare events could be usefully complemented by a computational method"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not compare the WEMD method to any existing computational cryptic pocket detection approaches (e.g., MD simulations, mixed-solvent MD, or machine learning methods). Without a benchmark, the claimed advantage over experiments is speculative.
  - **Why it matters** The field already has computational methods for cryptic pocket detection. The novelty and practical value of this work depend on showing improvement or complementarity.
  - **Resolution test** Include a comparison to at least one established computational method on the same dataset, reporting the same metrics.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Claim about Target X
  - **Evidence pointer** Abstract; location not provided
  - **Issue** "we can successfully rank candidate pockets from WEMD using our pocket ligandability prediction model, Target X" – no performance metric (e.g., AUC, enrichment factor) is provided for this ranking.
  - **Required correction** Report at least one quantitative measure of Target X's ranking performance on the WEMD-generated pockets.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Method description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "normal modes representing the direction of the most collective motion of a protein" but does not specify how many normal modes were used, how they were selected, or how they drive the WEMD simulations.
  - **Required correction** Provide key methodological parameters in the abstract or reference a detailed methods section.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Success rate reporting
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The success rates (57%, 92%, 84%, 46%) are reported without confidence intervals or error estimates. For a dataset of unknown size, these point estimates are not informative.
  - **Required correction** Report confidence intervals or standard errors, and specify the number of test cases.

- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset composition), R1-M2 (metric definitions), R1-M3 (comparison to existing methods)

- **Assessment against Nature-style criteria** 
  - **Originality**: The combination of normal-mode-driven WEMD with ligandability prediction (Target X) appears novel, but the abstract does not clearly differentiate from prior WEMD work by the same group.
  - **Scientific importance**: High – cryptic pocket detection is a bottleneck in targeting challenging proteins.
  - **Interdisciplinary readership**: Moderate – primarily computational chemistry and structural biology; drug discovery audience may find it relevant.
  - **Technical soundness**: Cannot be assessed from abstract alone; key methodological details and validation are missing.
  - **Readability for nonspecialists**: The abstract is clear and well-structured, though some metrics (e.g., volume overlap) could be better explained.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting approach with promising numbers, but the lack of dataset details, metric definitions, and comparison to existing methods prevents evaluation of the method's validity and significance. A full manuscript with rigorous validation is needed.

## Risk / unsupported claims
- The claim that the method "successfully samples cryptic pockets within 2 A of the known holo conformation 57% of the time" is unsupported without dataset details and metric definitions.
- The claim that Target X "successfully rank[s] candidate pockets" is unsupported without performance metrics.
- The implied advantage over experimental methods is unsupported without comparison to existing computational approaches.