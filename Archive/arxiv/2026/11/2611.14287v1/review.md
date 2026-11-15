## Review setup

- **Input scope** Title, author list, arXiv metadata, and landing page text only. No abstract, no main text, no figures, no tables, no supplementary materials, no code repository contents, no license information, no version history beyond the single submission date.
- **Assessment boundary** Assessment is limited to the claims and content that can be inferred from the title and the arXiv listing. No scientific content, methodology description, results, or validation data are available for evaluation.
- **Shared manuscript claim summary** The work presents ANTIOCH-VS, described as a modular, open-source ensemble virtual screening tool that operates from sequence to hits. The title implies a computational pipeline that integrates sequence-based target information with ensemble-based virtual screening to identify hit compounds.
- **Visible evidence base** Title, author list, arXiv subject classification (Chemical Physics), submission date, arXiv identifier, and the standard arXiv landing page boilerplate. No substantive scientific content is visible.
- **Missing materials affecting confidence** The complete manuscript, including abstract, introduction, methods, results, discussion, figures, tables, references, and any associated code or data links, is not provided. The absence of these materials makes any substantive scientific assessment impossible.

## Reviewer

- **Overall assessment** The provided material consists solely of a title and bibliographic metadata. There is no scientific content available to evaluate. The title suggests a potentially useful open-source tool for computational drug discovery, but without the manuscript text, methods, validation, or results, no assessment of scientific quality, technical soundness, or significance can be made. The submission cannot be evaluated in its current form.
- **Who would be interested in the results, and why** Based on the title alone, computational chemists, medicinal chemists, and researchers in structure-based drug discovery could be interested in an open-source ensemble virtual screening tool that operates from sequence to hits. Such a tool could lower barriers to entry for academic and industrial groups lacking commercial software licenses. However, this inference is speculative and based solely on the title.
- **Major strengths** From the title, the stated modularity and open-source nature of the tool are potentially positive attributes. The "sequence to hits" framing suggests an integrated pipeline that could reduce the need for multiple disparate software packages. No other strengths can be identified from the available material.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims to present a functional ensemble virtual screening tool that goes from sequence to hits.
  - **Evidence pointer** Location not provided. No abstract, methods, results, or validation data are available.
  - **Concern** The entire scientific content of the manuscript is unavailable. No abstract, methodology, results, figures, tables, or supporting information were provided for review. The title alone cannot support any assessment of the tool's functionality, performance, or validity.
  - **Why it matters** A scientific manuscript must be evaluated on its evidence, methods, and results. Without access to any of these, no judgment can be made about whether the tool works as claimed, whether the methods are sound, or whether the results support the conclusions. The review process cannot proceed without the substantive content.
  - **Resolution test** Provide the full manuscript, including abstract, main text, figures, tables, and any supplementary materials. The manuscript must include a clear description of the methods, validation results, and a discussion of limitations before any scientific assessment can be made.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Software availability
  - **Evidence pointer** Location not provided. No code repository link, installation instructions, or documentation are visible on the landing page.
  - **Issue** The title states that the tool is open-source, but no link to a code repository, license information, or documentation is visible in the provided material.
  - **Required correction** Provide a clear link to the code repository, specify the open-source license, and include installation and usage documentation either in the manuscript or in the repository.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Benchmarking
  - **Affected element** Validation strategy
  - **Evidence pointer** Location not provided. No benchmark datasets, comparison studies, or performance metrics are visible.
  - **Issue** The title implies a functional tool, but no evidence of benchmarking against existing virtual screening methods or validation on known target-ligand systems is visible.
  - **Required correction** Include a validation section with benchmark results against established virtual screening tools, using standard datasets and appropriate performance metrics such as enrichment factors or ROC curves.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Input data requirements
  - **Evidence pointer** Location not provided. No description of required input formats or data preparation steps is visible.
  - **Issue** The "sequence to hits" workflow implies specific input requirements, but no details on sequence format, structure prediction steps, or preparation of compound libraries are visible.
  - **Required correction** Clearly describe the input formats, any required preprocessing steps, and the workflow from sequence to screening results in the methods section.

## Risk / unsupported claims

- The claim that ANTIOCH-VS is a functional ensemble virtual screening tool is unsupported because no methods, results, or validation data were provided.
- The claim that the tool is open-source is unverifiable because no code repository or license information is visible.
- The claim that the tool operates from sequence to hits is unverifiable because no workflow description or case study is provided.
- Any claim regarding the tool's performance, accuracy, or utility relative to existing methods is not assessable from the supplied material.