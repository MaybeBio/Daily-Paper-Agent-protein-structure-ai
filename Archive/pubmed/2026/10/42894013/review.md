## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as presented in the provided manuscript text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors present Rider, a two-stage deep learning framework for RNA virus discovery from metatranscriptomes. Stage 1 uses a frozen ESM2 protein language model with a Transformer classifier for sequence-based screening; Stage 2 employs sliding-window structure prediction and alignment against a curated RdRp domain database (RDSDB) for structural validation. The authors claim superior sensitivity for divergent and fragmented viral sequences compared to existing tools, scalability to >10,000 metatranscriptomes, and application to an IBD cohort revealing previously missed viral diversity.
- **Visible evidence base** Figures 1–5, Supplementary Figures S1–S7, Supplementary Datasets 1–16, and methods text. Performance metrics (AUC, TPR, FPR), benchmark comparisons, case studies, and phylogenetic analyses are described.
- **Missing materials affecting confidence** Code availability, trained model weights, exact hyperparameters, full benchmark result tables, and detailed statistical outputs are not provided in the manuscript text. The actual RDSDB contents and the complete list of 10,000+ metatranscriptome accessions are not enumerated.

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated and potentially valuable framework for RNA virus discovery. The two-stage design, combining a frozen protein language model with structural validation, is a logical and innovative response to known limitations in sequence-based viral detection. The benchmarking against multiple baselines and the application to real-world datasets are commendable. However, several methodological details and validation aspects require clarification and strengthening before the claims can be fully accepted. The reliance on structural validation as a gold standard, the handling of false positives, and the interpretation of the IBD cohort results are areas of particular concern.
- **Who would be interested in the results, and why** Virologists, metagenomics and metatranscriptomics researchers, computational biologists developing tools for pathogen discovery, and researchers studying the human microbiome, particularly in the context of inflammatory bowel disease. The framework's scalability and sensitivity for divergent viruses would be of broad interest to the global virosphere discovery community.
- **Major strengths**
  - The two-stage architecture is a well-reasoned and practical solution to the dual challenges of sequence divergence and length heterogeneity.
  - The use of a frozen, compact ESM2 model with a lightweight trainable head is computationally efficient and scalable, a significant practical advantage.
  - The construction of a domain-specific structural database (RDSDB) and the use of structural alignment for validation is a rigorous approach that goes beyond sequence-based homology.
  - The extensive benchmarking against multiple baseline methods and on diverse datasets, including short fragments and long polyproteins, is thorough.
  - The application to a clinical cohort (IBD) demonstrates real-world utility and provides a compelling case study for the framework's ability to uncover previously missed viral diversity.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Validation
- **Claim pointer** The claim that Rider's structural validation (Stage 2) provides a "rigorous" and "reliable" criterion for identifying true RdRp domains, effectively eliminating false positives.
- **Evidence pointer** Results section "Rider overcomes the challenges in viral identification in metatranscriptomes", specifically "Identifying remote homologs through structure validation"; Figure 3c, 3d.
- **Concern** The manuscript demonstrates that structural validation can distinguish RdRp from non-RdRp proteins in a controlled setting. However, the claim of "effectively eliminating false positives" is too strong. The analysis of the 2,294 unverified sequences (Figure 4g) shows that structural validation fails for a significant portion of highly divergent candidates, which the authors attribute to limitations of ESMFold. This means the method's final output is still dependent on the quality of the initial structure prediction. The manuscript does not provide a clear strategy for how to handle these unverified but potentially real viral sequences, other than acknowledging they are a "challenge". The paper needs to more clearly define the operational meaning of a "false positive" in this context. A sequence that fails structural validation is not necessarily a false positive; it could be a true positive that ESMFold cannot fold. The authors should provide a more nuanced discussion of this limitation and its impact on the final set of reported viruses.
- **Why it matters** The core value proposition of the two-stage framework is the combination of sensitive screening with specific validation. If the validation step is known to have a high failure rate for the most divergent sequences (the very ones of most interest), then the framework's ability to "expand RNA virus discovery" is potentially limited. The paper must be transparent about this trade-off and provide guidance on how users should interpret the unverified set.
- **Resolution test** The authors should provide a quantitative analysis of the unverified sequences. For example, how many of the 2,294 unverified sequences are found by other tools (LucaProt, PalmScan)? If a significant number are co-detected, this would suggest they are likely true positives that the structural validation step is incorrectly rejecting. The authors should also discuss potential improvements to the structural validation step, such as using multiple structure prediction models or relaxing the threshold for highly divergent sequences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Benchmarking
- **Claim pointer** The claim that Rider achieves "sensitivity comparable to LucaProt, recalling >99% of previously cataloged RNA viruses" and outperforms it on short and fragmented sequences.
- **Evidence pointer** Results section "Rider: a deep representation model for diverse RNA virus discovery", Figure 2, Supplementary Datasets 3, 4, 6.
- **Concern** The benchmarking methodology, while extensive, has a potential critical flaw. The authors state that Rider's training data includes sequences from NCBI and other sources. It is unclear if the test sets derived from LucaProt's study (e.g., the 161,979 sequences) were rigorously excluded from Rider's training data. The authors mention "Pre-training aware test sets" for the ESM2 backbone, but it is not clear if the same rigor was applied to the fine-tuning data for the Transformer classifier. If any of the test sequences or their close homologs were seen during training, the reported recall rates would be inflated. The paper must explicitly state the exact overlap between the training data and all test sets, and ideally, perform a time-based split where the training data is strictly older than the test data.
- **Why it matters** This is a fundamental issue of data leakage in machine learning. If not addressed, the reported performance metrics are not trustworthy, and the claimed superiority over other tools could be an artifact of training on the test data.
- **Resolution test** The authors must provide a detailed analysis of sequence identity between the training set and each test set. They should also retrain the model on a dataset that excludes all sequences with >30% identity to the test sets and re-report the performance metrics. This would provide a true measure of generalization.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Biological interpretation
- **Claim pointer** The claim that the IBD cohort analysis reveals that "the depletion of the gut RNA virome remains a consistent descriptive pattern of Crohn's disease" and that the apparent "viral bloom" in UC is due to underestimation of fragmented viruses in healthy controls.
- **Evidence pointer** Results section "Extending to human gut virome: insights from an IBD cohort", Figure 5b–d.
- **Concern** The biological interpretation of the IBD data is a significant leap from the computational results. The analysis is based on a small cohort (n=77 total) and the statistical analysis is performed at the contig level, not the participant level, as the authors acknowledge. The conclusion that the "viral bloom" in UC is an artifact of methodology is a strong claim that has clinical implications. The authors need to be more cautious. The difference in detected viral abundance between UC and healthy controls when using a >100 aa threshold could be due to many factors, including differences in sequencing depth, sample processing, or true biological differences in the viral community structure that are not captured by this analysis. The paper should frame this as a hypothesis-generating observation, not a definitive re-interpretation of previous findings.
- **Why it matters** Over-interpreting results from a small, exploratory computational analysis can mislead the field and have implications for how future studies are designed. The authors should temper their conclusions and clearly state the limitations of the cohort and the statistical approach.
- **Resolution test** The authors should rephrase the conclusions to be more tentative. They should also consider performing a participant-level analysis, perhaps by aggregating contig-level data per participant, to see if the trends hold. A discussion of potential confounders and the need for validation in larger, independent cohorts is essential.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The claim that the framework is "scalable" and can be applied to "global RNA virome exploration."
- **Evidence pointer** Results section "Computational efficiency and scalability across synthetic and real-world datasets", Methods section "Runtime benchmarking and computational efficiency profiling".
- **Concern** While the speed of Stage 1 is impressive, the overall scalability of the pipeline is not fully demonstrated. The "stress test" for the structural validation module (Stage 2) used a maximum sequence length of 1200 amino acids. However, the paper also discusses the challenge of "massive polyproteins" exceeding 4000 amino acids. The sliding-window strategy is designed to handle this, but the computational cost of running ESMFold on multiple windows for thousands of long polyproteins is not benchmarked. The end-to-end runtime profiling on real-world data is useful, but it is not clear how many of the sequences in those datasets were long polyproteins. The paper should provide a more detailed analysis of the computational bottleneck of Stage 2 and its scalability to truly massive datasets.
- **Why it matters** The claim of scalability is central to the paper's potential impact. If the structural validation step is prohibitively expensive for large-scale studies, the practical utility of the framework is diminished.
- **Resolution test** The authors should provide a benchmark of the end-to-end pipeline on a dataset with a significant number of long polyproteins, showing the time taken for the structural validation step. They should also discuss potential strategies for optimizing this step, such as parallelization or using faster structure prediction models.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2e
- **Evidence pointer** Figure 2e, Results section "Ablation studies and feature visualization".
- **Issue** The t-SNE visualization is described as showing that Rider's Transformer "reshaped the distribution into more compact, separated clusters." However, the text also notes that "these visualizations do not establish a uniform classification advantage over ESM2-linear." This is a somewhat contradictory statement. If the visualization does not show a clear advantage, its inclusion is of limited value.
- **Required correction** The authors should either clarify what specific insight the t-SNE plot provides, or remove it if it is not informative. If kept, the caption should be more descriptive about what the reader should observe.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods section "Model design, training, and benchmarking"
- **Evidence pointer** Methods section, "Model architecture".
- **Issue** The description of the Transformer classifier is brief. The number of layers, attention heads, hidden dimensions, and other architectural details are not fully specified. This makes it difficult to reproduce the model.
- **Required correction** Provide a more detailed description of the Transformer architecture, including the number of layers, heads, feed-forward dimensions, and any regularization techniques used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 4i
- **Evidence pointer** Figure 4i, Results section "DNA read coverage supports Rider predictions".
- **Issue** The correlation between Rider scores and DNA mapping rates is reported for four different environments. The Pearson correlation coefficients are very small (e.g., r = -0.065, r = -0.014) and some are not statistically significant. The text states this is a "consistent negative correlation," but the effect sizes are negligible.
- **Required correction** The authors should temper their interpretation of these results. The weak correlations provide only very weak support for the claim that higher-confidence predictions have lower DNA mapping rates. The text should acknowledge the small effect sizes and the potential for confounding factors.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 caption.
- **Issue** The figure caption is very long and detailed. While informative, it could be streamlined to improve readability.
- **Required correction** Consider moving some of the detailed description of the workflow into the main text or a separate methods section, and keep the figure caption more concise.

## Risk / unsupported claims
- The claim that structural validation "effectively eliminates false positives" is not fully supported, as the method is shown to fail on a significant number of highly divergent sequences.
- The claim that the IBD analysis reveals the "true" nature of the gut virome in UC and CD is an over-interpretation of a small, exploratory, contig-level analysis.
- The claim of "scalability" for the entire pipeline is not fully demonstrated, as the computational cost of the structural validation step for long polyproteins is not benchmarked.
- The performance metrics on the LucaProt test set may be inflated if there is any data leakage between the training and test sets; this is not explicitly ruled out.
- The biological significance of the "519 Rider-only candidates" is not validated beyond co-occurrence with geNomad signals.