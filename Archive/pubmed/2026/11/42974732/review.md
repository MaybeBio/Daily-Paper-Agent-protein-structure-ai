## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose that ancestral sequence reconstruction (ASR)-informed data augmentation improves the training of generative and representation-learning models for protein engineering. Using ethylene-forming enzyme (EFE) as a model system, they report that variational autoencoders trained on ancestral and near-ancestral sequences generate variants with improved predicted and experimentally measured thermostability relative to models trained on modern sequences. They also report that ASR-enriched sequence sets are competitive with modern-sequence fine-tuning for ESM2-based stability classification in endolysin and lysozyme C tasks. All tested ancestral and ML-generated EFEs produced detectable ethylene, though ML-generated variants showed reduced activity relative to wild-type.
- **Visible evidence base** Abstract text only; no experimental details, numerical data, statistical analyses, or methodological descriptions provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental protocols, sequence datasets, model architectures and hyperparameters, thermostability assay details, activity measurements, statistical methods, and any code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting and timely hypothesis, namely that data-centric strategies such as ASR-informed augmentation can rival or outperform model-centric advances in protein engineering. The choice of EFE as a model system and the dual evaluation of generative and representation-learning tasks are sensible. However, the abstract provides insufficient quantitative detail to assess the robustness, magnitude, or generalizability of the reported effects. Several claims are stated without supporting numbers, effect sizes, or statistical significance, and the relationship between the stability gains and activity losses is not contextualized. The work may be of interest to the protein engineering and ML communities, but the current evidence base is too thin to establish the central case.
- **Who would be interested in the results, and why** Researchers in protein engineering, directed evolution, and machine learning applied to biological sequences would be interested. The work speaks to ongoing debates about data-centric versus model-centric improvements, and the use of ancestral sequences as a training strategy could inform practical choices for generative model development. Those working on thermostability prediction and design, particularly with ESM-based representations, may also find the fine-tuning comparisons relevant.
- **Major strengths** The hypothesis is clearly framed and addresses an underexplored area. The use of a real enzyme system with experimental validation of generated variants is a strength, as is the inclusion of both generative and representation-learning tasks. The observation that ancestral training captures stability-associated features more than catalytic optimization is an honest and potentially informative finding.
- **Major Concerns** The abstract lacks quantitative evidence for the central claims. No thermostability values, activity measurements, or statistical comparisons are provided. The claim that ancestral representations were "competitive" in classification tasks is vague without accuracy, AUC, or confidence intervals. The reduced activity of ML-generated variants is mentioned but not quantified, and the trade-off between stability and activity is not discussed in terms of practical utility. The generalizability of the approach beyond EFE and the two classification tasks is asserted but not supported.
- **Minor Comments** The abstract would benefit from stating the number of variants tested, the magnitude of thermostability improvement, and the statistical significance of the differences. The phrase "near-ancestral sequence datasets" is not defined. The relevance of the endolysin and lysozyme C tasks to the EFE findings is not explained. The abstract does not mention limitations or potential confounding factors, such as sequence diversity or dataset size.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to high, as ASR-informed augmentation is not widely explored for generative protein models. Scientific importance is potentially significant for the protein engineering community, but the evidence presented is insufficient to establish impact. Interdisciplinary readership is plausible, given the intersection of evolutionary biology and ML, but the abstract assumes familiarity with both fields. Technical soundness cannot be assessed from the abstract alone, as no methodological or statistical details are provided. Readability for nonspecialists is acceptable but would be improved by defining key terms and providing concrete numbers.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is promising and the experimental design appears reasonable, but the abstract does not provide sufficient quantitative support for the central claims. A revised version with detailed results, statistical analyses, and a clearer discussion of the stability-activity trade-off would be needed to assess the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that VAE models trained on ancestral and near-ancestral sequence datasets generate variants with improved predicted and experimentally measured thermostability relative to variants generated from modern-sequence training data.
- **Evidence pointer** Abstract, location not provided
- **Concern** No quantitative data are provided to support the thermostability improvement. The abstract does not report the magnitude of the improvement, the number of variants tested, the assay conditions, or any statistical measures such as p-values or confidence intervals.
- **Why it matters** Without quantitative evidence, the reader cannot evaluate whether the observed improvement is meaningful, reproducible, or within experimental noise. The central claim of the paper depends on this comparison.
- **Resolution test** Provide specific thermostability values (e.g., melting temperatures or half-inactivation times) for ancestral-trained versus modern-trained variants, with sample sizes and statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that all experimentally tested ancestral and ML-generated EFEs produced detectable ethylene, although ML-generated variants showed reduced activity relative to wild-type EFE.
- **Evidence pointer** Abstract, location not provided
- **Concern** The activity reduction is stated qualitatively without any quantitative measure. The abstract does not report the extent of the reduction, the number of variants with reduced activity, or whether this reduction is consistent across variants.
- **Why it matters** The trade-off between stability and activity is a critical consideration for protein engineering. Without quantification, the practical utility of the generated variants is unclear, and the claim that the approach "more strongly captured stability-associated features" is not substantiated.
- **Resolution test** Report activity values (e.g., ethylene production rates or yields) for wild-type, ancestral-trained, and modern-trained variants, with error bars and statistical comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that ASR-enriched sequence sets for fine-tuning ESM2 representations in endolysin and lysozyme C stability-classification tasks were competitive with modern-sequence fine-tuning in selected settings.
- **Evidence pointer** Abstract, location not provided
- **Concern** The term "competitive" is undefined. No performance metrics, such as accuracy, F1 score, or area under the ROC curve, are provided. The phrase "in selected settings" is vague and does not specify which settings or how many were tested.
- **Why it matters** The claim of competitiveness is central to the generalizability of the approach. Without metrics and a clear definition of the comparison, the reader cannot assess whether ASR-informed fine-tuning offers any advantage or is merely equivalent by chance.
- **Resolution test** Provide classification performance metrics for both ASR-enriched and modern-sequence fine-tuning across all tested settings, with confidence intervals and statistical tests for differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The abstract implies a generalizable strategy for stability-oriented protein sequence generation, but no methodological details are provided.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the VAE architecture, the ancestral sequence reconstruction method, the dataset sizes, the training procedures, or the criteria for selecting ancestral and near-ancestral sequences. Without these details, the work cannot be reproduced or evaluated for technical soundness.
- **Why it matters** Reproducibility is a core requirement for scientific claims. The lack of methodological information prevents independent verification and limits the usefulness of the findings to the community.
- **Resolution test** Provide a full methods section with model architectures, training hyperparameters, sequence selection criteria, and data availability statements.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "near-ancestral sequence datasets" is not defined. It is unclear whether these are sequences reconstructed at intermediate nodes of the phylogenetic tree or sequences with high similarity to ancestral reconstructions.
- **Required correction** Define "near-ancestral" explicitly in the methods or abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Discussion of trade-off
- **Evidence pointer** Abstract, location not provided
- **Issue** The reduced activity of ML-generated variants is mentioned but not discussed in the context of the intended application. It is unclear whether the stability gains outweigh the activity losses for practical use.
- **Required correction** Add a sentence contextualizing the stability-activity trade-off and its implications for real-world protein engineering.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Scope of claims
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract claims the strategy is "promising" for stability-oriented generation but only demonstrates it on one enzyme and two classification tasks. The generalizability is asserted without supporting evidence.
- **Required correction** Soften the generalizability claim or provide additional examples or a rationale for why the approach should transfer.

## Risk / unsupported claims
- The claim that ASR-informed data augmentation improves thermostability of generated variants is unsupported due to lack of quantitative data.
- The claim that ASR-enriched fine-tuning is "competitive" in classification tasks is unsupported due to lack of performance metrics.
- The claim that the approach "more strongly captured stability-associated features than catalytic optimization" is unsupported without quantitative activity and stability comparisons.
- The generalizability of the approach beyond the tested systems is asserted but not supported by evidence.
- The overall conclusion that ASR-informed augmentation is a "promising strategy" is not evaluable from the abstract alone.