## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present SeqSol, a sequence-level solubility prediction model trained on 71,425 proteins, which achieves 75.8% accuracy and an AUC of 0.840 on an independent test set. The model prioritizes single-amino-acid substitutions via WT-mutant rescoring. Candidate sites are further filtered by conformational flexibility, relative solvent accessibility, and evolutionary conservation. The integrated framework, SeqSol-FECS, reportedly increased the solubility of two industrial enzymes from 56.18% and 10.53% to over 95% while maintaining specific activities, using only 30 experimentally tested mutations.
- **Visible evidence base** Abstract text only; no methods section, dataset description, model architecture details, experimental protocols, or numerical validation data beyond the metrics stated in the abstract
- **Missing materials affecting confidence** Full methods, model training and validation details, dataset composition and split strategy, definition of the independent test set, mutation selection criteria, experimental solubility assay protocols, activity measurement methods, statistical analysis, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially useful framework for protein solubility engineering, combining sequence-level prediction with structural filtering criteria. The reported performance metrics and experimental outcomes are encouraging. However, the abstract alone provides insufficient detail to evaluate the robustness of the model, the validity of the validation strategy, or the generalizability of the experimental results. The claim that only 30 mutations were needed to achieve the reported solubility improvements is striking but cannot be assessed without experimental replication details and statistical context. The work may be of interest to researchers in protein engineering and biomanufacturing, but the evidence base provided is too limited to establish the case.
- **Who would be interested in the results, and why** Researchers in protein engineering, enzyme engineering, and biomanufacturing would be interested in a framework that combines solubility prediction with structural prioritization to reduce experimental burden. Those working on heterologous expression in E. coli and on industrial enzyme production would find the reported solubility improvements relevant. Computational biologists developing sequence-based predictors for protein properties may also be interested in the WT-mutant rescoring approach.
- **Major strengths** The integration of sequence-level prediction with structural filtering criteria is a sensible design choice that addresses the practical need to minimize activity loss. The reported use of a large training set of 71,425 proteins is a positive feature. The experimental validation on two industrial enzymes with maintained specific activities, if fully supported, would demonstrate practical utility. The claim of achieving high solubility improvements with a small number of tested mutations is potentially impactful.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide details on how the independent test set was constructed, whether it was sequence-disjoint from the training set, or how the WT-mutant rescoring was implemented. The criteria for prioritizing mutation sites are named but not defined quantitatively. The experimental solubility measurements lack replication information and error estimates. The claim of maintaining specific activities requires assay details and statistical comparison to wild-type values.
- **Assessment against Nature-style criteria**  
  Originality: The combination of sequence-level rescoring with structural filtering is not entirely novel but the specific integration may offer a new angle. The abstract does not clearly differentiate SeqSol from existing solubility predictors.  
  Scientific importance: If the reported results are robust, the framework could reduce experimental effort in solubility engineering, which is a relevant problem. However, the importance is not fully established from the abstract alone.  
  Interdisciplinary readership: The work bridges computational prediction and experimental enzymology, which could appeal to a broad readership, but the abstract is written in a specialized manner that may limit accessibility.  
  Technical soundness: Cannot be adequately assessed from the abstract. Key methodological details are missing.  
  Readability for nonspecialists: The abstract is concise but uses field-specific terms without sufficient context. The logic from model development to experimental validation is clear at a high level.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but insufficient to support the core claims. A full manuscript with detailed methods and complete experimental data would be required to assess whether the framework performs as reported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** SeqSol achieved an accuracy of 75.8% and an AUC of 0.840 on an independent test set.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not describe how the independent test set was constructed, whether it was separated from the training set at the sequence level to avoid homology leakage, or how the accuracy and AUC were computed. Without this information, the reported metrics cannot be interpreted.  
- **Why it matters** Performance metrics on an independent test set are only meaningful if the test set is truly independent and representative. If sequence similarity between training and test proteins is high, the reported accuracy and AUC may be inflated.  
- **Resolution test** Provide a clear description of the dataset split, including sequence identity thresholds used to ensure non-redundancy, and report the number of proteins in the training and test sets. State the evaluation protocol and any confidence intervals for the metrics.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** SeqSol is capable of prioritizing single-amino-acid substitutions through WT-mutant rescoring.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not explain how the WT-mutant rescoring is implemented, what model architecture is used, or how the model was trained to perform this rescoring. The mechanism by which the model prioritizes mutations is not described.  
- **Why it matters** The WT-mutant rescoring is a central feature of the framework. Without understanding the implementation, the reader cannot assess whether the approach is sound or whether it differs meaningfully from existing methods.  
- **Resolution test** Describe the model architecture, the training objective, and the rescoring procedure in detail. Provide a formal definition of the scoring function used to prioritize substitutions.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** Candidate mutation sites were prioritized according to conformational flexibility, relative solvent accessibility, and evolutionary conservation before solubility engineering.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract names three structural and evolutionary criteria but does not define how they are computed, what thresholds are used, or how they are combined with the SeqSol predictions. The prioritization procedure is not reproducible from the abstract.  
- **Why it matters** The integration of these criteria is a key component of the SeqSol-FECS framework. Without quantitative definitions, the method cannot be replicated or compared with other approaches.  
- **Resolution test** Provide the specific tools, parameters, and thresholds used for each criterion, and describe how the criteria are weighted or combined in the final prioritization.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** Using only 30 experimentally tested mutations, the SeqSol-FECS framework increased the solubility of two industrial enzymes from 56.18% and 10.53% to over 95%, respectively, while maintaining their specific activities.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract reports solubility improvements for two enzymes but provides no experimental details, such as the number of replicates, the assay method, the error bars, or the statistical significance of the improvements. The claim that specific activities were maintained is not supported by any numerical data.  
- **Why it matters** The experimental validation is the core evidence for the practical utility of the framework. Without replication and statistical context, the reported improvements could be within experimental noise or the result of favorable selection.  
- **Resolution test** Provide full experimental protocols, including solubility assay conditions, replicate numbers, and statistical analysis. Report specific activity values for wild-type and mutant enzymes with appropriate error estimates and statistical comparisons.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Model naming and framework description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The relationship between SeqSol and SeqSol-FECS is not fully clear. The abstract states that SeqSol was developed and then describes the SeqSol-FECS framework, but the distinction between the model and the full framework is not explicitly defined.  
- **Required correction** Clarify that SeqSol is the prediction model and SeqSol-FECS is the integrated framework that includes structural filtering, or define the relationship explicitly.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Training data description  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract states that 71,425 proteins were used for training but does not specify the source of these proteins, the range of sequence identities, or whether solubility labels were experimentally determined or computationally derived.  
- **Required correction** Provide a brief description of the training data source and the basis for solubility labels in the full manuscript.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Experimental validation scope  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The experimental validation is limited to two enzymes. While the results are promising, the abstract does not discuss whether the framework would generalize to other protein classes or expression conditions.  
- **Required correction** Add a brief statement in the discussion about the expected scope of applicability and any limitations of the framework.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Code and data availability  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No mention is made of code or data availability, which is important for a computational framework.  
- **Required correction** State in the full manuscript whether the model, training data, and code will be made publicly available.

## Risk / unsupported claims
- The claim that SeqSol correctly identified experimentally validated solubility-enhancing mutations from diverse proteins is unsupported in the abstract, as no specific examples or references are provided.
- The claim that the framework minimizes the risk of activity loss is not directly supported by the abstract, as only a general statement about maintaining specific activities is made without numerical evidence.
- The reported accuracy and AUC values cannot be evaluated without details on the test set construction and evaluation protocol.
- The claim that only 30 mutations were needed for the two enzymes is striking but cannot be assessed without information on how these 30 mutations were distributed between the two enzymes and how the selection was made.
- The generalizability of the framework to other proteins and expression systems is not addressed and cannot be inferred from the abstract.