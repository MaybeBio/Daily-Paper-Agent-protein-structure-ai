## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors report that the C-terminal intrinsically disordered region (CIDR) of the transcription factor RUNX2 is required for chromatin binding and osteogenic differentiation. They show that linear sequence motifs are dispensable, and instead features of the conformational ensemble predict function. They develop a generative design algorithm based on biophysical principles and produce de novo functional IDRs that rescue RUNX2 activity.
- **Visible evidence base** Abstract, introduction, results narrative, methods, and supplementary figure legends. No primary data files, figures, or tables were provided.
- **Missing materials affecting confidence** All figures, tables, and supplementary data files are absent. No numerical results, statistical outputs, or raw data are available for independent verification. The manuscript text alone is insufficient to assess the strength of the evidence.

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely question in the field of intrinsically disordered proteins and transcription factor biology. The authors present a compelling narrative that IDR conformational ensemble features, rather than linear motifs, drive RUNX2 function in a native cellular context. The conceptual advance is significant, and the integration of molecular dynamics simulations with generative design is innovative. However, the absence of all figures, tables, and data files makes it impossible to evaluate the technical soundness of the experiments or the validity of the conclusions. The claims are bold and would require strong evidence to be convincing. The manuscript is likely to be of high interest to the IDP and transcription factor communities, but the current submission cannot be assessed for publication readiness without the full data.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, transcription factor biology, chromatin biology, and protein design. The work is also relevant to those interested in stem cell differentiation and regenerative medicine. The generative design approach for IDRs would appeal to computational biologists and protein engineers.
- **Major strengths** The conceptual framing is clear and addresses a fundamental gap in the field. The use of a native differentiation assay is a strength compared to reductionist reporter systems. The combination of experimental and computational approaches is well integrated. The finding that linear motifs are dispensable is surprising and important. The generative design of functional IDRs is a significant technical achievement if the evidence supports it.
- **Major Concerns** The absence of all primary data prevents evaluation of the central claims. The manuscript text alone cannot support the conclusions drawn. Several specific concerns are listed below.
- **Minor Comments** Several methodological details are unclear from the text alone. The presentation would benefit from clearer descriptions of certain analyses.
- **Technical failings that need to be addressed before the case is established** The lack of figures, tables, and data files is the primary technical failing. Without these, no claim can be verified.
- **Assessment against Nature-style criteria** Originality: High. The work challenges the prevailing focus on linear motifs and proposes a new framework for IDR function. Scientific importance: High. The findings could reshape how the field thinks about TF IDRs and their role in gene regulation. Interdisciplinary readership: Moderate to high. The work bridges biophysics, cell biology, and computational design. Technical soundness: Not assessable from the provided text. Readability for nonspecialists: The text is generally well written and accessible, though some computational details may be challenging for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript cannot be evaluated without the full data. A revised submission with all figures and data would be required for a meaningful assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that the RUNX2 CIDR is required for chromatin binding and osteogenic differentiation, and that conformational ensemble features predict function.
- **Evidence pointer** Figures 1-5, supplementary figures S1-S14, all tables, and all data files are referenced but not provided.
- **Concern** The manuscript text describes experiments and results, but none of the actual data are available for review. No figures, tables, or numerical results are included. It is impossible to verify any of the claims made in the text without seeing the primary evidence.
- **Why it matters** The central claims of the manuscript are bold and would require strong experimental support. Without access to the data, the validity of the conclusions cannot be assessed. This is a fundamental barrier to evaluation.
- **Resolution test** Provide all figures, tables, and data files. Ensure that each claim in the text is supported by a specific figure or table.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report that certain variants show "full differentiation," "partial loss of function," or are "completely nonfunctional," and that correlations between conformational ensemble features and mineralization are significant.
- **Evidence pointer** Figures 2C, 2F, 3C, 3D, 5E, and supplementary figures S5, S7, S9, S14 are referenced but not provided.
- **Concern** The text reports qualitative outcomes and correlations, but no statistical details are provided. It is unclear how many replicates were performed, what statistical tests were used, and what the effect sizes and confidence intervals are. The claim that conformational ensemble features "predict" function requires a rigorous quantitative analysis.
- **Why it matters** The conclusions depend on the ability to distinguish between functional and non-functional variants, and to demonstrate that ensemble features are predictive. Without statistical rigor, these distinctions may not be reliable.
- **Resolution test** Provide detailed statistical analyses for all comparisons, including numbers of replicates, tests used, effect sizes, and confidence intervals. Show that the predictive power of ensemble features is statistically significant and not due to chance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** The authors state that the CIDR mediates chromatin binding and that this is required for osteogenic gene expression.
- **Evidence pointer** Figures 4A-J and supplementary figures S10-S13 are referenced but not provided.
- **Concern** The text describes single-molecule tracking, ChIP-seq, and RNA-seq experiments, but no results are shown. It is unclear how chromatin binding was measured, what the magnitude of the effects was, and how the authors distinguished between direct and indirect effects on gene expression.
- **Why it matters** The mechanistic model that the CIDR facilitates binding to clustered motifs in closed chromatin is central to the paper. Without evidence, this model remains speculative.
- **Resolution test** Provide the ChIP-seq and RNA-seq data, including quality metrics, peak calls, differential binding and expression analyses, and the single-molecule tracking data with appropriate controls.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Design validation
- **Claim pointer** The authors claim that de novo designed IDRs are "fully functional" and can drive osteogenic differentiation.
- **Evidence pointer** Figure 5E is referenced but not provided.
- **Concern** The text reports that two of six designed variants were fully functional, but no data are shown. It is unclear how "functional" was defined, what the success rate means in context, and whether the designed sequences truly have low identity to the wild-type CIDR.
- **Why it matters** The generative design approach is a key novelty of the paper. The success rate and the properties of the designed sequences must be clearly documented to support the claim that the approach works.
- **Resolution test** Provide the sequences of all designed variants, their predicted and measured properties, and the functional assay data. Show that the designed sequences are substantially different from the wild-type CIDR and that the functional ones meet predefined criteria.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Control experiments
- **Claim pointer** The authors conclude that linear motifs are dispensable for CIDR function based on scramble experiments.
- **Evidence pointer** Figures 2C, 2F, and supplementary figures S5-S7 are referenced but not provided.
- **Concern** The text states that all 28 individual tile scrambles were functional, and that local scrambles were functional while full scrambles were not. However, no data are shown. It is unclear how the scrambles were designed, whether they truly disrupt all potential linear motifs, and whether the full scrambles preserve local composition.
- **Why it matters** The conclusion that linear motifs are dispensable is a major finding that challenges existing models. This requires rigorous evidence that the scramble strategy effectively eliminates all motif-based interactions.
- **Resolution test** Provide the sequences of all scramble variants, demonstrate that they disrupt known and predicted motifs, and show the functional data for each variant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section
- **Evidence pointer** Methods, "Molecular dynamics simulations"
- **Issue** The description of the normalization procedure for contact probabilities and inter-bead distances is somewhat unclear. The equation for excess contacts is mentioned but not fully defined.
- **Required correction** Provide a clear mathematical definition of the excess contact calculation and the normalization procedure for inter-bead distances.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Generative IDR design"
- **Evidence pointer** Methods, "Generative IDR design"
- **Issue** The description of the generative design process is brief. It is unclear how the FINCHES intermap similarity is used as a constraint within GOOSE and what specific parameters were used.
- **Required correction** Provide a more detailed description of the design algorithm, including the objective function, constraints, and optimization parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "De novo design of functional RUNX2 CIDRs"
- **Evidence pointer** Figure 5E
- **Issue** The text states that the success rate of the design matches "state-of-the-art structured binder design," but this comparison is not quantified or referenced.
- **Required correction** Provide a specific reference and quantitative comparison for the success rate of structured binder design.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "RUNX2 CIDR is required to bind motif clusters in inaccessible chromatin"
- **Evidence pointer** Figure 4
- **Issue** The text mentions a linear model with motif count and accessibility as predictors, but the results of this model are not described in detail.
- **Required correction** Provide the coefficients, significance, and goodness-of-fit for the linear model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data, code, and materials availability
- **Evidence pointer** Data, code, and materials availability section
- **Issue** The statement that code is available on GitHub is good, but the specific repository name is not provided in the text.
- **Required correction** Provide the full URL or repository name for the code.

## Risk / unsupported claims
- The claim that the RUNX2 CIDR is required for chromatin binding is not supported by the provided text alone, as no binding data are shown.
- The claim that linear motifs are dispensable for CIDR function is not supported without the scramble data.
- The claim that conformational ensemble features predict function is not supported without the correlation analysis.
- The claim that de novo designed IDRs are fully functional is not supported without the functional assay data.
- The claim that the design success rate matches state-of-the-art structured binder design is not supported without a reference and quantitative comparison.
- The claim that the CIDR facilitates binding to clustered motifs in closed chromatin is speculative without the ChIP-seq and accessibility data.
- The claim that the platform measures "integrated IDR function" is not fully defined and would require validation.