## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose DNA-BFN, a Bayesian flow network framework for generative modeling of regulatory DNA sequences. The method models per-position categorical distributions via iterative Bayesian updates, avoiding explicit perturbation of discrete sequences. The authors claim consistent outperformance over state-of-the-art baselines across eight datasets, preservation of sequence feature statistics and regulatory patterns, few-shot design capability, and faster sampling efficiency.
- **Visible evidence base** Abstract text only; no quantitative results, dataset descriptions, baseline specifications, or code verification are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary data, dataset details, baseline implementations, hyperparameter settings, and evaluation metrics

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach that addresses a recognized limitation of diffusion models for discrete biological sequences. The methodological framing is coherent and the claimed results are broad in scope. However, the abstract alone provides no quantitative evidence, no comparison details, and no methodological specifics sufficient to evaluate technical soundness or reproducibility. The claims are plausible but currently unverifiable from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and generative model development would be interested. The approach could appeal to those working on sequence design for synthetic biology, enhancer/promoter engineering, and those seeking alternatives to diffusion models for discrete data. The general framing of probability-space generation may also interest machine learning researchers focused on discrete generative modeling.
- **Major strengths** The conceptual shift from noise perturbation to iterative Bayesian belief updates is a clear and potentially impactful idea. The claim of preserving discrete sequence structure while enabling differentiable training addresses a known limitation of diffusion approaches. The reported breadth of evaluation across eight datasets and multiple species suggests an effort toward generalizability.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The Bayesian flow network concept applied to regulatory DNA is novel in framing, though the underlying idea of iterative belief updates is not entirely new in machine learning. Scientific importance: Potentially high for regulatory genomics, but the abstract does not demonstrate biological impact beyond performance metrics. Interdisciplinary readership: The abstract is accessible to both computational and biological audiences, but lacks depth for either to assess rigor. Technical soundness: Cannot be evaluated from the abstract; no algorithmic details, loss functions, or convergence properties are given. Readability for nonspecialists: The abstract is clear in motivation and high-level method, but the term "Bayesian Flow Networks" may be unfamiliar without context.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract alone does not provide sufficient quantitative or methodological support. A full review would be required to determine if the claims hold.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "DNA-BFN consistently outperforms state-of-the-art baselines across eight regulatory sequence datasets"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract claims consistent outperformance but provides no quantitative metrics, no baseline names, no statistical significance tests, and no effect sizes. Without these, the claim is unverifiable.  
- **Why it matters** The central claim of the paper rests on this comparison. If the performance gain is marginal or only on specific metrics, the generalizability claim would be weakened.  
- **Resolution test** Provide a table or figure in the full manuscript with performance metrics (e.g., accuracy, likelihood, or biological validity scores) for all methods across all eight datasets, including error bars and significance tests.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** "DNA-BFN realizes a diffusion-like generative process without explicitly perturbing discrete nucleotide sequences, enabling fully differentiable training"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not describe the loss function, the Bayesian update rule, the network architecture, or how differentiability is achieved. The term "Bayesian Flow Networks" is not defined, and the relationship to existing flow-based or diffusion methods is unclear.  
- **Why it matters** Without methodological detail, the technical soundness cannot be assessed. The claim of "fully differentiable training" is central but unsubstantiated.  
- **Resolution test** Include a methods section with a formal description of the generative process, the update equations, the training objective, and a derivation or citation for the differentiability claim.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** "faithfully preserves sequence feature statistics and regulatory patterns"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not specify which sequence features or regulatory patterns were evaluated, how preservation was measured, or against what ground truth. The term "faithfully" is subjective without quantitative definitions.  
- **Why it matters** This claim is critical for biological relevance. If the model generates sequences that look statistically similar but lack functional regulatory activity, the practical utility is questionable.  
- **Resolution test** Provide specific metrics (e.g., k-mer frequency divergence, motif enrichment scores, or in silico regulatory activity predictions) and compare generated sequences to natural sequences in the full manuscript.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** "achieves faster sampling efficiency"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No runtime measurements, hardware specifications, or comparison baselines are given. "Faster" is relative and undefined.  
- **Why it matters** Sampling efficiency is a practical advantage claimed by the authors, but without concrete numbers, it cannot be evaluated or reproduced.  
- **Resolution test** Report wall-clock sampling times for DNA-BFN and all baselines under identical hardware and software conditions, with standard deviations across multiple runs.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "diffusion-like generative process" is vague. It is unclear whether the process is mathematically equivalent to diffusion or merely analogous.  
- **Required correction** Clarify the relationship to diffusion models, either by formal equivalence or by explicit distinction.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "eight regulatory DNA sequence datasets spanning diverse species, scales, and sequence lengths" but does not list the species, sequence length ranges, or dataset sources.  
- **Required correction** Provide a supplementary table listing dataset names, species, sequence counts, and length distributions.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Accessibility  
- **Affected element** Code availability  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The GitHub and Zenodo links are provided, but there is no statement on software dependencies, license, or whether the code is documented.  
- **Required correction** Add a brief statement on code documentation, dependencies, and license in the availability section.

## Risk / unsupported claims
- The claim of "consistent outperformance" is unsupported without quantitative data.
- The claim of "faithfully preserves sequence feature statistics and regulatory patterns" is unsupported without defined metrics.
- The claim of "faster sampling efficiency" is unsupported without runtime measurements.
- The claim of "fully differentiable training" is unverifiable without methodological details.
- The generalizability claim across "diverse species, scales, and sequence lengths" is unverifiable without dataset descriptions.