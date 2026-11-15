## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report that the CPVT1-associated hRyR2 mutation S616L, located in the alpha-helical NSol region of the N-terminal domain near a three-way domain junction, weakens the NTD/BSol interface via altered residue conformations and promotes a slight domain opening, based on molecular dynamics simulation. They also report that the mutation slightly increases the thermal stability of a 655-residue NTD-containing fragment, based on biophysical and biochemical assays.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, statistical analyses, or experimental details are provided
- **Missing materials affecting confidence** Full manuscript, methods section, simulation setup and force field parameters, convergence criteria, experimental protocols, raw data, figures, tables, statistical analyses, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a focused and potentially interesting study on a clinically relevant mutation in hRyR2, combining computational and experimental approaches. However, the evidence base is limited to a brief summary, and the core claims regarding interface weakening, domain opening, and thermal stability changes cannot be independently evaluated without the full methods and data. The study's significance is plausible given the link to CPVT1, but the current abstract does not provide sufficient detail to assess technical rigor or the robustness of the conclusions.
- **Who would be interested in the results, and why** Researchers in cardiac electrophysiology, calcium signaling, and ryanodine receptor biology would be interested, as the study addresses a disease-associated mutation in a key cardiac calcium release channel. Structural biologists and computational biophysicists studying protein dynamics and domain interfaces may also find the simulation approach relevant. Clinicians or geneticists focused on CPVT1 genotype-phenotype correlations could benefit from mechanistic insights into a specific mutation.
- **Major strengths** The study addresses a clinically relevant mutation with a clear mechanistic hypothesis. The combination of molecular dynamics simulation with experimental biophysical characterization is a complementary approach that can strengthen conclusions. The focus on a specific domain junction provides a targeted structural context for interpreting mutation effects.
- **Major Concerns** 
  - R1-M1: The abstract claims that S616L "slightly weakens the interface" and "promotes a slight opening" between NTD and BSol, but no quantitative metrics (e.g., binding free energy changes, distance or angle distributions, statistical significance) are provided. The magnitude of the effect and its reproducibility across simulation replicates are not assessable.
  - R1-M2: The claim that the mutation "slightly increases the thermal stability" of the NTD fragment is reported without any experimental details, such as the assay used (e.g., differential scanning fluorimetry, circular dichroism), the measured melting temperatures, or the error and replicate numbers. The direction of the effect is counterintuitive given the proposed destabilizing interface change, and this discrepancy is not addressed.
  - R1-M3: The abstract does not specify the simulation length, number of replicates, force field, or water model, nor whether the system reached equilibrium. Without these details, the reliability of the simulation-based conclusions cannot be evaluated.
- **Minor Comments** 
  - R1-m1: The abstract does not state how the 655-residue fragment was designed or whether it includes all relevant interacting domains. Clarification of the fragment boundaries and their relevance to the full-length receptor would help.
  - R1-m2: The phrase "changing the preferred conformation of the residues at the interface" is vague. The authors should specify which residues and what conformational change is observed.
  - R1-m3: The abstract does not mention whether the simulation findings were validated against any experimental structural data or whether the observed opening is within thermal fluctuations.
  - R1-m4: The clinical relevance of the "slight" changes is not discussed. The authors should comment on whether such subtle effects are consistent with the pathogenicity of S616L.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of MD to a specific CPVT1 mutation is not novel in itself, but the focus on a three-way domain junction may offer a new perspective. However, the abstract does not demonstrate a unique conceptual advance.
  - Scientific importance: Moderate. The findings could inform understanding of CPVT1 mechanisms, but the reported effects are "slight" and their functional significance is unclear. The importance is not established from the abstract alone.
  - Interdisciplinary readership: Limited. The study is primarily of interest to specialists in calcium channel biology and computational biophysics. The abstract does not frame the work for a broader audience.
  - Technical soundness: Not assessable. The absence of methodological details and quantitative data prevents evaluation of the technical rigor.
  - Readability for nonspecialists: The abstract is reasonably clear but uses domain-specific terminology (e.g., NSol, JSol, BSol) without sufficient context for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valid study, but the lack of quantitative results and methodological details means the core claims cannot be verified. A revised version with full data and methods would be needed to assess whether the case is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The mutation "slightly weakens the interface between the N-terminal domain and the bridging solenoid" and "promotes a slight opening between these domains."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no quantitative measures of interface strength or domain opening. Terms like "slightly weakens" and "slight opening" are subjective and cannot be evaluated without data such as interaction energies, residue contact maps, or distance trajectories. It is unclear whether the observed changes are statistically significant or within simulation noise.
- **Why it matters** The central mechanistic claim of the study depends on demonstrating a reproducible and meaningful change in the NTD/BSol interface. Without quantitative evidence, the conclusion is unsupported and could be an artifact of insufficient sampling or force field artifacts.
- **Resolution test** Provide quantitative metrics (e.g., free energy differences, contact probabilities, or domain separation distances) with error bars and statistical tests across multiple independent simulation replicates. Show that the observed changes exceed thermal fluctuations and are consistent across replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The mutation "slightly increases the thermal stability of the fragment."
- **Evidence pointer** Abstract text; location not provided
- **Concern** No experimental details are given for the thermal stability measurement. The assay type, buffer conditions, protein concentration, melting temperature values, and replicate numbers are absent. Moreover, the direction of the effect (increased stability) appears inconsistent with the proposed interface weakening, and this discrepancy is not explained.
- **Why it matters** The experimental result is a key part of the study's evidence base. Without proper controls and statistical analysis, the claim of increased thermal stability cannot be verified, and the apparent contradiction with the simulation finding raises questions about the interpretation.
- **Resolution test** Report the specific assay, raw melting temperatures (with standard deviations and replicates), and a statistical comparison between wild-type and mutant. Discuss how increased fragment stability is reconciled with the proposed interface destabilization, or provide a mechanistic explanation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The study uses "molecular dynamics simulation" to study the mutation's effect.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract omits critical simulation parameters, including the simulation length, number of replicates, force field, water model, temperature and pressure coupling, and system size. It is also unclear whether the system reached equilibrium and whether the results are converged.
- **Why it matters** Molecular dynamics results are highly sensitive to simulation setup and sampling. Without these details, the reliability and reproducibility of the simulation-based conclusions cannot be assessed, and the claim of a "slight opening" may be an artifact of insufficient sampling.
- **Resolution test** Provide full simulation methods, including software, force field, water model, ion concentration, simulation time, number of replicates, and convergence checks (e.g., RMSD stability, block averaging). Show that the observed interface changes are consistent across replicates and time periods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Experimental design
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not describe how the 655-residue fragment was constructed or whether it includes the full NTD and any adjacent domains that might influence stability.
- **Required correction** Specify the fragment boundaries, the rationale for this construct, and whether it recapitulates the relevant interactions in the full-length receptor.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Precision
- **Affected element** Mechanistic description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "changing the preferred conformation of the residues at the interface" is imprecise. It is unclear which residues are affected and what conformational change is observed.
- **Required correction** Identify the specific residues and describe the conformational change (e.g., rotamer shifts, side-chain reorientation) with supporting data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Simulation-experiment integration
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not discuss whether the simulated domain opening is consistent with the experimental thermal stability result or whether the two findings are independent.
- **Required correction** Add a brief statement reconciling the simulation and experimental results, or explicitly note that they address different aspects of the mutation's effect.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Significance
- **Affected element** Clinical relevance
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not connect the "slight" structural and stability changes to the pathogenic mechanism of CPVT1.
- **Required correction** Discuss how the observed changes might contribute to channel dysfunction, or state that the functional consequences remain to be determined.

## Risk / unsupported claims
- The claim that S616L "slightly weakens the interface" and "promotes a slight opening" is unsupported due to the absence of quantitative simulation data.
- The claim that the mutation "slightly increases the thermal stability" is unsupported due to the absence of experimental details and statistical analysis.
- The overall relevance of the findings to CPVT1 pathogenesis is not established from the abstract alone.