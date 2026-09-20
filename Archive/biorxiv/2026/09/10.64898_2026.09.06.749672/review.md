## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce SABLE, a versioned structural antibody benchmark that couples a fixed training collection with a leakage-controlled held-out test set, combining experimental and patent-derived AlphaFold3 models, with sequence-similarity filtering against the training set, per-entry nearest-neighbour records, and a Python/PyTorch API for reproducible evaluation.
- **Visible evidence base** Abstract text only; no quantitative results, validation metrics, or comparative analyses are reported
- **Missing materials affecting confidence** Full manuscript, methods section, figures, tables, benchmark statistics, validation experiments, API documentation, and any comparison with existing benchmarks

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable community resource for standardising antibody structure prediction evaluation. The concept of leakage-aware benchmarking with explicit nearest-neighbour reporting is timely and addresses a real methodological gap. However, the abstract provides no quantitative evidence of the benchmark's utility, no validation that the filtering procedure achieves its stated goal, and no demonstration that the resource functions as intended. The scientific case is therefore plausible but not established from the supplied material.
- **Who would be interested in the results, and why** Researchers developing deep-learning methods for antibody structure prediction, antibody-antigen docking, and antibody design would benefit from a standardised, leakage-controlled benchmark. The community lacks agreed-upon evaluation protocols, and a versioned resource with explicit redundancy labels would enable fairer cross-study comparisons. Machine-learning practitioners focused on generalisation assessment under distribution shift may also find the nearest-neighbour stratification approach of interest.
- **Major strengths** The proposed benchmark addresses a recognised problem in the field, namely train-test leakage arising from independent dataset construction. The design choice to record nearest training-set neighbours for each test entry is conceptually sound and enables users to quantify residual relatedness. The inclusion of patent-derived AlphaFold3 models selected after the model's temporal cutoff is a thoughtful approach to expanding test coverage while respecting temporal leakage constraints. The provision of a standardised API and metrics lowers the barrier to adoption.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Evidence sufficiency  
    **Claim pointer** The abstract implies that SABLE provides a leakage-controlled test set suitable for reproducible evaluation.  
    **Evidence pointer** Abstract, "leakage-controlled held-out test set" and "filtered against the training set using antibody and antigen sequence similarity filters"  
    **Concern** No data are presented demonstrating that the filtering procedure effectively eliminates or quantifiably reduces leakage. The abstract states that filters were applied but provides no threshold values, no distribution of nearest-neighbour similarities, and no analysis of how many test entries retain close training neighbours.  
    **Why it matters** The central value proposition of the benchmark rests on the adequacy of the leakage control. Without evidence that the filtering achieves its purpose, users cannot assess whether the benchmark meaningfully improves on existing resources.  
    **Resolution test** Provide a quantitative analysis showing the distribution of sequence identity between test entries and their nearest training neighbours, including the fraction of test entries above and below chosen thresholds, and demonstrate that performance rankings of representative models differ when evaluated on SABLE versus a naively constructed test set.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Validation of utility  
    **Claim pointer** The abstract implies that SABLE enables reproducible machine-learning development and evaluation.  
    **Evidence pointer** Abstract, "reproducible machine-learning development and evaluation" and "standardised benchmark metrics provide reproducible database access and evaluation code"  
    **Concern** No demonstration is provided that the benchmark is usable in practice. There are no example evaluations, no baseline results, no runtime or resource requirements, and no evidence that the API functions as described. The claim of reproducibility cannot be assessed without any empirical demonstration.  
    **Why it matters** A benchmark resource is only valuable if it can be readily adopted and if its outputs are meaningful. Without baseline results or a worked example, the community cannot judge whether the resource is fit for purpose.  
    **Resolution test** Include a baseline evaluation of at least two established antibody structure prediction methods on the SABLE test set, with runtime and resource usage reported, and demonstrate that the provided code reproduces the reported numbers.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** No  
    **Axis** Scope and representativeness  
    **Claim pointer** The abstract states that SABLE combines 16,511 experimental training entries with 327 manually reviewed test entries and 3,274 patent-derived AlphaFold3 models spanning 476 antigens.  
    **Evidence pointer** Abstract, "16,511 experimental training entries" and "3,274 high-confidence, patent-derived AlphaFold3 models"  
    **Concern** The abstract does not clarify the relationship between the 327 manually reviewed test entries and the 3,274 patent-derived models. It is unclear whether the patent-derived models are part of the test set, a separate validation set, or an auxiliary resource. The antigen count of 476 is not attributed to either subset.  
    **Why it matters** Users need to understand the exact composition of the test set to interpret benchmark results. Ambiguity in the resource structure undermines the stated goal of standardisation.  
    **Resolution test** Clearly specify the composition of the test set, including how many entries are experimental versus model-derived, how many unique antigens are represented in each subset, and whether the patent-derived models are intended for evaluation or for other purposes.  
- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Clarity  
    **Affected element** Benchmark name  
    **Evidence pointer** Abstract, "SABLE (Structural Antibody Benchmark for deep-Learning Evaluation)"  
    **Issue** The acronym expansion is provided, which is helpful, but the abstract does not state whether the resource is deposited in a public repository or how versioning is managed beyond the statement "versioned releases."  
    **Required correction** Add a sentence specifying the public repository location and the versioning scheme, such as semantic versioning or dated releases.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Reproducibility  
    **Affected element** Temporal cutoff statement  
    **Evidence pointer** Abstract, "selected after the AlphaFold3 temporal cutoff"  
    **Issue** The abstract does not state the specific date of the AlphaFold3 temporal cutoff, which is essential for users to understand the temporal scope of the test entries.  
    **Required correction** Provide the exact cutoff date in the abstract or refer to a methods section where it is specified.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Completeness  
    **Affected element** Benchmark metrics  
    **Evidence pointer** Abstract, "standardised benchmark metrics"  
    **Issue** The abstract does not list which metrics are included, such as RMSD, TM-score, or CDR-specific metrics.  
    **Required correction** Enumerate the specific metrics provided in the API, or state that a full list is available in the methods.  
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The absence of any quantitative validation of the leakage control and the lack of a demonstrated use case mean the central claims of the resource cannot be evaluated from the supplied material.

## Assessment against Nature-style criteria
- **Originality** The concept of a leakage-aware benchmark with explicit nearest-neighbour reporting is a useful contribution, though the general idea of benchmark resources for structural biology is not new. The specific focus on leakage quantification is a differentiating element.
- **Scientific importance** The problem addressed is real and of broad relevance to the antibody modelling community. A well-validated benchmark would have tangible impact on how methods are compared.
- **Interdisciplinary readership** The work sits at the intersection of structural biology, machine learning, and immunology. The abstract is written in a way that is accessible to these communities, though the lack of results limits its appeal.
- **Technical soundness** The design logic is reasonable, but technical soundness cannot be assessed without methods details and validation data. The filtering approach and the use of AlphaFold3 models require scrutiny that the abstract cannot support.
- **Readability for nonspecialists** The abstract is clearly written and avoids unnecessary jargon. The acronym and scope are explained adequately for a broad scientific audience.

## Recommendation posture
Currently not established from the provided evidence. The resource concept is promising and the design choices are defensible, but the absence of any quantitative validation or demonstration of utility means the scientific case is incomplete. I would be supportive if the authors provide evidence that the leakage control is effective and that the benchmark is usable in practice, as specified in R1-M1 and R1-M2.

## Risk / unsupported claims
- The claim that SABLE provides a "leakage-controlled" test set is unsupported without quantitative analysis of the filtering outcome.
- The claim that the resource enables "reproducible machine-learning development and evaluation" is unsupported without a demonstrated use case or baseline results.
- The claim that the patent-derived AlphaFold3 models are "high-confidence" is not verifiable from the abstract alone.
- The relationship between the 327 manually reviewed test entries and the 3,274 patent-derived models is ambiguous and cannot be resolved from the supplied material.