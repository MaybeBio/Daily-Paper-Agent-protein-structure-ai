## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, or supplementary data were provided for evaluation
- **Shared manuscript claim summary** The authors present CheMoDesign, a generative framework that extends de novo protein design beyond the canonical twenty amino acids by incorporating user-defined chemical building blocks, including post-translational modifications, synthetic residues, and chemical modifications. The framework is claimed to generate proteins with chemistry-dependent recognition and reactivity, validated through single-round experimental campaigns targeting thrombin, HER2, PD-L1, and CA IX.
- **Visible evidence base** Abstract text only; no experimental protocols, structural data, binding assays, selectivity data, or computational benchmarks were provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary information, sequence and structure data, experimental validation details, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially impactful framework that aims to make chemical mechanism a programmable dimension in de novo protein design. The concept is timely and addresses a genuine limitation in current generative protein design. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, experimental rigor, or generalizability of the claims. Several assertions, particularly regarding selectivity, affinity, and mechanism, require detailed experimental and computational support that is not visible in the supplied material. The work is potentially significant, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers in computational protein design, chemical biology, and synthetic biology would be interested. The framework's promise to incorporate noncanonical chemistry into designed proteins could appeal to those developing therapeutic binders, biosensors, or tools for targeted covalent inhibition. The potential to program post-translational modifications and bioorthogonal reactivity may also attract groups working on chemical probes and cell engineering.
- **Major strengths** The conceptual advance is clear and well framed. Extending the chemical alphabet of generative protein design beyond canonical residues addresses a recognized bottleneck. The range of demonstrated applications, from modification-dependent recognition to covalent capture and isoform-selective inhibition, suggests broad utility. The claim of single-round experimental success is notable if substantiated.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The concept of incorporating user-defined chemistry into generative protein design is novel and extends beyond incremental advances in the field. Scientific importance: If fully validated, the framework could enable new classes of protein-based tools and therapeutics, making the potential impact high. Interdisciplinary readership: The work bridges computational design, chemical biology, and protein engineering, which should attract a broad audience. Technical soundness: Not assessable from the abstract; the absence of methodological detail and raw data prevents evaluation of the framework's robustness. Readability for nonspecialists: The abstract is concise and accessible, though some terms such as "pair-representation conditioning" and "sequence-conditioned denoising" may be opaque to non-experts without further context.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual promise is clear, but the abstract does not provide sufficient experimental or computational detail to support the core claims. A supportive posture would require access to the full manuscript and validation data.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The framework generated proteins with chemistry-dependent recognition and reactivity in single-round experimental campaigns.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract claims successful generation of functional proteins across multiple targets and modification types in single-round campaigns, but no experimental data, success rates, or reproducibility metrics are provided.  
- **Why it matters** Single-round success is a strong claim that, if true, would distinguish this framework from iterative design approaches. Without data on hit rates, false positives, or replicate experiments, the reliability of the framework cannot be assessed.  
- **Resolution test** Provide experimental details including number of designs tested, hit rates, replicate counts, and statistical significance for each target and modification type.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Specificity and selectivity  
- **Claim pointer** Sulfotyrosine and nitrotyrosine enabled modification-dependent recognition of thrombin and HER2, respectively.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The claim of modification-dependent recognition implies that recognition is contingent on the presence of the specific chemical modification. No data are shown to demonstrate that unmodified controls fail to bind or that binding is lost upon modification removal.  
- **Why it matters** Without negative controls, the observed binding could be due to the protein scaffold alone rather than the chemical modification. This is central to the framework's premise that chemistry is a programmable determinant of function.  
- **Resolution test** Include binding data for matched controls lacking the modification, and demonstrate that recognition is lost or significantly reduced in their absence.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative validation  
- **Claim pointer** Post-expression chemical modifications yielded a light-activated covalent PD-L1 binder and an isoform-selective CA IX inhibitor (KD = 45 nM) designed to engage catalytic Zn2+.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** A single KD value is reported for the CA IX inhibitor, but no data are provided for the PD-L1 binder, including affinity, light-activation kinetics, or covalent labeling efficiency. The claim of isoform selectivity is not supported by any comparative data against CA XII or other carbonic anhydrases.  
- **Why it matters** Quantitative binding and selectivity data are essential to substantiate the functional claims. The absence of such data for the PD-L1 binder and the lack of selectivity context for CA IX leave the most impactful claims unverified.  
- **Resolution test** Provide full binding curves, KD values for all reported binders, selectivity panels for CA IX against related isoforms, and light-activation and covalent labeling data for the PD-L1 construct.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic attribution  
- **Claim pointer** CheMoDesign makes chemical mechanism a programmable dimension of de novo protein design.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not describe how the framework ensures that the designed proteins engage the intended chemical mechanism, such as Zn2+ coordination in CA IX or covalent bond formation in the PD-L1 binder. No structural or mechanistic evidence is presented.  
- **Why it matters** The central claim is that chemical mechanism is programmable, not merely that functional proteins were obtained. Without evidence that the designed chemistry is mechanistically responsible for the observed activity, the framework's core premise remains unsupported.  
- **Resolution test** Provide structural data, mutagenesis studies, or mechanistic assays demonstrating that the intended chemical interaction is required for function.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Framework description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The terms "pair-representation conditioning" and "sequence-conditioned denoising" are introduced without explanation, which may hinder comprehension for readers outside computational protein design.  
- **Required correction** Provide a brief plain-language description of these steps or a schematic in the full manuscript.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Scope of chemical space  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract lists several modification types but does not clarify the breadth of chemical space the framework can accommodate, such as limits on modification size, charge, or position.  
- **Required correction** Include a discussion of the scope and limitations of compatible chemical building blocks.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Experimental campaigns  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states "single-round experimental campaigns" but does not specify the number of independent campaigns or whether results were consistent across repeats.  
- **Required correction** Report the number of campaigns and any variability observed.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Comparison to existing methods  
- **Affected element** Benchmarking  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No comparison is made to existing design methods that incorporate noncanonical residues or post-translational modifications, making it difficult to assess the relative advantage of CheMoDesign.  
- **Required correction** Include benchmarks against relevant prior approaches in the full manuscript.

## Risk / unsupported claims
- The claim of "single-round experimental campaigns" is unsupported without data on design success rates and replicates.
- The claim of "modification-dependent recognition" is unsupported without negative control data.
- The claim of "isoform-selective CA IX inhibitor" is unsupported without selectivity data against related isoforms.
- The claim of "light-activated covalent PD-L1 binder" is unsupported without affinity, activation, and labeling data.
- The claim that "chemical mechanism is a programmable dimension" is unsupported without mechanistic or structural evidence.
- The reported KD of 45 nM for CA IX is a single quantitative value with no experimental context or error estimates.