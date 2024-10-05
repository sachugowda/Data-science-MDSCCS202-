
# ML using Scikit Learn-2

## 1. Introduction to Decision Trees and Random Forests

### Decision Trees:
- A **Decision Tree** is a supervised learning algorithm used for both classification and regression tasks.
- It splits data into subsets based on feature values and creates a tree-like model of decisions.
- The leaves represent the final classifications or predictions, and the branches represent the decision rules.

#### **Appropriate Problems for Decision Tree Learning:**
- Decision trees work well with problems that require interpretation of the model.
- Suitable for datasets where the relationships between variables are non-linear and complex.
- Not ideal for very large datasets as they can become computationally expensive.

#### **Basic Decision Tree Algorithm:**
- **Step 1**: Start with the entire dataset.
- **Step 2**: Choose the best feature to split the data.
- **Step 3**: Split the data into subsets based on this feature.
- **Step 4**: Recursively repeat the process for each subset.
- **Step 5**: Stop when no further splits are possible.

#### **Issues in Decision Tree Learning:**
- **Overfitting**: Decision trees can overfit when they grow too deep and become too specific to the training data.
- **Data Sensitivity**: Small changes in data can result in very different trees.
- **Bias**: Trees can be biased if some classes dominate the dataset.

- More detailed information on Decision Trees can be found here: [Decision Tree](https://www.geeksforgeeks.org/decision-tree-introduction-example/)

---

### Random Forests:
- **Random Forest** is an ensemble learning method that operates by constructing multiple decision trees during training and outputting the class that is the mode of the classes (classification) or mean prediction (regression) of the individual trees.
- It reduces overfitting by averaging multiple decision trees.

#### **Ensembles and Estimators in Random Forests:**
- **Ensemble Learning**: Random Forests combine the predictions of several trees to improve accuracy and robustness.
- **Estimators**: The number of trees in a random forest is determined by the `n_estimators` parameter. More estimators generally lead to better results but increase computational cost.

- More detailed information on Random Forests can be found here: [Random Forest](https://www.geeksforgeeks.org/random-forest-algorithm-in-machine-learning/)

---

## 2. K-Means Clustering

### Introduction to K-Means Clustering:
- **K-Means** is an unsupervised learning algorithm used for clustering data points into `K` groups based on feature similarity.
- It tries to minimize the variance within each cluster and assigns each point to the nearest cluster mean (centroid).

#### **Expectation and Maximization in Clustering:**
- **Expectation Step**: Each point is assigned to the nearest cluster based on the current centroid positions.
- **Maximization Step**: The centroids are recomputed based on the points assigned to each cluster.
- This process repeats iteratively until convergence, where cluster assignments no longer change.

#### **Weaknesses of K-Means Clustering:**
- **Fixed Number of Clusters**: You need to specify the number of clusters (`K`) in advance, which can be a challenge if the optimal number is unknown.
- **Sensitive to Initialization**: The results of K-Means can vary depending on the initial placement of centroids.
- **Non-Convex Clusters**: It assumes that clusters are convex and circular, which limits its ability to find more complex cluster shapes.

- More detailed information on K-Means can be found here: [K-Means](https://www.geeksforgeeks.org/k-means-clustering-introduction/)

---

## References:
- [Decision Tree Introduction](https://www.geeksforgeeks.org/decision-tree-introduction-example/)
- [Random Forest Algorithm](https://www.geeksforgeeks.org/random-forest-algorithm-in-machine-learning/)
- [K-Means Clustering Introduction](https://www.geeksforgeeks.org/k-means-clustering-introduction/)
