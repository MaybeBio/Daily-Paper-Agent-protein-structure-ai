## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce Protify, an open-source benchmarking platform for protein language models (pLMs), and report three main empirical findings: (1) DPLM3B is the top-performing self-supervised encoder on ProteinGym among 23 models tested; (2) across 32 supervised tasks, no single pLM dominates, with 14 different models achieving top scores and margins within run-to-run variability; (3) on enzyme optimal pH prediction, a general-purpose probe pipeline matches or exceeds a specialized model (EpHod) after 50 hyperparameter trials, but performance collapses under homology-controlled splits except for a transformer probe over full residue embeddings. The authors conclude that model rankings depend on evaluation design and that Protify makes design choices explicit, controlled, and replayable.
- **Visible evidence base** Abstract text only; no figures, tables, methods sections, or supplementary materials were provided
- **Missing materials affecting confidence** Full manuscript, methods descriptions, dataset curation details, model selection criteria, hyperparameter configurations, statistical analysis procedures, homology split definitions, and all quantitative results beyond the few values reported in the abstract

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable contribution to the pLM benchmarking landscape, addressing a real and recognized problem of fragmented evaluation practices. The platform concept is timely and the reported findings, particularly the task dependence of model rankings and the homology leakage effect, are of interest to the protein machine learning community. However, the abstract alone provides insufficient detail to assess the technical soundness of the benchmarking methodology, the statistical rigor of the comparisons, or the validity of the central claims. Several claims are stated without supporting quantitative context, and the homology leakage result, while striking, raises questions about experimental design that cannot be resolved from the provided material. The work is promising but the case is not fully established from the abstract alone.
- **Who would be interested in the results, and why** Researchers developing and applying protein language models, including computational biologists, machine learning practitioners working on protein function prediction, and bioinformaticians concerned with benchmark design and evaluation methodology. The findings on task dependence of model rankings and homology leakage have direct implications for model selection in practical applications and for the design of fair evaluation protocols. The platform itself would be of practical use to any group performing pLM benchmarking.
- **Major strengths** The work addresses a clearly identified and important problem in the field, namely the fragmentation of pLM evaluation practices. The scale of the benchmarking effort, with 35 models and 61 datasets supported and 23 models evaluated on ProteinGym, is substantial. The finding that no single model dominates across 32 tasks is a useful empirical contribution. The homology leakage result is potentially important and thought-provoking. The provision of an open-source platform with a low-code interface is a practical contribution that could have lasting value to the community.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and comparability
  - **Claim pointer** "the margins between the best and second-best models fell within run-to-run variability"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The claim that performance margins between top models fall within run-to-run variability is central to the conclusion that no single pLM dominates. However, the abstract provides no information on how run-to-run variability was measured, how many replicates were performed, what variance components were considered, or what statistical test was used to support this claim. Without this information, the claim cannot be evaluated.
  - **Why it matters** This claim underpins the paper's main conclusion about task dependence of model rankings. If the variability estimate is not robust, the conclusion that no model dominates could be an artifact of insufficient replication or high noise, rather than a genuine property of the models.
  - **Resolution test** Provide details on the number of replicates, the variance estimation method, and the statistical comparison procedure. Show that the variability estimate is based on a sufficient number of runs and that the conclusion holds under appropriate statistical testing.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental design and interpretation
  - **Claim pointer** "Under a homology-controlled split of the same data, every pooled-embedding probe collapsed to near-zero R2, and only a transformer probe over full residue embeddings recovered appreciable signal (R2 = 0.248)"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The homology leakage result is striking but the abstract does not describe the homology-controlled split construction, the sequence identity threshold used, the size of the training and test sets, or how the transformer probe differs architecturally from the pooled-embedding probes beyond the use of full residue embeddings. The comparison between the general-purpose probe and EpHod is also confounded by the fact that EpHod was selected from 11,550 training runs, while the probe used only 50 hyperparameter trials, making the comparison potentially unfair in either direction.
  - **Why it matters** The homology leakage finding is presented as a key insight, but without details on the split construction and probe architectures, it is unclear whether the result reflects a genuine property of the models or an artifact of the specific experimental setup. The comparison with EpHod, while interesting, may not be a fair head-to-head evaluation.
  - **Resolution test** Provide details on the homology split threshold, dataset sizes, and probe architectures. Clarify whether the comparison with EpHod is intended as a fair benchmark or as a demonstration of what is achievable with a general-purpose tool, and discuss the implications of the different training budgets.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scope and generalizability
  - **Claim pointer** "Model rankings therefore depend as much on evaluation design as on the models themselves"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** This is a broad conclusion drawn from a limited set of experiments. The abstract reports results on ProteinGym, 32 supervised tasks, and one specific enzyme property prediction task. While these are substantial, the claim that rankings depend "as much" on evaluation design as on models is a strong statement that would require evidence across a wider range of tasks, models, and evaluation settings to fully support.
  - **Why it matters** The conclusion is framed as a general principle about pLM evaluation. If it is overstated, it could mislead practitioners into over-weighting evaluation design relative to model choice. The claim needs to be scoped appropriately to the evidence.
  - **Resolution test** Either provide additional evidence across a broader range of evaluation settings or temper the conclusion to reflect the specific conditions under which the finding was obtained.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Platform description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract states that Protify supports 35 pretrained models and 61 curated datasets, and that 23 models were benchmarked on ProteinGym. It is unclear how the 23 models relate to the 35 supported models, and whether the 61 datasets include ProteinGym or are separate.
  - **Required correction** Clarify the relationship between the supported models and the benchmarked models, and specify whether ProteinGym is included in the 61 curated datasets.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Hyperparameter details
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "50 hyperparameter trials" for the general-purpose probe but does not specify the hyperparameter search space, the optimization method, or the selection criterion for the best trial.
  - **Required correction** Provide details on the hyperparameter search procedure in the full manuscript, and summarize the key settings in the abstract or a methods summary.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Performance metrics
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract reports R2 values for the enzyme optimal pH prediction task but does not report confidence intervals or variability for these values, which is particularly relevant given the emphasis on run-to-run variability elsewhere in the abstract.
  - **Required correction** Report confidence intervals or standard errors for the key performance metrics, and state the number of replicates used to compute them.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Accessibility
  - **Affected element** Data and code availability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract states that Protify is freely available at a GitHub URL, but does not mention whether the benchmarking results, including model predictions and evaluation scripts, are also released.
  - **Required correction** State clearly what data and code are released alongside the platform, including any benchmark results and evaluation pipelines.

## Risk / unsupported claims
- The claim that DPLM3B is the "top-performing self-supervised encoder" on ProteinGym is stated without specifying the evaluation metric, the number of ProteinGym tasks used, or the comparison set of encoders. This claim is not assessable from the abstract alone.
- The claim that "no single pLM dominated" across 32 tasks is supported only by the statement about margins falling within run-to-run variability, which is not backed by statistical details. This claim is currently not fully supported.
- The comparison between the general-purpose probe and EpHod is presented as a meaningful result, but the difference in training budgets (50 trials versus 11,550 runs) makes the comparison difficult to interpret. The claim that the probe "matched or exceeded" EpHod is not fully contextualized.
- The homology leakage finding, while potentially important, is described without sufficient experimental detail to assess its validity or generalizability. This claim is currently not assessable.
- The broad conclusion that "model rankings depend as much on evaluation design as on the models themselves" is an overgeneralization from the limited evidence presented in the abstract.

## Assessment against Nature-style criteria
- **Originality** The work addresses a recognized problem and offers a platform solution, which is a useful contribution, but the individual findings, such as task dependence of model rankings and homology leakage, are not entirely novel in concept. The originality lies primarily in the scale and standardization of the benchmarking effort rather than in a new conceptual insight.
- **Scientific importance** The problem of fragmented pLM evaluation is important for the field, and a standardized platform with large-scale benchmarking results would be of practical value. The homology leakage finding, if robust, could have significant implications for how pLM evaluations are designed. The importance is moderate to high, depending on the robustness of the findings.
- **Interdisciplinary readership** The work is likely to appeal primarily to computational biologists and machine learning researchers working on protein problems. The findings on evaluation design could also be of interest to a broader machine learning audience concerned with benchmark design, but the protein-specific focus may limit the breadth of readership.
- **Technical soundness** The technical soundness cannot be fully assessed from the abstract alone. The scale of the benchmarking effort is impressive, but the lack of statistical detail and experimental design information prevents a thorough evaluation. The homology split construction and the comparison with EpHod are particular areas where technical details are needed.
- **Readability for nonspecialists** The abstract is generally clear and accessible, with the key findings stated in plain language. However, some terms and concepts, such as "pooled-embedding probe" and "homology-controlled split," may be unfamiliar to nonspecialists and would benefit from brief explanations.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents a promising platform and interesting preliminary findings, but the lack of methodological detail and statistical rigor in the reported results prevents a full assessment of the claims. The work could become a strong contribution if the full manuscript provides the necessary experimental details and statistical support. I would be supportive if the technical concerns are resolved in the full manuscript.