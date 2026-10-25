## Projected Gradient Descent for Hallucination-Based Protein Binder Design


## Abstract

Gradient-based hallucination is a popular approach to protein binder design that backpropagates a loss defined on a structure predictor's output to guide optimisation in a continuous relaxation of sequence space, yet the choice of optimiser for this task has received little systematic evaluation. In this work we evaluate simplex-projected gradient descent (PGD) as an alternative to the commonly used gradient descent on softmax-reparameterised sequence logits. By updating amino-acid probabilities directly, PGD avoids softmax-induced gradient attenuation and allows amino acids suppressed early in optimisation to re-enter the design. Using an ESMFold2-based pipeline on ten targets, we find that PGD minimises the design loss in fewer iterations and produces designs with higher predicted interface confidence compared to its softmax counterpart. Simulating selection in real campaigns by considering the upper tail of the ipSAE distribution across a pool of 1,024 designs per target, we show that PGD significantly improves on six of the ten targets, with no significant degradation on any, and produces more structurally diverse designs on every target. Additionally, we find that pairing shorter PGD runs with candidate screening raises the total number of in silico hits per GPU-hour by 29\% relative to default-length trajectories. These results support PGD as a simple and effective alternative for hallucination-based binder design. Code and design data are publicly available.


## Competing Interest Statement

The authors have declared no competing interest.


## Footnotes

https://github.com/magnusross/pgd-hallucination

https://doi.org/10.5522/04/34493751


## Funder Information Declared

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area