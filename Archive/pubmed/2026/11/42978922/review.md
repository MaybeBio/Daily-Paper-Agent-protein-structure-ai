## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, methodological rigor, literature coverage, and framing of the AI-BMP4 intersection
- **Shared manuscript claim summary** The manuscript presents a narrative review of AI-driven advances in BMP4 research across drug discovery, structural modeling, and clinical translation, arguing that AI tools have accelerated progress but that significant gaps remain, particularly in BMP4-specific applications
- **Visible evidence base** Full text including abstract, introduction, methods, results sections, discussion, and references cited in text
- **Missing materials affecting confidence** Figures and tables referenced but not provided; reference list not fully visible; no supplementary materials

## Reviewer
- **Overall assessment** This review addresses a timely and potentially valuable intersection between BMP4 biology and artificial intelligence. The authors have organized a substantial body of literature into three coherent domains and provide a useful categorical framework (BMP4-specific, BMP pathway-targeted, transferable AI methods) that helps readers distinguish established results from speculative applications. However, the manuscript has several significant weaknesses. The literature search methodology is described as "systematic" but lacks the transparency and reproducibility expected of such claims. The review is heavily reliant on a small number of primary studies, several of which are described in considerable detail while others are mentioned only in passing. The critical distinction between AI-based and classical computational methods is handled inconsistently, and the authors sometimes overstate the role of AI in studies that primarily used traditional docking or regression approaches. The clinical translation section is largely speculative, with few concrete examples of AI-driven clinical impact. The manuscript would benefit from a more rigorous and balanced treatment of the evidence, clearer criteria for study inclusion, and a more critical assessment of the limitations of AI methods in this domain.

- **Who would be interested in the results, and why** Researchers working on BMP signaling, particularly those interested in therapeutic targeting of the BMP pathway, would find the consolidated summary of computational approaches useful. Computational biologists and AI practitioners seeking application domains in rare diseases or oncology may be interested in the identified gaps and opportunities. Clinicians involved in pancreatic, gastric, or glioblastoma research might find the prognostic biomarker sections relevant. However, the audience is likely to be relatively specialized, and the review does not currently make a compelling case for broader interdisciplinary readership.

- **Major strengths** The categorical framework distinguishing BMP4-specific, pathway-targeted, and transferable methods is a useful organizational principle. The authors are appropriately cautious in several places, explicitly noting when methods have not yet been applied to BMP4. The inclusion of negative results and failed trials (e.g., fidrisertib Phase II) adds balance. The section on limitations of AI structural prediction is honest and technically accurate. The future directions section identifies concrete, actionable research priorities.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The manuscript claims to be "a narrative review with systematic search elements" and describes a search strategy across five databases with specific Boolean queries and inclusion/exclusion criteria
- **Evidence pointer** Methods section, "Literature search strategy"
- **Concern** The search methodology is described in insufficient detail to be reproducible or verifiable. The authors state that "titles and abstracts were screened independently by two reviewers" and that "full texts were then assessed against the following criteria," but they do not report the number of records identified, screened, excluded, or included at each stage. No PRISMA-style flow diagram is provided, and the authors explicitly state the review is "not reported according to PRISMA guidelines." The Boolean queries are described as "representative" but the full search strings are not provided. The date range (2020-2026) is unusual given the manuscript appears to be submitted in 2026, and the authors do not clarify whether the search was completed before submission. The inclusion criteria are broad and subjective, and the authors do not specify how many studies fell into each of the three categories (A, B, C).
- **Why it matters** A review that claims systematic elements must provide sufficient methodological transparency for readers to assess the completeness and reproducibility of the literature search. Without this information, the review's coverage cannot be distinguished from a selective or biased sample of the literature. The lack of reporting standards undermines confidence in the conclusions drawn from the surveyed literature.
- **Resolution test** The authors should provide a detailed search strategy including full Boolean queries for each database, the number of records retrieved at each stage, the number of studies included and excluded with reasons, and a flow diagram. Alternatively, they should revise the manuscript to clearly state that this is a narrative review without systematic elements and remove claims of systematic searching.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript states that "AlphaFold3 and related tools have generated high-confidence predicted models of BMP4-receptor complex architecture, aspects of which were previously intractable to experimental structure determination"
- **Evidence pointer** Results section, "Protein structure prediction and computational modeling of BMP4"
- **Concern** The claim that AlphaFold3 has generated "high-confidence predicted models of BMP4-receptor complex architecture" is not supported by any specific citation or experimental validation in the text. The authors reference a 2025 study on BMP4 prodomain phosphorylation (Kim et al., 2025) but do not provide details of the predicted models, their confidence scores, or any comparison with experimental structures. The broader claim that these predictions address aspects "previously intractable to experimental structure determination" is speculative and not substantiated. The authors themselves later acknowledge that "these predictions remain to be fully validated experimentally," which partially mitigates the concern, but the initial framing overstates the current evidence base.
- **Why it matters** The central premise of the structural modeling section is that AI has made significant contributions to understanding BMP4-receptor interactions. If the key evidence for this claim is a single unpublished or very recent study with limited validation, the claim is not yet established. Readers may be misled into believing that AI-derived structures have been experimentally confirmed when they have not.
- **Resolution test** The authors should either provide specific examples with confidence metrics and any available experimental validation, or temper the claim to accurately reflect the current status of AI predictions for BMP4-receptor complexes. If the Kim et al. study is the primary evidence, its methods and findings should be described in sufficient detail for readers to assess the strength of the evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scope and framing
- **Claim pointer** The manuscript claims to provide "a comprehensive review of AI-driven advances in drug discovery, structural modeling, and clinical translation" for BMP4
- **Evidence pointer** Title, Abstract, and throughout
- **Concern** The review's scope is broader than its actual content. The drug discovery section is dominated by a single study (Tyagi et al., 2023) that the authors themselves acknowledge used "classical computational-chemistry methods" rather than AI. The BMP4-specific AI literature is extremely thin, and the authors compensate by discussing transferable methods developed on other targets at length. While this is transparently labeled, it means the review is more about potential applications than actual advances. The clinical translation section similarly relies on retrospective analyses and speculative extensions rather than established clinical applications. The title promises a "comprehensive review" but the content is more accurately described as a perspective on opportunities and gaps.
- **Why it matters** The framing may mislead readers about the maturity of the field. A reader seeking established AI-driven advances in BMP4 research would find very few concrete examples. The review's value lies in identifying gaps and opportunities, which is a legitimate contribution, but the framing should accurately reflect this.
- **Resolution test** The authors should either revise the title and framing to reflect the review's actual scope (e.g., "opportunities and challenges at the intersection of BMP4 biology and artificial intelligence") or substantially expand the coverage of actual AI applications to BMP4, if such literature exists.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Critical analysis
- **Claim pointer** The manuscript presents the Pareto optimization study (Shaikh et al., 2024) as evidence that "the BMP pathway cannot simultaneously optimize response speed, noise filtering, and input sensitivity" and that this "elegantly explains" system-level behaviors
- **Evidence pointer** Results section, "Systems-level modeling of BMP signaling dynamics"
- **Concern** The authors present this study as a key finding without critical evaluation. The Pareto front result is model-dependent and may not generalize across cell types or experimental conditions. The authors do not discuss potential limitations of the model, alternative interpretations, or conflicting evidence. The claim that this "elegantly explains" diverse system-level behaviors is an overstatement; the study provides a computational hypothesis, not a demonstrated mechanism.
- **Why it matters** A review should provide critical assessment of the studies it cites, not merely summarize their conclusions. The uncritical acceptance of model-based findings as explanatory may mislead readers about the strength of the evidence.
- **Resolution test** The authors should add a critical discussion of the limitations of the Pareto optimization approach, including model assumptions, parameter sensitivity, and the need for experimental validation. They should also temper the language from "elegantly explains" to something like "proposes a potential explanation that requires experimental testing."

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Clinical translation
- **Claim pointer** The manuscript states that "high BMP4 expression independently predicts poor overall survival, disease-free survival, and progression-free survival" in pancreatic adenocarcinoma, citing Wang et al. (2025)
- **Evidence pointer** Results section, "Pancreatic adenocarcinoma: BMP4 as a prognostic biomarker"
- **Concern** The clinical claims are based on retrospective analyses without external validation. The authors acknowledge this ("pending prospective validation") but the framing in the main text is more definitive than the evidence warrants. The nomogram C-index values (0.738 and 0.724) are modest and may not represent clinically meaningful improvement over existing prognostic tools. The authors do not discuss potential confounding factors, such as treatment heterogeneity or stage distribution, that could affect the observed associations.
- **Why it matters** Prognostic biomarker claims have direct clinical implications. Overstating the evidence for BMP4 as a prognostic marker could lead to premature clinical adoption or misdirected research efforts. The review should clearly distinguish between hypothesis-generating retrospective findings and validated clinical tools.
- **Resolution test** The authors should add a more prominent caveat about the retrospective nature of the evidence, discuss the limitations of the nomogram approach, and explicitly state that BMP4 is not yet ready for clinical use as a prognostic biomarker.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "Results" section
- **Issue** The abstract states "We find that AI has accelerated BMP4-related research along multiple axes, though with important caveats" but does not specify what those caveats are. The abstract would benefit from a brief enumeration of the most significant caveats to give readers an accurate preview of the review's conclusions.
- **Required correction** Add one or two sentences in the abstract summarizing the key caveats, such as the scarcity of BMP4-specific AI applications and the lack of experimental validation for AI predictions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The terms "AI" and "machine learning" are used interchangeably in several places, which can be confusing. For example, classical computational methods such as molecular docking are sometimes described in the context of AI without clear distinction. The authors should consistently distinguish between AI/ML methods and classical computational approaches.
- **Required correction** Define the scope of "AI" and "machine learning" early in the manuscript and use these terms consistently throughout. When describing studies that use classical methods, explicitly note that they are not AI-based.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of limitations
- **Evidence pointer** Results section, "Limitations and validation status of AI-based structure prediction for BMP4"
- **Issue** The limitations section focuses on structural prediction but does not address limitations of AI methods in drug discovery or clinical applications. For example, the authors do not discuss the risk of overfitting in small-sample machine learning, the generalizability of transferable methods, or the reproducibility challenges in AI-driven drug discovery.
- **Required correction** Add a paragraph discussing limitations of AI methods across all three domains, not just structural prediction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Citation of preprints
- **Evidence pointer** Methods section and throughout
- **Issue** The authors state that "bioRxiv and arXiv preprints were included where relevant and are explicitly labeled as non-peer-reviewed at first citation." However, it is not clear from the text which citations are preprints, as the labeling is not consistently applied in the visible text.
- **Required correction** Ensure that all preprint citations are clearly marked as such at the point of citation, not just in the methods section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-4
- **Evidence pointer** Referenced in text but not provided
- **Issue** The figures are referenced extensively but were not available for review. The authors should ensure that all figures are of high quality, clearly labeled, and directly support the claims made in the text. In particular, Figure 1 is described as a "Global Framework of AI-Driven BMP4 Research" and should provide a clear visual summary of the review's organizational structure.
- **Required correction** Ensure all figures are provided in the final submission and that they are self-explanatory to readers without specialized knowledge of either BMP4 biology or AI methods.

- **Technical failings that need to be addressed before the case is established** The search methodology must be reported in sufficient detail to be reproducible, or the claims of systematic searching must be removed. The evidence for AI-driven advances in BMP4-specific applications is thin and must be accurately framed as preliminary or prospective. The clinical claims require more prominent caveats about their retrospective and unvalidated nature.

- **Assessment against Nature-style criteria** 
  - **Originality**: The review addresses a genuinely novel intersection, but the originality is limited by the scarcity of actual AI-BMP4 applications to review. The categorical framework is a useful contribution, but the review is more a roadmap than a synthesis of established work.
  - **Scientific importance**: The topic is important, given the clinical significance of BMP4 in cancer, fibrosis, and FOP. However, the review does not currently make a compelling case that AI has already made substantial contributions to BMP4 research, which limits its immediate scientific impact.
  - **Interdisciplinary readership**: The review has the potential to appeal to both BMP4 biologists and AI researchers, but the current framing may not fully engage either audience. BMP4 biologists may find the AI sections too technical, while AI researchers may find the BMP4 biology oversimplified.
  - **Technical soundness**: The technical descriptions of AI methods are generally accurate, but the review lacks critical evaluation of the cited studies. The limitations of AI methods are acknowledged but not systematically analyzed.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible, with helpful definitions of key terms. However, some sections assume familiarity with both BMP4 biology and AI methods, which may limit accessibility for readers from one domain but not the other.

- **Recommendation posture** Supportive if technical concerns are resolved. The review addresses a timely and important topic, and the categorical framework is a useful contribution. However, the methodological transparency issues and the overstatement of the evidence base must be addressed before the review can be considered reliable. The authors should either substantially strengthen the evidence for AI-driven advances in BMP4 research or reframe the review as a perspective on opportunities and gaps rather than a comprehensive review of established advances.

## Risk / unsupported claims
- The claim that "AlphaFold3 and related tools have generated high-confidence predicted models of BMP4-receptor complex architecture" is not supported by specific evidence in the text.
- The claim that the Pareto optimization study "elegantly explains" system-level BMP signaling behaviors overstates the explanatory power of a computational model.
- The clinical claims regarding BMP4 as a prognostic biomarker in pancreatic, gastric, and glioblastoma cancers are based on retrospective analyses without external validation and are presented with insufficient caveats.
- The statement that "no published study has applied RFdiffusion or ProteinMPNN to engineer BMP4-based therapeutics" is presented as a definitive negative claim, which is difficult to verify and may be challenged by future or unpublished work.
- The claim that the review is "comprehensive" is not supported by the reported search methodology, which lacks transparency and reproducibility.