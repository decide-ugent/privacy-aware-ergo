# Privacy-Aware Ergonomic Analysis

Official implementation for **"Enabling Privacy-Aware AI-Based Ergonomic Analysis"**.

This work presents a privacy-preserving approach to ergonomic analysis using AutoEncoder-based obfuscation that maintains pose estimation accuracy while protecting individual privacy.

## Installation

```bash
pip install -r requirements.txt
```

## Dataset Preparation

The training script expects datasets in YOLO pose format. Use `prepare_dataset.sh` to convert your data or create a YAML config file:

```yaml
path: /path/to/your/dataset
train: images/train
val: images/val
test: images/test
kpt_shape: [17, 3]
names:
  0: person
```

## Training

Train the obfuscator/deobfuscator models:

```bash
python train_obfuscator.py --config_path path/to/config.yaml --nowandb
```

Use `--help` to see all available options.

## Evaluation

Evaluate trained models:

```bash
python eval.py \
    --config_path path/to/config.yaml \
    --load_path_obfuscator models/obfuscator.pt \
    --load_path_deobfuscator models/deobfuscator.pt
```

Compare with baseline methods:

```bash
# Gaussian blur
python eval.py --obfuscation_type gaussian_blur --kernel_size 21

# Noise injection  
python eval.py --obfuscation_type noise --std 0.1
```

## Citation

```bibtex
@article{DECONINCK2025371,
title = {Enabling Privacy-Aware AI-Based Ergonomic Analysis},
journal = {Procedia CIRP},
volume = {136},
pages = {371-376},
year = {2025},
note = {35th CIRP Design 2025},
issn = {2212-8271},
doi = {https://doi.org/10.1016/j.procir.2025.08.065},
url = {https://www.sciencedirect.com/science/article/pii/S2212827125008182},
author = {Sander {De Coninck} and Emilio Gamba and Bart {Van Doninck} and Abdellatif Bey-Temsamani and Sam Leroux and Pieter Simoens},
keywords = {Ergonomic Analysis, Privacy, Human Pose Estimation, Privacy-Aware Machine Learning},
}
```
