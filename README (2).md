# DL Assignment 01, Section B

Image classification on CIFAR10 using only 500 training images, tested on clean images and on corrupted (shifted) images.

## What is in this repo

* `DL_ASS01_XXF_YYYY.ipynb` : the full notebook with all outputs
* `README.md` : this file
* `screenshots/` : result images used below

## How to run

1. Install the libraries:
   `pip install torch torchvision scikit-learn pandas matplotlib jupyter`
2. Open the notebook in Jupyter, Colab or Kaggle.
3. Click Run All. CIFAR10 downloads by itself. A GPU makes it much faster.
4. Do not change the seeds. The results will match the ones below.

## Setup

* Seeds: 42, 43, 44. All results are mean ± std over these three seeds.
* Data: 50 images per class from the CIFAR10 training set (500 total). 400 are for training and 100 for validation.
* Test sets: the original 10,000 clean test images and a shifted version of them. They are never used for training or tuning.
* Shifted test: rotation up to 25 degrees, brightness and contrast change, 25% occlusion, and one extra hidden corruption.

## Model

A small CNN with two Inception style modules (1x1, 3x3 and 5x5 branches with 1x1 reductions) and global average pooling. It has about 448K trainable parameters, under the 1M limit. Trained from scratch with no pretrained weights.

## What was used

* Augmentation: crop, flip, rotation, color jitter, grayscale, blur, noise, Random Erasing, Mixup or CutMix.
* Regularization: BatchNorm, Dropout, weight decay, OneCycle learning rate, early stopping, label smoothing.
* Max 60 epochs, augmentation applied on the fly to training images only.

## Results

Fill these in from the notebook output.

| Configuration | Val Acc | Clean Test | Shifted Test |
|---|---|---|---|
| No augmentation | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| Geometric only | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| Photometric only | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| Geometric + photometric | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| + Cutout / Random Erasing | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| + Mixup or CutMix + label smoothing | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |
| Final model | XX.XX ± X.XX | XX.XX ± X.XX | XX.XX ± X.XX |

Final shifted test accuracy: **XX.XX ± X.XX %**
Biggest single improvement: **write the change name here**

## Screenshots

Take each screenshot from the notebook output, save it in the `screenshots` folder with the name shown, and the images will appear here.

**1. Clean, shifted and augmented images** (the "Look at the data" cell)

![Data samples](screenshots/data_samples.png)

**2. Baseline learning curves** (Part A plots)

![Baseline curves](screenshots/baseline_curves.png)

**3. Ablation table and bar chart** (Part D)

![Ablation results](screenshots/ablation_results.png)

**4. Confusion matrix** (Part E)

![Confusion matrix](screenshots/confusion_matrix.png)

**5. Eight misclassified images with reasons** (Part E)

![Misclassified images](screenshots/misclassified.png)

**6. Hidden corruption test and test time augmentation** (Part E and F)

![Hidden corruption and TTA](screenshots/hidden_and_tta.png)

**7. Final summary output** (last cell)

![Final summary](screenshots/final_summary.png)
