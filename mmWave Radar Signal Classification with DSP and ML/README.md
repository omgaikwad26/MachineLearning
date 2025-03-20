# mmWave Radar Object Classification with Random Forest

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📡 Project Overview
This project focuses on classifying moving objects (Cars, Drones, and People) using **mmWave radar spectrogram data**. The radar data is processed using **CFAR (Constant False Alarm Rate) detection** and includes range-Doppler matrices representing detected objects. 

I implemented a **Random Forest classifier** to automatically recognize targets based on their radar return signatures, combining **Digital Signal Processing (DSP)** techniques with **machine learning**.
---

## 🧠 Methodology

### Data
- Radar spectrograms captured via **FMCW radar** and labeled into three classes:
  - `Cars`
  - `Drones`
  - `People`
- Each radar sample is a **11x61 matrix** representing the range-Doppler map.
- Source: https://www.kaggle.com/datasets/iroldan/real-doppler-raddar-database

### Preprocessing Pipeline
- **Wavelet Denoising** (Daubechies wavelet + soft thresholding)
- **Median Filtering** (3x3 kernel)
- **Min-Max Normalization** to [0, 1] scale
- **Cropped matrices** to retain original **11x61** shape.

### Feature Engineering
- Flattened **11x61 matrices** into **671-dimensional feature vectors**.
- No handcrafted features required as Random Forest handles high-dimensional input well.

### Model
- **Random Forest Classifier**:
  - `n_estimators=100`
  - `max_depth=20`
  - Trained on an 80/20 train-test split.
  
### Visualizations
- **Feature Importance Heatmap**: Shows which Doppler and range bins were most influential.
- **Prediction Showcase**: 10 randomly selected CFAR samples, color-coded with prediction confidence bars.

---

## Results
- Model Prediction accuracy of over 91%
- Achieved strong classification results across **Cars**, **Drones**, and **People** classes.
- Identified key Doppler zones responsible for target differentiation.

---
## References:
- https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-rsn.2019.0307
- https://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.median_filter.html#scipy.ndimage.median_filter

