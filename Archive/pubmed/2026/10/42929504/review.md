## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors introduce "enhanced diffusion sampling," a framework that combines diffusion model-based equilibrium samplers with biased sampling protocols (umbrella sampling, metadynamics, and tilted ensembles) to improve rare-event sampling and free energy calculations. Three algorithms are presented: UmbrellaDiff, MetaDiff, and DeltaG-Diff. Demonstrations on toy landscapes and protein folding free energy calculations with BioEmu are claimed, with reported computational costs of minutes to hours of GPU time per system.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or validation data are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methodological derivations, benchmark details, error analysis, and comparison with existing methods

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing integration of diffusion models with established enhanced sampling techniques. The core idea of using diffusion model-generated ensembles as a starting point for biased sampling protocols, followed by exact reweighting, is timely and potentially impactful. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, the accuracy of the reported free energy calculations, or the claimed computational efficiency. The central claims regarding unbiased thermodynamic estimators and reduced computational cost are not substantiated with quantitative data in the provided material.
- **Who would be interested in the results, and why** Computational chemists, biophysicists, and researchers in molecular simulation would be interested, particularly those working on rare event sampling, free energy calculations, and the application of generative models to molecular systems. The potential to accelerate protein folding free energy calculations from days or weeks to minutes or hours would attract a broad audience in both methodology development and application-oriented research.
- **Major strengths** The conceptual framework is novel and addresses a clear gap in the field, namely the limitation of diffusion model samplers in computing observables that depend on rare equilibrium states. The proposal to combine diffusion models with classical enhanced sampling techniques is a natural and potentially powerful synthesis. The claimed computational speedup, if substantiated, would represent a significant practical advance.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is high, as the integration of diffusion models with biased sampling protocols appears novel. Scientific importance is potentially high given the central role of rare event sampling in molecular simulation. Interdisciplinary readership is plausible, spanning machine learning, statistical mechanics, and biophysics. Technical soundness cannot be assessed from the abstract alone, as no methodological details or validation results are provided. Readability for nonspecialists is adequate, with clear conceptual framing, though the abstract assumes familiarity with both diffusion models and enhanced sampling techniques.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising, but the abstract does not provide sufficient quantitative evidence to support the central claims of unbiased estimation, accuracy, and computational efficiency. A supportive posture would require access to the full manuscript with detailed methods and validation results.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their framework "preserv[es] unbiased thermodynamic estimators" and "recover[s] equilibrium statistics via exact reweighting."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract asserts that exact reweighting is used to recover equilibrium statistics from biased ensembles, but no details are provided on the reweighting scheme, its convergence properties, or the conditions under which it is exact. In practice, reweighting methods such as umbrella sampling and metadynamics require careful handling of statistical weights, and the accuracy of the reweighted estimates depends critically on the overlap between the biased and unbiased distributions. The abstract does not address how the diffusion model-generated ensembles interact with these requirements.
- **Why it matters** The central methodological claim is that the proposed methods yield unbiased thermodynamic estimates. If the reweighting is not exact or has poor convergence properties, the reported free energy calculations could be systematically biased, undermining the validity of the results.
- **Resolution test** The full manuscript must provide a rigorous derivation of the reweighting scheme, demonstrate its exactness under stated assumptions, and present convergence diagnostics (e.g., overlap measures, effective sample sizes) for the toy systems and protein folding applications.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "our methods reduce the cost of rare-state estimation, enabling protein folding free-energy calculations in minutes to hours of graphics processing unit time per system."
- **Evidence pointer** Abstract, location not provided
- **Concern** No quantitative data are provided to support the claimed computational cost. The abstract does not specify the systems studied, the number of GPU hours required, the accuracy of the resulting free energy estimates, or how these costs compare with established methods. Without such data, the claim of "minutes to hours" is unverifiable and may be misleading if the accuracy is insufficient or if the comparison baseline is not clearly defined.
- **Why it matters** The computational efficiency claim is a key selling point of the proposed methods. If the actual cost is higher than stated, or if the accuracy is compromised, the practical utility of the methods is substantially diminished.
- **Resolution test** The full manuscript must provide a detailed benchmark table listing the systems, GPU hardware, wall-clock times, and free energy estimates with associated uncertainties, alongside comparisons with established methods (e.g., conventional umbrella sampling or metadynamics) under matched conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation scope
- **Claim pointer** The authors state that they "demonstrate the three methods on toy free-energy landscapes and apply DeltaG-Diff to protein folding free-energy calculations with BioEmu."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not report any quantitative results from these demonstrations. No free energy values, error bars, or comparisons with reference calculations are provided. It is unclear whether the toy landscape results validate the methods' accuracy, and whether the protein folding calculations are benchmarked against known experimental or computational references.
- **Why it matters** Without quantitative validation, the reader cannot assess whether the methods produce accurate free energy estimates. The claim of successful demonstration is unsupported by visible evidence.
- **Resolution test** The full manuscript must present numerical results for the toy systems (e.g., free energy profiles compared with analytical solutions) and for the protein folding applications (e.g., folding free energies compared with experimental values or established computational references), including uncertainty quantification.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "batchwise analog" for MetaDiff is vague and does not clarify how the method differs from standard metadynamics or how the diffusion model is integrated.
- **Required correction** Provide a more precise description of the algorithmic structure of MetaDiff, including how the diffusion model generates biased ensembles and how the bias is updated across batches.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model specification
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not specify which diffusion model architecture is used for the toy systems or whether BioEmu is used as a fixed pretrained model or fine-tuned for the protein applications.
- **Required correction** State the model architecture and training details for each application, including whether BioEmu is used off-the-shelf or adapted.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with prior work
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not discuss how the proposed methods compare with existing approaches for rare event sampling using generative models, such as flow-based methods or other reweighting schemes.
- **Required correction** Add a brief statement in the abstract or introduction situating the work relative to prior generative model-based sampling methods.

## Risk / unsupported claims
- The claim of "unbiased thermodynamic estimators" is unsupported without a detailed derivation and convergence analysis.
- The claim of "minutes to hours of graphics processing unit time per system" is unsupported without benchmark data.
- The claim of successful demonstration on toy landscapes and protein folding is unsupported without quantitative results.
- The generalizability of the methods to systems beyond those tested is not assessable from the abstract.