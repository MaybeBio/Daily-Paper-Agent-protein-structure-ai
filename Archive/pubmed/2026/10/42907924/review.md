## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors use a protein language model-based algorithm (MAAPE) to infer evolutionary relationships between bacterial aromatic polyketide ketosynthases (KS) and chain length factors (CLF), proposing a common ancestral cluster (Cluster A), distinct evolutionary trajectories, coevolution, and horizontal gene transfer as major drivers of diversification.
- **Visible evidence base** Main text figures (Fig. 1a-c, Fig. 2a-e, Fig. 3a-b, Fig. 4a-b), supplementary tables S1-S9, supplementary figures S1-S3, methods descriptions
- **Missing materials affecting confidence** Supplementary files (Tables S1-S9, Figs. S1-S3) were not provided for inspection; raw data, code, and MAAPE algorithm implementation details are not accessible; statistical validation metrics for clustering and network analyses are not fully described

## Reviewer

- **Overall assessment** The manuscript presents a novel application of protein language model embeddings to study the evolution of type II polyketide synthases, a topic of considerable interest in natural product biosynthesis. The central claim of a common ancestral cluster and subsequent functional divergence is plausible and consistent with prior hypotheses, but the evidence provided in the main text is largely descriptive and lacks rigorous statistical validation. The MAAPE algorithm is not described in sufficient detail to assess its reliability, and the absence of supplementary data prevents verification of key results. The biological interpretations, while reasonable, are often speculative and not directly supported by the presented analyses. The manuscript has potential but requires substantial strengthening of the analytical framework and evidence base before the conclusions can be considered established.

- **Who would be interested in the results, and why** Researchers in natural product biosynthesis, enzymology, and evolutionary biology would find this work relevant. The application of protein language models to evolutionary inference is a growing area, and the specific focus on type II polyketide synthases connects to efforts in genome mining and rational engineering of polyketide pathways. The proposed coevolution and HGT hypotheses could inform experimental design for pathway engineering, making the work of interest to both fundamental and applied microbiologists.

- **Major strengths**
  1. The use of a protein language model (ESM-2) to capture evolutionary signals beyond traditional sequence alignment is a timely and potentially powerful approach.
  2. The identification of a mixed KS-CLF cluster (Cluster A) as a putative ancestral group is an interesting observation that challenges purely sequence-based phylogenies.
  3. The integration of functional prediction (DeepFRI) with embedding-based clustering provides a multi-layered perspective on protein evolution.
  4. The manuscript is clearly written and the figures are visually informative, aiding comprehension of complex network analyses.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The MAAPE algorithm reliably reconstructs evolutionary trajectories and identifies ancestral states from protein embeddings.
- **Evidence pointer** Methods section "MAAPE analysis", Fig. 2a-c
- **Concern** The MAAPE algorithm is described only at a conceptual level. The sliding window approach, co-occurrence matrix construction, and directionality assignment are not specified with enough detail to evaluate their validity or reproducibility. No benchmarks, simulations, or comparisons against known evolutionary scenarios are provided to demonstrate that the method accurately recovers true evolutionary relationships. The absence of statistical measures (e.g., bootstrap support, confidence intervals) for the inferred network topology is a critical gap.
- **Why it matters** The central conclusions of the paper rest entirely on the reliability of MAAPE. Without validation, the inferred ancestral cluster and evolutionary trajectories could be artifacts of the embedding space or the algorithm's parameters. Readers cannot assess whether the method distinguishes genuine phylogenetic signal from noise.
- **Resolution test** Provide a detailed algorithmic description, release code, and validate MAAPE on simulated datasets with known evolutionary histories or on empirical datasets with well-established phylogenies. Include statistical support values for the network edges and cluster assignments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** Cluster A represents a shared ancestral group for KS and CLF sequences, supporting a common origin.
- **Evidence pointer** Fig. 1b, Fig. 2a, Additional file 1: Table S2
- **Concern** The designation of Cluster A as ancestral is based on its mixed composition and the presence of the FABF outgroup. However, the criteria for defining "ancestral" are not explicitly stated. The cluster contains only 22 of 166 pairs, and the authors acknowledge potential biases in their product-focused dataset. The possibility that Cluster A reflects convergent sequence features or artifacts of the embedding reduction is not excluded. The claim of common ancestry requires independent support, such as phylogenetic analysis of the cluster members or structural evidence.
- **Why it matters** The common origin hypothesis is a key conclusion and a foundation for subsequent interpretations of coevolution and HGT. If Cluster A is not truly ancestral, the evolutionary narrative collapses.
- **Resolution test** Perform a rigorous phylogenetic analysis of Cluster A members using multiple methods and models. Test whether the cluster is robust to dataset composition (e.g., including non-product-associated sequences). Provide explicit criteria for ancestral state inference and rule out alternative explanations such as convergence or long-branch attraction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Coevolution between KS and CLF pairs is demonstrated by the ratio of distances to the ancestral node being close to 1.
- **Evidence pointer** Fig. 2d, Additional file 1: Table S9
- **Concern** The distance ratio analysis is presented as evidence of coevolution, but the statistical framework is unclear. The mean ratio of 1.0082 is reported without a measure of variance, a null model, or a test of significance. The six outlier pairs are identified but not analyzed in detail. The choice of the ancestral node as the centroid of Cluster A embeddings is arbitrary and may bias the results. Coevolution is a strong claim that requires more direct evidence, such as correlated mutation analysis or functional assays.
- **Why it matters** Coevolution is a central biological interpretation. If the distance ratio is not a valid proxy, the claim is unsupported. Overinterpretation of a descriptive metric as evidence of coevolution could mislead readers.
- **Resolution test** Provide a statistical test comparing the observed distance ratios to a null distribution (e.g., randomized pairings). Report confidence intervals and effect sizes. Use complementary methods (e.g., coevolutionary analysis of residue contacts) to corroborate the finding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** Horizontal gene transfer is a main driving force of KS/CLF polymorphism.
- **Evidence pointer** Fig. 4a-b, Discussion section
- **Concern** The inference of HGT is based on network edge weights and directionality, but no direct evidence of HGT (e.g., phylogenetic incongruence, GC content analysis, or taxonomic distribution) is presented. The interpretation of high-weight edges as HGT events is speculative. The authors do not account for alternative explanations such as gene duplication, loss, or convergent evolution. The claim that HGT is a "main" driving force is not quantitatively supported.
- **Why it matters** HGT is a major evolutionary mechanism, and attributing KS/CLF diversity to it has implications for understanding pathway evolution. An unsupported claim could lead to incorrect conclusions about the mobility and distribution of these biosynthetic genes.
- **Resolution test** Conduct explicit HGT detection analyses (e.g., phylogenetic reconciliation, sequence composition bias tests). Quantify the contribution of HGT relative to other mechanisms. Provide species-level context to support the HGT interpretation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The dataset of 166 KS-CLF pairs is comprehensive and curated.
- **Evidence pointer** Methods section "Data collection and phylogenetic analysis", Additional file 1: Table S1
- **Concern** The curation criteria are described briefly, but the source databases, search terms, and filtering steps are not fully specified. The exclusion of sequences with >90% identity is mentioned, but the impact of this threshold on diversity and representation is not discussed. The supplementary table containing the dataset was not available for review.
- **Why it matters** Reproducibility is a core requirement. Without a complete description of data acquisition and processing, other researchers cannot replicate the study or assess potential biases.
- **Resolution test** Provide a detailed data curation protocol, including database versions, accession numbers, and filtering criteria. Make the full dataset publicly available in a standard format.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 2a description
- **Evidence pointer** Fig. 2a
- **Issue** The figure caption states that only the top 10 highest-weighted edges from FAB to KS/CLF clusters and the top 5 between KS and CLF clusters are displayed. The rationale for these thresholds is not explained.
- **Required correction** Justify the edge display thresholds or state that they are for visual clarity only.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 2d
- **Evidence pointer** Fig. 2d
- **Issue** The distance ratio plot lacks error bars or a measure of dispersion. The reader cannot assess the variability of the ratios.
- **Required correction** Add error bars or a confidence band to the plot and report the standard deviation or interquartile range in the text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The term "Grammar of Life" is used without definition and may be confusing to readers unfamiliar with the concept.
- **Required correction** Define the term or replace it with a more standard phrase such as "sequence-encoded evolutionary information."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Functional prediction"
- **Evidence pointer** Methods section "Functional prediction"
- **Issue** The DeepFRI analysis is described, but the specific GO terms used for the vectorization are not listed. The dimensionality of the functional vectors is not stated.
- **Required correction** Provide a list of the GO terms included and the number of dimensions in the functional vectors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 3b
- **Evidence pointer** Fig. 3b
- **Issue** The heatmap shows functional similarities, but the biological significance of the observed similarity values is not discussed. A similarity of 0.5 is mentioned as "comparable," but the scale is not defined.
- **Required correction** Explain the range and meaning of the cosine similarity values and interpret the observed values in a biological context.

## Risk / unsupported claims
- The claim that Cluster A represents a shared ancestral group is not statistically validated and may be influenced by dataset composition.
- The inference of coevolution from distance ratios lacks a formal statistical framework and alternative explanations are not excluded.
- The assertion that HGT is a main driving force of KS/CLF polymorphism is speculative and not supported by direct HGT detection analyses.
- The functional convergence between nonoxidative CLFs and KSs is inferred from similarity scores without experimental validation.
- The general statement that PLM embeddings capture evolutionary information beyond sequence alignment is plausible but not rigorously demonstrated in this study.
- The biological interpretations regarding selective pressures (chemical competition, ecological niches, metabolic trade-offs) are presented as conclusions but are not directly tested.