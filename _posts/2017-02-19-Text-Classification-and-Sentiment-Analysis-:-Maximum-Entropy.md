---
layout: post
title: "Text Classification and Sentiment Analysis : Maximum Entropy"
description: "Discussion of theory behind popular Maximum Entropy Classifier in context of Natural Language Processing"
og_image: "post-images/nlp-word-cloud.jpg"
tags: [machine-learning, sentiment-analytics]
---

The principle behind Maximum Entropy is that the correct distribution is the one that maximizes the Entropy / uncertainty and still meets the constraints which are set by the ‘evidence’.

Let me explain this a bit more. In Information Theory, the word Entropy is used as a unit of measure for the unpredictability of the content of information. If you would throw a fair dice, each of the six outcomes have the same probability of occuring (1/6). Therefore you have maximum uncertainty; an entropy of 1. If the dice is weighted you already know one of the six outcomes has a higher probability of occuring and the uncertainty becomes less. If the dice is weighted so much that the outcome is always six, there is zero uncertainty in the outcome and hence the information entropy is also zero.
The same applies to letters in a word (or words in a sentence): if you assume that every letter has the same probability of occuring you have maximum uncertainty in predicting the next letter. But if you know that letters like E, A, O or I have a higher probability of occuring you have less uncertainty.

Knowing this, we can say that complex data has a high entropy, patterns and trends have lower entropy, information you know for a fact to be true has zero entropy (and therefore can be excluded).
The idea behind Maximum Entropy is that you want a model which is as unbiased as possible; events which are not excluded by known constraints should be assigned as much uncertainty as possible, meaning the probability distribution should be as uniform as possible. You are looking for the maximum value of the Entropy. If this is not entirely clear, I recommend you to read through this example.

The mathematical formula for Entropy is given by 

{% include image.html path="post-images/NLP-Max-Entropy/1.svg" path-detail="post-images/NLP-Max-Entropy/1.svg" alt="Equation" %}
so the most likely probability distribution p is the one that maximizes this entropy:

{% include image.html path="post-images/NLP-Max-Entropy/2.svg" path-detail="post-images/NLP-Max-Entropy/2.svg" alt="Equation" %}
It can be shown that the probability distribution has an exponential form and hence is given by:

{% include image.html path="post-images/NLP-Max-Entropy/3.svg" path-detail="post-images/NLP-Max-Entropy/3.svg" alt="Equation" %}

where ***f<sub>i</sub> (d,c)*** is a feature function, ***lambda<sub>i</sub>*** &nbsp; is the weight parameter of the feature function and ***Z(d)*** is a normalization factor given by

{% include image.html path="post-images/NLP-Max-Entropy/4.svg" path-detail="post-images/NLP-Max-Entropy/4.svg" alt="Equation" %}

This feature function is an indicator function, which is expresses the expected value of the chosen statistics (words) in the training set. These feature functions can then be taken as constraints for the classification of the actual dataset (by eliminating the probability distributions ***P(c&#124;d)*** which do not fit with these constraints).

Usually, the weight parameters are automatically determined by the Improved Iterative Scaling algorithm. This is simply a gradient descent function which can be iterated over until it converges to the global maximum. The pseudocode for the this algorithm is as follows:

1. Initialize all weight parameters lambda<sub>i</sub> &nbsp; to zero.
2. Repeat until convergence:
- calculate the probability distribution ***P<sub>lambda</sub>(c&#124;d)***  with the weight parameters filled in.
- for each parameter lambda<sub>i</sub> &nbsp; calculate change in lambda<sub>i</sub>. This is the solution to:
{% include image.html path="post-images/NLP-Max-Entropy/5.svg" path-detail="post-images/NLP-Max-Entropy/5.svg" alt="Equation" %}

- update the value for the weight parameter:
{% include image.html path="post-images/NLP-Max-Entropy/6.svg" path-detail="post-images/NLP-Max-Entropy/6.svg" alt="Equation" %}

In step 2b ***f(d,c)*** is given by the sum of all features in the training dataset ***d***:

{% include image.html path="post-images/NLP-Max-Entropy/7.svg" path-detail="post-images/NLP-Max-Entropy/7.svg" alt="Equation" %}
Maximum Entropy is a general statistical classification algorithm and can be used to estimate any probability distribution. For the specific case of text classification, we can limit its form a bit more by using word counts as features:

{% include image.html path="post-images/NLP-Max-Entropy/8.svg" path-detail="post-images/NLP-Max-Entropy/8.svg" alt="Equation" %}
