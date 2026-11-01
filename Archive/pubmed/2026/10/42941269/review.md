## Review setup
- **Input scope** Full manuscript text provided (Highlights, Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions, Acknowledgments). Supplementary tables and figures referenced but not supplied.
- **Assessment boundary** Assessment is limited to the supplied manuscript text. All supplementary materials (Table S1–S4, Figure S1, Table S3A–E) are referenced but unavailable, so claims that depend on them cannot be independently verified.
- **Shared manuscript claim summary** The authors report untargeted peptidomic identification of 219 soy-derived peptides in a fermented soy postbiotic (GAD), describe extensive overlapping sequence families and truncation ladders, select a 10-peptide diversity panel, dock these against an approximately 5000-protein human structure library, apply GO enrichment with a Jaccard-based ranking-depth heuristic and randomized-affinity negative controls, and prioritize 180 candidate protein targets (43 Tier 1/Tier 2) across mucosal immune regulation, extracellular-matrix remodeling, epithelial turnover, and tissue restitution. The authors frame all docking outputs as hypothesis-generating prioritization rather than validated interactions.
- **Visible evidence base** Main text sections 1–5, Highlights, Abstract, and Acknowledgments. Quantitative results are reported in text for PCA, clustering sensitivity (ARI, silhouette), representative-panel coverage, randomized-affinity controls, and Peptide 4 pose-aggregation. Figure and Table callouts (Figures 1–5, Table 1, Tables S1–S4, Figure S1, Table S3A–E) are cited but their contents are not visible.
- **Missing materials affecting confidence** Table S1 (peptide-level dataset), Table S2 (candidate provenance), Table S3A–E (convergence and pose-aggregation sensitivity), Table S4 (library representation bias), Figure S1 (ranking-depth trajectories), and Figures 1–5. These are central to verifying the reported peptide counts, candidate provenance, and sensitivity analyses.

## Reviewer
- **Overall assessment** This is a methodologically self-aware exploratory study that characterizes a fermented soy-derived peptide fraction and uses computational docking plus GO enrichment to generate prioritized biological hypotheses. The manuscript is unusually candid about its limitations, and several internal controls (clustering sensitivity, randomized-affinity permutation, pose-aggregation sensitivity, library representation-bias analysis) are reported. However, the central biological claims rest on computational predictions that are not experimentally validated, and key supporting evidence is in supplementary materials that are not available for review. The work is best read as a hypothesis-generating framework rather than as establishing peptide–protein associations or biological activity. Several technical points require clarification before the prioritization framework can be considered robustly established.

- **Who would be interested in the results, and why** Researchers in food-derived peptide biology, peptidomics, postbiotic and fermented-ingredient characterization, and computational structural biology / molecular docking would find the workflow relevant. Investigators studying upper-gastrointestinal mucosal defense, gastric injury, and tissue restitution may find the prioritized candidate contexts useful for hypothesis generation. The diversity-sampling and negative-control framework may also interest methodologists working on large-scale peptide–protein docking prioritization.

- **Major strengths**
  - The peptidomic characterization reports a substantial peptide inventory (219 sequences) with explicit mapping to source proteins and documentation of truncation ladders, which is a useful descriptive contribution.
  - The manuscript is transparent about the exploratory nature of the docking analysis and repeatedly states that predictions are not validated interactions.
  - Multiple internal controls are reported, including clustering sensitivity (ARI across alternative representations), a 10,000-panel coverage comparison, a 500-iteration randomized-affinity permutation test per peptide, and a pose-aggregation sensitivity analysis for Peptide 4.
  - The library representation-bias analysis (99.68% of screened accessions present in the reviewed proteome; approximately 21.4% coverage; enrichment for certain structural classes) is a valuable and honest characterization of the search space.
  - The provenance-tracking design (PDB/chain to gene, two independent prioritization routes) is a reasonable attempt at auditability.

- **Major Concerns**

  - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency for the central claim
    - **Claim pointer** The manuscript claims that docking-derived rankings contain "non-random functional structure" and that prioritized biological contexts (mucosal immune regulation, extracellular-matrix remodeling, epithelial turnover, tissue restitution) are supported.
    - **Evidence pointer** Section 3.3.2, Section 4, Table S2, Table S3A–E, Figure S1 (supplementary materials not provided)
    - **Concern** The central biological interpretation depends on GO enrichment derived from docking scores, but no experimental validation of any peptide–protein interaction is presented. The randomized-affinity control tests only whether GO enrichment exceeds what is expected after disrupting the score-to-protein association; it does not test whether the predicted interactions are physically correct. The authors acknowledge this, but the Discussion and Conclusions still present the prioritized contexts as the principal finding, which risks overstating what the evidence supports.
    - **Why it matters** Without orthogonal evidence (e.g., surface plasmon resonance, isothermal titration calorimetry, co-crystallography, or at minimum experimental binding assays for a subset), the reader cannot distinguish genuine interaction signal from artifacts of docking scoring, receptor preparation, and annotation density.
    - **Resolution test** Provide experimental validation for at least a small subset of prioritized peptide–protein pairs, or explicitly reframe the conclusions to state that no biological claim is made and that the output is purely a computational prioritization list.

  - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Reproducibility and traceability of the candidate set
    - **Claim pointer** The manuscript reports 180 unique candidate protein targets (129 via GO-guided route, 51 via top-ranked docking route) and 43 Tier 1/Tier 2 candidates.
    - **Evidence pointer** Section 3.3.2, Figure 5A, Figure 5B, Table S2 (not provided)
    - **Concern** The candidate set and its provenance are reported only in Table S2, which is not available. The text does not provide the identity of the 10 representative peptides, the specific PDB/chain entries, the recurrent GO terms used for filtering, or the tier assignments for individual candidates. The rule-based tier classification (Section 2.13) is described but the actual assignments and the criteria thresholds are not shown.
    - **Why it matters** Without the candidate list and provenance, the reader cannot assess whether the prioritization is reproducible, whether the tier assignments are consistent, or whether the 180-target count is sensitive to the many analytical choices described.
    - **Resolution test** Provide Table S2 in full, including peptide identity, PDB/chain, gene, GO term, identification route, and tier, and summarize the tier-assignment rules with explicit thresholds in the main text.

  - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Methodological validity of the ranking-depth heuristic
    - **Claim pointer** The Jaccard-based convergence procedure (J ≥ 0.80 across three consecutive valid transitions) was used to select a ranking depth for downstream GO interpretation, yielding depths from N = 85 to N = 315 across the 10 peptides.
    - **Evidence pointer** Section 2.9, Section 3.3, Figure S1, Table S3A–D (not provided)
    - **Concern** The convergence criterion is an operational heuristic with no biological ground truth, and the manuscript acknowledges this. However, the selected depth directly determines which proteins enter the enrichment analysis and therefore which GO terms and candidates are prioritized. The sensitivity analysis reported for Peptide 4 shows that longer consecutive windows shift the selected depth, and the pose-aggregation analysis shows convergence depth varies from N = 185 to N = 375 depending on aggregation. This indicates the downstream candidate set is substantially dependent on an arbitrary parameter.
    - **Why it matters** If the prioritized biological contexts change with the convergence definition, the robustness of the central interpretation is weakened.
    - **Resolution test** Report the full ranking-depth trajectories (Figure S1) and demonstrate that the recurrent GO terms and Tier 1/Tier 2 candidate set are stable across a range of convergence definitions, or explicitly state the degree of instability.

  - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Representativeness of the peptide panel
    - **Claim pointer** The 10-peptide diversity panel adequately samples the 219-peptide feature space and supports the downstream docking and prioritization.
    - **Evidence pointer** Section 3.3.1, Section 2.5
    - **Concern** The clustering sensitivity analysis shows only moderate agreement between alternative representations (ARI = 0.241 for PCA-only vs. submitted 10-cluster; ARI = 0.411 when constrained to 10 clusters; mean ARI = 0.659 across UMAP seeds; mean ARI = 0.553 on resampling). The coverage analysis shows the panel reduces mean nearest-representative distance by 8.30% relative to random panels, which is a modest improvement. The authors correctly interpret the panel as diversity-sampling rather than biological proxies, but the docking results are then presented as if the 10 peptides represent the broader peptidome.
    - **Why it matters** If the panel captures only a modest fraction of the feature space, the 180 candidate targets may not reflect the interaction potential of the full 219-peptide mixture, and the prioritized biological contexts may be panel-specific.
    - **Resolution test** Quantify what fraction of the 219-peptide feature space is within a defined distance of the panel, and discuss whether the prioritized contexts would be expected to change with a different panel.

  - **Concern ID** R1-M5
    - **Severity** Major
    - **Blocking** No
    - **Axis** Receptor preparation and docking validity
    - **Claim pointer** Docking against the approximately 5000-protein human structure library yields meaningful relative rankings of candidate interactors.
    - **Evidence pointer** Section 2.6, Section 2.7, Section 4
    - **Concern** The uniform removal of ligands, waters, ions, and cofactors, and protonation at pH 7, is acknowledged to potentially alter binding-site geometry and electrostatics. The use of a single predicted free-peptide conformation (OpenFold3) for docking is also acknowledged as a limitation. However, the manuscript does not report any validation of the docking protocol against known peptide–protein complexes (e.g., re-docking of co-crystallized peptides, or comparison with experimental binding data). Without such validation, the absolute and relative ranking performance of DiffPepDock plus PRODIGY in this specific setting is unknown.
    - **Why it matters** The entire prioritization rests on the assumption that the docking scores carry useful ranking information. If the protocol has not been benchmarked, the rankings may be dominated by systematic biases (e.g., receptor size, surface charge) rather than genuine interaction propensity.
    - **Resolution test** Provide a benchmark of the docking and scoring protocol against a set of experimentally characterized peptide–protein complexes, reporting rank correlation or enrichment factors.

- **Minor Comments**

  - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of statistical reporting
    - **Affected element** Section 3.3.1
    - **Evidence pointer** Section 3.3.1
    - **Issue** The coverage analysis reports P values (P = 2.0 × 10−4, P = 0.0059, P = 6.0 × 10−4, P = 8.0 × 10−4) for comparisons against 10,000 random panels, but the test statistic and the null distribution are not fully described. It is unclear whether these are one-sided or two-sided and whether multiple-comparison correction was applied.
    - **Required correction** State the test used, the directionality, and whether correction was applied.

  - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Internal consistency of reported numbers
    - **Affected element** Section 3.3.2
    - **Evidence pointer** Section 3.3.2
    - **Issue** The text states that for Peptide176, three of 500 randomized rankings produced at least as many significant terms as observed, yielding P = 4/501 = 0.007984. The formula P = (1 + n_null≥obs) / (B + 1) with n = 3 and B = 500 gives 4/501, which is consistent. However, the text also states that for nine of 10 peptides none of the 500 randomized rankings produced as many significant terms as observed, corresponding to P = 1/501. This is consistent with the formula. No error is apparent, but the presentation would benefit from a single consolidated table of per-peptide observed term counts, null counts, and P values.
    - **Required correction** Provide a consolidated per-peptide table of observed and null enrichment counts and empirical P values.

  - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Section 3.3
    - **Evidence pointer** Section 3.3
    - **Issue** The manuscript states that "receptor" refers to the screened protein structure and does not imply a biological receptor function. This clarification is helpful but appears only once. The term is used throughout the Results and Discussion in a way that could confuse non-specialist readers.
    - **Required correction** Consider using "screened protein" or "target protein" consistently, or repeat the clarification at first use in each major section.

  - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Reporting of the antioxidant peptide comparison
    - **Affected element** Section 3.2
    - **Evidence pointer** Section 3.2
    - **Issue** Three literature-reported antioxidant sequences were identified as exact contiguous regions within longer GAD peptides. The manuscript correctly notes that activity of the longer peptides cannot be inferred. However, it does not report whether the free sequences themselves were detected in GAD, nor whether the longer peptides are predicted to release them.
    - **Required correction** State explicitly whether the free antioxidant sequences were detected in the peptidomic data, and discuss the likelihood of their release.

  - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Use of AI assistance
    - **Affected element** Acknowledgments
    - **Evidence pointer** Acknowledgments
    - **Issue** Microsoft Copilot 365 was used to assist with terminology harmonization and consistency review of functional domains and tier classifications. The manuscript states that authors reviewed and finalized all outputs. This is appropriately disclosed, but the extent to which Copilot influenced the final tier assignments is not quantified.
    - **Required correction** Clarify whether any tier assignments were changed as a result of Copilot suggestions, and if so, how many.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation for the central biological interpretation), R1-M2 (candidate set and provenance not available for verification), R1-M3 (ranking-depth heuristic sensitivity), R1-M4 (panel representativeness), R1-M5 (docking protocol not benchmarked).

- **Assessment against Nature-style criteria**
  - **Originality** The peptidomic characterization of a fermented soy postbiotic and the integration of diversity-sampling peptide selection with proteome-scale docking and GO enrichment is a reasonably novel combination, though each component (peptidomics, docking, GO enrichment) is established. The main novelty is the workflow integration and the explicit negative-control framework.
  - **Scientific importance** The work is exploratory and hypothesis-generating. It does not establish biological activity or validated interactions. Its importance lies in providing a prioritized candidate list and a framework for future studies, which is a modest but legitimate contribution.
  - **Interdisciplinary readership** The work spans food science, peptidomics, computational structural biology, and gastrointestinal biology. It could interest a broad readership, but the lack of experimental validation and the reliance on supplementary materials limit its immediate impact.
  - **Technical soundness** The manuscript is unusually candid about limitations and includes several internal controls. However, the central technical weakness is the absence of docking-protocol benchmarking and experimental validation, and the dependence of the candidate set on an arbitrary convergence heuristic. The supplementary materials needed to verify the reported numbers are not available.
  - **Readability for nonspecialists** The manuscript is generally well written and the limitations are clearly stated. However, the density of methodological detail and the use of terms like "receptor" (redefined) and "convergence depth" may challenge non-specialist readers. A clearer separation of descriptive peptidomic findings from computational predictions would improve accessibility.

- **Recommendation posture** Currently not established from the provided evidence. The descriptive peptidomic characterization is a useful contribution, but the central biological prioritization claims rest on computational predictions that are not experimentally validated and on supplementary materials that are not available for verification. The manuscript would need to either provide experimental validation for a subset of prioritized interactions or substantially reframe its conclusions as a purely computational hypothesis-generation exercise, and provide the full supplementary data for independent assessment.

## Risk / unsupported claims
- The claim that the prioritized biological contexts (mucosal immune regulation, extracellular-matrix remodeling, epithelial turnover, tissue restitution) are supported by the data is not established, because the underlying peptide–protein interactions are computational predictions without experimental validation.
- The claim that the docking-derived rankings contain "non-random functional structure" is supported only in the limited sense that GO enrichment exceeds a permutation null; it does not establish that the predicted interactions are physically correct.
- The claim that the 10-peptide panel adequately samples the 219-peptide feature space is weak, given the moderate ARI values and the modest 8.30% reduction in nearest-representative distance relative to random panels.
- The claim that the 180 candidate targets and 43 Tier 1/Tier 2 candidates are robust is not verifiable from the supplied material, because Table S2 and the tier-assignment details are not provided.
- The claim that the Jaccard-based convergence procedure identifies a meaningful ranking depth is not supported beyond its operational definition; the manuscript acknowledges this but the downstream interpretation still depends on it.
- The claim that the docking protocol provides useful relative rankings is not supported by any benchmark against experimentally characterized peptide–protein complexes.
- The claim that the antioxidant peptide sequences embedded in longer GAD peptides have any functional relevance is explicitly not established, and the manuscript correctly states this, but the finding is still presented as a notable result.