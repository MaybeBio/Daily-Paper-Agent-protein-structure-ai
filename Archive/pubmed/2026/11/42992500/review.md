## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a molecular dynamics study of tobacco mosaic virus coat protein (TMVcp) under three conditions (Native, high hydrostatic pressure, and high hydrostatic pressure plus low temperature), using replicate-resolved analysis to characterize volumetric, hydration, and conformational responses. They report robust volumetric changes, condition-dependent near-protein hydration, and reproducible but non-dominant conformational redistribution, while explicitly cautioning against over-interpretation regarding equilibrium convergence or antibody remodelling.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or supplementary data provided
- **Missing materials affecting confidence** Full methods (force field, water model, barostat/thermostat settings, pressure-coupling scheme, system construction), all figures and tables, replicate-level trajectory data, convergence diagnostics, epitope definition and analysis details, statistical test specifications, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a carefully worded and methodologically self-aware study of pressure and pressure-cooling effects on TMVcp. The authors make a commendable effort to distinguish robust volumetric and hydration effects from weaker conformational signals, and they explicitly avoid overclaiming. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the simulations, the appropriateness of the statistical analyses, or the biological relevance of the findings. The claim of "non-dominant conformational redistribution" is intriguing but cannot be assessed without seeing the underlying distributions and convergence evidence. The study may be of interest to the biophysics and high-pressure biology communities, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in high-pressure biophysics, protein hydration and volumetric properties, and computational biophysics would find the replicate-resolved approach and the distinction between pressure-driven densification and cooling-associated hydration effects of interest. Those studying virus capsid assembly or coat protein dynamics under extreme conditions may also find relevance, though the abstract does not establish direct biological implications.
- **Major strengths** The explicit use of replicate-resolved analysis with three independent velocity-initialised runs per condition is a methodological strength. The authors' caution in distinguishing robust volumetric effects from weaker conformational signals, and their explicit statement that equilibrium convergence is not implied, reflects appropriate scientific restraint. The normalization of water occupancy for bulk densification is a thoughtful analytical step that strengthens the hydration claims.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors report specific volumetric changes (box volume decrease of 9.15% under HHP and 11.49% under HHP+LT) and density increases (10.07% and 12.98%) relative to Native.
  - **Evidence pointer** Abstract results section; location not provided
  - **Concern** The abstract provides no information about the simulation parameters that would determine whether these volumetric changes are physically meaningful. No force field, water model, barostat algorithm, or pressure-coupling scheme is specified. The box volume changes could be artefacts of the barostat response time, the coupling constant, or the system size. Without this information, the reported percentages cannot be evaluated for physical plausibility.
  - **Why it matters** The central quantitative claims of the paper rest on the fidelity of the pressure coupling and the equilibration protocol. If the barostat settings are inappropriate for the timescale or system size, the reported volume and density changes could be simulation artefacts rather than physical responses.
  - **Resolution test** Provide full simulation parameters in the methods, including force field, water model, barostat type and coupling constants, equilibration protocol, and system composition. Show that the box volume reached a stable plateau within the production window for each condition.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical validity
  - **Claim pointer** The authors report that PC1-PC2 did not separate conditions (Jensen-Shannon divergence 0.771 versus 0.768; p = 0.476), while PC3-PC4 showed significant separation (0.545 within conditions and 0.773 across conditions; p = 0.0143).
  - **Evidence pointer** Abstract results section; location not provided
  - **Concern** The selection of PC3-PC4 after observing that PC1-PC2 did not separate conditions raises a clear multiple-comparisons concern. The authors state that a "selection-aware exact permutation" retained significance, which suggests they attempted to address this, but the abstract does not describe how the selection was incorporated into the permutation procedure. Without details on the selection rule, the number of PCs tested, and the exact permutation scheme, the reported p-value of 0.0143 cannot be evaluated for validity.
  - **Why it matters** If the PC selection was data-driven and the permutation test did not properly account for the selection step, the reported significance could be inflated. This would undermine the central claim of "reproducible but non-dominant conformational redistribution."
  - **Resolution test** Describe the exact selection procedure and the permutation scheme in detail, including how the selection of PC3-PC4 was incorporated into the null distribution. Report results for all PCs tested, not only the selected ones.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Convergence and reproducibility
  - **Claim pointer** The authors report that "first-half versus second-half divergences indicated incomplete convergence" while also claiming "reproducible but non-dominant conformational redistribution."
  - **Evidence pointer** Abstract results section; location not provided
  - **Concern** The abstract simultaneously reports incomplete convergence and reproducible conformational differences. These two statements are in tension. If the simulations have not converged, the observed differences between conditions could reflect differential relaxation rates rather than steady-state conformational preferences. The 20 ns timescale with only 200 ps discarded is short for protein conformational sampling, and the abstract provides no evidence that the observed differences are stable over longer timescales.
  - **Why it matters** The claim of "reproducible" conformational redistribution requires that the observed differences are not merely transient responses to the pressure/temperature jump. If the system has not converged, the reported conformational differences may not represent equilibrium or quasi-equilibrium properties.
  - **Resolution test** Provide convergence diagnostics beyond first-half versus second-half comparisons, such as block averaging, cumulative average analyses, or extended simulation times. Show that the condition-associated differences persist when the analysis window is extended or when the discarded equilibration period is increased.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological relevance
  - **Claim pointer** The authors state that "Endpoint epitope comparisons showed residue-level enrichment for Native and HHP+LT, but not HHP" and that findings do not imply "causal antibody remodelling."
  - **Evidence pointer** Abstract results section; location not provided
  - **Concern** The abstract introduces epitope comparisons without any prior context in the abstract. No definition of the epitope, the antibody, or the comparison method is provided. The relevance of this analysis to the overall study is unclear, and the authors' own caution that this does not imply causal antibody remodelling suggests the finding is preliminary at best.
  - **Why it matters** If the epitope analysis is intended to connect the biophysical findings to potential immunological implications, the lack of context and the explicit caveat weaken the significance of this result. If it is not intended to have biological implications, its inclusion is confusing.
  - **Resolution test** Provide clear context for the epitope analysis in the introduction and methods, including the definition of the epitope, the rationale for the comparison, and the limitations of endpoint-only analysis. Clarify whether this analysis is exploratory or hypothesis-driven.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract methods section; location not provided
  - **Issue** The term "sequential pressure and pressure-cooling molecular-dynamics pathway" is not standard terminology and is not defined in the abstract.
  - **Required correction** Define what is meant by "sequential" in this context, or use more standard terminology such as "equilibration followed by production" or "stepwise pressure/temperature application."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Effect sizes
  - **Evidence pointer** Abstract results section; location not provided
  - **Issue** The abstract reports p-values for the Jensen-Shannon divergence comparisons but does not report effect sizes or confidence intervals. The difference between 0.771 and 0.768 (p = 0.476) is described as non-significant, but the magnitude of the difference that would be biologically or physically meaningful is not discussed.
  - **Required correction** Report effect sizes or standardized differences alongside p-values, and discuss what magnitude of divergence would constitute a meaningful conformational difference.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Simulation details
  - **Evidence pointer** Abstract methods section; location not provided
  - **Issue** The abstract states that 200 ps were discarded as equilibration, but no justification is provided for this choice. For a 20 ns simulation, 200 ps is a small fraction, and the equilibration period may be insufficient for the system to relax after a pressure or temperature change.
  - **Required correction** Justify the 200 ps equilibration discard with reference to system relaxation timescales, or provide evidence that key observables stabilized within this period.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Statistical test details
  - **Evidence pointer** Abstract results section; location not provided
  - **Issue** The "selection-aware exact permutation" test is mentioned but not described. The reader cannot evaluate whether this test is appropriate or correctly implemented.
  - **Required correction** Provide a brief description of the permutation procedure in the abstract or refer to a methods section where the full details are given.

## Risk / unsupported claims

- The claim of "robust volumetric changes" is plausible but cannot be fully evaluated without simulation parameters and convergence evidence.
- The claim of "reproducible but non-dominant conformational redistribution" is not fully supported given the acknowledged incomplete convergence.
- The claim that the residual hydration increase after normalization "persisted for HHP+LT (+4.9%)" is presented as a key finding but the statistical significance of this residual is not reported.
- The epitope comparison result is presented without sufficient context and is explicitly caveated by the authors; it should be treated as exploratory.
- The statement that findings "distinguish pressure-driven densification from cooling-associated local hydration effects" is a strong interpretive claim that requires the full evidence base to evaluate.
- The absence of any information about the starting structure, protonation states, or system size means that the generalizability of the findings to other TMVcp constructs or conditions cannot be assessed.