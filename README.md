# Epipolar-graph-vo

Repo highlights the work from the paper "Relational Epipolar Graph for Relative Pose Estimation" and thesis titled "GRAPH-BASED RELATIVE POSE ESTIMATION WITH EPIPOLAR GEOMETRY SUPERVISION FOR VISUAL SLAM".

## Overview
This repository contains an implementation for training and evaluating a graph-based visual odometry pipeline on KITTI-style data. The notebooks in this project cover:
- Data preparation from KITTI odometry sequences.
- Finding matched keypoints using LoFTR and processing the GT poses from dataset for training.
- Matched keypoints normalized by Camera Intrinsics and keypoint graphs are constructed.
- Finding an initial estimate of Essential Matrix to filter edges in the graph (Construction of Epipolar Graphs).
- Epipolar Graphs (Sparse Graph) passed to GNN to perform advance filtering when supervised over Geometric Loss Function.
- GNN Modules: a) 3xGCN + GAT + GA Pool, b) GAT + 2xGCN + GA Pool, c) GIN + Sum Pool and d) Cross Graph Attention.
- Loss Function Comprises of: MSE + Scale + (Spectral + Essential Matrix) + Yaw loss -> Weighted Composite Loss Function.
- Observations: a) Robust Pose Estimation, b) Lower Trajectory alignment with BA (Good Estimated Poses), c) Faster Training -> Lightweight architecture, d) Works with minimal correlation between scenes and e) Estimates are better compared to SAC methods and CNN based pose regression.
- Disadvantages: a) Dependent on a good initial estimate of Essential Matrix, b) Dependent on Camera Intrinsics and c) Needs transfer learning, not easily generalizable over direct testing.

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

