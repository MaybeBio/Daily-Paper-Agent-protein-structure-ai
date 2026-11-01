## De novo Protein Generating Model via Structure-Aware Graph Neural Networks


## Abstract

The focus of this paper is to create a protein conformation prediction model that is optimized for structural accuracy rather than sequence recovery. To achieve this goal, we created a graph neural network (GNN) [19] for the design of computational proteins that integrates differentiable structure prediction through ESMFold [13] via a structural loss function, allowing direct optimization of the 3D conformational accuracy. Our model takes protein backbone coordinates as input and predicts an amino acid sequence using a composite loss that heavily weights structural similarity. On a matched evaluation sample, our model achieves structural precision (RMSD, TM-score, and GDT-TS) that is statistically indistinguishable from ProteinMPNN, a leading sequence recovery-focused method, despite training with no direct sequence recovery supervision and substantially lower native sequence recovery. Our results demonstrate that sequence recovery is not necessary to achieve competitive structural accuracy and that proteins can possess multiple non-unique solutions, suggesting that protein sequence prediction models may perform comparably well under purely structural conformation training. This distinction in training data and model structure allows for the training of a protein-generating model on non-natural proteins. Creating a model designed for de novo protein generation.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://github.com/Justworkname/GenomeGenerator


## Funder Information Declared

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area