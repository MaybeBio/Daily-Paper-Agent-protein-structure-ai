## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends. Supplementary materials referenced but not provided.
- **Assessment boundary** Scientific validity, methodological rigor, interpretation of results, and clarity of claims as presented in the manuscript. No assessment of editorial fit or publication priority beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors evaluate Boltz-2's ability to predict kinase-inhibitor interaction patterns, including potency rankings, binding probability classification, mutation-dependent sensitivity shifts, and structural features, across eight kinases and nine inhibitors, concluding that relative patterns are reproduced more consistently than absolute potency values.
- **Visible evidence base** Main text figures (Figs. 1–7), Supplementary Tables S1–S17 as referenced, and Methods section describing benchmark construction, prediction workflows, and statistical analyses.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S18) were not provided. Experimental IC50 data curation details, complete prediction output tables, and structural comparison data are referenced but unavailable for verification. This materially limits assessment of data quality, statistical robustness, and reproducibility.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and relevant question: whether generative structure-prediction models like Boltz-2 can capture pharmacologically meaningful kinase-inhibitor interactions. The study design is thoughtful, with careful attention to sequence input definitions, statistical baselines, and potential training-data overlap. The finding that relative potency patterns are better reproduced than absolute values is plausible and useful. However, the manuscript has several significant weaknesses. The benchmark is small (57 wild-type pairs, eight kinases, nine inhibitors), and the authors appropriately acknowledge this, but the strength of some conclusions exceeds what this sample size supports. The structural analyses rely on a single representative structure per system, which may not capture the stochasticity of generative models. The training-data overlap analysis is incomplete, and the authors correctly note they cannot exclude prior exposure. The comparison with AlphaFold 3 and Chai-1 is limited to 12 complexes and does not include affinity prediction comparisons. The FI_RMSD analysis is exploratory and underpowered. The sequence-context effects, while interesting, are observed in only two kinases and require validation. The manuscript is generally well-written and accessible, but the discussion sometimes overreaches relative to the evidence presented. The methods are described in sufficient detail for replication, which is a strength. Overall, this is a competent and potentially useful benchmarking study, but the claims need to be tempered and several analyses need strengthening before the conclusions are fully established.

- **Who would be interested in the results, and why** Computational biologists and medicinal chemists working on kinase inhibitor discovery would find this study useful, as it provides practical guidance on interpreting Boltz-2 outputs for kinase targets. Researchers developing or benchmarking generative protein-ligand prediction models would also be interested, as the study highlights strengths and limitations of Boltz-2 in a focused therapeutic context. The discussion of training-data overlap and the distinction between relative and absolute prediction accuracy is relevant to anyone using such models for drug discovery applications.

- **Major strengths** The study addresses a clinically relevant and timely question with a carefully designed benchmark. The use of multiple sequence input definitions and statistical baselines strengthens the analysis. The residual analysis revealing potency-dependent compression is insightful. The explicit discussion of training-data overlap and its implications is commendable. The comparison with established scoring methods provides useful context. The manuscript is clearly written and the methods are described in sufficient detail for replication.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness and generalizability
- **Claim pointer** The authors claim that "mutation-dependent shifts in inhibitor sensitivity, inhibitor selectivity patterns, and overall potency rankings showed substantial agreement with the experimental patterns within the present benchmark" and that "relative kinase-inhibitor interaction patterns were reproduced more consistently than absolute potency values."
- **Evidence pointer** Results sections "Assessment of Boltz‑2 inhibitor potency predictions" and "Assessment of mutation‑dependent inhibitor sensitivity"; Figs. 1 and 3; Supplementary Tables S2, S5, S8, S9
- **Concern** The benchmark comprises only 57 wild-type pairs and a small number of mutants. The correlation coefficients (r = 0.81–0.82) are reported with confidence intervals, but the number of independent observations is limited. More critically, the mutation analysis appears to rely on a very small number of mutant-inhibitor pairs (the text mentions ABL1 T315I, EGFR T790M, EGFR C797S, and BRAF V600E, but the total number of mutant pairs is not stated). With such a small sample, the claim of "substantial agreement" for mutation-dependent shifts is not well supported. The authors acknowledge the benchmark is focused, but the strength of the conclusions should be tempered accordingly. Additionally, the generalizability to other kinases and inhibitors beyond this panel is unknown.
- **Why it matters** The central claim of the paper is that Boltz-2 reproduces relative interaction patterns. If the sample size is too small to support this claim statistically, the main conclusion is not established. Readers may over-interpret the results as evidence of general utility when the evidence is limited to a narrow panel.
- **Resolution test** Provide the total number of mutant-inhibitor pairs analyzed and report confidence intervals or effect sizes for the mutation-dependent shift analysis. If the sample is too small for inferential statistics, explicitly frame the mutation results as descriptive case studies. Alternatively, expand the benchmark to include more mutants and inhibitors to increase statistical power.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Training-data overlap and claim of predictive utility
- **Claim pointer** The authors state that "within the present benchmark, relative kinase-inhibitor interaction patterns were reproduced more consistently than absolute potency values" and suggest "potential utility for comparative analyses in which relative changes in drug response are of primary interest."
- **Evidence pointer** Discussion section; Methods section "Benchmark construction and experimental data curation"; Supplementary Tables S13, S14
- **Concern** The authors acknowledge that 11 of 12 structural benchmark pairs had potential direct structural training exposure, and that many affinity measurements were publicly available before Boltz-2's release. This means the evaluation is not a test of generalization but rather of reconstruction or memorization for most systems. The authors correctly note this limitation, but the framing of "potential utility" for comparative analyses is still problematic. If the model has seen the training data, the observed agreement may not reflect genuine predictive ability. The authors do not provide any analysis that separates systems with and without potential training overlap, nor do they attempt to quantify the degree of overlap. Without such analysis, the predictive utility claim is not established.
- **Why it matters** The scientific value of a benchmarking study depends on whether the results reflect genuine predictive capability or training-data memorization. If the latter, the conclusions are not informative for real-world applications where novel kinase-inhibitor pairs are the target.
- **Resolution test** Perform a stratified analysis comparing prediction accuracy for systems with and without potential training overlap. If the number of non-overlapping systems is too small, explicitly state that the results cannot distinguish memorization from generalization and temper the utility claims accordingly. Alternatively, use a temporally separated or prospectively curated benchmark to avoid this issue.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural analysis methodology
- **Claim pointer** The authors claim that "ligand-pose variability was associated with prediction behavior within the evaluated kinase-inhibitor systems" and that "larger RMSDLig values were not associated with larger prediction errors in magnitude, but were linked to systematic shifts in prediction bias."
- **Evidence pointer** Results section "Structural accuracy and ligand-pose variability in predicted complexes"; Figs. 4 and 5; Supplementary Tables S11–S13
- **Concern** The structural analysis relies on a single representative structure per system, selected as the prediction closest to the median predicted log10(IC50). This selection criterion is based on the affinity prediction, not on structural quality. The relationship between RMSDLig and prediction error is based on this single structure, which may not be representative of the full ensemble of predictions. The authors do not report how much structural variability exists across the ten runs for each system, nor do they analyze whether the relationship between RMSDLig and prediction error is stable across runs. The correlation of r = −0.42 is described as "moderate" but is based on a small number of systems (12 for the model comparison). The Mann–Whitney U test result (p = 7.74 × 10⁻⁴) is reported, but the sample size for this comparison is not stated.
- **Why it matters** The claim that ligand-pose variability is linked to prediction bias is potentially important, but the methodology used to establish it is not robust. If the relationship is not stable across prediction runs, the conclusion is not reliable. The small sample size further weakens the claim.
- **Resolution test** Report the distribution of RMSDLig values across all ten runs for each system, and analyze the relationship between RMSDLig and prediction error using all runs rather than a single representative structure. Provide the sample size for the Mann–Whitney U test. If the relationship is not stable across runs, temper the claim accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model comparison fairness
- **Claim pointer** The authors state that "Boltz-2 and AlphaFold 3 showed broadly similar RMSDLig distributions, whereas Chai-1 exhibited greater complex-dependent variability" and that "Boltz-2 showed the strongest agreement with experimental log10(IC50) values" compared to RTMScore, MMGBSA, and MMPBSA.
- **Evidence pointer** Results sections "Structural accuracy and ligand-pose variability in predicted complexes" and "Comparison with established affinity-scoring baselines"; Supplementary Tables S12, S15–S17
- **Concern** The comparison between Boltz-2, AlphaFold 3, and Chai-1 is limited to ligand-pose RMSD for 12 complexes. The comparison with RTMScore, MMGBSA, and MMPBSA is limited to affinity correlation for 57 pairs. These are different metrics and different system sets, making direct comparison difficult. More importantly, the affinity-scoring baselines were applied as rescoring methods to Boltz-2-predicted structures, which may disadvantage them. A fairer comparison would use each method's own predicted structures or experimental structures. The authors acknowledge this limitation, but the framing of "Boltz-2 showed the strongest agreement" is still somewhat misleading given the methodological asymmetry.
- **Why it matters** The claim that Boltz-2 outperforms established methods is central to the paper's utility argument. If the comparison is not fair, the conclusion is not supported.
- **Resolution test** Either apply all methods to the same set of structures (e.g., experimental structures) or use each method's own predicted structures for affinity scoring. If this is not feasible, explicitly state that the comparison is a rescoring benchmark conditioned on Boltz-2 structures and temper the claim of superiority.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Sequence context analysis
- **Claim pointer** The authors claim that "sequence-context extension had a stronger effect on binding probability estimates than on quantitative affinity prediction" and that "the extended C-terminal regions formed additional folded structural elements surrounding the kinase-domain C-lobe and activation loop."
- **Evidence pointer** Results section "Sequence-context effects on predicted kinase-inhibitor interactions"; Figs. 6 and 7; Supplementary Tables S4, S18
- **Concern** The sequence-context analysis is limited to EGFR and HER2, with some observations for ABL1 and BRAF. The claim that binding probability is more sensitive to sequence context than predicted log10(IC50) is based on a small number of systems. The structural interpretation, that extended regions form folded elements near the activation loop, is based on visual inspection of predicted structures without quantitative validation. The authors do not provide any statistical test for the difference in sequence-context sensitivity between binding probability and log10(IC50). The observation is interesting but exploratory.
- **Why it matters** The sequence-context findings could have practical implications for how users should construct inputs for Boltz-2 predictions. However, if the finding is not robust, users may be misled.
- **Resolution test** Provide statistical tests comparing the magnitude of sequence-context effects on binding probability versus log10(IC50) across all systems. Quantify the structural changes induced by sequence extension (e.g., distance between extended regions and activation loop) rather than relying on visual inspection. If the sample size is too small, explicitly frame this as a case study.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section "Boltz-2 prediction workflow"
- **Evidence pointer** Methods section, paragraph on Boltz-2 prediction workflow
- **Issue** The manuscript states that "recycling steps and diffusion samples were set to 10 and 5, respectively" and that "the use_potentials option was enabled." It is not clear whether these settings are standard for Boltz-2 or whether they were chosen based on preliminary testing. Additionally, the rationale for selecting the representative structure as the one closest to the median predicted log10(IC50) is not explained.
- **Required correction** Provide a brief justification for the chosen parameters and the representative structure selection criterion. If these are default settings, state so explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section "Benchmark construction and experimental data curation"
- **Evidence pointer** Methods section, paragraph on benchmark construction
- **Issue** The manuscript states that experimental IC50 data were curated from BindingDB and PubChem BioAssay, but the specific accession numbers or database identifiers for the curated data are not provided in the main text. The supplementary tables are referenced, but they were not available for review.
- **Required correction** Provide the database accession numbers or a link to the curated dataset in the main text or a data availability statement.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Assessment of Boltz‑2 inhibitor potency predictions"
- **Evidence pointer** Results section, first paragraph; Fig. 1
- **Issue** The manuscript reports Pearson and Spearman correlation coefficients with confidence intervals from bootstrap analyses, but does not report p-values for these correlations. Given the small sample size, p-values would help readers assess the strength of the associations.
- **Required correction** Report p-values for the correlation coefficients, or state that p-values were not computed due to the small sample size.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4 legend
- **Issue** The figure legend states that "kinase domains are shown as cartoons and inhibitors as sticks" but does not specify which structures are shown (e.g., representative predictions or specific runs). The figure itself was not available for review, but the legend should clarify the selection of structures displayed.
- **Required correction** Clarify in the figure legend how the displayed structures were selected from the prediction ensemble.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, first sentence; Discussion, first paragraph
- **Issue** The term "relative kinase-inhibitor interaction patterns" is used throughout the manuscript but is not explicitly defined. It appears to encompass potency rankings, selectivity patterns, and mutation-dependent shifts, but the reader has to infer this.
- **Required correction** Define "relative interaction patterns" explicitly in the introduction or at first use in the abstract.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "AlphaFold 3 comparison workflow"
- **Evidence pointer** Methods section, paragraph on AlphaFold 3 comparison
- **Issue** The manuscript states that AlphaFold 3 was run locally in a Docker container, but does not specify the exact version of the AlphaFold 3 model or the source of the code. This may affect reproducibility.
- **Required correction** Provide the exact version number and source repository for the AlphaFold 3 code used.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Interpretation of FI-RMSD analysis
- **Affected element** Results section "Structural accuracy and ligand-pose variability in predicted complexes"
- **Evidence pointer** Results section, paragraph on FI-RMSD; Supplementary Fig. S4
- **Issue** The manuscript reports a "modest positive trend" between inhibitor flexibility (FI-RMSD) and prediction accuracy (r = 0.68, p = 0.065). The p-value is above the conventional significance threshold, and the authors appropriately note this is exploratory. However, the direction of the trend is counterintuitive and deserves more discussion.
- **Required correction** Provide a brief discussion of why more flexible inhibitors might be predicted more accurately, or acknowledge that this finding may be an artifact of the small sample size.

## Risk / unsupported claims
- The claim that "mutation-dependent shifts in inhibitor sensitivity showed substantial agreement with the experimental trends" is not fully supported because the number of mutant-inhibitor pairs is not stated and may be very small.
- The claim that "relative kinase-inhibitor interaction patterns were reproduced more consistently than absolute potency values" is not established as a general property of Boltz-2, given the small benchmark size and potential training-data overlap.
- The claim that "ligand-pose accuracy and predictive utility are not equivalent measures of Boltz-2 performance" is based on a small structural subset (12 complexes) and a single representative structure per system.
- The claim that "sequence-context sensitivity may depend on how flanking regions are positioned relative to the kinase domain" is based on two kinase families and is speculative.
- The comparison with AlphaFold 3 and Chai-1 is limited to ligand-pose RMSD for 12 complexes and does not include affinity prediction, so no conclusion about relative affinity prediction performance can be drawn.
- The FI-RMSD analysis is exploratory and underpowered; the reported trend (r = 0.68, p = 0.065) is not statistically significant.
- The potential training-data overlap for both structural and affinity data is acknowledged but not quantified, and no analysis is provided to separate memorization from generalization.