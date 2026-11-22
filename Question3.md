## Question 3
How do you choose the number of clusters k, and how would you argue your clustering is good when there are no ground-truth labels?

## Answer
### Requirement 1
There is no single correct k, because "The number of clusters and memberships are unknown" in clustering.[1] So I would use several unsupervised measures and check that they agree.

**1. Choosing k**

SSE elbow: We cannot just pick the k with the lowest SSE. "An obvious way to reduce the SSE is to find more clusters," but "increasing the number of clusters is not always desirable."[2] If k equals the number of points and SSE = 0, but that tells us nothing. Instead, “we can try to find the natural number of clusters in a data set by
looking for the number of clusters at which there is a knee, peak, or dip in
the plot"[3] In the textbook example, there is "a distinct knee in the SSE and a distinct peak in the silhouette coefficient when the number of clusters is equal to 10."[3]

A real example: In a course paper, the authors tested k from 1 to 21 using WSSand the elbow method, and chose k = 6.[4]

Hierarchical clustering: We can also cut a dendrogram, because "Once a dendrogram is created, one can have a different number of clusters whenever needed."[5]

**2. Arguing the clustering is good without labels**

Step 1: Check that clusters really exist. "almost every clustering algorithm will find clusters in a data set, even if that data set has no natural cluster structure."[6]

Step 2: Measure cohesion and separation. The silhouette coefficient uses both: s = (b − a) / max(a, b), [7] For each point, we "calculate its average distance to all other objects in its cluster. Call this value ai." Then, for every other cluster,”calculate
the object’s average distance to all the objects in the given cluster. Find
the minimum such value with respect to all clusters; call this value bi.
" Finally, "the silhouette coefficient is si = (bi − ai)/ max(ai, bi)."[8]
- If a = 2 and b = 5, then s = (5 − 2)/5 = 0.6. Good: the point is closer to its own cluster.
- If a = 4 and b = 3, then s = (3 − 4)/4 = −0.25. Bad: "A negative value is undesirable."[8]

Step 3: Check that the clusters make sense. The course paper compared "intracluster means of each derived variable with global means" to describe how each cluster differs from the overall population.[9] The paper then trained a classifier on the cluster labels, with "a dual objective: achieving cluster interpretability through local and global SHAP values, and developing a tool for classifying future students.” [9]


[1]: CDS 303 Lecture, *Cluster Analysis (1)* (Week 13-1), slide 4 "Supervised vs. Unsupervised"

[2]: CDS 303 Lecture, *Cluster Analysis (1)* (Week 13-1), slide 22 "Reducing the SSE with post-processing."

[3]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 8 8.5.5 "Determining the Correct Number of Clusters," p. 546.

[4]: Alvarez-Garcia, Ibar-Alonso & Arenas-Parra (2024), "A comprehensive framework for explainable cluster analysis," *Information Sciences* 663, 120282 (CDS 303 course reading), p.13.

[5]: CDS 303 Lecture, *Cluster Analysis (1)* (Week 13-1), slide 29 "Dendrogram."

[6]: Tan et al., Ch. 8 8.5 "Cluster Evaluation," p. 532.

[7]: CDS 303 Lecture, *Cluster Analysis (2)* (Week 13-2), slide 23 "Silhouette Coefficient"

[8]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 8 8.5.2, "The Silhouette Coefficient," p.541.

[9]: Alvarez-Garcia et al. (2024), *Computers & Education* 223, 105166 (CDS 303 course reading), 3.3.3 "Clustering" and 3.3.4 "Classification."


### Requirement 2 

**AI-generated answer**

1. Loan Default Prediction: Model Comparison

To predict loan defaults, I would compare Logistic Regression, Decision Tree, and Random Forest.

- Logistic Regression: It is easy to interpret and explains how different factors affect the probability of loan default. However, it may struggle with complex, non-linear relationships.
- Decision Tree: It uses a series of rules to make predictions and can capture non-linear relationships. However, it can easily overfit the training data.
- Random Forest: It combines multiple decision trees to improve prediction accuracy and reduce overfitting. However, it is more complex and less interpretable than a single decision tree.

My Choice: Random Forest

I would choose Random Forest because loan default prediction involves many factors, such as income, credit score, debt, and payment history. These factors may have complex relationships. Random Forest can capture these patterns while reducing overfitting.

I would evaluate the model using precision, recall, F1-score, and ROC-AUC instead of relying only on accuracy, especially if the dataset is imbalanced. I would also use feature importance or SHAP values to understand the model's predictions.

2. Choosing the Number of Clusters (k)

When there are no ground-truth labels, I would use several methods to determine the optimal number of clusters.

- Elbow Method: I would run K-Means with different values of k and calculate the Within-Cluster Sum of Squares (WCSS). I would look for the elbow point where the decrease in WCSS starts to slow down.
- Silhouette Score: It measures how similar a data point is to its own cluster compared to other clusters. A higher score generally indicates better-defined clusters.
- Davies-Bouldin Index: It measures the similarity between clusters. A lower score indicates better separation.

How to Evaluate Clustering Without Ground-Truth Labels

Since there are no true labels, I would evaluate clustering quality based on:

- Cluster Separation: Check whether clusters are clearly separated.
- Cluster Cohesion: Check whether data points within each cluster are similar.
- Stability: Check whether similar clusters appear when running the algorithm multiple times or using different samples.
- Interpretability: Determine whether each cluster has meaningful and understandable characteristics.

Conclusion

I would combine the Elbow Method and Silhouette Score to choose a reasonable value of k. Then, I would evaluate the results using cluster separation, stability, and interpretability. A good clustering result should not only have good evaluation scores but also produce meaningful and useful groups.

**Critique of the AI answer** 
