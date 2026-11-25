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


[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.3 "Linear Algebra Techniques for Dimensionality Reduction," p. 52.

[2]: Alvarez-Garcia, Arenas-Parra & Ibar-Alonso (2024), "Uncovering student profiles. An explainable cluster analysis approach to PISA 2022," *Computers & Education* 223, 105166 (CDS 303 course reading), 4.1 "Derived student variables," p. 10.

[3]: Tan et al., Appendix B §B.1.1 "PCA – Mathematical Details," p. 687.

[4]: CDS 303 Lecture, *Dimensionality reduction* (Week 11-1),slide 28 "Standardize the features," and slide 39 "Pros and cons."

[5]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Appendix B §B.1.1 "PCA – Mathematical Details," p. 687.

[6]: CDS 303 Lecture, *Dimensionality reduction* (Week 11-1),slide24 “Principle component example”



### Requirement 2 

**AI-generated answer**

**Critique of the AI answer** 
