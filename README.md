# Anomaly-and-Change-Point-Detection-in-Nonstationary-Time-Series

This repository contains a Jupyter Notebook exploring the interaction between change point detection and anomaly detection methods. The goal is to evaluate whether preprocessing a signal with change point detection can improve anomaly detection performance, particularly in cases where anomalies have small magnitudes and would otherwise be overshadowed by underlying trends or structural changes.
The notebook compares different approaches using synthetic datasets as well as a network traffic dataset.

## Key Goals
- **Data generation**: Create synthetic signals with configurable change points and injected anomalies.  
- **Change point detection**: Apply methods such as CuSum, Binary Segmentation, and R-FPOP.  
- **Anomaly detection**: Compare Local Outlier Factor (LOF) and K-Means++ clustering, with and without preprocessing by change point detection.  
- **Evaluation**: Assess detection performance using F1-score, precision, and recall.  
- **Case study**: Apply the workflow to network throughput data to illustrate performance on real-world signals.  

## Structure of the Notebook
1. **Data-generating functions** – tools to create synthetic datasets with configurable change points and anomalies.  
2. **Change point detection** – implementation and comparison of algorithms (CuSum, Binary Segmentation, R-FPOP).  
3. **Anomaly detection** – application of LOF and K-Means++ directly on raw data and on residuals after change point preprocessing.  
4. **Evaluation metrics** – precision, recall, and F1-score reported across experiments.  
5. **Case study** – network dataset analysis with throughput signal and anomalies labeled.  

## Main Findings
- Built-in R-FPOP anomaly detection did not detect anomalies effectively.  
- Both **LOF** and **K-Means++** improved when applied on **R-FPOP residuals** instead of raw data.  
- F1-scores increased significantly:  
  - LOF: **0.50 → 0.633**  
  - K-Means++: **0.575 → 0.689**  
- Recall improved for both methods.  
- Precision improved for LOF but slightly decreased for K-Means++.  
- This suggests that change point detection helps isolate underlying trends, allowing anomaly detection methods to focus on smaller-magnitude anomalies.  

## Requirements
To run the notebook, you need an R installation for the R-FPOP part of the notebook. Install the following dependencies:

```bash
pip install numpy pandas matplotlib scikit-learn scipy ruptures rpy2

