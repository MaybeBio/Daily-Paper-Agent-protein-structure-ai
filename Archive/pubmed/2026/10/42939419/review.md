## Review setup
- **Input scope** Full manuscript text provided (Simple Summary, Introduction, Materials and Methods, Results, Discussion, Conclusions, Acknowledgments). Supplementary tables and figures are referenced but not supplied.
- **Assessment boundary** Assessment is limited to the supplied manuscript text. All supplementary items (Tables S1–S16, Figures S1A–S1D) and the primary data underlying the reported tool outputs were not available for inspection. No reanalysis of tool outputs was possible.
- **Shared manuscript claim summary** The manuscript reports an integrative in silico pipeline applied to 454 missense variants of RASSF2 retrieved from dbSNP, yielding 75 variants concordant across five pathogenicity predictors, then 19 variants concordant across three stability predictors, which are proposed as candidate destabilizing, oncogenic, and interaction-disrupting variants warranting experimental follow-up.
- **Visible evidence base** Main-text descriptions of methods and results, including reported counts, thresholds, tool versions, database access dates, and summary statistics (for example average pLDDT 77.88, ERRAT 92.4 percent, PROCHECK most-favored 83.8 percent, STRING network of 8 nodes and 19 edges). Underlying per-variant tables are referenced but not visible.
- **Missing materials affecting confidence** Tables S1–S16, Figures S1A–S1D, the full variant-level output of each predictor, the exact input files and parameter settings submitted to each server, and any code or workflow documentation. These are required to verify the reported counts and the concordance-based prioritization.

## Reviewer
- **Overall assessment** The manuscript addresses a legitimate and understudied target, RASSF2, and assembles a broad panel of established in silico predictors into a sequential filtering pipeline. The writing is generally clear and the limitations section is candid about the absence of experimental validation. However, the central contribution is a prioritized candidate list, and the evidence supporting that list cannot be verified from the supplied material because all variant-level tables are supplementary and unavailable. Several methodological choices are either internally inconsistent or insufficiently justified, and at least one reported result appears to contradict the stated selection criteria. As presented, the work is a hypothesis-generating computational survey rather than an established set of destabilizing variants.
- **Who would be interested in the results, and why** Cancer geneticists and computational biologists working on RAS effector and Hippo pathway tumor suppressors would find the candidate list of interest as a starting point for functional work. Pharmacogenomics and variant-curation groups may find the prioritization framework useful if the pipeline is made reproducible. The broader clinical oncology readership is unlikely to be served directly, because no variant is experimentally or clinically validated.
- **Major strengths** The target gene is biologically well motivated and the introduction links RASSF2 function to KRAS and MST1/MST2 signaling with appropriate citations. The use of concordance across multiple orthogonal predictors, rather than a single tool, is a reasonable design. The inclusion of AlphaMissense and AlphaFold-based structural analysis reflects current practice. The authors explicitly acknowledge that predictions are hypotheses and that experimental validation is required, and they note the low-to-moderate confidence of the RASSF2–KRAS complex. The discussion attempts to connect prioritized positions to domain architecture and to previously observed somatic positions in cBioPortal.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Verifiability and reporting completeness
- **Claim pointer** The manuscript claims that 454 missense variants were retrieved, that 75 were concordant across five tools, and that 19 were concordant across three stability tools.
- **Evidence pointer** Sections 3.1, 3.2, 3.4; Tables S1–S11 (not provided); Table 1 and Table 2 (not provided)
- **Concern** Every quantitative claim in the Results depends on supplementary tables that were not supplied. The per-tool counts, the identity of the 75 and 19 variants, and the per-variant scores cannot be checked. The main text also does not report the score distributions or the overlap structure needed to judge whether the concordance filter is doing meaningful work or simply intersecting correlated predictors.
- **Why it matters** The entire downstream analysis, including domain mapping, conservation, oncogenicity, and PPI disruption, is conditioned on the 19-variant set. If that set cannot be reconstructed, none of the secondary conclusions can be evaluated.
- **Resolution test** Provide all supplementary tables with per-variant scores for every tool, the exact input files, and a reproducible description of how multiallelic rsIDs were split and how ties or missing scores were handled. Report the full contingency structure of tool agreement.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency of the selection criteria
- **Claim pointer** The manuscript states that only variants with ΔΔG < −0.5 in DDMut and DynaMut2 and ΔΔG > 0.5 in ThermoMPNN were prioritized, and that 19 variants met this criterion.
- **Evidence pointer** Section 2.4; Section 3.4; Table 2 and Table S11 (not provided)
- **Concern** The sign conventions as written are not mutually consistent in a way that can be verified. DDMut and DynaMut2 are described as destabilizing when the score is negative, and ThermoMPNN as destabilizing when ΔΔG is positive, which is internally coherent, but the text of Section 3.4 states that ThermoMPNN predicted 64 variants to decrease stability with ΔΔG > 0 while also stating that DDMut and DynaMut2 predicted decreases with ΔΔG < 0. Without the tables, it is impossible to confirm that the 19-variant intersection was computed with the correct signs, and the reported counts (51, 54, 64) are not reconcilable with the stated thresholds from the text alone.
- **Why it matters** A sign error or threshold misapplication would invalidate the prioritized set, which is the core output of the study.
- **Resolution test** Provide the per-variant ΔΔG values from all three tools with explicit sign conventions, and state the number of variants passing each individual threshold as well as the intersection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural model validity for interface claims
- **Claim pointer** The manuscript claims that specific variants, notably V193D and Y275C, are predicted to destabilize or disrupt the RASSF2–KRAS and RASSF2–MST2 interfaces.
- **Evidence pointer** Section 3.12; Figure S1B–S1D (not provided); Table 10 (not provided)
- **Concern** The authors themselves report low-to-moderate confidence for the RASSF2–KRAS complex (pTM 0.63, ipTM 0.52) and moderate confidence for RASSF2–MST1 (pTM 0.68, ipTM 0.66) and RASSF2–MST2 (ipSAE 0.73, ipTM 0.68, pDockQ2 0.62). By the manuscript's own stated criteria, ipTM below 0.6 indicates a likely failed or low-confidence prediction. Interface-level variant effects computed on a low-confidence interface are not interpretable as evidence about binding.
- **Why it matters** The PPI disruption claims are presented in the Results and Conclusions as substantive findings, but they rest on models the authors describe as unreliable. This is a claim-evidence mismatch.
- **Resolution test** Either restrict interface claims to complexes meeting a pre-specified confidence threshold, or present them explicitly as exploratory and remove them from the Conclusions. Report per-residue confidence at the mutated positions and the distance to the interface for each variant analyzed.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Redundancy and independence of the predictor ensemble
- **Claim pointer** The manuscript treats agreement across five pathogenicity tools and across three stability tools as evidence of robustness.
- **Evidence pointer** Sections 2.2, 2.4, 3.2, 3.4
- **Concern** Several of the tools share training data, features, or architectural lineage. SIFT, PolyPhen2, and PhD-SNPg draw on related conservation and physicochemical signals; E-SNPs&GO and AlphaMissense both use protein language model embeddings; DDMut, DynaMut2, and ThermoMPNN are all structure-based ΔΔG predictors with overlapping training sets. Concordance among correlated predictors does not provide independent support, and the manuscript does not report any measure of predictor correlation or any benchmark of the ensemble against a labeled reference set.
- **Why it matters** The strength of the central claim rests on the assumption that agreement implies reliability. If the tools are correlated, the effective number of independent tests is much smaller than stated.
- **Resolution test** Report pairwise agreement and, if possible, correlation among tool scores on the 454-variant set. Benchmark the ensemble on a held-out set of RASSF2 or RASSF-family variants with known functional or clinical labels, if any exist.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of oncogenicity and clinical annotation
- **Claim pointer** The manuscript claims that all 19 variants are potentially oncogenic and that nine are oncogenic with high confidence, and it links these to cancer.
- **Evidence pointer** Sections 2.9, 3.8; Table 6 (not provided)
- **Concern** CScape is trained on somatic driver mutations, whereas the input here is germline dbSNP variation. The manuscript acknowledges this once in the Methods but then interprets the output in oncogenic terms throughout the Results and Discussion. In addition, the cBioPortal findings are positional coincidences at codons 235, 241, 245, 247, and 249 with different amino acid substitutions, which does not constitute evidence that the specific prioritized variants occur in tumors. The statement that no RASSF2 data are deposited in AACR GENIE is also a negative database result that should not be framed as a finding.
- **Why it matters** The oncogenicity framing may overstate the clinical relevance of germline variants that have no ClinVar classification and, in 18 of 19 cases, are extremely rare.
- **Resolution test** Reframe CScape output as a computational risk score applied out of its intended domain, separate germline from somatic evidence explicitly, and remove or clearly qualify the codon-position argument.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Downstream analyses disconnected from the prioritized variants
- **Claim pointer** The manuscript reports muTarget expression correlations and STRING network enrichment as part of the variant analysis.
- **Evidence pointer** Sections 2.14, 2.15, 3.13, 3.14; Tables S16 (not provided); Figure 6 and Figure 7 (not provided)
- **Concern** The muTarget analysis uses RASSF2 coding mutations in COAD and LUAD cohorts and does not test the 19 prioritized variants. The STRING analysis uses the RASSF2 gene name and does not incorporate any variant. Neither analysis can support conclusions about the prioritized missense variants, yet both appear in the Results and are discussed at length as if variant-specific.
- **Why it matters** These sections inflate the apparent scope of the study without adding variant-level evidence, and they may mislead readers about what was actually tested.
- **Resolution test** Either remove these analyses or relabel them clearly as gene-level context that is not variant-specific, and remove variant-related interpretive language from those sections.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Tool version and citation accuracy
- **Affected element** Methods Sections 2.2, 2.10, 2.13
- **Evidence pointer** Sections 2.2, 2.10, 2.13
- **Issue** PhD-SNPg is referred to as "PhD-SNP" in Section 3.2. GPS 6.0 is introduced in Section 2.10 but the threshold is attributed to "GPS 3.0," and Section 3.9 refers to "GPS 3.0." The version used is therefore ambiguous.
- **Required correction** Use a single consistent tool name and version throughout, and state the version actually executed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Threshold justification
- **Affected element** Methods Sections 2.2, 2.4, 2.9, 2.11
- **Evidence pointer** Sections 2.2, 2.4, 2.9, 2.11
- **Issue** Thresholds are stated but not justified against the tools' own recommended operating points. For example, AlphaMissense is used with a 0.5 cutoff although the developers recommend class-specific thresholds, and MutPred2 is used with 0.5 although the manuscript itself notes 0.68 and 0.80 correspond to 10 percent and 5 percent false-positive rates.
- **Required correction** Justify each threshold with a citation or a sensitivity analysis showing that the prioritized set is stable across reasonable threshold choices.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Database access dates
- **Affected element** Methods Sections 2.1 through 2.15
- **Evidence pointer** Sections 2.1 through 2.15
- **Issue** All access dates are in August 2026 and the manuscript date is October 2026. This is internally consistent but should be confirmed as correct, since future-dated accessions will confuse readers and reviewers.
- **Required correction** Verify and correct all access dates, or explain the dating convention.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Numerical reporting
- **Affected element** Results Sections 3.6 and 3.7
- **Evidence pointer** Sections 3.6, 3.7
- **Issue** Section 3.6 states that 14 variants are in the RA domain and two in the SARAH domain, and the Discussion states that 16 of 19 are in functionally important domains. Section 3.7 states that three variants showed structural changes and that "all the remaining 15 variants" were unchanged, which is consistent with 19 but should be stated explicitly. The arithmetic should be presented so readers can follow it without the supplementary tables.
- **Required correction** State the domain distribution and the structural-change counts explicitly and consistently in both Results and Discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Nomenclature and typography
- **Affected element** Throughout
- **Evidence pointer** Sections 2.3, 3.13, Discussion
- **Issue** "plDDT" and "pLDDT" are used interchangeably. "NRI12" appears where NR1I2 is intended. "Also." appears as a sentence fragment in the Discussion. "ipSAE" and "pDockQ2" are introduced without citation.
- **Required correction** Standardize nomenclature, correct the gene symbol, fix the fragment, and cite the interface metrics.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Redundant and unsupported interpretive language
- **Affected element** Discussion
- **Evidence pointer** Discussion paragraphs on muTarget and STRING
- **Issue** Several statements assert mechanistic roles for downstream genes, for example that CAVIN3 upregulation may be compensatory, that KRT40 upregulation points to epithelial reprogramming, and that GPR15 is tumor-suppressive in colon cancer, without variant-level evidence and in some cases without direct citation support in the supplied text.
- **Required correction** Soften or remove mechanistic assertions that are not supported by the presented data, and ensure each claim carries an appropriate citation.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. These concern the verifiability of the prioritized variant set, the internal consistency of the stability selection, and the use of low-confidence structural models to support interface-level claims. R1-M4, R1-M5, and R1-M6 additionally weaken the interpretive framework and should be addressed for the manuscript to be considered technically sound.

- **Assessment against Nature-style criteria** Originality is moderate. RASSF2 missense variant prioritization has not, to the authors' knowledge, been reported previously, but the methodological approach is a conventional stacking of existing web tools rather than a new method or resource. Scientific importance is currently limited because no variant is experimentally validated and the clinical annotations are absent; the work is hypothesis-generating. Interdisciplinary readership is plausible for cancer biology and computational genomics but not for the broader audience implied by a high-impact general journal, since the findings are predictions about a single gene. Technical soundness is not established from the supplied material, because the variant-level evidence is entirely supplementary and unavailable, the stability selection criteria cannot be verified, and the interface claims rest on models the authors describe as low confidence. Readability for nonspecialists is adequate in the Introduction and Simple Summary, but the Results are dense with tool names and thresholds and would benefit from a schematic of the filtering pipeline and a clear statement of what each stage does and does not establish.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript could become supportable as a computational prioritization study if the full variant-level data are provided, the stability selection is shown to be internally consistent, interface claims are either removed or restricted to adequately confident models, and the oncogenicity and gene-level analyses are reframed to match what was actually tested.

## Risk / unsupported claims
- The claim that 19 variants are destabilizing across three tools is not verifiable from the supplied material and depends on supplementary tables that were not provided.
- The claim that V193D and Y275C disrupt specific protein–protein interfaces is not supported, because the underlying complexes are reported by the authors as low to moderate confidence, and the RASSF2–KRAS ipTM of 0.52 falls below the manuscript's own threshold for a likely failed prediction.
- The claim that all 19 variants are potentially oncogenic is weakly supported, because CScape is applied outside its somatic training domain to germline variants, and no ClinVar classification exists for any of them.
- The claim that codon positions 235, 241, 245, 247, and 249 are mutation-sensitive is weakly supported, because the cBioPortal observations involve different amino acid substitutions at those positions and do not demonstrate occurrence of the prioritized variants.
- The muTarget expression correlations and the STRING network enrichment are not variant-specific and cannot be used to support conclusions about the 19 prioritized variants.
- The statement that no RASSF2 data are deposited in AACR GENIE is a negative database query result and should not be presented as a finding.
- The assertion that this is the first study to address nsSNPs in RASSF2 is a novelty claim that cannot be independently confirmed from the supplied material.