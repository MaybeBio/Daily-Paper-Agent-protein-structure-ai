## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, dataset construction, benchmarking approach, and interpretation of results
- **Shared manuscript claim summary** The authors present MODNAP, a curated dataset of 1039 experimentally determined structures containing ribose-based modified nucleotides, and benchmark AlphaFold 3 on this dataset, reporting high global accuracy but variable local accuracy for modified residue placement, frequent intramolecular validity failures, and reduced performance on post-training-cutoff structures
- **Visible evidence base** Full text, methods descriptions, results narrative, figure legends (Figs 1-10), supplementary figure legends (S1-S17), tables referenced (Table 1)
- **Missing materials affecting confidence** Actual figures and supplementary figures not provided; Table 1 not provided; raw data files not inspected; PoseBusters and RNAspider output files not provided; AlphaFold 3 configuration files not provided

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important gap in the structural biology community: the systematic evaluation of AI-based structure prediction methods on modified nucleic acids. The construction of MODNAP represents a valuable community resource. The benchmarking results are informative and the observation that global accuracy metrics mask local errors in modified residue placement is an important cautionary finding. However, several methodological details require clarification, the statistical treatment of results needs strengthening, and the interpretation of the training-cutoff analysis warrants more careful framing. The manuscript is potentially suitable for publication after substantial revision.

- **Who would be interested in the results, and why** Structural biologists using AlphaFold 3 for nucleic acid modeling, developers of structure prediction methods, researchers studying modified nucleic acids in epigenetics and RNA biology, computational chemists developing force fields for non-canonical residues, and the broader AI-for-science community interested in benchmarking methodology.

- **Major strengths** The dataset fills a clear gap in the field, as no curated benchmark set for modified nucleic acid modeling previously existed. The systematic analysis of the chemical landscape of modified nucleotides in the PDB is comprehensive and well-executed. The use of multiple evaluation metrics (RMSD, TM-score, lDDT, INF, I-INF) provides a multi-faceted assessment. The inclusion of a post-training-cutoff test set is a thoughtful design choice for assessing generalization. The PoseBusters analysis adds an important dimension beyond simple geometric superposition.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports success rates exceeding 80% at an RMSD threshold of 2.5 Å across the full MODNAP benchmark set, and stratifies results by molecule type and modification type
- **Evidence pointer** Results section "Performance of AlphaFold 3 on the MODNAP benchmark set", Fig 4, Table 1
- **Concern** The manuscript reports success rates and percentages across categories but provides no confidence intervals, statistical comparisons between categories, or measures of variability. The dataset is heavily skewed toward a small number of modifications (e.g., 5CM with n=172, 8OG with n=90, BRU with n=64), while 63 of 129 CCD IDs are represented by a single structure. Aggregate success rates will be dominated by the well-represented modifications, and the reported percentages for rare modifications are based on extremely small sample sizes. No statistical framework is presented for determining whether differences between categories (e.g., RNA vs DNA, or base vs sugar modifications) are meaningful.
- **Why it matters** Without appropriate statistical treatment, readers cannot assess whether reported differences between categories reflect genuine performance variations or sampling noise. The skewed distribution means that the overall success rate may not be representative of performance on rare or chemically unusual modifications, which are precisely the cases of most interest to the community.
- **Resolution test** Provide confidence intervals for all reported success rates, perform statistical comparisons between categories (e.g., Fisher's exact test or chi-square test for proportions), and clearly report sample sizes for each category. For categories with very small sample sizes, either aggregate them into broader groups or explicitly flag them as preliminary.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The manuscript states that AlphaFold 3 models were generated using default parameters with a single random seed (modelSeeds = [10]) and five diffusion samples, with the top-scoring model selected by pTM or ipTM
- **Evidence pointer** Methods section "AlphaFold 3 modeling"
- **Concern** The use of a single random seed is a significant methodological limitation. AlphaFold 3's diffusion-based generative module is stochastic, and different seeds can produce substantially different predictions, particularly for challenging targets. The selection of the top model by pTM or ipTM from only five samples may not be representative of the model's typical performance. The manuscript does not report any measure of run-to-run variability, nor does it explain why a single seed was chosen. Additionally, the criteria for selecting pTM versus ipTM for ranking are not specified; it is unclear whether this choice was made per-target or uniformly.
- **Why it matters** The stochastic nature of AlphaFold 3 means that results from a single seed may not be reproducible or representative. If the benchmark is intended as a community resource for evaluating and improving structure prediction methods, the results must be robust to the choice of random seed. The lack of variability reporting undermines confidence in the reported success rates.
- **Resolution test** Run a subset of targets (e.g., 50-100 structures spanning different categories) with multiple seeds (at least 3-5) and report the variability in success rates and RMSD values. If computational cost is prohibitive, justify the single-seed approach with evidence that AlphaFold 3 is deterministic or that variability is negligible for the targets studied. Clearly specify the model selection criteria.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of training-cutoff analysis
- **Claim pointer** The manuscript states that performance was consistently lower for post-cutoff structures than pre-cutoff structures across nearly every category, and interprets this as evidence that a portion of AlphaFold 3's accuracy is attributable to structures available during training
- **Evidence pointer** Results section "Performance of AlphaFold 3 on the MODNAP test set", Fig 10C and 10D
- **Concern** The interpretation of the post-cutoff performance decline as evidence of training-set memorization is confounded by several factors. First, the post-cutoff set (n=103) is small and may not be representative of the broader distribution of modified nucleic acid structures. Second, structures deposited after September 30, 2021 may systematically differ from earlier structures in terms of resolution, complexity, or novelty of modifications, independent of whether AlphaFold 3 saw them during training. Third, the manuscript does not report whether the post-cutoff structures contain modifications that are chemically distinct from those in the training set, which would be an alternative explanation for reduced performance. The claim that reduced performance "reinforces the interpretation that fine-grained placement of nucleotide modifications is a comparatively weaker aspect of AlphaFold 3's predictive capability" conflates memorization with generalization failure.
- **Why it matters** The training-cutoff analysis is a key contribution of the manuscript, as it addresses the important question of whether AlphaFold 3 generalizes to novel structures. If the interpretation is confounded, the conclusions may be misleading. The distinction between memorization and generalization failure has different implications for how the community should use and improve these methods.
- **Resolution test** Provide a more detailed characterization of the post-cutoff set, including the distribution of modification types, structural complexity, and resolution compared to the pre-cutoff set. If possible, identify whether the post-cutoff structures contain modifications or folds that are chemically or structurally novel relative to the training set. Consider alternative explanations for the performance decline and discuss them explicitly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark design
- **Claim pointer** The manuscript describes MODNAP as "the first curated dataset of experimentally determined structures containing modified nucleotides" and states it is designed for "benchmarking and/or training structure prediction methods"
- **Evidence pointer** Abstract, Introduction, Results section "Features and composition of MODNAP"
- **Concern** The dataset construction criteria are not fully described. The manuscript states that structures with resolution 3.5 Å or better and sequence lengths within certain limits were included, but does not describe how redundancy was handled (e.g., sequence similarity clustering, structural similarity filtering). It is unclear whether the 1039 structures represent independent folds or whether many are near-duplicates of well-studied systems. The manuscript also does not describe how the "test set" was selected from the full benchmark set beyond the training cutoff date, and whether this introduces selection bias. Finally, the claim of being "first" requires more careful verification, as other benchmark sets for nucleic acid structure prediction may exist.
- **Why it matters** For a benchmark resource, the construction criteria directly affect its utility and the interpretability of results obtained with it. If the dataset contains many near-duplicate structures, the effective sample size is much smaller than 1039, and reported success rates may be inflated. The community needs to understand the dataset's limitations to use it appropriately.
- **Resolution test** Describe the redundancy filtering approach in detail, including any sequence or structural similarity thresholds used. Provide a clear description of how the test set was selected and whether it is representative of the full benchmark set. Verify the claim of being "first" by searching for existing benchmark sets for modified nucleic acid structure prediction.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The manuscript reports that PoseBusters analysis reveals frequent intramolecular validity failures, primarily due to non-ideal ribose ring geometries, and that only 30.4% of models passed the non-aromatic ring non-flat test
- **Evidence pointer** Results section "Structure validity checks with PoseBusters test suite", Fig 3
- **Concern** The manuscript does not provide a detailed breakdown of which specific PoseBusters tests were failed, the distribution of failure severity, or whether failures correlate with specific modification types or structural contexts. The statement that "models that failed chemical validity checks did not appear to cluster around specific CCD IDs" is based on visual inspection of supplementary figures, not statistical analysis. The manuscript also does not discuss whether the ribose ring geometry failures are specific to modified nucleotides or whether they also occur for canonical nucleotides in the same predictions, which would help distinguish between a general limitation of AlphaFold 3 and a modification-specific problem.
- **Why it matters** The PoseBusters analysis is a key finding of the manuscript, as it reveals that high global accuracy can coexist with local chemical invalidity. Understanding the specific nature and distribution of these failures is essential for the community to know which types of predictions can be trusted and which require additional validation or refinement.
- **Resolution test** Provide a detailed breakdown of PoseBusters test failures by category and modification type, with statistical analysis of correlations. Compare ribose ring geometry failures between modified and canonical nucleotides within the same predictions. Discuss the practical implications of these failures for downstream applications.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Evaluation of AlphaFold 3 models against experimental structures"
- **Evidence pointer** Methods section, location not provided
- **Issue** The description of RMSD calculation states that it was performed "following least-squares global alignment of the entire complex," but it is unclear which atoms were included in the RMSD calculation (all atoms, backbone only, heavy atoms only). The manuscript also does not specify whether the RMSD was calculated over the full structure or over specific regions when comparing "full structure" versus "modified nucleotide only" RMSD values.
- **Required correction** Specify the atom selection for RMSD calculations and clarify the alignment procedure. State whether the same alignment was used for both full-structure and modification-specific RMSD calculations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Performance of AlphaFold 3 on the MODNAP benchmark set"
- **Evidence pointer** Fig 4, Table 1
- **Issue** The manuscript reports success rates at a 2.5-Å RMSD threshold but does not report results at other thresholds. The choice of 2.5 Å is not justified, and it is unclear whether conclusions would change at stricter (e.g., 1.5 Å) or looser (e.g., 4 Å) thresholds.
- **Required correction** Report success rates at multiple RMSD thresholds (e.g., 1.5, 2.0, 2.5, 3.0, 4.0 Å) or justify the choice of 2.5 Å as the primary threshold.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Entanglements in AlphaFold 3 models of modified RNA structures"
- **Evidence pointer** Supplementary Fig S12-S14
- **Issue** The manuscript reports that entanglements were detected in models across several CCD IDs but does not provide a quantitative comparison of entanglement rates between modified and canonical RNA structures, nor does it discuss whether the observed entanglement rates are higher or lower than expected based on previous studies of AlphaFold 3 on unmodified RNA.
- **Required correction** Provide quantitative entanglement rates and compare with published results for unmodified RNA, if available. Discuss whether the presence of modified nucleotides influences entanglement propensity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of limitations focuses on the choice of AlphaFold 3 and the composition of the dataset, but does not discuss the potential impact of the single-seed approach or the lack of statistical power for rare modifications on the conclusions.
- **Required correction** Add a discussion of how the single-seed approach and the skewed distribution of modifications might affect the generalizability of the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The data availability statement provides links to Zenodo and GitHub, but does not specify the exact contents of these repositories, the software versions used, or the computational environment required to reproduce the analysis.
- **Required correction** Provide a detailed description of the repository contents, including file formats, software dependencies, and version numbers.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The introduction cites several databases for modified nucleotides but does not discuss existing efforts to benchmark structure prediction methods on modified nucleic acids, if any exist. The claim that this is the first such evaluation should be supported by a more thorough literature search.
- **Required correction** Expand the literature review to include any prior evaluations of structure prediction methods on modified nucleic acids, and clarify the novelty of the current work in this context.

## Risk / unsupported claims
- The claim that MODNAP is "the first curated dataset of experimentally determined structures containing modified nucleotides" is not fully verified against existing resources.
- The interpretation that reduced performance on post-cutoff structures reflects training-set memorization is confounded by potential differences in structure characteristics between pre- and post-cutoff sets.
- The statement that "AlphaFold 3 achieves success rates exceeding 80% at an RMSD threshold of 2.5 Å" is presented without confidence intervals or consideration of the skewed distribution of modifications.
- The claim that "co-folding in the presence of protein partners may improve overall intramolecular geometric consistency" is based on aggregate comparisons without statistical testing.
- The assertion that entanglements are "not necessarily due to the presence of a specific modified nucleotide but is instead dependent on the RNA tertiary fold itself" is based on a limited number of examples and lacks systematic comparison with unmodified RNA structures.