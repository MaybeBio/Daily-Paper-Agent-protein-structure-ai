## Review setup
- **Input scope** Full manuscript text (abstract, introduction, computational methodology, results and discussion, conclusions, supporting information statement)
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by the provided evidence. No assessment of experimental data not included in the manuscript.
- **Shared manuscript claim summary** The manuscript claims that tetra-branched SET-M33 suppresses peptide self-aggregation while preserving membrane association, in contrast to its linear branch sequence Q33, which readily forms oligomers. The authors propose an atomistic rationale for this difference based on all-atom MD simulations.
- **Visible evidence base** Abstract, introduction, computational methodology, results and discussion sections, figures referenced (Figures 1-15), Table 1 (simulated systems), Table 2 (RDF/CN data). No raw simulation trajectories, no input parameter files, no force field modification details beyond description.
- **Missing materials affecting confidence** No supplementary information file was provided (only a statement that representative snapshots exist). No convergence metrics, no block-averaging or error analysis details beyond standard deviation. No control simulations (e.g., with neutral membranes or different ionic strengths). No experimental validation data for the simulation predictions.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in antimicrobial peptide design, namely how branching alters self-association and membrane binding. The simulation setup is reasonable and the comparison between linear and branched architectures is well motivated. However, the evidence presented is largely qualitative, and several key claims are not quantitatively supported by the data shown. The lack of convergence analysis, the absence of free-energy estimates, and the limited description of the enhanced sampling protocol weaken the conclusions. The manuscript is potentially interesting but requires substantial revision and additional analysis before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers in antimicrobial peptide design, computational biophysics of membrane-active peptides, and those interested in multivalent ligand-membrane interactions. The work may also be of interest to experimental groups working on SET-M33 or similar branched AMPs, as it provides a molecular-level hypothesis for their observed behavior.

- **Major strengths** The comparison between linear and branched architectures with equivalent sequence units is a well-designed approach. The use of multiple complementary analyses (contacts, RDF, SASA, hydration) is commendable. The manuscript is clearly written and the figures appear to support the qualitative narrative.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "SET-M33 remained more dispersed, as the branched scaffold and its high cationic charge limited peptide-peptide association while allowing multivalent membrane binding."
- **Evidence pointer** Results and Discussion, "M33 Membrane Association and Suppressed Self-Aggregation" section; Figure 8
- **Concern** The claim that SET-M33 suppresses self-aggregation is based on visual inspection of density maps and qualitative descriptions of contact analysis. No quantitative measure of aggregation propensity (e.g., cluster size distributions, aggregation free energies, or mean cluster lifetimes) is provided. The statement that "SET-M33 remained largely dispersed" is not supported by any numerical metric.
- **Why it matters** The central conclusion of the manuscript rests on the difference in aggregation behavior between Q33 and M33. Without quantitative metrics, the reader cannot assess the magnitude of the effect or whether the difference is statistically significant given the short simulation times and limited sampling.
- **Resolution test** Provide cluster size distributions over time, mean cluster sizes with error bars across replicas, and a statistical test comparing Q33 and M33 aggregation. Alternatively, compute potential of mean force (PMF) between two peptides of each architecture to quantify association free energies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Hydration-tuning enhanced sampling was applied to the system containing 10 Q33 peptides in water... allowing the effective hydration of selected species to be tuned and thereby accelerating association events."
- **Evidence pointer** Computational Methodology, "Hydration-Tuning Enhanced Sampling" section
- **Concern** The enhanced sampling method is described only by reference to prior work. The specific implementation details for this system are not provided: how the bias is scaled, how the "reduction" is calculated, what the coupling parameter is, and how the three bias levels (90%, 80%, 50%) were chosen. More critically, the authors state that "the resulting trajectories were not used to infer equilibrium populations," yet they use these biased trajectories to draw conclusions about aggregation propensity ("Q33 rapidly formed compact assemblies containing up to nine peptides"). The logic of using a non-equilibrium biased method to support a claim about intrinsic aggregation propensity is unclear.
- **Why it matters** The enhanced sampling results are used as key evidence for Q33 aggregation propensity. If the method is not rigorously described and its limitations not properly accounted for, the conclusions drawn from it are not reliable.
- **Resolution test** Provide a detailed description of the bias potential, its functional form, and how the reduction level is computed. Show that the observed aggregation is not an artifact of the bias by demonstrating that the same contacts are sampled in unbiased simulations at longer timescales, or by computing the bias-induced shift in the aggregation free energy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Both architectures associated rapidly with the bilayer but remained predominantly surface-bound, without persistent pore formation or complete insertion."
- **Evidence pointer** Results and Discussion, "Membrane Binding Mode" section
- **Concern** The claim that no pore formation or insertion occurs is based on 300 ns simulations (and 1 μs for selected M33 systems). This timescale is very short for observing membrane disruption events, which typically occur on microsecond to millisecond timescales. The authors acknowledge this limitation in the text, but the claim is still presented as a finding rather than as a limitation of the simulation timescale.
- **Why it matters** The absence of pore formation in short simulations does not establish that the peptides cannot form pores. The claim as stated overreaches the evidence.
- **Resolution test** Rephrase the claim to explicitly state that no pore formation was observed within the simulated timescales, and discuss the timescale limitation more prominently. Alternatively, perform longer simulations or use enhanced sampling methods to probe membrane disruption.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Overall, these results suggest that branched topology reduces uncontrolled peptide self-aggregation while maintaining efficient membrane engagement. This provides an atomistic rationale for the distinct behavior of SET-M33 relative to its linear branch sequence."
- **Evidence pointer** Conclusions section
- **Concern** The manuscript does not connect the simulation findings to the experimentally observed differences in antibacterial activity or stability between M33 and Q33. The introduction mentions that M33 shows increased resistance to proteases and peptidases, but the simulations do not address proteolytic stability. The relevance of the observed aggregation differences to the biological activity is asserted but not demonstrated.
- **Why it matters** The broader significance of the work depends on linking the molecular-level observations to the functional differences that motivate the study. Without this connection, the impact of the findings is limited.
- **Resolution test** Discuss how the observed differences in aggregation and membrane binding might relate to the experimentally measured antibacterial activity and stability. If possible, compare simulation predictions with experimental data on M33 and Q33 behavior.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The initial models were constructed with α-helical Q33 segments, including the four branch segments of M33."
- **Evidence pointer** Computational Methodology, "Peptide Models and System Construction" section; Results and Discussion, "Secondary-Structure Evolution" section
- **Concern** The manuscript does not state how the initial α-helical conformations were generated, whether the helical content was stable during equilibration, or whether the results depend on the initial conformation. The secondary-structure analysis reports average helical content but does not show the time evolution or the distribution across replicas.
- **Why it matters** The secondary-structure results are used to support the claim that Q33 is stabilized by membrane binding while M33 is not. If the initial helical bias influences the results, the conclusions may not be robust.
- **Resolution test** Provide time series of secondary-structure content for each replica, and discuss whether the initial helical conformation relaxes to a common ensemble. Consider running simulations from different initial conformations (e.g., fully extended) to test convergence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "to do this, systems containing equivalent numbers of Q33 sequence units were simulated." This phrasing is awkward and the connection to the preceding sentence is unclear.
- **Required correction** Rephrase for clarity, e.g., "Systems were constructed with equivalent numbers of Q33 sequence units to enable direct comparison."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Computational Methodology, "Peptide Models and System Construction"
- **Evidence pointer** Computational Methodology section
- **Issue** The lipid composition is described as a ratio of 2:1.3:1 for DOPE, DPPG, and DPPE. The use of a non-integer ratio (1.3) is unusual and the total number of lipids per leaflet (245) is not divisible by the sum of the ratio components (4.3). This suggests the actual numbers of each lipid type are not integers, which is impossible.
- **Required correction** Clarify the exact number of each lipid type in the bilayer. If the ratio is approximate, state the exact composition used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Computational Methodology, "Molecular Dynamics Protocol"
- **Evidence pointer** Computational Methodology section
- **Issue** The manuscript states that "Electrostatic and van der Waals interactions were truncated at 1.2 nm." This is a relatively short cutoff for electrostatic interactions, and the use of PME with a 1.2 nm real-space cutoff is standard, but the manuscript should clarify whether the van der Waals interactions were simply truncated or if a switching function was used.
- **Required correction** Specify the treatment of van der Waals interactions at the cutoff (e.g., plain truncation, switch function) and justify the choice.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results and Discussion, "Membrane Coverage, Lateral Organization, and Contact Distance"
- **Evidence pointer** Results and Discussion section
- **Issue** The section title mentions "Contact Distance" but the text describes minimum-distance distributions. The term "contact distance" is not defined and could be confused with contact maps used elsewhere.
- **Required correction** Use consistent terminology, e.g., "peptide-membrane minimum distance" throughout.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results and Discussion, "Secondary-Structure Evolution"
- **Evidence pointer** Results and Discussion section
- **Issue** The reported helical content values are given as "25 ± 0.19%" and "42 ± 0.56%" for Q33 in solution and membrane-bound, respectively. The standard deviations are extremely small, which is surprising given the expected conformational variability. It is unclear whether these are standard deviations across replicas or across time.
- **Required correction** Clarify how the mean and standard deviation were computed, and report the variability across replicas separately from temporal fluctuations.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The conclusions section largely repeats the results without adding new interpretation or discussing limitations. A more critical discussion of the limitations of the simulation approach would strengthen the manuscript.
- **Required correction** Add a paragraph discussing the limitations of the study, including timescale constraints, the simplified membrane model, and the lack of experimental validation.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Computational Methodology, "Peptide Models and System Construction"
- **Evidence pointer** Computational Methodology section
- **Issue** The manuscript states that the branched core was parameterized using PyRED with RESP charges at HF/6-31G(d) level. This is a standard approach, but the manuscript does not report the resulting partial charges or provide validation of the parameterization (e.g., comparison with quantum mechanical reference data).
- **Required correction** Provide the partial charges as supplementary material or describe validation of the parameterization.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results and Discussion, "Q33 Aggregation in Solution and at the Membrane"
- **Evidence pointer** Results and Discussion section
- **Issue** The text states "In the 8-Q33 system, dimers and occasional tetramers were observed at the membrane interface." It is unclear whether these observations are from a single trajectory or averaged across replicas, and how "occasional" is quantified.
- **Required correction** Specify the number of replicas and the frequency of tetramer formation across replicas.

## Risk / unsupported claims
- The claim that SET-M33 suppresses self-aggregation is not quantitatively supported; no aggregation metrics are provided.
- The use of hydration-tuning enhanced sampling to infer aggregation propensity is not rigorously justified, as the method is described only by reference and the biased trajectories are not used for equilibrium analysis.
- The claim that both architectures remain surface-bound without pore formation is only valid for the simulated timescales and should be stated as such.
- The connection between the simulation results and the experimentally observed differences in antibacterial activity and stability is asserted but not demonstrated.
- The secondary-structure analysis is based on initial α-helical models, and the dependence of the results on the initial conformation is not assessed.
- The lipid composition ratio (2:1.3:1) is internally inconsistent with the stated total number of lipids per leaflet.