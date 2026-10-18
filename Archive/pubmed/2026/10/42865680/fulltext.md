# Rare missense variants identified by whole-genome sequencing in men with oligoasthenoteratozoospermia: An experimental study


## Background
  Oligoasthenoteratozoospermia (OAT) is a major cause of male infertility, characterized by low sperm count, poor motility, and abnormal morphology. While genetic factors contribute to a substantial proportion of cases, the specific variants underlying OAT remain largely unknown, especially in populations with high rates of consanguinity.


## Objective
  To identify rare candidate variants potentially associated with OAT using whole-genome sequencing (WGS) in 7 men from consanguineous families.


## Materials and Methods
  7 men with OAT from consanguineous families, with normal karyotypes and no Y-chromosome microdeletions, were selected. WGS was performed, and variants were called using DeepVariant. These variants were then annotated using the Ensembl variant effect predictor. Rare variants were prioritized based on their predicted pathogenicity and relevance to reproduction, and candidate variants were validated. Protein structure modeling and analysis of mutation-induced effects on molecular interactions were carried out using Swiss model and AlphaFold.


## Results
  We identified 2 rare homozygous missense variants in DNAH9 (p.Pro355Leu) and CFAP45 (p.Arg493Trp) in the index case with OAT. Both genes have been implicated in sperm flagellar structure and motility. Additional variants in genes associated with spermiogenesis, acrosomal integrity, and testicular function were also identified.


## Conclusion
  Our findings demonstrate the potential utility of WGS in identifying rare candidate variants potentially associated with OAT. The identified DNAH9 and CFAP45 variants, together with additional candidate variants, may contribute to the impaired sperm function observed in this man. This study also highlights the value of genome-wide analyses in improving our understanding of male infertility, particularly in consanguineous populations, and provides a foundation for future functional studies and personalized diagnostic approaches.


## 1. Introduction
  The World Health Organization defines infertility as the inability to conceive after at least 12 months of regular, unprotected intercourse. It affects 8–12% of couples of reproductive age and represents a significant global reproductive health issue (1). Male infertility can result from various causes, including genetic mutations, impaired testicular function, systemic diseases, medication use, and lifestyle factors. Genetic causes are estimated to account for roughly 10–15% of male infertility cases (2). Clinically, male infertility most commonly presents as azoospermia, where no sperm are detected in the ejaculate (3, 4), or as abnormalities in sperm number (oligozoospermia), reduced motility (asthenozoospermia), and shape (teratozoospermia), or combinations of these conditions (5, 6). Oligoasthenoteratozoospermia (OAT) is one of the main causes of male infertility, characterized by a reduced sperm count, decreased progressive sperm motility, and abnormal morphology. This combined phenotype often suggests underlying disturbances in complex molecular pathways governing germ cell proliferation, differentiation, flagellar assembly, and structural integrity of the spermatozoon. Due to its multifaceted nature, OAT is frequently associated with genetic factors, making it an important focus of molecular and genomic investigations aimed at elucidating the underlying mechanisms of male infertility (7, 8).

  Whole-exome sequencing and whole-genome sequencing (WGS) have been extensively used to identify genetic variants linked to OAT. Studies using these approaches have identified novel OAT-associated genes, including dynein axonemal heavy chain (DNAH)1, cilia- and flagella-associated protein (CFAP) 43, CFAP44, cation channel sperm associated 2, and testis expressed 11, significantly expanding our understanding of the molecular mechanisms of the disorder (9–12). Among these approaches, WGS provides a more comprehensive assessment of the genome by enabling the detection of a broader spectrum of genetic alterations, including variants in coding and non-coding regions, structural rearrangements, copy number variations, and repeat expansions. In addition, WGS offers more uniform coverage across complex genomic regions while maintaining reliable sequencing of protein-coding sequences. This broader genomic assessment is particularly valuable in consanguineous populations, where rare homozygous variants may contribute to male infertility phenotypes (3, 4, 13).

  In this research, we utilized WGS to detect rare missense variants in an Iranian man with OAT, marking the first genome-wide study in this population and highlighting the importance of population-specific genomic research in male infertility.


## 2. Materials and Methods

### Participant selection and sample preparation
  To perform this experimental study, 7 men with OAT, all with normal karyotypes and no Y chromosome microdeletions, were recruited from consanguineous families at the Yazd Reproductive Sciences Institute, Yazd, Iran between August 2023 and March 2024. All men had no history of drug abuse, varicocele, testicular torsion, orchitis, or cryptorchidism. Peripheral blood (5–10 mL) was collected in EDTA tubes, and genomic DNA was extracted using the High Pure PCR Template Preparation kit (Roche Diagnostics, Mannheim, Germany). DNA quality and concentration were assessed with a NanoDrop 1000 spectrophotometer (Thermo Scientific, Waltham, MA, USA) and a Quantus fluorometer (Promega, Madison, WI, USA), and samples were stored at -20 C until further analysis.


### WGS and variant prioritization in OAT
  Genomic DNA extracted from men with OAT was sequenced using the Illumina NovaSeq X platform, achieving an average coverage of  ∼ 30 ×  ( ∼ 120 Gbp per sample). Raw FASTQ files were processed using the CGP map, including quality control with FastQC v0.12.0, alignment to the human reference genome (GRCh38) using BWA-MEM2, and duplicate marking/sorting with biobambam2 and SAMtools (14, 15).

  Variant calling was performed with DeepVariant v1.6.0, retaining high-confidence variants (PASS status) (16). Variants were filtered using VCFtools v0.1.16 with thresholds of quality score  ≥  30, mean depth of coverage  ≥  10 × , and genotype call rate  ≥  90% (17). Functional annotation was conducted using ensembl variant effect predictor (release 112), selecting representative transcripts, and incorporating protein-level predictions (SIFT, PolyPhen-2) (18), population allele frequencies (1000 Genomes, gnomAD), and CADD scores from dbNSFP v4.4a annotated via SnpSift v5.2 (19).

  Rare variants were prioritized by excluding alleles with gnomAD genome frequency  ≥  0.01, while variants lacking frequency annotations were retained to capture potentially novel rare variants. Downstream analyses evaluated variant type, inheritance patterns, and predicted pathogenicity using MutationTaster. Expression relevance was assessed using genotype-tissue expression v7, and functional associations with fertility and spermatogenesis were explored via PubMed searches using gene IDs combined with keywords such as “spermatogenesis”, “infertility”, and “reproductive biology”.

  Copy-number variants were detected with ClinSV v1.0 and integrated with single-nucleotide variants and small insertions/deletions to provide a comprehensive overview of genomic alterations associated with male infertility (20). Variants were further prioritized according to their inheritance pattern, predicted functional consequences, tissue-specific expression profiles, and previously reported or biologically plausible roles in spermatogenesis, sperm motility, or male infertility. Particular attention was given to rare homozygous variants identified in genes with testis-enriched expression and functional relevance to flagellar structure and reproductive biology.


### Validation of variants
  Visual inspection of binary alignment/map files was performed for candidate variants identified in DNAH9 and cilia and flagella associated protein 45 (CFAP45) using integrative genomics viewer (v2.14.0) (21). The identified rare variants were further validated by Sanger sequencing using an ABI 3500XL genetic analyzer. Sequence chromatograms were analyzed with FinchTV software. Primers were designed for the DNAH9 and CFAP45 variants, and both variants were successfully confirmed by Sanger sequencing.


### Structural protein modeling

#### Domain annotation
  The NCBI conserved domain was searched for putative conserved domains within the protein sequence at https://www.ncbi.nlm.nih.gov/Structure/cdd/wrpsb.cgi.


#### Amino acid substitution effects
  To evaluate the potential functional consequences of the identified missense variants, several computational prediction tools were employed. Sorting intolerant from tolerant (https://sift.bii.a-star.edu.sg/) was used to assess the impact of amino acid substitutions on protein function based on sequence conservation and physicochemical properties of amino acids. Variants with SIFT scores below 0.05 were considered potentially deleterious. The Seq Rep value provided by SIFT was also examined to estimate the reliability of predictions, as low values may indicate insufficient sequence information at the corresponding position.

  Polymorphism phenotyping version 2 (http://genetics.bwh.harvard.edu/pph2/) was applied to predict the possible effects of amino acid substitutions on protein structure and biological function. This method integrates sequence conservation, structural information, and evolutionary characteristics to generate a position-specific independent count score. Variants were classified as benign (0.00–0.15), possibly damaging (0.15–0.85), or probably damaging (0.85–1.00). Sensitivity and specificity values provided by the software were used to evaluate prediction confidence. The functional impact of amino acid substitutions was further investigated using Protein variation effect analyzer (PROVEAN, http://provean.jcvi.org/index.php), an alignment-based algorithm designed to assess the effects of missense variants and small insertions/deletions. Variants with scores below -2.5 were considered deleterious.

  Predicting human deleterious SNPs in the human genome (PHD-SNPg, https://snps.biofold.org/phd-snpg) was employed to classify single-nucleotide variants as pathogenic or benign using sequence-based machine learning approaches. Variants with prediction probabilities greater than 0.5 were considered potentially pathogenic. Protein stability changes resulting from amino acid substitutions were evaluated using I-Mutant2.0 (http://folding.biofold.org/i-mutant/i-mutant2.0.html). This support vector machine-based tool estimates the change in Gibbs free energy associated with a mutation. Negative change in Gibbs free energy values indicate decreased protein stability, whereas positive values suggest increased stability.


#### Structural consideration
  The 3-dimensional structure of the mutant and wild-type proteins was determined using the Swiss model software at https://swissmodel.expasy.org/, and the orientation and  σ  and  φ  angles of the mutant amino acids were calculated in comparison to the original amino acids.


### Ethical Considerations
  Informed consent was obtained for genome sequencing under protocols approved by the ethics committee of Shahid Sadoughi University of Medical Sciences, Yazd, Iran (Code: IR.SSU.MEDICINE.REC.1402.125).


## 3. Results
  In this study, WGS was performed in 7 men diagnosed with OAT. Among these individuals, one man from a consanguineous family harbored a rare homozygous candidate variant in genes with known or possible roles in sperm function and male fertility (Figure 1A). Therefore, subsequent analyses focused on this genetically informative case to investigate potential molecular contributors to the OAT phenotype. The remaining men did not show similarly prioritized variants after comprehensive filtering and variant interpretation. Semen analysis revealed severe OAT, with a semen volume of 3 mL, high viscosity, sperm concentration of 2  ×  10⁶/mL, absence of progressive motility, and  <  1% normal sperm morphology. Evaluation of non-progressive motility was not reliable because of the extremely low sperm count. Both motile and immotile spermatozoa were observed, and the sample was considered suitable for intracytoplasmic sperm injection according to World Health Organization 2021 guidelines. Hormonal evaluation revealed levels of luteinizing hormone 12.69 mIU/mL, follicle-stimulating hormone 4.20 mIU/mL, testosterone 3.581 ng/mL, estradiol 36.81 pg/mL, and thyroid stimulating hormone 1.266 µIU/mL, all within or close to the respective reference ranges.


### Identified candidate variants potentially associated with OAT
  In one man with OAT, we identified 2 rare homozygous missense variants: c.1064C > T in the DNAH9 gene, resulting in a proline-to-leucine substitution at position 355 (p.Pro355Leu)and c.1477C > T in the CFAP45 gene, causing an arginine-to-tryptophan substitution at position 493 (p.Arg493Trp) (Table I).

  DNAH9 encodes a component of the outer dynein arm heavy chain expressed in many tissues and organs, including the testis, with 4.733 transcripts per million (https://gtexportal.org/home/gene/DNAH9), whereas CFAP45 is predominantly expressed in the testis with 82.50 transcripts per million (https://gtexportal.org/home/gene/CFAP45).

  The other variants identified in the men with OAT have been classified as possessing lower impact or being benign. However, it is important to note that further research is needed to explore their potential roles in the development of OAT. These include homozygous missense variants: c.1810G > A in the insulin-like growth factor II receptor (IGF2R) gene, c.905G > A in the F-Box only protein 24 (FBXO24) gene, c.118G > A in the actin-related protein T1 (ACTRT1) gene, c.1159G > A in the spermatogenesis-associated protein 2 (SPATA2) gene, and c.176C > T in the GIT ArfGAP 1 (GIT1) gene.


### Validation of variants
  The identified missense variants in DNAH9 (c.1064C > T; chr17:11617570 C > T) and CFAP45 (c.1477C > T; chr1:159873044 G > A) were independently validated using binary alignment map file inspection and Sanger sequencing. Confirmation of the DNAH9 variant is shown in figure 1B, 1C, while validation of the CFAP45 variant is presented in figure 1D, 1E.


### Protein structure and functional insights

#### Domain annotation
  5 major domains were identified in the DNAH9 protein, including Dynein heavy chain, N-terminal region 1 (interval: 214–789), Dynein heavy chain, N-terminal region 2 (interval: 1292–1698), hydrolytic ATP binding site of dynein motor region (interval: 1832–2158), microtubule-binding stalk of dynein motor (interval: 3067–3410), and Dynein heavy chain C-terminal domain (interval: 4189–4484). The P355L mutation is located precisely in the Dynein heavy chain, N-terminal region 1.

  Dynein heavy chains interact with other heavy-chain subunits to generate dimeric assemblies and with intermediate- and light-chain complexes to establish the basal cargo-binding unit. The N-terminal domain identified in this family contains motifs implicated in mediating these intermolecular interactions. Structural studies suggest that this region is intrinsically flexible and does not form a stable rigid conformation. Schematic illustration of DNAH9 and CFAP45 domains is shown in figure 2.

  Most of the CFAP45 protein (interval: 184–524) belongs to the trichohyalin-plectin-homology (TPH) domain (accession: pfam13868). The R493W mutation is located exactly in this domain.

  The TPH domain represents a family of eukaryotic proteins that includes trichoplein (also known as mitostatin). Trichoplein was initially identified as a meiosis-associated nuclear structural protein but was subsequently shown to participate in mitochondrial dynamics. This protein localizes to the mitochondrial outer membrane, where increased expression reduces mitochondrial motility, whereas its depletion enhances mitochondrial movement. These effects are thought to result from interactions that link mitochondria to actin intermediate filaments. The p.Arg493Trp variant identified in CFAP45 is located within this conserved the TPH domain, suggesting that it may influence the structural or functional properties of the protein. Schematic illustration of DNAH9 and CFAP45 domains is shown in figure 2.


#### Amino acid substitution effects
  Using SIFT, substitution at pos 493 from R to W in CFAP45 is predicted to AFFECT PROTEIN FUNCTION, and substitution at pos 355 from P to L in DNAH9is predicted to be TOLERATED. Using the PROVEAN analyzer, it is found that both CFAP45 R493W and DNAH9 P355L substitutions had deleterious effects with PROVEAN scores of -6.233 and -6.808, respectively.

  In the next step, the stability of mutant protein sequences was studied via the I-Mutant2.0 tool as well as protein structure. I-Mutant2.0 predicted a decrease in the stability of mutant sequences.

  Also, the effects of the amino acid substitutions were further evaluated using PHD-SNPg. Table II shows the results.


#### Structural consideration
  3D structure of CFAP45 protein was predicted by Swiss model according to CFAP45 AlphaFold DB model of CFA45_HUMAN (gene: CFAP45, organism: Homo sapiens [Human]) as template with protein data bank ID Q9UL and global model quality estimate (GMQE) 0.73. 3D structure of DNAH9 protein was predicted by Swiss model according to Dynein axonemal heavy chain 996 nm repeat of human respiratory doublet microtubule and associated axonemal complexes as template with protein data bank ID 8j07 and GMQE 0.82. GMQE is a quality indicator provided by SWISS-MODEL that ranges from 0–1, with higher values reflecting greater confidence in the predicted structure. This score is derived from both the quality of the target-template alignment and the structural characteristics of the selected template. Because GMQE is influenced by sequence coverage, models representing only part of the target protein generally receive lower scores than those with more complete coverage. 3D structure was determined for the mutated protein as well as the wild type. The orientation and the  σ  and  Ψ  angles of the mutant amino acids were calculated in comparison to the original amino acids.

  In CFAP45 wild type, the  σ  and  Ψ  angles for ARG493 were calculated -63.28 and -41.39, respectively, while in CFAP45 mutant type, the  σ  and  Ψ  angles for TRP493 were calculated -62.99 and -43.11, respectively.

  In DNAH9 wild type, the  σ  and  Ψ  angles for PRO355 calculated -64.72 and -30.37, respectively, while in DNAH9 mutant type, the  σ  and  Ψ  angles for LEU355 calculated -58.00 and -40.09, respectively.

  The tertiary structure of protein with Ramachandran plot's structure assessment is shown in figure 3A, and the position of native and mutant amino acids in 3D structure is illustrated in figure 3B.


## 4. Discussion
  We identified rare variants through WGS in this study. In the index case from a consanguineous family, 2 rare homozygous missense variants were detected in DNAH9 (c.1064C > T, p.Pro355Leu) and CFAP45 (c.1477C > T, p.Arg493Trp). Both genes are involved in sperm flagellar structure and ciliary function, and therefore represent biologically plausible candidates for further investigation in relation to the observed OAT phenotype. However, these variants are currently classified as variants of uncertain significance (VUS), and their clinical relevance remains to be established (Table I).

  DNAH9 encodes an axonemal dynein heavy chain that forms an important component of the outer dynein arm, which is essential for the generation of flagellar motility. Defects in dynein heavy chain proteins have been repeatedly implicated in impaired sperm motility and impaired flagellar function (22, 23). Given that cilia and flagella are highly conserved structures in various types of human cells and organs, pathogenic variants in DNAH9 may cause chronic respiratory diseases such as bronchiectasis and recurrent respiratory tract infections, as well as male infertility (24, 25).

  The identified p.Pro355Leu variant is located in the N-terminal region of DNAH9, a domain involved in dynein assembly and interaction with side chains. Although classified as a VUS, multiple in silico analyses predicted a deleterious effect and reduced protein stability, supporting a possible functional impact on sperm motility.

  In a previous study of 536 infertile men with primary ciliary dyskinesia, loss-of-function mutations in the DNAH9 gene were identified in 4 individuals from 3 unrelated families. Among these cases, one individual presented with asthenozoospermia, while fertility evaluation was not performed in the remaining 3 individuals due to their young age (24).

  In another study, whole-exome sequencing was performed in men with severe non-syndromic asthenozoospermia. The researchers identified heterozygous variants in DNAH9 that selectively impaired sperm motility without causing systemic ciliary dysfunction. These findings suggest that DNAH9 variants represent novel pathogenic contributors not only to syndromic severe asthenozoospermia, such as primary ciliary dyskinesia, but also to severe non-syndromic asthenozoospermia (22).

  CFAP45 is highly expressed in the testis and is involved in axonemal organization and ciliary function. Members of the CFAP family have been shown to maintain the structural integrity of the sperm flagellum, which is essential for motility (26–28).

  The R493W substitution replaces a positively charged arginine with a bulky hydrophobic tryptophan, representing a substantial physicochemical change. This alteration is predicted to disrupt local electrostatic interactions and potentially abolish stabilizing hydrogen bonds essential for protein-protein interactions within the axoneme. Such structural perturbation may interfere with the CFAP45 interaction network, including its functional association with dynein-related components, ultimately impairing flagellar movement and contributing to defective sperm motility.

  Previous studies have shown that CFAP52, together with CFAP45, is required for normal sperm motility in mice. Analyses using CFAP52 knockout models revealed that loss of CFAP52 results in asthenozoospermia and male infertility. It has also been shown that CFAP52 directly interacts with CFAP45, and deletion of CFAP52 led to a marked reduction in CFAP45 protein levels, which in turn disrupted dynein ATPase-driven microtubule sliding within the sperm flagellum. These findings highlight the importance of CFAP45 in maintaining axonemal integrity and sperm motility (29).

  Another study showed that CFAP45 is an essential factor for normal sperm motility and ciliary function. CFAP45 deficiency in humans and animal models leads to a motile ciliopathy characterized by asthenospermia and, in some cases, laterality defects such as situs inversus or heterotaxy. Importantly, affected individuals often present with mild or absent respiratory symptoms and, therefore, do not meet the diagnostic criteria for primary ciliary dyskinesia, which suggests a predominant effect on sperm flagellar function (30).

  Genetic findings in this case suggest that the OAT phenotype may be due to the combined effects of multiple variants. The ACTRT1 missense variant (c.118G > A, p.Gly40Arg) is of particular interest given the role of ACTRT1 in acrosomal integrity and sperm head formation, as demonstrated in both human and animal studies (31).

  The FBXO24 variant (c.905G > A, p.Arg302His) affects a gene essential for spermiogenesis, with known functions in mRNA alternative splicing, mitochondrial organization, and flagellar development (32).

  Furthermore, the SPATA2 variant (c.1159G > A, p.Gly387Arg), although currently classified as a VUS, affects a gene with significantly higher expression levels in the testis and has been implicated in Sertoli cell function and germ cell survival through TNF signalling pathways (33).

  The IGF2R variant (c.1810G > A, p.Gly604Ser) may indirectly influence spermatogenesis through IGF-related pathways associated with oxidative stress and testicular homeostasis (34).

  Finally, the GIT1 variant (c.176C > T, p.Thr59Met), a gene involved in cytoskeletal organization and intracellular signalling, may further contribute to defects in sperm development and motility (35).

  Therefore, these variants may contribute to the development of the OAT phenotype by perturbing key molecular pathways involved in spermatogenesis and sperm function, underscoring their potential pathogenic relevance in this case.

  However, additional functional studies and validation in larger cohorts are required to clarify the biological and clinical significance of these findings. Although WGS was performed in 7 men with OAT, the primary findings were derived from a single genetically informative case. In addition, the identified variants are currently classified as VUS according to American College of Medical Genetics and Genomics criteria, and no functional assays or segregation analyses were available to confirm their pathogenicity. Furthermore, DNA samples from additional family members were unavailable, limiting further evaluation of the inheritance pattern of the identified variants.


## 5. Conclusion
  This study highlights the potential utility of WGS in identifying rare candidate variants potentially associated with OAT. We identified 2 rare homozygous missense variants in DNAH9 and CFAP45, both of which encode proteins with established roles in axonemal structure and sperm flagellar motility. Additional variants identified in genes involved in spermiogenesis, acrosomal integrity, Sertoli cell function, intracellular signalling, and testicular homeostasis suggest that the OAT phenotype in this case may arise from the combined effects of multiple genetic alterations rather than a single causative variant. Overall, our findings expand the spectrum of candidate genes associated with OAT. Further functional validation and studies in larger cohorts will be essential to clarify the pathogenic relevance of these variants and their potential implications for genetic diagnosis and personalized management of male infertility.


## Data Availability
  Data supporting the findings of this study are available upon reasonable request from the corresponding author.


## Author Contributions
  S. Sadeghzadeh designed the study, drafted the manuscript, prepared samples, reviewed patients' medical histories, and contributed to data interpretation. A. Malcher data interpretation and assisted in manuscript editing and finalization, performed gene selection for WGS, and contributed to data interpretation. R. Ebrahimi Askari prepared patient samples and contributed to data interpretation. F. Sefid performed protein structure modeling and assisted in interpreting variant effects. R. Ibrahim interpreted molecular data and assisted in manuscript editing and finalization. K. Pastuszak and A. Srivastava performed bioinformatics analyses. M. Dehghani contributed to patient selection and genetic data collection. S. Vahidi recruited patients and conducted clinical evaluations as an andrologist. M. Lotfi assisted in data interpretation. N. Ghasemi coordinated the study, supervised the project, and contributed to genetic data collection and interpretation. M. Kurpisz coordinated the study, supervised the project, and contributed to manuscript finalization. All authors have read and approved the final version of the manuscript.

  2 corresponding authors were designated due to the collaborative nature of this study between the Yazd Reproductive Sciences Institute, Yazd, Iran and the Institute of Human Genetics, Polish Academy of Sciences, Poland, with joint supervision and coordination of the project.


## Conflict of Interest
  The authors declare that there is no conflict of interest.


## Acknowledgements
  We thank all the authors for their collaboration and contributions. Our sincere appreciation also goes to the patients for their participation. This work was supported by the National Science Center in Poland, (Grant no.: 2020/37/B/NZ5/00549) (to MK). KITE artificial intelligence assistant was used exclusively for grammar checking.