## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, or full-text data were available for evaluation
- **Shared manuscript claim summary** The abstract argues that deep learning has advanced structure-based enzyme design, particularly via diffusion-based scaffold generation and sequence design, but that current methods yield enzymes with limited turnover rates because they optimize substrate binding rather than transition-state stabilization. It proposes that targeting electrostatic catalysis, multistate behavior, and conformational dynamics, alongside improved activity oracles, evolutionary information, protein language models, and lab-in-the-loop optimization, could enhance catalytic efficiency.
- **Visible evidence base** Abstract text only; no quantitative data, benchmark comparisons, case studies, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, figures, tables, methods, specific enzyme examples, quantitative performance metrics, and any comparative analyses against alternative design strategies

## Reviewer
- **Overall assessment** The abstract presents a coherent and timely perspective on the current state and limitations of deep learning in enzyme design. The central thesis, that current structure-based approaches often produce tight substrate binders rather than efficient catalysts due to insufficient transition-state stabilization, is plausible and aligns with trends in the field. However, the abstract provides no empirical evidence, case examples, or quantitative support for this claim, and the proposed solutions are listed without critical evaluation of their feasibility or expected impact. As a perspective piece, the abstract is readable and logically structured, but its scientific depth is limited by the absence of supporting data and the lack of engagement with counterarguments or alternative frameworks.
- **Who would be interested in the results, and why** Computational biologists, protein engineers, and enzymologists working on enzyme design and directed evolution would find this perspective relevant. Researchers developing generative models for protein design, particularly those using diffusion models or language models, would also be interested in the critique of current limitations and the proposed future directions. The abstract could inform research prioritization in both academic and industrial settings focused on biocatalysis.
- **Major strengths** The abstract clearly identifies a specific and important gap in current enzyme design, namely the distinction between substrate binding and transition-state stabilization. It offers a focused set of proposed improvements that are grounded in established physicochemical principles. The writing is concise and accessible to a broad scientific audience.
- **Major Concerns** The central claim that current methods yield tight substrate binders rather than transition-state stabilizers is presented without supporting evidence, such as comparative kinetic data or structural analyses. The proposed solutions, including electrostatic catalysis design and multistate modeling, are not critically assessed for their current maturity or practical challenges. The abstract does not acknowledge potential counterexamples where deep learning has achieved high turnover rates, nor does it discuss the role of directed evolution in complementing computational design.
- **Minor Comments** The abstract would benefit from a brief mention of specific enzyme classes or reactions where the described limitations are most pronounced. The phrase "lab-in-the-loop optimization" is used without definition, which may confuse nonspecialist readers. The final sentence is somewhat repetitive of the opening, and the abstract could end with a more forward-looking or actionable statement.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative or qualitative evidence to support the claim that current approaches yield tight substrate binders. Without such evidence, the central thesis remains an assertion rather than an established observation. Additionally, the proposed improvements are not linked to any preliminary results or feasibility assessments, leaving their potential impact unsubstantiated.
- **Assessment against Nature-style criteria** Originality: The perspective is not entirely novel, as the limitation of computational enzyme design in achieving high turnover is a known challenge, but the specific framing around transition-state stabilization versus substrate binding is a useful synthesis. Scientific importance: The topic is of high importance to the enzyme design community, and the abstract addresses a critical bottleneck. Interdisciplinary readership: The abstract is written in a way that should be accessible to computational scientists, biochemists, and enzymologists, though some terms may require prior knowledge. Technical soundness: The abstract is technically plausible but lacks the evidence needed to assess soundness of the claims. Readability for nonspecialists: The abstract is generally clear, but the lack of definitions for some terms and the absence of concrete examples reduce accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The perspective is potentially valuable, but the abstract must be supported by evidence from the full manuscript, including specific examples, quantitative data, and a more critical discussion of the proposed solutions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that current structure-based enzyme design approaches "typically yield tight substrate binders rather than enzymes that selectively stabilize the chemical transition state."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The claim that current methods yield tight substrate binders rather than transition-state stabilizers is presented as a general observation, but no data, examples, or references are provided to support this assertion. The abstract does not cite specific enzymes, kinetic measurements, or structural comparisons that would substantiate this pattern.
- **Why it matters** This claim is the central thesis of the perspective. If it is not supported by evidence, the entire argument for redirecting design efforts toward transition-state stabilization loses its foundation. Readers cannot assess whether this is a well-established trend or an anecdotal impression.
- **Resolution test** The full manuscript must provide specific examples of designed enzymes with high k(cat)/K(M) but low k(cat), along with comparative data or structural evidence showing that these enzymes bind substrates tightly without stabilizing the transition state. Alternatively, the authors should cite published studies that systematically demonstrate this pattern.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of proposed solutions
- **Claim pointer** The abstract proposes that "computational design of electrostatic catalysis, multistate behavior, and conformational dynamics could potentially enhance transition-state stabilization and improve catalytic activity."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The proposed solutions are listed without any assessment of their current feasibility, limitations, or expected impact. For example, computational design of electrostatic catalysis is a long-standing challenge, and it is unclear how deep learning would address it beyond existing methods. Similarly, multistate design and conformational dynamics are computationally demanding and not yet routine.
- **Why it matters** A perspective piece should not only identify gaps but also critically evaluate the promise and challenges of proposed directions. Without this, the abstract reads as a wish list rather than a scientifically grounded roadmap.
- **Resolution test** The full manuscript should include a discussion of the current state of each proposed approach, including any preliminary results, known bottlenecks, and how deep learning specifically would advance these areas.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Consideration of alternative perspectives
- **Claim pointer** The abstract implies that structure-based design is the primary path forward, with improvements in activity oracles, evolutionary information, and language models as supporting tools.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not acknowledge the substantial role of directed evolution in achieving high catalytic efficiency in practice. Many successful enzyme engineering campaigns combine computational design with laboratory evolution, and the abstract does not discuss how the proposed deep learning approaches would integrate with or replace this paradigm.
- **Why it matters** The perspective may overstate the potential of purely computational approaches and understate the practical importance of experimental optimization. A balanced view would strengthen the credibility of the perspective.
- **Resolution test** The full manuscript should include a discussion of the complementary roles of computational design and directed evolution, and how the proposed deep learning methods would fit into existing workflows.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity for nonspecialists
- **Affected element** Term "lab-in-the-loop optimization"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term is used without definition, and nonspecialist readers may not understand what it entails.
- **Required correction** Provide a brief explanation, such as "iterative cycles of computational design and experimental testing guided by machine learning," or use a more self-explanatory phrase.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Specificity
- **Affected element** General claim about "diverse catalytic functions and complex catalytic motifs"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that structure-based approaches have "enabled the emergence of enzymes with diverse catalytic functions and complex catalytic motifs," but no examples are given.
- **Required correction** Mention one or two specific enzyme classes or reactions to illustrate the claim, or refer to a figure or table in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Redundancy
- **Affected element** Final sentence
- **Evidence pointer** Abstract text; location not provided
- **Issue** The final sentence largely restates the opening claim about the need to move beyond substrate binding toward efficient catalysis.
- **Required correction** Replace with a more specific or forward-looking statement, such as a call for benchmarking standards or a particular technical milestone.

## Risk / unsupported claims
- The claim that current methods "typically yield tight substrate binders rather than enzymes that selectively stabilize the chemical transition state" is unsupported in the abstract and requires evidence from the full manuscript.
- The assertion that "computational design of electrostatic catalysis, multistate behavior, and conformational dynamics could potentially enhance transition-state stabilization" is speculative and not backed by preliminary data or feasibility analysis.
- The statement that "more reliable activity oracles, integration of evolutionary information, protein language models, and lab-in-the-loop optimization could further enhance design performance" is a list of possibilities without critical evaluation or evidence of expected impact.
- The overall claim that "deep learning has substantially advanced structure-based enzyme design" is plausible but not quantified or exemplified in the abstract.