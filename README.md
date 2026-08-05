# Efficient Hyperspectral Image Classification using Spectral–Spatial Analysis

This project focuses on improving hyperspectral image analysis by exploring efficient dimensionality reduction and spectral–spatial feature fusion techniques. The goal is to classify land-cover materials from invisible wavelength information using benchmark hyperspectral data.

The project is directly aligned with modern diagnostic imaging research using hyperspectral technology — enabling richer material and tissue identification than standard RGB imaging.

---

## 🌈 What is Hyperspectral Imaging?

Hyperspectral cameras capture **100+ wavelengths** beyond visible light  
(UV–Visible–IR).  
Each pixel is represented as a **spectral signature** — a high-dimensional vector indicating its unique material composition.

Example shape:
Height × Width × Bands
145 × 145 × 220

---

##  Objective

The objective of this project is to build a **baseline classification pipeline using spectral signatures**, enhance its efficiency and accuracy through **dimensionality reduction with PCA**, further improve performance by **integrating spatial context for spectral–spatial fusion**, and finally **evaluate all enhancements using standard classification metrics** to demonstrate the overall improvement of the system.

## 🛰️ Dataset
**Indian Pines Hyperspectral Dataset**  
Size: `(145 × 145 × 220)` spectral cube  
Classes: **16 land-cover categories** (agriculture + vegetation)  
Labels provided as **ground truth class map**

Dataset source (Kaggle):  
🔗 https://www.kaggle.com/datasets/abhijeetgo/indian-pines-hyperspectral-dataset
---

## 🧠 Techniques Used

| Category | Methods |
|---------|---------|
| Preprocessing | Normalization, noise handling |
| Visualization | Spectral band plots, GT map |
| Dimensionality Reduction | PCA |
| Classification Baseline | SVM, KNN |
| Spectral Similarity | Spectral Angle Mapper (SAM) |
| Spatial Enhancement | Neighborhood filtering |

---

## 📊 Results

This project evaluates hyperspectral image classification using spectral-only and spectral–spatial machine learning approaches on the Indian Pines dataset.

### 🔹 Spectral Signature Analysis
- Visualized 200-band spectral signatures for representative land-cover classes
- Demonstrated clear wavelength-dependent differences between visually similar crops (e.g., corn vs soybean)
- Highlighted the advantage of hyperspectral data over RGB imagery for material discrimination

### 🔹 Baseline Spectral Classification (PCA + SVM)
- Dimensionality reduced from 200 bands to 30 principal components (≈98.6% variance retained)
- Achieved:
  - **Balanced Accuracy:** 84.2%
  - **Macro F1-score:** 0.776
- Strong performance for classes with distinct spectral signatures (Woods, Wheat, Hay-windrowed)
- Moderate confusion among spectrally similar crop types (corn and soybean variants)

### 🔹 KNN Baseline Comparison
- Evaluated K-Nearest Neighbors as a reference baseline
- Achieved:
  - **Balanced Accuracy:** 68.6%
  - **Macro F1-score:** 0.714
- Observed higher sensitivity to noise and class imbalance compared to SVM

### 🔹 Spectral–Spatial Feature Fusion (Proposed Method)
- Augmented each pixel’s spectral vector with a 3×3 neighborhood mean spectrum
- Resulting feature dimension: 400 → reduced to 30 via PCA
- Achieved:
  - **Balanced Accuracy:** 89.3%
  - **Macro F1-score:** 0.832
- Significant improvement for spectrally overlapping classes (corn and soybean variants)
- Reduced pixel-level noise and improved spatial coherence in predictions

### 🔹 Classification Map Visualization
- Generated full-scene classification map using the spectral–spatial SVM model
- Predictions show smooth, field-level regions with sharp class boundaries
- Visual comparison with ground truth confirms strong spatial alignment

### 🔹 Class-wise Performance Analysis
- Per-class precision, recall, and F1-scores computed using classification reports
- Minority classes benefited from class-weighted learning and spatial context
- Remaining errors primarily occur among highly similar crop categories

Overall, the results demonstrate that incorporating spatial context significantly enhances hyperspectral image classification performance and robustness in real-world, imbalanced datasets.


## 📁 Repository Structure
```text
Hyperspectral-Classification
├── Data
│   ├── IPgt.npy
│   └── indianpinearray.npy
│
├── Notebooks
│   └── Hyperspectral_Image_Classification_Spectral_Spatial.ipynb
│
├── results
│   ├── accuracy_comparison.png
│   ├── classification_map.png
│   ├── spectral_signature_plots.png
│   └── gt_vs_prediction.png
│
├── Report
│   └── Hyperspectral_Analysis_Report.pdf
│
└── README.md
```
## Techstack
- Python  
- NumPy, Pandas  
- scikit-learn  
- scikit-image / OpenCV  
- Matplotlib  
- Git + GitHub  
---
##  Future Work
- Apply CNN for spectral–spatial deep learning
- Extend to medical hyperspectral datasets when available
- Real-time hyperspectral segmentation
---


##  Acknowledgements
Indian Pines dataset originally captured by **AVIRIS sensor**  
Used widely in hyperspectral image classification research
> Better imaging → Earlier detection → Healthier future.
