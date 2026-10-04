## SMartini: automated small molecule parametrization for Martini 3 force field


## Abstract

We present SMartini, an automated pipeline for deriving Martini 3 coarse-grained force-field parameters for arbitrary small molecules. Starting from a molecular structure or a SMILES string, the pipeline maps the all-atom molecule onto a coarse-grained bead representation and automatically fits both bonded and non-bonded parameters. Bonded parameters are obtained via Boltzmann inversion of atomistic molecular dynamics trajectories; successive rounds of coarse-grained simulation and distribution-matching updates then refine these estimates until the coarse-grained conformational ensemble reproduces the all-atom reference within tolerance. We validate the pipeline on a diverse set of small molecules including drug-like compounds, metabolites, and cofactors. Implemented as a modular sequence of scripts that can be orchestrated on high-performance computing clusters, SMartini makes automated parametrization of large ligand libraries practical and reduces the manual effort required for coarse-grained model development, enabling high-throughput coarse-grained simulations of protein--ligand systems within the Martini 3 ecosystem


## Competing Interest Statement

The authors have declared no competing interest.


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area