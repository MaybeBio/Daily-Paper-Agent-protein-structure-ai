## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and figure legends as provided.
- **Assessment boundary** The review is based solely on the provided manuscript text. No supplementary figures, tables, or source data files were available for inspection. Statistical analyses and simulation details were assessed from the methods description only.
- **Shared manuscript claim summary** The authors propose that proteins containing native non-covalent lasso entanglements (NCLEs) are more prone to misfolding via entanglement changes, and that this misfolding has divergent consequences: some entangled proteins are preferentially ubiquitinated and degraded by the proteasome, while others misfold into near-native states that evade degradation and persist in cells.
- **Visible evidence base** Abstract; main text sections (Results, Discussion); Methods sections describing logistic regression, coarse-grained simulations, metastable state clustering, and co-translational folding simulations; Figure 1–3 descriptions; Table 1 listing proteins used in simulations.
- **Missing materials affecting confidence** Supplementary Figures S1–S32, Supplementary Tables S1–S8, Supplementary Data 1 and 2, and Source Data were not provided. These are referenced for key results including per-protein misfolding probabilities, Qnorm values, rSASA values, contingency tables, and simulation parameters. Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting question: whether entanglement-related misfolding has measurable consequences for protein homeostasis, specifically proteasomal degradation. The combination of proteome-wide ubiquitination data with coarse-grained simulations is a reasonable approach. However, the current evidence base has several limitations. The statistical association between NCLEs and ubiquitination is based on a binary classification of proteins as ubiquitinated or not, which may be sensitive to thresholds and data quality. The simulation component relies on a coarse-grained model with parameters that are not fully justified, and the sample size of 10 proteins per group is small. The central claim that near-native misfolded states evade degradation is supported only indirectly, through simulation metrics (Qnorm, rSASA) rather than direct experimental evidence. The manuscript would be strengthened by additional validation, sensitivity analyses, and a clearer articulation of the causal model linking misfolding to ubiquitination.

- **Who would be interested in the results, and why** Researchers in protein folding, proteostasis, and protein quality control would be the primary audience. The work connects a structural feature (entanglement) to a functional outcome (degradation), which could interest those studying the molecular basis of protein misfolding diseases. Computational biologists working on coarse-grained simulations of protein folding may also find the methodological approach relevant. The claim that near-native misfolded states are widespread and persistent could have implications for understanding age-related loss of protein function.

- **Major strengths**
  1. The question is novel and timely, connecting a recently described class of misfolding to a well-studied degradation pathway.
  2. The use of existing proteome-wide ubiquitination data is efficient and provides a broad context.
  3. The combination of statistical analysis with mechanistic simulations is a thoughtful approach.
  4. The authors acknowledge limitations of their simulation model and discuss alternative interpretations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "proteins containing native non-covalent lasso entanglements (NCLEs) are 93% more likely to be ubiquitinated and targeted for proteasomal degradation than proteins lacking native entanglements"
- **Evidence pointer** Results section "Natively entangled proteins are 93% more likely to be ubiquitinated"; Methods "Logistic regression analysis"; Table S1 (not provided)
- **Concern** The logistic regression analysis relies on a binary classification of proteins as ubiquitinated (YU) or non-ubiquitinated (NU) based on detection of Kε-GG peptides. This classification is highly dependent on detection limits, peptide coverage, and the threshold used to define "young" ubiquitination. The authors do not report how many proteins were classified as YU versus NU, what fraction of the proteome each represents, or how sensitive the odds ratio is to the choice of thresholds. The 93% effect size is reported with a confidence interval, but the underlying data quality and potential misclassification bias are not addressed. Additionally, the analysis includes only proteins with high-quality AlphaFold structures (pLDDT ≥ 85), which may introduce selection bias if structural quality correlates with other properties relevant to ubiquitination.
- **Why it matters** If the binary classification is noisy or biased, the reported odds ratio may be inflated or spurious. The central claim of the paper depends on this statistical association being robust and meaningful.
- **Resolution test** The authors should provide a detailed breakdown of the YU and NU protein sets, including numbers, overlap with the full proteome, and sensitivity analyses varying the thresholds for young age and ubiquitination status. They should also consider continuous measures of ubiquitination rather than binary classification, and test whether the association holds when controlling for additional covariates such as protein abundance, expression level, or structural class.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "entanglement misfolding, primarily through failure to form native entanglements, increases susceptibility to proteasomal degradation"
- **Evidence pointer** Results section "Young ubiquitinated, entangled proteins are more prone to misfolding"; Figure 2G; Methods "Estimation of protein misfolding propensity"
- **Concern** The causal direction is asserted but not established. The authors show that entangled proteins are more likely to be ubiquitinated and that entangled proteins have higher misfolding probabilities in simulations. However, they do not demonstrate that misfolding is the cause of ubiquitination for these specific proteins. Ubiquitination could be driven by other features correlated with entanglement, such as protein length, surface hydrophobicity, or expression levels. The simulation results show a correlation between group membership (YU vs NU) and misfolding propensity, but this does not establish that misfolding causes ubiquitination. The authors acknowledge this in the Discussion ("implies but does not establish a causal role"), but the abstract and title present the relationship more strongly.
- **Why it matters** The title and abstract make a causal claim that is not supported by the evidence presented. Overstating the causal relationship could mislead readers and overstate the significance of the findings.
- **Resolution test** The authors should either soften the causal language throughout the manuscript or provide additional evidence for causality, such as experiments where misfolding is modulated and ubiquitination is measured, or analyses showing that misfolding propensity mediates the relationship between entanglement and ubiquitination.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation validity
- **Claim pointer** "ubiquitinated proteins with native entanglements are four-fold more likely to misfold than non-ubiquitinated proteins without entanglements"
- **Evidence pointer** Results section "Young ubiquitinated, entangled proteins are more prone to misfolding"; Figure 2G; Methods "Temperature quenching simulations"
- **Concern** The coarse-grained simulation model is a Gō-based model, which is known to bias folding toward the native state and may not accurately capture misfolding kinetics or thermodynamics. The authors use a temperature quench protocol (800 K to 310 K) that is far from physiological conditions. The choice of 2 μs simulation time is arbitrary, and the claim that misfolded states are "long-lived" is based on extrapolation from these short simulations. The sample size of 10 proteins per group is small, and the selection criteria for these proteins (random selection after excluding transmembrane and elongated proteins) may not be representative. The authors do not report the uncertainty in the misfolding probability estimates beyond bootstrap confidence intervals, and the hierarchical bootstrap method is not fully described.
- **Why it matters** The simulation results are used to provide a mechanistic explanation for the statistical association. If the simulations are not reliable or representative, the mechanistic interpretation is weakened.
- **Resolution test** The authors should provide more details on the simulation model validation, including comparisons to experimental folding data where available. They should also report the distribution of misfolding probabilities across all proteins in each group, not just the group means, and discuss whether the results are robust to changes in simulation time, temperature protocol, and model parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "approximately one-third of the globular proteome populates near-native entanglement-misfolded states that evade proteasomal degradation"
- **Evidence pointer** Discussion section; based on extrapolation from simulation results
- **Concern** This estimate is derived from a small sample of 10 proteins per group and relies on the assumption that the simulation results can be extrapolated to the entire proteome. The authors do not describe how this estimate was calculated, what assumptions were made, or what the uncertainty is. The claim that these states "evade proteasomal degradation" is inferred from the absence of ubiquitination, but absence of ubiquitination does not necessarily mean the protein is misfolded or that it evades degradation through other pathways.
- **Why it matters** This is a strong quantitative claim that goes beyond the data presented. If the estimate is not well-supported, it could be misleading.
- **Resolution test** The authors should provide a clear description of how the one-third estimate was derived, including the statistical model and assumptions. They should also discuss alternative explanations for why some entangled proteins are not ubiquitinated, such as efficient chaperone-mediated refolding or degradation by non-proteasomal pathways.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Protein entanglement misfolding" is used as a noun phrase, which is grammatically awkward and may confuse readers unfamiliar with the concept.
- **Required correction** Consider rephrasing to "Misfolding involving changes in protein entanglement" or "Entanglement-related protein misfolding" for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Natively entangled proteins are 93% more likely to be ubiquitinated"
- **Evidence pointer** Results section; Table S1 (not provided)
- **Issue** The odds ratio is reported with a 95% confidence interval, but the number of proteins in each group and the model fit statistics (e.g., pseudo-R², concordance) are not reported. The contingency table is referenced as Table S1, which was not available for review.
- **Required correction** Report the sample sizes, the number of events (YU proteins) in each group, and basic model fit statistics in the main text or in a table that is included in the main manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods "Processing other independent human ubiquitination datasets"
- **Evidence pointer** Methods section
- **Issue** The description of the threshold selection for classifying proteins as ubiquitinated in the independent datasets is vague. The authors state that a threshold was identified corresponding to "the separation between the two major modes of the observed distribution," but do not describe how this was done objectively or whether the threshold was pre-specified.
- **Required correction** Provide a more detailed description of the threshold selection procedure, including whether it was data-driven or pre-specified, and report the actual threshold values used for each dataset.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph on evolutionary trade-offs
- **Evidence pointer** Discussion section
- **Issue** The discussion of evolutionary trade-offs is speculative and not directly supported by the data presented. While this is appropriate for a Discussion section, the authors should clearly distinguish between conclusions drawn from their data and hypotheses for future work.
- **Required correction** Add explicit language indicating that the evolutionary implications are speculative and require further investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods "Temperature quenching simulations"
- **Evidence pointer** Methods section
- **Issue** The methods state that "the force field parameters were tuned to reproduce the structural stability of each protein" but do not provide the actual parameter values or the criteria used for tuning. The final parameter values are referenced as Tables S6–S8, which were not available.
- **Required correction** Include the parameter values in the main text or a supplementary table that is provided with the manuscript, and describe the tuning procedure in sufficient detail for reproduction.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2G and 2H
- **Issue** The figure shows group-level comparisons of misfolding probability, but individual protein-level data points are not shown. Given the small sample size (n = 10 per group), it is important to see the distribution of values across individual proteins.
- **Required correction** Add individual data points to the figure or provide them in a supplementary table.

## Risk / unsupported claims
- The claim that "approximately one-third of the globular proteome populates near-native entanglement-misfolded states that evade proteasomal degradation" is not supported by the data presented. This estimate appears to be derived from a small simulation sample and is not accompanied by a clear statistical derivation.
- The claim that near-native misfolded states "evade proteasomal degradation" is inferred from the absence of ubiquitination, but absence of ubiquitination does not establish that the protein is misfolded or that it evades degradation.
- The causal claim that "entanglement misfolding... increases susceptibility to proteasomal degradation" is not established. The data show an association, but causality is not demonstrated.
- The generalizability of the findings to "diverse organisms" is asserted without direct evidence from non-human systems.
- The statement that "90% of the non-ubiquitinated, entangled proteins exhibit misfolding" is based on a small sample (n = 10) and the criterion for "exhibiting misfolding" (95% CI not overlapping zero) is not a standard hypothesis test and may be overly liberal.