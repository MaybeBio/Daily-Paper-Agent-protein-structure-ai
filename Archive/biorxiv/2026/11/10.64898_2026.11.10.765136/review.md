## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors audit three components of a protein generate-and-screen pipeline: repetition steering, ESMFold confidence, and an activation readout. They report that steering preserves confidence at its operating point but exhibits a cliff at a specific alpha value, that direction matters at moderate push but not at saturation, that unsteered generator activations predict the confidence gate with moderate accuracy, that length sensitivity can manufacture false nulls, and that no balanced-accuracy interval excludes chance for experimental stability on matched design-scramble pairs. They conclude that predicting the gate does not establish foldability and that readouts should be tested for what they measure before use in selection.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods descriptions, statistical details, dataset descriptions, code repository contents, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a potentially useful cautionary audit of common practices in protein language model pipelines. The core message, that predicted confidence and activation readouts should not be conflated with experimental foldability, is sensible and worth stating. However, the abstract as provided is too compressed to evaluate the technical soundness of the claims. Key quantities are presented without context, the relationship between the different analyses is not fully clear, and the statistical and methodological details necessary to assess the validity of the conclusions are absent. The work may be of interest to practitioners in protein design and machine learning, but the evidence base provided is insufficient to establish the case.
- **Who would be interested in the results, and why** Researchers developing protein generate-and-screen pipelines, particularly those using protein language models for steering or design, would be the primary audience. The cautionary findings about confidence metrics and activation readouts are relevant to anyone using ESMFold or similar tools for candidate selection. The replication of length sensitivity effects and the demonstration of false nulls are also relevant to experimentalists interpreting stability assays. The work may also interest methodologists working on interpretability and evaluation of language models in scientific domains.
- **Major strengths** The abstract addresses a practical and under-examined question, namely whether common readouts in protein design pipelines measure what they are assumed to measure. The inclusion of a negative result, that experimental stability cannot be predicted from the confidence gate, is valuable. The authors also appear to have conducted matched controls, such as composition- and length-matched design-scramble pairs, which is a strength if the underlying methods are sound. The provision of code and data is commendable.
- **Major Concerns** The abstract is too brief to support the claims made. Several quantitative results are presented without sufficient context or statistical detail. The relationship between the different analyses is not fully clear. The central negative result, that no balanced-accuracy interval excludes chance, is stated without the necessary details to assess its strength. The claim that predicting the gate does not establish foldability is a reasonable inference but requires more evidence than the abstract provides.
- **Minor Comments** The abstract would benefit from clearer definitions of key terms, such as the activation readout and the confidence gate. The use of the term "confessions" in the title is informal for a scientific manuscript. The abstract does not state the number of proteins, designs, or replicates used, which limits interpretability. The GitHub repository is mentioned but its contents are not described.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide enough methodological detail to assess the validity of the statistical claims. The cliff at alpha_50 = 1.240x is presented without confidence intervals or a description of the fitting procedure. The ROC-AUC of 0.786 +/- 0.004 is reported but the underlying model and cross-validation scheme are not described. The balanced-accuracy intervals are mentioned but their construction is not explained. The length sensitivity replication is stated but not quantified.
- **Assessment against Nature-style criteria** Originality: the question of whether readouts track their intended targets is not new, but the specific combination of steering, confidence, and activation readouts in a single audit may offer a useful synthesis. Scientific importance: the findings are potentially important for practitioners, but the abstract does not establish the robustness of the results. Interdisciplinary readership: the work sits at the intersection of machine learning and protein biophysics, and the abstract is written in a way that is largely accessible to both communities, though some terms are undefined. Technical soundness: cannot be assessed from the abstract alone; the statistical details are insufficient. Readability for nonspecialists: the abstract is concise but assumes familiarity with protein language models, steering, and ESMFold, which limits accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient methodological and statistical detail to assess the validity of the claims. A full manuscript with methods, figures, and statistical analyses would be required to evaluate the work properly.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The authors report a fitted cliff at alpha_50 = 1.240x with the sweep's own control at 64.0%, and state that direction matters at moderate matched-norm push but not at saturation.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports specific quantitative results without any description of the underlying statistical methods. The cliff at alpha_50 = 1.240x is presented as a fitted value, but no confidence intervals, fitting procedure, or model selection criteria are described. The comparison to the sweep's own control at 64.0% is unclear in its meaning and significance. The claim that direction matters at moderate push but not at saturation is stated without any effect sizes, error bars, or statistical tests.
- **Why it matters** These quantitative claims are central to the paper's message about steering behavior. Without statistical context, the reader cannot assess whether the observed effects are robust or could be artifacts of the fitting procedure or the specific operating point chosen. The distinction between moderate and saturated push is a qualitative claim that requires quantitative support.
- **Resolution test** Provide the full methods for the steering experiments, including the fitting procedure, confidence intervals for alpha_50, the definition of matched-norm push, and the statistical tests used to compare conditions. Show the data points and error bars for the relevant comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that no balanced-accuracy interval excludes chance for experimental stability on composition- and length-matched design-scramble pairs.
- **Evidence pointer** Abstract, location not provided
- **Concern** This is the central negative result of the abstract, but it is stated in a single sentence without any supporting details. The reader does not know how many design-scramble pairs were tested, what experimental stability assay was used, how balanced accuracy was computed, what the confidence intervals were, or what the range of observed values was. The claim that no interval excludes chance is strong and requires substantial evidence.
- **Why it matters** The conclusion that predicting the gate does not establish foldability rests entirely on this negative result. If the analysis is underpowered, the null result may be uninformative. If the assay is noisy, the result may not generalize. The abstract does not provide enough information to distinguish between a robust null result and an underpowered study.
- **Resolution test** Provide the number of design-scramble pairs, the assay details, the distribution of balanced accuracy values, the confidence interval construction method, and a power analysis or equivalent justification that the study was adequately powered to detect meaningful effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors report that unsteered generator activations predict the confidence gate with ROC-AUC 0.786 +/- 0.004, supporting cost-aware, model-specific triage.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe what the activation readout is, how it was constructed, what model was used, how the ROC-AUC was computed, or what cross-validation scheme was employed. The claim that this supports cost-aware triage is an inference that requires the reader to understand the relationship between the activation readout and the confidence gate, which is not explained.
- **Why it matters** The activation readout is one of the three components the authors claim to audit. Without a clear description of what it is and how it was measured, the reader cannot evaluate whether the reported predictive performance is meaningful or whether the triage recommendation is justified.
- **Resolution test** Describe the activation readout in detail, including the model architecture, the layer or representation used, the dimensionality, and the classification setup. Provide the ROC-AUC computation details, including cross-validation scheme and number of samples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that they replicate established length sensitivity, through which shortening can manufacture false nulls.
- **Evidence pointer** Abstract, location not provided
- **Concern** The replication of length sensitivity is mentioned but not quantified. The reader does not know what the original finding was, how the replication was conducted, or what the magnitude of the effect was. The claim that shortening can manufacture false nulls is important but requires evidence.
- **Why it matters** This finding is presented as a cautionary note about experimental design. Without quantification, the reader cannot assess the practical importance of the effect or whether the replication is convincing.
- **Resolution test** Provide the details of the length sensitivity analysis, including the range of lengths tested, the effect size, and a comparison to the original finding being replicated.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title
- **Evidence pointer** Title, location not provided
- **Issue** The title uses the informal term "Confessions" which is unusual for a scientific manuscript and may not convey the technical nature of the work.
- **Required correction** Consider a more descriptive title that reflects the audit nature of the study, such as "An Audit of Steering, Activation Readouts, and Confidence Metrics in Protein Language Model Pipelines."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** Several terms are used without definition, including "repetition steering," "confidence gate," and "activation readout." Readers outside the immediate subfield may struggle to follow the abstract.
- **Required correction** Provide brief definitions or contextual descriptions for these terms in the abstract, or restructure the abstract to make the pipeline components clearer.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not state the scale of the study, such as the number of proteins, designs, or replicates. This limits the reader's ability to gauge the robustness of the findings.
- **Required correction** Include key numbers, such as the number of design-scramble pairs, the number of proteins tested, and the number of replicates, where relevant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data statement
- **Evidence pointer** Abstract, location not provided
- **Issue** The GitHub repository is mentioned but its contents, structure, and any dependencies are not described. The reader cannot assess whether the code is usable or the data are accessible.
- **Required correction** Provide a brief description of the repository contents, including the main scripts, data files, and any required dependencies or environment specifications.

## Risk / unsupported claims

- The claim that steering preserves confidence at its operating point is unsupported without details on the operating point and the measurement of confidence.
- The claim that a fitted cliff follows at alpha_50 = 1.240x is unsupported without the fitting procedure and confidence intervals.
- The claim that direction matters at moderate matched-norm push but not at saturation is unsupported without effect sizes and statistical tests.
- The claim that unsteered generator activations predict the confidence gate with ROC-AUC 0.786 +/- 0.004 is unsupported without details on the activation readout and the classification setup.
- The claim that no balanced-accuracy interval excludes chance for experimental stability is unsupported without details on the assay, the number of pairs, and the interval construction.
- The claim that predicting the gate does not establish foldability is an inference that is not fully supported by the abstract alone.
- The replication of established length sensitivity is mentioned but not quantified, making the claim unassessable.
- The recommendation that cost-aware, model-specific triage is supported by the activation readout is an inference that requires more evidence.