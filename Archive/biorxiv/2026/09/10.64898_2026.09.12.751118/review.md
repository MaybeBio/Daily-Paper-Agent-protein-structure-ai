## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract, with no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors introduce latent generative search for binder design, a framework that applies reward-guided search at inference time to a generative model called Proteina-Complexa, which codesigns sequence and structure in a continuous latent space. They report that this approach outperformed other tested methods in a multiplexed phage display screen of over one million designs, produced high-affinity binders against therapeutic receptors, a viral attachment protein, and intracellular signalling targets, and generated the first de novo proteins that bind a free carbohydrate, including one that discriminates between blood-group antigens.
- **Visible evidence base** Abstract text only. No methods, figures, tables, or supplementary data were provided for review.
- **Missing materials affecting confidence** Full manuscript, methods section, experimental protocols, statistical analyses, benchmark definitions, phage display screen details, binding affinity measurements, specificity data, and all primary data. The absence of these materials severely limits the ability to evaluate the validity and robustness of the reported claims.

## Reviewer

- **Overall assessment** The abstract presents an ambitious and potentially significant advance in de novo protein design, specifically targeting polar, solvent-exposed epitopes and flexible ligands such as carbohydrates. The core idea of reward-guided latent generative search with sequence-structure codesign is conceptually interesting and could address known limitations of current inverse-folding approaches. However, the abstract alone provides insufficient evidence to assess the technical soundness, statistical rigor, or reproducibility of the reported results. The claims of "first de novo proteins that bind a free carbohydrate" and broad superiority over other methods require detailed experimental and computational evidence that is not visible here. The manuscript may be of high interest to the protein design and engineering community, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational protein designers, structural biologists, and engineers working on binder design, antibody engineering, and therapeutic development would be interested. The claim of accessing previously untapped target classes, particularly carbohydrates, would also attract researchers in glycobiology and vaccine development. The methodological advance of codesigning sequence and structure in latent space with inference-time search is relevant to the broader generative modeling community.
- **Major strengths** The problem addressed is well-recognized and important. The proposed framework conceptually removes the inverse-folding step, which is a plausible source of inefficiency in current methods. The scale of the experimental screen, over one million designs, suggests a serious empirical effort. The reported success on a carbohydrate target class, if substantiated, would represent a notable advance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The concept of latent generative search with sequence-structure codesign appears novel, though the abstract does not provide enough detail to distinguish it clearly from prior generative approaches. Scientific importance: The target class of polar, flexible ligands is of high importance, and a demonstrated advance would be significant. Interdisciplinary readership: The topic bridges machine learning, structural biology, and therapeutic development, which is well suited to a broad audience. Technical soundness: Not assessable from the abstract alone. Readability for nonspecialists: The abstract is reasonably clear, though terms such as "latent generative search" and "codesigns sequence and structure" may require elaboration for a general audience.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "latent generative search produced more validated binders than every other method tested"
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of superiority over every other method tested is presented without any comparative details. No information is given on which methods were compared, how the comparison was controlled, what metrics were used, or how statistical significance was assessed.
- **Why it matters** A claim of universal superiority is strong and requires a rigorous, well-controlled benchmark. Without details on the comparator methods, experimental conditions, and statistical analysis, the claim cannot be evaluated or reproduced.
- **Resolution test** Provide a full description of the benchmark, including the list of comparator methods, the experimental setup, the number of replicates, the statistical tests used, and the effect sizes. Show that the comparison was fair and that the reported advantage is robust.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "the first de novo proteins that bind a free carbohydrate, including one that discriminates between blood-group antigens"
- **Evidence pointer** Abstract, location not provided
- **Concern** This is a strong novelty claim. The abstract does not provide any experimental data on the carbohydrate-binding proteins, such as binding affinities, specificity measurements, structural characterization, or the definition of "free carbohydrate." It is also unclear how the authors established that no prior de novo carbohydrate binders exist.
- **Why it matters** Novelty claims of this magnitude require a thorough literature search and direct experimental evidence. Without data on binding kinetics, specificity, and structural validation, the claim is unsupported.
- **Resolution test** Provide binding affinity data, specificity assays against related carbohydrates, structural or biophysical characterization of the binder-carbohydrate interaction, and a clear literature search demonstrating the absence of prior de novo carbohydrate binders.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The model codesigns sequence and structure - generating them together in a continuous latent space - and thereby removes the inverse-folding step"
- **Evidence pointer** Abstract, location not provided
- **Concern** The technical description of the model is minimal. No details are provided on the architecture, training data, latent space properties, or how reward-guided search is implemented. The claim that codesign removes the inverse-folding step is plausible but requires a clear explanation of how sequence and structure are jointly generated and how this differs from existing approaches.
- **Why it matters** The methodological contribution is central to the paper. Without a detailed technical description, the novelty and validity of the approach cannot be assessed, and the work cannot be reproduced or built upon.
- **Resolution test** Provide a full methods section describing the model architecture, training procedure, latent space design, and the reward-guided search algorithm. Include a comparison with existing sequence-structure codesign methods to clarify the claimed distinction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "It delivered high-affinity binders across therapeutic receptors, a viral attachment protein and intracellular signalling targets"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract lists target classes but provides no quantitative data. No affinity values, target names, or functional assays are described. The term "high-affinity" is undefined.
- **Why it matters** The practical utility of the method depends on the quality of the binders produced. Without quantitative affinity data and functional validation, the claim of high-affinity binders is unsubstantiated.
- **Resolution test** Provide a table of target names, measured affinities, assay types, and functional validation results. Define the threshold for "high-affinity" in the context of the intended applications.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "In a screen of more than one million designs by multiplexed phage display"
- **Evidence pointer** Abstract, location not provided
- **Concern** The scale of the screen is stated, but no details are given on the design library construction, the phage display protocol, the selection strategy, or the criteria for calling a "validated binder." The reproducibility of the screen is therefore not assessable.
- **Why it matters** The screen is the primary experimental evidence for the method's success. Without a detailed protocol and clear validation criteria, the results cannot be reproduced or independently verified.
- **Resolution test** Provide a complete description of the library design, phage display selection, hit identification, and validation pipeline. Include details on controls, replicates, and the definition of a validated binder.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "latent generative search" is introduced without definition or context. Readers unfamiliar with generative models may not understand what this means.
- **Required correction** Define the term clearly in the abstract or provide a brief explanation of how the search operates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Target class description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions "therapeutic receptors, a viral attachment protein and intracellular signalling targets" but does not name any of them. This makes it difficult to assess the breadth and relevance of the results.
- **Required correction** Provide at least a few named examples of the targets in each class, or refer to a table in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Comparison statement
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "its codesigned sequences surpassing post hoc redesign" is vague. It is unclear what "post hoc redesign" refers to and how the comparison was made.
- **Required correction** Clarify what post hoc redesign means in this context and describe the comparison briefly.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Code and data availability
- **Evidence pointer** Footnotes, location not provided
- **Issue** The abstract mentions a GitHub repository and a research page, but it is unclear whether the code, model weights, and data are fully accessible or whether there are restrictions.
- **Required correction** State clearly in the abstract or a data availability statement what is publicly released and under what license.

## Risk / unsupported claims

- The claim that latent generative search produced more validated binders than every other method tested is unsupported without comparative data and statistical analysis.
- The claim of generating the first de novo proteins that bind a free carbohydrate is unsupported without experimental data and a literature search.
- The claim of high-affinity binders across multiple target classes is unsupported without quantitative affinity measurements.
- The technical claim that codesigning sequence and structure removes the inverse-folding step is not assessable without a detailed methods description.
- The reproducibility of the phage display screen is not assessable without a full protocol and validation criteria.