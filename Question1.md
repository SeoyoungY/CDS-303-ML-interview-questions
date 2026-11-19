## Question 1
Your model shows 95% accuracy on a fraud-detection dataset where only 2% of transactions are fraudulent. 
Is this a good model? How would you evaluate and improve it?

### Answer
**Requirement 1**
No, it is not a good model. The textbook gives this example: if 1% of transactions are fraud, "a model that predicts every transaction as legitimate has an accuracy of 99% even though it fails to detect any of the fraudulent activities."[1] Here the fraud is 2%, so the same "all normal" model gets 9,800/10,000 = 98% accuracy. Our 95% is worse than doing nothing. "Since the accuracy measure treats every class as equally important, it may not be suitable for analyzing imbalanced data sets."[2]


[1]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7, p. 295; CDS 303 Lecture, *Imbalanced Class Problem* (Week 3), slide 7 "Problem with Accuracy" (990/1000 = 99%).
[2]: Tan, Steinbach & Kumar, *Introduction to Data Mining*, Ch. 5 5.7.1 "Alternative Metrics," p. 295.
