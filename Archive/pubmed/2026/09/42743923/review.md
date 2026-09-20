## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose that sampling multiple simultaneous mutations from protein language models outperforms single-mutant sampling strategies for functional protein design, and they support this with in silico comparisons across three protein families and a de novo binder design validation
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or validation data are available
- **Missing materials affecting confidence** Full methods, all figures and tables, hyperparameter details, statistical analyses, and the de novo binder design results

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable contribution to the field of protein design, addressing a recognized limitation of current sampling strategies. The central claim, that multi-mutant sampling better captures epistatic effects, is biologically reasonable and aligns with known constraints on protein fitness landscapes. However, the abstract provides no quantitative evidence, no methodological specificity, and no statistical support. The validation on a de novo binder design task is mentioned but not described in any detail. As presented, the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational protein designers, machine learning researchers working on generative models for biological sequences, and experimentalists seeking improved design pipelines would be interested. The work addresses a practical bottleneck in applying protein language models to functional design, which has direct relevance for therapeutic and industrial applications.
- **Major strengths** The problem is well framed and important. The comparison of sampling strategies across multiple protein families is a sensible design. The inclusion of a de novo binder design task as a downstream validation is a strong choice for demonstrating practical utility.
- **Major Concerns** The abstract lacks all quantitative results, making the central claim unverifiable. The methodological novelty is unclear, as the abstract does not specify what the "several approaches tailored for protein design" are. The scope of validation, including the number of designs tested and the success criteria for the binder task, is not stated.
- **Minor Comments** The abstract would benefit from stating the specific protein families used. The phrase "major therapeutic target" is vague and should name the target. The relationship between the in silico framework and existing benchmarks is not clarified.
- **Technical failings that need to be addressed before the case is established** No quantitative evidence is provided for the central claim. The de novo binder validation is described without any results. Statistical significance of the reported improvements is not mentioned.
- **Assessment against Nature-style criteria** Originality: moderate, as the idea of multi-mutant sampling is not entirely new, but the systematic comparison may add value. Scientific importance: potentially high, given the relevance to functional protein design. Interdisciplinary readership: the topic bridges machine learning and molecular biology, which is of broad interest. Technical soundness: cannot be assessed from the abstract alone. Readability for nonspecialists: the abstract is clear and accessible, though some terms such as "epistatic interactions" may require background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising, but the absence of any quantitative results or methodological detail prevents a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "sampling multiple mutations simultaneously substantially outperforms single-mutant approaches by better capturing epistatic effects"
- **Evidence pointer** Abstract, location not provided
- **Concern** The central claim of the paper is stated without any supporting quantitative data. No performance metrics, effect sizes, or statistical comparisons are provided.
- **Why it matters** The claim is the core contribution of the work. Without numerical evidence, the reader cannot evaluate the magnitude of the improvement or its significance.
- **Resolution test** Provide performance metrics for multi-mutant versus single-mutant sampling across all three protein families, including effect sizes and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological specificity
- **Claim pointer** "we develop an in silico framework to systematically compare sampling methods and introduce several approaches tailored for protein design"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe what the proposed sampling approaches are, how they differ from existing methods, or what the in silico framework entails.
- **Why it matters** Without methodological detail, the novelty and reproducibility of the work cannot be assessed.
- **Resolution test** Describe the proposed sampling methods and the framework in sufficient detail, including algorithmic differences from prior work.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation completeness
- **Claim pointer** "validate our findings on a de novo binder design task against a major therapeutic target"
- **Evidence pointer** Abstract, location not provided
- **Concern** The de novo binder validation is mentioned but no results are reported. The number of designs, success rate, binding affinity measurements, or any other outcome metrics are absent.
- **Why it matters** This validation is presented as supporting evidence for the central claim. Without results, it cannot serve that role.
- **Resolution test** Report the outcomes of the binder design task, including success criteria and quantitative results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Protein family specification
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that three protein families were evaluated but does not name them.
- **Required correction** Specify the three protein families in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Specificity
- **Affected element** Therapeutic target description
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "a major therapeutic target" is vague and does not allow the reader to assess the relevance of the validation.
- **Required correction** Name the therapeutic target.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology accessibility
- **Affected element** Use of "epistatic interactions"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term is used without definition, which may hinder nonspecialist readers.
- **Required correction** Provide a brief explanation of epistasis in the context of protein function.

## Risk / unsupported claims
- The claim that multi-mutant sampling "substantially outperforms" single-mutant approaches is unsupported by any data in the abstract.
- The claim that the proposed approaches are "tailored for protein design" is not substantiated by methodological description.
- The de novo binder design validation is mentioned but entirely unevaluable from the supplied material.
- The generalizability of the findings across "eukaryotic, prokaryotic, and viral" protein families is asserted but not demonstrated with results.