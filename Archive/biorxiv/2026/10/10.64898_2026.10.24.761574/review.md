## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusion, Author Contributions, Declaration of Competing Interest, Acknowledgments). Figures and Tables are referenced but not supplied as visual content.
- **Assessment boundary** Assessment is limited to the supplied text. No figure images, table contents, sequence data, PAE plots, or BLASTp outputs were provided for independent inspection. No experimental data are reported.
- **Shared manuscript claim summary** The authors claim that BindCraft was used to design de novo miniprotein binders against seven selected hotspots spanning the SH2, linker, DNA-binding, and coiled-coil domains of STAT3; that 11 designs from five hotspots met a high-confidence AlphaFold3 (AF3) threshold (ipTM >= 0.75, pLDDT >= 90 for most of the complex); that these binders are predicted to dock with their intended domain and mostly within 4.5 Angstrom of at least one targeted hotspot residue; that some binder pairs are predicted to dock simultaneously without overlap and could support a sandwich assay format; and that BLASTp indicates the sequences are novel.
- **Visible evidence base** Narrative description of the computational workflow, parameter changes, hotspot selection criteria, scoring thresholds, and summarized results. All quantitative support resides in Tables 1 through 6 and Figures 1 through 6, none of which are supplied in inspectable form. No experimental binding, affinity, specificity, or functional data are presented.
- **Missing materials affecting confidence** Figure 1 (workflow), Figure 3 (AF3 models of all 11 binders), Figure 4 (simultaneous docking), Figure 5 (PAE plots), Figure 6 (numbering guide), Table 1 (BindCraft parameters), Table 2 (pipeline yield), Table 3 (ipTM values and sequences), Table 4 (BLASTp results), Table 5 (interface and overlap analysis), Table 6 (hotspot function and numbering). Absence of these prevents verification of essentially every quantitative claim.

## Reviewer
- **Overall assessment** This is a purely computational design report that generates and ranks minibinder candidates against STAT3 using BindCraft and AlphaFold3, with no experimental validation. The workflow is described clearly and the authors are explicit about the absence of wet-lab data. However, the central claims rest entirely on predicted confidence metrics (ipTM, pLDDT, PAE) that are not measures of binding, and the manuscript itself acknowledges this. The evidence base as supplied is insufficient to establish that any of the 11 candidates binds STAT3, that they engage the intended hotspots, or that the sandwich-assay proposal is physically realizable. The work is best characterized as a hypothesis-generating sequence disclosure rather than an established result. Several methodological choices (threshold selection, single-seed AF3 evaluation, structural superposition to construct a ternary model, BLASTp parameters) require clarification before even the computational claims can be assessed.
- **Who would be interested in the results, and why** Researchers in computational protein design and de novo binder engineering, particularly those working with BindCraft, RFdiffusion, and AlphaFold-based scoring pipelines, may find the reported yield statistics and hotspot-selection heuristics of practical interest. Groups working on STAT3 as an oncology target and on peptide or miniprotein inhibitors of transcription factors may be interested in the disclosed sequences as starting points for experimental screening. The sandwich-assay concept, if validated, would interest assay-development groups. Because no experimental validation is presented, the immediate audience is limited to those who would independently test the designs.
- **Major strengths** The manuscript is transparent about its limitations, explicitly stating that no experimental validation was performed and that ipTM does not translate to affinity. The hotspot-selection criteria are stated concretely (three residues, within 10 Angstrom C-alpha distance, at least two hydrophobic residues, partial surface exposure, preference for secondary structure), which makes the design rationale reproducible in principle. The decision to report the negative preliminary RFdiffusion/ProteinMPNN/AF2 results for hotspots 1 through 3 is a useful disclosure. The authors provide a numbering crosswalk between AFS and PDB 6NJS schemes, which is a genuine practical contribution for anyone attempting to reproduce or extend the work. The distinction between interface contact (within 4.5 Angstrom) and visual coverage is thoughtfully discussed, and the authors note the two measures often disagree rather than collapsing them into a single favorable metric.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidentiary support for the central claim
- **Claim pointer** The manuscript claims that 11 high-confidence minibinders were designed that bind STAT3 at or near the input hotspot residues, and that these constitute promising leads for therapeutic development.
- **Evidence pointer** Abstract, Section 3.1, Section 3.2, Table 3, Figure 3, location not provided for the underlying data
- **Concern** The entire claim of binding rests on AlphaFold3 confidence metrics (ipTM, pLDDT, PAE) with no experimental binding, affinity, or specificity measurement. The authors themselves state in Section 4.3 that AF3 ipTM does not translate directly to a binding constant. AlphaFold-class models are known to produce plausible interfaces for non-binding pairs, and ipTM is a self-consistency score rather than an affinity predictor. No negative controls (for example, designed binders against an unrelated surface, or STAT3 against an unrelated miniprotein) are reported to calibrate what an ipTM of 0.75 to 0.93 means in this specific system.
- **Why it matters** The central claim of the paper is that these are STAT3 binders. Without experimental validation or at minimum a calibration of the scoring metric against known binders and non-binders, the claim is not established. The therapeutic framing in the Abstract and Conclusion amplifies a claim the evidence cannot support.
- **Resolution test** Provide experimental binding data (for example, SPR, BLI, ITC, or pull-down) for at least a subset of the 11 candidates, or provide a calibration showing that the AF3 ipTM threshold used separates known STAT3 binders from known non-binders in this system. Alternatively, substantially soften the claim throughout to "computationally predicted candidate binders requiring experimental validation" and remove therapeutic-lead framing.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Target engagement and hotspot specificity
- **Claim pointer** The manuscript claims that most binders dock within 4.5 Angstrom of one or more targeted hotspot residues and that all 11 cover their intended domain.
- **Evidence pointer** Section 3.5, Table 5, Figure 3, location not provided
- **Concern** The reported results show that only 4 of 11 binders visually cover all their input hotspot residues, 2 cover none, and one binder (Hotspot4b_l77_s720724) has no hotspot residue among its interface residues at all. The authors acknowledge that the two measures of docking location often disagree. Yet the Abstract states that "most" binders dock within 4.5 Angstrom of one or more targeted hotspot residues, which is technically true but obscures that hotspot engagement is partial or absent for a majority of candidates. The claim that all 11 cover their intended domain is based on AF3 predictions that have not been experimentally verified, and domain-level coverage is a much weaker statement than hotspot engagement.
- **Why it matters** The design intent was site-specific targeting. If binders do not engage the intended hotspot, the rationale for selecting those hotspots (biological function, druggability) does not carry over to the binders. The discrepancy between interface contact and visual coverage also raises the question of which metric, if either, is meaningful for a predicted model.
- **Resolution test** Report per-binder hotspot engagement with explicit counts and clearly separate the two metrics in the main text rather than only in table notes. State plainly how many binders engage all, some, or none of their intended hotspot residues. If hotspot engagement is the design goal, explain why binders that fail it are retained as top candidates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of the sandwich-assay claim
- **Claim pointer** The manuscript claims that several minibinders are predicted to dock simultaneously to STAT3 without overlap and that such pairs have the potential to constitute STAT3 sandwich assays.
- **Evidence pointer** Section 2.6, Section 3.2, Figure 4, location not provided
- **Concern** The simultaneous docking model was not generated by predicting a ternary complex. The authors explicitly state in Section 2.6 that they declined to submit the ternary complex to AF3 because the tool would distort folds, and instead superimposed two independently predicted binary models in ChimeraX. This is a structural alignment of two separately predicted poses, not a prediction or measurement of simultaneous binding. There is no energetic or steric assessment of whether both binders can occupy the surface at once, no consideration of linker geometry for an assay format, and no experimental demonstration of simultaneous binding.
- **Why it matters** The sandwich-assay proposal is presented as a potential application and is one of the more distinctive claims of the paper. It rests on a superposition that cannot establish co-occupancy. Presenting it as a candidate format without this caveat in the Abstract overstates what the modeling supports.
- **Resolution test** Either perform an actual ternary complex prediction with an appropriate tool and report the result, or provide a quantitative steric and energetic argument for co-occupancy, or explicitly reframe the sandwich-assay statement as a speculative hypothesis contingent on experimental demonstration of simultaneous binding. The Abstract should not present it as a supported outcome.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility of the design and scoring pipeline
- **Claim pointer** The manuscript reports specific BindCraft parameter modifications and AF3 thresholds that define the high-confidence set.
- **Evidence pointer** Section 2.3, Section 2.4, Table 1, location not provided
- **Concern** The parameter changes are described (weights_con_inter raised from 1.0 to 2.0, inter_contact_distance reduced from 20 to 10 Angstrom, inter_contact_number revised from 2 to 3), but the full parameter set is deferred to Table 1, which is not supplied. The rationale for the specific AF3 thresholds (ipTM >= 0.75, pLDDT >= 90 for >= 85% of the complex) is not justified against any benchmark. The pLDDT criterion is described as determined by visual inspection of the ribbon structure, which is not a quantitative or reproducible criterion. The number of AF3 seeds or recycles is not stated. Whether the reported ipTM values are from a single prediction or an average is not stated.
- **Why it matters** Without the full parameter set and a stated, reproducible scoring protocol, independent groups cannot reproduce the design campaign or the selection of the 11 candidates. The visual pLDDT assessment in particular is a subjective step embedded in a quantitative selection pipeline.
- **Resolution test** Provide the complete BindCraft parameter set, state the AF3 run configuration (seeds, recycles, model version), replace the visual pLDDT assessment with a quantitative per-residue criterion and report the fraction of residues meeting it, and justify the chosen thresholds against a benchmark or a sensitivity analysis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Novelty assessment methodology
- **Claim pointer** The manuscript claims that BLASTp found no matches for six binders and only very low-significance matches for the other five, suggesting the sequences are novel and not chimeras of known proteins.
- **Evidence pointer** Section 2.7, Section 3.4, Table 4, location not provided
- **Concern** The BLASTp parameters include an E-value cutoff threshold of 10, which is unusually permissive for a novelty assessment, and a seed word size of 5, which is short and increases sensitivity to spurious short matches. The significance threshold for interpreting matches is stated separately as 10^-5 in Section 3.4, which creates an inconsistency between the search parameter and the interpretation threshold. The claim of "absolute novelty" in the Conclusion is stronger than a BLASTp search can support, since BLASTp detects sequence similarity, not structural or functional novelty, and does not exclude the possibility that a designed sequence adopts a known fold or engages an off-target partner.
- **Why it matters** The novelty claim is one of the stated hypotheses of the paper. If the search parameters are not appropriate or the interpretation threshold is inconsistent with the search threshold, the novelty conclusion is weakened. "Absolute novelty" is not a claim BLASTp can establish.
- **Resolution test** Justify the E-value cutoff of 10 and the word size of 5, or rerun with standard parameters and report both. Reconcile the search threshold with the interpretation threshold. Replace "absolutely novel" with a precise statement of what the search does and does not establish.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Specificity and off-target risk
- **Claim pointer** The manuscript presents the binders as candidates for targeting STAT3, with the SH2 domain noted as highly conserved among STAT proteins.
- **Evidence pointer** Section 1, Section 4.3, location not provided
- **Concern** The authors acknowledge in Section 4.3 that they did not investigate binding specificity against other proteins and that evaluating interaction with other STAT proteins would be instructive. Given that the SH2 domain is explicitly described in the Introduction as highly conserved among STAT proteins, and that several binders target the SH2 domain or adjacent regions, the absence of any specificity analysis is a substantive gap. No computational cross-reactivity screen against other STAT family members or against the human proteome is reported.
- **Why it matters** Selectivity is a central concern for STAT3-targeting therapeutics, as the Introduction itself notes. A binder that engages STAT3 but also engages STAT1, STAT5, or other conserved surfaces would not address the stated limitation of existing small-molecule inhibitors.
- **Resolution test** Perform a computational specificity screen, at minimum docking or AF3 evaluation against other STAT family members and ideally against a broader set of human proteins, and report the results. If specificity is not assessed, remove or substantially qualify any implication that these binders address the selectivity problem noted in the Introduction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Binder naming
- **Evidence pointer** Section 3.5, Section 4.2, Table 5
- **Issue** Binder identifiers are inconsistent. Most follow the pattern 6NJS_HS8_l75_s347865, but one is written as Hotspot4b_l77_s720724 without the 6NJS prefix, and Section 4.2 contains a garbled phrase "6NJS_HS11_l53_s331773 l64, l53" that appears to be a drafting error.
- **Required correction** Standardize all binder identifiers to a single format throughout the text and tables, and correct the garbled phrase in Section 4.2.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Numerical consistency
- **Affected element** Reported ipTM ranges
- **Evidence pointer** Section 3.1
- **Issue** The text states BindCraft ipTM values range from 0.81 to 0.94 and AF3 ipTM values range from 0.75 to 0.93. It is not stated whether these are per-binder single values or ranges across multiple predictions, and the relationship between the BindCraft (AF2) ipTM and the AF3 ipTM for the same binder is not discussed.
- **Required correction** State whether each reported value is a single prediction or an aggregate, and clarify the relationship between the two scoring stages.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Method description completeness
- **Affected element** AF3 evaluation protocol
- **Evidence pointer** Section 2.4
- **Issue** The manuscript states that sequences were manually submitted to the AlphaFold Server but does not report the number of seeds, recycles, or the model version, nor whether any prediction was repeated.
- **Required correction** Report the AF3 run configuration and whether predictions were repeated or averaged.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical interpretation
- **Affected element** BLASTp significance threshold
- **Evidence pointer** Section 2.7, Section 3.4
- **Issue** The search uses an E-value cutoff of 10 while the interpretation uses a significance threshold of 10^-5. The two thresholds are not reconciled.
- **Required correction** Explain the relationship between the search cutoff and the interpretation threshold, or use a single consistent threshold.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Claim scope
- **Affected element** Conclusion wording
- **Evidence pointer** Section 5
- **Issue** The Conclusion states the sequences "appear to be absolutely novel." "Absolutely" is not supportable by a BLASTp search.
- **Required correction** Replace with a precise statement of what the BLASTp results show, for example that no significant sequence similarity to known proteins was detected under the stated parameters.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure and table accessibility
- **Affected element** All figures and tables
- **Evidence pointer** Figures 1 through 6, Tables 1 through 6
- **Issue** The supplied manuscript text references all figures and tables but none were provided in inspectable form, so the quantitative basis of every result could not be verified.
- **Required correction** Ensure all figures and tables are supplied with the manuscript, with legible labels and complete notes, and that Table 5 notes define both metrics unambiguously.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reference formatting
- **Affected element** In-text citations
- **Evidence pointer** Section 1, Section 2.8, Section 4.2
- **Issue** Several citations appear with irregular spacing (for example "[ 1 ]", "[ 2 ]") and reference [20] is cited in Section 4.2 but the reference list was not supplied for verification.
- **Required correction** Standardize citation formatting and supply the full reference list.

- **Technical failings that need to be addressed before the case is established** R1-M1 (absence of experimental validation for the binding claim), R1-M2 (partial or absent hotspot engagement for a majority of candidates), R1-M3 (sandwich-assay claim rests on structural superposition rather than ternary prediction or measurement). R1-M4, R1-M5, and R1-M6 are non-blocking but must be resolved for the computational claims to be reproducible and for the specificity and novelty statements to be defensible.

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The application of BindCraft to STAT3 is a new combination, and the disclosure of designed sequences against multiple STAT3 domains has some value as a community resource. However, the methodological approach (BindCraft design followed by AlphaFold3 rescoring) is an established pattern, and the manuscript does not introduce a new method, benchmark, or conceptual advance. The sandwich-assay idea is the most distinctive element but is not supported by the evidence presented.
  - **Scientific importance** Currently limited. The work is hypothesis-generating and provides no experimental evidence that any candidate binds STAT3. The therapeutic framing in the Abstract and Conclusion is not matched by the evidence. Importance would increase substantially with even a small set of experimental binding measurements.
  - **Interdisciplinary readership** Limited in the current form. The paper is addressed to computational design specialists. The biological and clinical framing suggests an intent to reach oncology and drug-development audiences, but without experimental data those readers have no basis to act on the results beyond treating the sequences as screening candidates.
  - **Technical soundness** Partially sound but incomplete. The design pipeline is described with reasonable clarity, and the authors are candid about limitations. However, the scoring thresholds are not benchmarked, the pLDDT criterion is assessed visually, the AF3 run configuration is not reported, the BLASTp parameters are questionable and internally inconsistent, the ternary model is a superposition rather than a prediction, and no specificity analysis is performed. These are addressable but collectively they prevent the computational claims from being fully established.
  - **Readability for nonspecialists** Reasonable. The Introduction provides adequate background on STAT3 and the motivation for targeting it. The Methods and Results are dense with tool-specific terminology (ipTM, pLDDT, PAE, BindCraft parameters) that is not always explained for a general audience. A brief glossary or expanded definitions at first use would help.

- **Recommendation posture** Currently not established from the provided evidence. The computational workflow is described clearly enough to be potentially reproducible once the missing tables and parameters are supplied, and the authors are transparent about the absence of experimental validation. However, the central claims of binding, hotspot engagement, and sandwich-assay feasibility are not supported by the evidence presented, and the therapeutic framing exceeds what the data can bear. The manuscript would need experimental validation of at least a subset of candidates, or a substantial reframing as a purely computational candidate-disclosure report with all claims correspondingly qualified, before the case could be considered established.

## Risk / unsupported claims
- The claim that the 11 designs are STAT3 binders is unsupported. Only predicted confidence metrics are reported, and the authors acknowledge these do not translate to binding.
- The claim that most binders dock within 4.5 Angstrom of a targeted hotspot residue is technically reported but obscures that only 4 of 11 visually cover all hotspot residues and 2 cover none.
- The claim that binder pairs could constitute STAT3 sandwich assays is unsupported. It rests on superposition of two independently predicted binary models, not on a ternary complex prediction or measurement.
- The claim that the sequences are "absolutely novel" is unsupported by BLASTp, which assesses sequence similarity only and cannot establish absolute novelty.
- The implication that these binders address the selectivity limitations of existing STAT3 inhibitors is unsupported, since no specificity analysis against other STAT proteins or off-targets was performed.
- The framing of the candidates as leads for preclinical drug development is unsupported by the absence of any experimental affinity, specificity, stability, or functional data.
- The pLDDT-based high-confidence criterion is not reproducible as described, since it depends on visual inspection of ribbon structures rather than a quantitative per-residue computation.
- The relationship between BindCraft (AF2) ipTM and AF3 ipTM for the same binder is not reported, so the incremental value of the AF3 rescoring step cannot be assessed.