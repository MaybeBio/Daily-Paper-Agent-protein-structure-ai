## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, results, discussion, funding, data availability)
- **Assessment boundary** Technical soundness and scientific validity of the proposed Voronoi-based time-dependent analysis framework as applied to titin I27 MD simulations; claims regarding the method's utility for detecting protein conformational changes
- **Shared manuscript claim summary** The authors present a Voronoi tessellation-based computational framework for analyzing time-dependent amino acid side-chain packing in MD trajectories. Applied to titin I27 at 300 and 400 K, the method tracks per-residue Voronoi volume changes and neighbor reorganization, identifying localized "breathing" motions and internal packing shifts that precede or accompany conformational changes. The authors claim this approach offers advantages over existing tools in terms of modularity, low-level control, and ability to capture subtle dynamic events.
- **Visible evidence base** Main text with Figures 1-4 referenced; Supplementary Figures S1-S6 and Movie S1 mentioned but not provided; GitHub repository for code availability
- **Missing materials affecting confidence** Supplementary figures (S1-S6) and Movie S1 are referenced but not included in the provided material; no raw data or trajectory files; no validation against experimental data or established methods; no statistical analysis details beyond mean/SD; no convergence or error analysis for the MD simulations

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful computational tool for time-resolved Voronoi analysis of protein packing in MD simulations. The methodological framework is clearly described and the demonstration on titin I27 shows some interesting observations. However, the scientific claims regarding the method's ability to detect "subtle changes preceding conformational transitions" are not fully supported by the evidence presented. The analysis is largely descriptive, lacks quantitative validation, and the biological significance of the observed changes remains unclear. The manuscript would benefit from stronger validation against established methods, more rigorous statistical treatment, and a clearer demonstration of unique insights that this method provides over existing approaches.

- **Who would be interested in the results, and why** Computational biophysicists and molecular dynamics practitioners studying protein dynamics, allostery, and folding would be the primary audience. Researchers developing geometric analysis tools for biomolecular simulations may find the modular framework valuable. Those studying protein packing and its relationship to conformational change could use this approach to complement existing analyses. The method's potential application to protein-protein interfaces and surface hydration may interest researchers in protein engineering and drug design.

- **Major strengths** 
  1. The methodological framework is clearly described with a logical workflow (Figure 1) and the code is made openly available, supporting reproducibility.
  2. The use of Voro++ for time-resolved analysis is a sensible adaptation of an established library, and the modular design allows for flexible customization.
  3. The demonstration on titin I27 at two temperatures provides a concrete example of the method's capabilities, including the identification of residue-specific volume changes and neighbor reorganization events.
  4. The authors appropriately acknowledge limitations of simple volume measurements and discuss potential extensions of the method.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Validation
  - **Claim pointer** The authors claim the method can detect "subtle changes preceding protein conformational transition or unfolding" and identify "areas where intra-protein shifts and 'proteinquakes' originate."
  - **Evidence pointer** Results section, Figures 2-3; location not provided
  - **Concern** The manuscript does not provide quantitative validation of the Voronoi-based volume measurements against established methods or experimental data. While the authors mention comparison with CHARMM COOR VOLUme (Methodology section), no results of this comparison are shown. The claim that the method can detect events "preceding" conformational changes is not supported by any predictive analysis or comparison with known transition states. The single 200-ns trajectory at each temperature is insufficient to establish statistical significance of the observed events.
  - **Why it matters** Without validation, the reader cannot assess whether the Voronoi volumes and neighbor dynamics accurately reflect physical packing changes. The claim of detecting precursors to conformational transitions requires either multiple independent trajectories showing consistent pre-transition signals or comparison with known experimental/structural data. The current evidence is largely descriptive and could reflect simulation artifacts or stochastic fluctuations.
  - **Resolution test** Provide comparison of Voronoi volumes with CHARMM COOR VOLUme results for the same trajectories. Include multiple independent simulations (at least 3 replicates) to assess reproducibility of the observed events. If claiming detection of pre-transition events, demonstrate that the identified changes consistently precede a known conformational transition in a test system with established transition behavior.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance / Biological significance
  - **Claim pointer** The authors state the framework is "useful for extracting geometric yet physically relevant information" and can inform "protein allostery, conformational change, and folding."
  - **Evidence pointer** Abstract, Introduction, Concluding Discussion; location not provided
  - **Concern** The biological significance of the observed changes is not established. The manuscript describes volume changes and neighbor reorganization at 400 K but does not connect these observations to specific functional implications for titin I27 or general principles of protein dynamics. The relevance to allostery, folding, or conformational change is asserted but not demonstrated. The choice of titin I27 as a demonstration system is not justified in terms of known allosteric behavior or conformational transitions.
  - **Why it matters** For a methods paper, demonstrating biological utility is essential to establish the method's value to the community. Without clear biological context or functional interpretation, the observations remain phenomenological. The claim that this approach can inform allostery and conformational change requires at least one example where the method provides insights not obtainable from standard analyses (RMSD, RMSF, contact maps).
  - **Resolution test** Apply the method to a system with well-characterized allosteric transitions or conformational changes and demonstrate that the Voronoi-based analysis reveals new mechanistic insights. Alternatively, provide a more detailed functional interpretation of the titin I27 observations in the context of its known mechanical properties and immunoglobulin domain behavior.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Methodology
  - **Claim pointer** The authors state that the solvent layer provides "a boundary where Voronoi cells of surface residues in contact with solvent can be built" and that the 5 Å (7 Å for 400 K) cutoff is sufficient.
  - **Evidence pointer** Methodology, Preprocessing and Voronoi Tessellation; location not provided
  - **Concern** The choice of solvent shell thickness (5 Å or 7 Å) is not justified. The authors do not demonstrate that this cutoff is sufficient to avoid boundary effects on Voronoi cell calculations for surface residues. The difference in cutoff between 300 K and 400 K systems introduces a potential confound when comparing results between temperatures. No sensitivity analysis is provided to show that results are robust to the choice of solvent shell thickness.
  - **Why it matters** Voronoi cell volumes and neighbor relationships for surface residues depend critically on the surrounding solvent molecules included in the calculation. An insufficient solvent shell could lead to artificial truncation of Voronoi cells and incorrect volume estimates. The different cutoffs at the two temperatures could bias the temperature comparison.
  - **Resolution test** Perform a sensitivity analysis with varying solvent shell thicknesses (e.g., 3, 5, 7, 10 Å) and show that the key results are robust. Justify the choice of different cutoffs for the two temperatures or use the same cutoff for both.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Statistical rigor
  - **Claim pointer** The authors describe "significant" differences and "sharp increases" in volumes and neighbor reorganization events.
  - **Evidence pointer** Results section, Figures 2-4; location not provided
  - **Concern** No statistical analysis is provided for the observed differences between 300 K and 400 K. The manuscript reports mean values and standard deviations but does not perform hypothesis testing, confidence interval estimation, or effect size calculations. The identification of "significant" events appears to be based on visual inspection of traces rather than quantitative criteria.
  - **Why it matters** Without statistical rigor, the reader cannot distinguish genuine temperature-dependent effects from random fluctuations. The stochastic nature of MD simulations requires appropriate statistical treatment, especially when making claims about specific events at specific time points.
  - **Resolution test** Provide statistical tests (e.g., t-tests, Mann-Whitney U tests) for volume differences between temperatures. For time-resolved events, use change-point detection algorithms or define quantitative thresholds for what constitutes a "significant" change. Report confidence intervals for all key measurements.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / Reproducibility
  - **Affected element** Methodology, MD Simulation
  - **Evidence pointer** Methodology section; location not provided
  - **Issue** The manuscript states that the system was neutralized with Na and Cl at "about 50-mM concentration" but does not specify the exact number of ions added or the method used to determine this concentration. The equilibration protocol is described but key parameters (e.g., pressure coupling method, temperature coupling constants during production) are not fully specified.
  - **Required correction** Provide exact ion counts, specify the ion placement method, and include all relevant simulation parameters in a table or supplementary material to ensure reproducibility.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Presentation / Figure quality
  - **Affected element** Figure 2B
  - **Evidence pointer** Results section, Figure 2B; location not provided
  - **Issue** The color scale in Figure 2B is described but the figure itself is not provided in the manuscript text. The authors should ensure that the color scale is clearly legible and that the mapping between colors and volume changes is intuitive.
  - **Required correction** Ensure all figures are self-explanatory with clear legends, color bars, and axis labels. Consider adding a schematic in Figure 1 that more clearly illustrates the workflow steps.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction, Concluding Discussion
  - **Evidence pointer** Introduction section; location not provided
  - **Issue** The manuscript cites several Voronoi-based tools but does not provide a systematic comparison of their capabilities versus the proposed method. The claim that existing tools "limit modularity and make customized trajectory analysis less convenient" is not quantitatively supported.
  - **Required correction** Provide a table comparing features of existing tools (e.g., MOLE, TRAVIS, Voronoia, Voronota) with the proposed method, including computational efficiency, output options, and customization capabilities.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical clarity
  - **Affected element** Methodology, Postprocessing
  - **Evidence pointer** Methodology section; location not provided
  - **Issue** The description of how neighbor faces are identified and how multiple atoms within the same residue are combined is somewhat vague. The statement "multiple interfaces for atoms belonging to a single neighboring residue were combined to count only as one neighbor" needs more detail on the algorithm.
  - **Required correction** Provide pseudocode or a more detailed algorithmic description of the neighbor counting and face identification procedures.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results, Temperature-Dependent Behaviors
  - **Evidence pointer** Results section, Figure 2A; location not provided
  - **Issue** The total Voronoi volume difference of 624 Å³ between 300 and 400 K is reported as an average over 200 ns, but the time-dependence of this difference is not shown. It is unclear whether this difference is constant or grows over time.
  - **Required correction** Show the time evolution of the volume difference or provide a time-averaged value with a measure of temporal variability.

## Risk / unsupported claims
- The claim that the method can detect "subtle changes preceding protein conformational transition or unfolding" is not supported by the presented evidence, as no transition or unfolding event is analyzed.
- The assertion that the approach can inform "protein allostery, conformational change, and folding" is speculative and not demonstrated with specific examples.
- The statement that existing Voronoi tools "limit modularity and make customized trajectory analysis less convenient" is not quantitatively supported by comparative benchmarks.
- The claim that the 5 Å solvent shell is sufficient for accurate Voronoi cell construction is not validated with sensitivity analysis.
- The biological significance of the observed volume changes and neighbor reorganization at 400 K is not established.
- The comparison between 300 K and 400 K results may be confounded by the different solvent shell cutoffs used (5 Å vs 7 Å).
- The manuscript does not demonstrate that the observed events are reproducible across independent simulations.