## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, technical soundness, structural interpretation, pharmacological validation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors report cryo-EM structures of the delta opioid receptor (δOR) bound to the peptide agonist DADLE, alone and in complex with positive allosteric modulators (PAMs) MIPS3614 and MIPS3983. They identify a lipid-facing allosteric binding site at the interface of transmembrane helices 2, 3, and 4, and propose that MIPS3614 stabilises the active receptor conformation through a hydrogen bond with N1313.35, a residue within the conserved sodium binding site. The mechanism is supported by mutagenesis, functional assays, MD simulations, and structure-guided optimisation yielding MIPS3983 with improved affinity.
- **Visible evidence base** Cryo-EM structures (δOR-DADLE at 2.0 Å; δOR-DADLE-MIPS3614 at 1.9 Å; δOR-DADLE-MIPS3983 at 1.9 Å), pharmacological assays (cAMP inhibition, β-arrestin 2 recruitment, mGsi recruitment, Nb33 recruitment), MD simulations, mutagenesis data, tissue assays (mouse colon), and SAR data for nine analogues
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; PDB accession codes not listed; validation statistics (FSC curves, model geometry) not shown; full SAR synthetic procedures not provided; raw data files not accessible

## Reviewer

### Overall assessment
This manuscript presents a technically impressive structural study of the delta opioid receptor in complex with a peptide agonist and positive allosteric modulators. The 2.0 Å and 1.9 Å cryo-EM reconstructions represent high-quality structural data that will be of significant interest to the GPCR community. The identification of a lipid-facing allosteric site at the TM2/TM3/TM4 interface, coupled with the proposed mechanism involving stabilisation of the active-state conformation of the conserved sodium binding site, is conceptually novel and mechanistically plausible. The combination of structural, pharmacological, computational, and medicinal chemistry approaches provides a comprehensive validation strategy. However, several technical concerns need to be addressed, particularly regarding the interpretation of the N1313.35 rotamer change, the lack of clear density for BMS-986187, the selectivity data interpretation, and the statistical rigour of some functional assays. The manuscript is well-written and will appeal to a broad readership, but the current evidence does not fully establish all claims as presented.

### Who would be interested in the results, and why
Structural biologists studying GPCRs, particularly opioid receptors, will find the high-resolution structures valuable. Pharmacologists working on allosteric modulation of GPCRs will be interested in the proposed mechanism linking the allosteric site to the sodium binding pocket. Medicinal chemists pursuing opioid receptor drug discovery will benefit from the structure-guided optimisation data. Researchers studying the therapeutic potential of δOR in pain and gastrointestinal disorders will find the native tissue data relevant. The work also has broader relevance to the field of biased agonism and allosteric regulation of class A GPCRs.

### Major strengths
1. High-resolution cryo-EM structures (1.9–2.0 Å) of δOR in multiple functional states, representing a technical achievement
2. Identification of a previously uncharacterised lipid-facing allosteric binding site with clear structural definition
3. The proposed mechanism linking PAM binding to stabilisation of the active-state sodium site conformation is conceptually novel
4. Comprehensive validation through mutagenesis, multiple functional readouts, MD simulations, and native tissue assays
5. Structure-guided optimisation yielding a compound with improved affinity provides translational relevance
6. The manuscript is clearly written and the figures are well-organised

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation
- **Claim** "MIPS3614 stabilizes the active receptor conformation through a critical hydrogen bond with residue N1313.35 in the conserved sodium binding site"
- **Evidence pointer** Figure 5a, Results section "Molecular mechanism of positive allosteric modulation"
- **Concern** The manuscript proposes that the hydrogen bond between MIPS3614 and N1313.35 is critical for the allosteric mechanism, but the evidence for this specific interaction being causal rather than correlative is not fully established. The N1313.35D mutation abolishes PAM activity, but this residue also coordinates the sodium ion in the inactive state. The observed 5.5 Å rotamer change of N1313.35 between inactive and active states may be a consequence of receptor activation rather than a specific effect of PAM binding. The MD simulations show stabilisation of the outward rotamer in the presence of PAM, but the simulations are based on the PAM-bound structure, creating potential circularity. The manuscript does not provide sufficient control experiments to distinguish whether the hydrogen bond is the primary driver of allosteric modulation or one of several contributing interactions.
- **Why it matters** The central mechanistic claim of the paper rests on this specific interaction. If the hydrogen bond is not the primary determinant of allosteric modulation, the proposed mechanism would need substantial revision. The distinction between stabilisation of an active-state conformation versus direct perturbation of the sodium site has implications for understanding how this class of PAMs works and for structure-based drug design.
- **Resolution test** Provide additional mutagenesis data targeting the hydrogen bond acceptor/donor pair more specifically (e.g., N1313.35Q to preserve hydrogen bonding capacity but alter geometry, or N1313.35D with compensatory mutations in the PAM). Alternatively, perform MD simulations with the hydrogen bond disabled (e.g., by modifying the ligand) to demonstrate that the rotamer stabilisation is lost. A structure of an inactive-state PAM complex would also help establish whether PAM binding alone can induce the conformational change.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Pharmacological validation
- **Claim** "Both PAMs exhibited robust agonism due to high signal amplification, which made it difficult to fit an allosteric model to the data" (cAMP assays) and "Both PAMs exhibited similar levels of functional cooperativity (αβ = 5-7) and low levels of PAM agonism (τB = 0.1-1) across all recruitment assays"
- **Evidence pointer** Figure 2b, 2h, 2f, 2m
- **Concern** The manuscript reports that PAM agonism was observed in cAMP assays but could not be quantified due to signal amplification. This is a significant limitation because it means the intrinsic efficacy of these PAMs is not well characterised. The authors state that PAM agonism was low in recruitment assays, but the relationship between the observed agonism and the allosteric mechanism is not fully explored. If these compounds have significant intrinsic efficacy, they are not pure PAMs, which has implications for the proposed mechanism and for therapeutic development. The manuscript does not discuss whether the observed agonism is mediated through the same allosteric site or through a different mechanism.
- **Why it matters** The distinction between PAMs with and without intrinsic efficacy is pharmacologically important. Compounds with intrinsic efficacy may cause receptor desensitisation and tolerance, which would undermine the proposed therapeutic advantage of PAMs over orthosteric agonists. Understanding the degree of intrinsic efficacy is also important for interpreting the mechanism of action.
- **Resolution test** Perform additional experiments to quantify the intrinsic efficacy of MIPS3614 and MIPS3983 in a system with lower receptor reserve, or use a constitutively active receptor mutant to assess efficacy independent of agonist stimulation. Alternatively, provide a more detailed analysis of the agonism observed in cAMP assays, including whether it is blocked by a neutral allosteric ligand or by the N1313.35D mutation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity and specificity
- **Claim** "MIPS3614 showed no significant PAM activity at κOR, M4 mAChR or SSTR2 in a mini-Gsi recruitment assay, while modest PAM activity was observed at µOR"
- **Evidence pointer** Supplementary Figure 9d–f
- **Concern** The selectivity data are presented in a supplementary figure that is not provided in the manuscript text. The modest PAM activity at µOR is acknowledged but not quantified or discussed in detail. Given that the allosteric binding site is largely conserved across opioid receptor subtypes, the structural basis for the observed selectivity is not clearly explained. The manuscript mentions that the A1233.27I difference could cause steric clashes, but this is not experimentally tested. The selectivity data are important for the therapeutic claims, but the current presentation is insufficient to evaluate the degree of selectivity.
- **Why it matters** The therapeutic potential of δOR PAMs depends on their selectivity over µOR, given the abuse liability of µOR activation. If MIPS3614 has significant PAM activity at µOR, this could limit its therapeutic utility. The manuscript claims that the binding site is conserved, which raises questions about how selectivity is achieved.
- **Resolution test** Provide the full selectivity data with quantitative analysis, including concentration-response curves for MIPS3614 at µOR, κOR, SSTR2, and M4 mAChR. Test the A1233.27I mutation in the context of δOR to determine if this residue is responsible for the observed selectivity. Discuss the potential therapeutic implications of the observed µOR activity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigour
- **Claim** "MIPS3614 significantly reduced this response and increased the time interval between contractions" (colonic motility assays)
- **Evidence pointer** Figure 2p, 2q
- **Concern** The colonic motility data are presented with n = 5 biological replicates, and the significance is reported as P = 0.0496 for one comparison. This P value is barely below the conventional threshold of 0.05, and the manuscript does not report effect sizes or confidence intervals. The variability in whole-organ motility assays is typically high, and the small sample size raises concerns about the robustness of the conclusion. The manuscript also does not report whether the experimenter was blinded to treatment conditions.
- **Why it matters** The native tissue data provide important translational evidence for the therapeutic potential of MIPS3614. If the effect is marginal or not reproducible, this would weaken the therapeutic claims. The statistical rigour of the tissue assays needs to be sufficient to support the conclusions.
- **Resolution test** Increase the sample size, report effect sizes with confidence intervals, and provide information about blinding and randomisation. Consider using a more robust statistical approach, such as mixed-effects modelling, to account for repeated measures.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation
- **Claim** "We did not observe sufficient cryo-EM density to confidently model BMS-986187"
- **Evidence pointer** Results section "Allosteric site of the delta opioid receptor", Figure 3b
- **Concern** The inability to model BMS-986187 is presented as a null finding, but the manuscript does not provide sufficient detail about the experimental conditions used. The authors state that BMS-986187 was incubated with the complex prior to vitrification, but the concentration, incubation time, and temperature are not specified. It is possible that the compound did not bind under the conditions used, or that it bound with low occupancy. The manuscript also does not discuss whether alternative approaches (e.g., different detergent, nanodisc, or lipid bilayer conditions) were attempted. The subsequent claim that BMS-986187 binds the same site as MIPS3614 is based on mutagenesis data, but this is indirect evidence.
- **Why it matters** The structural characterisation of BMS-986187 binding would strengthen the claim that both compounds share the same binding site. The inability to obtain density for BMS-986187 could indicate that the compound has lower affinity or different binding kinetics, which would be relevant for understanding the structure-activity relationships.
- **Resolution test** Provide more detail about the experimental conditions used for the BMS-986187 complex. Consider using higher concentrations, different incubation conditions, or alternative sample preparation methods. If density is still not observed, discuss the limitations of the approach and provide additional evidence (e.g., competition binding, mutagenesis) to support the claim that both compounds share the same binding site.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2b–e, 2h–k
- **Evidence pointer** Figure 2
- **Issue** The concentration-response curves in Figure 2 are described in the text but the figure itself is not provided. The manuscript states that data were fit to the operational model of allosterism, but the quality of the fits is not shown. It would be helpful to see the actual curves with the fitted models overlaid, as well as the residuals or confidence intervals for the estimated parameters.
- **Required correction** Include the concentration-response curves with fitted models in the main figures or supplementary material, and provide confidence intervals for the estimated allosteric parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** MD simulation methods
- **Evidence pointer** Methods section "Computational chemistry"
- **Issue** The MD simulation methods are described in reasonable detail, but the force field parameters for the ligands are not specified. The manuscript states that GAFF2 was used for ligands, but the charge derivation method (e.g., RESP, AM1-BCC) is not mentioned. The simulation time (1 μs) and number of replicates (six) are stated, but the convergence criteria and the analysis methods for the PCA and rotamer populations are not fully described.
- **Required correction** Provide additional details about ligand parameterisation, including the charge derivation method and any validation of the ligand parameters. Describe the convergence criteria for the simulations and the specific analysis methods used to generate the rotamer population plots and PCA results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of mutagenesis data
- **Affected element** Figure 4e–i
- **Evidence pointer** Figure 4
- **Issue** The mutagenesis data show that several mutations reduce PAM activity, but the manuscript does not clearly distinguish between mutations that affect PAM binding versus those that affect receptor function more broadly. For example, mutations that reduce surface expression (Figure 4h) may confound the interpretation of functional assays. The manuscript should clarify which mutations specifically affect PAM binding versus those that have more general effects on receptor function.
- **Required correction** Provide a more detailed analysis of the mutagenesis data, including the relationship between surface expression and functional responses. Consider normalising functional data to receptor expression levels where appropriate.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The manuscript does not explicitly discuss the limitations of the study. For example, the inability to obtain a structure with BMS-986187, the potential for the lipid environment to influence the allosteric site, and the limited selectivity data are not critically discussed. A more balanced discussion of the limitations would strengthen the manuscript.
- **Required correction** Add a paragraph discussing the limitations of the study and the remaining questions that need to be addressed in future work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not fully contextualise the findings within the broader literature on δOR allosteric modulation. The recent cryo-EM structure of BMS-986187 bound to µOR is mentioned in the Discussion, but the relationship between the δOR and µOR allosteric sites is not discussed in detail. A more thorough comparison with the µOR PAM structure would help readers understand the conserved and divergent features of these sites.
- **Required correction** Expand the Discussion to include a more detailed comparison with the µOR-BMS-986187 structure and other GPCR PAM structures, highlighting the conserved and unique features of the δOR allosteric site.

## Risk / unsupported claims
1. The claim that MIPS3614 stabilises the active receptor conformation through a specific hydrogen bond with N1313.35 is not fully established; the causal role of this interaction requires additional experimental support.
2. The claim that BMS-986187 binds the same allosteric site as MIPS3614 is based on indirect evidence (mutagenesis) and is not directly supported by structural data.
3. The selectivity data for MIPS3614 at other opioid receptor subtypes are presented in a supplementary figure that is not provided, making the claims difficult to evaluate.
4. The statement that "MIPS3614 effectively modulates δOR signalling in both recombinant systems and native tissues" is supported by the data presented, but the magnitude and clinical relevance of the effects are not quantified.
5. The claim that the allosteric site is "lipid-facing" is supported by the structural data, but the functional significance of this lipid-facing location is not experimentally tested.
6. The manuscript states that "structure-guided optimisation yields MIPS3983 with enhanced binding affinity and retained cooperativity," but the SAR data for all nine analogues are not fully presented, making it difficult to assess the structure-activity relationships.
7. The MD simulation results are described as supporting the proposed mechanism, but the specific simulation parameters, convergence criteria, and statistical analysis of the simulation data are not fully described, limiting the ability to evaluate the robustness of these findings.