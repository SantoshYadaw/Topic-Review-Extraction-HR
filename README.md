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
2. [02_train_gpt2.ipynb](notebooks/02_train_gpt2.ipynb)
3. [03_predict_gpt2.ipynb](notebooks/03_predict_gpt2.ipynb)

Usage via Scripts
------------
If you wish to run via the python scripts, run them in the following order

1. Preprocess the raw data:
``` python -m src.data.make_dataset ```

2. Train the gpt2 model:
``` python src.models.train_model ```

3. Call inference using trained gpt2 model:
``` python src.models.predict_model ```

Exploratory Data Analysis
------------

Exploratory Data Analysis notebook can be found in [01_eda.ipynb](notebooks/01_eda.ipynb). Please refer to the notebook for the details.


Evaluation Metrics
------------
The Evaluation notebook can be found in [03_predict_gpt2.ipynb](notebooks/03_predict_gpt2.ipynb). Two evaluation metrics were considered to evaluate the output from the trained gpt2 model against the original given text in the validation dataset.


Model's Performance
------------

Future Work
------------


References
------------