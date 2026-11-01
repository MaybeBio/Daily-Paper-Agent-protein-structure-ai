## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions, Acknowledgments). Supplementary items are referenced but not supplied.
- **Assessment boundary** Assessment is restricted to the material supplied in the manuscript body. All Supplementary Figures (S1–S7) and Supplementary Tables (S1–S3) are cited but unavailable, so any claim whose support resides only in those items is treated as not independently verifiable here.
- **Shared manuscript claim summary** The authors use ColabFold to build models of human ferroportin (hFPN) in inward-open, occluded, and outward-open states, validate them against experimental structures via TM-align, run 1 µs MD simulations (three replicas for wild type, two for N174I, one for G80S), and interpret state-dependent salt bridges and hydrogen bonds in the context of known pathogenic mutations. They propose that a stable core (TM1, TM5, TM7b, TM8, TM10) is flanked by mobile peripheral helices, that TM1/TM5 may act as a pivot, that G323 flexibility governs TM7b movement in the final export phase, and that N174I traps the transporter in a non-functional outward-open state via loss of the N174–Q478 hydrogen bond and gain of hydrophobic contacts (L474, L170, I159).
- **Visible evidence base** Main-text Figures 1–7, Tables 1–2, and the described Methods. Quantitative support for model validation (pTM, pLDDT, PAE, TM-scores, RMSD) is partly in main text and partly deferred to Supplementary Figures S2 and Table S3.
- **Missing materials affecting confidence** Supplementary Figures S1–S7 and Supplementary Tables S1–S3; no trajectory data, no convergence metrics beyond RMSD/RMSF summaries, no per-replica numerical tables for interaction frequencies, no sequence alignment content, no membrane composition table, no mutation mapping figure.

## Reviewer
- **Overall assessment** The manuscript addresses a genuinely underdetermined structural problem, namely the conformational dynamics of the only known human iron exporter and the state-specific consequences of pathogenic variants. The workflow is conventional and appropriate in principle (AI-based modeling, TM-align validation, all-atom MD in a membrane, interaction analysis). However, the central mechanistic conclusions rest on a thin and internally inconsistent simulation base. Replica counts are asymmetric across systems (three wild-type, two N174I, one G80S), the authors themselves report that per-helix mobility is not reproducible across replicas within the same conformational state, and the G80S mutant is then dropped from interaction analysis without a principled criterion. The most heavily promoted mechanistic claim, that N174I locks the outward-open state, is supported by two replicas of a single conformational state with no transition sampling. The manuscript is candid about the need for enhanced sampling in the Conclusions, which is commendable, but this candor does not substitute for the missing evidence. As written, the work is a hypothesis-generating modeling study, and it should be framed and bounded as such rather than presented as an elucidation of conformational stabilization.
- **Who would be interested in the results, and why** Researchers in iron metabolism and ferroportin-related iron overload, particularly those interpreting variant pathogenicity; structural biologists working on MFS/SLC transporters and alternating-access mechanisms; computational biophysicists interested in AI-generated conformational ensembles and their behavior under MD; and clinically oriented groups seeking a structural rationale for distinguishing loss-of-function from gain-of-function SLC40A1 variants.
- **Major strengths** The problem selection is well motivated, and the Introduction gives a clear, accurate account of hFPN topology, the two binding sites, the alternating-access cycle, hepcidin regulation, and the clinical reclassification of ferroportin disease versus SLC40A1-related hemochromatosis. The explicit rationale for modeling, namely the absence of an inward-open hFPN structure and the unresolved loops in cryo-EM structures, is sound. The validation strategy using TM-align against both ferroportin structures and unrelated MFS/SLC transporters is reasonable, and the reported TM-scores for the outward-open comparison (0.96, 1.42 Å against 6W4S) are strong. The decision to exclude loop and terminal regions from clustering and from TM-score interpretation is methodologically defensible. The Discussion is unusually explicit about the limits of the approach and about the need for enhanced sampling, and the distinction drawn between LOF and GOF variant classes is handled with appropriate clinical nuance, including the acknowledgment that some LOF variants also reduce hepcidin binding.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Sampling adequacy and statistical support
- **Claim pointer** The manuscript claims that specific residues stabilize specific conformational states, that TM1 and TM5 act as a pivot, and that N174I traps hFPN in a non-functional outward-open state.
- **Evidence pointer** Section 3.2, Section 3.2.1, Table 2, Section 3.2.2, Figure 4, Figure 5, Figure 6, Figure 7, Supplementary Figures S6 and S7
- **Concern** The simulation base is too small and too uneven to support state-resolved mechanistic claims. Wild-type systems have three replicas, N174I has two, and G80S has one. The authors state in Section 3.2.1 that per-helix mobility changes "in an apparently incoherent way from one replica to another in the same hFPN conformational state," which is a direct admission that the observable of interest is not reproducible within a state. Interaction frequencies are then reported as single aggregate values (for example approximately 37 percent, 18 percent, and 12 percent for the Y64–N144 hydrogen bond) without per-replica dispersion, confidence intervals, or a test of whether the differences between states exceed the between-replica variance. With three replicas of 1 µs each, and with at least one wild-type replica per state showing RMSD above 3.0 Å, the reported state differences in interaction persistence are not separable from sampling noise.
- **Why it matters** The entire mechanistic narrative, including the pivot hypothesis and the N174I locking model, depends on the assumption that the simulated ensembles are converged and that state-to-state differences are real. If the per-replica variance is comparable to the between-state difference, the central conclusions are not established.
- **Resolution test** Provide per-replica interaction frequencies and per-replica RMSF values for all analyzed helices, with explicit between-replica and between-state variance. Extend wild-type and mutant sampling to a matched number of replicas (at minimum three per system) and demonstrate convergence of the reported observables, for example by block averaging or by showing that interaction frequencies plateau. Report whether the state differences survive a statistical comparison that accounts for replica-level clustering.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidential basis for the N174I mechanism
- **Claim pointer** The N174I mutation traps hFPN in the outward-open conformation by disrupting the N174–Q478 hydrogen bond and forming stable hydrophobic interactions with L474, L170, and I159, rendering the transporter unable to cycle back to the inward-open state.
- **Evidence pointer** Section 3.2.2, Figure 6, Figure 7, Section 4, Section 5
- **Concern** This claim is the most prominent mechanistic conclusion of the paper, yet it is supported only by two 1 µs simulations of a single conformational state. No simulation samples the outward-open to inward-open transition, so the assertion that the mutant is "unable to cycle back" is not tested. The hydrophobic contacts reported for I174 are with residues that already form the hydrophobic environment of the wild-type N174 (I159, L170, I177, F360, L474), so the observation that a hydrophobic residue placed in a hydrophobic pocket makes hydrophobic contacts is close to a restatement of the substitution rather than an independent mechanistic finding. The authors also report that RMSD and RMSF for the mutant do not differ significantly from wild type, which is in tension with a strong destabilizing or locking effect.
- **Why it matters** The N174I mechanism is presented as a principal contribution and is used to explain a clinical phenotype. If the only distinguishing observation is the loss of one hydrogen bond and the presence of hydrophobic contacts that are geometrically expected, the mechanistic claim is not established.
- **Resolution test** Either provide transition-pathway evidence (for example enhanced sampling, metadynamics, or Markov state modeling) showing that the mutant has a substantially reduced outward-open to inward-open transition rate relative to wild type, or explicitly downgrade the claim to a hypothesis and remove the "unable to cycle back" language. In either case, report per-replica contact occupancies for I174 with each hydrophobic partner and compare them against the corresponding wild-type N174 contact occupancies.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency of the analysis pipeline
- **Claim pointer** The G80S mutant is excluded from intramolecular interaction analysis because its RMSF values do not differ significantly from wild type, while N174I is retained despite the same reported absence of significant RMSF differences.
- **Evidence pointer** Section 3.2.1, Table 2, Section 3.2.2
- **Concern** The stated exclusion criterion is applied inconsistently. The authors write that RMSF values from G80S and N174I replicas "do not differ significantly from those of the wild-type replicas," and then retain N174I for interaction analysis while dropping G80S. The justification given for dropping G80S is that its expected effect was destabilization of the outward-open state, which was not observed. This is a post hoc selection that removes a discordant result from the analysis while retaining a concordant one, and it is not a neutral methodological choice.
- **Why it matters** Selective retention of systems based on whether they reproduce a prior expectation biases the interaction analysis and weakens the credibility of the remaining mutant conclusions. It also leaves the G80S variant, which is clinically relevant, without any reported mechanistic interpretation despite being simulated.
- **Resolution test** Apply a single, pre-stated criterion to all mutant systems. Either analyze both mutants with the same interaction protocol and report both outcomes, including the negative G80S result, or state explicitly that mutant interaction analysis is exploratory and report all mutants. If G80S is excluded, the exclusion rule must be defined independently of the expected direction of the effect.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model validity and conformational assignment
- **Claim pointer** ColabFold produced reliable structural models of the inward-open, occluded, and outward-open conformations of hFPN, including regions unresolved in experimental structures.
- **Evidence pointer** Section 2.2, Section 3.1, Figure 1, Supplementary Figure S2, Supplementary Table S3
- **Concern** The three conformational states were generated by varying a single ColabFold parameter (max_msa_cluster) across non-overlapping ranges (512–1024, 16–32, 32–64). The manuscript does not establish that this parameter manipulation is a valid route to distinct functional states rather than a route to differently regularized models of the same state. The validation is a global fold comparison (TM-score, RMSD) against experimental structures, which confirms fold but does not confirm that the model occupies the intended conformational state. The pTM values (0.74, 0.72, 0.74) are modest and nearly identical across states, and the discriminating evidence for state assignment is deferred to Supplementary Figure S2 and Supplementary Table S3, which are not available for assessment. The inward-open model is validated only against a bacterial homolog (5AYO), not against human hFPN, which is acknowledged but not quantified as a limitation.
- **Why it matters** If the three models do not reliably correspond to the three intended states, then all state-dependent comparisons of interactions and mobility are comparisons between modeling artifacts rather than between functional states.
- **Resolution test** Provide state-discriminating metrics beyond global fold, for example inter-lobe angle, solvent accessibility of the intracellular and extracellular vestibules, or distances between the gating helices, and show that each model falls in the expected range relative to the corresponding experimental structure. Report the full Supplementary Table S3 content in the main text or as a source data file, and state explicitly how the max_msa_cluster ranges were chosen and whether the resulting models are robust to variation within each range.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic overreach relative to evidence
- **Claim pointer** Iron is guided toward the S2 site by TM5 movement while tethered to D181, and D325 displaces R466 to bind the metal, freeing R466 to relocate near D181 to facilitate the conformational transition.
- **Evidence pointer** Section 3.2.2, Figure 5, Section 4
- **Concern** This proposed transport pathway is built from average inter-residue distances in three static conformational ensembles. No iron ion is present in any simulation, no metal-binding energetics are computed, and no transition between states is sampled. The distances reported (for example D181–D325 at 12.8, 11.5, and 13.5 Å across states) are large relative to a coordination shell and vary by amounts comparable to their standard deviations. The mechanism is presented in the Discussion with appropriate hedging, but it is also carried into the Conclusions as a substantive finding.
- **Why it matters** A sequential metal-handoff mechanism requires direct evidence of metal coordination and of state-dependent binding affinity. Distance fluctuations of flexible side chains in the absence of the substrate cannot distinguish a guided pathway from incidental proximity.
- **Resolution test** Either perform simulations with Fe2+ present at the proposed sites and report coordination and residence times, or compute binding free energies for the proposed intermediate states, or restrict the claim to a clearly labeled speculation and remove it from the Conclusions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility of methods
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, Supplementary Table S2, Supplementary Figure S3
- **Issue** The membrane composition is deferred entirely to Supplementary Table S2 and Supplementary Figure S3, and the protonation state assignment cites PROPKA with reference number 39, which is the same reference number used for the CHARMM-GUI membrane archive in the preceding sentence. The reference numbering appears inconsistent at this location.
- **Required correction** State the lipid composition in the main text, verify and correct the PROPKA citation, and report the protonation states assigned to the titratable residues that participate in the reported salt bridges, in particular D157, D181, D325, R40, R88, and R466.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Force field and ion parameters
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The manuscript specifies CHARMM36m with AMBER22 and 0.15 M NaCl but does not state the water model or the ion parameters used. The treatment of the Fe2+ ion is not described because no iron was simulated, which should be stated explicitly given the transporter's function.
- **Required correction** Report the water model and ion parameter set, and state explicitly that no substrate ion was included in the simulations and what the consequences of that omission are for the interpretation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Analysis thresholds
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The salt bridge criterion is a maximum donor-acceptor distance of 4 Å with only formally charged residues considered, and hydrogen bonds are analyzed with default hbond settings. The 10 percent frequency cutoff is applied, but the rationale for 10 percent is not given, and the effect of this cutoff on the reported interactions is not shown.
- **Required correction** State the angle criterion for hydrogen bonds and salt bridges, justify the 10 percent cutoff, and report how the set of reported interactions changes if the cutoff is varied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clustering procedure
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, Supplementary Figure S4
- **Issue** The k-means clustering uses a fixed residue range for the N-lobe (24–234) and two ranges for the C-lobe (308–391 and 452–549). The basis for these specific boundaries is not given, and the elbow method is applied per replica, which means different replicas may yield different cluster counts and therefore non-comparable representative structures.
- **Required correction** Justify the residue ranges, report the selected cluster number for each replica, and state whether representative structures across replicas are directly comparable.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure and table completeness
- **Affected element** Table 1, Table 2, Figure 1, Figure 2, Figure 3, Figure 4, Figure 5, Figure 6, Figure 7
- **Evidence pointer** Table 1, Table 2, Figure 1 through Figure 7
- **Issue** Table 1 is described as listing known pathogenic mutations but its content, including the LOF/GOF assignment and the supporting references, cannot be evaluated from the text alone. Table 2 reports RMSF values but the text states these values are not interpretable across replicas, which raises the question of what Table 2 is intended to demonstrate. Figure 3 is used to support the TM7b reorientation claim, but the quantitative basis for the orientation change is not given in the text.
- **Required correction** Provide the full content of Table 1 with variant classification and evidence level, clarify the purpose of Table 2 given the stated non-reproducibility, and quantify the TM7b orientation change in Figure 3 with a defined metric such as a helix axis angle relative to TM1.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology and classification
- **Affected element** Section 1, Section 4
- **Evidence pointer** Section 1, Section 4
- **Issue** The manuscript uses LOF and GOF labels as if they were cleanly separable, then correctly notes in the Discussion that some LOF variants also reduce hepcidin binding, which undermines the classification. The term "hepcidin resistance" is used for D181V without defining the assay or source context.
- **Required correction** Define the operational criteria used to assign LOF and GOF, and state explicitly which variants are ambiguous under those criteria.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract, Section 1, Section 4
- **Evidence pointer** Abstract, Section 1, Section 4
- **Issue** The Abstract and Introduction are dense with domain-specific abbreviations (TSAT, MFS, ICL3, ECL5, S1, S2, FD, SLC40A1-HC, IRP-IRE) that are defined once and then used heavily. A nonspecialist reader will struggle to follow the mechanistic argument in the Discussion, where helix identities, residue numbers, and conformational states are interleaved without a summary schematic of the proposed cycle.
- **Required correction** Add a single summary figure showing the proposed conformational cycle with the key residues and interactions annotated at each state, and reduce abbreviation density in the Abstract.

- **Technical failings that need to be addressed before the case is established** R1-M1 (sampling adequacy and absence of per-replica statistics), R1-M2 (N174I locking claim unsupported without transition sampling), R1-M3 (inconsistent mutant inclusion criterion), R1-M4 (state assignment not independently validated), R1-M5 (metal-handoff mechanism asserted without substrate or energetics).

- **Assessment against Nature-style criteria** Originality is moderate. The application of ColabFold to generate a full-length inward-open hFPN model and the state-resolved interaction analysis are incremental rather than conceptual advances, and the general approach of modeling MFS transporters and interpreting variants through MD is well established. Scientific importance is potentially high at the clinical level, because a structural rationale for SLC40A1 variant classification would be useful, but the current evidence does not deliver that rationale; the variant interpretations remain hypotheses. Interdisciplinary readership is plausible, spanning iron biology, clinical genetics, and membrane transporter biophysics, but the manuscript is written for a specialized computational audience and would need substantial restructuring, including a summary schematic and reduced abbreviation load, to reach a broad readership. Technical soundness is the weakest axis. The simulation design is underpowered for the claims, replica counts are unequal across systems, the authors report non-reproducible per-helix mobility within states, one mutant is dropped on a post hoc basis, and the headline mechanism is not tested by any transition sampling. Readability for nonspecialists is limited by dense terminology and by the absence of a single integrative figure. On the criteria as a whole, the manuscript does not currently meet the bar for a broad-interest venue, and its primary value at present is as a hypothesis-generating computational study.

- **Recommendation posture** Currently not established from the provided evidence. The work could become supportive of a narrower claim, namely that AI-generated full-length hFPN models are consistent with experimental folds and that certain state-dependent interactions are plausible, if the sampling is extended to matched replica counts, per-replica statistics are reported, the mutant inclusion criterion is made consistent, and the N174I and metal-handoff mechanisms are either tested by enhanced sampling or explicitly demoted to hypotheses throughout, including in the Conclusions.

## Risk / unsupported claims
- The claim that N174I traps hFPN in a non-functional outward-open state and prevents reversion to inward-open is not supported by the supplied evidence, because no transition is sampled and the mutant shows no significant RMSD or RMSF difference from wild type.
- The claim that G323 flexibility is essential for the occluded-to-outward-open transition and that G323V impairs export by reducing loop flexibility is a structural rationalization without mutational simulation or experimental validation in the supplied material.
- The proposed iron-handoff sequence involving D181, D325, and R466 is not supported, because no iron ion was simulated and no binding energetics were computed.
- The claim that TM1 and TM5 act as a pivot for the conformational transition is an interpretation of RMSF patterns that the authors themselves report as non-reproducible across replicas within a state.
- The claim that R40Q, R88G, D157G, and D181V cause incorrect protein folding through loss of electrostatic interactions is not supported, because no folding or stability calculation was performed and the variants were not simulated except where noted.
- The claim that Y64N and N144H alter the inward-outward equilibrium and reduce hepcidin responsiveness is not supported, because neither mutant was simulated and the equilibrium statement is not derived from any computed quantity.
- The state assignments of the three ColabFold models are not independently verifiable from the supplied material, because the discriminating evidence is in Supplementary Figure S2 and Supplementary Table S3, which were not provided.
- The reported state-dependent interaction frequencies cannot be assessed for statistical significance, because per-replica values and variance are not reported.
- The membrane composition, protonation states, water model, and ion parameters are not verifiable from the supplied material, because they are deferred to Supplementary Table S2 and Supplementary Figure S3 or are not stated.