## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, technical soundness, claim support, and significance of the reported ML-assisted directed evolution of plant Rubisco
- **Shared manuscript claim summary** The authors apply the structure-informed protein language model ESM-IF1 to recommend amino acid substitution sites in the large subunit of tobacco Rubisco, construct a site-saturated library at these sites, and use a Rubisco-dependent E. coli selection system to identify variants with improved carboxylation kinetics, including the T391I substitution that improves carboxylation rate by 29% and aerobic carboxylation efficiency by 43%, with several variants carrying substitutions absent from natural plant Rubisco sequences and assembly competence confirmed in planta.
- **Visible evidence base** Main text figures 1-6 (referenced), tables 1 and S1-S8 (referenced), supplementary figures S1-S8 (referenced), methods descriptions, and data/code availability statements
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S8) not provided; raw NGS data not provided; detailed statistical analysis outputs not provided; plasmid maps and sequences not provided; full kinetic data for all variants not provided

## Reviewer
- **Overall assessment** This manuscript presents a compelling application of structure-informed machine learning to a long-standing challenge in plant biotechnology: engineering Rubisco for improved carboxylation efficiency. The work is timely, technically ambitious, and the results, if fully supported by the data, would represent a meaningful advance in both directed evolution methodology and our understanding of Rubisco's catalytic plasticity. The combination of ML-guided library design with a high-throughput in vivo selection system is elegant, and the identification of multiple improved variants, including one with a substantial 43% improvement in aerobic carboxylation efficiency, is notable. However, the manuscript as presented has several gaps in evidence that prevent full assessment of the claims. The absence of the supplementary materials, which contain critical data on library composition, NGS analysis, and full kinetic characterization, is a significant limitation. Additionally, several methodological details and statistical considerations require clarification before the conclusions can be fully accepted. The phylogenetic analysis and the in planta assembly data are presented in a way that suggests they are confirmatory, but the depth of evidence is not fully visible. Overall, this is a promising and potentially important contribution, but the current evidence base is insufficient to fully establish all claims.

- **Who would be interested in the results, and why** Plant biologists and crop scientists interested in improving photosynthetic efficiency for yield enhancement would find this work directly relevant. Synthetic biologists and protein engineers working on directed evolution methodologies would be interested in the demonstration that structure-informed ML models can effectively reduce the search space for beneficial mutations in a challenging enzyme system. Computational biologists developing and applying protein language models would find the application to a real-world engineering problem valuable. The work also speaks to the broader question of whether laboratory evolution can access sequence space beyond what natural selection has explored, which would interest evolutionary biologists. Finally, researchers working on Rubisco biology specifically, including those studying its biogenesis, assembly, and catalytic mechanism, would find the identification of new functional sites valuable.

- **Major strengths** The study addresses a problem of high biological and agricultural significance with a well-reasoned approach. The use of ESM-IF1, a structure-informed model, is a thoughtful choice given the known limitations of sequence-only models for highly conserved proteins like Rubisco. The comparison between ESM-1bv and ESM-IF1 predictions provides useful insight into the value of structural information. The development of a streamlined library (~400 variants) that achieves a 1700-fold higher enrichment rate compared to error-prone PCR libraries is a compelling demonstration of the efficiency of ML-guided design. The identification of variants with improved kinetics, particularly T391I with a 29% increase in kcatc and 43% improvement in kcatc/KCair, is a significant result. The confirmation that several improved variants carry substitutions absent from natural plant Rubisco sequences is conceptually important, suggesting that ML can access rare or unexplored sequence solutions. The in planta assembly data, while preliminary, addresses a critical concern about whether mutations selected in E. coli would be compatible with the more complex chloroplast environment. The use of the Farquhar model to translate in vitro kinetic improvements into predicted photosynthetic gains provides a useful framework for assessing agricultural relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The claim that "ML-assisted library design followed by selection in Rubisco-dependent E. coli identified multiple enriched variants displaying improved catalytic efficiency" and the specific kinetic parameters reported in Table 1
- **Evidence pointer** Table 1, Figures 2-4, Supplementary Tables S1-S5, Supplementary Figures S2-S3
- **Concern** The supplementary materials, which contain the detailed data supporting the library composition, NGS analysis, enrichment calculations, and full kinetic characterization, are not provided. Without these data, it is impossible to verify the completeness of the library, the rigor of the selection, the statistical significance of the enrichment, or the accuracy of the reported kinetic parameters. The manuscript states that the library contained ~400 variants covering 49 sites, but the actual coverage per site, the number of replicates, and the criteria for defining "enriched" are not fully described in the main text. The kinetic measurements are reported for a subset of variants, but the number of independent measurements, the error bars, and the statistical comparisons to wild-type are not visible.
- **Why it matters** The central claims of the paper rest on the quality and completeness of the library and the reliability of the kinetic measurements. If the library had poor coverage at key sites, or if the enrichment was not robustly reproduced, the conclusions about ML-guided design efficiency would be weakened. Similarly, if the kinetic improvements are not statistically robust or are based on a small number of measurements, the headline results could be overstated.
- **Resolution test** Provide the supplementary materials, including full NGS data, library coverage statistics, enrichment calculations with replicates, and complete kinetic data with appropriate statistical analysis (e.g., number of replicates, standard errors, significance tests). The kinetic parameters in Table 1 should be accompanied by confidence intervals and the number of independent measurements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that "the T391I substitution improved carboxylation rate by 29% and aerobic carboxylation efficiency by 43%"
- **Evidence pointer** Table 1, Figure 4A, Supplementary Figure S2
- **Concern** The kinetic characterization methodology raises several questions. The manuscript describes using soluble protein from E. coli lysates for initial measurements, with a purification protocol developed for more detailed analysis. The variability in kcatc measurements from lysates is acknowledged (Supplementary Figure S2), but the final values in Table 1 are presumably from purified protein. The purification method using His6Ubq-tagged RbcS is described, but the efficiency of assembly of the tagged complex, the yield, and the purity of the final product are not fully quantified. The manuscript states the purified Rubisco was "typically >70% pure," which leaves room for contaminating proteins that could affect activity measurements. Additionally, the assay conditions for measuring kcatc and KCair are described briefly, but the CO2 concentration range, the number of data points, and the fitting procedure are not detailed. The manuscript also does not report measurements of kcatO or KO for the improved variants, which would be necessary to fully understand the mechanistic basis of the improved carboxylation efficiency.
- **Why it matters** The quantitative claims about kinetic improvements are the core results of the paper. If the measurements are not sufficiently rigorous, the conclusions about the magnitude of improvement and the potential for agricultural impact would be undermined. The lack of KO data also limits the interpretation of whether the improvements are specific to carboxylation or reflect general changes in catalytic properties.
- **Resolution test** Provide detailed kinetic assay protocols, including CO2 and O2 concentration ranges, number of replicates, and fitting procedures. Report kcatO and KO values for the improved variants. Provide a more detailed characterization of the purified protein, including purity assessment (e.g., SDS-PAGE with densitometry) and confirmation of correct assembly (e.g., native PAGE or size exclusion chromatography with multi-angle light scattering).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The claim that "several improved variants carried amino acid changes not found in the evolutionary lineage of plants, despite being assembly competent in plant chloroplasts, demonstrating that ML-assisted protein design can explore functional sequence space beyond what is observed from natural sequence diversity"
- **Evidence pointer** Figure 4D-E, Supplementary Figure S7, Table 1
- **Concern** The phylogenetic analysis presented in Supplementary Figure S7 is described as showing that some improved variants carry substitutions absent from natural plant Rubisco sequences. However, the analysis is not visible, and the criteria for "not found in the evolutionary lineage of plants" are not clearly defined. The manuscript states that T391I is "generally observed only in distantly related Rubisco from diatoms and bacteria," but the frequency of isoleucine at this position across the full diversity of Rubisco sequences is not quantified. The claim that these substitutions are "rare" or "absent" from plants needs to be supported by a clear description of the sequence database used, the search criteria, and the statistical significance of the rarity. Additionally, the in planta assembly data (Figure 5) is presented as evidence that these rare substitutions are compatible with chloroplast biogenesis, but the data appears to be from transient expression in N. benthamiana, which may not fully recapitulate stable transformation outcomes.
- **Why it matters** The claim that ML can access sequence space beyond natural diversity is conceptually important and distinguishes this work from more conventional directed evolution approaches. If the rarity analysis is not rigorous, this claim would be weakened. The in planta assembly data is also critical for establishing the practical relevance of the findings.
- **Resolution test** Provide the full phylogenetic analysis, including the sequence database used, the alignment methods, and the frequency of each improved substitution across major Rubisco lineages. Provide more detailed data on the in planta assembly experiments, including the number of biological replicates, the efficiency of assembly, and ideally, data from stable transformants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that "ML-assisted library preparation is therefore effective for generating small, streamlined Rubisco libraries that successfully navigate the high degree of sequence conservation present in land plant isoforms"
- **Evidence pointer** Figure 3B, Supplementary Table S5
- **Concern** The comparison between the ML-guided library and error-prone PCR libraries is presented as a 1700-fold higher enrichment rate, but the details of this comparison are not fully visible. The error-prone PCR library from prior work (reference 12) may have used different selection conditions, different starting templates, or different definitions of "enriched." The manuscript does not describe how the enrichment rates were normalized or whether the comparison is apples-to-apples. Additionally, the library construction method using gene fragments from Twist Biosciences and Golden Gate Assembly is described, but the efficiency of the assembly, the number of transformants obtained, and the representation of all 49 sites in the final library are not quantified.
- **Why it matters** The efficiency of the ML-guided library design is a key methodological contribution. If the comparison to error-prone PCR is not rigorous, the claim of superior efficiency would be overstated. The library quality also directly impacts the interpretation of the selection results.
- **Resolution test** Provide a detailed comparison of the ML-guided library and the error-prone PCR library, including the number of variants screened, the selection conditions, and the criteria for enrichment. Report the library coverage statistics, including the number of transformants, the representation of each target site, and the number of variants per site.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The claim that "we further confirmed that ML-recommended, catalytically improved NtRbcL variants could assemble correctly in chloroplasts"
- **Evidence pointer** Figure 5, Supplementary Figure S8
- **Concern** The in planta assembly experiments use a novel N. benthamiana line (NbrbcM) in which the native rbcL is replaced with R. rubrum rbcM. The manuscript describes the generation of this line but does not provide detailed characterization of its phenotype, growth characteristics, or the efficiency of the plastome transformation. The transient expression system using agroinfiltration is described, but the efficiency of transformation, the expression levels achieved, and the reproducibility of the assembly results are not quantified. The manuscript states that "detectable levels of assembled Rubisco" were observed at 5 days post-infiltration, but the sensitivity of the detection method and the quantification of assembly efficiency are not provided.
- **Why it matters** The in planta assembly data is important for establishing that the improved variants are not only functional in E. coli but also compatible with the chloroplast environment. If the assembly data is not robust, the translational potential of the findings would be less certain.
- **Resolution test** Provide detailed characterization of the NbrbcM line, including confirmation of rbcL replacement, growth phenotypes, and Rubisco content. Provide quantitative data on the transient expression experiments, including transformation efficiency, expression levels, and assembly efficiency. Ideally, include data from stable transformants.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Location not provided
- **Issue** The introduction states that Rubisco "has proven challenging to engineer" but does not provide a concise summary of the specific challenges (e.g., chloroplast genome transformation, complex assembly requirements, catalytic trade-offs) that have historically hindered engineering efforts. A brief overview of these challenges would help contextualize the significance of the authors' approach.
- **Required correction** Add 2-3 sentences in the introduction summarizing the key technical barriers to Rubisco engineering, with appropriate citations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Preliminary screening and characterization"
- **Evidence pointer** Figure 2C, location not provided
- **Issue** The growth assays in Figure 2C appear to be qualitative (presence/absence of growth) rather than quantitative. The manuscript does not describe how growth was scored or whether the assays were performed in replicate.
- **Required correction** Provide a description of the growth assay methodology, including the number of replicates, the scoring criteria, and any statistical analysis. If the assays are qualitative, state this explicitly and discuss the limitations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** Table 1 reports kinetic parameters for multiple variants, but the units for kcatc and KCair are not explicitly stated in the table. The reader must infer the units from the text.
- **Required correction** Add units to the table headers or footnotes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, "ESM model implementation"
- **Evidence pointer** Location not provided
- **Issue** The methods state that ESM-1bv recommendations were generated "as described previously" and ESM-IF1 scoring was performed "as described previously," but the specific parameters, versions, and any modifications to the published protocols are not described. This makes it difficult to reproduce the computational analysis.
- **Required correction** Provide more detail on the specific model versions, any hyperparameters used, and the exact procedure for generating and scoring the recommendations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph 2
- **Evidence pointer** Location not provided
- **Issue** The discussion mentions that "reductions in chloroplast Rubisco content, increased XuBP production, and reduced activation state caused by these substitutions in planta may have prevented their evolutionary adoption in plants." This is speculative and not directly tested in the current work. While such speculation is appropriate for a discussion section, it should be clearly labeled as a hypothesis.
- **Required correction** Frame these potential limitations as hypotheses that require testing, and suggest specific experiments that could address them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods, "Variant library generation and selection"
- **Evidence pointer** Location not provided
- **Issue** The methods describe the construction of the site-saturated library but do not describe the selection conditions in detail. The concentration of arabinose, the CO2 and O2 levels, the duration of selection, and the number of passages are not fully specified.
- **Required correction** Provide a detailed description of the selection conditions, including the range of arabinose concentrations tested, the atmospheric conditions, and the selection timeline.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability statement
- **Evidence pointer** Location not provided
- **Issue** The statement says "All data and code needed to evaluate and reproduce the results in the paper are present in the paper and/or the Supplementary Materials." However, the supplementary materials are not provided with this submission, and the raw NGS data are only available through NCBI SRA. The statement should be more specific about what data are available where.
- **Required correction** Clarify the data availability statement to specify which data are in the main text, which are in the supplementary materials, and which are in external repositories.

- **Technical failings that need to be addressed before the case is established** R1-M1 (evidence completeness for library and kinetics), R1-M2 (kinetic characterization rigor), R1-M3 (phylogenetic analysis rigor), R1-M4 (library comparison methodology)

- **Assessment against Nature-style criteria** 
  - Originality: The application of a structure-informed protein language model to guide directed evolution of Rubisco is novel. While ML-guided protein engineering is an emerging field, this specific application to a challenging plant enzyme with a streamlined library design represents an original contribution. The finding that ML can identify substitutions absent from natural plant sequences is conceptually interesting.
  - Scientific importance: The work addresses a problem of fundamental importance in photosynthesis research and has potential implications for crop improvement. The demonstration that Rubisco's catalytic properties can be improved through targeted mutations is significant, though the magnitude of improvement and its translation to whole-plant photosynthesis remains to be established.
  - Interdisciplinary readership: The work bridges machine learning, protein engineering, plant biology, and photosynthesis research. The methods and findings would be of interest to researchers in all these fields, though the presentation assumes familiarity with both ML concepts and Rubisco biology.
  - Technical soundness: The overall approach is sound, but the current evidence base is incomplete. The lack of supplementary materials, the limited detail on kinetic characterization, and the absence of key control experiments prevent full assessment of technical rigor. The statistical treatment of the data is not fully visible.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible, but some sections assume significant background knowledge. The introduction and discussion are accessible to a broad scientific audience, but the results section may be challenging for readers not familiar with directed evolution or Rubisco kinetics. The use of abbreviations without always defining them clearly could be improved.

- **Recommendation posture** Supportive if technical concerns are resolved. The core concept is promising and the preliminary results are encouraging, but the current evidence base is insufficient to fully establish the claims. The manuscript would benefit from providing the supplementary materials, more detailed kinetic characterization, and a more rigorous phylogenetic analysis. If these concerns are addressed, this could be a valuable contribution to the field.

## Risk / unsupported claims
- The claim that ML-assisted library design achieves a 1700-fold higher enrichment rate compared to error-prone PCR is not fully supported without detailed comparison data.
- The claim that improved variants carry substitutions "not found in the evolutionary lineage of plants" is not fully supported without the complete phylogenetic analysis.
- The claim that variants are "assembly competent in plant chloroplasts" is based on transient expression data and may not fully predict stable transformation outcomes.
- The predicted photosynthetic improvements from the Farquhar model are based on in vitro kinetic parameters and assume equivalent Rubisco content and activation state in planta, which may not hold.
- The statement that "ML-assisted protein design can explore functional sequence space beyond what is observed from natural sequence diversity" is an interpretation that requires more evidence to be fully established.
- The mechanistic explanation for how T391I improves kcatc is speculative and not directly tested.
- The claim that the approach "sidesteps" natural constraints on Rubisco evolution is not fully supported, as the long-term stability and fitness consequences of these mutations in plants are unknown.