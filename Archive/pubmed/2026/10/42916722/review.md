## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material provided
- **Shared manuscript claim summary** The authors report that ring-flip dynamics of a buried phenylalanine in cytochrome C are non-Markovian, governed by memory-dependent friction arising from delayed steric responses of adjacent cavity residues, and exhibit fractional viscosity dependence despite full burial of the ring.
- **Visible evidence base** Abstract text only; no numerical data, simulation details, or statistical analyses are available
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, convergence criteria, error estimates, comparison with experimental rates, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting hypothesis linking protein breathing to non-Markovian ring-flip dynamics, but the evidence base is insufficient to evaluate the validity of the central claims. The authors invoke advanced rate theories and enhanced sampling methods without providing any quantitative results, error analysis, or methodological justification. The fractional viscosity dependence claim is intriguing but unsupported by any data in the supplied material. The work may be of interest to computational biophysicists, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Computational biophysicists and physical chemists studying protein dynamics, particularly those interested in memory effects in condensed-phase reactions, ring-flip kinetics in proteins, and the role of solvent viscosity in buried residue dynamics. Experimentalists using NMR relaxation to probe aromatic ring flips may also find the predictions testable.
- **Major strengths** The conceptual framing connecting protein breathing to memory-dependent friction is timely and potentially significant. The use of Grote-Hynes theory and reactive flux formalism is appropriate for addressing non-Markovian effects. The prediction of fractional viscosity dependence for a buried ring is a nontrivial and falsifiable claim.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: the concept of memory-dependent friction in ring flips is not entirely new, but the specific application to a buried residue in cytochrome C with fractional viscosity dependence is a fresh angle. Scientific importance: potentially high if the claims are quantitatively supported, as it would link solvent properties to internal protein dynamics in a nonintuitive way. Interdisciplinary readership: the topic bridges physical chemistry, biophysics, and molecular simulation, but the abstract is too sparse to attract broad readership. Technical soundness: cannot be assessed from the abstract alone; the absence of any quantitative results is a critical gap. Readability for nonspecialists: the abstract is reasonably clear but relies on jargon (non-Markovian, Grote-Hynes theory) without sufficient context for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the full manuscript provides quantitative rate estimates, error bars, convergence checks, and a clear demonstration that the memory kernel is indeed the dominant factor controlling the flip rate.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to "accurately estimate the ring-flip rates" using enhanced sampling and advanced rate theories.
- **Evidence pointer** Abstract only; location not provided
- **Concern** No numerical values, error estimates, or comparison with experimental or previous computational rates are provided. The term "accurately" is unsubstantiated without any quantitative benchmark.
- **Why it matters** The central claim of the paper rests on the accuracy of the rate estimates. Without numbers, the reader cannot judge whether the rates are physically reasonable or whether the enhanced sampling converged.
- **Resolution test** Provide the computed flip rates with statistical uncertainties, compare them to known experimental values (if available) or to results from unbiased simulations, and state the convergence criteria used for the enhanced sampling runs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that "memory-dependent friction" arises from "combined steric hindrance" and "delayed response" of adjacent residues.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract asserts a mechanistic interpretation without presenting any data on the time-dependent friction kernel, the correlation functions of the cavity residues, or the timescales of the delayed response. No evidence is shown that the dynamics are indeed non-Markovian in the sense claimed.
- **Why it matters** The non-Markovian character is the core conceptual novelty. If the memory kernel is not explicitly computed or characterized, the claim is speculative rather than demonstrated.
- **Resolution test** Show the computed friction kernel or velocity autocorrelation function for the ring dihedral, compare Markovian versus non-Markovian rate predictions, and provide a timescale analysis of the cavity residue fluctuations relative to the flip event.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim "fractional viscosity dependence of the flip rate despite the ring being completely buried."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No data on the viscosity dependence are presented. The abstract does not specify the range of viscosities studied, the exponent of the fractional dependence, or how the viscosity was varied in the simulations (e.g., by changing solvent properties or using a continuum model).
- **Why it matters** This is a striking and potentially controversial prediction. Without quantitative results, the claim cannot be evaluated, and it is unclear whether the effect is robust or an artifact of the simulation setup.
- **Resolution test** Provide a plot of flip rate versus solvent viscosity with the fitted exponent and its uncertainty, state the method used to vary viscosity, and show that the effect persists across multiple independent simulation conditions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "protein breathing motions" is used without definition or reference to a specific structural coordinate.
- **Required correction** Define what is meant by breathing motions in this context, for example, specific collective coordinates or RMSD fluctuations of the protein backbone.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** System description
- **Evidence pointer** Abstract, second sentence
- **Issue** The specific phenylalanine residue is not identified by its sequence position, and the simulation conditions (force field, temperature, box size) are not stated.
- **Required correction** Specify the residue number and provide key simulation parameters in the abstract or refer to the methods section for details.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with prior work
- **Evidence pointer** Abstract, overall
- **Issue** No mention is made of how these findings relate to previous studies of ring flips in proteins, particularly those using NMR or other simulation approaches.
- **Required correction** Add a sentence situating the results in the context of existing literature on ring-flip dynamics and memory effects.

## Risk / unsupported claims
- The claim of "accurate" rate estimation is unsupported without quantitative data.
- The mechanistic claim of memory-dependent friction from delayed residue response is not evidenced.
- The fractional viscosity dependence claim is entirely unsupported in the abstract.
- The relevance of the findings to "stabilizing the folded conformation and anchoring incoming substrate molecules" is asserted but not connected to any results.