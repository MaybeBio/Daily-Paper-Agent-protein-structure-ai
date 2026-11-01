## Review setup
- **Input scope** Abstract only, as provided in the submission record. No full text, figures, tables, or Supporting Information were supplied.
- **Assessment boundary** Evaluation is restricted to the claims and evidence visible in the abstract. Mechanistic, structural, and quantitative assertions that would normally rest on figures, tables, and methods sections cannot be independently verified here.
- **Shared manuscript claim summary** The authors report that ultrasound-synchronized in situ crystallization of covalent organic frameworks (COFs) around enzymes traps transient high-activity, open enzyme conformations before relaxation, yielding enhanced catalytic activity. They report a six-framework library, a 3.4-fold activity increase for horseradish peroxidase driven mainly by a reduced Michaelis constant, >70% retention over 10 cycles, molecular dynamics identification of a globally reorganized open state with displaced gating phenylalanines, 2D solid-state NMR characterization of COF-enzyme interfacial interactions, ex situ controls that fail, and extension to laccase, cytochrome c, and lipase with 3.8-fold, 2.7-fold, and 1.5-fold enhancements over conventional stirring.
- **Visible evidence base** Abstract-level statements only. No numerical tables, kinetic traces, structural models, NMR spectra, simulation parameters, synthesis details, or statistical reporting are visible.
- **Missing materials affecting confidence** Full text, all figures and tables, Methods, Supporting Information, enzyme loading and leaching data, control experiments beyond the stated ex situ comparison, simulation protocols and convergence data, NMR acquisition and assignment details, and statistical treatment. These omissions materially limit confidence in every quantitative and mechanistic claim.

## Reviewer
- **Overall assessment** The concept is attractive and potentially of broad interest. Coupling a transient conformational perturbation to a crystallization event that kinetically traps the perturbed state is a coherent and testable hypothesis, and the reported extension across four enzymes suggests generality. However, from the supplied material the central mechanistic claim, namely that the observed activity gains arise from locking a specific transient open conformation rather than from conventional immobilization effects such as increased local concentration, reduced aggregation, altered mass transfer, or support-induced conformational selection, is not established. The evidence is described but not shown, and several alternative explanations are not excluded by the abstract alone. The work is promising but currently unproven on the visible record.

- **Who would be interested in the results, and why** Researchers in enzyme immobilization and biocatalysis, materials chemists working on COFs and reticular frameworks, sonochemistry and mechanochemistry groups, and structural biologists interested in cryptic sites and conformational selection. If substantiated, the approach would interest process chemists seeking stable, recyclable biocatalysts with enhanced intrinsic kinetics, and would be relevant to the broader question of whether non-equilibrium protein states can be stabilized by designed hosts.

- **Major strengths**
  - The central hypothesis is clearly stated and mechanistically falsifiable, and the authors report an ex situ control that, if properly executed, directly tests the necessity of temporal synchrony.
  - Use of a six-framework library with varied pore size and chemistry is an appropriate design for probing steric and nonbonded contributions.
  - The combination of molecular dynamics and 2D solid-state NMR, if rigorously executed, is a suitable multi-technique approach to a conformational claim.
  - Extension to laccase, cytochrome c, and lipase, if reproduced under matched conditions, would support generality beyond a single enzyme.
  - The reframing of immobilization as conformational upgrading is a conceptually useful contribution if the mechanism holds.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic attribution
- **Claim pointer** The captured species is a transient high-activity open enzyme conformation, and the activity enhancement is caused by locking this conformation.
- **Evidence pointer** Abstract statements referencing molecular dynamics and 2D solid-state NMR; no figures, tables, or methods provided. Location not provided.
- **Concern** The abstract asserts that the trapped species is a globally reorganized open state, but no structural data, order parameters, or population estimates are visible. It is not shown that the encapsulated enzyme differs conformationally from enzyme immobilized without synchronization, nor that the open state is the catalytically relevant species rather than a coincidental structural variant.
- **Why it matters** The entire novelty claim depends on conformational locking rather than on conventional immobilization effects. Without direct structural comparison between synchronized and non-synchronized samples, the mechanism is asserted rather than demonstrated.
- **Resolution test** Provide comparative structural data, for example solid-state NMR chemical shifts or MD-derived metrics, for enzyme in synchronized COF, non-synchronized COF, and free enzyme, showing a distinct and reproducible conformational population that correlates quantitatively with activity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Control adequacy
- **Claim pointer** Ex situ controls in which activation precedes encapsulation fail entirely, establishing that temporal synchrony is mechanistically essential.
- **Evidence pointer** Abstract statement only. Location not provided.
- **Concern** The ex situ control is described as failing entirely, but the abstract does not specify how activation was maintained or verified before encapsulation, how long the delay was, or whether the enzyme had already relaxed. A control that fails because the perturbation was absent at the moment of encapsulation does not by itself prove that a transient state was trapped in the synchronized case.
- **Why it matters** This control is the primary mechanistic discriminator in the abstract. If its design does not isolate temporal synchrony from other differences such as enzyme concentration, mixing, or COF nucleation state, the mechanistic conclusion is unsupported.
- **Resolution test** Report the ex situ protocol with timing, the independent verification that the enzyme was activated at the point of encapsulation, and matched controls for all non-temporal variables, ideally with a time-resolved series showing loss of the effect as the delay increases.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The optimal framework increased horseradish peroxidase activity 3.4-fold, primarily through a marked reduction in the Michaelis constant, with >70% activity retained over 10 cycles.
- **Evidence pointer** Abstract statement only. Location not provided.
- **Concern** No kinetic parameters, error estimates, replicate numbers, or definitions of the comparison baseline are visible. It is unclear whether the 3.4-fold increase is relative to free enzyme, to enzyme in COF without ultrasound, or to a conventional immobilization reference, and whether the reported Km reduction is statistically robust.
- **Why it matters** The magnitude and origin of the enhancement are central to the claim of conformational upgrading. Without baseline definition and statistics, the numbers cannot be evaluated or reproduced.
- **Resolution test** Provide full kinetic parameters with confidence intervals and replicate counts, explicit definition of each comparator, and raw activity data underlying the reported fold changes and recycling retention.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Alternative explanations
- **Claim pointer** Enhanced activity is attributed to conformational locking rather than to other immobilization-related effects.
- **Evidence pointer** Abstract statements on activity, kinetics, and simulations. Location not provided.
- **Concern** The abstract does not exclude conventional contributors such as increased effective enzyme concentration, reduced autolysis or aggregation, altered substrate partitioning within the COF, changes in diffusion or mass transfer, or preferential encapsulation of a more active subpopulation. Ultrasound itself can alter enzyme activity and aggregation independently of any locking effect.
- **Why it matters** If any of these alternatives account for the effect, the mechanistic and conceptual novelty is substantially reduced.
- **Resolution test** Include controls for enzyme loading, leaching, substrate partitioning, and ultrasound-only treatment without COF formation, and show that activity per accessible enzyme molecule, not per sample, is enhanced.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generality and comparability
- **Claim pointer** Extension to laccase, cytochrome c, and lipase enhanced immobilized enzyme activity 3.8-fold, 2.7-fold, and 1.5-fold over conventional stirring.
- **Evidence pointer** Abstract statement only. Location not provided.
- **Concern** The comparison baseline is conventional stirring, which differs from the synchronized condition in multiple respects including ultrasound exposure, nucleation kinetics, and mixing. The fold changes vary widely across enzymes, and no structural or kinetic evidence is presented that the same locking mechanism operates in each case.
- **Why it matters** The claim of a general strategy requires that the mechanism, not merely the outcome, be shared across enzymes. A 1.5-fold change in particular may be within the range of ordinary immobilization effects.
- **Resolution test** Report per-enzyme structural or kinetic evidence for conformational trapping, matched controls isolating ultrasound from synchronization, and statistical comparison against appropriate immobilization references.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of the term locking
- **Evidence pointer** Title and abstract. Location not provided.
- **Issue** Locking implies a kinetically trapped, persistent state, but the abstract does not report the timescale over which the conformation is retained or whether it relaxes during storage or catalysis.
- **Required correction** Define locking operationally and report conformational stability over time and across catalytic cycles.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Structural specificity
- **Affected element** Gating phenylalanine displacement
- **Evidence pointer** Abstract statement on molecular dynamics. Location not provided.
- **Issue** The identity and conservation of the gating phenylalanines are not specified, and it is not stated whether their displacement is observed in simulation only or also supported experimentally.
- **Required correction** Name the residues, state the enzyme and numbering, and clarify whether the displacement is simulated, experimentally observed, or both.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Framework library description
- **Affected element** Six frameworks with varied pore size and chemistry
- **Evidence pointer** Abstract statement. Location not provided.
- **Issue** Pore sizes, chemical functionalities, and the rationale for the specific set are not given, so the structure-activity relationship cannot be assessed.
- **Required correction** Provide a table of framework identities, pore dimensions, and functional groups with the corresponding activity data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Crystallization and enzyme integrity
- **Affected element** Sonochemical in situ crystallization
- **Evidence pointer** Abstract statement. Location not provided.
- **Issue** The abstract does not address whether ultrasound or the crystallization conditions cause enzyme denaturation, fragmentation, or partial unfolding, which would confound activity interpretation.
- **Required correction** Report enzyme integrity assays, for example activity of released enzyme and spectroscopic or electrophoretic characterization, before and after the process.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Reported fold changes and cycling retention
- **Evidence pointer** Abstract statements. Location not provided.
- **Issue** No replicate counts, variance, or batch-to-batch reproducibility data are visible.
- **Required correction** Report sample sizes, dispersion measures, and independent batch replication for all activity and stability values.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5. The most critical are R1-M1 and R1-M2, since the mechanistic claim of conformational locking rests on structural differentiation and on the validity of the synchrony control.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of synchronizing a transient conformational perturbation with host crystallization to trap a non-equilibrium enzyme state is distinctive and, on the visible record, not a routine extension of standard immobilization. Originality is plausible but contingent on the mechanism being demonstrated.
  - **Scientific importance** Potentially high if the mechanism is substantiated, because it would provide a general route to non-equilibrium protein states. Currently the importance is asserted rather than evidenced, since the abstract does not exclude conventional explanations.
  - **Interdisciplinary readership** The work sits at the intersection of biocatalysis, framework materials, sonochemistry, and protein structural dynamics, which is appropriate for a broad chemistry audience. The abstract is accessible to that audience.
  - **Technical soundness** Cannot be confirmed from the supplied material. Key structural, kinetic, and control data are described but not shown, and several alternative explanations are not addressed in the visible text.
  - **Readability for nonspecialists** The abstract is clearly written and the central idea is communicated effectively. Some terms, such as cryptic sites and gating residues, would benefit from brief definition for a general readership.

- **Recommendation posture** Currently not established from the provided evidence. The concept is worth pursuing, and the assessment could become supportive if the structural differentiation, the synchrony control, and the kinetic baselines are documented with full data and appropriate statistics.

## Risk / unsupported claims
- The claim that a specific transient open conformation is captured and is responsible for the activity increase is unsupported by visible structural evidence.
- The claim that temporal synchrony is mechanistically essential rests on an ex situ control whose design and verification are not described.
- The reported fold changes and Michaelis constant reduction are not evaluable without defined baselines, replicates, and statistics.
- The claim of generality across laccase, cytochrome c, and lipase is not supported by per-enzyme mechanistic evidence, and the 1.5-fold lipase result may be within the range of ordinary immobilization effects.
- The claim that the captured state is beyond equilibrium reach is not assessable from the abstract, since no thermodynamic or kinetic stability data are provided.
- The assertion that 2D solid-state NMR elucidates the stabilizing interfacial interactions is not verifiable without spectra, assignments, and distance or coupling measurements.