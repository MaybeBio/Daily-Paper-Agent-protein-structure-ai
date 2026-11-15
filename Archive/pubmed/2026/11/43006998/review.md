## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors develop a ReaxFF parameter set for the Pd-Zn system using DFT training sets generated with structure prediction and DFT calculations. They use MD simulations to study alloying in Pd@Zn and Zn@Pd core-shell models, reporting a two-stage, diffusion-controlled process with distinct diffusion coefficients and activation energies. They propose a kinetic model for the fast alloying stage, finding that the alloying activation energy increases with alloying progress and scales with the cube root of the total atom number. They also simulate a Zn/Pd(111) slab model, reproducing experimentally observed temperature-dependent surface alloy structures (multilayer at lower temperatures, bilayer at higher temperatures).
- **Visible evidence base** Abstract text only; no numerical data, figures, tables, or methodological details provided

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable contribution to computational materials chemistry, addressing a gap in theoretical understanding of PdZn alloy formation relevant to catalysis. The development of a ReaxFF parameter set for Pd-Zn and its application to diffusion kinetics is timely and could interest researchers in force field development, alloy simulation, and catalytic materials. However, the abstract alone provides insufficient detail to assess the validity of the force field, the robustness of the kinetic model, or the strength of the slab model comparison. Several claims are stated without quantitative support, and the scaling relationship and temperature-dependent structural findings require careful verification against the full data.
- **Who would be interested in the results, and why** Researchers in computational catalysis, reactive force field development, and alloy materials science would find these results relevant. The PdZn system is important for methanol steam reforming, so experimental groups studying PdZn catalysts may also be interested in the mechanistic insights. The methodological approach combining DFT, ReaxFF, and MD could appeal to those developing transferable force fields for metal alloy systems.
- **Major strengths** The work addresses an underexplored theoretical question, namely the formation kinetics of PdZn alloys, which has clear catalytic relevance. The use of DFT-based training sets for ReaxFF development is a standard and defensible approach. The inclusion of multiple simulation models (core-shell and slab) provides a broad view of the alloying process. The reported reproduction of experimental temperature-dependent surface structures adds credibility to the force field.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate to high, as the specific application of ReaxFF to Pd-Zn alloy formation kinetics appears novel. Scientific importance is significant given the catalytic relevance of PdZn, but the abstract does not yet demonstrate that the findings materially advance understanding beyond what is known empirically. Interdisciplinary readership is plausible, spanning catalysis, materials science, and computational chemistry, but the abstract is written in a specialized manner that may limit accessibility. Technical soundness cannot be fully assessed from the abstract alone; the force field development and MD methodology are standard, but the lack of quantitative results prevents verification. Readability for nonspecialists is limited by the dense presentation of technical terms without context, though the core narrative is understandable.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence. The abstract suggests a promising study, but the absence of quantitative data and methodological details means the core claims cannot be evaluated. Full manuscript review would be necessary to determine whether the force field is validated, the kinetic model is robust, and the slab simulations are convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that ReaxFF parameters for the Pd-Zn system were developed using DFT training sets, and that MD simulations revealed a two-stage, diffusion-controlled alloying process with distinct diffusion coefficients and activation energies.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no quantitative details on the force field accuracy, such as fitting errors, validation against DFT or experimental data, or comparison with existing potentials. Similarly, the reported diffusion coefficients and activation energies are not given numerically, so the reader cannot assess the magnitude or physical reasonableness of these values.
- **Why it matters** Without quantitative validation, the reliability of the ReaxFF parameters is unestablished. Diffusion coefficients and activation energies are central to the kinetic claims, and their absence prevents any assessment of whether the two-stage mechanism is convincingly supported or merely asserted.
- **Resolution test** The full manuscript must provide fitting errors for the ReaxFF parameters, validation against DFT reference data or experimental properties, and numerical values for diffusion coefficients and activation energies with associated uncertainties or statistical measures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the alloying activation energy of the rapid alloying stage increases with the advance of alloying and is proportional to the cube root of the total atom number of the system.
- **Evidence pointer** Abstract, location not provided
- **Concern** This scaling relationship is presented as a key finding, but the abstract provides no data points, fitting procedure, or physical justification. The cube root dependence is a specific and nontrivial claim that requires clear evidence, such as a plot or table showing activation energy versus atom number, and a discussion of the underlying mechanism.
- **Why it matters** If the scaling relationship is robust, it could have predictive value for larger systems, which is a potentially important contribution. However, as stated, it is an unsupported assertion that could be an artifact of the limited system sizes or the specific simulation setup.
- **Resolution test** The full manuscript must show the data supporting the scaling relationship, including the range of system sizes tested, the fitting method, and a physical explanation for the cube root dependence. Statistical significance and robustness to simulation parameters should be demonstrated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that simulations of a Zn/Pd(111) slab model reproduced the experimentally observed temperature dependence of the surface alloy structure, with a multilayer PdZn alloy at lower temperatures and a bilayer alloy at higher temperatures.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not specify the temperature range, the criteria for defining multilayer versus bilayer structures, or the experimental reference used for comparison. Without these details, the claim of reproduction is vague and cannot be evaluated for accuracy or significance.
- **Why it matters** This comparison to experiment is a key validation of the force field and the simulation approach. If the reproduction is qualitative only, it may be coincidental or dependent on arbitrary thresholds. The claim needs to be substantiated with clear structural metrics and a direct comparison to the cited experimental data.
- **Resolution test** The full manuscript must provide the simulation temperatures, a quantitative definition of multilayer and bilayer structures (e.g., layer-resolved composition profiles), and a direct comparison to the experimental observations, including any error bars or sensitivity analysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract uses terms such as "ReaxFF," "core-shell models," and "slab model" without brief explanations, which may hinder readers outside computational chemistry.
- **Required correction** Add a short phrase to define ReaxFF as a reactive force field and briefly describe the core-shell and slab models in plain terms.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Contextual framing
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the formation mechanism of PdZn alloys has not been addressed theoretically, but it does not mention any prior computational studies or why existing methods are insufficient.
- **Required correction** Include a brief statement on the limitations of prior theoretical work to strengthen the novelty claim and provide context.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Kinetic model description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions a "kinetic model was proposed for the fast alloying stage" but gives no indication of the model form, assumptions, or how it was validated.
- **Required correction** Provide a brief description of the kinetic model in the abstract or indicate that full details are in the manuscript, to allow readers to gauge its scope.

## Risk / unsupported claims
- The claim that ReaxFF parameters were successfully developed is unsupported without fitting errors or validation data.
- The two-stage diffusion-controlled mechanism is unsubstantiated without numerical diffusion coefficients and activation energies.
- The scaling relationship between activation energy and cube root of atom number is unsupported without data and physical justification.
- The reproduction of experimental temperature-dependent surface structures is unverifiable without temperature ranges, structural definitions, and experimental references.
- The statement that the formation mechanism has not been addressed theoretically is unverifiable without a literature survey.