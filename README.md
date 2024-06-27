# Clustering Project: Wine Quality Dataset Analysis

---

## Overview

This project explores clustering techniques on the "Wine Quality Dataset" to classify wine samples based on their chemical properties. We leverage two clustering algorithms, K-Means and Agglomerative Clustering, to analyze the dataset and uncover potential groupings. The goal is to identify meaningful clusters that correspond to inherent characteristics of the wine, potentially relating to their quality or type (red or white).

---

## Introduction

The "Wine Quality Dataset" is a widely-used dataset in the field of machine learning and data analysis. It includes data on the chemical properties and quality ratings of Portuguese "Vinho Verde" wine, both red and white variants. The quality ratings, given by professional wine tasters, range from 0 to 10. This dataset presents an excellent opportunity to apply clustering techniques to uncover patterns in the chemical properties that may influence wine quality.

---

## Dataset Information

### Dataset Name and URL

- **Dataset Name:** Wine Quality Dataset
- **Dataset URL:** [Wine Quality Dataset](https://archive.ics.uci.edu/ml/datasets/Wine+Quality)

### Data Dictionary

The dataset contains the following features:

- **fixed acidity:** Fixed acidity (g(tartaric acid)/dm³)
- **volatile acidity:** Volatile acidity (g(acetic acid)/dm³)
- **citric acid:** Citric acid (g/dm³)
- **residual sugar:** Residual sugar (g/dm³)
- **chlorides:** Chlorides (g(sodium chloride)/dm³)
- **free sulfur dioxide:** Free sulfur dioxide (mg/dm³)
- **total sulfur dioxide:** Total sulfur dioxide (mg/dm³)
- **density:** Density (g/cm³)
- **pH:** pH level
- **sulphates:** Sulphates (g(potassium sulphate)/dm³)
- **alcohol:** Alcohol content (% vol.)
- **quality:** Wine quality (score between 0 and 10)
- **color:** Wine color (red/white)

---

## Data Preparation

The data preparation process involves loading the dataset, combining the red and white wine data, standardizing the features, and preparing the data for clustering.

---

## Clustering Algorithms

We utilize two clustering algorithms for this analysis:

1. **K-Means Clustering:** A popular algorithm that partitions data into `k` clusters by minimizing the variance within each cluster.
2. **Agglomerative Clustering:** A hierarchical clustering method that builds nested clusters by repeatedly merging pairs of clusters.

---

## Optimal Number of Clusters

To determine the optimal number of clusters, we evaluate the silhouette scores for a range of cluster numbers. The silhouette score measures how similar an object is to its own cluster compared to other clusters, ranging from -1 to 1. A high silhouette score indicates well-defined clusters.

---

## Applying the Best Clustering Models

Based on the silhouette scores, we apply the best clustering models to the data and visualize the results.

### K-Means Clustering

- **Silhouette Score:** 0.27053
- **Best Parameters:** `{'init': 'random', 'max_iter': 300, 'n_clusters': 2, 'n_init': 20, 'tol': 0.0001}`
- **Interpretation:** The K-Means clustering results show two well-defined clusters. These clusters align significantly with the red and white wine types, suggesting that K-Means effectively identifies the inherent division between these two wine types. The centroids of each cluster provide insights into the typical chemical compositions of different wine types, such as levels of acidity, sugar content, and alcohol percentage.

### Agglomerative Clustering

- **Silhouette Score:** 0.78968
- **Best Parameters:** `{'linkage': 'complete', 'metric': 'euclidean', 'n_clusters': 2}`
- **Interpretation:** Despite the high silhouette score, the Agglomerative Clustering results indicate an issue with clustering quality. One cluster contains only a single data point while the other contains the rest, suggesting that this method did not form meaningful clusters. The high silhouette score is misleading as it does not reflect the practical effectiveness of the clustering.

### Analysis of K-Means Clustering with 3 Clusters

- **Silhouette Score:** 0.23002
- **Interpretation:** Although the silhouette score is slightly lower than the 2-cluster model, the 3-cluster model may reveal additional structure within the data, potentially indicating sub-classifications within the red and white wines. This can provide further insights into variations in wine characteristics such as acidity or sugar content levels.

---

## Parameter Justification

The parameters for both K-Means and Agglomerative Clustering were chosen to maximize the average silhouette score. The parameter grids ensured a comprehensive search for the best configurations:

### K-Means Clustering Parameter Grid

- **n_clusters:** Number of clusters (range: 2 to 7)
- **init:** Initialization method ('k-means++' and 'random')
- **n_init:** Number of initializations (10 and 20)
- **max_iter:** Maximum iterations (300 and 500)
- **tol:** Tolerance (1e-4 and 1e-3)

### Agglomerative Clustering Parameter Grid

- **n_clusters:** Number of clusters (range: 2 to 7)
- **metric:** Distance metric ('euclidean', 'l1', 'l2', 'manhattan', 'cosine')
- **linkage:** Linkage criterion ('ward', 'complete', 'average', 'single')

This comprehensive approach ensured that we explored a wide range of parameter settings to identify the optimal configurations for each clustering algorithm.

---

## Conclusion

Both K-Means and Agglomerative Clustering provided insights into the wine dataset's structure.

- **K-Means Clustering:** Effectively identifies the division between red and white wines. The 2-cluster model is particularly meaningful, with the potential for further insights from the 3-cluster model.
- **Agglomerative Clustering:** Despite a high silhouette score, the clustering results are flawed due to impractical grouping, indicating the need for careful interpretation of high silhouette scores.

Overall, K-Means clustering is more reliable for this dataset, successfully capturing the primary division between red and white wines and potentially revealing additional sub-structure. Agglomerative Clustering results should be interpreted with caution due to the identified issues with cluster formation.

---

## Dependencies and Resources

- **Python**: 3.x
- **pandas**: Data manipulation and analysis
- **matplotlib**: Plotting and visualization
- **seaborn**: Statistical data visualization
- **scikit-learn**: Machine learning library
- **numpy**: Numerical operations
- **silhouette_score**: Metric for evaluating clustering quality

---

This project demonstrates the application of clustering techniques to classify wine samples based on their chemical properties, providing a foundation for further exploration and understanding of wine quality.
