## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The abstract reports the 2027 status of InterPro (version 110.0), a freely accessible protein sequence classification resource. It claims: integration of signatures from multiple member databases; annotations for hundreds of millions of sequences with extensive UniProtKB coverage; mapping to Gene Ontology, PDBe, and AlphaFold Database; new developments including InterPro-N (a deep-learning method increasing UniProtKB sequence coverage to over 90%); transition from InterProScan 5 to InterProScan 6; integration of structure-based domain classifications and AlphaFold predicted structures; a redesigned protein viewer; a new Model Context Protocol (MCP) server; and creation of 9484 new InterPro entries over two years, bringing the total to 54 922.
- **Visible evidence base** Abstract text only; no quantitative validation, benchmark results, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, benchmark or evaluation data for InterPro-N, performance comparisons for InterProScan 6, details of the MCP server implementation, and any user or community validation studies

## Reviewer

- **Overall assessment** This abstract describes a major update to a widely used bioinformatics resource. The scope of the reported developments is substantial and the resource is clearly of high community value. However, the abstract is largely descriptive and lacks quantitative evidence to support several key claims, particularly the performance and coverage gains attributed to InterPro-N and InterProScan 6. The scientific case for the novelty and impact of these developments cannot be fully assessed from the abstract alone. The manuscript is likely to be of interest to a broad computational biology audience, but the strength of the technical claims needs to be verified against the full text.
- **Who would be interested in the results, and why** Researchers in protein bioinformatics, functional annotation, genome analysis, and structural biology would be interested. The resource is also relevant to those using Gene Ontology annotations, AlphaFold structure data, and AI-assisted database querying. The reported increase in UniProtKB coverage and the new MCP server would appeal to developers of automated analysis pipelines and AI-based tools.
- **Major strengths** The resource is freely accessible and has a long-standing user base. The reported integration of deep learning (InterPro-N), a re-engineered software suite (InterProScan 6), and structure-based classifications represents a coherent and forward-looking update. The inclusion of an MCP server for AI assistants is timely and innovative. The scale of the update (9484 new entries) demonstrates active curation and community engagement.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "InterPro-N, a deep-learning method that increases sequence coverage of UniProtKB to over 90%"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract claims that InterPro-N increases sequence coverage of UniProtKB to over 90% but provides no details on the method architecture, training data, evaluation metrics, or comparison with previous coverage levels. It is unclear what "coverage" means precisely (e.g., fraction of sequences with at least one annotation, fraction of residues covered, or something else) and how this was measured.
  - **Why it matters** This is the central technical claim of the update. Without a clear definition of coverage and a demonstration that the increase is robust and not an artifact of the method, the claim cannot be evaluated. Overstated or ambiguous coverage claims could mislead users who rely on InterPro for functional annotation.
  - **Resolution test** The full manuscript should provide a precise definition of coverage, describe the InterPro-N architecture and training data, and present benchmark results against previous InterPro versions and possibly other methods. A clear statement of the previous coverage percentage and the absolute number of newly covered sequences would also be needed.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "the transition from InterProScan 5 to the completely re-engineered InterProScan 6"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that InterProScan 6 is "completely re-engineered" but provides no information on what changed, why the re-engineering was necessary, or how performance (speed, memory, accuracy) compares with InterProScan 5. No benchmarks or usage statistics are given.
  - **Why it matters** InterProScan is a critical tool for many users. A major re-engineering could introduce changes in output format, behavior, or compatibility that affect existing pipelines. Without evidence of improved or maintained performance, users cannot assess whether migration is worthwhile or safe.
  - **Resolution test** The full text should describe the architectural changes, present benchmark comparisons (e.g., runtime, memory usage, annotation accuracy) against InterProScan 5, and discuss any changes to output formats or API compatibility.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "the integration of structure-based domain classifications and predicted structures from AlphaFold"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract mentions integration of structure-based domain classifications and AlphaFold predicted structures but does not specify which classifications are integrated, how they are mapped to InterPro entries, or what new biological insights or functional annotations this enables. The novelty relative to previous InterPro releases is unclear.
  - **Why it matters** Structure-based classification is a growing area, and the integration of AlphaFold structures is timely. However, the abstract does not explain how this integration improves the resource for users, whether it changes annotation confidence, or whether it enables new types of queries. Without this context, the claim is vague.
  - **Resolution test** The full text should name the specific structure-based resources integrated, describe the mapping procedure, and provide examples or statistics showing how many InterPro entries now benefit from structural evidence and what new annotations are possible.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The term "Model Context Protocol (MCP) server" is introduced without explanation. Nonspecialist readers may not know what MCP is or why it is significant.
  - **Required correction** Add a brief parenthetical explanation, for example "a protocol that allows AI assistants to interact with external data sources" or similar, to make the innovation accessible to a broader audience.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract states "9484 new InterPro entries have been created, bringing the total to 54 922" but does not indicate the time period precisely beyond "over the past two years." It is unclear whether this refers to the period since the last NAR update or a different interval.
  - **Required correction** Specify the exact date range for the new entries, for example "between January 2025 and December 2026" or similar, to allow readers to gauge curation rate.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "hundreds of millions of sequences" but does not give a precise number or the exact fraction of UniProtKB covered. This is imprecise for a resource paper.
  - **Required correction** Provide a specific number of annotated sequences and the percentage of UniProtKB covered, ideally with a reference to the UniProtKB release version used.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking because the central technical claims (coverage increase and re-engineered software) are not supported by any quantitative evidence in the abstract. R1-M3 is not blocking but requires clarification in the full text.
- **Assessment against Nature-style criteria** Originality: The use of deep learning for coverage expansion and the MCP server are novel elements, but the abstract does not demonstrate how these differ from prior approaches in the field. Scientific importance: The resource is clearly important, but the abstract does not quantify the impact of the new features on biological discovery or annotation accuracy. Interdisciplinary readership: The abstract is written for a bioinformatics audience and would be accessible to computational biologists, but the MCP server and deep learning aspects may not be clear to experimental biologists. Technical soundness: Not assessable from the abstract; the key claims lack supporting data. Readability for nonspecialists: The abstract is generally clear but includes jargon (e.g., MCP) without explanation.
- **Recommendation posture** Supportive if technical concerns are resolved. The resource is valuable and the update is substantial, but the abstract alone does not establish the validity of the key technical claims. The full manuscript must provide the missing quantitative evidence and methodological details.

## Risk / unsupported claims

- The claim that InterPro-N increases UniProtKB coverage to over 90% is unsupported in the abstract; no definition of coverage, method details, or evaluation are provided.
- The claim that InterProScan 6 is "completely re-engineered" is unsupported; no performance or compatibility data are given.
- The claim of "integration of structure-based domain classifications and predicted structures from AlphaFold" is vague and not substantiated with specific resources or outcomes.
- The statement "ensuring extensive coverage of UniProtKB" is imprecise and not quantified.
- The total number of entries (54 922) and the count of new entries (9484) are stated without a clear time frame or comparison to previous releases.