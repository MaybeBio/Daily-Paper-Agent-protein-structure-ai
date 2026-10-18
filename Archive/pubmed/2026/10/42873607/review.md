## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors present RNADaemon, a reinforcement learning framework that applies adaptive external force-field biases to steer all-atom molecular dynamics simulations toward native-like RNA tertiary structures, trained on 479 monomeric RNA structures and evaluated on 14 test cases. The agent reportedly approaches SimRNA and FARFAR2 in median RMSD, recovers global folds of most reference structures, but underperforms AlphaFold 3 and trRosettaRNA. The authors attribute a performance ceiling to the scalar Bellman error and claim this is the first continuous-action deep RL application with all-atom force fields for RNA tertiary structure prediction.
- **Visible evidence base** Abstract text only; no quantitative results, figures, tables, or methodological details provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, training and evaluation protocols, hyperparameters, baseline comparison details, statistical significance tests, and code availability

## Reviewer
- **Overall assessment** The abstract presents a technically ambitious framework that combines deep reinforcement learning with all-atom molecular dynamics for RNA structure prediction. The core idea is novel and potentially of interest to the structural biology and machine learning communities. However, the abstract provides insufficient quantitative detail to evaluate the strength of the reported results. The performance claims are stated qualitatively, and the central diagnostic claim regarding the scalar Bellman error is presented without supporting evidence. The framing is honest about current limitations relative to state-of-the-art methods, which is commendable, but the evidence base is too thin to establish the case for the framework's utility or the diagnostic insight.
- **Who would be interested in the results, and why** Computational structural biologists working on RNA folding and prediction, researchers developing machine learning approaches for biomolecular simulation, and method developers in the reinforcement learning community interested in scientific applications. The benchmark comparison and diagnostic analysis would be of interest to those seeking to understand the limitations of RL-guided simulation approaches.
- **Major strengths** The formulation of RNA tertiary structure prediction as a Markov Decision Process with continuous-action Soft Actor-Critic is conceptually novel and represents a meaningful departure from existing prediction paradigms. The honest reporting of performance relative to AlphaFold 3 and trRosettaRNA is scientifically appropriate. The identification of a specific information bottleneck, the scalar Bellman error, provides a concrete hypothesis for future investigation.
- **Major Concerns** The abstract lacks quantitative results, making it impossible to assess the magnitude of the reported performance. The claim of approaching SimRNA and FARFAR2 in median RMSD is vague without actual numbers or statistical comparisons. The diagnostic claim about the scalar Bellman error is presented as a finding but no evidence is shown. The evaluation on only 14 test cases raises questions about statistical power and generalizability.
- **Minor Comments** The abstract would benefit from reporting specific RMSD values and error bars. The claim of being the first application of this specific RL approach should be verified against a broader literature search. The relationship between the training set of 479 structures and the diversity of RNA folds represented is not addressed.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is high, as the combination of continuous-action RL with all-atom force fields for RNA prediction appears novel. Scientific importance is moderate, given the central challenge of RNA structure prediction, but the demonstrated performance does not yet establish a competitive advantage. Interdisciplinary readership is plausible, spanning structural biology, computational chemistry, and machine learning. Technical soundness cannot be assessed from the abstract alone, as no methodological details or quantitative results are provided. Readability for nonspecialists is adequate, though the abstract assumes familiarity with RL terminology and RNA structure metrics.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The agent "approaches SimRNA and FARFAR2 in median RMSD" and "recovers the global fold of most reference structures"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract reports no quantitative RMSD values, no comparison statistics, and no definition of what constitutes "approaching" or "recovering the global fold." Without specific numbers, confidence intervals, or statistical tests, the performance claims cannot be evaluated or reproduced.
- **Why it matters** The central contribution of the work is the performance of the RL-guided framework. If the performance relative to baselines is not quantified, the reader cannot determine whether the approach offers any practical utility or whether the reported limitations are meaningful.
- **Resolution test** Provide median and per-case RMSD values for RNADaemon, SimRNA, FARFAR2, AlphaFold 3, and trRosettaRNA, with appropriate statistical comparisons and a clear definition of "global fold recovery."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "We identify the scalar Bellman error as a fundamental information bottleneck that currently limits the performance of the agent"
- **Evidence pointer** Abstract; location not provided
- **Concern** This diagnostic claim is presented as a finding, but no evidence is shown in the abstract. It is unclear whether this is supported by ablation studies, error analysis, or theoretical reasoning. The term "fundamental" implies a structural limitation rather than a tunable parameter issue, which requires substantial evidence.
- **Why it matters** This claim frames the future direction of the work and has implications for the broader RL-for-science community. If unsupported, it could mislead subsequent research efforts.
- **Resolution test** Present ablation experiments or analyses that directly test the role of the scalar Bellman error, such as comparisons with alternative error formulations or demonstrations that the error correlates with prediction failures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "Trained on 479 monomeric RNA structures and evaluated on 14 test cases from CASP16, RNA-Puzzles, and the PDB"
- **Evidence pointer** Abstract; location not provided
- **Concern** The evaluation set of 14 test cases is small, and the abstract does not describe the diversity of these cases in terms of RNA length, structural complexity, or fold class. Without this information, the generalizability of the findings cannot be assessed.
- **Why it matters** RNA tertiary structure prediction performance is highly dependent on the difficulty of the target. A small, potentially biased test set could produce misleading conclusions about the method's capabilities.
- **Resolution test** Provide a detailed description of the 14 test cases, including length, fold class, and difficulty metrics, and discuss how they represent the broader space of RNA structures.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Performance comparison statement
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "approaches SimRNA and FARFAR2 in median RMSD" is ambiguous. It is unclear whether this means the method is statistically indistinguishable, slightly worse, or comparable within a specific margin.
- **Required correction** Specify the actual median RMSD values and the margin of difference, or state the statistical test used to support the comparison.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Novelty claim
- **Evidence pointer** Abstract; location not provided
- **Issue** The claim of being the first application of continuous-action deep RL with all-atom force fields for RNA tertiary structure prediction is strong and would benefit from a brief contextualization of prior RL-based structure prediction efforts.
- **Required correction** Add a sentence acknowledging prior RL applications in biomolecular structure prediction and clarify the specific novelty of this work.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Training and evaluation details
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not mention whether the training data and code will be made available, which is important for reproducibility and community adoption.
- **Required correction** State data and code availability in the abstract or indicate where this information can be found.

## Risk / unsupported claims
- The claim that RNADaemon "approaches SimRNA and FARFAR2 in median RMSD" is unsupported without quantitative values.
- The claim that the scalar Bellman error is a "fundamental information bottleneck" is unsupported without direct evidence.
- The claim of being the "first application" of this specific RL approach is unverifiable from the abstract alone.
- The generalizability of the method beyond the 14 test cases is not assessable from the provided information.