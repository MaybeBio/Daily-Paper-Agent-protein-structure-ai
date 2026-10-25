## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose simplex-projected gradient descent (PGD) as an alternative to gradient descent on softmax-reparameterised sequence logits for hallucination-based protein binder design. They report that PGD minimises design loss in fewer iterations, produces designs with higher predicted interface confidence, improves in silico hit rates on six of ten targets with no significant degradation, yields more structurally diverse designs, and increases in silico hits per GPU-hour by 29% when paired with candidate screening.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data were supplied
- **Missing materials affecting confidence** Full manuscript, methods description, all figures and tables, supplementary information, code repository contents, and design data are not available for assessment

## Reviewer

- **Overall assessment** The abstract presents a potentially useful methodological contribution to the protein binder design community, addressing a practical gap in optimiser selection for gradient-based hallucination. The claims are specific and quantitative, which is commendable. However, the evidence base provided is insufficient to evaluate the technical soundness of the approach, the statistical rigour of the comparisons, or the generalisability of the findings. Several claims require detailed methodological and statistical support that is not visible in the abstract alone.
- **Who would be interested in the results, and why** Computational protein designers, particularly those working on binder design and de novo protein hallucination. Researchers developing optimisation methods for sequence design in continuous relaxation spaces would also find the comparison between PGD and softmax-based approaches relevant. The efficiency gains in GPU-hours may interest practitioners running large-scale in silico screening campaigns.
- **Major strengths** The work addresses a specific and under-evaluated component of the hallucination pipeline, namely the optimiser choice. The proposed method is conceptually simple and likely easy to implement, which lowers the barrier to adoption. The evaluation includes multiple targets and a practical metric (hits per GPU-hour) that reflects real campaign constraints. The inclusion of structural diversity as an outcome measure is a useful addition beyond loss minimisation.
- **Major Concerns** The abstract alone does not provide sufficient detail to assess the validity of the reported improvements. Key methodological choices, statistical tests, and baseline configurations are not described. The claim of "no significant degradation on any" target requires knowledge of the statistical power and test used. The 29% improvement in hits per GPU-hour depends on unspecified screening thresholds and trajectory lengths. The mechanism by which PGD allows suppressed amino acids to re-enter the design is stated but not demonstrated.
- **Minor Comments** The abstract would benefit from specifying the number of independent runs or seeds used. The choice of ESMFold2 as the structure predictor and its potential influence on the results is not discussed. The relationship between predicted interface confidence and experimentally validated binding is not addressed. The public availability of code and data is noted but the contents are not described.
- **Technical failings that need to be addressed before the case is established** The statistical methodology for comparing PGD against the softmax baseline is not described. The definition of "in silico hit" and the ipSAE threshold used are not provided. The computational cost comparison appears to conflate optimisation iterations with wall-clock time, which may be misleading if per-iteration costs differ between methods. The diversity metric is not defined.
- **Assessment against Nature-style criteria** Originality: moderate. The application of PGD to hallucination-based design is a reasonable incremental contribution, but the core idea of projected gradient methods in probability simplices is well established in optimisation literature. Scientific importance: potentially relevant to a specialised community, but the abstract does not demonstrate broad biological or methodological significance beyond an incremental improvement. Interdisciplinary readership: limited; the work is primarily of interest to computational protein designers and optimisation researchers. Technical soundness: not assessable from the abstract; the absence of methodological detail precludes evaluation of the statistical and computational claims. Readability for nonspecialists: the abstract is reasonably clear for a technical audience but assumes familiarity with hallucination-based design, ipSAE, and sequence logit reparameterisation.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigour
- **Claim pointer** "PGD significantly improves on six of the ten targets, with no significant degradation on any"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract reports significant improvement on six of ten targets and no significant degradation on any, but does not describe the statistical test used, the multiple-comparison correction applied, the number of independent replicates, or the variance structure of the metrics compared. Without this information, the significance claims cannot be evaluated.
- **Why it matters** The central claim of the paper rests on the statistical comparison between PGD and the softmax baseline. If the tests are underpowered, improperly corrected, or based on non-independent samples, the conclusions may not hold. The "no significant degradation" claim is particularly sensitive to statistical power.
- **Resolution test** Provide a detailed description of the statistical framework, including the test used, the number of independent runs, the handling of multiple comparisons across ten targets, and the effect sizes observed. Show that the tests are adequately powered to detect meaningful differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** "PGD avoids softmax-induced gradient attenuation and allows amino acids suppressed early in optimisation to re-enter the design"
- **Evidence pointer** Abstract; location not provided
- **Concern** The mechanism by which PGD enables re-entry of suppressed amino acids is stated as a property of the method, but no evidence is presented to demonstrate that this occurs in practice or that it contributes to the observed improvements. The gradient attenuation argument is plausible but requires formal or empirical support.
- **Why it matters** The proposed advantage of PGD over the softmax baseline is central to the motivation of the work. If the mechanism is not demonstrated, the improvement could be attributed to other factors, such as different effective learning rates or update scales.
- **Resolution test** Provide a formal argument or empirical demonstration that PGD allows recovery of suppressed amino acids, and show that this property is linked to the observed performance gains, for example through ablation or trajectory analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational cost comparison
- **Claim pointer** "pairing shorter PGD runs with candidate screening raises the total number of in silico hits per GPU-hour by 29% relative to default-length trajectories"
- **Evidence pointer** Abstract; location not provided
- **Concern** The 29% improvement in hits per GPU-hour depends on the definition of "shorter" runs, the screening threshold, and the baseline trajectory length. The abstract does not specify these parameters, nor does it clarify whether the comparison accounts for the computational cost of screening itself.
- **Why it matters** The efficiency claim is a practical selling point of the method. If the comparison is not apples-to-apples, or if the screening cost is excluded, the reported improvement may be misleading.
- **Resolution test** Specify the trajectory lengths compared, the screening protocol and its computational cost, and the exact calculation of hits per GPU-hour. Show that the comparison is fair and that the result is robust to reasonable variations in these parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Outcome metric validity
- **Claim pointer** "produces designs with higher predicted interface confidence" and "more structurally diverse designs on every target"
- **Evidence pointer** Abstract; location not provided
- **Concern** The metrics used to support these claims are not defined. "Predicted interface confidence" presumably refers to a specific output of ESMFold2, but the exact quantity is not stated. The structural diversity metric is also unspecified. Without definitions, the claims cannot be reproduced or compared with other work.
- **Why it matters** The practical value of the method depends on whether the reported improvements in predicted confidence and diversity translate to better experimental outcomes. If the metrics are poorly chosen or defined, the claims may not be meaningful.
- **Resolution test** Define all metrics precisely, including how they are computed from the model outputs and how diversity is quantified. Justify the choice of these metrics as proxies for binder quality.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental setup
- **Evidence pointer** Abstract; location not provided
- **Issue** The number of independent runs or random seeds used for each target is not stated. Stochastic optimisation results can vary substantially across seeds, and the reported improvements may not be stable.
- **Required correction** Report the number of independent replicates and the variance across runs for the key metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Generalisability
- **Affected element** Target selection
- **Evidence pointer** Abstract; location not provided
- **Issue** The ten targets are not described. Their diversity in terms of size, fold, binding interface characteristics, or difficulty is unknown, which limits the reader's ability to judge the generalisability of the findings.
- **Required correction** Provide a brief description of the ten targets and justify their selection as a representative test set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "hallucination-based" is used without definition. While familiar to practitioners, the abstract should briefly clarify what this entails for readers outside the immediate subfield.
- **Required correction** Add a brief explanation of hallucination-based design in the abstract or introduction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Practical relevance
- **Affected element** Experimental validation
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract reports only in silico results. No experimental validation of designed binders is mentioned, which limits the practical significance of the claims.
- **Required correction** State clearly that results are in silico only, or include any experimental validation if available.

## Risk / unsupported claims

- The claim that PGD "allows amino acids suppressed early in optimisation to re-enter the design" is stated without supporting evidence in the abstract.
- The statistical significance claims for six of ten targets are not supported by any described statistical methodology.
- The 29% improvement in hits per GPU-hour is not supported by a described calculation or comparison framework.
- The claim of "more structurally diverse designs on every target" is not supported by a defined diversity metric.
- The generalisability of the findings beyond the ten unspecified targets is not established.
- The relationship between predicted interface confidence and experimental binder success is not addressed, leaving the practical relevance of the primary outcome metric unclear.