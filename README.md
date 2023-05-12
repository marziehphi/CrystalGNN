# Crystal Graph Convolutional Neural Networks

This experimental study was carried out at AstraZeneca's Department. However, the project's focus isn't solely on machine learning; rather, it's on applying machine learning to the subject of materials science. To be more specific, it has to do with the field of material discovery, namely the improvement of properties. The research centered on two fundamental process:

- Train a Crystal Graph Convolutional Neural Network model with a customized dataset.
- Predict material properties of selected crystals with the CGConv Neural Network model.
  
<!--
# Table of Contents
- [Crystal Graph Convolutional Neural Networks](#-crystal-graph-convolutional-neural-networks)
- [Table of Contents](#-table-of-contents)
- [AIM](#-aim)
- [Prerequisites](#-prerequisites)
- [Usage](#-usage) 
- [Preprocessing](#-usage)
- [Phase One: Formation Energy](#phase-one-formation-energy)
- [Phase Two: Intensity values (XRPD Technique)](#phase-two-intensity-values-xrpd-technique)
- [Citation](#-authors)
-->

# AIM

The goal of this study is to see if graph neural networks can be utilized to predict crystal characteristics and hence speed up the crystal structure prediction framework. As a result, we concentrated on examining the proposed strategy from two perspectives:

- `Computational speed` and `financial cost`.
- How far we can go with the graph neural network model in material science? We checked the `model's transferability` on two different targets: `Formation Energy` and `Intensity values` of x-ray powder diffraction (XRPD) technique.

# Prerequisites

This packages requires:

- PyTorch
- scikit-learn
- pymatgen
- pytorch-lightning

The easiest way of installing the prerequisites is via 'conda'. If you are using the JupyterHUB, run the following command to create a new environment and then install all prerequisites.

```bash
# create new environment
$ ml Miniconda3
$ conda create -n jcml19 python=3.8.12
# activate new environment
$ conda activate jcml19

# create definition file 
cat << EOF > jcml19.yml
---
display_name: 'JCML19_python_3.8'
language: 'python'
manager: 'conda'
conda_env: 'jcml19'
EOF
# run the script
ml jupyterlab_kernel_generator
CONDA_PREFIX="/opt/scp/software/Anaconda3/2019.10" jupyterlab_kernel_generator --definition ./jcml19.yml
```
After creating a new environment then install all needed prerequisites.

```bash
# Pytorch install
pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 torchaudio==0.9.0 -f https://download.pytorch.org/whl/torch_stable.html

# pymatgen install
pip install pymatgen==2022.2.7

# pytorch-lightning install
pip install pytorch-lightning=1.5.9
```

# Usage


## Preprocessing

- The notebook `collect-data.ipynb` collects structures, and their intensity values from the folder `database` and save them as  `CSV` format in folder `data`.

- The `dataset` folder shows:
  
The `train.csv`, `valid.csv`, and `test.csv` after preprocessing (standardization) step. 

The `org-train.csv`, `org-valid.csv`, `and org-test.csv` without preprocessing (standardization) step.

- The `atom-init.json` file that stores the initialization vector for each element.
- The folder `content` and `log` contain the model's checkpoints and metrics [Mean Absolute Error (MAE) and Mean Square Error (MSE)], respectively.

## Phase One: Formation Energy

- The notebook `gnn-qm.ipynb` that displays the CGConv Neural network model's training, testing, and prediction stage on formation energy.


## Phase Two: Intensity values (XRPD Technique)
The folder `XRPD`, contains:

- The notebook `gnn-xrpd.ipynb` that displays the CGConv Neural network model's training, testing, and prediction stage on Intensity values after XRPD technique.
  

# Citation
If you use this code or the models in your research, please cite the following:

```
@misc{marziehphi,
  author = {Farahani, Marzieh},
  title = {Accelerate Prediction of Crystal Material Properties Using Deep GNNs},
  year = {2022},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/marziehphi/CrystalGNN}},
}
```
