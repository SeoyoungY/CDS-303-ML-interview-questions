## Question 5
Walk me through using PCA before training a classifier: what preprocessing it needs, how you choose the number of components, and when it can hurt.

## Answer
### Requirement 1

- Use continuous attributes: PCA is "a linear algebra technique for continuous attributes."[1] For categorical variables, a course paper used a different method (MCA) instead of PCA.[2]
- Center the data. The textbook assumes the "data matrix D has been preprocessed so that the mean of each attribute (column) is 0."[3]

[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch.2.3.3 "Linear Algebra Techniques for Dimensionality Reduction," p. 52.

[2]: Alvarez-Garcia, Arenas-Parra & Ibar-Alonso (2024), "Uncovering student profiles. An explainable cluster analysis approach to PISA 2022," *Computers & Education* 223, 105166 (CDS 303 course reading), 4.1 "Derived student variables," p. 10.

[3]: Tan et al., Appendix B §B.1.1 "PCA – Mathematical Details," p. 687.


### Requirement 2 

**AI-generated answer**

**Critique of the AI answer** 
