## Abstract

We introduce Cadense, a generative framework for antibody ensemble prediction that produces diverse Fv structures from sequence, informed by conformational dynamics. While a valuable resource, static structure prediction provides only a single snapshot of dynamic proteins, whose motions influence their binding and other properties. This is particularly relevant for antibodies, an important class of molecules for drug discovery, where flexible complementarity determining region (CDR) loops are difficult to model with static approaches. Cadense addresses this gap by generating ensembles that match conformational and biophysical property distributions from molecular dynamics (MD), while reducing the computational burden from days of simulation to seconds of generation. We show Cadense ensembles can recover both apo and holo conformations of the same antibody and serve as effective input to physics-based docking, capturing the conformational flexibility important to properly model antibody–antigen interactions. Together, these results establish Cadense as a useful tool for antibody conformational ensemble generation with the promise to enable faster, dynamics-aware antibody design.


## 1 Introduction

Antibodies recognize and neutralize pathogens through specific binding to antigens. Therapeutic antibodies exploit these properties: engineered to bind disease-relevant targets with high specificity, they represent the fastest-growing class of biological drugs and have proven crucial in treating cancers, autoimmune disorders, and infectious diseases [ 1 , 2 ].

The discovery and optimization of therapeutic antibodies has traditionally relied on iterative immunization or display campaigns followed by experimental screening to identify candidates with favorable binding and developability properties [ 3 ]. Structure prediction tools, including AlphaFold2 [ 4 ] and antibody-specific methods such as ImmuneBuilder [ 5 , 6 ], IgFold [ 7 ], and Ibex [ 8 ], have enabled earlier integration of structural information into design workflows [ 9 ]. More recently, co-folding models like AlphaFold3 [ 10 ], Boltz [ 11 ], Chai [ 12 ] and Protenix [ 13 ] have extended this capability to antibody–antigen complex prediction. The development of these machine learning structure and complex prediction methods has made protein structures more widely available and influential for decision-making in drug discovery. Alongside, structure-based machine learning models have driven progress in de novo design [ 14 , 15 ], allowing for scalable, high-throughput generation of candidate binders against target proteins of interest. Despite this progress, the structural methods underlying these advances operate on static snapshots of inherently flexible, dynamic biomolecules, a limitation particularly consequential for antibodies, where conformational diversity in the CDR loops directly mediates function [ 16 , 17 ].

Crystallography captures the state most amenable to packing in the lattice, which may or may not be the binding-competent conformation. Blackler et al. illustrated this by solving 20 diverse structures of the same antibody in the absence of antigen. The conformation matching the antigen-bound geometry was already present among these apo structures, showing that the holo conformation was pre-sampled by antibody-only dynamics [ 18 ]. A broader analysis with ITsFlexible shows that approximately 8% of identical CDR sequences crystallize into distinct structural clusters, and MD reveals flexibility in 84% of CDR-H3 loops versus 64% apparent from crystal structures alone [ 19 ]. Recent coarse-grained MD simulations further confirm that CDR loops exhibit distinct flexibility profiles often underestimated by static structures [ 20 ]. The practical consequences are clear: ensemble-based docking consistently outperforms single-structure approaches [ 21 ], and developability-relevant surface properties, such as hydrophobic patches and charge distributions, shift across conformational states in ways that affect candidate ranking [ 22 – 24 ].

While molecular dynamics can indeed capture this conformational diversity, the computational cost of individual simulations makes it impractical for evaluating large candidate libraries [ 22 ]. Recently, generative machine learning approaches such as AlphaFlow [ 25 ] and BioEmu [ 26 ] have begun to address this, moving beyond static outputs to predicting ensembles of protein structures. Boltz-2 [ 27 ] also integrates dynamic ensembles in their training pipeline to predict biomolecular complexes. Most directly related to the present work, ABodyBuilder4-STEROIDS generates antibody conformational ensembles with a generative model trained on mostly coarse grained antibody molecular dynamics simulations [ 28 ].

There are, however, limitations that block direct application of these methods to therapeutic anti-bodies. BioEmu [ 26 ] operates on single protein chains, so it cannot model an antibody variable fragment with a paired heavy and light chain. Workarounds that diffuse the heavy chain alone and graft loops onto a static light chain introduce clashes at the interface and discard correlated motions between chains [ 29 ]. AlphaFlow [ 25 ] shares this same restriction. Both models also rely on multiple sequence alignments (MSAs) for conditioning signal. For antibodies, whose diversity arises from V(D)J recombination and somatic hypermutation rather than evolutionary divergence, an MSA is an unnecessary input to structure-based models, as shown by performant approaches to MSA-free antibody structure prediction [ 6 – 8 ]. Lastly, ABB4-STEROIDS is trained primarily on coarse grained simulations whose coarse grained representation can obscure sidechain and loop dynamics as a tradeoff for scalable simulation [ 30 ].

We present Cadense ( C onformational A ntibody D iffusion Ense mbles), an equivariant diffusion model that generates diverse antibody conformational ensembles directly from sequence, orders of magnitude faster than simulation. Trained on a large dataset of conventional all-atom molecular dynamics trajectories of antibody Fv regions, Cadense samples CDR loop conformations and backbone flexibility. The model operates on generic backbone frames and torsion angles, replacing MSAs with protein language model embeddings [ 31 ], and contains no antibody-specific architectural inductive biases beyond the training data. Antibodies, with their flexible loops that influence important binding and biophysical properties [ 16 , 22 ], serve as a rigorous testbed for validating this MSA-free ensemble generation framework. We evaluate two training variants of Cadense that share the same architecture but differ in their pretraining schemes and how MD trajectories are shown to the model. The primary model, referred to simply as Cadense, uses a curriculum learning strategy where MD frames are weighted by the equilibrium populations of metastable conformational states identified via tICA and PCCA+ clustering of Markov state models (Section 4.4). A second variant, Cadense- dist , is finetuned on uniformly sampled MD frames (across time) and is used where reproducing continuous distributional properties of the MD ensemble is the focus.

We demonstrate Cadense’s impact in several ways. First, we show that the generated conformational ensembles span important functional states, recovering both apo and holo states for antibodies with paired crystal structures, while also capturing the diversity from simulations, e.g., through comparable root mean square fluctuation (RMSF). Next, we show that Cadense- dist derived property distributions reduce false-positive risk flags 3.5-fold compared to static structure assessment on our curated benchmark, at a fraction of the computational cost of MD. Lastly we look at physics-based docking with Cadense ensembles, where the model’s ability to flexibly capture diverse CDR conformations leads to significantly improved docking performance over static structures. Together, these results establish Cadense as a practical tool for integrating dynamics into structure-based antibody design.


## 2 Results

Unless otherwise noted, results in this section use the primary Cadense model, trained with the curriculum learning strategy described in Section 4.4 , and sampled at normal temperature (see Sec. 4.3) and without guidance. Analyses of per-residue flexibility (RMSF) and biophysical property distributions use Cadense- dist , the variant finetuned on uniformly sampled MD frames, which we find better reproduces the continuous distributional characteristics of the simulation ensemble.


## 2.1 Cadense produces realistic conformational ensembles

A key challenge in antibody structure prediction is capturing the conformational flexibility of CDR loops, particularly CDR-H3. Static structure predictors return a single conformation by construction, and while recent diffusion-based models such as AlphaFold3 and Boltz can generate multiple samples, their outputs are typically concentrated around a single dominant state [ 32 ]. For antibodies, this state is usually the antigen-bound ( holo ) conformation, reflecting the over-representation of bound structures in training data [ 33 ], leaving the apo state unrepresented. For applications like docking or property prediction, analyzing both states, and ideally the ensemble connecting them, is crucial [ 21 , 22 ].

Among the apo – holo pairs that we held out from training (Sec. 4.5), we identified three pairs with significant conformational changes and single them out to demonstrate that Cadense ensembles span both conformational states ( Figure 2 ). Three cases were held out from Cadense training, while the public PDB structures ( 1xf3/2fr4, 4ygv/4yhi, 4s1r ) are present in the training sets of ABodyBuilder3 [ 6 ], Boltz-2, and Ibex [ 8 ]. We also crystallized the antibody found in holo conformation in 4s1r and arrived at the apo structure Apo 2 , which is unseen by all methods. For each case, we generated 500 Cadense samples (followed by light post-hoc filtering) and compared them to predictions from ABodyBuilder3, Boltz-2, and Ibex (both apo - and holo -conditioned modes). To compare predicted CDR-H3 loops to both experimental references, we use the angular distance function d = 2(1 − cos(Δ θ )), averaged over backbone dihedrals ( ϕ, ψ ) and loop residues [ 34 , 35 ]. This alignment-free metric captures local backbone conformation differences; values range from 0 (identical) to 4 (maximally different, i.e. Δ θ = π ) per angle. We plot dihedral distance-to- holo against distance-to- apo for each predicted structure.

Cadense ensembles consistently produced samples close to both apo and holo references, spanning the conformational space between them. Baseline methods clustered tightly near the holo state, which was included in their training, largely missing the apo state. For the Apo 2 → 4s1r case, where all methods attempt to predict a true out-of-distribution conformation, the best Cadense sample achieved lower dihedral distance to both references than any baseline prediction, and the full ensemble covered the range between states ( Figure 2 , bottom row). Aggregated across a broader set of seven antibodies with significant conformational changes (ranked by H3 RMSD between apo and holo ), Cadense was the only method to consistently place samples near both references in both dihedral distance and RMSD ( Supplementary Figure A1 ).

A second internally crystallized structure, Apo 1, is likewise unseen by every method evaluated here and shows the same behavior ( Figure 1d ). The Cadense ensemble recovers the CDR-H3 loop conformation, with the best sample reaching sub-angstrom RMSD to the apo state, while Boltz-2, Ibex in apo mode and ABodyBuilder3 remain further away in both dihedral distance and RMSD. Together with Apo 2, this gives two experimentally determined out-of-distribution cases in which the ensemble contains the crystallographic conformation. In order to provide some labeling to the ensembles, we defined two scores, centrality and support , described briefly in Fig. 3 and in full detail in Appendix B. As shown in the Figure, restricting to the supported and high centrality subset of the ensemble allowed the identification of structures more similar to the experimental apo and holo conformations.

Beyond capturing discrete apo and holo states, a useful ensemble model should reproduce the continuous per-residue flexibility profile observed in MD simulations. We evaluated this using Cadense- dist , the variant finetuned on uniformly spaced MD frames, by computing the C α root-mean-square fluctuation (RMSF) from Cadense- dist and Boltz-2 ensembles and correlating it with MD-derived RMSF across 22 held-out antibodies from pOAS, selected to be absent from public structural databases ( Figure 4a ). Cadense- dist ensembles achieved a median Pearson correlation with MD of 0.84, compared to 0.57 for Boltz-2, with notably lower variance. Per-residue traces for representative cases ( Figure 4b, c ) illustrate that Cadense- dist closely tracks the MD flexibility profile across both CDR loops and framework regions, capturing peaks at CDR-H3 and other flexible segments. In contrast, Boltz-2 ensembles substantially underestimate flexibility throughout the Fv, producing near-uniform low RMSF values that fail to distinguish flexible loops from rigid framework. These results confirm that Cadense- dist ensembles encode physically meaningful conformational diversity, not merely structural noise, and that this diversity is calibrated to match the dynamics learned from simulation data. In Supplementary Figure A2 , we show that Cadense- dist ensembles converge to this correlation quickly, within roughly 50 inference structures. We further compare CDR-H3 ensemble diversity against MD for Cadense, Cadense- dist , Boltz-2, ABB4-STEROIDS and ITsFlexible in Supplementary Figure A3 .


## 2.2 Cadense ensembles are useful for property flagging and developability

Antibody developability assessment relies on surface properties like hydrophobicity and charge, which are typically computed from static predicted structures. However, these properties vary significantly across conformational ensembles, and static models introduce systematic biases that dynamics can correct [ 22 ]. Running MD for every candidate is not tractable at early stages in drug discovery, where screening libraries may contain hundreds to thousands of molecules. We asked whether Cadense- dist generated ensembles, which can be sampled in under a minute per antibody (Supplementary Table A1), could replace time consuming MD simulations for property estimation.

We identified N = 72 test case antibodies excluded from training. Fifty-five antibodies were chosen from our simulation dataset based on disagreements between ensemble-averaged biophysical properties and those calculated from the first frame of the MD trajectory. The remaining 17 were selected as controls where first-frame and ensemble-averaged properties agreed. Agreement was assessed using risk flags [ 22 ]: properties exceeding the 95th percentile of clinical-stage therapeutics are flagged red (high risk), those between the 90th and 95th percentile amber (medium risk), and those below the 90th percentile green (acceptable). A disagreement was defined as any case where the first-frame flag differed from the ensemble-averaged flag for a given property.

Cadense- dist ensembles reduced false red flags 3.5-fold compared to static snapshots, here the first frame of the MD trajectory ( Figure 5a ) on our curated benchmark. Generated ensembles produced only 4 green → red misclassifications versus 14 for the first-frame baseline. Overall, Cadense- dist ensembles achieved higher accuracy across all flag categories, with particular improvements in green and amber classification and red precision ( Figure 5b ).

Figure 5c illustrates the distributional agreement between MD and generated ensembles for representative antibodies chosen from the properties test set to cover diverse regions of surface property space, characterized by CDR surface hydrophobicity, computed as a hydrophobic patch score over the CDR surface on the Wimley–White scale ( CDR HPATCH WW ), and CDR electrostatic potential, computed from a

Poisson–Boltzmann treatment (APBS) summed over the CDR surface ( CDR APBS sum ). Contours overlap closely, confirming that Cadense- dist ensembles reproduce the property distributions sampled by MD.


## 2.3 Cadense ensembles are effective input to physics-based docking

We now turn to physics-based docking with ensembles, building off the observation that binding-competent paratope conformations can be found in ensembles even starting from apo conformations [ 18 , 21 ], and that this can translate into an effective approach for ensemble-based docking from dynamics.

Here we show that Cadense ensembles capture the conformational diversity relevant to binding, and improve docking outcomes over static predictors. We test this hypothesis at scale on 44 internal antibody– antigen complexes, comparing Cadense ensembles against single-structure baselines ABodyBuilder3 and Ibex- holo 1 and Boltz-2 cofolding, using HADDOCK3 [ 36 ] for physics-based docking.

We adapted the ensemble-docking protocol of Ref. [ 21 ] to HADDOCK3 to isolate the contribution of paratope conformational sampling from global search. Antibody structures were pre-aligned to the holo antigen pose, and the bound antigen conformation was used throughout. To suppress global rigid-body search, we disabled random initial orientations, applied center-of-mass restraints, and limited the rigidbody stage to a single model with reduced van der Waals weighting to prevent rejection of input poses by clash-sensitive scoring prior to refinement. Local interface optimization was performed by flexible refinement ( flexref ) and final energy minimization ( emref ), yielding 50 docked poses per input structure. Ambiguous interaction restraints were defined from the ground truth complex paratope and epitope. For each input structure, we retained the best HADDOCK-scored as that structure’s representative.

For single-structure methods (ABodyBuilder3, Ibex- holo ) this yields one final prediction. For Cadense, representatives from each ensemble member were then ranked by HADDOCK score, and we evaluated selection at Top-1 and Top-5 (averaging DockQ across the top-ranked poses). We also report an oracle selector that chooses the highest-DockQ representative as an upper bound what a perfect scoring function could extract from the ensemble.

We also include Boltz-2 cofolding as a reference point for full complex prediction. This is purely for a reference noting the difficulty of these models to generalize outside their training distribution [ 8 ]. Boltz-2 predicts the complex directly from sequence and is reported here as the best DockQ across 100 seeds.

Cadense ensembles with HADDOCK-based selection outperformed single-structure baselines ( Figure 6 ); broadening selection to the Top-5 docks further improved the score, suggesting that the HAD-DOCK score is a reasonable selection criterion for dock quality. These results indicate that the Cadense ensemble reliably contains high-quality docking solutions, and that simple scoring functions can identify them. However, the oracle performance does offer better performance overall, showing that optimally picking the best complex is still open for further development [ 38 , 39 ].

To assess generalization, we stratified results by CDR-H3 edit distance to the nearest public sequence ( Figure 6 ). For antibodies with novel CDR-H3 loops (edit distance 7+), single-structure methods showed degraded performance, while Cadense ensembles maintained higher scores. This suggests that conformational sampling provides robustness to distributional shift, precisely where single-structure predictors struggle most.


## 3 Discussion

Cadense generates diverse conformational ensembles of antibody structures from sequence alone, useful for sampling beyond static structures (including binding-relevant apo and holo conformations), computing biophysical properties, and as input for docking. While molecular dynamics has demonstrated utility in these areas, Cadense ensembles offer a faster alternative, scalable to early stage antibody discovery and design.

Cadense moves beyond the limitations of existing structure prediction tools, which produce a single conformation by construction or, in the case of generative models trained primarily on crystal structures like Boltz-2, tend to cluster around a dominant mode. Our diffusion ensembles produce structures near both experimental apo and holo references for held-out test antibodies, most notably for Apo 1 and Apo 2 , two new structures we crystallized in-house that were unseen by all methods. We release both to the Protein Data Bank (accession codes 38LM for Apo 1 and 38LO for Apo 2 ) as a resource for benchmarking antibody ensemble generation. Our docking results reinforce this point: diverse sampling, particularly in CDR loops, provides robustness to distributional shift precisely where single-structure methods struggle most, as evidenced by maintained performance on antibodies with novel CDR-H3 sequences ( Figure 6 ). On biophysical properties, Cadense- dist demonstrates immediate value. Screening can be a useful tool for antibody discovery and engineering, but false red flags waste resources by eliminating viable candidates at early stages. The 3.5-fold reduction in green → red misclassifications translates directly to more calibrated filtering, offering an obvious replacement for computing biophysical properties from static structures without an additional time requirement.

While we provide the centrality and support scores to help label the ensembles, these constructions are still not explicitly labeling which samples may be most apo -like or holo -like. Learning such a score is a promising direction for future work, potentially through learned selectors trained on docking outcomes [ 38 , 39 ], which could help recover the oracle-level performance in docking (0.60 against 0.41 mean DockQ). However, even unlabeled, the ensembles have meaningful practical utility. For docking, ranking by HADDOCK score recovers high quality docks from the ensemble candidates, better than static structure baselines. Property estimation operates at the ensemble level, and we show ensemble-averaged flags track MD reference risk flags more closely than any single structure. Lastly, since we demonstrate coverage of the conformational space by recovering experimental conformations ( Fig. 2 ) and correlating with RMSF from dynamics ( Fig. 4 ), this opens up the possibility of flexibility screening for designs. As CDR rigidity is already linked to binding affinity [ 16 , 17 ], Cadense allows for flexibility to be considered across large libraries of designed antibodies.

Several limitations warrant discussion. Cadense learns the conformational distribution present in its training data and cannot extrapolate to motions or states absent from that data, in particular conformational changes on timescales beyond those sampled with our short 200 ns conventional simulations. Accordingly the model also does not yield kinetic information, which is another extension we leave for future work. Our docking benchmark uses holo antigen structures for pre-alignment [ 21 ] and restraints for both paratope and epitope, so performance in more general settings remains to be considered. Finally, the current model operates on Fv regions only; extension to full-length antibodies or other modalities would require an expanded simulation dataset for training. In the same vein, the current framework models antibody dynamics in isolation; explicitly incorporating the antigen and modeling conformational dynamics on the target side is a natural extension, though it would likewise require corresponding complex simulation data.

Looking forward, incorporating experimental observables from nuclear magnetic resonance [ 40 ] or hydrogen–deuterium exchange [ 41 ] for inference-time guidance [ 42 ] or train-time experimental finetuning [ 26 ] could aid the diversity and generalizability of generated ensembles. More broadly, this work suggests that generative models trained on simulation data can serve as efficient surrogates for physics-based sampling across protein classes where conformational flexibility impacts function and throughput constraints limit MD usage. Cadense enables routine access to antibody conformational ensembles, allowing for important aspects of the dynamic nature of antibodies to inform earlier stages of antibody design and discovery.


## 4 Cadense model

In this section we describe the model architecture, diffusion formulation, sampling procedure, and training data used to build Cadense; full algorithmic details and derivations are provided in the supplementary materials.


## 4.1 Architecture overview

Cadense follows a two-component design ( Figure 1a ): (1) an input conditioner that performs initial featurization through compute-intensive layers, and (2) a lighter-weight score model that performs denoising diffusion of protein structure. This split amortizes the cost of the input conditioner, which is evaluated once per sequence, across all diffusion timesteps.

We represent protein geometry using backbone rigid frames for each residue i —translations t i ∈ ℝ 3 and rotations r i ∈ SO(3) derived from C α , N, and C atoms ala AlphaFold2 [ 4 ]—together with five torsion angles χ iq ∈ SO(2), q ∈ { 0, …, 4 } , per residue (one backbone oxygen torsion and four side-chain dihedrals).

The input conditioner initializes single (per-residue) and pair (per-residue-pair) representations from sequence features, including protein language model embeddings [ 31 ] and relative position encodings, then refines them through Pairformer-style attention blocks analogous to AlphaFold2 and AlphaFold3 [ 4 , 10 ]. To improve computational efficiency, we use a form of semi-local triangle attention and triangle multiplication operations inspired by Proteus [ 43 ], reducing the naїve O ( n 3 ) complexity to O ( kn 2 ) for coordination number k ≤ n and total number of residues n .

The score model is built on the Equiformer architecture [ 44 ], a graph attention network incorporating SE(3)-equivariant components based on irreducible representations of SO(3). We restrict steerable features to maximum order L max = 1 (scalars and vectors) and use depth-wise Clebsch–Gordan tensor products to manage computational cost in the interaction layers. The message-passing graph is constructed using k -nearest neighbors supplemented with random long-range edges sampled with inverse-cubic radial propensity, following Chroma [ 45 ]. Following Equifold [ 46 ], we employ a hierarchical message-passing scheme with three node types: backbone nodes (one per residue), side-chain nodes (each connected only to their parent backbone node), and a global auxiliary node fully connected to all backbone nodes that maintains a latent representation of the system state (Appendix F).


## 4.2 Diffusion formulation

Structure generation is realized by a joint Riemannian diffusion model over the product manifold SE(3) × SO(2) 5 defined by rigid backbone frames, SE(3) = SO(3) ⋉ ℝ 3 , and side-chain torsion angles [ 47 ]. For backbone translations, we use a variance-preserving (VP) schedule with a geometric progression [ 48 ], constraining translations to the zero center-of-mass subspace [ 49 ]. The stationary distribution is a zero-center-of-mass projected normal distribution with isotropic covariance scaled by physical length units. For backbone rotations, we use a variance-exploding (VE) schedule [ 50 ] where the forward process corresponds to Brownian motion on SO(3), and the stationary distribution is the Haar measure, i.e., the high-noise limit of the IGSO(3) heat kernel [ 49 ]. Side-chain torsions similarly follow a VE schedule on SO(2), where the stationary distribution is again the Haar measure, in this case the high-noise limit of the wrapped normal distribution [ 51 ].


## 4.3 Sampling

Baseline sampling uses Euler–Maruyama discretization of the time-reversed SDEs over SE(3) × SO(2) 5 . Following Chroma [ 45 ], we implement hybrid Langevin dynamics to control the trade-off between sample diversity and quality. This introduces a temperature-like rescaling parameter λ 0 , where λ 0 > 1 emphasizes high-likelihood states, together with an equilibration factor ψ > 0 that introduces annealed Langevin dynamics to improve mixing across multimodal distributions. When guidance potentials are applied (see below), we include up to 5 corrector steps per predictor step following annealed Langevin dynamics [ 50 ] to ensure adequate mixing under the additional gradient fields.

At generation time, auxiliary guidance potentials can be composed with the learned score to steer sampling toward desired structural properties. Gradients of these potentials are incorporated into both predictor and corrector steps of the reverse dynamics. We use guidance based on AlphaFold2 structure violation losses [ 4 ] to reduce steric clashes in generated structures; further details and the impact of guidance on sample quality are provided in Appendix H.3.

Generated structures pass a post-hoc geometric quality filter (Appendix A.1); comparator methods are evaluated unfiltered, and rejected samples count against the Cadense generation budget.

Unless otherwise noted, results use the normal-temperature setting λ 0 = 1, ψ = 0 without guidance. Generated structures pass a post-hoc geometric quality filter (Appendix A.1); comparator methods are evaluated unfiltered, and rejected samples count against the Cadense generation budget.


## 4.4 Training data and strategy

Cadense is trained on molecular dynamics trajectories of 13,192 unique antibody Fv sequences. Sequences were drawn from SAbDab [ 52 ], TheraSAbDab [ 53 ], and pOAS [ 54 ], with subselection strategies designed to maximize diversity in sequence space and surface properties (Appendix D). Initial structures were predicted with ESMFold [ 31 ] and refined with Rosetta [ 55 ], then used to initiate 200 ns molecular dynamics simulations using the Amber FF14SB force field [ 56 ] with TIP3P water (Appendix D).

For training, we extract frames from the production trajectories and represent each as backbone frames and torsion angles. We evaluate two strategies for frame selection during the MD finetuning stage. The primary model (Cadense) uses a curriculum learning strategy, and trajectories are clustered before training. For clustering, we first projected CDR backbone dihedral features with tICA [ 57 ], constructed a Markov state model, and then applied PCCA+ [ 58 ] clustering to identify metastable conformational states; all of this was done using the PyEMMA package [ 59 ] (Appendix E). Training frames are then sampled proportionally to the stationary distribution of the MSM, weighting the data toward equilibrium-populated metastable states. The second variant (Cadense- dist ) uses uniformly spaced frames from each trajectory, providing broader temporal coverage of the simulation ensemble. Both variants share the same architecture and have one stage of crystal-structure pretraining. In contrast to the three-stage curriculum strategy of the base Cadense model, Cadense- dist has a pretraining stage on crystal structures (no synthetic data) and is finetuned on equally spaced MD frames. We find the first recovers discrete functional states more sharply, while the second better reproduces continuous distributional quantities such as RMSF and biophysical property distributions.

Cadense : base model, three-stage curriculum learning, uses clustered MD frames for training

Cadense- dist : MD distribution specialist model, pretrained on experimental crystal structures, finetuned on equally spaced MD frames

Both models are trained to denoise structures corrupted according to the noise schedules described in Appendix G.1, with a piecewise-linear timestep sampling scheme that samples uniformly for t > 0.25 (below which structures are essentially resolved given the noise schedules).


## 4.5 Held-out evaluation sets

Three held-out sets were constructed for the analyses in Section 2:

Apo/holo pairs . A set of 33 antibodies with paired apo and holo crystal structures.

Biophysical properties and RMSF evaluation . A set of 72 antibodies chosen for biophysical property analysis. The selection criteria are further detailed in Section 2.2 ; a subset of these structures (N=22 antibodies from pOAS) was used for the RMSF evaluation in Fig 4 .

Internal crystal structures . Two Fab structures, Apo 1 and Apo 2, expressed, purified and crystallized in-house (Appendix C).

To prevent data leakage between training and our evaluation sets, we clustered all the sequences from the curriculum learning dataset in Fig. 1 against the held-out sequence sets using MMSeqs2 [ 60 ] at 80% sequence identity, and clusters overlapping with the test set were also held out from training.


## Acknowledgements

We thank the staff of the Shanghai Synchrotron Radiation Facility (SSRF) beamline BL02U1, where diffraction data were collected and Yanshu Dou and colleagues at Viva Biotech for work related to the crystal structures. We thank Feng Wang and Hong Li for their coordination of protein purifications.


## Appendix A Supplementary tables & figures


## A.1 Structural quality control of generated antibody ensembles

We applied post-generation structural quality control (QC) to Cadense-generated Fv structures. Input structures were standardized to contain heavy and light chains labeled H and L. A structure was retained only if it passed all of the following checks: Here, is the minimum inter-chain C α –C α distance; L Fv is the number of heavy- and light-chain C α residues; and N clash is the number of atom pairs belonging to different residues that are separated by at most 2.0 Å. The clash criterion (second line) therefore sets a clash budget that scales with system size, retaining a structure only if it contains at most 1.2 such clashing atom pairs per Fv residue; it limits steric overlaps and is not a filter on the number of residues.

CDR-H3 residues were defined using AHo numbering. For each evaluable H3 residue, the backbone ϕ and ψ angles were compared with the 90 × 90 MDAnalysis Ramachandran reference grid. Residues outside the retained reference contour (grid value below 1.0, corresponding to the MDAnalysis 99% reference contour) were counted as Ramachandran outliers. The permitted number of outliers therefore scaled with H3 length, L H3 .

The dimensionless VH–VL separation score was defined as where µ H and µ L are the C α centroids and R g,H and R g,L are the corresponding C α radii of gyration. Peptide-bond planarity was evaluated over both chains using ω = C α,i –C i –N i +1 – C α,i +1 . A peptide bond was classified as an omega outlier when its dihedral was more than 30 ° from both the cis (0 ° ) and trans ( ± 180 ° ) states. Structures with no evaluable omega angles, or with any parsing or scoring error, failed QC. All thresholds were inclusive.

QC was treated as part of the Cadense generation protocol and was therefore used to filter only Cadense structures. Comparator methods were evaluated without post-hoc structural filtering. Cadense structures rejected by QC still counted toward the raw generation budget, and endpoint statistics were calculated from the retained Cadense structures.


## Appendix B Ensemble-derived centrality and support scores

We use centrality to describe a generated member’s position relative to the center of its ensemble and support to describe the recurrence of similar conformations across subsets of that ensemble. We calculate both scores within each antibody’s QC-passing ensemble using CDR-H3 ϕ, ψ angles. The calculation uses generated structures, sequence-derived residue correspondence, and sample identifiers; experimental coordinates and distances to the apo/holo references enter only the subsequent visualization and evaluation.


## B.1 Centrality (closeness to ensemble medoid)

For an ensemble of n members, let θ it denote angle t of member i , with T = 2 L angles for a CDR-H3 loop of L residues. We match CDR-H3 residues using AHo numbering and calculate the pairwise (square-root) dihedral distance This distance represents each angle by its sine and cosine and respects angular periodicity; we use this same metric to compare ensemble members distance to experimental apo and holo conformations in Fig. 2 .

We first identify the ensemble medoid, the generated member with the smallest mean distance to the other members: We then assign centrality by the empirical rank of a i , with higher scores for members closer to the medoid: Here 1 {·} is the indicator function. The ranking includes the member itself and assigns equal centrality to equal medoid distances. We resolve a medoid tie by input order and calculate centrality on the full QC-passing ensemble before support filtering. We keep these scores fixed during subset selection.


## B.2 Support (recurrence across folds)

We construct B = 20 reproducible partitions of the same ensemble into K = 5 disjoint folds. For each partition, we assign folds by a deterministic hash of the antibody identifier, sample identifier, and partition index. Let be fold g in partition b , and let identify the fold containing member i . We find the nearest neighbor of i in each of the four other folds and take the median of these distances: Small values indicate that the member has close conformational matches across several folds. The partitions reuse one generated ensemble; they do not correspond to separate generation runs.

To account for variation in neighbor spacing across the ensemble, we compare recurrence distances among members at similar distances from the medoid. We sort the members by a i using a stable sort and define a local comparison window W i around each member’s rank. The window contains w 0 = min {n , max[51, ⌈ 0.10 n⌉ ] } members. We increase an even w 0 by one when w 0 < n and shift the window at either end of the ordering to preserve its size. Within each partition, we rank against the recurrence distances in W i , then take the median of these scores across partitions: Higher support therefore indicates closer cross-fold recurrence than for other members at comparable medoid distances. This local comparison reduces the tendency to assign low support to peripheral members solely because their neighborhoods are sparser. It does not require support and centrality to be statistically independent.


## Appendix C Crystallography details


## C.1 Protein expression and purification, crystallization, and structure determination

Fab proteins were expressed and purified as previously described [ 61 ] and concentrated to 10 mg/mL, respectively, and crystallized in various PEG and ethylene glycol solutions. Crystals were cryocooled in liquid nitrogen, in their growth conditions supplemented with ethylene glycol. Diffraction data were collected at synchrotron sources, and those data were scaled using XDS [ 62 ] or HKL2000 [ 63 ]. The structures were determined by molecular replacement, using PHASER [ 64 ], and the models were adjusted in COOT [ 65 ] and refined in PHENIX [ 66 ] (Table C2). The data set for the Apo 1 structure showed significant anisotropy, with spherical completeness > 50% in the highest resolution bin occurring at 2.8 Å resolution and elliptically truncated data to 2.5 Å resolution utilized in refinement. The CDR regions of the Fabs were generally well ordered in the electron density maps ( Figure C4 ).


## Appendix D Large antibody molecular dynamics dataset


## D.1 Sequence selection

The dataset comprises 13,192 unique antibody Fv sequences drawn from three sources: the Structural Antibody Database (SAbDab) [ 52 ], the Therapeutic Structural Antibody Database (TheraSAbDab) [ 53 ], and the paired Observed Antibody Space (pOAS) [ 54 ]. From SAbDab and TheraSAbDab, we selected all non-redundant antibody sequences available as of January 2024. For pOAS, which contains over 2 million sequences, we applied two complementary subselection strategies. The first intentionally oversampled sequences with extreme surface patch properties, specifically Fv surface electrostatic potential (calculated via APBS) and spatial aggregation propensity (SAP BM ) scores. The second maximized diversity across V-gene usage, Fv and CDR lengths, clonotype, and predicted biophysical properties including charge and hydrophobicity. All sequences were selected based on the Fv region.


## D.2 Structure prediction and refinement

Selected Fv sequences were folded using ESMFold (3B parameters) [ 31 ], which generates structure predictions end-to-end from sequence using the ESM-2 language model. To ensure Fv stability, sequences were folded as Fabs using the Herceptin constant domain as a template. Predicted structures were then minimized in Rosetta using the default score function with a custom disulfide bond energy weight of 10.0. Both backbone and sidechain dihedrals were allowed to move during minimization, which used the L-BFGS Armijo nonmonotone algorithm.


## D.3 Molecular dynamics simulations

Simulations were initiated from the ESMFold-predicted and Rosetta-minimized structures. Hydrogen atoms were added using PROPKA [ 67 ] at pH 7.4, and protonation states were assigned using PDB2PQR [ 68 ] with the Amber FF14SB force field [ 56 ]. Each antibody was solvated in a cubic box of TIP3P water with a 10 Å buffer from the protein surface, and the system was neutralized with NaCl ions.

System preparation proceeded as follows: (1) 2,000 steps of conjugate-gradient energy minimization; (2) 0.5 ns heating to 300 K under isothermal-isobaric (NPT) conditions with harmonic restraints on the protein (10 kcal mol -1 Å -2 ); (3) an additional 2,000 steps of unrestrained conjugate-gradient minimization; (4) 0.5 ns NPT equilibration at 1 atm and 300 K with restraints (10 kcal mol -1 Å -2 ); (5) 1 ns equilibration with reduced restraints (1 kcal mol -1 Å -2 ); and (6) final unrestrained equilibration at 300 K.

Production simulations were carried out under NPT conditions using hydrogen mass repartitioning (HMR), enabling a 4 fs timestep. Temperature was maintained at 298 K using Langevin dynamics with a collision frequency of 3 ps -1 . Periodic boundary conditions were applied in all directions, electrostatic interactions were calculated using the particle mesh Ewald method [ 69 ] with a real-space cutoff of 10 Å, and hydrogen bond lengths were constrained with the SHAKE algorithm [ 70 ]. Each simulation was run for 200 ns on NVIDIA A100 GPUs, requiring approximately 12 hours per trajectory.


## Appendix E MSM and PCCA+ conformational clustering

We used a time-resolved clustering procedure to identify metastable conformational states in the molecular dynamics trajectories used for Cadense training. The models fitted here are used only to bias frame selection during training, not to estimate thermodynamic quantities. With 200 ns trajectories, the fitted MSMs give an approximate rather than a converged description of the underlying dynamics; we rely on them for the relative weighting of conformational states within a trajectory, and model quality is assessed against experimental structures and MD-derived observables rather than against the MSM itself.

For each trajectory, we extracted the backbone ϕ and ψ dihedral angles for the six antibody complementarity-determining regions (CDRs): H1, H2, H3, L1, L2, and L3. Because dihedral angles are periodic, we represented each angle θ using its sine and cosine, which avoids an artificial discontinuity between π and π . The resulting feature vector described the CDR backbone conformation at each trajectory frame.


## E.1 tICA projection and microstate assignment

We projected each dihedral feature trajectory onto time-lagged independent components using PyEMMA’s tICA implementation. We used a lag time of 50 frames and retained the first 30 components. The tICA coordinates were scaled using the kinetic-map convention, which weights each component according to its relaxation timescale and contribution to slow configurational dynamics. The trajectories used a frame spacing of 0.1 ns, so the tICA lag corresponded to 5 ns.

We then applied K-means clustering in the 30-dimensional tICA space. Each trajectory was partitioned into 150 microstates using a fixed random seed of zero. The number of microstates was fixed across all trajectories rather than selected per system. The resulting sequence of discrete microstate labels provided the input for Markov state model estimation. We used the tICA projection for both the dynamical state assignment and the subsequent selection of representative structures.


## E.2 Markov state model estimation

We estimated a reversible Markov state model for each trajectory from its discrete microstate sequence; reversibility is imposed by the estimator rather than tested. To select the MSM lag time, we evaluated lag times between 0.1 and 2.0 ns. For each candidate lag time, we calculated the leading five implied timescales, and selected the first lag time at which all five changed by less than 20% relative to the next tested lag time. The selected lag time could therefore vary between trajectories. We treat this as a practical heuristic for lag-time selection rather than as evidence of Markovianity; at these trajectory lengths the implied timescales are not expected to be fully converged.

At the selected lag time, we fit a reversible Bayesian Markov state model using 200 posterior samples. When Bayesian estimation failed, we used the corresponding reversible maximum-likelihood MSM. The stationary distribution of the fitted MSM provided a stationary weight for each microstate under that model.


## E.3 PCCA+ macrostates and representative structures

We applied PCCA+ to each fitted MSM and grouped the 150 microstates into 12 metastable macrostates, again using a fixed number across all trajectories. PCCA+ uses the slow dynamical modes of the MSM to group microstates that exchange rapidly with one another while separating states connected by slower transitions. For each macrostate M k , we calculated its stationary weight by summing the stationary probabilities of its constituent microstates, where π i denotes the MSM stationary probability of microstate i . We normalized the resulting macrostate weights for use during training-frame selection.

We selected up to 10 structural representatives from each macrostate. For every microstate, we identified the trajectory frame closest to its K-means centroid in tICA space. We calculated the centroid of the microstates assigned to each PCCA+ macrostate and selected the microstate representatives closest to this macrostate centroid. The corresponding trajectory frames were written as representative PDB structures. This procedure preserved the dynamical organization supplied by the MSM and selected structures near the geometric center of each metastable state.

The resulting PCCA+ macrostate weights defined the curriculum used for the primary Cadense model. Frames associated with more heavily weighted macrostates received greater sampling weight, whereas uniformly spaced frame selection was used for the Cadense- dist variant. The two models therefore used the same structural and dihedral representations but differed in whether MD frames were sampled according to MSM-derived stationary weights or temporal spacing.


## Appendix F Model architecture details


## F.1 Protein geometry parameterization

We parameterize each residue by a backbone rigid frame—a translation t i ∈ ℝ 3 and rotation r i ∈ SO(3), derived from the C α , N, and C backbone heavy atoms following AlphaFold2 Algorithm 21 [ 4 ]—together with five torsion angles χ iq ∈ SO(2) for q ∈ { 0, …, 4 } . Here χ 0 ≡ ψ is the backbone oxygen torsion and χ 1 , …, χ 4 are the four side-chain dihedral angles. For residue types with fewer than four side-chain torsions, the extra angles are masked during inference according to the fixed residue identity. The state of a system is specified by {t i }, {r i }, {χ iq } , collectively denoted Z .


## F.2 Input feature embedding

The InputFeatureEmbedder initializes single (per-residue, ) and pair (per-residue-pair, ) representations for the input conditioner. Single representations are constructed from:

One-hot encoded amino acid identity

Protein language model embeddings from ESM-2 [ 31 ]

Per-residue confidence features

Noise level embeddings via learned lookup tables

These are concatenated and projected through a linear layer (without bias). Pair representations are initialized from relative position encodings based on residue index and chain index, following AlphaFold2 and AlphaFold3 [ 4 , 10 ].


## F.3 Input conditioner

The input conditioner constitutes the computational bulk of the model. Single and pair embeddings from the InputFeatureEmbedder are passed through a 1D–2D mixing layer (outer product of single representations added to pair representations), then refined through N cycles Pairformer blocks. Each Pairformer block includes triangle attention across rows and columns of the pair representation, triangle multiplicative updates, and single-representation attention, analogous to the Evoformer/Pairformer stacks in AlphaFold2/3 [ 4 , 10 ].

To improve computational efficiency, we use semi-local variants of triangle attention and triangle multiplication following Proteus [ 43 ]. Attention coefficients, which are rank-3 tensors for triangle attention, are sparsified using a neighborhood sampling scheme: k -nearest sequence neighbors plus random graph edges (without radial propensity sampling, to avoid leaking geometric information into the input conditioner). This reduces the computational complexity from O ( n 3 ) to O ( kn 2 ) for coordination number k ≤ n and n residues.

At each recycling iteration, the single and pair representations from the previous cycle are added (after layer normalization and linear projection) to the current representations before entering the Pairformer stack. The final single { s i } and pair { z ij } embeddings, along with their initial representations and , serve as conditioning information for the diffusion module.


## F.4 Diffusion conditioner

At each diffusion timestep, the conditioning embeddings are updated by the DiffusionConditioner before being passed to the score model. This module:

Concatenates current single/pair embeddings with their initial (pre-Pairformer) versions

Adds self-conditioning information: the output single and pair embeddings from the previous diffusion timestep (initialized to zero for the first step), following RFdiffusion [ 71 ] and Proteus [ 43 ]

Incorporates a learned time embedding via sinusoidal encoding projected through layer normalization and a linear layer

Refines through N transition transition blocks (2-layer MLPs with residual connections)


## F.5 Score model

The score model predicts denoising scores for all geometric degrees of freedom given the current noised structure Z ( t ) and conditioning embeddings.

Backbone coordinates t i are used to construct a message-passing graph G with k = 32 nearest-neighbor edges plus f = 32 random long-range edges sampled with inverse-cubic radial propensity, following Chroma [ 45 ].

The pair embeddings z ij within the score model are augmented with geometric features derived from the current structure, including backbone distance (distogram), planar angles, and dihedral angles between connected residues. These provide the score model with information about the current structural state at each diffusion timestep, biasing the local triangle attention updates with physically relevant geometric context.

The conditioning single and pair embeddings are first refined through Pairformer blocks with triangle attention restricted to the edges of the local graph G , reducing computational cost relative to full-attention Pairformer blocks in the input conditioner.

The core of the score model uses the Equiformer architecture [ 44 ], a graph attention network with SE(3)-equivariant message passing based on irreducible representations of SO(3). We restrict steerable features to maximum order L max = 1, i.e., scalar ( L = 0) and vector ( L = 1) features, and use depth-wise Clebsch– Gordan tensor products to reduce computational complexity. (We do not use the eSCN tensor product simplifications from Equiformer V2 [ 72 ], as the gains are minimal at L max = 1.)

Side-chain torsion angles are mapped to global SE(3) frames following Equifold [ 46 ], producing 6 frames per residue (1 backbone + up to 5 torsion-derived). Each global frame is assigned a node in the equivariant layers with initial features derived from the backbone rotation and sequence embeddings.

We employ three tiers of nodes in the equivariant layers:

Backbone (BB) nodes : one per residue, connected via the Chroma-style graph G

Side-chain (SC) nodes : one per global frame (excluding the backbone frame), connected only to their parent BB node. Initial BB featurization includes a directed message-passing step from SC to BB nodes

Global auxiliary node : a single node holding a latent representation of the full system state, fully connected to all BB nodes

Message passing alternates between: (1) directed aggregation of all BB features to the auxiliary node, and (2) standard message passing across the combined graph of BB nodes and the auxiliary node. This hierarchy avoids the O ( n BB ×n SC ) cost that would arise from building a full radial graph over all backbone and side-chain nodes, while still enabling side-chain information to influence backbone denoising through the hierarchical update.


## Appendix G Diffusion process details


## G.1 Forward processes and noise schedules

We apply independent diffusion processes to each type of geometric parameter, using a variance-preserving (VP) process for translations and variance-exploding (VE) processes for rotations and torsions, following Song et al. [ 50 ].

Backbone translations t i are constrained to zero center-of-mass (∑ i t i = 0), following FrameDiff [ 49 ]. The noise schedule follows a geometric progression with an implicit physical length scale, parameterized following Kingma et al. [ 48 ]. The stationary distribution is a zero-center-of-mass projected normal with isotropic diagonal covariance scaled by physical units. Minimum and maximum noise scales are 0.05 Å and 300.0 Å, respectively.

Backbone rotations follow Brownian motion on SO(3) with a variance-exploding schedule [ 50 ]. The stationary distribution is the uniform Haar measure, i.e., the high-noise limit of the IGSO(3) heat kernel. Minimum noise scale is 0.035 rad.

Side-chain and backbone oxygen torsion angles follow Brownian motion on SO(2) with a VE schedule [ 50 ], following DiffDock [ 51 ]. The stationary distribution is the uniform measure on SO(2) (the high-noise limit of the wrapped normal distribution). Torsion angles with π -periodicity are handled specially in loss calculations based on residue identity. Minimum noise scale is 0.035 rad.

Setting noise schedules simultaneously across parameter types is nontrivial. Following Biroli et al. [ 73 ], we calibrated schedules so that the symmetry-breaking phase transitions for different degrees of freedom occur at approximately the same diffusion time. We estimated approximate transition scales as 1.0 Å for translations and 0.2 rad for rotations and torsions. Given minimum noise levels (set to expected data noise scales) and these transition scales, maximum noise levels were determined from the functional forms of the schedules and further adjusted empirically.


## G.2 Correlated noise for zero-center-of-mass translations

The zero-center-of-mass constraint on translations induces correlations in the noise distribution. The covariance matrix of the stationary distribution for translations within a residue group of n residues is given by , where σ is the schedule-dependent noise scale. Sampling is performed by drawing from an unconstrained normal and projecting onto the zero-center-of-mass subspace.


## Appendix H Sampling details


## H.1 Reverse diffusion

Baseline reverse-diffusion sampling uses Euler–Maruyama discretization of the time-reversed SDEs over SE(3) × SO(2) 5 . We use evenly spaced timesteps (corresponding to ρ = 1 in the EDM parameterization of Karras et al. [ 74 ]).


## H.2 Hybrid Langevin dynamics

Following Chroma [ 45 ], we implement hybrid Langevin dynamics to control the diversity–quality tradeoff. The target distribution is rescaled as , where λ 0 > 1 is a low-temperature regime emphasizing high-likelihood states. This induces a time-dependent rescaling of the scores of the form λ t = F ( λ 0 , σ t ), where the functional form of F depends on the noise schedule and the manifold of the given degrees of freedom.

To compensate for inadequate reweighting of relative populations across modes under simple score rescaling, we introduce an equilibration factor ψ > 0 that adds a component of slow, annealed Langevin dynamics [ 50 ]. The reverse step under hybrid dynamics takes the form: where Φ denotes the predicted scores, P com is the zero-center-of-mass projection, ϵ Z is noise sampled on the appropriate manifold, and exp is the Riemannian exponential map.

Corrector steps follow annealed Langevin dynamics at fixed noise level t , using the same form but without the drift term f and with unit noise scaling.


## H.3 Guidance potentials

At inference time, auxiliary differentiable potentials can be composed with the learned score to guide sampling. Gradients are added to the score in both predictor and corrector steps. We use guidance based on the AlphaFold2 structure violation loss [ 4 ], which penalizes steric clashes and bond geometry violations, to improve the physical quality of generated structures. When guidance is active, we found it necessary to include corrector steps (up to 5 per predictor step) to allow the reverse dynamics to mix adequately under the additional gradient field.


## Footnotes

1 We found Ibex- holo outperformed the apo version for docking, consistent with [ 8 ], so we omit the latter in this section.