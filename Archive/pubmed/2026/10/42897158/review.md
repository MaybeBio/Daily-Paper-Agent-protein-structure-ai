## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, methodological rigor, interpretation of results, and alignment with claims. Editorial quality and formatting are considered only where they affect comprehension.
- **Shared manuscript claim summary** The authors investigate the molecular mechanisms by which a negative allosteric modulator (NAM), AS408, and mutations at position E1303.41 in the β1-adrenergic receptor (β1AR) reduce G protein signalling. They propose that E1303.41 mutations act as a rheostat, shifting receptor equilibria towards pre-active or inactive states, whereas AS408 acts by uncoupling the intracellular region from the orthosteric pocket, stabilising an alternative non-productive conformation.
- **Visible evidence base** Pharmacological assays (TRUPATH, NanoBRET), biophysical assays (BLI), NMR spectroscopy (19F and 13C), MD simulations, and a conformational BRET biosensor.
- **Missing materials affecting confidence** Supplementary figures, tables, and methods referenced but not provided. Raw data and statistical analysis details are not fully available. Details of the BRET biosensor validation and MD simulation convergence are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and technically sophisticated investigation into allosteric modulation of the β1AR. The combination of pharmacological, biophysical, and computational approaches is commendable and provides a rich dataset. The central claim that AS408 and E1303.41 mutations reduce signalling via distinct mechanisms is interesting and potentially significant. However, the evidence for the most novel claim, the "uncoupling" mechanism of AS408, is largely indirect and relies on interpretation of NMR chemical shifts and MD simulations. The manuscript would be strengthened by more direct evidence, such as structural data or additional functional assays that specifically probe the proposed conformational changes. The distinction between the mechanisms is not always clear-cut, and the authors should address the possibility that AS408's effects are a more extreme version of the same equilibrium shift caused by the mutations.
- **Who would be interested in the results, and why** Researchers in GPCR biology, particularly those interested in allosteric modulation, conformational dynamics, and drug development. The study provides a methodological framework for dissecting allosteric mechanisms using multiple orthogonal approaches, which is valuable for the field. The findings on the distinct mechanisms of a NAM versus mutations at the same site have implications for understanding GPCR signalling bias and for structure-based drug design.
- **Major strengths**
  1. The use of a multi-disciplinary approach (pharmacology, biophysics, NMR, MD) to address a complex biological question is a major strength.
  2. The study provides a detailed characterisation of a series of E1303.41 mutations, showing a clear structure-activity relationship for signalling.
  3. The NMR data, particularly the 19F studies, provide direct biophysical evidence for conformational changes in the receptor.
  4. The development and use of a conformational BRET biosensor to validate findings in a cellular context is a strong addition.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for central claim
  - **Claim pointer** The central claim is that AS408 "uncouples the intracellular region of β1AR from the influence of the orthosteric pocket" by stabilising an alternative, non-productive conformation.
  - **Evidence pointer** Figures 3, 4, 5, and 7; Results sections "AS408 reduces β1AR signalling by binding the TM3-TM4-TM5 site" and "AS408 uncouples the β1AR intracellular surface from agonist".
  - **Concern** The evidence for the "uncoupling" mechanism is largely indirect. The NMR data show that AS408 binding affects the intracellular region (19F probes) and the core (13C probes) differently, and that the effects are distinct from those of the E1303.41 mutations. However, the interpretation that this represents a "non-productive conformation" that is "uncoupled" from the orthosteric pocket is a significant leap. The data could also be interpreted as AS408 stabilising a different point on the same conformational landscape, or as an allosteric effect that propagates differently through the protein. The MD simulations show a different binding pose, but this is a computational prediction. The lack of a high-resolution structure of the β1AR-AS408 complex, or of a direct measurement of the proposed conformational change (e.g., via DEER spectroscopy or smFRET), leaves the central claim under-supported. The authors should either provide more direct evidence or temper their conclusions.
  - **Why it matters** The novelty of the paper rests on the claim that AS408 works by a mechanism distinct from simply shifting the existing equilibrium. If the evidence is not conclusive, the paper's main contribution is reduced to a detailed characterisation of a NAM, which is less significant.
  - **Resolution test** The authors should provide more direct evidence for the proposed "uncoupling" mechanism. This could include: (1) a cryo-EM or X-ray structure of the β1AR-AS408 complex; (2) DEER or FRET measurements that directly probe the distance between the orthosteric pocket and the G protein binding site in the presence and absence of AS408; or (3) a more rigorous analysis of the NMR data, such as relaxation dispersion experiments, to show that the "non-productive" conformation is a distinct, kinetically stable state. If such data are not available, the conclusions should be revised to be more cautious, framing the "uncoupling" as a hypothesis rather than a demonstrated mechanism.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative analysis and interpretation
  - **Claim pointer** The authors claim that E1303.41 mutations act as a "rheostat" for signalling, with different mutations having different effects on the equilibrium between pre-active and active states.
  - **Evidence pointer** Figures 1 and 2; Results section "E130X3.41 mutations reduce activity by shifting β1AR equilibria".
  - **Concern** The "rheostat" model is inferred from the NMR population analysis and the pharmacological data. However, the NMR population analysis is based on deconvolution of broad, overlapping signals, which can be subjective and prone to error. The authors do not provide a quantitative error analysis for the population estimates. Furthermore, the correlation between the NMR populations and the functional outputs (TRUPATCH, BLI) is not rigorously quantified. A more quantitative analysis, such as plotting the NMR population of the active state against the Emax or EC50 values and performing a correlation analysis, would strengthen the "rheostat" claim.
  - **Why it matters** The "rheostat" model is a key conceptual framework for understanding the effects of the mutations. If the quantitative link between the biophysical and functional data is weak, the model is less convincing.
  - **Resolution test** The authors should provide a quantitative correlation analysis between the NMR-derived populations and the functional parameters. They should also provide error bars for the NMR population estimates, perhaps by repeating the deconvolution with different initial conditions or using a more objective fitting method.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Relevance of the model system
  - **Claim pointer** The study uses a turkey β1AR construct with several thermostabilising mutations and truncations. The authors imply that the findings are relevant to the human β1AR and to drug development.
  - **Evidence pointer** Methods section "β1AR constructs—Biophysics"; Discussion.
  - **Concern** The biophysical and NMR experiments are performed on a heavily modified turkey β1AR construct. While this is a common and necessary approach for such studies, the authors should more explicitly discuss the potential limitations of this model. The thermostabilising mutations, particularly the E130W3.41 mutation that is reversed in this study, are known to alter the conformational landscape of the receptor. The authors should discuss whether the "uncoupling" mechanism proposed for AS408 is likely to be relevant in the context of the native, unmodified receptor, and in the human β1AR. The functional data are collected in HEK293T cells, which is good, but the biophysical data are from a different construct.
  - **Why it matters** The translational relevance of the findings is a key part of the paper's significance. If the mechanism is an artefact of the modified construct, its importance is diminished.
  - **Resolution test** The authors should add a discussion of the potential limitations of the thermostabilised construct. They could also perform key experiments, such as the BRET biosensor assay, on a construct that is closer to the wild-type sequence to confirm that the observed effects are not dependent on the specific mutations used for the biophysical studies.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 2
  - **Evidence pointer** Figure 2b, c
  - **Issue** The 19F NMR spectra in Figure 2b are complex and the deconvolution is difficult to follow. The population analysis in Figure 2c is clear, but the connection to the spectra could be made more explicit.
  - **Required correction** Consider adding a schematic or a more detailed annotation to Figure 2b to help the reader understand how the deconvolution was performed and how the populations were derived.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical analysis
  - **Affected element** Figures 1d-f, 3a-c, 6c
  - **Evidence pointer** Figure legends
  - **Issue** The figure legends state that data are mean ± SEM, but the number of independent experiments (n) is not always clear. For example, in Figure 1f, it is stated that n=3 for BLI, but it is not clear if this is biological or technical replicates.
  - **Required correction** Please clarify the number of independent biological replicates for each experiment in the figure legends.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of MD simulations
  - **Affected element** Figure 2e, f
  - **Evidence pointer** Results section "E130X3.41 mutations reduce activity by shifting β1AR equilibria"
  - **Issue** The MD simulations are used to support the interpretation of the NMR data. However, the simulations are only 1 µs long, which may not be sufficient to capture the conformational changes associated with the different mutations. The authors acknowledge this, but the interpretation of the simulation data should be more cautious.
  - **Required correction** The authors should more clearly state the limitations of the MD simulations and avoid over-interpreting the specific interactions observed.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Nomenclature
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract
  - **Issue** The term "allosteric signalling network" is used, but it is not clearly defined. It is unclear if this refers to a specific network of residues or a more general concept.
  - **Required correction** Please define the term "allosteric signalling network" when it is first used.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The central claim of a novel "uncoupling" mechanism is not sufficiently supported by the provided evidence. Direct structural or biophysical evidence is needed.
  - R1-M2: The quantitative link between the NMR population analysis and the functional data is not rigorously established.

- **Assessment against Nature-style criteria**
  - **Originality** The study is original in its approach, combining multiple techniques to dissect the mechanism of a NAM. The concept of "uncoupling" as a mechanism is interesting, but not entirely unprecedented. The idea that a NAM can stabilise a conformation that is not part of the canonical activation pathway is a valuable contribution.
  - **Scientific importance** The findings have the potential to be important for understanding GPCR allostery and for drug development. If the "uncoupling" mechanism is confirmed, it would provide a new paradigm for how NAMs can exert their effects. The detailed characterisation of the E1303.41 mutations is also valuable.
  - **Interdisciplinary readership** The topic is of interest to a broad readership in pharmacology, structural biology, and biophysics. The methods used are sophisticated and will be of interest to specialists. The paper is likely to be cited by researchers in the GPCR field.
  - **Technical soundness** The technical quality of the work is high. The pharmacological and biophysical assays are well-executed. The NMR experiments are state-of-the-art. The MD simulations are standard. However, the interpretation of the data, particularly the NMR data, is not always fully justified.
  - **Readability for nonspecialists** The paper is well-written and the logic is generally clear. However, the complexity of the methods and the data may make it challenging for a non-specialist to fully appreciate the significance of the findings. The abstract is accessible, but the results section is dense.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important and novel finding, but the central claim of a distinct "uncoupling" mechanism requires stronger evidence. The authors should either provide more direct experimental support or revise their conclusions to be more cautious. The quantitative link between the biophysical and functional data should also be strengthened.

## Risk / unsupported claims
- The claim that AS408 stabilises a "non-productive conformation" that is distinct from previously characterised states is not directly supported by the data. It is an interpretation of NMR chemical shifts and MD simulations.
- The claim that the effects of AS408 represent an "uncoupling" of the allosteric network is a hypothesis that is not directly tested.
- The "rheostat" model for E1303.41 mutations is plausible but is not rigorously quantified.
- The relevance of the findings to the native, unmodified human β1AR is not established, as the biophysical experiments are performed on a heavily modified turkey construct.