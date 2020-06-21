# SPE-201351-MS
__Big Data and Machine Learning Analysis of Eagle Ford EUR prediction__

Title: __Regional to Local Machine-Learning Analysis for Unconventional Formation Reserve Estimation: Eagle Ford Case Study__

Authors: __Peidong Zhao, Rencheng Dong, Yu Liang__

SPE/OnePetro ID: __SPE-201351-MS__

## Abstract

Unconventional tight reservoirs currently make up more than 60% of domestic oil and gas production in the United States. However, developing unconventional formations requires intensive drilling and completion campaigns to maintain steady production of a field. Therefore, the prediction of estimated ultimate recovery, which measures the producible reserve from a well, is demanding, particularly as operators becomes more rational under the current volatile market conditions. Despite unconventional reservoirs being considered a resource play with low geological risks, their economic appraisal is challenged by unknown stimulation outcomes and intricate producing mechanisms. Therefore, this work aimed to leverage machine-learning techniques with big data to analyze the multivariant relationship of geological and engineering parameters with unconventional reservoir production and to improve the prediction of estimated ultimate recovery in unconventional formations.

In this case study, a multiscale machine-learning workflow was deliberated and applied to a big data set from the Eagle Ford shale. First, quality control and feature selection were performed on a data set consisting of 4,067 wells with 30+ geophysical, petrophysical, drilling and completion, and production features. Then, a regional inferencing model, based on a K-nearest neighbor with bagging algorithm, was trained to obtain the spatial trend of estimated ultimate recovery across the Eagle Ford formation. The last part of the analysis was to build a local-scale prediction model. With the study area confined to East Texas, a random forest regression was performed to rigorously predict oil and gas estimated ultimate recoveries. The selected training features were finalized based on the results of a higher-dimension regression, as well as domain knowledge. Overall, the data-driven model trained with physically controlled data captured the production behavior of the Eagle Ford shale.

The application of the proposed workflow on the Eagle Ford shale demonstrates a progressive building of the machine-learning model. The quality control of data allows global inspection of the data set and, more importantly, confirms the statistical distribution of training data. This study emphasizes the philosophy of multiscale data analytics. The large-scale model portraying sweet spots using location variables grants direct guidance for acreage acquisition and development across the basin; the small-scale model trained with reduced dimensionality generates quantitative prediction of oil and gas estimated ultimate recoveries for an area of interest. Compared with our previous work using higher dimensionality and extensive spatial interest, this progressive learning maintains similar explained variance in out-bag model check, but grants 26% and 52% reductions in mean square error for predicting oil and gas estimated ultimate recoveries in the Eagle Ford formation. In the end, prediction validation is performed by revisiting the data set. Overall, the proposed workflow demonstrates successful application in the Eagle Ford formation such that it can be directly implemented for other unconventional resource plays.


## Conflicts of Interest Statement
The contributors of this repository declare no competing interests. This repository is for educational purposed only. For additional information request, please contact
  * Yu (Reservoir+Production+Completion, liangyu@utexas.edu) for Dataset and ML regression
  * Peidong (Geomechanics+Drilling+Completion, peidongzhao@utexas.edu) for Trend Model and ML regression
  * Rencheng (Reservoir+Production, rencheng_dong@utexas.edu) for Geostatistical Model and Trend Model

## ML workflow for Unconventional Formation Reserve Estimation

<p>
    <img src="/MachineLearning_Plot/02_ML_WorkFlow.png"  />
</p>

## Data and Feature Selection 
Dataset or sensitive information is unpublished for confidentiality.

The training data for each model are selected from total of 4,067 wells based on two criteria: credential source and statistical distribution. 
  1. Trend Model (KNN-bagging Algorithm)
      * 1st screening: select wells from operator with 30+ wells in the basin
      * 2nd screening: remove wells with super-high EUR  ( Oil > 4.5e5 bbl, Gas > 4.5e6 boe)
      * Training Data: 3,000+ wells across Eagle Ford
      * Predictor Features: relative location
      * Respondse Features: Oil EUR, Gas EUR
  
  2. Predicting Model (Random Forest Regression)
      * Multicolinearity mitigation: pair-wise Pearson correlation coefficient
      * Domain Knowledge: Geology, Geomechanics, Reservoir Engineering, etc.
      * Training: 200+ wells in East Texas
      * Predicting Features: 
        - well location, well depth, lateral length, horizontal azimuth, and proppant intensity (lb/ft)
        - oil type, TOC, VRE, hydrocarbon pore volume, compressive strength, Young's modulus, pressure gradient, Upper Eagle Ford thickness, Lower Eagle Ford thickness, , density of producing fluid
      * Respondse Features: Oil EUR, Gas EUR
## Eagle Ford Shale Trend Model

<p>
    <img src="/MachineLearning_Plot/09_Oil_KNN_Map_2.png" width='50%'height= '50%' | img src="/MachineLearning_Plot/06_Gas_KNN_Map_2.png" width='50%' height= '50%'>
    </>
</p>

## EUR Prediction for East Texas Eagle Ford
### Oil EUR

<p>
    <img src="/MachineLearning_Plot/25_RandomForest_Oil_3_FeatureImportance.png" width='50%'height= '50%' >
</p>

### Gas EUR
</p>
    <img src="/MachineLearning_Plot/19_RandomForest_Gas_3_FeatureImportance.png" width='50%' height= '50%'>
</p>

## Conclusions
In this study, we present a multiscale machine-learning workflow to predict EUR in unconventional formations. The latest approach reduces predicting error by more than 50% compared with our previous work on the Eagle Ford shale. The workflow consists of four parts: data collection, data preprocessing and quality control, trend modeling, and regression modeling. 

The deliberated quality control of data and feature selection underwrites the predicting accuracy of machine learning. Feature selection was performed iteratively using machine-learning results from previous work while being guided by domain knowledge. The reduced dimensionality proved beneficial in the subsequent model building.

The trend model adopted a KNN-bagging algorithm. With well location being the only training feature, the EUR trend was mapped across the formation. Results from the trend model delineated multiple sweet spots within the Eagle Ford region, implying locations for future drilling. The regional-scale trend model also indicated two distinct trends in South Texas and East Texas. With that, the East Texas area was cropped for the local-scale regression model. Compared with simple kriging results, the KNN-bagging method shows the advantage of simplicity and adaptability for large-scale data sets with complicated spatial variations.

The regression model selected the random forest algorithm to predict oil and gas EURs in the East Texas Eagle Ford formation. The random forest regression was performed under rigorous cross-validation and hyperparameter tuning. With reduced training features and spatial interest, the explained variance was the same for gas EUR and 61% decline for oil EUR, but the mean square error of testing achieved striking reductions of 52% for gas EUR and 26% for oil EUR. The results of feature ranking indicate influence from the randomness of training and test split and random forest algorithm, so we implemented an ensemble approach to resolve the issue.

In the end, we revisited the data set to validate the machine-learning results. The high-production wells are clustered within a specific range of geological features. However, regarding the dispersed distribution of EUR at a promising feature value, we suggest developing probability-based models for future work to assess subsurface uncertainty. The review of engineering features indicates the needs of the latest data, which would expand the learning scope of the computer algorithm. To further extend this workflow, we also specify to include operational cost to perform economic optimization of the well using the regression results.

Overall, with the assistance of the progressive learning and guidance of domain knowledge, this work shows boosted capability in predicting Eagle Ford EUR as compared to our previous work. The workflow presented in this work can be directly adopted to other unconventional plays.

## Acknowledgements 

The authors wish to thank [Prof. Michael Pyrcz](https://github.com/GeostatsGuy) and Honggeun Jo at the University of Texas at Austin for their helpful discussions during the courses of geostatistics and subsurface machine learning. Our program has applied open-source packages: scikit-learn (https://pypi.org/project/scikit-learn) and GeostatsPy (https://pypi.org/project/geostatspy).




