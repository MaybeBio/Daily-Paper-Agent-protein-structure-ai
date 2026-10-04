## EnsPlex: Integrative Protein Complex Prediction through Multi-source Complementary Structural Sampling and Topology-Aware Candidate Selection


## Abstract

Protein complex structure prediction depends on both the breadth of candidate coverage and the ability to select accurate models within a limited output budget. Most existing approaches emphasize only one stage. End-to-end models and molecular docking workflows generate candidate structures, whereas quality-assessment models primarily rerank a predefined candidate pool. A complete strategy must account for complementary sampling across generators, differences among scoring scales and the allocation of final candidate quotas. Here, EnsPlex is presented as a multi-source framework that couples structural sampling with candidate selection for protein-protein interaction complex prediction. EnsPlex combines conformation-expanded docking, AlphaFold-Multimer, AlphaFold3 and Boltz-1 to expand the sampled conformational space. Conformation-expanded docking comprises monomer conformational expansion followed by flexible HADDOCK docking. FACET is trained to predict candidate quality using DockQ and its component metrics as supervision. Across 102 antigen-antibody systems, EnsPlex achieved up to a 27.8% relative improvement in target success rate over AlphaFold3 with its built-in ranking under matched output budgets. FACET also improved within-source ranking in the internal candidate pools and in homology-filtered external data. These findings support the utility of EnsPlex for structure prediction in the evaluated antigen-antibody systems.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://doi.org/10.5281/zenodo.22857353

https://doi.org/10.5281/zenodo.22858234

https://github.com/H18020306/EnsPlex


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area