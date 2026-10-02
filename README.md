# CSC2062: Image Feature Extraction and Statistical Analysis

## Overview
This repository contains a comprehensive pipeline for processing, analyzing, and classifying a dataset of 112 PGM images. The project bridges fundamental computer vision techniques with rigorous statistical testing and machine learning. The initial processing phase reads the raw PGM files, applies a 128-midpoint threshold to binarize the data, and converts the output into structured CSV matrices for downstream analysis.

## Feature Extraction
The project systematically extracts 13 geometric and topological features from the image matrices using custom Python algorithms:
* **Standard Features:** Calculates properties such as bounding boxes, aspect ratios, and total pixel areas.
* **Topological Analysis:** Utilizes 8-way connectivity to identify general regions and 4-way orthogonal connectivity to detect specific internal features (e.g., "eyes" or hollowness). 
* **Custom Feature Engineering:** Implements an `Extent` feature (the ratio of object area to bounding box area) to successfully differentiate objects with identical bounding boxes and aspect ratios.

## Statistical Analysis
To evaluate the descriptive power of the extracted features, the project applies several statistical methods:
* **Normality Testing:** Evaluates the distribution of pixel counts across the dataset using theoretical normal distribution thresholds (`norm.ppf`) to identify outliers.
* **Hypothesis Testing:** Conducts Welch's T-Tests across 16 derived variables to determine statistical significance and evaluate null hypotheses.
* **Correlation:** Analyzes feature independence and relationships to prevent multicollinearity in predictive models.

## Machine Learning & Classification
The final phase of the pipeline evaluates the predictive power of the extracted features using `scikit-learn`:
* **Multiple Linear Regression:** Models continuous relationships and evaluates individual feature significance (e.g., isolating the impact of height and width).
* **Logistic Regression:** Fits a binary classification model (visualized with an S-shaped probability curve) to categorize the processed image data.

## Tech Stack
* **Language:** Python
* **Libraries:** NumPy, Pandas, SciPy, scikit-learn, Matplotlib/Seaborn (for visualization)
* **Environment:** Jupyter Notebook
