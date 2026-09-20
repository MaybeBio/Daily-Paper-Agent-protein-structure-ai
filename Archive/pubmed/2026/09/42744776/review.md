## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, computational methodology, and evolutionary inference presented in the manuscript
- **Shared manuscript claim summary** The authors investigate the evolutionary emergence of enantioselectivity in plant borneol dehydrogenases (BDHs) using ancestral sequence reconstruction (ASR), identifying a trajectory from the unselective ancestor N30 (E = 12) to the selective ancestor N32 (E > 200) involving 19 mutations, of which one (I111L) is in the active site. They demonstrate that the L111I mutation increases selectivity in N30, while back-mutation I111L decreases selectivity in N32, and that additional peripheral mutations (V136L/G169A/V183I) are required for high selectivity. Crystal structures and machine learning/molecular mechanics (ML/MM) simulations suggest that protein dynamics, rather than static structural changes, shape enantioselectivity, with funnel-metadynamics simulations revealing a correlation between active-site solvent-accessible surface area and selectivity.
- **Visible evidence base** Abstract, full introduction, results and discussion sections, methods section, Table 1, Figures 1-8 (referenced), Supplementary Figures 1-55 (referenced), Supplementary Tables 1-8 (referenced)
- **Missing materials affecting confidence** Supplementary Information files (detailed methods for ASR, crystallography statistics, simulation parameters), Source Data file, Reporting Summary, raw diffraction data, simulation input files and trajectories, sequence alignment files

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental question in evolutionary biochemistry: how does enantioselectivity emerge through natural evolution? The authors combine ancestral sequence reconstruction, structural biology, site-directed mutagenesis, and state-of-the-art computational approaches to dissect the evolutionary trajectory of borneol dehydrogenases. The work is ambitious and the combination of experimental and computational methods is impressive. However, several concerns regarding the robustness of the evolutionary inference, the statistical treatment of the computational results, and the generalizability of the conclusions need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in enzyme engineering, protein evolution, biocatalysis, and computational enzymology would find this work of significant interest. The demonstration that peripheral mutations can act synergistically with an active-site switch to confer high enantioselectivity has practical implications for directed evolution and rational design strategies. The application of ML/MM methods to resolve dynamic differences that conventional MD cannot capture is also of methodological interest to the computational chemistry community. The work bridges fundamental evolutionary biology and applied biocatalysis, making it relevant to a broad readership.

- **Major strengths**
  1. The use of ancestral sequence reconstruction to trace the evolutionary emergence of enantioselectivity is a powerful and timely approach, and the BDH system is well-chosen given the availability of both selective and unselective extant enzymes.
  2. The combination of experimental mutagenesis, crystallography, and multiple computational methods (ML/MM, funnel metadynamics, MM-ISMSA) provides a multi-pronged approach to dissecting the molecular basis of enantioselectivity.
  3. The identification of a single active-site switch (position 111) that requires peripheral mutations for full effect is a nuanced finding that highlights the importance of epistasis in enzyme evolution.
  4. The demonstration that static structures fail to explain enantioselectivity, while dynamic simulations succeed, is an important methodological insight.
  5. The correlation between SASA and enantioselectivity provides a potentially generalizable predictor for engineering efforts.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evolutionary inference robustness
- **Claim pointer** The authors claim that the trajectory from N30 to N32 represents "the critical evolutionary step towards enantioselectivity" and that the identified mutations represent "a plausible evolutionary pathway to stereoselectivity."
- **Evidence pointer** Results and discussion, "Ancestral sequence reconstruction of BDHs" section; Figure 2
- **Concern** The ASR methodology relies on a single reconstruction approach (maximum likelihood with JTT model via PhyML and GRASP). The authors do not report posterior probabilities for individual residues along the N30-N32 branch, nor do they discuss alternative reconstructions (e.g., Bayesian approaches) that might yield different ancestral sequences. The phylogenetic tree includes only 97 sequences from 59 genera, which may be insufficient to confidently resolve deep nodes. Furthermore, the authors state that "all point mutations leading from the common, unselective ancestor N6 of SrBDH1 and to AaBDH2 are amino acid substitutions that occurred in this enzyme family," but this claim requires demonstration that the reconstructed ancestral states are statistically well-supported at each position.
- **Why it matters** The central evolutionary narrative depends on the accuracy of the ancestral sequences. If alternative reconstructions place different residues at position 111 or at the peripheral positions, the entire trajectory and the conclusions about epistasis could change. The claim that this is a "plausible evolutionary pathway" is weaker than the claim that this is the actual pathway, but the manuscript sometimes conflates these.
- **Resolution test** Provide posterior probability or bootstrap support values for the key ancestral nodes (especially N30 and N32) and for the specific residues at positions 111, 136, 169, and 183. Perform a sensitivity analysis using alternative reconstruction methods (e.g., Bayesian inference) and demonstrate that the key conclusions are robust. If alternative reconstructions are possible, discuss how they would affect the interpretation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of computational results
- **Claim pointer** The authors claim that ML/MM simulations "consistently stabilized productive enzyme-substrate configurations and resolved enantiomer-specific behaviors" and that funnel-metadynamics simulations revealed "a correlation between the active-site's solvent-accessible surface area and selectivity."
- **Evidence pointer** Results and discussion, "Biased molecular dynamics simulations" section; Figure 8; Supplementary Figures 27-42; Supplementary Table 8
- **Concern** The statistical treatment of the computational results is insufficient. For the ML/MM simulations, only three 10 ns replicas per system are reported. The funnel-metadynamics results report ΔΔG values with statements about "statistical uncertainty" but the methods for estimating these uncertainties are not described in sufficient detail. The claim of a "correlation" between SASA and selectivity appears to be based on qualitative visual inspection of violin plots rather than a quantitative statistical test. No confidence intervals, effect sizes, or formal hypothesis tests are reported for the key comparisons. The convergence of the funnel-metadynamics simulations is mentioned but the supporting data are only in supplementary figures that were not provided for review.
- **Why it matters** The computational results are central to the mechanistic conclusion that dynamics, not static structure, determine enantioselectivity. Without proper statistical treatment, the reader cannot assess whether the observed differences between enantiomers are robust or could arise from insufficient sampling or random fluctuations. The claim of a SASA-selectivity correlation, if it is to guide future engineering efforts, needs quantitative support.
- **Resolution test** Provide a detailed description of the uncertainty estimation for all reported ΔΔG values, including the block-averaging or bootstrap procedures used. Report the results of formal statistical tests (e.g., permutation tests or t-tests) comparing the SASA distributions between selective and unselective variants. Show convergence plots for the funnel-metadynamics simulations in the main text or provide them in the supplementary information with clear convergence criteria. If the SASA correlation is claimed, report the correlation coefficient and its confidence interval.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation of computational predictions
- **Claim pointer** The authors state that "the peripheral mutations in N30_L111I/L47W/E74K/V79I/E153Q/Y197H are mainly located in loop regions or termini of the α-helices pointing away from the active site" and that these mutations contribute to enantioselectivity through epistatic effects.
- **Evidence pointer** Results and discussion, "Analysis of evolutionary pathways between ancestors" section; Table 1; Figure 6
- **Concern** The manuscript reports that N30_L111I/L47W/E74K/V79I/E153Q/Y197H and N30_L111I/V136L/G169A/V183I both achieve high enantioselectivity (E > 200), but the mechanistic explanation for why these particular combinations of peripheral mutations work is largely descriptive. The authors do not perform reciprocal mutations in N32 to test whether the reverse mutations (e.g., N32 with the N30 peripheral residues) would reduce selectivity, nor do they test whether the peripheral mutations alone (without L111I) have any effect on selectivity. The claim that these mutations act epistatically would be strengthened by a more systematic mutational analysis.
- **Why it matters** The manuscript's central claim is that epistasis between the active-site switch and peripheral mutations is required for high enantioselectivity. However, the experimental design does not fully test this claim. Without reciprocal mutations or single-peripheral-mutation controls, alternative explanations (e.g., that the peripheral mutations independently contribute to selectivity) cannot be excluded.
- **Resolution test** Perform reciprocal mutations in N32 (e.g., N32_L136V/A169G/V183I and N32_L47W/E74K/V79I/E153Q/Y197H) to test whether removing the N32 peripheral residues reduces selectivity. Test individual peripheral mutations in the N30_L111I background to determine which mutations are necessary and sufficient for the high-selectivity phenotype. If the manuscript is already in revision, at minimum discuss these alternative interpretations explicitly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions
- **Claim pointer** The authors conclude that "this example of the natural emergence of this important catalytic feature will guide future protein engineering endeavors to improve enzyme selectivity."
- **Evidence pointer** Results and discussion, final paragraph
- **Concern** The manuscript studies a single enzyme family (BDHs) and a single substrate (1-borneol). The conclusion that the findings will "guide future protein engineering endeavors" is a strong claim that requires discussion of the extent to which the identified principles (peripheral mutations, dynamics-based selectivity) are likely to generalize to other enzyme families. The authors do not discuss whether the BDH system is representative or exceptional in terms of the evolutionary mechanisms identified.
- **Why it matters** The broader significance of the work, and its relevance to the Nature-style criteria of broad impact, depends on the generalizability of the findings. If the mechanisms identified are specific to BDHs, the impact is more limited.
- **Resolution test** Add a discussion section that addresses the generalizability of the findings, drawing on the existing literature on enantioselectivity evolution in other enzyme families. If the authors believe the findings are generalizable, they should articulate the specific principles that are likely to transfer and the conditions under which they would not.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of nomenclature
- **Affected element** Abstract and throughout
- **Evidence pointer** Abstract, "Ancestral sequence reconstruction of BDHs" section
- **Issue** The manuscript uses "E" for enantioselectivity (E = 12, E > 200) but also uses "E" in the context of "E-value" and "Ecomp." The distinction between these terms is not always clear, particularly in the abstract where "E = 12" appears without explanation of the measurement method.
- **Required correction** Define the enantiomeric ratio (E) and the competitive E-value (Ecomp) clearly at first use, and ensure consistent usage throughout the manuscript. Consider using a subscript or different notation to distinguish between the two.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figure 8
- **Evidence pointer** Figure 8
- **Issue** The kernel density estimate (KDE) plots in Figure 8b and 8e are described as showing "mean values from 3 x 10 ns ML/MM simulations" but the figure itself does not clearly indicate the spread of the data across replicas. The box plots in Figure 8c and 8f show medians and interquartile ranges but the number of data points per box is not stated.
- **Required correction** Add the number of data points to the box plots and consider overlaying individual replica data points on the KDE plots to show the spread across replicas.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methods completeness
- **Affected element** Methods, "Funnel metadynamics simulations" section
- **Evidence pointer** Methods, "Funnel metadynamics simulations" section
- **Issue** The methods section for funnel metadynamics does not specify the collective variables used beyond "projection and extension funnel coordinates," nor does it describe how the funnel parameters were chosen. The reference to a tutorial for funnel maker is helpful but the specific parameters for this system should be stated.
- **Required correction** Provide the specific collective variables, funnel dimensions, and the rationale for the chosen parameters. If the parameters were optimized, describe the optimization procedure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement (not provided in the manuscript text)
- **Evidence pointer** Not applicable
- **Issue** The manuscript does not include a data availability statement in the provided text. Given the computational nature of the work, it is important to state where the simulation input files, trajectories, and analysis scripts can be accessed.
- **Required correction** Add a data availability statement that specifies where the computational data and analysis scripts are deposited (e.g., Zenodo, GitHub) and how to access them.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting of kinetic data
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The specific activities in Table 1 are reported as mean ± standard deviation, but the number of replicates (n) is not stated in the table or in the methods section for the activity measurements.
- **Required correction** State the number of replicates for the activity measurements in the methods section and add the n value to the table legend.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Discussion of alternative hypotheses
- **Affected element** Results and discussion, "Analysis of evolutionary pathways between ancestors" section
- **Evidence pointer** Results and discussion, "Analysis of evolutionary pathways between ancestors" section
- **Issue** The authors propose that the loss of activity toward (−)-1-borneol in N32 is due to the I111L mutation affecting the water relay mechanism. However, they do not discuss alternative explanations, such as direct steric hindrance of the (−)-enantiomer by the isoleucine side chain or changes in substrate binding orientation.
- **Required correction** Add a brief discussion of alternative mechanistic explanations and why the water relay hypothesis is favored over these alternatives.

## Risk / unsupported claims
- The claim that the identified trajectory from N30 to N32 represents "the critical evolutionary step towards enantioselectivity" is not fully supported without posterior probability or bootstrap support values for the ancestral reconstructions at the key nodes.
- The claim of a "correlation between the active-site's solvent-accessible surface area and selectivity" is not quantitatively supported; no correlation coefficient or statistical test is reported.
- The statement that "all point mutations leading from the common, unselective ancestor N6 of SrBDH1 and to AaBDH2 are amino acid substitutions that occurred in this enzyme family" is presented as a fact but requires demonstration that the reconstructed ancestral states are statistically well-supported.
- The claim that the findings "will guide future protein engineering endeavors" is an extrapolation that is not supported by evidence of generalizability beyond the BDH family.
- The assertion that "protein dynamics rather than structural changes shape these catalytic properties" is based on computational simulations that were not fully validated experimentally; the experimental data (crystal structures) show no major structural differences, but the causal link between dynamics and selectivity is inferred from simulations alone.
- The statement that "N32 is more strongly adapted to high enantioselectivity than N30" is based on a single mutational analysis and requires additional experimental support to be fully established.