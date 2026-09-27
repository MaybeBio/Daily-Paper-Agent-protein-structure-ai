# A Step-by-Step Protocol for Efficient Global Accuracy Estimation of Protein Complex Structural Models with MViewEMA


## Abstract
  Estimation of model accuracy (EMA) is a critical step in protein structure prediction, enabling the ranking and selection of models in the absence of experimental structures. EMA methods aim to function independently of modeling approaches, ensuring broad applicability across diverse prediction workflows. Recent state-of-the-art EMA methods often improve estimation accuracy by incorporating consensus information from model pools, multiple sequence alignments (MSAs), structural templates, or protein language model representations. However, these strategies typically incur substantial computational cost or rely on information derived from the modeling process itself, which may introduce bias and compromise the independence of the assessment. This protocol describes the use of MViewEMA for global accuracy estimation of protein complex models from a single input structure. MViewEMA extracts residue–residue interaction features from complementary micro-, meso-, and macro-environmental perspectives and integrates multi-scale structural representations through a multi-view representation learning framework to predict global confidence scores. The protocol provides detailed procedures for input structure preparation, feature extraction, model inference, and global confidence score output, together with a tutorial for using the MViewEMA web server. The protocol provides a workflow based solely on structural information from the input model, achieving a balance between computational efficiency and estimation accuracy. It enables large-scale evaluation and selection of predicted models for protein structure prediction and downstream structural analysis applications.

  Key features

  • Provides an efficient and accurate single-model EMA framework for protein complex accuracy estimation.

  • Integrates residue–residue interaction features across micro-, meso-, and macro-environmental views through multi-view representation learning.

  • Performs independent protein structural model assessment without requiring MSAs, templates, protein language models, or consensus information from model ensembles.

  • Supports large-scale protein complex model ranking and selection for downstream structural analysis applications.


## Graphical overview
  

  Schematic illustration of the MViewEMA workflow for protein complex structure model accuracy estimation. An input protein complex model is first subjected to multi-view feature extraction, including micro-environment (MiE), meso-environment (MeE), and macro-environment (MaE) representations. Each view is processed by a dedicated neural network module employing graph attention, convolutional, and Transformer architectures. The resulting multi-view representations are integrated to yield a final global confidence score.


## Background
  The rapid development of protein structure prediction methods, particularly recent advances in protein complex prediction, has generated vast numbers of computationally predicted protein structural models [1–4]. This rapid expansion has created a key challenge: reliable identification of high-quality structures from large candidate model pools [5]. Protein structure model accuracy estimation (EMA), also referred to as model quality assessment (MQA), aims to evaluate the reliability of predicted structures in the absence of experimentally determined reference structures, which is critical for downstream model ranking and selection in structural biology applications [6].

  Existing EMA methods can be broadly categorized into three classes: consensus-based methods, quasi-single-model methods, and single-model methods [7–9]. Consensus-based approaches estimate model accuracy by comparing a set of candidate structures and exploiting structural agreement among models [10–13]. These methods often achieve high accuracy when a sufficiently large and diverse model pool is available, but their performance is influenced by the quality of the input models [9]. Quasi-single-model methods use externally derived structural references to augment single-model features, improving robustness through additional structural context [14–16], but their effectiveness may be influenced by the quality of external references and incur additional computational cost [9]. In contrast, single-model methods directly estimate model accuracy from an individual structure [17–23], but a substantial number of these methods rely on computationally expensive feature generation procedures, such as multiple sequence alignment (MSA), template search, or protein language model-based feature extraction.

  This protocol describes a step-by-step workflow for applying MViewEMA [20] to global accuracy estimation of protein complex structural models. MViewEMA is a single-model framework based on multi-view representation learning, which enables global accuracy estimation from a single input protein complex structure [20]. Specifically, MViewEMA characterizes residue–residue interaction features from three complementary perspectives, namely micro-environmental (MiE), meso-environmental (MeE), and macro-environmental (MaE) views. These views are processed using graph attention, convolutional, and Transformer architectures and integrated via cross-view integration to generate a global confidence score [20].

  This protocol operates directly on a single protein complex structure and is independent of structure prediction pipelines, enabling evaluation across models generated by different methods. By avoiding reliance on model ensembles, external structural references, and computationally intensive feature generation, this protocol facilitates efficient large-scale evaluation [20], being applicable to downstream structural biology tasks. In protein structure prediction, it can support confidence scoring and quality annotation of models, facilitating functional annotation and protein–protein interaction analysis. In high-throughput settings, it enables rapid screening of large-scale structural model collections, supporting automated prioritization workflows. The implementation is specifically designed for global quality assessment of protein complex structural models. Its applicability is currently limited to protein-only complex structural models and does not extend to protein–ligand or protein–nucleic acid complexes. Furthermore, the protocol focuses on global model accuracy estimation rather than interface-level or residue-level local quality assessment.


## Equipment
  1. Local execution workflow

  a. Linux system (Ubuntu 18.04 or later)

  b. x86-64 architecture CPU (≥8 cores; recommended for inference on large protein complexes with >2,000 residues)

  c. NVIDIA GPU with CUDA support (≥16 GB VRAM; recommended for accelerating inference on protein complexes with ≤2,000 residues)

  d. System memory (RAM) (≥16 GB)

  Note: GPU-based inference is suitable for small-to-medium-sized protein complexes with ≤2,000 residues. For complexes with >2,000 residues, CPU-based inference is recommended to avoid GPU memory overflow.

  2. Web server workflow: Desktop or laptop computer with stable internet access and a modern operating system (Windows, macOS, or Linux)


## Software and datasets
  1. Web browser (Google Chrome, Microsoft Edge, or Mozilla Firefox)

  2. MViewEMA, http://zhanglab-bioinf.com/MViewEMA/ (accessed July 6, 2026); MViewEMA source code is open-source and available at https://github.com/iobio-zjut/MViewEMA (accessed July 6, 2026)

  3. Python (version ≥ 3.8)

  4. PyTorch (version 1.11.0)

  5. PyTorch Geometric (PyG) (version 2.0.4; https://pytorch-geometric.readthedocs.io, accessed July 6, 2026; PyTorch-based geometric deep learning library)

  6. PyRosetta (version ≥ 2021.38+release.4d5a969; https://www.pyrosetta.org, accessed July 6, 2026; Rosetta license required for academic and commercial use; [24])

  7. (Optional) Singularity container environment for dependency-free execution; available at http://zhanglab-bioinf.com/DeepUMQA-X/static/env.sif (7.31 GB; accessed July 6, 2026). This container is a shared software environment maintained by our laboratory and includes all dependencies required for MViewEMA.


## Procedure
  A. Local execution of MViewEMA

  1. Code availability and environment setup: MViewEMA is made freely available to the scientific community as an open-source software package for efficient global accuracy estimation of protein complex structural models (http://zhanglab-bioinf.com/MViewEMA/). The source code can be downloaded and locally deployed for structural feature extraction, data preprocessing, and deep learning–based inference. The overall workflow is illustrated in the Graphical overview. Users should first obtain the source code and prepare the required runtime environment according to the Software and datasets section.

  2. Data requirement

  a. Input file (mandatory): Prepare a text file containing paths to one or more protein complex structures in PDB format, with each line corresponding to a single structure path ending in .pdb.

  Before running inference, ensure that each input PDB file conforms to the standard PDB format. The file should contain standard ATOM records with complete residue and atomic information, including valid chain identifiers, residue names, residue sequence numbers, atom names, and Cartesian coordinates. Ensure that the input structure contains protein chains only by removing non-protein components, including ligands, nucleic acids, and water molecules. Retain only one coordinate conformation for residues with multiple alternative atomic locations. Different protein chains should be separated using TER records.

  Improperly formatted PDB files or missing required fields may result in parsing or feature extraction errors during local execution. If preprocessing fails because of formatting errors or missing required information, check the input PDB file, correct the formatting issues or missing fields, and rerun MViewEMA.

  b. Model checkpoint (mandatory): Use a pretrained MViewEMA model checkpoint file (.ckpt) for inference. The checkpoint file contains trained network parameters used for global accuracy estimation and resides in the checkpoints/directory of the software package.

  c. Output directory (mandatory): Specify an output directory for saving extracted features, intermediate files, and predicted global accuracy scores generated during inference.

  3. Main inference execution: Execute MViewEMA inference using the following command:

  python run_inf.py \

  --test_fpath INPUT_PDBS_LIST \

  --ckpt_path TM_CKPT \

  --output OUT_DIR

  4. Optional execution

  a. Optional runtime parameters: MViewEMA supports several optional arguments for customized execution, including the number of data-loading workers (--num_workers), feature-only preprocessing mode (--only_process_feat), feature extraction control (--process_feat), and maximum sequence length limitation (--max_length).

  b. Singularity container-based execution

  i. Container environment setup: Optionally execute MViewEMA within a Singularity container to ensure reproducibility and simplify dependency management. Launch the container image (.sif) with GPU support enabled and bind the working project directory to the container environment:

  singularity shell --nv --bind /path/to/project:/workspace /path/to/env.sif

  The Singularity container is provided at http://zhanglab-bioinf.com/DeepUMQA-X/static/env.sif.

  ii. Environment activation: After entering the container, activate the pre-installed Conda environment before running inference:

  source /miniconda/bin/activate

  conda activate pytorch

  This environment contains all required dependencies for MViewEMA execution, including PyTorch and related libraries.

  iii. Inference execution: Execute the inference pipeline inside the container by calling the main script run_inf.py and specifying the input PDB path list file, pretrained checkpoint, and output directory:

  python /workspace/run_inf.py \

  --test_fpath /workspace/ INPUT_PDBS_LIST \

  --ckpt_path /workspace/ TM_CKPT \

  --output /workspace/ OUT_DIR

  5. Output format: The pipeline generates a CSV file ([out_dir].csv), where each row corresponds to an input protein model and includes the PDB file name and the predicted global accuracy score (TM-score-based confidence).

  B. How to use MViewEMA web server

  1. Job submission

  a. Open the MViewEMA web server (http://zhanglab-bioinf.com/MViewEMA/), as shown in Figure 1.

  b. Upload protein complex structure models: MViewEMA supports submission of single PDB files, multiple PDB files (up to 10 models per submission), or a compressed ZIP file containing models of the same protein complex target, as shown in Figure 2. No explicit limit is imposed on the number of models in ZIP submissions. All uploaded structure files must end with the .pdb extension. Click on PDB format to view an example PDB file and the required format specifications.

  i. Paste the text content of a PDB file directly into the input text box. Alternatively, upload at least one protein complex structure model file in PDB format.

  ii. Click the Add model button to add additional input boxes for uploading multiple structure models of the same protein complex. The server accepts up to 10 structure models per submission.

  iii. Alternatively, upload a compressed ZIP file containing all structure models of the same protein complex, where each model file ends with the .pdb extension. Compress the folder in the format ./files or ./dir/files before uploading.

  Note: Users must separate different protein chains using the “TER” record in PDB files.

  c. Provide an email address (optional): Optionally provide an email address for receiving notification messages and result links.

  d. Assign a job name (optional): Optionally assign a custom job name for the submitted task to facilitate result identification and management. If no job name is provided, the server automatically generates a default job name using the current timestamp followed by an 8-character unique identifier.

  e. Submit the job: Click the Submit button at the bottom of the page to submit the task.

  f. View task status and notifications: After job submission, the page automatically redirects to the task status page, as shown in Figure 3.

  Notes:

  1. If only a single PDB structure is submitted, the calculation typically finishes within several minutes, and the server automatically redirects to the result page.

  2. If multiple PDB structures or a compressed archive are submitted, the calculation may require additional processing time.

  3. If an email address is provided during submission, the server sends a notification email containing a hyperlink to the result page after task completion.

  4. Click the Reset button at the bottom of the page to clear all uploaded information and reset the submission form.

  2. Result page: The MViewEMA result page displays the predicted global confidence scores for submitted protein complex structure models, as shown in Figure 4. The server additionally saves the prediction results as a CSV file and provides the file as a downloadable hyperlink below the page title. Click [job_name].csv to download the result file. The CSV file contains three columns, including an index column, the model, and the predicted global confidence score.

  3. Receive email notifications: If you provide an email address, the server sends a confirmation email after job submission named “MViewEMA submission for [your job name],” which includes the job ID and a hyperlink to the full result page on the MViewEMA server, as shown in Figure 5. Once the computation is completed, the server sends a second notification email named “MViewEMA server results for [your job name],” containing the job ID, a hyperlink to the full result page, and the results as a CSV file attachment. Users can access the full results by clicking the provided hyperlink, as shown in Figure 6.


## Validation of protocol
  This protocol has been used and validated in the following research article:


## General notes and troubleshooting
  General notes

  1. MViewEMA performs global accuracy estimation directly from input protein complex structures without requiring multiple sequence alignments, template information, or protein language model features. The method supports both web server–based prediction and standalone local execution.

  2. Prepare all input protein complex structures in standard PDB format before inference. Remove alternative atomic coordinates and retain only a single conformation for each residue to avoid preprocessing and feature extraction errors.

  3. The MViewEMA web server supports submission of single PDB files, multiple PDB files, and compressed ZIP archives containing multiple structure models of the same protein complex. Ensure that all uploaded structure files end with the .pdb extension.

  4. Prediction time depends on the number and size of submitted protein complex structures. Single-structure evaluation typically finishes within several minutes, whereas batch submissions containing multiple structures may require substantially longer processing times.

  5. For protein complexes with ≤2,000 total residues, GPU-based local inference can accelerate prediction. For complexes with >2,000 total residues, CPU-based inference is recommended to avoid GPU memory overflow, although the runtime may be longer.

  6. The web server is suitable for convenient evaluation of a small number of protein complex structure models. For high-throughput or large-scale batch evaluation, the local execution workflow is recommended for improved efficiency.

  7. MViewEMA provides global confidence scores for protein complex structure models and is primarily intended for model quality ranking and model selection applications.

  8. MViewEMA is intended for global accuracy estimation of protein-only complex structural models. Residue-level or interface-level quality assessment, as well as assessment of protein–ligand or protein–nucleic acid complex models, are beyond the scope of the current protocol.

  Troubleshooting

  Problem 1: Upload failure during web-server submission.

  Possible cause: Uploaded structure files do not end with the .pdb extension.

  Solution: Rename all structure files using the standard .pdb extension before submission.

  Problem 2: Feature extraction or preprocessing failure.

  Possible cause: The input PDB file does not conform to the standard PDB format, contains missing required information (e.g., ATOM records, chain identifiers, residue names, residue sequence numbers, atom names, or Cartesian coordinates), includes non-protein components, contains multiple alternative atomic locations, or has residues with missing backbone atoms.

  Solution: Verify that the input structure is a standard protein-only PDB file and that it conforms to the standard fixed-column PDB format. Ensure that all required information for structure parsing and feature extraction is present, including valid ATOM records, chain identifiers, residue names, residue sequence numbers, atom names, and Cartesian coordinates. Remove non-protein components, retain only one coordinate conformation for residues with multiple alternative atomic locations, separate different protein chains using TER records, and correct any formatting issues before rerunning MViewEMA.

  Problem 3: ZIP archive upload failure.

  Possible cause: Incorrect directory organization inside the compressed archive.

  Solution: Compress the folder according to the recommended directory structure (./files or ./dir/files) before uploading.

  Problem 4: Long waiting time during prediction.

  Possible cause: Multiple large protein complex structures are submitted simultaneously.

  Solution: Reduce the number of submitted structures or use the standalone local version of MViewEMA for batch evaluation.

  Problem 5: Incomplete result generation or prediction interruption.

  Possible cause: The submitted protein complex structure exceeds memory or sequence-length limitations.

  Solution: Reduce the input structure size or adjust the maximum sequence length parameter (--max_length) during local execution. For protein complexes containing more than 2,000 residues, use CPU-based local inference to avoid GPU memory overflow. If inference fails due to an inappropriate --max_length setting, increase this parameter according to the total sequence length and available system memory.

  Problem 6: Missing email notification after job submission.

  Possible cause: An incorrect or unavailable email address is provided during submission.

  Solution: Verify the email address before submitting the prediction task.


## Acknowledgements
  Lei Xie: Methodology, Validation, Software, Writing—Original Draft. Enjia Ye: Methodology, Validation, Software, Writing—Original Draft. Dong Liu: Methodology, Software, Writing—Review & Editing. Guijun Zhang: Conceptualization, Methodology, Writing—Review & Editing, Supervision, Funding acquisition.

  We thank members of the Guijun Zhang lab for discussion and feedback. Computational resources were provided by the College of Information Engineering at Zhejiang University of Technology. This work was supported by the National Key R&D Program of China (2022ZD0115103, G.Z.), the National Nature Science Foundation of China (62573386, G.Z.; 62173304, G.Z.), the “Pioneer” and “Leading Goose” R&D Program of Zhejiang (2025C01190, G.Z.), and the Zhejiang Province High-level Talent Special Support Program (2023R5248, G.Z.).

  This protocol was derived from the original research study published in [20].