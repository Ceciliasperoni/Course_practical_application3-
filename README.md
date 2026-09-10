### Practical Application 3 - Comparing Classifiers
Comparing classifiers for predicting whether a client will subscribe to a bank long-term deposit
ML/AI  Professional Certificate Berkeley
**Cecilia Speroni**

#### Overview
According to Moro et. al 2014, the business goal is to improve the effectiveness of marketing campaigns for long-term deposit subscriptions by reducing the number of marketing contacts. 

To achieve this goal, this assigment compares the performance of several classifiers (K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) for predicting whether a client will subscribe to a term deposit, and recommends using the preferred model to rank clients by predicted probability and prioritize calls within the bank’s marketing outreach effort.

#### Objective 
The objective of this project is to improve the effectiveness of bank marketing efforts for term deposits by identifying clients who are more likely to subscribe and better targeting marketing efforts.

#### Dataset
The dataset was provided for the assignment. It comes from [the UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/222/bank+marketing), including records from a Portuguese banking institution with infromation on marketing campaigns efforts.

#### Methodology
I compare the performance of several classification models—Logistic Regression, K-Nearest Neighbors, Decision Trees, and Support Vector Machines—focusing primarily on recall.

Subscription to a bank term deposit as a result of a marketing effort has a relatively low conversion rate. In this setting, a model can achieve high accuracy simply by predicting that no one will subscribe, but such model would have little practical value because the goal is to identify clients who are likely to subscribe. Although I focus on recall, I also output and discuss additional measures such as accuracy, precision, and F1 score.

I train all models on the training data and assess performance on a held-out test sample. Because subscription rates are highly imbalanced, I stratify the train/test split on the outcome to maintain similar subscription rates in both samples. All models are evaluated on the same test data, except SVM, which uses a smaller random sample provided for the assignment to reduce computation time.

I use 5-fold cross-validation with grid search to select hyperparameters that maximize recall. I tune:

- Logistic Regression: C, which controls the strength of regularization.
- KNN: Number of neighbors.
- Decision Tree: Maximum tree depth and minimum leaf size.
- SVM: C and kernel type.

#### Results
- Overall, the tuned models have similar recall (18–19%), and all of them still identify fewer than one in five actual subscribers. Tuning the hyperparameters did not meaningfully improve the models’ ability to identify subscribers.
- The preferred model is a logit for this application. Although it did not have the highest recall, it is simpler and more interpretable than more computationally intensive approaches, while still achieving very similar predictive performance.

**Practical business recommendations:**

- Instead of using the model to just predicting whether someone would subscribe, I'd recommend that banks use it to prioritize scarce marketing effort. If you have a budget to make, say, 1000 calls, then rank clients by the predicted probability and contact the top 1000 prospects.
- Try different marketing strategies and compared subcriptions obtained per 1,000 contacts amidst marketing cost.

#### Next Steps 
In the annotated notebook, I elaborate on ideas for future modeling work. As an alternative to ranking clients by predicted probability to prioritize calls, one could explore different classification thresholds for Logistic Regression and assess the trade-offs between precision and recall when turning predicted probabilities into an operational targeting rule.

##### Contact and Further Information
https://www.linkedin.com/in/cecilia-speroni/
