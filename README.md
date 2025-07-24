# Prediction of Protein Secondary Structures using Deep Learning

This project was developed as part of the course *Bioinformatics* in the *Molecular Techniques in Life Science (MTLS)* master's program. It implements a machine learning pipeline for predicting protein secondary structures from amino acid sequences using deep learning models built with Keras. 

The pipeline classifies each amino acid residue into one of the three major secondary structure types:
- **H**: alpha-helix  
- **E**: beta-sheet  
- **C**: coil

The complete pipeline includes:
- Parsing FASTA input or loading PSSM profiles
- Applying a sliding window over PSSMs to encode sequence context
- Training or loading dense neural network models using Keras, using different architectures and sliding window sizes
- Predicting secondary structure labels residue-wise
- Visualizing accuracy, loss, and cross-validation results

The data were sourced from Katarina Elez's GitHub repository: [https://github.com/katarinaelez/protein-ss-pred](https://github.com/katarinaelez/protein-ss-pred).

## Tested Models

All models are based on a **fully connected (dense) neural network architecture** and use a **sliding window** approach to encode contextual information around each central residue via its PSSM profile.

| Model Name           | Architecture Description                                 |
|----------------------|----------------------------------------------------------|
| `model_default`      | Default dense network model (see report for outline)     |
| `model_reg`          | Adds L2 regularization to the default model              |
| `model_tanh`         | Uses Tanh activation instead of ReLU                     |
| `model_less_layers`  | Decreased number of layers compared to default model     |
| `model_extra_layers` | Increased number of layers compared to default model     |

**Best-performing model:** `model_extra_layers` with a **17-residue window**, achieving **74.4% blind test accuracy**.

## Attached Files

The repository includes:

- `secondary_structure_predictor.ipynb`: Final notebook with training, evaluation, and prediction code  
- `model_extra_layers_w17_submodel_3.json`: Architecture of the best-performing model (Keras JSON format)  
- `model_extra_layers_w17_submodel_3_weights.pkl`: Trained weights for the best-performing model  
- `4s1h_entry.fasta`: Example FASTA file for testing sequence parsing  
- `secondary_structure_predictor_report.pdf`: Detailed project report

These files allow full reproduction of model training using the provided Keras architecture and weights.

