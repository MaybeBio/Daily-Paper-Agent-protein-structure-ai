## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, or supplementary material were provided
- **Shared manuscript claim summary** The authors report all-atom molecular dynamics simulations of a 12-residue p53 CTD fragment at varying distances from the S100B binding cleft, in pure water versus 150 mM NaCl. They claim that at 10 Å from the native binding surface, the peptide forms stable bound-like helical segments only in salt, that this effect is distance-dependent and surface-specific, and that it arises from a structured long-range electrostatic microenvironment created by ions organized on the negatively charged S100B surface, without direct protein-IDR contacts.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or simulation parameters were provided
- **Missing materials affecting confidence** Full methods, simulation setup details, force field parameters, convergence criteria, statistical analyses, conformational ensemble data, free energy calculations, and all figures or tables

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting hypothesis regarding salt-mediated long-range electrostatic effects on IDR conformational pre-organization. However, the evidence base is limited to a summary of findings without any quantitative data, methodological detail, or statistical validation. The central claims, while plausible, cannot be evaluated for technical soundness or robustness from the supplied material. The concept of ions as active participants in molecular recognition is not new, but the specific claim of a surface-templated ion organization that pre-organizes bound-like conformations at a distance without direct contact is a distinctive proposition that warrants careful examination.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, coupled folding and binding mechanisms, electrostatic effects in biomolecular recognition, and ion-specific effects in protein interactions. The work may also interest computational biophysicists developing simulation approaches for IDP systems and experimentalists investigating salt-dependent binding kinetics.
- **Major strengths** The hypothesis is clearly articulated and mechanistically specific. The use of a confinement setup to isolate distance-dependent effects is a creative methodological choice. The claim of a synergistic effect between surface topology and physiological salt is conceptually interesting and could have broad implications for understanding IDR binding in cellular environments.
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
  Originality: The specific claim of a long-range, salt-mediated, surface-templated electrostatic pre-organization is a distinctive contribution, though the broader concept of ion-mediated IDP behavior is established.  
  Scientific importance: If substantiated, the findings could inform understanding of IDR binding mechanisms under physiological conditions, which is of moderate to high importance.  
  Interdisciplinary readership: The topic bridges biophysics, computational chemistry, and molecular recognition, with potential appeal to a broad readership.  
  Technical soundness: Cannot be assessed from the abstract alone; no methodological details, convergence analyses, or statistical validations are provided.  
  Readability for nonspecialists: The abstract is reasonably clear, though terms such as "confinement setup" and "long-range electrostatic microenvironment" would benefit from brief contextual explanation.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and worth pursuing, but the abstract alone does not provide sufficient quantitative or methodological support to assess the validity of the central claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that at 10 Å from the native binding surface, the peptide spontaneously forms stable, bound-like helical segments exclusively in the salt solution.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative measure of helicity, no definition of "stable" or "bound-like," no statistical comparison between conditions, and no indication of simulation length, number of replicates, or convergence criteria. Without these details, the claim of exclusivity in salt cannot be evaluated.  
- **Why it matters** The central finding rests on a comparative observation between two conditions. If the simulations are under-sampled, insufficiently converged, or the helical propensity metric is not rigorously defined, the conclusion may be an artifact of limited sampling or subjective criteria.  
- **Resolution test** Provide helicity time series, ensemble averages with error bars, replicate information, and a clear operational definition of "bound-like helical segments" with a threshold justified by structural comparison to the bound state.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the effect is distance-dependent, vanishing at 20 Å, and specific to the native binding surface.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No data are shown for the 20 Å condition or for any non-native surface control. The claim of surface specificity requires a comparison against a negatively charged but non-native surface or a surface with different topology. Without such controls, the attribution of the effect to the native surface topology is unsupported.  
- **Why it matters** The mechanistic interpretation depends on distinguishing surface-specific effects from generic ionic strength effects on IDP helicity. If the effect occurs near any charged surface, the claim of native surface specificity is overstated.  
- **Resolution test** Provide comparative simulations at 20 Å and at equivalent distances from a control surface with similar charge density but different topology, with quantitative helicity comparisons.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic support  
- **Claim pointer** The authors claim that the negatively charged S100B surface organizes solvated ions into a structured, long-range electrostatic microenvironment that thermodynamically stabilizes bound-like helical conformations.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No evidence is presented for ion organization, the structure of the proposed microenvironment, or thermodynamic stabilization. The abstract states the mechanism as a result without showing ion density maps, radial distribution functions, free energy profiles, or any thermodynamic quantity.  
- **Why it matters** The proposed mechanism is the core explanatory claim of the work. Without direct evidence of ion structuring and its thermodynamic consequence, the mechanism remains speculative.  
- **Resolution test** Provide ion density maps or distribution functions around the S100B surface, free energy calculations for helix formation in the presence and absence of salt, and a demonstration that the proposed ion organization correlates with the observed conformational bias.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability  
- **Claim pointer** The authors imply that the observed effect facilitates binding of the full-length p53 CTD to S100B.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The simulations use a 12-residue fragment, not the full CTD. The abstract does not address whether the fragment behavior extrapolates to the full-length IDR, which may have additional intramolecular interactions, different effective local concentrations, or altered electrostatic context.  
- **Why it matters** The broader significance claim depends on relevance to the full biological system. If the fragment behaves differently from the full CTD, the conclusions may not transfer.  
- **Resolution test** Provide simulations or experimental data on the full-length CTD or a longer construct, or explicitly discuss and justify the fragment as a representative model with supporting evidence.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Methods description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "novel confinement setup" is not explained. It is unclear whether this refers to spatial restraints, a simulation box design, or an enhanced sampling approach.  
- **Required correction** Briefly describe the confinement setup in the abstract or refer to a methods section with sufficient detail for readers to understand the approach.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Simulation parameters  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No force field, water model, salt model, temperature, or pressure conditions are stated. These parameters are critical for reproducing ion-specific and electrostatic effects.  
- **Required correction** Include force field and simulation condition details in the methods or supplementary information.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical rigor  
- **Affected element** Sampling  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No information is given on the number of independent simulations, total simulation time, or whether the observed helical conformations are transient or persistent across replicates.  
- **Required correction** Report replicate counts, total simulation times, and measures of statistical uncertainty for the reported observables.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Mechanistic language  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "identifying the ions in the solution as active participants in molecular recognition" is a strong interpretive statement. The data may support a thermodynamic bias, but "active participants" implies a specific mechanistic role that may exceed the evidence.  
- **Required correction** Soften the language to reflect that ions contribute to the conformational bias, unless direct evidence of ion-mediated recognition events is provided.

## Risk / unsupported claims
- The claim that the effect is "specific to the native binding surface" is unsupported without control surface simulations.
- The claim of a "structured, long-range electrostatic microenvironment" is unsupported without ion distribution or correlation data.
- The claim of "thermodynamic stabilization" is unsupported without free energy calculations.
- The extrapolation from a 12-residue fragment to the full-length p53 CTD binding behavior is not justified.
- The claim that the effect "facilitates binding" is inferential and not directly tested.