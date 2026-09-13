## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full manuscript, figures, tables, or supplementary materials provided
- **Shared manuscript claim summary** The authors present PDV, a single-file offline HTML molecular visualization tool built on 3Dmol.js, with four re-implemented analytical engines (SASA, antibody numbering and germline assignment, non-covalent interaction detection, developability-liability scanning), each validated against established references with reported quantitative agreement.
- **Visible evidence base** Abstract text only; no code repository, benchmark datasets, validation protocols, or comparison details are accessible
- **Missing materials affecting confidence** Full manuscript, validation methodology, benchmark dataset compositions, statistical analysis details, software architecture description, and any figures or tables

## Reviewer
- **Overall assessment** The abstract describes a potentially useful tool that addresses a genuine gap between lightweight web viewers and feature-rich desktop software. The reported validation metrics are impressive at face value, but the abstract alone provides insufficient detail to assess the rigor of the benchmarking, the generalizability of the results, or the practical usability of the tool. The claims are plausible but not fully verifiable from the supplied material.
- **Who would be interested in the results, and why** Structural biologists, protein engineers, and antibody researchers who need quick, installation-free structural analysis without sacrificing quantitative accuracy. The tool could also appeal to educators and researchers in resource-limited settings where desktop software installation is impractical.
- **Major strengths** The tool addresses a real and well-articulated need. The choice to validate each engine against established references is commendable and directly supports the credibility of the quantitative claims. The single-file offline delivery model is a practical and innovative solution to accessibility barriers.
- **Major Concerns** The abstract reports high agreement metrics but does not describe the validation conditions, dataset selection criteria, or potential biases. The claim of "validated" analytics requires scrutiny of whether the reference implementations were used correctly and whether the test sets are representative. The scope of the developability-liability scanner is not defined, making its validation status unclear.
- **Minor Comments** The abstract would benefit from clarifying the relationship between PDV and 3Dmol.js in terms of licensing and code provenance. The performance characteristics for large structures or complex scenes are not mentioned. The user interface and learning curve are not addressed.
- **Technical failings that need to be addressed before the case is established** The validation methodology is not described in sufficient detail to assess whether the reported metrics are meaningful. Specifically, the SASA correlation range, the numbering accuracy threshold, and the interaction detector F1 score all require context on dataset composition, error definitions, and comparison baselines.
- **Assessment against Nature-style criteria** Originality: moderate, as the combination of features in a single-file web tool is novel, though each individual component exists elsewhere. Scientific importance: potentially high for the antibody engineering community, but the abstract does not demonstrate a unique scientific insight. Interdisciplinary readership: the tool could attract readers from structural biology, immunology, and computational chemistry, but the abstract is written primarily for a specialist audience. Technical soundness: not fully assessable from the abstract; the validation claims are promising but under-specified. Readability for nonspecialists: the abstract is dense and assumes familiarity with multiple specialized tools and metrics.
- **Recommendation posture** Supportive if technical concerns are resolved, specifically if the full manuscript provides rigorous validation details and the tool is demonstrated to be robust and usable in practice.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "PDV’s SASA reproduces FreeSASA at Pearson r ≈ 0.997–0.998 across 2,582 structures spanning proteins, nucleic acids and ligands"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract reports a Pearson correlation range but does not specify the exact comparison protocol, such as whether the same atomic radii and probe radius were used, how surface area was computed for nucleic acids and ligands, or whether the 2,582 structures were selected to avoid redundancy or bias.
- **Why it matters** Pearson correlation can be high even with systematic offsets or scaling errors. Without details on the comparison metric, error distribution, and dataset composition, the claim of "reproduces" is not fully substantiated.
- **Resolution test** The full manuscript should provide a detailed methods section describing the SASA algorithm parameters, the reference implementation version, the dataset selection criteria, and a scatter plot or error analysis showing agreement beyond a single correlation coefficient.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "its numbering reproduces RIOT for over 99.88% of 1.3 million residue positions across 16,996 sequences and four schemes"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not clarify what constitutes a "reproduced" position, how mismatches were defined, or whether the four numbering schemes were weighted equally. The threshold of 99.88% is high, but the failure modes and their structural or functional significance are not discussed.
- **Why it matters** Numbering accuracy is critical for antibody analysis, and even small error rates can affect downstream applications such as CDR identification or germline assignment. The abstract does not indicate whether errors are random or systematic.
- **Resolution test** The full manuscript should define the exact matching criteria, provide a breakdown of errors by scheme and sequence type, and discuss any systematic failure cases with examples.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "its interaction detector reproduces PLIP at macro-F1 0.82, matching Arpeggio as closely as PLIP itself does"
- **Evidence pointer** Abstract; location not provided
- **Concern** The macro-F1 score is reported without context on the interaction types included, the dataset size, or the definition of a true positive. The comparison to Arpeggio is vague, as the abstract does not state the Arpeggio-to-PLIP agreement metric used for the comparison.
- **Why it matters** Interaction detection is highly sensitive to parameter choices and interaction definitions. Without a clear benchmark protocol, the F1 score cannot be interpreted as evidence of reliable performance.
- **Resolution test** The full manuscript should specify the interaction categories, the benchmark dataset, the annotation protocol, and provide a detailed comparison table showing PDV, PLIP, and Arpeggio performance on identical inputs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope and completeness
- **Claim pointer** "a developability-liability scanner" is listed as one of the four validated engines
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not describe what the developability-liability scanner detects, what reference it was validated against, or what metrics were used. This is the only engine without a reported validation result.
- **Why it matters** Developability assessment is a key selling point for antibody researchers, and an unvalidated or under-described component undermines the overall claim of "validated quantitative analytics."
- **Resolution test** The full manuscript should describe the scanner's feature set, the validation reference, and the performance metrics, or explicitly state if this component is not yet validated.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Tool description
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states PDV is "an extensive modification of 3Dmol.js" but does not clarify the extent of modification or whether the original 3Dmol.js license terms are compatible with the PolyForm Noncommercial License.
- **Required correction** Provide a brief statement on code provenance and license compatibility in the full manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Usability
- **Affected element** Performance characteristics
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not mention performance limits, such as maximum structure size or number of objects, which could affect practical use.
- **Required correction** Include a performance benchmark or a statement on expected limitations in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Availability
- **Evidence pointer** Abstract; location not provided
- **Issue** The tool is available at a specific URL, but the abstract does not state whether the source code is accessible for inspection or modification.
- **Required correction** Clarify the availability of source code and any versioning information.

## Risk / unsupported claims
- The claim that PDV "brings validated, quantitative structural analysis into a no-install, simple to use tool" is not fully supported by the abstract alone, as the validation details are not provided.
- The developability-liability scanner is listed as validated but no validation evidence is reported in the abstract.
- The statement that PDV "matches Arpeggio as closely as PLIP itself does" is not verifiable without the specific comparison metric and dataset.
- The generalizability of the SASA validation across "proteins, nucleic acids and ligands" is not assessable without dataset composition details.