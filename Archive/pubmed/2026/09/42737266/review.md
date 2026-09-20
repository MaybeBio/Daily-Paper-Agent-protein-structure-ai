## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors propose that malondialdehyde (MDA) induces deterioration of water-holding capacity (WHC) in bovine myofibrillar proteins (MPs) through a mechanism involving cysteine redox remodeling, secondary and tertiary structural rearrangement, and enhanced disulfide-associated cross-linking, with molecular docking supporting spatial feasibility of MDA association near identified cysteine sites.
- **Visible evidence base** Figures 1-5 (described in text), Table 1 (amino acid composition), Table 2 (57 cysteine sites), Table 3 (docking scores), Table S1 (referenced), methods sections 2.1-2.16
- **Missing materials affecting confidence** Actual figure images, Table 1-3 data values, Table S1, raw proteomics data, docking coordinate files, statistical output details, validation parameters for proteomics and docking

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question in meat science, namely the molecular mechanism by which MDA compromises WHC of myofibrillar proteins. The study combines multiple analytical techniques including multispectral methods, redox proteomics, and molecular docking, which is a commendable integrative approach. However, several concerns limit the strength of the conclusions. The causal link between cysteine redox modifications and WHC deterioration is inferred rather than directly demonstrated. The molecular docking results are presented as supporting spatial feasibility, but the scores are weak and the selection of only 12 of 57 sites for docking is not justified. The redox proteomics methodology, while described, lacks critical validation details. The study is largely correlative, and the authors appropriately acknowledge that validation in whole-meat systems is needed, but the mechanistic claims in the title and abstract are stronger than the evidence supports.

- **Who would be interested in the results, and why** Researchers in meat science and food protein chemistry would be interested in the identification of specific cysteine sites in myofibrillar proteins that respond to MDA treatment. Those studying lipid-protein co-oxidation mechanisms would find the integrative approach combining redox proteomics with structural analysis useful. The potential practical implications for meat processing and preservation, particularly regarding antioxidant interventions, would interest food technologists. The study may also be relevant to the broader oxidative stress and protein modification community, though the food science framing limits this reach.

- **Major strengths** The study addresses a mechanistically important question with practical relevance. The combination of WHC measurements, structural analysis, redox proteomics, and molecular docking is methodologically ambitious and provides multiple lines of evidence. The identification of 57 specific cysteine sites in structural proteins is a valuable dataset. The authors appropriately acknowledge limitations, including the need for whole-meat validation. The discussion of the biphasic nature of oxidation effects on protein structure is thoughtful and well-reasoned.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The title and abstract state a "mechanism of MDA-induced deterioration in WHC" and claim that "cysteine redox remodeling was associated with structural reorganization and increased water mobility, thereby contributing to WHC deterioration."
- **Evidence pointer** Abstract; Sections 3.1-3.6; Discussion
- **Concern** The study demonstrates correlations between MDA concentration, structural changes, cysteine oxidation, and WHC loss, but does not establish causality. No experiments directly manipulate cysteine oxidation (e.g., thiol-blocking agents, reducing agents, site-directed mutagenesis) to demonstrate that cysteine modification is necessary or sufficient for WHC deterioration. The claim of a "mechanism" implies causal understanding that the data do not provide.
- **Why it matters** The central claim of the manuscript is mechanistic. Without causal evidence, the study remains descriptive and correlative. The title and abstract overstate what the experimental design can establish.
- **Resolution test** Provide direct experimental evidence that preventing cysteine oxidation (e.g., via thiol-protecting agents) or restoring thiols (e.g., via reducing agents) attenuates WHC loss, or temper the mechanistic claims to correlative ones.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Molecular docking validity
- **Claim pointer** "Molecular docking of 12 representative cysteine sites supported the spatial feasibility of MDA pre-association near these cysteine-containing regions, with actin C258 exhibiting the most negative docking score among the examined sites (−3.3 kcal/mol)."
- **Evidence pointer** Section 2.15; Section 3.6; Table 3; Figure 5
- **Concern** The selection of only 12 of 57 identified cysteine sites for docking is not justified. The docking scores range from −1.8 to −3.3 kcal/mol, which are weak and generally considered non-specific. The claim that these scores "support spatial feasibility" is not quantitatively substantiated. No comparison with negative controls (e.g., docking MDA to random protein surfaces or unrelated proteins) is provided. The crystal structures used are not specified by PDB ID, and the "predicted active or oxidation-related binding regions" are not defined.
- **Why it matters** The docking results are presented as a key piece of evidence supporting the mechanism. Weak, non-validated docking with arbitrary site selection does not meaningfully support the conclusion that MDA specifically associates with these cysteine regions.
- **Resolution test** Justify the selection of 12 sites, provide PDB IDs and define binding regions, include negative controls, and discuss whether scores in this range are meaningful for a small molecule like MDA.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Redox proteomics methodology
- **Claim pointer** "Redox proteomics identified 581 differential cysteine redox sites, including 343 increased and 238 decreased sites."
- **Evidence pointer** Section 2.14; Section 3.5; Table 2; Table S1
- **Concern** The redox proteomics workflow is described but lacks critical validation details. The authors state that reduced thiols were blocked with NEM and oxidized thiols were labeled after TCEP reduction, but no information is provided on labeling efficiency, completeness of NEM blocking, false discovery rate for site identification, or how quantification was normalized across samples. The interpretation that decreased site intensity reflects "less reducible oxidation states" is speculative without additional validation.
- **Why it matters** The proteomics data are central to the mechanistic claims. Without demonstrated reliability of the redox proteomics workflow, the identification of 57 sites as "MDA-responsive" is not fully trustworthy.
- **Resolution test** Provide validation data for the redox proteomics workflow, including labeling efficiency, FDR, normalization strategy, and ideally orthogonal validation of selected sites (e.g., by targeted mass spectrometry or biochemical assays).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis and data presentation
- **Claim pointer** Multiple claims of significant differences (e.g., "p < 0.05" for WHC, water distribution, structural parameters)
- **Evidence pointer** Sections 3.1-3.3; Figures 1-3
- **Concern** The statistical methods are described only as "one-way ANOVA followed by Tukey's HSD" (Section 2.16), but the number of independent replicates for each assay is not stated. The figures are described in text but not visible in the provided material, so the variance structure and effect sizes cannot be assessed. For the proteomics data, the statistical threshold (fold change ≥2, p < 0.05) is stated, but multiple testing correction is not mentioned.
- **Why it matters** Without clarity on replicates and appropriate multiple testing correction, the reliability of the reported significant differences cannot be evaluated.
- **Resolution test** State the number of replicates for each assay, show variance in figures, and describe multiple testing correction for proteomics data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and physiological relevance
- **Claim pointer** The study claims relevance to "postmortem beef" and "fresh meat" WHC, and the discussion extends to practical interventions.
- **Evidence pointer** Introduction; Discussion
- **Concern** The study uses an isolated myofibrillar protein model with purified MDA at concentrations up to 10 mM. The relevance of these concentrations to actual postmortem meat conditions is not established. MDA concentrations in postmortem muscle are typically much lower (micromolar range). The authors acknowledge the need for whole-meat validation but do not address whether the concentrations used are physiologically relevant.
- **Why it matters** If the MDA concentrations used are not representative of real postmortem conditions, the practical implications and mechanistic conclusions may not translate to actual meat systems.
- **Resolution test** Provide context on MDA concentrations found in postmortem muscle and justify the concentration range used, or temper claims of practical relevance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The extraction method for myofibrillar proteins is referenced to Li et al. and Liu et al. but the key parameters (buffer composition, pH, centrifugation conditions) are not fully described in the text.
- **Required correction** Provide the full extraction protocol or include it as supplementary material.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 3.1
- **Evidence pointer** Figure 1
- **Issue** The text reports moisture content decreased from 82.15% to 75.12%, but the units and measurement method (e.g., oven drying, Karl Fischer) are not specified in the methods.
- **Required correction** Specify the moisture determination method and units clearly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.2
- **Evidence pointer** Figure 2d
- **Issue** The increase in tryptophan fluorescence intensity without a shift in emission maximum is interpreted as "tertiary-structure rearrangement," but increased fluorescence could also result from increased quantum yield due to quenching of nearby residues or other local effects.
- **Required correction** Acknowledge alternative interpretations or provide additional evidence (e.g., ANS binding, circular dichroism) to support the tertiary structure claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.15
- **Evidence pointer** Section 2.15
- **Issue** The PDB IDs for the protein structures used in docking are not provided, and the "predicted active or oxidation-related binding regions" are not defined.
- **Required correction** List PDB IDs and describe how binding regions were predicted.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 3.5
- **Evidence pointer** Table 2
- **Issue** The text states 57 sites correspond to 34 UniProt entries, but the relationship between sites and entries is not clearly explained. Some proteins have multiple sites; the functional significance of multiple sites in one protein is not discussed.
- **Required correction** Clarify the site-to-protein mapping and discuss whether multiple sites in a single protein have additive or distinct effects.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 4
- **Evidence pointer** Discussion, first paragraph
- **Issue** The phrase "self-amplifying lipid-haem-protein oxidation network" is evocative but not clearly defined or supported by data in this study.
- **Required correction** Either define this concept with appropriate references or remove it to maintain a more measured tone.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Practical implications
- **Affected element** Section 4
- **Evidence pointer** Discussion, final paragraph
- **Issue** The practical recommendations (e.g., "limiting MDA formation," "carbonyl-scavenging compounds") are speculative and not tested in this study.
- **Required correction** Clearly distinguish between findings and speculative recommendations, or cite supporting studies for the proposed interventions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.14
- **Evidence pointer** Section 2.14.3
- **Issue** The mass spectrometry parameters (e.g., instrument model, resolution, collision energy details) are not fully specified, limiting reproducibility.
- **Required correction** Provide complete MS parameters or reference a published protocol.

## Risk / unsupported claims
- The claim of a "mechanism" for MDA-induced WHC deterioration is not supported by causal evidence; the study is correlative.
- The molecular docking results are presented as supportive but use weak scores and lack negative controls and justification for site selection.
- The physiological relevance of the MDA concentrations used (up to 10 mM) to actual postmortem meat conditions is not established.
- The interpretation of decreased cysteine site intensity as "less reducible oxidation states" is speculative without additional validation.
- The claim that "cysteine redox remodeling was associated with structural reorganization" is supported only by correlation, not by direct manipulation.
- The practical recommendations in the discussion are not tested in this study and should be framed as speculative.
- The statement that "MDA can be stabilized near myosin residues through hydrogen-bonding and hydrophobic interactions before subsequent oxidative or covalent modification" is based on weak docking scores and requires more robust evidence.
- The claim that "the combined increase in disulfide-associated interactions and MDA-sensitive amino acid modification favors conformational rearrangement and cross-linking" is inferred from indirect measurements and requires direct evidence of cross-link formation.

## Assessment against Nature-style criteria
- **Originality** Moderate. The application of redox proteomics to identify specific cysteine sites in myofibrillar proteins in the context of MDA-induced WHC loss is a novel contribution. However, the general concept that lipid oxidation products modify proteins and affect functionality is well established.
- **Scientific importance** Moderate. The study addresses a practical problem in meat science with potential economic implications. The identification of specific cysteine sites could inform targeted interventions. However, the importance is limited by the correlative nature of the findings and the lack of validation in whole-meat systems.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to meat scientists and food protein chemists. The methods are standard in these fields, and the findings are unlikely to attract readers from outside food science or protein chemistry.
- **Technical soundness** The individual techniques are generally sound, but the integration of results into a mechanistic narrative exceeds what the data can support. The redox proteomics workflow lacks validation details, and the docking is not rigorously controlled. The statistical reporting is incomplete.
- **Readability for nonspecialists** The manuscript is clearly written and logically organized. The abstract and introduction are accessible. However, the discussion is dense and assumes familiarity with protein oxidation chemistry and meat science terminology. The figures are described but not visible in the provided material, so their clarity cannot be assessed.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a correlative study with an overclaimed mechanistic narrative. The central claims of causality are not supported by the experimental design. The molecular docking evidence is weak and not rigorously validated. The redox proteomics methodology requires additional validation details. The study has merit as a descriptive account of MDA-induced changes in myofibrillar proteins, but the mechanistic conclusions and the title need to be substantially tempered. Major revisions addressing the causal inference concern, docking validation, and statistical reporting would be required before the manuscript could be considered for publication.