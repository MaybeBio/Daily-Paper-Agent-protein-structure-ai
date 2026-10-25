## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and methods as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose a sequence-only deep learning pipeline for predicting HER2 epitopes and VHH nanobody paratopes, using a frozen ESM2 650M model as a feature extractor and a lightweight trainable module with cross-attention. Training uses three public data sources, including a competition assay dataset ("AVIDa hHER2") that is not yet public. A structure-derived residue prior is introduced for HER2-specific epitope prediction. The authors report high performance on binder classification (PR AUC 0.999) and moderate paratope prediction (PR AUC 0.659), while acknowledging near-baseline performance for epitope prediction on novel antigens (PR AUC 0.070). A leakage-safe evaluation protocol is emphasized.
- **Visible evidence base** Abstract text only; no figures, tables, code, or dataset documentation provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset access details, model architecture specifics, hyperparameters, training/validation split details, and the "AVIDa hHER2" dataset itself (not yet public)

## Reviewer
- **Overall assessment** The abstract presents a technically plausible approach to a challenging problem in antibody engineering, with a commendable emphasis on leakage-safe evaluation. However, the evidence base is limited to the abstract, and several claims cannot be verified without the full manuscript. The reported performance numbers are inconsistent in their implications, and the near-baseline epitope prediction result, while honestly reported, raises questions about the practical utility of the method. The reliance on a not-yet-public dataset for a central training signal is a significant concern for reproducibility.
- **Who would be interested in the results, and why** Researchers and practitioners in therapeutic antibody engineering, computational immunology, and protein language model applications. The focus on HER2, a clinically relevant target, and the sequence-only formulation would appeal to those seeking to avoid costly structure prediction steps. The leakage-safe evaluation protocol would interest methodologists in the field.
- **Major strengths** The explicit commitment to leakage-safe evaluation with a sealed test set opened once is a notable strength. The honest reporting of a near-baseline result for novel antigen epitope prediction is commendable. The use of a frozen protein language model as a feature extractor with a lightweight trainable head is a sensible design choice for computational efficiency.
- **Major Concerns** The central training dataset is not public, undermining reproducibility. The performance numbers are difficult to interpret without context, and the relationship between the competition-derived domain signal and the residue-level predictions is unclear. The abstract does not provide sufficient detail on the cross-attention mechanism or the residue prior construction to assess technical soundness.
- **Minor Comments** The abstract is dense and would benefit from clearer separation of the different prediction tasks. The claim of "leakage free" for the 87.7% domain recovery result needs more precise definition. The release of "two submission variants" per test clone is mentioned but not explained in terms of how they are reconciled.
- **Technical failings that need to be addressed before the case is established** The unavailability of the "AVIDa hHER2" dataset is a primary technical failing for reproducibility. The lack of detail on the residue prior and its validation is a secondary concern.
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of a frozen ESM2 with a structure-derived prior is not entirely novel, but the specific application to VHH nanobodies on HER2 with a leakage-safe protocol has some originality. Scientific importance: Moderate. The problem is important, but the near-baseline epitope result limits the immediate impact. Interdisciplinary readership: Limited. The abstract is highly specialized and would not attract a broad readership. Technical soundness: Not fully assessable from the abstract; the evaluation protocol is a strength, but the dataset issue is a weakness. Readability for nonspecialists: Poor. The abstract is dense and assumes significant background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract shows promise, but the dataset availability issue and the lack of methodological detail prevent a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The model is trained on "AVIDa hHER2" competition assay data, which is stated to be "to be published" and the authors "have no right to share."
- **Evidence pointer** Abstract, "Training data" section (location not provided)
- **Concern** The central training signal for the binder head and the competition-derived domain contrast relies on a dataset that is not publicly available and cannot be shared by the authors. This makes the reported results, particularly the PR AUC 0.999 for the binder head, impossible to reproduce or independently verify.
- **Why it matters** Reproducibility is a cornerstone of scientific validity. Without access to the training data, other researchers cannot validate the method, compare against it, or build upon it. This is a fundamental barrier to the manuscript's contribution.
- **Resolution test** The authors must provide a clear plan for making the "AVIDa hHER2" dataset available, either through the SEPIQ 2026 organizers or through a controlled access mechanism, before the results can be considered reproducible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The residue-level epitope prediction on novel antigens is reported as near baseline (PR AUC 0.070), while the structure-derived residue prior reaches 0.26 to 0.29 once the domain is correct.
- **Evidence pointer** Abstract, "Results" section (location not provided)
- **Concern** The abstract reports a near-baseline performance for the primary task of epitope prediction on novel antigens. The improvement from the residue prior is conditional on the domain being correct, which itself is only correct for 87.7% of held-out clones. The abstract does not clarify how these numbers combine to give an overall performance estimate for the full pipeline on a novel HER2 antibody.
- **Why it matters** The central claim of the manuscript is the utility of the sequence-only approach. If the epitope prediction is near baseline for novel antigens, the practical value of the method is severely limited, and the conditional improvement from the prior may not translate to real-world use.
- **Resolution test** The authors should provide an end-to-end performance estimate for the full pipeline on a held-out set of HER2 antibodies, combining the domain classification accuracy with the residue-level prediction performance, to demonstrate the overall utility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The model uses a "structure-derived residue prior" built from 25 mined HER2 antibody complexes and validated by leave-one-out.
- **Evidence pointer** Abstract, "Methods" section (location not provided)
- **Concern** The abstract does not describe how the residue prior is constructed, how it is integrated with the language model features, or what the leave-one-out validation entails. The improvement from 0.070 to 0.26-0.29 is substantial, but without methodological detail, it is unclear whether this prior is generalizable or overfit to the 25 complexes.
- **Why it matters** The residue prior is a key component of the claimed performance improvement. Without understanding its construction and validation, the technical soundness of the approach cannot be assessed.
- **Resolution test** The full manuscript must provide a detailed description of the residue prior construction, its integration into the model, and the leave-one-out validation results, including error bars and a comparison to a non-informative prior.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract structure
- **Evidence pointer** Abstract (location not provided)
- **Issue** The abstract mixes multiple prediction tasks (binder classification, paratope prediction, epitope prediction, domain classification) without clearly separating their definitions, evaluation metrics, and results.
- **Required correction** Restructure the abstract to clearly delineate each task, its input/output, and its performance metric, possibly in a table or bulleted format.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Leakage free" claim
- **Evidence pointer** Abstract, "Results" section (location not provided)
- **Issue** The claim of "leakage free" for the 87.7% domain recovery result is not defined. It is unclear what leakage was tested for and how it was prevented.
- **Required correction** Provide a precise definition of the leakage considered and the measures taken to prevent it, such as sequence clustering thresholds and test set construction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** "Two submission variants"
- **Evidence pointer** Abstract, "Results" section (location not provided)
- **Issue** The abstract mentions releasing "two submission variants per test clone" but does not explain the difference between them or how they are evaluated.
- **Required correction** Clarify the nature of the two variants and whether the reported performance numbers correspond to one or both.

## Risk / unsupported claims
- The claim of "leakage free" for the 87.7% domain recovery result is unsupported without a definition of the leakage tested.
- The overall utility of the method is unsupported because the near-baseline epitope prediction (PR AUC 0.070) is not reconciled with the conditional improvement from the residue prior.
- The reproducibility of all results is unsupported due to the unavailability of the "AVIDa hHER2" dataset.
- The technical soundness of the residue prior is unsupported without methodological detail.