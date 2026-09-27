## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific validity, methodological rigor, claims substantiation, and presentation quality of the reported work
- **Shared manuscript claim summary** The authors repurpose AlphaFold Multimer (AFM) as a classification model to predict protein-protein interactions across the entire human mitochondrial proteome, generating a compendium of 2,895 predicted interactions (MitoMatch). They report 85% precision, link 85 uncharacterized proteins to potential pathways, extend predictions to 11 eukaryotic organisms, and experimentally validate selected predictions in the coenzyme Q metabolon and mitochondrial copper delivery pathway, including a novel COA4-COX11 interaction.
- **Visible evidence base** Abstract, full introduction, full results section with figure descriptions, full discussion, full methods section, supplementary information descriptions
- **Missing materials affecting confidence** Actual figures and supplementary data files (Supplementary Data 1-3, Supplementary Tables 1-2, Supplementary Figures 1-13) are not provided; detailed statistical outputs and quality metrics for AFM predictions are not fully visible; raw mass spectrometry data and complete volcano plot results are not accessible

## Reviewer
- **Overall assessment** This manuscript presents a large-scale computational screen using AlphaFold Multimer to predict mitochondrial protein-protein interactions, with experimental validation for selected predictions. The scale of the screen (630,003 pairs) and the focus on a well-defined organellar proteome are commendable. The experimental follow-up on COA4-COX11 is a strong feature that elevates the work beyond a purely computational resource. However, several methodological concerns regarding the validation of the classification approach, the handling of false positives, and the interpretation of conservation analyses need to be addressed. The manuscript is potentially important for the mitochondrial biology community, but the current evidence does not fully establish the reliability of the full interactome resource.

- **Who would be interested in the results, and why** Mitochondrial biologists studying uncharacterized proteins, bioinformaticians developing protein-protein interaction prediction methods, researchers studying coenzyme Q biosynthesis, and investigators working on cytochrome c oxidase assembly and mitochondrial copper metabolism. The resource could accelerate functional annotation of orphan mitochondrial proteins.

- **Major strengths**
  1. The scale and systematic nature of the screen across the entire mitochondrial proteome is ambitious and potentially valuable.
  2. The use of a recent PDB dataset for benchmarking the classification approach is appropriate and addresses training contamination concerns.
  3. The experimental validation of the COA4-COX11 interaction, including reciprocal co-IP in both yeast and human cells, provides strong evidence for at least one novel prediction.
  4. The demonstration that AFM can recover known interactions and predict structures consistent with experimental data adds credibility.
  5. The resource is made publicly available through a web portal, which will facilitate community use.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim 85% precision for their AFM-based classification approach and use an ipTM cutoff of 0.5 to define interactions.
- **Evidence pointer** Results section, Figure 1b-c, Supplementary Figure 2b-c
- **Concern** The precision estimate of 85% is derived from a small curated test set of 12 experimentally validated mitochondrial interactions. This is an extremely small sample size for estimating a precision rate, and the confidence interval around this estimate must be very wide. The authors do not report the number of true positives and false positives at the chosen cutoff in this test set, nor do they provide confidence intervals. Furthermore, the test set is limited to copper delivery pathway proteins, which may not be representative of the diverse interaction types across the entire mitochondrial proteome.
- **Why it matters** The entire resource is predicated on the reliability of the classification. If the precision estimate is not robust, the 2,895 predicted interactions may contain a substantial number of false positives, undermining the utility of MitoMatch for hypothesis generation.
- **Resolution test** Provide the full confusion matrix for the test set at the chosen cutoff, report confidence intervals for the precision estimate, and ideally validate the cutoff on a larger, more diverse set of experimentally confirmed mitochondrial interactions from multiple pathways.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "using the mean ipTM as a classifier metric yielded ~40% of all true positives at 90% precision whereas the best ipTM score yielded only 30% of the true hits at the same precision."
- **Evidence pointer** Results section, Figure 1c
- **Concern** The precision-recall analysis is performed on a dataset with a 1:100 true:false ratio, which is an artificial construct. The actual ratio of true to false interactions in the mitochondrial proteome is unknown and likely much lower than 1:100. The performance metrics derived from this artificial ratio may not translate to the actual screening conditions. Additionally, the authors do not report the area under the precision-recall curve or other summary statistics that would allow comparison with other methods.
- **Why it matters** The choice of the mean over the max ipTM score is justified based on this analysis. If the analysis is not representative of real screening conditions, the justification for this methodological choice is weakened.
- **Resolution test** Perform a sensitivity analysis varying the true:false ratio across a plausible range and show that the superiority of the mean ipTM score is robust. Report additional performance metrics such as the area under the precision-recall curve.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "MitoMatch provides a resource for annotating uncharacterized mitochondrial proteins by identifying the proteins they interact with."
- **Evidence pointer** Discussion section
- **Concern** While the resource is potentially useful, the manuscript does not provide a systematic assessment of how many of the 85 uncharacterized proteins with predicted partners have predictions that are likely to be biologically meaningful. The authors show a heatmap of predicted interactions across pathways, but do not discuss whether the predicted partners for orphan proteins are enriched in specific pathways or functional categories in a way that would support specific functional hypotheses. The experimental validation focuses on only one protein (COA4).
- **Why it matters** The claim that this resource will "greatly accelerate the functionalization of the human mitochondrial proteome" is strong. To support this, the authors should demonstrate that the predictions for orphan proteins are not random and provide some prioritization or functional enrichment analysis.
- **Resolution test** Perform a functional enrichment analysis on the predicted interaction partners of the 85 uncharacterized proteins. Show that the predicted partners are enriched in specific pathways or complexes beyond what would be expected by chance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "extending the AFM-based analysis to 11 diverse eukaryotes identifies evolutionarily conserved interactions among human hits, including regulators of core bioenergetic pathways."
- **Evidence pointer** Results section, Figure 2
- **Concern** The conservation analysis relies on reciprocal best-hit searches to identify orthologs. This approach can miss paralogous relationships and may not accurately reflect functional conservation. The authors report that 93%, 87%, and 44% of homologous hits are predicted to be interacting in chimpanzee, mouse, and yeast, respectively, but do not provide a statistical framework for assessing whether these rates are significantly higher than expected by chance. A proper null model is needed to establish that conservation rates are meaningful.
- **Why it matters** The conservation analysis is presented as a key feature of the resource, providing cross-species validation. Without a statistical framework, the observed conservation rates could be trivially high or low.
- **Resolution test** Generate a null distribution of conservation rates by shuffling interaction labels or using randomized protein pairs matched for expression or other properties. Show that the observed conservation rates are significantly higher than the null.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "our analysis further revealed that a total number of interface residues of greater than 20 and lower global stoichiometry... also increased the ipTM score."
- **Evidence pointer** Results section, Supplementary Figure 1c-f
- **Concern** This analysis identifies factors that influence ipTM scores, but the authors do not incorporate these factors into their screening pipeline or use them to adjust confidence in individual predictions. If certain types of interactions are systematically more likely to receive high ipTM scores, the resource may be biased toward those interaction types.
- **Why it matters** Understanding the biases in the prediction method is important for users of the resource. If the authors have identified factors that influence scores, they should either account for them in the scoring or clearly communicate these biases to users.
- **Resolution test** Discuss how the identified factors affect the interpretation of predictions. Consider providing per-interaction confidence metrics that account for these factors, or at minimum, provide guidance to users on how to interpret predictions for different interaction types.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction moves quickly from the general problem of uncharacterized mitochondrial proteins to the specific approach of using AFM. A brief explanation of how AFM works and why ipTM scores are suitable for interaction prediction would help nonspecialist readers understand the methodological foundation.
- **Required correction** Add 2-3 sentences in the introduction explaining the basic principle of AFM and the meaning of ipTM scores in the context of interaction prediction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, AlphaFold Multimer pipeline
- **Evidence pointer** Methods section
- **Issue** The description of the AFM pipeline is brief. Details on model versions, number of recycles, and any filtering of predictions based on confidence beyond the ipTM cutoff are not provided.
- **Required correction** Provide additional details on the AFM version used, the number of seeds or models averaged, and any additional filtering criteria applied to the predictions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, MitoMatch resource
- **Evidence pointer** Results section, Figure 1e
- **Concern** The comparison with existing databases (STRING, BioGRID, IntAct, BioPlex, HuRI, PDB) is presented as a single percentage (43% recovery). It would be informative to know the recovery rate for each database individually, as they have different coverage and reliability.
- **Required correction** Provide a breakdown of the recovery rate for each database separately, perhaps as a supplementary table or additional panel in Figure 1.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Coenzyme Q section
- **Evidence pointer** Results section, Figure 3
- **Concern** The description of the coenzyme Q metabolon experiments is dense and assumes significant background knowledge of the CoQ biosynthesis pathway. Nonspecialist readers may struggle to understand the significance of the identified interactions.
- **Required correction** Add a brief introductory sentence in this section explaining the CoQ biosynthesis pathway and why identifying the metabolon components is important.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Statistical analysis
- **Evidence pointer** Methods section
- **Issue** The statistical analysis section is very brief. Details on multiple testing corrections for the mass spectrometry data, normalization methods, and criteria for defining significant interactors are not fully described.
- **Required correction** Expand the statistical analysis section to include details on data normalization, significance thresholds, and multiple testing corrections.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Copper delivery pathway
- **Evidence pointer** Results section, Figure 4
- **Concern** The manuscript states that COA4-KO cells show reduced COX11 abundance and reduced mitochondrial copper content, but the mechanistic link between COA4 and COX11 function is not fully explored. The authors suggest a role in copper delivery but do not directly demonstrate a defect in copper transfer to COX11 or downstream targets.
- **Required correction** Acknowledge this limitation explicitly in the discussion and suggest future experiments to directly test the mechanistic role of COA4 in copper transfer.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (precision estimate based on 12 interactions), R1-M2 (artificial true:false ratio in precision-recall analysis), R1-M4 (lack of statistical framework for conservation analysis)

- **Assessment against Nature-style criteria**
  - **Originality**: The application of AFM to a complete organellar proteome is a novel and potentially valuable contribution. The focus on the mitochondrial proteome is well-chosen given its biological importance and the number of uncharacterized proteins. The experimental validation of a specific prediction (COA4-COX11) adds originality beyond purely computational work.
  - **Scientific importance**: The resource has the potential to accelerate functional annotation of mitochondrial proteins, which is an important goal. The experimental validation of COA4 provides a proof-of-concept that could inspire similar approaches. However, the full impact will depend on the reliability of the predictions, which is not fully established.
  - **Interdisciplinary readership**: The work bridges computational biology, structural biology, and mitochondrial biochemistry. The resource could be of interest to a broad audience, but the presentation is somewhat specialized and may not fully engage nonspecialists.
  - **Technical soundness**: The core methodology is sound in principle, but the validation of the classification approach is based on a very small test set, and the precision-recall analysis uses an artificial ratio. The conservation analysis lacks a statistical framework. These issues need to be addressed to establish technical reliability.
  - **Readability for nonspecialists**: The manuscript is generally well-written but assumes significant background knowledge in both computational biology and mitochondrial biology. Some sections, particularly the coenzyme Q and copper delivery experiments, are dense and may be challenging for nonspecialist readers.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially valuable resource with a strong experimental validation component. However, the reliability of the full interactome is not fully established due to the small validation set and the lack of statistical rigor in the conservation analysis. These issues should be addressed before the resource can be recommended for broad use.

## Risk / unsupported claims
- The claim of 85% precision for the AFM-based classification is not robustly supported given the small test set (12 interactions) and the lack of confidence intervals.
- The claim that the mean ipTM score is superior to the max ipTM score is based on an artificial 1:100 true:false ratio and may not hold under real screening conditions.
- The claim that conserved interactions are "evolutionarily conserved" is based on reciprocal best-hit analysis without a statistical framework to rule out chance.
- The claim that MitoMatch "will greatly accelerate the functionalization of the human mitochondrial proteome" is speculative and not directly supported by the data presented.
- The statement that the COA4-COX11 interaction places COA4 "at a specific step in the mitochondrial copper delivery pathway" is partially supported by the data, but the mechanistic details of COA4 function remain unclear.