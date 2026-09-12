## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** The manuscript as provided, including abstract, introduction, sections on gene sequence analysis, protein structure prediction, drug design, future outlook, and conclusion.
- **Shared manuscript claim summary** This manuscript claims to provide a comprehensive survey of large language models (LLMs) in bioinformatics, covering their principles, applications in gene sequence analysis, protein structure prediction, and drug design, and discussing future directions and challenges.
- **Visible evidence base** The manuscript includes a narrative review of existing literature, a timeline figure (Figure 1), a model architecture comparison table (Table 1), and a figure illustrating LLM applications in bioinformatics (Figure 3). No original experimental data, code, or quantitative benchmarks are presented.
- **Missing materials affecting confidence** No original data, code, or systematic evaluation methodology is provided. The survey lacks a PRISMA-style search strategy, inclusion/exclusion criteria, or a quantitative comparison of model performance across studies. The figures (Figure 1, 2, 3) are described but not shown.

## Reviewer
- **Overall assessment** This manuscript presents a broad, narrative-style survey of large language models in bioinformatics. While the topic is timely and the scope is ambitious, the manuscript suffers from a lack of depth, originality, and critical analysis. It reads more as a descriptive list of models and applications than a critical synthesis that would guide future research. The absence of a systematic methodology, quantitative comparisons, and a clear conceptual framework significantly limits its value as a survey. The manuscript does not meet the standards of originality, scientific importance, or technical soundness expected for a high-impact journal.
- **Who would be interested in the results, and why** Early-career researchers or students seeking a high-level, non-technical introduction to the application of LLMs in bioinformatics might find this survey useful. However, the lack of critical analysis and depth means it offers limited value for experts in the field.
- **Major strengths**
    - The topic is highly relevant and timely, given the rapid integration of LLMs into bioinformatics.
    - The manuscript covers a wide range of applications, from genomics to drug design.
    - The inclusion of a timeline and a table summarizing representative models provides a useful, albeit superficial, overview.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Originality and Scientific Importance
    - **Claim pointer** The manuscript claims to be a "comprehensive survey" that reviews the "background and research status of biological large-scale models" and "discusses future directions."
    - **Evidence pointer** Entire manuscript
    - **Concern** The manuscript is a descriptive narrative review that lacks a systematic methodology. It does not define a search strategy, inclusion/exclusion criteria, or a framework for evaluating the quality of the cited studies. The "comprehensive" claim is not supported. The review primarily lists models and their applications without critical analysis, comparison, or synthesis. For example, the section on "Gene sequence analysis" presents a series of model descriptions (DeepMicrobes, MetaTransformer, ConF, etc.) without a comparative analysis of their strengths, weaknesses, or the contexts in which one might be preferred over another. The "Future outlook" section is generic and does not offer novel or specific research directions.
    - **Why it matters** A survey in a high-impact journal must provide more than a list of existing work. It should offer a critical synthesis, identify key trends, highlight unresolved challenges, and propose a roadmap for future research. The current manuscript fails to do this, making it a low-impact contribution that does not advance the field.
    - **Resolution test** The authors must restructure the manuscript as a systematic review with a clearly defined methodology (e.g., PRISMA guidelines). They should include a quantitative or qualitative comparison of model performance across key tasks, identify specific gaps in the literature, and propose concrete, testable hypotheses or research directions. The "comprehensive" claim must be justified by the methodology.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness and Depth
    - **Claim pointer** The manuscript claims to review the "basic principles of LLMs" and their applications.
    - **Evidence pointer** Sections: Introduction, Gene sequence analysis, Protein structure prediction, Drug design
    - **Concern** The technical depth is insufficient for a survey aimed at an informed audience. The explanation of LLM principles is superficial (e.g., "Model scale: The number of parameters owned by the training model"). The discussion of model architectures (e.g., Transformer, GNN) is basic and does not delve into the specific adaptations required for biological sequences (e.g., tokenization strategies like k-mer vs. BPE, positional encoding for long sequences). The section on "Model architecture comparison and selection rationale" is a brief, generic list of model types without a clear connection to the specific challenges of bioinformatics data. The manuscript does not critically evaluate the limitations of applying LLMs to biological data, such as the challenge of modeling 3D structures from 1D sequences, the impact of data bias, or the computational cost of training large models.
    - **Why it matters** A survey must provide sufficient technical detail for readers to understand the core concepts and evaluate the claims. The current level of detail is more appropriate for a magazine article than a scientific review. The lack of depth undermines the manuscript's credibility and utility.
    - **Resolution test** The authors should significantly expand the technical sections. For example, they should explain the key components of the Transformer architecture (self-attention, multi-head attention, positional encoding) and how they are adapted for genomic or protein sequences. They should provide a more detailed comparison of different tokenization strategies and their impact on model performance. They should also discuss the specific challenges of applying LLMs to biological data, such as the need for inductive biases (e.g., equivariance for 3D structures) and the problem of data scarcity for rare variants.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Readability and Structure
    - **Claim pointer** The manuscript is presented as a "comprehensive survey."
    - **Evidence pointer** Entire manuscript
    - **Concern** The manuscript's structure is disjointed and lacks a clear narrative flow. The introduction jumps between historical timelines, model characteristics, and applications without a clear logical progression. The sections on "Gene sequence analysis" and "Protein structure prediction" contain subsections that are not well-integrated (e.g., "Model architecture comparison and selection rationale" appears as a subsection within "Gene sequence analysis" but is not clearly linked to the preceding or following content). The "Future outlook" section is a list of general challenges (data scarcity, multimodal integration) that are not specifically tied to the models or applications discussed earlier.
    - **Why it matters** A well-structured survey guides the reader through the material, building a coherent argument. The current structure is confusing and makes it difficult to follow the authors' main points. This reduces the manuscript's readability and impact.
    - **Resolution test** The authors should reorganize the manuscript with a clear, logical structure. For example, they could start with a section on the fundamental principles of LLMs, followed by sections on specific application domains (genomics, proteomics, drug design), each with a consistent structure (e.g., problem definition, key models, comparative analysis, challenges). The "Future outlook" should be a synthesis of the challenges identified in the preceding sections, leading to specific, actionable research directions.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and Accuracy
    - **Affected element** Abstract
    - **Evidence pointer** Abstract
    - **Issue** The abstract states: "Biological large-scale models are a cross-disciplinary research field that combines mathematics, computer science, and biology, aiming to simulate and understand the structure, function, and dynamic changes of biological systems through the establishment of complex computational models." This definition is too broad and could apply to many areas of computational biology, not specifically LLMs.
    - **Required correction** Refine the abstract to focus specifically on large language models and their unique contributions to bioinformatics, rather than "biological large-scale models" in general.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Accuracy
    - **Affected element** Introduction
    - **Evidence pointer** Introduction
    - **Issue** The statement "DeepSeek-R1 ... reported in Nature" is not supported by the provided reference (Guo et al., 2025). The reference is not verifiable from the manuscript. The authors should ensure all claims about specific publications are accurate and properly cited.
    - **Required correction** Verify the publication venue for DeepSeek-R1 and correct the citation if necessary. If the claim is not verifiable, it should be removed.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Table 1
    - **Evidence pointer** Table 1
    - **Issue** The manuscript states "Table 1 summarizes representative applications..." but the table itself is not provided in the manuscript text. The reader cannot evaluate the claims made about the table's contents.
    - **Required correction** Include Table 1 in the manuscript.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section: "Research on end-to-end protein structure prediction model"
    - **Evidence pointer** Section: "Research on end-to-end protein structure prediction model"
    - **Issue** The sentence "DeepECA (Fukuda and Tomii, 2020) has been proposed to address the potential decrease in statement results caused by rich sequences" is unclear. What are "statement results"?
    - **Required correction** Clarify the meaning of "statement results" or rephrase the sentence.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Accuracy
    - **Affected element** Section: "Applications of large language models in virtual screening and ligand discovery"
    - **Evidence pointer** Section: "Applications of large language models in virtual screening and ligand discovery"
    - **Issue** The claim that "large language models (LLMs) can predict and generate new compound structures by learning a large amount of biomedical data, and can even perform drug design without a clear target structure" is an overstatement. While some generative models can propose novel molecules, "drug design without a clear target structure" is a highly active research area with significant limitations, and the manuscript does not provide evidence for this strong claim.
    - **Required correction** Temper the claim to reflect the current state of the art, e.g., "LLMs can be used to propose novel molecular structures, and in some cases, can suggest potential ligands even when the target structure is not fully resolved, though this remains a challenging area of research."

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2. The manuscript lacks a systematic methodology and sufficient technical depth to be considered a valuable scientific contribution.

- **Assessment against Nature-style criteria**
    - **Originality**: Low. The manuscript is a narrative review that does not present a novel synthesis, framework, or critical analysis. It largely re-describes existing work without offering new insights.
    - **Scientific importance**: Low to Medium. The topic is important, but the manuscript's superficial treatment and lack of critical analysis mean it does not significantly advance understanding or guide future research.
    - **Interdisciplinary readership**: Medium. The topic is inherently interdisciplinary, but the manuscript's lack of depth and poor structure may limit its appeal to experts in any one field (e.g., computer science, biology).
    - **Technical soundness**: Low. The technical explanations are superficial and sometimes inaccurate. The lack of a systematic methodology undermines the survey's validity.
    - **Readability for nonspecialists**: Low to Medium. The manuscript is written in accessible language, but the disjointed structure and lack of clear narrative make it difficult to follow for a nonspecialist seeking a coherent overview.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires a fundamental restructuring and significant expansion of its technical and critical content to be considered for publication in a high-impact journal. A major revision is needed, but the current scope and approach suggest the manuscript may be more suitable for a lower-tier review journal.