## Review setup
- **Input scope** Full manuscript text (abstract, main text sections, figure captions referenced but not provided)
- **Assessment boundary** Scientific claims, methodology, experimental design, and result interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors propose chain-of-structures (COS), a four-round reasoning-to-generation framework for enzyme design that couples a language reasoning expert with an all-atom diffusion generator. They claim COS outperforms four baseline methods on five of six metrics, including 57.0% EC3 agreement and TM-score 0.729, and that both the written reasoning records and the continuous latent channel contribute to performance.
- **Visible evidence base** Abstract, Sections 1-6, Tables 3 referenced (not shown), Figures 1-2 referenced (not shown), training data statistics, ablation results
- **Missing materials affecting confidence** Tables 1-3, Figures 1-2, detailed hyperparameters, baseline implementation details, statistical significance tests, experimental validation data, code availability

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting framework that explicitly connects language-based reasoning to structural generation for enzyme design. The four-round hierarchical approach is well-motivated and the architectural choices are sensible. However, the evidence provided is insufficient to establish the claimed advantages. Key results are referenced but not shown, baseline comparisons lack statistical rigor, and the reported margins are small. The work is at an early exploratory stage and would benefit from stronger validation, including experimental characterization and more robust benchmarking.

- **Who would be interested in the results, and why** Researchers in computational protein design, AI for science, and enzyme engineering would find this work relevant. The framework's explicit reasoning-to-generation interface addresses a growing interest in interpretable AI-driven design. The methodological insights on coupling language models with diffusion generators could inform future work in multimodal scientific AI.

- **Major Strengths**  
  1. The four-round hierarchical decomposition from catalytic core to complete protein is chemically well-reasoned and provides interpretable intermediate states.
  2. The dual-channel interface (discrete residues plus continuous latents) is a thoughtful design that enables structural supervision of the reasoning model.
  3. The data construction pipeline, including structural alignment-based label transfer with calibrated TM-score thresholds, is careful and addresses a known challenge in enzyme annotation.
  4. The ablation study design is informative, separating the contributions of written reasoning records from the continuous channel.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "chain-of-structures leads the compared baselines on five of six metrics, achieving 57.0% EC3 agreement and a TM-score of 0.729"
  - **Evidence pointer** Table 3 (referenced, not provided)
  - **Concern** The central performance claim rests entirely on Table 3, which is not included in the provided material. Without the actual numbers, standard deviations, and baseline descriptions, the claimed superiority cannot be evaluated. The reported 1.7-point EC3 margin over CodeFP is small and may not be statistically significant.
  - **Why it matters** The primary contribution of this work is the claimed performance improvement. If the margin is within noise, the framework's value reduces to a conceptual demonstration rather than a practical advance.
  - **Resolution test** Provide Table 3 with full statistics, including per-method standard deviations, number of independent runs, and significance tests (e.g., paired bootstrap or Wilcoxon). Report effect sizes and confidence intervals.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental validation
  - **Claim pointer** "the resulting structure becomes context for the next decision" and the overall design quality implied by TM-score 0.729
  - **Evidence pointer** Section 5, location not provided
  - **Concern** No experimental validation is reported. TM-score and pLDDT are computational proxies that do not guarantee functional enzymes. For a design method targeting catalytic function, the absence of any wet-lab characterization (expression, activity, selectivity) severely limits the claims' practical relevance.
  - **Why it matters** Computational metrics can be misleading for enzyme design. Without experimental confirmation, the framework's utility for real design problems remains unproven.
  - **Resolution test** Include at least a small set of designed enzymes characterized experimentally, or clearly state that experimental validation is ongoing and frame the work as purely computational.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Baseline fairness
  - **Claim pointer** "chain-of-structures leads the compared baselines on five of six metrics"
  - **Evidence pointer** Section 5, location not provided
  - **Concern** The baseline methods (DPLM, CFP-Gen, MMCP-Gen, CodeFP) are described only by name. Their training data, conditioning protocols, and hyperparameters are not specified. If baselines were not given equivalent computational budgets or access to the same reaction-conditioning information, the comparison may be unfair.
  - **Why it matters** Unfair baselines can inflate apparent improvements and mislead the field about the true state of the art.
  - **Resolution test** Provide full implementation details for all baselines, including training data, conditioning inputs, and compute. Consider adding a baseline that uses the same diffusion generator without the reasoning interface to isolate the contribution of the COS framework.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** "COS leads the compared baselines on five of six metrics" and the framework's applicability to enzyme design broadly
  - **Evidence pointer** Section 4.5, location not provided
  - **Concern** The test set spans 98 EC classes, but the total test size is only 1,149 records. The diversity of reactions and the difficulty distribution across classes are not analyzed. Performance on a small, potentially biased test set may not generalize to the broader enzyme design space.
  - **Why it matters** Enzyme design challenges vary enormously across reaction types. A method that works well on common classes may fail on rare or mechanistically complex reactions.
  - **Resolution test** Report performance stratified by EC class, reaction complexity, and sequence identity to training data. Include an analysis of failure modes and their correlation with reaction features.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** "we complete post-training in one week on eight NVIDIA H100 GPUs"
  - **Evidence pointer** Section 3.3, location not provided
  - **Concern** The training pipeline is described at a high level, but critical details are missing: exact data splits, augmentation strategies, learning rates, LoRA ranks, diffusion sampling parameters, and the specific version of Qwen and RFdiffusion3 used. The code and trained models are not mentioned as available.
  - **Why it matters** Reproducibility is fundamental to scientific progress. Without these details, other groups cannot build on this work or verify the claims.
  - **Resolution test** Provide a detailed hyperparameter table, release code and model checkpoints, and specify all software versions and random seeds.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.2, equation 1
  - **Evidence pointer** Section 2.2, location not provided
  - **Issue** The equation for the dual-channel interface is referenced but not shown. The description of how the continuous latent is extracted from the language model's hidden state is vague.
  - **Required correction** Display the equation explicitly and clarify the exact mechanism for extracting and projecting the continuous latent.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data quality
  - **Affected element** Section 4.1, data construction
  - **Evidence pointer** Section 4.1, location not provided
  - **Concern** The data pipeline relies on predicted structures and predicted ligand poses. The accuracy of these predictions is not assessed against experimental structures for the final dataset.
  - **Required correction** Report the distribution of prediction confidence scores and, if possible, validate a subset against experimental structures.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Metric interpretation
  - **Affected element** Section 5, MMD discussion
  - **Evidence pointer** Section 5, location not provided
  - **Concern** The MMD metric is described as measuring distance to the natural k-mer distribution, but the choice of k and the reference distribution are not specified.
  - **Required correction** Specify the k-mer length, the reference dataset, and the exact MMD formulation used.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Temporal claim
  - **Affected element** Section 4.4, temporal split discussion
  - **Evidence pointer** Section 4.4, location not provided
  - **Concern** The statement that entries are "mostly from around 2008" is surprising for a 2026 manuscript and may reflect a data source bias that limits relevance to modern enzyme design.
  - **Required correction** Clarify the temporal distribution of the data and discuss implications for the method's applicability to contemporary design targets.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Related work
  - **Affected element** Section 1, references [4-11]
  - **Evidence pointer** Section 1, location not provided
  - **Concern** The related work section is brief and does not clearly differentiate COS from Proteo-R1 and ProteinReasoner beyond the four-round structure.
  - **Required correction** Expand the comparison with these methods, highlighting specific architectural and methodological differences.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (missing results table), R1-M2 (no experimental validation), R1-M3 (baseline fairness), R1-M5 (reproducibility details)

- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The four-round hierarchical decomposition and dual-channel interface are novel combinations of existing ideas, but the individual components (language reasoning, diffusion generation, residue-level conditioning) are established.
  - **Scientific importance** Moderate. Enzyme design is an important problem, and interpretable reasoning-to-generation frameworks could have impact. However, the demonstrated improvements are marginal and lack experimental confirmation.
  - **Interdisciplinary readership** Moderate. The work bridges AI and biochemistry, but the presentation assumes familiarity with both protein design and language model training, potentially limiting accessibility.
  - **Technical soundness** Weak. The central results are not shown, statistical rigor is absent, and reproducibility details are insufficient.
  - **Readability for nonspecialists** Weak. The manuscript uses field-specific jargon without adequate introduction, and the abstract assumes knowledge of Scinetics' prior work.

- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is interesting, but the missing results table, lack of experimental validation, and insufficient methodological detail prevent assessment of the core claims. The authors should provide complete results with statistical analysis, add experimental validation or clearly scope the work as computational, and release code and detailed hyperparameters.

## Risk / unsupported claims
- The claim of leading on five of six metrics is unsupported because Table 3 is not provided.
- The statement that "the functional gains do not come at the cost of designability" is not fully supported without experimental folding validation.
- The claim that the continuous channel carries structural training signals back to the reasoner is plausible but not directly demonstrated with gradient analysis or ablation of the latent pathway alone.
- The assertion that "writing the design down is worth approximately as much as the strongest label-conditioned generator" is an interpretation based on a small margin that may not be statistically significant.
- The generalizability claim to enzyme design broadly is not supported given the limited test set diversity and lack of stratified analysis.
- The temporal claim about data from 2008 is presented without discussion of its implications for the method's relevance.