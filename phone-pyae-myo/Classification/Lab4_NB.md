## 1. Differences Between NB Classifiers

The three Naive Bayes classifiers differ fundamentally in their underlying assumptions about how data is distributed, making each suitable for different types of features.
### GaussianNB
This classifier assumes that continuous features follow a Gaussian (normal) distribution, estimating the mean and variance for each feature within each class. This makes it particularly well-suited for continuous numerical data like financial transaction amounts, account balances, and other quantitative features commonly found in fraud detection datasets.

### BernoulliNB
On the other hand, BernoulliNB is designed for binary or boolean features, assuming that each feature follows a Bernoulli distribution (essentially a coin flip). It estimates the probability of each feature being "present" (1) or "absent" (0) for each class. This classifier is traditionally used in text classification where features represent the presence or absence of specific words in documents.

### MultinomialNB
This method assumes features follow a multinomial distribution and is specifically designed for discrete count data, such as word frequencies in text documents. It requires non-negative integer features and is commonly used in natural language processing tasks where features represent how many times specific words appear in a document. The fundamental issue we observed with MultinomialNB in our fraud detection task is that financial transaction data contains negative values and continuous features, which violate the classifier's core assumptions.

## 2. Find and compare the precision and recall for all three NB classifiers

The precision and recall results reveal significant differences in how each model handles fraud detection.
### GaussianNB
Using this method achieved a precision of 38.06% and a recall of 86.13%. This means that while only about 38% of its fraud predictions were actually fraudulent transactions, it successfully identified 86% of all actual fraud cases in the dataset. This represents a high-recall, lower-precision approach that tends to cast a wider net but with more false alarms.

### BernoulliNB
BernoulliNB demonstrated the opposite pattern with a precision of 92.86% and a recall of 75.91%. This indicates that when BernoulliNB predicts a transaction is fraudulent, it's correct about 93% of the time, making it very reliable in its fraud predictions. However, it only catches about 76% of actual fraud cases, meaning it misses more genuine fraud instances compared to GaussianNB.

### MultinomialNB
This classifier completely failed in this fraud detection task, achieving 0% for both precision and recall. The confusion matrix reveals that MultinomialNB predicted zero fraud cases across the entire test set, classifying every single transaction as legitimate. This total failure stems from the fundamental mismatch between the algorithm's assumptions (discrete count data) and the nature of financial transaction data (continuous features with negative values). Even after applying MinMax scaling to make the features non-negative, the underlying continuous distribution of the data remained incompatible with MultinomialNB's multinomial assumptions.

## 3. Which model would you choose for fraud detection? Why?

While BernoulliNB achieved impressive precision, its approach of treating continuous financial features as binary variables results in significant information loss. The high precision comes at the cost of missing genuine fraud cases, which is particularly problematic in fraud detection where the consequences of false negatives (missed fraud) are typically much more severe than false positives (unnecessary investigations).

In conclusion, GaussianNB strikes the optimal balance between mathematical appropriateness for the data type, business cost considerations, and fraud detection effectiveness, making it the clear choice for this application.