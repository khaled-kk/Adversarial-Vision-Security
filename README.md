# Adversarial Vision Security

Evaluating how adversarial attacks degrade an ImageNet classifier, and how JPEG compression performs as a pre-processing defence.

## Overview

This project attacks a pretrained **InceptionV3** model (ImageNet weights) with two gradient-based attacks, **FGSM** and **PGD**, and then measures how much accuracy JPEG compression restores when it is applied to the adversarial images before classification.

- **Model:** InceptionV3 (`weights='imagenet'`), TensorFlow/Keras
- **Data:** ImageNet ILSVRC2012 validation images, 299x299, with the official ground-truth mapping
- **Attacks:** FGSM and PGD at epsilon 0, 2 and 6 (epsilon 0 is the no-attack reference)
- **Defence:** JPEG re-compression at quality factors QF-10 to QF-100, compared with no defence
- **Metrics:** Top-1 and Top-5 accuracy for every attack, epsilon and quality factor

## Repository contents

| File | Purpose |
| --- | --- |
| `IPM2S23.ipynb` | Full pipeline: label mapping, FGSM/PGD attack generation, JPEG defence, Top-1/Top-5 evaluation |
| `attachment/` | ImageNet label and ground-truth mapping files used by the notebook |
| `orignal and compresed images link.txt` | Google Drive link to the original, attacked and compressed image sets |

## How to run

1. Download the image folders from the Drive link in `orignal and compresed images link.txt`.
2. Upload them to your own Google Drive using the same folder names the notebook expects (`FGSM/`, `pgd/`, `Sorted QF folders/`).
3. Open `IPM2S23.ipynb` in Google Colab, mount Drive, and run the cells in order.
4. The Top-1 and Top-5 accuracy tables are produced by the `findTOP1` and `findTOP5` cells at the end of the notebook.

## Notes

- The pipeline mounts Google Drive, so it is designed for Colab rather than local execution.
- Attacks are untargeted perturbations of the input image; the defence never sees the model weights, it only re-encodes the image.

<!-- TODO (Khaled): run the final cells, then paste the Top-1 / Top-5 results table here and add one sentence on which quality factor restores the most accuracy. -->

*Developed by Khaled Walid, MSc Data Science, University of Europe for Applied Sciences.*
