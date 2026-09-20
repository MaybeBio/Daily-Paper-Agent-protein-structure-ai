## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodological soundness, and interpretation of results as presented in the manuscript
- **Shared manuscript claim summary** The authors use computational methods (AlphaFold3, CavityPlus, AllositePro, Gromacs MD, HDOCK) to predict interaction interfaces between two lncRNAs (MALAT1, H19) and two diabetes-related proteins (ASK1, YAP1) in Rattus norvegicus, and propose that these predicted interfaces may have biological relevance in diabetes-related signalling pathways.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results (including Tables 1-8 and Figures 1-10), Discussion, Limitations, Conclusion
- **Missing materials affecting confidence** Supplementary data files, PDB structures, MD trajectory files, docking output files, sequence alignment details, validation metrics for docking (e.g., RMSD of docking poses), and any code or parameter files for reproducibility

## Reviewer

- **Overall assessment** This manuscript presents a purely computational, hypothesis-generating study aimed at predicting lncRNA-protein interaction interfaces. The topic is of potential interest to the diabetes and non-coding RNA communities, and the authors are appropriately cautious in framing their findings as hypotheses requiring experimental validation. However, the study has several significant technical weaknesses that undermine confidence in the reported results. The structural models for the lncRNAs are acknowledged to have low global confidence (pTM < 0.5), and MALAT1's model reportedly contains severe atomic clashes (ranking score of -99.81), yet these models are used directly for docking without any reported correction or refinement. The molecular dynamics simulations are performed only on unliganded proteins, not on the docked complexes, which limits the ability to assess complex stability. The docking results are reported without any validation metrics (e.g., comparison to known complexes, cross-docking, or experimental benchmarks). The manuscript also contains internal inconsistencies, such as the abstract stating "PAE < 1 Å" as evidence of high confidence while the methods section correctly notes that PAE values below 5 Å indicate very high confidence, and the results section misinterprets the meaning of pTM for lncRNA models. The claim that H19 binds near the TEAD-binding domain and phosphorylation sites is based on spatial proximity in a low-confidence model and is presented with appropriate caution, but the overall evidence base is too weak to establish the case. The manuscript would benefit from substantial additional analyses, including model refinement, docking validation, and ideally, experimental correlation or at least comparison with known RNA-binding protein data.

- **Who would be interested in the results, and why** Researchers studying the role of lncRNAs in diabetes and metabolic diseases, particularly those interested in MALAT1 and H19 biology, may find the predicted interaction interfaces of interest as a starting point for experimental studies. Computational biologists working on RNA-protein interaction prediction may also be interested in the methodological pipeline, though they would likely note the limitations. The study may also be of interest to groups studying YAP1 regulation and Hippo signalling, given the predicted H19 interactions near the TEAD-binding domain and phosphorylation sites.

- **Major strengths** The authors are appropriately cautious in their interpretation, repeatedly stating that their findings are hypothesis-generating and require experimental validation. The study addresses a relevant and under-explored topic, namely the structural basis of lncRNA-protein interactions in diabetes-related pathways. The use of multiple complementary computational methods (structure prediction, cavity analysis, MD, docking) is a reasonable approach for a hypothesis-generating study. The authors acknowledge key limitations, including the low confidence of lncRNA models and the lack of complex MD simulations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "Structural assessment showed high local confidence for both proteins and lncRNAs (PAE < 1 Å)" and use the AlphaFold3 models for subsequent docking studies.
- **Evidence pointer** Abstract; Results, Table 1; Materials and Methods, Molecule modelling
- **Concern** The manuscript reports that MALAT1's model has a ranking score of -99.81, which the authors attribute to "a massive physical collision of atoms or clashes." Despite this acknowledged severe defect, the same model is used for molecular docking without any reported correction, refinement, or energy minimization. Similarly, both lncRNA models have pTM values below 0.5, indicating low global confidence, yet the docking results are presented as meaningful predictions. The use of structurally flawed models for docking undermines the reliability of all subsequent interface predictions. The authors should either refine the models, use alternative approaches for RNA structure prediction, or clearly demonstrate that the docking results are robust to the identified model defects.
- **Why it matters** Docking results are only as reliable as the input structures. If the RNA models contain severe atomic clashes and low global confidence, the predicted interfaces may be artifacts of the flawed models rather than biologically meaningful interactions. This directly affects the validity of the central claims of the study.
- **Resolution test** The authors should provide evidence that the docking results are robust to model quality, for example by: (1) refining the RNA models (e.g., using RNA-specific structure prediction tools or energy minimization) and repeating docking; (2) comparing docking results across multiple independent RNA structure predictions; or (3) demonstrating that the predicted interfaces are consistent with known RNA-binding protein preferences or experimental data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "Molecular dynamics indicated transient stabilisation with persistent conformational heterogeneity" and use MD results to support the biological plausibility of the predicted interactions.
- **Evidence pointer** Results, ASK1 analyses; Results, YAP1 analyses; Table 3; Figures 2, 3, 7, 8
- **Concern** The molecular dynamics simulations were performed only on the unliganded proteins, not on the docked protein-lncRNA complexes. The authors acknowledge this in the Limitations section, but the MD results are nevertheless used in the Results and Discussion to support the stability and relevance of the predicted complexes. MD simulations of the apo proteins cannot provide information about the stability of the predicted protein-RNA complexes. The high RMSD values reported (e.g., ASK1 mean RMSD of 12.38 Å, YAP1 mean RMSD of 35.24 Å) indicate substantial conformational changes from the starting structures, which raises questions about the relevance of the initial AlphaFold3 models for docking. The authors should either perform MD simulations of the docked complexes or clearly separate the MD results (which describe protein dynamics) from the docking results (which describe predicted complexes) and avoid using the former to support the latter.
- **Why it matters** The MD results are used to support the biological relevance of the predicted interactions, but they do not actually test the stability of those interactions. This conflation of apo-protein dynamics with complex stability is a logical error that could mislead readers about the strength of the evidence.
- **Resolution test** The authors should either: (1) perform MD simulations of the docked complexes and report complex stability metrics (e.g., protein-RNA contacts over time, binding free energy estimates); or (2) revise the text to clearly state that MD was used only to assess protein dynamics and does not provide evidence for complex stability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report docking scores and confidence scores for the predicted complexes and select Model 1 as the best interaction pose.
- **Evidence pointer** Results, ASK1-MALAT1 binding complexes, Table 4; Results, YAP1-H19 binding complexes, Table 7
- **Concern** The docking results are reported without any validation. No metrics are provided to assess the quality of the docking poses (e.g., comparison with known RNA-protein complex structures, cross-docking validation, or assessment of the docking energy landscape). The ligand RMSD values for the ASK1-MALAT1 complex are extremely high (e.g., 139.48 Å for Model 1), which suggests that the RNA is not docked in a well-defined binding pose but rather in a highly extended or unrealistic conformation. The authors do not explain how these RMSD values should be interpreted or why Model 1 is preferred over models with lower RMSD values. The selection of Model 1 based solely on docking score without considering structural plausibility is not justified.
- **Why it matters** Without validation, the docking results cannot be distinguished from random or artefactual predictions. The high ligand RMSD values suggest that the docking may not have converged to a meaningful binding mode, which would invalidate the interface predictions.
- **Resolution test** The authors should provide: (1) a clear justification for the selection of Model 1, including consideration of structural plausibility and not just docking score; (2) validation of the docking protocol, for example by docking a known RNA-protein complex and showing that the correct interface is recovered; or (3) comparison of the predicted interfaces with known RNA-binding sites on these proteins or homologous proteins.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "these results identify structurally plausible RNA-protein interaction interfaces that overlap with known regulatory hotspots in YAP1" and discuss potential implications for diabetes-related signalling.
- **Evidence pointer** Abstract; Discussion, YAP1-H19 complex
- **Concern** The biological relevance of the predicted interactions to diabetes is not established. The authors note that most experimental evidence for YAP1 phosphorylation sites comes from cancer and developmental biology models, and they do not provide any diabetes-specific context beyond general statements about metabolic dysregulation. The connection between the predicted interfaces and diabetes-related pathology is entirely speculative. While the authors are appropriately cautious in their language, the framing of the study as relevant to diabetes may overstate the significance of the findings.
- **Why it matters** The study's significance is partly based on its relevance to diabetes, but the evidence linking the predicted interactions to diabetes is weak. This could mislead readers about the potential clinical or translational relevance of the findings.
- **Resolution test** The authors should either: (1) provide additional computational evidence linking the predicted interactions to diabetes-specific pathways (e.g., analysis of diabetes-associated mutations or expression data); or (2) revise the framing to more clearly position the study as a general hypothesis-generating investigation of lncRNA-protein interactions, with diabetes as one potential context.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "Docking and simulations suggested MALAT1 binding to exposed ASK1 surfaces, while H19 was predicted to associate with YAP1 regions encompassing the TEAD-binding domain and conserved regulatory phosphorylation sites."
- **Evidence pointer** Abstract; Results, ASK1-MALAT1 interface; Results, YAP1-H19 interface; Tables 5 and 8
- **Concern** The interface analysis is presented as a list of residues and nucleotides, but no analysis is provided to assess the chemical complementarity of the interfaces, the conservation of the interacting residues across species, or the potential functional significance of the specific contacts. The authors do not discuss whether the predicted interfaces are consistent with known RNA-binding properties of these proteins (e.g., surface charge, hydrophobicity, known RNA-binding domains). The lack of any interface analysis beyond listing contacting residues limits the biological interpretation of the results.
- **Why it matters** A list of contacting residues without analysis of the interface properties does not provide meaningful insight into the potential function or specificity of the predicted interactions. This weakens the biological interpretation and the value of the study as a hypothesis-generating resource.
- **Resolution test** The authors should provide additional analysis of the predicted interfaces, such as: (1) assessment of interface complementarity (e.g., shape, charge, hydrogen bonding); (2) conservation analysis of the interacting residues; or (3) comparison with known RNA-binding proteins or RNA-binding domains.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "PAE < 1 Å" as evidence of high confidence, but the methods section defines PAE < 5 Å as very high confidence. The abstract's threshold is unnecessarily strict and inconsistent with the methods.
- **Required correction** Revise the abstract to use the same PAE threshold as the methods section, or clarify the significance of the specific PAE values obtained.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results, ASK1-MALAT1 binding complexes
- **Evidence pointer** Table 4
- **Concern** The ligand RMSD values in Table 4 are extremely high (ranging from 76.52 to 196.68 Å), which is unusual for docking results. The authors do not explain how these values should be interpreted or why such high RMSD values are expected for RNA-protein docking.
- **Required correction** Provide an explanation for the high ligand RMSD values, or discuss whether these values indicate that the docking poses are not well-defined.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, Molecular docking studies
- **Evidence pointer** Materials and Methods, Molecular docking studies
- **Issue** The methods section does not specify the version of the HDART server used, the parameters for the docking, or how the top 10 models were generated and ranked. This limits reproducibility.
- **Required correction** Provide additional details on the docking protocol, including software version, parameters, and model selection criteria.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results, YAP1 analyses
- **Evidence pointer** Figure 7
- **Concern** The figure caption for Figure 7 contains a typographical error ("trayectory" instead of "trajectory").
- **Required correction** Correct the typographical error in the figure caption.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Discussion, YAP1-H19 complex
- **Evidence pointer** Discussion, YAP1-H19 complex
- **Issue** The discussion of O-GlcNAcylation and mechanobiological context, while interesting, is not directly connected to the predicted H19 interaction interfaces. The authors note that the predicted interfaces do not overlap with the O-GlcNAcylation site, and the mechanobiological discussion is general. This section reads as background rather than as a direct interpretation of the results.
- **Required correction** Either strengthen the connection between these topics and the predicted interfaces, or move this material to the Introduction to provide context.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results, ASK1-MALAT1 interface
- **Evidence pointer** Results, ASK1-MALAT1 interface
- **Issue** The sentence "Model 1, obtained from the molecular docking studies, showed that at the interface of the ASK1-MALAT1 complex (Fig. 5)." is grammatically incomplete.
- **Required correction** Revise the sentence for grammatical correctness.

## Risk / unsupported claims
- The claim that MALAT1 binds to ASK1 and H19 binds to YAP1 is unsupported by the evidence provided, as the docking results are based on low-confidence RNA models and are not validated.
- The claim that the predicted interfaces "overlap with known regulatory hotspots in YAP1" is based on spatial proximity in a low-confidence model and is not supported by any functional data.
- The claim that "molecular dynamics indicated transient stabilisation" of the complexes is unsupported, as MD was performed only on unbound proteins, not on the complexes.
- The biological relevance of the predicted interactions to diabetes is not established and is presented as speculation, which is acknowledged by the authors but still framed as a significant finding.
- The use of AlphaFold3 for lncRNA structure prediction is not validated, and the authors do not discuss the known limitations of AlphaFold for RNA structure prediction.
- The manuscript does not provide any comparison with experimental data on MALAT1-ASK1 or H19-YAP1 interactions, which would be necessary to assess the plausibility of the predictions.