## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive consistency based solely on the provided text; figures, tables, and supplementary data referenced but not directly examined
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations and Kirkwood–Buff theory to show that monosaccharides (glucose, mannose, xylose) differentially interact with the carbohydrate-binding module (CBM) and catalytic domain (CD) of Cel7A. The CBM is preferentially solvated by sugars, especially xylose, while the CD is preferentially hydrated. Localized sugar accumulation at the CD tunnel entrance and loops B2, B3, and A3 is proposed to explain reduced processivity, while CBM sugar binding is proposed to explain reduced association rate.
- **Visible evidence base** Methods descriptions, qualitative results narrative, references to Figures 1–9, Tables S1–S6, and supplementary figures; no numerical data, statistical analyses, or figure content directly visible
- **Missing materials affecting confidence** All figures, tables, supplementary information, simulation trajectory analyses, convergence assessments, and force field validation data; no quantitative values for Γ, KBI, MDDF peak heights, or occupancy/residence times are provided in the text

## Reviewer

- **Overall assessment** This manuscript addresses a relevant and timely question in biomass depolymerization: how monosaccharide inhibitors differentially affect the two functional domains of Cel7A. The combination of MD simulations with Kirkwood–Buff theory is appropriate and potentially powerful. However, the current text presents qualitative claims without the quantitative evidence needed to evaluate their robustness. The central distinction between CBM preferential sugar binding and CD preferential hydration is interesting, but the manuscript does not provide sufficient numerical detail, statistical uncertainty estimates, or convergence analyses to assess whether these conclusions are supported. The mechanistic interpretations linking simulation observables to experimental kinetic parameters (k_on, processivity) are plausible but require more careful argumentation and quantitative support.

- **Who would be interested in the results, and why** Researchers in enzymatic biomass conversion, cellulase engineering, and biofuel production would find these results relevant. The study addresses a practical problem—product inhibition of cellulases—and offers molecular-level hypotheses that could guide enzyme engineering or process design. Computational biophysicists interested in protein–carbohydrate interactions and solvation thermodynamics may also find the methodological approach of interest. The distinction between domain-specific inhibition mechanisms could inform rational design of more inhibitor-tolerant cellulase variants.

- **Major strengths**
  1. The study addresses a mechanistically important and practically relevant question: how different monosaccharides inhibit the two functional domains of Cel7A through distinct mechanisms.
  2. The combination of MD simulations with Kirkwood–Buff theory and MDDF analysis is methodologically sophisticated and appropriate for characterizing preferential solvation.
  3. The authors explicitly account for anomeric equilibria and validate additivity assumptions with mixed-anomer simulations, demonstrating careful attention to chemical detail.
  4. The interpretation connects simulation observables to experimentally measured kinetic parameters (k_on, processivity), providing testable hypotheses.
  5. The study covers a wide concentration range (0.1–2.0 mol L⁻¹) and multiple sugars, allowing comparative analysis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Our results reveal an unsuspected contrast in the solvation preferences of the two domains: while sugars are preferentially excluded from the CD, the CBM exhibits preferential sugar binding."
- **Evidence pointer** Figures 1–9, Tables S3; location not provided
- **Concern** The central claim of opposing solvation preferences between CBM and CD is presented qualitatively. No numerical values for Γ (preferential interaction parameter) are given in the text. The magnitude of the effect, its statistical significance across replicates, and its dependence on concentration are not quantified. The claim that the CD "preferentially excludes" sugars while the CBM "preferentially binds" them requires quantitative support showing that the Γ values are significantly different from zero and from each other, with appropriate uncertainty estimates.
- **Why it matters** This is the foundational claim of the paper. Without quantitative evidence, the reader cannot assess whether the observed differences are robust, biologically meaningful, or within statistical noise. The claim of an "unsuspected contrast" implies a notable effect size that must be demonstrated.
- **Resolution test** Provide numerical Γ values with standard errors for both domains across all concentrations and sugars. Include statistical tests showing that CBM Γ values are significantly positive and CD Γ values are significantly negative (or at least significantly different from each other). Show convergence of these values over simulation time.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretive validity
- **Claim pointer** "By more effectively occupying these key aromatic sites, xylose accumulation is consistent with a reduced availability of the CBM for anchoring onto the crystalline cellulose surface, offering a structural explanation for its greater impact on productive binding relative to mannose."
- **Evidence pointer** Figures 2, 4, 5; Tables S5, S6; location not provided
- **Concern** The manuscript proposes that sugar accumulation at CBM tyrosine residues (Y5, Y31, Y32) would interfere with cellulose binding, but no direct evidence is provided that sugar occupancy at these sites would competitively inhibit cellulose adsorption. The simulations are performed with free sugars in solution, not with cellulose present. The extrapolation from sugar accumulation at tyrosine residues in the absence of cellulose to reduced cellulose binding is speculative. The authors do not address whether the binding affinity of monosaccharides at these sites is sufficient to compete with the much larger cellulose chain, nor do they consider the relative thermodynamics of sugar versus cellulose binding.
- **Why it matters** The proposed mechanism for reduced k_on depends on this competitive interference argument. If sugar binding at the CBM face does not actually compete with cellulose binding under relevant conditions, the interpretation collapses. The manuscript needs to either provide thermodynamic estimates of competitive binding or soften the claim to a hypothesis.
- **Resolution test** Provide estimates of sugar binding affinity at the CBM tyrosine sites (e.g., from occupancy data or free energy calculations) and compare with known cellulose binding affinity. Alternatively, perform simulations with both cellulose and sugars present to directly test competition. At minimum, discuss the relative affinities and acknowledge the speculative nature of the competitive mechanism.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** "We employed all-atom molecular dynamics simulations combined with the Kirkwood–Buff solution theory."
- **Evidence pointer** Methods section; location not provided
- **Concern** The manuscript does not report essential simulation quality metrics. No RMSD convergence plots, no block-averaging or autocorrelation analyses for the KBI calculations, no assessment of finite-size effects beyond a brief mention, and no validation that the 20 ns equilibration was sufficient for the system to reach equilibrium. The KBI calculations are notoriously sensitive to finite-size effects and convergence; the authors mention using a bulk region between 10–15 Å but do not demonstrate that this choice yields converged results. Additionally, the CHARMM36m force field is used for protein and TIP3P for water, but the sugar force field (ADD) is less established; no validation of sugar conformational sampling or comparison with experimental data is provided.
- **Why it matters** The reliability of the thermodynamic conclusions depends entirely on the quality and convergence of the simulations. Without these quality metrics, the reader cannot assess whether the reported preferential interaction parameters are converged, accurate, or artifacts of insufficient sampling or force field inaccuracies.
- **Resolution test** Provide convergence plots for Γ and KBI values as a function of simulation time. Report block-averaged standard errors. Show that results are robust to the choice of bulk region boundaries. Include validation of the ADD sugar force field (e.g., comparison of sugar conformational populations with experimental NMR data or quantum calculations).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative support for mechanistic claims
- **Claim pointer** "Even at low sugar concentrations, the WASA of these tryptophans decreases by more than 50%"
- **Evidence pointer** Figure 6b–d; location not provided
- **Concern** The claim of a >50% reduction in WASA at tryptophan residues is striking but is presented without numerical values, error estimates, or concentration dependence details. It is unclear what "low sugar concentrations" means quantitatively, whether this effect is specific to tryptophans or general to the protein surface, and whether the WASA reduction is due to direct sugar binding or to general changes in protein conformation or hydration. The relationship between WASA reduction and impaired catalytic function is asserted but not quantitatively linked.
- **Why it matters** This is a key mechanistic claim linking sugar presence to impaired substrate interaction. Without quantitative details, the significance and specificity of the effect cannot be evaluated. The claim of >50% reduction is strong and requires robust statistical support.
- **Resolution test** Provide WASA values with standard errors for tryptophan residues and for control residues across concentrations and sugars. Show that the effect is specific to functionally relevant residues and not a global protein surface effect. Provide a statistical comparison between sugar types and concentrations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions
- **Claim pointer** "By reconciling broader solvation preferences with highly specific site interactions, our findings offer a picture of how glucose and hemicellulose-derived sugars inhibit Cel7A."
- **Evidence pointer** Conclusions section; location not provided
- **Concern** The simulations are performed on isolated CBM and CD domains, not on the full-length enzyme. The authors acknowledge this as a strategy to deconvolve domain-specific effects, but the implications for the full-length enzyme are not discussed. The linker region, which connects the two domains and may influence their relative orientation and dynamics, is absent. Additionally, the simulations are performed in simple sugar solutions without cellulose, lignin, or other components of the lignocellulosic biomass environment. The extrapolation to the complex industrial context is not adequately qualified.
- **Why it matters** The practical relevance of the findings depends on whether the domain-specific behaviors observed in isolation persist in the full-length enzyme and in realistic biomass environments. Without discussion of these limitations, readers may overinterpret the results.
- **Resolution test** Add a limitations paragraph discussing the potential effects of the linker, the absence of cellulose, and the simplified solution conditions. If possible, perform at least one simulation of the full-length enzyme with sugars to test whether the domain-specific behaviors are preserved.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "an unsuspected contrast" but does not provide any quantitative context. The term "unsuspected" is subjective and not necessary for a scientific abstract.
- **Required correction** Replace "unsuspected" with a more neutral descriptor such as "distinct" or "differential."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section; location not provided
- **Issue** The manuscript states that 20 independent replicates of 80 ns were run for CBM and 5 replicates of 1000 ns for CD, but does not report the total simulation time per system or the computational cost. The number of replicates differs substantially between domains, which may affect the statistical power of comparisons.
- **Required Correction** Report total simulation time per system and justify the different replication strategies for CBM versus CD.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive caution
- **Affected element** Results section on CD solvation
- **Evidence pointer** "Solvation properties of the Cel7A CD in sugar solutions"; location not provided
- **Issue** The statement that glucose shows "a markedly higher preference for the catalytic acid/base residue (E217) compared to mannose or xylose" is presented as a key finding, but the quantitative difference and its statistical significance are not reported.
- **Required Correction** Provide the numerical density values or interaction energies for E217 with each sugar, with uncertainty estimates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction cites several relevant studies but does not clearly position this work relative to previous computational studies of cellulase inhibition. The novelty of the Kirkwood–Buff approach for this system is asserted but not contextualized.
- **Required Correction** Add a brief paragraph in the introduction or discussion explicitly comparing the present approach and findings with prior computational studies of Cel7A inhibition.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Results; location not provided
- **Issue** The term "preferential binding" is used for the CBM and "preferential exclusion" for the CD, but the distinction between these terms and the operational definition used in the analysis is not clearly explained for readers unfamiliar with Kirkwood–Buff theory.
- **Required Correction** Add a brief explanation of what Γ > 0 and Γ < 0 mean physically in the context of protein–sugar–water ternary systems.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Quantitative values for Γ with error estimates are essential to support the central claim of opposing solvation preferences.
  - R1-M2: The competitive mechanism between sugar and cellulose binding at the CBM requires thermodynamic justification or direct testing.
  - R1-M3: Convergence and quality metrics for the simulations are necessary to establish the reliability of the thermodynamic calculations.

- **Assessment against Nature-style criteria**
  - **Originality**: The application of Kirkwood–Buff theory combined with MD simulations to dissect domain-specific inhibition of a cellulase is methodologically novel. The finding of opposing solvation preferences between CBM and CD, if robust, would be an original contribution. However, the conceptual framework of monosaccharide inhibition of cellulases is well established, and the novelty lies primarily in the molecular-level mechanistic detail.
  - **Scientific importance**: The question of product inhibition of cellulases is of significant practical importance for biofuel production. A molecular-level understanding of how different sugars inhibit different domains could inform enzyme engineering strategies. However, the importance is incremental rather than transformative, as the study provides mechanistic hypotheses rather than definitive experimental validation.
  - **Interdisciplinary readership**: The topic bridges enzymology, computational biophysics, and biofuel technology. The findings would be of interest to researchers in these fields. However, the manuscript is written primarily for a computational biophysics audience and may not be fully accessible to experimental enzymologists without additional context.
  - **Technical soundness**: The methodological approach is appropriate, but the manuscript currently lacks the quantitative detail and quality metrics needed to assess technical soundness. The force field choice for sugars (ADD) is less established than alternatives, and no validation is provided. The statistical treatment of the simulation data is not described.
  - **Readability for nonspecialists**: The manuscript is reasonably well organized, but the methods and results sections assume familiarity with Kirkwood–Buff theory and MD simulation analysis. The abstract is accessible, but the main text would benefit from more explicit explanations of key concepts and their biological relevance.

- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and the methodological approach is appropriate, but the manuscript in its current form does not provide sufficient quantitative evidence to establish the claims. The authors should provide numerical values with error estimates, convergence analyses, and a more careful discussion of the mechanistic interpretations. If these concerns are addressed, the manuscript could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim of "preferential exclusion" of sugars from the CD is not quantitatively supported in the text; no Γ values are provided.
- The claim that sugar accumulation at CBM tyrosine residues "masks" the cellulose-binding interface and explains reduced k_on is speculative without evidence of competitive binding.
- The claim that sugar-induced restriction of B3 loop flexibility "could potentially modulate product release or the forward progression of the cellulose chain" is presented as a mechanism without direct evidence linking loop dynamics to processivity.
- The statement that glucose shows "markedly higher preference" for E217 compared to other sugars is not quantitatively supported.
- The extrapolation from isolated domain simulations to full-length enzyme behavior is not adequately qualified.
- The relevance of concentrations up to 2.0 mol L⁻¹ to industrial conditions is acknowledged but not quantitatively contextualized; the authors note this exceeds typical conditions but do not discuss what the high-concentration behavior implies for lower, more relevant concentrations.