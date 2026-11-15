## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, claim support, and presentation quality of the submitted work
- **Shared manuscript claim summary** The authors propose HEIWA, a hybrid explicit-implicit water attention module, to inject solvent-mediated force field information into ESM3 residue embeddings. They use thermophilic protein classification as a proxy task to demonstrate that ESM3 exhibits biophysical artifacts (e.g., misidentifying H-bonds as destabilizing) due to the absence of explicit solvent modeling, and that HEIWA corrects these artifacts while preserving classification performance and improving kinetic stability of generated proteins in molecular dynamics simulations.
- **Visible evidence base** Main text figures (referenced as Figure 1, Figure 2, Figure 3, Figure 4, Figure 5, Figure 6), supplementary figures (S1–S26), supplementary tables (S1, S2), and methods section
- **Missing materials affecting confidence** Actual figure images, supplementary data files, model architecture diagrams, hyperparameter search details, and full statistical outputs were not provided. The manuscript text alone limits quantitative verification of reported results.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question in protein language modeling: whether structure-based models like ESM3 possess adequate force field awareness, and whether explicit solvent encoding can improve physical consistency. The authors identify a plausible limitation (vacuum bias) and propose a novel attention mechanism to address it. The proxy task of thermophilic classification is well chosen, and the biophysics-guided model selection is a thoughtful approach. However, several methodological details are unclear, the statistical rigor of some comparisons is questionable, and the claimed generalizability to unfamiliar SUPFAMs requires stronger evidence. The work is potentially interesting to the protein modeling and computational biology communities, but the current evidence does not fully establish the central claims.

- **Who would be interested in the results, and why** Researchers in protein language models, structure prediction, and de novo protein design would be interested in the demonstration that solvent encoding can improve physical consistency of structure-based models. Computational biophysicists and molecular dynamics practitioners may find the proxy task and biophysics-guided selection strategy useful. The work also speaks to the broader question of what structure-based language models actually learn about protein physics, which is of interest to the machine learning for science community.

- **Major strengths** The manuscript identifies a specific, testable limitation of ESM3 (vacuum bias) and proposes a mechanistically motivated solution. The use of thermophilic classification as a proxy for force field awareness is creative and well justified. The biophysics-guided model selection using RMSF benchmarks is a rigorous approach to ensure physical meaningfulness of latent outputs. The ablation studies and control experiments (Gaussian random vectors, reversed gates) are appropriate. The molecular dynamics validation of generated proteins is a strong addition that connects the model improvement to practical outcomes.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and evidence quality
- **Claim pointer** The authors claim that HEIWA "restores biophysical soundness" and that "4 out of 120 hyperparameter combinations" passed the biophysical correlation test, with improved correlations with RMSF and SASA.
- **Evidence pointer** Results sections "HEIWA Restores Biophysical Soundness after Hyperparameter Optimization" and "Ablation of SASA and Membrane Gates", Figures 3 and 4, location not provided
- **Concern** The manuscript reports correlations and pass/fail criteria but does not provide effect sizes, confidence intervals, or statistical significance tests for the key comparisons. For example, the claim that HEIWA improves logit-RMSF correlation is supported only by qualitative statements ("better correlate") without reporting correlation coefficients or p-values. The selection of "4 out of 120" hyperparameters passing the test is presented without a null model or multiple testing correction. The manuscript should report quantitative correlation values, their uncertainties, and appropriate statistical tests for all key comparisons.
- **Why it matters** Without quantitative statistical evidence, the reader cannot assess whether the observed improvements are meaningful or could arise by chance, especially given the large number of hyperparameter combinations tested.
- **Resolution test** Provide correlation coefficients (Spearman rho) with confidence intervals for logit-RMSF and logit-SASA comparisons between baseline and HEIWA models. Report p-values for the binomial tests and justify the absence of multiple testing correction. Show the distribution of correlation values across all 120 hyperparameter combinations to demonstrate that the selected models are not outliers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity and reproducibility
- **Claim pointer** The HEIWA module is described as using "all-query-to-all-key water–residue attention" with "distinct water key vectors" and a "rotational attention score" to capture angular dependence of interatomic forces.
- **Evidence pointer** Methods section "HEIWA" and subsections "Rotational Attention" and "All-to-All Attention and Swish-Activated LoRA (SoRA) for Output Compression", location not provided
- **Concern** The mathematical formulation of HEIWA is incomplete. The manuscript states that water keys k_wh, k_wl, and k_wo represent different interaction types, but does not specify how these are initialized, whether they are learned, or how the number of heads is determined beyond a single DSSP-based experiment. The rotational attention formula (a_r = 1 - sigma(q_pa · k_wa / 3 + b_p + b_w)) is presented without derivation or justification for the scaling factor of 3. The SoRA mechanism is described with equations but the dimensions and rank selection criteria are not specified. The integration of HEIWA into the ESM3 architecture (where exactly the attention is applied, how the output is combined with the frozen embedding) is not described in sufficient detail for reproduction.
- **Why it matters** Reproducibility is a core requirement for computational work. Without complete architectural and training details, other researchers cannot implement or build upon HEIWA.
- **Resolution test** Provide a complete mathematical specification of HEIWA, including tensor dimensions, initialization schemes, and the exact insertion point in the ESM3 architecture. Justify the scaling factor in the rotational attention formula. Specify the rank selection procedure for SoRA and provide the DSSP-based head count determination details.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support and generalizability
- **Claim pointer** The authors claim that "HEIWA learns biophysical patterns that can be extended to SUPFAM absent from the training data set" and that molecular dynamics simulations show "improved kinetic stability under thermophilic conditions."
- **Evidence pointer** Results sections "Learning of Individual-Residue Stability Can Be Extended to Unfamiliar SUPFAMs" and "Molecular Simulations Show Greater Kinetic Stability of de novo Structures Generated Using HEIWA", Figures 5 and 6, Tables 2 and 3, location not provided
- **Concern** The generalizability claim is based on a single experiment with 19 proteins for de novo generation and 80 SUPFAMs in the grouped test set. The manuscript does not report how many of the 19 generated proteins showed improved stability, the magnitude of improvement, or the variability across proteins. The comparison between full HEIWA and reversed SASA gate is reported as not statistically significant for the binomial test, which undermines the specificity of the HEIWA effect. The metadynamics results are described as "complementary qualitative context" but are then used to support claims about kinetic stability. The manuscript should clarify whether the primary evidence for improved stability comes from the temperature ramping or metadynamics simulations and should report per-protein results.
- **Why it matters** The central practical claim of the paper is that HEIWA improves the quality of generated proteins. If the evidence is weak or inconsistent, the practical value of the method is not established.
- **Resolution test** Report per-protein RMSF comparisons between baseline and HEIWA-generated structures, including the number of proteins improved, unchanged, and worsened. Provide the distribution of improvements and clarify which simulation protocol (temperature ramping or metadynamics) is the primary evidence. Discuss the lack of statistical significance in the reversed SASA gate comparison and its implications for the specificity of HEIWA.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline comparison and alternative explanations
- **Claim pointer** The authors state that "models with 2 and 3 solvent heads are insufficient to resolve the H-bond destabilization and glycine stabilization problems" and that 4 or 5 heads are required.
- **Evidence pointer** Results section "HEIWA Restores Biophysical Soundness after Hyperparameter Optimization", Figure 3, location not provided
- **Concern** The manuscript does not compare HEIWA against alternative approaches to incorporating solvent information, such as adding SASA as an input feature, using a different attention mechanism, or simply increasing model capacity. The claim that the improvement is due to the specific HEIWA design rather than the additional parameters or the attention mechanism in general is not tested. The observation that 4-5 heads are needed could indicate that the model simply needs more capacity, not that the water attention mechanism is specifically beneficial.
- **Why it matters** Without appropriate controls, the specific contribution of the HEIWA mechanism over simpler alternatives is unclear, which limits the scientific insight and practical guidance for future model design.
- **Resolution test** Include ablation experiments with (a) a baseline model with increased capacity matched to HEIWA parameter count, (b) a model with SASA as an additional input feature, and (c) a standard multi-head attention mechanism without the water-specific design. Compare biophysical consistency and classification performance across these conditions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation and clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction, location not provided
- **Issue** The abstract states that "per-residue logit mis-correlated with H-bonds as a destabilizing attribute" which is grammatically awkward and unclear. The Introduction contains a sentence fragment ("as in natural language models") and several run-on sentences that impede readability.
- **Required correction** Revise the abstract for clarity and grammatical correctness. Edit the Introduction for sentence structure and flow.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section
- **Evidence pointer** Methods section "Hardware", location not provided
- **Issue** The hardware description is unusually specific about consumer-grade components (e.g., "Intel Ultra 9 285 K CPU") but does not report GPU memory, total training time, or computational cost of the hyperparameter search. This information is important for assessing the practical feasibility of the approach.
- **Required correction** Provide GPU specifications, total training time, and an estimate of the computational cost of the full hyperparameter search.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section on molecular dynamics
- **Evidence pointer** Results section "Molecular Simulations Show Greater Kinetic Stability", Table 2, location not provided
- **Issue** The manuscript reports p-values for binomial tests but does not report the test statistic or the number of ties excluded. The statement "after ties were excluded" is vague.
- **Required correction** Report the exact binomial test statistic, the number of ties, and the total number of comparisons for each test.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion, location not provided
- **Issue** The manuscript claims this is "the first study to incorporate explicit solvent encoding into a residue-resolution protein language model," but does not discuss recent work on solvent-aware protein representations or implicit solvent models in machine learning, which may be relevant prior art.
- **Required correction** Add a brief discussion of related work on solvent modeling in protein machine learning to contextualize the novelty claim.

## Risk / unsupported claims
- The claim that HEIWA is "the first study to incorporate explicit solvent encoding into a residue-resolution protein language model" is not verifiable from the provided text and may be overstated without a comprehensive literature review.
- The claim that "HEIWA learns biophysical patterns that can be extended to SUPFAM absent from the training data set" is not fully supported by the reported evidence, as the generalization experiment uses a single data split and the results are not quantitatively detailed.
- The claim of "improved kinetic stability under thermophilic conditions" is based on simulations with a small number of proteins (19) and inconsistent agreement between temperature ramping and metadynamics results.
- The assertion that the improvement is specifically due to solvent encoding rather than increased model capacity is not tested with appropriate control experiments.
- The manuscript states that "HEIWA also largely preserves the embedding structure of ESM3" but does not provide quantitative evidence for this claim beyond a qualitative UMAP visualization reference.
- The claim that "prediction error strongly depends on SASA" is based on a single figure without reported effect sizes or statistical tests.
- The statement that "the model did not meaningfully learn SUPFAM-specific summation because of the pooling operation" is a conclusion drawn from indirect evidence and requires more direct testing.