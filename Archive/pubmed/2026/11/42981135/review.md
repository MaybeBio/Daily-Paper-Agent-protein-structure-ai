## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors combine pan-cancer histone mutation profiling with 31.5 microseconds of all-atom molecular dynamics simulations of complete nucleosomes to study recurrent mutations in H2A, H2B, H3, and H4 tails. They report mutation-specific redistribution of tail-DNA contacts, changes in MM/GBSA-derived relative interaction-energy estimates, and Markov state modeling results showing altered metastable tail-DNA contact states. They conclude that cancer-associated histone-tail mutations reshape conformational and interaction-state landscapes in nucleosomes.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, mutation selection rationale, statistical analyses, Markov state model validation, and all quantitative results

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational study addressing an important gap in understanding how noncanonical histone tail mutations affect nucleosome dynamics. The scale of simulations (31.5 microseconds total) is substantial and the focus on understudied mutation sites beyond canonical H3 oncohistones is timely. However, the abstract alone provides insufficient detail to evaluate technical rigor, statistical robustness, or biological significance. Several claims are stated without quantitative support, and the relationship between simulation-derived observables and functional relevance remains unclear.
- **Who would be interested in the results, and why** Researchers in chromatin biology, epigenetics, computational biophysics, and cancer genomics would be interested. The work connects cancer-associated mutations to physical changes in nucleosome dynamics, which could inform understanding of chromatin dysregulation in cancer and guide future experimental studies on oncohistone mechanisms.
- **Major strengths** The study addresses a poorly understood area by extending beyond canonical H3 mutations to include H2A, H2B, and H4 tails. The simulation scale (31.5 microseconds) is substantial for complete nucleosome systems. The combination of pan-cancer profiling with molecular dynamics and Markov state modeling provides a multi-layered approach to characterize mutation effects.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The abstract claims that simulations "reveal mutation-specific redistribution of tail-DNA contacts across the nucleosomal DNA surface" and that Markov state modeling "resolves metastable tail-DNA contact states."  
  - **Evidence pointer** Abstract only; no figures or quantitative results provided  
  - **Concern** The abstract provides no quantitative metrics for the claimed redistribution of tail-DNA contacts, no statistical significance measures, and no convergence assessment for the simulations. For Markov state modeling, no validation details are given (e.g., implied timescales, Chapman-Kolmogorov tests, or state count selection). Without these, the robustness of the reported conformational states and their population distributions cannot be evaluated.  
  - **Why it matters** Molecular dynamics results are only meaningful if simulations are converged and analyses are statistically sound. The absence of any convergence or validation information makes it impossible to determine whether the observed differences between mutant and wild-type systems reflect genuine physical effects or simulation artifacts.  
  - **Resolution test** Provide convergence metrics (e.g., RMSD stabilization, block error analysis), statistical tests comparing contact distributions between systems, and Markov state model validation (implied timescale plots, model selection criteria, and uncertainty estimates for state populations).

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Scientific importance  
  - **Claim pointer** The abstract states that "recurrent and understudied mutation sites beyond canonical H3 oncohistones" are identified and that selected substitutions perturb tail conformational ensembles and DNA contacts.  
  - **Evidence pointer** Abstract only; no mutation list or selection criteria provided  
  - **Concern** The abstract does not specify which mutations were studied, how they were selected from the pan-cancer profiling, or what criteria defined "recurrent" and "understudied." Without this information, the biological relevance of the chosen mutations cannot be assessed, and the generalizability of the findings to the broader landscape of cancer-associated histone mutations remains unclear.  
  - **Why it matters** The study's significance depends on whether the selected mutations are clinically relevant and whether they represent a meaningful class of alterations. If the selection criteria are arbitrary or biased, the conclusions may not extend beyond the specific systems simulated.  
  - **Resolution test** List the specific mutations studied, their cancer-type frequencies, and the rationale for selection. Provide evidence that these mutations are understudied in the context of nucleosome dynamics.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Technical soundness  
  - **Claim pointer** The abstract states that "changes in MM/GBSA-derived relative interaction-energy estimates" accompany the contact redistribution.  
  - **Evidence pointer** Abstract only; no energy values or error estimates provided  
  - **Concern** MM/GBSA calculations are known to be sensitive to the choice of internal dielectric constant, entropy contributions, and the conformational ensemble used. The abstract provides no details on the MM/GBSA protocol, no error estimates, and no comparison to alternative methods. The word "estimates" suggests uncertainty, but the magnitude and direction of changes are not reported.  
  - **Why it matters** Interaction-energy estimates are used to support the physical interpretation of mutation effects. If the MM/GBSA results are not robust or are presented without uncertainty quantification, they cannot substantiate the claim that mutations alter interaction networks in a meaningful way.  
  - **Resolution test** Provide MM/GBSA values with standard errors, describe the protocol (including dielectric constant and entropy treatment), and show that conclusions are robust to methodological choices.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Readability for nonspecialists  
  - **Affected element** Abstract text  
  - **Evidence pointer** Abstract  
  - **Issue** The phrase "conformational ensembles" and "interaction-state landscapes" is used without defining what these mean in practical terms for a reader unfamiliar with molecular dynamics terminology.  
  - **Required correction** Briefly define these terms or provide a concrete example of what a "redistribution of tail-DNA contacts" means structurally.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Scientific importance  
  - **Affected element** Abstract text  
  - **Evidence pointer** Abstract  
  - **Issue** The abstract does not state whether the observed perturbations are expected to have functional consequences (e.g., altered transcription factor access, chromatin compaction, or post-translational modification crosstalk).  
  - **Required correction** Add one sentence connecting the physical changes to potential biological outcomes, even if speculative.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Technical soundness  
  - **Affected element** Abstract text  
  - **Evidence pointer** Abstract  
  - **Issue** The abstract mentions "neighboring interaction networks" are affected but does not specify the spatial or sequence range of these effects.  
  - **Required correction** Clarify whether the effects are local (within a few residues) or propagate over longer distances along the histone tail or nucleosome surface.

- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation convergence and statistical validation), R1-M2 (mutation selection rationale and biological relevance), R1-M3 (MM/GBSA protocol and uncertainty quantification)

## Risk / unsupported claims
- The claim that mutations "reshape conformational and interaction-state landscapes" is not supported by quantitative evidence in the abstract.
- The claim that the study provides "a molecular-level physical picture" is premature without demonstration of simulation convergence and model validation.
- The biological relevance of the selected mutations cannot be assessed without the mutation list and selection criteria.
- The generalizability of findings to "many noncanonical mutations" is not established from the abstract alone.

## Assessment against Nature-style criteria
- **Originality** The focus on noncanonical histone tail mutations beyond H3 is a valuable extension of existing oncohistone research. The combination of pan-cancer profiling with long-timescale simulations is not entirely novel but is applied to an underexplored problem.
- **Scientific importance** Potentially high if the findings reveal general principles of how histone tail mutations perturb nucleosome dynamics. However, the abstract does not yet demonstrate that the observed effects are biologically consequential or generalizable.
- **Interdisciplinary readership** The topic bridges cancer genomics, chromatin biology, and computational biophysics, which could attract a broad audience. The abstract is accessible but lacks the specificity needed to engage experts in any single field.
- **Technical soundness** Cannot be assessed from the abstract. The absence of convergence metrics, statistical validation, and methodological details is a critical gap.
- **Readability for nonspecialists** The abstract is generally clear but uses jargon without definition. The significance of the findings for a general scientific audience is not articulated.

## Recommendation posture
Currently not established from the provided evidence. The abstract describes a potentially valuable study, but the absence of quantitative results, methodological details, and validation makes it impossible to assess whether the claims are supported. If the full manuscript addresses the technical concerns (convergence, statistical rigor, mutation selection rationale) and provides clear quantitative evidence, the work could be considered for publication. However, based on the abstract alone, the case is not made.