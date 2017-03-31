---
layout: post
title: "Text Classification and Sentiment Analysis : Introduction"
description: "Natural Language Processing (NLP) is a vast area of Computer Science that is concerned with the interaction between Computers and Human Language..."
og_image: "post-images/nlp-word-cloud.jpg"
tags: [machine-learning, sentiment-analytics]
---

Within NLP many tasks are – or can be reformulated as – classification tasks. In classification tasks we are trying to produce a classification function which can give the correlation between a certain ‘feature’ **D** and a class **C**. This Classifier first has to be trained with a training dataset, and then it can be used to actually classify documents. Training means that we have to determine  its model parameters. If the set of training examples is chosen correctly, the Classifier should predict the class probabilities of the actual documents with a similar accuracy (as the training examples).

After construction, such a Classifier could for example tell us that document containing the words “Bose-Einstein condensate” should be categorized as a Physics article, while documents containing the words “Arbitrage” and “Hedging” should be categorized as a Finance article.
Another Classifier could tell us that mails starting with “Dear Customer/Guest/Sir” (instead of your name) and containing words like “Great opportunity” or “one-time offer” can be classified as spam.
Here we can already see two uses of classification models: topic classification and spam filtering. For these purposes a Classifiers work quiet well and perform better than most trained professionals.

A third usage of Classifiers is Sentiment Analysis. Here the purpose is to determine the subjective value of a text-document, i.e. how positive or negative is the content of a text document. Unfortunately, for this purpose these Classifiers fail to achieve the same accuracy. This is due to the subtleties of human language; sarcasm, irony, context interpretation, use of slang, cultural differences and the different ways in which opinion can be expressed (subjective vs comparative, explicit vs implicit).

In this blog series I will discuss the theory behind three popular Classifiers (Naive Bayes, Maximum Entropy and Support Vector Machines) in the context of Sentiment Analysis.

The contents of this blog series is as follows:

1. Basic concepts of text classification:
- Tokenization
- Word normalization
- bag-of-words model
- Classifier evaluation
2. Naieve Bayesian Classifier
3. Maximum Entropy Classifier
4. Support Vector Machines