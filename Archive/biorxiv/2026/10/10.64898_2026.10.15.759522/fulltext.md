## Sequence-only prediction of VHH nanobody epitopes and paratopes on HER2 with a frozen protein language model ( ESM2) and a structure-derived residue prior


## Abstract

Mapping which antigen residues an antibody contacts (the epitope) and which antibody residues do the contacting (the paratope) is central to therapeutic antibody engineering, yet most accurate methods require a solved or predicted three dimensional complex. We address a sequence only formulation: predict the HER2 epitope and the single domain antibody (VHH, or nanobody) paratope from the two sequences alone, with no three dimensional structure prediction at any stage. We pair a frozen ESM2 650M protein language model, used strictly as a feature extractor, with a lightweight trainable module per chain encoders, a shared cross attention block, and epitope, paratope and binder heads (12.2M trainable parameters) trained jointly on three public sources: HER2 binding and blocking competition assays ("AVIDa hHER2" to be published by organizers of SEPIQ 2026 The authors have no right to share the dataset to public ), residue level antibody antigen contacts (SAbDab2), and two reference antibody crystal structures. The blocking competition signal is de confounded into a trastuzumab minus pertuzumab contrast whose sign encodes the HER2 domain and which is used only as a training target, never as a model input. Under a three way, sequence cluster level split with a test set opened exactly once, the binder head reaches PR AUC 0.999 and the paratope head 0.659, while residue level epitope prediction on novel antigens remains near baseline (0.070) a limitation the sealed split exposes rather than hides. Sequence alone recovers the competition derived HER2 domain (the competitor class) for 87.7% of held out clones, a leakage free result. For HER2 specifically, a residue prior built from 25 mined HER2 antibody complexes and validated by leave one out reaches 0.26 to 0.29 residue PR AUC once the domain is correct, roughly 3.6 times the language model head alone. We release and report two submission variants per test clone, a fully sequence only prediction and a competition informed one ,and document which data were used where. Keywords: epitope prediction; paratope prediction; nanobody; VHH; HER2; protein language model; ESM2; cross attention; antibody antigen interface; leakage safe evaluation.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://sepiq.uk/

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area