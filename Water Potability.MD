This document contains an explanation of each variable in the dataset, followed by the notes I've been taking along the analysis process.


Content
The water_potability.csv file contains water quality metrics for 3276 different water bodies.

1. pH value:
PH is an important parameter in evaluating the acid–base balance of water. It is also the indicator of acidic or alkaline condition of water status. WHO has recommended maximum permissible limit of pH from 6.5 to 8.5. The current investigation ranges were 6.52–6.83 which are in the range of WHO standards.

2. Hardness:
Hardness is mainly caused by calcium and magnesium salts. These salts are dissolved from geologic deposits through which water travels. The length of time water is in contact with hardness producing material helps determine how much hardness there is in raw water. Hardness was originally defined as the capacity of water to precipitate soap caused by Calcium and Magnesium.

3. Solids (Total dissolved solids - TDS):
Water has the ability to dissolve a wide range of inorganic and some organic minerals or salts such as potassium, calcium, sodium, bicarbonates, chlorides, magnesium, sulfates etc. These minerals produced un-wanted taste and diluted color in appearance of water. This is the important parameter for the use of water. The water with high TDS value indicates that water is highly mineralized. Desirable limit for TDS is 500 mg/l and maximum limit is 1000 mg/l which prescribed for drinking purpose.

4. Chloramines:
Chlorine and chloramine are the major disinfectants used in public water systems. Chloramines are most commonly formed when ammonia is added to chlorine to treat drinking water. Chlorine levels up to 4 milligrams per liter (mg/L or 4 parts per million (ppm)) are considered safe in drinking water.

5. Sulfate:
Sulfates are naturally occurring substances that are found in minerals, soil, and rocks. They are present in ambient air, groundwater, plants, and food. The principal commercial use of sulfate is in the chemical industry. Sulfate concentration in seawater is about 2,700 milligrams per liter (mg/L). It ranges from 3 to 30 mg/L in most freshwater supplies, although much higher concentrations (1000 mg/L) are found in some geographic locations.

6. Conductivity:
Pure water is not a good conductor of electric current rather’s a good insulator. Increase in ions concentration enhances the electrical conductivity of water. Generally, the amount of dissolved solids in water determines the electrical conductivity. Electrical conductivity (EC) actually measures the ionic process of a solution that enables it to transmit current. According to WHO standards, EC value should not exceeded 400 μS/cm.

7. Organic_carbon:
Total Organic Carbon (TOC) in source waters comes from decaying natural organic matter (NOM) as well as synthetic sources. TOC is a measure of the total amount of carbon in organic compounds in pure water. According to US EPA < 2 mg/L as TOC in treated / drinking water, and < 4 mg/Lit in source water which is use for treatment.

8. Trihalomethanes:
THMs are chemicals which may be found in water treated with chlorine. The concentration of THMs in drinking water varies according to the level of organic material in the water, the amount of chlorine required to treat the water, and the temperature of the water that is being treated. THM levels up to 80 ppm is considered safe in drinking water.

9. Turbidity:
The turbidity of water depends on the quantity of solid matter present in the suspended state. It is a measure of light emitting properties of water and the test is used to indicate the quality of waste discharge with respect to colloidal matter. The mean turbidity value obtained for Wondo Genet Campus (0.98 NTU) is lower than the WHO recommended value of 5.00 NTU.

10. Potability:
Indicates if water is safe for human consumption where 1 means Potable and 0 means Not potable.


## Choose metric
https://machinelearningmastery.com/framework-for-imbalanced-classification-projects/


## EDA

* Check for missing values and for errors. The library `pandas_profiling` comes in handy. 
    ```
    # looking at stats
    pandas_profiling.ProfileReport(df)
    ```
* Plot data distribution. All variables look Gaussian.

* There is no qualitative variable, so there is no need for mapping any variable or creating dummy variables.

* Correlation matrix

* Are classes balanced?

* There are missing values. Do we assume MAR, MCAR or MNAR? How many missings are there per variable and in which proportion? Does some particular observation contain a lot of missing values? Should we delete observations or impute with the median or the mean or kNN? 

* Variable pH is measured with a logarithmic scale, while other variables proably measure in linear scale. Perhaps should take this into account to improve the model's performance.

* tSNE and MDS to assess separability

## Spot checking models/algorithms
https://machinelearningmastery.com/framework-for-imbalanced-classification-projects/

* QDA
* Logistic regression

* SVM
* Kernel SVM
* Decision tree
* kNN
* MLP

* Random forest
* XGBoost


* Random oversampling

* SVM SMOTE

* SMOTE and Random undersampling

* Weighted logistic regression

* SVM using `class_weight` and `sample_weight`


## Fine-tune promising models/algorithms Choose best model(s)
I've decided to tune hyperparameters and compare models all in one single step, instead of spotting various models first and then fine-tuning the most promising ones. This allows to fairly compare models with a set of good hyperparameters. Nonetheless, the chosen model(s) will have to be tuned on the whole training set to predict on the testing set and extract a generalization error.

The metric by which to compare models shall be determined based on the model's output (whether it be probabilities or labels) and the problem at hand (e.g. do we we favor error type I or II?)


## Error Analysis and presentation of resultsd