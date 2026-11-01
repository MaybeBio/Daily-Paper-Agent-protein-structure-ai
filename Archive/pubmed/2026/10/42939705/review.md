## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions, Acknowledgments). Supplementary items referenced but not supplied.
- **Assessment boundary** Assessment is restricted to the supplied manuscript text. All Supplementary Material (Table S1, Figures S1–S5) and any raw data, spectra, or statistical files are unavailable and therefore cannot be verified.
- **Shared manuscript claim summary** The authors report that (i) AI-based structure prediction plus MD and docking suggest the SUMO tag can sterically occlude IL-33 receptor-binding interfaces in a model-dependent manner; (ii) intact SUMO-IL-33 shows only 12.0% molar epitope recognition by sandwich ELISA versus 87.6% for cleaved IL-33; (iii) an optimized cleavage protocol (1.0% mol/mol SUMO protease, 4 °C, 1 h) plus subtractive IMAC yields 38.56 mg native IL-33 from 203.35 mg fusion input (~19% mass, ~32.6% molar recovery); and (iv) tag removal is operationally necessary for IL-33 functional availability in screening.
- **Visible evidence base** Main-text descriptions of modeling (I-TASSER, C-I-TASSER, AlphaFold2, AlphaFold3, RoseTTAFold), MD (GROMACS, CHARMM27/TIP3P, 200 ns × 3 plus 100 ns AlphaFold3), HADDOCK docking, SDS-PAGE cleavage optimization, subtractive IMAC recovery, Bradford quantification, and sandwich ELISA. Quantitative values are reported in the text; the corresponding figures (Figures 1–7), Table 1, Table 2, and all Supplementary items are referenced but not included in the supplied material.
- **Missing materials affecting confidence** Supplementary Table S1, Figures S1–S5, the primary Figures 1–7 and Tables 1–2 as actual data objects, raw ELISA and Bradford datasets, replicate counts and dispersion statistics, SDS-PAGE gel images, and the docking/MD parameter files. These are needed to verify the central quantitative claims.

## Reviewer
- **Overall assessment** The manuscript addresses a practical and legitimate bottleneck in IL-33/ST2 drug-discovery workflows, namely whether an intact SUMO fusion can substitute for tag-cleaved cytokine in screening assays. The combination of structural modeling with an empirical bioprocess readout is a reasonable framing, and the ELISA comparison (12.0% versus 87.6% molar epitope recognition) is the strongest and most decision-relevant element. However, the computational arm is explicitly exploratory and self-acknowledged as model-dependent, the docking comparison is a single-snapshot analysis with a small ΔG difference, and the recovery and purity claims rest on figures and tables that are not available for inspection. As presented, the bioprocess conclusion is plausible but not yet independently verifiable, and the structural conclusion is presented with more confidence than the underlying sampling supports.

- **Who would be interested in the results, and why** Groups producing recombinant IL-33 or other SUMO-fused cytokines in E. coli for screening or biophysical assays; laboratories in resource-limited settings seeking an in-house alternative to commercial IL-33 reagents; researchers using AI structure prediction plus MD to reason about fusion-tag interference in PPI interfaces; and groups developing IL-33/ST2 axis inhibitors who need a defined, accessible target protein source.

- **Major strengths** The question posed is operationally meaningful and directly tied to assay cost and feasibility. The ELISA molar comparison between intact fusion and cleaved cytokine provides a concrete, functionally interpretable readout of tag interference. The cleavage optimization is described with defined parameters (enzyme ratio, temperature, time) and a stated standardized condition. The authors repeatedly and explicitly flag the exploratory nature of the MD and docking results and identify the specific experimental validations (SAXS, mutagenesis, SPR) that would be required, which is an appropriate framing of computational uncertainty.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / quantitative support
- **Claim pointer** The manuscript reports a mass recovery of ~19% and a molar recovery of ~32.6% (38.56 mg native IL-33 from 203.35 mg desalted SUMO-IL-33), and uses these values to support the claim of a high-yield, cost-effective production pipeline.
- **Evidence pointer** Section 3.4 and Figure 7; Table 2; location not provided for raw quantification data.
- **Concern** The recovery figures are stated as single point values without replicate counts, dispersion, or an accounting of losses at each step (clarification, first IMAC, desalting/concentration, cleavage, subtractive IMAC). The Bradford assay used for quantification is a total-protein method and cannot distinguish native IL-33 from co-eluting contaminants or from residual uncleaved fusion in the flow-through. The purity of the final 38.56 mg preparation is asserted but not demonstrated in the supplied material.
- **Why it matters** The central bioprocess claim depends on both the yield and the identity/purity of the recovered species. Without purity assessment and loss accounting, the reported recovery cannot be attributed specifically to native IL-33, and the "high-yield" characterization is not established.
- **Resolution test** Provide replicate recovery measurements with means and dispersion, a step-by-step mass balance, and purity determination for the final preparation (for example densitometry of a documented SDS-PAGE gel, or an orthogonal method such as RP-HPLC or intact mass spectrometry) confirming that the flow-through fraction is native IL-33 and quantifying residual fusion and tag.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / statistical inference
- **Claim pointer** Intact SUMO-IL-33 exhibits 12.0 ± 0.8% molar epitope recognition versus 87.6 ± 3.6% for cleaved IL-33, interpreted as substantial steric masking by the SUMO tag.
- **Evidence pointer** Section 3.5 and Table 2; location not provided for raw ELISA data.
- **Concern** The number of independent ELISA replicates, the number of independent protein preparations tested, and the calibration approach used to convert between Bradford mass concentrations and ELISA-derived molar concentrations are not specified in the supplied text. The molar conversion relies on assumed molecular weights (30.8 kDa fusion, 17.9 kDa native) and on the assumption that Bradford and ELISA standard curves are both accurate for the two different species. Any systematic difference in Bradford response between the fusion and the cleaved protein would propagate directly into the reported percentages.
- **Why it matters** The 12.0% versus 87.6% contrast is the principal empirical pillar of the paper's conclusion that tag removal is operationally necessary. If the molar normalization is biased, the magnitude of the reported masking effect is not established.
- **Resolution test** Report the number of biological and technical replicates, the ELISA standard curve and dynamic range, spike-recovery or dilution-linearity controls for both protein species, and an independent orthogonal concentration determination (for example A280 with calculated extinction coefficients) to validate the Bradford-based molar inputs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / computational inference
- **Claim pointer** MD simulations and HADDOCK docking suggest that the SUMO tag may sterically occlude IL-33 receptor-binding interfaces, with reduced binding propensity for the fusion (ΔG = −12.2 versus −14.5 kcal/mol).
- **Evidence pointer** Sections 3.2.2, 3.3.2, and 4; Figures 3 and 5; Figure S4; location not provided for trajectory and docking parameter files.
- **Concern** The docking comparison rests on a single end-point snapshot from trajectory 1 of a single starting model, and the reported ΔG difference is small relative to the stated HADDOCK score uncertainties (for example −154.9 ± 19.7 for the fusion cluster). The authors themselves note that the trajectories are non-convergent, that CHARMM/TIP3P tends to over-compact flexible segments, and that the AlphaFold3 trajectory adopts an extended orientation with no occlusion. The manuscript therefore contains internal evidence that the occlusion result is one outcome among several rather than a robust structural finding.
- **Why it matters** The structural arm is presented as providing a mechanistic explanation for the ELISA result, but the computational evidence as described is consistent with multiple inter-domain orientations, only some of which produce occlusion. The mechanistic link is therefore weaker than the narrative implies.
- **Resolution test** Either (a) present ensemble-based docking across multiple snapshots from all trajectories and all starting models with explicit reporting of the fraction of conformations showing site 1 or site 2 occlusion, or (b) explicitly downgrade the structural claim to a hypothesis and remove language implying mechanistic explanation of the ELISA data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / model selection
- **Claim pointer** The RoseTTAFold model RF-1 was selected as the optimal structure based on Ramachandran and MolProbity criteria and used for all downstream MD and docking.
- **Evidence pointer** Sections 3.1.1, 3.1.2, and 4; Table 1; Figures S1–S3; location not provided for the underlying validation outputs.
- **Concern** The selection criterion is local stereochemistry, which the authors correctly note does not assess interdomain orientation across a flexible linker. The chosen model is then used to generate the compact, occluded state that drives the paper's structural narrative, while the AlphaFold models that adopt extended conformations are set aside. The manuscript acknowledges this as a scope limitation, but the selection nonetheless determines the direction of the downstream result.
- **Why it matters** Model selection based on a criterion orthogonal to the property under study (interdomain orientation) creates a risk that the reported occlusion is a consequence of the selection procedure rather than a property of the fusion protein.
- **Resolution test** Report the interdomain orientation distributions for all twenty generated models, state explicitly how many adopt compact versus extended arrangements, and either analyze a representative subset of each class or justify why a single model is adequate for the stated conclusion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Cleavage optimization
- **Evidence pointer** Section 3.4 and Figure 6
- **Issue** The text states that 0.1% and 1.0% enzyme ratios, three temperatures, and three time points were evaluated, but only the selected condition is described quantitatively. The comparative data for the non-selected conditions are not summarized in the text.
- **Required correction** Provide a summary of cleavage efficiency across all tested conditions, with a quantitative measure of digestion completeness and replicate information.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** MD simulation setup
- **Evidence pointer** Section 2.3
- **Issue** The force field is stated as CHARMM27, which is an older parameter set for proteins; the manuscript does not specify the water model version details, thermostat/barostat, timestep, or how the three independent trajectories differed beyond random initial velocities.
- **Required correction** Specify the full simulation parameters and confirm whether a more current CHARMM variant was considered, or justify the choice of CHARMM27.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Molecular weight values
- **Evidence pointer** Sections 3.4, 3.5, and 4
- **Issue** The fusion is described as ~32 kDa in Section 2.4 and as 30.8 kDa in Section 3.5, and the SUMO partner as 12.8 kDa, while the construct includes an 8× His tag plus SUMO plus IL-33 residues 112–270. The basis for each value is not stated.
- **Required correction** Reconcile the molecular weight values and state whether they are theoretical (sequence-derived) or experimentally determined.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Claim calibration
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract; Section 5
- **Issue** The Abstract states that the work establishes a "high-yield pipeline," while the recovery is ~19% by mass and the structural findings are described in the same Abstract as model-dependent and requiring further verification. The strength of the yield claim and the strength of the structural claim are not aligned with the reported uncertainty.
- **Required correction** Qualify the yield characterization and ensure the Abstract's confidence level matches the exploratory framing used in the Results and Discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Contextual framing
- **Affected element** Discussion and Conclusions
- **Evidence pointer** Section 4; Section 5
- **Issue** The claim of cost-effectiveness and value in resource-constrained settings is asserted without any cost comparison against commercial IL-33 or against alternative expression strategies.
- **Required correction** Either provide a cost estimate per milligram of purified IL-33 relative to commercial reagent pricing, or remove the cost-effectiveness claim.

- **Technical failings that need to be addressed before the case is established** R1-M1 (recovery and purity not verifiable), R1-M2 (ELISA molar normalization and replicate structure not specified), R1-M3 (single-snapshot docking and non-convergent trajectories), R1-M4 (model selection criterion orthogonal to the property under study).

- **Assessment against Nature-style criteria** Originality is moderate. The individual components (SUMO fusion expression, MD of a fusion construct, ELISA-based epitope comparison) are established approaches; the novelty lies in the specific combination applied to the question of whether an intact SUMO-IL-33 chimera can serve as a screening surrogate. Scientific importance is currently limited by the fact that the central operational conclusion, that tag removal is necessary, is supported primarily by a single ELISA comparison whose normalization is not fully documented, while the structural explanation is explicitly exploratory. Interdisciplinary readership potential exists at the interface of structural biology, bioprocess development, and drug discovery, but the manuscript as supplied does not deliver a structural result robust enough to interest structural biologists, nor a sufficiently characterized reagent to serve as a standalone bioprocess reference. Technical soundness is partial. The experimental design is reasonable, but key quantitative claims lack the replicate structure, purity evidence, and normalization detail needed for independent verification, and the computational arm is internally acknowledged to be model-dependent and non-convergent. Readability for nonspecialists is adequate in the Introduction and Discussion, though the Results contain dense methodological detail and the distinction between exploratory and established findings could be signaled more clearly at the section level rather than only in caveats.

- **Recommendation posture** Currently not established from the provided evidence. The operational conclusion regarding tag removal is plausible and may be correct, but the recovery, purity, and ELISA normalization claims require the missing data before the case can be considered made. The structural claims should be reframed as hypotheses unless ensemble-based analysis is provided.

## Risk / unsupported claims
- The claim of a "high-yield pipeline" is not supported as stated, because purity of the final preparation and stepwise loss accounting are not provided (Section 3.4, Figure 7).
- The claim that the SUMO tag sterically occludes the ST2-binding interface is supported only by a single-snapshot docking result from one trajectory of one starting model, while the manuscript's own AlphaFold3 trajectory shows an extended, non-occluding orientation (Sections 3.2.2, 3.3.2, Figure S4).
- The quantitative magnitude of epitope masking (12.0% versus 87.6%) is not independently verifiable because the molar normalization procedure, replicate structure, and raw ELISA data are not supplied (Section 3.5, Table 2).
- The claim that the intact fusion is "not a suitable direct surrogate for screening applications" is supported by the ELISA data in direction but not in magnitude, and is not corroborated by any direct binding measurement such as SPR or ITC, which the authors themselves identify as necessary (Section 4).
- The cost-effectiveness claim relative to commercial reagents is asserted without supporting cost data (Sections 4 and 5).
- The docking-derived ΔG values (−12.2 versus −14.5 kcal/mol) are presented as indicators of reduced binding propensity, but the difference is small relative to the reported score uncertainties and is derived from a single conformation (Section 3.3.2, Figure 5).