# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Project 3: Using Natural Language Processing (NLP) Modelling to Predict Desktop CPU Brand Popularity


## Introduction

**Problem Statement:** <br> 
As an aspiring entrepreneur embarking on a new custom Gaming/Enthusiast Desktop PC building startup, which desktop computer processing unit (CPU) brand should I carry to minimize dead stock/slow moving inventory?

**Natural Language Processing (NLP)**<br>
Natural language processing (NLP) is a branch of artificial intelligence (AI) that concerns with making computers understand and process human natural languages. This field of data science strives to build machines that understand and respond with text or speech of their own—in much the same way humans do. NLP combines computational linguistics—rule-based modeling of human language—with statistical, machine learning, and deep learning models. 

(Adapted from: https://www.ibm.com/cloud/learn/natural-language-processing#:~:text=Natural%20language%20processing%20(NLP)%20refers,same%20way%20human%20beings%20can.)

Structuting and processing human communication is the core of NLP. In this project, we are taking from a source of unstructured human communication in the form of Reddit posts within certain topic of interests (clustered into individual subreddits). The aim is to create an NLP model that is able to accurately classify a wall of text into one of two classes. 

As per the Problem Statement above, the two topics of choice are the two Consumer CPU giants, AMD and Intel.

<ins>Key Considerations</ins><br>
<br>
**Low Initial Capital**<br>
As a startup, capital is low and parts brought in need to be quickly sold off to obtain more funds to grow the business. Stock procured must be in-demand for the short term.

**AMD vs. Intel in the PC Hardware Ecosystem**<br>
The reason behind the requirement to choose a CPU brand is because the CPU brand will dictate other parts like motherboard, DRAM etc. and parts are not interchangeable.

**Target Market**<br>
Knowing what the target market wants is Business 101 and the target demographic for the Custom PC building startup are PC Gamers and Enthusiasts (aka followers of the PC Master Race https://pcmasterrace.org/guide)

## Executive Summary

In this project, 20,000 total posts from both ```r/AMD``` and ```r/Intel``` was scrapped and used to train an NLP model to accurately classify posts from subreddit ```r/BuildaPC```. This is to quantify the number of posts for AMD vs. Intel  in the subreddit to quantify the more popular CPU brand for Desktop PC builders/enthusiasts.

A pipeline was formed to test various models' performance in conjunction with different vectorizers. 2 different vectorizers (CountVectorizer, TfidfVectorizer) were used together with 3 different classifiers (LogisticRegression, MultinomialNB, RandomForestClassifier). Models were benchmarked and evaluated based on their Test (i.e. Holdout) accuracy score. 

After feature engineering and hyperparameter tuning was done, the final model that was chosen to be deployed to production were as follows:

|Vectorizer|Classifier|Test Accuracy Score|Hyperparameters| 
|---|---|---|---|
|TfidfVectorizer()|LogisticRegression()|93.71%|'tvec__max_features’ = 30_000<br>'tvec__n_gram_range' = (1,1)<br>'lr__C': 1.0|

Upon deployment and using the model on ```r/BuildaPC```, AMD was chosen to be the the CPU brand to carry for the custom PC builing startup.
