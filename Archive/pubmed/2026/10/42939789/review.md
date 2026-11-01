## Review setup
- **Input scope** Full manuscript text provided (Abstract through Conclusions, including Tables 1–3 and Figures 1–5 as cited in text)
- **Assessment boundary** Evaluation of the manuscript as a review article, based solely on the supplied text. No independent verification of cited primary literature, no access to figure panels, table contents, or supplementary materials.
- **Shared manuscript claim summary** Cid1 from *S. pombe* is a well-characterized poly(U) polymerase whose UTP selectivity, RNA 3′-end positioning, and catalytic cycling are governed by coordinated interactions among the CAT domain, CD domain, nucleotide-recognition motif, interdomain hinges, and β-trapdoor; engineering of these elements has broadened substrate scope and enabled applications in RNA tailing, sequencing, labelling, functional RNA engineering, and controlled RNA/XNA synthesis.
- **Visible evidence base** Narrative synthesis of cited primary structural (PDB 4EP7, 4FH5, 4E80, 4NKU), biochemical, mutagenesis, and engineering studies; Tables 1–3 referenced; Figures 1–5 referenced but not inspectable.
- **Missing materials affecting confidence** Figure panels (1–5), full Table 1–3 contents, supplementary materials, reference list with full bibliographic details, and any included meta-analysis or systematic search methodology.

## Reviewer
- **Overall assessment** This is a broad and generally well-organized review that covers the structural biology, catalytic mechanism, substrate tolerance, protein engineering, and biotechnological applications of Cid1. The manuscript is strongest in its mechanistic sections, where it carefully distinguishes supported models from proposed ones and explicitly flags unresolved questions (e.g., the second Mg²⁺ in 4EP7, the indirect role of R139, the distributive versus processive debate). However, the review is largely descriptive and does not critically evaluate the primary literature, reconcile conflicting reports, or provide a systematic framework for assessing the maturity of the claimed applications. Several claims about engineering outcomes and application readiness are asserted without sufficient quantitative support or explicit acknowledgment of the limited evidence base. The manuscript would benefit from a more analytical stance, clearer separation of established versus speculative content, and explicit statements of the criteria used to select and weight the cited studies.
- **Who would be interested in the results, and why** Researchers in RNA biology, enzymology, and RNA therapeutics; protein engineers interested in template-independent polymerases; biotechnologists developing enzymatic RNA synthesis platforms; and structural biologists studying nucleotidyltransferase mechanisms. The review is also relevant to those comparing Cid1 with TdT and other TENT-family enzymes for synthetic biology applications.
- **Major strengths** The manuscript provides a comprehensive and current overview of Cid1 biology, structure, and engineering. It correctly emphasizes that UTP selectivity is not determined by a single residue but emerges from a distributed network involving the NRM, hinges, and β-trapdoor. The mechanistic sections are nuanced, distinguishing structural observations from functional inferences and explicitly noting when a model remains proposed rather than established. The inclusion of engineering studies (PUPdel, PUPdel2, H336R variants) and application examples (nanopore sequencing, sgRNA-Click, controlled RNA synthesis) is valuable. The writing is generally clear and accessible to a nonspecialist audience.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Critical synthesis and evidence weighting
- **Claim pointer** The review asserts that engineered Cid1 variants have enabled "improved activity, altered substrate specificity, and potential applications in enzymatic RNA synthesis" and that PUPdel2 exhibits "improved recombinant expression, increased thermostability, and enhanced catalytic efficiency toward selected modified nucleotides."
- **Evidence pointer** Sections 3.2, 3.5, 4.4; Table 3; location not provided for quantitative comparisons
- **Concern** The manuscript reports engineering outcomes largely as qualitative statements without providing the underlying quantitative metrics (e.g., fold improvements, error rates, yields, statistical confidence) or the assay conditions under which they were obtained. For PUPdel2, the text states that "the contributions of individual substitutions and their interactions to the observed gains in expression, thermal stability, and catalytic activity have not been systematically resolved," yet the review still presents these gains as established. This creates an impression of maturity that the cited evidence may not support.
- **Why it matters** Readers may overestimate the robustness of the engineering claims and the readiness of Cid1-based platforms for practical use. A review should clearly distinguish between demonstrated improvements and preliminary observations.
- **Resolution test** Provide a summary table or structured comparison of reported variants with quantitative metrics (activity, thermostability, substrate scope, cycle number, yield) and explicitly state which metrics are derived from single studies versus replicated or independently validated results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Application readiness and translational claims
- **Claim pointer** The review states that Cid1-based controlled RNA synthesis "represents the most advanced, but still proof-of-concept, application" and that the platform achieved "ten full liquid-phase synthesis cycles" with "approximately 95% average coupling efficiency," while also noting that "no more than 50 pmol of a fully modified N + 10 product was recovered from a 200 nmol starting reaction."
- **Evidence pointer** Section 4.4; Figure 5D; location not provided for raw data
- **Concern** The manuscript does not adequately contextualize the gap between the reported coupling efficiency and the overall yield, nor does it compare Cid1-based synthesis with established phosphoramidite or in vitro transcription methods in quantitative terms. The statement that Cid1-based synthesis "cannot yet replace phosphoramidite chemistry or in vitro transcription" is appropriately cautious, but the preceding description of ten cycles and 95% efficiency may lead readers to underestimate the cumulative yield problem.
- **Why it matters** Application-focused readers need a clear, quantitative assessment of where Cid1-based synthesis currently stands relative to competing technologies.
- **Resolution test** Include a quantitative comparison of Cid1-based synthesis with phosphoramidite and IVT in terms of yield, length, modification compatibility, and cost, with explicit acknowledgment of the data limitations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic model reconciliation
- **Claim pointer** The review presents two catalytic cycle models (Muñoz-Tello et al. and Yates et al.) and states that "these models differ in their interpretation of RNA movement and conformational transitions" but "collectively describe a common mechanism."
- **Evidence pointer** Section 3.6; Figure 4A, 4B
- **Concern** The manuscript does not critically evaluate the evidence supporting each model or explain how the distributive behavior reported by Yates et al. is reconciled with the iterative translocation proposed by Muñoz-Tello et al. The statement that iterative translocation "may occur under specific structural conditions but does not represent the only catalytic outcome" is vague and does not resolve the mechanistic disagreement.
- **Why it matters** A review should help readers understand which aspects of the catalytic cycle are well established and which remain contested, rather than presenting multiple models side by side without adjudication.
- **Resolution test** Provide a structured comparison of the two models, including the specific structural and biochemical evidence supporting each, the points of conflict, and the experiments that could distinguish between them.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Substrate specificity data consistency
- **Claim pointer** The review states that "GaMD/MM-PBSA simulations further supported this preference, predicting Cid1 binding affinity in the order UTP > ATP > CTP > GTP," while also noting that "this ranking differs somewhat from the biochemical results, which showed weak GTP incorporation but no detectable CTP incorporation under their assay conditions."
- **Evidence pointer** Section 2.3; Table 2; location not provided for simulation parameters
- **Concern** The manuscript acknowledges the discrepancy but does not explore its implications. If computational predictions and biochemical assays disagree on the relative ranking of CTP and GTP, this raises questions about the reliability of the computational model or the assay conditions. The review does not state which evidence should be weighted more heavily or why.
- **Why it matters** Readers may be confused about the true substrate preference hierarchy and the predictive value of the computational approach.
- **Resolution test** Discuss the possible sources of the discrepancy (e.g., force field limitations, assay sensitivity, metal-ion conditions) and provide a clear statement of which ranking is best supported by direct experimental evidence.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scope and completeness of literature coverage
- **Claim pointer** The review states that "the most recent review dedicated to Cid1 was published in 2008" and that "subsequent advances in structural studies, protein engineering, and biotechnological applications have generated significant new insights that warrant an updated review article."
- **Evidence pointer** Section 1; location not provided for search strategy
- **Concern** The manuscript does not describe the methodology used to identify and select the cited literature. It is unclear whether the review is comprehensive, whether a systematic search was performed, and how studies were prioritized. Several key claims rely on a limited number of primary studies (e.g., references 65, 66, 9, 61, 62, 63), and the review does not indicate whether conflicting or negative results exist in the broader literature.
- **Why it matters** Without a transparent search strategy, readers cannot assess the completeness or potential bias of the review.
- **Resolution test** Provide a brief description of the literature search strategy, inclusion criteria, and any limitations on coverage.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Use of "poly(U) polymerase," "terminal uridylyltransferase," and "TUTase"
- **Evidence pointer** Sections 1, 2.2, 2.3
- **Issue** The manuscript uses these terms interchangeably in some places while also noting that they are "primarily functional designations rather than mutually exclusive phylogenetic classifications." This could confuse nonspecialist readers.
- **Required correction** Define the terms explicitly at first use and use them consistently thereafter, or provide a brief glossary.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure and table referencing
- **Affected element** Figures 1–5 and Tables 1–3
- **Evidence pointer** Throughout the manuscript
- **Issue** The text frequently refers to figures and tables for details (e.g., "more details can refer to Table 3"), but the figure panels and table contents are not available for inspection in the supplied material. It is therefore impossible to verify whether the visual elements support the claims made in the text.
- **Required correction** Ensure that all key quantitative and structural claims are stated in the text and not solely dependent on figure or table content.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of engineering nomenclature
- **Affected element** Residue numbering in PUPdel and PUPdel2
- **Evidence pointer** Sections 3.1, 3.3, 3.5
- **Issue** The manuscript explains that PUPdel numbering differs from full-length Cid1 by 12 positions, but the repeated conversions (e.g., C63I → C75I, D97P → D109P) are cumbersome and could lead to errors. The relationship between PUPdel2 substitutions and full-length numbering is also not consistently provided.
- **Required correction** Provide a single conversion table or use full-length numbering consistently throughout, with a note on the original nomenclature.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Overstatement of application potential
- **Affected element** Statements about therapeutic relevance
- **Evidence pointer** Sections 4.3, 4.4
- **Issue** The manuscript states that the Cid1-based synthesis platform produced "natural and therapeutically relevant modified RNA sequences" and that terminal 2′-O-methyluridine modification "produced at least a threefold increase in protein expression in the tested cellular system." These claims are not accompanied by sufficient context (e.g., which sequences, which cell types, whether the effect was replicated).
- **Required correction** Qualify these statements with explicit reference to the specific study conditions and avoid implying general therapeutic utility without further validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference formatting and completeness
- **Affected element** Citations
- **Evidence pointer** Throughout the manuscript
- **Issue** The reference list is not provided in the supplied material, and some citations appear as large blocks (e.g., [3,6,7,58,59]) without indication of which reference supports which specific claim. This makes it difficult to trace evidence.
- **Required correction** Ensure that each specific claim is supported by a clearly identified reference, and avoid grouping references when they support different points.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**
  - **Originality** The review does not present new primary data but provides a timely synthesis of a topic last reviewed in 2008. The originality lies in its integration of recent structural, engineering, and application advances. However, the lack of critical analysis and quantitative synthesis limits its added value beyond a descriptive summary.
  - **Scientific importance** Cid1 is a well-established model for template-independent RNA uridylation, and the review covers a broad range of relevant topics. The importance is moderate to high for specialists in RNA enzymology and RNA biotechnology, but the review does not break new conceptual ground.
  - **Interdisciplinary readership** The manuscript is accessible to nonspecialists in its early sections but becomes increasingly technical. The application sections are of potential interest to biotechnologists and RNA therapeutics researchers. Greater effort to contextualize mechanistic details for a broader audience would improve reach.
  - **Technical soundness** The mechanistic sections are generally careful and well referenced. However, the engineering and application sections lack quantitative rigor and critical evaluation of the cited evidence. The absence of a described search strategy and the reliance on a limited number of primary studies for key claims weaken the technical foundation.
  - **Readability for nonspecialists** The writing is clear and well structured. Technical terms are generally explained. However, the density of residue-level detail and the lack of a summary figure or table that integrates structural and functional information may overwhelm nonspecialist readers.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript provides a useful and timely overview of Cid1 biology and engineering, but it requires a more critical and quantitative synthesis of the engineering and application literature, explicit reconciliation of conflicting mechanistic models, and a transparent description of the literature search strategy before it can be considered a definitive review.

## Risk / unsupported claims
- The claim that PUPdel2 exhibits "improved recombinant expression, increased thermostability, and enhanced catalytic efficiency" is presented without quantitative metrics or independent validation.
- The claim that Cid1-based synthesis achieved "approximately 95% average coupling efficiency" is not contextualized with respect to cumulative yield, error rates, or comparison with established methods.
- The claim that terminal 2′-O-methyluridine modification "produced at least a threefold increase in protein expression" is not accompanied by sufficient experimental detail (cell type, mRNA construct, replication).
- The claim that the poly(I)-tailing approach has "not yet been incorporated into a publicly available commercial nanopore-sequencing kit" is a statement about commercial status that may change and is not supported by a cited source in the supplied text.
- The statement that "the most recent review dedicated to Cid1 was published in 2008" is not supported by a systematic search or citation of the search methodology.
- The assertion that Cid1 is "the principal poly(A)-tail uridyltransferase that contributes to mRNA decay directionality in *S. pombe*" is based on cited studies but the review does not discuss potential conflicting evidence or the limitations of the transcriptome-wide analyses.