## Review setup
- **Input scope** Full manuscript text (Abstract, Results, Discussion, Methods) without supplementary figures, tables, or data files
- **Assessment boundary** Scientific claims, methodological soundness, and logical coherence as presented in the main text; supplementary materials referenced but not independently verified
- **Shared manuscript claim summary** The authors propose that small viral genomes (<11.6 kbp) encoding HK97-fold major capsid proteins (MCPs) with encapsulin-like domains represent an evolutionary link between HK97-fold viruses and encapsulins. They argue that the procapsid state is the evolutionary nexus enabling bidirectional transitions between these two biological compartments, supported by phylogenetic, structural, and genomic evidence.
- **Visible evidence base** Main text figures (Figs. 1-6), Methods section, and referenced supplementary files (not directly inspected)
- **Missing materials affecting confidence** Supplementary figures (S1-S9), supplementary tables (S1-S4), data files (S1-S16), and the GitHub repository were not provided for independent verification

## Reviewer

### Overall assessment
This manuscript presents a compelling and well-structured hypothesis regarding the evolutionary relationship between HK97-fold viruses and encapsulins. The identification of 93 twilight-zone viral genomes with encapsulin-enriched MCPs is a novel contribution that challenges the prevailing unidirectional "viruses-to-encapsulins" model. The integration of sequence-based and structure-based phylogenetics, combined with genomic context analysis, provides a multi-pronged approach that strengthens the central claims. However, several technical concerns regarding the interpretation of phylogenetic signals, the statistical robustness of key comparisons, and the speculative nature of the proposed evolutionary model require careful consideration before the conclusions can be fully accepted.

### Who would be interested in the results, and why
This work will appeal to virologists studying viral evolution and capsid structure, evolutionary biologists interested in the origins of cellular compartments, and researchers working on encapsulins as biotechnological tools. The proposed bidirectional evolutionary model and the identification of potential "transitional" viral forms have broad implications for understanding how protein shells diversify functionally. The biophysical framework linking capsid size to genome packaging capacity will also interest structural biologists and those studying the biophysics of self-assembly.

### Major strengths
1. The study addresses a significant and unresolved question in evolutionary biology: the directionality of evolution between viral capsids and cellular compartments.
2. The multi-method approach (sequence phylogeny, structure phylogeny, domain co-occurrence networks, genomic context) provides complementary lines of evidence.
3. The identification of a substantial number of novel twilight-zone viral genomes from diverse biomes expands the known diversity of HK97-fold systems.
4. The biophysical model linking internal volume to genome packaging capacity provides a quantitative framework for understanding evolutionary constraints.
5. The discussion of alternative hypotheses (e.g., satellite viruses, ssDNA packaging) demonstrates intellectual rigor.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic inference
- **Claim pointer** The authors claim that structural phylogenetic analysis reveals "at least three transition events between encapsulins and HK97-fold viruses, suggesting bidirectional evolution."
- **Evidence pointer** Figure 5C, Structural Groups 1, 4, and 5; Methods section "Structure-based phylogeny"
- **Concern** The structural phylogenetic tree is rooted using midpoint rooting, which the authors acknowledge is not optimal. Midpoint rooting assumes a roughly clock-like evolution, which is unlikely for such divergent protein families. The identification of "mixed" groups containing both viral and encapsulin sequences could be an artifact of the rooting method rather than evidence of true evolutionary transitions. Furthermore, the bootstrap support for Structural Group 4 is only moderate (BS = 61), which is below conventional thresholds for robust phylogenetic inference. The claim of "at least three transition events" rests heavily on the interpretation of these groupings, and without a reliable outgroup or alternative rooting strategy, the directionality of these transitions cannot be established.
- **Why it matters** The central thesis of bidirectional evolution depends on the correct interpretation of the phylogenetic relationships. If the rooting is incorrect, the "mixed" groups may simply reflect ancestral polymorphism or long-branch attraction rather than genuine virus-encapsulin transitions. The moderate bootstrap support for one of the three key groups further weakens the claim.
- **Resolution test** The authors should perform additional phylogenetic analyses with an appropriate outgroup (e.g., other HK97-fold proteins from clearly distinct lineages) or use alternative rooting methods (e.g., relaxed molecular clock models) to test whether the mixed groups remain monophyletic and whether the inferred transitions are robust. Sensitivity analyses excluding fast-evolving sites or using different substitution models would also help assess the stability of these groupings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical comparison
- **Claim pointer** The authors claim that "the fraction of identified HK97-fold major capsid proteins (MCPs) was significantly smaller in the twilight zone (11% or 536 MCPs) than in the control region (29% or 798)."
- **Evidence pointer** Figure 2C, Supplementary Figure S1, Supplementary Table S1
- **Concern** The statistical significance of this comparison is not reported in the main text. The authors state a difference in proportions but do not provide a test statistic, p-value, or effect size. Given that the twilight zone and control region are defined by arbitrary length cutoffs, it is unclear whether this difference reflects a biological phenomenon or is an artifact of the sampling and assembly methods. Additionally, the total number of contigs in each category is not clearly stated, making it impossible to assess the power of the comparison.
- **Why it matters** This observation motivates the entire study. If the lower frequency of HK97-fold MCPs in twilight-zone genomes is not statistically robust, the premise that these small genomes represent a distinct and under-sampled category of viral entities is weakened.
- **Resolution test** The authors should report the results of a formal statistical test (e.g., chi-square test or Fisher's exact test) comparing the proportions of HK97-fold MCPs between twilight-zone and control genomes, including confidence intervals for the difference. They should also discuss potential confounding factors such as assembly bias, sequencing depth, and genome completeness.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional interpretation
- **Claim pointer** The authors state that "the only structural proteins identified were the HK97-fold MCP and scaffold protein" in the dominant group of encapsulin-enriched mini genomes, and that these genomes "lack portal or tail genes."
- **Evidence pointer** Figure 4B, Figure 4C, Methods section "Genome annotation"
- **Concern** The absence of portal and tail genes is inferred from automated annotation tools (VPF-LPM, VIBRANT, Pfam). The authors acknowledge that some metagenomic elements may represent misclassified systems, but they do not discuss the sensitivity and specificity of their annotation pipeline for detecting these specific gene families. Portal proteins and tail proteins are highly divergent, and it is possible that some twilight-zone genomes encode such proteins that are simply not recognized by current HMM profiles. The claim that these entities lack portal and tail genes is therefore only as strong as the annotation tools used.
- **Why it matters** The absence of portal and tail genes is used to argue that these twilight-zone viruses are "simpler" and potentially more ancestral. If this absence is an artifact of annotation failure, the evolutionary interpretation would be compromised.
- **Resolution test** The authors should validate the absence of portal and tail genes in a subset of genomes using more sensitive methods, such as structure-based searches (e.g., Foldseek against the PDB) or manual curation of the genomic regions flanking the MCP gene. They should also report the false-negative rate of their annotation pipeline on a set of known viral genomes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural comparison
- **Claim pointer** The authors claim that "viral procapsids are more structurally similar to encapsulins than to the mature capsid state" based on comparison of a single encapsulin (PDB 6NJ8) and a single procapsid/mature capsid pair (PDB 7RWZ and 8VD4).
- **Evidence pointer** Figure 6A, Methods section "Full compartment comparisons"
- **Concern** The structural comparison is based on only one encapsulin and one virus system. The authors report internal diameters and volumes but do not provide a quantitative measure of structural similarity (e.g., root-mean-square deviation of Cα atoms, TM-score, or a comparison of subunit packing). The claim of "striking similarity" is therefore subjective. Furthermore, the comparison between a T=4 encapsulin and a T=4 procapsid may not be representative of all encapsulins and procapsids, which can adopt different T-numbers and subunit organizations.
- **Why it matters** The structural similarity between procapsids and encapsulins is a key piece of evidence for the proposed evolutionary link. Without a quantitative and systematic comparison across multiple systems, the claim remains anecdotal.
- **Resolution test** The authors should perform a systematic structural comparison of multiple encapsulin and procapsid structures (including different T-numbers) using quantitative measures of structural similarity. They should also compare the internal volume and packaging capacity across a broader set of structures to determine whether the observed similarity is general.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evolutionary model
- **Claim pointer** The authors propose that "HK97-fold shells emerged as lower-symmetry biochemical compartments" and that "crossing a critical capacity allows T=1 icosahedral shells to accommodate minimal genomes."
- **Evidence pointer** Figure 6D, Discussion section
- **Concern** This evolutionary model is presented as speculative ("we speculate"), which is appropriate, but the biophysical arguments are not fully developed. The claim that T=1 shells have sufficient volume to accommodate "minimal genomes" is based on a rough calculation of internal volume and DNA packaging density. However, the authors do not consider the additional volume required for the genome to be packaged in an ordered manner, the presence of internal proteins, or the mechanical constraints of DNA bending. The model also assumes that genome size is the primary selective pressure driving capsid expansion, without considering alternative explanations (e.g., host cell entry requirements, stability constraints).
- **Why it matters** The proposed model is a major conclusion of the paper and is presented as a framework for future research. If the biophysical assumptions are flawed, the model may mislead future investigations.
- **Resolution test** The authors should provide a more rigorous biophysical analysis, including calculations of the maximum genome length that can be packaged at different T-numbers, considering DNA bending energy and excluded volume effects. They should also discuss alternative selective pressures that could drive capsid size evolution.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Twilight zone" and "fringe zone" definitions
- **Evidence pointer** Methods section "Identifying environmental HK97-fold viral genomes in the twilight zone"
- **Issue** The terms "twilight zone" and "fringe zone" are introduced with specific length cutoffs (11.6 kbp and 20 kbp), but the rationale for these cutoffs is not explained. The 11.6 kbp threshold is defined by the smallest isolated HK97-fold virus genome, but it is unclear why 20 kbp was chosen as the upper boundary for the control region.
- **Required correction** Provide a brief justification for the chosen length cutoffs, or acknowledge that they are arbitrary and discuss the sensitivity of the results to these choices.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary data files
- **Evidence pointer** Methods section, Data Files S1-S16
- **Issue** The manuscript references 16 supplementary data files, but the main text does not provide a summary of their contents. This makes it difficult for readers to assess the scope of the data without downloading all files.
- **Required correction** Add a supplementary table listing each data file with a brief description of its contents.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Effect sizes
- **Evidence pointer** Figure 3B, 3C
- **Concern** The authors report p-values and Cliff's delta for the comparison of Phage-coat coverage and encapsulin domain fractions, but they do not report confidence intervals for the medians or the raw data distributions. This limits the interpretability of the effect sizes.
- **Required correction** Provide boxplots or violin plots showing the full distributions, and report 95% confidence intervals for the effect sizes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of bidirectional evolution
- **Evidence pointer** Discussion section
- **Concern** The authors mention that bidirectional evolution has been observed in other viral capsid folds (e.g., single jelly-roll proteins), but they do not cite specific examples. This would strengthen the argument that their findings are part of a broader pattern.
- **Required correction** Add citations to specific studies documenting bidirectional evolution in other capsid protein families.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 6D
- **Evidence pointer** Figure 6D
- **Concern** The schematic in Figure 6D is dense and may be difficult for non-specialist readers to interpret. The arrows and labels are not clearly explained in the figure legend.
- **Required correction** Expand the figure legend to explain each step of the proposed model, and consider simplifying the schematic or adding a separate panel with a step-by-step illustration.

### Technical failings that need to be addressed before the case is established
1. Lack of a formal statistical test for the key comparison of HK97-fold MCP frequency between twilight-zone and control genomes (R1-M2).
2. Midpoint rooting of the structural phylogeny without sensitivity analysis or alternative rooting strategies (R1-M1).
3. Absence of quantitative structural similarity metrics for the procapsid-encapsulin comparison (R1-M4).
4. Potential annotation bias in the detection of portal and tail genes (R1-M3).

### Assessment against Nature-style criteria
- **Originality**: High. The hypothesis of bidirectional evolution between HK97-fold viruses and encapsulins via procapsids is novel and challenges the prevailing unidirectional model. The identification of twilight-zone viral genomes as potential transitional forms is an original contribution.
- **Scientific importance**: High. The question of how viral capsids and cellular compartments evolved is fundamental to understanding the origins of life and the evolution of biological complexity. The proposed model has implications for multiple fields, including virology, evolutionary biology, and synthetic biology.
- **Interdisciplinary readership**: Moderate to high. The topic bridges virology, structural biology, and evolutionary biology. The biophysical arguments will appeal to biophysicists, while the genomic analyses will interest microbiologists. However, the heavy reliance on specialized terminology (e.g., T-numbers, HK97-fold) may limit accessibility to a broader readership.
- **Technical soundness**: Moderate. The multi-method approach is commendable, but several technical concerns (phylogenetic rooting, statistical reporting, annotation sensitivity) need to be addressed. The structural comparisons are based on a limited number of structures.
- **Readability for nonspecialists**: Moderate. The abstract and introduction are accessible, but the Results and Discussion sections assume significant background knowledge. The authors should consider adding a glossary or expanding the figure legends to improve accessibility.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a novel and important hypothesis with substantial supporting evidence. However, the central claims of bidirectional evolution and the procapsid nexus model depend on the robustness of the phylogenetic analyses and the statistical validity of the key comparisons. If the authors can address these concerns through additional analyses and more rigorous reporting, the manuscript would be suitable for publication in Nature Communications.