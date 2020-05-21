# SPE-201351-MS
Jupyter Notebook for Eagle Ford EUR prediction

Title: Region-to-Local Machine Learning Analysis for Unconventional Formation Reserve Estimation: Eagle Ford Case Study

Authors: Peidong Zhao, Yu Liang

SPE/OnePetro Document ID: SPE-201351-MS

Abstract: To be uploaded

## Conflicts of Interest Statement
The contributors of this repository declare no competing interests exist. This repository is for educational purposed only. The contributors can be reached at peidongzhao@utexas.edu and liangyu@utexas.edu 

## Data and Feature Selection 
Dataset or sensitive information is unpublished for confidentiality.

The training data for each model are selected from total of 4067 wells based on two criteria: credential source and statistical distribution. 
  1. Trend Model (KNN+Bagging)
      * 1st screening: select wells from operator with 30+ wells in the basin
      * 2nd screening: remove wells with super-high EUR  ( Oil > 4.5e5 bbl, Gas > 4.5e6 boe)
      * Train Data: 3785 wells
      * Predictor Features: relative location
      * Respondse Features: Oil EUR, Gas EUR
  
  2. Predicting Model (Random Forest Regression)
      * Multicolinearity mitigation: pair-wise Pearson correlation coefficient
      * Domain Knowledge: Geology, Geomechanics, Reservoir Engineering, etc.
