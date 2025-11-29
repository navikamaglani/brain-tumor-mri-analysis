#  Automated Brain Tumor Classification & Segmentation  
### Hybrid Classical Image Processing + CNN Analysis (T1-Weighted MRI)

This project implements a complete end-to-end pipeline for **brain tumor detection, segmentation, and classification** using a blend of classical image processing techniques and a custom **Convolutional Neural Network (CNN)**.  

The system works with **T1-weighted contrast-enhanced MRI slices** from the publicly available **Figshare dataset** and achieves:

-  **98% classification accuracy** across meningioma, glioma, and pituitary tumors  
-  Classical tumor segmentation using thresholding + morphology  
-  Hyperparameter sensitivity analysis  
-  Model interpretability using **Grad-CAM++**  
-  Texture analysis using GLCM features  

---

##  Pipeline Overview

**Classical Segmentation Pipeline**
1. Load grayscale MRI slice  
2. Median filtering (noise removal)  
3. Histogram normalization  
4. Percentile thresholding (85–90%)  
5. Morphological refinement  
6. Largest connected component extraction  
7. Tumor mask overlay  

**Deep Learning Classification Pipeline**
- 3-layer CNN (32 → 64 → 128 filters)  
- ReLU activations  
- Max-pooling  
- Dense layer (128 units)  
- Dropout regularization  
- Softmax output (3 classes)  

**Explainability**
- Manual **Grad-CAM++** implementation  
- Highlighted class-discriminative regions  
- Identifies whether the model is focused on tumor areas  
---

##  Results Summary

### **Segmentation**
Classical segmentation showed:
- Good separation for high-contrast tumors  
- Failures for low-contrast gliomas  
- Sensitivity to threshold percentile and median filtering  

### **Classification**
- ✔ 98% accuracy (test set)  
- ✔ Strong performance across all three tumor classes  
- ✔ Grad-CAM++ confirms model attention on tumor regions  

---

## Dataset
Dataset: **Cheng et al., Figshare Brain Tumor MRI Dataset**  

Contains:
- 766 T1-weighted MRI slices  
- Tumor labels (meningioma, glioma, pituitary)  
- MATLAB `.mat` files with image & metadata  

Dataset link: https://figshare.com/articles/dataset/brain_tumor_dataset/1512427  

---

##  Installation & Usage
pip install -r requirements.txt

Open the notebook:

Run the cells to perform:
- Data extraction  
- Preprocessing  
- Segmentation  
- CNN training  
- Grad-CAM++ visualization  

---

## 🧪 Hyperparameter Analysis

### **Median Filter Size**
| Kernel | Tumor Area | Dice |
|--------|------------|------|
| 3      | 562 px     | 0.0033 |
| 5      | 739 px     | 0.0033 |

### **Threshold Percentile**
| Percentile | Tumor Area | Dice |
|------------|-------------|------|
| 85         | 739 px      | 0.0028 |
| 90         | 403 px      | 0.0028 |

---

##  Future Improvements
- Integrate **U-Net** for deep segmentation  
- Add multimodal MRI (T2, FLAIR, DWI)  
- Move to **3D CNNs** for volumetric context  
- Patient-level train/validation split  
- External dataset validation  

---







