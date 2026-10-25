## Review setup

- **Input scope** Abstract only (title, author list, and arXiv metadata provided; no abstract text, figures, tables, or methods were included in the supplied material)
- **Assessment boundary** The manuscript's stated contribution, as inferred from the title and submission metadata, is a method named EMBER for predicting TCR–pMHC binding without requiring a docked complex structure. No technical content, results, or validation data were available for assessment.
- **Shared manuscript claim summary** The title asserts that EMBER can predict TCR–pMHC binding in the absence of a docked complex, implying a computational approach that bypasses structural docking steps typically required in this domain.
- **Visible evidence base** Title, author list, submission date, arXiv identifier, and subject classification (Quantitative Biology, Quantitative Methods). No abstract, main text, figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** The complete abstract, all methodological details, all results, all validation data, all figures and tables, and any code or data availability statements. Without these, no technical claim can be evaluated.

## Reviewer

- **Overall assessment** The supplied material consists solely of a title and bibliographic metadata. The title indicates a potentially relevant contribution to computational immunology, specifically in the area of TCR–pMHC binding prediction. However, the absence of any substantive content, including the abstract itself, precludes any meaningful evaluation of the method, its novelty, its validation, or its claims. The manuscript cannot be assessed in its current form from the provided evidence.
- **Who would be interested in the results, and why** Based on the title alone, researchers in computational immunology, T-cell epitope prediction, and structural bioinformatics would likely be interested if the method delivers accurate binding predictions without docking, as this could reduce computational cost and remove a common failure mode in existing pipelines. Clinicians and vaccine developers might also find value if the method generalizes across alleles and epitopes. However, these are speculative inferences from the title and cannot be confirmed without content.
- **Major strengths** None can be identified from the supplied material. The title suggests a clear methodological focus, but no evidence of implementation, performance, or comparison is available.
- **Major Concerns** The following concerns are raised based on the absence of content. Each is marked as blocking because the core claim cannot be assessed without the missing material.
- **Minor Comments** None can be identified from the supplied material.
- **Technical failings that need to be addressed before the case is established** The complete absence of technical content is the sole failing. No method description, no dataset description, no evaluation protocol, no baseline comparison, and no results are available. The case for the method's utility is entirely unestablished.
- **Assessment against Nature-style criteria** Originality cannot be assessed because no comparison to existing methods is provided. Scientific importance cannot be assessed because no evidence of predictive performance or biological insight is provided. Interdisciplinary readership cannot be assessed because the presentation and framing are unknown. Technical soundness cannot be assessed because no methodological detail or validation is available. Readability for nonspecialists cannot be assessed because no text is available. All five criteria are unevaluable from the supplied material.
- **Recommendation posture** Currently not established from the provided evidence. A substantive manuscript, including at minimum the abstract, methods, results, and validation, is required before any recommendation can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The title claims that EMBER predicts TCR–pMHC binding without a docked complex.
- **Evidence pointer** Location not provided
- **Concern** The supplied material contains no abstract, no main text, and no supplementary information. The only claim available is the title itself, which cannot be verified or evaluated in any way.
- **Why it matters** A scientific claim requires supporting evidence, including a description of the method, the data used, the evaluation protocol, and the results. Without any of these, the claim is unfalsifiable and cannot be assessed for validity, novelty, or utility.
- **Resolution test** Provide the full abstract and manuscript text, including a description of the EMBER method, the datasets used, the evaluation metrics, and the results. The claim can then be assessed against the evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The title implies that EMBER achieves binding prediction without a docked complex, which suggests a methodological departure from docking-dependent approaches.
- **Evidence pointer** Location not provided
- **Concern** No methodological detail is available. It is unknown how EMBER represents TCR and pMHC inputs, what features it uses, what model architecture it employs, or how it avoids the need for docking. Without this information, the technical approach cannot be evaluated for soundness or feasibility.
- **Why it matters** The central claim of the work is a methodological one. If the method is not described, reviewers and readers cannot determine whether the approach is technically valid, whether it is genuinely docking-free, or whether it is likely to generalize beyond the training data.
- **Resolution test** Provide a detailed methods section describing the input representation, model architecture, training procedure, and the specific mechanism by which docking is avoided. This will allow assessment of technical soundness.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and reproducibility
- **Claim pointer** The title implies that EMBER provides accurate binding predictions, which is a performance claim.
- **Evidence pointer** Location not provided
- **Concern** No results, no performance metrics, no baseline comparisons, and no validation datasets are provided. It is impossible to determine whether EMBER achieves any level of predictive accuracy, whether it outperforms existing methods, or whether its predictions are biologically meaningful.
- **Why it matters** A prediction method is only useful if it is validated. Without results, there is no evidence that EMBER works, and no basis for comparing it to existing TCR–pMHC binding predictors.
- **Resolution test** Provide results on benchmark datasets, including performance metrics such as AUC, accuracy, or correlation, and comparisons to established methods. Include details on cross-validation or independent test sets to establish generalizability.

### Minor Comments

None identified from the supplied material.

## Risk / unsupported claims

- The title's claim that EMBER predicts TCR–pMHC binding without a docked complex is entirely unsupported because no evidence is provided.
- Any implied performance or utility of the method is unsupported because no results are available.
- Any implied novelty relative to existing methods is unevaluable because no comparison or literature context is provided.
- All claims about the method's architecture, inputs, or training are unevaluable because no methodological description is available.