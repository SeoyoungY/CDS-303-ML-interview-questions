## Question 2
You need a model for loan-default prediction. Compare logistic regression, a decision tree, and a random forest — which would you choose and why?

## Answer
### Requirement 1
I choose a random forest.

Logistic regression: It uses f(x) = 1/(1 + e^−(b + w1X1 + … + wpXp)), the "Sigmoid function." The output is between 0 and 1[1]. For example, if b + w1X1 + … + wpXp = 2, then f(x) = 1/(1 + e^−2) = 0.88, an 88% chance of default. But this kind of model "Learns linear decision boundaries,"[2] so it "Cannot results in good prediction performance when the classification boundary or the input/output relationship is not linear."[3]

Decision tree: In the course uses loan data as its tree example: Home Owner, Marital Status, and Annual Income predict "Defaulted Borrower."[4] One rule from that tree is: not a home owner, single, and income > 80K → default = Yes. Trees are "Easy to interpret for small-sized trees."[5] But a full tree "tends to memorize the training dataset, rather than discovering significant patterns."[6]

Random forest: It builds many decision trees. Each tree is trained on a bootstrap sample, and "At every internal node of decision tree, randomly sample p attributes for selecting split criterion."Each tree grows "until all leaves are pure (unpruned tree)," and the final answer comes from a "Majority voting scheme."[7] With 1,000 loans, each tree sees about 1 − (1 − 1/1000)^1000 ≈ 63.2% of them. The other 36.8% (out-of-bag) can be used for validation.[8] Random forests "Solve overfitting issue of decision trees" and have "A lower variance than a single decision tree."[9]

The textbook compares these methods with ten-fold cross-validation.[10] On the "German" data set (1,000 records), accuracy was 70.90% for a decision tree and 74.5% for a random forest. That is 3.6 points, or about 36 more correct predictions out of 1,000. On the "Credit" data set (690 records), both got 85.8%, so a random forest does not always win.[10]

Why random forest:  It was more accurate on the German data, and it controls the overfitting of a single tree. Its weak point is that it is "Difficult to interpret" (a "Black box"), but "Importance scores complement the cons."[9] We can find which features matter by shuffling one feature and checking the OOB error: if it is "well used for split," then "pi > ei."[11] For example, if shuffling Annual Income raises the error from 0.20 to 0.30, income matters.

But Logistic regression can perform as a baseline. 
If the forest is not clearly better on the test set, I would use the simpler model: "Given two models with the same generalization errors, the simpler model is preferred over the more complex model."[12] On the Credit data, decision tree and random forest got 85.8%, so this rule would choose the simpler model. 

[1]: CDS 303 Lecture, *Artificial Neural Networks (1)* (Week 6-1), slide 3 "Logistic regression."

[2]: CDS 303 Lecture, *Artificial Neural Networks (1)* (Week 6-1), slide 10 (“Basic Architecture of Perceptron").

[3]: CDS 303 Lecture, *Artificial Neural Networks (1)* (Week 6-1), slides 25 "Nonlinearly Separable Data"

[4]: CDS 303 Lecture, *Basic Classification* (Week 2-2), slide 12 "Example of a Decision Tree."

[5]: CDS 303 Lecture, *Basic Classification* (Week 2-2), slide 65 "Pros and cons"

[6]: CDS 303 Lecture, *Model Overfitting* (Week 3-1), slide 26 "Model Selection for Decision Trees."

[7]: CDS 303 Lecture, *Ensemble Methods* (Week 4-1), slides 27–28 "Random Forest Algorithm."

[8]: CDS 303 Lecture, *Ensemble Methods* (Week 4-1), slide 16 "Bagging (Bootstrap AGGregatING)."

[9]: CDS 303 Lecture, *Ensemble Methods* (Week 4-1), slide 31 "Pros and cons – Bagging / RF."

[10]: Tan et al., Ch. 5 5.6.7, Table 5.5, p. 294.

[11]: CDS 303 Lecture, *Ensemble Methods* (Week 4-1), slide 30 "Variable importance"

[12]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 4 4.4, Definition 4.2, p. 181.


### Requirement 2 

**AI-generated answer**

1. Compare the Three Models

| Model | Advantages | Disadvantages |
|---|---|---|
| Logistic Regression | Easy to interpret, fast, and provides probability estimates. | May struggle with complex, nonlinear relationships. |
| Decision Tree | Easy to understand and visualize; captures nonlinear patterns. | Can overfit and be unstable. |
| Random Forest | Usually provides strong predictive performance, handles complex relationships, and reduces overfitting. | Less interpretable and requires more computational resources. |

2. Which Model Would I Choose?

I would choose **Random Forest** because loan-default prediction involves many factors, such as income, credit score, employment history, debt, and payment history.

Random Forest combines multiple decision trees to make predictions, which helps reduce overfitting and capture complex relationships between variables.

However, I would also use Logistic Regression as a baseline model because financial institutions need to understand why a borrower is classified as high-risk.

3. How Would I Evaluate the Models?

I would compare the three models using the following metrics:

- Precision: Measures how many borrowers predicted to default actually default.
- Recall: Measures how many actual defaulters the model correctly identifies.
- F1-score: Balances precision and recall.
- ROC-AUC: Measures how well the model distinguishes between borrowers who default and those who do not.

I would also consider the financial costs of false positives and false negatives when evaluating the models.

4. Conclusion

I would choose Random Forest if it demonstrates better performance on unseen data. However, I would not rely on accuracy alone. Since loan decisions involve financial risks, I would also consider interpretability, fairness, and regulatory requirements.

Overall, Random Forest is a strong choice for predictive performance, while Logistic Regression is a good choice when transparency and interpretability are the highest priorities.

**Critique of the AI answer** 
