## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use ColabFold to generate structural models for a sequence-reversed variant (rRop) of the wtRop coiled-coil protein, then apply classical molecular dynamics and well-tempered metadynamics to compute free energy surfaces across four collective variables. They report that both parallel and antiparallel rRop models deviate from the native antiparallel orientation, with the antiparallel variant showing greater instability, loss of helicity, disrupted hydrogen bonding, increased solvent-accessible surface area, and a compromised hydrophobic core. The parallel variant is claimed to share greater conformational similarity with the parent protein.
- **Visible evidence base** Abstract text only; no numerical data, figures, tables, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation parameters, convergence criteria for metadynamics, free energy surface plots, error estimates, and any statistical analysis

## Reviewer
- **Overall assessment** The study addresses a conceptually interesting question about sequence reversal effects on coiled-coil stability, combining AI-based structure prediction with enhanced sampling simulations. However, the abstract alone provides insufficient evidence to evaluate the technical soundness of the simulations, the convergence of the metadynamics calculations, or the robustness of the free energy comparisons. The central claims about differential stability between parallel and antiparallel rRop variants are plausible but not verifiable from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics and protein engineering, particularly those studying coiled-coil motifs, protein design, and the application of AI-based structure prediction combined with enhanced sampling methods. The work may also interest experimentalists seeking computational predictions for sequence-reversed protein variants.
- **Major strengths** The combination of AI-based structure prediction with atomistic enhanced sampling is a timely methodological approach. The use of multiple collective variables to characterize conformational free energy surfaces is thorough. The comparison between parallel and antiparallel orientations of the reversed sequence provides a systematic framework for assessing sequence reversal effects.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. Sequence reversal is a specific perturbation, and the combination of ColabFold with metadynamics is not entirely novel, though the application to this system may offer new insight.  
  - Scientific importance: Moderate. The findings could inform protein design principles, but the abstract does not establish broad significance beyond the specific wtRop system.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biophysicists and protein chemists; the abstract does not frame the results for a broader audience.  
  - Technical soundness: Not assessable from the abstract. No convergence criteria, force field details, simulation lengths, or error analysis are provided.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses specialized terminology without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents interesting claims, but the lack of methodological detail and quantitative results prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that free energy analysis reveals both rRop models deviate from the native antiparallel orientation to stabilize at an intermediate angle.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative free energy differences, no error bars, and no convergence assessment for the well-tempered metadynamics simulations. Without these, the claim that the models "stabilize" at an intermediate angle cannot be evaluated.  
- **Why it matters** The central conclusion of the paper depends on the reliability of the free energy surfaces. If the simulations are not converged or the free energy differences are within statistical error, the claim is unsupported.  
- **Resolution test** Provide free energy surface plots with error estimates, convergence metrics (e.g., time evolution of free energy differences), and a clear statement of the statistical significance of the observed minima.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the antiparallel rRop variant exhibits the most significant instability, characterized by increased monomer separation and a more pronounced loss of secondary structure.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No quantitative measures of monomer separation, helicity, or secondary structure content are provided. The abstract states qualitative differences without numerical support.  
- **Why it matters** The comparative claim between the antiparallel variant, the parallel variant, and the wild-type requires quantitative data to establish the magnitude and significance of the differences.  
- **Resolution test** Report numerical values for monomer separation, helicity percentage, and secondary structure content for all three systems, with standard errors and statistical tests.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the antiparallel model demonstrates a disrupted hydrogen bond network, increased solvent-accessible surface area, and failure to maintain a robust hydrophobic core.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** These structural descriptors are mentioned without any quantitative data or reference to specific figures or tables. The abstract does not indicate how these properties were calculated or compared across systems.  
- **Why it matters** These claims are central to the mechanistic interpretation of instability. Without quantitative support, they remain assertions rather than findings.  
- **Resolution test** Provide numerical values for hydrogen bond counts, solvent-accessible surface area, and hydrophobic core packing metrics for each system, with appropriate error analysis.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological validity  
- **Claim pointer** The authors used ColabFold to generate initial models for the unknown rRop sequence, which yielded both parallel and antiparallel monomeric orientations.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not specify the confidence scores of the ColabFold predictions, the criteria for selecting the models, or whether the predicted orientations were validated against any experimental or known structural data.  
- **Why it matters** The initial models serve as the starting point for all subsequent simulations. If the models are of low confidence or incorrectly oriented, the downstream results may be biased.  
- **Resolution test** Report ColabFold confidence metrics (e.g., pLDDT, PAE), describe the model selection criteria, and discuss any validation of the predicted orientations.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Definition of collective variables  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The four collective variables are listed but not defined precisely. For example, "torsion angle similarity" is ambiguous.  
- **Required correction** Provide explicit mathematical definitions or references for each collective variable.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Simulation details  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No information is given about force field, water model, simulation temperature, or simulation length.  
- **Required correction** Include these details in the methods section of the full manuscript.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Conformational similarity claim  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The claim that the parallel variant shares greater conformational similarity with the parent protein is stated without specifying the metric used to define similarity.  
- **Required correction** Define the similarity metric (e.g., RMSD, contact map overlap) and report the corresponding values.

## Risk / unsupported claims
- The claim that both rRop models "stabilize at an intermediate angle" is unsupported without free energy data and error analysis.
- The claim that the antiparallel variant exhibits "the most significant instability" is unsupported without quantitative comparisons.
- The claims regarding disrupted hydrogen bond network, increased solvent-accessible surface area, and compromised hydrophobic core are unsupported without numerical data.
- The claim that the parallel variant shares "greater conformational similarity" with the parent protein is unsupported without a defined similarity metric.
- The overall reliability of the ColabFold-generated models cannot be assessed without confidence scores or validation.