# Language Identification Project 🇮🇹 🇩🇪󠁧󠁢󠁥󠁮󠁧󠁿 🇫🇷 

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

## Results
* **MultinomialNB** + **HashingVectorizer**: 
  * Accuracy = 0.9283 ± 0.0023
* **Rocchio Algorithm** + **HashingVectorizer**: 
  * Accuracy = 0.8496 ± 0.0026
* **k-Nearest Neighbors** + **HashingVectorizer**: 
  * Accuracy = 0.8922 ± 0.0022

---

* **MultinomialNB** + **TF-IDF Vectorizer**: 
  * Accuracy = 0.9347 ± 0.0017
* **Rocchio Algorithm** + **TF-IDF Vectorizer**: 
  * Accuracy = 0.8866 ± 0.0026
* **k-Nearest Neighbors** ± **TF-IDF Vectorizer**: 
  * Accuracy = 0.9137 ± 0.0036

---

* **Rocchio Algorithm** + **Dense Word Embeddings**: 
  * Accuracy = 0.7899 ± 0.003
* **k-Nearest Neighbors** + **Dense Word Embeddings**: 
  * Accuracy = 0.8899 ± 0.003

---

* **BERT Transformer model**:
  * Accuracy: 0.9428 ± 0.0018

## Final considerations

* Obviously the best model in terms of accuracy is the **BERT Transformer model**, but also the **MultinomialNB + TF-IDF Vectorizer** turned out to be very performing in this task, obtaining very good performances even if it is a simpler model. 

* In general for what concerns the text representation methods, we can say that using the **TF-IDF Vectorizer** results to be the best approach; in fact if we make a comparison with the **Hashing Vectorizer** we archived better performances for all the classifiers. Instead with the use of a **Dense word embedding** model we obtained comparable results with the other text representations for what concerns the **k-Nearest Neighbors**, and worse results using the the **Rocchio algorithm**. This can be due to the simple approach adopted when creating the sentence embeddings or maybe to the fact that we trained the embedding model only on the training corpus.

* Instead with regards to the classification methods tried, we can say that the most effective classifier turned out to be the **MultinomialNB**, followed by the **k-Nearest Neighbors** and lastly by the **Rocchio Algorithm**. We can notice that there is not so much difference between the performances obtained by the **BERT Transformer** model and the **MultinomialNB**; this is probably due to a not so thorough fine-tuning of the parameters of the SOTA model.

### Future works

* The exploration of hyperparameters could be much more extensive, but it was necessary to find a tradeoff between the time needed to search for them and the time available for experimentation.

* For what concerns the BERT Transformer model we can try using the **BERT base multilingual** model, that despite being a heavier model and having longer training times, it can provide better performance

* Implementing a better preprocessing of the different sentences

* Training the dense embedding model on the whole corpus (train + test)

* Trying other simple classifiers or neural networks

* Experiments with sentences, containing 2 languages showed very bad ability of such models to predict both labels, but it was expected behavior. Training dataset contains only single-language samples and models were trained to predict only one label well. So, models are quite confused when they get something different. We can overcome these issues by changing model architectures and logic, changing dataset to have multilanguage samples.

