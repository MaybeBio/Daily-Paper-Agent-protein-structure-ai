## Learning the limits of protein structure models with NMR chemical shifts


## Abstract

Protein foundation models are intended to implicitly learn the chemical rules underlying protein function. However, systematically evaluating what biochemistry these models have learned remains difficult, as most downstream tasks lack experimental data fine-grained enough to expose their failure modes. NMR chemical shifts fill this gap: as direct per-atom reporters of local chemical environment, they offer a sensitive probe of structure-based representations. In this work, we present a systematically curated chemical shift dataset designed to minimize experimental confounders. We use it to benchmark diverse protein foundation models in their ability to predict backbone 15N chemical shifts, atoms that are known to be sensitive to many effects. The largest error across all models is in core residues with evidence of fast-timescale dynamics, which we investigate mechanistically using molecular dynamics simulations. Given the biological relevance of structured dynamic regions, we trained a new model based on the best of these embeddings, SLAE, to predict its own error. SLAE-ERR achieves a mean absolute error of 0.76 ppm for predicting error. Together, we hope that the datasets, evaluation tasks, and models presented here are sources of guidance for protein design model improvement.


## Competing Interest Statement

The authors have declared no competing interest.


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats