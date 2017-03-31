---
layout: post
title: "Text Classification and Sentiment Analysis : Basic Concepts"
description: "Some basic concepts in NLP include Tokenization, Word Normalization, Bag of Words Model, Classifier Evaluation..."
og_image: "post-images/nlp-word-cloud.jpg"
tags: [machine-learning, sentiment-analytics]
---

## Tokenization

Tokenization is the name given to the process of chopping up sentences into smaller pieces (words or tokens). The segmentation into tokens can be done with decision trees, which contains information to correctly solve the issues you might encounter. Some of these issues you would have to consider are:

1. The choice for the delimiter will for most cases be a whitespace (“We’re going to Barcelona” -> [“We’re”, “going”, “to”, “Barcelona.”]), but what should you do when you come across words with a white space in them (“We’re going to The Hague.”->[“We’re”, “going”,”to”,”The”, “Hague”]).

2. What should you do with punctuation marks? Although many tokenizers are geared towards throwing punctuation away, for Sentiment analysis a lot of valuable information could be deduced from them. ! puts extra emphasis on the negative/positive sentiment of the sentence, while **?** can mean uncertainty (no sentiment).

3. “, ‘ , [], () can mean that the words belong together and should be treated as a separate sentence. Same goes for words which are **bold**, *italic*, __underlined__, or inside a link. If you also want to take these last elements into considerating, you should scrape the html code and not just the text.

## Word Normalization:

Word Normalization is the reduction of each word to its base/stem form (by chopping of the affixes). While doing this, we should consider the following issues:

1. Capital letters should be normalized to lowercase, unless it occurs in the middle of a sentence; this could indicate the name of a writer, place, brand etc.

2. What should be done with the apostrophe (‘); “George’s phone” should obviously be tokenized as “George” and “phone”, but I’m, we’re, they’re should be translated as I am, we are and they are. To make it even more difficult; it can also be used as a quotation mark.

3. Ambigious words like High-tech, The Hague, P.h.D., USA, U.S.A., US and us.

## Bag-of-words:

After the text has been segmented into sentences, each sentence has been segmented into words, the words have been tokenized and normalized, we can make a simple bag-of-words model of the text. In this bag-of-words representation you only take individual words into account and give each word a specific subjectivity score. This subjectivity score can be looked up in a sentiment lexicon. If the total score is negative the text will be classified as negative and if its positive the text will be classified as positive.

## Classifier Evaluation:

For determining the accuracy of a single Classifier, or comparing the results of different Classifier, the F-score is usually used. This F-score is given by

{% include image.html path="post-images/NLP-Basic-Concepts/classifier-evaluation.svg" path-detail="post-images/NLP-Basic-Concepts/classifier-evaluation.svg" alt="Classifier Evaluation" %}

where **p** is the precision and r is the recall. The precision is the number of correctly classified examples divided by the total number of classified examples. The recall is the number of correctly classified examples divided by the actual number of examples in the training set.


 



