---
layout: post
title: "Text Classification and Sentiment Analysis : Naive Bayes"
description: "Discussion of theory behind Naive Bayes Classifier in context of Seniment Analysis"
og_image: "post-images/nlp-word-cloud.jpg"
tags: [machine-learning, sentiment-analytics]
---

Naive Bayes classifiers are studying the classification task from a Statistical point of view. The starting point is that the probability of a class  **C** is given by the posterior probability **P(C&#124;D)** given a training document **D**. Here **D** refers to all of the text in the entire training set. It is given by **D = ( d<sub>1</sub>, d<sub>2</sub>, .., d<sub>n</sub> )**, where  **d<sub>i</sub>** is the **i<sup>th</sup>** attribute (word) of document **D**.

Using Bayes’ rule, this posterior probability can be rewritten as:


{% include image.html path="post-images/NLP-Naive-Bayes/1.svg" path-detail="post-images/NLP-Naive-Bayes/1.svg" alt="Equation" %}

Since the marginal probability **P(D)** is equal for all classes, it can be disregarded and the equation becomes:

{% include image.html path="post-images/NLP-Naive-Bayes/2.svg" path-detail="post-images/NLP-Naive-Bayes/2.svg" alt="Equation" %}

The document **D** belongs to the class **C** which maximizes this probability, so:

{% include image.html path="post-images/NLP-Naive-Bayes/3.svg" path-detail="post-images/NLP-Naive-Bayes/3.svg" alt="Equation" %}

{% include image.html path="post-images/NLP-Naive-Bayes/4.svg" path-detail="post-images/NLP-Naive-Bayes/4.svg" alt="Equation" %}

Assuming conditional independence of the words d<sub>i</sub>, this equation simplifies to:


{% include image.html path="post-images/NLP-Naive-Bayes/5.svg" path-detail="post-images/NLP-Naive-Bayes/5.svg" alt="Equation" %}

{% include image.html path="post-images/NLP-Naive-Bayes/6.svg" path-detail="post-images/NLP-Naive-Bayes/6.svg" alt="Equation" %}


Here **P(d<sub>i</sub>&#124;C)** is the conditional probability that word **i** belongs to class **C**. For the purpose of text classification, this probability can simply be calculated by calculating the frequency of word **i** in class **C** relative to the total number of words in class **C**.


{% include image.html path="post-images/NLP-Naive-Bayes/7.svg" path-detail="post-images/NLP-Naive-Bayes/7.svg" alt="Equation" %}

 

We have seen that we need to multiply the class probability with all of the prior-probabilities of the individual words belonging to that class. The question then is, how do we know what the prior-probabilities of the words are?  Here we need to remember that this is a supervised machine learning algorithm: we can estimate the prior-probabilities with a training set with documents that are already labeled with their classes. With this training set we can train the model and obtain values for the prior probabilities. This trained model can then be used for classifying unlabeled documents.

This is relatively easy to understand with an example. Lets say we have counted the number of words in a set of labeled training documents. In this set each text document has been labeled as either Positive, Neutral or as Negative. The result will then look like :


{% include image.html path="post-images/NLP-Naive-Bayes/8.png" path-detail="post-images/NLP-Naive-Bayes/8.png" alt="Result Table" %}

From this table we can already deduce each of the class probabilites:

***P(C<sub>pos</sub>) = 0.141,***

***P(C<sub>neu</sub>) = 0.723,***

***P(C<sub>neg</sub>) = 0.141.***
 

If we look at the sentence  “This blog-post is awesome.”, then the probabilities for this sentence belonging to a specific class are:

{% include image.html path="post-images/NLP-Naive-Bayes/9.svg" path-detail="post-images/NLP-Naive-Bayes/9.svg" alt="Equation" %}

{% include image.html path="post-images/NLP-Naive-Bayes/10.svg" path-detail="post-images/NLP-Naive-Bayes/10.svg" alt="Equation" %}

{% include image.html path="post-images/NLP-Naive-Bayes/11.svg" path-detail="post-images/NLP-Naive-Bayes/11.svg" alt="Equation" %}

This sentence can thus be classified in the positive category.