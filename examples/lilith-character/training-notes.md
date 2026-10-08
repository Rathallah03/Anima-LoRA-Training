# Training Notes — Lilith Character LoRA

## Experiment purpose

The Lilith LoRA was an earlier successful training experiment and served as a practical validation of the Anima LoRA training workflow.

## Dataset structure

The dataset used image files paired with same-name text captions:

```text
image_001.png
image_001.txt
image_002.png
image_002.txt
...
```

The original dataset remains local/private and is not redistributed here.

## Validation flow

1. Prepare character images.
2. Create matching captions.
3. Train a character LoRA using Anima.
4. Test the resulting LoRA locally.
5. Iterate/check the output.
6. Publish the successful result to Civitai.

## Repository role

This case study is kept separate from the reproducible Kaggle notebook so the repository contains both:

- a **reproducible training pipeline**, and
- a **real-world training example** showing that the workflow has been successfully used.

## Planned evidence

The following can be added later:

- training configuration / hyperparameters
- dataset statistics
- representative dataset samples (only where redistribution is permitted)
- generated validation samples
- training screenshots
- model/release link supplied by the author
- notes on what worked and what was changed during experimentation
