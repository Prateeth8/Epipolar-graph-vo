# Epipolar-graph-vo

Website highlighting the work from the paper "Relational Epipolar Graph for Relative Pose Estimation".

## Overview
This repository contains an implementation for training and evaluating a graph-based visual odometry pipeline on KITTI-style data. The notebooks in this project cover:
- data preparation from KITTI odometry sequences
- keypoint and pose preprocessing
- training graph neural network models for relative pose estimation

## Dataset
- KITTI Odometry Dataset: https://www.kaggle.com/datasets/hocop1/kitti-odometry

## Resources
- Thesis / Extended Implementation: https://drive.google.com/drive/folders/1AOZD6ErdRgdIjDDBGGNiBs7snoGW3oy_?usp=sharing
- Paper: https://arxiv.org/abs/2604.04554

## Setup
1. Create a Python environment (Python 3.10+ recommended).
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. For GPU support with PyTorch, install the CUDA-enabled wheels separately if needed:
   ```bash
   pip install torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0 --index-url https://download.pytorch.org/whl/cu124
   ```
4. Install the PyTorch Geometric dependencies matching your torch version from the official PyG wheels page.

## Project Files
- [train_vo.ipynb](train_vo.ipynb) — training and evaluation workflow
- [kitti-data-prep.ipynb](kitti-data-prep.ipynb) — KITTI preprocessing and dataset preparation

## Notes
- Update the file paths in the notebooks before running them on your local KITTI data.
- The notebooks currently include placeholders for calibration, image, and preprocessed .npy paths that must be replaced with your own dataset locations.

