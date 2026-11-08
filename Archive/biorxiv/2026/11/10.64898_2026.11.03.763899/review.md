## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose FoldAbS, a supervised screening framework that repurposes frozen protein folding models as foundation encoders for antibody screening. The framework is claimed to evaluate specificity, affinity, and developability within a single architecture. An instantiation with the Protenix model (FoldAbS-Px) is reported to achieve performance gains of up to 13.1%, 9.2%, and 6.2% in specificity, affinity, and developability, respectively, over baseline approaches.
- **Visible evidence base** Abstract text only; no methodological details, benchmark descriptions, baseline specifications, or quantitative results beyond the three percentage improvements
- **Missing materials affecting confidence** Full manuscript, methods section, benchmark datasets, baseline definitions, statistical significance tests, ablation studies, and code repository contents

## Reviewer

- **Overall assessment** The abstract presents a conceptually appealing idea, namely the reuse of protein folding model representations as general-purpose encoders for antibody screening tasks. The framing is timely and the claimed gains are nontrivial. However, the abstract alone provides insufficient evidence to evaluate the validity, generalizability, or significance of the results. Key methodological choices, benchmark rigor, and statistical support are not described. The central claim of consistent improvements cannot be assessed from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational antibody design and therapeutic development would be the primary audience. The work also speaks to the broader community interested in repurposing large biological models as foundation encoders, particularly those working on protein representation learning and structure-aware prediction tasks. The potential to unify multiple screening criteria in one framework could appeal to industrial practitioners in antibody discovery pipelines.
- **Major strengths** The conceptual reframing of folding models as foundation encoders is a useful and potentially impactful idea. The unified treatment of specificity, affinity, and developability addresses a real gap in current screening pipelines. The use of an open-source model (Protenix) and the provision of code support reproducibility in principle.
- **Major Concerns** The abstract does not provide enough information to evaluate the core claims. The following concerns are raised based on the supplied material.
- **Minor Comments** Several elements of the abstract would benefit from clarification or additional detail.
- **Technical failings that need to be addressed before the case is established** The abstract lacks any description of the evaluation protocol, including datasets, baselines, metrics, and statistical testing. Without these, the reported percentage gains cannot be interpreted. The claim of consistency across all three criteria is not supported by any visible evidence.
- **Assessment against Nature-style criteria** Originality is moderate to high, as the idea of repurposing folding models as encoders is not widely explored. Scientific importance is potentially high for the antibody screening community, but the evidence base is too thin to establish significance. Interdisciplinary readership is plausible given the intersection of machine learning and structural biology. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is adequate, though some terms such as "foundation encoder" and "confidence scorers" may require more context in a full manuscript.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract alone does not support the reported conclusions. A full manuscript with detailed methods and results would be required for a substantive evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The framework is claimed to achieve "consistent improvements over baseline approaches" with gains of up to 13.1%, 9.2%, and 6.2% in specificity, affinity, and developability, respectively.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports specific performance gains but provides no information on the benchmark datasets, baseline methods, evaluation metrics, or experimental setup. Without these details, the reported percentages are uninterpretable and cannot be verified.
- **Why it matters** The central claim of the paper rests on these quantitative results. If the baselines are weak, the tasks are trivial, or the metrics are nonstandard, the reported gains may not reflect genuine improvements. The reader cannot assess the significance of the results without knowing the evaluation context.
- **Resolution test** The full manuscript must describe the datasets, baselines, metrics, and experimental protocol in sufficient detail to allow replication. Statistical significance tests or confidence intervals should be reported for the claimed gains.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The framework is described as "coupling the folding model with lightweight, task-specific heads" to evaluate all three therapeutic criteria within a single architecture.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not explain how the frozen folding model representations are extracted, how the task-specific heads are designed, or how the three objectives are combined during training. The term "supervised screening framework" is used, but the training procedure, loss functions, and label sources are not described.
- **Why it matters** The methodological contribution is central to the paper's novelty. Without a clear description of the architecture and training scheme, the reader cannot understand what is actually being proposed or how it differs from existing approaches that also use structure-aware features.
- **Resolution test** The full manuscript should provide a detailed description of the model architecture, feature extraction procedure, head designs, and training objectives. A diagram or pseudocode would be helpful.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability and scope
- **Claim pointer** The abstract states that FoldAbS "seamlessly evaluates all three therapeutic criteria within a single architecture" and that the results "reposition protein folding models from structure predictors and confidence scorers into reusable foundation encoders."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports results for a single instantiation (FoldAbS-Px) with the Protenix model. It is unclear whether the framework generalizes to other folding models, whether the reported gains are specific to Protenix, or whether the three tasks are equally well handled. The claim of "reusable foundation encoders" implies broader applicability that is not demonstrated.
- **Why it matters** The significance of the work depends on whether the framework is broadly applicable or narrowly tied to one model. If the results are model-specific, the claim of a general framework is overstated.
- **Resolution test** The full manuscript should include experiments with at least one additional folding model, or a clear discussion of why Protenix is representative. Task-wise results should be reported separately to show that all three criteria are handled well.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "foundation encoder" is used without definition. Readers unfamiliar with the machine learning terminology may not understand what is meant.
- **Required correction** Define the term explicitly, for example by stating that the folding model is used as a fixed feature extractor whose internal representations are fed into task-specific prediction heads.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Quantitative reporting
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The reported gains of 13.1%, 9.2%, and 6.2% are presented as "up to" values, which suggests they may be the best results across multiple settings. The abstract does not indicate whether these are average improvements, best-case improvements, or improvements on specific benchmarks.
- **Required correction** Specify the exact meaning of the reported percentages, including the benchmark and setting to which they apply. Report average and variance if available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility statement
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The code repository is mentioned, but no license, dependencies, or usage instructions are described in the abstract. This is not a flaw per se, but the reader cannot assess the usability of the code.
- **Required correction** In the full manuscript, provide a clear description of the code repository contents, including dependencies and a usage example.

## Risk / unsupported claims

- The claim of "consistent improvements over baseline approaches" is unsupported because no baseline definitions or evaluation protocols are provided.
- The claim that FoldAbS "seamlessly evaluates all three therapeutic criteria" is unsupported because no task-specific results are shown.
- The claim that folding models are "reusable foundation encoders" is not established because only one model instantiation is reported.
- The reported performance gains of 13.1%, 9.2%, and 6.2% are unverifiable without knowledge of the datasets, metrics, and statistical significance.
- The generalizability of the framework to other folding models is not assessable from the abstract.