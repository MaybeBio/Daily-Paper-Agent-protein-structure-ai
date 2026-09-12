## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors present PRIS, a unified structure-based deep-learning framework comprising PRISeq (nucleotide probability estimation) and PRIScore (residue-nucleotide distance prediction). PRIS is claimed to improve native-like protein-RNA structure selection from AlphaFold3, infer position-specific binding preferences, and enable high-throughput virtual screening of RNA libraries with superior performance over existing methods.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided.
- **Missing materials affecting confidence** Full manuscript, all figures/tables, method details, benchmark definitions, dataset descriptions, code, and supplementary information.

## Reviewer
- **Overall assessment** The abstract presents a potentially impactful framework for structure-based RNA screening, combining structure selection and binding preference inference. The reported performance metrics are impressive, particularly the speed and enrichment factors. However, the abstract lacks sufficient methodological detail and validation context to assess the robustness of the claims. Key concerns include the absence of benchmark composition, statistical significance, and comparison fairness. The framework’s novelty relative to existing deep learning approaches for protein-RNA interactions is not clearly articulated.
- **Who would be interested in the results, and why** Researchers in computational structural biology, RNA bioinformatics, and therapeutic RNA discovery (e.g., aptamer design) would be interested. The framework promises to accelerate RNA library screening by integrating structure prediction with binding preference inference, which could streamline the identification of functional RNAs.
- **Major strengths** 1. The unified framework (PRISeq + PRIScore) addresses two complementary tasks—structure selection and binding preference inference—within a single architecture, which is a practical advance. 2. The reported screening speed (129,248 RNA hairpins in 11.95 seconds) and enrichment factor (EF 0.5% of 14.40) are notably high, suggesting potential for high-throughput applications. 3. The framework is demonstrated on multiple targets (MS2, NELF-E, GFP), indicating some generality.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodological transparency and reproducibility
    - **Claim pointer** PRIScore improves selection of native-like protein-RNA predictions from AlphaFold3, achieving a top-1 success rate of 81.91% on a docking benchmark, compared to 79.26% for AlphaFold3.
    - **Evidence pointer** Abstract only; no benchmark details provided.
    - **Concern** The abstract does not describe the composition of the docking benchmark (e.g., number of complexes, diversity of protein/RNA types, resolution range). The reported improvement (2.65 percentage points) is small, and without error bars or statistical testing, it is unclear whether this difference is significant. Additionally, the method by which AlphaFold3 predictions were generated and filtered is not specified.
    - **Why it matters** Without benchmark details and statistical rigor, the claimed improvement over AlphaFold3 cannot be evaluated. A small absolute gain may be within the noise of the prediction method.
    - **Resolution test** Provide the full benchmark dataset, performance metrics with confidence intervals or standard deviations, and a statistical test (e.g., paired t-test or Wilcoxon) comparing PRIScore to AlphaFold3.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Comparison fairness and baseline selection
    - **Claim pointer** On a PWM benchmark, PRISeq achieved a mean absolute error (MAE) of 0.75, outperforming FoldX, Rosetta-based scoring functions, and NA-MPNN.
    - **Evidence pointer** Abstract only; no benchmark details provided.
    - **Concern** The abstract does not specify the PWM benchmark (e.g., number of complexes, RNA length, source of experimental binding data). The baselines (FoldX, Rosetta, NA-MPNN) are not described in terms of their implementation or parameter settings. It is unclear whether these baselines were run under comparable conditions (e.g., same input structures, same scoring protocol).
    - **Why it matters** Without a clear description of the benchmark and baseline configurations, the claim of outperformance is unverifiable. Different implementations or input structures could lead to different results.
    - **Resolution test** Provide the full benchmark dataset, baseline implementation details (including version, parameters, and input structures), and a table comparing MAE with standard deviations across multiple runs or cross-validation.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Validation of virtual screening claims
    - **Claim pointer** In virtual screening against MS2 protein, PRISeq screens 129,248 RNA hairpins within 11.95 seconds, achieving the highest EF 0.5% of 14.40, approximately double the best baseline.
    - **Evidence pointer** Abstract only; no screening details provided.
    - **Concern** The abstract does not describe the RNA library (e.g., sequence diversity, length, source), the baseline methods used for comparison, or the definition of enrichment factor (EF 0.5%). The screening time is reported without hardware specifications (e.g., GPU/CPU type, memory), making it impossible to assess computational efficiency. Additionally, the claim of "approximately double the best baseline" requires explicit identification of that baseline and its EF value.
    - **Why it matters** Virtual screening claims are highly sensitive to library composition, baseline selection, and hardware. Without these details, the reported performance cannot be reproduced or compared to other methods.
    - **Resolution test** Provide the RNA library composition, baseline methods and their EF values, hardware specifications, and a clear definition of EF 0.5%. Report screening time with standard deviation across multiple runs.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Novelty and differentiation
    - **Claim pointer** PRIS is a "unified structure-based deep-learning framework" that combines structure selection and binding preference inference.
    - **Evidence pointer** Abstract only.
    - **Concern** The abstract does not clearly differentiate PRIS from existing deep learning methods for protein-RNA interaction prediction (e.g., RNABindR, PRIME, or graph-based methods). The key architectural innovations (A-GAT, k-MPI attention) are mentioned but not explained in terms of their advantage over standard attention or graph convolution mechanisms.
    - **Why it matters** For a Nature-level journal, the novelty of the framework must be clearly established relative to the state of the art. Without this, the contribution may be incremental.
    - **Resolution test** Provide a clear comparison table or discussion of existing methods, and explain why A-GAT and k-MPI attention are necessary and superior for this task.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The abstract states that PRIS "effectively enriches active aptamers against NELF-E and GFP while preserving sequence diversity," but no quantitative metrics (e.g., enrichment factor, diversity index) are provided for these targets.
    - **Required correction** Include quantitative results for NELF-E and GFP, or state that these results are presented in the full manuscript.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The term "native-like" is used without a clear definition. In the context of protein-RNA docking, "native-like" typically refers to structures within a certain RMSD threshold (e.g., < 2 Å or < 5 Å). The threshold used should be specified.
    - **Required correction** Define "native-like" explicitly (e.g., RMSD < X Å) in the abstract or full manuscript.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract
    - **Issue** The abstract mentions "AlphaFold3" but does not specify the version or whether the predictions were used as-is or refined.
    - **Required correction** Specify the AlphaFold3 version and any post-processing steps applied to its predictions.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. These concerns relate to missing benchmark details, statistical validation, and comparison fairness, which are essential for evaluating the core claims of the framework.

- **Assessment against Nature-style criteria**
    - **Originality**: The unified framework combining structure selection and binding preference inference is a practical integration, but the abstract does not clearly demonstrate how the individual components (A-GAT, k-MPI attention) are novel beyond existing graph-based methods. The originality is currently unclear.
    - **Scientific importance**: The problem of high-throughput RNA screening is important for therapeutic discovery. If validated, the framework could have significant impact. However, the abstract does not provide enough evidence to assess the magnitude of the advance.
    - **Interdisciplinary readership**: The topic bridges structural biology, machine learning, and RNA therapeutics, which is of broad interest. The abstract is written in a way that is accessible to nonspecialists, though some technical terms (e.g., k-MPI attention) could be better explained.
    - **Technical soundness**: The technical soundness cannot be assessed from the abstract alone. The reported metrics are promising, but the lack of benchmark details, statistical tests, and baseline comparisons raises concerns.
    - **Readability for nonspecialists**: The abstract is generally clear, but the description of the architecture (A-GAT, k-MPI) is too brief for a nonspecialist to understand the innovation. A brief explanation of why these components are advantageous would improve readability.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting framework with promising metrics, but the lack of methodological detail, benchmark descriptions, and statistical validation prevents a reliable assessment of the claims. The authors should provide the full manuscript and supplementary materials to address the major concerns.

## Risk / unsupported claims
- The claim that PRIScore improves AlphaFold3's top-1 success rate (81.91% vs. 79.26%) is unsupported without benchmark details and statistical significance.
- The claim that PRISeq outperforms FoldX, Rosetta, and NA-MPNN on a PWM benchmark is unsupported without benchmark composition and baseline implementation details.
- The claim of virtual screening performance (EF 0.5% of 14.40, 129,248 hairpins in 11.95 seconds) is unsupported without library description, baseline comparison, and hardware specifications.
- The claim that PRIS "effectively enriches active aptamers against NELF-E and GFP while preserving sequence diversity" is unsupported without quantitative metrics for these targets.