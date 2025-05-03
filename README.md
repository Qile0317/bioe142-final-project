# Final project for Bioengineering C142, Spring 2025 at UC Berkeley

**Abstract:** I introduce a streamlined machine-learning potential that delivers density-functional accuracy for small CHON molecules at force-field speed. Using the ANI Atomic Environment Vector descriptor and TorchANI, I trained element-specific feed-forward networks on a curated GDB subset. An architecture sweep identified a single-hidden-layer model (128 neurons per element; 197K parameters) as the best. With Adam optimisation, the model attains an RMSE of 1.03 kcal on an unseen test set while retaining laptop-scale training (~minutes on an RTX 3050). ReLU activations outperformed CELU variants. Overall, a much more compressed model than the original ANI-1 potential was achieved, with a similar performance on the small organic molecule dataset.

## Usage

To get to the same environment as the one used for this project's models, you can use the provided conda `environment.yml` file. In general, to just get the actual model in python, do the following:

1. Clone the repository with:

```bash
git clone https://github.com/Qile0317/bioe142-final-project.git
```

2. Load pytorch and load the model pth file:

```python
import torch
model = torch.load('models/ff_relu_model.pth')
```

## Directory Structure

```bash
.
├── README.md # this file
├── checkpoints # Jupyter notebook checkpoints
│   ├── checkpoint1.ipynb
│   ├── checkpoint2.ipynb
│   ├── checkpoint3.ipynb
│   └── checkpoint4.ipynb
├── data # the GDB 4 heavy atom dataset used
│   └── ani_gdb_s01_to_s04.h5
├── environment.yml # the conda environment file
├── instructions # instructor instruction pdfs
│   ├── ANI.pdf
│   ├── FINALSPROJECT_142_242.pdf
│   └── Final project guidelines.pdf
├── main-project-notebook.ipynb # the final model training and eval notebook
├── models # the trained models
│   ├── ff_celu_model.pth # CELU-activated ANN
│   └── ff_relu_model.pth # RELU-activated ANN
└── writeup # latex files for the final writeup
    ├── main-body.tex
    ├── main.pdf
    ├── main.tex
    └── references.bib
```
