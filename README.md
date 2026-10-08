# Anima LoRA Training Pipeline

A reproducible Kaggle notebook for training LoRA adapters on **Anima Base v1.0** using `sd-scripts` and Accelerate.

## Overview

This project packages a training workflow that covers:

- downloading the Anima Base model, Qwen3 0.6B text encoder, and Qwen Image VAE
- preparing a Kaggle dataset workspace
- validating image/caption pairs
- validating model files and the Anima training modules
- installing and checking `sd-scripts` dependencies
- generating training and dataset TOML configuration files
- running a final pre-flight validation
- launching LoRA training with Accelerate on 2 GPUs
- synchronizing the generated LoRA output
- cleaning temporary dataset/output files after the run

## Target environment

The notebook is written around the following environment:

| Component | Target |
|---|---|
| Platform | Kaggle Notebook |
| GPU | 2× NVIDIA T4 |
| Precision | FP16 |
| Training resolution | 1024 |
| LoRA network dim | 32 |
| LoRA network alpha | 16 |
| Learning rate | 1e-4 |
| Epochs | 4 |
| Repeats | 50 |
| Batch size / GPU | 2 |
| Gradient accumulation | 1 |
| Scheduler | cosine |
| Optimizer | AdamW |
| Gradient checkpointing | enabled |

These values are the defaults currently encoded in the notebook and can be changed for an experiment.

## Models

The notebook downloads the following files from the Anima model repository:

- `anima-base-v1.0.safetensors`
- `qwen_3_06b_base.safetensors`
- `qwen_image_vae.safetensors`

Model weights are intentionally **not** stored in this repository.

## Dataset format

The training dataset is expected to contain matching image/caption pairs, for example:

```text
dataset_training/
├── 001.png
├── 001.txt
├── 002.png
├── 002.txt
└── ...
```

The notebook checks that every supported image has a corresponding `.txt` caption and vice versa.

## Training flow

```text
Anima Base + Qwen + VAE
          │
          ▼
     Dataset setup
          │
          ▼
 Image/caption validation
          │
          ▼
   sd-scripts validation
          │
          ▼
     TOML generation
          │
          ▼
   Pre-flight checks
          │
          ▼
 Accelerate / 2× NVIDIA T4
          │
          ▼
       LoRA .safetensors
```

## Repository structure

```text
Anima-LoRA-Training/
├── README.md
├── .gitignore
└── notebooks/
    └── training-lora-model-anima-base.ipynb
```

## Notes

This repository contains the workflow/code, not the dataset or generated LoRA weights. Check the licenses and usage terms of the base model, dependencies, and training data before redistribution.
