Topic Review Extraction - HR
==============================

Author: Santosh Yadaw | [LinkedIn](https://www.linkedin.com/in/santosh-yadaw-b32025111/) | [Github](https://github.com/SantoshYadaw/)

Overview
------------

In this project, we aim to train a model to extract common themes/reviews from a review data set

Project Organization
------------

    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. 
    │
    ├── setup.yml   <- The requirements file for reproducing the analysis environment
    │
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │

--------

Environment Setup
------------
1. Build the necessary environment to run the code
```conda env create -f setup.yml```

2. Ensure your have downloaded the dataset from the repo and it is placed under data > raw folder.
--------

Usage via Notebook
------------
Run the notebooks in the order below to perform EDA, Model training and Model evaluation

1. [01_eda.ipynb](notebooks/01_eda.ipynb)
2. [02_topic_model.ipynb](notebooks/02_topic_model.ipynb)

[TODO]: Usage via Scripts
------------

Exploratory Data Analysis
------------

Exploratory Data Analysis notebook can be found in [01_eda.ipynb](notebooks/01_eda.ipynb). Please refer to the notebook for the details.


Topic Modeling Approachs
-----------

More in-depth analysis of the performance can be found in [02_topic_model.ipynb](notebooks/02_topic_model.ipynb). 

1. Latent Dirichlet Allocation (LDA) is a popular method for topic modeling. This helps identify overarching topics in the entire dataset.

2. Embedding based Approaches + Clustering: The idea here is to try different embedding based model to convert the employee feedback into embeddings and then try to cluster them using different clustering algorithms. The underlying assumption here is that employee feedbacks which are similar in the embedding space will belong to a specific topic. This method would produce better results over LDA since it can help to preserve the semantic and syntactic meaning instead of using the traditional BOW approach. 

a. Doc2Vec + KMeans - Using of Doc2Vec to generate the embeddings to generate topics followed by using Kmeans clustering method to cluster the similar documents together.

<p align="center">
  <img src="references/Topics_by_department_LDA_kmeans.png" width=35%/>
  <br>                  
</p>

b. Doc2Vec + Kmeans - Convert documents to embeddings via Doc2Vec model. Clusters are form via Kmeans - documents with underlying similarity are likely similar documents/topics.

<p align="center">
  <img src="references/Topics_by_department_doc2vec_kemans.png" width=35%/>
  <br>                  
</p>

c. SBert + DBScan - Convert documents to embeddings via SBERT model. Clusters are form via DBScan (Density-Based Spatial Clustering of Applications with Noise - density based cluster technique that groups data points based on their density and proximity to each other) - documents with underlying similarity are likely similar documents/topics.

Why use DBScan?
- Groups 'densely grouped' data points into a single cluster
- Identifies clusters in large spatial datasets by looking at the local density of the data points
- Robust to outliers 
- Does not require us to specify the number of clusters beforehand like K-Means

<p align="center">
  <img src="references/Topics_by_department_sbert_dbscan.png" width=35%/>
  <br>                  
</p>

d. SBert + HDBScan - Convert documents to embeddings via SBERT model.Clusters are form via HDBScan (Hierarchical Density-Based Spatial Clustering of Applications with Noise - density based cluster technique that groups data points based on their density and proximity to each other and over varying epsilon values and integrates the results tgo fgind the cluster that gives the best stability over epsilon) - documents with underlying similarity are likely similar documents/topics.

Why use HDBScan?
1. More robust to varying DBScan
2. Good clustering out of the box without miuch parameter tuning
3. Robust to outliers 
4. Does not require us to specify the number of clusters beforehand like K-Means

<p align="center">
  <img src="references/Topics_by_department_sbert_hdbscan.png" width=35%/>
  <br>                  
</p>

Future Work
------------

References
------------