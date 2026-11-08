## Review setup
- **Input scope** Full manuscript text (abstract, introduction, design, results, conclusions, availability, data availability) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, benchmark validity, and software utility as presented in the provided text
- **Shared manuscript claim summary** The authors present PHENOMS, an open-source Python package with a Rust-accelerated engine for hydrogen-bond analysis in MD trajectories, claiming significant computational speedups over existing tools, biological validity via retrospective EGFR case studies, and robust reproducibility features
- **Visible evidence base** Text descriptions of benchmarks (Table 1, Table S1 referenced but not visible), biological case study descriptions (Fig. 2 referenced but not visible), software architecture descriptions, and availability statements
- **Missing materials affecting confidence** All figures, tables, supplementary data, benchmark scripts, and the actual software repository contents; no quantitative benchmark data visible; no validation statistics; no comparison of biological results to experimental data beyond qualitative statements

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software tool for hydrogen-bond analysis in MD simulations, with a plausible design and a clear motivation rooted in HDX-MS interpretation. However, the provided text alone does not establish the core claims. The benchmark results are only described narratively with no visible data tables or figures, the biological validation is qualitative and lacks statistical rigor, and several methodological details are insufficiently specified. The software availability and reproducibility infrastructure are commendable, but the scientific case as presented is incomplete.
- **Who would be interested in the results, and why** Computational structural biologists, HDX-MS practitioners seeking atomistic interpretation of protection data, and researchers developing or using MD analysis tools. The performance claims, if substantiated, would interest those analyzing large trajectories or many replicates. The integration of HDX-MS with MD analysis addresses a genuine need in the field.
- **Major Strengths** The software addresses a real methodological gap by linking HDX-MS protection patterns to atomistic hydrogen-bond dynamics. The Rust-accelerated design is a sensible approach to a known performance bottleneck. The emphasis on reproducibility, including unit tests, Docker workflows, and Zenodo deposition, is exemplary. The focus on per-frame hydrogen-bond resolution rather than filtered or averaged results is scientifically defensible.
- **Major Concerns** The benchmark claims are not verifiable from the provided text. The biological validation is qualitative and does not demonstrate statistical significance or quantitative agreement with experimental data. The quality control criteria are described but their sensitivity and specificity are not evaluated. The comparison with MDAnalysis uses different hydrogen-bond definitions, confounding the performance comparison. The manuscript does not describe how the residue-level protection scores are calibrated or validated against experimental HDX-MS data.
- **Minor Comments** The abstract claims an average 16-fold speedup and up to 100-fold, while the introduction claims 7- to 22-fold over MDAnalysis and up to ~115-fold over MDTraj, and the results section reports 11-fold and 115-fold for the full system. These numbers are not internally consistent. The description of the quality control module is detailed but the thresholds appear arbitrary without sensitivity analysis. The statement about the "reproducibility crisis" is supported by citations but the connection to PHENOMS is somewhat tangential. The manuscript would benefit from a clearer statement of what is new relative to the authors' prior publications (references 11, 12, 16, 24).
- **Technical failings that need to be addressed before the case is established** The benchmark data must be presented in full. The biological case studies need quantitative comparison with experimental HDX-MS data, including appropriate statistical measures. The hydrogen-bond definition used by PHENOMS must be compared with MDAnalysis under matched conditions to support the performance claims. The protection score calculation needs explicit mathematical definition and validation.
- **Assessment against Nature-style criteria** Originality: moderate. The concept of linking HDX-MS to MD hydrogen-bond analysis is not new, and the authors cite prior work in this direction. The Rust acceleration is an engineering contribution rather than a conceptual advance. Scientific importance: potentially significant for the HDX-MS and MD communities, but the demonstrated impact is not yet established. Interdisciplinary readership: the tool bridges computational chemistry and experimental biophysics, which could attract a broad audience, but the current presentation is heavily software-focused. Technical soundness: cannot be fully assessed without the missing data; the described architecture is reasonable but the validation is insufficient. Readability for nonspecialists: the manuscript is generally clear but assumes familiarity with both HDX-MS and MD analysis; the software-oriented sections may be dense for experimentalists.
- **Recommendation posture** Currently not established from the provided evidence. The software may be useful and the approach is sound, but the core claims of performance and biological validity require the missing data and additional validation before the case is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims benchmark speedups of 7- to 22-fold over MDAnalysis and up to ~115-fold over MDTraj, and an average 16-fold speedup with up to 100-fold in the abstract.
- **Evidence pointer** Table 1, Table S1, Results section "Algorithmic Efficiency Benchmark" (tables not visible in provided material)
- **Concern** The benchmark results are described only in prose. No actual data table, figure, or numerical comparison is visible in the provided text. The numbers cited in the abstract, introduction, and results are not fully consistent with each other. The comparison with MDAnalysis uses different hydrogen-bond definitions, which confounds the performance comparison.
- **Why it matters** The performance claims are a central selling point of the software. Without visible benchmark data, the claims cannot be verified or reproduced by readers. The inconsistent numbers across sections raise questions about the robustness of the measurements. The unmatched hydrogen-bond definitions mean the speedup could reflect algorithmic differences rather than raw performance.
- **Resolution test** Provide the full benchmark tables with all systems, trajectory lengths, and thread counts. Run MDAnalysis with identical Baker-Hubbard criteria to enable a matched comparison. Ensure all reported speedup values are consistent across abstract, introduction, and results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The manuscript claims that PHENOMS "recapitulate[s] HDX-MS protection patterns" and "identifies the EGFR L858R hotspot mutation site" in the biological case study.
- **Evidence pointer** Results section "Biological Benchmark", Fig. 2 (not visible in provided material)
- **Concern** The biological validation is described only qualitatively. The text states that PHENOMS "indicated the A-loop region is among the regions exhibiting the largest increases in conformational dynamics" and that this is "consistent with" published HDX-MS findings. No quantitative comparison, statistical test, or correlation coefficient is provided. The claim of identifying the L858R hotspot is not substantiated with any numerical or statistical evidence.
- **Why it matters** The biological relevance of the tool depends on demonstrating that its output meaningfully correlates with experimental HDX-MS data. A qualitative statement of consistency is insufficient to establish this. Without quantitative validation, readers cannot assess the reliability or sensitivity of the method.
- **Resolution test** Provide a quantitative comparison between PHENOMS-derived protection scores and experimental HDX-MS protection values, including appropriate statistical measures (e.g., correlation coefficients, confidence intervals). Show that the identified hotspot is statistically significant relative to the distribution of scores across all residues.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological specification
- **Claim pointer** The manuscript describes a "residue-level score" that "serves as a proxy for changes in protection against hydrogen exchange" and can be "exported directly into PDB B-factors."
- **Evidence pointer** Design and Implementation section "Differential Analysis and Network Topology" (location not provided)
- **Concern** The mathematical definition of the protection score is not provided. The text describes what the score does but not how it is calculated. The relationship between hydrogen-bond occupancy, bond persistence, and the final residue-level score is unclear. The calibration of this score against experimental HDX-MS data is not described.
- **Why it matters** The protection score is the key output that links the software to HDX-MS interpretation. Without a precise definition, users cannot understand what the score means, how to interpret its magnitude, or how to compare it across studies. The claim that it can be used as a proxy for protection requires validation that is not presented.
- **Resolution test** Provide the explicit mathematical formula for the protection score, describe how it is derived from hydrogen-bond metrics, and validate its relationship to experimental protection values using a calibration dataset.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark scope
- **Claim pointer** The manuscript claims that PHENOMS is suitable for "large systems and long trajectories" and demonstrates this with a 1,000-frame benchmark.
- **Evidence pointer** Results section "Algorithmic Efficiency Benchmark", Table S1 (not visible in provided material)
- **Concern** The 1,000-frame benchmark is only mentioned for PLCγ2, and MDTraj was excluded due to memory requirements. The scaling behavior for larger systems or longer trajectories is not described. The memory footprint of PHENOMS is not quantified.
- **Why it matters** The claim of suitability for large systems and long trajectories is central to the tool's utility. Without data on memory usage, scaling with system size, or performance on multi-microsecond trajectories, this claim is not established.
- **Resolution test** Provide memory usage measurements and scaling data across a range of system sizes and trajectory lengths. Include a discussion of the practical limits of the software.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction (location not provided)
- **Issue** The speedup values are reported inconsistently. The abstract states "average 16-fold speedup (up to 100-fold)", the introduction states "7- to 22-fold faster than MDAnalysis and up to ~115-fold faster than MDTraj", and the results section reports "approximately 11-fold and 115-fold speedups" for the full system. These numbers should be reconciled.
- **Required correction** Ensure all speedup values are consistent across sections, or clearly explain the different contexts in which each value applies.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Benchmark methodology
- **Affected element** Results section "Algorithmic Efficiency Benchmark"
- **Evidence pointer** Results section (location not provided)
- **Concern** The comparison with MDAnalysis uses different hydrogen-bond definitions, which the authors acknowledge. This is a reasonable choice for "typical out-of-the-box usage" but limits the interpretability of the speedup.
- **Required correction** Consider adding a matched-criteria comparison as a supplementary analysis to separate algorithmic efficiency from definitional differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Software validation
- **Affected element** Design and Implementation section
- **Evidence pointer** Design and Implementation section (location not provided)
- **Issue** The manuscript mentions a "comprehensive unit test suite" but does not describe what is tested or the coverage achieved.
- **Required correction** Provide a brief description of the test coverage and the types of validation performed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Availability section
- **Evidence pointer** Availability and Future Directions section (location not provided)
- **Issue** The Docker-based benchmarking workflow is mentioned but not described in detail. The Zenodo deposition is stated but the contents are not enumerated.
- **Required correction** Describe what the Docker workflow includes and what data and scripts are deposited on Zenodo.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction (location not provided)
- **Issue** The manuscript cites prior work from the authors' group (references 11, 12, 16, 24) but does not clearly state what is new in PHENOMS relative to these earlier methods.
- **Required correction** Add a paragraph explicitly distinguishing PHENOMS from the authors' prior contributions.

## Risk / unsupported claims
- The benchmark speedup values (7- to 22-fold, up to 115-fold, average 16-fold, up to 100-fold) are not verifiable from the provided text as the underlying data tables are not visible.
- The claim that PHENOMS "recapitulates HDX-MS protection patterns" is unsupported by quantitative evidence in the provided text.
- The claim of identifying the EGFR L858R hotspot mutation site is not substantiated with statistical analysis.
- The suitability of PHENOMS for "large systems and long trajectories" is not established without memory usage and scaling data.
- The protection score's validity as a proxy for HDX-MS protection is asserted but not validated with experimental calibration data.
- The statement that PHENOMS "captures protein dynamic behavior that directly corroborates published HDX-MS observations" is qualitative and cannot be assessed without the actual comparison data.