# T-conditioned_moleular_representation
1) Code
   - preprocessing
     - csv_to_pkl.py: import `.csv` data file and save `.pkl` file
     - custom_dataset_single.py: dataset for Chemprop-based modeling 
     - fastprop_csv_dataset.py: dataset for Fastprop-based modeling 
     - feature_vectors.py: feature selection for graph construction
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

The models are based on **Directed Message Passing Neural Network (D-MPNN)** and **descriptors** with temperature conditioning.

#### Key Components

- **Molecular Encoders**
  - Separate encoders for solute and solvent  

- **Temperature Encoding**
  - Gaussian RBF expansion  
  - Projection into latent feature space  

- **FiLM (Feature-wise Linear Modulation)**
  - Applies temperature-dependent scaling and shifting  
  - Enables continuous conditioning  

- **Prediction Head**
  - Outputs predicted log solubility  

---

## Application Study Results

`47_pairs_result_graph.zip`

This file contains visualization results for **47 solute–solvent pairs** (File name: `'Solute name'_'Solvent name'.png`):

#### In `Chemprop` folder, each file compare expermental solubility with:
- SAFT-γ Mie  
- Chemprop  
- Chemprop w/FiLM

#### In `Fastprop` folder, each file compare expermental solubility with:
- SAFT-γ Mie 
- Fastprop  
- Fastprop w/FiLM  





