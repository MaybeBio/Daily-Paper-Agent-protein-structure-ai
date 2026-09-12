## Review setup
- **Input scope** Full manuscript (Computational and structural biotechnology journal, 2026)
- **Assessment boundary** Claims, methods, results, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors propose PromptGPCR, an AlphaFold-based inference framework that uses biologically informed sequence prompts to guide AlphaFold-Multimer and AlphaFold 3 toward predicting both active and inactive GPCR structures with higher accuracy than existing methods, and demonstrate improved performance in molecular docking.
- **Visible evidence base** Abstract only; no figures, tables, methods section, or supplementary materials provided
- **Missing materials affecting confidence** Full methods, all figures/tables, supplementary data, code availability, benchmark datasets, statistical analyses, and comparison details

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important problem—predicting multiple conformational states of GPCRs, which is a known limitation of current AlphaFold implementations. The core idea of using biologically informed sequence prompts to steer AlphaFold toward specific states is conceptually interesting. However, the provided abstract alone is insufficient to evaluate the technical validity, reproducibility, or significance of the claimed results. Critical details about the prompting strategy, benchmark design, and quantitative comparisons are absent, making it impossible to assess whether the claims are supported.

- **Who would be interested in the results, and why** Structural biologists, computational chemists, and drug discovery researchers working on GPCR-targeted therapeutics would be interested, as accurate multi-state GPCR prediction could directly impact structure-based drug design for agonists and antagonists.

- **Major strengths**
  - The problem of predicting both active and inactive GPCR states is well-recognized and practically important.
  - The approach of using sequence-based prompts to guide AlphaFold is conceptually novel and potentially generalizable.
  - The claim of improved molecular docking success rates suggests practical utility in drug discovery pipelines.

- **Major Concerns**
  - **Concern ID** R1-M1
    **Severity** Major
    **Blocking** Yes
    **Axis** Methodological clarity
    **Claim pointer** "We provide AlphaFold-Multimer and AlphaFold 3 with biological sequences based on knowledge of structural biology as prompts to guide the models in the multi-state prediction task."
    **Evidence pointer** Abstract; location not provided
    **Concern** The nature of the "prompts" is entirely undefined. The abstract does not specify what biological sequences are used, how they are derived from structural biology knowledge, how they are incorporated into AlphaFold's input, or whether this is a simple sequence concatenation, a modified MSA, or a more complex conditioning strategy. Without this information, the method cannot be reproduced or evaluated.
    **Why it matters** The core novelty of the work hinges on the prompting strategy. If the prompts are trivial (e.g., appending a known active-state sequence), the contribution is minimal. If they are sophisticated, the lack of detail prevents assessment of their validity and generalizability.
    **Resolution test** Provide a clear description of the prompting mechanism, including the exact input format, the source and selection criteria for the prompt sequences, and how they differ from standard AlphaFold inputs. Include a schematic or pseudocode.

  - **Concern ID** R1-M2
    **Severity** Major
    **Blocking** Yes
    **Axis** Quantitative validation
    **Claim pointer** "Experimental results demonstrate that PromptGPCR can accurately predict active and inactive structures compared to baselines."
    **Evidence pointer** Abstract; location not provided
    **Concern** No quantitative metrics (e.g., RMSD, TM-score, GDT_TS, or state-specific metrics) are reported. The claim of "accurate" prediction is unsubstantiated. The abstract does not specify which baselines were used (e.g., standard AlphaFold2/3, RoseTTAFold, or other GPCR-specific methods), nor the number of GPCR targets tested, nor the statistical significance of any improvements.
    **Why it matters** Without numerical evidence, the central claim of the paper cannot be evaluated. The field requires rigorous benchmarking against established methods on a representative set of GPCRs with known active and inactive structures.
    **Resolution test** Report full benchmarking results including: (1) list of GPCR targets and their state annotations, (2) quantitative comparison metrics (RMSD, TM-score, etc.) for both active and inactive predictions, (3) comparison against at least standard AlphaFold2/3 and one other state-of-the-art method, (4) statistical tests (e.g., paired t-test or Wilcoxon) for significance.

  - **Concern ID** R1-M3
    **Severity** Major
    **Blocking** Yes
    **Axis** Downstream validation
    **Claim pointer** "PromptGPCR exhibits higher success rates in molecular docking than baselines, and this indicates that the predictions of PromptGPCR may have a certain degree of usability in downstream application scenarios involving specific GPCR conformational states."
    **Evidence pointer** Abstract; location not provided
    **Concern** The docking success rate is mentioned but not defined. What constitutes "success"? Is it enrichment of known ligands, pose prediction accuracy (RMSD < 2 Å), or something else? Which docking program was used? How many ligands were tested? Were the docking experiments blinded to the known active/inactive state? Without these details, the docking claim is uninterpretable.
    **Why it matters** Docking validation is a key practical test of structural accuracy. Poorly defined success criteria can inflate apparent performance. The field requires standardized docking benchmarks (e.g., DUD-E, DEKOIS) with clear metrics.
    **Resolution test** Provide: (1) definition of docking success, (2) docking software and parameters, (3) number and source of ligands, (4) results for each GPCR target, (5) comparison to docking on experimental structures (if available) and on baseline predictions.

- **Minor Comments**
  - **Concern ID** R1-m1
    **Severity** Minor
    **Axis** Clarity
    **Affected element** Abstract
    **Evidence pointer** Abstract
    **Issue** The phrase "biological sequences based on knowledge of structural biology as prompts" is vague and could be misinterpreted. It is unclear whether these are sequences from homologous GPCRs in specific states, engineered sequences, or something else.
    **Required correction** Replace with a precise description, e.g., "We use the sequence of a known active-state GPCR (e.g., β2-adrenergic receptor in active conformation) as a prompt appended to the target GPCR sequence in the AlphaFold input."

  - **Concern ID** R1-m2
    **Severity** Minor
    **Axis** Scope
    **Affected element** Abstract
    **Evidence pointer** Abstract
    **Issue** The abstract claims PromptGPCR predicts "highly accurate structures" but does not define a threshold for "highly accurate." This is subjective.
    **Required correction** Replace with a quantitative statement, e.g., "achieving median TM-score > 0.9 for active-state predictions" or similar.

  - **Concern ID** R1-m3
    **Severity** Minor
    **Axis** Reproducibility
    **Affected element** Abstract
    **Evidence pointer** Abstract
    **Issue** No mention of code or data availability. For a computational method, this is essential for reproducibility.
    **Required correction** Add a statement about code and data availability (e.g., GitHub repository, Zenodo archive).

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Undefined prompting strategy
  - R1-M2: Absence of quantitative validation metrics
  - R1-M3: Unclear docking validation protocol

- **Assessment against Nature-style criteria**
  - **Originality**: The concept of using sequence prompts to steer AlphaFold toward specific GPCR states is moderately original. However, similar ideas (e.g., using templates or MSA manipulation) have been explored. The novelty depends on the specific implementation, which is not described.
  - **Scientific importance**: High. GPCR multi-state prediction is a critical bottleneck in structure-based drug design. If validated, this method could have significant impact.
  - **Interdisciplinary readership**: Moderate. The work bridges computational biology and drug discovery, but the abstract is too technical for a broad audience without context.
  - **Technical soundness**: Cannot be assessed from the abstract alone. The lack of quantitative results and methodological detail prevents evaluation.
  - **Readability for nonspecialists**: The abstract is reasonably clear for a specialist audience but uses jargon (e.g., "prompts," "AlphaFold-Multimer") without explanation. A nonspecialist would struggle to understand the method.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting concept but lacks the quantitative and methodological detail necessary to support the claims. A full manuscript with rigorous benchmarking and clear method description is required before a meaningful assessment can be made.

## Risk / unsupported claims
- "PromptGPCR can accurately predict active and inactive structures" – unsupported; no quantitative metrics provided.
- "PromptGPCR exhibits higher success rates in molecular docking than baselines" – unsupported; docking success criteria and results not defined.
- "PromptGPCR may have a certain degree of usability in downstream application scenarios" – speculative; no evidence of real-world application.
- "We provide AlphaFold-Multimer and AlphaFold 3 with biological sequences based on knowledge of structural biology as prompts" – unverifiable; method not described.