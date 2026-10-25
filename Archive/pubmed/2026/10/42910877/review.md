## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations of seven tripeptides (six C-terminal amidated D/Y/F sequence isomers plus FFD) to compute conformational free-energy landscapes based on intramolecular side-chain dihedral angles. They introduce a novel numerical method to characterize these landscapes and report a correlation between thermal conformational accessibility and self-assembly propensity. They also evaluate water model effects on conformational ensembles and investigate ionization state influences. The methodology is claimed to implicitly account for sequence context, have low computational cost, and represent progress toward theory-informed design of peptide materials.
- **Visible evidence base** Abstract text only; no quantitative results, correlation coefficients, simulation parameters, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation protocols, force field parameters, water model specifications, ionization state definitions, statistical analyses, and any validation of the proposed numerical characterization method

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach linking single-molecule conformational ensembles to supramolecular self-assembly outcomes. The idea of using side-chain dihedral-based free-energy landscapes as a predictor is plausible and potentially useful. However, the abstract provides insufficient quantitative evidence to evaluate the strength of the claimed correlation, the robustness of the novel method, or the generality of the conclusions. The scope is narrow (seven tripeptides), and the leap from single-molecule simulations to assembly propensity requires more careful justification than is visible here.
- **Who would be interested in the results, and why** Researchers in peptide self-assembly, computational biophysics, and peptide materials design would be interested. The work addresses a practical need for low-cost computational predictors of assembly behavior, which is relevant to the growing field of sequence-defined peptide materials. The water model comparison may also interest those developing simulation protocols for short peptides.
- **Major strengths** The approach is computationally economical, using single-molecule simulations rather than expensive multi-molecule assembly simulations. The focus on sequence isomers is a well-chosen test case because it isolates sequence context effects. The explicit consideration of water model and ionization state effects shows methodological awareness.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The correlation between conformational accessibility and self-assembly propensity is stated without any quantitative support. The novel numerical method for characterizing FELs is not described in sufficient detail to assess its validity or reproducibility. The predictive claim is based on only seven peptides, which is a very small sample for establishing a general scheme.
- **Assessment against Nature-style criteria** Originality is moderate; the idea of using conformational ensembles to predict assembly is not entirely new, though the specific use of side-chain dihedral collective variables and the numerical characterization method may offer novelty. Scientific importance is limited by the narrow scope and lack of demonstrated predictive power beyond the specific sequences studied. Interdisciplinary readership is plausible given the intersection of computational chemistry and materials science, but the abstract does not clearly articulate broader implications. Technical soundness cannot be assessed from the abstract alone; the absence of methodological detail and quantitative results is a significant barrier. Readability for nonspecialists is acceptable but the abstract assumes familiarity with FELs and MD terminology.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises a correlation and a novel method but provides no numbers, no statistical measures, and no validation. A supportive posture would require the full manuscript to demonstrate the strength and significance of the correlation, the robustness of the method, and the generality of the conclusions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim a correlation between thermal conformational accessibility and a sequence's tendency to self-assemble or remain in solution.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that a correlation is found but provides no quantitative details. No correlation coefficient, significance level, number of data points, or effect size is reported. It is unclear whether the correlation is strong, weak, or merely suggestive given only seven sequences.
- **Why it matters** The central claim of the paper rests on this correlation. Without quantitative support, the reader cannot judge whether the relationship is meaningful or coincidental. The small sample size of seven peptides makes statistical robustness particularly important.
- **Resolution test** Provide the correlation coefficient, a measure of statistical significance, and ideally a leave-one-out or cross-validation analysis to show that the correlation is not driven by a single outlier sequence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors introduce a novel method to numerically characterize the computed FELs.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe what this novel method is, how it works, or what it measures. Terms such as "thermal conformational accessibility" are introduced without definition. The reader cannot assess whether the method is sound, reproducible, or genuinely novel.
- **Why it matters** A novel method is a key contribution of the paper. If the method is not clearly described and justified, the work cannot be evaluated or built upon by others. Reproducibility is a core requirement for computational methods.
- **Resolution test** Provide a detailed description of the method in the full manuscript, including the mathematical formulation, the parameters used, and a validation against known systems or alternative characterization approaches.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope and generalizability
- **Claim pointer** The methodology is claimed to be "an important advancement toward a general scheme for the theory-informed design of peptide materials."
- **Evidence pointer** Abstract, location not provided
- **Concern** The study uses only seven tripeptides, all with D, Y, or F side chains. This is a very limited chemical space. The claim of advancement toward a general scheme is not supported by the evidence presented. It is unclear whether the correlation would hold for other amino acids, longer peptides, or different assembly conditions.
- **Why it matters** The broader significance of the work depends on its generalizability. If the approach only works for a narrow class of sequences, its practical utility is limited. The abstract overreaches relative to the evidence.
- **Resolution test** Either temper the claim in the abstract to reflect the limited scope, or provide additional data in the full manuscript showing that the approach extends to other sequence families or peptide lengths.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "thermal conformational accessibility" is used without definition. It is unclear whether this refers to the population of accessible states at a given temperature, the free-energy barrier heights, or some other metric.
- **Required correction** Define the term explicitly when first used, and state how it is computed from the FEL.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Water model comparison
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that water model selection effects are evaluated and rationalized, but no specific water models are named and no findings are summarized.
- **Required correction** Name the water models compared and briefly state the key finding, such as which model produced the most reliable ensembles or how the models differed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Ionization state investigation
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions investigating ionization state effects but does not state which ionization states were considered or what the outcome was.
- **Required correction** Specify the ionization states studied and summarize the main result, such as whether protonation state significantly altered the conformational ensembles.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Experimental validation
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not state whether the self-assembly propensities used for the correlation are from experiments or from other simulations. This is important for interpreting the nature of the correlation.
- **Required correction** Clarify the source of the self-assembly propensity data, and if experimental, cite the relevant measurements.

## Risk / unsupported claims
- The correlation between thermal conformational accessibility and self-assembly propensity is unsupported by any quantitative data in the abstract.
- The novelty and validity of the numerical method for characterizing FELs cannot be assessed from the abstract.
- The claim of advancement toward a general design scheme is unsupported given the limited sequence scope.
- The water model and ionization state findings are mentioned but not described, making them unevaluable.
- The relationship between single-molecule conformational ensembles and multi-molecule assembly outcomes is asserted but not mechanistically justified in the abstract.