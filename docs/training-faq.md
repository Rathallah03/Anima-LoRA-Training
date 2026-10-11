# Training FAQ

This FAQ answers common questions about preparing and running the Anima LoRA training notebook.

## Which environment is the notebook designed for?

The documented target environment is a Kaggle Notebook with 2 NVIDIA T4 GPUs and FP16 training. The README lists the current notebook defaults as 1024 resolution, LoRA network dimension 32, alpha 16, learning rate `1e-4`, 4 epochs, 50 repeats, batch size 2 per GPU, gradient accumulation 1, cosine scheduler, AdamW optimizer, and gradient checkpointing enabled.

These are project defaults, not universal recommendations. Check the notebook cells before a run because the values may change.

## What files should the dataset contain?

Each supported image needs a caption file with the same base filename and a `.txt` extension. For example:

```text
dataset_training/
├── 001.png
├── 001.txt
├── 002.png
├── 002.txt
└── ...
```

Check that filenames match exactly, captions are not unintentionally empty, and the directory does not contain unexpected files. Run the notebook's dataset validation cells before training.

## Where do the model files come from?

The notebook expects these model files:

- `anima-base-v1.0.safetensors`
- `qwen_3_06b_base.safetensors`
- `qwen_image_vae.safetensors`

The model weights are not stored in this repository. Confirm that each file was downloaded successfully and that its path matches the notebook configuration.

## What should I check before starting training?

1. Confirm that the expected GPUs are available in the active Kaggle session.
2. Check that all required model files exist at the configured paths.
3. Run the dataset and training-module validation cells.
4. Review the generated TOML configuration files.
5. Run the final pre-flight validation and confirm that the output location has enough space.

## What if GPU memory runs out?

First, read the full error traceback and check the actual GPU configuration. If memory is insufficient, consider reducing the batch size or adjusting other memory-intensive settings. Change one setting at a time, then rerun the relevant validation checks. Results and feasible settings depend on the available GPU memory and training configuration.

## Why can a run fail after dependencies were installed?

Notebook environments can change between sessions, and package versions or runtime state may differ. Re-run the notebook's dependency and training-module checks in the active session, then inspect the first relevant error in the traceback before reinstalling packages or changing versions.

## Where should I look for a failed run?

Start with the first meaningful error in the notebook output rather than only the final failure message. Then check the related stage: dataset validation, model-path validation, dependency checks, TOML generation, pre-flight validation, or the training process itself.

## Where are the trained weights saved?

Follow the output path configured in the notebook and verify that the resulting LoRA file was synchronized to its intended destination before temporary files are cleaned up. This repository intentionally does not store generated LoRA weights.
