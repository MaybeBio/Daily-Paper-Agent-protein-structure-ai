## UnibindMD: An Integrated AI and Molecular Dynamics Platform for De Novo Peptide Binder Design


## Abstract

UnibindMD is an integrated computational platform that turns a protein target into validated de novo peptide-binder leads by chaining five orthogonal stages: deep-learning binder design (BindCraft), independent structure prediction and confidence assessment (AlphaFold3-class / Boltz-2), binding-affinity prediction (PRODIGY), developability profiling (ADMET-AI), and all-atom molecular-dynamics validation (GROMACS/CHARMM36m). The platform targets a persistent weakness of single-method design, namely that confidence metrics such as ipTM and pLDDT are self-consistent but not independent, so a design predicted to be confident may still be physically unstable. We demonstrate UnibindMD on three Andes virus (ANDV) intervention points, a setting of urgent need given a case fatality rate approaching 40%, a 2026 MV Hondius cruise-ship outbreak (13 cases, 3 deaths), and no approved therapeutic: the Gn-Gc glycoprotein complex (viral entry), the L-protein endonuclease domain (cap-snatching; PDB 6Q99), and the host VEGFR2 kinase (vascular permeability; PDB 2XIR). Across nine BindCraft campaigns (4,475 trajectories) the platform produced 464 accepted binders (acceptance 2.3-67.6%), with top candidates reaching ipTM = 0.94 and pLDDT = 0.94. The three selected leads were predicted by PRODIGY to bind with G = -9.1 to -11.1 kcal mol-1 (Kd 8 nM-0.2 μM), and all three remained stably bound over 100 ns of unrestrained molecular dynamics (receptor CαRMSD ≤ 2.6 Å, retained peptide fold, ≥ 99.5% of frames preserving more than half of the initial interface contacts, and 75-82% helical content). ADMET-AI flagged the expected poor oral bioavailability of large polar peptides and no PAINS alerts. By converting single-prediction design into a cross-validated, dynamics-tested workflow, UnibindMD provides a rapid, scalable, and generalizable path from any protein target to validated peptide-binder candidates.


## Competing Interest Statement

The authors have declared no competing interest.

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area