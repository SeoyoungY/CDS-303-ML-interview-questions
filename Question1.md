## Question 1
Your model shows 95% accuracy on a fraud-detection dataset where only 2% of transactions are fraudulent. 
Is this a good model? How would you evaluate and improve it?

### Answer
**Requirement 1**

No, it is not a good model. The textbook gives this example: if 1% of transactions are fraud, "a model that predicts every transaction as legitimate has an accuracy of 99% even though it fails to detect any of the fraudulent activities."[1] Here, fraud is 2%. In 10,000 transactions, that is 200 fraud and 9,800 normal. It is right 9,800 times, so its accuracy is 9,800/10,000 = 98%, but it catches zero fraud. Our model's 95% is lower than this 98% model."Since the accuracy measure treats every class as equally important, it may not be suitable for analyzing imbalanced data sets."[2]

How to evaluate: 
Use recall and precision. The textbook says, "Recall measures the fraction of positive examples correctly predicted by the classifier," and precision is "the fraction of records that actually turns out to be positive in the group the classifier has declared as a positive class."[3] For example, recall means "how much fraud did we catch?" and precision means "how many of our fraud alarms were real?" For Model A, recall = TP/(TP+FN) = 150/200 = 0.75, precision = TP/(TP+FP) = 150/600 = 0.25, and F1 = 2rp/(r+p) = 2(0.75)(0.25)/(0.75+0.25) = 0.375. For Model B, recall = 0/200 = 0, so it catches no fraud. 
Use the ROC curve, which "plots TPR against FPR for possible thresholds."[4] Model A is at TPR = 0.75, FPR = 450/9,800 = 0.046, so it  is not random. Model B is at TPR = 0, FPR = 0.031, below it, so it is worse than random.
Use cross validation. The "test set should be set aside for a truly final evaluation."[5] When we split data, "a class that is overrepresented in one subset will be underrepresented in the other."[6] 


[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7, p. 295; CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slide 7 "Problem with Accuracy" (990/1000 = 99%).

[2]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7.1 "Alternative Metrics," p. 295.

[3]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7.1 "Alternative Metrics," p. 297 (Eqs. 5.74–5.76: precision, recall, F1); CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slide 9 "Alternative Measures."

[4]: CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slides 17–18.

[5]: CDS 303 Lecture, *Model Overfitting* (Week 3-1), slide 16.

[6]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 4 4.5.1 "Holdout Method," p. 187.

