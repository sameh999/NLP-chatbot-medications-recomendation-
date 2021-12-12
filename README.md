# Contents
### Problem Formulation:	2
### Goal	2
### Project Pipeline	3
### Data Collection	4
### Dataset Features	5
### Exploratory Data analysis	6
### Text Transformation and Feature Engineering	7
### Classification Algorithms:	7
### Clustering Algorithms	9
### Evaluation	11
### Classification Evaluation	11
### Clustering Evaluation	11
### Error Analysis	11
### Deployment	12
### References	12


## Problem Formulation:
There is a need for a chatbot app for smartphones that allows users to have online conversations. Based on the information provided by the user, the chatbot can recommend which medications to take. The development of the application has the potential to improve consumer-pharmacy communication while also assisting the pharmacy in developing a better customer management system.
## Goal :
A chatbot system that not only can understand and analyze the clients’ symptoms but also diagnose the disease as well as recommend the suitable drugs based on machine learning algorithms and Natural Language Processing techniques. 
## Project Pipeline:

- Data collection

- >  Data Preparation  
`Remove
	Stop Words
	Punctuation
`

- > Feature Engineering
`TF-IDF 
 &LDA`
- > ML Modeling
`Classification
	(SVM, KNN, DT) &Clustering
	K-Means
`
- > Evaluation
  `Confusion Matrix
	Accuracy
	F1-Score &Silhouette Score `

- 

- > Integration & Deployment
 `Flask/NGROK`
 `DialogFlow `
 `Front-end and Telegram s`
![pipeline ](https://i.ibb.co/wRncZp8/2021-12-12-113804.png)
# Data Collection
We use EPAR for medicines' open-source dataset and (EPAR) European public assessment medical reports from European Medicines Agency (EMA) to build our system. 
### Sample of the dataset 
![](https://i.ibb.co/hgw3HfD/1.png)
### Sample of the description or indication 
![](https://i.ibb.co/5cNPxJX/2.png)
The “Condition/indication” feature will be used in NLP steps.
# Dataset Features

## Description of Some features: 
     - Category: Human or Veterinary
     - Medicine name: about 600 unique drugs	
     - Therapeutic area: diseases like Anemia, Diabetes, Bacterial Infections, and more
     - International non-proprietary name (INN) / common name
     - Patient safety: a binary feature with yes or no
     - Orphan medicine: a binary feature with yes or no
     - Condition/indication: text descriptions of drugs and diseases 
     - URL: for each drug
We will use the “Condition/indication” feature for NLP stages and “Medicine name”, “Therapeutic area” and other features for fulfillment
## Exploratory Data analysis
![Data analysis](https://i.ibb.co/4T41ZKd/1.png)

- We apply a word cloud EDA on the “Condition / indication” feature and we got most frequent words as shown in the figure.

![](https://i.ibb.co/VmM4F21/download.png)

- This bar chart shows the frequencies of each disease with respect to the number of drugs. We will use the most 20 diseases and their drugs in future steps.

- After applying some filters and exploring most features manually, we found that this data set has many blank or missing values and some inconsistent values. We will deal with these issues in the data preparation step.

### Text Transformation and Feature Engineering

-  We implement 2 approaches of text transformation:

**1. TF-IDF:** 
      The bag of the word doesn't capture the importance of the word it gives you the frequency of the word. TF-IDF resolves this matter through the computation of two values. TF is the count of occurrences of the word in a document. IDF of the word across a set of documents. It tells us how common or rare a word is in the entire document set. The closer it is to 0, the more common is the word. This metric can be calculated by taking the total number of documents, dividing it by the number of documents that contain a word, and calculating the logarithm. We then multiply these two values TF and IDF. We used sklearn tf-idf-transformer which transforms a count matrix to a normalized tf or tf-idf representation.

**2.  LDA:**
    Latent Dirichlet Allocation (LDA) algorithm is an unsupervised learning algorithm that attempts to describe a set of observations as a mixture of distinct categories. LDA is most commonly used to discover a user-specified number of topics shared by documents within a text corpus. Here each observation is a document, the features are the presence (or occurrence count) of each word, and the categories are the topics. Since the method is unsupervised, the topics are not specified upfront and are not guaranteed to align with how a human may naturally categorize documents. The topics are learned as a probability distribution over the words that occur in each document. Each document, in turn, is described as a mixture of topics.

## Classification Algorithms:
![](https://i.ibb.co/hfLPdTW/4.png)
![](https://i.ibb.co/GWDwLR0/5.png)
![](https://i.ibb.co/s95hssL/6.png)

![](https://i.ibb.co/qRrgFM9/7.png )
## Clustering Algorithms
![](https://i.ibb.co/Prc25KD/8.png)
## K-Means + LDA 
![](https://i.ibb.co/m0G0cNc/9.png)
![](https://i.ibb.co/RSmChx3/10.png)
- We implement 3 algorithms:

- K-Means:
     The goal of this algorithm is to find groups in the data, with the number of groups represented by the variable K. The algorithm works iteratively to assign each data point to one of K groups based on the features that are provided. Data points are clustered based on feature similarity. The results of the K-means clustering algorithm are:

1.  The centroids of the K clusters, which can be used to label new data

2. Labels for the training data (each data point is assigned to a single cluster)
# Evaluation
## Classification Evaluation
![](https://i.ibb.co/9qMpKk2/11.png" alt="11)
## Clustering Evaluation
![](https://i.ibb.co/rFyQxP0/12.png)
![](https://i.ibb.co/tD8J05D/13.png)

Accuracy of the system is **66.5%**
## Error Analysis

- 	Remove the very beginning and the very last paragraphs of each book

- 	Remove the most frequent and the least weighted words from TF-IDF Transformation

- 	Try different collections of books
![](https://i.ibb.co/MNC91rL/14.png)
![](https://i.ibb.co/WvZVcnG/15.png)

