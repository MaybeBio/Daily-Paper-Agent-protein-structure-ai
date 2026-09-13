## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full manuscript, figures, tables, or supplementary materials were provided.
- **Shared manuscript claim summary** The authors identify four conserved non-active-site residues (S118, V120, L158, D159) in OXA-232 beta-lactamase and show, via alanine scanning, that S118 and D159 are essential for catalysis and structural integrity, while V120 and L158 modulate substrate-specific turnover. Bicarbonate rescue experiments suggest carbamylation dependence.
- **Visible evidence base** Abstract text only; no experimental data, kinetic parameters, spectra, or simulation outputs are visible.
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, supplementary information, raw kinetic data, circular dichroism spectra, molecular dynamics simulation details, and statistical analyses.

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting study on the role of non-active-site residues in OXA-232, a clinically relevant carbapenemase. The identification of S118 and D159 as essential, and V120 and L158 as modulatory, is a plausible advance. However, the abstract alone provides insufficient evidence to evaluate the rigor of the kinetic, structural, and simulation data. The claim of "deacylation-deficient" and "selective acylation defects" cannot be assessed without the actual stopped-flow or mass spectrometry data. The bicarbonate rescue experiment is intriguing but its interpretation is unclear from the abstract. The study's significance for rational drug design is overstated given the preliminary nature of the findings as presented.
- **Who would be interested in the results, and why** Researchers in antimicrobial resistance, beta-lactamase enzymology, and structure-guided drug design would be interested. The work could inform efforts to develop inhibitors that target non-active-site residues in OXA-48-like carbapenemases, a growing clinical threat.
- **Major strengths** 1. Addresses a genuine gap in understanding the role of non-active-site residues in OXA-48-like enzymes. 2. Uses a combination of alanine scanning, kinetics, spectroscopy, and simulations. 3. The bicarbonate rescue experiment is a clever approach to probe carbamylation dependence.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "Kinetic analysis with purified proteins revealed the reduction in catalytic efficiency of all the mutants compared to wild-type protein. Though the L158A and D159A mutated proteins become deacylation-deficient, the mutations S118A and V120A exhibited selective acylation defects without trapping intermediates."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The abstract claims specific mechanistic defects (deacylation deficiency vs. selective acylation defects) but provides no quantitative data (e.g., kcat, Km, kcat/Km values, pre-steady-state rate constants, or evidence of intermediate trapping). Without these data, the mechanistic distinction is unsubstantiated.
    - **Why it matters** The central mechanistic conclusion of the paper rests on distinguishing acylation from deacylation defects. If the kinetic data are not robust or the methods are inappropriate, the entire functional interpretation collapses.
    - **Resolution test** Provide the full kinetic parameters (kcat, Km, kcat/Km) for wild-type and all mutants against a panel of substrates. For the deacylation-deficient claims, provide evidence of acyl-enzyme intermediate accumulation (e.g., by mass spectrometry or stopped-flow fluorescence). For the acylation-defective claims, provide pre-steady-state data showing reduced acylation rates.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** "It is evident from circular dichroism spectroscopy and molecular dynamics simulations that OXA-232S118A, OXA-232V120A, OXA-232L158A and OXA-232D159A nearly retained their secondary structures and compactness."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The abstract states that the mutants "nearly retained" secondary structure and compactness, but provides no quantitative metrics (e.g., mean residue ellipticity values, RMSD, Rg from simulations). The phrase "nearly retained" is vague and could mask significant local perturbations that affect function.
    - **Why it matters** The claim that the mutations do not globally disrupt structure is critical to attributing functional changes to specific catalytic roles rather than to protein misfolding. Without quantitative evidence, this conclusion is unsupported.
    - **Resolution test** Provide CD spectra with deconvolution of secondary structure content (e.g., % alpha-helix, beta-sheet) for wild-type and all mutants. Provide MD simulation data including RMSD, RMSF, and radius of gyration over time, with statistical comparisons.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Interpretation
    - **Claim pointer** "Interestingly, bicarbonate supplementation partially rescued the lost activities in soluble mutants, underscoring the carbamylation dependence."
    - **Evidence pointer** Abstract; location not provided
    - **Concern** The abstract does not specify which mutants showed rescue, to what extent, or whether the rescue was statistically significant. The mechanism of rescue (e.g., restoring the carbamylated lysine) is not demonstrated.
    - **Why it matters** The bicarbonate rescue experiment is presented as a key finding, but without details on the magnitude and specificity of rescue, its significance is unclear. It could be a non-specific effect.
    - **Resolution test** Provide quantitative rescue data (e.g., fold-change in activity or MIC) for each mutant with and without bicarbonate, including statistical analysis. Show that rescue is specific to carbamylation-dependent activity (e.g., by using a non-carbamylatable control).

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract; location not provided
    - **Issue** The phrase "causes of the extensive of beta-lactam resistance" is grammatically awkward and unclear.
    - **Required correction** Revise to "a cause of extensive beta-lactam resistance" or "contributes to extensive beta-lactam resistance."

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract; location not provided
    - **Issue** The abstract does not state the number of replicates or statistical methods used for any experiment.
    - **Required correction** Include a brief statement of statistical approach (e.g., "Data are mean ± SD from three independent experiments") in the abstract or full manuscript.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Overstatement
    - **Affected element** Abstract text
    - **Evidence pointer** Abstract; location not provided
    - **Issue** The final sentence claims the study "providing significant resources in rationally designing future therapeutics." This is an overreach based on the data presented in the abstract.
    - **Required correction** Tone down the claim to something like "providing insights that may inform future inhibitor design."

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative kinetic data to support mechanistic claims) and R1-M2 (lack of quantitative structural data to support the claim of retained structure) are blocking. Without these, the core conclusions are not established.

- **Assessment against Nature-style criteria**
    - **Originality** Moderate. The concept of probing non-active-site residues in OXA-48-like enzymes is not entirely novel, but the specific focus on S118, V120, L158, and D159 in OXA-232 is a reasonable extension of existing work.
    - **Scientific importance** Potentially high, if the mechanistic distinctions are robust. Understanding how non-active-site residues modulate activity could inform inhibitor design. However, the importance is diminished if the claims are not well-supported.
    - **Interdisciplinary readership** Limited. The work is primarily of interest to the beta-lactamase and antimicrobial resistance community. The abstract does not present findings that would broadly appeal to a general biological or chemical audience.
    - **Technical soundness** Cannot be assessed from the abstract alone. The claims require rigorous kinetic, structural, and computational evidence that is not visible.
    - **Readability for nonspecialists** The abstract is reasonably clear for a specialist audience but uses jargon (e.g., "deacylation-deficient," "carbamylation dependence") that would be opaque to nonspecialists.

- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis, but the key mechanistic claims (acylation vs. deacylation defects, structural retention, bicarbonate rescue) are unsupported by the visible data. A full manuscript with quantitative data is required for evaluation. Supportive if technical concerns are resolved.