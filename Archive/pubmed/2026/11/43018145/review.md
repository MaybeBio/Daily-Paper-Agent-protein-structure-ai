## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a whole-proteome structural analysis of Treponema pallidum subsp. pallidum (Nichols strain, TPANIC) using AlphaFold and FoldSeek, achieving high-confidence models for approximately 92% of the proteome, assigning putative functions to 24 previously uncharacterized proteins, and proposing a revised composition of the outer membrane biogenesis machinery (a spirochete-specific BAM-TAM complex containing BamA, TamB, BamD, and BamB) based on comparative structural analyses and AlphaFold-Multimer modeling.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, model confidence metrics, validation statistics, list of the 24 assigned proteins, details of the BAM-TAM complex modeling, and any experimental corroboration

## Reviewer

- **Overall assessment** The abstract presents a potentially valuable application of AlphaFold-based structural prediction to a pathogen with a minimal genome and many uncharacterized proteins. The stated goals are clear and the approach is timely. However, the abstract alone provides insufficient evidence to evaluate the robustness of the structural models, the confidence of the functional assignments, or the validity of the proposed BAM-TAM complex revision. The claim of a "clearer prediction" of biological and pathogenic attributes is not substantiated by the evidence visible in the abstract. The work may be of interest to the spirochete and structural biology communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying Treponema pallidum biology and syphilis pathogenesis, spirochete outer membrane biology, and those applying AlphaFold-based structural genomics to minimal or fastidious organisms. The proposed BAM-TAM complex would be of particular interest to investigators of bacterial outer membrane protein biogenesis and spirochete-specific secretion systems.
- **Major strengths** The abstract addresses a clear and important gap, namely the large fraction of uncharacterized proteins in a clinically significant pathogen. The use of both precomputed and newly generated AlphaFold models, combined with FoldSeek for structural homology matching, is a sensible and current methodological approach. The reported coverage of approximately 92% of the proteome is a strong quantitative claim if supported by appropriate confidence metrics. The proposed revision of the BAM-TAM complex composition is a specific and testable hypothesis that could have broader implications for spirochete biology.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims high-confidence predicted structural models for approximately 92% of the TPANIC proteome.
  - **Evidence pointer** Abstract, "high-confidence predicted structural models for approximately 92% of the TPANIC proteome"; location not provided
  - **Concern** The abstract does not define what constitutes "high-confidence" in this context. No metrics such as pLDDT scores, predicted aligned error, or template modeling scores are provided. The threshold for inclusion in the 92% figure is not stated, and it is unclear whether this coverage refers to full-length models or domain-level coverage.
  - **Why it matters** Without a clear definition of confidence thresholds, the 92% coverage claim cannot be independently assessed. If the threshold is permissive, the functional assignments derived from these models may be unreliable. This is the foundational claim on which all downstream interpretations rest.
  - **Resolution test** Provide the specific confidence metric thresholds used, the distribution of scores across the proteome, and the proportion of residues covered per model. State whether the 92% refers to full-length proteins or domain-level coverage.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that structural homolog identification enabled functional annotation of 24 previously uncharacterized proteins.
  - **Evidence pointer** Abstract, "assign potential functional annotations to 24 previously uncharacterized proteins"; location not provided
  - **Concern** No details are given for the 24 proteins, including their identities, the confidence of the structural matches, the E-values or alignment scores from FoldSeek, or whether the assigned functions were validated by any independent method. The abstract does not state how many of these assignments are considered high-confidence versus speculative.
  - **Why it matters** Functional annotation from structural homology is only as reliable as the underlying match. Without evidence of match quality and independent validation, these assignments remain hypotheses. The claim of a "clearer prediction" of biological attributes depends on the reliability of these 24 assignments.
  - **Resolution test** List the 24 proteins with their predicted functions, provide FoldSeek match scores and structural alignment statistics, and indicate whether any assignments were corroborated by experimental data or additional computational methods.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that comparative structural analyses and AlphaFold-Multimer modeling redefined the composition of the TPA outer membrane biogenesis machinery, supporting a conserved spirochete-specific BAM-TAM complex containing BamA, TamB, BamD, and BamB.
  - **Evidence pointer** Abstract, "redefined the composition of the TPA outer membrane biogenesis machinery"; location not provided
  - **Concern** The abstract provides no details on the evidence for this redefinition. No information is given on the structural models of the individual components, the predicted interfaces, the confidence of the multimer predictions, or how this composition differs from previous annotations. The claim of a "conserved spirochete-specific" complex implies comparative analysis across species, but no such data are shown.
  - **Why it matters** This is the most specific and potentially impactful claim in the abstract. If the BAM-TAM complex composition is revised, it has implications for understanding outer membrane biogenesis in TPA and related spirochetes. However, without supporting structural and comparative evidence, this claim cannot be evaluated.
  - **Resolution test** Provide the AlphaFold-Multimer models for the proposed complex, including interface scores and predicted aligned error plots. Show comparative structural alignments with BAM-TAM components from other spirochetes or bacteria. Clearly state how the proposed composition differs from prior annotations.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Coverage claim
  - **Evidence pointer** Abstract, "approximately 92% of the TPANIC proteome"; location not provided
  - **Issue** The abstract does not clarify whether the 92% coverage is based on the total number of annotated proteins (977) or a different denominator, and whether this includes proteins with transmembrane regions or intrinsically disordered regions that are typically harder to model.
  - **Required correction** State the denominator and any exclusions, and comment on coverage for challenging protein classes.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Context
  - **Affected element** Prior work
  - **Evidence pointer** Abstract, "building upon prior structural conservation studies"; location not provided
  - **Concern** The abstract references prior structural conservation studies but does not specify how this work differs from or extends them beyond the number of newly annotated proteins.
  - **Required correction** Briefly state the specific prior studies and the incremental contribution of this work.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Clearer prediction"
  - **Evidence pointer** Title and abstract; location not provided
  - **Concern** The phrase "clearer prediction" in the title is vague and not operationally defined. It is unclear what metric of clarity or accuracy is being referenced.
  - **Required correction** Replace with a more specific claim, such as "improved functional annotation coverage" or "revised structural models," or define the term in the abstract.

## Risk / unsupported claims

- The claim of "high-confidence predicted structural models for approximately 92% of the TPANIC proteome" is unsupported without defined confidence thresholds and score distributions.
- The claim of functional annotation for 24 previously uncharacterized proteins is unsupported without protein identities, match scores, or validation.
- The claim of a redefined BAM-TAM complex containing BamA, TamB, BamD, and BamB is unsupported without multimer modeling details, interface confidence, or comparative data.
- The claim that the atlas provides a "clearer prediction of the organism's biological and pathogenic attributes" is not assessable from the abstract alone and appears overstated relative to the evidence presented.
- The statement that the approach will "help elucidate" roles in biology, pathogenesis, and host immune interactions is a forward-looking expectation, not a demonstrated outcome, and is appropriately framed as such.