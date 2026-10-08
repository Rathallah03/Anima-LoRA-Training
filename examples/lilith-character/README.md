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

## Dataset

The original training dataset contains paired image/caption files, for example:

```text
lilith_001_original.png
lilith_001_original.txt
lilith_002_original.png
lilith_002_original.txt
lilith_003_original.png
lilith_003_original.txt
...
```

The complete source dataset is **not included in this repository**. The repository documents the dataset structure and training process without redistributing the full source image collection.

## Training Result

The resulting LoRA was tested locally after training and successfully produced the intended character appearance. The trained model was subsequently published on Civitai.

This case study serves as a practical validation of the broader pipeline:

**Dataset → Captioning → LoRA Training → Local Validation → Release**

## Why this example is included

This experiment demonstrates that the training workflow is not only theoretical or notebook-based: it was previously used to produce a working character LoRA from a real image/caption dataset.

Additional training notes, configuration details, screenshots, and representative results can be added here as they are prepared.

> **Note:** The original source dataset and trained model weights are intentionally kept outside this GitHub repository unless redistribution rights are confirmed.
