```markdown
# Anomaly Detection in Compressor Operations

This repository contains the implementation of an anomaly detection system for compressor operations at Numaligarh Refinery Limited (NRL), developed as part of a summer internship project by Hrishab Kakoty, Julon Senapati, Jitu Boro, Jintumoni Basumatary, and Kuldip Das from Central Institute of Technology, Kokrajhar.

## Project Overview

The project focuses on detecting anomalous behavior in compressor operational metrics using the K-Means clustering algorithm on an unlabelled dataset. The dataset includes operational metrics such as `Suction_Flow`, `Suction_Pressure`, `Discharge_Flow`, and `Discharge_Pressure`, collected over time.

### Objective
- Perform clustering to identify natural groupings in compressor data.
- Detect anomalies by identifying data points that deviate significantly from clusters.

## Dataset
- **Source**: Compressor operational data from NRL.
- **Columns**: `TimeStamp`, `Suction_Flow`, `Suction_Pressure`, `Discharge_Flow`, `Discharge_Pressure`.
- **Size**: 3753 rows.

## Prerequisites
- Python 3.11+
- Libraries: `numpy`, `pandas`, `scikit-learn`, `matplotlib`, `seaborn`
- Install dependencies:
  ```bash
  pip install numpy pandas scikit-learn matplotlib seaborn
  ```

## Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/compressor-anomaly-detection.git
   cd compressor-anomaly-detection
   ```
2. Ensure the dataset (`compressor_data.csv`) is in the project root.
3. Run the analysis script or notebook:
   ```bash
   jupyter notebook anomaly_detection.ipynb
   ```

## Methodology
- **Data Preprocessing**: Dropped rows with missing values in numeric columns (`Suction_Flow`, `Suction_Pressure`, `Discharge_Flow`, `Discharge_Pressure`).
- **K-Means Clustering**: Applied K-Means with varying cluster counts (K=2, K=3, K=4) to group similar data points.
- **Anomaly Detection**: Identified anomalies as data points exceeding a distance threshold from their cluster centroid.
- **Evaluation**: Used silhouette scores to assess clustering quality.

## Comparison of K=2, K=3, and K=4
- **K=3 Clusters**:
  - **Cluster Sizes**: [2929, 117, 447]
  - **Silhouette Score**: ~0.923
  - **Pairwise Distances**:
    ```
    Cluster_1: [0.000000, 6583.899516, 16438.509688]
    Cluster_2: [6583.899516, 0.000000, 15437.567249]
    Cluster_3: [16438.509688, 15437.567249, 0.000000]
    ```
  - **Observation**: Smaller clusters (e.g., size 117) were considered anomalous due to low data point counts (<10% of total).
- **K=2 Clusters**:
  - **Silhouette Score**: ~0.923 (slightly better fit).
  - **Observation**: Provided better clustering quality, indicating two natural groupings in the data, with fewer anomalies detected, suggesting a more cohesive structure.
- **K=4 Clusters**:
  - **Silhouette Score**: Lower than K=2 and K=3 (exact value not specified but implied less optimal).
  - **Observation**: Increased cluster count led to less distinct groupings, reducing anomaly detection effectiveness.

**Conclusion**: The K=2 model was found to be the best fit based on the highest silhouette score, indicating better cluster separation and more reliable anomaly detection.

## Results
- **Anomalies**: Identified based on distance thresholds and smaller cluster sizes.
- **Visualization**: Pair plots highlighted anomalies in red, showing relationships between features.
- **Insights**: Anomalies corresponded to unusual compressor behaviors, with timestamps aiding further investigation.

![1stNRL Image 19](https://github.com/user-attachments/assets/3a7c32ec-1651-4160-9165-fda6375baf6a)

