## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present RNASeek, a 1.6-billion-parameter generative foundation model based on a DeepSeek architecture, trained on a cross-phyla transcriptomic corpus. The model uses natural-language tokens for conditional prediction and sequence design. Claims include zero-shot capture of species-specific transcript features and intron–exon boundaries; fine-tuning for ribozyme self-cleavage activity and viral mRNA stability prediction with interpretable features; GRPO-based reinforcement learning for sequence generation; and experimental validation showing wild-type-level ribozyme activity and superior 3′ UTR stability compared to training data and benchmarked AI-generated sequences.
- **Visible evidence base** Abstract text only; no quantitative results, statistical measures, dataset descriptions, or experimental protocols provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model architecture details, training corpus composition, fine-tuning datasets, experimental methods, benchmark definitions, and statistical analyses

## Reviewer
- **Overall assessment** The abstract describes an ambitious and potentially impactful framework that unifies generative modeling, functional prediction, and reinforcement learning for RNA design. The conceptual integration of a cross-phyla foundation model with GRPO-based optimization is timely and aligns with current trends in AI-driven biomolecular engineering. However, the abstract provides no quantitative evidence, no comparative baselines with statistical rigor, and no details on experimental validation. The claims of zero-shot capability, interpretable features, and experimental superiority are stated without supporting numbers or methodological specifics. As presented, the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in RNA biology, synthetic biology, and computational biology would be interested in a unified generative framework for RNA design. Those working on foundation models for biomolecules, particularly in the context of regulatory RNA engineering, would find the pretrain–predict–optimize paradigm relevant. The potential for cross-species generalization and reinforcement learning-based design could attract a broad interdisciplinary audience spanning machine learning and molecular engineering.
- **Major strengths** The proposed framework addresses a clear gap in connecting RNA foundation models to functional sequence design. The use of natural-language tokens for conditional generation is an innovative approach that may enhance flexibility. The integration of interpretable feature analysis with reinforcement learning-based optimization is conceptually strong. The inclusion of experimental validation, if robust, would significantly strengthen the practical relevance of the work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is high, as the combination of a cross-phyla generative model with GRPO for RNA design appears novel. Scientific importance is potentially substantial given the central role of RNA in regulation and engineering. Interdisciplinary readership is plausible, spanning computational and experimental biology. Technical soundness cannot be assessed from the abstract alone, as no quantitative or methodological details are provided. Readability for nonspecialists is adequate, with clear conceptual framing, but the lack of concrete results limits the ability to evaluate the work's significance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising framework, but the absence of quantitative results, statistical validation, and methodological transparency prevents a supportive recommendation. A full manuscript with detailed evidence would be required to assess the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that RNASeek captures species-specific transcript features and intron–exon boundaries in a zero-shot setting.
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of zero-shot capability is stated without any quantitative metrics, such as accuracy, F1 scores, or comparison to existing methods. No details are given on the evaluation tasks, datasets, or baselines used to establish this capability.
- **Why it matters** Zero-shot performance is a strong claim that requires rigorous benchmarking to demonstrate generalization beyond training data. Without quantitative evidence, the claim is unverifiable and may overstate the model's capabilities.
- **Resolution test** Provide specific evaluation tasks, datasets, and metrics for zero-shot performance, including comparisons to state-of-the-art models and statistical significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that fine-tuned RNASeek predicts ribozyme self-cleavage activity and viral mRNA stability, revealing interpretable sequence features.
- **Evidence pointer** Abstract, location not provided
- **Concern** No quantitative performance measures are provided for the fine-tuned predictors, such as correlation coefficients, AUC values, or error rates. The interpretable features are described qualitatively, but no evidence is shown to support the claim that these features are statistically significant or biologically meaningful.
- **Why it matters** Predictive performance and interpretability are central to the utility of the model. Without quantitative validation, the predictors' reliability and the interpretability claims cannot be assessed.
- **Resolution test** Report performance metrics for both prediction tasks, including cross-validation results and comparisons to existing predictors. Provide statistical analysis of the identified features, such as enrichment scores or effect sizes, with appropriate controls.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that GRPO-guided generation produces faster-cleaving ribozymes and stability-enhancing 3′ UTRs while satisfying user-specified IUPAC constraints.
- **Evidence pointer** Abstract, location not provided
- **Concern** The outcomes of GRPO-guided generation are described without any quantitative data, such as fold improvements in cleavage rates or stability measures, success rates for constraint satisfaction, or comparisons to non-RL baselines. The experimental validation is mentioned but not detailed.
- **Why it matters** The core contribution is the RL-based design capability. Without quantitative outcomes and experimental validation details, the effectiveness of the approach cannot be evaluated.
- **Resolution test** Provide quantitative results for generated sequences, including activity measurements, stability metrics, constraint satisfaction rates, and statistical comparisons to training data and benchmarked AI-generated sequences. Include experimental protocols and replicate numbers.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The abstract claims that experimentally validated RNASeek-generated ribozymes achieve wild-type levels of activity and that generated 3′ UTRs exceed the performance of training data and benchmarked AI-generated sequences.
- **Evidence pointer** Abstract, location not provided
- **Concern** No experimental details are provided, including the number of tested sequences, assay conditions, controls, or statistical analysis. The claim of exceeding benchmarks lacks specification of the benchmarks used.
- **Why it matters** Experimental validation is critical for establishing real-world utility. Without detailed methods and results, the claims are not reproducible or verifiable.
- **Resolution test** Describe experimental procedures, including constructs, cell lines or in vitro conditions, replicates, and statistical tests. Specify the benchmarks and provide raw data or clear summaries with error bars and significance levels.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model architecture description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states the model is built on a "DeepSeek architecture" but does not clarify which specific variant or how it was adapted for RNA sequences.
- **Required correction** Specify the exact architecture version and any modifications made for RNA tokenization and generation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Training corpus description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions a "cross-phyla transcriptomic corpus" but provides no details on species coverage, data sources, or preprocessing.
- **Required correction** Describe the corpus composition, including number of species, sequence types, and any filtering criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "zero-shot"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "zero-shot" is used without defining the task formulation or the training data exclusion criteria.
- **Required correction** Clarify what zero-shot means in this context, including how the evaluation tasks were excluded from training.

## Risk / unsupported claims
- Zero-shot capture of species-specific transcript features and intron–exon boundaries is unsupported without quantitative evaluation.
- Interpretable sequence features associated with ribozyme activity and mRNA stability are unsupported without statistical evidence.
- GRPO-guided generation producing faster-cleaving ribozymes and stability-enhancing 3′ UTRs is unsupported without quantitative outcomes.
- Experimental validation claims of wild-type-level activity and superior 3′ UTR performance are unsupported without experimental details and data.
- The claim that generated 3′ UTRs exceed benchmarked AI-generated sequences is unverifiable without specification of benchmarks and statistical comparisons.