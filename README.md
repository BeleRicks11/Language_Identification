# Language Identification Project 🇮🇹 🇧🇷󠁧󠁢󠁥󠁮󠁧󠁿 🇫🇷 

Text Mining project realized as a part of the Data Mining, Text Mining and Big Data Analytics exam of the Master's degree in Artificial Intelligence at the  University of Bologna.

The aim of this project is to compare different text representations and learning models in the context of a classification task. 

Given an unknown paragraph written in one dominant language, it has to be decided which language it is.

The dataset that we will use is the [WiLI-2018 - Wikipedia Language Identification Dataset](https://zenodo.org/record/841984)

## Overview

I tried three different text representations :

* CountVectorizer (BoW)
* TF-IDF
* Dense Word Embedding (FastText)

For each of them I compared three different algorithms for classification:

* Multinomial Naive Bayes
* Rocchio Algorithm (Nearest Centroids)
* k-Nearest Neighbors

Then I compared the results obtained with the previous techniques with a BERT Transformer model representing the state-of-the-art.
