## Question 5
Walk me through using PCA before training a classifier: what preprocessing it needs, how you choose the number of components, and when it can hurt.

## Answer
### Requirement 1

1. Preprocessing PCA needs
- Use continuous attributes: PCA is "a linear algebra technique for continuous attributes."[1] For categorical variables, a course paper used a different method (MCA) instead of PCA.[2]
- Center the data. The textbook assumes the "data matrix D has been preprocessed so that the mean of each attribute (column) is 0."[3]
- Standardize the features. The lecture's first step is "Standardize the features," and it notes that this step "affects the result," because "PCA is not scale invariant."[4] Without it, a feature with large values would have a large variance and take over the first component.

2. Choosing the number of components

Each component's eigenvalue is its variance, and the textbook says, "The variance of the ith new attribute is λi," and "The sum of the variance of the original attributes is equal to the sum of the variance of the new attributes."[5] So the share of variance for each component is its eigenvalue divided by the sum of all eigenvalues.

- Lecture example: the eigenvalues are 3 and 1, so PC1 explains 3/(3 + 1) = 75%.[6]
- Iris data: PC1 explains 92.5% and PC2 explains 5.3%, so two components keep 97.8%.[7]

The lecture gives three rules: "Cumulative proportion of explained variance should be at least 0.8," "Keep only PCs with above-average variance," and "Look at the scree plot of eigenvalue."[8]


3. When PCA can hurt

- PCA ignores the class labels. It is built only from the covariance matrix of the attributes.[9] So the direction with the most variance may not be the direction that separates the classes. In the Iris example, Setosa is well separated, but Versicolour and Virginica are "much closer to each other."[7]
- Non-linear patterns. "PCA only considers linear combinations of the original variables."[4] The textbook says PCA is "not good at dimensionality reduction when the points have a complicated, non-linear relationship."[10]
- Uncorrelated features. "Dimension reduction can only be achieved if the original variables are correlated. Otherwise, PCA does nothing."[4]



[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.3 "Linear Algebra Techniques for Dimensionality Reduction," p. 52.

[2]: Alvarez-Garcia, Arenas-Parra & Ibar-Alonso (2024), "Uncovering student profiles. An explainable cluster analysis approach to PISA 2022," *Computers & Education* 223, 105166 (CDS 303 course reading), 4.1 "Derived student variables," p. 10.

[3]: Tan et al., Appendix B §B.1.1 "PCA – Mathematical Details," p. 687.

[4]: CDS 303 Lecture, *Dimensionality reduction* (Week 11-1),slide 28 "Standardize the features," and slide 39 "Pros and cons."

[5]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Appendix B §B.1.1 "PCA – Mathematical Details," p. 687.

[6]: CDS 303 Lecture, *Dimensionality reduction* (Week 11-1),slide24 “Principle component example”

[7]: Tan et al., Appendix B, Example B.2 "Iris Data," p. 688.

[8]CDS 303 Lecture, *Dimensionality reduction* (Week 11-1),slide 33 “# of principal components”

[9]: Tan et al., Appendix B §B.1.1, Definition B.1, p. 686.

[10]: Tan et al., Appendix B §B.2.3 "ISOMAP," p. 698.



### Requirement 2 

**AI-generated answer**

**Critique of the AI answer** 
