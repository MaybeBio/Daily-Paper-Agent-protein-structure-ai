## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, materials and methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and methodological soundness as presented in the provided text
- **Shared manuscript claim summary** The authors propose that inter-glycan interactions, specifically involving the isoform-specific N64 glycan and the shared N169 glycan, dynamically modulate the maturation of the N45 N-glycan in human Fcγ receptor III, based on reciprocal site-directed mutagenesis and molecular dynamics simulations
- **Visible evidence base** Descriptive LC-MS/MS glycoprofiles from single measurements for six FcγRIII variants; MD simulation contact maps, contact frequencies, hydrogen bond analyses, and SASA calculations for M8B and Man5 glycan models
- **Missing materials affecting confidence** Raw mass spectrometry data, statistical analyses, replicate measurements, simulation trajectory details, convergence assessments, force field validation, and supplementary figures/tables referenced but not provided

## Reviewer
- **Overall assessment** The manuscript addresses a timely and mechanistically important question in glycobiology, namely whether neighboring glycans can modulate site-specific N-glycan processing in a mammalian immune receptor. The combination of reciprocal mutagenesis and MD simulation is conceptually appropriate. However, the experimental evidence is limited to descriptive single-measurement glycoprofiles without replicates or statistical analysis, and the simulation methodology lacks sufficient detail to assess convergence and robustness. The central claim that dynamic inter-glycan contacts regulate N45 maturation is plausible but not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in glycobiology, glycoproteomics, and biopharmaceutical development would be interested. The findings bear on predictive models of glycoform heterogeneity, which are relevant for therapeutic antibody and Fc-fusion protein production. The proposed mechanism of inter-glycan regulation could also inform studies of other densely glycosylated receptors and viral envelope proteins.
- **Major strengths** The study addresses a specific and well-defined question with a clear hypothesis. The reciprocal mutagenesis design is elegant, leveraging the natural isoform difference between FcγRIIIa and FcγRIIIb. The use of MD simulations with two glycan models (M8B and Man5) to probe different processing stages is thoughtful. The authors appropriately acknowledge the descriptive nature of their glycoprofiles and frame their conclusions cautiously.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental evidence
  - **Claim pointer** The authors claim that introduction of the N64 sequon into FcγRIIIa reduced N45 glycan maturation and that N64 removal from FcγRIIIb produced the reciprocal effect, based on glycoprofiles shown in Fig. 2
  - **Evidence pointer** Results and discussion, Fig. 2, Supplementary Table S1
  - **Concern** The glycoprofiles are derived from single LC-MS/MS measurements per sample, with no biological replicates, technical replicates, or statistical analysis. The authors explicitly state this limitation in the Materials and methods. Without replicate measurements, it is impossible to assess whether the observed differences between variants (e.g., 86.7% vs. 40.5% complex/hybrid at N45) are reproducible or within experimental variability. The claim of a reciprocal effect rests entirely on these unvalidated single measurements.
  - **Why it matters** The central experimental conclusion depends on quantitative differences in glycoform distributions. Single measurements cannot establish the reliability of these differences, and the absence of error bars or statistical testing precludes any assessment of effect size or significance. This is a fundamental limitation that affects the validity of the primary claim.
  - **Resolution test** Provide at least three biological replicates per variant with full statistical analysis (e.g., ANOVA with multiple comparison correction). Show that the observed differences are reproducible and statistically significant. If replicates are not feasible, the claims must be substantially weakened and reframed as preliminary observations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Simulation methodology
  - **Claim pointer** The authors claim that MD simulations show high-frequency N45-N64 contacts (0.94 and 0.86 in FcγRIIIa(D64N) and FcγRIIIb, respectively) and that these contacts support the relevance of inter-glycan interactions to N45 maturation
  - **Evidence pointer** Results and discussion, Fig. 4, Supplementary Fig. S2, Supplementary Table S2
  - **Concern** The simulation methodology is described with insufficient detail to evaluate its robustness. The total production time per replica (73.5 ns) is short for glycoprotein systems, and no convergence assessment is reported. The contact definition (minimum distance less than 3 Å) is stringent and may not capture biologically relevant glycan-glycan interactions. The use of a single starting structure (PDB 1FNL) with modeled mutations and glycan attachments introduces potential bias that is not addressed. No information is provided on replica exchange acceptance rates, effective sampling, or equilibration quality.
  - **Why it matters** The simulation results are used as direct evidence for the proposed mechanism. If the simulations are not converged or the contact definition is inappropriate, the reported contact frequencies may not reflect the true dynamical behavior of the system. The mechanistic conclusion would be unsupported.
  - **Resolution test** Provide detailed convergence analysis (e.g., block averaging, time evolution of contact frequencies), report replica exchange statistics, justify the contact definition, and consider longer simulations or multiple independent starting structures. If convergence cannot be demonstrated, the simulation claims should be downgraded to preliminary observations.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic interpretation
  - **Claim pointer** The authors state that "the N45 glycan dynamically contacts neighboring N64 and N169 glycans" and that these contacts "reshape the local glycan environment around N45," implying a causal relationship between inter-glycan contacts and reduced maturation
  - **Evidence pointer** Abstract, Results and discussion, Fig. 4
  - **Concern** The correlation between contact frequency and reduced maturation is not established as causal. The authors do not demonstrate that the contacts specifically occlude access of processing enzymes (e.g., mannosidases) to the N45 glycan. Alternative explanations, such as altered protein conformation or dynamics induced by the N64 glycan, are not excluded. The N169Q single mutant shows minimal effect on N45 processing (89.1% complex/hybrid vs. 86.7% in wild-type), yet N169 is reported to contact N45 at high frequency in wild-type FcγRIIIa. This inconsistency is not addressed.
  - **Why it matters** The proposed mechanism requires that inter-glycan contacts directly limit enzyme access. Without demonstrating occlusion or excluding alternative mechanisms, the interpretation remains speculative. The N169Q result, in particular, appears to contradict the proposed model and requires explanation.
  - **Resolution test** Perform additional simulations or experiments that directly test the occlusion hypothesis, such as measuring solvent accessibility of the N45 glycan in the presence and absence of N64, or comparing enzyme kinetics on wild-type and mutant substrates. Address the N169Q inconsistency explicitly.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Fig. 2 glycoprofiles
  - **Evidence pointer** Results and discussion, Fig. 2
  - **Issue** The glycoprofiles are described as "descriptive" and based on single measurements, but the figure presumably presents them as bar charts or pie charts without error bars. This presentation may mislead readers into interpreting the differences as robust.
  - **Required correction** Clearly label the figure as descriptive single-measurement data, and consider presenting raw values in a table format to avoid implying statistical significance.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Quantification methodology
  - **Affected element** Glycoform quantification
  - **Evidence pointer** Materials and methods, Quantification and classification of N45 glycoforms
  - **Issue** The quantification uses precursor ion intensities from a single glycopeptide, excluding missed-cleavage peptides and minor variants. This approach may introduce bias if the chosen glycopeptide is not representative of the total N45 glycan population.
  - **Required correction** Justify the choice of the single glycopeptide for quantification, or show that alternative glycopeptide forms yield consistent results.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Simulation model choice
  - **Affected element** MD simulation glycan models
  - **Evidence pointer** Materials and methods, Molecular dynamics simulations
  - **Issue** The use of M8B and Man5 models is justified, but the choice of these specific glycan compositions over others (e.g., M9 or GlcNAc-terminated species) is not explained. The relevance of these models to the actual processing states in the experimental system is unclear.
  - **Required correction** Provide a brief justification for the glycan model choices and discuss how they relate to the experimental glycoform distributions.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction and Discussion
  - **Evidence pointer** Introduction, Results and discussion
  - **Issue** The discussion of prior work on inter-glycan interactions in viral glycoproteins is brief. A more detailed comparison with those systems, including the proposed mechanisms, would strengthen the contextual framing.
  - **Required correction** Expand the discussion of relevant prior work on glycan-glycan interactions and their functional consequences.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data and code availability
  - **Evidence pointer** Data and code availability
  - **Issue** The mass spectrometry data are deposited, but simulation input files, trajectories, and analysis scripts are not mentioned. This limits reproducibility of the computational work.
  - **Required correction** Deposit simulation input files, parameter files, and analysis scripts in a public repository, and provide access details.

## Risk / unsupported claims
- The claim that N64 introduction "reduced N45 glycan maturation" in FcγRIIIa is unsupported due to single-measurement data without replicates or statistical analysis
- The claim that N64 removal "shifted N45 in the opposite direction" in FcγRIIIb is similarly unsupported for the same reason
- The claim that N45-N64 contacts "reshape the local glycan environment" is not directly demonstrated; the simulations show contact frequencies but do not establish a causal link to enzyme accessibility
- The statement that "N45 maturation appears to be limited by an intrinsic local structural environment" is presented as a conclusion but is not directly tested in this study
- The relevance of the MD simulation results to the experimental system is not fully established, as the simulations use model glycan compositions that may not match the actual processing states
- The N169Q result (minimal effect on N45 processing despite high contact frequency) is inconsistent with the proposed model and is not explained, undermining the generalizability of the inter-glycan contact mechanism

## Assessment against Nature-style criteria
- **Originality** The concept of inter-glycan interactions modulating site-specific glycan maturation in a mammalian receptor is relatively novel. Most prior work has focused on protein-glycan or enzyme-substrate interactions. The idea that glycans can dynamically influence each other's processing adds a new dimension. However, similar concepts have been proposed for viral glycoproteins, so the novelty is incremental rather than paradigm-shifting.
- **Scientific importance** The question of what determines site-specific glycan processing is of broad importance in glycobiology and biopharmaceutical development. If the proposed mechanism is validated, it could inform predictive models of glycoform heterogeneity. However, the current evidence is too limited to establish the mechanism with confidence, and the importance of the specific finding (N64 as a modulator) is modest given that it is one of several factors likely at play.
- **Interdisciplinary readership** The topic bridges glycobiology, structural biology, and computational biophysics. The manuscript is written in a way that is accessible to glycobiologists, but the simulation methodology may be challenging for non-specialists. The broader significance for immunology and biotherapeutics is mentioned but not developed in depth.
- **Technical soundness** The experimental design (reciprocal mutagenesis) is sound in principle, but the lack of replicates and statistical analysis is a significant technical weakness. The simulation methodology is described at a level that is insufficient to assess its technical quality. The contact definition and simulation length raise concerns about the reliability of the results.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. The abstract and introduction effectively frame the question. However, the results section assumes familiarity with glycan classification and simulation terminology, which may limit accessibility for a broader readership.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents an interesting hypothesis and a conceptually appropriate experimental approach, but the experimental data are descriptive single measurements without statistical validation, and the simulation methodology is insufficiently detailed to assess robustness. The central claim of inter-glycan regulation of N45 maturation is plausible but not convincingly demonstrated. The authors should be encouraged to provide replicate measurements with statistical analysis, strengthen the simulation methodology and convergence assessment, and address the inconsistency posed by the N169Q result. If these concerns are resolved, the manuscript could make a valuable contribution to the field.