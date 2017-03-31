---
layout: post
title: "Text Classification and Sentiment Analysis : Support Vector Machines"
description: "Discussion of SVM Classifier in context of Natural Language Processing and Sentiment Analysis"
og_image: "post-images/nlp-word-cloud.jpg"
tags: [machine-learning, sentiment-analytics]
---

Although it is not immediatly obvious from the name, the SVM algorithm is a ‘simple’ linear classification/regression algorithm. It tries to find a hyperplane which seperates the data in two classes as optimally as possible.

Here as optimally as possible means that as much points as possible of label A should be seperated to one side of the hyperplane and as points of label B to the other side, while maximizing the distance of each point to this hyperplane.

{% include image.html path="post-images/NLP-SVM/svm-max-sep-hyperplane-with-margin.jpg" path-detail="post-images/NLP-SVM/svm-max-sep-hyperplane-with-margin.jpg" alt="SVM Hyperplane" %}

In the image above we can see this illustrated for the example of points plotted in 2D-space. The set of points are labeled  with two categories (illustrated here with black and white points) and SVM chooses the hypeplane that maximizes the margin between the two classes. This hyperplane is given by

{% include image.html path="post-images/NLP-SVM/1.svg" path-detail="post-images/NLP-SVM/1.svg" alt="Equation" %}

where **x<sub>i</sub>** = **(x<sub>i1</sub>, x<sub>i2</sub>, .. , x<sub>in</sub> )** is a n-dimensional input vector, y<sub>i</sub> is its output value, **w** = **(w<sub>1</sub>, w<sub>2</sub>, .. , w<sub>n</sub> )** is the weight vector (the normal vector) defining the hyperplane and the ***alpha<sub>i</sub>*** terms are the Lagrangian multipliers.

Once the hyperplane is constructed (the vector ***w*** is defined) with a training set, the class of any other input vector ***x<sub>i</sub>*** can be determined:
if ***w.x<sub>i</sub> + b >= 0*** then it belongs to the positive class (the class we are interested in), otherwise it belongs to the negative class (all of the other classes).

We can already see this leads to two interesting questions:

1. SVM only seems to work when the two classes are linearly separable. How can we deal with non-linear datasets? Here I feel the urge to point out that the Naive Bayes and Maximum Entropy are linear classifiers as well and most text documents will be linear. Our training example of Amazon book reviews will be linear as well. But an explanation of the SVM system will not be complete without an explanation of Kernel functions.

2. SVM only seems to be able to separate the dataset into two classes? How can we deal with datasets with more than two classes. For Sentiment Classification we have for example three classes (positive, neutral, negative) and for Topic Classification we can have even more than that.

### Kernel Functions:
The classical SVM system requires that the dataset is linearly separable, i.e. there is a single hyperplane which can separate the two classes. For non-linear datasets a Kernel function is used to map the data to a higher dimensional space in which it is linearly separable. This video gives a good illustation of such a mapping. In this higher dimensional feature space, the classical SVM system can then be used to construct a hyperplane.

### Multiclass classification:
The classical SVM system is a binary classifier, meaning that it can only separate the dataset into  two classes. To deal with datasets with more than two classes usually the dataset is reduced to a binary class dataset with which the SVM can work. There are two approaches for decomposing a multiclass classification problem to a binary classification problem: the one-vs-all and one-vs-one approach.
In the one-vs-all approach one SVM Classifier is build per class. This Classifier takes that one class as the positive class and the rest of the classes as the negative class. A datapoint is then only classified within a specific class if it is accepted by that Class’ Classifier and rejected by all other classifiers. Although this can lead to accurate results (if the dataset is clustered), a lot of datapoints can also be left unclassified (if the dataset is not clustered).
In the one-vs-one approach, you build one SVM Classifier per chosen pair of classes. Since there are **0.5N(N-1)** possible pair combinations for a set of N classes, this means you have to construct more Classifiers. Datapoints are then categorized in the class for which they have received the most points.

In our example, there are only three classes (positive, neutral, negative) so there is no real difference between these two approaches. In both approaches we have to construct two hyperplanes; positive vs the rest and negative vs the rest.