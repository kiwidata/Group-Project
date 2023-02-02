# Group Project - Emission by Country
Carbon emissions and environmental protection issues become a widely used term and concept in the public debate on responsibility and abatement action against the threat of global climate change. Therefore, forecasting carbon emissions is of great significance to track countries' progress in meeting carbon emission targets set by the Paris Climate Agreement. This project analyzes estimates of global and national CO2 emissions using machine learning models aiming to predict CO2 emissions from country-specific parameters such as emissions from fossil fuels and emissions per capita.

# Dataset information
This dataset provided by CICERO Center for International Climate Research as part of the Global Carbon Project is an in-depth look into the global CO2 emissions at the country-level, facilitating a better comprehension of each nation's contribution to the global cumulative impact of human activity on climate. Emissions from coal, oil, gas, cement, flaring, and other sources, as well as emissions per capita, are all included in this country-level survey of global fossil CO2 emissions.

The dataset is publicly available at https://doi.org/10.5281/zenodo.7215364 and licenced under the <a href="https://datacatalog.worldbank.org/public-licenses#cc-by">Creative Commons Attribution 4.0 International license</a>.

# Project structure

The project is divided into three stages:

* Stage 1: Data cleaning and preparation
* Stage 2: Data exploration and visualization
* Stage 3: Predictive analysis with the machine learning algorithm

# Built with

* **Programming language**
	- Python 3.7
* **Libraries**
	- **dataset handling**: pandas, numpy
	- **data visualization**: tableau, matplotlib
	- **machine learning**: scikit-learn
* **Presentation**: 
	- Jupyter Notebook
  
# Summary of all project stages
The highlights of all project stages are briefly introduces in the following:

### Stage 1: Data cleaning and preparation

* Global data overview
* Definition of the initial project goals
* Data cleaning
    - dealing with missing values
    - transformation of the columns into a numerical data type
    - renaming of features
    - removing empty columns and rows
* Data frame transformation
    - melting of the data for each variable
    - integration of the data into a suitable data frame format
* Removal of missing values
    - detection of missing values
    - removal of missing values by filtering the columns and rows, so that minimal amount of features and rows are lost
* Export the clean data frame to a file

### Stage 2: Data exploration and visualization

* Feature/column abbreviations and units
* Definition of the hypothesis to be tested
* Feature engineering
    - features overview
    - derivation of additional important features
    - removal of unnecessary features
* Prepare the visualization
* Create plots
	- a global look onto all relationships and detailed plots of chosen dependencies
    - detection of outliers
    - discussion of dependencies and trends
* Conclusions

### Stage 3: Predictive analysis with the machine learning algorithm

* Selection of dependent and independent variables
* Dataset splitting into training and test subsets
* Feature selection with recursive feature elimination and cross-validation
* Conclusions

# SQL/RDS/EDR

# Statistics and Linear Regression

## Overview

Two Goals were set for this analysis.
1) Statical Analysis to find the countries that contributed the most to global emissions. 
2) The global emission trends and predictions to see if the Paris Accord 2030 Goal of CO2 Emission can be reached. The Paris Accord states that the goal for Emission should be at least a 40% reduction by 2030 compared to 1990 levels.

## Results

### Top 3 Polluters

Based on our dataset : China (30.9%), USA (13.5%), India (7.3%) are the world biggest polluters. These 3 countries emitted more than 51.7% (19189 MtCO2) of all global CO2 in 2021.

![Top 3 Polluters ](https://user-images.githubusercontent.com/111706055/215375812-a95d7479-8eac-4b3d-80fb-9d0c6245e846.png)

### Emission Trends & Linear Regression

Looking at Emission Trends, we looked at 4 different timeframes : 1750-2021, 1900-2021, 2000-2021, and 1980-2021.

#### 1750-2021
The graph below shows an exponential growth in MtCO2 emission from 1750-2021.

![1750_2021 timeframe](https://user-images.githubusercontent.com/111706055/215376639-8ccdb183-1bce-493a-93d3-9f3a32aadbe0.png)

A linear regression was made by changing the emission variable into a log function.

![1750_2021 timeframe log scales](https://user-images.githubusercontent.com/111706055/215959763-988bd2c3-def3-4725-98e4-5b3e3b5c46f3.png)

These graphs really does show the massive upscale of CO2 over the years. The R2 for the linear regression is 98.7% accurate which should in theory give us a very good prediction. Howvever the predictions seems quite high. Even looking at 2021 it shows 63487.6 MtCO2 which is almost double the actual number that we currenty have (37123 MtCO2). In 2100 its shows more than 20x the amount of CO2 emission than 2021. The growth rate of CO2 emission did change over the years, hence this model cannot be use because it assumes a constant growth rate and the predictions seems off the charts. The timeframe had to be adjusted to more recent dates.

### 1900-2021

The graph below shows more a linear growth than an exponential growth. Linear regression was used for this data. 

![1900_2021 timeframe](https://user-images.githubusercontent.com/111706055/215377535-a33c8826-f855-43d5-91d7-e760ae31b9bb.png)

The R2 was accurate by 90.7% which mean the predictions were accurate by 90.7%. However it seems that the emission growth rate changed drastically over the last 120 years. Using this linear model we predicted by 2020 there would be 31907.7 MtCO2 emitted, but in actuality it was 35264.08 MtCO2 globally. The emission growth rate is still a factor. Hence we reduced the timeframe to look at more recent dates to find more accurate predictions that would assumed the actual current CO2 emission growth rate.

![1900_2021 linear](https://user-images.githubusercontent.com/111706055/215378373-cbfabc9c-4c64-403b-b9de-83fe67222fa9.png)


### 2000-2021

The graph still shows a linear growth and its R2 is 91.4% accurate. However it does appear less agressive than the previous plot from 1900-2021.
This might signal a plateau for the emission. Hence this might signal better predictions. Furthermore the 2021 emission (38555.41 MtCO2) of this linear regression is much closer to the 2021 total actuals of 371123.85 MtCO2 which reinforced the theory of a better prediction than the previous 1900-2021 model. 

![2000_2021 timeframe](https://user-images.githubusercontent.com/111706055/215378649-7c76645f-0d06-4c16-9bb2-6c9b07f083cd.png)

Comparing both linear model predictions '1900-2021' and '2000-2021' we have the following:

![both models](https://user-images.githubusercontent.com/111706055/215379183-37b05b74-484c-4b17-9121-197ac0b4b307.png)

The prediction from the '2000-2021' model is more than 50% than that of the 1900-2021 model in 2100. Both are accurate in term of their R2. However the predictions are not close. This shows the growth rate of emission is not constant and actually accelerated over time. One final linear regression with the timeframe of 1980-2021 was done to compare to the 2000-2021 timeframe.

### 1980-2021
The graph still shows a linear growth and its R2 is 96.37% accurate.This is more than 5% more accurate than our previous models (not including the 1750-2021 model). The 2021 emission (37661 MtCO2) of this linear regression is much closer to the 2021 total actuals of 371123.85 MtCO2 than our previous models. This model seems to have the best accuracy and also take in consideration the actual growth rate.

![1980_2021 timeframe](https://user-images.githubusercontent.com/111706055/215379606-f626836d-9774-4efc-b259-c8b46f8a7ecb.png)

Comparing the linear model predictions '1900-2021', '2000-2021', '1980-2021' we have the following:

![model comparison ](https://user-images.githubusercontent.com/111706055/215380250-68e775a5-9e09-4389-a781-db384c399e18.png)

The prediction models 2000-2021 and 1980-2021 seems very close. Especially looking at the next 5 years. This shows evidence that the actual growth rate did not change much during the last 40 years and that the prediction model can be used.The prediction does start to diverge the longer time passes. 

The model comparison shows 3 important components:

- Since 1900 the emission growth rate has drastically increased and our predicted emission shifted upward over the years. This is apparent looking at the 2020 year where the actual CO2 emission quantity is much larger than the predicted forecast of the '1900-2021' trend.

- The graphs shows that the emission level does seems to want to plateau in term of growth rate. This is evident since the 1980-2021 and 2000-2021 models are very close in term of predictions. 

- All graphs shows that the CO2 level will keep increasing with the current global emission rate. This is true for all 3 predictions. 

The table below shows the prediction rate of all the models in the next 30 years. 

![all model forecast including exp](https://user-images.githubusercontent.com/111706055/215960400-e1bcffe8-7b98-47c3-92fc-08231024ae2d.png)

All models indeed shows an increase in CO2 emission globally over the years.

## Conclusion 

The top 3 polluting countries (China, USA, and India) contributes to more than 51% of all global CO2 currently (2021).

In 1990 global emissions were 22757.48 MtCO2. Based on the paris accord the goal was to reduce emissions by at least 40% by 2030 (~16000 MtCO2) compared to 1990 levels. However based on our models this will not be the case. The most accurate model '1980-2021' shows a prediction of 42129 MtCO2 in 2030. An 85% increased from 1990. The most optimistic model '1900-2022' shows a prediction of 34367 MtCO2 by 2030 which would show a slight decline from today's level, however this is assuming emission growth rate decrease, and even then it will not meet the desired goal. We can conclude that, based on these models, The paris climate accord goal of CO2 emission will not be reached based on the current levels of global emissions. This is assuming the emission trend remains the same. 


# Tableau
