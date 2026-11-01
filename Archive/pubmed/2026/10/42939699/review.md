## Review setup
- **Input scope** Full manuscript text (abstract, introduction, main sections, conclusions)
- **Assessment boundary** Scientific content, methodological framing, internal consistency, and evidence quality as presented in the supplied text
- **Shared manuscript claim summary** The manuscript argues that AI for therapeutic peptide discovery cannot be reduced to sequence generation; it proposes a two-dimensional Peptide–AI Evidence Grid separating methodological rigor (M0–M3) from translational depth (T0–T3), applies this grid to representative studies, and provides a reporting checklist for peptide-specific AI work
- **Visible evidence base** The manuscript text itself, including descriptions of cited studies, tables referenced (Tables 2–8), and the proposed grid framework
- **Missing materials affecting confidence** Full reference list, actual table contents, figures, supplementary materials, and the complete text of Sections 5–8 (only summaries visible in the provided excerpt)

## Reviewer
- **Overall assessment** This is a thoughtful, well-structured critical review that addresses a genuine gap in the peptide-AI literature: the conflation of computational performance with therapeutic relevance. The central argument, that representation and evaluation are inseparable and that methodological rigor and translational depth must be assessed independently, is sound and timely. The proposed Evidence Grid is a useful conceptual contribution, though its operational value depends on details not fully visible in the supplied text. The manuscript is generally well-written and accessible, though some sections are dense and the treatment of specific studies is necessarily selective. The main weaknesses are the lack of a systematic methodology for study selection, the absence of quantitative synthesis, and the risk that the grid, as presented, may be too coarse to resolve disputes about individual claims.

- **Who would be interested in the results, and why** Researchers developing or applying AI methods to peptide discovery, including computational biologists, medicinal chemists, and peptide engineers. The manuscript would also interest methodologists working on reporting standards for machine learning in biology, and journal editors or reviewers seeking frameworks to evaluate peptide-AI claims. The Evidence Grid and checklist could serve as practical tools for these groups.

- **Major strengths**
  1. The central thesis is important and clearly articulated: peptide AI is not a single problem, and evaluation must be claim-specific.
  2. The class-based organization (endocrine, PPI, oncology, delivery, vaccine, self-assembly) is sensible and preserves important distinctions.
  3. The Evidence Grid is a genuinely useful conceptual tool that separates methodological rigor from translational progress, addressing a common source of overstatement.
  4. The manuscript engages with practical constraints (manufacturability, regulatory guidance, synthesis feasibility) that are often ignored in computational reviews.
  5. The reporting checklist (Table 9) is a practical, actionable contribution.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Systematic review rigor
- **Claim pointer** The manuscript claims to be a "critical review" that "examines AI use across the major peptide classes" and "compares" methods, but the selection criteria for included studies are not described.
- **Evidence pointer** Section 1 (Introduction), final paragraph; Section 11 (Outlook) is not visible
- **Concern** The manuscript does not describe a systematic search strategy, inclusion/exclusion criteria, or a protocol for study selection. The phrase "representative studies" is used, but the basis for representativeness is not justified. This limits the reproducibility of the review and makes it difficult to assess whether the conclusions are robust to the choice of included studies.
- **Why it matters** A critical review that does not disclose its selection methodology cannot be distinguished from a narrative that cherry-picks examples to support a predetermined thesis. The Evidence Grid's credibility depends on the fairness and transparency of the studies to which it is applied.
- **Resolution test** Add a methods subsection describing the search strategy (databases, dates, terms), inclusion/exclusion criteria, and the number of records screened and included. If the review is intentionally non-systematic, state this explicitly and justify the selection rationale.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality / Quantitative support
- **Claim pointer** The manuscript states that "none reached M3 (0/25; 0/11 in Table 4 and 0/14 in Table 5)" and that the translational distribution is "twelve T0, eight T1, four T2, and one T3."
- **Evidence pointer** Section 9.1, Section 12 (Conclusions); Tables 4 and 5 (not visible)
- **Concern** The quantitative claims about the distribution of M/T scores across 25 studies are presented without the underlying data. The reader cannot verify these assignments, assess the criteria used, or understand borderline cases. The manuscript acknowledges assignments are "the author's reading," but this is insufficient for a claim that is central to the review's argument.
- **Why it matters** The Evidence Grid's utility depends on its consistent and transparent application. If the assignments are not reproducible, the grid becomes an opinion piece rather than an analytical tool.
- **Resolution test** Provide a supplementary table listing each scored study, the specific claim assessed, the M and T scores assigned, and a brief justification for each. This would allow readers to audit the assignments and apply the grid to their own work.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scope / Completeness
- **Claim pointer** The manuscript claims to cover "the major peptide classes" and to compare "sequence-based, chemical, graph, structure-aware, and multimodal representations," but the treatment of some classes appears uneven.
- **Evidence pointer** Section 2 (Design Space), Sections 5–8 (not fully visible)
- **Concern** The visible text suggests that antimicrobial peptides receive substantial attention, while other classes (e.g., vaccine epitopes, self-assembling materials) are treated more briefly. The manuscript does not justify this imbalance. If the review is intended to be comprehensive, the depth of coverage should be more uniform; if it is selective, the selection criteria should be stated.
- **Why it matters** Readers in underrepresented areas may find the review less useful, and the conclusions about the field as a whole may be biased by the uneven coverage.
- **Resolution test** Either expand the treatment of underrepresented classes or explicitly state that the review prioritizes certain classes for defined reasons (e.g., maturity of AI methods, availability of prospective data).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Model evaluation
- **Claim pointer** The manuscript discusses the limits of structure prediction for short and non-canonical peptides and the risk of circular evaluation in generative models.
- **Evidence pointer** Section 4.4, Section 6 (Generative Design), Section 7 (Structure-Aware Design)
- **Concern** The discussion of circular evaluation is conceptually correct but does not provide concrete examples of how this problem manifests in the cited studies, nor does it offer quantitative criteria for detecting it. The manuscript would be stronger if it illustrated the problem with a specific case and proposed operational checks (e.g., comparing generated sequences to training set nearest neighbors, reporting the correlation between predictor confidence and experimental success).
- **Why it matters** The field's main methodological risk is precisely this circularity, and the review's value would be enhanced by making the diagnosis more actionable.
- **Resolution test** Add a subsection or boxed example showing a specific case of circular evaluation, with quantitative evidence of how the predictor's confidence diverged from experimental outcomes, and propose a simple diagnostic test.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Section 9 (Evidence Grid)
- **Evidence pointer** Section 9, Table 6 (not visible)
- **Issue** The terms "methodological rigor" and "translational depth" are defined only by their levels (M0–M3, T0–T3), but the manuscript does not explain how a reader should assign a score in ambiguous cases, particularly when a study reports multiple claims of different strength.
- **Required correction** Add a short paragraph on scoring conventions, including how to handle multi-claim studies and whether scores are assigned to the strongest or the typical claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability / Structure
- **Affected element** Section 11 (Outlook)
- **Evidence pointer** Section 11 (not visible in the supplied text)
- **Issue** The Outlook section is listed in the table of contents but its content is not provided. If it is a list of priorities, it should be integrated with the Evidence Grid to show how each priority maps to specific M/T levels.
- **Required correction** Ensure the Outlook section explicitly references the grid and explains how each priority would be evaluated under it.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evidence / Citation practice
- **Affected element** Section 2.5 (Ocular delivery study)
- **Evidence pointer** Section 2.5, reference [17]
- **Issue** The ocular delivery study is cited as a template for complete evidence chains, but the manuscript does not describe the specific AI methods used or the nature of the prospective validation in sufficient detail for the reader to understand why it is exemplary.
- **Required correction** Add two or three sentences describing the AI method, the prospective design, and the specific evidence that justifies the T3 assignment.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness / Benchmarking
- **Affected element** Section 3.1 (Split design)
- **Evidence pointer** Section 3.1, reference [54] (PepBenchmark)
- **Issue** The manuscript mentions PepBenchmark as an emerging effort but does not describe its scope, tasks, or how it differs from existing benchmarks.
- **Required correction** Add a brief description of PepBenchmark's tasks and how it addresses peptide-specific challenges.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Section 4.2 (Chemical representations)
- **Evidence pointer** Section 4.2, reference [70] (HELM)
- **Issue** The distinction between HELM and SMILES/graph representations is described, but the practical implications for model choice are not stated.
- **Required correction** Add a sentence on when HELM is preferable to SMILES or graphs for peptide modeling.

## Risk / unsupported claims
- The quantitative claim that "none reached M3" across 25 scored studies is unsupported without the underlying scoring data.
- The claim that the Evidence Grid is a "peptide-specific synthesis of established reporting and maturity concepts" is plausible but not fully verifiable from the supplied text, as the relationship to MLTRL is described only briefly.
- The statement that "the sole T3 entry remains a preclinical animal study [17]" is presented as fact but depends on the author's scoring, which is not auditable.
- The claim that "similarity-aware splitting, matched toxicity assays, and species-specific labels are prerequisites" is asserted as a general principle but is not derived from a systematic comparison of studies with and without these features.
- The manuscript's statement that "the central scientific question is therefore not whether AI can assign persuasive scores, but whether it improves experimental decisions" is a reasonable thesis but is not empirically tested in the review; it remains an assertion.