## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors report the molecular characterisation of vitellogenin (Vg) and its receptor (VgR) in *Maruca vitrata*, including cloning, phylogenetic analysis, protein modelling, docking, and CRISPR-based sgRNA design and *in vitro* validation.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, all figures/tables, detailed methods (cloning, CRISPR design, *in vitro* cleavage assay protocols, docking parameters), sequence data, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a logical progression from gene characterisation to CRISPR tool development for a pest of agricultural importance. However, the claims are supported only by summary statements without any visible data. The core functional validation—sgRNA cleavage activity—is described qualitatively, and the docking result is presented without context or error metrics. The abstract alone does not provide sufficient evidence to evaluate the technical soundness or reproducibility of the work.

- **Who would be interested in the results, and why** Researchers working on lepidopteran pest management, insect reproductive biology, and CRISPR-based gene editing in non-model insects. The work provides preliminary molecular resources for future functional studies of Vg in *M. vitrata*.

- **Major strengths** 1. Addresses a relevant pest species with high economic impact. 2. Integrates multiple approaches (cloning, phylogenetics, modelling, CRISPR) in a single study. 3. Reports a negative result (sgRNA3 failure) which is valuable for sgRNA design guidelines.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness – data availability
  - **Claim pointer** "sgRNA1 targeting the LPD_N domain and sgRNA2 targeting the signal peptide region exhibited efficient site-specific cleavage activity, whereas sgRNA3 failed to induce cleavage because of an unfavourable secondary structure"
  - **Evidence pointer** Abstract only; no figure or table cited
  - **Concern** The abstract states that sgRNA1 and sgRNA2 showed "efficient site-specific cleavage activity" and that sgRNA3 failed due to "unfavourable secondary structure," but no quantitative data (e.g., cleavage efficiency percentages, gel images, replicate numbers) are provided. The claim about secondary structure is speculative without supporting structural predictions or experimental validation.
  - **Why it matters** The central functional claim of the study—that validated sgRNAs are ready for embryo microinjection—rests entirely on these *in vitro* cleavage results. Without visible data, the claim cannot be assessed for reproducibility or statistical significance.
  - **Resolution test** Provide gel images, quantification of cleavage efficiency (e.g., band intensity ratios), replicate data, and secondary structure predictions for all three sgRNAs.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness – docking analysis
  - **Claim pointer** "Homology models of Vg and VgR (GMQE: 0.58 and 0.51) showed a favourable interaction by protein-protein docking (score: -295.66)"
  - **Evidence pointer** Abstract only; no figure or table cited
  - **Concern** The docking score of -295.66 is presented without units, comparison to a control (e.g., random or known non-interacting proteins), or any measure of confidence (e.g., Z-score, RMSD, or multiple docking runs). GMQE values of 0.58 and 0.51 indicate moderate model quality, which may limit the reliability of the docking prediction.
  - **Why it matters** The docking result is used to support the biological relevance of the Vg-VgR interaction, but without proper validation, the claim of a "favourable interaction" is unsubstantiated.
  - **Resolution test** Provide docking statistics, control docking results, model validation metrics (e.g., Ramachandran plots), and a clear statement of what the score represents.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance – novelty
  - **Claim pointer** "this study provides the first CRISPR-oriented functional characterisation and sgRNA validation of the M. vitrata Vg gene"
  - **Evidence pointer** Abstract only
  - **Concern** The abstract does not clarify how this work differs from the previously reported *M. vitrata* Vg sequence (MG799570.1), with which it shares 99.04% identity. The novelty appears limited to the CRISPR component, but the functional characterisation (cloning, phylogenetics, domain analysis) largely replicates existing data.
  - **Why it matters** The claim of "first CRISPR-oriented functional characterisation" is potentially valid, but the abstract does not demonstrate that the CRISPR work goes beyond sgRNA design and *in vitro* cleavage to actual functional disruption (e.g., in embryos or adults).
  - **Resolution test** Clarify in the abstract or full text what new biological insight the CRISPR validation provides beyond confirming that sgRNAs can cut the target *in vitro*.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract
  - **Issue** The phrase "preliminary molecular resources for future CRISPR/Cas9 studies" is vague. It is unclear whether the sgRNAs have been tested in vivo or only in vitro.
  - **Required correction** Specify the current stage of validation (e.g., "in vitro-validated sgRNAs" vs. "in vivo-tested sgRNAs").

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract
  - **Issue** The abstract mentions "three conserved domains" but only names LPD_N, DUF1943, and VWD. It does not state which domain was targeted by sgRNA3 or why the signal peptide region was chosen for sgRNA2.
  - **Required correction** Briefly justify the selection of target regions for each sgRNA.

- **Technical failings that need to be addressed before the case is established** R1-M1 (sgRNA cleavage data missing), R1-M2 (docking validation missing)

- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The Vg sequence is nearly identical to a previously reported one; the CRISPR component is novel but limited to *in vitro* validation.
  - **Scientific importance**: Moderate. The pest is economically important, but the study does not demonstrate functional disruption of reproduction, which would be required for high impact.
  - **Interdisciplinary readership**: Low. The work is primarily of interest to entomologists and insect molecular biologists; the CRISPR application is not sufficiently advanced to attract a broader audience.
  - **Technical soundness**: Not assessable from the abstract alone. Key data (cleavage assays, docking) are missing.
  - **Readability for nonspecialists**: Adequate. The abstract is clearly written but uses field-specific terminology without explanation.

- **Recommendation posture** Currently not established from the provided evidence. The abstract lacks the quantitative data needed to evaluate the core claims of sgRNA validation and docking analysis. A full manuscript with figures, methods, and statistical details is required for a meaningful assessment.

## Risk / unsupported claims
- "sgRNA1 and sgRNA2 exhibited efficient site-specific cleavage activity" – unsupported; no data provided.
- "sgRNA3 failed to induce cleavage because of an unfavourable secondary structure" – unsupported; speculative without structural data.
- "Homology models showed a favourable interaction by protein-protein docking (score: -295.66)" – unsupported; no docking validation or controls.
- "first CRISPR-oriented functional characterisation" – potentially overstated; the abstract describes only *in vitro* validation, not functional characterisation in vivo.