## Review setup
- **Input scope** Abstract
- **Assessment boundary** Claims and evidence presented in the abstract only
- **Shared manuscript claim summary** The authors report the engineering of a GH42 β-galactosidase (Tn1577) from *Thermotoga naphthophila* RUK10 using consensus design and virtual binding energy screening, yielding a triple mutant (M10, H271Q/V357G/Q340E) with a 6.5-fold increase in lactose hydrolysis activity at 55°C. The mutant is claimed to achieve near-complete hydrolysis of raw whey lactose within 2 hours under mild conditions (52.7°C, pH 5.5, 2.9 U/mL), preserving whey protein integrity.
- **Visible evidence base** Abstract text only; no figures, tables, or supplementary data provided.
- **Missing materials affecting confidence** Full manuscript, including Methods, Results, Figures, Tables, Supplementary Information, and any raw data or statistical analyses.

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially impactful engineering strategy for improving a thermophilic GH42 β-galactosidase for whey lactose hydrolysis. The combination of consensus design and virtual screening is a rational approach, and the claimed 6.5-fold activity improvement is notable. However, the abstract lacks critical quantitative evidence to support the mechanistic claims and the reported performance metrics. The absence of any data on thermostability, kinetic parameters, and the statistical basis for the response surface methodology (RSM) optimization makes the current claims unverifiable. The mechanistic narrative, while plausible, is not supported by any presented data.
- **Who would be interested in the results, and why** Researchers in industrial enzymology, dairy science, and food biotechnology would be interested. The work addresses a practical bottleneck in lactose-free dairy processing by offering a potentially more efficient and thermostable enzyme that operates under mild conditions, preserving whey protein value. The engineering strategy itself may be of interest to protein engineers.
- **Major strengths** 
  - The synergistic engineering strategy (consensus design + virtual screening) is a rational and potentially generalizable approach for enzyme improvement.
  - The target application (whey lactose hydrolysis) is of clear industrial and environmental importance.
  - The claimed 6.5-fold activity improvement and near-complete hydrolysis in 2 hours are practically significant if substantiated.
- **Major Concerns**
  - **Concern ID** R1-M1
    **Severity** Major
    **Blocking** Yes
    **Axis** Data completeness and verification
    **Claim pointer** "mutant M10 achieves a remarkable 6.5-fold increase in lactose hydrolysis activity at 55 degrees C compared with the wild-type enzyme."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract provides no quantitative data to support this claim. No specific activity values (e.g., U/mg), kinetic parameters (kcat, Km), or statistical error bars are reported. The basis for the "6.5-fold" increase is unclear.
    **Why it matters** Without these data, the magnitude of improvement cannot be assessed, and the claim is unverifiable. The fold-change could be misleading if the wild-type activity is very low or if the measurement conditions are not standardized.
    **Resolution test** Provide the specific activity (U/mg) of wild-type and M10 at 55°C, along with standard deviations and number of replicates. Report Michaelis-Menten kinetic parameters (kcat, Km, kcat/Km) for both enzymes.
  - **Concern ID** R1-M2
    **Severity** Major
    **Blocking** Yes
    **Axis** Mechanistic support
    **Claim pointer** "Molecular dynamics (MD) simulations revealed that M10s performance is driven by 3 key structural alterations... This engineered rigidity introduces a beneficial kinetic trade-off: it drastically accelerates catalytic turnover by intentionally weakening substrate affinity..."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract presents a detailed mechanistic model (remodeled substrate tunnel, rigidified catalytic pocket, allosteric Q340E mutation, weakened substrate affinity) but provides no quantitative MD simulation data (e.g., RMSD, RMSF, binding free energy calculations, tunnel dimensions) to support these claims. The "beneficial kinetic trade-off" is a specific hypothesis that requires direct kinetic evidence (e.g., increased kcat, increased Km).
    **Why it matters** The mechanistic narrative is central to the paper's novelty and scientific interest. Without supporting data, it remains speculation. The claim of "weakened substrate affinity" is directly testable via Km measurement.
    **Resolution test** Provide key MD simulation results (e.g., RMSF plots, tunnel analysis, binding free energy from MM/GBSA). Report the Km and kcat values for wild-type and M10 to directly test the "weakened substrate affinity" and "accelerated turnover" claims.
  - **Concern ID** R1-M3
    **Severity** Major
    **Blocking** Yes
    **Axis** Industrial performance validation
    **Claim pointer** "Response surface methodology established ideal industrial parameters: 52.7 degrees C, pH 5.5, and an enzyme dosage of 2.9 U/mL. Under these conditions, M10 accomplishes near-complete lactose hydrolysis of raw whey within a brief 2-h window."
    **Evidence pointer** Abstract; location not provided
    **Concern** The abstract reports optimized parameters and a performance claim ("near-complete lactose hydrolysis") without any data. The RSM model fit (e.g., R², p-values), the actual hydrolysis percentage, and the experimental validation of the predicted optimum are not provided. The definition of "near-complete" is ambiguous.
    **Why it matters** The industrial applicability of the enzyme hinges on this claim. Without quantitative data (e.g., % lactose conversion, time course, reproducibility), the claim is not credible.
    **Resolution test** Provide the RSM model statistics (e.g., ANOVA table, R², lack-of-fit test). Report the actual lactose hydrolysis percentage (e.g., >95%) achieved under the optimized conditions, with error bars from triplicate experiments. Show a time-course of lactose hydrolysis.
- **Minor Comments**
  - **Concern ID** R1-m1
    **Severity** Minor
    **Axis** Clarity and terminology
    **Affected element** "home-discovered"
    **Evidence pointer** Abstract
    **Issue** The term "home-discovered" is informal and ambiguous. It is unclear if this means the enzyme was newly identified in the authors' lab or if it is a previously known enzyme from a public database.
    **Required correction** Replace with a standard term such as "newly identified," "previously uncharacterized," or provide a reference to its discovery.
  - **Concern ID** R1-m2
    **Severity** Minor
    **Axis** Readability for nonspecialists
    **Affected element** "anion-pi interaction"
    **Evidence pointer** Abstract
    **Issue** While a standard term in structural biology, "anion-pi interaction" may not be familiar to all readers in the dairy science community. The abstract should briefly explain its significance (e.g., "a stabilizing non-covalent interaction").
    **Required correction** Add a brief parenthetical explanation, e.g., "a stabilizing non-covalent interaction between a negatively charged residue and an aromatic ring."
  - **Concern ID** R1-m3
    **Severity** Minor
    **Axis** Data presentation
    **Affected element** "6.5-fold increase"
    **Evidence pointer** Abstract
    **Issue** The fold-change is reported without a baseline or error. It is unclear if this is the maximum activity or the activity under specific conditions.
    **Required correction** Specify the conditions (e.g., "at 55°C, pH 5.5, and 1 mM lactose") and report the absolute values with errors.

## Risk / unsupported claims
- The claim of a 6.5-fold activity increase is unsupported without specific activity or kinetic data.
- The entire mechanistic model (remodeled tunnel, rigidified pocket, allosteric regulation, kinetic trade-off) is unsupported without MD simulation data and kinetic parameters.
- The claim of "near-complete lactose hydrolysis" under optimized RSM conditions is unsupported without quantitative hydrolysis data and model statistics.
- The claim that the mild thermal regimen "prevents the thermal denaturation of other valuable whey components" is an inference not directly tested in the abstract.