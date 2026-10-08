# 🧪 Lilith Character LoRA — Training Case Study

This directory documents an earlier successful **Anima character-LoRA training experiment** used to validate the training workflow before building the reproducible Kaggle pipeline in this repository.

## Overview

- **Character:** Lilith
- **Source:** *The NOexistenceN of you AND me* / related NOexistenceN works
- **Training type:** Character LoRA
- **Base model:** Anima
- **Dataset format:** Image + same-name `.txt` caption sidecar
- **Training result:** Successful character LoRA
- **Output:** FP16 SafeTensors LoRA
- **Release:** Published on Civitai

## 📂 Case Study Structure

```text
lilith-character/
├── README.md
├── training-notes.md
├── dataset/
│   ├── image + caption pairs
│   └── (representative samples)
└── results/
    └── (generated outputs)
```

## 🖼️ Dataset

The `dataset/` directory contains a small representative subset of the original training data. Each image is paired with a same-name `.txt` caption file:

```text
lilith_001_original.png
lilith_001_original.txt

lilith_032_original.jpg
lilith_032_original.txt

...
```

The complete source dataset is **not included in this repository**. The repository documents the dataset structure and training process without redistributing the full source image collection.

## 🎨 Generated Results

The `results/` directory is reserved for representative outputs generated with the trained LoRA.

These samples demonstrate the practical result of the training process and allow the training case study to be evaluated independently from the source dataset.

## 🔄 Training Flow

**Dataset → Captioning → LoRA Training → Local Validation → Generated Results → Release**

## Why this example is included

This experiment demonstrates that the training workflow is not only theoretical or notebook-based: it was previously used to produce a working character LoRA from a real image/caption dataset.

The accompanying `training-notes.md` records the experiment and can be expanded with training parameters, validation details, and release information.

> **Note:** The original full dataset and trained model weights are intentionally kept outside this GitHub repository unless redistribution rights are confirmed.
