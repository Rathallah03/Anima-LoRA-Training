# Training Notes — Lilith Character LoRA

## Experiment

This case study records an earlier successful **Anima character-LoRA training experiment** for Lilith. The original training TOML/config files are no longer available, so the technical details below are reconstructed from the metadata embedded in the released LoRA file.

The metadata was inspected using a LoRA metadata viewer after the trained SafeTensors file had already been released.

## Training Configuration

| Parameter | Recorded value |
|---|---|
| Base Model | `anima-base-v1.0.safetensors` (Anima) |
| VAE | `qwen_image_vae.safetensors` |
| Prediction Type | `epsilon` |
| Training Module | `networks.lora_anima` |
| Resolution | 1024 × 1024 |
| Batch Size | 1 |
| Gradient Accumulation Steps | 1 |
| LoRA Dim / Alpha | 32 / 16 |
| Network Dropout | None |
| Learning Rate | 0.0001 |
| Text Encoder LR | None |
| UNet LR | None |
| Optimizer | AdamW8bit |
| Scheduler | cosine_with_restarts |
| Weight Decay | 0.1 |
| Betas | (0.9, 0.99) |
| Warmup Steps | 100 |
| SNR | None |
| Noise Offset | 0.03 |
| Pyramid Noise Iterations | None |
| Epochs | 9 of 10 |
| Training Steps | 1863 of 2070 |
| Total Images | 59 |
| Dataset Repeats | 7 |
| Recorded Training Time | 4h 1m 17s |
| Training Date | August 31, 2026 |

### Network

The metadata records:

```text
Module: networks.lora_anima
Dim / Alpha: 32 / 16
Network Dropout: None
```

### Optimizer & Scheduler

```text
Optimizer: AdamW8bit
Scheduler: cosine_with_restarts
Learning Rate: 0.0001
Weight Decay: 0.1
Betas: (0.9, 0.99)
Warmup Steps: 100
```

## Dataset

The training metadata records:

- **59 total images**
- **7 repeats**
- **2070 total planned steps**

The repository contains only a small representative subset of the original dataset. The full source dataset is intentionally not redistributed here.

Each training sample follows the image + same-name caption format:

```text
lilith_001_original.png
lilith_001_original.txt

lilith_032_original.jpg
lilith_032_original.txt

...
```

## Trigger Words

The released LoRA metadata contains two character triggers:

```text
lilith_default
lilith_fantasy
```

The metadata also records character/appearance tags associated with the two variants.

### Default variant

The recorded trigger is:

```text
lilith_default
```

with attributes including white hair, very long hair, red eyes, black ribbons, white shirt, black skirt, and related outfit details.

### Fantasy variant

The recorded trigger is:

```text
lilith_fantasy
```

with attributes including white hair, very long hair, red eyes, pointed/black crown, cape, breastplate, white skirt, high heel boots, sword, and related fantasy outfit details.

## Training Result

The training completed to **epoch 9 of 10**, with **1863 of 2070 steps** recorded in the embedded metadata.

The resulting LoRA was tested with local inference and produced recognizable Lilith outputs across both the default and fantasy variants. Representative generated outputs are available in the `results/` directory.

## Release

The trained model was subsequently published on Civitai:

[Lilith (2 Outfits) — The NOexistenceN of you AND me [Anima]](https://civitai.com/models/2904771/lilith-2-outfits-the-noexistencen-of-you-and-me-anima)

## Important Documentation Note

The values above describe the **earlier Lilith experiment**. They should not be confused with the configuration of the newer Kaggle training notebook in this repository.

The Kaggle notebook represents a later, more structured and reproducible training pipeline. The Lilith experiment is included as a real-world validation case showing that the underlying Anima LoRA training workflow was successfully used before the current pipeline was organized.

## Evidence Chain

```text
59-image dataset
      ↓
Image + caption pairs
      ↓
Anima Base v1.0
      ↓
LoRA training
      ↓
1863 / 2070 recorded steps
      ↓
Local inference validation
      ↓
Multiple generated results
      ↓
Civitai publication
```

> **Source of training parameters:** embedded metadata recovered from the released LoRA file. The original TOML/config files are no longer available, so undocumented parameters are intentionally not inferred.
