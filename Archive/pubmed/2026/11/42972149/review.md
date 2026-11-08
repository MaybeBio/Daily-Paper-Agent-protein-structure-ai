## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, technical accuracy, completeness of coverage, and clarity of the presented review
- **Shared manuscript claim summary** The manuscript argues that AlphaFold (AF), particularly AlphaFold3 (AF3), expands the scope of natural product (NP) research beyond traditional small-molecule targets by enabling structure prediction of macromolecular NPs, co-folding-based virtual screening, and modeling of molecular glue (MG)-mediated ternary complexes.
- **Visible evidence base** Full text including introduction, methods/technical descriptions, case studies, tables (Tables 1–3), figures (Figs. 1–7), and references cited within the text
- **Missing materials affecting confidence** Graphical abstract image not accessible; figure images not viewable; reference list not fully provided; no supplementary information or data availability statement

## Reviewer
- **Overall assessment** This review provides a timely and well-structured overview of AlphaFold applications in natural product research, covering technical evolution, structural prediction of canonical targets, hit-to-lead discovery, macromolecular NP interactions, and molecular glue strategies. The manuscript is generally well-written and logically organized. However, several technical inaccuracies, overstatements, and gaps in critical evaluation weaken the overall impact. The review would benefit from a more balanced discussion of AF limitations, clearer differentiation between established results and speculative potential, and correction of specific factual errors.
- **Who would be interested in the results, and why** Researchers in natural product chemistry, computational drug discovery, structural biology, and AI-driven pharmaceutical sciences would find this review valuable. It provides a consolidated resource for understanding how AF-based methods can be applied to NP target identification, virtual screening, and peptide/protein NP characterization. The molecular glue section may interest medicinal chemists exploring PPI modulation.
- **Major strengths** The manuscript offers a comprehensive and current overview of AF series evolution with clear comparative tables. The inclusion of co-folding strategies and molecular glue applications represents a forward-looking perspective. The case studies, particularly the HDAC11 example and COValid benchmark, provide concrete illustrations of AF utility. The discussion of limitations and emerging tools like IsoDDE adds practical value.
- **Major Concerns** Several technical claims require verification or qualification. The performance metrics cited for AF3 on COValid and DEKOIS2.0 need contextualization against baseline methods. The manuscript overstates AF3's generalizability to MG-mediated ternary complexes without acknowledging training data limitations. The distinction between AF2/AFM and AF3 capabilities is sometimes blurred. The review lacks critical comparison with non-AF docking methods in specific NP application contexts. The IsoDDE section relies on a single source and may be premature for inclusion as established science.
- **Minor Comments** Several statements could be clarified or supported with additional context. The manuscript would benefit from a dedicated section on validation strategies for AF-predicted structures in NP contexts. The figures are referenced but not described in sufficient detail for readers without access. The conclusion is somewhat repetitive of earlier sections.
- **Technical failings that need to be addressed before the case is established** R1-M1 (AF3 performance overstatement), R1-M2 (MG ternary complex generalizability), R1-M3 (IsoDDE claims)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The review consolidates existing literature but offers limited novel synthesis or critical framework. **Scientific importance**: High. AF applications in NP research are rapidly expanding, and a reliable review serves the community. **Interdisciplinary readership**: Good. The manuscript bridges computational biology, natural product chemistry, and drug discovery. **Technical soundness**: Mixed. Several technical claims require correction or qualification (see Major Concerns). **Readability for nonspecialists**: Adequate. The manuscript explains technical concepts clearly, though some sections assume familiarity with structural biology terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The review addresses a relevant and timely topic with useful organization, but requires corrections to technical claims, more balanced critical evaluation, and clearer separation of established findings from speculative potential.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical accuracy
- **Claim pointer** The manuscript states that AF3 achieved an average adjusted LocAUC of 71.8 ± 5.9% on the COValid benchmark, markedly outperforming DOCK6 (12.1 ± 9.9%), and that AF3-like models achieved mean AUROC of 0.913, mean BEDROC of 0.755, and mean EF0.5% of 22.98 on DEKOIS2.0.
- **Evidence pointer** Section "Hit identification via AlphaFold-based co-folding: a novel structure-guided virtual screening strategy", location not provided
- **Concern** The performance metrics are presented without adequate context. The COValid benchmark is described as the "first dedicated benchmark dataset for covalent protein–ligand screening," which may limit comparability with established methods. The DEKOIS2.0 results are presented as outperforming "traditional docking tools" but the specific comparators and their performance values are not provided. Additionally, the manuscript does not discuss potential biases in benchmark design, the choice of confidence metrics (min-iPAE) versus alternative scoring functions, or the generalizability of these results to diverse NP chemical space. The claim that AF3 "markedly outperforms" DOCK6 requires verification that the comparison is apples-to-apples (same ligand preparation, same target conformations, same evaluation protocol).
- **Why it matters** Performance claims in virtual screening benchmarks directly influence whether readers adopt AF3-based workflows. Overstated or poorly contextualized metrics could mislead researchers in selecting methods for NP screening campaigns. The review's credibility depends on accurate and balanced reporting of comparative performance.
- **Resolution test** Provide the performance values for all comparator methods (DOCK6, Glide, AutoDock Vina, Gnina) on the same benchmarks. Discuss potential sources of bias in benchmark design and whether AF3's advantage persists across diverse NP-like chemical libraries. Clarify whether the reported metrics reflect prospective or retrospective validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Overgeneralization
- **Claim pointer** The manuscript states that AF3 co-folding "predicts ternary complexes directly by integrating the SMILES strings of natural MGs with the amino acid sequences of the protein partners" and that this approach can model "MG-induced ternary complexes with conformational changes and de novo PPI formation."
- **Evidence pointer** Section "AlphaFold-based strategies for characterizing molecular glue-mediated ternary complexes", location not provided
- **Concern** The manuscript overstates AF3's capability for MG-mediated ternary complex prediction. AF3 was trained primarily on static protein structures and co-folding data, not specifically on MG-induced ternary complexes. The claim that AF3 can predict "de novo PPI formation" induced by MGs is speculative and not supported by the cited literature. The manuscript acknowledges that "current models are not specifically trained on MG-mediated ternary complexes" but then presents AF3 co-folding as a viable strategy for this purpose without adequate caveats. The distinction between modeling known ternary complexes (where the MG is present in training data) versus predicting novel MG-induced PPIs (where the interaction is not observed) is not clearly articulated.
- **Why it matters** Molecular glue research is an emerging and technically challenging field. Overstating AF3's predictive power for MG-mediated ternary complexes could lead researchers to rely on inaccurate models, wasting resources and potentially drawing incorrect mechanistic conclusions. The review should clearly delineate what AF3 can and cannot do in this context.
- **Resolution test** Provide explicit caveats about AF3's training data limitations for MG-mediated complexes. Distinguish between cases where AF3 can reliably model known ternary complexes versus predict novel MG-induced PPIs. Cite specific validation studies demonstrating AF3's accuracy on MG-mediated ternary complexes, or state clearly that such validation is lacking.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Source reliability
- **Claim pointer** The manuscript describes IsoDDE, introduced by Isomorphic Labs in February 2026, as achieving "substantially higher success rates than AF3" in antigen–antibody complex modeling and capable of "inferring cryptic binding sites directly from primary amino acid sequences."
- **Evidence pointer** Section "Emerging advances: beyond AlphaFold3", location not provided
- **Concern** The IsoDDE section relies on a single source (reference [156]) and describes a tool introduced only months before the manuscript date. The claims of "substantially higher success rates" and "AlphaFold 4-level" advancement are presented without independent verification or peer-reviewed validation. The description of IsoDDE's capabilities appears promotional rather than critical. Given the rapid pace of AI tool development, such claims require more rigorous scrutiny and should be clearly labeled as preliminary or vendor-reported.
- **Why it matters** Including unverified claims about a proprietary tool undermines the review's objectivity. Readers may mistake vendor-reported performance for independently validated results. The review should either provide independent benchmark data or clearly indicate the preliminary nature of these claims.
- **Resolution test** Provide independent validation data for IsoDDE's performance, or clearly label the section as describing vendor-reported capabilities that have not yet undergone peer review. Consider whether this section is necessary for the review's core message, or whether it could be moved to a "future directions" discussion with appropriate caveats.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Advantages" in Table 2
- **Evidence pointer** Table 2, location not provided
- **Issue** The "Advantages" column for several models uses vague terms such as "strong screening and enrichment capability" (SPOC) and "superior to traditional flexible docking methods" (DiffBindFR) without quantitative context or comparison criteria.
- **Required correction** Provide specific metrics or comparative benchmarks for each claimed advantage, or rephrase to indicate qualitative assessment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Proteinaceous natural products"
- **Evidence pointer** Table 3, location not provided
- **Issue** Table 3 lists seven proteins with pharmacological activities but does not specify which AF version was used for each prediction or the confidence scores of the models. This information is critical for readers to assess the reliability of the structures.
- **Required correction** Add columns for AF version used and confidence metrics (e.g., pLDDT ranges) for each entry.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Advantages", subsection on AF2 virtual screening
- **Evidence pointer** Section "Advantages", location not provided
- **Issue** The statement that AF2 models "rival experimentally determined structures" in virtual screening is based on two specific case studies (TAAR1 and 5-HT2A). This is presented as a general conclusion, but the manuscript does not discuss cases where AF2 models underperformed or the conditions under which AF2 models are likely to be less reliable.
- **Required correction** Add a brief discussion of conditions where AF2 models may be less suitable for virtual screening (e.g., highly flexible proteins, proteins with large conformational changes upon ligand binding).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Conclusion"
- **Evidence pointer** Section "Conclusion", location not provided
- **Issue** The conclusion is largely a summary of the main text without offering a critical perspective on the field's trajectory or identifying key open questions. It reads as repetitive rather than synthetic.
- **Required correction** Add a brief discussion of the most pressing challenges and promising future directions, such as integration with experimental structural biology, handling of post-translational modifications, or application to NP biosynthesis enzymes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Challenges, complementary solutions, and emerging advances"
- **Evidence pointer** Section "Current limitations and complementary solutions", location not provided
- **Issue** The discussion of AF limitations focuses on stereochemical violations and hallucination effects but omits other well-documented limitations, such as difficulty with multi-domain proteins, conformational ensembles, and proteins with large disordered regions that are functionally relevant.
- **Required correction** Expand the limitations section to include these additional challenges and discuss how they specifically impact NP research applications.

## Risk / unsupported claims
- The claim that AF3 "markedly outperforms" DOCK6 on COValid is presented without full comparator data or discussion of benchmark design limitations.
- The assertion that AF3 co-folding can predict "de novo PPI formation" induced by molecular glues is speculative and not supported by direct validation evidence.
- The description of IsoDDE as an "AlphaFold 4-level" advancement with "substantially higher success rates" is based on a single vendor-associated source and lacks independent verification.
- The statement that AF2 models "rival experimentally determined structures" in virtual screening is overgeneralized from two case studies without discussing failure modes.
- The claim that AF "enables structural characterization of diverse NP targets" is presented as a general conclusion, but the manuscript does not systematically evaluate the accuracy of AF predictions across different target classes.
- The publication statistics cited for peptide NP research (3975 papers from 2016–2020 vs. 6271 from 2021–2025) are presented without source or methodology, making them unverifiable.