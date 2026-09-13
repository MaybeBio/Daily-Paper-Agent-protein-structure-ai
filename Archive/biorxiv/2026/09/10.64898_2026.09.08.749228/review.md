## Review setup
- **Input scope** Full manuscript (bioRxiv preprint, 2026)
- **Assessment boundary** Scientific content, methodology, results, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors present a case study in which a general-purpose LLM agent (Claude Opus 4.8), operating under human supervision within a fixed compute budget, drives the semi-autonomous development of QuickFold, an 8.9 M-parameter RNA 3D structure prediction model. Over 297 iterations, the model evolved from a random baseline to match the performance of established open-source predictors (RhoFold+, NuFold) on lDDT and TM-score on a held-out test set, while being substantially faster at inference. The authors frame this work less as a new state-of-the-art predictor and more as a demonstration of feedback-driven, agent-led model development for hard biological problems.
- **Visible evidence base** Abstract; Sections 1-4 (Introduction, Agentic workflow, Results, Discussion); Supporting Information sections A.1-A.8 (Benchmark curation, Metrics definition, Agent roles, Other optimization runs, Detailed model evolution, Final model, Detailed model performance, User feedback); Tables 1, 3, 4, 5, 6, 7; Figures 1, 2, 3, 4 (described in text)
- **Missing materials affecting confidence** The manuscript does not provide the actual code, configuration files, or the full ledger of agent iterations. The full set of 297 iteration outcomes is summarized but not presented in a machine-readable or fully inspectable form. The specific prompts and rule files used in the Cursor harness are described but not provided verbatim. The raw training and validation loss curves are described (Figure 4) but the figure itself is not visible in the text. The test-set PDB identifiers are listed in Table 2, which is referenced but not provided in the text.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and timely case study in agent-driven scientific model development. The core idea—using a general-purpose LLM agent to iteratively propose, implement, train, and evaluate model changes for a genuinely hard biological problem—is novel and well-executed. The authors provide a detailed and honest account of the workflow, including its limitations, the division of labour between human and agent, and the practical caveats. The resulting model, QuickFold, is a non-trivial architectural achievement that matches established baselines at a fraction of the inference cost. However, several technical concerns regarding the statistical rigor of the performance comparison, the reproducibility of the agent-driven process, and the generalizability of the findings need to be addressed before the central claims can be fully accepted.
- **Who would be interested in the results, and why** This work will be of high interest to researchers in computational structural biology, particularly those working on RNA structure prediction, as it demonstrates a new paradigm for model development. It will also be of significant interest to the broader machine learning community, especially those working on AI for science, automated machine learning (AutoML), and agentic systems. The detailed analysis of the human-agent division of labour and the practical lessons learned (e.g., the importance of feedback timing, the "be bolder" heuristic) are valuable for anyone designing or deploying LLM agents for complex, iterative tasks.
- **Major strengths** 1. The core concept is novel and timely, directly addressing a key question in AI for science: can general-purpose agents drive progress on hard, real-world problems, not just toy benchmarks? 2. The experimental design is thoughtful and well-documented, including a carefully curated benchmark with a temporal train/val/test split, a fixed compute budget, and a detailed ledger of agent actions. 3. The authors provide an unusually honest and self-critical discussion of the method's limitations, including the modest absolute performance of the final model, the difficulty of pushing beyond the state of the art, and the practical challenges of managing agent-generated code. 4. The resulting model, QuickFold, is a genuine engineering achievement, demonstrating that an agent can assemble known architectural components into a highly efficient and competitive predictor.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Statistical rigor of performance comparison
    - **Claim pointer** "On the held-out test set (n = 80), QuickFold matches RhoFold+ and NuFold on lDDT and TM-score within seed noise..."
    - **Evidence pointer** Table 1, Section 3.2, Section A.7
    - **Concern** The claim that QuickFold "matches" the baselines is based on a comparison of mean performance metrics (lDDT, TM-score) on a test set of only 80 targets. The authors report seed noise for QuickFold (lDDT 0.600 ± 0.016) but do not provide a formal statistical test (e.g., a paired t-test, Wilcoxon signed-rank test, or bootstrapped confidence interval for the difference in means) to support the claim of equivalence. The baselines (RhoFold+, NuFold) are reported as deterministic or with near-zero spread, which is misleading. The comparison is further complicated by the fact that the baselines were given shallow MSAs (median depth 3), which the authors acknowledge is a regime where they are expected to underperform. The claim of "matching" is therefore not rigorously established.
    - **Why it matters** The central scientific claim of the paper is that the agent-driven process produced a model competitive with established methods. Without a proper statistical test, the reader cannot assess whether the observed differences are meaningful or simply due to chance, especially given the small test set and the acknowledged data limitations for the baselines. This undermines the core conclusion.
    - **Resolution test** The authors should perform and report a formal statistical comparison between QuickFold and each baseline on the test set. This should include: (1) reporting the mean and standard deviation of the per-target difference in lDDT and TM-score (QuickFold minus baseline); (2) reporting a p-value from a paired statistical test (e.g., Wilcoxon signed-rank test) for the null hypothesis that the median difference is zero; (3) reporting a bootstrapped 95% confidence interval for the mean difference. If the confidence interval includes zero and the p-value is > 0.05, the claim of "matching" is supported. If not, the claim should be qualified. The analysis should also be repeated for the subset of targets with deep MSAs (n=15) to assess the impact of the shallow-alignment regime on the baselines.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Reproducibility of the agent-driven process
    - **Claim pointer** "We designed a development loop where, under a fixed budget and with human supervision, the agent iteratively proposed, implemented, trained, and evaluated model changes."
    - **Evidence pointer** Section 2, Section 2.1, Section 2.2
    - **Concern** The agent-driven process is described in detail, but the manuscript does not provide the specific code, configuration files, prompts, or rule files that define the agent's behavior. The process is realized "entirely inside the Cursor harness as a set of rule files, prompts, and subagents driving a single LLM (Claude Opus 4.8)." While the general workflow is clear, the exact implementation is a black box. The reproducibility of the central result—that an LLM agent can drive this development—is therefore severely limited. The outcome is likely highly sensitive to the specific LLM version, the prompt engineering, the rule files, and the random seed of the LLM.
    - **Why it matters** A core claim of the paper is that the *process* of agent-driven development is a contribution. For this to be a useful contribution to the field, other researchers must be able to reproduce the process, or at least understand its key parameters well enough to adapt it. Without the code and prompts, the work is a single, non-reproducible demonstration.
    - **Resolution test** The authors should make the following materials publicly available in a repository (e.g., GitHub, Zenodo): (1) the complete set of rule files and prompts used to define the agent's behavior in the Cursor harness; (2) the code for the final QuickFold model; (3) the code for the training and evaluation pipeline; (4) the full, append-only ledger of all 297 iterations, including the agent's proposed changes, the critic's evaluation, and the outcome (accept/reject). If full release is not possible due to proprietary constraints (e.g., the use of a commercial LLM API), the authors should provide a detailed pseudocode or a simplified, open-source implementation of the core loop that demonstrates the principle.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability and significance of the finding
    - **Claim pointer** "We frame this less as a new predictor than as a case study in feedback-driven, agent-led model development."
    - **Evidence pointer** Abstract, Section 4
    - **Concern** The manuscript is framed as a case study, which is appropriate. However, the generalizability of the findings is unclear. The success of the agent-driven process is demonstrated on a single problem (RNA 3D structure prediction) with a single LLM (Claude Opus 4.8) and a single human supervisor. The authors acknowledge that the process was not fully autonomous and required significant human intervention (98 human turns, ~60 of which were "be bolder" prompts). The paper does not provide a clear analysis of which aspects of the problem or the setup were critical for success. Would the same approach work for a different biological problem (e.g., protein-ligand docking, molecular dynamics force field parameterization)? Would it work with a different, potentially weaker, LLM? The value of the case study is diminished without a discussion of the boundary conditions for its applicability.
    - **Why it matters** The paper's main contribution is the demonstration of a new mode of model development. For this to be a significant contribution, the community needs to understand *when* and *why* this mode is likely to be effective. The current manuscript does not provide this analysis.
    - **Resolution test** The authors should add a dedicated discussion section or expand the existing Discussion to explicitly address the generalizability of their findings. This should include: (1) a reasoned analysis of the problem characteristics that made the agent-driven approach successful (e.g., a well-defined metric, a cheap-to-evaluate proxy, a modular architecture space); (2) a discussion of the likely failure modes for other types of problems; (3) a speculation on the sensitivity of the results to the choice of LLM, based on the "other optimization runs" (Section A.4) where different LLMs were tested.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Section 3.1, Figure 2
    - **Evidence pointer** "Figure 2a", "Figure 2b", "Figure 2c"
    - **Issue** The text refers to "Figure 2a", "Figure 2b", and "Figure 2c" but the figure itself is not provided in the manuscript text. The description of the figure is detailed, but the reader cannot visually inspect the key data showing the model's evolution, the discontinuous progress, and the clash rate reduction.
    - **Required correction** Ensure that Figure 2 is included in the final manuscript. If the figure is too large, consider splitting it into separate panels or providing a high-resolution version in the supplementary information.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Section A.7, Table 7
    - **Evidence pointer** "Table 7"
    - **Issue** The text states "QuickFold's TM-score rises to ≈0.49 (Table 7)" for the subset of targets with deep MSAs (n=15). The authors correctly caution that this slice is small. However, the text does not provide the corresponding lDDT value for this subset, which would be useful for a complete picture.
    - **Required correction** Add the lDDT value for the deep-MSA subset to the text or to Table 7.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Section A.6, Table 3
    - **Evidence pointer** "Table 3"
    - **Issue** The text describes a "ten-term multi-stage loss" and references Table 3. The table is described as listing the ten terms, but the text does not explicitly state which terms are active throughout and which are ramped in. This information is present but could be clearer.
    - **Required correction** In the text describing Table 3, explicitly list the four validity/global-fold terms that are ramped in (soft-TM, backbone continuity, backbone bond-angle, van der Waals clash) and state that the other six are active throughout.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Section A.1
    - **Evidence pointer** "Table 2"
    - **Issue** The text references "Table 2" for the test-set PDB identifiers, but the table is not provided in the manuscript text.
    - **Required correction** Include Table 2 in the supplementary information.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor of performance comparison) and R1-M2 (reproducibility of the agent-driven process) are blocking concerns. R1-M3 (generalizability) is a major concern that should be addressed to strengthen the paper's contribution.

## Assessment against Nature-style criteria
- **Originality**: High. The concept of using a general-purpose LLM agent to drive the iterative development of a model for a hard biological problem is novel. While prior work has shown agentic loops for toy problems or neural architecture search, this is a compelling demonstration on a complex, real-world task with a costly evaluation function.
- **Scientific importance**: Medium to High. The work addresses a fundamental question in AI for science. If the findings are robust and reproducible, they could have a significant impact on how computational models are developed for biological problems, potentially widening access to model building for domain experts without deep ML expertise. The immediate practical importance of QuickFold itself is moderate, as it matches but does not exceed the state of the art.
- **Interdisciplinary readership**: High. The work bridges structural biology, machine learning, and AI agent research. The narrative is accessible to a broad scientific audience, and the honest discussion of limitations is commendable.
- **Technical soundness**: Medium. The experimental design is thoughtful, but the central claim of performance equivalence is not supported by rigorous statistical testing. The reproducibility of the core process is a major concern. The technical details of the model and workflow are otherwise well-described.
- **Readability for nonspecialists**: High. The manuscript is well-written and clearly structured. The authors do an excellent job of explaining the workflow, the challenges, and the limitations in a way that is accessible to a reader with a general scientific background.

## Recommendation posture
Supportive if technical concerns are resolved. The core idea is novel and the execution is thoughtful, but the two blocking concerns (statistical rigor of the performance comparison and reproducibility of the agent-driven process) must be addressed before the central claims can be accepted. The authors should provide a formal statistical test for the performance comparison and release the code, prompts, and ledger to enable reproducibility. Addressing the generalizability concern would further strengthen the paper.

## Risk / unsupported claims
- The claim that QuickFold "matches" RhoFold+ and NuFold on lDDT and TM-score is not supported by a formal statistical test and is therefore considered unsubstantiated from the provided evidence.
- The claim that the agent-driven process is reproducible is unsupported, as the core implementation (code, prompts, rule files) is not provided.
- The claim that the agent "owned the metrics, mechanisms, and implementation" while the human "owned visual structural judgement, and the scope of the work" is a qualitative observation that is well-supported by the narrative but is not quantitatively validated.