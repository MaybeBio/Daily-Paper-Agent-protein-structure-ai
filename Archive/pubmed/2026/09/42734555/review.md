## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose SA-MPNN, a hybrid framework integrating ESM2 sequence representations into the ThermoMPNN architecture via a self-attention fusion mechanism, trained on Megascale, and report modest but consistent improvements over ThermoMPNN across benchmark datasets, with wet-lab validation on AtBgl1A showing a top variant with a 5.97 °C Tm increase over wild-type.
- **Visible evidence base** Abstract text only; no quantitative benchmark results, no architecture details, no experimental protocols, no statistical analyses are provided
- **Missing materials affecting confidence** Full methods, all benchmark tables and figures, training and evaluation details, wet-lab experimental procedures, statistical significance tests, and any code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful engineering contribution, namely the integration of evolutionary sequence information into a structure-based inverse folding model for stability prediction. The motivation is clear and the choice of a lightweight hybrid approach is sensible. However, the abstract provides no quantitative evidence for the claimed improvements, no details on the fusion mechanism or training regime, and only a single case-study wet-lab result without error bars or replicates. As it stands, the core claims of consistent gains over ThermoMPNN and practical applicability are not established from the supplied material.
- **Who would be interested in the results, and why** Computational protein engineers and developers of stability prediction tools would be interested, as the work addresses a practical bottleneck in therapeutic and industrial protein engineering. Researchers working on inverse folding models and protein language model integration would also find the architectural approach relevant. The wet-lab validation on a beta-glucosidase adds applied value for biocatalysis-focused groups.
- **Major strengths** The problem is well-motivated and practically important. The proposed approach of combining pLM representations with geometric structural embeddings is conceptually sound and addresses a recognized limitation of IFMs. The inclusion of wet-lab validation, even as a case study, is a strength that goes beyond purely computational benchmarking.
- **Major Concerns** The abstract lacks all quantitative benchmark data, making the claimed improvements impossible to evaluate. The wet-lab result is presented without experimental detail or statistical context. The novelty relative to existing hybrid approaches is not articulated.
- **Minor Comments** The abstract would benefit from stating the number of parameters in the "lightweight" model, the size of the Megascale training set used, and the specific benchmark datasets and metrics. The phrase "modest but consistent gains" is vague and should be replaced with actual numbers. The wet-lab section should mention the number of variants tested and the measurement error of the Tm assay.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: moderate; the combination of ESM2 with ThermoMPNN is incremental over existing fine-tuned IFM approaches. Scientific importance: moderate to high for the protein engineering community, but the advance appears incremental. Interdisciplinary readership: limited; the work is primarily of interest to computational biologists and protein engineers. Technical soundness: not assessable from the abstract alone; no methodological or statistical detail is provided. Readability for nonspecialists: the abstract is accessible but relies on domain-specific terms (IFM, pLM, Tm) without brief definitions.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require full quantitative results and methodological detail to be evaluated. A revised manuscript with complete benchmark data and experimental protocols could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "SA-MPNN achieved modest but consistent gains over ThermoMPNN on various benchmark data sets"
- **Evidence pointer** Abstract; location not provided
- **Concern** No quantitative results are reported. The abstract does not state any performance metrics, dataset names, effect sizes, or statistical significance for the claimed improvements over ThermoMPNN.
- **Why it matters** The central claim of the paper is that SA-MPNN outperforms ThermoMPNN. Without any numbers, this claim cannot be verified, and the magnitude and consistency of the gains remain unknown.
- **Resolution test** Provide benchmark tables with metrics (e.g., Spearman correlation, AUC, RMSE) for all datasets, including baseline ThermoMPNN values, with confidence intervals or significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "a self-attention-based integration mechanism to effectively combine the two modalities"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract states that various fusion strategies were evaluated and self-attention was selected, but no details are given on the alternatives, the selection criteria, or the architecture of the fusion module.
- **Why it matters** The fusion mechanism is the core methodological contribution. Without details, readers cannot assess its novelty, reproduce the work, or understand why it outperforms simpler alternatives.
- **Resolution test** Describe the fusion module architecture, the alternative strategies tested, and the quantitative comparison that motivated the final choice.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental rigor
- **Claim pointer** "the optimal variant, GC20, achieved a melting temperature (Tm) of 76.98 degrees C, representing a 5.97 degrees C increase over the wild-type"
- **Evidence pointer** Abstract; location not provided
- **Concern** The wet-lab validation is reported as a single Tm value with no indication of replicates, measurement error, or the number of variants tested. The selection process for the "top-ranking variants" is not described.
- **Why it matters** A single measurement without error bars cannot support a claim of improved thermostability. The practical applicability claim rests on this result, so it must be statistically robust.
- **Resolution test** Report the number of variants tested, the number of replicates per measurement, the standard deviation or error of the Tm assay, and a statistical comparison between GC20 and wild-type.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model description
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "lightweight" is used without any parameter count or computational cost comparison.
- **Required correction** State the number of parameters or inference time relative to ThermoMPNN.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Training data
- **Evidence pointer** Abstract; location not provided
- **Issue** The Megascale dataset is mentioned but its size and composition are not specified.
- **Required correction** Provide the number of mutations and proteins in the training set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** Terms such as IFM, pLM, and Tm are used without definition, which may hinder nonspecialist readers.
- **Required correction** Define these terms at first use or provide a brief glossary.

## Risk / unsupported claims
- The claim of "modest but consistent gains" over ThermoMPNN is unsupported by any quantitative data in the abstract.
- The claim that self-attention is the "effective" fusion mechanism is unsupported without comparison data.
- The wet-lab result for GC20 is presented as a single value without error or replicates, making the claim of improved thermostability unverifiable.
- The general statement that SA-MPNN supports "practical applicability in protein engineering" is not established from a single case study.