# Fake-News-Detection

This project intends to utilize Natural Language Processing based ML to accurately predict the authenticity of the news articles. Additionally, an experiment was conducted to find the ideal algorithm across different skew (class sizes) ratios and text vectorization methods. I will describe the ETL pipelines for this NLP application.

**Data Life Cycle Steps**

**(A) Data Extraction**

- The dataset utilized for this experiement was Clement Bisaillon’s Kaggle news dataset. Here's a link: https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset
- Dataset consisted of two different sets of files each of which was made up of true and fake news articles with the following fields: News Title, News Content, Subject and Date
- Additionally, the distribution of fake versus real news across the ratios - 1:1, 1:4, 1:9, 1:99 - to test our model’s ability to overcome the data imbalance.

**(B) Data Pre-processing/Transformation**

Upon completion of the data extraction phase, I pre-processed the raw text data to transform it for the vectorization phase. 
This phase consisted of the following:
a. Search for null records
b. Replace all non-alphabetic characters (numbers, special characters, etc.) with a space
c. Convert all text to lowercase
d. Remove stopwords (“the”, “a”, “reuters” etc.) from the text 
e. Lemmatize the text


**(C) Data Loading**

Vector Conversion: Following preprocessing, I proceeded to vectorize our text on the basis of two methods - TFIDF and CountVectorizer. We chose to
showcase these methods in order to observe whether the choice of vectorization impacts performance.


**(D) Training Phase**

The input transformation phase resulted in the conversion of the entire article corpus to ML acceptable input as word vectors.

Each of these vectors was then used to perform a train test split with the test size being 35% of available samples. 
The scope of the experiment was limited to the these classifiers:

a. Random Forest

b. Passive Aggressive Classifier

c. Linear SVC

d. RBF SVC

e. Decision Tree

f. Multinomial Naive Bayes

g. Complement Naive Bayes

h. Neural Network (MLP)


**(E) Skew Size Variance**

Lastly, then the models were re-run and observed performance across different class sizes.


**EXPERIMENT CONCLUSIONS:**

The result analysis confirmed that classifiers like Decision Tree, Random Forest and Passive Aggressive tend to generally perform well at identifying minority classes despite skew of the dataset. However, the algorithms like the Naive Bayes and SVMs tend to suffer depending on the minority class distribution. Additionally, we
observed best performance when the split was 1:4 between fake versus real news.
