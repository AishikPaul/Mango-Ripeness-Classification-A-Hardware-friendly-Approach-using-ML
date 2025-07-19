# Mango Image Classification Using Handcrafted Feature Extraction and Random Forest Classifier

## Overview

This project implements a complete pipeline for **classifying mango images** using a wide range of **handcrafted features** derived from color, texture, and shape information. The classification is performed using a **Random Forest Classifier**, and the approach is fully interpretable and lightweight.

---

## Dataset Structure




Each subfolder represents a mango class (e.g., *ripe*, *unripe*, *diseased*), containing relevant images.

---

## Feature Extraction

### Preprocessing Steps:
- Resize all images to **100×100** pixels.
- Convert each image to:
  - **Grayscale**
  - **HSV**
  - **LAB**

### Extracted Features:
1. **Color Statistics**:
   - RGB: mean, standard deviation, skewness (for each channel)
   - HSV and LAB: mean and standard deviation (for each channel)

2. **Grayscale Intensity**:
   - Mean and standard deviation

3. **Yellow Pixel Percentage**:
   - Percentage of pixels with Hue ∈ [20, 40] in HSV (indicating yellow region)

4. **Dark Pixel Percentage**:
   - Percentage of pixels with Value < 50 in HSV

5. **Local Binary Pattern (LBP)**:
   - Uniform LBP with 10-bin histogram (P=8, R=1)

6. **Edge Density**:
   - Ratio of edge pixels using Canny Edge Detection

7. **Color Histograms**:
   - 16-bin normalized histograms for each RGB channel

8. **Shape Features**:
   - Contour-based: Area, Perimeter, Circularity of the largest contour

9. **Haralick Texture Features**:
   - 13 statistical descriptors from GLCMs (using `mahotas`)



---

## Classification Model

### Model: **Random Forest Classifier**
- Implementation: `scikit-learn`
- Parameters:
  - `n_estimators=100`
  - `random_state=42`

### Preprocessing:
- Feature Standardization using `StandardScaler`

### Evaluation Metrics:
- Accuracy
- Classification Report (Precision, Recall, F1-score)
- Confusion Matrix

---

## Results


> Accuracy: 91.87%

---

## Highlights

- Fully interpretable handcrafted pipeline
- Lightweight, no deep learning required
- Easy to adapt for other fruits or agricultural products

---


## Conclusion

This handcrafted approach to mango classification offers a balance between **performance and interpretability**, making it an ideal choice for real-world applications in agricultural automation, especially where resources are limited.

---
