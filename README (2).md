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

<img width="1229" height="836" alt="image" src="https://github.com/user-attachments/assets/fd8f29b7-3117-40ec-a1c3-2708cbee56e5" />

<img width="837" height="472" alt="image" src="https://github.com/user-attachments/assets/456972a3-c75e-4313-a420-b89ee797b6a5" />

**2. Baseline learning curves** (Part A plots)

<img width="1139" height="773" alt="image" src="https://github.com/user-attachments/assets/e7542761-2b08-4f68-bfd4-2bad4451da1f" />


**3. Ablation table and bar chart** (Part D)

<img width="1143" height="499" alt="image" src="https://github.com/user-attachments/assets/d443d419-b65a-49dc-83bb-216177046049" />

**4. Confusion matrix** (Part E)

<img width="1095" height="764" alt="image" src="https://github.com/user-attachments/assets/5e6e1593-2795-47fa-b750-9a1c63edab83" />


**5. Eight misclassified images with reasons** (Part E)

<img width="1147" height="728" alt="image" src="https://github.com/user-attachments/assets/024756a3-0938-4109-8844-03510b2fb092" />

**6. Hidden corruption test and test time augmentation** (Part E and F)

<img width="949" height="191" alt="image" src="https://github.com/user-attachments/assets/986f3302-1439-47d1-8b0d-322eecdf6741" />


**7. Final summary output** (last cell)

<img width="1035" height="521" alt="image" src="https://github.com/user-attachments/assets/c4941e91-1215-4b59-aff5-9592e046e43b" />

