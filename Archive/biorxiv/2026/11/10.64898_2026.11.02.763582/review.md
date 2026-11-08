## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, methods, results, case studies, conclusions, and data availability. Figures and tables are referenced but not provided.
- **Assessment boundary** The scientific validity of the proposed RNA validation method, the soundness of the benchmarking approach, the interpretation of the PDB scan results, and the strength of the claims made in the abstract and conclusions.
- **Shared manuscript claim summary** The authors extend the protein-focused validation tool conkit-validate to RNA structures. The method uses contact-map overlap (CMO) and a machine-learning classifier to detect register errors and other modelling mistakes in RNA structures, leveraging coevolutionary information from structure prediction models. The authors claim performance comparable to the protein version, independence from local map resolution, and complementary value to map-based validation methods.
- **Visible evidence base** The manuscript text describes the benchmarking dataset creation, the prediction methods used (AF3, Boltz, Protenix, trRosettaRNA2, RNAPro), the CMO and classifier results, and five case studies. Quantitative results are presented in figures and tables that were not available for review.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are missing. This includes the F1 score plots, ROC curves, confusion matrices, feature importance plots, and the detailed case study figures. The methods section is incomplete, with equations and algorithm details not fully described. The supplementary notes referenced in the text are not provided.

## Reviewer

- **Overall assessment** The manuscript presents a timely and potentially useful extension of a protein validation method to RNA. The core idea, using predicted contact maps to detect register errors in RNA structures, is sound and addresses a real gap in the field. However, the current manuscript has several significant weaknesses. The benchmarking dataset is small and artificially generated, the comparison to existing methods is limited, and the PDB scan results are difficult to interpret without the missing figures. The case studies are interesting but the evidence for the claimed errors is not always conclusive. The manuscript would benefit from a more rigorous evaluation of the method's limitations and a clearer demonstration of its practical utility.
- **Who would be interested in the results, and why** Structural biologists who determine RNA structures by cryo-EM or X-ray crystallography would be the primary audience. The method offers a mapless validation approach that could be useful when map quality is poor. Developers of structure prediction and validation tools would also be interested in the methodological details and the comparison of different prediction methods. The work is relevant to the broader community interested in RNA structure and function.
- **Major strengths**
    1.  The problem addressed is important. RNA structure validation is underdeveloped compared to protein validation, and register errors are a known and serious issue.
    2.  The approach is conceptually novel in the RNA field, adapting a proven protein method (conkit-validate) rather than inventing a new one from scratch.
    3.  The use of multiple prediction methods (general and RNA-specific) and both structure and distogram inputs is a thoughtful and thorough approach.
    4.  The case studies, particularly the 8RXH and 9BUQ examples, provide concrete illustrations of the method's potential and its limitations.
    5.  The authors are transparent about the method's limitations, including the issue of false positives and the dependence on prediction quality.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The benchmarking dataset of 49 structures with artificially induced errors is used to claim the method "shows performance similar to that previously achieved for proteins."
    - **Evidence pointer** Methods, Benchmark dataset creation; Results, Contact map alignment identifies known errors in the benchmark data
    - **Concern** The benchmarking dataset is created by artificially degrading high-resolution cryo-EM maps and then re-tracing them with DeepCryoRNA. This is a reasonable approach, but the resulting errors may not be representative of the errors that occur in real experimental structure determination. The manuscript does not discuss the types of errors that are most common in real RNA structures and whether the artificial errors are similar. The claim of "performance similar to that previously achieved for proteins" is difficult to evaluate without the actual performance numbers and a direct comparison to the protein study.
    - **Why it matters** If the benchmarking set does not reflect real-world errors, the reported performance metrics may be misleading. The claim of similarity to the protein version is a key selling point and needs to be substantiated with comparable metrics.
    - **Resolution test** The authors should provide a more detailed analysis of the types of errors in the benchmarking set and compare them to known error types in the PDB. They should also present the performance metrics (F1, precision, recall) for the RNA method alongside the corresponding metrics from the protein study.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The PDB scan is used to claim that the method "can identify register errors where the density alone cannot decide between models."
    - **Evidence pointer** Results, Complementarity of contact and map based methods in a limited PDB scan; Case studies
    - **Concern** The PDB scan results are presented in a way that is difficult to assess. The numbers of flagged chains are given, but the key figure (Fig. 8) showing the overlap between methods is not available. The case studies are presented as evidence, but the selection criteria for these cases are not stated. It is unclear how many of the flagged errors were confirmed, how many were false positives, and how many remain unresolved. The claim that the method can identify errors "where the density alone cannot decide" is only supported by a single case study (8RXH) where the density was not used to decide.
    - **Why it matters** The practical utility of the method depends on its performance on real PDB structures. Without a clear and unbiased assessment of the scan results, it is impossible to judge whether the method is genuinely useful or whether it produces too many false positives to be practical.
    - **Resolution test** The authors should provide a more systematic analysis of the PDB scan results, including a breakdown of the flagged errors by type, a comparison of the different methods' performance, and a clear statement of how many errors were confirmed by visual inspection or other means. The case studies should be presented as part of a larger, unbiased survey.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific importance
    - **Claim pointer** The abstract claims the method "remains applicable where map-based approaches are not" and that it provides "complementary value."
    - **Evidence pointer** Results, Complementarity of contact and map based methods in a limited PDB scan; Conclusions
    - **Concern** The claim of complementarity is based on the observation that the CMO method's detection rate does not depend on local resolution. However, the manuscript does not directly compare the performance of conkit-validate to map-based methods on the same set of structures. The case study of 4WCE shows a case where the map-based method could not confirm the error, but this is a single example. A more direct comparison, perhaps by running a map-based method on the same benchmarking set, would strengthen the claim.
    - **Why it matters** The value proposition of the method is that it provides information that map-based methods cannot. This needs to be demonstrated more rigorously than with a single case study.
    - **Resolution test** The authors should run a map-based validation method (e.g., CMS) on the same benchmarking set and compare the detection rates. They should also provide a more detailed analysis of the cases where conkit-validate and CMS disagree.
    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness
    - **Claim pointer** The machine learning classifier is trained and evaluated on the same artificially generated dataset, and the manuscript claims it can detect "errors other than register shifts."
    - **Evidence pointer** Methods, Machine learning classification; Results, Performance of machine learning classifiers
    - **Concern** The classifier is trained on the same type of artificial errors used for benchmarking the CMO method. This is a circular validation. The manuscript does not describe the types of errors the classifier is designed to detect, nor does it provide evidence that the classifier can generalize to real-world errors. The feature importance analysis is mentioned but not shown.
    - **Why it matters** A classifier trained on artificial errors may not perform well on real structures. The claim that it can detect errors beyond register shifts is not supported by the evidence presented.
    - **Resolution test** The authors should describe the error types in the training set and test the classifier on a set of real structures with known errors. They should also show the feature importance analysis to demonstrate that the classifier is using meaningful information.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Introduction
    - **Evidence pointer** Introduction, paragraph 1
    - **Issue** The introduction is well-written but assumes a high level of familiarity with the field of structure validation. The distinction between map-based and model-based validation could be explained more clearly for a general structural biology audience.
    - **Required correction** Consider adding a brief explanation of the two main classes of validation methods and why a mapless approach is needed.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methods, Benchmark dataset creation
    - **Evidence pointer** Methods, Benchmark dataset creation
    - **Issue** The threshold for defining a contact is set to 12.5 Å based on F1 score optimization. This is a very long distance for a contact, and it is not clear if this is physically meaningful for RNA.
    - **Required correction** The authors should discuss the physical interpretation of this threshold and whether it is appropriate for RNA, given that the method was originally developed for proteins.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Results, Case study 8I3Z
    - **Evidence pointer** Results, Case study from the PDB 8I3Z chain B
    - **Issue** The false positive in the 8I3Z case is attributed to the lack of context in the prediction. This is an important limitation, but it is only discussed in a single case study.
    - **Required correction** The authors should discuss the broader implications of this limitation and how users can assess whether their prediction has sufficient context.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Originality
    - **Affected element** Discussion
    - **Evidence pointer** Conclusions
    - **Issue** The conclusions section is brief and does not discuss the method's limitations in the context of other validation approaches.
    - **Required correction** A more detailed discussion of the method's place in the validation landscape, its limitations, and potential future improvements would strengthen the manuscript.
    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methods, Filtering
    - **Evidence pointer** Methods, Filtering
    - **Issue** The filtering step uses a machine learning classifier trained on the same data as the main classifier. This could lead to overfitting.
    - **Required correction** The authors should clarify how the filter was trained and whether it was evaluated on a separate dataset.
- **Assessment against Nature-style criteria**
    - **Originality** The adaptation of a protein contact-map validation method to RNA is a novel contribution. The use of predicted contact maps for validation, rather than just structure prediction, is a creative idea. However, the core methodology is not new, and the novelty lies in the application.
    - **Scientific importance** The problem of RNA structure validation is important and growing in relevance as more RNA structures are determined. A reliable mapless validation method would be a valuable tool. The potential impact is significant, but the current evidence is insufficient to fully establish the method's utility.
    - **Interdisciplinary readership** The work is primarily of interest to structural biologists and computational biologists. The methods are specific to the field, and the broader impact on other disciplines is not immediately apparent.
    - **Technical soundness** The technical approach is generally sound, but there are significant concerns. The benchmarking dataset is artificial and may not be representative. The evaluation of the PDB scan is incomplete without the figures. The machine learning classifier's validation is circular. These issues need to be addressed.
    - **Readability for nonspecialists** The manuscript is clearly written but is technical and assumes a specialist audience. The abstract is accessible, but the methods and results sections would be challenging for a nonspecialist.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the case studies are compelling. However, the current manuscript does not fully establish the method's validity and utility. The authors need to provide a more rigorous evaluation, particularly of the benchmarking dataset and the PDB scan results.

## Risk / unsupported claims

- The claim that the method's performance is "similar to that previously achieved for proteins" is not supported by direct comparison.
- The claim that the method "can identify register errors where the density alone cannot decide between models" is only supported by a single case study and is not a general conclusion.
- The claim that the method "remains applicable where map-based approaches are not" is based on a single analysis of detection rate vs. resolution and needs more direct evidence.
- The performance of the machine learning classifier on real-world errors is unknown, as it was only tested on artificial errors.
- The effectiveness of the filtering step is not fully evaluated, and its training procedure is unclear.