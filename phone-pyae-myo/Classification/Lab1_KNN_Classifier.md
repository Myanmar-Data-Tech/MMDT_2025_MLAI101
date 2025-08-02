#### a) What is fraud detection, and why is it important?

Fraud detection is the process of identifying and preventing fraudulent activities, particularly in financial transactions.

#### b) Analysis with 70% Training and 30% Testing Split

- When we changed how we divided our data from using 60% for training and 40% for testing to 70% for training and 30% for testing, we got some interesting results. By giving more examples to learn from (about 2,170 extra samples), we expected it to get better at spotting fraud.
- The results were mixed though: one measure of how well it can tell fraud from normal transactions (AUC) did get better, going from 0.92 to 0.93. However, other measures like how accurate and precise it was got slightly worse, but only by tiny amounts. The most important finding for catching fraud was that the model missed fewer bad transactions that it went from missing 28 fraudulent cases to only missing 22. This is really important because in fraud detection, it's usually worse to miss a fraud than to accidentally flag a normal transaction as suspicious. The smaller test group (6,508 samples instead of 8,678) might have affected some of these results since we had fewer examples to check our model against.
- Overall, the differences were pretty small, which shows our model works consistently. But the 70%/30% split seems slightly better for fraud detection because it catches more fraud cases and does a better job overall at separating good and bad transactions, even though we have less data to test it with.

#### c) Keeping the test size fixed at 40%, try changing the number of neighbors (in KNN). How does the model’s performance vary with different K values? Which value gives the best result, and how do you define what makes it the "best"?

I conducted a systematic evaluation of the K-Nearest Neighbors algorithm using different K values ranging from 1 to 20, while keeping the test size fixed at 40%. The testing revealed interesting patterns about how the choice of K affects model performance in fraud detection.

**Performance Variation with K Values:**
The results showed that model performance varies significantly with different K values. Lower K values (K=1-5) generally performed better than higher values. Specifically, K=3 emerged as the optimal choice, achieving the highest F1-score of 0.8755, along with strong accuracy (99.64%) and excellent precision (97.32%). In contrast, as K increased beyond 10, the overall performance gradually declined, with F1-scores dropping to around 0.84 for K values between 16-20.

**Best Performing Model:**
K=3 provides the best overall performance when considering all metrics together. This model successfully balances the trade-off between catching actual fraud cases (recall of 79.56%) and avoiding false alarms (precision of 97.32%). The F1-score of 0.8755 represents this optimal balance, making it well-suited for fraud detection where both missing real fraud and flagging legitimate transactions are costly mistakes.

**Defining "Best" Performance:**
For fraud detection, the "best" model is determined by the F1-score because it balances precision and recall. While K=1 had the highest recall (81.75%), it suffered from lower precision (83.58%), meaning it would flag too many legitimate transactions as fraud. Conversely, very high K values like K=20 achieved excellent precision (98.06%) but missed more actual fraud cases. K=3 strikes the right balance, making it the most practical choice for real-world fraud detection applications.

In conclusion, the analysis demonstrates that choosing the right K value is crucial for optimal KNN performance, and K=3 provides the best combination of fraud detection capability while maintaining acceptable false positive rates.
