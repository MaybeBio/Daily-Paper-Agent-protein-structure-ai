## Review setup
- **Input scope** Full manuscript text provided (Abstract, Introduction, Results, Discussion, Materials and Methods, Data Availability, Acknowledgements). Figures and Supplementary Figures are referenced but not supplied as images; figure legends are not included.
- **Assessment boundary** Assessment is restricted to the supplied text. No figure panels, supplementary figures, supplementary tables (including Table S1), raw data, or statistical reporting tables were available. Conclusions that depend on visual inspection of blots, gels, or binding curves cannot be independently verified.
- **Shared manuscript claim summary** The manuscript claims that the RNA-binding domain of human GEMIN5 is an extended surface rather than a single motif, comprising (i) a serine-rich flexible loop between helices 19 and 20 near the TPR-like dimerization module and (ii) an acidic cluster within the intrinsically disordered region of the RBS domain, and that these elements cooperatively regulate RNA binding, self-dimerization, recruitment of endogenous GEMIN5, ribosome binding, and cap-dependent translation.
- **Visible evidence base** Text describes in vitro EMSA with purified recombinant proteins (D5 and SL1 probes), RNA pulldown from total cytoplasmic extracts using a streptavidin aptamer-tagged D5 RNA, SDS-resistant oligomer analysis by immunoblot, Ni-NTA pulldown for GEMIN5-FLAG recruitment, subcellular fractionation for 80S/S30 ribosome association, luciferase reporter assays under control and GEMIN5-silenced conditions, and AlphaFold-based structural modeling. Quantitative support is asserted but the underlying figures, replicates, and statistics are not visible.
- **Missing materials affecting confidence** All figures (Fig 1 to Fig 6), all supplementary figures (Fig S1 to Fig S5), Table S1, figure legends, raw immunoblots and EMSA autoradiographs, binding curves and fitted parameters, densitometric quantification values, replicate numbers per experiment, uncropped images, and the AlphaFold model coordinates or confidence metrics.

## Reviewer
- **Overall assessment** The manuscript addresses a legitimate and interesting question, namely how non-canonical and disordered elements within the C-terminal region of GEMIN5 contribute to RNA recognition. The conceptual framing, that an extended surface including a serine-rich loop and an acidic IDR cluster cooperatively regulates RNA binding, is plausible and consistent with the cited structural literature. However, from the supplied text alone the central claims are not independently verifiable, because the evidence rests on figures that were not provided, on binding assays whose quantitative treatment is only partially described, and on AlphaFold models that are used to support mechanistic conclusions. Several claims, particularly the cooperativity of the two elements, the causal link between self-dimerization and loss of GEMIN5 recruitment, and the interpretation of the translation data, are stated more strongly than the described evidence supports. The work is potentially publishable after technical and interpretive concerns are resolved, but the case is not established from the material supplied.
- **Who would be interested in the results, and why** Researchers in RNA biology and RNA-binding protein biochemistry, particularly those working on non-canonical RNA-binding domains, intrinsically disordered regions in RBPs, and autoinhibition or cooperative RNA recognition. Also relevant to groups studying the SMN complex, GEMIN5-associated neurodevelopmental disorders, and translation control. Structural biologists interested in how flexible loops and IDRs contribute to nucleic acid recognition in oligomeric assemblies would find the model-driven hypotheses of interest, provided the models are presented with appropriate uncertainty.
- **Major strengths** The question is well motivated and situated within a clear structural context derived from prior Cryo-EM work. The combination of in vitro binding assays with purified proteins and binding assays in the competitive environment of total cell extracts is a sensible strategy to distinguish intrinsic affinity from cellular context. The use of multiple truncation constructs (G5C, TPRα28, TPRα26, TPRα20, TPR, α18–26) provides a systematic scan of the C-terminal helical region. The attempt to connect RNA binding to downstream functional readouts (endogenous GEMIN5 recruitment, ribosome association, translation) is a strength in principle, and the inclusion of the G5C-Leu oligomerization-deficient mutant as a control is appropriate. The discussion links findings to patient variants, which is a reasonable translational framing.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for the core claim
- **Claim pointer** The manuscript claims that the RBD of GEMIN5 is an extended binding surface in which a serine-rich loop (EGKSSSSYH, helices 19–20) and an acidic cluster within the IDR (including EE1324–1325) cooperatively regulate RNA binding.
- **Evidence pointer** Fig 1D, Fig 1E, Fig 2B, Fig 2C, Fig 3B, Fig 3C, Fig S1, Fig S2A, Fig S2B, Fig S3A, Fig S3B; figure panels and legends not provided.
- **Concern** The central claim of an extended, cooperative RNA-binding surface is asserted on the basis of figures that were not supplied. The text reports dose-dependent binding and statistically significant differences, but no binding curves, fitted dissociation constants, replicate counts, or raw quantification are visible. Cooperativity is a specific mechanistic term that requires either direct measurement of coupled binding or a quantitative comparison of single versus combined mutations; the described experiments test individual and some combined substitutions but do not appear to include a design that isolates cooperativity from additive effects.
- **Why it matters** If the two elements act additively rather than cooperatively, the mechanistic model and the abstract's wording would need revision. Without visible quantitative binding data, the reader cannot judge the magnitude or reproducibility of the reported effects.
- **Resolution test** Provide all figure panels with legends, raw and uncropped blots and gels, binding curves with fitted parameters and confidence intervals, replicate numbers, and a quantitative comparison of single, double, and combined mutants that explicitly tests whether the effects are additive or cooperative.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity and interpretation of RNA-binding assays
- **Claim pointer** The manuscript claims that TPRα20 and TPRα26 bind GEMIN5 cognate targets D5 and SL1 with dose dependence, and that the serine-rich loop and acidic cluster regulate this binding.
- **Evidence pointer** Fig 1D, Fig 1E, Fig 2B, Fig 2C, Fig 3B, Fig 3C, Fig S1, Fig S2, Fig S3; Materials and Methods sections "RNA electrophoretic mobility shift assay" and "RNA binding assay in total cytoplasmic cell extracts".
- **Concern** The specificity of the reported interactions is not established from the supplied text. The manuscript does not describe control RNAs of unrelated sequence or structure, nor competition experiments with unlabeled cognate versus non-cognate RNA, nor tests with an unrelated Xpress-tagged protein to control for nonspecific bead or aptamer binding. The streptavidin aptamer pulldown measures proteins associated with the aptamer-tagged RNA, and the text does not describe an aptamer-only control. In addition, the in vitro binding buffer contains 250 mM NaCl, which is high, and the effect of ionic strength on the observed differences between constructs is not addressed.
- **Why it matters** Without specificity controls, the reported dose-dependent binding of TPRα20 and TPRα26 could reflect general nucleic acid or matrix association rather than cognate recognition, which would undermine the claim that these regions constitute a bona fide RNA-binding surface.
- **Resolution test** Include binding assays with at least one non-cognate RNA control, competition with unlabeled cognate and non-cognate RNA, an aptamer-only or empty-bead control, and an unrelated Xpress-tagged protein control. Report the effect of varying salt concentration on binding for the key constructs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Causal inference from correlation
- **Claim pointer** The manuscript claims that mutants SSS1141–1143AAA and SY1144–1145AA are compromised in both RNA binding and oligomerization dynamics, and that this inverse correlation with self-dimerization explains diminished GEMIN5 recruitment and reduced ribosome binding.
- **Evidence pointer** Fig 4A, Fig 4B, Fig 6A, Fig 6B, Fig 6C, Fig 6D; figure panels and legends not provided.
- **Concern** The argument rests on an inverse correlation between self-dimerization intensity and GEMIN5 recruitment or ribosome association. Correlation is presented as mechanism. The manuscript does not show that disrupting dimerization directly causes loss of recruitment, for example by testing an independent oligomerization-deficient mutant in the same recruitment and ribosome assays, nor does it exclude that the substitutions alter protein folding, stability, or expression level in a way that indirectly affects all readouts.
- **Why it matters** The mechanistic conclusion that oligomerization dynamics control recruitment and ribosome binding would not be supported if the mutants are globally misfolded or differentially expressed.
- **Resolution test** Provide expression and solubility controls for all mutants, include an independent oligomerization-deficient variant in the recruitment and ribosome assays, and, if feasible, use a direct dimerization measurement rather than SDS-resistant oligomers as the primary readout.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Use of computational modeling to support mechanistic claims
- **Claim pointer** The manuscript claims that AlphaFold modeling of G5C with D5 RNA shows the RNA surrounded by S1141–1144 of one subunit and R1035 and K1061 of the other, and that TPRα26 forms an elongated dimer engulfing the RNA, supporting the involvement of the serine-rich motif in RNA binding.
- **Evidence pointer** Fig 5A, Fig 5B, Fig 5C, Fig S5; Discussion section "Dissecting RNA interaction mediated by an extended RNA-binding surface".
- **Concern** AlphaFold predictions of protein–RNA complexes are used here as mechanistic evidence rather than as hypothesis-generating models. The text does not report model confidence metrics, per-residue pLDDT or PAE values, agreement with the deposited Cryo-EM structure beyond a stated overlap, or any experimental validation of the predicted RNA-contacting residues. The claim that the RNA is "surrounded" by specific residues is a model-derived statement, not an observation.
- **Why it matters** Structural models with unresolved flexible regions and no experimental validation cannot carry the mechanistic weight assigned to them, particularly when the IDR remains unstructured in the models while the same IDR is claimed to regulate binding.
- **Resolution test** Report model confidence metrics, explicitly label all modeling as hypothesis-generating, and, where possible, validate predicted contacts by mutagenesis of the implicated residues (for example R1035, K1061, R1090) with binding assays.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of translation data
- **Claim pointer** The manuscript claims that SSS1141–1143AAA and SY1144–1145AA increase cap-dependent translation and that this occurs through a mechanism independent of endogenous GEMIN5.
- **Evidence pointer** Fig S4A, Fig S4B, Fig S4C, Fig S4D; Results section "RNA binding and self-dimerization negatively impact on GEMIN5 recruitment and ribosome binding".
- **Concern** The interpretation of the translation data is not fully supported by the described design. The claim of independence from endogenous GEMIN5 is inferred from the behavior of mutants under silencing conditions, but the text does not report silencing efficiency, does not show that residual GEMIN5 is functionally negligible, and does not exclude indirect effects of the overexpressed fragments on translation machinery. The direction of the effect, increased translation with reduced ribosome binding, is counterintuitive and is not mechanistically explained.
- **Why it matters** The conclusion that these mutants act independently of GEMIN5 is a strong mechanistic claim that requires direct evidence, not inference from a partial knockdown.
- **Resolution test** Report knockdown efficiency at protein level, include rescue or re-expression controls, and provide a mechanistic explanation or additional experiment that reconciles increased translation with decreased ribosome association.

- **Major Concerns** (continued)

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Statistical and quantitative reporting
- **Claim pointer** The manuscript reports statistically significant differences for RNA binding, recruitment, ribosome binding, and translation, with P-values indicated by asterisks.
- **Evidence pointer** Statistical analyses section; figure legends not provided.
- **Concern** The statistical methods section states that significance between two groups was determined by an unpaired two-tailed t test, but the experimental designs described involve multiple comparisons across several mutants and conditions. No correction for multiple testing is described. Replicate numbers are stated as at least three but are not specified per experiment. Effect sizes and confidence intervals are not reported.
- **Why it matters** Without correction for multiple comparisons and without per-experiment replicate reporting, the reliability of the reported significance is difficult to assess.
- **Resolution test** Specify replicate numbers for each experiment, apply and state an appropriate multiple-comparison correction, and report effect sizes with confidence intervals.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Nomenclature consistency
- **Affected element** Construct naming throughout Results and Methods
- **Evidence pointer** Results sections and Materials and Methods "Constructs"
- **Issue** The manuscript uses several overlapping naming conventions, including TPRα20, TPRα26, TPRα28, α18–26, RBS1, RBS1–1326, and RBS1–1361, and the relationship between these names and the amino acid coordinates is not always stated at first use.
- **Required correction** Provide a single consolidated table or figure mapping each construct name to its exact amino acid boundaries and parent backbone, and use these names consistently.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Protein purification and refolding
- **Evidence pointer** Materials and Methods "Expression and purification of proteins"; Fig S3A
- **Issue** The text states that TPRα20, α18–26, TPRα26, and mutants were purified under 8 M urea and then dialyzed, and that native and denatured-refolded TPRα26 gave similar binding. The refolding protocol, final urea carryover, and verification of folded state are not described in detail.
- **Required correction** Describe the refolding procedure, report residual urea or imidazole concentrations, and provide evidence (for example circular dichroism or a functional assay) that the refolded proteins are properly folded.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability statement
- **Evidence pointer** Data Availability section
- **Issue** The statement says data will be made available upon reasonable request, which is not consistent with current expectations for structural models, raw blots, and quantitative datasets.
- **Required correction** Deposit the AlphaFold models and any structural coordinates, provide uncropped blots and gels as supplementary material, and make source data for the quantitative figures available in a public repository.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Citation of methods for SDS-resistant oligomer detection
- **Evidence pointer** Materials and Methods "Protein expression in cultured cells"
- **Issue** The text cites references (40, 41, 42) for the SDS-resistant oligomer protocol, but these numbers appear to correspond to references cited elsewhere for unrelated methods (flDPnn prediction and RNA pulldown). This may be a citation numbering error.
- **Required correction** Verify and correct the reference numbers for the SDS-resistant oligomer protocol.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure legend completeness
- **Affected element** All figures
- **Evidence pointer** Figure legends not provided
- **Issue** Figure legends were not included in the supplied material, so the number of replicates, statistical tests, and definitions of error bars cannot be verified.
- **Required correction** Provide complete figure legends stating n, the statistical test used, what error bars represent, and whether images are representative.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6.

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The concept that disordered and flexible regions contribute to RNA binding in GEMIN5 is a reasonable extension of prior structural work, but the individual elements (serine-rich loop, acidic IDR cluster) are not unprecedented in RBP biology, and the novelty depends on demonstrating a specific cooperative mechanism that is not yet established from the supplied evidence.
  - **Scientific importance** Potentially significant for the GEMIN5 and SMN complex field and for understanding non-canonical RNA-binding surfaces, but the current evidence base is insufficient to establish the mechanistic claims at the level implied by the abstract.
  - **Interdisciplinary readership** Moderate. The work would interest RNA biologists, structural biologists, and clinicians studying GEMIN5-associated neurodevelopmental disorders, but the mechanistic conclusions are currently too uncertain to support broad interdisciplinary claims.
  - **Technical soundness** Not established from the supplied material. Key figures, raw data, specificity controls, quantitative binding parameters, and model confidence metrics are missing. Statistical treatment of multiple comparisons is not described.
  - **Readability for nonspecialists** The abstract is concise and accessible. The Introduction is well structured. The Results, however, rely heavily on construct nomenclature and on figure references that cannot be evaluated, which would make the argument difficult to follow for a nonspecialist reader without the figures.

- **Recommendation posture** Currently not established from the provided evidence. Supportive in principle if the technical concerns, particularly the missing figures and raw data, specificity controls, quantitative binding analysis, and model validation, are resolved.

## Risk / unsupported claims
- The claim of cooperativity between the serine-rich loop and the acidic IDR cluster is not supported by the described experimental design, which does not isolate cooperativity from additive effects.
- The claim that TPRα20 and TPRα26 bind cognate RNA specifically is not supported without non-cognate RNA controls, competition experiments, and aptamer-only or unrelated-protein controls.
- The claim that self-dimerization inversely controls GEMIN5 recruitment and ribosome binding is correlative and not supported by a direct causal test.
- The claim that AlphaFold models show the RNA "surrounded" by specific residues is a model-derived statement presented without confidence metrics or experimental validation.
- The claim that the serine-rich motif mutants increase translation through a mechanism independent of endogenous GEMIN5 is not supported without demonstrated knockdown efficiency and rescue controls.
- The claim that the RBD of GEMIN5 consists of an extended binding surface is plausible but not established from the supplied material, because the supporting figures and quantitative data were not provided.
- The statement in the Data Availability section that data will be made available upon reasonable request is inconsistent with the need for access to structural models and raw quantitative data.