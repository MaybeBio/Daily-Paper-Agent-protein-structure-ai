## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors present PDV, a single-file, offline HTML molecular visualization tool with validated quantitative analytics (SASA, antibody numbering, interaction detection, developability scanning) and an antibody-specific toolkit, built as a modification of 3Dmol.js.
- **Visible evidence base** Abstract text; no figures, tables, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, figures, tables, supplementary data, validation datasets, code repository, and user documentation

## Reviewer
- **Overall assessment** The abstract describes a potentially useful tool that addresses a genuine gap in the molecular visualization landscape: combining lightweight, no-install web delivery with validated quantitative analytics. The validation statistics reported for SASA, antibody numbering, and interaction detection are impressive and suggest careful benchmarking. However, the abstract alone provides insufficient detail to assess the tool’s novelty, usability, and the robustness of the validation. Key technical claims (e.g., “publication-quality outline rendering,” “portable sessions”) are stated without evidence. The antibody-specific toolkit is mentioned but not described in sufficient depth to evaluate its utility. The manuscript may be of interest to the structural biology and antibody engineering communities, but the current evidence base is too thin to support the strong claims made.

- **Who would be interested in the results, and why** Structural biologists, protein engineers, and antibody researchers who need a lightweight, browser-based tool for routine visualization and quantitative analysis (SASA, interaction detection, antibody numbering) without installing heavy desktop software. The validated analytics and antibody-specific features could be particularly appealing for labs with limited computational resources or for teaching environments.

- **Major strengths**
    1. Addresses a clear gap: a no-install web viewer with validated quantitative analytics, combining the convenience of web tools with the depth of desktop software.
    2. Impressive validation statistics for SASA (Pearson r ≈ 0.997–0.998 against FreeSASA across 2,582 structures) and antibody numbering (>99.88% agreement with RIOT across 1.3 million positions), suggesting careful benchmarking.
    3. Single offline HTML file delivery is a practical advantage for reproducibility and offline use.

- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Validation completeness
    - **Claim pointer** “PDV’s SASA reproduces FreeSASA at Pearson r ≈ 0.997–0.998 across 2,582 structures spanning proteins, nucleic acids and ligands”
    - **Evidence pointer** Abstract; no figure or table provided
    - **Concern** The abstract reports a Pearson correlation coefficient but does not specify whether this is for per-residue SASA, per-atom SASA, or total SASA. The range “0.997–0.998” suggests variation across structure types, but the source of this variation is unclear. No details are given on the test set composition, the reference implementation version, or the statistical methods used (e.g., whether outliers were excluded, whether the correlation is on raw or log-transformed values).
    - **Why it matters** Without these details, the reported correlation cannot be properly interpreted or reproduced. A high Pearson r can mask systematic biases (e.g., constant offset, scaling errors) that would affect downstream analyses.
    - **Resolution test** Provide a figure (e.g., scatter plot with regression line and Bland-Altman plot) showing per-residue SASA values from PDV vs. FreeSASA for a representative subset of structures. Report the mean absolute error and root-mean-square error alongside the correlation. Specify the test set composition and any filtering criteria.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Validation completeness
    - **Claim pointer** “its numbering reproduces RIOT for over 99.88% of 1.3 million residue positions across 16,996 sequences and four schemes”
    - **Evidence pointer** Abstract; no figure or table provided
    - **Concern** The abstract reports a high agreement rate but does not specify what constitutes a “reproduction” (exact match of residue numbering? same scheme assignment?). The 0.12% disagreement rate (≈1,560 positions) is not characterized: are these systematic errors in specific CDR regions, or random mismatches? The four numbering schemes are not named.
    - **Why it matters** Antibody numbering is critical for CDR definition and downstream analysis. Even a small fraction of errors could mislead users if they occur in functionally important regions. Without error characterization, the tool’s reliability for antibody research is unclear.
    - **Resolution test** Provide a confusion matrix or error analysis table showing the types and locations of mismatches. Name the four schemes and report per-scheme accuracy. Include a figure showing example alignments where PDV and RIOT agree and disagree.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Validation completeness
    - **Claim pointer** “its interaction detector reproduces PLIP at macro-F1 0.82, matching Arpeggio as closely as PLIP itself does”
    - **Evidence pointer** Abstract; no figure or table provided
    - **Concern** The macro-F1 score of 0.82 is reported without context: what is the test set size? What interaction types are included (e.g., hydrogen bonds, hydrophobic contacts, π-stacking)? How are true positives, false positives, and false negatives defined? The claim that PDV “matches Arpeggio as closely as PLIP itself does” is ambiguous—does this mean PDV’s agreement with PLIP is similar to Arpeggio’s agreement with PLIP? If so, what is the reference value?
    - **Why it matters** Interaction detection is a complex task with many edge cases. Without a clear evaluation protocol, the reported F1 score cannot be assessed for reliability or compared to other tools.
    - **Resolution test** Provide a table showing per-interaction-type precision, recall, and F1 scores for PDV vs. PLIP. Specify the test set (e.g., PDB structures, number of complexes). Include a comparison with Arpeggio using the same test set and evaluation criteria.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Claim about “publication-quality outline rendering”
    - **Evidence pointer** Abstract
    - **Issue** The term “publication-quality” is subjective and not defined. It is unclear what specific rendering features (e.g., anti-aliasing, ray tracing, resolution control) are provided.
    - **Required correction** Define “publication-quality” in terms of specific rendering capabilities (e.g., resolution, anti-aliasing, export formats) or provide a figure comparing PDV output to a standard (e.g., PyMOL).

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Claim about “portable sessions”
    - **Evidence pointer** Abstract
    - **Issue** The term “portable sessions” is vague. Does this mean the entire session state (scene, representations, selections) can be saved and reloaded? In what format? Is it human-readable?
    - **Required correction** Specify the session file format (e.g., JSON, PSE) and describe what state is preserved (e.g., camera position, coloring, selections).

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Antibody-specific toolkit
    - **Evidence pointer** Abstract
    - **Issue** The abstract mentions an “antibody numbering and germline-assignment engine” and a “developability-liability scanner” but provides no details on the germline assignment method or the types of liabilities scanned (e.g., aggregation, immunogenicity, stability).
    - **Required correction** Briefly describe the germline assignment algorithm (e.g., BLAST against IMGT/V-QUEST) and list the liability types detected (e.g., aggregation-prone regions, deamidation sites, oxidation sites).

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Insufficient detail on SASA validation (correlation metric, test set, error analysis)
    - R1-M2: Insufficient detail on antibody numbering validation (error characterization, scheme names)
    - R1-M3: Insufficient detail on interaction detector validation (test set, per-type metrics, comparison baseline)

- **Assessment against Nature-style criteria**
    - **Originality**: Moderate. The concept of a lightweight web viewer with validated analytics is not entirely new (e.g., Mol* has some analysis features), but the combination of a single offline HTML file with validated SASA, antibody numbering, and interaction detection appears novel. The validation approach is a strength.
    - **Scientific importance**: Potentially high for the antibody engineering community, where validated, accessible tools for numbering and developability assessment are in demand. The SASA and interaction detection features are broadly useful for structural biology.
    - **Interdisciplinary readership**: Moderate. The tool is primarily targeted at structural biologists and antibody engineers. The abstract is written in a technical style that may not be accessible to nonspecialists (e.g., “Shrake–Rupley solvent-accessible surface area,” “macro-F1”).
    - **Technical soundness**: Cannot be fully assessed from the abstract alone. The reported validation statistics are promising but lack the detail needed to evaluate their reliability. The tool’s implementation as a modification of 3Dmol.js is a reasonable approach.
    - **Readability for nonspecialists**: The abstract is dense with technical terms and acronyms (SASA, RIOT, PLIP, Arpeggio, macro-F1). A brief explanation of these terms and their significance would improve accessibility.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising tool with impressive validation statistics, but the lack of detail on the validation methodology, error characterization, and tool features prevents a full assessment. The authors should provide the full manuscript with figures, tables, and supplementary data to support their claims.

## Risk / unsupported claims
- “publication-quality outline rendering” – unsupported; no evidence provided.
- “portable sessions” – unsupported; no evidence provided.
- “developability-liability scanner” – unsupported; no details on the types of liabilities or validation.
- “germline-assignment engine” – unsupported; no details on the algorithm or validation.
- The claim that PDV “matches Arpeggio as closely as PLIP itself does” is ambiguous and unsupported without a direct comparison.