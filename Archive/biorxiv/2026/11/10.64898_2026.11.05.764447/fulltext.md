## pLM-bVAE: protein language model-enhanced binary representation improves quantum annealing-based protein sequence design


## Abstract

Quantum annealing (QA) has been explored as an approach for protein design in vast combinatorial sequence spaces. Applying QA to protein sequence design requires amino acid sequences to be encoded as binary vectors, and optimized vectors to be decoded back into amino acid sequences. Thus, both the quality of binary encoding and sequence reconstruction accuracy are important for effective QA-based optimization. Binary variational autoencoder (bVAE) has been used to map protein sequences to binary representations in QA-based protein sequence design. However, bVAE was originally developed for natural language modeling, and its suitability for proteins has not been systematically evaluated. Here, we present pLM-bVAE, which incorporates protein representations derived from a pretrained protein language model (pLM) into the original bVAE model. In computational experiments on three public protein variant datasets, pLM-bVAE showed higher sequence reconstruction accuracy and binary encoding performance than bVAE. Moreover, we incorporated pLM-bVAE into a QA-based protein sequence design framework. Across all three datasets, pLM-bVAE generated more high-scoring sequences with greater sequence dissimilarity from the training and validation data than bVAE. Our results demonstrate that pLM-bVAE provides an effective binary representation for improving QA-based protein sequence design. Availability The source code used in this manuscript is available at https://github.com/hueda8/pLM-bVAE.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://github.com/hueda8/pLM-bVAE


## Funder Information Declared

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area