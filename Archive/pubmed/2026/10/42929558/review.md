## Review setup
- **Input scope** Full manuscript text (abstract, introduction, implementation, validation, conclusion) without figures, tables, or supplementary material
- **Assessment boundary** Scientific and technical evaluation of the described methodology, validation strategy, and reported results; software usability and reproducibility considerations
- **Shared manuscript claim summary** The authors present GroScore, an open-source Python toolkit for automated scoring of protein–protein interaction (PPI) structures using bidirectional steered molecular dynamics (SMD) with explicit solvent. The tool introduces bidirectional pulling (unbinding and rebinding), an interface-cutout mode for computational efficiency, support for three force fields, and automated handling of small molecules, noncanonical amino acids, structural ions, and crystal waters. Validation on the HADDOCK benchmark (46 complexes) shows significant correlations (Pearson r = 0.51–0.66) across force fields; on the larger PPB-Affinity dataset (2431 successful simulations), weak but significant correlations are reported (Pearson r = 0.16 overall; subset-dependent, up to r = 0.40). CAPRI Score_set testing shows improved near-native pose ranking (49 vs. 40 Top-10) compared to the unidirectional predecessor. Small-molecule ternary complex tests (19 systems) show significant stabilization for 13 cases using the CGI estimator.
- **Visible evidence base** Main text descriptions of validation results; references to Figures 1–3, Table 1, and Supplementary Figures S1–S11 and Table S1 (none of which were provided)
- **Missing materials affecting confidence** All figures, tables, and supplementary material; benchmark dataset composition details; specific correlation values with confidence intervals for individual force fields; computational cost comparisons; software documentation and test suite details

## Reviewer

- **Overall assessment** The manuscript describes a timely and potentially useful software tool that addresses a real need in the PPI scoring field. The bidirectional SMD approach is a sensible methodological improvement over the unidirectional predecessor, and the interface-cutout strategy for computational efficiency is pragmatic. However, the validation results as described are mixed: while the HADDOCK benchmark correlations are encouraging, the PPB-Affinity results are weak in absolute terms, and the authors' explanations for subset-dependent performance, while plausible, are not quantitatively supported in the provided text. The small-molecule ternary complex results are interesting but raise questions about the physical interpretation of the scoring scheme. The manuscript would benefit from clearer presentation of the statistical methods, more detailed reporting of benchmark results, and a more critical discussion of the limitations of the approach for absolute affinity prediction.

- **Who would be interested in the results, and why** Computational structural biologists and bioinformaticians working on protein–protein interaction prediction, docking, and scoring will be the primary audience. Researchers developing or using AI-based structure prediction methods (AlphaFold, RoseTTAFold, etc.) who need post-hoc scoring functions to rank candidate complexes will find this tool relevant. The open-source, automated nature of the software and its integration with GROMACS and SLURM make it potentially attractive for high-throughput applications. The small-molecule handling may also interest researchers working on proximity-inducing compounds (molecular glues, PROTACs), though this application is less thoroughly validated.

- **Major strengths**
  1. The bidirectional pulling approach directly addresses a known limitation (exponential work averaging bias) of the unidirectional predecessor, and the authors provide a clear rationale for this methodological choice.
  2. The interface-cutout mode is a practical and well-motivated strategy for reducing computational cost, and the reported correlation between cutout and no-cutout scores (r = 0.87–0.96) provides evidence that this approximation preserves per-complex ranking.
  3. The software is open-source, automated, and integrates with widely used tools (GROMACS, SLURM), which lowers the barrier to adoption.
  4. Validation across multiple benchmarks (HADDOCK, PPB-Affinity, CAPRI Score_set) and force fields provides a reasonably broad assessment of performance.
  5. The authors are transparent about the limitations of the approach, including the weak absolute correlations on heterogeneous datasets and the deliberate omission of standard-state corrections.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and result interpretation
- **Claim pointer** "Significant positive correlations (Pearson r = 0.51–0.66) of calculated scores to experimental binding affinities were obtained for all tested force fields" (HADDOCK benchmark); "weak but significant correlation (Pearson r = 0.16, Spearman ρ = 0.24)" (PPB-Affinity overall)
- **Evidence pointer** Validation section, Figure 1, Table 1, Figures S1–S4, S10 (none provided)
- **Concern** The manuscript reports correlation coefficients without providing confidence intervals, p-values, or details on the statistical testing procedure. For the HADDOCK benchmark (n = 46), a Pearson r of 0.51–0.66 would have wide confidence intervals, and the authors do not state whether these are significantly different from each other across force fields. For the PPB-Affinity dataset, the overall r = 0.16 with n = 2431 would be statistically significant but practically weak; the authors should report the distribution of scores and residuals, not just the correlation. The subset-dependent results (r = 0.17–0.40) are presented with qualitative explanations but no statistical comparison of whether these differences are significant.
- **Why it matters** The central claim of the paper is that GroScore produces scores that correlate with experimental binding affinities. Without proper uncertainty quantification and statistical testing, the reader cannot assess the reliability of this claim or compare performance across force fields, datasets, or modes (cutout vs. no-cutout). The weak overall correlation on PPB-Affinity raises questions about the practical utility of the method for heterogeneous datasets, and the authors' explanations need quantitative support.
- **Resolution test** Provide 95% confidence intervals for all reported correlation coefficients; state the statistical test used (e.g., t-test for Pearson r) and whether correlations across force fields or datasets are significantly different; include scatter plots with regression lines and residual analysis for the PPB-Affinity subsets; report the distribution of scores for each subset to support claims about dynamic range limitations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of small-molecule ternary complex application
- **Claim pointer** "With CGI, a significant negative shift indicating ternary-complex stabilization by the small molecule was obtained for 13 of the 19 systems" and the subsequent categorization of the six nonsignificant cases
- **Evidence pointer** Validation section, Figure 3 (not provided)
- **Concern** The small-molecule ternary complex validation is presented with only 19 systems, and the authors provide qualitative explanations for the six nonsignificant cases. However, the physical interpretation of the "GroScore difference (glued – non-glued)" is unclear. The authors state that the inducer is "assigned to one of the two binding partners according to its chain identifier" and that "no restraints tether it to its host partner; its association with the host is therefore maintained only by the physical force field." This raises questions about whether the simulation setup adequately samples the inducer's dissociation from its host, and whether the scoring scheme can distinguish between specific stabilization and nonspecific effects. The categorization of the six nonsignificant cases into three groups is based on literature knowledge, but the authors do not provide quantitative criteria for these categories or a statistical framework for evaluating the sensitivity of the method.
- **Why it matters** The small-molecule application is a significant extension of the tool beyond protein-only systems, and the authors claim practical utility for molecular glue and PROTAC scoring. However, with only 19 systems and a 68% success rate, the evidence is preliminary. The physical interpretation of the scoring scheme for ternary complexes needs clarification, and the authors should demonstrate that the method can distinguish between true stabilizers and non-stabilizers with appropriate controls.
- **Resolution test** Provide a more detailed description of the simulation setup for ternary complexes, including how the inducer is positioned and how its dissociation from the host is sampled. Include control experiments with non-binding or weakly binding small molecules. Report the distribution of GroScore differences for all 19 systems with confidence intervals, and provide quantitative criteria for the categorization of nonsignificant cases. If possible, expand the validation set or clearly state the limitations of the current dataset.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark representativeness and generalizability
- **Claim pointer** "Validation on the curated HADDOCK affinity benchmark and the larger and more heterogeneous PPB-Affinity aggregate shows significant correlations with experimental binding data across diverse system classes"
- **Evidence pointer** Validation section, Table 1 (not provided)
- **Concern** The PPB-Affinity dataset is described as "much larger" but the authors report only the overall correlation (r = 0.16) and subset-specific values (r = 0.17–0.40). The subset-dependent performance varies substantially, and the authors attribute this to dataset curation quality and dynamic range. However, the manuscript does not provide details on the composition of each subset (e.g., number of complexes, range of affinities, structural diversity) or the criteria for inclusion. The HADDOCK benchmark (46 complexes) is described as "highly curated" but the overlap with the Affinity Benchmark v5.3 subset of PPB-Affinity is not discussed. The CAPRI Score_set results are presented as a ranking improvement (49 vs. 40 Top-10) but without statistical significance testing or comparison to other scoring methods.
- **Why it matters** The generalizability of GroScore across different types of PPIs is a key claim. Without detailed information on benchmark composition and subset characteristics, the reader cannot assess whether the weak overall correlation reflects method limitations or dataset heterogeneity. The CAPRI results are presented as an improvement over the predecessor but not compared to other state-of-the-art scoring functions, limiting the assessment of GroScore's competitive position.
- **Resolution test** Provide a detailed breakdown of each PPB-Affinity subset (number of complexes, affinity range, structural characteristics, source). Discuss the overlap between the HADDOCK benchmark and the Affinity Benchmark v5.3 subset. For the CAPRI results, report the statistical significance of the improvement (e.g., Wilcoxon signed-rank test) and, if possible, compare to other scoring methods on the same set.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational cost and practical utility
- **Claim pointer** "interface cutout for reduced computational cost" and "showcasing the scoring efficiency of GroScore on consumer-grade hardware"
- **Evidence pointer** Implementation section, Validation section (CAPRI results)
- **Concern** The manuscript claims that the interface cutout mode "dramatically reduces computational cost" and reports throughput of 56 poses/day on an NVIDIA RTX 5080 GPU, but no quantitative comparison of computational cost between cutout and no-cutout modes is provided in the text. The authors mention "small differences in the simulation wall-times without cutout mode between the force fields" but do not report actual wall-times or speedup factors. For a tool intended for high-throughput scoring, the computational cost is a critical practical consideration.
- **Why it matters** The practical utility of GroScore depends on its computational efficiency. If the cutout mode provides only marginal speedup, or if the full-system simulations are prohibitively expensive, the tool's applicability to large-scale screening would be limited. The authors should provide concrete timing data to support their efficiency claims.
- **Resolution test** Report wall-times for cutout vs. no-cutout modes for representative complexes across all force fields, including the speedup factor. Provide a breakdown of computational cost by simulation stage (equilibration, pulling, analysis). Discuss the scaling of computational cost with system size and the practical limits of the approach.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility and software documentation
- **Affected element** Software availability and documentation
- **Evidence pointer** Abstract, Implementation section
- **Issue** The manuscript states that GroScore is available on GitHub under the MIT License, but no version number, dependency list, or link to documentation is provided in the text. The description of the pipeline is high-level, and the specific parameters used for the validation simulations (e.g., pulling rate, spring constant, simulation temperature) are not stated in the main text.
- **Required correction** Provide a specific version number and a link to the documentation in the manuscript. Include a table of key simulation parameters used in the validation studies, or refer to a specific section of the SI where these are listed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity of methodological description
- **Affected element** Interface cutout procedure
- **Evidence pointer** Implementation section, Interface Cutout subsection
- **Issue** The description of the interface cutout procedure is brief. The authors state that residues within 2.0 nm of the interface are retained, but it is unclear how the "interface" is defined (e.g., based on interatomic distances, solvent-accessible surface area, or a combination). The elastic network distance restraints at chain breaks are described, but the choice of force constant (250 kJ·mol–1·nm–2) and the range (0.4–0.9 nm) are not justified.
- **Required correction** Provide a more detailed description of the interface definition and the rationale for the elastic network parameters. If this information is in the SI, refer to the specific section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** CAPRI Score_set results
- **Evidence pointer** Validation section
- **Issue** The CAPRI results are reported as "49 (including 13 high-quality and 23 medium-quality) near-native poses were ranked within the Top-10 of each target, compared to 40 (including 9 high-quality and 21 medium-quality) with the original unidirectional setup." The authors do not report the total number of targets or poses, the distribution of ranks, or any statistical test for the improvement.
- **Required correction** Report the total number of targets and poses, the distribution of ranks (e.g., median, interquartile range), and the result of a paired statistical test comparing the bidirectional and unidirectional methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of weak correlations
- **Affected element** PPB-Affinity results
- **Evidence pointer** Validation section
- **Issue** The authors report a weak overall correlation (r = 0.16) on the PPB-Affinity dataset and attribute this to dataset heterogeneity and dynamic range limitations. However, they do not discuss whether this level of correlation is practically useful for ranking candidate complexes in a screening context, or how it compares to other scoring methods on the same dataset.
- **Required correction** Add a brief discussion of the practical implications of the weak correlation, including a comparison to other scoring methods if available, and a statement about the expected utility of GroScore for ranking in a screening context.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology and scope
- **Affected element** Title and abstract
- **Evidence pointer** Title, Abstract
- **Issue** The title states "Automated Scoring of Protein–Protein Interactions" but the validation includes small-molecule ternary complexes (molecular glues and PROTACs). The abstract mentions "automated handling of small molecules" but does not clearly state that the tool can score ternary complexes. This may be misleading for potential users.
- **Required correction** Clarify in the abstract that the tool supports scoring of ternary complexes involving small-molecule inducers, or adjust the title to reflect the broader scope.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of confidence intervals and statistical tests for all reported correlation coefficients (R1-M1).
  2. Insufficient detail on the small-molecule ternary complex validation, including simulation setup and controls (R1-M2).
  3. Missing quantitative data on computational cost and speedup from the interface cutout mode (R1-M4).
  4. No comparison to other state-of-the-art scoring methods on the same benchmarks, limiting the assessment of GroScore's competitive position.

- **Assessment against Nature-style criteria**
  - **Originality**: The bidirectional SMD approach with interface cutout is a reasonable incremental improvement over existing SMD-based scoring methods, but the core concept of using nonequilibrium work measurements for PPI scoring is not new. The combination of features (bidirectional pulling, multiple force fields, automated small-molecule handling) is somewhat novel, but the methodological advance is modest.
  - **Scientific importance**: PPI scoring is an important problem in structural biology, and a reliable, automated, open-source tool would be valuable. However, the weak correlations on heterogeneous datasets suggest that the method has limited predictive power for absolute affinity prediction, and the authors themselves acknowledge this limitation. The practical utility for high-throughput screening remains to be demonstrated.
  - **Interdisciplinary readership**: The work is primarily of interest to computational structural biologists and bioinformaticians. The methods and results are unlikely to attract a broad interdisciplinary audience beyond this niche.
  - **Technical soundness**: The methodological choices are generally sound and well-motivated, but the statistical reporting is incomplete, and the validation on the small-molecule ternary complex set is preliminary. The lack of comparison to other methods weakens the technical case.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible to readers with a background in molecular dynamics and PPI prediction. The introduction provides a good overview of the field and the limitations of existing methods. However, some technical details (e.g., the CGI estimator) may be challenging for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript describes a useful and potentially valuable software tool, and the methodological improvements over the predecessor are sensible. However, the statistical reporting needs to be strengthened, the small-molecule validation needs more detail and controls, and the computational cost claims need quantitative support. The authors should also provide a comparison to other scoring methods to establish the competitive position of GroScore.

## Risk / unsupported claims
- The claim that bidirectional pulling "overcomes the numerical bias of exponential work averaging" is not quantitatively supported in the provided text; the authors should show a direct comparison of unidirectional vs. bidirectional results on the same systems.
- The claim that the interface cutout mode "dramatically reduces computational cost" is not supported by quantitative data in the provided text.
- The categorization of the six nonsignificant small-molecule ternary complex cases into three groups is based on literature knowledge but is not quantitatively justified.
- The claim that "bidirectional pulling... substantially reduces the anticorrelation between scores and buried surface area" is mentioned but not quantified in the provided text.
- The overall PPB-Affinity correlation (r = 0.16) is described as "weak but significant," but the practical utility of this level of correlation for ranking candidate complexes is not discussed.
- The CAPRI Score_set improvement (49 vs. 40 Top-10) is reported without statistical significance testing or comparison to other methods.