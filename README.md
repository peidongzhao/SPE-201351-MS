# SPE-201351-MS
Big Data and Machine Learning Analysis of Eagle Ford EUR prediction

Title: Regional to Local Machine-Learning Analysis for Unconventional Formation Reserve Estimation: Eagle Ford Case Study

Authors: Peidong Zhao, Rencheng Dong, Yu Liang

SPE/OnePetro Document ID: SPE-201351-MS

Abstract: To be uploaded

## Conflicts of Interest Statement
The contributors of this repository declare no competing interests. This repository is for educational purposed only. For additional information request, please contact
  * Yu (Reservoir+Production+Completion, liangyu@utexas.edu) for Dataset and ML regression
  * Peidong (Geomechanics+Drilling+Completion, peidongzhao@utexas.edu) for Trend Model and ML regression
  * Rencheng (Reservoir+Production, rencheng_dong@utexas.edu) for Geostatistical Model and Trend Model

## ML workflow for Unconventional Formation Reserve Estimation

<p>
    <img src="https://github.com/peidongzhao/SPE-201351-MS/blob/master/MachineLearning_Plot/02_ML_WorkFlow.png"  />
</p>



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
