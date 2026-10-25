## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence; no assessment of formatting or editorial style beyond Nature-style criteria
- **Shared manuscript claim summary** The authors propose a simulation-free method (graph-driven sampling, GDS) to generate a basis set for constructing Koopman models of protein folding, eliminating the need for extensive molecular dynamics (MD) simulations in basis construction. They demonstrate this on a 2D model and the WW domain protein, claiming improved variational estimates of folding timescales and identification of kinetic traps.
- **Visible evidence base** Methods descriptions, results for 2D model and WW domain, comparisons to prior work, supplementary material referenced but not provided
- **Missing materials affecting confidence** Supplementary figures and tables (Figure S2, SI methods for lagtime selection, NTL9 results, Q-based comparisons), full MD trajectory details, code availability, and detailed parameter choices for GDS and Koopman fitting

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially impactful idea: using a graph-based, simulation-free approach to construct basis sets for Koopman models of protein folding. The 2D proof-of-concept is well described and supports the core hypothesis. However, the WW domain application, while promising, raises several concerns regarding the validity of the kinetic estimates, the interpretation of the identified "kinetic trap," and the generalizability of the approach. The reliance on existing ANTON MD data for parameterization, while pragmatic, limits the claim of being "simulation-free" in a practical sense. The manuscript is clearly written and accessible, but the evidence as presented is insufficient to fully establish the superiority or broad utility of the method over existing approaches.
- **Who would be interested in the results, and why** Computational biophysicists and chemists working on protein folding, Markov state models, and enhanced sampling. Researchers developing new methods for kinetic model construction that aim to reduce computational cost. The work may also interest method developers in the Koopman operator and dynamical systems community.
- **Major strengths** 1) The core idea is novel and addresses a real bottleneck in MSM construction (basis selection without MD). 2) The 2D model provides a clear, controlled demonstration of the concept. 3) The use of the SCH metric is physically motivated and appears to offer advantages over simpler metrics. 4) The identification of a kinetic trap in the WW domain, if validated, is a significant finding. 5) The manuscript is generally well-written and accessible to a broad audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation of kinetic trap), R1-M2 (simulation-free claim), R1-M3 (comparison to prior work), R1-M4 (generalizability).
- **Assessment against Nature-style criteria** **Originality:** High. The concept of using GDS for basis construction is novel and distinct from existing MD-based or order-parameter-based approaches. **Scientific importance:** Potentially high, as it addresses a fundamental computational bottleneck in studying protein dynamics. However, the importance is contingent on the robustness and generalizability of the method, which are not fully established here. **Interdisciplinary readership:** Moderate. The work is primarily of interest to computational chemists and biophysicists; the broader biological or chemical community may find the technical details less accessible. **Technical soundness:** The 2D model is sound. The WW domain application is suggestive but has unresolved issues regarding the interpretation of the kinetic trap and the comparison to prior work. **Readability for nonspecialists:** The abstract and introduction are accessible, but the methods and results sections are dense and require specialist knowledge. Overall, the manuscript has strong potential but requires substantial revision and additional evidence to meet the high bar for a Nature-style publication.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the current evidence does not fully establish the method's validity and superiority. The authors must address the concerns regarding the kinetic trap, the practical scope of the "simulation-free" claim, and the robustness of the comparison to prior work.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of interpretation
- **Claim pointer** The manuscript claims that the GDS-constructed Koopman model "definitively identifies a 'kinetic trap' within the folding pathway(s) of the FIP35 WW domain which previous conventional VAMP-based approaches struggled to resolve."
- **Evidence pointer** Results and Discussion, WW Domain section, Figure 4 and associated text; location not provided
- **Concern** The identification of the "kinetic trap" is a central result, but the evidence presented is not sufficient to support the claim of "definitive" identification. The interpretation relies on visual inspection of free energy surfaces and contact map averages. It is not clear how the authors distinguish a true kinetic trap (a metastable state with a significant residence time) from a transient, non-committal intermediate. The manuscript does not provide quantitative metrics such as state populations, mean first passage times into and out of the trap, or a comparison of the trap's stability relative to thermal fluctuations. Furthermore, the claim that previous methods "struggled to resolve" this trap is not substantiated with a direct comparison of the resolved free energy surfaces or state decompositions from prior work.
- **Why it matters** The identification of a novel kinetic trap is a key selling point of the method. If this interpretation is not robust, the primary advantage of the GDS approach over existing methods is weakened. A definitive claim requires quantitative evidence of metastability and a clear demonstration that the trap is not an artifact of the basis set or the analysis procedure.
- **Resolution test** The authors should provide quantitative evidence of the trap's metastability, such as: (1) the population of the trap state from the MSM; (2) the residence time or mean first passage time to escape the trap; (3) a comparison of the free energy barrier separating the trap from the unfolded and folded states; (4) a direct comparison of the free energy surface and state decomposition obtained from the GDS-based model with that from a conventional MSM built on the same ANTON data, to demonstrate the claimed improvement in resolution.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim accuracy
- **Claim pointer** The title and abstract state the method is "Simulation-Free" and that it "does not rely on extensive, computationally demanding MD data for configuration space partitioning."
- **Evidence pointer** Title, Abstract, Introduction; location not provided
- **Concern** The claim of being "simulation-free" is misleading. While GDS itself does not generate MD trajectories, the method's validation and parameterization for the WW domain rely entirely on the existing ANTON MD dataset. The kinetic parameters (timescales) are extracted by projecting this MD data onto the GDS-generated basis. The method is therefore not "simulation-free" in a practical sense; it is "MD-basis-construction-free." This distinction is crucial. The authors do acknowledge this in the conclusion, but the title and abstract overstate the case. This could mislead readers about the method's true requirements and potential applications.
- **Why it matters** The primary claim of novelty and utility is the removal of the MD bottleneck. If the method still requires MD data for any meaningful kinetic output, its advantage is reduced to a pre-processing step. The claim must be accurately scoped to avoid overstating the method's capabilities.
- **Resolution test** The authors should revise the title and abstract to accurately reflect the method's scope, e.g., "Simulation-Free Basis Construction for Koopman Models" or "MD-Free Basis Selection for Koopman Models." The text should clearly state that while GDS generates the basis without MD, the parameterization of the kinetic model (i.e., estimating transition probabilities) still requires MD data, and the method's primary advantage is in reducing the amount of MD data needed for basis selection, not eliminating it entirely.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that the GDS-based model "variationally improves folding time scale estimates" compared to previous studies, citing a folding time of 13.8 μs vs. 10.2 μs from prior work.
- **Evidence pointer** Results and Discussion, WW Domain section; location not provided
- **Concern** The comparison to prior work is not sufficiently detailed. The authors compare their folding time to a single value (10.2 μs) from previous studies, but it is unclear if this is an apples-to-apples comparison. The previous studies may have used different lag times, different state definitions, different analysis methods, or even different definitions of the "folding time." The manuscript does not provide a table comparing the key parameters of the different models (e.g., number of states, lag time, basis functions, clustering method). Without this context, the claim of "variational improvement" is not convincing. A variational improvement means that the estimated timescale is closer to the true value, but the true value is unknown. A longer timescale could also be an artifact of a poorly converged model or a different definition of the folded state.
- **Why it matters** The claim of variational improvement is a key quantitative result. If the comparison is not rigorous, the claim is unsupported. The authors need to demonstrate that the difference in timescales is significant and that it arises from the quality of the basis set, not from other methodological differences.
- **Resolution test** The authors should provide a detailed comparison table (in the main text or SI) listing the model parameters for their GDS-based model and the prior models they compare against. They should also discuss the uncertainty in their estimate (e.g., via bootstrapping) and the sensitivity of the result to the choice of lag time and basis function parameters. A more robust demonstration would be to show that their model converges to a stable timescale with fewer basis functions than a conventional model built on the same data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript suggests the method is "quite general" and "could equally be applied to protein–protein interaction networks, drug–protein binding, protein misfolding, and other complex transient biophysical processes."
- **Evidence pointer** Conclusion; location not provided
- **Concern** The generalizability claim is not supported by the evidence. The method is demonstrated on a single, small protein (WW domain, 35 residues) and a 2D toy model. The success of GDS relies on the ability to generate a connected path of physically plausible intermediate contact maps between unfolded and folded states. For larger proteins or more complex processes (e.g., binding), the contact map space becomes vastly larger and the GDS optimization may struggle to find relevant paths. The manuscript does not discuss the computational scaling of GDS with system size or the potential challenges in applying it to more complex systems.
- **Why it matters** The potential impact of the method depends on its applicability to a wide range of problems. If the method only works for small, simple proteins, its significance is limited. The authors should either provide evidence of scalability or temper their claims about generalizability.
- **Resolution test** The authors should discuss the computational cost of GDS as a function of protein size and contact map complexity. They could also perform a proof-of-concept on a second, larger protein to demonstrate scalability. If this is not feasible, the claims of generalizability should be significantly softened.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, GDS algorithm description
- **Evidence pointer** Methods, Graph Driven Sampling section; location not provided
- **Issue** The description of the GDS algorithm is brief. The specific details of the Metropolis-Hastings updates, the cooling schedule, and the convergence criteria are not fully specified. The choice of the parameter k_cont = 0.05 for the WW domain is mentioned but not justified in detail.
- **Required correction** Provide a more detailed algorithmic description, including pseudo-code if possible. Justify the choice of k_cont and other key parameters, perhaps with a sensitivity analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Koopman model fitting
- **Evidence pointer** Methods, Markov Models in Contact-Map Space section; location not provided
- **Issue** The manuscript states that the Koopman model was fit using the "unbiased Koopman reweighting algorithm" implemented in the deeptime package. However, the specific parameters of the fitting procedure (e.g., regularization, number of basis functions used in the final model) are not provided.
- **Required correction** Provide the specific parameters used for the Koopman model fitting, or a reference to a configuration file or code repository where these are available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, WW Domain section
- **Evidence pointer** Results and Discussion, WW Domain section; location not provided
- **Issue** The text describing the free energy surfaces and the kinetic trap is somewhat terse. The figures are referenced, but the key features of the plots are not described in sufficient detail in the text.
- **Required correction** Expand the description of the figures, explicitly pointing out the features that support the interpretation of the kinetic trap and the different folding pathways.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, NTL9 section
- **Evidence pointer** Results and Discussion, Markov Model of NTL9 section; location not provided
- **Issue** The NTL9 results are only briefly mentioned and are relegated to the SI. Given that this is a second demonstration of the method's applicability, it would strengthen the paper to include at least a summary of the key findings in the main text.
- **Required correction** Include a brief summary of the NTL9 results in the main text, highlighting the key timescales and any differences from the WW domain results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction contains a typo: "Markov State Models (MSMs) have emerged as a powerful frameworkk" (extra 'k').
- **Required correction** Correct the typo.

## Risk / unsupported claims
- The claim of "definitively" identifying a kinetic trap is unsupported by the quantitative evidence provided.
- The claim of being "simulation-free" is overstated and misleading, as MD data is still required for kinetic parameterization.
- The claim of "variational improvement" over prior work is not rigorously established due to a lack of detailed comparison.
- The claim of generalizability to other biophysical processes is speculative and not supported by evidence.
- The performance of the GDS method for proteins larger than the WW domain is unknown and not discussed.