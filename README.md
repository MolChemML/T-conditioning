# T-conditioned_molecular_representation
This repository implements temperature-conditioned molecular representations for predicting organic solubility across varying temperatures.

1) Code
   - preprocessing
     - csv_to_pkl.py: Converts `.csv` data into `.pkl` format for efficient loading
     - custom_dataset_single.py: Dataset class for Chemprop-based models
     - fastprop_csv_dataset.py: Dataset class for Fastprop-based models
     - feature_vectors.py: Feature construction for molecular graph representation
   - models
     - chemprop: model architecture information (Chemprop, Chemprop w/FiLM)
     - fastprop: model architecture information (Fastprop, Fastprop w/FiLM)
     
2) 47_pairs_result_graph
   - Chemprop
   - Fastprop

---

## Code Overview

### 1. Data Preprocessing (`code/preprocessing`)

This folder prepares raw solubility data for training. First,

- Converts SMILES into molecular graph representations using RDKit  
- Constructs solute–solvent pairs  
- Includes temperature (`T`) and target solubility (`logS`)  
- Saves processed dataset as a `.pkl` file  

Second,

- Custom PyTorch dataset for solute–solvent systems  
- Molecular graphs encoded via message-passing features  
- Includes:
  - Atom features  
  - Bond features  
  - Molecular descriptors  


### 2. Model Architecture (`code/models`)

The models are based on **Directed Message Passing Neural Network (D-MPNN)** and **descriptors** with temperature conditioning vial FiLM.
This allows continuous modulation of molecular representations with respect to temperature.

#### Key Components

- **Molecular Encoders**
  - Separate encoders for solute and solvent  

- **Temperature Encoding**
  - Scalar temperature is expanded using Gaussian RBF 

- **FiLM (Feature-wise Linear Modulation)**
  - Learns feature-wise scaling (γ) and shifting (β) based on temperature  
  - Applied to both solute and solvent representations  

- **Prediction Head**
  - Outputs predicted log solubility  

---

## Application Study Results

The file `47_pairs_result_graph.zip` contains visualization results for 47 solute–solvent pairs.

Each plot shows:
- Experimental solubility (ground truth)
- SAFT-γ Mie predictions
- Baseline model predictions (Chemprop, Fastprop)
- T-conditioned model predictions (Chemprop w/FiLM, Fastprop w/FiLM)

File naming:
'SoluteName_SolventName.png'

---

## Citation
If you use this work, please cite:
[Will be updated]


