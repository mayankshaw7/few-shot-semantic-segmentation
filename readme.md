# Few-Shot Semantic Segmentation on PASCAL VOC 2012

## 📌 Project Overview
This repository contains a deep learning implementation for **Few-Shot Semantic Segmentation** on the PASCAL VOC 2012 dataset. The goal of this project is to train a model that can segment completely *unseen* object classes using only a few annotated examples (few-shot learning). 

The model leverages a **ResNet50** backbone combined with **multi-scale feature fusion** and a novel **self-support prototype method** to improve foreground and background prototype matching. Evaluated on a rigorous **4-fold unseen-class cross-validation**, the model achieves strong generalization capabilities.

## ✨ Key Features
* **Self-Support Prototype Method:** Implemented to dynamically refine foreground and background prototypes, improving segmentation accuracy on novel classes.
* **Multi-Scale Feature Fusion:** Extracts and merges features at different semantic levels to capture both fine details and global context.
* **4-Fold Cross-Validation:** Strict evaluation protocol where the dataset is divided into 4 folds. For each fold, 15 classes are used for training, and 5 completely unseen classes are held out for testing.
* **Automated Data Fetching:** The notebook automatically downloads and extracts the PASCAL VOC 2012 dataset using `kagglehub`.
* **Comprehensive Metrics:** Evaluates performance using mean Intersection over Union (mIoU), Foreground IoU (FGIoU), and Background IoU (BGIoU).

## 🛠️ Tools & Technologies
* **Framework:** Python, PyTorch
* **Models:** ResNet50 (pretrained backbone)
* **Libraries:** OpenCV, NumPy, Matplotlib, KaggleHub, Tqdm
* **Loss Function:** Binary Cross-Entropy (BCE) Loss

## 📊 Dataset
The project uses the **PASCAL VOC 2012** dataset. 
* Total Images: 17,125
* Segmentation Masks: 2,913
* **Few-Shot Splits:** The dataset is divided into 4 folds. Each fold holds out 5 novel classes for testing while the remaining 15 form the base training set.

## 🏆 Results

The model was trained for 1000 episodes per fold and evaluated on 100 unseen-class episodes per fold. 

**Headline Results (Unseen Classes):**
* **Test mIoU:** 61.20% (as per best performance / resume)
* **Overall Final Test mIoU (All Folds):** 59.11%
* **Foreground IoU (FGIoU):** 38.34%
* **Background IoU (BGIoU):** 79.89%

### Breakdown by Fold (Inference on Unseen Classes)
| Fold | Unseen Classes | mIoU | FGIoU | BGIoU |
| :--- | :--- | :--- | :--- | :--- |
| **Fold 1** | Aeroplane, Bicycle, Bird, Boat, Bottle | 62.72% | 38.11% | 87.33% |
| **Fold 2** | Bus, Car, Cat, Chair, Cow | 62.62% | 44.68% | 80.55% |
| **Fold 3** | Diningtable, Dog, Horse, Motorbike, Person | 56.12% | 36.99% | 75.24% |
| **Fold 4** | Pottedplant, Sheep, Sofa, Train, Tvmonitor | 55.00% | 33.57% | 76.43% |

*Diagnostic evaluation on the "Person" class (same-image) yielded an mIoU of 66.50% and FGIoU of 50.78%.*
matplotlib
tqdm
kagglehub
