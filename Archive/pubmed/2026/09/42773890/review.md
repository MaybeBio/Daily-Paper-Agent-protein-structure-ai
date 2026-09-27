## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report the design, computational selection, recombinant expression, and biophysical characterization of a mutant IL-21R extracellular domain intended to act as a high-affinity decoy receptor for IL-21, with potential therapeutic application in autoimmune disorders.
- **Visible evidence base** Abstract text only; no figures, tables, methods section, or supplementary data provided
- **Missing materials affecting confidence** Full methods, computational parameters, experimental protocols, raw SPR data, structural validation data, statistical analyses, and any in vitro or in vivo functional assays

## Reviewer
- **Overall assessment** The abstract presents a plausible pipeline for engineering a decoy receptor, but the evidence provided is insufficient to establish the central claims of improved affinity, maintained structure, or therapeutic potential. Several key quantitative and methodological details are absent, and the reported 1.4-fold affinity improvement is modest and of unclear biological significance. The work may be of interest to a specialized audience, but the current evidence base does not support the broad conclusions drawn.
- **Who would be interested in the results, and why** Researchers in protein engineering, cytokine signaling, and autoimmune disease therapeutics may find the approach relevant. Those working on decoy receptors or IL-21 blockade specifically would be the primary audience. The computational design workflow may also interest computational biologists, though the novelty of the approach is not established from the abstract alone.
- **Major strengths** The use of a rational mutagenesis strategy targeting known binding-site residues is a sound approach. The combination of computational screening with experimental validation (SPR, secondary structure analysis) is commendable. The reported KD values are in the picomolar range, indicating high-affinity binding.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The mutant IL-21R exhibits a 1.4-fold increase in binding affinity compared to the wild-type receptor (KD = 50pM vs. 70pM)
  - **Evidence pointer** Abstract, SPR results; location not provided
  - **Concern** The abstract reports a single KD value for each construct without any indication of replicates, error bars, or statistical significance. A 1.4-fold difference in KD may fall within experimental variability for SPR measurements, particularly at picomolar concentrations where mass transport and rebinding effects can confound results.
  - **Why it matters** The central claim of the paper is that the mutant is a "high-affinity" decoy receptor with improved binding. If the affinity improvement is not statistically robust, the entire premise of the engineered decoy is weakened.
  - **Resolution test** Provide SPR sensorgrams, replicate measurements (n ≥ 3), standard deviations, and a statistical test (e.g., t-test or ANOVA) comparing wild-type and mutant KD values. Also report the fitting model and any controls for mass transport limitations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation
  - **Claim pointer** The decoy receptor could be considered an effective therapeutic agent for blocking IL21 and controlling or preventing the progression of autoimmune and inflammatory diseases
  - **Evidence pointer** Abstract, concluding statement; location not provided
  - **Concern** No functional data are presented to demonstrate that the decoy receptor actually inhibits IL-21 signaling in cells. Binding affinity alone does not establish competitive inhibition, receptor blockade, or downstream signaling suppression. No cell-based assays, animal models, or ex vivo experiments are described.
  - **Why it matters** The therapeutic claim is the most significant conclusion of the work. Without functional evidence, the decoy receptor's efficacy remains speculative, and the conclusion overreaches the presented data.
  - **Resolution test** Include cell-based assays showing inhibition of IL-21-induced STAT3 phosphorylation or downstream gene expression in the presence of the decoy receptor. Ideally, also demonstrate efficacy in an animal model of autoimmunity or inflammation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Structural validation
  - **Claim pointer** The protein retained its overall secondary structure after mutagenesis, with slight alterations in alpha-helical content
  - **Evidence pointer** Abstract, secondary structure analysis; location not provided
  - **Concern** The abstract states that secondary structure was "retained" but also that alpha-helical content was "slightly altered." These statements are somewhat contradictory and lack quantitative detail. No percentages, spectra, or comparison to the wild-type are provided. Moreover, secondary structure preservation does not guarantee that the mutant folds correctly or that the binding interface is properly presented.
  - **Why it matters** A decoy receptor must maintain its structural integrity to bind IL-21 effectively. If the mutant has altered structure, the binding affinity measurements may not reflect a properly folded protein, and the therapeutic potential is compromised.
  - **Resolution test** Provide quantitative secondary structure estimates (e.g., from circular dichroism) for both wild-type and mutant, with error estimates. Ideally, include a high-resolution structure (X-ray, cryo-EM, or NMR) or at least a validated homology model showing the mutant retains the binding interface geometry.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Mutagenesis rationale
  - **Evidence pointer** Abstract, methods description; location not provided
  - **Issue** The abstract states that five residues (33, 38, 70, 94, 130) were mutated but does not explain why these specific residues were chosen or how OSPREY was used to select the mutations. The rationale for the final mutant combination (Q33S, E38D, M70T, L94N, M130S) is unclear.
  - **Required correction** Briefly describe the selection criteria (e.g., predicted binding energy, stability scores) and why the specific substitutions were favored over alternatives.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Expression and purification details
  - **Evidence pointer** Abstract, expression description; location not provided
  - **Issue** The abstract mentions expression in E. coli Rosetta-gami but provides no information on yield, purity, solubility, or refolding steps. These factors are critical for assessing the practical utility of the decoy receptor.
  - **Required correction** Include yield, purity (e.g., SDS-PAGE or SEC profile), and any refolding or solubilization steps in the full manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "High-affinity" designation
  - **Evidence pointer** Abstract, title and results; location not provided
  - **Issue** The title and abstract describe the decoy receptor as "high-affinity," but the wild-type already has picomolar affinity (KD = 70 pM). A 1.4-fold improvement, while measurable, may not warrant the "high-affinity" descriptor as a distinguishing feature.
  - **Required correction** Clarify whether the improvement is biologically meaningful or simply a modest enhancement. Consider tempering the language if the improvement is not functionally significant.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Specificity
  - **Affected element** Selectivity claim
  - **Evidence pointer** Abstract, binding characterization; location not provided
  - **Issue** The abstract does not address whether the mutant decoy receptor retains specificity for IL-21 or whether it might cross-react with other cytokines that share the common gamma chain (e.g., IL-2, IL-4, IL-15).
  - **Required correction** Include binding assays against related cytokines to demonstrate selectivity, or at least discuss the potential for cross-reactivity.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical robustness of KD), R1-M2 (lack of functional validation), R1-M3 (incomplete structural characterization)
- **Assessment against Nature-style criteria**  
  Originality: The approach of engineering a decoy receptor via targeted mutagenesis is not novel in concept, though the specific mutations and computational workflow may offer incremental novelty. This is not established as a transformative advance from the abstract.  
  Scientific importance: IL-21 blockade is a relevant therapeutic target, but the modest affinity improvement and lack of functional data limit the perceived importance.  
  Interdisciplinary readership: The work bridges computational biology, protein engineering, and immunology, but the abstract is too specialized and lacks context for a broad audience.  
  Technical soundness: The computational and experimental methods are not described in sufficient detail to assess rigor. The SPR data lack statistical backing, and the structural analysis is qualitative.  
  Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with decoy receptor concepts and SPR terminology. It does not provide sufficient background for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible pipeline, but the central claims of improved affinity, structural preservation, and therapeutic potential are not supported by the data shown. The authors should provide full experimental details, statistical analyses, and functional validation before the case can be considered.

## Risk / unsupported claims
- The claim that the mutant exhibits a 1.4-fold increase in binding affinity is unsupported without replicate measurements and statistical analysis.
- The claim that the decoy receptor is an "effective therapeutic agent" is unsupported by any functional or in vivo data.
- The claim that the protein "retained its overall secondary structure" is weakly supported by qualitative statements without quantitative data.
- The therapeutic potential for "controlling or preventing the progression of autoimmune and inflammatory diseases" is speculative and not supported by the presented evidence.