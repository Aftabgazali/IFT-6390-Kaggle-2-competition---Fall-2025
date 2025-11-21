
# IFT6390 – Kaggle Competition 2 (Retina Classification)

This repo contains my solution for **Kaggle Competition 2** in the IFT6390 course.  
The task is to classify small retinal images (28×28×3) into **5 classes (0–4)**.

## Project Structure

```bash
.
├── data/
│   ├── train_data.pkl   # not included – download from the course/Kaggle
│   └── test_data.pkl
├── scripts/
│   ├── baseline_model.ipynb    # NumPy softmax baseline
│   └── advanced_models.ipynb   # ResNet18 advanced model
````

## Models

* **Baseline – Softmax Regression (NumPy only)**

  * Grayscale + normalization + standardization of pixels.
  * From-scratch softmax classifier with mini-batch SGD, L2 regularization, early stopping.
  * Validation accuracy ≈ **0.53**, Kaggle LB ≈ **0.505** (beats course baseline ≈ 0.45).

* **Advanced – ResNet18 (PyTorch)**

  * Pretrained ResNet18, resized to 224×224, ImageNet normalization.
  * Fine-tunes `layer3`, `layer4`, and a dropout-regularized classification head.
  * Data augmentation (flip, rotation) + early stopping + stronger weight decay.
  * Validation accuracy ≈ **0.60**, Kaggle LB ≈ **0.52**.

## How to Run

1. Place `train_data.pkl` and `test_data.pkl` in `data/`.
2. Open the notebooks in `scripts/` (in order: baseline, then advanced).
3. Run all cells to reproduce training, plots, and `submission.csv` files.

This repo is mainly for educational purposes (coursework + experimentation), not as a polished library.