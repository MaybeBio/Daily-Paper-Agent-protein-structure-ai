## Review setup
- **Input scope** Full manuscript text (Introduction, Methods, Results, Discussion, Conclusion, Data availability, Ethics, Author contributions, Conflict of interest, Generative AI statement, Publisher's note, Supplementary material, Acknowledgments)
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims based solely on the provided manuscript text. Supplementary materials referenced but not provided.
- **Shared manuscript claim summary** The authors integrate clinical-genomic surveillance with structural modeling and molecular dynamics to investigate how SARS-CoV-2 Spike N-terminal domain (NTD) sequence variability across pre- and post-vaccination periods relates to structural reorganization of a neutralizing antibody supersite. They report an exploratory association between Q23K and disease severity in the pre-vaccination period, a post-vaccination deletion event (ORF9b -29/N -33) associated with non-severe disease, and structural evidence for reorganization of the NTD-1-87 antibody interface in both Q23K and a post-vaccination NTD motif (T19I/A27S/D24 -26).
- **Visible evidence base** Clinical-genomic surveillance data (local cohort n=126; expanded cohort n=534), phylogenetic analysis, structural modeling (AlphaFold3), molecular dynamics simulations (GROMACS, CHARMM36), statistical analyses (logistic regression, Firth's penalized regression, Kruskal-Wallis, Dunn's post hoc, Cliff's delta, epsilon squared). Tables 1-3 and Figures 1-5 referenced. Supplementary Tables S1-S7 and Supplementary Figures S1-S7 referenced but not provided.
- **Missing materials affecting confidence** Supplementary Methods (S1-S7), Supplementary Tables S1-S7, Supplementary Figures S1-S7, and all referenced figures (Figures 1-5) are not provided. GISAID accession numbers and dataset details are not listed in the visible text. This substantially limits verification of methodological details, statistical outputs, and structural results.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question in SARS-CoV-2 evolution: how NTD sequence variability across different immune contexts relates to structural changes at a neutralizing antibody supersite. The integration of clinical-genomic surveillance with structural modeling is a commendable approach. However, the manuscript has several significant issues. The primary claims are heavily qualified as exploratory, which is appropriate given the study design, but this limits the strength of the conclusions. The structural analysis relies on a single antibody (1-87) and a modeled complex assembled by rigid superposition, with no experimental validation. The statistical associations are presented with appropriate caveats, but the confounding between outcome and sequencing source in the post-vaccination period is a serious limitation that is acknowledged but not fully resolved. The manuscript would benefit from clearer presentation of the structural results and a more critical discussion of the limitations of the modeling approach. The writing is generally clear but could be more concise in places. Overall, the manuscript presents a reasonable hypothesis-generating study, but the evidence does not fully establish the central claim of a mechanistic link between sequence variability and structural reorganization of the antibody supersite.

- **Who would be interested in the results, and why** Researchers in viral evolution, SARS-CoV-2 genomics, structural virology, and antibody biology would find this study of interest. The integration of surveillance data with structural modeling offers a framework for prioritizing antigenically relevant mutations for functional testing. The regional focus on Brazil and the comparison of pre- and post-vaccination periods provides useful epidemiological context. The structural findings, while preliminary, may inform hypotheses about NTD antibody escape mechanisms. Public health researchers tracking SARS-CoV-2 evolution may also find the methodological approach relevant.

- **Major strengths**
  1. The study addresses a timely and important question about NTD antigenic evolution in the context of changing population immunity.
  2. The integration of clinical-genomic surveillance with structural modeling is a novel and potentially valuable approach.
  3. The authors are appropriately cautious in interpreting their statistical associations as exploratory and hypothesis-generating.
  4. The acknowledgment and discussion of confounding and methodological limitations is thorough and transparent.
  5. The use of multiple analytical approaches (phylogenetics, structural modeling, MD simulations) provides a multi-faceted perspective.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that structural modeling and molecular dynamics support "reorganization of the modeled antibody-antigen interface, with redistribution of supersite contacts rather than loss of structural compatibility."
  - **Evidence pointer** Results section "Structural modeling and molecular dynamics"; Figures 1, 3-5; Supplementary Figures S2-S7; Supplementary Tables S4-S6
  - **Concern** The structural conclusions are based entirely on computational modeling without any experimental validation. The complex was assembled by rigid superposition onto the experimentally resolved 7L2D structure rather than co-folded, and the authors acknowledge that interface geometry was not independently optimized. The MD simulations assess a pre-formed complex and therefore inform on stability rather than association kinetics or epitope accessibility. The key figures and supplementary materials that would allow assessment of the structural results are not provided. The claim of "reorganization" is based on contact-persistence analysis, but the biological significance of this reorganization is unclear, especially given that the predicted binding free energy differences are within the error of the predictor. The authors themselves note that the results "should not be interpreted as quantitative affinity differences." This raises the question of what exactly the structural analysis demonstrates beyond a qualitative observation of different contact patterns in silico.
  - **Why it matters** The central claim of the manuscript, as stated in the title, is that sequence variability "links" to "structural reorganization" of the antibody supersite. If the structural evidence is purely computational and not experimentally validated, the strength of this claim is substantially weakened. The title may overstate what the evidence supports.
  - **Resolution test** Provide the actual structural data (figures, contact maps, trajectory analyses) for review. Include a more detailed discussion of the limitations of the modeling approach and explicitly state what can and cannot be concluded from computational predictions alone. Consider softening the title to reflect the hypothesis-generating nature of the structural findings. Ideally, include some experimental validation (e.g., binding assays, neutralization assays) to support the structural predictions.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical validity and confounding
  - **Claim pointer** The manuscript reports that Q23K was associated with severity in the pre-vaccination period (adjusted OR not fully reported in visible text) and that ORF9b -29/N -33 was associated with non-severe disease in the post-vaccination period.
  - **Evidence pointer** Results section "Genomic analysis and mutational profile"; Table 2; Supplementary Table S3
  - **Concern** The statistical analysis has several issues. First, the number of statistical tests performed is not clearly stated, and multiple testing correction is only applied to the screening step, not to the final adjusted models. Second, the Q23K association is based on a small number of mild cases with the mutation (2.0%, likely 3 of 153), leading to very wide confidence intervals (adjusted OR = 16.67, 95% CI 4.09-68.04 in the strict severity analysis). Third, the post-vaccination analysis is confounded by sequencing source, as acknowledged. The sensitivity analysis restricted to GISAID-only samples shows the association persists, but this does not rule out source-related artifacts within GISAID submissions. Fourth, the selection of mutations for adjusted modeling is not fully transparent. The manuscript states that mutations with prevalence >5% were eligible, but the criteria for which mutations were "prioritized" for multivariable modeling are not clearly described.
  - **Why it matters** The statistical associations are the basis for prioritizing mutations for structural analysis. If the associations are not robust, the rationale for the structural work is weakened. The confounding in the post-vaccination period is a serious limitation that cannot be fully resolved with the available data.
  - **Resolution test** Provide a more detailed description of the statistical analysis plan, including the number of tests performed and how multiple testing was handled. Report the full adjusted models with all covariates. Consider using more conservative statistical approaches (e.g., Firth's penalized regression for rare events). Acknowledge more explicitly that the Q23K association is based on very few events and may not be replicable. For the post-vaccination period, consider whether the analysis can be strengthened by restricting to GISAID-only samples with additional quality filters.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability and external validity
  - **Claim pointer** The manuscript implies that findings from a regional cohort in Espírito Santo, Brazil, may inform understanding of NTD evolution more broadly.
  - **Evidence pointer** Results section "Clinical and epidemiological characterization"; Discussion
  - **Concern** The study is based on a relatively small regional cohort, particularly in the post-vaccination period where only mild cases were available locally. The expanded cohort relies heavily on GISAID data with heterogeneous metadata. The generalizability of the findings to other geographic regions and immune contexts is unclear. The authors acknowledge this limitation but could more explicitly discuss how the regional focus may limit the broader applicability of the conclusions.
  - **Why it matters** The title and framing of the manuscript suggest broader implications for understanding NTD antigenic evolution. If the findings are highly context-dependent, the significance of the study is reduced.
  - **Resolution test** Add a more explicit discussion of the limitations of the regional focus and the potential for different patterns in other geographic and immunological contexts. Consider whether the conclusions can be appropriately generalized or whether they should be more narrowly framed.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and presentation
  - **Affected element** Title
  - **Evidence pointer** Title
  - **Issue** The title states "Antigenic remodeling of the SARS-CoV-2 Spike N-terminal domain links sequence variability to structural reorganization of a neutralizing antibody supersite." The word "links" implies a causal or mechanistic connection that the evidence may not fully support, given the exploratory nature of the findings and the purely computational structural analysis.
  - **Required correction** Consider revising the title to more accurately reflect the hypothesis-generating nature of the study, e.g., "Sequence variability in the SARS-CoV-2 Spike N-terminal domain is associated with structural reorganization of a neutralizing antibody supersite in silico."

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods
  - **Evidence pointer** Methods section "Structural modeling and molecular dynamics"
  - **Issue** The manuscript states that AlphaFold3 was used for modeling but does not provide sufficient detail on the input sequences, alignment methods, or model selection criteria. The MD simulation parameters are referenced to supplementary methods, which are not provided.
  - **Required correction** Provide more detail on the modeling and simulation parameters in the main text or ensure that the supplementary methods are accessible and complete.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability statement
  - **Issue** The data availability statement is vague and does not provide specific accession numbers or repository details. The GISAID dataset identifiers are mentioned in the methods but not in the data availability statement.
  - **Required correction** Provide specific accession numbers for all datasets, including GISAID EPI_SET identifiers, and clarify where supplementary data can be accessed.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Internal consistency
  - **Affected element** Results and Discussion
  - **Evidence pointer** Results section "Genomic analysis and mutational profile"; Discussion
  - **Issue** The manuscript states that Q23K was "regionally concentrated in Espírito Santo (57.4%)" but also notes that the phylogenetic analysis showed no evidence of a single transmission cluster. These statements are not contradictory but could be clarified to avoid confusion about the geographic distribution versus phylogenetic clustering.
  - **Required correction** Clarify the distinction between geographic concentration and phylogenetic clustering in the text.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Ethical reporting
  - **Affected element** Ethics statement
  - **Evidence pointer** Ethics statement
  - **Issue** The ethics statement is repetitive and contains redundant language. It also states that written informed consent was not required but does not clearly explain the basis for this waiver beyond stating that stored samples and secondary data were used.
  - **Required correction** Streamline the ethics statement and provide a clearer justification for the waiver of informed consent.

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Language and style
  - **Affected element** Throughout
  - **Evidence pointer** Various sections
  - **Issue** The manuscript contains some awkward phrasing and grammatical errors (e.g., "This study was conducted in accordance with the ethical standards of the Declaration of Helsinki" repeated twice in the ethics statement). The writing could be more concise in places.
  - **Required correction** Careful proofreading and editing for clarity and conciseness.

## Risk / unsupported claims
- The claim that structural reorganization of the NTD-1-87 interface occurs is based solely on computational modeling without experimental validation. This is a hypothesis, not an established finding.
- The association between Q23K and severity in the pre-vaccination period is based on a small number of events and should be considered exploratory.
- The association between ORF9b -29/N -33 and non-severe disease in the post-vaccination period is confounded by sequencing source and should be interpreted with caution.
- The claim that "alterations in distinct lineages converged on the same antigenic neighborhood" is based on limited data and may be overstated.
- The generalizability of the findings beyond the regional context of Espírito Santo, Brazil, is not established.
- The structural conclusions are based on a single antibody (1-87) and may not represent the broader polyclonal antibody response to the NTD supersite.
- The manuscript states that "no ELISA, SPR/BLI or neutralization assay was performed, and no experimental binding measurement supports the modeled interface, all interface conclusions are therefore computational." This is an important limitation that should be more prominently featured in the abstract and discussion.