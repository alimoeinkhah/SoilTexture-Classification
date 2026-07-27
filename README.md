# Soil Texture Classification Using Sentinel-2 and Landsat-9

An end-to-end remote sensing and machine learning workflow for mapping clay- and sand-dominated soils at two depth intervals in Semnan Province, Iran.

## Project Overview

This project investigates the use of freely available Sentinel-2 and Landsat-9 imagery for soil texture classification across a 143.9 km² arid region in Semnan Province, Iran.

Spectral bands and indices were combined with 3,000 SoilGrids samples to classify clay and sand content at two soil depths:

- 0–5 cm (surface soil)
- 5–15 cm (subsurface soil)

Random Forest (RF) and Support Vector Machine (SVM) classifiers were trained and evaluated using five-fold cross-validation. Random Forest consistently outperformed SVM across both sensors, soil components, and depth intervals.

## Study Data

| Dataset | Description |
|---|---|
| Sentinel-2 | Cloud-free Level-2A image acquired on 28 May 2024 |
| Landsat-9 | Surface reflectance image acquired on 26 May 2024 |
| SoilGrids | 3,000 soil samples containing clay and sand information |
| Study area | 143.9 km² in Semnan Province, Iran |
| Soil depths | 0–5 cm and 5–15 cm |

## Methodology

The project was implemented through the following workflow:

1. Satellite image acquisition and preprocessing
2. Cloud and cloud-shadow masking
3. Study-area clipping
4. Spectral-band extraction
5. Vegetation and soil index calculation
6. SoilGrids sample preparation
7. Satellite-value extraction at sample locations
8. Correlation and regression analysis
9. Class balancing using SMOTE
10. Random Forest and SVM model training
11. Five-fold cross-validation
12. Accuracy and Cohen’s Kappa evaluation
13. Feature-importance analysis
14. Production of classified soil texture maps

## Spectral Features

The analysis included satellite spectral bands and several vegetation and soil-related indices:

- NDVI
- SAVI
- EVI
- MCARI
- IRECI
- MTCI
- S2REP

## Machine Learning Models

### Random Forest

Random Forest was implemented with 100 decision trees and the Gini impurity criterion. It produced the strongest and most stable results across all configurations.

### Support Vector Machine

SVM was implemented using the Radial Basis Function kernel. Its performance was generally lower than Random Forest, particularly for clay classification.

## Model Performance

### Sentinel-2 Results

| Soil component | Depth | Model | Accuracy | Kappa |
|---|---:|---|---:|---:|
| Clay | 0–5 cm | RF | 83.51% | 0.670 |
| Clay | 0–5 cm | SVM | 54.46% | 0.089 |
| Clay | 5–15 cm | RF | 82.84% | 0.657 |
| Clay | 5–15 cm | SVM | 53.22% | 0.065 |
| Sand | 0–5 cm | RF | 87.44% | 0.749 |
| Sand | 0–5 cm | SVM | 61.48% | 0.230 |
| Sand | 5–15 cm | RF | 87.45% | 0.749 |
| Sand | 5–15 cm | SVM | 59.90% | 0.198 |

### Landsat-9 Results

| Soil component | Depth | Model | Accuracy | Kappa |
|---|---:|---|---:|---:|
| Clay | 0–5 cm | RF | 83.12% | 0.662 |
| Clay | 0–5 cm | SVM | 53.97% | 0.079 |
| Clay | 5–15 cm | RF | 82.68% | 0.654 |
| Clay | 5–15 cm | SVM | 52.28% | 0.046 |
| Sand | 0–5 cm | RF | **89.49%** | **0.790** |
| Sand | 0–5 cm | SVM | 72.67% | 0.454 |
| Sand | 5–15 cm | RF | 89.18% | 0.784 |
| Sand | 5–15 cm | SVM | 69.51% | 0.390 |

## Key Findings

- Random Forest consistently outperformed SVM across all configurations.
- The best result was obtained using Landsat-9 and Random Forest for surface sand classification.
- The best-performing model achieved 89.49% accuracy and a Kappa coefficient of 0.790.
- Sentinel-2 and Random Forest achieved 87.45% accuracy for subsurface sand classification.
- Landsat-9 showed strong performance for sand mapping, supported by its SWIR bands and EVI.
- Sentinel-2 red-edge bands and IRECI contributed strongly to clay discrimination.
- Both sensors demonstrated potential for scalable soil texture mapping in arid and semi-arid environments.

## Technologies

- Python
- Google Earth Engine
- Rasterio
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Sentinel-2
- Landsat-9
- SoilGrids

## Repository Structure

```text
SoilTexture-Classification/
├── Sentinel-2/
│   ├── preprocessing and index-calculation scripts
│   ├── machine-learning scripts
│   ├── trained models
│   └── classified maps
├── Landsat-9/
│   ├── preprocessing and index-calculation scripts
│   ├── machine-learning scripts
│   ├── trained models
│   └── classified maps
├── feature_importance_plots/
├── Other/
│   └── SoilGrids_Points.csv
└── README.md
```

## Project Context

Developed as part of the MSc in Geoinformatics Engineering at Politecnico di Milano.

- **Authors:** Ali Moeinkhah and Hafizullah Sarwary
- **Supervisors:** Prof. Mariagrazia Fugini and Prof. Giovanna Venuti
- **Academic year:** 2024–2025
