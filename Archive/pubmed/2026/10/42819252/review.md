## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) with figure legends referenced but figures not provided; supplementary material referenced but not provided.
- **Assessment boundary** Technical soundness of the AF3-ReD method, validity of claims regarding enhanced conformational sampling, comparison against MSA subsampling baseline, and generalizability across protein classes.
- **Shared manuscript claim summary** The authors introduce AF3-ReD, a repulsive biasing potential applied during the diffusion denoising process of AlphaFold3, inspired by metadynamics, to enhance sampling of alternative protein conformations. They claim successful sampling of ligand-bound conformations for motor, kinase, and transporter proteins that default AF3 fails to capture, with improved precision and diversity relative to MSA subsampling.
- **Visible evidence base** Full text of methods, results narrative, and discussion; figure and table legends; no actual figures, tables, or supplementary data provided.
- **Missing materials affecting confidence** All figures (main and supplementary), all tables (including Tables S1–S5), supplementary methods, MD simulation details, and the actual numerical data supporting precision/diversity calculations. Without these, quantitative claims cannot be independently verified.

## Reviewer

- **Overall assessment** The manuscript presents a conceptually interesting and timely approach to a recognized limitation of AlphaFold3, namely its tendency to predict a single dominant conformational state. The idea of borrowing enhanced sampling concepts from MD simulations and applying them to diffusion-based generative models is well motivated and the implementation appears technically plausible. However, the evidence presented in the text alone is insufficient to fully evaluate the strength of the claims. The authors report successes across multiple protein classes, but the absence of figures, quantitative data, and supplementary information limits verification of the central claims. The comparison with MSA subsampling is a useful baseline, but the reported advantages of AF3-ReD require closer scrutiny, particularly regarding the parameter sensitivity and the biological relevance of the sampled states.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein structure prediction and conformational sampling would find this work directly relevant. Researchers developing diffusion-based generative models for biomolecular applications, including protein design, would also be interested in the methodological contribution. Additionally, structural biologists studying conformational transitions in motor proteins, kinases, and transporters, particularly those interested in ligand-induced conformational changes, would benefit from a tool that can sample alternative states. The work also speaks to the broader community interested in integrating AI-based structure prediction with enhanced sampling methodologies.

- **Major strengths** The manuscript addresses a well-recognized limitation of AlphaFold3 with a conceptually elegant solution that requires no retraining. The metadynamics-inspired approach is well justified and the implementation details are clearly described. The authors provide a thoughtful comparison with MSA subsampling, which is a relevant and commonly used baseline. The selection of diverse protein targets, including cases where conformational states were unresolved at the training cutoff, strengthens the generalizability claims. The discussion of limitations, particularly the failure on the E3 ubiquitin ligase complex and the side-chain sampling limitation, is honest and adds credibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that AF3-ReD "successfully samples multiple conformational states in the AF3 distribution, including ligand-bound conformations of motor, kinase, and transporter proteins, which are rarely captured by the default AF3 settings."
- **Evidence pointer** Figures 1–5, Tables S1–S5, Figures S1–S24; location not provided for specific data points
- **Concern** The central claim of successful conformational sampling across multiple protein classes is presented without the actual figures and quantitative data needed for verification. The text describes distributions, RMSD values, and precision/diversity metrics, but the numerical values and visual representations are not available in the provided material. For example, the claim that AF3-ReD predicts closed conformations of TF1β with RMSDs near 2 Å to the experimental structure is stated but not substantiated with the actual distribution plots or RMSD values.
- **Why it matters** The core contribution of this work is the demonstration that AF3-ReD enhances conformational sampling. Without access to the figures showing the conformational distributions, the RMSD plots, and the precision/diversity comparisons, the validity of this central claim cannot be assessed. The reader cannot determine whether the sampled conformations are truly distinct from the default AF3 predictions or whether the reported successes are robust across the parameter space.
- **Resolution test** Provide all main and supplementary figures with clear axis labels, legends, and statistical annotations. Include the numerical data for precision and diversity metrics with error bars from independent sampling runs. Show representative structures with ligand-binding site overlays for each protein class.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the repulsive force acting on the i-th Cα atom is smoothed over the adjacent n_smooth Cα atoms on each side" and that this smoothing is necessary because "the denoising process lacks constraints between adjacent atoms, such as covalent bonds."
- **Evidence pointer** Methods section, "Repulsive Biasing Potential in AlphaFold3 Diffusion Model (AF3-ReD)"; location not provided
- **Concern** The force smoothing approach is described but its necessity and effectiveness are not rigorously demonstrated. The authors state that raw repulsive forces are not effective at facilitating concerted motions, but no comparative data are shown between smoothed and unsmoothed forces. Furthermore, the choice of n_smooth = 10 is justified only by a statement that parameter dependence of a transporter protein was factored into the selection, without presenting the actual sensitivity analysis. The mechanism by which smoothing over 10 residues on each side preserves local structural integrity while enabling global conformational changes is not explained.
- **Why it matters** The force smoothing is a critical component of the method. If the smoothing is not properly validated, the method's success could be attributed to an arbitrary parameter choice rather than a principled design. The claim that AF3-ReD maintains high precision while increasing diversity depends on this smoothing being effective across different protein sizes and topologies. Without comparative data, the technical soundness of the core methodological innovation is not fully established.
- **Resolution test** Provide a systematic comparison of AF3-ReD performance with and without force smoothing, and with varying n_smooth values, for at least two protein targets. Show that the chosen n_smooth = 10 is optimal or near-optimal across targets, and explain the structural rationale for the smoothing length.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparison adequacy
- **Claim pointer** The authors claim that "AF3-ReD provides a promising approach to predicting dynamic conformational changes of proteins associated with ligand binding" and that it outperforms MSA subsampling in terms of precision and diversity.
- **Evidence pointer** Figures 5A–H, Figures S21; location not provided
- **Concern** The comparison between AF3-ReD and MSA subsampling is presented as a key result, but the comparison framework has potential limitations. The precision metric uses a threshold of 50% of the RMSD between the two stable endpoint states, which may be overly generous or restrictive depending on the protein. The diversity metric based on Shannon entropy of a 2D RMSD histogram is reasonable but the choice of reference structures and the bin width (0.2 Å) could influence the results. More importantly, the comparison does not appear to account for the computational cost of the two methods in the precision/diversity trade-off, even though the authors note that AF3-ReD has negligible computational overhead.
- **Why it matters** The claim that AF3-ReD is superior to MSA subsampling is a key selling point of the manuscript. If the comparison metrics are not robust or if the comparison does not fairly represent the trade-offs, the conclusion may be overstated. The authors do note that MSA subsampling can produce structurally degraded predictions at low MSA depths, which is a valid point, but the quantitative comparison should be carefully scrutinized.
- **Resolution test** Provide the full precision-diversity curves for both methods across the entire parameter range tested, with confidence intervals. Discuss the sensitivity of the conclusions to the choice of threshold and bin width. Consider reporting the computational cost explicitly in the comparison.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "AF3-ReD provides a promising approach to predicting dynamic conformational changes of proteins associated with ligand binding, which could be further extended to other diffusion-based generative models."
- **Evidence pointer** Results sections on motor, kinase, and transporter proteins; Discussion; location not provided
- **Concern** The generalizability claim is supported by results on five protein targets across three classes, but the selection is limited. The E3 ubiquitin ligase complex, which represents a larger multisubunit system, was not successfully sampled, and the authors acknowledge this limitation. The manuscript does not discuss what characteristics of a protein system make AF3-ReD likely to succeed or fail. The extension to other diffusion models is speculative and not supported by any preliminary data.
- **Why it matters** The broader impact of this work depends on its generalizability. If AF3-ReD only works for relatively small, single-domain proteins with well-defined open-closed transitions, its utility is more limited than the claims suggest. Understanding the failure modes and the system requirements would help the community apply the method appropriately.
- **Resolution test** Discuss the structural and dynamical features that correlate with AF3-ReD success or failure across the tested targets. If possible, include at least one additional target that represents a different type of conformational change or a larger complex to test the boundaries of the method.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equation 5 and associated text
- **Evidence pointer** Results section, "Repulsive Biasing Potential in AlphaFold3 Diffusion Model (AF3-ReD)"; location not provided
- **Issue** The description of the Gaussian repulsive potential width decreasing linearly over the denoising process is clear, but the relationship between the time variable t and the noise level σ_d(t) is not explicitly defined. The authors mention that the denoising process runs from t = 0 to t_max = 160, but the mapping between t and the noise schedule used in AlphaFold3 is not described.
- **Required correction** Clarify the relationship between the denoising time t and the noise level σ_d(t) in the AlphaFold3 diffusion process, and specify how the Gaussian width parameter interpolates between its initial and final values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, "Structure Prediction of Proteins"
- **Evidence pointer** Methods section; location not provided
- **Issue** The authors state that "no templates were used in any of the structure predictions" but do not specify whether the AlphaFold3 pipeline was run with its default settings for all other parameters, such as the number of diffusion steps, the random seed initialization, or the MSA depth for the default condition.
- **Required correction** Provide the complete list of AlphaFold3 parameters used for the default condition, including the number of diffusion steps, the random seed range, and any other relevant settings, to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Sampling precision and diversity calculations
- **Evidence pointer** Methods section, "Sampling Precision and Diversity"; location not provided
- **Issue** The authors report that four independent samplings were used to estimate the average and standard error of precision and diversity for some targets, but it is unclear whether this was done for all targets and all conditions. The number of independent runs for the default AF3 and MSA subsampling conditions is not explicitly stated.
- **Required correction** Clearly state the number of independent sampling runs for each condition and target, and report the standard errors for all precision and diversity values, not just for selected cases.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of the E3 ubiquitin ligase complex results
- **Evidence pointer** Results section, "Application of AF3-ReD to the E3 Ubiquitin Ligase Complex"; location not provided
- **Issue** The authors state that AF3-ReD "extended the conformational distribution toward the open state" but did not achieve RMSD below 5 Å from the experimental open structure. The discussion of why the method failed to capture the full conformational change is brief and does not explore potential reasons, such as the size of the complex, the nature of the conformational change, or the choice of RMSD as the collective variable.
- **Required correction** Expand the discussion of the E3 ubiquitin ligase complex failure to include a more detailed analysis of the structural features that may have limited the sampling, and discuss whether alternative collective variables or parameter settings could potentially overcome this limitation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion; location not provided
- **Issue** The manuscript mentions several independent works exploring similar directions but does not provide a detailed comparison of AF3-ReD with these approaches. The Discussion mentions Richman et al., Hori et al., and Xie et al. but does not clearly articulate the methodological differences and potential advantages of AF3-ReD over these methods.
- **Required correction** Provide a more detailed comparison with the related works, highlighting the specific methodological innovations of AF3-ReD and the situations in which it would be preferred over alternative approaches.

## Risk / unsupported claims
- The claim that AF3-ReD "successfully samples multiple conformational states" across protein classes cannot be fully verified without the figures and quantitative data.
- The claim that AF3-ReD achieves "high precision values of over 0.9" for all tested proteins is stated but not substantiated with the actual values.
- The claim that AF3-ReD's computational cost is "almost unchanged" relative to default AF3 is plausible but not quantified.
- The claim that AF3-ReD "could be further extended to other diffusion-based generative models" is speculative and not supported by any experimental evidence.
- The statement that the parameter set refined for TF1β "also worked well for OxT" is made without showing the actual results for the parameter sensitivity analysis on the transporter.
- The claim that AF3-ReD predicted conformations "along the transition pathway between the occluded and inward-open states" for OxT is not supported by the provided text alone, as the relevant figure is not available.
- The biological relevance of the "highly open" states predicted for PGK, which the authors suggest may correspond to SAXS-observed states, is presented as a possibility but not rigorously established.