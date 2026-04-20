# T-conditioned_moleular_representation
1) Code
   - preprocessing
     -- csv_to_pkl.py:
     -- custom_dataset_single.py:
     -- fastprop_csv_dataset.py:
     -- feature_vectors.py:
   - models
     -- chemprop.py:
     -- Fastprop.py:
     
2) 47_pairs_result_graph
   - Chemprop
   - Fastprop

---

## Code Overview

### 1. Data Preprocessing (`code/preprocessing`)

This module prepares raw solubility data for training.

- Converts SMILES into molecular graph representations using RDKit  
- Constructs solute–solvent pairs  
- Includes temperature (`T`) and target solubility (`logS`)  
- Saves processed dataset as a `.pkl` file  


### 2. Dataset & Feature Construction

- Custom PyTorch dataset for solute–solvent systems  
- Molecular graphs encoded via message-passing features  
- Includes:
  - Atom features  
  - Bond features  
  - Molecular descriptors  
- Temperature is explicitly included as an input variable  

### 3. Model Architecture (`code/models`)

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

This file contains visualization results for **47 solute–solvent pairs**, comparing:

- Experimental solubility  
- SAFT-γ Mie  
- Chemprop  
- Chemprop + FiLM  
- Fastprop  
- Fastprop + FiLM  





