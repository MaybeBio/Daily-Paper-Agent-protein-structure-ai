## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion, supplementary figure legends, funding, data availability)
- **Assessment boundary** Scientific content, technical soundness, methodological rigor, claims-to-evidence alignment, and clarity of the presented work. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The authors present ecCLIP, a high-throughput CLIP-seq platform combining endogenous split-mNeonGreen tagging with ligation-free library preparation, applied to 67 RBPs in HEK293T cells. They introduce Borzuki, a Borzoi-derived model incorporating ecCLIP data for improved RNA half-life and 3' UTR variant effect prediction, and Pythia, a structure-aware neural network with a fixed dilated convolutional layer encoding base-pairing features. Pythia is benchmarked on BEACON tasks and used to predict and experimentally validate (via MPRC) sequence- and structure-dependent RBP binding determinants, including allele-specific effects of trait-associated variants.
- **Visible evidence base** Main figures (Fig. 1a-c, 2a-i, 3a-e, 4a-d, 5a-e), supplementary figures (S1a-j, S2a-i, S3a-g, S4a-g, S5a-b), methods sections 4.1-4.19, data availability statements
- **Missing materials affecting confidence** Full figure panels and legends not provided; exact numerical values for many reported statistics not visible; complete details of MPRC library design and variant selection not fully specified; details of Borzuki training data composition and hyperparameter tuning not fully described; no information on replicate numbers for MPRC experiments beyond "two biological replicates"

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious resource: a high-throughput RBP binding atlas generated with a new experimental platform (ecCLIP), integrated into two complementary modeling frameworks (Borzuki for RNA fate prediction, Pythia for structure-aware binding prediction). The work is technically impressive and the combination of experimental atlas generation, deep learning modeling, and experimental validation via MPRC is commendable. However, several technical concerns and gaps in evidence presentation limit the strength of the claims as currently written. The manuscript would benefit from clearer reporting of validation statistics, more rigorous benchmarking against existing methods, and additional evidence that the structure-aware component of Pythia provides unique predictive value beyond sequence-based models.
- **Who would be interested in the results, and why** Researchers in RNA biology, post-transcriptional gene regulation, computational biology, and deep learning for genomics. The ecCLIP atlas provides a new resource for RBP binding sites in a common cell line. The Borzuki and Pythia models offer tools for predicting RNA stability and RBP binding from sequence, with potential applications in variant interpretation. The MPRC validation framework is a methodological contribution for testing structure-dependent binding hypotheses.
- **Major strengths** 1) The ecCLIP platform addresses real limitations in existing CLIP protocols (antibody dependence, ligation bias) through endogenous tagging and ligation-free library preparation. 2) The scale of the atlas (67 RBPs) is a significant resource. 3) The integration of experimental data with deep learning models (Borzuki, Pythia) is a forward-looking approach. 4) The MPRC validation provides direct experimental evidence for model predictions, which is rare in this field. 5) The BEACON benchmarking provides standardized comparison against existing methods.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (negative control adequacy), R1-M2 (MPRC validation statistics), R1-M3 (Borzuki ablation interpretation), R1-M4 (Pythia structure arm contribution), R1-M5 (variant effect validation scope)
- **Assessment against Nature-style criteria** **Originality:** High. The combination of endogenous tagging CLIP with structure-aware deep learning and MPRC validation is novel. **Scientific importance:** Potentially high, if the resource and models prove broadly useful. The atlas and models could enable new insights into post-transcriptional regulation. **Interdisciplinary readership:** Moderate to high. The work bridges experimental RNA biology, computational genomics, and deep learning. **Technical soundness:** Mixed. The experimental platform appears well-designed, but several validation and benchmarking aspects need strengthening (see Major Concerns). **Readability for nonspecialists:** The abstract and introduction are accessible, but the methods and results sections assume significant expertise in both CLIP-seq and deep learning. Some concepts (e.g., fixed dilated convolutions, Borzoi architecture) could be explained more clearly for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core resource and modeling framework are valuable, but the current evidence does not fully establish all claims, particularly regarding the unique contribution of the structure-aware component and the robustness of the MPRC validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design / controls
- **Claim pointer** "We applied ecCLIP to 67 endogenously tagged RBPs in HEK293T cells, generating a high-quality transcriptome-scale atlas that recovered known binding preferences and captured post-transcriptional regulons linked to RNA half-life."
- **Evidence pointer** Section 2.1, Fig. 1, Supp. Fig. S1
- **Concern** The manuscript does not describe a rigorous negative control for the ecCLIP protocol. The authors mention a "tag-only negative-control BED set" in Section 4.5, but no details are provided on how this control was generated, whether it was a non-RBP mNeonGreen-tagged protein, a parental cell line, or an untagged control. Without a proper negative control, it is difficult to assess the specificity of the peaks called and the false discovery rate of the atlas.
- **Why it matters** The entire atlas and all downstream modeling depend on the quality and specificity of the called peaks. If the negative control is inadequate, the atlas may contain a substantial number of false positives, which would propagate through Borzuki and Pythia training and validation.
- **Resolution test** Provide a detailed description of the negative control, including the cell line, the tag construct, and the processing pipeline. Show that the negative control produces significantly fewer peaks than the tagged RBPs, and ideally demonstrate that known non-RBP proteins do not produce peaks. Report the number of peaks called in the negative control and the FDR threshold used.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation / experimental evidence
- **Claim pointer** "MPRC confirmed that Pythia-nominated structural features correspond to functional determinants of RBP binding. Among sites predicted by Pythia to be structure-dependent, structure-preserving reporters were closer to the reference than structure-disrupting reporters at all 11 reference-enriched sites, using the same number of mutations in both conditions (one-sided paired Wilcoxon P = 4.9 × 10 −4 ; Fig. 4c )."
- **Evidence pointer** Section 2.5, Fig. 4c, Supp. Fig. S4
- **Concern** The MPRC validation is based on a small number of sites (11 reference-enriched structure-dependent sites, 8 non-structure-dependent sites). The statistical test is a paired Wilcoxon test across sites, but the number of sites is very small. Additionally, the manuscript does not report effect sizes or confidence intervals for the differences between structure-preserving and structure-disrupting constructs. The binomial logistic regression analysis is mentioned but the results are not fully reported. The choice of the 0.25 log2(IP/input) threshold for "reference-enriched" is not justified.
- **Why it matters** The MPRC validation is the key experimental evidence supporting the central claim that Pythia's structure-aware predictions are biologically meaningful. With such a small number of sites and incomplete statistical reporting, the robustness of this conclusion is uncertain.
- **Resolution test** Report the full results of the logistic regression analysis, including coefficients, standard errors, and p-values for each site. Provide effect sizes (e.g., Cohen's d) and confidence intervals for the differences between construct types. Justify the choice of the reference-enrichment threshold. Consider increasing the number of validated sites or providing a power analysis to show the study is adequately powered.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model evaluation / ablation interpretation
- **Claim pointer** "In matched ablations, adding ecCLIP data improved prediction of RNA half-life and of MPRA-measured 3 ′ UTR variant effects on RNA stability, showing that the ecCLIP atlas carries regulatory information about RNA fate that existing data does not."
- **Evidence pointer** Section 2.2, Fig. 2e, Supp. Fig. S2
- **Concern** The ablation study shows that adding ecCLIP data improves performance, but the manuscript does not clearly describe what "matched ablations" means. Were the models trained with the same architecture and hyperparameters, differing only in the input data? How many replicates of the ablation were performed? The improvement in performance is reported but the magnitude of the improvement and its statistical significance are not clearly stated. Furthermore, the claim that ecCLIP provides information "that existing data does not" is strong and requires a more detailed comparison of the types of information captured by ecCLIP versus ENCODE eCLIP.
- **Why it matters** The claim that ecCLIP adds unique predictive value is central to the paper's contribution. Without clear ablation methodology and statistical reporting, this claim is not fully supported.
- **Resolution test** Provide a detailed description of the ablation methodology, including model architecture, hyperparameters, and training procedure. Report the performance metrics for each ablation with confidence intervals and statistical tests. Perform an analysis of the types of binding sites uniquely captured by ecCLIP versus ENCODE eCLIP (e.g., in terms of sequence features, structural context, or genomic location).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Model architecture / contribution of structure component
- **Claim pointer** "Pythia predicted RBP binding from sequence and structural context and decomposed predictions into sequence-and structure-dependent components."
- **Evidence pointer** Section 2.3, Fig. 3, Supp. Fig. S3
- **Concern** The manuscript does not provide a clear ablation of the Pythia architecture itself. Specifically, it is not shown that the structure-aware component (the fixed dilated convolutional layer) contributes to improved performance over a sequence-only version of Pythia. The comparison against BEACON baselines is informative, but these baselines may not be directly comparable in terms of training data and architecture. A direct ablation of Pythia with and without the structure arm would more directly support the claim that structure-aware modeling is beneficial.
- **Why it matters** The central novelty of Pythia is its explicit structure-aware architecture. Without a direct ablation, it is unclear whether the structure component provides unique predictive value or whether the performance is driven primarily by the sequence component.
- **Resolution test** Train a version of Pythia with only the sequence arm (no structure arm) and compare its performance to the full Pythia on the RBP binding prediction task. Report the performance difference and its statistical significance. This ablation should be performed for all 67 RBPs.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Variant effect validation / clinical relevance
- **Claim pointer** "We used the same MPRC strategy to confirm allele-specific binding effects for variants prioritized by Pythia."
- **Evidence pointer** Section 2.6, Fig. 5, Supp. Fig. S5
- **Concern** The manuscript reports that 24 of 88 tested RBP-variant pairs showed significant allele-specific binding, but the criteria for "significant" are not fully described. The correlation between predicted and observed effects is modest (Pearson r = 0.33). The manuscript does not report how many variants were prioritized by Pythia and how many were tested. The selection of variants for testing is not described in detail. The trait annotations for the highlighted variants are presented as "hypotheses for follow-up," but the manuscript does not discuss potential confounding factors or alternative explanations for the observed allele-specific effects.
- **Why it matters** The variant effect prediction is a key translational application of the work. The modest correlation and incomplete reporting of the validation strategy limit the strength of the claims about Pythia's utility for variant interpretation.
- **Resolution test** Provide a detailed description of the variant selection process, including the number of variants prioritized by Pythia, the criteria for selection, and the number tested. Report the full results of the MPRC experiments, including effect sizes and confidence intervals for each variant. Discuss potential confounding factors (e.g., linkage disequilibrium, cell-type specificity) and how they were addressed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / terminology
- **Affected element** Section 2.1, Fig. 1
- **Evidence pointer** "eclair CLIP (ecCLIP)"
- **Issue** The name "eclair CLIP" is used without explanation of the acronym. It is unclear what "eclair" stands for.
- **Required correction** Provide a brief explanation of the name, e.g., "efficient, clonal, and rapid" or similar, or state that it is a coined name.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility / data availability
- **Affected element** Section 4.5, Data availability
- **Evidence pointer** "All raw and processed sequencing data are available from the Gene Expression Omnibus (GEO) under accession number GSE349934."
- **Issue** The manuscript states that data are available, but the specific GEO accession is only mentioned in the Data availability section. It would be helpful to also include the accession number in the main text or figure legends where the data are first described.
- **Required correction** Include the GEO accession number in the main text (e.g., in Section 2.1) or in the relevant figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.2, Fig. 2
- **Evidence pointer** "In matched ablations, adding ecCLIP data improved prediction of RNA half-life"
- **Issue** The manuscript reports improvements in prediction but does not provide the actual performance metrics (e.g., correlation coefficients, MSE) for the models with and without ecCLIP data. The magnitude of the improvement is not quantified.
- **Required correction** Report the specific performance metrics for each ablation condition, with confidence intervals and p-values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / methodology
- **Affected element** Section 4.12, Pythia model
- **Evidence pointer** "The fixed layer enumerates candidate Watson-Crick and wobble base-pairing rules across a range of distances and bulge configurations."
- **Issue** The description of the fixed dilated convolutional layer is brief. It is unclear how the "bulge configurations" are parameterized and how the layer handles gaps or bulges in RNA duplexes.
- **Required correction** Provide a more detailed description of the fixed layer, including the exact kernel design, the range of dilation rates, and how bulges are handled. A supplementary figure or table showing the kernel configurations would be helpful.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation / discussion
- **Affected element** Section 3, Discussion
- **Evidence pointer** "The atlas was generated in HEK293T cells, so extending ecCLIP across cell types, cell perturbations, and disease contexts will be important for modeling context-specific regulation."
- **Issue** The discussion of limitations is brief. The authors could more thoroughly discuss the potential impact of cell-type specificity on the generalizability of the atlas and models, and how the MPRC validation in HEK293T cells might not fully capture in vivo binding behavior.
- **Required correction** Expand the discussion of limitations, including a more detailed consideration of cell-type specificity, potential artifacts from endogenous tagging, and the limitations of the MPRC reporter system.

## Risk / unsupported claims
- The claim that ecCLIP provides information "that existing data does not" is not fully supported without a more detailed comparison of the types of information captured by ecCLIP versus ENCODE eCLIP.
- The claim that Pythia's structure-aware component provides unique predictive value is not supported without a direct ablation of the Pythia architecture.
- The claim that MPRC "confirmed" Pythia's predictions is strong; the modest correlation (r = 0.33) and small number of validated sites suggest the confirmation is partial.
- The claim that the highlighted trait-associated variants "nominate local RNA-processing hypotheses" is speculative and not directly tested in the manuscript.
- The generalizability of the atlas and models to other cell types and conditions is not established, and the discussion of this limitation is brief.