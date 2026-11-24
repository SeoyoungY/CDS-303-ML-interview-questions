## Question 4
Why do distance-based methods like k-NN and k-means struggle in high dimensions, and what would you do about it?

## Answer
### Requirement 1

1. Why they struggle

-Data becomes sparse: "The curse of dimensionality refers to the phenomenon that many types of data analysis become significantly harder as the dimensionality of the data increases." As dimensions grow, "the data becomes increasingly sparse."[1] The lecture adds that "The number of instances increases exponentially to achieve the same explanation ability."[2] For example, say we want 10 points per unit length. In 1 dimension, we need 10 points. In 2 dimensions, we need 10² = 100. In 10 dimensions, we need 10¹⁰ = 10,000,000,000 points. This is because volume grows like r^d, so "unless the number of points grows exponentially with the number of dimensions, the density tends to 0."[3]

-Distances become similar: "proximity tends to become more uniform in high-dimensional spaces," because "there are more dimensions (attributes) that contribute to the proximity between two points."[3] If every point is about the same distance away, the "nearest" neighbor or centroid is not really near. For clustering, "the definitions of density and the distance between points which are critical for clustering become less meaningful." [1] which leads to "reduced classification accuracy and poor quality clusters."[4]

-Useless and badly scaled features add noise: Euclidean distance "treats all dimensions equally,"[5] so k-NN is "Sensitive to lots of irrelevant attributes (affect distance)."[5] Scale also matters. The textbook gives an example: "The height attribute has a low variability, ranging from 1.5 m to 1.85 m, whereas the weight attribute may vary from 90 lb. to 250 lb."[6] So height changes by at most 1.85 − 1.5 = 0.35, but weight can change by 250 − 90 = 160. Without scaling, "the proximity measure may be dominated by differences in the weights of a person."[6]

2. What I would do
- Scale the features: The textbook says standardization "is often necessary to avoid having a variable with large values dominate the results of the calculation."[7]
- Remove useless features: Feature selection keeps only useful attributes. This does not lose information "if redundant and irrelevant features are present."[8]
- Reduce dimensions with PCA:  PCA finds new attributes that "capture the maximum amount of variation in the data."[8] The course paper say "This approach helps address the curse of dimensionality associated with k-means using Euclidean distance."[9]


[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.3 "Dimensionality Reduction – The Curse of Dimensionality," p. 51.

[2]: CDS 303 Lecture, *Dimensionality reduction* (Week 11-1), slide 7 "Curse of Dimensionality.”

[3]: Tan et al., Ch.9.1.2 "Data Characteristics – High Dimensionality," p. 572.

[4] Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.3 "Dimensionality Reduction – The Curse of Dimensionality," p. 52. 

[5]: CDS 303 Lecture, *Nearest Neighbor* (Week 4-2), slide 9 "Choice of proximity measure matters" and slide 15 "Pros and Cons."

[6]: Tan et al., Ch.5.2.2 "Characteristics of Nearest-Neighbor Classifiers," p. 227.

[7]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.7 "Variable Transformation – Normalization or Standardization," p. 64.

[8]: Tan et al., Ch.2.3.3 "Linear Algebra Techniques for Dimensionality Reduction" and 2.3.4 "Feature Subset Selection," p. 52.

[9]: Alvarez-Garcia, Arenas-Parra & Ibar-Alonso (2024), "Uncovering student profiles. An explainable cluster analysis approach to PISA 2022," *Computers & Education* 223, 105166 (CDS 303 course reading), Ch 3.3.3 "Clustering," p. 7.




### Requirement 2 

**AI-generated answer**

Distance-based methods like k-NN and k-means struggle in high-dimensional data because of the curse of dimensionality.

As the number of features increases, data points become more spread out, and the distances between points become less meaningful. It becomes harder to identify which points are truly similar or close to each other.

For example, in a dataset with hundreds of features, two observations may appear close in some dimensions but very different in others. This makes it difficult for k-NN to identify reliable nearest neighbors and for k-means to create meaningful clusters.

How would I address this problem?
1. Feature Selection: Remove irrelevant or redundant features to reduce the number of dimensions.
2. Dimensionality Reduction: Use PCA (Principal Component Analysis) to transform the data into fewer dimensions while preserving important information.
3. Feature Scaling: Standardize or normalize features so that variables with larger numerical ranges do not dominate distance calculations.
4. Feature Engineering: Create more meaningful features that better represent the relationships in the data.
Conclusion: I would start by removing unnecessary features, apply scaling, and then use PCA if needed. This can make distance calculations more meaningful, improve model performance, and reduce computational costs.

**Critique of the AI answer** 
