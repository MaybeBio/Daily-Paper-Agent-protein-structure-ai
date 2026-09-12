## Review setup
- **Input scope** Full manuscript (abstract + main text + figures/tables not provided)
- **Assessment boundary** Only the abstract and metadata provided; no main text, figures, tables, or supplementary materials are available.
- **Shared manuscript claim summary** The authors used AlphaFold2 to predict structures of seven MPXV proteins, performed virtual screening of 6405 drugs against these targets, and experimentally validated three hit compounds (cepharanthine, eltrombopag, simeprevir) against A35R via SPR, obtaining micromolar KD values. They claim this establishes an AI-driven framework for rapid drug screening against emerging viral threats.
- **Visible evidence base** Abstract only; no experimental data, docking scores, MD simulation results, or structural models are visible.
- **Missing materials affecting confidence** Main text, all figures, tables, supplementary data, SPR sensorgrams, MD trajectories, docking score distributions, and any statistical analyses are absent. The assessment is severely limited.

## Reviewer
- **Overall assessment** The abstract presents a logical workflow combining AI structure prediction, virtual screening, and experimental validation for MPXV drug repurposing. The identification of three compounds with micromolar binding to A35R is a plausible starting point. However, the absence of any primary data, methodological details, or control experiments in the provided material makes it impossible to evaluate the technical soundness, reproducibility, or significance of the findings. The authors are appropriately cautious about the lack of antiviral activity data, but the core claims of "high-accuracy structures" and "measurable binding signals" cannot be verified from the abstract alone.
- **Who would be interested in the results, and why** Researchers in antiviral drug discovery, computational structural biology, and emerging infectious disease preparedness would be interested. The integrated AI-screening-validation pipeline could serve as a template for rapid response to novel viral threats, and the identified compounds may be starting points for further optimization.
- **Major strengths** 1. The combination of AlphaFold2 structure prediction with large-scale virtual screening and experimental SPR validation is a modern, integrated approach. 2. The authors explicitly acknowledge the limitations (no antiviral activity demonstrated), which is scientifically honest. 3. The focus on both polymerase and surface proteins provides a broad target set.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Data availability and reproducibility
    - **Claim pointer** "Using AlphaFold2, we predicted high-accuracy structures for seven essential MPXV proteins"
    - **Evidence pointer** Abstract; no structural models or validation metrics provided
    - **Concern** The claim of "high-accuracy structures" is unsupported. No pLDDT scores, predicted aligned error (PAE) plots, or comparison to experimental structures (if available) are presented. Without these, the quality of the predicted models cannot be assessed.
    - **Why it matters** Docking accuracy is critically dependent on target structure quality. If the predicted structures are inaccurate, the entire virtual screening pipeline is compromised.
    - **Resolution test** Provide pLDDT scores for all seven models, PAE plots, and, if possible, superimposition with any available experimental structures or cryo-EM maps. Show that the binding sites are well-predicted.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental validation rigor
    - **Claim pointer** "Three compounds... exhibited measurable A35R‑associated binding signals with equilibrium dissociation constants (KD) in the micromolar range"
    - **Evidence pointer** Abstract; no SPR data, sensorgrams, or binding curves provided
    - **Concern** The SPR data are not shown. Key experimental details are missing: protein purity, immobilization method, buffer conditions, concentration series, fitting model, and whether the binding is specific or due to nonspecific interactions. Micromolar KD values are weak and could arise from artifacts.
    - **Why it matters** Without raw data and controls (e.g., negative control compounds, blank surface, or known binders), the claim of measurable binding is not substantiated. The field requires rigorous biophysical validation for hit compounds.
    - **Resolution test** Provide representative SPR sensorgrams, steady-state binding curves, fitting residuals, and a table of KD values with errors. Include a negative control compound and a control surface.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Novelty and prior art
    - **Claim pointer** "Notably, all three have been previously reported to target other MPXV proteins, reinforcing their potential for repurposing."
    - **Evidence pointer** Abstract; no references or prior data provided
    - **Concern** The abstract states these compounds are already known to target other MPXV proteins, but no details are given. This raises questions about the novelty of the finding: are the authors simply confirming known promiscuous binders? The lack of citation or comparison to prior work makes it impossible to assess the incremental contribution.
    - **Why it matters** If these compounds are already well-characterized as MPXV binders, the new contribution (binding to A35R) may be incremental. The field needs to know whether this is a novel target for these drugs or a rediscovery.
    - **Resolution test** Clearly cite the prior reports, discuss the overlap, and explain what new information the current study adds (e.g., first demonstration of A35R binding, or improved affinity).

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness
    - **Affected element** Target selection rationale
    - **Evidence pointer** Abstract
    - **Issue** The abstract lists "three polymerase-related and four surface proteins" but does not explain why these seven were chosen over other MPXV proteins. The rationale for focusing on A35R for experimental validation is also unclear.
    - **Required correction** Briefly state the selection criteria (e.g., essential for viral replication, druggability, structural coverage) and why A35R was prioritized.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Methodological detail
    - **Affected element** Virtual screening protocol
    - **Evidence pointer** Abstract
    - **Issue** The abstract mentions "molecular docking" but does not specify the docking software, scoring function, or whether any consensus scoring or enrichment analysis was performed.
    - **Required correction** Provide the name of the docking program and key parameters in the abstract or main text.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Docking score dataset
    - **Evidence pointer** Abstract
    - **Issue** The abstract reports "44,835 drug-protein pairs" but does not indicate the distribution of scores, the cutoff used for "high-scoring," or how the 26 compounds for SPR were selected from this large set.
    - **Required correction** Clarify the selection criteria for the 26 compounds (e.g., top N by score, diversity selection, or manual curation).

- **Technical failings that need to be addressed before the case is established** R1-M1 (structure quality), R1-M2 (SPR data and controls). Without these, the core claims of accurate structure prediction and validated binding are not established.

- **Assessment against Nature-style criteria** 
    - **Originality**: Moderate. The combination of AlphaFold2 + virtual screening + SPR is not novel per se, but the application to MPXV A35R and the specific hit compounds may have some novelty. However, the prior knowledge of these compounds targeting other MPXV proteins reduces originality.
    - **Scientific importance**: Potentially high if the compounds show antiviral activity, but the abstract explicitly states no antiviral activity has been demonstrated. The current work is a preliminary screening, not a definitive discovery.
    - **Interdisciplinary readership**: The topic (MPXV drug repurposing) is of broad interest to virologists, computational chemists, and public health researchers. However, the lack of functional data limits appeal.
    - **Technical soundness**: Cannot be assessed from the abstract alone. The missing structural validation and SPR data are critical gaps.
    - **Readability for nonspecialists**: The abstract is clear and well-structured, with appropriate caveats. It is accessible to a broad scientific audience.

- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible workflow, but the absence of primary data, structural validation, and experimental controls means the claims cannot be evaluated. A full manuscript with all supporting data is required for a meaningful assessment.