## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and methods as described in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present a computational framework that fine-tunes a protein language model on curated epitope datasets to generate synthetic linear epitope libraries, then filters these sequences using transformer-based classifiers trained on viral and bacterial epitope data. The claimed outcome is libraries that reproduce statistical and sequence-level properties of natural epitopes and are compatible with high-throughput screening platforms such as droplet microfluidics.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark comparisons, dataset descriptions, or validation metrics are provided
- **Missing materials affecting confidence** Full methods, dataset curation details, model architecture specifications, training and evaluation protocols, quantitative performance metrics, comparison against existing epitope prediction or generation tools, and any experimental validation data

## Reviewer
- **Overall assessment** The abstract describes a conceptually reasonable pipeline that combines generative and discriminative language models for epitope library design. The idea is timely and aligns with current trends in applying protein language models to immunology. However, the abstract provides no quantitative evidence that the generated libraries indeed reproduce natural epitope properties, that the filtering step improves functional relevance, or that the approach outperforms existing methods. As presented, the claims are plausible but unsubstantiated. The chapter appears to be a methods description rather than a primary research report, which tempers expectations, but even for a methods chapter the absence of any performance characterization limits the reader's ability to assess utility.
- **Who would be interested in the results, and why** Researchers in computational immunology, vaccine design, and peptide library engineering would be the primary audience. Those working on generative models for biological sequences and on high-throughput screening integration would also find the framework relevant. The droplet microfluidics compatibility angle may attract experimentalists seeking AI-guided library design.
- **Major strengths** The combination of generative and discriminative language models in a single pipeline is a sensible design choice. The explicit framing of classifiers as filters rather than pathogen-origin predictors is a clear and appropriate scoping decision. The stated compatibility with high-throughput screening platforms indicates practical intent beyond purely computational benchmarking.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. Without quantitative evidence of library quality and without a demonstration that the filtering step adds value, the core claims of the framework cannot be evaluated.
- **Assessment against Nature-style criteria**  
  Originality: Moderate. The combination of fine-tuned protein language models with discriminative filtering for epitope library generation is not entirely novel, as similar generative-discriminative pipelines exist in other sequence-design contexts, but the specific application to linear epitope libraries is a reasonable niche contribution.  
  Scientific importance: Moderate. Epitope discovery is relevant to vaccinology and diagnostics, but the abstract does not demonstrate that the approach advances the state of the art.  
  Interdisciplinary readership: Moderate. The work bridges machine learning and immunology, but the abstract is written at a level that assumes familiarity with both fields without providing sufficient context for either audience.  
  Technical soundness: Not assessable from the abstract. No metrics, baselines, or validation procedures are described.  
  Readability for nonspecialists: Acceptable. The abstract is concise and avoids jargon overload, though terms such as "transformer-based classification models" and "droplet microfluidics" are used without brief explanation.
- **Recommendation posture** Currently not established from the provided evidence. The framework is plausible and the direction is worthwhile, but the abstract alone does not provide sufficient support for the claims. If the full chapter includes quantitative validation, the case may become supportive.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The framework generates synthetic epitope libraries that "reproduce key statistical and sequence-level properties of naturally occurring epitopes."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract asserts that the generated libraries reproduce statistical and sequence-level properties of natural epitopes, but no quantitative comparison is presented. There are no metrics such as amino acid frequency distributions, motif enrichment scores, sequence similarity distributions, or diversity measures that would substantiate this claim.  
- **Why it matters** The central value proposition of the framework is that generated libraries are biologically plausible and useful for screening. Without quantitative evidence of property reproduction, a reader cannot determine whether the generative model produces anything beyond random peptide sequences with superficial epitope-like features.  
- **Resolution test** Provide a comparison between generated and experimentally confirmed epitope sequences using at least two quantitative measures, such as k-mer frequency correlation, position-specific amino acid propensity, or embedding-space distance distributions, with appropriate statistical tests.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** Filtering with transformer-based classifiers "enrich[es] functional relevance" of generated sequences.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract states that filtering enriches functional relevance but provides no data showing that filtered sequences are more likely to be epitopes than unfiltered ones. No precision, recall, enrichment factor, or comparison against unfiltered generation is reported.  
- **Why it matters** The filtering step is a key component of the pipeline. If it does not measurably improve the proportion of plausible epitopes, the additional computational complexity is not justified. The claim of enrichment is central to the framework's utility.  
- **Resolution test** Report the fraction of generated sequences classified as epitopes before and after filtering, along with any available experimental validation or at least a benchmark against known epitope databases.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Comparative positioning  
- **Claim pointer** The framework is presented as a useful tool for epitope library generation, implying advantage over existing approaches.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No comparison is made against existing epitope prediction tools, generative sequence models, or random library baselines. The abstract does not state what this framework adds beyond what current methods already achieve.  
- **Why it matters** Without a baseline comparison, the reader cannot assess whether the framework is a meaningful advance or a reimplementation of known techniques. This is particularly relevant for a methods chapter, where positioning relative to prior work is essential.  
- **Resolution test** Include a comparison against at least one existing epitope prediction or generation method using a common evaluation metric, or clearly state the specific limitations of prior approaches that this framework addresses.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "curated epitope datasets" but does not specify their size, source, species, or whether they are linear or conformational epitopes.  
- **Required correction** Specify the datasets used, including source databases, number of sequences, and any filtering criteria applied during curation.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Model details  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract refers to "a large language model pre-trained on protein sequences" without naming the model or its version. This is insufficient for reproducibility.  
- **Required correction** Name the specific model and version used, and state whether the fine-tuning code and hyperparameters are publicly available.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scope clarity  
- **Affected element** Application claim  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states the libraries are "designed to be compatible" with droplet microfluidics but does not describe any design choices that ensure this compatibility, such as sequence length constraints or synthesis considerations.  
- **Required correction** Briefly describe the design features that enable compatibility with droplet microfluidics, or soften the claim to indicate intended rather than demonstrated compatibility.

## Risk / unsupported claims
- The claim that generated libraries "reproduce key statistical and sequence-level properties" of natural epitopes is unsupported by any quantitative evidence in the abstract.
- The claim that filtering "enrich[es] functional relevance" is unsupported by any comparative data.
- The claim of compatibility with droplet microfluidics is stated as a design goal rather than a demonstrated property; the abstract provides no evidence of experimental validation.
- The overall utility of the framework relative to existing methods is not assessable due to the absence of baseline comparisons.