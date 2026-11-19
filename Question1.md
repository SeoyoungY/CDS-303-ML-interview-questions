## Question 1
Your model shows 95% accuracy on a fraud-detection dataset where only 2% of transactions are fraudulent. 
Is this a good model? How would you evaluate and improve it?

### Answer
### Requirement 1

No, it is not a good model. The textbook gives this example: if 1% of transactions are fraud, "a model that predicts every transaction as legitimate has an accuracy of 99% even though it fails to detect any of the fraudulent activities."[1] Here, fraud is 2%. In 10,000 transactions, that is 200 fraud and 9,800 normal. It is right 9,800 times, so its accuracy is 9,800/10,000 = 98%, but it catches zero fraud. Our model's 95% is lower than this 98% model."Since the accuracy measure treats every class as equally important, it may not be suitable for analyzing imbalanced data sets."[2]

How to evaluate: 
- Use recall and precision. The textbook says, "Recall measures the fraction of positive examples correctly predicted by the classifier," and precision is "the fraction of records that actually turns out to be positive in the group the classifier has declared as a positive class."[3] For example, recall means "how much fraud did we catch?" and precision means "how many of our fraud alarms were real?" For Model A, recall = TP/(TP+FN) = 150/200 = 0.75, precision = TP/(TP+FP) = 150/600 = 0.25, and F1 = 2rp/(r+p) = 2(0.75)(0.25)/(0.75+0.25) = 0.375. For Model B, recall = 0/200 = 0, so it catches no fraud. 
- Use the ROC curve, which "plots TPR against FPR for possible thresholds."[4] Model A is at TPR = 0.75, FPR = 450/9,800 = 0.046, so it  is not random. Model B is at TPR = 0, FPR = 0.031, below it, so it is worse than random.
- Use cross validation. The "test set should be set aside for a truly final evaluation."[5] When we split data, "a class that is overrepresented in one subset will be underrepresented in the other."[6] 

How to improve:
- Lower the threshold from 0.5 to C(−,+)/(C(−,+) + C(+,−)) to obtain a cost-sensitive classifier. This catches more fraud but gives more false alarms.[7]
- Resample the training data "so that the rare class is well represented in the training set."[8] 
- Use boosting. "Records that are wrongly classified will have their weights increased in the next round."[9] But boosting can overfit, because it focus on training examples that are wrongly classified[10]



[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7, p. 295; CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slide 7 "Problem with Accuracy" (990/1000 = 99%).

[2]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7.1 "Alternative Metrics," p. 295.

[3]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7.1 "Alternative Metrics," p. 297 (Eqs. 5.74–5.76: precision, recall, F1); CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slide 9 "Alternative Measures."

[4]: CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slides 17–18.

[5]: CDS 303 Lecture, *Model Overfitting* (Week 3-1), slide 16.

[6]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 4 4.5.1 "Holdout Method," p. 187.

[7]: Tan et al., Ch. 5 5.7.3, p. 304 (Eq. 5.83).

[8]: Tan et al., Ch. 5 5.7.4, p. 305

[9]: CDS 303 Lecture, *Ensemble Methods* (Week 4-1), slide 34.

[10]: Tan et al., Ch. 5 5.6.5, p. 290.


### Requirement 2 

**AI-generated answer**

No, 95% accuracy does not necessarily mean the model is good. In this case, the dataset is highly imbalanced because only 2% of transactions are fraudulent.

1. Why is 95% accuracy misleading?
Since 98% of transactions are legitimate, a model that simply predicts every transaction as legitimate would achieve 98% accuracy without detecting a single fraudulent transaction. Therefore, a 95%-accurate model may actually perform worse than a model that makes no fraud predictions at all.

2. How would I evaluate the model?
Instead of relying only on accuracy, I would use the following evaluation metrics:
- Precision: Out of all transactions predicted as fraud, how many are actually fraudulent?
- Recall: Out of all actual fraudulent transactions, how many does the model correctly identify?
- F1-score: The harmonic mean of precision and recall, balancing both metrics.
- Confusion Matrix: Shows true positives, true negatives, false positives, and false negatives.
- PR-AUC (Precision-Recall AUC): Measures the trade-off between precision and recall and is particularly useful for imbalanced datasets.
For fraud detection, I would pay special attention to recall because missing fraudulent transactions (false negatives) can cause significant financial losses.

3. How would I improve the model?
I would consider the following approaches:
- Resampling: Use oversampling (such as SMOTE) to increase fraudulent samples or undersampling to reduce legitimate transactions.
-  Class weights: Give higher penalties to misclassifying fraudulent transactions so the model pays more attention to the minority class.
-  Threshold tuning: Adjust the classification threshold to improve fraud detection rather than automatically using 0.5.
-  Feature engineering: Create more informative features, such as transaction frequency, unusual spending patterns, and transaction amounts.
-  Model comparison: Test different algorithms, such as Random Forest, XGBoost, and Logistic Regression, to find the best-performing model.

**Critique of the AI answer** 

What it got right.

The AI answer explains the main problem well. It says that a model predicting "legitimate" for every transaction gets 98% accuracy, so 95% may be worse than doing nothing. Its definitions of precision and recall are correct. It also says that recall matters most because missed fraud is costly.

What is missing or vague.

Most of the answer is a list of terms. It names precision, recall, F1, and PR-AUC, but it never calculates any of them. We still do not know how much fraud this model catches. It also says to "adjust the classification threshold," but it does not say to what value or why. It never mentions the cost of mistakes, so it cannot show *how much worse* a missed fraud is than a false alarm.

What an interviewer would push back on.

- "Two models can both have 95% accuracy. How would you tell them apart?"
- "What threshold would you choose, and why that number?"
- "If you use SMOTE, do you apply it before or after the train/test split?"
- "Why would XGBoost or Random Forest help here?"

The AI answer cannot answer these questions.

Where my answer goes deeper.

I showed two models with the same 95% accuracy: one catches 150 frauds and the other catches none. I calculated recall (0.75), precision (0.25), and F1 (0.375). I compared costs (5,450 vs. 20,000) and placed both models on the ROC curve. I also computed the threshold from the cost matrix: 1/(1+100) ≈ 0.01.

What I should have covered.

The AI mentioned PR-AUC, class weights, and feature engineering. Class weights connect to cost-sensitive learning, and feature engineering could improve any model. My answer did not discuss these.

