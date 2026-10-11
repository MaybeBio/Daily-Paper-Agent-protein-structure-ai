## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that homologs of MdDOX-Co, a 2-oxoglutarate-dependent dioxygenase previously shown to catalyze atypical GA 12alpha-hydroxylation, display functional divergence within the DOXC41 clade. Phylogenetic, biochemical, and computational analyses identify two functional types with distinct GA hydroxylation regioselectivity. A single-residue substitution (T214P) is reported to switch catalytic activity from 12alpha-hydroxylation to 2beta-hydroxylation.
- **Visible evidence base** Phylogenetic analyses, recombinant enzyme biochemical assays, GC-MS detection, enzyme structure predictions, molecular docking, molecular dynamics simulations, and a site-directed variant (T214P) characterized biochemically. Specific data are not shown in the abstract.
- **Missing materials affecting confidence** Full methods, quantitative activity data, phylogenetic tree details, structural model validation metrics, MD simulation parameters and convergence criteria, GC-MS chromatograms, and kinetic parameters for the variant. None of these are available from the abstract alone.

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting finding regarding functional divergence in a less-studied GA metabolic clade and proposes a structural mechanism for regioselectivity switching. The claim of a single-residue switch is compelling but rests on a limited set of experiments described only at summary level. The evidence base is insufficient to fully evaluate the robustness of the phylogenetic assignment, the biochemical characterization, or the computational predictions. The work may be of interest to specialists in plant hormone metabolism and 2ODG enzymology, but the current abstract does not provide enough detail to assess technical soundness or the strength of the causal claim.
- **Who would be interested in the results, and why** Researchers studying gibberellin biosynthesis and catabolism, plant hormone metabolic enzymes, 2-oxoglutarate-dependent dioxygenase structure-function relationships, and enzyme evolution. The proposed single-residue switch could be of interest to those working on enzyme engineering or directed evolution of dioxygenases.
- **Major strengths** The study addresses a clear gap in understanding the structural basis of regioselectivity in a novel GA hydroxylase clade. The combination of phylogenetic, biochemical, and computational approaches is appropriate for the question. The identification of a specific residue and validation through a variant is a strong experimental design.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide quantitative evidence for the claimed switch. Without kinetic parameters, product identity confirmation, or structural validation of the predicted models, the single-residue switch claim cannot be fully assessed. The phylogenetic support for the two functional types is not described.
- **Assessment against Nature-style criteria**  
  Originality: The finding of a single-residue switch in a novel GA metabolic clade is potentially original, but the abstract does not demonstrate how this advances beyond existing knowledge of GA2ox structure-function relationships.  
  Scientific importance: The work could be important for understanding GA metabolic diversity, but the broader significance is not articulated beyond the clade itself.  
  Interdisciplinary readership: The topic is likely to appeal mainly to plant biochemists and enzymologists; the abstract does not frame the work for a broader audience.  
  Technical soundness: Cannot be assessed from the abstract. The absence of quantitative data and methodological details prevents evaluation of the reliability of the biochemical and computational results.  
  Readability for nonspecialists: The abstract is concise and generally clear, but terms such as DOXC41 and 2beta-hydroxylation may be opaque to nonspecialists without additional context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but does not provide sufficient detail to support the central claim of a single-residue switch. Full data are required for a definitive assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that a single-residue switch (T214P) shifted the catalytic activity of MdDOX-Co from 12alpha-hydroxylation to 2beta-hydroxylation.  
- **Evidence pointer** Abstract only; no quantitative data provided  
- **Concern** The abstract states that a synthesized variant with the T214P substitution shifted activity, but no data are shown to support the extent of the shift, the product profile, or the activity levels of the variant relative to the wild-type enzyme.  
- **Why it matters** A single-residue switch is a strong mechanistic claim. Without quantitative evidence such as product ratios, kinetic parameters, or at least representative chromatograms, the claim cannot be evaluated. The possibility of partial or residual activity is not addressed.  
- **Resolution test** Provide quantitative data comparing wild-type and variant activities, including product identification by GC-MS, relative product yields, and kinetic parameters if measurable.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Computational validation  
- **Claim pointer** The authors state that enzyme structure predictions, molecular docking, and MD simulations identified a key residue that distinguishes the two activities.  
- **Evidence pointer** Abstract only; no structural or simulation details provided  
- **Concern** The abstract does not describe the quality of the predicted structures, the docking scores, or the MD simulation parameters and convergence. Without these details, the reliability of the computational identification of T214 as the key residue is unclear.  
- **Why it matters** The computational results are used to rationalize the biochemical switch. If the structural models are inaccurate or the simulations are not robust, the proposed mechanism may be incorrect.  
- **Resolution test** Provide validation metrics for the predicted structures, docking results, and MD simulation convergence and stability data. Show that the identified residue is consistently supported across multiple independent simulations or structural analyses.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Phylogenetic support  
- **Claim pointer** The authors claim that MdDOX-Co homologs branch into two functional types based on hydroxylation site.  
- **Evidence pointer** Abstract only; phylogenetic tree not shown  
- **Concern** The abstract states that phylogenetic analyses revealed two functional types, but no information is given on the number of homologs analyzed, the statistical support for the clades, or the correlation between phylogenetic grouping and functional activity.  
- **Why it matters** The evolutionary interpretation depends on a robust phylogeny. If the clade assignments are weakly supported or the functional data are limited to a few homologs, the claim of functional divergence may be overstated.  
- **Resolution test** Show the phylogenetic tree with support values, list the homologs tested for activity, and demonstrate that the functional types correspond to well-supported clades.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract  
- **Issue** The term "2beta-hydroxylation" is used without explaining its relationship to GA inactivation, which may be unclear to readers unfamiliar with GA metabolism.  
- **Required correction** Briefly define 2beta-hydroxylation as the canonical GA inactivation step or provide a one-sentence context.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** Generalizability  
- **Evidence pointer** Abstract  
- **Issue** The abstract does not state how many homologs were characterized biochemically, so the breadth of the functional divergence claim is unclear.  
- **Required correction** Specify the number of homologs tested and the distribution of activities across the clade.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Significance framing  
- **Evidence pointer** Abstract  
- **Issue** The broader implications of a single-residue switch for understanding GA metabolic evolution or for enzyme engineering are not stated.  
- **Required correction** Add one sentence on the potential implications for understanding enzyme evolution or for engineering GA hydroxylases.

## Risk / unsupported claims
- The claim that T214P shifts activity from 12alpha-hydroxylation to 2beta-hydroxylation is unsupported by quantitative data in the abstract.
- The claim that computational methods identified the key residue is not verifiable without structural and simulation details.
- The claim of two functional types within the DOXC41 clade is not supported by visible phylogenetic or biochemical data.
- The generalizability of the findings beyond the specific homologs tested is not assessable from the abstract.