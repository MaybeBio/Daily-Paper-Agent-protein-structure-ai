## Review setup

- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability, contributions, acknowledgements) as provided in the submission. Figures, tables, and supplementary materials are referenced but not provided.
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, and interpretation as presented in the text. No assessment of code functionality, reproducibility of the wet-lab experiments beyond what is described, or verification of the GitHub repository contents.
- **Shared manuscript claim summary** The authors introduce zPolaron, a heterogeneous graph neural network for protein inverse folding on protein–ligand complexes. The model integrates structural, interaction, and evolutionary information via six edge types and ESM-2 embeddings, using a confidence-guided iterative decoding strategy. Claims include: state-of-the-art sequence recovery on a low-similarity test set; superior zero-shot fitness prediction on ProteinGym and a DAOx multi-substrate benchmark; strong sensitivity in identifying loss-of-function mutations in binding pockets; and wet-lab validation showing a 17.84-fold activity improvement for CalA6-D205A-S160G and a 1.91-fold improvement for CalB-I121M.
- **Visible evidence base** Text descriptions of results in Sections 3.1–3.5, including numerical values for recovery rates, correlations, AUC/AP, and fold improvements. Methodological details in Sections 2.1–2.4. All figures, tables, and supplementary materials are referenced but not visible.
- **Missing materials affecting confidence** All figures (Figs. 1–5), supplementary figures (Figs. S1–S5), supplementary methods (Section 3 of Supplementary Materials), dataset composition details, and the GitHub repository contents. Without these, statistical significance, effect sizes, baseline comparisons, and experimental reproducibility cannot be independently verified.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant and timely problem: moving protein inverse folding beyond structural recovery toward functional fitness prediction. The proposed architecture, combining heterogeneous graph representations with ESM-2 embeddings and iterative decoding, is a reasonable and well-motivated design. The wet-lab validation is a notable strength that elevates the work beyond purely computational benchmarking. However, the manuscript as presented has several critical gaps. The absence of all figures and supplementary materials makes it impossible to verify the quantitative claims, assess statistical rigor, or evaluate the experimental setup. The framing in the abstract and introduction overstates the novelty of integrating evolutionary information, as prior inverse folding methods already incorporate such signals. The wet-lab section lacks critical controls and quantitative details. The claim that zPolaron "fills the missing puzzle of inverse folding" is not supported by the evidence presented, which is largely incremental over existing methods.
- **Who would be interested in the results, and why** Computational protein design researchers, particularly those working on inverse folding, enzyme engineering, and fitness prediction. The wet-lab validation of predicted variants would also interest protein engineers and synthetic biologists seeking practical tools for enzyme optimization. The methodological combination of graph neural networks with protein language models is relevant to the broader machine learning for structural biology community.
- **Major strengths** 1) The problem framing is important: sequence recovery alone is insufficient for functional protein design, and the authors provide a clear argument for integrating interaction and evolutionary constraints. 2) The heterogeneous graph design with six edge types is a thoughtful architectural choice that explicitly encodes physicochemical interactions. 3) The confidence-guided iterative decoding strategy is a sensible compromise between autoregressive and one-shot generation. 4) The wet-lab validation, if reproducible, provides compelling evidence of practical utility that is rare in this field. 5) The analysis of B-factor sensitivity (Section 3.1) addresses a practical concern about robustness to structural uncertainty.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figures and statistical rigor), R1-M2 (overstated novelty), R1-M3 (incomplete wet-lab reporting), R1-M4 (unclear dataset construction and leakage control).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The integration of interaction and evolutionary information is a reasonable extension of existing work, but the individual components (heterogeneous graphs, ESM-2 embeddings, iterative decoding) are all established techniques. The specific combination and the wet-lab validation provide some novelty, but the conceptual advance over LigandMPNN and CARBONARA is incremental.  
  *Scientific importance*: Moderate to high. Functional fitness prediction is a critical bottleneck in protein design, and demonstrating practical utility via wet-lab validation is valuable. However, the importance is diminished by the lack of clear evidence that the improvements are statistically significant and generalizable beyond the tested systems.  
  *Interdisciplinary readership*: Moderate. The work bridges computational biology, machine learning, and enzymology. The wet-lab results could attract a broader audience, but the presentation is heavily computational and may not be accessible to experimentalists without additional context.  
  *Technical soundness*: Cannot be fully assessed. The architectural choices are reasonable, but the absence of figures, supplementary methods, and statistical details prevents verification of the claims. The wet-lab section lacks critical controls.  
  *Readability for nonspecialists*: Moderate. The introduction and discussion are accessible, but the methods section assumes significant familiarity with graph neural networks and protein language models. The abstract is clear but overstates the novelty.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, and the wet-lab validation is promising, but the missing figures, supplementary materials, and statistical details preclude a supportive recommendation. Major revisions are required to address the concerns below.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and statistical rigor
- **Claim pointer** The manuscript claims zPolaron "outperforms all baselines" across sequence recovery, fitness prediction, and mutation effect identification, with specific numerical values (e.g., recovery rate exceeding 80% at 10 iterations, Spearman correlations of −0.609 and −0.530, AUC of 0.934 and 0.995).
- **Evidence pointer** Sections 3.1–3.4; all figures (Figs. 1–5) and supplementary figures (Figs. S1–S5) are referenced but not provided.
- **Concern** The central quantitative claims cannot be verified without the figures and supplementary materials. No confidence intervals, standard errors, or statistical tests are reported for any of the benchmark comparisons. The number of independent runs, the variance across runs, and the significance of differences between zPolaron and baselines are not stated. For the wet-lab experiments, no replicates, error bars, or statistical analysis are presented. The claim of "significantly higher" recovery rate (Section 3.1) is unsupported without statistical testing.
- **Why it matters** Nature-style publications require rigorous statistical evidence. Without measures of variance and significance, the reader cannot determine whether the observed improvements are meaningful or within noise. This is particularly important given the small number of test systems (10 PDB entries for stability, 8 enzyme targets for fitness, 2 enzymes for mutation analysis).
- **Resolution test** Provide all figures and supplementary materials. Add confidence intervals, standard errors, or statistical tests (e.g., paired tests across targets) for all benchmark comparisons. Report the number of independent runs and the variance. For wet-lab experiments, provide replicate numbers, error bars, and appropriate statistical analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and positioning
- **Claim pointer** The abstract states that "none of [structural, interaction, evolutionary constraints] are handled in a unified manner by existing pretrained models" and that zPolaron "fills the missing puzzle of inverse folding."
- **Evidence pointer** Section 1 (Introduction), Abstract.
- **Concern** The claim that existing models do not handle evolutionary information is inaccurate. ESM-2 embeddings, which the authors use, are derived from evolutionary sequence data. ProteinMPNN and ESM-IF have been shown to capture evolutionary constraints implicitly. LigandMPNN explicitly incorporates ligand context. The novelty of zPolaron appears to be the specific combination of heterogeneous graph edges with ESM-2 embeddings and iterative decoding, not the introduction of a fundamentally new information source. The "missing puzzle" framing overstates the gap.
- **Why it matters** Overstated novelty undermines the credibility of the contribution. The manuscript should accurately position zPolaron relative to existing methods, acknowledging that evolutionary information is already used in various forms, and clarify what specific architectural or methodological advance enables the improved performance.
- **Resolution test** Revise the introduction and abstract to accurately describe the state of the art. Provide a clear, specific statement of what zPolaron adds beyond existing methods, supported by ablation studies that isolate the contribution of each component.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation and reporting
- **Claim pointer** Section 3.5 claims wet-lab validation showing "CalA6-D205A-S160G achieves a 17.84-fold improvement in catalytic activity over native CalA" and "CalB-I121M shows a 1.91-fold increase."
- **Evidence pointer** Section 3.5, Fig. 5, Fig. S5.
- **Concern** The wet-lab section is severely under-reported. No details are given on: (i) the number of biological and technical replicates; (ii) the assay conditions beyond buffer, pH, and temperature; (iii) how the 17.84-fold and 1.91-fold values were calculated (e.g., initial rates, endpoint assays, product quantification); (iv) whether the improvements are statistically significant; (v) the expression and purification yields for each variant; (vi) whether the variants were characterized for stability, expression level, or solubility beyond activity. The statement that CalA8 was "predominantly expressed as inclusion bodies" suggests variability in expression that is not controlled for. Without these details, the wet-lab claims cannot be evaluated.
- **Why it matters** Wet-lab validation is a major strength of the manuscript, but only if it is rigorously reported. The current description is insufficient for reproduction or independent verification. The 17.84-fold improvement is a strong claim that requires robust evidence.
- **Resolution test** Provide full experimental details: replicate numbers, statistical analysis, assay protocols, calculation methods, and characterization of all variants (expression, solubility, stability). Include raw data or representative chromatograms/curves in the supplementary materials.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset construction and leakage control
- **Claim pointer** Section 2.2 describes the training set as "the protein–ligand complex dataset released by the LigandMPNN study" and the test set as "249 low-similarity PDB structures published between 2023 and 2025, collected independently," with sequence similarity "strictly below 40%."
- **Evidence pointer** Section 2.2, Section 3.1.
- **Concern** The dataset construction is described too briefly. Key questions remain: (i) How was the 40% sequence similarity threshold computed (global vs. local alignment, which tool)? (ii) Was the threshold applied per-chain or per-complex? (iii) Were the test PDB structures checked for ligand identity and binding site similarity to training structures, or only sequence similarity? (iv) How many structures were excluded by the filtering, and what was the final distribution of protein families and ligand types? (v) For the ProteinGym and DAOx benchmarks, were the structures used for scoring consistent with the training set (e.g., did any ProteinGym targets overlap with training structures)? (vi) The stability benchmark uses only 10 PDB entries, which is a very small sample. The manuscript does not state whether these 10 entries are representative or how they were selected.
- **Why it matters** Leakage between training and test sets is a common pitfall in protein design benchmarks. If the test set is not truly independent, the reported improvements may be inflated. The small sample sizes also raise concerns about generalizability.
- **Resolution test** Provide a detailed description of dataset construction, including the alignment tool and parameters, the filtering process, and the final composition of all datasets. Report the number of structures excluded at each step. For the stability benchmark, justify the selection of the 10 PDB entries and consider expanding the set. Verify and report that no test targets share significant sequence or structural similarity with training data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model description
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1, equations (1)–(3)
- **Issue** The model architecture is described at a high level, but the equations are not fully defined. The message-passing update, attention weight computation, and edge feature construction are not specified in sufficient detail. The dimension of edge features (d_e) is mentioned but not explained. The integration of ESM-2 embeddings with graph features is described only qualitatively.
- **Required correction** Provide a complete mathematical specification of the model, including the attention mechanism, message functions, edge feature construction, and the fusion of ESM-2 embeddings. Include a diagram or pseudocode in the supplementary materials.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Baseline selection and comparison
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1, Fig. 2a
- **Issue** The baseline methods (CARBONARA, ABACUS-T, LigandMPNN, ProteinMPNN) are appropriate, but the comparison is not described in detail. It is unclear whether all baselines were retrained on the same training set, whether hyperparameters were tuned per method, and whether the same decoding strategy (e.g., iterative vs. one-shot) was used for all methods.
- **Required correction** Describe the training and evaluation protocol for all baselines, including hyperparameter selection, decoding strategy, and any differences in input features. State whether the comparison is fair in terms of model capacity and training data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting in figures
- **Affected element** Section 3.1–3.4, Figs. 2–4
- **Evidence pointer** Sections 3.1–3.4
- **Issue** The text reports mean values (e.g., mean ΔPSSM = −0.62) but does not report the distribution or variance. For the correlation analyses, no confidence intervals are given. The ROC/PR curves in Figs. 4i–l are described qualitatively without reporting the number of positive and negative samples.
- **Required correction** Add error bars, confidence intervals, or box plots to all figures. Report the number of samples for each ROC/PR analysis. Consider adding a supplementary table with all numerical results and their variances.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 4
- **Evidence pointer** Section 4.1, 4.2
- **Issue** The discussion of limitations focuses on the sequence recovery metric but does not address limitations of the zPolaron model itself, such as its dependence on accurate ligand poses, sensitivity to the quality of input structures, or the computational cost of iterative decoding. The discussion of evolutionary constraints is insightful but does not acknowledge that ESM-2 embeddings may not capture all relevant evolutionary signals for ligand-binding sites.
- **Required correction** Add a subsection on model limitations, including input structure quality, ligand pose dependence, computational cost, and potential failure modes. Acknowledge the limitations of ESM-2 embeddings for capturing binding-site-specific evolutionary constraints.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility of wet-lab experiments
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The wet-lab methods are described in a single paragraph without sufficient detail. The source of the genes, the expression host strain, the induction conditions, the lysis method, and the HPLC analysis conditions are mentioned but not fully specified. The "standard curves" are referenced but not described.
- **Required correction** Provide a complete experimental protocol in the supplementary materials, including all buffer compositions, instrument settings, and data analysis procedures.

## Risk / unsupported claims

- The claim that zPolaron "fills the missing puzzle of inverse folding" is unsupported and overstated. The manuscript demonstrates incremental improvements on benchmarks, not a fundamental resolution of a known gap.
- The claim that "none of [structural, interaction, evolutionary constraints] are handled in a unified manner by existing pretrained models" is inaccurate, as ESM-2 and related models already incorporate evolutionary information.
- The specific numerical claims (17.84-fold, 1.91-fold, AUC 0.934/0.995, Spearman −0.609/−0.530) are unsupported without the corresponding figures, raw data, and statistical analysis.
- The claim that zPolaron is "insensitive to structural uncertainty" (Section 3.1, B-factor analysis) is based on a single analysis and lacks statistical verification.
- The generalizability of zPolaron to diverse protein families and ligand types is claimed but not demonstrated, given the limited number of test systems.
- The statement that "any two of the three information sources suffice to surpass all baselines" (Section 5) is presented without the ablation data (Fig. S2) being visible.